---
title: "you give me sound i ditch the windows vista"
date: 2008-06-29
forum: Multimedia Software
---

### Post by satish.bty on 2008-06-29
hi all respected friends.intalled ubuntu 8 onmy lenovo3000 n200.my sound card was also listed .HDA intel ALC 861/VD.BUT I DID NOT GOT ANY SOUND. I tried to solve with some threas but i think i messed up.and in tthe end in alsa mixer it shows  [COLOR="Red"]Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
[/COLOR]
.you help me out please. i am newbie .i swear i will never look to windows after this. thanks in advance.awaiting for your reply.

---

### Post by shmuel88 on 2008-06-29
Hi,

Not sure if this helps but on my laptop the speakers were actually under surround, which was muted (I think it is something to do with HD audio). To fix it I opened up volume control, then went to the preferences and ticked surround to be visible (headphones were front), and unmuted it.

It could be something similar on yours.

Hope that helps,
Sam

---

### Post by satish.bty on 2008-06-29
no it wont work pls help me out

---

### Post by Pjotr123 on 2008-06-29
This will probably do the job:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 6 )

You appear to have the same sound chipset.

---

### Post by satish.bty on 2008-06-29
> **Pjotr123 said:**
> This will probably do the job:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 6 )

You appear to have the same sound chipset.
not working yet and i feel miserable

---

### Post by satish.bty on 2008-06-30
no help yet??? .people pls get me out of it.!!!

---

### Post by satish.bty on 2008-06-30
Hub (rev 0c)
	Subsystem: Lenovo Unknown device 383c
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Unknown device 383e
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Lenovo Unknown device 383e
	Flags: bus master, fast devsel, latency 0
	Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo Unknown device 3846
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo Unknown device 3847
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Lenovo Unknown device 3849
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fc504000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Unknown device 384e
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: c8000000-c9ffffff
	Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo Unknown device 3843
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo Unknown device 3844
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo Unknown device 3845
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Lenovo Unknown device 3848
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at fc504400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
	Memory behind bridge: fc200000-fc2fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Lenovo Unknown device 3840
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo Unknown device 386d
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Lenovo Unknown device 3841
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 1c00 [size=8]
	I/O ports at 18f4 [size=4]
	I/O ports at 18f8 [size=8]
	I/O ports at 18f0 [size=4]
	I/O ports at 18e0 [size=16]
	I/O ports at 18d0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Lenovo Unknown device 3842
	Flags: medium devsel, IRQ 10
	Memory at 68000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945BG Network Connection
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
	Subsystem: Lenovo Unknown device 3861
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at c8000000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Lenovo Unknown device 3829
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at fc200000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
	Subsystem: Lenovo Unknown device 382a
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at fc200800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
	Subsystem: Lenovo Unknown device 382c
	Flags: medium devsel, IRQ 11
	Memory at fc200c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
	Subsystem: Lenovo Unknown device 382d
	Flags: medium devsel, IRQ 11
	Memory at fc201000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f
[COLOR="Red"]**this is what it shows pls get me ut of it**[/COLOR]

---

