---
title: "Kozumi K-1500PCI wireless N PCI adapter chipset ralink 3062 not working"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by Patricio_Alvarez on 2013-09-03
Hi, I´m new to Linux I´ve just installed Ubuntu 10.04lts and tried to made Kozumi K-1500PCI wireless N PCI adapter chipset ralink 3062 to work.

I made this steps:

2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
   
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
   
4> $make            
   
$make install

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       

modprobe rt2860sta


In networks tools I get this: ( mac adress is present)

[IMG]http://i40.tinypic.com/msoheg.jpg[/IMG]

Wht I´m doing wrong?
Regards

Patricio

---

