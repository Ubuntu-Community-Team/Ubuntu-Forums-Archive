---
title: "R30 ThinkPad Glade Video Only 800x600  9.04"
date: 2009-08-19
forum: Multimedia Software
---

### Post by harrismh777 on 2009-08-19
hi folks,
I fired openSUSE...

... now loading all machines on 9.04 ubuntu... love it until now,

My R30 ThinkPad will only come up in 800x600.  I am sure I can get around
this with some XORG conf entry... but don't know what.

Anyone know what I need to do to the conf file to get past 800x600?

Thanks !   :)

---

### Post by harrismh777 on 2009-08-20
Well, here is the xorg.conf file that works... cheers!

:KS

Section "Device"
	     Identifier	     "Configured Video Device"
EndSection

Section "Monitor"
	     Identifier	     "Configured Monitor"
	     HorizSync	     28-49
	     VertRefresh     	43-72
EndSection

Section "Screen"
	     Identifier	     "Default Screen"
	     Monitor		     "Configured Monitor"
	     Device		     "Configured Video Device"
	     DefaultDepth	     24
	     SubSection	     "Display"
	     	     Modes	     "1024x768" "800x600" "640x480"
	     EndSubSection
EndSection

---

