---
title: "NVdia borked"
date: 2009-03-31
forum: Multimedia Software
---

### Post by Roanoke on 2009-03-31
I believe I am in deep crap here. First, despite having the drivers (I think), jockey-gtk says that no proprietary drivers are in use. Second, upon running nvidia-settings, I get this in an error box:
```

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

```
and I can't run Nexuiz (asked on #nexuiz, they said it is because of graphics card problems, [nexuiz output]( http://paste.ubuntu.com/141072/))
I would greatly appreciate help on getting out of this hole.

---

### Post by xc3RnbFO8P on 2009-04-01
What graphics card do you have?
If you have Nvidia card, see if you got **Nvidia-???-Modaliases** installed.

---

### Post by Roanoke on 2009-04-01
> **Ringi said:**
> What graphics card do you have?
If you have Nvidia card, see if you got **Nvidia-???-Modaliases** installed.

Yes, I have 177.
EDIT: I don't have any mention of 'nvidia' when I do lspci, but no mention of ATI. Why?
```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by xc3RnbFO8P on 2009-04-01
Show the output of **xorg.conf**.
> gedit /etc/X11/xorg.conf

In Synaptic Package Manager check if got installed:
libgl1-mesa-dri
libgl1-mesa-dev
libgl1-mesa-glx

---

### Post by DeMus on 2009-04-01
> **Roanoke said:**
> Yes, I have 177.
EDIT: I don't have any mention of 'nvidia' when I do lspci, but no mention of ATI. Why?
```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

From the list you present I only see an Intel graphic chip:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
What makes you think you have an nVidia card?
In fact all on board equipment is Intel. So unless you have a card which is not presented by "lspci", I'm pretty sure you have an Intel graphics controller and should try to get the right driver from Intel.

---

### Post by Roanoke on 2009-04-01
> **Ringi said:**
> Show the output of **xorg.conf**.


In Synaptic Package Manager check if got installed:
libgl1-mesa-dri
libgl1-mesa-dev
libgl1-mesa-glx
I have all of those installed.
```

$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection
# Uncomment the following section if you you have a TabletPC that supports touch
# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "touch"
#  Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
#  Option        "Device"        "/dev/input/wacom" # USB ONLY
#  Option        "Type"          "touch"
#  Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
# EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Virtual	2464 1189
	EndSubSection
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/input/wacom" # USB ONLY?
	Option        "Type"          "stylus"
	Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/input/wacom" # USB ONLY?
	Option        "Type"          "eraser"
	Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/input/wacom" # USB ONLY?
	Option        "Type"          "cursor"
	Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "pad"
	Option        "Device"        "/dev/input/wacom"    # USB ONLY
	Option        "Type"          "pad"
	Option        "USB"           "on"                  # USB ONLY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice   "stylus"  "SendCoreEvents"
	InputDevice   "eraser"  "SendCoreEvents"
	InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
	InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option          "SHMConfig"             "on"
EndSection
$

```

@DeMus: Well, I guess I just assumed that, since I have a laptop (and my previous one (this is only my second one) had an nvidia card). Is there a concrete way to check?

---

### Post by xc3RnbFO8P on 2009-04-02
In /etc/X11/ is there a xorg.conf.backup file?

---

### Post by Roanoke on 2009-04-02
> **Ringi said:**
> In /etc/X11/ is there a xorg.conf.backup file?
I use RCS for that.
EDIT: It appears I don't have an nvidia card, I have an intel card.

---

### Post by Roanoke on 2009-04-03
Bump

---

### Post by Roanoke on 2009-04-04
After a while in #ubuntu, I found out that I had an nvidia driver installed which messed everything up.

---

