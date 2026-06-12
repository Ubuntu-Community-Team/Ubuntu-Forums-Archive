---
title: "Video Playback Problems - Could it be a problem in the Xorg.conf file?"
date: 2008-08-23
forum: Multimedia Software
---

### Post by thermg on 2008-08-23
Hi All,

I managed to successfully install the ATI drivers for my X1950XT and got Compiz working fine.

I then proceeded to install VLC and test a video and the playback is very strange indeed. It flickers between the film and black within the player. Also when playing and the player is not the selected window the video overlays on to the top of the selected window:

[[IMG]http://img120.imageshack.us/img120/1319/screenshotzx5.th.png[/IMG]](http://img120.imageshack.us/my.php?image=screenshotzx5.png)


My xorg.conf file looks like:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "2"
	Option	    "Textured2D" "on"
	Option	    "TexturedXrender" "on"
	BusID       "PCI:1:0:0"
	Option		"XaaNoOffscreenPixmaps"                "true"

EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

And running fglrxinfo gives:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7873 Release
```

Is there something missing from my setup or are there other packages etc that I need to install. I believe I have installed all of the medibuntu packages. 

I am running Hardy Heron 64-Bit.

Many thanks in advance for your help.

Ross

---

### Post by shirilover on 2008-08-23
Compiz and video overlay do not play well together.
Try disabling compiz and see if playback improves.

---

### Post by thermg on 2008-08-25
Hi,

Thanks for that. Disabling Compiz did make a difference, no overlay on video playback. Is there a way to get both working nicely together? Maybe a different player perhaps?

---

