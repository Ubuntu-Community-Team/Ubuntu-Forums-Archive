---
title: "Driver for Philips webcam?"
date: 2009-06-28
forum: Multimedia Software
---

### Post by GabrielWolff on 2009-06-28
I'm looking for a way to get the SPC220NC webcam working on Jaunty.
For now it doesn't even recognize there is anything stuck into the USB port.

I remember checking out if it should work before buying the cam, but that was quite a while ago.

Any clue anyone?

G

---

### Post by GabrielWolff on 2009-06-28
I managed to find the driver, but get an error message when trying to build 
```
gabriel@gabriel-laptop:~/gspcav1-20071224$ sudo ./gspca_build 

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
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/gabriel/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/gabriel/gspcav1-20071224/gspca_core.o
/home/gabriel/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/gabriel/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/gabriel/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/gabriel/gspcav1-20071224/gspca_core.c: At top level:
/home/gabriel/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/gabriel/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/gabriel/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/gabriel/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/gabriel/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/gabriel/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/gabriel/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/gabriel/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/gabriel/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/gabriel/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

```

---

### Post by matrixblue on 2009-07-04
[http://ubuntuforums.org/showthread.php?t=1138254&highlight=gspca+jaunty](http://ubuntuforums.org/showthread.php?t=1138254&highlight=gspca+jaunty)

and follow the instructions in post #2 that will get it to compile.

Even after the compile I still can't get it to work though....but I guess it's a step in the right direction.

---

