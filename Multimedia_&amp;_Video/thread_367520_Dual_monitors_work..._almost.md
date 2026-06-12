---
title: "Dual monitors work... almost"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by SourceV on 2007-02-22
After many trial and error steps I have finally made it work. However, there are still one problems that I need to resolve in order to make it work as it should be.

The cursor on the primary screen (Laptop 1280x800) acts as it is on the external screen (19" 1280x1024), therefore if I enter it from the top of the external screen there is no problem, but if I enter it from the bottom of the external screen it misses the object by 224 pixels or less, depending on where exactly I entered.

I would appreciate if any one could assist me in resolving this. Thank you.

Here is information about my system:
Kubuntu 6.10 Running on Acer Aspire 5100 lapop
ATI Radeon Xpress 1100 chipset
External screen is Acer AL1917

```

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Acer AL1917"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Option "DesktopSetup" "horizontal,reverse" #Enable Big Desktop 
	Option "Mode2" "1280x1024" #Resolution for second monitor 
	Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO 
	Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work 
	Option "HSync2" "80" #This sets the horizontal sync for the secondary display. 
	Option "VRefresh2" "75" #This sets the refresh rate of the secondary display.
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "External Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor    "Acer AL1917"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

