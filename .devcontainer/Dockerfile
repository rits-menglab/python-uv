ARG UV_VERSION=0.5.11

FROM ghcr.io/astral-sh/uv:$UV_VERSION AS uv


FROM nvcr.io/nvidia/cuda:12.1.1-devel-ubuntu22.04
ENV DEBIAN_FRONTEND=noninteractive
LABEL maintainer="a5chin <a5chin.origin+contact@gmain.com>"

RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    gnupg \
    netbase \
    sq \
    wget \
    ; \
    rm -rf /var/lib/apt/lists/*

# hadolint ignore=DL3008
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    # For OpenCV etc...
    libgl1 libglib2.0-0 \
    # To remove the image size, it is recommended refresh the package cache as follows
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY --from=uv --chown=vscode: /uv /uvx /bin/
