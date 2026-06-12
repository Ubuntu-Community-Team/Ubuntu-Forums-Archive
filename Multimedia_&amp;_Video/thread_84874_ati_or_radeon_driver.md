---
title: "ati or radeon driver"
date: 2005-11-01
forum: Multimedia &amp; Video
---

### Post by duffman25 on 2005-11-01
Hi

can someone explain me what's the diference between the ati & the radeon driver from X.org? Ubuntu configured by default to ati, but I've been playing with the xorg.conf file & I can get to gnome with the radeon one. Apparently there's not much difference.

On another question, for nvidia card you only have the nv driver?

I have two computer, one with an ati x600 & the other with a gforce 6600GT.

---

### Post by 23meg on 2005-11-01
I don't use ATI but to the best of my knowledge "ati" is the open source driver that ships with Ubuntu whereas "radeon" is the proprietary ATI driver. In nvidia, similarly, "nv" is the default driver and "nvidia" is Nvidia's closed source one.

---

### Post by duffman25 on 2005-11-01
[QUOTE=duffman25]Hi

can someone explain me what's the diference between the ati & the radeon driver from X.org? Ubuntu configured by default to ati, but I've been playing with the xorg.conf file & I can get to gnome with the radeon one. Apparently there's not much difference.

On another question, for nvidia card you only have the nv driver?

I have two computer, one with an ati x600 & the other with a gforce 6600GT.[/QUOTE]

I found some info here:
[http://wiki.x.org/wiki/VideoDrivers](http://wiki.x.org/wiki/VideoDrivers)

---

### Post by duffman25 on 2005-11-01
[QUOTE=23meg]I don't use ATI but to the best of my knowledge "ati" is the open source driver that ships with Ubuntu whereas "radeon" is the proprietary ATI driver. In nvidia, similarly, "nv" is the default driver and "nvidia" is Nvidia's closed source one.[/QUOTE]

Not exactly, you're right with nvidia, but the propietary ati driver is called fglrx. Ati appears to have various drivers, depending on the card in use, radeon, r128 & atimisc.

---

### Post by 23meg on 2005-11-01
I stand corrected :)

---

### Post by Dracontopes on 2005-11-01
radeon is an older module I think, and 3d acceleration works only with the r200 chip. 2d acceleration works with all cards however. (well, most of them, my 9700pro works good) When Xorg7 will be released, compositing with the radeon module will be possible because it works with EXA. So hopefully, ATi + radeon driver = good 2d perf (well, at least with compositing). :D 

However, I'm not totally sure.

**Research:**
[http://xorg.freedesktop.org/wiki/radeon]("http://xorg.freedesktop.org/wiki/radeon")
[http://xorg.freedesktop.org/wiki/ati]("http://xorg.freedesktop.org/wiki/ati")

[http://xorg.freedesktop.org/wiki/ExaStatus]("http://xorg.freedesktop.org/wiki/ExaStatus")
> 
[SIZE=1]  Supported: (Will be included in 6.9/7.0)  [/SIZE][LIST]
[*][SIZE=1]   i128  (Solid and Copy only so far, incompatible with DGA, only tested on T2R4 cards)[/SIZE]
[*][SIZE=1]   radeon (r100/r200 with Render accel, r300 core-only.  May be issues in non-DRI mode, and DGA unsupported).[/SIZE]
[*][SIZE=1]   sis  (sis/xgi; Solid() and Copy() hooks only)[/SIZE][/LIST]

---

