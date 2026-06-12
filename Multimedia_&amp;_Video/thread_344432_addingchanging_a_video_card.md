---
title: "adding/changing a video card"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by farscape on 2007-01-22
I have onboard video on my ubuntu box. works great. I added a PCI NVidia e-GeForce MX 4000 128MB video card. I dual boot with this machine and my daughter needed video with a little more guts. So I boot to Ubuntu. I get the Initial Ubuntu screen that shows everything loading. Now when I should get the login screen.......nothing. Any Ideas? Is there something I should have done to set up the change? I'm at a loss.

---

### Post by Shatrat on 2007-01-22
Try booting into safe mode using the second entry in your Grub list.
use the command dpkg-reconfigure xserver-xorg
Accept the defaults when you arent sure of the answers, and use the nv driver or the vesa one.
Afterwards you might want to install the nvidia legacy driver to get 3d and higher resolutions, but nv or vesa should be able to at least get you a graphical environment.

---

### Post by farscape on 2007-01-23
> **Shatrat said:**
> Try booting into safe mode using the second entry in your Grub list.
use the command dpkg-reconfigure xserver-xorg
Accept the defaults when you arent sure of the answers, and use the nv driver or the vesa one.
Afterwards you might want to install the nvidia legacy driver to get 3d and higher resolutions, but nv or vesa should be able to at least get you a graphical environment.

It worked. Thank you very much. :D

---

### Post by joecoin on 2007-01-24
> **Shatrat said:**
> Try booting into safe mode using the second entry in your Grub list.
use the command dpkg-reconfigure xserver-xorg
Accept the defaults when you arent sure of the answers, and use the nv driver or the vesa one.
Afterwards you might want to install the nvidia legacy driver to get 3d and higher resolutions, but nv or vesa should be able to at least get you a graphical environment.


I have the same card, only in a 64 meg version. I cannot get the driver to install and run. I am using the 9631 driver. per Nvidias website. 

Whe I use the "nvidia" line in my xorg.conf, I get the "no screens found" error.

What is the correct driver to use for this card?

---

