---
title: "I cannot get stk11xx-1.3.1 to work, previous topics do not help"
date: 2008-06-18
forum: Multimedia Software
---

### Post by Lord Xeb on 2008-06-18
Here is what I get:

```
nathan@nathan-laptop:~/Desktop/stk11xx-1.3.1$ make -f Makefile.standalone driver
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/nathan/Desktop/stk11xx-1.3.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-usb.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-v4l.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-sysfs.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-dev.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-buf.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-bayer.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-dev-a311.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-dev-a821.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-dev-6a31.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-dev-6a33.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-dev-6a51.o
  CC [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx-dev-6a54.o
  LD [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/nathan/Desktop/stk11xx-1.3.1/stk11xx.mod.o
  LD [M]  /home/nathan/Desktop/stk11xx-1.3.1/stk11xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
nathan@nathan-laptop:~/Desktop/stk11xx-1.3.1$ make -f Makefile.standalone clean
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/nathan/Desktop/stk11xx-1.3.1 clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CLEAN   /home/nathan/Desktop/stk11xx-1.3.1/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
nathan@nathan-laptop:~/Desktop/stk11xx-1.3.1$ ./configure && make
bash: ./configure: No such file or directory
nathan@nathan-laptop:~/Desktop/stk11xx-1.3.1$ && make
bash: syntax error near unexpected token `&&'
nathan@nathan-laptop:~/Desktop/stk11xx-1.3.1$ make
make: *** No targets.  Stop.
nathan@nathan-laptop:~/Desktop/stk11xx-1.3.1$ sudo modprobe videodev
nathan@nathan-laptop:~/Desktop/stk11xx-1.3.1$ sudo modprobe v4l1-compat
nathan@nathan-laptop:~/Desktop/stk11xx-1.3.1$ sudo modprobe v4l1-compat
nathan@nathan-laptop:~/Desktop/stk11xx-1.3.1$ sudo insmod stk11xx.ko
insmod: can't read 'stk11xx.ko': No such file or directory

```


What should I do? I am trying to get an USB EasyCap Video & Audio capture card to work and this isn't working. Would Myth make it work?

---

