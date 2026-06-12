---
title: "ATI Extended Plasma TV Desktop"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by CulleyS on 2007-09-22
Section "Device"
	Identifier	"ATI Radeon X800 PCIe1"
	Driver		"ati"
	BusID		"PCI:5:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "Monitor Layout"          "LCD, CRT"
        Option          "CRT2Postion"             "RightOf"
        Option          "MetaModes"               "1600x1200-1900x1080"
        Option          "MergedXinerama"          "on"
        Option          "MergedNonRectangular"    "true"
        Option          "MergedFB"                "true"
        Screen          0
EndSection

Section "Device"
	Identifier	"ATI Radeon X800 PCIe2"
	Driver		"ati"
	BusID		"PCI:5:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "Monitor Layout"          "LCD, CRT"
        Option          "CRT2Postion"             "RightOf"
        Option          "MetaModes"               "1600x1200-1900x1080"
        Option          "MergedXinerama"          "on"
        Option          "MergedNonRectangular"    "true"
        Option          "MergedFB"                "true"
        Screen          1
EndSection

Section "Monitor"
	Identifier	"Dell 2001FP"
	Option		"DPMS"    "true"
        Option          "NoDDC"
	HorizSync	30-80
	VertRefresh	56-76
EndSection

Section "Monitor"
	Identifier	"Plasma TV"
	Option		"DPMS"    "true"
        Option          "NoDDC"
	HorizSync	30-80
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Radeon X800 PCIe1"
	Monitor		"Dell 2001FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Radeon X800 PCIe2"
	Monitor		"Plasma TV"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1900x1080"
	EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		0    "Screen0"    0 0
        Screen          1    "Screen1"    RightOf    "Screen0"
        Option          "Xinerama"       "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
         Option  "Composite" "Enable"
EndSection



With that xorg.conf I have my current monitor (DELL 2001FP) working just fine in 1600x1200.  As you can tell from the xorg.conf I'm running an ATI Radeon x800 PCIe card.  

I have a dual boot machine.  When I boot into Windows XP, I'm running an extended desktop scenario.  My primary monitor, run through my VGA/Analog port, is the Dell 2001FP.  My secondary monitor, is my Pioneer 4270 Plasma TV and comes out of the DVI/Digital port.  In the Windows environment, it's being run as an extended desktop.  Not left of, right of, above, below, or clone, but extended.  Reason is, I have it set to a resolution of 1900x1080, not 1600x1200 like my Dell.  Also, my computer is in one room and my Plasma TV is another.  Extended setup was optimal, because I wasn't running the monitors side-by-side.

Most of the forum posts I've seen are either for the nvidia TwinView setup or for running dual-monitor off of a laptop as "left of, right of, etc."   Still, I did look into a mergedfb set-up, and followed the instructions on this page [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174) for mergedfb, but had no luck.  I kept getting black screens on both monitors when I'd boot into Ubuntu.

Any suggestions on a way to proceed?  One final thing I should point out, is I'm using the AIGLX drivers, not the FGLRX.  If I need to switch, I suppose I could. 

Thanks,

Culley

---

