---
title: "change primary display with ATI video card"
date: 2013-03-17
forum: Multimedia Software
---

### Post by hurtstotalktoyou on 2013-03-17
I'm not informed enough to write a how-to guide, so instead I will just post a "solved" thread explaining some problems I had last night and how I fixed them.  Hopefully others will find it useful.

Note:  I used Linux Mint 13 MATE LTS, but this all should work on any relatively recent ubuntu-based distro.

**The Problem:**  By default, Ubuntu/Mint/etc. chooses the DVI output for the primary display.  But I want the VGA output for the primary display.  It is quite difficult to switch.

Contrary to suggested solutions elsewhere on the forms, **xrandr does NOT solve the problem!**  Or at least, it doesn't solve my problem.  So I don't mess with xrandr.

**My solution:**

**(1)**  Install ubuntu/mint/etc. with the only the VGA monitor plugged in.  Do not plug in the DVI monitor yet!

**(2)**  Install the restricted ATI drivers.

**(3)**  Plug in the DVI display.

**(4)**  Run

```
gksu amdcccle
```

and set up the "single display desktop (multi-desktop)" mode for each monitor.

**(5)**  Following [this guy's advice](http://ubuntuforums.org/showthread.php?t=1476796&p=10359223#post10359223), I ran

```
gksu gedit /etc/X11/xorg.conf
```

and switched the lines *Option "Monitor-DFP2" "0-DFP2"* and *Option "Monitor-CRT1" "0-CRT1"* under the *Device* settings.

In other words, my old xorg.conf file looked like this:

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[2]-0" 1600 0
	Screen         "amdcccle-Screen[2]-1" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
[color=red]	Option	    "Monitor-DFP2" "0-DFP2"[/color]
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-1"
	Driver      "fglrx"
[color=red]	Option	    "Monitor-CRT2" "0-CRT2"[/color]
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-1"
	Device     "amdcccle-Device[2]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

And the new file looks like this:

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[2]-0" 1600 0
	Screen         "amdcccle-Screen[2]-1" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
[color=red]	Option	    "Monitor-CRT2" "0-CRT2"[/color]
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-1"
	Driver      "fglrx"
[color=red]	Option	    "Monitor-DFP2" "0-DFP2"[/color]
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-1"
	Device     "amdcccle-Device[2]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

**(6)**  Again run

```
gksu amdcccle
```

and perform any other changes you wish.

**Remaining issues:**  This solved my problem for the most part.  However grub2 still comes up on the DVI display.  It's not a hardware issue, because on a previous version of ubuntu (specfically, version 10.04) I had grub2 display on both DVI and VGA.  So I'm not sure how to fix that, but it's not a big deal for me.  The main thing is getting ubuntu itself to behave.  And now it does!

This is all thanks to [sero](http://ubuntuforums.org/member.php?u=263429), who graciously provided the key ingredient.

---

