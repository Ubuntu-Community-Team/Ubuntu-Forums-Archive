---
title: "ali m650 driver compiling Error 2"
date: 2010-09-11
forum: Multimedia Software
---

### Post by 666porcondissaum on 2010-09-11
I know Ive been a lil redundant, there are a lot that has been said about this cam, some made them work, others not. My point is, I haven't. Once it worked, about 2 years ago, but suddenly after the Jaunty updates it has stopped. Here is my output from make:

> ~/m560x-driver/m560x/branches/m5602$ make
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/home/ugperi/m560x-driver/m560x/branches/m5602 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /home/ugperi/m560x-driver/m560x/branches/m5602/m5602_core.o
/home/ugperi/m560x-driver/m560x/branches/m5602/m5602_core.c: In function ‘m5602_read_bridge’:
/home/ugperi/m560x-driver/m560x/branches/m5602/m5602_core.c:55: error: implicit declaration of function ‘info’
/home/ugperi/m560x-driver/m560x/branches/m5602/m5602_core.c: At top level:
/home/ugperi/m560x-driver/m560x/branches/m5602/m5602_core.c:150: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/ugperi/m560x-driver/m560x/branches/m5602/m5602_core.c: In function ‘m5602_usb_probe’:
/home/ugperi/m560x-driver/m560x/branches/m5602/m5602_core.c:300: warning: assignment from incompatible pointer type
make[2]: *** [/home/ugperi/m560x-driver/m560x/branches/m5602/m5602_core.o] Error 1
make[1]: *** [_module_/home/ugperi/m560x-driver/m560x/branches/m5602] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [all] Error 2


Please I need some help, Ive given up about 2 years, but willing to give this note another chance, can someone send me some advice about this error or either send me to the solution, Im totally noob on linux can't do a thing without an especific howto. Thanks in advance.:o

---

### Post by Kreisverkehr on 2010-11-14
Hey guys

I've got the same problem with this cam, but I never got this working.
I am on maverick now.
I googled this error, but no results...
I also noticed that some kernel module is missing. It is called "compat_ioctl32"

I wish someone could help us.

Kreisverkehr

---

