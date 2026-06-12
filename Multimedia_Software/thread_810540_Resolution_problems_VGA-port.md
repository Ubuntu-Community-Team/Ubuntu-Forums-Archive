---
title: "Resolution problems VGA-port"
date: 2008-05-28
forum: Multimedia Software
---

### Post by mikael_b on 2008-05-28
Hi,

I have just bought a 40" Samsung LCD and would like to connect it to my computer. The only problem is that while I connect it with a VGA cable and then go in to nvidia-settings the maximum resolution that I can set is 640x480. The wired thing is that during the startup and shutdown (while ubuntu is loading) it change into the correct resolution but when the log on screen is shown it has disconnected the TV, then when I try to activate I can't select the correct resolution.

This is my xorg.conf

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by mrtomservo on 2008-05-28
Well, I know that for standard analog TV, 640 by 480 is the norm.  What type of video card do you have?  If you don't know, could you type:

```
lspci | grep VGA
```

and post the output here?  There is very likely a setting you should be able to change to achieve your required output.  Do you know what resolution your tv supports?

---

### Post by mikael_b on 2008-05-28
> ~$ lspci | grep VGA
05:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)

The tv name is Samsung LE-40M86BD and I think that the resolution should be  1920x1080   for that model.

---

### Post by mikael_b on 2008-05-30
Anyone?

---

### Post by mrtomservo on 2008-05-30
Well, i'm just taking guesses here... but have you tried adding resolutions by hand in your xorg.conf?  (Back up your xorg.conf before editing it by hand) For instance, under section "Screen" adding something like this: (with resolutions you're sure your tv can support)

Section "Screen"
Identifier "Default Screen"
Device "nVidia"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Viewport 0 0
Depth 24
[B][I]Modes "1600x1200" "1600x1024" "1440x900" "1400x1050" "1360x768" "1280x1024" "1280x960" "1280x800" "1280x720" "1152x864" "1024x768" "800x600" "640x480"
[/I][/B]EndSubSection 
EndSection

---

