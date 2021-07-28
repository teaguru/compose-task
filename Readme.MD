1.	Написать 2 Dockerfile с web сервисом прим. (nginx, apache), передать конфигурацию в контейнер прим. nginx.conf ,образы должны работать на разных портах.
2.	Собрать образы, используя double tagging ,положить собранные образы в локальное registry
3.	Написать docker-compose.yaml ,в котором должен быть создан сервис из 2 ранее созданных образов (использовать локальное registry ), с помощью которых можно публиковать статику, образы должны запускаться в разных сетях, но должны использовать 1 хостовой вольюм со статикой на двоих, а также образы должны быть ограничены по ресурсам (memory, cpu)

Итог: через веб браузер должна быть доступна статика на 2 опубликованных портах сервиса.

Собираем images  и публикуем в локальный репозиторий
docker build -t my-apache2:01 -t my-apache2:latest -t my-apache02 .
docker push  localhost:5000/my-apache2

docker build -t some-content-nginx:01 -t some-content-nginx:02 Dokerfile.apache .
docker push  localhost:5000/some-content-nginx