## About Docker

Docker 是一个开源的应用容器引擎，让开发者可以打包他们的应用以及依赖包到一个可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。

## [Install Docker](https://docs.docker.com/install/linux/docker-ce)

我们重点说明docker在centos和ubuntu操作系统下的安装和使用，Mac下安装比较简单，直接下载dmg镜像安装即可，使用和centos，ubuntu基本无异，
不推荐在windows下部署，会有文件路径问题抽风。

- Centos系统

  ```shell
  yum install -y yum-utils  device-mapper-persistent-data lvm2sudo 
  yum-config-manager --add-repo  https://download.docker.com/linux/centos/docker-ce.reposudo 
  yum install docker-ce -y
  systemctl enable docker
  systemctl start docker
  ```

在安装过程中，也许会遇到Requires: container-selinux >= 2.9 的异常；
可以打开[Centos下载包](http://mirror.centos.org/centos/7/extras/x86_64/Packages/)中的最新container-selinux包的地址,
然后运行：

```
yum install -y http://mirror.centos.org/centos/7/extras/x86_64/Packages/container-selinux-2.68-1.el7.noarch.rpm
```



- [Ubuntu系统](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

  ```shell
  sudo apt-get update
  sudo apt-get install apt-transport-https ca-certificates 
  curl software-properties-commoncurl -fsSL https://download.docker.com/linux/ubuntu/gpg | 
  sudo apt-key add -sudo apt-key fingerprint 0EBFCD88sudo add-apt-repository \   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \   $(lsb_release -cs) \   stable"
  sudo apt-get update   sudo apt-get install docker-ce
  ```

- [Mac系统](https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac)

https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac

- [Windows](https://docs.docker.com/docker-for-windows/install/#start-docker-for-windows)

https://docs.docker.com/docker-for-windows/install/#start-docker-for-windows

## [Install docker-compose](https://docs.docker.com/compose/overview/)

install [docker-compose](https://docs.docker.com/compose/overview/)

```shell
pip install docker-compose -i https://mirrors.aliyun.com/pypi/simple/
```



如果pip不存在，可以尝试

```shell
sudo yum install python-pip sudo pip install --upgrade pip
```



**Start**



- 一键启动（快速体验）

  ```shell
  docker-compose up -d && docker-compose logs -f  
  # 打开浏览器localhost:8080
  ```

- 初始登录账号如下，开启你的zabbix5.2.3之旅吧

  ```shell
  超管：Admin  密码：zabbix
  ```

- 常用操作

  ```shell
  # 构建服务docker-compose build
  # 启动服务,启动过程中可以直接查看终端日志，观察启动是否成功docker-compose up
  # 启动服务在后台，如果确认部署成功，则可以使用此命令，将应用跑在后台，作用类似 docker-compose up -d
  # 查看日志,效果类似 tail -f waller.logdocker-compose logs -f
  # 停止服务,会停止服务的运行，但是不会删除服务所所依附的网络，以及存储等docker-compose stop
  # 删除服务，并删除服务产生的网络，存储等，并且会关闭服务的守护docker-compose down
  ```

