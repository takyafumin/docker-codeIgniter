# docker-codeIgniter

codeIgniter用のdocker環境

## 環境

- PHP 7.2.8


## ディレクトリ構成

|ディレクトリ|用途|
|--|--|
|docker/|docker関連ファイル
|src/|プログラムソース|
|README.md|このファイル|

## 使い方

git clone し、dockerにて起動する

```bash
git clone https://github.com/takyafumin/docker-laravel.git
cd docker-codeIgniter
docker-compose up -d


# dockerプロセス確認
$ docker-compose ps
        Name                       Command              State           Ports
--------------------------------------------------------------------------------------
codeigniter-dev_db_1    docker-entrypoint.sh mysqld     Up      0.0.0.0:3306->3306/tcp
codeigniter-dev_php_1   docker-php-entrypoint php-fpm   Up      9000/tcp
codeigniter-dev_web_1   nginx -g daemon off;            Up      0.0.0.0:8000->80/tcp
```

codeIgniter プロジェクトを作成する(ローカルで実行)

```bash
docker-compose exec php composer create-project kenjis/codeigniter-composer-installer ci
```

nginxのdocumentRootを変更する

```bash
# default.conf
-    root  /var/www/html;
+    root  /var/www/html/ci/public;
```

nginxの設定を反映する

```bash
docker-compose down && docker-compose up -d
```
