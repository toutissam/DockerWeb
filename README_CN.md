![docker+nginx](https://github.com/antscript/DockerWeb/raw/master/img/dockerweb.png)
# What is DockerWeb ?
#### DockerWeb是一个静态网站搭建及部署工具.

#### 使用DockerWeb可以非常方便的在服务器/VPS/云主机上部署静态网站.

#### 并且可以通过Github或Bitbucket对网站进行自动更新.

***

# 功能特点
* **使用Docker container运行,易于维护，备份和迁移都极其方便**
* **使用非常简单** <a href="http://v.youku.com/v_show/id_XMTQ4NDUxNjcxNg==" target="_blank">通过DockerWeb五分钟搭建一个静态网站</a>
* **可通过Github或Bitbucket的webhook自动部署更新**

***

# 用法


* **Step 0**: 安装Docker和Git
Docker : [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)

Git : [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)


* ### **Step 1**: Fork DockerWeb 并克隆到本地
如果是Bitbucket , 可直接从Github导入

* ### **Step 2**: 配置SSH (Github不需要)
复制本机或新生成一对id_rsa和id_rsa.pub到服务器的/root/.ssh/目录下

* ### **Step 3**: 配置HTTPS (如果需要https访问请配置)
复制ssl.crt和ssl.key到服务器

* ### **Step 4**: 编辑setup/config.sh为适合你的配置

* ### **Step 5**: 将仓库push到Github或Bitbucket

* ### **Step 6**: 添加webhook用于自动部署更新
```
#Github  
Setting -> Webhooks & services -> add webhook
Payload URL : http(s)://yourdomain.com:9000/hooks/your_webhook_id
```
```
#Bitbucket  
Setting -> Webhooks  -> Add webhook
Title : title you want
URL   : http(s)://yourdomain.com:9000/hooks/your_webhook_id
```

* ### **Step 7**: 登陆服务器，克隆你提交的仓库并运行setup/setup.sh

* ### **Step 8**: 如果有多个网站，运行 multi-web/init.sh

* ### **Step 9**: 访问你的网站

* ### **Step 10**: 使用Github或者Bitbucket进行部署更新

* ### **Step 11**: 加入开机启动
```
#单个网站
cp path_to_dockerWeb/setup/dockerWebStartup /etc/init.d/
echo "/bin/sh /etc/init.d/dockerWebStartup" >> /etc/rc.d/rc.local
chmod +x /etc/rc.d/rc.local

#多个网站
cp path_to_dockerWeb/multi-web/dockerWebStartup /etc/init.d/
echo "/bin/sh /etc/init.d/dockerWebStartup" >> /etc/rc.d/rc.local
chmod +x /etc/rc.d/rc.local
```

***

# DockerWeb：部署多个网站
管理和维护多个网站一种方法是直接创建多个仓库，将所有文件拷贝到仓库中，分别用单个网站的方式进行部署。
另一种更优雅的管理多个网站的方式是使用仓库的分支：
* 为不同网站创建分支，在对应分支上进行网站管理及维护
* 为不同网站创建有不同id的webhook
* 通过切换不同分支对不同网站进行部署

***
# 视频演示
* **通过DockerWeb五分钟搭建一个静态网站 :** 
<a href="http://v.youku.com/v_show/id_XMTQ4NDUxNjcxNg==" target="_blank">http://v.youku.com/v_show/id_XMTQ4NDUxNjcxNg==</a>
<a href="https://www.youtube.com/watch?v=VQmeIzExRco" target="_blank">https://www.youtube.com/watch?v=VQmeIzExRco</a>

***
# 3rd party tools
#### [https://github.com/adnanh/webhook](https://github.com/adnanh/webhook)
