---
title: "Green/Blue tint on Video files"
date: 2011-05-09
forum: Multimedia Software
---

### Post by G_Dem on 2011-05-09
Hi guys, hope someone can help. It seems to have only recently starting happening. I've tried VLC and Movie Player, and different types of format such as AVI and 3gp. Anything I could try to eliminate things?

[IMG]http://i2.photobucket.com/albums/y1/G_R5GTT/Screenshot.png[/IMG]

---

### Post by G_Dem on 2011-05-09
I seemed to have fixed it now. I switched from NVIDIA accelerated graphics driver (version 173) to (version current recommended). Seems strange though that the info for the driver says "The driver is activated but not currently in use". The xorg config file says im using the nvidia driver:

Driver         "nvidia"
VendorName     "NVIDIA Corporation"

---

