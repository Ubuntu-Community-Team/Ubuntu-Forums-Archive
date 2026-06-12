---
title: "xserver-xorg"
date: 2009-05-03
forum: Multimedia Software
---

### Post by fajerpeter on 2009-05-03
I have upgraded to Jaunty from Intrepid but lost the video graphics altogether.  I can only boot in the "recovery" terminal,  and attempted 
dpkg-reconfigure -phigh xserver-xorg 
which finds only the keyboard but not video cards (Radeon X550)

I tried to manually change /etc/X11/xorg.conf   entry of Device to 
Identifier  "Generic VGA"
Driver   "vesa"

to get the generic driver but no luck there.

thanks

---

### Post by xc3RnbFO8P on 2009-05-03
If upgrading fails, try fresh install.

---

### Post by fajerpeter on 2009-05-04
Got it to work in a following way by partly following Phoronix instructions to reinstall the xserver-xorg:

apt-get autoremove
apt-get install xserver-xorg-video-radeon xserver-xorg-video-ati  xserver-xorg-video-radeonhd
dpkg-reconfigure xserver-xorg

(I still did not get to the video card configuration but just the keyboard, i.e. the last step might not be necessary if xorg.conf was set to "Configulre Video Device" )

reboot

---

### Post by eldragon on 2009-05-04
> **fajerpeter said:**
> Got it to work in a following way by partly following Phoronix instructions to reinstall the xserver-xorg:

apt-get autoremove
apt-get install xserver-xorg-video-radeon xserver-xorg-video-ati  xserver-xorg-video-radeonhd
dpkg-reconfigure xserver-xorg

(I still did not get to the video card configuration but just the keyboard, i.e. the last step might not be necessary if xorg.conf was set to "Configulre Video Device" )

reboot

why install the three of them?

---

### Post by fajerpeter on 2009-05-04
Not much thought or expertise (on my part) here, just following Phoronics instructions.    Would I get away with installation of a single package ?

thanks

peter

---

