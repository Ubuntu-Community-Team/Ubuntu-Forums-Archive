---
title: "openGL and ati problem after using Envy"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by djorzgul on 2007-06-03
Hello, this is the problem:
I installed ATI drivers via Envy, and everything worked fine.
In xorg.config it is listed correct:
[I]Section "Device"
	Identifier	"ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:3:0:0"[/I]


but when I try to run Apple's Shake 4.1 performance is unusable, and I get this message:
*Xlib:  extension "XFree86-DRI" missing on display ":0.0".*
which is the same message I get when I run *glxinfo |grep rendering*:
[I]Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No[/I]

so what is the catch, if someone can explain to me?
Thanks in advance.

dj.

---

### Post by Alex Fernandez on 2007-06-03
add this to the xorg.conf:

Section "Extensions"
Option "Composite" "0"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

then restart X (ctrl + alt + backspace) and test that its all working with fglrxinfo (should say OpenGL vendor string: ATI Technologies Inc.)

---

### Post by djorzgul on 2007-06-03
hmh,
I did everything and I get this now (:
[I]Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)[/I]

Here is the xorg.config file, in case I missed something since I am not very experienced ubuntuer:

> Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

	[B]Section "ServerFlags"
	Option "AIGLX" "off"[/B]
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

[B]Section "Extensions"
	Option "Composite" "0"
[/B]
EndSection



---

### Post by Alex Fernandez on 2007-06-03
Try changing that to: 
Option "Composite" "Disable"

For some reason (and I really have no idea) sometimes 0 doesnt work but Disable does, other times its other way round.

Secondly, did you install the Ubuntu xorg-driver-fglrx package, or did you install it from the ATi website via thier intaller file? (if its via the ATi site then make sure you have added fglrx to the restriected driver in /etc/default/linux-restricted-modules-common (sudo gedit /etc/default/linux-restricted-modules-common)

[http://ubuntuforums.org/showthread.php?t=221320&page=21](http://ubuntuforums.org/showthread.php?t=221320&page=21)

---

### Post by djorzgul on 2007-06-03
in restricted file I have just one entry:
DISABLED_MODULES="fglrx"
is that ok?

---

### Post by djorzgul on 2007-06-03
Ok, 
I replaced "0" with "Disabled" in xorg.config.
I removed this DISABLE_MODULES line from restricted thingy.
Rebooted, and voila, it works :D Thanks for all tips

for *fglrxinfo* I get nice:
[I]display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)[/I]

but for g*lxinfo |grep rendering* I get:
*direct rendering: No*???

and shake's interface is still slow as hell.

also when I run *fgl_glxgears*
I get errors:
[I]Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33[/I]

suggestions?

---

### Post by djorzgul on 2007-06-08
problem solved by following instructions on ubuntu wiki
[LINK]("http://https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

thanks for help one more time, and viva l'ubuntu :)

---

