### 以centos8为基础镜像运行projector-idea-u
原因： 因为centos7的util-linux的版本太低了，导致setsid 工具没有--wait这个参数，而新版的Idea都是默认使用setsid --wait去启动，并且setsid这个工具很难更新，因此直接使用centos8

### 安装oracle-jdk 不要使用open-jdk  
原因： 因为open-jdk的yum 安装路径十分诡异， bazel不能自动识别JAVA_HOM,会导致bazel插件运行失败
安装步骤
```
cd /home/projector-user
ft get xxxx.rpm ./
yum localinstall xxx.rpm   #安装路径在/usr/java里面
vim /etc/profile

#/etc/prfile
JAVA_HOME=/usr/java/jdk1.8.0_311-i586
JRE_HOME=/usr/java/jdk1.8.0_311-i586/jre
PATH=$PATH:$JAVA_HOME/bin
CLASSPATH=.:$JAVA_HOME/lib
HOME=/usr
export JAVA_HOME CLASSPATH HOME

```

### 安装Bazle4.2.0
```
去github直接找 后面再配
```