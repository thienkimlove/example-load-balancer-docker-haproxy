# using  docker-app-no-database as example of scale using tutumn/haproxy

# setup


First run with one web container : docker-compose up -d

Benmark : ab -n 1000 -c 100 http://docker4.tuelinh.vn/


Scale : docker-compose scale web=5

Benmakr again using apacheBench.


#normal setup



RUN nginx proxy

docker run -d -p 80:80 --restart=always -v /var/run/docker.sock:/tmp/docker.sock -t jwilder/nginx-proxy

CLONE to directory

git clone git@github.com:thienkimlove/docker-app-no-database.git <directory>

cd <directory> && cp .env.example .env && cp docker-compose.yml.example docker-compose.yml 

EDIT .env AND docker-compose.yml

RUN 

composer install && chmod -R 777 storage && chmod -R 777 bootstrap && mysql -uroot -ptieungao -e "CREATE DATABASE dockerapp;" && php artisan migrate && docker-compose up -d
