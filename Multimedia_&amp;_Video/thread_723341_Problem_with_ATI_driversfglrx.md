---
title: "Problem with ATI drivers/fglrx"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by Max Carey on 2008-03-13
I recently upgraded from Feisty (7.04) to Gutsy (7.10) and ran into some problems that I think are graphics card related.  Boots up fine, but when I get to the Ubuntu login screen, it flashes momentarily, takes a second to reload, and then repeats that cycle over and over. I tried reconfiguring xorg.conf several times, even using vesa instead of the default ati, but it didn't fix the problem. So I manually installed ATI's fglrx driver using this guide:  [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

After running aticonfig --initial and rebooting, fglrxinfo outputs
```
Error: unable to open display (null)
```

and of course I get the same problem with the login screen.  fglrx is listed when I run lsmod and dmesg. /var/log/Xorg.0.log has no error (EE) messages. My xorg.conf is:
```
Section "Files"
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
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"DELL M993c"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"DELL M993c"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

Anybody have any ideas as to what could be going on? I don't know why fglrxinfo doesn't work, or if I'm even on the right track to fixing my login screen problem.

---

### Post by Max Carey on 2008-03-13
bump

---

### Post by Max Carey on 2008-03-15
No ideas? Anyone?

---

