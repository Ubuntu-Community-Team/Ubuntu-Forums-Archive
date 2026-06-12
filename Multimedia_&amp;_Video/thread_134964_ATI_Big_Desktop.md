---
title: "ATI Big Desktop"
date: 2006-02-22
forum: Multimedia &amp; Video
---

### Post by zachtib on 2006-02-22
OK, this has been giving me a headache for a while,
I've followed the guide here: [http://gentoo-wiki.com/HOWTO_Dual_Monitors#With_the_proprietary_binary_driver](http://gentoo-wiki.com/HOWTO_Dual_Monitors#With_the_proprietary_binary_driver)

but no luck, in gdm, i can move my mouse over to the second screen, but once I log on, I cannot

My setup is this:

IBM Thinkpad with Radeon Mobility 9000

Laptop's LCD does 1400x1050

To the left of my thinkpad is a 19" LCD, running at 1280x1024
Currently, I can't get the secondary monitor to the LEFT of the main screen, it always shows up to the right (I would just physically move the LCD, but the llayout of my desk won't allow it)

Here's my current xorg.conf: (I know, its ugly)
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      1  "aticonfig Screen 1" 0 0
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

##	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
##	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dri"
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
	Identifier   "aticonfig Monitor 1"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 1"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 1"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "DesktopSetup" "horizontal"
	Option	    "UseInternalAGPGART" "off"
	Option	    "MonitorLayout" "LVDS,AUTO"
	Option	    "EnablePrivateBackZ" "yes"
	Option	    "Mode2" "1280x1024"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
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
EndSection


```

If anyone knows how to fix this, I'd appreciate it

---

