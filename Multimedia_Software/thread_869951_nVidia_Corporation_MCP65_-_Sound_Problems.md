---
title: "nVidia Corporation MCP65 - Sound Problems"
date: 2008-07-25
forum: Multimedia Software
---

### Post by mr_abz2k8 on 2008-07-25
Hi all,

I'm new to these forums, presenting with a serious problem which is making me consider taking 5 steps back to Vista :shock:

I recently bought a second hand HP Pavilion dv9500em from a friend. It came with Vista Home Premium and all was fine... Until I figured "Lets try Linux!"

So I grabbed the Live CD for Hardy Heron (8.04), installed well and good. I was in bliss, technically speaking.

Then one thing became apparent.

Playing mp3's were fine for about 30mins or so, then leave the laptop for a while to return with... Lo and behold - no sound. So after poking around the settings, to no avail the only thing I could possibly think of is to update and reboot (as most users tell you to do that).

Sound magically blares from speakers, again for a short time and disappears again after a short while. After scouring the forums while following many FAQs and guides found on these graceful pages, nothing here or Google mentions my sound card. *Sulks*

Admittedly, I poked around trying to get DVD's to work on totem-xine.

Apart from that, any suggestions are greatly appreciated.

Techy specs:
AMD Turion64 x2 @ 2.1GHz
nVidia GeForce 8400GS
nVidia Corporation MCP65 High Definition Audio
nVidia PCI bridge

results from "lspci -v"
```
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 1d00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 255
	Memory at f2200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at f2486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at f2488000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f2487000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30e0 [size=8]
	Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f2480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
	Memory behind bridge: f2100000-f21fffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f03c:30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: <access denied>

00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 30f8 [size=8]
	I/O ports at 30ec [size=4]
	I/O ports at 30f0 [size=8]
	I/O ports at 30e8 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at f2484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f2000000-f20fffff
	Prefetchable memory behind bridge: 00000000f2500000-00000000f25fffff
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: f0000000-f1ffffff
	Prefetchable memory behind bridge: 00000000f2600000-00000000f27fffff
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 1367
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f2000000 (64-bit, non-prefetchable) [size=16K]
	Memory at f2500000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 4000 [size=128]
	Capabilities: <access denied>

07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f2100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at f2100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f2100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f2101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f


```

If any other info is needed, please feel free to PM!

Thanks again if you read this far :)

---

### Post by mr_abz2k8 on 2008-07-26
I figured the solution to the problem, thought I'd add it here, in the slight chance it may help some one.

Under System > Preferences > Sound, select your device for sound and other options. A bit of a n&#369;b problem, but I didnt have a clue!

---

