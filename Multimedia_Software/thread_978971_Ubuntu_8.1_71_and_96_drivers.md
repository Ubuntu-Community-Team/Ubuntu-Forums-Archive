---
title: "Ubuntu 8.1 71 and 96 drivers?"
date: 2008-11-11
forum: Multimedia Software
---

### Post by chych on 2008-11-11
Well I hope someone can help with my dilemna here!

My system has an AGP Geforce4 MX 440 and a PCI Geforce2 400; in Ubuntu 8.04 everything was working well (although with a painstakingly crafted xorg file), but my dual monitor config broke in 8.1 since xorg.conf usage is completely different now. 

First off I don't care about compiz. I just want both screens displaying, preferably with direct rendering.

My main screen on the AGP card works, PCI card does not, and direct rendering works... though the Nvidia driver is *not* installed (Restricted Hardware Manager wants me to install nvidia-96-glx but if I do that, gdm doesn't start! So this can't be installed, and I have to remove it). Installing nvidia-71-glx does nothing, and more annoyingly, I cant have nvidia-71-glx and nvidia-96-glx installed simultaneously, what gives! My two cards require these two different drivers, I'd think.

If I run nvidia-xconfig, I get nothing displayed, so I have to let ubuntu rewrite the xorg.conf to its strange default one that seems to have nothing in it... Any pointers on where to go would be helpful, I have no idea what to do, since xorg.conf isn't what it used to be.

---

