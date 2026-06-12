---
title: "[SOLVED] GDM refresh rate inconsistent with Gnome"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by samjh on 2007-11-07
[SIZE="5"]Problem solved![/SIZE]

I ran:```
sudo nvidia-settings
```
[list][*]Go to X Server Display Configuration.
[*]Manually specify refresh rate to 85 Hz (default setting is Auto).
[*]Choose Save to X Configuration File.
[*]Quit, and restart.[/list]

=====================

**Original post**

I've had this problem since Gutsy release, and it's about time it was solved.

I am running Ubuntu Gutsy (Gnome edition) with Nvidia driver enable via Restricted Drivers Manager.  The driver package is nvidia-glx-new.  Graphics card is an Nvidia GeForce 7600GT plugged into a Samsung Samtron 75E monitor.

In Edgy and Feisty, the GDM login screen resolution and refresh rate matched the corresponding Gnome desktop settings: ie. 1024x768 @ 85 Hz.  But in Gutsy, the GDM refresh rate drops to 60 Hz.

This is not a problem when I'm using the open source Xorg driver.  Only when I use the restricted Nvidia driver does GDM differ in its refresh rate.

I have been working around this using the Screen and Graphics applet and manually choosing my monitor to the closest possible match (Samsung Samtron 75M(E) Plus), but it doesn't recognise the fact my monitor supports up to 120 Hz, the supported refresh rate drops to 70 Hz.  Interestingly if I do this, the GDM refresh rate is 85 Hz!

Something really weird is going on here.  Can someone please help get my GDM to respect the 85 Hz refresh rate, with Nvidia restricted driver installed, and without using the quirky work-around that I've just posted?

Here are the relevant sections of my xorg.conf file:
```
Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"

EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

