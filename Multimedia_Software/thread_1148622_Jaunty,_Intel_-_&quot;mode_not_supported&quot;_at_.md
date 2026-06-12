---
title: "Jaunty, Intel - &quot;mode not supported&quot; at external monitor/TV"
date: 2009-05-04
forum: Multimedia Software
---

### Post by noerknhar on 2009-05-04
Hi guys. I'm experiencing a strange issue since I upgraded to jaunty. I've read several guides and such about jaunty and intel graphics having problems, but I think that my problem is sort of "unique". Please go on reading instead of linking sticky threads - I've seen them.

I own a Samsung LE32 S81B 32inch LCD TV. It's connected to my Amilo SI3655 via DVI->HDMI. Using inteprid, I was able to simply "activate" my TV on 1360x768 (or 1368:768?) by typing "xrandr --output HDMI-1 --auto --right-of LVDS". Everything worked fine and I was able to watch movies on my TV without any problems. Now, that I've upgraded to jaunty, my TV reports "mode not supported" when trying that command. (I've checked xrandr --verbose and everything seems normal. I even compared the values with the ones specified in my TV's handbook. 

For a better understanding, here's the output of "xrandr --verbose"
```
noerknhar@noerkNB:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2640 x 800
VGA disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3b
	Timestamp:  21677
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
LVDS connected 1280x800+0+0 (0x3e) normal (normal left inverted right x axis y axis) 287mm x 180mm
	Identifier: 0x3c
	Timestamp:  21677
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       1
	CRTCs:      1
	Panning:    0x0+0+0
	Tracking:   0x0+0+0
	Border:     0/0/0/0
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID_DATA:
		00ffffffffffff003064070301010101
		08120103801d12780aa6869556528628
		28525500000001010101010101010101
		0101010101019e20009051201f304880
		36001fb4100000180000000f0039402e
		640104020b5a6e050f00000000fe0054
		4d444953504c41590a202020000000fe
		004c544431333345574d5a0a202000eb
	PANEL_FITTING:	full_aspect
		supported: center       full_aspect  full        
	BACKLIGHT_CONTROL:	kernel
		supported: native       legacy       combination  kernel      
	BACKLIGHT: 7 (0x00000007)	range:  (0,7)
  1280x800 (0x3e)   83.5MHz -HSync -VSync *current +preferred
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  803 end  809 total  831           clock   59.8Hz
  1024x768 (0x3f)   94.5MHz +HSync +VSync
        h: width  1024 start 1072 end 1168 total 1376 skew    0 clock   68.7KHz
        v: height  768 start  769 end  772 total  808           clock   85.0Hz
  1024x768 (0x40)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x41)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x42)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x43)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x44)   56.3MHz +HSync +VSync
        h: width   800 start  832 end  896 total 1048 skew    0 clock   53.7KHz
        v: height  600 start  601 end  604 total  631           clock   85.1Hz
  800x600 (0x45)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x46)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x47)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x48)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x49)   36.0MHz -HSync -VSync
        h: width   640 start  696 end  752 total  832 skew    0 clock   43.3KHz
        v: height  480 start  481 end  484 total  509           clock   85.0Hz
  640x480 (0x4a)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  492 total  520           clock   72.8Hz
  640x480 (0x4b)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x4c)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x4d)   35.5MHz -HSync +VSync
        h: width   720 start  756 end  828 total  936 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  446           clock   85.0Hz
  640x400 (0x4e)   31.5MHz -HSync +VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  445           clock   85.1Hz
  640x350 (0x4f)   31.5MHz +HSync -VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  350 start  382 end  385 total  445           clock   85.1Hz
HDMI-1 connected (normal left inverted right x axis y axis)
	Identifier: 0x3d
	Timestamp:  21677
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID_DATA:
		00ffffffffffff004c2da40200000000
		2e1001038010098c0ae2bda15b4a9824
		15474aa1080001010101010101010101
		010101010101662150b051001b304070
		3600a05a0000001e011d007251d01e20
		6e285500a05a0000001e000000fd0031
		470f3209000a202020202020000000fc
		0053414d53554e470a20202020200115
		02031af1468413051403122309070783
		01000066030c00200080011d00bc52d0
		1e20b8285540a05a0000001e011d8018
		711c1620582c2500a05a0000009e011d
		80d0721c1620102c2580a05a0000009e
		8c0ad08a20e02d10103e9600a05a0000
		00188c0ad090204031200c405500a05a
		00000018000000000000000000000069
  1360x768 (0xbe)   85.5MHz +HSync +VSync +preferred
        h: width  1360 start 1424 end 1536 total 1792 skew    0 clock   47.7KHz
        v: height  768 start  771 end  777 total  795           clock   60.0Hz
  1280x720 (0xbf)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1024x768 (0x42)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x47)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4c)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0xc0)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
noerknhar@noerkNB:~$ 
```

I even tried --mode "1280x720" - that one works without any problems (but seriously, the resolution is not quite as good as it could be!). --mode "1360x768" results in 'mode not supported'.

I also tried "cvt 1360 768" and "cvt 1368 768", parsed the resulting modelines to xrandr --newmode and tried to use them. 'mode not supported'.

What I've also done:
- deleting monitors.xml
- reset of xorg.conf
- bleeding edge intel graphics drivers
- not as bleeding but also edge intel graphics drivers

AND THEN, there was a solution. I installed the old intel driver version 2.4 from a repository I've found and tadaaa, everything works. "xrandr --verbose" has the EXACT SAME parameters with that driver and my TV responds within seconds doing the exact same thing as it did with inteprid. The only BIG issue is that I can no longer watch FullHD-movies on my notebook because of massive performance issues. With newer drivers, even with the one shipped with jaunty, I did not have these performance issues ever (2.4 in inteprid also was much much better...dunno why tho). Also I am experiencing extreme bad performance in games and even in gnome.

I really really really hope someone maybe has an idea, has experienced the same problem or even has the same TV to have some "tryouts". This is nothing I can stand with and I am even thinking about installing inteprid again...

PS: Sorry for my bad english, but it has been a long day and I am german and stuff...you know ;) 
PPS: someone in the german ubuntuusers.de-forums reported that he was experiencing the same issues with another TV. For him it was the "cvt 1360 768" and --newmode thing that worked perfectly - but that did not for me...

