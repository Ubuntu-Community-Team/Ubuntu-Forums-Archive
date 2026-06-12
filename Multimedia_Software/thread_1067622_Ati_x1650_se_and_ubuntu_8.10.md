---
title: "Ati x1650 se and ubuntu 8.10"
date: 2009-02-12
forum: Multimedia Software
---

### Post by rickrob on 2009-02-12
Got the new ati driver installed from the ati site and running compiz.But my video flicker in vlc and totem are driving me insane.But even more imp is the video seems to lag even in firefox.Ex:Tabs are really slow to switch this is my xorg.conf. Any ideas?


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
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
	Option	    "TexturedVideo" "on"
	BusID       "PCI:2:0:0"
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

---

### Post by Siggma on 2009-02-23
> **rickrob said:**
> Got the new ati driver installed from the ati site and running compiz.But my video flicker in vlc and totem are driving me insane.But even more imp is the video seems to lag even in firefox.Ex:Tabs are really slow to switch this is my xorg.conf. Any ideas?

You can partially correct the flicker by running:
gstreamer-properties
Select the video option that works correctly.

You can get reasonable video by installing smplayer. It even has a special mode for the fglrx driver in the repository. However it does not fix the tearing.

Short answer: no, it's an ongoing issue that there seems to be no way to correct, at least if you believe ATI.

However, Ubuntu video performs flawlessly in a Vbox under windows so it has to be the ATI driver. I too have gone round and round with this issue. I strongly suspect that ATI is deliberately dragging their feet. It's been over a year and they have still not implemented a working sync to refresh. The options remain in the configuration and in the Catalyst control panel but have no effect whatsoever in the driver. Personally I think they are in "bed" with Bill Gates in terms of attempting to corner the market and prevent the proliferation of publicly supported software like Ubuntu for as long as possible. I think it's a political move, not a technical move. It takes but a few lines of code to implement sync to refresh which would stomp the tearing in a heartbeat. It does not take an entire year to implement.

Feedback to ATI can be posted at [phoronix forums]("http://www.phoronix.com/forums/") where you can read the tireless list of excuses from Bridgman (the ati rep)to  your hearts content.

-Another frustrated ATI X1650 owner.
P.S. This card has an R530 chipset.

---

