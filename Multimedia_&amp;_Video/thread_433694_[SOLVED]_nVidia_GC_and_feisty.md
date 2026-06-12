---
title: "[SOLVED] nVidia GC and feisty"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by pieroxy on 2007-05-05
I just upgraded from Edgy to Feisty and my nvidia driver doesn't work anymore... The X server starts with the error : Failed to load the NVIDIA kernel module.

I changed my xorg.conf to 'nv' and this is working fine, but the desktop effects don't work with nv, plus the performances aren't as good as with the nvidia driver...

What is wrong ?

---

### Post by zvacet on 2007-05-05
I´&#7743; not an expert,but I think you have to upgrade drivers too.

---

### Post by pieroxy on 2007-05-06
Well, how does one do that? I sure installed nvidia-glx and this package is up to date on my system, so I don't quite get what I need to do...

---

### Post by pieroxy on 2007-05-08
I got that one: I followed a guide where you have to remove all nvidia-* packages. But I didn"t know that nvidia-glx isn't enough to run the nvidia drivers: I needed to install the nvidia kernel module as well.

Just so you know.

---

