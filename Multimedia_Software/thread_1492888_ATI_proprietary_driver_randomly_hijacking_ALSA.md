---
title: "ATI proprietary driver randomly hijacking ALSA?"
date: 2010-05-25
forum: Multimedia Software
---

### Post by kleei2 on 2010-05-25
So it appears the ATI proprietary video driver is hijacking ALSA about 1 out of every 5 system bootups.  On a bad bootup I have no sound and cannot umute the volume.  Opensource is not an currently an option so don't bother suggesting it.  Here is a screenshot of a good & bad bootup with alsamixer running to show ATI as the culprit:

[removed]

....running Crunchbang 9.04.01 32bit (Ubuntu derivative)
2.6.28-13-generic kernel

I'm pretty sure it's ATI's driver as I've never had this problem until I installed it.  Any ideas on fixing this?

thanks in advance

---

### Post by kleei2 on 2010-05-27
SOLVED:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
under the heading:
_**[SIZE=3]"Configuring default soundcards / stopping multiple soundcards from switching"[/SIZE]**_

---

