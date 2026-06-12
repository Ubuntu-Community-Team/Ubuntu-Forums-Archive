---
title: "DRI on R300 (Radeon 9700 PRO) based ATI card in Intrepid?"
date: 2008-11-24
forum: Multimedia Software
---

### Post by moody_cz on 2008-11-24
Hi,

I'd like to ask u if there's a way how to run DRI on this card in Intrepid. In 8.04LTS it worked just fine, however, after upgrade I had to run X server in low-graphics mode. 

I checked X.log and it was complaining that /dev/dri/card0 doesnt exist. I use an opensource radeon driver. After I disabled DRI in xorg.conf, it works without any errors, but the performance in 3D is very low and I can't use 3D desktop effects as well.

Installing FGLRX drivers end up with segmentation fault after running aticonfig --initial -f.

If there is no way out of that, has anyone tried to downgrade back to version 8.04LTS? Without clean install, of course.

Thanks for any answer,
Jiri

---

### Post by Anfanglir on 2008-12-11
I've got the same problem on Intrepid with my Radeon 9700 (hardy worked fine).

:( Anfanglir

---

### Post by gausscannon on 2008-12-20
Same here. Have you yet found a workaround?

---

