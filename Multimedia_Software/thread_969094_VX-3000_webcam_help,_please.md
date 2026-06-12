---
title: "VX-3000 webcam help, please"
date: 2008-11-03
forum: Multimedia Software
---

### Post by Penguins007 on 2008-11-03
I hope someone can come back and help me with this. I was unable to make my vx-3000 works on my 8.10 Ubuntu. I tried with 8.04, maybe similiar with 8.10?

I have followed the instruction from [http://ubuntuforums.org/showthread.p...vx-3000+webcam](http://ubuntuforums.org/showthread.p...vx-3000+webcam), and downloaded from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html). Then click gspcav1-20071224.

But seems my outcome is not what I expected?

root@localhost:/home/zeplinthree/Desktop# cd gspcav1-20071224
root@localhost:/home/zeplinthree/Desktop/gspcav1-20071224# dir
changelog Etoms license Pixart Sunplus-jpeg
Conexant gspca_build Makefile READ_AND_INSTALL Transvision
cutlog.py gspca_core.c Makefile.kld Sonix utils
decoder gspca.h Mars-Semi Sunplus Vimicro
root@localhost:/home/zeplinthree/Desktop/gspcav1-20071224# cd .drivers
bash: cd: .drivers: No such file or directory
root@localhost:/home/zeplinthree/Desktop/gspcav1-20071224# sudo ./gspca_build

REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
.gspca.o.cmd *.o *.ko *.mod.* .[a-z]* core *.i \
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
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/zeplinthree/Desktop/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
CC [M] /home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.o
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c: At top level:
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/zeplinthree/Desktop/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2
root@localhost:/home/zeplinthree/Desktop/gspcav1-20071224#

---

