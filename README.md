
## mongodb


## 前言
在laravel 里面集成mongodb 

## 手动安装 以Ubuntu为例
 [官方文档地址](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)

## 1.确定系统版本

> $ cat /etc/issue

### 2.Import the public key
> $ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4

### 3.Create a list file for MongoDB
> $ echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list

### 4.Reload local package database
> $ sudo apt-get update

### 5. Install the MongoDB packages
> $ sudo apt-get install -y mongodb-org

### 6. 安装完成后，在命令行执行 mongo 就可以进入 Mongodb
> $ sudo service mongod start

### 7.进入mongo
> $ mongo

### 8.use admin;
> use admin;

### 9.创建一个用户，用户名叫 homestead，密码是 secret， 角色是超级管理员 root
> db.createUser({user:'homestead',pwd:'secret',roles:['root']})

### 10. 安装PHP mango 拓展
> $ sudo apt-get install php-mongodb

### 11.使用下面命令检查是否完成

> $ php -m | grep mongodb

### 12.在laravel 项目中安装 jenssegers/mongodb *laravel 5.5需要安装3.3 5.6以上需要3.4
> $ composer require jenssegers/mongodb:~3.4.0

### 13.配置config/database.php
> 'connections' => [
      'mongodb' => [
          'driver'   => 'mongodb',
                     'host'     => env('MONGODB_HOST', 'localhost'),
                     'port'     => env('MONGODB_PORT', 27017),
                     'database' => env('MONGODB_DATABASE'),
                     'username' => env('MONGODB_USERNAME'),
                     'password' => env('MONGODB_PASSWORD'),
                     'options'  => [
                         'database' => 'admin' // sets the authentication database required by mongo 3
                     ]    
      ]
]



