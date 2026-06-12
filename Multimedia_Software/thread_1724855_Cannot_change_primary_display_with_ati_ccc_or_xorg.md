---
title: "Cannot change primary display with ati ccc or xorg.config"
date: 2011-04-08
forum: Multimedia Software
---

### Post by ajbelis23 on 2011-04-08
I have google'd the crap out of this and have yet to find a "solved" forum. I currently have 2 sapphire ati 5770's in xfire. I also have two monitors. My (preferred) primary display has a dvi input and my other display is hdmi. I have them both plugged into only one of the cards. For some reason it keeps setting the hdmi display as the primary. And I want them in extended view. The ATI CCC suite does not support changing the primary monitor and I have tinkered with the xconfig but I do not really know what I am doing, so I have ultimately not been successful. here is my xorg.config file. 

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP4"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	Option	    "Monitor-DFP4" "0-DFP4"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Configured Screen Device"
	Device     "Configured Video Device"
	SubSection "Display"
		Virtual   3600 1080
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3600 1920
		Depth     24
	EndSubSection
EndSection

``` 

Sorry if posted in the wrong section or there are answers out there. But like I said I couldn't find anything. Any help?:confused:

Thanks guys,
B-man

---

### Post by BicyclerBoy on 2011-04-09
What happens if you swap over the two monitor entries in the device section ?

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
        Option	    "Monitor-DFP4" "0-DFP4"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:2:0:0"
EndSection

---

