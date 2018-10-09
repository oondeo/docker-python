FROM oondeo/python:3.7 as development

FROM oondeo/alpine:3.8
ENV SUMMARY="python alpine base image without development tools"	\
    DESCRIPTION="Alpine base image. The image use scripts and configurations compatible \
        with redhat openshift."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="python" \
      io.openshift.s2i.scripts-url=image:///usr/libexec/s2i \
      io.s2i.scripts-url=image:///usr/libexec/s2i \
      com.redhat.component="core" \
      name="oondeo/python" \
      version=$ALPINE_VERSION \
      release="1" \
      maintainer="OONDEO <info@oondeo.es>"

COPY --from development /usr/local /usr/

ENV VENV_HOME="$HOME/.env" \
    PYTHON_BIN="python" 

ENV PIP_NO_CACHE_DIR=off \
    PYTHONUNBUFFERED=1 \
    PYTHONIOENCODING=UTF-8 \
    PYTHONDONTWRITEBYTECODE='' \
    PIP_BIN="pip"

RUN install-deps /usr/local 



