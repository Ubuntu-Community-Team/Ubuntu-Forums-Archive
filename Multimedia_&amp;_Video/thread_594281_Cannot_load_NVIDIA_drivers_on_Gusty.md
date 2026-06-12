---
title: "Cannot load NVIDIA drivers on Gusty"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Kool_Kat on 2007-10-27
Similar to others, I am also having problems with NVIDIA drivers.

Configuration is AMD64 Gusty with NVIDIA 6600GT video card on an ASROCK 939Dual-SATA2 motherboard.

The thread with the most similar problem to mine is this one [http://ubuntuforums.org/showthread.php?t=497264](http://ubuntuforums.org/showthread.php?t=497264)
I also get a blank screen when I try to use the nvidia drivers. I have tried the automatic restricted driver install, doing it manually either via the nvidia instructions or others contained in this forum, and I have also tried using envy. None of them work.

Using the manual approach to driver installation I am left with the following error in my xorg log file.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6d) [0x48670d]
1: /lib/libc.so.6 [0x2b638a1fb7d0]
2: /usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv001174X+0x36) [0x2b638c6af986]

Fatal server error:
Caught signal 11.  Server aborting

I have spent several days on this problem and its driving me nuts. Any ideas?

---

### Post by Kool_Kat on 2007-10-27
Apologies - dyslexic fingers - that should have been Gutsy - not Gusty :)

---

