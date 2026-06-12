---
title: "Big Desktop big problem!!!"
date: 2006-02-24
forum: Multimedia &amp; Video
---

### Post by adam.tropics on 2006-02-24
Ok, so there are countless posts up here about this, but I'm not getting anywhere, so here's another one.

I have a toshiba laptop, running an ati radeon xpress 200m with ubuntu, and it all works perfectly fine. However, I have somehow accumulated an extra 17" crt monitor and am trying to get Big Desktop to run. I have seen that the fact that my laptop is widescreen creates a slight problem in the sense of keeping the whole desktop 'rectangular', so my thought was to use a vertical setup, with the laptop at 1280*800, and thew crt at 1280*1024. I thought this would fix it. Now having read and tried from so many posts, my xorg.conf is now a bit of a mess and Big Desktop is not there yet. I get both monitors on (laptop as primary) and if i move the mouse to the absolute bottom of the screen i can see the pointer at the absolute top of the crt,but that's it and the crt is not showing anything else. I was able to get it working as a horizontal desktop, however screen resolution ruined that so I want the vertical. Help!!!!

My xorg.conf, (mess that it is!!!)

[HTML]
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	ModeLine     "1280x800@60" 83.9 1280 1312 1624 1656 800 816 824 841
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 1"
	HorizSync    30.0 - 71.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "DesktopSetup" "vertical"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 1"
	Driver      "fglrx"
	Option	    "MonitorLayout" "LVDS,AUTO"
	Option	    "HSync2" "30-71"
	Option	    "VRefresh2" "50-160"
	Option	    "Mode2" "1280x1024"
	Option	    "EnablePrivateBackZ" "yes"
	Option	    "UseInternalAGPGART" "off"
	Option	    "DesktopSetup" "vertical"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 1"
	Device     "ATI Graphics Adapter 1"
	Monitor    "aticonfig Monitor 1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection[/HTML]

---

### Post by adam.tropics on 2006-02-25
Progress. All now fine except the screen resolution. I can select 1280*1600 but I am after 1280*1824.(1280*800 screen above 1280*1024 screen) It seems to assume I have two identical screen resolution requirements. I have specified in xorg.conf the individual resolutions, but how can i manually specify the combined resolution????

---

