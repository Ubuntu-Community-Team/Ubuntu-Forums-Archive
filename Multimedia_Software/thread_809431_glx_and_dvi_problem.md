---
title: "glx and dvi problem"
date: 2008-05-27
forum: Multimedia Software
---

### Post by ishkabob on 2008-05-27
Hi everyone.  I'm having a very strange problem with GLX.  If I connect my monitor using a dvi cable instead of a vga cable (dual-headed card obviously), anything that needs hardware acceleration causes my display to periodically go black for a few seconds.  For example, I connect using DVI, boot up and everything works fine, but when i start glxgears, my monitor starts to go black every 10 or so seconds.  Anyone have any ideas?  I've attached my xorg.conf:

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"macintosh"
	Option		"XkbLayout"	"us"
EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 Option "CorePointer"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ExplorerPS/2"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "true"
 Option "Buttons" "7"
 Option "ButtonMapping" "1 2 3 6 7"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
EndSection

```

---

### Post by ishkabob on 2008-05-28
bump

---

### Post by ishkabob on 2008-05-28
bump

---

### Post by ishkabob on 2008-06-04
bump

---

