---
title: "[SOLVED] Gnome screen resolution tops @ 1024x768 on ATI Rage Pro"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by bungee_70 on 2007-08-18
Hi,

I just did a clean install of Ubuntu 7.04 on my PC with an ATI Rage Pro AGP 4MB card (everything defaulted).  In Gnome, I can't set my resolution above 1024x768 even though my monitor is 1600x1200. In my old Red Hat 7.3, I had no problem using higher resolution with the card.

In xorg.conf, I see multiple "Display" subsections that all look the same as below, except for Depth:
> SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection


One thing I find weird is:
> Section "Device"
        Identifier      "ATI Technologies Inc 3D Rage Pro AGP 1X/2X"
        Driver          "ati"
        BusID           "PCI:1:0:0"
because it seems to say that the bus is PCI while my card is AGP.

I don't see what I can do. Any help? Thank you very much for your time!

---

### Post by bungee_70 on 2007-08-18
bump

---

### Post by Harlequin on 2007-08-19
Try removing all modes from Xorg.conf other than the one you want.

ie

> SubSection "Display"
Depth 24
Modes "1600x1200" 
EndSubSection

Then do an X restart

---

### Post by bungee_70 on 2007-08-19
Thank you for your reply.

I tried it and now the resolution tops @1280x800, but goes beyond the limit of my monitor, like if my monitor was still only capable of displaying 1024x768, leaving some pixels out at each side. Trying to go back in 1024x768 with the "Screen Resolution" in System/Preferences, I have a screen corruption of a small square on top left.

Any other idea? Thank you!

---

### Post by bungee_70 on 2007-08-19
Ok, I solved my problem: my video card would only work at 16bit color depth at that resolution, so I followed your suggestion but with 16bit instead of 24 and it works great, except for the corrupted square at top left which goes away after a while.

I just don't understand why the installer didn't configure correctly my card  at first time... It's hardly a newbee thing to go edit xorg.conf...

Thank you for your good suggestion, though!

---

### Post by Harlequin on 2007-08-20
It's one of my few install gripes with Ubuntu, the detection of graphics cards - but is far better than any of the others...  I usually find that Ubuntu default top out is 1024 x 768 and anything else you want editing xorg is the only way to achieve it.

---

