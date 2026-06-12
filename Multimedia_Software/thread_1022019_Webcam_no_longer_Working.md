---
title: "Webcam no longer Working"
date: 2008-12-26
forum: Multimedia Software
---

### Post by AngelAir on 2008-12-26
Hello everyone,

My webcam is no longer working on 8.10.  I had installed Ubuntu 8.04 on my system and installed the first or oldest version of EasyCam in order to detect and use my webcam.  It worked.  Now I have upgraded my system to Ubuntu 8.10.  Try to install the same EasyCam, but; could only fing EasyCam 2.  After installing it; the webcam is recognized as a 'Microdia USB2.0 Webcam12', it goes to the process of installation but when finish the webcam is not installed.  Any suggestions? :(

---

### Post by goodbadwolf on 2009-01-01
I am also facing the exact same problem. 

dmesg says:

[ 1541.828044] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 1541.996465] usb 1-2: configuration #1 chosen from 1 choice

lsusb says:

Bus 001 Device 003: ID 0c45:6270 Microdia U-CAM PC Camera NE878

easycam says:

goodbadwolf@goodbadwolf-desktop:/usr/include/linux$ gksudo 'python /usr/share/EasyCam2/core.py --gtk'
GO !
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-7-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E:  creating symbolic link `/lib/modules/2.6.27-7-generic/build/include/linux/config.h': File exists
Couldn't find package linux-source-2.6.24
rm: cannot remove `/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/usbvideo/microdia.ko': No such file or directory
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS= clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/usr/share/EasyCam2/drivers/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /usr/share/EasyCam2/drivers/microdia/microdia-usb.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /usr/share/EasyCam2/drivers/microdia/microdia-usb.c:27:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /usr/share/EasyCam2/drivers/microdia/microdia-usb.c:27:
include/linux/mmzone.h:218: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[2]: *** [/usr/share/EasyCam2/drivers/microdia/microdia-usb.o] Error 1
make[1]: *** [_module_/usr/share/EasyCam2/drivers/microdia] Error 2
make: *** [driver] Error 2
cp: cannot stat `microdia.ko': No such file or directory
FATAL: Module microdia not found.
FATAL: Module microdia not found.


please help me.

---

