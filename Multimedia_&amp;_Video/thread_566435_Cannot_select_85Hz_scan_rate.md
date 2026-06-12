---
title: "Cannot select 85Hz scan rate"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by FarmerJo on 2007-10-03
Hi,

I am using a Flatron F900P monitor but cannot increase the refresh rate above 78Hz when using a screen resolution of 1280x1024. 

First how do you know what the colour depth is for any selected resolution?

How do I modify the xorg.conf file to enable me to select a refresh rate of 85Hz?

I have made some changes to this file already in the monitor section as follows.

Section "Monitor"
	Identifier	"L900P"
	Option		"DPMS"
	Horizsync	28-107
	Vertrefresh	43-200
EndSection

The Identifier, Horizsync and Vertrefresh have been modified to values which I think are correct.

Also the screen section has been updated as follows.

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce 7300 LE"
	Monitor		"L900P"
	Defaultdepth	24
	SubSection "Display"
		Depth	1

In this case only the Monitor value has been changed.

I know that the video card and monitor are both capable of supporting this refresh rate because this setting is used in my windose setup.

Regards
FarmerJo

---

