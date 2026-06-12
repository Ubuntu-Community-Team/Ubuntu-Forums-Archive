---
title: "Yum problem...."
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by veda87 on 2009-08-13
I am on a client machine, I need to download some software packages from my server machine.
So I started with configuring additional repositories in yum

I created a file named **server.repo** in **/etc/yum.repos.d**```
[server1]
name = server1 Server
baseurl = ftp://192.168.0.254/pub/Server/
enabled = 1
gpgcheck = 0
```Then I cleaned up all and tried my installation. But I got some error...```
[root@station75 ~]# yum install dovecot
Loading "rhnplugin" plugin
Loading "security" plugin
Loading "installonlyn" plugin
This system is not registered with RHN.
RHN support will be disabled.
Setting up Install Process
Setting up repositories
server1                   100% |=========================| 1.3 kB    00:00     
Reading repository metadata in from local files
Parsing package install arguments
Resolving Dependencies
--> Populating transaction set with selected packages. Please wait.
---> Downloading header for dovecot to pack into transaction set.
media://1192656534.547140%232/dovecot-1.0-1.2.rc15.el5.i386.rpm: [Errno 4] IOError: <urlopen error unknown url type: media>
Trying other mirror.
Error: failed to retrieve dovecot-1.0-1.2.rc15.el5.i386.rpm from server1
error was [Errno 4] IOError: <urlopen error unknown url type: media>
[root@station75 ~]# 
```
I don't know what is this error, My **server ip address is 192.168.0.254** and in the server the packages are available at **/var/ftp/pub/Server**. 

Can anyone help me on this....

---

