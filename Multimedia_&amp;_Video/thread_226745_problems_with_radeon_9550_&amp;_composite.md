---
title: "problems with radeon 9550 &amp; composite"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by Jeff_Ciesielski on 2006-07-31
I have to some degree gotten composite to work, but for some reason, when I add the line

Section "Extensions"
Option "Composite" "Enable"
EndSection

to my xorg.conf file, my card looses 3d acceleration.  when I run fglrxinfo or glxgears, my accelerator shows up as mesa, and composite wont work (obviously). It shows an error to the effect that "dri cant be found on screen 0".  Why would composite screw up dri?  Any help would be appreciated. :) 

note: im using the xorg-drivers-fglrx package for my drivers, I havn't installed the ati proprietary drivers yet.

---

### Post by whatever on 2006-07-31
> **Jeff_Ciesielski said:**
> note: im using the xorg-drivers-fglrx package for my drivers, I havn't installed the ati proprietary drivers yet.
xorg-drivers-fglrx = ati proprietary drivers :rolleyes: 

the fglrx driver does not support composite yet.

---

