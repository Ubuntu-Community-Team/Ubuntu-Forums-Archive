---
title: "Dual Monitors - Radeon7000 - Default Install"
date: 2006-04-05
forum: Multimedia &amp; Video
---

### Post by Industrial PhD on 2006-04-05
I'm not sure if this is the right forum for this but since I'm fairly new to Ubuntu, I'll give it a try.

I have just installed the Breezy Badget onto my PC. I have a Radeon 7000 card, with 1 DVI port and 1 DSUB port, both are plugging into their own Dell 1703FP monitor. Right now I'm getting mirrored displays (Same thing on both monitors)

Lspci gives me:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

This box does not have internet access at this time, due to domain / firewall authentication issues that I am working on (my IT department is slow), but I'd like to get the dual monitor configured in the meantime. I have just the base install, so if Breezy doesn't install it by default, I don't have it.

Every walkthrough I've found on here is for nVidia, but of the new ATi one's I've found call out something called 'aticonfig' which I can't seem to find using 'locate' at a terminal prompt.

Is there a walkthrough out there somewhere that can help me? If not, is this aticonfig package something I can download somewhere else and drop onto my system and install from there, or is it only apt-get?


Thanks,
Indy

---

### Post by Industrial PhD on 2006-04-05
Just for kicks, here's the xorg.conf file.

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 1703FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
	Monitor		"DELL 1703FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thanks,
Indy

---

### Post by Apache777 on 2007-01-30
Hey buddy, I've got the same card.  My xorg.conf for this device is:

```
#*****ATI7000*****
Section "Device"
	Identifier  "ati7000[0]"
	Driver      "ati"
	BusID       "PCI:3:2:0" 
EndSection

Section "Device"
	Identifier  "ati7000[1]"
	Driver      "ati"
	BusID       "PCI:3:2:0"
	**Screen      1**
EndSection
```

And dual head is working for me :-) Try something like this and it should be fine. 
Apache:guitar:

---

