---
title: "2 Video Cards, 3 Monitors - Configuration Problems"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by asgardfleet on 2007-11-15
Hi,

I have just installed 7.10 and having trouble setting up my video cards and monitors.

I have a PCI-E : Geforce 6200 and a PCI: Geforce FX5500.

I have two monitors connected to the 6200 and 1 to the 5500.

However Ubuntu seems to take the 5500 (PCI) as the default card and not the PCI-E.
Hence on boot up the Ubuntu loading screen displays on the first 2 monitors and nothing on the third but then login screen and then anything else is on the 3rd monitor.

I have included the lspci output and xorg.conf, if anyone is able to tell me what is wrong with my config or if there is something else I am missing, Thanks.

lspci
```
geoff@linux-desktop:/var/log$ lspci -x | grep VGA
01:06.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
```

xorg.conf
```
Section "Device"
	Identifier	"Device1"
	Boardname	"NVIDIA GeForce 6600 1"
	Busid		"PCI:5:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection

Section "Device" 
	Identifier	"Device2"
	Boardname	"NVIDIA GeForce 5500"
	Busid		"PCI:1:6:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"Device0"
	Monitor 	"monitor0"
	DefaultDepth	24
	
	Subsection "Display"
		Depth 24
		Modes "1280x1024" "1024x768" "800x600"
	EndSubsection

EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"Device1"
	Monitor 	"monitor1"
	DefaultDepth	24
	
	Subsection "Display"
		Depth 24
		Modes "1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubsection

EndSection

Section "Screen" 
	Identifier	"screen2"
	Device		"Device2"
	Monitor 	"monitor2"
	DefaultDepth	24
	
	Subsection "Display"
		Depth 24
		Modes "1280x1024" "1024x768" "800x600"
	EndSubsection

EndSection

Section "Monitor"
	Identifer "monitor0"
	HorizSync	30-90
	VertRefresh	60
	Option		"dpms"
EndSection

Section "Monitor"
	Identifer "monitor1"
	HorizSync	30-90
	VertRefresh	60
	Option		"dpms"
EndSection

Section "Monitor" 
	Identifer "monitor2"
	HorizSync	30-90
	VertRefresh	60
	Option		"dpms"
EndSection




Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"screen0"	0	0
	Screen	1	"screen1"	RightOf	"screen0"
	Screen  2	"screen2"	RightOf "screen1"
	Option          "Xinerama" "true"
	  	
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
```

---

