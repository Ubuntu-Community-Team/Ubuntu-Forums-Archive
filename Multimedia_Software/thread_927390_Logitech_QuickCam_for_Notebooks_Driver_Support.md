---
title: "Logitech QuickCam for Notebooks Driver Support?"
date: 2008-09-22
forum: Multimedia Software
---

### Post by igfud on 2008-09-22
I was wondering if anyone has been able to get a Logitech QuickCam for Notebooks to successfully work in Ubuntu 8.04?  If I just plug it in and type in lsusb in the terminal, I receive the following output:

```
Bus 001 Device 003: ID 046d:08dd Logitech, Inc. 
```

My goal is getting it to work with Skype.  If it is plugged in, Skype seems to be very laggy.  When I go to options to test video, it shows the correct name in the "Select webcam" drop down, but when I click on the "Test" button nothing seems to happen.

If I try starting up Camorama, I can see the image but it is extremely dark with some vertical white flickering lines at the bottom of the image.  If I start Cheese, it doesn't seem to detect a webcam at all.

Is there any chance that I could get this webcam to work in Ubuntu, or should I just return it?  I heard the QuickCam Pro 9000 for Notebooks was supposed to work well, but I really don't want to spend $100 on a webcam.....

Thanks,
igfud

---

### Post by wolfen69 on 2008-09-22
see [this]("http://qce-ga.sourceforge.net/").

---

### Post by igfud on 2008-09-23
Thanks for the reply!

On the readme file, it said to use "make" to compile the driver.  I tried "sudo make install" and received the following output:

```
mike@mike-laptop:~/Desktop/qc-usb-0.6.6$ sudo make install
[sudo] password for mike: 
make -C "/lib/modules/2.6.24-19-generic/build" SUBDIRS="/home/mike/Desktop/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/mike/Desktop/qc-usb-0.6.6/.tmp_versions ; rm -f /home/mike/Desktop/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/mike/Desktop/qc-usb-0.6.6
  gcc -m32 -Wp,-MD,/home/mike/Desktop/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/mike/Desktop/qc-usb-0.6.6/.tmp_qc-driver.o /home/mike/Desktop/qc-usb-0.6.6/qc-driver.c
In file included from /home/mike/Desktop/qc-usb-0.6.6/qc-driver.c:47:
/home/mike/Desktop/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:59,
                 from include/linux/videodev.h:15,
                 from /home/mike/Desktop/qc-usb-0.6.6/quickcam.h:95,
                 from /home/mike/Desktop/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/mike/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/mike/Desktop/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/mike/Desktop/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/mike/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/mike/Desktop/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/mike/Desktop/qc-usb-0.6.6/qc-driver.c: At top level:
/home/mike/Desktop/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/mike/Desktop/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/mike/Desktop/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [quickcam.ko] Error 2
```

I also tried "make all" and received the same output/errors.  Any idea on how I can fix this?

Thanks,
igfud

---

### Post by wolfen69 on 2008-09-23
[Here]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech") is a list of compatible Logitech webcams. you might want to return yours and get one of these.

---

### Post by igfud on 2008-09-24
I finally found a HOWTO on the correct process to install the driver.  The instructions seemed to work okay.  Skype video conference seems to work, but the image is still quite dark and grainy. 

I think I may return the webcam.  I really wish companies would offer more open source drivers. :(  Even if I could get it to work, it doesn't seem like it should take 5+ hours to install a working driver.

[Here is a screenshot]("http://igfudsothers.googlepages.com/Screenshot-1.png") of Camorama running.  The image is pretty clear and bright with the Windows driver.

Thank you for the list of working webcams.  Hmm....yeah it seems like they are 2-3 times the price of this one.

igfud

---

### Post by smartsmokey on 2008-12-18
> **igfud said:**
> I finally found a HOWTO on the correct process to install the driver.  The instructions seemed to work okay.  Skype video conference seems to work, but the image is still quite dark and grainy. 

I think I may return the webcam.  I really wish companies would offer more open source drivers. :(  Even if I could get it to work, it doesn't seem like it should take 5+ hours to install a working driver.

[Here is a screenshot]("http://igfudsothers.googlepages.com/Screenshot-1.png") of Camorama running.  The image is pretty clear and bright with the Windows driver.

Thank you for the list of working webcams.  Hmm....yeah it seems like they are 2-3 times the price of this one.

igfudyeah but see how dark your picture is???? Same problem with me. MODS: not sure how old thread is, sorry if it's.....old.

---

