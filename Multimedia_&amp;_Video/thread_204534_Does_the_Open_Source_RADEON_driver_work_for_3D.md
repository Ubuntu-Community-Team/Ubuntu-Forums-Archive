---
title: "Does the Open Source RADEON driver work for 3D?"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by vyruss on 2006-06-27
Hi, I'm trying out the open source "ati" driver, which I guess autoloads the RADEON driver. I have an ATI Radeon 9500 Pro card (which has the R300 chipset).

According to my Xorg.0.log, DRI is enabled, however according to glxinfo I have no 3D acceleration. 

I thought that this had been enabled, at least experimentally, by now?

Is there any way to get 3D out of the open source ATI driver for the R300 chipset?


Thanks,
Jimmy

---

### Post by BoneKracker on 2006-06-27
Did you not find the answer by searching the forums?  I seem to recall seeing a LOT of discussion regarding that.

---

### Post by Ranime on 2006-06-27
Further more, the "ati" and "radeon" drivers are for 2d only (with some minor 3d support)...

---

### Post by vyruss on 2006-06-27
[QUOTE=BoneKracker]Did you not find the answer by searching the forums?  I seem to recall seeing a LOT of discussion regarding that.[/QUOTE]

No, I did not find anything on the *current* state of the driver. It is supposed to accelerate 3D on the R300 chipset *now*, but I can't get it to work.

---

### Post by whatever on 2006-06-27
i get 3d acceleration with the "ati" driver on my radeon 9700 by default, but:
[list]
[*] it's much slower than fglrx
[*] no support for pixelshader etc.
[*] after some minutes of using opengl the whole system freezes. the only workarround for this is to initialize the card with the fglrx driver before unloading fglrx again and using the ati/radeon driver.[/list]

i tried both, the driver included with dapper and the current mesa cvs. some error messages are gone in cvs, but because of the freeze thing accelerated 3d is disabled in cvs for radeon 9700 and has to be forced with r300_force_r300=1 (which results in freezing after some minutes again ;)).

however, the open source driver is not completely useless.
let's assume it does not freeze with your card. in this case you get:
[list][*]quake3, tuxracer, neverball playable (with reflections off in neverball) 
[*]very fast xv overlay without overscan bug (noticed in tvtime with fglrx).
[/list]

=> at the moment you should stay with fglrx, but the open source driver will probably become usable in some months/years

edit: i tried the mesa cvs about 3 weeks ago, so there may have been some changes in the meantime
edit2: if you got fglrx installed on your system it replaces your libGL.so.1.2, so you won't get open source 3d without preloading the mesa-libGL

---

### Post by vyruss on 2006-06-29
[QUOTE=whatever]however, the open source driver is not completely useless.
let's assume it does not freeze with your card. in this case you get:
[list][*]quake3, tuxracer, neverball playable (with reflections off in neverball) 
[*]very fast xv overlay without overscan bug (noticed in tvtime with fglrx).
[/list]

=> at the moment you should stay with fglrx, but the open source driver will probably become usable in some months/years

edit: i tried the mesa cvs about 3 weeks ago, so there may have been some changes in the meantime
edit2: if you got fglrx installed on your system it replaces your libGL.so.1.2, so you won't get open source 3d without preloading the mesa-libGL[/QUOTE]

OK, thanks!

---

