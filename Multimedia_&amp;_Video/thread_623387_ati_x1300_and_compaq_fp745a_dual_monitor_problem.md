---
title: "ati x1300 and compaq fp745a dual monitor problem"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by kickehy on 2007-11-25
Hey everyone, I have 7.10 running with a dell e193fp as my default monitor and am TRYING to run my compaq fp745a as my secondary display. I have an ati x1300 (which has way too many problems with any operating system....i know) and am using the restricted ati drivers. I DO NOT have compiz running (my compy is too old for it) and am using fglrx. I've tride using this post but it didn't work for me [http://ubuntuforums.org/showthread.php?t=592016]("http://ubuntuforums.org/showthread.php?t=592016") I've also tried using the built-in gui for using my other monitor but it just makes my screen all black upon reboot. Here's the output of my fglrxinfo:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

Here is my xorg.conf BEFORE I've tried using dual monitors:
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

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
	Option	    "Name" "Logitech USB RECEIVER"
	Option	    "Buttons" "10"
	Option	    "ButtonMapping" "1 2 3 6 7"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Dell E193FP"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Dell E193FP"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

Any ideas? Thanks for your help!

---

