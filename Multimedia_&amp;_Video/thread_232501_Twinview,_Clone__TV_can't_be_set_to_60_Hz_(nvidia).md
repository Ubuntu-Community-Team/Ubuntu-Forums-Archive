---
title: "Twinview, Clone:  TV can't be set to 60 Hz (nvidia)"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by sifian on 2006-08-08
I've gotten my TV out to work alright, but when I have my vid card display to both my crt monitor and my tv simultaneously, it seems to be locked at 50 hz.  The annoying thing about this is it causes some vsync issues on the TV.

here is the device section from my xorg.conf

```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"

	Option "TwinView" "true"
	Option "TwinViewOrientation" "Clone"
	Option "TVOutFormat" "S-VIDEO"
	Option "TVStandard" "NTSC-M"
	Option "Metamodes" "1280x1024, NULL; 640x480, 640x480"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
EndSection
```

Now with this setting, 1280x1024 runs at 60 Hz, and 640x480 runs at 50 hz.

I've tried using the following line:

```
Option "Metamodes" "1280x1024, NULL; NULL, 640x480"
```

which will allow me to view my monitor and my TV separately at 60 hz.  The problem is when I switch back to 1280, X crashes on me, forcing me to do a hard reset on my system. 

Any suggestions?

---

