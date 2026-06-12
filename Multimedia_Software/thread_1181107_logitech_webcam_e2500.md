---
title: "logitech webcam e2500"
date: 2009-06-07
forum: Multimedia Software
---

### Post by aadvark164 on 2009-06-07
Ive been trying to get my webcam working and having no success. I need help!! Im new to linux so please dont confuse me Im confused enough already!. I have been trying to compile the qc-usb.0.6.6 driver as per the instructions on the quickcam express page and this is the output I get.

richard@richard-laptop:/usr/src/qc-usb-0.6.6$ sudo make all
make -C "/lib/modules/2.6.28-11-generic/build" SUBDIRS="/usr/src/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /usr/src/qc-usb-0.6.6/.tmp_versions ; rm -f /usr/src/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/qc-usb-0.6.6
  gcc -Wp,-MD,/usr/src/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)"  -c -o /usr/src/qc-usb-0.6.6/.tmp_qc-driver.o /usr/src/qc-usb-0.6.6/qc-driver.c
In file included from /usr/src/qc-usb-0.6.6/qc-driver.c:47:
/usr/src/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:60,
                 from include/linux/videodev.h:16,
                 from /usr/src/qc-usb-0.6.6/quickcam.h:95,
                 from /usr/src/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/usr/src/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/usr/src/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/usr/src/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/usr/src/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/usr/src/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/usr/src/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_poll’:
/usr/src/qc-usb-0.6.6/qc-driver.c:2256: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_open’:
/usr/src/qc-usb-0.6.6/qc-driver.c:2308: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_close’:
/usr/src/qc-usb-0.6.6/qc-driver.c:2376: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_read’:
/usr/src/qc-usb-0.6.6/qc-driver.c:2424: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_mmap’:
/usr/src/qc-usb-0.6.6/qc-driver.c:2479: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_ioctl’:
/usr/src/qc-usb-0.6.6/qc-driver.c:2511: error: ‘struct video_device’ has no member named ‘priv’
/usr/src/qc-usb-0.6.6/qc-driver.c:2529: error: ‘struct video_device’ has no member named ‘type’
/usr/src/qc-usb-0.6.6/qc-driver.c: At top level:
/usr/src/qc-usb-0.6.6/qc-driver.c:3008: error: unknown field ‘type’ specified in initialiser
/usr/src/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initialiser
/usr/src/qc-usb-0.6.6/qc-driver.c: In function ‘qc_usb_init’:
/usr/src/qc-usb-0.6.6/qc-driver.c:3158: error: ‘struct video_device’ has no member named ‘priv’
make[2]: *** [/usr/src/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/usr/src/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [quickcam.ko] Error 2
richard@richard-laptop:/usr/src/qc-usb-0.6.6$

---

### Post by MarkoCro on 2009-06-08
My E3500 works out of the box in Jaunty. You need no drivers (Webcam UVC driver already in Jaunty).

---

