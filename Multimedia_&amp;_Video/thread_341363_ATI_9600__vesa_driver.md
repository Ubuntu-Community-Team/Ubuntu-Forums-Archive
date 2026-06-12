---
title: "ATI 9600 : vesa driver"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by Stemp on 2007-01-18
Since Edgy my ATI 9600 card seems to be unrecognized by xorg and use instead the vesa driver.
Am I the only one ? 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/73572](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/73572)

---

### Post by crispy_420 on 2007-01-19
Why not install ATI driver (fglrx) and edit xorg to use it?

---

### Post by Stemp on 2007-01-19
Well in fact i use the free ati/radeon driver. 
But on a fresh install xorg is set to vesa driver, that's my problem.
Another thing, xorg falsely detect wacom devices.

---

### Post by Robocoastie on 2007-01-19
can't you just manually edit your xorg.conf and change it from "vesa" to "radeon"?

I'd love it if x would correctly id my card and make it vesa instead of ati. Whenever I do an ubuntu based install I get the "unable to start x" error and have to vim edit the xorg.conf file to change from "ati" to "vesa" until the install is done and I can set up the latest ati drivers.

---

### Post by Stemp on 2007-01-19
> can't you just manually edit your xorg.conf and change it from "vesa" to "radeon"?

That's what I do, but as my card is ati/radeon capable it's just boring
Your card is apparently not working well with the free driver and X use it by default, and mine work perfectly with the free driver and X use the vesa driver. Just strange ;)

---

### Post by crispy_420 on 2007-01-19
for some reason wacom devices are always there by default. if you look in synaptic for xorg, the drivers are installed and you can always remove them or just comment them out in your xorg.

---

### Post by je1117 on 2007-01-19
> **crispy_420 said:**
> Why not install ATI driver (fglrx) and edit xorg to use it?

i'm with crispy.

---

