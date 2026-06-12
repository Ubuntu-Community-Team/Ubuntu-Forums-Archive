---
title: "sound gone in Ubuntu Gutsy after installation xp"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by zorro740 on 2008-04-17
hi guys,
I have HP dv 2000 laptop and after i ve installed the XP & I  fix  the sound card Conexant High Definition Audio drivers sounds work in XP but Unfortunately gone in Ubuntu,

i fix the problem b4 but really i 4get hw 2 fix it again
 Anybody have an Idea about this issue...
Tnxxxxx

P.S :Getting the ALSA drivers from a *fresh* kernel didnt work

---

### Post by xc3RnbFO8P on 2008-04-17
In Terminal:
> wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2)
> tar xvpjf alsa-driver-1.0.16rc1.tar.bz2
> cd alsa-driver-1.0.16rc1
> ./configure --with-cards=hda-intel
> make
> sudo make install

---

