---
title: "1366x768 not listed under options with ATI Radeon HD 5830"
date: 2011-05-26
forum: Multimedia Software
---

### Post by grindboy on 2011-05-26
Hi Guys,

I've just bought a new rig. The graphics card (as listed in the title) is a ATI Radeon HD 5830. With the normal out of the box drivers I can get a resolution of 1366x768 (The native resolution of my 32inch panel) but the 3D performance isn't good.

With the ATI proprietary drivers installed 1366x768 isn't in the options (The ATI menu and the normal one)

So I need to generate an xorg.conf and add the resolution?

Any help would be appreciated and I can of course provide whatever log files and commandline outputs you need.

Many Thanks

Grindboy

[edit] OK so I checked to see if the 3D performance was any better with the proprietary drivers (despite the funky resolution) and it caused Minecraft (The only game I really play under Linux) to freeze on startup. I think what I'll do is stick with the Radeon Open Source driver (which runs all the visual effects nicely anyway) and just do all my gaming in Windows.

Thanks to everyone who looked at the thread, sorry if you ended up here after a Google search looking for answers.

---

### Post by grindboy on 2011-05-28
Right I've decided I want to try and fix this (if only to learn more about the inner workings of Ubuntu)

I've managed to install the latest drivers from the ATI website and as a result I'm now working with Catalyst Control Center (CCC) 11.5. The bad news is this doesn't give me the required resolution (1366x768). The good news is that it has generated an Xorg.conf! :D After changing the resolution the xorg.conf even included a resolution line which I have changed to 1366x768. This hasn't changed the resolution however even after forcing CCC to use the Xorg.conf with this command: 
```
$ sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

```
Which according to the unofficial AMD linux community wiki should force the xorg.conf changes.

My current Xorg.conf is below:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

As you can see I've changed preferred mode to 1366x768 without effect.

Any help would be greatly appreciated

Grindboy

[edit]

Thought my full system specs would be helpful:
- CPU: AMD Phenom II X4 Quad Core 840 "95W Edition" 3.20GHz 
- Motherboard: Gigabyte GA-M68MT-S2 (Socket AM3) DDR3 Motherboard
- RAM: 4GB (2x2GB) DDR3 1600MHz Dual Channel
- PSU: OCZ StealthXStream 2 500W Power Supply
- GPU: Sapphire ATI Radeon HD 5830

---

### Post by grindboy on 2011-05-29
::BUMP::

It occurred to me that the driver would only support 1360x768 (The standard VESA resolution)

I've tried this and no joy. Anyone want to wade in here? I feel like I'm just prodding and hoping for the best at the moment.

---

