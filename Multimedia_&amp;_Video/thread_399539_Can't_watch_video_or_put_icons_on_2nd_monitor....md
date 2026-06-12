---
title: "Can't watch video or put icons on 2nd monitor..."
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by randalotto on 2007-04-02
Hi,

I've tried searching around, but haven't been able to find a solution.

So I have a dual monitor setup running that works for the most part. I can move windows between the monitors, get them to maximize in each, etc... I followed the "BigDesktop" instructions found [here]("http://ubuntuforums.org/showthread.php?t=221174") and [here]("http://www.ubuntuforums.org/showthread.php?p=1773544"). 

I have two main problems:

1. I can't put icons, folders, or files on the second desktop. It just sits there, blank... Oddly, I CAN put the KDE launcher panel on the second monitor. Even then, however, all of the files and such remain only on the first monitor. If I try moving it over to the 2nd monitor, it just goes to the edge of the 1st.

2. I can't play video on the second monitor, or away from my mouse on the first... Alot of times, I'd like to be working in one monitor with something playing in the other. If I launch a video in the first monitor, in whatever player, and move my mouse over to the 2nd monitor, the video "slides" out of the player. If I only move a little onto the other screen, I get half a video... Don't really know how else to explain that one.

Anyway, I'm running the fglrx driver on an ATI Radeon X800 GTO2. here's my xorg.conf (with some of the irrelevant stuff cut out, like mouse...)

> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"	
	BusID       "PCI:5:0:0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option 	    "DesktopSetup"  "horizontal" #Enable Big Desktop
	Option 	    "Mode2"         "1280x1024" #Resolution for second monitor
	Option 	    "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
	Option 	    "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
	Option 	    "HSync2" "65" #This sets the horizontal sync for the secondary display. 
	Option 	    "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"	
	BusID       "PCI:5:0:0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option 	    "DesktopSetup"  "horizontal" #Enable Big Desktop
	Option 	    "Mode2"         "1280x1024" #Resolution for second monitor
	Option 	    "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
	Option 	    "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
	Option 	    "HSync2" "65" #This sets the horizontal sync for the secondary display. 
	Option 	    "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection


Thanks for any help.


Randy

---

### Post by randalotto on 2007-04-03
Anyone?

---

### Post by randalotto on 2007-04-04
So the icons thing seems to be KDE specific, but the video thing happens in Gnome or KDE. Does no one have any advice for me?

---

### Post by randalotto on 2007-04-11
So no one has any clue? I'd really like to get this working...

---

### Post by randalotto on 2007-04-17
One more appeal for help... anyone?

---

### Post by redwheelbarrow on 2007-05-22
I hope you accidentally pasted your xorg.conf twice... **cause there's doubles of everything.** You should fix that.

No cure for #1, it's just a really interesting bug. Fill out a comment form on ati.com

For #2 You could try turning Option "VideoOverlay" "off" and Option "OpenGLOverlay" "on", and switching the output of your video player to OpenGL. 
Or setting Option "EnablePrivateBackZ" "no".

---

