FROM ywfwj2008/bt-panel:latest
MAINTAINER ywfwj2008 <ywfwj2008@163.com>

ENV REMOTE_PATH=https://github.com/ywfwj2008/bt-panel/raw/master \
    PHP_56_PATH=/www/server/php/56 \
    PHP_70_PATH=/www/server/php/70 \
    PHP_71_PATH=/www/server/php/71 \
    PHP_72_PATH=/www/server/php/72

WORKDIR /tmp

# install php5.6
RUN bash /www/server/panel/install/install_soft.sh 0 install php 5.6 && \
    bash /www/server/panel/install/install_soft.sh 0 install fileinfo 56 && \
    bash /www/server/panel/install/install_soft.sh 0 install opcache 56 && \
    ${PHP_56_PATH}/bin/pecl install redis && \
    ${PHP_56_PATH}/bin/pecl install memcached-2.2.0 && \
    rm -rf /tmp/*

# install php7.0
RUN bash /www/server/panel/install/install_soft.sh 0 install php 7.0 && \
    bash /www/server/panel/install/install_soft.sh 0 install fileinfo 70 && \
    bash /www/server/panel/install/install_soft.sh 0 install opcache 70 && \
    ${PHP_70_PATH}/bin/pecl install redis && \
    ${PHP_70_PATH}/bin/pecl install memcached && \
    rm -rf /tmp/*

# install php7.1
RUN bash /www/server/panel/install/install_soft.sh 0 install php 7.1 && \
    bash /www/server/panel/install/install_soft.sh 0 install fileinfo 71 && \
    bash /www/server/panel/install/install_soft.sh 0 install opcache 71 && \
    ${PHP_71_PATH}/bin/pecl install redis && \
    ${PHP_71_PATH}/bin/pecl install memcached && \
    rm -rf /tmp/*

# install php7.2
RUN bash /www/server/panel/install/install_soft.sh 0 install php 7.2 && \
    bash /www/server/panel/install/install_soft.sh 0 install fileinfo 72 && \
    bash /www/server/panel/install/install_soft.sh 0 install opcache 72 && \
    ${PHP_72_PATH}/bin/pecl install redis && \
    ${PHP_72_PATH}/bin/pecl install memcached && \
    rm -rf /tmp/*

# expose port
EXPOSE 8888 80 443 21 20 888 3306 9001 25

# Set the entrypoint script.
ADD ${REMOTE_PATH}/entrypoint.sh /entrypoint.sh
RUN chmod 777 /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

#Define the default command.
CMD ["supervisord", "-c", "/etc/supervisor/supervisord.conf"]
