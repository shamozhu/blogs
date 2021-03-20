### Redis是什么?
Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache, and message broker. Redis provides data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes, and streams. Redis has built-in replication, Lua scripting, LRU eviction, transactions, and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster。
以上redis官网上一段原文。

### 安装环境准备
我是在VM中安装CentOS7 64系统，具体安装过程此处省略。
计划安装目录：/data01/app
![image](/resources/images/redis/VM-CentOS.png)


### 下载Redis安装包
打开[https://redis.io/download](https://redis.io/download "https://redis.io/download")，进入redis官网下载，如下图：
![image](/resources/images/redis/redis.png)


当前最新发布的稳定版本为6.2.3，我们点击下载后就要台得到一个redis-x.tar.gz的包。将下载好的安装包传VM中的CentOS中，如下图：
![image](/resources/images/redis/redis-cp.png)

当然，还可以直接在CentOS中直接wget等命令下载。

### 执行解压并安装

```
tar xzf redis-6.2.1.tar.gz
cd redis-6.2.1
make
```
如下图
![image](/resources/images/redis/redis-make.png)

### 启动Redis服务
安装好后，进入src目录启动redis-server

```
cd src
./redis-server
```
![image](/resources/images/redis/redis-server.png)


显示如上，使用是默认商口6379，进程ID为19165，至此安装和启动已经完成。接下来，我们测试一下使用redis-cli来操作数据。

### 使用redis-cli连接Redis服务
我们再打一个Terminal登录，已安装redis-server的那台CentOS的VM,如下：
![image](/resources/images/redis/redis-cli1.png)


进入安装目录/data01/app/redis-6.2.1,并且使用redis-cli连接本机的redis-server

```
cd /data01/app/redis-6.2.1
cd src
./redis-cli
```
![image](/resources/images/redis/redis-cli-test.png)


上图所示，给name set值为"IT码农-三叔"，为啥get出来显示确为乱码啊? 因为我们的中文在Redis中保存的是以UTF8编码后的值，如果想显示为正常的中文值，
只须在启动redis-cli时加上--raw的参数即可。
![image](/resources/images/redis/redis-cli-raw.png)
Over.
