---
title: "ATI HD3850 - Gamma - QuakeWorld - EzQuake"
date: 2008-06-26
forum: Multimedia Software
---

### Post by MarkUK on 2008-06-26
Hi
Installed the latest 8.4s all seems well apart from a couple of horrid problems.

1 - I have to turn off Visual Effects to play a game as my screen flickers like mad :confused: Is this a bug with the new drivers , it also happens if i use the proprietary drivers.

2 - Games run fine apart from when playing for around 5 mins the gamma sets back to default (realy dark) even though the setting have not changed in the menu, just by nocking the gamma up a spot resets this for about 5 mins then i have to redo again :(.

Screen is a 19" wide connected via DVI not VGA.

> Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
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
	Option		"Composite"	"Enable"
EndSection


Is the correct driver installed for my card ? or is there a HD driver in the ATI package ?

Cheers
Mark

---

