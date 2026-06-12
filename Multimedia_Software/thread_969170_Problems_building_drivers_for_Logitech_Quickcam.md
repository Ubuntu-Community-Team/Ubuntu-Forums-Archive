---
title: "Problems building drivers for Logitech Quickcam"
date: 2008-11-03
forum: Multimedia Software
---

### Post by gluonman on 2008-11-03
I'm trying to install the drivers for my Logitech Quickcam so I can use it with kopete. I've managed to get it to work before and had it working up until my switch from Hardy to Intrepid. I think it's a kernel issue. But when I used module-assistant to build and install gspca and qc-usb it attempted to create a symlink in /usr/src/linux but reported that it could not create the link. Also, when I simply tried to manually extract the gspca and qc-usb directories from the .tar.bz2 files that I downloaded to /usr/src/modules and issued the command "make", this is the output I got:

example for making gspca:
```
gluonman@Orion:/usr/src/modules/gspca$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
mkdir: cannot create directory `/usr/src/modules/gspca/.tmp_versions': Permission denied
  CC [M]  /usr/src/modules/gspca/gspca_core.o
Assembler messages:
Fatal error: can't create /usr/src/modules/gspca/.tmp_gspca_core.o: Permission denied
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
In file included from /usr/src/modules/gspca/gspca_core.c:859:
/usr/src/modules/gspca/Mars-Semi/mr97311.h: In function ‘mr97311_stopN’:
/usr/src/modules/gspca/Mars-Semi/mr97311.h:109: warning: pointer targets in passing argument 3 of ‘pcam_reg_write’ differ in signedness
In file included from /usr/src/modules/gspca/gspca_core.c:861:
/usr/src/modules/gspca/Pixart/pac7311.h: In function ‘pac7311_reg_write’:
/usr/src/modules/gspca/Pixart/pac7311.h:79: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h: In function ‘pac7311_start’:
/usr/src/modules/gspca/Pixart/pac7311.h:218: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:219: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:220: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:221: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:222: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:223: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:224: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:225: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:226: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:227: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:228: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:229: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:230: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:231: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:232: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:233: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:234: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:235: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:236: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:237: warning: pointer targets in passing argument 5 of ‘spca5xxRegWrite’ differ in signedness
/usr/src/modules/gspca/gspca_core.c: In function ‘spca50x_alloc’:
/usr/src/modules/gspca/gspca_core.c:1735: warning: pointer targets in assignment differ in signedness
/usr/src/modules/gspca/gspca_core.c:1740: warning: pointer targets in assignment differ in signedness
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
make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 2
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2
```

Just from the the fact that either of these processes worked perfectly well before when I first purchased the cam back in my gutsy days and also in hardy, I'm guessing that the issue now in intrepid is because of the new kernel. The fact that the symlink couldn't be created in /usr/src/linux and I couldn't make /usr/src/modules/gspca also indicate for me that there is a kernel issue.
But diagnostics aside, can anyone give me a solution? I need gspca and qc-usb built so I can use my webcam.

---

