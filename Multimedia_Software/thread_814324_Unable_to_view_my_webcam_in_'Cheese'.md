---
title: "Unable to view my webcam in 'Cheese'"
date: 2008-05-31
forum: Multimedia Software
---

### Post by pjpeter on 2008-05-31
I've got a labtec cam and will like to get it working in Cheese but I am unable to view it.

I've tried installing the following driver for it but error seem to crop up maybe as it's for a older kernel version.

[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)


Errors:

include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/peter/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/peter/Desktop/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/peter/Desktop/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/peter/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/peter/Desktop/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/peter/Desktop/qc-usb-0.6.6/qc-driver.c: At top level:
/home/peter/Desktop/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initialiser
make[2]: *** [/home/peter/Desktop/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/peter/Desktop/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [quickcam.ko] Error 2


Is someone able to help?

---

### Post by AndThenWhat on 2008-06-13
I get this exact same error.  I have a 046d:0840 Logitech, Inc. QuickCam Express.  When I try to compile the tarball qc-usb-0.6.6 from the website it gives me that error 2 thing.  someone really needs to help on this because i have scoured the internet for hours to no avail. :confused:

---

### Post by AndThenWhat on 2008-06-13
Okay, I downloaded a gspca or something and compiled that from source and viola! My webcam is working, although the video quality looks crappier than on windows.

I attached the source code that I had to compile to fix the problem.

---

