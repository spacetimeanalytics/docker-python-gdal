FROM ubuntu:16.04
MAINTAINER Erle Carrara <carrara.erle@gmail.com>

ENV GDAL_VERSION=2.1.3
ENV GDAL_VERSION_PYTHON=2.1.3

RUN apt-get update && \
    apt-get -y install \
        wget \
        libcurl4-openssl-dev \
        build-essential \
        libpq-dev \
        ogdi-bin \
        libogdi3.2-dev \
        libjasper-runtime \
        libjasper-dev \
        libjasper1 \
        libgeos-c1v5 \
        libproj-dev \
        libpoppler-dev \
        libsqlite3-dev \
        libspatialite-dev \
        python \
        python-pip \
        python-dev \
        python-numpy-dev


RUN wget http://download.osgeo.org/gdal/$GDAL_VERSION/gdal-${GDAL_VERSION}.tar.gz -O /tmp/gdal-${GDAL_VERSION}.tar.gz && \
    tar -x -f /tmp/gdal-${GDAL_VERSION}.tar.gz -C /tmp

RUN cd /tmp/gdal-${GDAL_VERSION} && \
    ./configure \
        --prefix=/usr \
        --with-python \
        --with-geos \
        --with-geotiff \
        --with-jpeg \
        --with-png \
        --with-expat \
        --with-libkml \
        --with-openjpeg \
        --with-pg \
        --with-curl \
        --with-spatialite && \
    make && make install

RUN rm /tmp/gdal-${GDAL_VERSION} -rf

RUN pip install GDAL==${GDAL_VERSION_PYTHON}

CMD ["python2"]
