---
title: "why are my fonts so large with the nvidia driver"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by tcashin on 2006-11-06
I installed the nvidia drivers for edgy and now some of the fonts for my apps are much larger.  In particular, the gdm login screen has large, bold, fonts and the fonts in Matlab (R2006b) are much larger and take up too much space.  I probably wouldn't care about this issue if it were just the GDM login, but the matlab fonts are just too big.

Any idea why this is so, and how I can restore the fonts back to the size they were using the "nv" driver?  Is this an X issue?  I've used linux for sometime but I'm still quite unfamiliar with all of the configuration and administration tasks.

I'm running ubuntu 6.10 on a Dell D620 with an NVIDIA Quadro NVS 110M card.

Thanks

---

### Post by ReaderRat on 2006-11-06
Has the resolution changed or just the fonts?

---

### Post by kruzztee on 2006-11-06
nvidia driver automatically set font DPI to X current screen resolution. the reason why you got the font much larger because your screen resolution is larger than 1024x768 (the default DPI setting is 96 dpi). To make your font set to default at 96 dpi no matter the screen resolution you need to edit your xorg.conf file.

> 
add this to your device setting in xorg.conf
/etc/X11/xorg.conf
    ....
    Option   "UseEdidDpi"   "FALSE"
    Option   "DPI"   "96 x 96"
    ....


---

### Post by tcashin on 2006-11-08
Thanks kruzztee! That did it! (I tweaked the dpi to 86x86 to get it right).  Any chance you know why this only affects some of the fonts and not everything?  All of my other menu fonts and apps look fine and unaffected by the DPI setting.  It was just the GDM login and some (but again not all) of the fonts within MATLAB.  I'm pretty naive about fonts so any info/background you can provide would be appreciated.

---

### Post by vreemde eend on 2007-11-20
had the same problem, solution worked great, thanks!

---

