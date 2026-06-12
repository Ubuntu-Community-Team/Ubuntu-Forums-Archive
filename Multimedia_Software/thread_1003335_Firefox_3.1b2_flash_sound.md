---
title: "Firefox 3.1b2 flash sound"
date: 2008-12-06
forum: Multimedia Software
---

### Post by CholericKoala on 2008-12-06
So I'm testing Firefox 3.1 beta2 build2, which is what I am posting from, and everything is quite fast and snappy.  However, when I go on youtube, or anything with flash, sound does not work.  When I open up my pulse audio settings, it will not allow me to look at the playback tab which normally shows what streams are playing.  It automatically switches me to the output devices tab.  Any ideas?

Thanks.

---

### Post by gandaran on 2008-12-06
> **CholericKoala said:**
> So I'm testing Firefox 3.1 beta2 build2, which is what I am posting from, and everything is quite fast and snappy.  However, when I go on youtube, or anything with flash, sound does not work.  When I open up my pulse audio settings, it will not allow me to look at the playback tab which normally shows what streams are playing.  It automatically switches me to the output devices tab.  Any ideas?

Thanks.
remove flash 9 (if you are using flash 9) and install adobe flash 10 which should fix the pulseaudio flash sound issue, or fix the flash 9 sound problem (ubuntu 8.04 + adobe flash 9), to ways to do it, first easy one and not recommended as it may crash firefox is just to install **libflashsupport** package, the other is fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
you may need to fix pulseaudio too if flash 10 still won't fix the sound issue.

---

