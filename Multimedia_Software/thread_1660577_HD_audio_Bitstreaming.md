---
title: "HD audio Bitstreaming"
date: 2011-01-05
forum: Multimedia Software
---

### Post by itsab67 on 2011-01-05
Has anyone sucessfully bitstreamed Dolby TrueHD or DTS Master Audio to there audio reciever via hdmi using either a AT*I or Nvida card ? Is this even possible to do in Ubuntu 10.10 ? If so what graphics card are you using?*
 
*I know it works well in windows using mediaplayer classic and ffdshow*
 
*ive tried everything on this issue and cannot get bitstreaming to work with my A*TI Radeon 5450 card.
 
So either ubuntu just cant bitstream or perhaps i need a different card?

---

### Post by BicyclerBoy on 2011-01-05
It can work with nvidia GT220/240/430 (driver 260) with alsa 1.0.23.

Have no info about AMD/ATI ...

AFAIK This alsa version is included in kernel updates for 10.10.

It works in 10.04 if you install alsa 1.0.23 + kernel modules..

Then need some player s/w to take advantage..

I believe with windoze you must replace the windoze (kernel) audio driver because it is 16 bit limited.
I don't think it is PnP.

---

### Post by itsab67 on 2011-01-06
Ok its good to know that bitstreaming does in fact work with Ubuntu with Nvidia GT series video cards. 
 
Does anyone know if bitstreaming works with the A*TI  HD Radeon 5xxx series cards?*
 
*im hoping so or i will have to buy a new video card  *

---

