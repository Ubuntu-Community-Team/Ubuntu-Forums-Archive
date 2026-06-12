---
title: "no sound.plz help"
date: 2008-09-29
forum: Multimedia Software
---

### Post by dr vedak on 2008-09-29
hi there.i'm a new bee to linux and dont wish to switch back to windows.i installed ubuntu 8.04 and kde on acer aspire 5920.i m not getting audio.tried various tricks discussed in other forums.m working on ship and will be back home after 2 months.company is filtering internet traffic and not allowing to download drivers.i m not sure whether the problem is with drivers.audio working fine on windows xp.plz help

---

### Post by markbuntu on 2008-09-29
Most likely, you do not need to download any driver as you have them all already. This is an excerpt from my guide that may help you figure out what is going on:

If you are having trouble determining which module or module option you need for your sound card the entire list of supported cards and options is already on your computer ( the driver directory where this file resides also has all sorts of miscellaneous information on specific sound cards/devices):

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

** This is the part that will most likely help you**

If you are having problems with the HDA card/chip on your laptop or one of these:

HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8 ),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461
 you should look here (look through the entire thread if the OP does not fix your problem , people have posted solutions for many specific machines):

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Start in Post #2 here:

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

The entire troubleshootin guide is here, you may want to read it when you have some spare time:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Bon Voyage!!

mark

---

