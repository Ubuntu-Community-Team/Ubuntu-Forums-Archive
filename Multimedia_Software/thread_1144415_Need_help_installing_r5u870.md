---
title: "Need help installing r5u870"
date: 2009-04-30
forum: Multimedia Software
---

### Post by acidgawd on 2009-04-30
When I try to install r5u870 this is what I get:


acidgawd@ubuntu:~/Desktop/r5u870-0.11.2$ sudo make
make -C /lib/modules/2.6.28-11-generic/build M=/home/acidgawd/Desktop/r5u870-0.11.2 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.o
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_open’:
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:115: error: implicit declaration of function ‘videobuf_queue_pci_init’
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1130: error: implicit declaration of function ‘video_usercopy’
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1134: error: implicit declaration of function ‘video_ioctl2’
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c: At top level:
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1176: error: unknown field ‘type’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1177: error: unknown field ‘type2’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1180: error: unknown field ‘vidioc_querycap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1180: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1180: error: initializer element is not computable at load time
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1180: error: (near initialization for ‘usbcam_videodev_template.num’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1181: error: unknown field ‘vidioc_enum_fmt_cap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1181: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1182: error: unknown field ‘vidioc_g_fmt_cap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1182: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1183: error: unknown field ‘vidioc_s_fmt_cap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1183: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1183: error: initializer element is not computable at load time
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1183: error: (near initialization for ‘usbcam_videodev_template.tvnorms’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1184: error: unknown field ‘vidioc_try_fmt_cap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1184: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1184: error: initializer element is not computable at load time
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1184: error: (near initialization for ‘usbcam_videodev_template.current_norm’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1185: error: unknown field ‘vidioc_reqbufs’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1185: warning: initialization from incompatible pointer type
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1186: error: unknown field ‘vidioc_querybuf’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1186: warning: initialization from incompatible pointer type
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1187: error: unknown field ‘vidioc_qbuf’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1187: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1187: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1188: error: unknown field ‘vidioc_dqbuf’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1188: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1188: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1189: error: unknown field ‘vidiocgmbuf’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1189: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1189: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1190: error: unknown field ‘vidioc_enum_input’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1190: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1190: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1191: error: unknown field ‘vidioc_streamon’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1191: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1191: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1192: error: unknown field ‘vidioc_streamoff’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1192: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1192: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1193: error: unknown field ‘vidioc_g_input’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1193: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1193: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1194: error: unknown field ‘vidioc_s_input’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1194: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1194: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1195: error: unknown field ‘vidioc_queryctrl’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1195: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1195: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1196: error: unknown field ‘vidioc_g_ctrl’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1196: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1196: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1197: error: unknown field ‘vidioc_s_ctrl’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1197: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1197: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1198: error: unknown field ‘vidioc_querymenu’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1198: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1198: warning: (near initialization for ‘usbcam_videodev_template’)
make[3]: *** [/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/acidgawd/Desktop/r5u870-0.11.2/usbcam] Error 2
make[1]: *** [_module_/home/acidgawd/Desktop/r5u870-0.11.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2
acidgawd@ubuntu:~/Desktop/r5u870-0.11.2$ sudo make install
make -C /lib/modules/2.6.28-11-generic/build M=/home/acidgawd/Desktop/r5u870-0.11.2 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.o
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_open’:
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:115: error: implicit declaration of function ‘videobuf_queue_pci_init’
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1130: error: implicit declaration of function ‘video_usercopy’
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1134: error: implicit declaration of function ‘video_ioctl2’
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c: At top level:
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1176: error: unknown field ‘type’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1177: error: unknown field ‘type2’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1180: error: unknown field ‘vidioc_querycap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1180: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1180: error: initializer element is not computable at load time
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1180: error: (near initialization for ‘usbcam_videodev_template.num’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1181: error: unknown field ‘vidioc_enum_fmt_cap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1181: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1182: error: unknown field ‘vidioc_g_fmt_cap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1182: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1183: error: unknown field ‘vidioc_s_fmt_cap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1183: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1183: error: initializer element is not computable at load time
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1183: error: (near initialization for ‘usbcam_videodev_template.tvnorms’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1184: error: unknown field ‘vidioc_try_fmt_cap’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1184: warning: initialization makes integer from pointer without a cast
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1184: error: initializer element is not computable at load time
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1184: error: (near initialization for ‘usbcam_videodev_template.current_norm’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1185: error: unknown field ‘vidioc_reqbufs’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1185: warning: initialization from incompatible pointer type
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1186: error: unknown field ‘vidioc_querybuf’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1186: warning: initialization from incompatible pointer type
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1187: error: unknown field ‘vidioc_qbuf’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1187: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1187: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1188: error: unknown field ‘vidioc_dqbuf’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1188: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1188: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1189: error: unknown field ‘vidiocgmbuf’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1189: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1189: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1190: error: unknown field ‘vidioc_enum_input’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1190: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1190: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1191: error: unknown field ‘vidioc_streamon’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1191: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1191: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1192: error: unknown field ‘vidioc_streamoff’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1192: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1192: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1193: error: unknown field ‘vidioc_g_input’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1193: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1193: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1194: error: unknown field ‘vidioc_s_input’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1194: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1194: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1195: error: unknown field ‘vidioc_queryctrl’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1195: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1195: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1196: error: unknown field ‘vidioc_g_ctrl’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1196: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1196: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1197: error: unknown field ‘vidioc_s_ctrl’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1197: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1197: warning: (near initialization for ‘usbcam_videodev_template’)
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1198: error: unknown field ‘vidioc_querymenu’ specified in initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1198: warning: excess elements in struct initializer
/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.c:1198: warning: (near initialization for ‘usbcam_videodev_template’)
make[3]: *** [/home/acidgawd/Desktop/r5u870-0.11.2/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/acidgawd/Desktop/r5u870-0.11.2/usbcam] Error 2
make[1]: *** [_module_/home/acidgawd/Desktop/r5u870-0.11.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2


Anybody know how to install this thing?

---

### Post by slingshotsuicide on 2009-10-10
I'm struggling with the same thing on my dv9030us with ricoh webcam 1000.  I got similar messages trying to build untill I realized that the version I had downloaded was for the x86 and I needed the x86_64.  If this is the case for you, you can get the right driver from here:
[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)
Also I should mention, that I have had to reinstall it with each kernal update, so don't delete the build folder, as you'll be able to skip ahead to 'make install' when it disappears on kernal upgrades.

And btw, take a minute to contact ricoh and HP to let them know another linuxhead wants proper support.

---

### Post by duxi on 2009-11-30
I've the solution here!

Worked fine for me :)

[http://duxthefux.blogspot.com/2009/11/webcam-ricoh-r5u870-einrichten.html](http://duxthefux.blogspot.com/2009/11/webcam-ricoh-r5u870-einrichten.html)

Best regards

---

### Post by Ironfisher on 2010-10-14
You may need to install this some packages:

sudo apt-get install build-essential libusb-dev libncurses-dev gettext linux-headers-`uname -r` libglib2.0-dev

---

