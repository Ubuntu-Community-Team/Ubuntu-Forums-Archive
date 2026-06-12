---
title: "Dual monitor config problems."
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by mig27 on 2007-03-03
After finally getting my wireless connection working, I've got round to getting dual monitors set up properly.

I have an ATI Radeon X1800XT as the video card, with a Belinea 2225S1 22" WS TFT (1680x1050) as the screen on the right, with an Acer AL1715 17" TFT (1280x1024) on the left.

I am trying to do this via the aticonfig options.

Current xorg.conf file (hopefully the only parts which are relevant, please let me know if more is needed and I'll post the rest):

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Left Screen" 0 0
	Screen         "Right Screen" RightOf "Left Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
	Identifier   "Acer AL1715"
	HorizSync    30.0 - 83.0
	VertRefresh  55.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Belinea WS 2225S1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "0 ATI Radeon X1800XT"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen	    0
EndSection

Section "Device"
	Identifier  "1 ATI Radeon X1800XT"
	Driver      "fglrx"
	Option 	    "VideoOverlay" "on"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Left Screen"
	Device     "0 ATI Radeon X1800XT"
	Monitor    "Acer AL1715"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Right Screen"
	Device     "1 ATI Radeon X1800XT"
	Monitor    "Belinea WS 2225S1"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection


Section "DRI"
	Mode         0666
EndSection
```

This results in both monitors working, but with the Acer (on the left physically) being on the right of the Belinea (on the right physically). Both screens are running at 1280x1024 aswell, I can't select a higher resolution on the 22" screen either.

Any idea what is going wrong? As I really want a dual screen setup working properly, with the Acer 17" running at 1280x1024 on the left, and the Belinea 22" at 1680x1050 on the right.

---

### Post by mig27 on 2007-03-03
Got it all fixed, correct resolutions and so on, now I just need to fix the icon on the second screen. It's showing up as a large block, pretty pixelated, difficult to describe.

Any ideas?

---

### Post by leodp on 2007-03-09
In the Device section add:

	option "SWCursor" "on"
	option "HWCursor" "off"

Leo

---

### Post by mig27 on 2007-03-09
That fixed the cursor itself, but caused other glitches whenever I scrolled or clicked a mouse button, would result in a mouse cursor being "left behind" and was even worse.

---

### Post by leodp on 2007-03-09
Yes, I see it also on my PC.
Sorry for not being able to help you, but I'm having problems with my card too.

I'm trying to get two separate desktops now (even if without 3D and dragging of windows between screens) but cannot get it.

Leo

---

### Post by mig27 on 2007-03-09
I'm just left with the block image for the mouse cursor on the second screen (or the click/scroll issues) which doesn't bother me that much since I mainly use the second screen for watching videos on, or for viewing reference material on, neither of which are that affected by the block cursor.

I got my config (nearly) working properly by using the dual head option for aticonfig, then modifying xorg.conf to fix resolutions and so on (can also be done via the screen resolution setting, will only work after the dualhead setup option).

Hopefully my xorg.conf file will be of help to you (removed irrelevant lines and have the options you suggested commented out to avoid more graphic problems):

```
Section "
	Identifier     "Default Layout"
	Screen         "Left Screen" 0 0
	Screen         "Right Screen" LeftOf "Left Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
	Identifier   "Acer AL1715"
	HorizSync    30.0 - 83.0
	VertRefresh  55.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Belinea WS 2225S1"
	HorizSync    30.0 - 83.0
	VertRefresh  55.0 - 75.0
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "0 ATI Radeon X1800XT"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "/etc/X11/xorg.conf" "Default Layout"
	BusID       "PCI:1:0:0"
#	Option	    "SWCursor" "on"
#	Option	    "HWCursor" "off"
EndSection

Section "Device"
	Identifier  "1 ATI Radeon X1800XT"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:1:0:0"
	Screen      1
#	option "SWCursor" "on"
#	option "HWCursor" "off"
EndSection

Section "Screen"
	Identifier "Right Screen"
	Device     "0 ATI Radeon X1800XT"
	Monitor    "Acer AL1715"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Left Screen"
	Device     "1 ATI Radeon X1800XT"
	Monitor    "Belinea WS 2225S1"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by cprofitt on 2007-03-22
I am having the same issues -- only after a clean install -- I did not have this issue when I first set this machine up... so I am not sure that the cause is.

I will post a solution if I can find one... I am on the hunt... then to configuring my wireless.

---

