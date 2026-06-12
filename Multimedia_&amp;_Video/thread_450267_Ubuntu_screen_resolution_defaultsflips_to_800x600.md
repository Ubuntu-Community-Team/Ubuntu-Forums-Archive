---
title: "Ubuntu screen resolution defaults/flips to 800x600"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by SMAH on 2007-05-21
Ubuntu has a bad habit of flipping resolutions or defaulting resolutions to 800x600.

On one PC I have Ubuntu 7.04 installed, where the graphics chipset (nVidia 6150) and monitor (1280x1024 LCD) are both capable of doing 1280x1024, I cannot get Ubuntu to do more than 800x600 on the default nv open source driver. That is all that appears on the screen resolution application under system-->preferences. I tried editing the /etc/X11/xorg.conf file, removing everything except 1280x1024 resolution and 24 bit color depth and set the default color depth to 24. After rebooting, this change has no effect. When I switch to the nVidia binary driver, the resolution changes to 1280x1024, but the nVidia driver causes blocks of colour near the cursor to be shifted over, and causes the occasional freeze up. What is going on here? Why is Ubuntu ignoring the resolution in the xorg.conf file? Is this something to do with the monitor's resolution being detected wrongly?

On another PC, I have Ubuntu 6.10 LTS installed and dual booting with Windows 2000. The display is set to 1280x1024, and worked most of the time. However on some occasions, for no apparent reason, the display resolution would flip to 800x600. On rebooting, it would return to the 1280x1024 resolution that was set. It seems that on every occasion that this happened, I had previously booted into MS Windows 2000, although it did not occur on every instance I booted into Windows 2000. I finally fixed this by replacing the xorg.conf with one from a Fedora core 6 installation I am using off the same PC using a KVM switch.

What the hell is going on here? Is the resolution switching problem due to the monitor resolution not being detected properly or perhaps due to Windows having set color depth differently on the previous session? Could it be something to do with the KVM switch?

---

### Post by SMAH on 2007-05-21
sorry 6.06 LTS not 6.10 LTS.

---

