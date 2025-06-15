FROM php:8.2-apache

# Устанавливаем необходимые модули
RUN docker-php-ext-install pdo pdo_pgsql pgsql

# Загружаем HotelDruid
RUN curl -L https://www.hoteldruid.com/download/hoteldruid-latest.tar.gz | tar xz -C /var/www/html/ --strip-components=1

# Права на папку
RUN chown -R www-data:www-data /var/www/html

# Открываем порт
EXPOSE 80
