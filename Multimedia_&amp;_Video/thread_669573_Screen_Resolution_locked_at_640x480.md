---
title: "Screen Resolution locked at 640x480"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by fatsheep on 2008-01-16
I just upgraded this machine to Ubuntu 7.10 and, as I expected, Nvidia drivers broke.  I looked online, installed the newest version of envy and got the Nvidia driver installed.  That worked fine but I cannot get my screen resolution higher than 640x480!  

I have tried changing this setting both in System>Preferences>Screen Resolution and in the nvidia-settings.  Neither has an option for 1680x1050.  I even tried adding an entry for 1680x1050 in xorg.conf.  Still no luck...

**Monitor**: Acer 22" AL2223W (native resolution 1680 x 1050)
**Graphics Card**: Nvidia 7600 GT (PCI-E)

I have attached screenshots of two panels in nvidia-settings that might provide useful info and my xorg.conf file (note that I added in the 1680x1050 entry by hand).

---

### Post by BMWDriver on 2008-01-16
Try to choose the screen again, and make sure the widescreen tick box is ticked on the bottom left when the list of screen pops up. It's in that exact dialog box that you showed us, just initially choose another screen, and choose yours again.

---

