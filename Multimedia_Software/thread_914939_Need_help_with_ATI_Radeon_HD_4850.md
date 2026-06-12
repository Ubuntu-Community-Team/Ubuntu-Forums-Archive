---
title: "Need help with ATI Radeon HD 4850"
date: 2008-09-09
forum: Multimedia Software
---

### Post by zami on 2008-09-09
**CORRECTION!  It's a 3850, not a 4850**  I can't figure out how the change the title though.

I seem to be having trouble with my ATI card.  (I'm only *guessing* it's the card but it sounds like some of these problems are common to ATI.)

-screensavers lock up instead of closing when I "wake" my computer, requiring a CTRL+ALT+Backspace (X server restart?)

-launching some programs (especially anything via Crossover Games - and I mean the problem begins at the Crossover menu, haven't actually launched anything 3d yet) results in the screen going *all* wonky, looking like the image has been busted into a thousand mosaic tiles and scattered across my screen.  This too needs a CTRL+ALT+Backspace

-if I actually enable Compiz effects, randomly the screen will go all white or all black.  Another CTRL+Alt_Backspace

So!  My question is... is this worth pursuing?  Are my problems caused by something I have/have not done or is this purely an ATI issue?

(I should add, I don't think this is a problem with the physical card, because I dual-boot and the card performs fine in Windows.)

Details

Drivers: I installed via EnvyNG (after two disastrous attempts at installing manually) with envyng-core, envyng-gtk (and other packages auto chosen) installed via Synaptic.
When I look in "Hardware Drivers" it says my ATI driver *is* in use but *not* enabled.  (The enabled box is not checked, the in use light is green.)  Last time I "enabled" the driver through this program I got nothing but a white screen past log-in.  I now fear it.

Video Card: ATI Radeon HD 3850 "Sapphire" 

OS: Ubuntu 8.04 (all updated)

System: 2.0GiB memory, 3GhzIntel Pentium 4 

Xorg.conf

Section "Screen"
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
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection



Any help appreciated!
Thanks
-zami

---

### Post by zami on 2008-09-09
I've messed around more with manual install via these instructions
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) (proprietary)
and these as well
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) (open source)

Still get an all black or all white screen, and end up just logging into a failsafe terminal and running "sudo envyng -g", just so I can get back to browsing for further help.

More info - 

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850
OpenGL version string: 2.1.7659 Release

looks good to me...

Is it possible this is a Compiz issue, not ATI or something I've done/not done?

-zami

---

