---
title: "terminal trouble with Java"
date: 2010-03-20
forum: Multimedia Software
---

### Post by savyboy24 on 2010-03-20
I am trying to install Java following these directions [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU). Everything was going good until recent. Can someone please tell what is going on with the terminal

maverick@Maverick-laptop:~$ cd /opt
maverick@Maverick-laptop:/opt$ sudo mkdir java
maverick@Maverick-laptop:/opt$ cd java
maverick@Maverick-laptop:/opt/java$ sudo mkdir 64
maverick@Maverick-laptop:/opt/java$ sudo mv ~/jre-6u18-linux-x64.bin /opt/java/64
maverick@Maverick-laptop:/opt/java$ cd /opt/java/64
maverick@Maverick-laptop:/opt/java/64$ sudo ./jre-6u18-linux-x64.bin
sudo: ./jre-6u18-linux-x64.bin: command not found
maverick@Maverick-laptop:/opt/java/64$ sudo ./jre-6u18-linux-x64.bin
sudo: ./jre-6u18-linux-x64.bin: command not found
maverick@Maverick-laptop:/opt/java/64$ cd /opt/java/64
maverick@Maverick-laptop:/opt/java/64$ sudo ./jre-6u18-linux-x64.bin
sudo: ./jre-6u18-linux-x64.bin: command not found

Dont know why is is saying command not found or what to do next.

---

### Post by DaithiF on 2010-03-20
Hi,
the file needs to be made executable.  
```
chmod +x jre-6u18-linux-x64.bin

```then run it as before

---

### Post by savyboy24 on 2010-03-21
Thanks it worked!!!!

---

