---
title: "Reversing dual screen order w/ twinview?"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by SanguineIllusion on 2006-11-12
Ok so I have 2 19" DVI LCDs that I got working in windows but not so much in Ubuntu. I've gotten so close but for some reason its treating the right monitor as the primary instead of the left. So when I scroll off the right side of my right monitor, the cursor appears on the left side of my left monitor.

I need help reversing the order in xorg.conf. Any help is appreciated. Her'es my xorg.conf devices section:

Section "Device"
	Identifier	"nVidia 7800GT"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"UseFBDev"		"true"
	Option		"TwinView"		"True" 
	Option 		"TwinViewOrientation" 	"RightOf" 
	Option 		"UseEdidFreqs" 		"True" 
	Option 		"MetaModes" 		"1280x1024,1280x1024; 1024x768,1024x768"
	Option		"UseDisplayDevice"	"DFP"
	#Option		"TwinViewOrientation"	"RightOf"
	#Option		"ConnectedMonitor"	"DFP-1,DFP-0"
	
EndSection

Section "Monitor"
	Identifier	"L90D+"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Those two commented options are things I've already tried that won't work. Any help would be greatly appreciated.

---

### Post by robertmcox on 2006-11-12
Excuse me if I'm missing something obvious, but why can't you just reverse the 2 DVI cables?

---

### Post by SanguineIllusion on 2006-11-12
I'm trying to avoid doing that because I primarily use windows XP and I have it set up properly on there with the current dvi cable configuration. This may make me sound lazy though, but with nview on XP, its kind of picky and gets "confused" easily so I would prefer not changing the dvi cables and just finding out from somebody who knows better than I do how to switch the monitors w/ twinview.

---

### Post by kdawg on 2006-11-12
Maybe if you post the entire xorg.conf I could try to help... I'm still slightly new at this too though, but from what I see, what you posted has the line 
```
Option "TwinViewOrientation" "RightOf"
```
In the device section and commented at the end, I may just be confused though, but try changing that to "LeftOf" ......  

well, thats my 2 cents worth!

---

### Post by SanguineIllusion on 2006-11-13
Sorry it took me so long to get back to you. I haven't had the opportunity to get back to ubuntu till now. LeftOf and RightOf produce the same result, right screen displaying the left video and vice versa. Heres my full xorg.conf:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia 7800GT"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"UseFBDev"		"true"
	Option		"TwinView"		"True" 
	Option 		"TwinViewOrientation" 	"RightOf" 
	Option 		"UseEdidFreqs" 		"True" 
	Option 		"MetaModes" 		"1280x1024,1280x1024; 1024x768,1024x768"
	#Option		"UseDisplayDevice"	"DFP"
	Option		"TwinViewOrientation"	"LeftOf"
	#Option		"ConnectedMonitor"	"DFP-1,DFP-0"
	
EndSection

Section "Monitor"
	Identifier	"L90D+"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia 7800GT"
	Monitor		"L90D+"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Any ideas?

---

### Post by SanguineIllusion on 2006-11-13
OMG, I feel so stupid. I didn't realize that RightOf was farther up in the file and that I was adding a second one. I fixed the right of up above and it worked!

Small question though: is there any way to span the toolbar things across both monitors instead of just one? Right now its only on my right monitor.

---

