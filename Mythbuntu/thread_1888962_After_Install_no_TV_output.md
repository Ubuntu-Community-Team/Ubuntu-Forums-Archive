---
title: "After Install no TV output"
date: 2011-11-30
forum: Mythbuntu
---

### Post by svalvasori on 2011-11-30
Hi all,

Just decided to rid myself of WMC 7 and installed the latest Mythbuntu (11.10). During installtion, I have clear output on both my laptop screen and the TV. After the installation completes, I only have output on my laptop. I'm not sure exactly what information you need to help me troubleshoot, but here is a start.

NVIDIA GPU NB9M-NS
NVIDIA Driver 173.14.30

I can see DFP-2 (Denon) in the NVIDIA X Server Settings, which is what my TV is connected to but I only see 1 "screen"

My Xorg.conf:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Extensions"
	Option	"Composite"	"Disable"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"TVOutFormat"	"COMPONENT"
	Option	"TVStandard"	"HD480i"
	Option	"DPI"	"100x100"
	Option	"ConnectedMonitor"	"TV"
	Option	"NoLogo"	"True"
EndSection


I incorrectly set the TV resolution during install, which is why it says HD480i, but I would think it would still display that.

Any help would be greatly appreciated!

---

### Post by nickrout on 2011-12-01
try runnig nvidia-settings

---

