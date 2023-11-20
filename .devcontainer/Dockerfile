ARG OS_VERSION=39

FROM fedora:${OS_VERSION}

ENV FEDORA_VERSION=39
ENV PHP_VERSION=8.2

RUN dnf update -y && dnf install -y \
    curl \
    git \
    unzip \
    wget \
    vim \
    && dnf clean all

# Install PHP
RUN dnf install -y https://rpms.remirepo.net/fedora/remi-release-${FEDORA_VERSION}.rpm
RUN dnf module install -y php:remi-${PHP_VERSION} && php -v

# Install composer
RUN curl -sSL https://getcomposer.org/installer | php \
    && chmod +x composer.phar \
    && mv composer.phar /usr/local/bin/composer

# Install current LTS version of NodeJS
RUN dnf install -y nodejs