If you need any further details, please feel free to ask.


edit: inb4, here's "lspci -v"
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 2297
	Memory at f8000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0
	Memory at f8400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82567LF Gigabit Network Connection (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at f8500000 (32-bit, non-prefetchable) [size=128K]
	Memory at f8524000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1820 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1860 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f8725800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f8520000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f4000000-f5ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: c2000000-cbefffff
	Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 18a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f8725c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2300
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 1c00 [size=32]
	Memory at f8725000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: medium devsel, IRQ 10
	Memory at c0000000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]
	Kernel modules: i2c-i801

04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1201
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	Memory at f6000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

0c:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at c2000000 (32-bit, non-prefetchable) [size=2K]
	Memory at c4000000 (32-bit, non-prefetchable) [size=128]
	Memory at c6000000 (32-bit, non-prefetchable) [size=128]
	Memory at c8000000 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

0c:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at cbeffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0c:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: fast devsel, IRQ 19
	Memory at cbeff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

0c:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at cbeff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0c:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at cbeff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

---

### Post by noerknhar on 2009-05-05
I allow myself to bump this thread. I hope I do not violate any rules. If so, please inform me and I won't do it again ;)

---

### Post by noerknhar on 2009-05-07
Hello everybody. I tried the 30-rc2 kernel in combination with newest xorg-edgers-drivers some minutes ago. Performance was great, TV still showing "mode not supported".

Maybe - if noone has an idea about how to fix this issue - do you know how/whom to inform about that? bugreports and such? Never did...

---

### Post by noerknhar on 2009-05-16
Still no news from my side :(

> **noerknhar said:**
> I allow myself to bump this thread. I hope I do not violate any rules. If so, please inform me and I won't do it again ;)

---

