---
title: "dxr3 modules"
date: 2005-11-07
forum: Multimedia &amp; Video
---

### Post by Jabone on 2005-11-07
I tried to install em8300-0.15.1 modules. Compilation went fine except few warnings:

/usr/src/em8300-0.15.1/modules/em8300_audio.c: In function `preprocess_digital':/usr/src/em8300-0.15.1/modules/em8300_audio.c:169: warning: ignoring return value of `copy_from_user', declared with attribute warn_unused_result
  CC [M]  /usr/src/em8300-0.15.1/modules/em8300_fifo.o
/usr/src/em8300-0.15.1/modules/em8300_fifo.c: In function `em8300_fifo_write_nolock':
/usr/src/em8300-0.15.1/modules/em8300_fifo.c:207: warning: ignoring return value of `copy_from_user', declared with attribute warn_unused_result

anyway modules were created and loaded without problems. Analog audio works too. Problem is that video will not show on tv. Screen flashes and stays black. 

Kernel is 2.6.12-9-k7 and I've tried with gcc-4.0 and gcc-3.4. 

Has anybody get modules to load and show video on tv with breezy? I use composite video cable. 

Hoary worked fine with adv717x pixelport_16bit=0

Thanks for help

---

