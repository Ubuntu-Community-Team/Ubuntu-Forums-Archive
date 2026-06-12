---
title: "Geforce 4 Card - What driver?"
date: 2008-11-05
forum: Multimedia Software
---

### Post by LostOverThere on 2008-11-05
So yes I have one of those dreaded NVidia Geforce 4 graphics cards, or a GeForce4 MX 440 AGP 8x to be precise. Yes, its one of *those* cards that is "bad" with Ubuntu 8.10 and am curious as to which driver to install. 

Cheers.

---

### Post by forger on 2008-11-05
> GeForce4 MX 440
 0x0171

GeForce4 MX 440-SE
 0x0173

GeForce4 440 Go
 0x0174

GeForce4 440 Go 64M
 0x0179

GeForce4 MX 440 with AGP8X
 0x0181

GeForce4 MX 440SE with AGP8X
 0x0182


The 96 driver supports them: nvidia-glx-96
System > Administration > Hardward drivers > check and install the **96** driver

---

### Post by LostOverThere on 2008-11-05
Sorry? Edit what? I really dont understand.:confused:

---

### Post by forger on 2008-11-05
sorry, I made a mistake, read it again now that it's correct :)

---

### Post by LostOverThere on 2008-11-05
Hmm, there's absolutely no drivers in the Hardware Drivers list.

EDIT: When I try to install it from Synaptic, it gives me an error, saying that its conflicting with xserver-xorg-core.

---

### Post by sisco311 on 2008-11-05
try to install it from a terminal and post the error message:
```
sudo aptitude install nvidia-glx-96
```

---

### Post by LostOverThere on 2008-11-05
Thanks, but yeah, like I said. It conflicts with xserver-xorg-core.

Here's the confliction error to be exact:

[http://pastebin.ws/49lh7t](http://pastebin.ws/49lh7t)

---

### Post by sisco311 on 2008-11-05
it's a known bug in the current drivers:
[https://bugs.launchpad.net/ubuntu/intrepid/+source/nvidia-graphics-drivers-96/+bug/251107]("https://bugs.launchpad.net/ubuntu/intrepid/+source/nvidia-graphics-drivers-96/+bug/251107")

you can try to install the new beta drivers by enabling 
the proposed repos:[https://wiki.ubuntu.com/Testing/EnableProposed]("https://wiki.ubuntu.com/Testing/EnableProposed")

---

