---
title: "video driver not installing"
date: 2008-11-28
forum: Multimedia Software
---

### Post by shariefbe on 2008-11-28
i selected the zc0301 driver as module when i compile the kernel...and i copied the "zc0301.ko" file from default kernel...but when insert using "insmod" its not working..showing the error..

insmod: error inserting 'zc0301.ko': -1 Invalid module format

how to insert this driver?

---

### Post by shariefbe on 2008-11-28
i am having zc0301 folder...in this

1.Kconfig
2.Makefile
3.zc0301.h
4.zc0301_core.c
5.zc0301_pas202bcb.c
6.zc0301_pb0330.c
7.zc0301_sensor

with this file how to compile this module?..the content of Makefile is..

zc0301-objs := zc0301_core.o zc0301_pb0330.o zc0301_pas202bcb.o

obj-$(CONFIG_USB_ZC0301) += zc0301.o

---

### Post by shariefbe on 2008-11-28
somebody understand my problem and suggest me what to do?

---

