---
title: "VGA 82815 xorg setup"
date: 2008-07-23
forum: Multimedia Software
---

### Post by [pl]ice on 2008-07-23
hi guys,

 I have truble finding info about drivers:
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 04)


not sure how should I set up xorg, and what drivers to use, can't find much info on google.

 Could someone pls help me out? Current xorg config is a bare minimum:


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

thank you

---

### Post by overdrank on 2008-07-23
Hi and the drivers for the intel graphics should come with Ubuntu. I have several intel graphics systems and no issues. What issues are you having?
If you would like to change the resolution and driver you can use the command ```
gksu displayconfig-gtk
```

---

### Post by [pl]ice on 2008-07-23
Edit:
  Solved the problem :) that command worked nicely, but i shot myself in the foot... i was setting it up remotley, and ssh and vnc, didn't know that user had to login before i can vnc!! hahah
got the resolution, the Monitor was wrongly selected, increased no of herts and allowed me to get higher resolution
thanks!
> **overdrank said:**
> Hi and the drivers for the intel graphics should come with Ubuntu. I have several intel graphics systems and no issues. What issues are you having?
If you would like to change the resolution and driver you can use the command ```
gksu displayconfig-gtk
```
  Hi,
   mainly the resolutin at the moment is 800x640 so none of the windows fit in.. i added other resolutions, like in other examples but it just doesn't like it, and it won't go to gnome. Then I tried to add the driver 'i815' and that didn't work as well. So i'm stuck :/
  Will try that command and see whats happens. Logs don't show much

---

