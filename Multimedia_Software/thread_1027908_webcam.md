---
title: "webcam"
date: 2009-01-01
forum: Multimedia Software
---

### Post by Opiemsith1 on 2009-01-01
I have an old cheap webcam that i'm trying to get to work and i've gotten as far as compiling and installing the ov51x-jpeg driver from source and getting a flickering green screen instead of nothing. I was wondering if anyone knew how to get this cam to work or if i'm out of luck. I don't know the cams name but here's the output from lsusb: Bus 001 Device 002: ID 05a9:a518 OmniVision Technologies, Inc. D-Link DSB-C310 WebCam

Any help is appreciated, thanks.

---

### Post by Opiemsith1 on 2009-01-01
I decided to google the device name (duh lol) and i found [this]("http://ubuntuforums.org/showthread.php?t=690666") guide that looks like it should work. The only problem is that the patched driver won't make. Here's the output:
opiemsith1@opiemsith1-desktop:~/Desktop/ov51x-jpeg-1.5.3~skype_patch$ make
make -C /lib/modules/2.6.27-9-generic/build M=/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.o
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:115:27: error: asm/semaphore.h: No such file or directory
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c: In function ‘proc_ov511_create’:
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:749: error: ‘proc_root’ undeclared (first use in this function)
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:749: error: (Each undeclared identifier is reported only once
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:749: error: for each function it appears in.)
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c: In function ‘proc_ov511_destroy’:
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:767: error: ‘proc_root’ undeclared (first use in this function)
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c: In function ‘ov51x_v4l1_ioctl’:
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:6365: error: implicit declaration of function ‘video_usercopy’
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c: At top level:
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:6615: error: unknown field ‘owner’ specified in initializer
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:6615: warning: initialization from incompatible pointer type
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:6617: error: unknown field ‘type’ specified in initializer
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:6618: error: unknown field ‘hardware’ specified in initializer
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:6618: error: ‘VID_HARDWARE_OV511’ undeclared here (not in a function)
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c: In function ‘ov51x_probe’:
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:8339: error: incompatible types in assignment
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c: At top level:
/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.c:8486: fatal error: opening dependency file /home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/.ov51x-jpeg-core.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch/ov51x-jpeg-core.o] Error 1
make[1]: *** [_module_/home/opiemsith1/Desktop/ov51x-jpeg-1.5.3~skype_patch] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

Again, any help would be great.

---

### Post by Opiemsith1 on 2009-01-02
bump

---

### Post by Opiemsith1 on 2009-01-03
nobody? not even a "no, it's not possible"?

---

