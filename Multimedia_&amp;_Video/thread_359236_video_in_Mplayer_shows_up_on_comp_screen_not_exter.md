---
title: "video in Mplayer shows up on comp screen not external"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by nelio2k on 2007-02-11
Hi all,
I set up Ubuntu fine. I can watch DVDs and other video files such as AVIs without problem on my computer. However, when I mirror my screen onto the external monitor, everything works fine except when I'm playing a movie. The movie will be playing fine on my laptop screen (even within the mplayer window), but the external monitor wouldn't show the movie inside the mplayer window, but it would be blank. I tried to reboot it again with only external display and the laptop monitor inactive, but it would still not show the video up on the external display. I hear sound and everything seems to work fine. I'm not even dual-monitoring, but merely mirroring what's on my display to the monitor. 
I have a IBM Thinkpad R32, with ATI Mobility Radeon M6 LV. 

Here's my Xorg.conf file. (Only the Device and Screen section, which I think matters the most)
Any help is greatly appreciated!

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option	    	"VideoOverlay" "on"
	Option		"EnableDepthMoves" "true"
EndSection


Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by PrawnHead on 2007-02-22
Did you get a solution on this? I have a Dell Insipiron 4100 (same video card) with the same issue. Thanks.

---

### Post by nelio2k on 2007-02-22
naw, no one really replied... i have no clue either.

---

