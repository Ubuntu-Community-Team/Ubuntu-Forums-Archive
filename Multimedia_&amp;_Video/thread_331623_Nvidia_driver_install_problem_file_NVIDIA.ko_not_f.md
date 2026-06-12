---
title: "Nvidia driver install problem: file NVIDIA.ko not found"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by Patrick K on 2007-01-04
I tried installing the Nvidia-glx drivers on my Edgy system. It has a GeForce 2 MX 100/200 card. According to the list I saw on tseliot's site the glx driver is the correct one. The drivers were downloaded from the site listed on his installation page. Using his Method 1, I was able to log out and log back in to the GUI. However, when I rebooted I got the following error:
> FATAL: Could not open '/lib/modules/2.6.17-10.generic/volatile//NVIDIA.ko
(EE) NVIDIA (0): Failed to load NIVIDA kernel module
(EE) NVIDIA (0): ***aborted***
(EE) Screens(s) found, but none have a usable configruation

After restoring xorg.conf, I looked in that directory and it wasn't there. I did a search on this forum but didn't turn up any post with NVIDIA.ko. It isn't to be found on my system, either.

What is the best way to tackle getting these drivers correctly installed?

---

### Post by Patrick K on 2007-01-05
Any thoughts on this issue?

---

### Post by tseliot on 2007-01-06
Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Patrick K on 2007-01-06
I ran "**envy_0.7.5-0ubuntu1_all.deb**" the first time I tried installing  and had to manually edit xorg.conf to restard the GUI. For whatever reason the automatic backup didn't work. That is why I tried manually installing. I'll give it another try.

---

### Post by Patrick K on 2007-01-06
I ran the script agani and, for whatever reason it worked. Like I said, it didn't the first time. Thanks.

---

