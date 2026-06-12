---
title: "Video player shuts down when attempting to play viedeo!"
date: 2009-04-21
forum: Multimedia Software
---

### Post by clyde9999 on 2009-04-21
playing video shuts all video players down.

VLC
> [????????] x11 video output error: X11 request 133.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  80
  Current serial number in output stream:  81


Totem
> The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 69 error_code 11 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


I am using Ubuntu 9.04, my computer is a Dell Precision PP01X two core P3 laptop with 512 meg of ram

I hope someone can help with this issue.

Jack

---

### Post by VMC on 2009-04-21
When I had a similar error from totem it ended up being Xorg and/or Intel driver. From terminal type "lspci -v" and look for video section. Report back what chip you use.

---

### Post by clyde9999 on 2009-04-22
> **VMC said:**
> When I had a similar error from totem it ended up being Xorg and/or Intel driver. From terminal type "lspci -v" and look for video section. Report back what chip you use.

HI VMC,

Here is what I came up with,

> clyde9@clyde9-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
	Flags: bus master, fast devsel, latency 0
	Memory at e8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: e0000000-e7ffffff
	Kernel modules: shpchp

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=10, sec-latency=32
	I/O behind bridge: 0000e000-0000ffff
	Memory behind bridge: f4000000-fbffffff
	Prefetchable memory behind bridge: 30000000-39ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Intel Corporation Device 4541
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at bfa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
	Subsystem: Intel Corporation Device 4541
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at dce0 [size=32]
	Kernel driver in use: uhci_hcd

01:00.0 VGA compatible controller: nVidia Corporation NV11GL [Quadro2 MXR/EX/Go] (rev b2)
	Subsystem: Dell Device 00e5
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 11
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at fd000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, rivafb

02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
	Subsystem: Dell Device 00e5
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at ec00 [size=256]
	Memory at f8ffe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: Maestro3
	Kernel modules: snd-maestro3

02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
	Subsystem: 3Com Corporation Device 6456
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at e800 [size=256]
	Memory at f8ffdc00 (32-bit, non-prefetchable) [size=128]
	Memory at f8ffd800 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at 38000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
	Subsystem: 3Com Corporation Device 615b
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at e400 [size=256]
	Memory at f8ffd400 (32-bit, non-prefetchable) [size=256]
	Memory at f8ffd000 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>

02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
	Subsystem: Dell Device 00e5
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: f4000000-f7fff000
	I/O window 0: 0000e000-0000e0ff
	I/O window 1: 0000f000-0000f0ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
	Subsystem: Dell Device 00e5
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at f8001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 34000000-37fff000 (prefetchable)
	Memory window 1: 3c000000-3ffff000
	I/O window 0: 0000f400-0000f4ff
	I/O window 1: 0000f800-0000f8ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller (prog-if 10)
	Subsystem: Dell Device 00e5
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at f8ffc800 (32-bit, non-prefetchable) [size=2K]
	Memory at f8ff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

07:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: PROXIM Inc Device 0a10
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at 3c000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci, ath5k


Thank you so much for your help. 

clyde9999

---

### Post by xc3RnbFO8P on 2009-04-22
Try this:
[http://ubuntuforums.org/showthread.php?t=1132119]("http://ubuntuforums.org/showthread.php?t=1132119")

---

### Post by clyde9999 on 2009-04-22
Thank you so much Ringi, Works like a charm!!!!


Blessings to you,

Jack:P

---

