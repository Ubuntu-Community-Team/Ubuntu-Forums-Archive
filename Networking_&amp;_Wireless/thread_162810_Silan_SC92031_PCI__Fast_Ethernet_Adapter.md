---
title: "Silan SC92031 PCI  Fast Ethernet Adapter"
date: 2006-04-19
forum: Networking &amp; Wireless
---

### Post by yoramfr on 2006-04-19
I can't make a lan card work.
Here is the readme.txt 
```


*************************************************
**   Silan SC92031 PCI  Fast Ethernet Adapter  **
**                                             **
**   LINUX driver                              **
*************************************************

Introduction:
=============

    The instructions are for linux driver installation. You must
    compile the source code to generate sc92031.o and use insmod command to
    insert sc92031.o as module.

Contents of the Subdirectory:
=============================

    readme.txt                This file.
    sc92031.c                 The linux core driver source code file
    Makefile                  Makefile for generating driver object file
   
Kernel Supported
================
    This driver support linux kernel version 2.4.x/2.5.x now.

Installation
============
    1) Create a temporary directory:
        # mkdir /temp

    2) Change to the temporary directory:
        #cd /temp

    3) Copy driver (sl_linux.tgz) from CD-ROM to the temporary directory, and follow the commands:
       # mount -t iso9660 /dev/cdrom /mnt
       # cp /mnt/sl_linux.tgz /temp

    4) untar the archive file:
       # tar xzvf sl_linux.tgz
       # cd sc92031
   
    5) Compile the driver source files and it will generate sc92031.o, and
       copy it to correct driver installation path (The installation directory
       is different in different kernel versions. In 2.4.x kernel, the path is
       /lib/modules/KERNEL_VERSION/kernel/drivers/net/, and in 2.2.x kernel,
       the path is /lib/modules/KERNEL_VERSION/net/)
       # make install

    6) Check configuration file (/etc/modules.conf or /etc/conf.modules,it
       depend on your Linux distribution) for loading kernel modules. Make sure
       there is the following content in the configuration file, where # is
       interface number :
        alias eth# sc92031
 
    7) Reboot now:
        shutdown -r now

    8) Install your driver module (If the driver module is in the wrong place,
       an error message will appear, and say that can't find the driver
       module):
        insmod sc92031.o

    8) Use ifconfig command to assign the IP address, where # is network
       interface number:
        ifconfig eth# <IP>

    9) Check the interface works:
        ping <remote_host_IP>

Uninstallation
==============
    Please enter the following commands to uninstall your driver:
      # make uninstall

Module Parameter:
=================
The following parameters can be set when we install the driver module. You can add this parameters when
you execute 'insmod' command to install the driver
      # insmod sc92031.o  work_node =0x00

work_mode
  work_mode is used for setting the speed and duplex mode of NIC.Value is as followed:
        AUTOSELECT 0x00
   M10-HALF   0x01
   M10-FULL   0x02
   M100-HALF  0x04
   M100-FULL  0x08
    
If you want to use other modes,it can be changed by the following steps:
        # ifdown eth0
        # rmmod sc92031
        # insmod sc92031.o work_mode= **** 


```

The ubuntu 5.10 doesn't know what is "make".
And I can't get to the network.

---

### Post by hellmet on 2006-05-08
The driver is for Kernel 2.4 or 2.5X
Ubuntu 5.10 is on 2.6X
If you have got the driver for 2.6X
Compile that and also give it to me.
I'd be grateful.
I too have the same NIC..as I discovered
that my card was a cheap duplicate of the Silan NIC
and it was made to work like RTL8139D.

---

### Post by jacksondafonseca on 2007-03-24
Use the ndiswrapper program it is included on Ubuntu CD. 
Take the disk driver that comes with your board. 
The driver for WinXP works perfectly here. 
Ndiswrapper is too easy to use. 
So you will build a ethernet linux driver based on your Windows ethernet driver.

---

### Post by dhopley on 2007-12-22
Dear Forum , 
Hi , I have had a series of problems with sc92031 . My set up is a dual boot Pentium III under Windows 98SE and Ubuntu 7.10 , which I have just upgraded from Ubuntu 7.04 , and my PC is fitted with an ethernet card , an SC92031 10/100 PCI . Originally I was able to compile the drivers on my supplied CD for both the 98SE and Ubuntu 7.04 systems for use by the network card , but unfortunately there are compile problems under Ubuntu 7.10 , specifically a missing module 'PCI_Module_INIT' . I installed ndiswrapper-1.45 under linux-headers-2.6.22-14-generic and that was working fine with my Windows 98SE driver file netslnt.inf , but after the recent Ubuntu 7.10 upgrade of linux-headers-2.6.22.14 and linux-headers-2.6.22-14-generic from version 46 to 47 my wired connection was lost . 
The working Ubuntu 7.10 data follows :
derek@ubuntu:~$ sudo ndiswrapper -v 
[sudo] password for derek: 
utils version: '1.9', utils version needed by driver: '1.9' 
module details: 
filename: /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko 
version: 1.45 
vermagic: 2.6.22-14-generic SMP mod_unload 586 
derek@ubuntu:~$ 
I have succeeded in getting it working again as follows :
derek@ubuntu:~$ gksudo gedit /etc/modprobe.d/blacklist
and adding the line below :
blacklist sc92031
The reason seems that sc92031.ko has been included in the 18/12/07 upgrade set of drivers , but in my case isn't working . Any comments  anyone ?
Derek

---

