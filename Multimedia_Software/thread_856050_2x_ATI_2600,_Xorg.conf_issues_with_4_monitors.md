---
title: "2x ATI 2600, Xorg.conf issues with 4 monitors"
date: 2008-07-11
forum: Multimedia Software
---

### Post by Geoscientist on 2008-07-11
I am trying to set up 4 monitors on Ubuntu. I can get as far as a cloned pair of monitors. 

Earlier on, I posted [here](http://ubuntuforums.org/showthread.php?t=851860&highlight=monitors)
Since then, I have had some progress but it is acting quite unusually.

Radeona0 and Radeona1 are the devices for each monitor on the first card, and
Radeonb0 and Radeonb1 are the devices for each monitor on the second card. 

The monitors are arranged left to right; a0, a1, b0, b1. 
Within the xorg.conf file, the device, monitor and screen sections use these annotations to refer to these 4 monitors. 

When I refer to two monitors (eg a0 and b0) "act as a pair", I mean the desktop is extended across, though I cant click and drag across open windows.

The ServerLayout section contains
```
	Screen "Screena0"
	Screen "Screenb0" RightOf "Screena0"
```
a0 and b0 act as a pair, and a1 and b1 are cloning a0 and b0 respectively. 

If I use the following ServerLayout;
```
	Screen "Screena1"
	Screen "Screenb0" RightOf "Screena1"
```
Then b0 and b1 act as a pair; and there is no signal to a0 and a1. 

If I use the following ServerLayout;
```
	Screen "Screena0"
	Screen "Screenb1" RightOf "Screena0"
```
It fails, and reverts to low graphics mode. 

The error log contains the warning line 
```
(WW) RADEON(2): R600 support is mostly incomplete and very experimental
```
Maybe these issues are specific to this chipset.

Any ideas would be much appreciated.

Here is the Xorg.conf file;
```
Section "Device"
	Identifier "Radeona0"
	Driver "ati"
	BusID "PCI:1:0:0"
	Screen 0
EndSection

Section "Device"
	Identifier "Radeona1"
	Driver "ati"
	BusID "PCI:1:0:0"
	Screen 1
EndSection

Section "Device"
	Identifier "Radeonb0"
	Driver "ati"
	BusID "PCI:2:0:0"
	Screen 0
EndSection

Section "Device"
	Identifier "Radeonb1"
	Driver "ati"
	BusID "PCI:2:0:0"
	Screen 1
EndSection

Section "Monitor"
	Identifier "Monitora0"
	Option "DPMS"
	Modeline "1280x1024" 108.00 1280 1328 1440 1688 1024 1025 1028 1066
EndSection

Section "Monitor"
	Identifier "Monitora1"
	Option "DPMS"
	Modeline "1280x1024" 108.00 1280 1328 1440 1688 1024 1025 1028 1066
EndSection

Section "Monitor"
	Identifier "Monitorb0"
	Option "DPMS"
	Modeline "1280x1024" 108.00 1280 1328 1440 1688 1024 1025 1028 1066
EndSection

Section "Monitor"
	Identifier "Monitorb1"
	Option "DPMS"
	Modeline "1280x1024" 108.00 1280 1328 1440 1688 1024 1025 1028 1066
EndSection

Section "Screen"
	Identifier "Screena0"
	Device "Radeona0"
	Monitor "Monitora0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screena1"
	Device "Radeona1"
	Monitor "Monitora1"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screenb0"
	Device "Radeonb0"
	Monitor "Monitorb0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screenb1"
	Device "Radeonb1"
	Monitor "Monitorb1"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Screena0"
	Screen "Screenb0" RightOf "Screena0"
EndSection

```

---

