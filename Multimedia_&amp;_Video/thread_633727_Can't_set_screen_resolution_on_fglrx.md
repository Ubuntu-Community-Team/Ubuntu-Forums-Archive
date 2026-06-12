---
title: "Can't set screen resolution on fglrx?"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by tofuoni on 2007-12-06
First - thanks to the people who write howtos and answer questions in these forums.  Thanks to you guys, I'm pretty much all set up!

My last little problem is that I can't figure out how to change the display resolution on my middle monitor.  My xorg.conf is posted below.  I have three monitors.  From the left to the right, the first two are on the fglrx driver.  They are the two heads on an Radeon card.  My problem is, how do I change the display resolution for just one of them??  As you can see in my config, I have tried to set the resolution to 1680x1050 for screen1, but it doesn't take.

Thanks in advance for any advice!

```

Section "Module"
	Load           "glx"
	Load           "GLcore"
EndSection
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         0 "screen0"
        Screen         1 "screen2" RightOf "screen0" 
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	Option         "Xinerama" "true"
EndSection

#--------------------------------------------------
Section "Device"
	Identifier  "ati head 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "NoLogo" "True"
	Option	    "AllowGLXWithComposite" "True"
	Option	    "DesktopSetup" "horizontal"
EndSection

Section "Device"  
	Identifier  "ati head 1"
	Driver      "fglrx"
	BusID       "PCI:1:0:1"
EndSection

Section "Device"
	Identifier  "nvidia"
	Driver      "nv"
	VendorName  "RIVA"
	BoardName   "RIVA TNT2"
	BusID       "PCI:2:4:0"
	Option      "DesktopSetup" "horizontal"
EndSection


#--------------------------------------------------
Section "Monitor"
	Identifier   "monitor0"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "monitor1"
	Option	    "DPMS"
EndSection

Section "Monitor"  
	Identifier   "monitor2"
	Option	    "DPMS"
EndSection


#--------------------------------------------------
Section "Screen"
	Identifier "screen0"
	Device     "ati head 0"
	Monitor    "monitor0"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1024x768"
	EndSubSection
EndSection

Section "Screen" 
	Identifier "screen1"
	Device     "ati head 1"
	Monitor    "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Screen" 
	Identifier "screen2"
	Device     "nvidia"
	Monitor    "monitor2"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1024x768"
	EndSubSection
EndSection


#--------------------------------------------------
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection




```

---

### Post by tofuoni on 2007-12-08
I'd like to indulge myself with a bump...

Anyone have any ideas on this?

---

