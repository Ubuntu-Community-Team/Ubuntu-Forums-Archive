---
title: "How to install my webcam?"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by terrera on 2007-01-05
Hi,

I'm absolutely new to Linux and I am using Ubuntu 6.06 Dapper. It is working wonderfully and its is not being too hard for me since I am being able to find help already posted on Ubuntu forums. However there is only one last thing that I am not being able to install: webcam.

aMSN does not find the camera (actually, I have two webcams) and I already tried installing EasyCam2, but it also does not find my cameras.

On the Terminal, I typed...

lsusb

... as described here and I get the following:

felipe@Torre:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 002: ID 07b2:5100 Motorola BCS, Inc. SurfBoard SB5100 Cable ModemBus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 007: ID 04cb:0125 Fuji Photo Film Co., Ltd
Bus 002 Device 002: ID 06a5:d800 Divio Chicony TwinkleCam
Bus 002 Device 001: ID 0000:0000

So there you have it; my Fuji digital camera (that can be used as webcam, model A310) and by real webcam, (model PD-308).

I have Windows Drivers for both cameras, but I can't find any linux drivers for them. Is there any way I can install the webcams using the Windows drivers or any other way to install any of these cams?

Thank you very much for your help!

---

### Post by GarBhaD on 2007-01-05
Try reading this thread:
[http://ubuntuforums.org/showthread.php?t=303330](http://ubuntuforums.org/showthread.php?t=303330)
I know your webcams are not logitech, but this driver supports a lot of devices. Look for your model in this list.
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by terrera on 2007-01-07
Thanks!

It worked after I tested a third differente webcam because the two others I had (as mentioned on the post) did not work at all!

---

### Post by FIREcracker on 2007-01-11
hi...have you solved with that cam? :O i cant make it run!!!!
how did you get it work??? please answeeeeeeeeeeeeeer!!!
M@

---

### Post by parvinder on 2007-09-09
Hi,

I have Logitech QC for notebook. I downloaded the spca5xx.......tar.gz but how do I install it after extracting.....

I hope I have to 
make
make install


but when I do the make I get some warnings and erorrs as below:
  CC [M]  /home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:39:26: error: linux/config.h: No such file or directory
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca50x_init_isoc’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:1623: warning: assignment from incompatible pointer type
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_open’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: implicit declaration of function ‘video_devdata’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: implicit declaration of function ‘video_get_drvdata’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_close’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2489: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_do_ioctl’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2549: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_ioctl’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3093: warning: implicit declaration of function ‘video_usercopy’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_read’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3112: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_mmap’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3211: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: At top level:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3263: error: variable ‘spca50x_template’ has initializer but incomplete type
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: error: unknown field ‘owner’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: error: unknown field ‘name’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: error: unknown field ‘type’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: error: unknown field ‘hardware’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: error: unknown field ‘fops’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: unknown field ‘release’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: ‘video_device_release’ undeclared here (not in a function)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: error: unknown field ‘minor’ specified in initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: excess elements in struct initializer
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: (near initialization for ‘spca50x_template’)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘cd_to_spca50x’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: implicit declaration of function ‘to_video_device’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: initialization makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3341: warning: return makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca50x_create_sysfs’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3450: warning: implicit declaration of function ‘video_device_create_file’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_probe’:
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: implicit declaration of function ‘video_device_alloc’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: assignment makes pointer from integer without a cast
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5514: error: dereferencing pointer to incomplete type
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5516: warning: implicit declaration of function ‘video_set_drvdata’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: warning: implicit declaration of function ‘video_register_device’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: (Each undeclared identifier is reported only once
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: for each function it appears in.)
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5550: error: dereferencing pointer to incomplete type
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5551: warning: implicit declaration of function ‘video_device_release’
/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5553: warning: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/localuser/Downloads/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o] Error 1
make[1]: *** [_module_/home/localuser/Downloads/spca5xx-v4l1goodbye] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2

please help! 

Output of lsusb is as given below:
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08a9 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

