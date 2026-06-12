---
title: "Logitech Quickcam Express (046d:0850) on Ubuntu 10.04 Lucid Lynx"
date: 2010-06-26
forum: Multimedia Software
---

### Post by Incarnation on 2010-06-26
Hi everyone. I'm attempting to make my Logitech Quickcam Express work with Ubuntu 10.04.

I'm not sure what may be the problem but it doesn't seem to work with any of the applications so far.

I visited [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/) and attempted to extract and compile the drivers but ran into problems.

```
incarnation@incarnation-desktop:~/Desktop/qc-usb-0.6.6$ make all
make -C "/lib/modules/2.6.32-22-generic/build" SUBDIRS="/home/incarnation/Desktop/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/incarnation/Desktop/qc-usb-0.6.6/.tmp_versions ; rm -f /home/incarnation/Desktop/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/incarnation/Desktop/qc-usb-0.6.6
  gcc -Wp,-MD,/home/incarnation/Desktop/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)"  -c -o /home/incarnation/Desktop/qc-usb-0.6.6/.tmp_qc-driver.o /home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c
In file included from /home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:47:
/home/incarnation/Desktop/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:60,
                 from include/linux/videodev.h:17,
                 from /home/incarnation/Desktop/qc-usb-0.6.6/quickcam.h:95,
                 from /home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_proc_create’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:997: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_proc_init’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:1035: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_poll’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:2256: error: ‘struct video_device’ has no member named ‘priv’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_open’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:2308: error: ‘struct video_device’ has no member named ‘priv’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_close’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:2376: error: ‘struct video_device’ has no member named ‘priv’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_read’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:2424: error: ‘struct video_device’ has no member named ‘priv’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_mmap’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:2479: error: ‘struct video_device’ has no member named ‘priv’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_ioctl’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:2511: error: ‘struct video_device’ has no member named ‘priv’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:2529: error: ‘struct video_device’ has no member named ‘type’
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: At top level:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:3008: error: unknown field ‘type’ specified in initializer
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:3013: warning: initialization from incompatible pointer type
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_usb_init’:
/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.c:3158: error: ‘struct video_device’ has no member named ‘priv’
make[2]: *** [/home/incarnation/Desktop/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/incarnation/Desktop/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [quickcam.ko] Error 2
incarnation@incarnation-desktop:~/Desktop/qc-usb-0.6.6$ 
```Can anyone help me out?

---

### Post by no2498 on 2010-06-27
in/on 910 and up cheese webcam booth should be loaded
look for it in sound & video
try the cam in cheese first

if it does not come on

try this

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

your cam should just work

if cheese is not installed it is in the repose or is the add/remove program

---

### Post by kenworth on 2010-07-02
Thanks no2468, but saying it should work doesn't help, I have the same problem and so far all I read is that cheese should work. Well it doesn't and compiling the source fails with an error.

Is there someone who can actually provide help here ?

---

### Post by Megra on 2010-07-03
A solution is to follow the tutorial on [at-last-the-old-webcam-logitech-quickcam-web-works-on-my-debian-box]("http://gnugalaxy.wordpress.com/2008/02/11/at-last-the-old-webcam-logitech-quickcam-web-works-on-my-debian-box/") ([http://gnugalaxy.wordpress.com/2008/02/11/at-last-the-old-webcam-logitech-quickcam-web-works-on-my-debian-box/](http://gnugalaxy.wordpress.com/2008/02/11/at-last-the-old-webcam-logitech-quickcam-web-works-on-my-debian-box/)) and patch the source code by removing the 2 lines:

    entry->owner = THIS_MODULE;
    qc_proc_entry->owner = THIS_MODULE;

You may have to blacklist the qcmessenger module.

---

### Post by Arjuna Rao Chavala on 2010-07-06
> **kenworth said:**
> Thanks no2468, but saying it should work doesn't help, I have the same problem and so far all I read is that cheese should work. Well it doesn't and compiling the source fails with an error.

Is there someone who can actually provide help here ?

I have logitech quickcam/easy cool ID 046d:08af. It used to work in 08.10 and did not work after upgrading to 10.04.

I researched and reverted back 2.0.0.68 version of skype ([http://www.mediafire.com/file/jatmujn4ynz/skype-debian_2.0.0.68-1_i386.deb](http://www.mediafire.com/file/jatmujn4ynz/skype-debian_2.0.0.68-1_i386.deb) )
 and used the same commands to configure namely
$ sudo mv /dev/video0 /dev/video1
$ gstfakevideo v4l2src device=/dev/video1
to launch skype.
I could test video in skype options properly.
You need to install libgstreamer0.10-dev and download, build and install  gstfakevideo from  [http://code.google.com/p/gstfakevideo/source/checkout](http://code.google.com/p/gstfakevideo/source/checkout) (for that you may need to install subversion package.)
You can also check basic video by using gstreamer-properties and testing video input with v4l2 setting.

Hope this helps.
Arjun

---

### Post by Arjuna Rao Chavala on 2010-07-23
After some tweaking  of  my ubuntu, the previous suggestion of gstfakevideo stopped working. 
I found [http://www.blog.arun-prabha.com/2010/01/21/logitech-quickcam-chat-with-skype-2-1-in-ubuntu-linux/](http://www.blog.arun-prabha.com/2010/01/21/logitech-quickcam-chat-with-skype-2-1-in-ubuntu-linux/)
as per that give the following command.
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
Make sure you have libv4l-0 installed. If not, install it before you  try the above command.  
This worked.

---

