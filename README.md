Nuxt v2.14.x
Laravel8.x Sanctum SPA認証

# --------------------------
# Docker
# --------------------------

docker-compose up -d
docker-compose down --rmi all --volumes --remove-orphans

# --------------------------
# Laravel
# --------------------------

composer install
composer create-project --prefer-dist laravel/laravel . "9.*"
chmod -R 777 storage
chmod -R 777 bootstrap/cache/
cp .env.example .env

# artisan
php artisan key:generate
php artisan migrate:refresh --seed

# cors
composer require fruitcake/laravel-cors
php artisan vendor:publish --tag="cors"

# --------------------------
# Nuxt
# --------------------------

# install
yarn install

# start
yarn dev