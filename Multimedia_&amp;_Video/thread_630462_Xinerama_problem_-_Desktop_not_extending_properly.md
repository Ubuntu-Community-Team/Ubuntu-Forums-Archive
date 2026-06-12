---
title: "Xinerama problem - Desktop not extending properly"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by benmoss on 2007-12-03
I've looked through the archives quite a bit, but I haven't found anyone with the same problem as me.

I have a Dell laptop (with Intel video card) connected to a docking station.  I have two LCD monitors - one using the analog output of the docking station, and the other using the digital output.  Xinerama was working perfectly for me in 7.04 to extend my primary desktop onto the second LCD.  However, after upgrading to 7.10, I have a problem.

My desktop is not extending.  On my secondary LCD, I do have a background color, and I can move my mouse around on the second screen.  But I cannot drag a window from my primary screen to the secondary one.  This makes me think that in my xorg.conf file, I have properly told it that the screen exists, but maybe Xinerama itself isn't enabled.  I have followed the directions in a couple of the Xinerama howto's and nothing has worked so far.

Thanks in advance!

Here is my xorg.conf:
```


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
	Load	"i2c"
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


# Section "Extensions"
# Option "Composite" "Enable"
# EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"dvorak"
EndSection


Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ImPS/2"
	Option "Emulate3Buttons" "true"
	Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "0"
EndSection

Section "Device"
	Identifier "intel0"
	Driver "i810"
	BusID "PCI:0:2:0"
	Option "MonitorLayout" "CRT,DFP"
	#VideoRam 131072
	Screen 0
	#Option "DevicePresence" "true"
	Option "DDCMode" "true"
	# Option "ForceBIOS" "800x600=1400x1050"
	# Option "FlipPrimary" "true"
EndSection

Section "Device"
	Identifier "intel1"
	# Option "Rotate" "CCW"
	Driver "i810"
	BusID "PCI:0:2:0"
	Screen 1
	#Option "DisplayInfo" "false"
	Option "DDCMode" "true"
	Option "MonitorLayout" "CRT,DFP"
	#Option "DevicePresence" "true"
	# Option "ForceBIOS" "1920x1440=1920x1200"
	# Option "FlipPrimary" "true"
EndSection

Section "Monitor"
	Identifier "LCD1"
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier "LCD2"
	Option "DPMS"
	# Modeline "1280x1024" 114.98 1280 1312 1744 1776 1024 1045 1055 1076
	# DisplaySize 519 324
	# HorizSync 30-81
	# VertRefresh 60-60
	# Modeline "1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

Section "Screen"
	Identifier "Screen1"
	Device "intel0"
	Monitor "LCD1"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device "intel1"
	Monitor "LCD2"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Xinerama"
	Screen 0 "Screen1" 0 0
	Screen 1 "Screen2" RightOf "Screen1"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "Synaptics Touchpad"
	Option "Xinerama" "true"
EndSection

Section "DRI"
	Mode 0666
EndSection

```

---

