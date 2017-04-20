FROM ubuntu:latest
MAINTAINER Little Mouse <xiaomiwujiecao@gmail.com>
ENV PORT 22287
ENV DEPENDENCIES python-gevent python-pip python-m2crypto python-wheel python-setuptools
ENV VERSION v1.1.1

RUN apt-get update \
&& apt-get install -y $DEPENDENCIES \
&& rm -rf /var/lib/apt/lists/* \
&&  pip install shadowsocks
WORKDIR /shadows
ONBUILD ADD ./shadowsocks.json $WORKDIR
ONBUILD EXPOSE $PORT
ONBUILD COPY . $WORKDIR
ONBUILD ENTRYPOINT ["ssserver","-c","shadowsocks.json","start"]
