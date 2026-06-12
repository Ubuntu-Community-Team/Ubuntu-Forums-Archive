---
title: "strange audio hiccup."
date: 2009-04-21
forum: Multimedia Software
---

### Post by jackechanprime on 2009-04-21
ok, i'm not that tech savvy, but i'm pretty sure this isn't supposed to happen. my computer will only play audio from one running application at a time. i don't know if that's a driver issue... or... something else? i think... i hear the term audio channels around somewhere... but at this point i'm pretty much appealing to the gods. (namely you guys)

oh, right. system specs and stuff. campaq presario C700. ubuntu, up to date version.

lspci -v spits all this junk out. O_o no clue which one's the 'sound card' as those two words don't appear anywhere in all that gibberish.. :\ though it does appear to be telling me waht my graphics and wireless cards are...

???O_O???
jack


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 51000000 (64-bit, non-prefetchable) [size=1M]
	Memory at 40000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 30d0 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, fast devsel, latency 0
	Memory at 51100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Conexant Presario C700
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 52400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 51300000-523fffff
	Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 3060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 3040 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at 52404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 51200000-512fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 30a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 222
	I/O ports at 30b8 [size=8]
	I/O ports at 30dc [size=4]
	I/O ports at 30b0 [size=8]
	I/O ports at 30d8 [size=4]
	I/O ports at 3020 [size=32]
	Memory at 52404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: medium devsel, IRQ 11
	Memory at 52404c00 (32-bit, non-prefetchable) [size=256]
	I/O ports at 3000 [size=32]

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 51300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Unknown device 30d9
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at 1000 [size=256]
	Memory at 51200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

---

### Post by jackechanprime on 2009-04-23
bump

---

### Post by jackechanprime on 2009-04-25
bump for the day.

---

