FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

############
#
# TODO: implement the rest of the image
#
############
WORKDIR /var/task
COPY pyproject.toml ./
COPY handler.py ./

ENV VIRTUAL_ENV="${LAMBDA_TASK_ROOT}/.venv"
ENV PYTHONUNBUFFERED=1
ENV PYTHONPATH="${LAMBDA_TASK_ROOT}/.venv/lib/python3.13/site-packages"
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

RUN uv venv $VIRTUAL_ENV && uv sync

USER root
EXPOSE 8080
CMD ["handler.resize_handler"]
