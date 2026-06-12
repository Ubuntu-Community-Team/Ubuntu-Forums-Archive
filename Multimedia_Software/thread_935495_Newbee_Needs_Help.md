---
title: "Newbee Needs Help"
date: 2008-10-01
forum: Multimedia Software
---

### Post by LINUX_ID10T on 2008-10-01
I am new to Ubuntu and Linux all together and I am fighting with my Alienware Laptop. I have ran all updates, verified (I think) that the system recognizes the sound card and i still can not get sound from the speakers, only from the headphone jack.

I have been trying several recommendations from this forum, books, other websites and I am just smoked.....

Here is the info from my lspci -v listing:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, fast devsel, latency 0 
	Capabilities: <access denied> 

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=0 
	I/O behind bridge: 0000d000-0000dfff 
	Memory behind bridge: f8f00000-fbdfffff 
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff 
	Capabilities: <access denied> 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, fast devsel, latency 0, IRQ 20 
	Memory at f8efc000 (64-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0 
	I/O behind bridge: 0000e000-0000efff 
	Memory behind bridge: fbe00000-fbefffff 
	Capabilities: <access denied> 

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0 
	Memory behind bridge: fbf00000-fbffffff 
	Capabilities: <access denied> 

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0 
	I/O behind bridge: 00006000-00006fff 
	Memory behind bridge: fc000000-feafffff 
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff 
	Capabilities: <access denied> 

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 19 
	I/O ports at cc00 [size=32] 

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 20 
	I/O ports at c880 [size=32] 

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 18 
	I/O ports at c800 [size=32] 

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 16 
	I/O ports at c480 [size=32] 

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 19 
	Memory at f8efbc00 (32-bit, non-prefetchable) [size=1K] 
	Capabilities: <access denied> 

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32 
	Memory behind bridge: feb00000-febfffff 
	Capabilities: <access denied> 

00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0 
	Capabilities: <access denied> 

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20 
	I/O ports at 01f0 [size=8] 
	I/O ports at 03f4 [size=1] 
	I/O ports at 0170 [size=8] 
	I/O ports at 0374 [size=1] 
	I/O ports at ffa0 [size=16] 
	Capabilities: <access denied> 

01:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Memory at f8ffc000 (32-bit, non-prefetchable) [size=16K] 
	Bus: primary=01, secondary=02, subordinate=04, sec-latency=0 
	I/O behind bridge: 0000d000-0000dfff 
	Memory behind bridge: f9000000-fbdfffff 
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff 
	Capabilities: <access denied> 

02:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=0 
	I/O behind bridge: 0000d000-0000dfff 
	Memory behind bridge: f9000000-fbdfffff 
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff 
	Capabilities: <access denied> 

02:01.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=02, secondary=04, subordinate=04, sec-latency=0 
	Capabilities: <access denied> 

03:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7950 GTX (rev a1) (prog-if 00 [VGA controller]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, fast devsel, latency 0, IRQ 16 
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M] 
	Memory at c0000000 (64-bit, prefetchable) [size=512M] 
	Memory at f9000000 (64-bit, non-prefetchable) [size=16M] 
	I/O ports at dc00 [size=128] 
	[virtual] Expansion ROM at fbde0000 [disabled] [size=128K] 
	Capabilities: <access denied> 

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12) 
	Subsystem: Rioworks Unknown device 2054 
	Flags: bus master, fast devsel, latency 0, IRQ 219 
	Memory at fbefc000 (64-bit, non-prefetchable) [size=16K] 
	I/O ports at e800 [size=256] 
	Expansion ROM at fbec0000 [disabled] [size=128K] 
	Capabilities: <access denied> 

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61) 
	Subsystem: Intel Corporation Unknown device 1100 
	Flags: bus master, fast devsel, latency 0, IRQ 218 
	Memory at fbffe000 (64-bit, non-prefetchable) [size=8K] 
	Capabilities: <access denied> 

0a:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 64, IRQ 18 
	Memory at febff800 (32-bit, non-prefetchable) [size=2K] 
	Capabilities: <access denied> 

