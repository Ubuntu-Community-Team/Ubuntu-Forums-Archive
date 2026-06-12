---
title: "Stuck with 1024 X 786"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by DevNull11 on 2007-08-31
I just installed my Nvidia drivers on my new install and now I'm stuck with 1024 x 786. I what to set my resolution to 1280 x 1024 which I use with Windows. Normally I would play with Xorg config to fix this problem but since my driver are working I don't want to screw it up.

---

### Post by Lord Illidan on 2007-08-31
Then, use : gksudo nvidia-settings, go to XServer Display Configuration, and modify your res from there.

---

### Post by wolfger on 2007-08-31
So... what do you want? There isn't any way to get a better resolution than whatever is set in xorg.conf 
I had to alter mine to get better than 1024, and I had no problems with it. If you're nervous about it, just save a copy of the current conf so you can restore it later. (in fact, it's smart to do so even if you aren't worried)

---

### Post by Lord Illidan on 2007-08-31
> **wolfger said:**
> So... what do you want? There isn't any way to get a better resolution than whatever is set in xorg.conf 
I had to alter mine to get better than 1024, and I had no problems with it. If you're nervous about it, just save a copy of the current conf so you can restore it later. (in fact, it's smart to do so even if you aren't worried)

The Nvidia-settings dialog will alter the Xorg.conf for him..although he could do it manually easily enough. Do make a backup first, though, a simple

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

can be a life-saver.

---

