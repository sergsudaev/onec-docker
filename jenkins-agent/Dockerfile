ARG DOCKER_USERNAME
ARG BASE_IMAGE
ARG BASE_TAG

FROM ${DOCKER_USERNAME}/${BASE_IMAGE}:${BASE_TAG}

LABEL maintainer="Nikita Gryzlov <NikGryzlov@1bit.com>, FirstBit"

RUN apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
      git \
      locales \
      openssh-client \
      wget \
  && localedef -i ru_RU -c -f UTF-8 -A /usr/share/locale/locale.alias ru_RU.UTF-8

ENV LANG ru_RU.UTF-8

COPY ./jenkins-agent/docker-entrypoint.sh /
RUN chmod 755 /docker-entrypoint.sh \
  && chmod +x /docker-entrypoint.sh

ENTRYPOINT ["/docker-entrypoint.sh"]
