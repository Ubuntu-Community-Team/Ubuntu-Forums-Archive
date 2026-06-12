---
title: "Ati Radeon 9500 &gt; 9700 Softmod"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by rocktorrentz on 2006-06-30
I have found various posts on the forums and around the internet on how to softmod my 9500 to a 9700 under linux using the xorg.conf file. However these are for different distros and older versions of ubuntu and my xorg.conf appears to be different. In the guides it says to do the following:
> 
#ADD
ChipID 0x4E44
#CHANGE
BusID "PCI:1:0:0" # vendor=1002, device=4e44


The problem is I have no line which looks like the line under '#CHANGE' in the above code in my xorg.conf. I have a BusID but not the rest. I have tried just adding the ChipID bit in my device section but it makes no difference to my glxgears fps. Does anyone know what I need to do in my Dapper xorg.conf? My device section looks like this:
> 
Section "Device"
	Identifier  "ATI Technologies, Inc. R300 AD [Radeon 9500 Pro]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection


Thanks
rocktorrentz

---

