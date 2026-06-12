---
title: "Ubuntu 10.10 no sound from headset jack (with alsa info)"
date: 2011-03-14
forum: Multimedia Software
---

### Post by emailmyremail on 2011-03-14
I have a new install of 10.10 on a Toshiba Satellite with a dual boot of win7.  

I installed 10.10 and on the first night I swore the headphone jack sent sound to my external speakers (may of been plugged in during install).  Then the next day I couldn't get any sound out of the jack.  Sound kept coming out of my internal speakers.  In win7 the jack worked normally.

In Ubuntu I have checked sound preferences and my alsa mixer.  There is no listing for a headphone jack (so it is not muted).  

here is my alsa info:
[http://www.alsa-project.org/db/?f=471694b28ddcdc2e25237c9a6fd30a4c8b8f34af](http://www.alsa-project.org/db/?f=471694b28ddcdc2e25237c9a6fd30a4c8b8f34af)

not sure if this will help me:
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by emailmyremail on 2011-03-18
> **Temüjin said:**
> The satellite 655 uses the same codec and needs  keyword "options snd-hda-intel model=ideapad" for all jacks to work  properly. Try thinkpad if that doesn't work. Here's the full list:
```
Conexant 5066
=============
  laptop    Basic Laptop config (default) 
  hp-laptop    HP laptops, e g G60
  asus        Asus K52JU, Lenovo G560
  dell-laptop    Dell laptops
  dell-vostro    Dell Vostro
  olpc-xo-1_5    OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad    Lenovo Thinkpad
```

I put in the ideapad code rebooted and played music from though my  external speakers and danced when sound actually came out!  Thank You  Temujin!

---

