---
title: "Radeon 7000: fine with sub-D, resets with DVI"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by orbister on 2007-06-21
Hi Folks,

I am running Ubuntu 7.04 on an IBM Netvista 8318. I have just installed an ATI Radeon 7000 (lspci ->  ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]) card with the "radeon" driver.

It seems to be working fine, as long as I use the analogue sub-D connection to my Hyundai L72D screen. If I try the DVI-D connector, it still works but some applications appear to reset the screen (goes black, small 'click' from the speakers. restarts a second or two later) every time I close a window. Thunderbird does it. Firefox doesn't. Openoffice.org word processor does it, but the spreadhseet doesn't. A terminal window doesn't.

It makes the machine unusably irritating, so I am back to b-o-o-ring old analogue. Anybody got any bright ideas about sorting it?

xorg.conf includes

Section "Device"
	Identifier	"ATI Radeon 7000"
	Driver		"radeon"
	BusID		"PCI:2:1:0"
        Option          "UseFBDev" "True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Ian

---

