---
title: "flickering image with ASUS EAH3850"
date: 2008-09-07
forum: Multimedia Software
---

### Post by gknippels on 2008-09-07
I'm running the 64-bit Hardy Heron 8.04 and use an ASUS EAH3850 ATI graphics card. I've tried ENVYNG to install the ATI driver and although the software installs perfectly and I seem to have all the card options available I always end up with a 'flickering' picture. I have two flat panel displays the Iiyama ProLite E1900S and the Iiyama Prolite E1902S, one hookup with the DVI connecter, the other with the standard VGA connector. I've tried various refresh rates from 60-75 Hz, but under all conditons the picture quality remains unacceptable due to the flickering.

Any suggestions? The card works fine with the default (non-hardware accelerated) drive that Ubuntu installs when I do a clean install, but it doens't give me any dual-monitor options.

Any suggestion?:confused:

---

### Post by puppywhacker on 2008-09-07
hoi,

In the file /etc/X11/xorg.conf there are a few sections, the first one is Device where I use "fglrx" for Driver. For the monitor sections the modelines are normally for generic lcd displays, this fits 99% of the screens, but not necessarily fit your Iiyama's.

You can specify the option "DPMS" which I believe to read the prefered settings from your monitor. (but what do I know)

Since your screens are optimally running at 1280x1024 30-80 KHz Horizontal Sync. Most LCD screens run at a refresh range of 60 Hz

Section "Monitor"
[INDENT]	Identifier   "Monitor0"
	VendorName   "Iiyama"
	ModelName    "LCD Panel 1280x1024"
	HorizSync    31.5 - 80.0
	VertRefresh  56.0 - 75.0
	Option	    "dpms"
	Modeline "1280x1024@70" 141.82 1280 1312 1848 1880 1024 1044 1056 1076 -hsync -vsync[/INDENT]
EndSection

Eitherway the log file /var/log/Xorg.0.log might (or not) be useful

---

