# laradock-cakephp4

## インストールログ
### dockerをサブモジュール に追加
$ git submodule add -f https://github.com/laradock/laradock.git laradock
Completed successfully

### .env作成
$ cd laradock/
$ cp env-example .env
$ vim .env

```
- COMPOSE_PROJECT_NAME=laradock
+ COMPOSE_PROJECT_NAME=laradock-cakephp4

- PHP_VERSION=7.3
+ PHP_VERSION=7.4
```

### docker-compose up
$ ./sync.sh up nginx mysql phpmyadmin


### workspaeにログイン
$ ./sync.sh bash

### composer install
$ curl -sS https://getcomposer.org/installer | php


 ### cakephp install
$ composer create-project --prefer-dist cakephp/app cakephp4


### ドキュメントルートの変更
$ vim laradock/nginx/sites/default.conf
-  root /var/www/public;
+  root /var/www/cakephp4/webroot;

### nginxコンテナを再起動
$ docker-compose restart nginx

