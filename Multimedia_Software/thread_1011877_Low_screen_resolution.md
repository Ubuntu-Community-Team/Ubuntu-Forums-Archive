---
title: "Low screen resolution"
date: 2008-12-15
forum: Multimedia Software
---

### Post by carloshiga on 2008-12-15
Hi,

I have installed Ubuntu 8.10 but I can't get a screen resolution higher than 840x480. My video card is a Nvidia GeForce4 MX 4000. The driver seems to be working fine. Here is my xorg.conf:

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

I tried to put this:

```

SubSection "Display"
		Depth		24
		Modes		"800x600" "1024x768"
EndSubSection

```

in the "Screen" section but nothing happens. Any idea?

---

### Post by IQRules on 2008-12-15
Here is what I have.

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
                Virtual 2384 768
        EndSubSection
EndSection

---

