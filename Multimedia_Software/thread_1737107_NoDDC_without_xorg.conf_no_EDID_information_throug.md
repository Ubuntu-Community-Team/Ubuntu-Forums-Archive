---
title: "NoDDC without xorg.conf: no EDID information through displayport/DVI"
date: 2011-04-23
forum: Multimedia Software
---

### Post by dsjstc on 2011-04-23
Apparently you can't get EDID information through a Displayport->DVI adapter.  That means that a default install of Lucid (or Natty!) does not recognize the resolutions of any monitor connected with such an adapter.

I'd rather not create an entire multihead xorg.conf just to specify NoDDC.  Is there any other way to pass that option to X?

---

### Post by dsjstc on 2011-07-21
Edit To /etc/gdm/PreSession/Default

Before the initctl line, add:
xrandr --addmode DisplayPort-0 1280x1024

You can list the available port names with 
xrandr -q

---

