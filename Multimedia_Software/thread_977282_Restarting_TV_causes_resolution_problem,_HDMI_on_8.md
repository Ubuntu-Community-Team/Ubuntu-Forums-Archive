---
title: "Restarting TV causes resolution problem, HDMI on 8.10"
date: 2008-11-10
forum: Multimedia Software
---

### Post by bsv on 2008-11-10
Hi everyone,

I have set up my first HTPC over the weekend and after several sleepless nights I now have a lovely working (almost completely!) mythtv setup. However  I have problem whenever I turn off my tv (a Samsung 22" LCD connected via HDMI). When I turn it back on what was widescreen has become square, ie. the screen is squashed into the left side of the screen, losing about a quarter of the screen real estate. I can still see everything, it's not cutting it off, it's resizing.

If I log out of ubuntu and log back in it fixes the problem. My xorg.conf is as follows:

```
Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
	ModeLine     "1280x1024" 108.0 1280 1366 1472 1720 1024 1024 1026 1062 +hsync +vsync
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection
```

Any ideas?

Cheers,
Ben

---

### Post by bsv on 2008-11-11
bump. If I haven't specified the problem well, please let me know.

Cheers,
Ben.

---

