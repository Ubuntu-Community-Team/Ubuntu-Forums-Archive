---
title: "How to configure a video projector Panasonic PT-AE500 ?"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by srouquette on 2007-03-26
Hello,

I have some problems to use my video projector, it doesn't seem to send ddc information to xorg (found it in xorg's log file)
I have a ATI Radeon 9700 and I'm using the radeon drivers provided by xorg.

Which kind of information should I provide in xorg.conf to use MergedFB ?

I posted my problem [here](http://www.ubuntuforums.org/showpost.php?p=2340917&postcount=58), but it's more a problem linked to my video projector than MergedFB.

I found there was a [patch for the SiS driver](http://webcvs.freedesktop.org/xorg/xc/programs/Xserver/hw/xfree86/drivers/sis/sis.h?view=log), but is there something for ATI which could fix my problem ?

Thanks for your answers.

---

### Post by srouquette on 2007-03-26
I discovered something new, the ddc work when I boot linux with the videoproj enabled, but it doesn't work if I restart X.

---

