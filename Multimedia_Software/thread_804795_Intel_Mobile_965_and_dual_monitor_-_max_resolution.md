---
title: "Intel Mobile 965 and dual monitor - max resolution limitation?"
date: 2008-05-23
forum: Multimedia Software
---

### Post by ivasic on 2008-05-23
I'm using Mobile Intel(R) 965 Express Chipset on Toshiba laptop and have external TFT monitor connected.
Laptop monitor resolution is 1280x800 and ext. monitor resolution is 1680x1050.

I'm planning to install (K)Ubuntu and I've read somewhere about Intel driver limitation for dual head regarding max horizontal resolution and that if it's exceeded - I won't be able to use 3D acceleration.

Is this true? If so, what's the maximal resolution driver can handle?

---

### Post by BandD on 2008-06-13
According to this [page]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen") for xrandr the max resolution with dri still viable is 2048x2048

But you can set it up so that the screens over lap a little.  They have a nice diagram and everything  on that page.

---

