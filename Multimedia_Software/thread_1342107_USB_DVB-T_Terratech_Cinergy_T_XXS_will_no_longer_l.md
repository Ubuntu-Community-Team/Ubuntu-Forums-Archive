---
title: "USB DVB-T Terratech Cinergy T XXS will no longer load driver"
date: 2009-11-30
forum: Multimedia Software
---

### Post by Skerit on 2009-11-30
My Terratech USB DVB-T device (Cinergy T XXS) used to load fine in ubuntu 9.04, but since I upgraded it won't work anymore.

I've tried forcing it (modprobe dvb_usb_dib0700 force_lna_activation=1)
but still, no new dvb device is made, no driver is shown in the proc output.

Anyone know what happened?
The drivers have been in the kernel since 2.6.26
[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_USB_XXS](http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_USB_XXS)

---

### Post by kvroose on 2010-01-05
I see that you're flemish, you can find the answer here:

[http://forum.ubuntu-nl.org/hardware-en-drivers/installatie-terratec-dvb-t-xxs/](http://forum.ubuntu-nl.org/hardware-en-drivers/installatie-terratec-dvb-t-xxs/)

for non-dutch-talking people:

the problem is situated in the 'make' process: the system fails to install firedtv but the installation is not required to make everything work. The solution:

disable firedtv by entering this command in terminal:

nano v4l/.config

then add this line : 'CONFIG_DVB_FIREDTV=n' to the file.

Normally this should do it...

---

### Post by Nu-Sence on 2010-07-28
Thanks! That worked for me.

---

