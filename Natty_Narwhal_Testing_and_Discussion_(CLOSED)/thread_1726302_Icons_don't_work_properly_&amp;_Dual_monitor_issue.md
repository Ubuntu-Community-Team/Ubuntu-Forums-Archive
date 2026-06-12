---
title: "Icons don't work properly &amp; Dual monitor issue"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by DarK420 on 2011-04-10
So in the picture below you can see how on the desktop photoshop has a icon. However when I dragged it over to unity it doesnt work. How can I fix this?


One more problem I'm having is I have 2 different monitors with Dual screen set up. The big monitor is 1920x1080 the other is 1440x900. However whenever I log out it resets the big one to 1440x900. My gfx card is ATI radeon 5770

---

### Post by DarK420 on 2011-04-11
I fixed the icon problem. 
dual screens still act up though

---

### Post by sdemmitt on 2011-04-11
so what was your fix for the icons?

---

### Post by DarK420 on 2011-04-11
I made a folder dedicated to launchers & the Icon pictures then just dragged the launcher with the icon over to unity. 

[[IMG]http://www1.picturepush.com/photo/a/5430289/220/5430289.png[/IMG]](http://picturepush.com/public/5430289)

I'll log off and see if it remained when I come back

---

### Post by DarK420 on 2011-04-11
Yeah they all stayed. Now I just need to fix my damn monitor. Idk why it resets every single time back to 1440x900 to match my smaller monitor.

---

### Post by sdemmitt on 2011-04-11
have you tried this?

[http://maketecheasier.com/how-to-setup-dual-monitors-with-xrandr/2009/06/01](http://maketecheasier.com/how-to-setup-dual-monitors-with-xrandr/2009/06/01)

---

### Post by DarK420 on 2011-04-11
None of that helps much xD
Does this help you guys at all?

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[2]-0" 0 0
EndSection

Section "Monitor"
	Identifier   "0-DFP4"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
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
	Option	    "PreferredMode" "1440x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP4" "0-DFP4"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-1"
	Driver      "fglrx"
	Option	    "Monitor-DFP4" "0-DFP4"
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3360 1920
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-1"
	Device     "amdcccle-Device[2]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by DarK420 on 2011-04-11
anyone know a way to make my resolution stay at 1980x1020 permanently

---

### Post by Blasphemist on 2011-04-11
I haven't had just your issue with the resolution, mine didn't change, but I've had to use the multiple display app that is a gui for xrandr to make mine behave better.

---

### Post by DarK420 on 2011-04-12
> **Blasphemist said:**
> I haven't had just your issue with the resolution, mine didn't change, but I've had to use the multiple display app that is a gui for xrandr to make mine behave better.

ugh can't seem to get it to work. It always resets when I restart.. =/
Something so simple should be easy imo xD hope it gets fixed sometime

---

