---
title: "Envy on 8.04 ?"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by adelodder on 2008-01-26
I had this great idea of upgrading Ubuntu 7.10 to version 8.04.

When I try to install the NVidia drivers with Envy 0.9.10, I get following error message:

```
python pulse.py nvidia 
root@4000BABA:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.10
ENVY ERROR: Your Operating System does not seem to be supported by Envy
```

The only way under 7.10 to get my secondary screen at a 1280x720 (HD720p) resolution, was to install the NVidia drivers through Envy.

The best result I get installing the Nvidia drivers with the 'Restricted Drivers Manager' is a 1280x720 resolution with mest up colors (blue blueish).

Hence my question: Has someone been able to run Envy on Ubuntu 8.04 Hardy Heron?

have a nice day

---

### Post by tseliot on 2008-01-29
maybe you can try this:
```
sudo nvidia-settings
```

and make sure that the correct resolution and refresh rate are set in the NVIDIA panel (and save your settings).

---

### Post by leeley on 2008-02-22
:mad:When ever I run sudo nvidia-settings I get this
 You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server

Code form lspci as follows
00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [40] HyperTransport: Slave or Primary Interface
	Capabilities: [5c] HyperTransport: MSI Mapping
	Capabilities: [68] HyperTransport: UnitID Clumping
	Capabilities: [74] HyperTransport: Interrupt Discovery and Configuration
	Capabilities: [7c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-

00:01.0 PCI bridge: ALi Corporation PCI Express Root Port (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: fa700000-fa7fffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] Express Root Port (Slot+) IRQ 0
	Capabilities: [7c] HyperTransport: MSI Mapping
	Capabilities: [88] HyperTransport: Revision ID: 1.05

00:02.0 PCI bridge: ALi Corporation PCI Express Root Port (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fa800000-fa8fffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] Express Root Port (Slot+) IRQ 0
	Capabilities: [7c] HyperTransport: MSI Mapping
	Capabilities: [88] HyperTransport: Revision ID: 1.05

00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
	Flags: bus master, fast devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: [40] HyperTransport: Slave or Primary Interface
	Capabilities: [60] HyperTransport: Interrupt Discovery and Configuration
	Capabilities: [80] AGP version 3.0

00:05.0 PCI bridge: ALi Corporation AGP8X Controller (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	Memory behind bridge: fa900000-fe9fffff
	Prefetchable memory behind bridge: 9ff00000-bfefffff

00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff

00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
	Subsystem: ASRock Incorporation ASRock 939Dual-SATA2 Motherboard
	Flags: bus master, medium devsel, latency 0

00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
	Subsystem: ASRock Incorporation Unknown device 7101
	Flags: medium devsel

00:08.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
	Subsystem: ASRock Incorporation ASRock 939Dual-SATA2 Motherboard
	Flags: bus master, medium devsel, latency 32, IRQ 24
	I/O ports at e800 [size=256]
	Memory at febff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 2

00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
	Subsystem: ASRock Incorporation Unknown device 5263
	Flags: bus master, medium devsel, latency 32, IRQ 23
	I/O ports at e400 [size=256]
	Memory at febfec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7) (prog-if 8a [Master SecP PriP])
	Subsystem: ASRock Incorporation ASRock 939Dual-SATA2 Motherboard IDE (PATA)
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ff00 [size=16]

00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ASRock Incorporation ASRock 939Dual-SATA2 Motherboard
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
	Memory at febfd000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ASRock Incorporation ASRock 939Dual-SATA2 Motherboard
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21
	Memory at febfc000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ASRock Incorporation ASRock 939Dual-SATA2 Motherboard
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
	Memory at febfb000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: ASRock Incorporation Unknown device 5239
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
	Memory at febfe800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel

03:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 A-LE (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Unknown device a295
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 5
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at a0000000 (32-bit, prefetchable) [size=256M]
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 3.0

04:07.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
	Subsystem: Conexant Unknown device 2005
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at dc00 [size=8]
	Capabilities: [40] Power Management version 2

I have edited my xorg file to no result except that when I reboot I get low graphics 800x600.

When I rename the xorg file to what ever and use no xorg file I get 1040x768
I was using Gutsy every thing worked great  am now using using hardy
HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:confused:

---

### Post by adelodder on 2008-02-22
I have got mine working with the latest NVidia drivers and without using envy.

First I downloaded the driver from [http://www.nvidia.com/object/linux_display_ia32_169.09.html]("http://www.nvidia.com/object/linux_display_ia32_169.09.html").  Copied it into my home folder.

Then I logged out.  At the login screen I pressed Ctrl-Alt-F1.

and used following commands:

```

su
sudo /etc/init.d/kdm stop     *or sudo /etc/init.d/gdm stop*
sh NVIDIA-Linux-x86-169.09-pkg1.run

```
It installed the latest drivers and reconfigured my Xorg.conf just like I needed it:
Dual screen with HD720p settings for my TV screen.

Let us know if it worked out.

---

