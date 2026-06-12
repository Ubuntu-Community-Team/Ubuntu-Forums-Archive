---
title: "Last thing keeping windows on my computer"
date: 2009-03-20
forum: Multimedia Software
---

### Post by innactpro on 2009-03-20
Getting my LegoCam working is the last thing keeping me from removing windows.

I found this:
[http://qce-ga.sourceforge.net/]("http://qce-ga.sourceforge.net/")

lsusb:
> Bus 001 Device 004: ID 046d:0850 Logitech, Inc. QuickCam Web

Which is the LegoCam, both of which are listed as supported cameras on the qc-usb: Linux Driver for Quickcam USB cameras page.

When I make all, I get:
> make -C "/lib/modules/2.6.24-23-rt/build" SUBDIRS="/home/jason/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-rt'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/jason/qc-usb-0.6.6/.tmp_versions ; rm -f /home/jason/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/jason/qc-usb-0.6.6
  gcc -m32 -Wp,-MD,/home/jason/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/jason/qc-usb-0.6.6/.tmp_qc-driver.o /home/jason/qc-usb-0.6.6/qc-driver.c
In file included from /home/jason/qc-usb-0.6.6/qc-driver.c:47:
/home/jason/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:59,
                 from include/linux/videodev.h:15,
                 from /home/jason/qc-usb-0.6.6/quickcam.h:95,
                 from /home/jason/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/jason/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/jason/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/jason/qc-usb-0.6.6/qc-driver.c:824: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/jason/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/jason/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/jason/qc-usb-0.6.6/qc-driver.c:824: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/jason/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/jason/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/jason/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/jason/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/jason/qc-usb-0.6.6/qc-driver.c: At top level:
/home/jason/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/jason/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/jason/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-rt'
make: *** [quickcam.ko] Error 2

I see all the errors and warnings, though have no real idea how to fix them.

I have visited:
[http://ubuntuforums.org/showthread.php?t=53755]("http://ubuntuforums.org/showthread.php?t=53755")
[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")
[https://help.ubuntu.com/community/EasyCam]("https://help.ubuntu.com/community/EasyCam")
[http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")
[http://linuxtv.org/hg/~pinchartl/uvcvideo/]("http://linuxtv.org/hg/~pinchartl/uvcvideo/")

Trying to get this going, I have also looked at many other threads. This is the closest I have gotten to my specific camera. This camera works fine when in windows, so I know the camera and everything between it and the computer work.

Skype will recognize the quickcam, though it will disappear after clicking test in Skype.

When I try to select it as a capture device in vlc, the LED on the camera will falsh, then nothing. Once it locked up the computer so only a hard boot would work.

In Cheese, all I have ever gotten, and still do, are the color bars and static.

One other time while trying to get this working, the computer locked up, again requiring a hard boot.

Spoon feeding is preferred, but just pointing me in the right direction would be just as appreciated. I noticed at least one other person with a LegoCam specifically mentioned, not getting theirs working either.

I'm running 8.04, as I prefer to stay with the LTS versions.

I've done the kernel headers thing as well as build essentials and all other matter of what I can't even remember anymore. Come to think of it, I don't have the printer or networking quite ironed out yet. So I guess I lied a little about this being the last thing.

Thanks for any help.

---

