---
title: "KLM not produced by 'make' / how to create/check symbolic link?"
date: 2008-12-21
forum: Multimedia Software
---

### Post by xarte on 2008-12-21
I'm trying to follow the instructions on this page to install the driver.
[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)

I assumed that the prerequisites were met, and went ahead and ran 'make all
 but no .ko file has been created that I can see or that is recognised when I try to insmod.

got kernel 2.6.24, GCC installed.

how do I check this:
"Kernel source for the kernel you are running. The symbolic link /lib/modules/`uname -r`/build should point to the source directory."

got these error messages during make 

```
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/xarte/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_i2c_init&#8217;:
/home/xarte/qc-usb-0.6.6/qc-driver.c:824: error: &#8216;struct urb&#8217; has no member named &#8216;lock&#8217;
/home/xarte/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/xarte/qc-usb-0.6.6/qc-driver.c: In function &#8216;qc_isoc_start&#8217;:
/home/xarte/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/xarte/qc-usb-0.6.6/qc-driver.c: At top level:
/home/xarte/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field &#8216;hardware&#8217; specified in initializer


```

---

### Post by xarte on 2008-12-21
more errors:

```

make[2]: *** [/home/xarte/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/xarte/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [quickcam.ko] Error 2

```

---

