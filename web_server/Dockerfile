FROM ubuntu:latest
LABEL author="FaunType"

ENV TZ=America/New_York
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update
RUN apt-get install -y apache2 php php-cli php-fpm php-json php-common php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath
RUN mkdir -p /var/lock/apache2
RUN mkdir -p /var/run/apache2

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_PID_FILE /var/run/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_LOG_DIR /var/log/apache2
ENV LANG C


RUN ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load
RUN ln -s /etc/apache2/mods-available/headers.load /etc/apache2/mods-enabled/headers.load

COPY 001-fauntype.conf /etc/apache2/sites-available/001-fauntype.conf
RUN ln -s /etc/apache2/sites-available/001-fauntype.conf /etc/apache2/sites-enabled/001-fauntype.conf

CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
