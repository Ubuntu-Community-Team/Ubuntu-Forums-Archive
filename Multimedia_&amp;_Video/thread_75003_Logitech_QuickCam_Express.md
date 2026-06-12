---
title: "Logitech QuickCam Express"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by UbuntuKhan on 2005-10-13
I have a Logitech QuickCam Express which works fine in 98 and XP, but did not work with the ubuntu Hoary livecd (in fact it detected the camera but it would not work or I was just to stupid to make it work). Would it work with breezy? What should I do to make it work?

---

### Post by mips on 2005-10-13
[QUOTE=UbuntuKhan]I have a Logitech QuickCam Express which works fine in 98 and XP, but did not work with the ubuntu Hoary livecd (in fact it detected the camera but it would not work or I was just to stupid to make it work). Would it work with breezy? What should I do to make it work?[/QUOTE]


Hi,

There is a search function at the top of the page, some results:

[http://ubuntuforums.org/showthread.php?t=75082&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=75082&highlight=Logitech+QuickCam)
[http://ubuntuforums.org/showthread.php?t=73208&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=73208&highlight=Logitech+QuickCam)
[http://ubuntuforums.org/showthread.php?t=73303&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=73303&highlight=Logitech+QuickCam)
[http://ubuntuforums.org/showthread.php?t=53755&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=53755&highlight=Logitech+QuickCam)
[http://ubuntuforums.org/showthread.php?t=24827&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=24827&highlight=Logitech+QuickCam)
[http://ubuntuforums.org/showthread.php?t=65105&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=65105&highlight=Logitech+QuickCam)
[http://ubuntuforums.org/showthread.php?t=63875&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=63875&highlight=Logitech+QuickCam)
[http://ubuntuforums.org/showthread.php?t=63653&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=63653&highlight=Logitech+QuickCam)
[http://ubuntuforums.org/showthread.php?t=62718&highlight=Logitech+QuickCam](http://ubuntuforums.org/showthread.php?t=62718&highlight=Logitech+QuickCam)

---

### Post by Plasma_NZ on 2008-04-06
Ok slight problem, lots of postings regarding these cams.. yet everyone seems to have difference issues...

Here's my problem..

lsusb 

Bus 001 Device 007: ID 046d:0840 Logitech, Inc. QuickCam Express

Accordingly it's ment to be supported by the qc-driver from source-forge... so i download it.. and follow the make all etc.. and i get the following errors...

Im using Hardy Heron 64bit 

```
make -C "/lib/modules/2.6.24-15-generic/build" SUBDIRS="/home/physics/Downloads/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-15-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)

```

and further down during compile..

```
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/physics/Downloads/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/physics/Downloads/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/physics/Downloads/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/physics/Downloads/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/physics/Downloads/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/physics/Downloads/qc-usb-0.6.6/qc-driver.c: At top level:
/home/physics/Downloads/qc-usb-0.6.6/qc-driver.c:2998: warning: initialization from incompatible pointer type
/home/physics/Downloads/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/physics/Downloads/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/physics/Downloads/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-15-generic'
make: *** [quickcam.ko] Error 2

```

Any idea's ?

---

### Post by Plasma_NZ on 2008-04-07
Bump... Amazing how generic stuff never works...

---

### Post by maxownz on 2008-04-28
Just installed Hardy Heron (8.04) tonight and am getting those exact errors when making the gc-usb-0.6.6 driver...

---

### Post by Lothas on 2008-05-05
I have the Lego Mindstorms Vision Command camera:
Bus 001 Device 004: ID 046d:0850 Logitech, Inc. QuickCam Web

and it doesn't work properly, not even in Hardy. Since 7.10 the built-in mic works ok (little down on gain) but the camera is still not working. This is one of the only things keeping me from moving completely to Ubuntu.

I'm also still getting errors trying to compile the qc-usb driver :(

---

