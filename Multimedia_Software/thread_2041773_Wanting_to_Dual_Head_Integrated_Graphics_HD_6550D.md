---
title: "Wanting to Dual Head Integrated Graphics HD 6550D"
date: 2012-08-13
forum: Multimedia Software
---

### Post by naubol on 2012-08-13
Hello,

I am trying to integrate two vga connections to my motherboard using my integrated graphics on my cpu.  The specs are as follows.

OS: Ubuntu 12.04 64 bit Desktop
uname -a: Linux austin 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

RAM: 8G DDR3 (I believe...running at 1333) Single Stick
Motherboard: [[COLOR="Cyan"]Biostar A75MG[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138361")
CPU: [[COLOR="Cyan"]AMD A8-3870K[/COLOR]]("http://www.jr.com/amd/pe/AMD_AD3870WNGXB/")
Integrated Graphics: AMD Radeon HD 6550D
Monitor 1: [[COLOR="Cyan"]DELL E2209WF[/COLOR]]("http://www.ascendtech.us/dell-22-e2209wf-widescreen-lcd-monitor_i_m22dele2209wfws.aspx")
Monitor 2: [[COLOR="Cyan"]ACER AL2216W[/COLOR]]("http://support.acer.com/acerpanam/monitor/0000/acer/al2216w/al2216wsp2.shtml")

The back of the motherboard has two connectors, one DVI, one VGA.  I have the dell coming into the DVI via VGA to DVI connector, and the Acer just plain VGA.  The acer never shows anything when both monitors are plugged in, however these two monitors were pushing dual screens on another box, so I know the acer works.

I am usually very reluctant to post for help, but I tried a lot of things and am feeling frustrated.  I did search for some comments on integrated graphics but my searches did not return results that seemed on point.

In addition to trying ati's config tool for fglrx and using dual head options, etc, I tried many variations on this hand-written xorg.conf file...

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "screen1" 0 0
	Screen	    1  "screen2" RightOf "screen1"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
EndSection

Section "Monitor"
	Identifier	"monitor1"
	VendorName	"Dell"
	ModelName	"E2209WF"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier	"monitor2"
	VendorName	"Acer"
	ModelName	"AL2216W"
	DisplaySize	473 296
	VertRefresh	60
	Option		"DPMS" "True"
EndSection

Section "Device"
	Identifier  "device1"
	Driver      "fglrx"
	BusID       "PCI:0:1:0"
EndSection

Section "Screen"
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "screen2"
	Device     "device1"
	Monitor    "monitor2"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Any comments or help would be appreciated...

N

---

### Post by gordintoronto on 2012-08-13
What happens if you disconnect the Dell? How about if you connect the Dell's cable to the Acer?

Not all DVI to VGA converters are equal. Both monitors have DVI connectors: I suggest you get a DVI cable.

---

### Post by naubol on 2012-08-13
Well, replacing the vga/vga cable + vga/dvi to dvi/dvi worked, and I now have dual head.  Thank you...

N

---