0a:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 64, IRQ 17 
	Memory at febff400 (32-bit, non-prefetchable) [size=256] 

0a:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: medium devsel, IRQ 4 
	Memory at febff000 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, fast devsel, latency 0 
	Capabilities: <access denied> 

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=0 
	I/O behind bridge: 0000d000-0000dfff 
	Memory behind bridge: f8f00000-fbdfffff 
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff 
	Capabilities: <access denied> 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, fast devsel, latency 0, IRQ 20 
	Memory at f8efc000 (64-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0 
	I/O behind bridge: 0000e000-0000efff 
	Memory behind bridge: fbe00000-fbefffff 
	Capabilities: <access denied> 

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0 
	Memory behind bridge: fbf00000-fbffffff 
	Capabilities: <access denied> 

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0 
	I/O behind bridge: 00006000-00006fff 
	Memory behind bridge: fc000000-feafffff 
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff 
	Capabilities: <access denied> 

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 19 
	I/O ports at cc00 [size=32] 

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 20 
	I/O ports at c880 [size=32] 

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 18 
	I/O ports at c800 [size=32] 

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 16 
	I/O ports at c480 [size=32] 

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0, IRQ 19 
	Memory at f8efbc00 (32-bit, non-prefetchable) [size=1K] 
	Capabilities: <access denied> 

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32 
	Memory behind bridge: feb00000-febfffff 
	Capabilities: <access denied> 

00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 0 
	Capabilities: <access denied> 

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20 
	I/O ports at 01f0 [size=8] 
	I/O ports at 03f4 [size=1] 
	I/O ports at 0170 [size=8] 
	I/O ports at 0374 [size=1] 
	I/O ports at ffa0 [size=16] 
	Capabilities: <access denied> 

01:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Memory at f8ffc000 (32-bit, non-prefetchable) [size=16K] 
	Bus: primary=01, secondary=02, subordinate=04, sec-latency=0 
	I/O behind bridge: 0000d000-0000dfff 
	Memory behind bridge: f9000000-fbdfffff 
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff 
	Capabilities: <access denied> 

02:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=0 
	I/O behind bridge: 0000d000-0000dfff 
	Memory behind bridge: f9000000-fbdfffff 
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff 
	Capabilities: <access denied> 

02:01.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=02, secondary=04, subordinate=04, sec-latency=0 
	Capabilities: <access denied> 

03:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7950 GTX (rev a1) (prog-if 00 [VGA controller]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, fast devsel, latency 0, IRQ 16 
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M] 
	Memory at c0000000 (64-bit, prefetchable) [size=512M] 
	Memory at f9000000 (64-bit, non-prefetchable) [size=16M] 
	I/O ports at dc00 [size=128] 
	[virtual] Expansion ROM at fbde0000 [disabled] [size=128K] 
	Capabilities: <access denied> 

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12) 
	Subsystem: Rioworks Unknown device 2054 
	Flags: bus master, fast devsel, latency 0, IRQ 219 
	Memory at fbefc000 (64-bit, non-prefetchable) [size=16K] 
	I/O ports at e800 [size=256] 
	Expansion ROM at fbec0000 [disabled] [size=128K] 
	Capabilities: <access denied> 

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61) 
	Subsystem: Intel Corporation Unknown device 1100 
	Flags: bus master, fast devsel, latency 0, IRQ 218 
	Memory at fbffe000 (64-bit, non-prefetchable) [size=8K] 
	Capabilities: <access denied> 

0a:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI]) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 64, IRQ 18 
	Memory at febff800 (32-bit, non-prefetchable) [size=2K] 
	Capabilities: <access denied> 

0a:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: bus master, medium devsel, latency 64, IRQ 17 
	Memory at febff400 (32-bit, non-prefetchable) [size=256] 

0a:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a) 
	Subsystem: Rioworks Unknown device 2052 
	Flags: medium devsel, IRQ 4 
	Memory at febff000 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied

I need really simple instructions on how to mode this. I have just about everything else done.

Help the Linux_ID10T, it will be considered a good deed.

---

