---
title: "Logitech Quickcam Messenger Problem on Compiling Driver"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by arxitektonas on 2007-05-10
Hi , 

i have the Logitech Quicam Messenger 

Bus 002 Device 002: ID 046d:08f6 Logitech, Inc. 

And i when i try to install the camera using 

[http://ubuntuforums.org/showthread.php?t=191770&highlight=logitech+messenger]("http://ubuntuforums.org/showthread.php?t=191770&highlight=logitech+messenger")

I installed the headers ,camorama etc ...when i used the installer from that source file 

[http://home.mag.cx/messenger/source/qc-usb-messenger-1.6.tar.gz]("http://home.mag.cx/messenger/source/qc-usb-messenger-1.6.tar.gz")

after some enters .. this fault happened ...

....

=== Entering root mode ===
make -C "/lib/modules/2.6.20-15-generic/build" SUBDIRS="/home/archi/Desktop/qc-usb-messenger-1.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
Makefile:499: /usr/src/linux-headers-2.6.20-15-generic/arch/i386/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.20-15-generic/arch/i386/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [quickcam.ko] Error 2
=== Leaving root mode ===
[!] Module install failed to /lib/modules/2.6.20-15-generic/misc/quickcam.ko
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 


Am i miss something ??? Can someone help ? Thanks :)

---

