# ![Holer Client](http://blog.wdom.net/upload/2019/11/v3sonj7kuogp1orspp1ek7t4jt.png)

Holer客户端软件支持以下两种使用方式，根据实际需求，任选其中一种方式即可，holer软件下载，[**详见文档**](https://github.com/wisdom-projects/holer/releases)。

[**方式一：**](#1-使用公开的holer映射或者开通holer服务) <br/>
使用**公开的holer映射**或者**开通holer服务**，通过**holer客户端软件**经**holer服务器**实现公网访问，[**详见第1节**](#1-使用公开的holer映射或者开通holer服务)。<br/>

[**方式二：**](https://github.com/wisdom-projects/holer-server) <br/>
使用**holer服务端软件**搭建holer服务，通过**holer客户端软件**经**自己服务器**实现公网访问，[**详见文档**](https://github.com/wisdom-projects/holer-server)。<br/>

Holer客户端软件有Java版本，[**详见1.1节**](#11-使用java版本的holer客户端实现步骤)和Go版本，[**详见1.2节**](#12-使用go版本的holer客户端实现步骤)，根据偏好，任选其中一种版本使用即可。

## 1. 使用公开的holer映射或者开通holer服务

**方式一:**使用**公开的holer映射**或者**开通holer服务**，通过holer客户端软件经**holer服务器**实现公网访问。<br/>

**公开的holer映射**详情如下：

访问密钥                      |访问域名    |公网地址   |本地地址|使用场景
-----------------------------|-----------|-----------|-----------|--------
HOLER_CLIENT-2F8D8B78B3C2A0AE|holer65530.wdom.net|holer.org:65530|127.0.0.1:8080|WEB
HOLER_CLIENT-3C07CDFD1BF99BF2|holer65531.wdom.net|holer.org:65531|127.0.0.1:8088|WEB
HOLER_CLIENT-2A623FCB6E2A7D1D|holer65532.wdom.net|holer.org:65532|127.0.0.1:80|WEB
HOLER_CLIENT-AF3E6391525F70E4|N/A|holer.org:65533|127.0.0.1:3389|远程桌面
HOLER_CLIENT-822404317F9D8ADD|N/A|holer.org:65534|127.0.0.1:22|SSH
HOLER_CLIENT-27DD1389DF1D4DBC|N/A|holer.org:65535|127.0.0.1:3306|数据库

这里以映射本地Tomcat默认端口8080为例，选择表中的第一条映射进行配置；如果Web服务端的端口是80或者8088，请选择相匹配的端口映射，其他TCP端口映射步骤类似，更多的使用示例请参考[**官方文档**](http://blog.wdom.net)。

### 1.1 使用Java版本的holer客户端实现步骤

Java版本的holer客户端软件（[源代码](https://github.com/wisdom-projects/holer-client/tree/master/Java)，[软件包](https://github.com/wisdom-projects/holer-client/releases)）是由Java语言实现，支持跨平台。<br/>

#### 1.1.1 安装 Java
安装Java 1.7或者更高版本，执行命令 `java -version` 检查Java是否可用。

#### 1.1.2 安装Web服务端

以Tomcat为例，安装并启动Tomcat，默认安装的端口是8080；<br/>
在浏览器里输入如下URL来检查Tomcat服务是否可以正常访问：<br/>
`http://127.0.0.1:8080`

#### 1.1.3 下载并配置holer客户端 
下载并解压软件包[`holer-client.zip`](https://github.com/wisdom-projects/holer-client/releases)
修改配置文件：<br/>
`holer-client/conf/holer.conf`<br/>

设置`HOLER_ACCESS_KEY`如下：

`HOLER_ACCESS_KEY=HOLER_CLIENT-2F8D8B78B3C2A0AE`

#### 1.1.4 启动holer

进入目录：<br/>
`cd holer-client/bin`<br/>

**Windows系统**:<br/>
执行命令 `startup.bat` 或双击 `startup.bat`<br/>
如果需要停止进程，执行命令`shutdown.bat`或双击`shutdown.bat`<br/>

**Linux系统**:<br/>
执行命令 `bash startup.sh`<br/>
如果需要停止进程，执行命令 `bash shutdown.sh`<br/>

然后就可以通过如下URL来访问Web应用：<br/>
`http://holer65530.wdom.net` 或者 `http://holer.org:65530` 

#### 1.1.5 设置开机启动

进入目录：<br/>
`cd holer-client/bin`<br/>

**Windows系统**:<br/>
双击 `setup.vbs` <br/>
**注意事项：** <br/>
请确保当前用户对如下目录具有读取、写入、执行、修改等权限：<br/>
`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp `<br/>

**Linux系统**:<br/>
执行命令 `bash setup.sh`<br/>
**注意事项：** <br/>
**CentOS 7, RedHat 7, Ubuntu 18** 及更高版本，建议执行命令`bash setup-service.sh`设置开机启动；<br/>

根据提示输入**holer access key**和**holer server host** <br/>
输入示例：
```
------------------------------------------
Enter holer access key: HOLER_CLIENT-2F8D8B78B3C2A0AE
------------------------------------------
Enter holer server host: holer.org
------------------------------------------
```

### 1.2 使用Go版本的holer客户端实现步骤
Go版本的holer客户端软件（[源代码](https://github.com/wisdom-projects/holer-client/tree/master/Go)，[软件包](https://github.com/wisdom-projects/holer-client/releases)）是由GO语言实现，支持多种操作系统和硬件架构。<br/>

#### 1.2.1 安装Web服务端

以Tomcat为例，安装并启动Tomcat，默认安装的端口是8080；<br/>
在浏览器里输入如下URL来检查Tomcat服务是否可以正常访问：<br/>
`http://127.0.0.1:8080`

#### 1.2.2 下载holer客户端

根据实际的系统平台，选择匹配的软件包下载并解压[`holer-xxx.tar.gz`](https://github.com/wisdom-projects/holer-client/releases)

#### 1.2.3 启动holer

这里以`Windows & Linux x86-64bit` 为例，启动holer执行如下命令：<br/><br/>
**Windows系统**:<br/>
`holer-windows-amd64.exe -k HOLER_CLIENT-2F8D8B78B3C2A0AE -s holer.org`<br/>
也可以执行命令 `startup.bat` 或者双击 `startup.bat`<br/>
如果需要停止进程，执行命令`shutdown.bat`或双击`shutdown.bat`<br/>

**Linux系统**:<br/>
`nohup ./holer-linux-amd64 -k HOLER_CLIENT-2F8D8B78B3C2A0AE -s holer.org &`<br/>
也可以执行命令 `bash startup.sh`<br/>
如果需要停止进程，执行命令 `bash shutdown.sh`<br/>

首次启动根据提示输入**holer access key**和**holer server host** <br/>
输入示例：
```
------------------------------------------
Enter holer access key: HOLER_CLIENT-2F8D8B78B3C2A0AE
------------------------------------------
Enter holer server host: holer.org
------------------------------------------
```

#### 1.2.4 设置开机启动
进入目录：<br/>
`cd holer-client/bin`<br/>

**Windows系统**:<br/>
双击 `setup.vbs` <br/>
**注意事项：** <br/>
请确保当前用户对如下目录具有读取、写入、执行、修改等权限：<br/>
`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp `<br/>

**Linux系统**:<br/>
执行命令 `bash setup.sh`<br/>
**注意事项：** <br/>
**CentOS 7, RedHat 7, Ubuntu 18** 及更高版本，建议执行命令`bash setup-service.sh`设置开机启动；<br/>
根据提示输入**holer access key**和**holer server host** <br/>
输入示例：
```
------------------------------------------
Enter holer access key: HOLER_CLIENT-2F8D8B78B3C2A0AE
------------------------------------------
Enter holer server host: holer.org
------------------------------------------
```

# 2. 支持与帮助

## 2.1 Holer使用示例
获得更多的holer使用示例，请参考[**官方文档**](http://blog.wdom.net)。

## 2.2 问题帮助
使用中遇到问题可以查看holer日志信息来排查问题的具体原因。

### 2.2.1 Holer客户端日志
#### 2.2.1.1 Java版本的holer客户端
查看日志文件：
`holer-client/logs/holer-client.log`

#### 2.2.1.2 Go版本的holer客户端
**Linux系统** <br/>
查看可执行程序所在目录下的日志文件`logs/holer-client.log`或者`nohup.out`文件。

**Windows系统** <br/>
查看可执行程序所在目录下的日志文件`logs/holer-client.log`

### 2.2.2 Holer服务端日志
查看日志文件：
`holer-server/logs/holer-server.log`

## 2.3 申请holer服务
用户可以使用上述公开的holer映射详见[第1节](#1-使用公开的holer映射或者开通holer服务)，也可以申请**holer服务**，holer服务[**详见文档**](http://blog.wdom.net/article/23)。
