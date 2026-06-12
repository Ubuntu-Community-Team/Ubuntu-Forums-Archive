---
title: "Webcam Philips PSC220NC"
date: 2009-11-04
forum: Multimedia Software
---

### Post by ventolt on 2009-11-04
I can't manage to get my webcamp **Philips PSC220NC** working. I actually can not compile the driver. I have tried several patches, but it didn't work. Well, in the list of webcams supported on linux, my webcam is absent, but on the list of Skype webcam lists, it says that I need the latest gspca version ( src: [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) ). All I see now on skype test is a green and violet screen. So here is the error: 
```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/pijus/Desktop/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/pijus/Desktop/gspcav1-20071224/gspca_core.o
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
In file included from /home/pijus/Desktop/gspcav1-20071224/gspca_core.c:845:
/home/pijus/Desktop/gspcav1-20071224/utils/spcausb.h: In function ‘spca5xxRegRead’:
/home/pijus/Desktop/gspcav1-20071224/utils/spcausb.h:95: error: implicit declaration of function ‘info’
/home/pijus/Desktop/gspcav1-20071224/utils/spcausb.h: In function ‘spca_set_interface’:
/home/pijus/Desktop/gspcav1-20071224/utils/spcausb.h:278: error: implicit declaration of function ‘warn’
In file included from /home/pijus/Desktop/gspcav1-20071224/gspca_core.c:853:
/home/pijus/Desktop/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_init’:
/home/pijus/Desktop/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:122: error: called object ‘info’ is not a function
/home/pijus/Desktop/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:136: error: called object ‘info’ is not a function
/home/pijus/Desktop/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:141: error: called object ‘info’ is not a function
/home/pijus/Desktop/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:148: error: called object ‘info’ is not a function
/home/pijus/Desktop/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:176: error: called object ‘info’ is not a function
/home/pijus/Desktop/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_start’:
/home/pijus/Desktop/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:214: error: called object ‘info’ is not a function
/home/pijus/Desktop/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:230: error: called object ‘info’ is not a function
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c: At top level:
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c:2615: warning: initialization from incompatible pointer type
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/pijus/Desktop/gspcav1-20071224/gspca_core.c:4301: error: incompatible types when assigning to type ‘struct device’ from type ‘struct device *’
make[2]: *** [/home/pijus/Desktop/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/pijus/Desktop/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [default] Error 2
```
It's a typical error, other people have had the same problem, but I can't use the same ways... It simply doesn't work. Anyone could manage to get working it with Ubuntu 9.10?

---

