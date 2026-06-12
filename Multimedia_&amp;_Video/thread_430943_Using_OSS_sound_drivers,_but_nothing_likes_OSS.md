---
title: "Using OSS sound drivers, but nothing likes OSS"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by wsmoser2004 on 2007-05-02
I have a pretty old laptop, which used to run Windows 2000.  The sound card is notoriously difficult to get working (and to my knowledge there aren't even Windows XP drivers for it...).  lspci tells me that it's a Creative EV1938.  The modules that ALSA loads is snd_ens1371, which doesn't work.  It appears to work, that is, I can control the volume with alsamixer, but no sound comes out.

I am able to get some sound by using the OSS module es1371, but the problem is that a large part of Xubuntu is trying to use ALSA (I think).  I am able to change things like xine, mplayer, and so forth to use OSS, but I am still having trouble making things like Flash 9 work with OSS, or sounds at the login screen, etc.  Is there a way to tell everything to use OSS?  It would make this old laptop almost perfect ;)

---

### Post by eracerbit on 2007-05-14
any news on this? having a similar situation myself, only oss seems to work on this old soundblaster card.

edit: the oss drivers load ok. tried to load esd like this: ```
 esd -d /dev/dsp 
``` ...but esd says it can't find a PCM at /dev/dsp. /dev/dsp exists.

---

### Post by ThomasNovin on 2007-05-18
According to this page:

[http://www.opensound.com/press/2007/OSSv4.txt](http://www.opensound.com/press/2007/OSSv4.txt)

The latest version of OSS supports Flash 9. There is also some notes about compatibility with ALSA-apps.

---

