---
title: "Refresh rates &amp; Co"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by PartisanEntity on 2007-04-10
I am a little confused concerning certain sections of my xorg.conf file. I have a laptop to which I also have attached a TFT monitor. My graphics card is an Nvidia GeForce Go 6200.

Here are the relevant sections of my xorg.conf in colour coding which questions posted below:
```

[COLOR="Red"]Section "Monitor"[/COLOR]
    Identifier     "Generic Monitor"
[COLOR="DarkOrange"]    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0[/COLOR]
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40M? [GeForce Go 6200]"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
[COLOR="RoyalBlue"]    Option "UseEdidFreqs" "True"[/COLOR]
    Option "MetaModes" "CRT: 1680x1050, DFP: 1280x800"
    Option "UseDisplayDevice" "CRT, DFP"
    Option "ConnectedMonitor" "CRT, DFP"
EndSection
```

To what does the [COLOR="Red"]red[/COLOR] section apply? (To my laptop LCD or the TFT or both?)

Does the [COLOR="DarkOrange"]orange[/COLOR] apply to both my laptop lcd and the attached TFT?

What does the [COLOR="RoyalBlue"]blue[/COLOR] section mean and to which display does it apply?

I am asking these questions because I would like to make sure my TFT monitor uses the correct refresh rates.

Sometimes I notice a very faint flickering on the TFT monitor, it is more easily noticeable on grey colours, since this is a brand new TFT monitor I am worried that I might have it running on incorrect refresh rates.

I am a bit of a newb when it comes to display settings, so please give me the data step by step :)

Thanks in advance.

---

### Post by PartisanEntity on 2007-04-10
Oh and I forgot to mention that I am using an analog connection because my laptop doesn't h ave DVI.

---

### Post by PartisanEntity on 2007-04-11
bump

---

### Post by hardyn on 2007-04-11
red applies to monitor 0, or the laptop display.
addional montoirs will be montor 1, or whatever you choose to call them.

yellow, just to monitor 0

blue is a driver specific setting, and it it up to nvidia. it may addess both monitors.


for example, here is my xorg.conf file

```
 
Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
    	VendorName	"NVIDIA Corporation"
    	BoardName	"GeForce Go 6600"
	Option		"AddARGBGLXVisuals"	"True"
	Option          "AllowGLXWithComposite" "True"
	Option		"NoLogo"		"True"
	Screen		0
EndSection

Section "Device"
	Identifier     "Videocard1"
	Driver         "nvidia"
	BusID          "PCI:1:0:0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce Go 6600"
	Screen          1
EndSection

Section "Monitor"
	# HorizSync source: edid, VertRefresh source: edid
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "LPL"
	HorizSync       30.0 - 75.0
	VertRefresh     60.0
	Option         "DPMS"
EndSection

Section "Monitor"
	# HorizSync source: builtin, VertRefresh source: builtin
	Identifier     "Monitor1"
	VendorName     "Unknown"
	ModelName      "TV-0"
	HorizSync       28.0 - 33.0
	VertRefresh     43.0 - 72.0
	Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1680x1050_60 +0+0; 1280x1024 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by PartisanEntity on 2007-04-11
Thanks for the info.

I just used the Nvidia settings application to give the TFT and the LCD seperate X screens.

Then I told the Nvidia settings application to write the changes to the X configuration file, and it also added the correct refresh rates.

Upon restarting this annoying and very light flicker I kept seeing in the background on certain colours is gone from the TFT.

:)

---

