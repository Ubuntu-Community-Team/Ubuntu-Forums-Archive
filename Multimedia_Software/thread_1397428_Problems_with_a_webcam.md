---
title: "Problems with a webcam"
date: 2010-02-03
forum: Multimedia Software
---

### Post by xcoder_123 on 2010-02-03
Hello,

For past to three days I have been trying to find solution in google for my logitech E2500 webcam!

This webcam in VLC xawtv works just fine, but not in skype!

I have tried this guide
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)


And I have an error on launching sudo ./gspca_build

I' m using ubuntu 9.10 karmic!
I have already installed build-essential!

And here is the error:

```


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
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/zapinsh/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/zapinsh/gspcav1-20071224/gspca_core.o
/home/zapinsh/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
In file included from /home/zapinsh/gspcav1-20071224/gspca_core.c:848:
/home/zapinsh/gspcav1-20071224/utils/spcausb.h: In function ‘spca5xxRegRead’:
/home/zapinsh/gspcav1-20071224/utils/spcausb.h:95: error: implicit declaration of function ‘info’
/home/zapinsh/gspcav1-20071224/utils/spcausb.h: In function ‘spca_set_interface’:
/home/zapinsh/gspcav1-20071224/utils/spcausb.h:278: error: implicit declaration of function ‘warn’
In file included from /home/zapinsh/gspcav1-20071224/gspca_core.c:856:
/home/zapinsh/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_init’:
/home/zapinsh/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:122: error: called object ‘info’ is not a function
/home/zapinsh/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:136: error: called object ‘info’ is not a function
/home/zapinsh/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:141: error: called object ‘info’ is not a function
/home/zapinsh/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:148: error: called object ‘info’ is not a function
/home/zapinsh/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:176: error: called object ‘info’ is not a function
/home/zapinsh/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_start’:
/home/zapinsh/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:214: error: called object ‘info’ is not a function
/home/zapinsh/gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h:230: error: called object ‘info’ is not a function
/home/zapinsh/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/zapinsh/gspcav1-20071224/gspca_core.c:2466: error: implicit declaration of function ‘video_usercopy’
/home/zapinsh/gspcav1-20071224/gspca_core.c: At top level:
/home/zapinsh/gspcav1-20071224/gspca_core.c:2612: error: unknown field ‘owner’ specified in initializer
/home/zapinsh/gspcav1-20071224/gspca_core.c:2612: warning: initialization from incompatible pointer type
/home/zapinsh/gspcav1-20071224/gspca_core.c:2614: error: unknown field ‘type’ specified in initializer
/home/zapinsh/gspcav1-20071224/gspca_core.c:2618: warning: initialization from incompatible pointer type
/home/zapinsh/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/zapinsh/gspcav1-20071224/gspca_core.c:2772: error: implicit declaration of function ‘video_device_create_file’
/home/zapinsh/gspcav1-20071224/gspca_core.c:2783: error: implicit declaration of function ‘video_device_remove_file’
/home/zapinsh/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/zapinsh/gspcav1-20071224/gspca_core.c:4314: error: incompatible types when assigning to type ‘struct device’ from type ‘struct device *’
make[2]: *** [/home/zapinsh/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/zapinsh/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [default] Error 2


```Best regards!

---

### Post by ajgreeny on 2010-02-03
Does it work in cheese?  If so, I would expect it to be OK in skype as well.

I assume you have the devices dialog in skype set up properly.  Sorry to ask that, but you never know.

---

### Post by xcoder_123 on 2010-02-06
Yes, in cheese my camera is working. Still not in skype!
By the way skype finds my camera, cameras ID is the same in skype as in lsusb!

---

### Post by strangequarks on 2010-02-10
Hi there,

I just had this problem, got the webcam today and it didn't work at first. Installed cheese and that could see it just fine. Works in skype too now, because I followed the instructions here:

[https://help.ubuntu.com/community/Webcam#Testing%20your%20webcam](https://help.ubuntu.com/community/Webcam#Testing%20your%20webcam)

I went to System > Preferences > Main Menu, then found skype in the lists of menus and clicked Properties, then changed command to exactly what that guide said. 

Opened skype then the usual way, went to Options > Video Devices and clicked Test - and it worked!

Probably worth a try for you too? I'm running a (fairly) clean installation of Karmic.

---

### Post by no2498 on 2010-02-10
you need to look for skype help ive seen a lot of problems with skype
it seems to be with the program
and ubuntu does not use the old drivers now
v4l1 is part of v4l2 now


look at what you ended up with

ome/zapinsh/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/home/zapinsh/gspcav1-20071224/gspca_core.c:2772: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/home/zapinsh/gspcav1-20071224/gspca_core.c:2783: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/home/zapinsh/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/home/zapinsh/gspcav1-20071224/gspca_core.c:4314: error: incompatible types when assigning to type &#8216;struct device&#8217; from type &#8216;struct device *&#8217;
make[2]: *** [/home/zapinsh/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/zapinsh/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [default] Error 2

the cams come on in more programs than before

---

