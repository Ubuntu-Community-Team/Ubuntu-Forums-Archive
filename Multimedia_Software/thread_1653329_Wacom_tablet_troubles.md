---
title: "Wacom tablet troubles"
date: 2010-12-26
forum: Multimedia Software
---

### Post by ac3raven on 2010-12-26
I have a CTL-460 Wacom Bamboo tablet and I need to get it working in Ubuntu 10.04

The "xserver-xorg-input-wacom" package is installed.  And I edited my "10-wacom.conf" file to look like this:

```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "2"
        Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection


```

And I rebooted Ubuntu after that but its not working at all.  I can see it in lsusb as:

```
Bus 002 Device 003: ID 056a:00d4 Wacom Co., Ltd 

```

What am I missing?

EDIT: I'm in Ubuntu, not Lubuntu.

---

### Post by Favux on 2010-12-26
Hi ac3raven,

The default wacom.ko (the usb kernel driver) in Lucid is from linuxwacom 0.8.4-1 and it does not have your tablet model.  You need to compile and install an newer wacom.ko.  Please see the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by ac3raven on 2010-12-26
That worked.

---

