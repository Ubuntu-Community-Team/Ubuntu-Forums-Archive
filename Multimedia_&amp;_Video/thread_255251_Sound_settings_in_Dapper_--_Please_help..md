---
title: "Sound settings in Dapper -- Please help."
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by kagashe on 2006-09-11
Hi,

The sound recording is not working for me in Dapper Drake. In Ubuntu 5.10 I had solved the problem and posted [here]("http://www.ubuntuforums.org/showthread.php?t=155053").

I had made these settings in Ubuntu 5.10 but I don't find them in Ubuntu 6.06.
> System>Preferences>Sound
Uncheck Enable Sound Server Startup
System>Preferences>Multimedia System Selector
Set Default Sink to OSS Open Sound System
Set Default Source to OSS Open Sound System 

kagashe

---

### Post by ajgreeny on 2006-09-11
It will be best to use alsa as your sound system software, not oss as you are trying to use.  Alsa lets you use software sound sharing and is better in most (all?) respects than oss.

Have you also checked that your mic is OK and is picking up sounds?  Look in alsamixer or whatever sound config you use to see if it is muted by mistake.

Also it is worth looking at audacity for sound recording as it will give you many more options for the sound you have recorded than the gnome or kde basic packages.

---

