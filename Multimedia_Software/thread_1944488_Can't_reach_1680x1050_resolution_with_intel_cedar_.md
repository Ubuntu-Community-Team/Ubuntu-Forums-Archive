---
title: "Can't reach 1680x1050 resolution with intel cedar graphic card"
date: 2012-03-21
forum: Multimedia Software
---

### Post by BreakYourTV on 2012-03-21
Hello,
I've recently buy a small fan less pc: 
[tango fanless silent]("http://aleutia.com/products/fanless-pc/tango-fanless-silent-pc?SID=0ic97bmbnb7gah80bcm7c0gc60")
with graphic card: Intel® Cedar Trail

Ubuntu 11.10 is installed.
In settings, I can set the resolution to one of the following: 680x480, 1024x768 or 1280x1024
But I can't reach the native resolution of my screen: 1680x1050.

There is no more xorg.conf in last version of ubuntu...
What should I do?

---

### Post by Yellow Pasque on 2012-03-21
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by BreakYourTV on 2012-03-21
This driver seems to be designed for Poulsbo GMA500,
but I have a GMA5600 Cedarview:
```
~$ lspci -nn | egrep "VGA|Display"
00:02.0 VGA compatible controller [0300]: Intel Corporation Cedarview Integrated Graphics Controller [8086:0be2] (rev 09)
~$ grep Chipset /var/log/Xorg.0.log
[  1011.526] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
[  1011.532] (II) VESA(0): VESA VBE OEM: Intel(R)XX Graphics Chipset Accelerated VGA BIOS
[  1011.771] (II) VESA(0): VESA VBE OEM: Intel(R)XX Graphics Chipset Accelerated VGA BIOS
~$ dmesg | grep agp
[    1.157803] Linux agpgart interface v0.103
```
Do you think it will works?

---

### Post by Yellow Pasque on 2012-03-21
Both GMA500/600 use the Powervr sgx535 graphics core, but I can't say for sure whether emgd will work.

---

### Post by BreakYourTV on 2012-03-21
I don't think it will work because cedarview proc are gma5600 not gma500/600 poulso...

Someone have advice me to try the kernel 3.3 that should manage this proc...

---

### Post by BreakYourTV on 2012-03-22
About the new kernel 3.3:
[http://lists.freedesktop.org/archives/dri-devel/2012-January/018076.html]("http://lists.freedesktop.org/archives/dri-devel/2012-January/018076.html")
gma500: Add support for Cedarview

---

