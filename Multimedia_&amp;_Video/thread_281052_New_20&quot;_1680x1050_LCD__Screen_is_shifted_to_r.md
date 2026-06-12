---
title: "New 20&quot; 1680x1050 LCD / Screen is shifted to right"
date: 2006-10-20
forum: Multimedia &amp; Video
---

### Post by jgbiggs on 2006-10-20
I am trying to get a decent xorg config set up for my new 20" widescreen LCD.

After I re-ran sudo dpkg-reconfigure xserver-xorg, the display is now at 1680x1050 but the screen is shifted almost 3 inches to the right!

I have run xvidtune and googled around a bunch but cannot find a solution.

Anyone else have this problem?  (the shift to the right?)

---

### Post by Kateikyoushi on 2006-10-20
I also have it but only 2 cm which I could correct in the lcd's OSD menu.
Unfortunately that machine runs XP and have to set it up manually every time the OS is switched. :-/

---

### Post by jgbiggs on 2006-10-20
same here, I use a kvm switch to bounce back and forth between ubuntu and xp

---

### Post by handy on 2006-10-20
Have you set the appropriate refresh rates for your monitor in **/etc/X11/xorg.conf** ?

-------------
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	***_30-107_***  <---> *change*
	VertRefresh	***_48-120_***  <---> *change* 
EndSection
----------------

Find out from your manual or makers web site or google the correct numbers for your model monitor.

See how you go with that... :)

---

