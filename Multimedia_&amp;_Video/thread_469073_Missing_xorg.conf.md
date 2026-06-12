---
title: "Missing xorg.conf"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by polaren on 2007-06-09
Hi! I have just made a fresh install of xubuntu 7.04 and I have some problems installing the ati-drivers. There is no xorg.conf in /etc/X11/ so I can't do: 

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
(since there isn't any file to wright to.)

I have tried creating a new xorg.conf but it disappears as soon as I restart the xserver.
I have also tried:
```
sudo dpkg-reconfigure xserver-xorg
```
but with no success.

Does anyone have an idea why I keep loosing my xorg.conf (it isn't just being replaced, it disappears completely!)?

Thank You.

---

### Post by diatribe on 2007-06-09
uhm, I think the xserver would not even start without an xorg.conf; are you sure you're not missing it?

---

### Post by lluisanunez on 2007-06-09
Open a terminal and type
```
 locate xorg.conf

```

---

### Post by polaren on 2007-06-09
> **diatribe said:**
> uhm, I think the xserver would not even start without an xorg.conf; are you sure you're not missing it?

Yes, I think you are right. 

Everything works fine now, I found out that it was the "aticonfig --inital" command that removed my xorg.conf. Instead of running the command I manually edited xorg.conf to point to the fglrx driver instead of vesa.

I'm sorry I took your time, thanks anyway! :)

---

