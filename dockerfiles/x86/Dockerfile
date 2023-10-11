FROM public.ecr.aws/sam/build-provided.al2:1.98.0-20231003192354-x86_64

LABEL maintainer="OpenAQ Dev Team <dev@openaq.org>"

RUN yum install -y make sqlite-devel zlib-devel bash git gcc-c++

RUN mkdir -p /build
RUN git clone https://github.com/felt/tippecanoe.git /build/tippecanoe

WORKDIR /build/tippecanoe

# Checkout version 2.32.1
RUN git checkout f7dc7fa 

RUN make \
  && make install

RUN mkdir /build/tippecanoe/bin

RUN cp /build/tippecanoe/tippecanoe /build/tippecanoe/bin/tippecanoe

WORKDIR /build/tippecanoe

CMD zip -r /tmp/build.zip bin
