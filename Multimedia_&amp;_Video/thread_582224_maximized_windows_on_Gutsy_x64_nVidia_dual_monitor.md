---
title: "maximized windows on Gutsy x64 nVidia dual monitor"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Nick Payne on 2007-10-19
Strange behaviour. Geforce 7600 dual head digital output to a pair of Dell 2001fp monitors. After enabling the nVidia restricted driver, when I go into Screens and Graphics I see one plug and play monitor and one unknown monitor. If I set both monitors to Dell 2001fp and 1600x1200 resolution, and extend the desktop onto the second monitor, I get the desktop across both monitors, but I also get the Gnome top and bottom panel going across both monitors, and maximizing a windows maximizes it across both monitors rather than just one one monitor. Also, any dialog or window that tries to appear centered on the screen appears split across the two monitors.

If I leave the first monitor set to plug and play and only set the 2nd monitor to Dell 2001fp, still having both at 1600x1200 resolution, then I don't get the problem with Gnome panel - it  is only on the RH monitor, nor do I get the problem with the maximized windows or centered dialogs. They maximize or center on a single screen as they should.

---

### Post by Nick Payne on 2007-10-21
I spoke too soon. After installing xserver-xgl, for compiz, the display has gone back to maximizing across both monitors.

---

### Post by darigaz625 on 2007-10-22
maybe you should try and enable xinerama?

---

### Post by MiiJaySung on 2007-10-22
xinerama + compiz = CRASH!

Annoying I know, I got the same issue

---

### Post by ERICwithanH on 2008-05-23
I had the same problem after installing the Envy Nvidia drivers.

To fix it, I did the following:

First, I made a copy of my xorg.conf file:

```
cp /etc/X11/xorg.conf xorg.conf_backup
```

Then, I edited the xorg.conf file:

```

sudo gedit /etc/X11/xorg.conf

```

I added the lines in red:

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
[COLOR="Red"]	Option "TwinView"
	Option "MetaModes" "1680x1050 1680x1050"[/COLOR]
EndSection

```

Of course, you would enter your desired resolution for each screen in place of my resolutions.

Hope that works for you.

Oh, and I have Ubuntu 8.04 Hardy, not Gutsy...

---

