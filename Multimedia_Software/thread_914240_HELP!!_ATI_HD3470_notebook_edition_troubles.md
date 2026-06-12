---
title: "HELP!! ATI HD3470 notebook edition troubles"
date: 2008-09-08
forum: Multimedia Software
---

### Post by ntrgc89 on 2008-09-08
So I just recently installed Ubuntu on my new T400, and at first everything seemed fine. Resolution was fine, everything transfered to my external monitor without a hitch, and compiz seemed to be working until I enabled ring switcher, when it didn't actually show the windows moving around the screen, just the text at the bottom of which one I was (apparently) looking at. 

So I've been trying to find solutions to the problem without much avail. The radeon driver didn't help, the ati driver didn't help, and fglrx, as expected, is a nightmare. Even the simple act of trying to play a divx file just about crashed my system. Here's my lspci, if that helps, and my xorg.conf

```

00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Cantiga PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Cantiga MEI Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
03:00.0 Network controller: Intel Corporation Unknown device 4236
04:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 11)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)

```

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
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

```

I should also probably mention that I have the switchable graphics, so I'm a bit suspicious it might have switched to using the integrated ones, which is causing all the trouble, but I really can't tell. I thought about switching to the integrated one but saw some bad posts about it. Any help? Thanks much, it's appreciated.

---

### Post by syxbit on 2008-09-11
i doubt fglrx works with that card yet (it's too new)
i ordered the same laptop, but with just intel gfx (it hasn't arrived yet)

my advice, run intrepid for the next little while, as that has the new intel gfx driver, with the intel graphics card set in the bios (you can't use the switch, i don't think)

or you could use a different distro. some other distro's are using newer xorg's than hardy, and will support it (like Arch Linux, which is what i use)

---

### Post by Zero Prime on 2008-09-11
I have the ATI 3200 chipset.  I used Envy and it works great.  I also use the 2.6.24-21-generic kernel.

---

### Post by robertpolson on 2008-09-17
How did you install intrepid  on t400 ?

It does not install on mine.

---

