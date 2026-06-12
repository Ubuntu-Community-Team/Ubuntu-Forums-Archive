---
title: "Running two X screens with the OSS radeon driver?"
date: 2014-12-19
forum: Multimedia Software
---

### Post by SagaciousKJB on 2014-12-19
I installed 14.04 on a dual boot yesterday.  ATI dropped support for my car for the current fglrx drivers, so I have to go back to using the OSS radeon driver.  On my 12.0.4.5 installation I'm still using fglrx, and my Xorg.conf is setup as following for dual screens...

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
	Screen         "amdcccle-Screen[1]-1" 1366 0
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-TV"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "800x480"
	Option	    "TargetRefresh" "30"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-TV" "0-TV"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Used the amdccle obviously....

So following this template and reading the xorg.conf manual page, I came up with this for the radeon driver in 14.04

```
Section "Monitor"
	Identifier   "Laptop"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "TV"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "800x480"
	Option	    "TargetRefresh" "30"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Device0"
	Driver      "radeon"
	BusID       "PCI:1:5:0"
	Screen      0
EndSection

Section "Device"
	Identifier  "Device1"
	Driver      "radeon"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Device0"
	Monitor    "Laptop"
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Device1"
	Monitor    "TV"
EndSection

Section "ServerLayout"
	Identifier "Layout1"
	Screen "Screen0"
	Screen "Screen1" LeftOf "Screen0"
EndSection

```

It doesn't fail out right, it just doesn't produce any output on the TV.

I prefer using two X screens because I like to use Mplayer and it's easier to use the switch "--display host:0.1" to ensure it opens on the right display Window.  I don't really like the way RandR just makes one big screen...  But I suppose I will settle for using it if I can't run two X screens.

Can anyone tell me what I'm doing wrong or if there is just a compatability issue?

---

### Post by SagaciousKJB on 2014-12-27
Well I guess I will just hope someone answers by the time LTS ends for 12.04...

---

