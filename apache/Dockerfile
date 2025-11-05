FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# Update Ubuntu and install Apache + DNS tools
RUN apt-get update && \
    apt-get install -y -qq --no-install-recommends \
        apache2 \
        dnsutils \
        netbase \
        iputils-ping \
        curl && \
    a2enmod proxy proxy_http proxy_ajp rewrite deflate headers proxy_connect proxy_html lbmethod_byrequests && \
    mkdir -p /var/lock/apache2 /var/run/apache2 && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Copy files
COPY index.html /var/www/html/index.html
COPY 000-default.conf /etc/apache2/sites-enabled/000-default.conf

EXPOSE 80
CMD ["apache2ctl", "-D", "FOREGROUND"]

