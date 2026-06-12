---
title: "Changing video card (from NVidia to ATI)"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by Robban59 on 2005-10-25
Hi everybody,

I'm still running Hoary but am planning to upgrade to Breezy ASAP;
on my PC I have a Nvidia Geforce 4200 that I plan to substitute with a more recent one either a 6600GT or a X800GT.

First question : from a UBUNTU hw support point of view, is it better to have an Nvidia or an ATI card ? Any major compatibility/performance problems ? 
My GE4200 is serving me well and had no problems whatsoever under Hoary.

Second question : when I do change the video card, how do I go about it ? 
I presume I start Hoary with the old card installed, sort of "deinstall" the Nvidia drivers, power off, change video card, power on, install ATI drivers.
But what are the command/XORG.conf editings to do all that ? 

Better to do this in Hoary or Breezy or is it the same ? 

Thanks so much in advance/Robban

---

### Post by mo_x on 2005-10-25
I think nvidia provides better drivers. If you search these forums you will find many problems with the ATI drivers (no personal experience).
If you go with an nvidia card you won't have to change the driver.
Maybe you can change you xorg.conf to use the vesa or vga driver before you change the card so you are sure X is working.

---

