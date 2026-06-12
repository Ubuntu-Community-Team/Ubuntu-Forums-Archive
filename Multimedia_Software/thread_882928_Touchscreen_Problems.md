---
title: "Touchscreen Problems"
date: 2008-08-07
forum: Multimedia Software
---

### Post by ew16301 on 2008-08-07
I have a Megavision Mv155 touchscreen with Ubuntu hardy. Ive done fresh reformat and im trying to get the touchscreen to work with linux. Ive tried tons of things and i still cant get it to work (mutouch, egalax, evtouch, microtouch). The closest I have gotten is where the screen moves the mouse to the bottom left corner of the screen everytime I touch it, and ive gotten it to click when I touch it, but not move (Only clicks where the cursor is currently located). Ive noticed the devices mapped to the touch screen also respond differently when placed in the xorg (/dev/input/eventX) (/dev/usb/hiddev0). Here is my current xorg.conf where the mouse moves to the bottom left corner. Any help would be greatly appreciated, as im trying to setup a mediacenter with Boxee on a bluetooth network .

```
ection "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
     Identifier "EETI"
     Driver    "egalax"
     Option    "Device"    "usbauto"
     Option     "Parameters" "/var/lib/eeti.param"
     Option     "ScreenNo"   "0"
     Option "MoveLimit" "5"
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
	InputDevice	"Synaptics Touchpad"
  	InputDevice     "EETI" "SendCoreEvents"
EndSection
```

---

### Post by kurtpetrey on 2008-08-25
Do you have the cd that came with the Monitor?  I just purchased this monitor and the cd is cracked.  I would really appreciate it if you could email me the software or if you could upload the data somewhere that I can download it.  

Kurt

---

