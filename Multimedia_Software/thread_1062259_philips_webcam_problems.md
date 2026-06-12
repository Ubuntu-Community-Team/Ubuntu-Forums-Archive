---
title: "philips webcam problems"
date: 2009-02-06
forum: Multimedia Software
---

### Post by relaxedcrazyman on 2009-02-06
hello, i have read some other posts, and tried a couple of things, but nothing seems to work. FYI i am super noobie, simple instructions please.

i have my philips webcam plugged in, the light is on, but nothing recognizes it. i tried ekiga, vlc and easycam2. they all say that they are not detecting the webcam. HELP!!!

Thanks!

---

### Post by arvevans on 2009-02-06
duplicate posting...?

---

### Post by relaxedcrazyman on 2009-02-06
wasnt sure if i was posting in right place

---

### Post by ohgodnotanother1 on 2009-02-08
Type "lsusb" into a terminal and check whether the output contains something about your webcam. Perhaps post the output below.

---

### Post by relaxedcrazyman on 2009-02-08
Bus 007 Device 002: ID 0d49:3100 Maxtor Hi-Speed USB-IDE Bridge Controller
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:262c Pixart Imaging, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 003: ID 046d:c525 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



i believe it is the pixart

---

### Post by ohgodnotanother1 on 2009-02-09
GSPCA seems to support your webcam from what I can gather from their site:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Try the solution described here: [http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20080723-enabling_a_webcam_under_ubuntu.html](http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20080723-enabling_a_webcam_under_ubuntu.html)

---

### Post by xc3RnbFO8P on 2009-02-09
Bug report:
[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/313594]("https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/313594")

---

### Post by relaxedcrazyman on 2009-02-09
when i tried the gspca build step, i got this in terminal


```
themaster@themaster-desktop:~/downloads/gspcav1-20071224$ sudo ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/themaster/downloads/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/themaster/downloads/gspcav1-20071224/gspca_core.o
/home/themaster/downloads/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/themaster/downloads/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/themaster/downloads/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/themaster/downloads/gspcav1-20071224/gspca_core.c: At top level:
/home/themaster/downloads/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/themaster/downloads/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/themaster/downloads/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/themaster/downloads/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/themaster/downloads/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/themaster/downloads/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/themaster/downloads/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/themaster/downloads/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/themaster/downloads/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/themaster/downloads/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
```



i decided to keep going just in case it worked, when i run spcagui i get this,

```
themaster@themaster-desktop:~$ spcagui
SpcaGui version: 0.3.5 date: 18 September 2005
video device /dev/video0
ERROR opening V4L interface 
: No such file or directory

```



could it be caused by that bug?

---

### Post by relaxedcrazyman on 2009-02-11
so i read a bunch of forums about people having problems compiling gspca, but none of them seemed to work for me. anyone have any insight into getting gspca to work?

---

