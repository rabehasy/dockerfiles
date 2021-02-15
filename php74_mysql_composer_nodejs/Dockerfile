FROM php:7.4-fpm

# -------------------------------------------
# Softwares
# ---------------------------------------------
RUN apt-get update -y \
    && apt-get install -y --no-install-recommends libzip-dev libpq-dev zip unzip \
    libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
    libxslt-dev \
    ssh \
    wget

# -------------------------------------------
# Xsl
# ---------------------------------------------
RUN docker-php-ext-install xsl && docker-php-ext-enable xsl

# ----------------------
# GD  
# ----------------------
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install -j$(nproc) gd

# ----------------------
# Mysql  
# ----------------------
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-enable mysqli

# ----------------------
# INTL
# ----------------------
RUN docker-php-ext-configure intl
RUN docker-php-ext-install json calendar intl

# ----------------------
# ZIP
# ----------------------
RUN docker-php-ext-install zip

# ----------------------
# Composer
# ----------------------
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# ----------------------
# Nodejs
# ----------------------
RUN curl -sL https://deb.nodesource.com/setup_15.x | bash -
RUN apt-get install -y nodejs

# ----------------------
# Symfony
# ----------------------
RUN wget https://get.symfony.com/cli/installer -O - | bash
