## Usage

[原README.md](https://github.com/yujintang/mongo-cluster-docker/blob/master/README_old.md)

**本教程用于单机搭建mongodb集群环境、以供开发使用，请勿用于生产环境**

### 1. clone
```
git clone git@github.com:yujintang/mongo-cluster-docker.git
cd mongo-cluster-docker
```

### 2.初始化volume对应文件夹
```
./init_dir.sh
```

### 3.使用docker-compose启用mongodb-cluster
```
docker-compose up -d
```
### 4.进入mongo-router并设置某个数据库分片
#### 4.1 进入docker
```
docker-compose exec mongo-router mongo
```
#### 4.2 切换admin
```
use admin
```
#### 4.3 查看分片状态
```
sh.status()
```
#### 4.4 对test数据库分片
```
db.runCommand({ enablesharding: 'test'})
```
### 4.关闭docker-cluster
```
docker-compose stop
```
### 5.移除docker-cluster
```
docker-compose rm
```
## Port 映射本地端口
```
Sharding1: 30011,30012, 30013
Sharding2: 30021,30022, 30023
config: 30001, 30002, 30003
router: 40000
```