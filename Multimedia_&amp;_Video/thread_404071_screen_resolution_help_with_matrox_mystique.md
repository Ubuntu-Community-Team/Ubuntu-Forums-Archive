---
title: "screen resolution help with matrox mystique"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by Psychotron on 2007-04-07
Hi I need some help with my Dapper server install.  I of course installed ubuntu-desktop and am having trouble with screen resolutions with my matrox mystique and sceptre X9w Naga v1.1.  I can only get up to 800x600 and want higher.  I have the server hooked to the monitor via the D-Sub port.  I have tried both the mga and vesa driver in xorg.conf.  I need higher resolutions if you can please help me.

My lspci:
```

PCI:0:0:0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133]
PCI:0:1:0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
PCI:0:7:0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South]
PCI:0:7:1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
PCI:0:7:2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
PCI:0:7:3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
PCI:0:7:4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI]
PCI:0:13:0 Ethernet controller: Accton Technology Corporation SMC2-1211TX
PCI:0:17:0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique]
PCI:0:19:0 Mass storage controller: Triones Technologies, Inc. HPT366/368/370/370A/372/372N

```

and my xorg.conf:
```

Section "Device"
	Identifier	"Matrox Graphics, Inc. MGA 1064SG [Mystique]"
	Driver		"vesa"
	BusID		"PCI:0:17:0"
	Option		"OldDmaInit"		"True"
EndSection

Section "Monitor"
	Identifier	"Sceptre"
	Option		"DPMS"
	HorizSync	24-82
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Matrox Graphics, Inc. MGA 1064SG [Mystique]"
	Monitor		"Sceptre"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x720" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x720" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x720" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x720" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x720" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x720" "1024x768"
	EndSubSection
EndSection

```

I had to edit the Modes in order to make it match the monitor correctly.  But still stuck at 640x480 and 800x600.  I am thinking its because of the old matrox card.

---

### Post by Psychotron on 2007-04-08
anyone?

---

### Post by sdowney717 on 2007-04-08
perhaps it is too old

PCI:0:17:0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique]

[http://en.wikipedia.org/wiki/VGA](http://en.wikipedia.org/wiki/VGA)

Video Graphics Array (VGA) is an analog computer display standard first marketed in 1987 by IBM. While it has been obsolete for some time except in the pocket PC market where it is becoming the new standard, it was the last graphical standard that the majority of manufacturers decided to follow, making it the lowest common denominator that all PC graphics hardware supports prior to a device-specific driver being loaded. For example, the Microsoft Windows splash screen appears while the machine is still operating in VGA mode, which is the reason that this screen always appears in reduced resolution and color depth.

The term VGA is often used to refer to a resolution of 640×480, regardless of the hardware that produces the picture. It may also refer to the 15-pin D-subminiature VGA connector which is still widely used to carry analog video signals of all resolutions.

VGA was officially superseded by IBM's XGA standard, but in reality it was superseded by numerous extensions to VGA made by clone manufacturers that came to be known as "Super VGA".

---

### Post by Psychotron on 2007-04-08
actually I don't think it is that old.  Specs on the card say it can do 1024x768 and higher.  I dunno, anyone else got any ideas?

I fixed it by taking the matrox out and putting in an old s3virge velocity 3d card I found...got tons of resolutions now.

---

