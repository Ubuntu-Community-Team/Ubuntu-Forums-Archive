---
title: "Cannot compile IVTV"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by ermannobonifazi on 2006-07-09
I'm not able to compile IVTV on my ubuntu box.
I'm running kernel 2.6.15-25-686 and linux headers installed (no full sources). I know full sources are not needed. I was able to install easily IVTV on my SUSE partition (same machine, same HW) but every time i try to make IVTV I got a lot of error.
Note that I've tried many release of IVTV (from 0.4.0 to 0.4.6), but the error is usually quite the same. Others components compile ok except for ivtvctl.c

make[2]: Entering directory `/usr/src/linux-headers-2.6.15-25-686'
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/tuner.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/tveeprom.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/tda9887.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-osd.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-queue.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-driver.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-fileops.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-i2c.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-streams.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-firmware.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-reset.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-gpio.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-irq.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-mailbox.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-vbi.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-kthreads.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-audio.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-ioctl.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-controls.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-video.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-cards.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/v4l1-compat.o
  CC [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-yuv.o
  LD [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv.o
  LD [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-fb.o
  Building modules, stage 2.
  MODPOST
  CC      /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-fb.mod.o
  LD [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv-fb.ko
  CC      /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv.mod.o
  LD [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/ivtv.ko
  CC      /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/tda9887.mod.o
  LD [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/tda9887.ko
  CC      /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/tuner.mod.o
  LD [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/tuner.ko
  CC      /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/tveeprom.mod.o
  LD [M]  /home/ebonifazi/MyDownload/ivtv-0.4.4/driver/tveeprom.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-25-686'
make[1]: Leaving directory `/home/ebonifazi/MyDownload/ivtv-0.4.4/driver'
make -C utils all
make[1]: Entering directory `/home/ebonifazi/MyDownload/ivtv-0.4.4/utils'
make -C ../driver ivtv-svnversion.h
make[2]: Entering directory `/home/ebonifazi/MyDownload/ivtv-0.4.4/driver'
make[2]: Leaving directory `/home/ebonifazi/MyDownload/ivtv-0.4.4/driver'
cc -I/home/ebonifazi/MyDownload/ivtv-0.4.4/utils -I/home/ebonifazi/MyDownload/ivtv-0.4.4/utils/../driver -D_GNU_SOURCE -O2 -Wall   -c -o ivtvctl.o ivtvctl.c
make[1]: Leaving directory `/home/ebonifazi/MyDownload/ivtv-0.4.4/utils'
....
-----
.....
ivtvctl.c:1860: error: syntax error before string constant
ivtvctl.c:1860: warning: type defaults to ‘int’ in declaration of ‘printf’
ivtvctl.c:1860: warning: data definition has no type or storage class
ivtvctl.c:1863: warning: type defaults to ‘int’ in declaration of ‘close’
ivtvctl.c:1863: warning: parameter names (without types) in function declarationivtvctl.c:1863: warning: data definition has no type or storage class
ivtvctl.c:1864: error: syntax error before numeric constant
ivtvctl.c:1864: warning: type defaults to ‘int’ in declaration of ‘exit’
ivtvctl.c:1864: warning: data definition has no type or storage class
make[1]: *** [ivtvctl.o] Error 1
make: *** [all] Error 2

---

