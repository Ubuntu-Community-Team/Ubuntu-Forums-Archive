---
title: "problem installing Maya 2011 on Linux64 bit Ubuntu 12.04"
date: 2012-09-28
forum: Multimedia Software
---

### Post by teha on 2012-09-28
vooh@vooh-P61A-D3:~$  sudo apt-get install alien tcsh fam libxp libxpm libxprintapputil libxprintutil cpio rpm ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libxp
E: Unable to locate package libxpm
E: Unable to locate package libxprintapputil
E: Unable to locate package libxprintutil

and other command :
 vooh@vooh-P61A-D3:~$  sudo apt-get install alien tcsh fam libxp6 libxpm4 libxprintapputil1 libxprintutil1 cpio rpm ia32-libs
[sudo] password for vooh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libxprintapputil1
E: Unable to locate package libxprintutil1

---

### Post by lukeiamyourfather on 2012-09-28
Maya is not supported on Ubuntu. Those package names are assuming you're using Fedora or RHEL. To find the names of the packages on Ubuntu try 'apt-cache search'.

---

### Post by teha on 2012-09-28
i know that maya did not support Ubuntu but it still can setup it on Ubuntu and many people follow the instructions but have many problems [http://ubuntuforums.org/showthread.php?t=1555394](http://ubuntuforums.org/showthread.php?t=1555394) 
that is how to install it

---

### Post by jerrrys on 2012-09-28
[http://packages.ubuntu.com/precise/libxp-dev](http://packages.ubuntu.com/precise/libxp-dev)
[http://packages.ubuntu.com/precise/libxpm-dev](http://packages.ubuntu.com/precise/libxpm-dev)
[http://packages.ubuntu.com/lucid/libxprintapputil-dev](http://packages.ubuntu.com/lucid/libxprintapputil-dev)
[http://packages.ubuntu.com/lucid/libxprintutil-dev](http://packages.ubuntu.com/lucid/libxprintutil-dev)

Thats what you got to work with, good luck

---

