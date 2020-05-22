FROM ubuntu:20.04


ENV TZ=Europe/Moscow
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get upgrade -y
# RUN apt-get install -y wget curl gnupg2
# RUN echo `deb [arch=amd64] http://nginx.org/packages/mainline/ubuntu/ disco nginx` > /etc/apt/sources.list.d/nginx.list
# RUN echo `deb-src http://nginx.org/packages/mainline/ubuntu/ disco nginx` > /etc/apt/sources.list.d/nginx.list
# RUN wget http://nginx.org/keys/nginx_signing.key
# RUN apt-key add nginx_signing.key
# RUN apt-get update
RUN apt-get install -y wget curl nginx git php-fpm php-cli php-curl php-mysql php-pgsql php-mbstring


COPY ./conf/default /etc/nginx/sites-available/default
COPY ./conf/www.conf /etc/php/7.4/fpm/pool.d/www.conf

EXPOSE 80
CMD service php7.4-fpm start && nginx && tail -f /var/log/nginx/error.log

