---
title: "Hardy sound and video support"
date: 2008-04-25
forum: Multimedia Software
---

### Post by dirkoid on 2008-04-25
Okay, I made the absolutely ridiculous mistake of installing 8.04 on the first day and assuming it might actually work out of the box.
Yeah, right ...

Sound and video are both hosed OOB.

Equipment as follows

Gateway T6815 Laptop
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Section "Device"
Identifier "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "1280x800"
EndSubSection
EndSection

The entries above are copied from another xorg.conf as 8.04 can't seem to create a usable one on a dare.

The xorg.conf created by 8.04 is:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Nice, huh?

I don't care that much about sound at this point, but video is hosed. GDM, Gnome and KDE both set their desktop size to 1024x768 even though the actual useable real estate is 1280x800. I can move apps across the screen but the menus never move.

When I run

dpkg-reconfigure xserver-xorg

it only gives me the options to configure the keyboard and that's it.

It doesn't detect the video card and doesn't allow reconfiguration of the screen settings.

Quite frankly I'm so utterly disgusted with Ubuntu at this point I'm ready to drop it and go back to RHEL.

I certainly don't want to have to reinstall Feisty at this point but that's the last release that actually worked correctly.

Pardon my french but what a piece of crap.

Any help short of a complete reinstallation would be appreciated.

---

### Post by spudratic on 2008-04-27
same problem as above.Why would someone change the xorg file like it is in 8.04.I can't even tell what intel video driver I'm running.fire some if they are getting paid on throw them out if they are not or let them sweep the floors or clean the bathrooms.

---

