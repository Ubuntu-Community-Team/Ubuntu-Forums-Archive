---
title: "ATI card and resolution not detected"
date: 2010-09-06
forum: Multimedia Software
---

### Post by Fristi on 2010-09-06
Hi all

After a while I decided to give ubuntu another go so I set up a dual boot configuration. Everything works well except my graphics card. I have 2 problems (don't know if they are connected)

To start with, it's a laptop with an onboard Radion 3200 and it has another ATI Mobility Radeon HD4570 built in. I have an external screen attached to my laptop. (1920x1080)

When Ubuntu first booted it asked me if I wanted to install proprietary drivers, so I did that. Now when I took a look in the control center it showed my two monitors but they were both attached to the 3200 and I can't seem to find anything about the other (better) card. It does not appear in the proprietary drivers, I can't (I think) select it in the configuration utility.

If I execute 
```
sudo lshw

```
then it does show both adapters:
```
*-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:29 memory:c0000000-cfffffff(prefetchable) ioport:c000(size=256) memory:fbcf0000-fbcfffff memory:fbb00000-fbbfffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:d000(size=4096) memory:fbd00000-fbdfffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M92 [Mobility Radeon HD 4500 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:18 memory:d0000000-dfffffff(prefetchable) ioport:d000(size=256) memory:fbdf0000-fbdfffff memory:fbdc0000-fbddffff(prefetchable)
```

How can I install the other graphics card (or turn it on, or whater, I just want my laptop to use that one).

The other problem I have is that I can't select the max. resolution on my external screen, it can't go higher then 1600xsomething and that it won't even display because the refresh rate is to high.

Hopefully someone can help me with this.

edit: I added my xorg.conf file for extra information:

```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1600 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "true"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1366x768"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
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

Some additional info:

```

kevin@Zaphod:~$ lspci | grep ATI
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

```

The laptop in question is an ASUS X5DAB

---

### Post by Yellow Pasque on 2010-09-06
If battery life is not an issue, you may be able to turn off the integrated video card in the BIOS.

---

### Post by Fristi on 2010-09-07
I'll give that a go :).

I did discover that the aticonfig tool does detect both graphic adapters, I just need to figure out how I can make it use the better one..

```

kevin@Zaphod:~$ aticonfig --list-adapters
* 0. 01:05.0 ATI Radeon HD 3200 Graphics 
  1. 02:00.0 ATI Mobility Radeon HD 4500 Series

* - Default adapter

```

As you can see here, it detects both adapters, but it makes the 'bad' one the default, does anyone know how I can change this to the other one?

Resolution remains a problem aswell.

EDIT: I took a look in my bios, but no avail. I can't turn it of. Problem with laptop BIOS is that it's very limited.

---

### Post by Yellow Pasque on 2010-09-07
Try:
```
sudo aticonfig --initial adapter=<something>
```
Not sure what <something> should be, maybe the number or name of the adapter you want. Read the --help or man page of aticonfig.

---

### Post by Fristi on 2010-09-07
I executed the command:
```

sudo aticonfig --initial --adapter=1

```
where 1 is the better graphics adapter.

This certainly does something because when I log out and back in, the only thing I get to see is a black screen. First with a caret, not blinking or anything, just a caret in the left upper corner, afterwards it goes black and nothing happens. Rebooted, nothing changed. So apparently it does something..

---

### Post by Fristi on 2010-09-07
With the help of xrandr I managed to fix the resolution of my external screen. Had to add a mode for the resolution, worked flawlessly.

Xinorama is not doing what I want, so now I'm working with two desktops, only downside is that I cant drag windows in between them. (I could do that with xinorama enabled, but then my menubars were on my laptop screen, I want them on my external screen and did not yet find how to change that).

So, now only the graphics adapter thing remains

---

