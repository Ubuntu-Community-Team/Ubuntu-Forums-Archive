---
title: "Problems after installing ATI proprietary FGLRX driver"
date: 2011-02-02
forum: Multimedia Software
---

### Post by xelasha on 2011-02-02
Recently put an ATI HD5450 into my system, I'm running Ubuntu 10.4. When I booted up I went ahead and installed the ATI proprietary FGLRX driver via 'Hardware Drivers' and I'm experiencing some issues with many things.

Firstly my screensavers are really screwed up, this happens with multiple screen savers as soon as they start. It seems like some kind of resolution issue judging by the separate section on the right.
[http://img64.imageshack.us/img64/637/imag0041h.jpg](http://img64.imageshack.us/img64/637/imag0041h.jpg)
[http://img51.imageshack.us/img51/6711/imag0043lm.jpg](http://img51.imageshack.us/img51/6711/imag0043lm.jpg)

And I've had lots of glitches and quirks with all video players, last night I experienced serious lag during a video that lasted 30+ minutes. I managed to click the 'force quit' icon I have on my panel and have it force quit VLC and it took about 5 minutes or so to close VLC. I also tried a few different video modes like OpenGL, X11, etc. All same results. I tried a few video players but I'm still getting issues.

But then after VLC closed, gnome just gave up on me, all my panels were blank and unresponsive and I had no top bars on my windows (minimize,maximize,close). Amongst this I've had other small quirks and glitches but nothing worth noting. 

I'm betting it's a driver issue simply because non of this ever happened when I was using onboard video.

Xorg file:
```

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual	3200 1080
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3200 1080
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

```

But looking at that xorg file it seems that the settings absolutely do not match my running setup, the position for both Monitor's are set to 0 0 and the resolution is 1280x1024. When in fact I only have one of my monitors running at that resolution, the other is running at 1920x1080. 

Any suggestions into how to fix this issue would be greatly appreciated.

---

### Post by xelasha on 2011-02-03
*bump*

---

### Post by xelasha on 2011-02-03
*bump*

---

### Post by xelasha on 2011-02-05
*bump*

---

