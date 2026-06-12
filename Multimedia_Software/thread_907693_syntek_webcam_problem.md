---
title: "syntek webcam problem"
date: 2008-09-01
forum: Multimedia Software
---

### Post by polig4e on 2008-09-01
Hello,
During the past few days my webcam started dying after working for 2-3 minutes. The only changes I have on my system is update on linux-headers as well as change in the wireless drivers.

I am using stk11xx drivers. I downloaded the latest version stk11xx.1.3.1 and tried to recompile them.

I got the following error:

sudo make -f Makefile.standalone

make -C /lib/modules/2.6.24-18-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [driver] Error 2

I tried it with my current headers (24-19) but I have the same error again.

I read about that bug in the kernel, but couldn't find a solution. I guess it has nothing to do with the webcam, but still this is the context of my problem.

Thank you in advance!

---

### Post by Crafty Kisses on 2008-09-02
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

