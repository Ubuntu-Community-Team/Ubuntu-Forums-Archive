---
title: "Firefox renders pages incorrectly (flash issue?)"
date: 2009-04-08
forum: Multimedia Software
---

### Post by Vaphell on 2009-04-08
I use Hardy (64) and use FF 3 (64) with npwrapper.libflashplayer.so Shockwave Flash 10.0 r15

I always have problems with blizzard sites, namely diablo3.com and starcraft2.com. There is always something messed up. It looks like if firefox had problems with depth on flash heavy pages - things that should be below are not. I tried googling, but flash is so problematic under linux i couldn't find anything connected to 'page depth' in dozens of linux ff/flash threads. I thought it is a generic problem with flash, but recently i found out that Opera doesn't suffer from it.

I attached 2 screenshots - same page shown by firefox and opera
Is there any fix to that problem except using Opera?

---

### Post by binbash on 2009-04-08
At my 64 bit system that page works fine with firefox and this is not about flash, there is no flash there.

[http://www.blizzard.com/diablo3/media/screenshots.xml#84](http://www.blizzard.com/diablo3/media/screenshots.xml#84)

---

### Post by gandaran on 2009-04-08
> **binbash said:**
> At my 64 bit system that page works fine with firefox and this is not about flash, there is no flash there.

[http://www.blizzard.com/diablo3/media/screenshots.xml#84](http://www.blizzard.com/diablo3/media/screenshots.xml#84)
yes there is flash, click on the exit icon on your link, the following screenshots page has flash and works fine here with 32-bits flash.

---

### Post by Vaphell on 2009-04-08
ok, I finally managed to fix this annoying issue

I purged every trace of libflashplayer.so and npwrapper.libflashplayer.do from my system along the lines of this tutorial
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)
then I copied freshly downloaded 64bit libflashplayer.so to /usr/lib/firefox-3.0.8/plugins
and viola, no more renderig glitches :D

---

