---
title: "Geforce 5500 + Wireless"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by [S|G] on 2007-01-16
Recently I noticed that NVidia is not supporting some video cards (such as gf4 and gf5) on their latest drivers, and this support is only avaliable using the legacy drivers they provided. The problem is, when I updated my restricted modules my video card stopped working (it's a GeForce FX 5500).

I managed to get it working again by uninstalling the restricted modules and installing the official nvidia drivers (9631) that still had support for it. The problem is, now I have a wireless card and it doesn't work without the restricted modules. Installing the restricted modules and then installing the official nvidia drivers works - until next reboot.

It seems that the kernel loads the restricted module drivers instead of the official ones (X complains about conflicting driver versions).  

While I have managed to find a way for it to work (quite ugly: manually delete the nvidia driver from the restricted drivers) I don't think it's a very appropriate thing to do, and I'm sure that the driver will break again when I update the modules.

Is there any solution to that?
Thanks!

---

### Post by ibbrxx on 2007-01-18
i am struggling to get my 5500 card working.
please could you guide me how to?

---

