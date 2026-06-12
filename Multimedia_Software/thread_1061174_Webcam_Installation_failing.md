---
title: "Webcam Installation failing"
date: 2009-02-05
forum: Multimedia Software
---

### Post by crokett on 2009-02-05
I am trying to install a webcam in Ubuntu Intrepid.  lsusb shows this:

```

Bus 003 Device 002: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam


```

So after some searches I downloaded the source for the gspca module and tried to use module-assistant to make and install.  That failed so I extracted the files manually then ran 

'sudo make'

It fails with these errors.  My kernel is 2.6.27-11.  The gspca package didn't have any dependencies in package manager.  Are there different libraries I need? 

```

make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Error 2


```

---

### Post by ohgodnotanother1 on 2009-02-05
Try this: [http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20080723-enabling_a_webcam_under_ubuntu.html](http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20080723-enabling_a_webcam_under_ubuntu.html)

If it doesn't work try this: [http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20081231-logitech-quickcam-messenger-communicate-ubuntu-linux-config.html](http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20081231-logitech-quickcam-messenger-communicate-ubuntu-linux-config.html)

---

### Post by crokett on 2009-02-06
That did not work. spcagui control window starts, the camera window opens then closes.  

I did some research overnight and the gspca drivers are already included as a module so I should not have to build them.  The build is failing anyway. I *think* I got the module installed correctly.  output of lsmod | grep gspca:

I would expect that 0 next to gspca_zc3xx to be used b the camera, no? So shoun't it be a 1?

```

gspca_zc3xx            55936  0 
gspca_main             29312  1 gspca_zc3xx
videodev               41344  1 gspca_main
usbcore               149360  8 snd_usb_audio,snd_usb_lib,gspca_zc3xx,gspca_main,usbhid,uhci_hcd,ehci_hcd

```

output of lsusb:

```

gspca_zc3xx            55936  0 
gspca_main             29312  1 gspca_zc3xx
videodev               41344  1 gspca_main
usbcore               149360  8 snd_usb_audio,snd_usb_lib,gspca_zc3xx,gspca_main,usbhid,uhci_hcd,ehci_hcd

```

So as far as I can tell Linux is seeing the camera it just can't use it.

---

