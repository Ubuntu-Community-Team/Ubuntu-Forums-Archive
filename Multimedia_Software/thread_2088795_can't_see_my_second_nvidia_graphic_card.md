---
title: "can't see my second nvidia graphic card"
date: 2012-11-27
forum: Multimedia Software
---

### Post by alwentio on 2012-11-27
Hi all,

I just installed ubuntu 10.04 with two nvidia graphics cards, but nvidia x server settings doesn't recognize the second one.

I installed the proprietary drivers from nvidia, and the first one is working well.
lspci shows the two graphical cards.
So I changed my xorg.conf to add the second one, with the right BusID :

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"  #was not initially set
    VendorName     "NVIDIA Corporation"
EndSection

#added
Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    BusID          "PCI:2:0:0"
    VendorName     "NVIDIA Corporation"
EndSection

And I restart X.
But nothing happens, I can't see the second one in nvidia X server settings.

Any ideas ?

Thanks.

---

### Post by BicyclerBoy on 2012-11-27
32 or 64 bit install ?
Are the video cards the same model?
What are the cards?

Read/Post the file /var/log/Xorg.0.log..

32bit systems can have a problem with not allocating enough RAM for the initial boot process.

---

