---
title: "compatibility with wireless adaptor"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by jlundberg on 2006-02-20
I have a D-Link, WNA-1330 wireless adaptor for my toshiba laptop, but I am not certain where I can get the drivers to support it for Ubuntu.  The D-Link website does not list any support for this adaptor with Linux.  I hope I am not screwed and do not need to buy another adaptor!

---

### Post by byen on 2006-02-20
well.. for such cases you can easily configure your hardware using a tool called ndiswrapper. Have a look around ... there are many threads showing you how you could use ndiswrapper to configure your wireless hardware.
I see this is your first post. Welcome to Ubuntu.

---

### Post by Lambert on 2006-02-20
These are new devices from d-link for 2006. so there's not much info on these.

Post output of this terminal command.

```
sudo lspci -v
```

This will tell us what chipset is in the device and we can proceed from there.

---

### Post by jlundberg on 2006-02-20
Thanx guys I will have a crack at it from the Live boot and see what it is...

---

### Post by pfs01089 on 2006-07-28
Just wondering if you had any luck with the WNA-1330, im getting a friends older laptop and would like to go wireless, im looking at either the WNA-1330 or WNA-2330, just curious as to how your experience is going with the 1330.

P

---

### Post by Spono on 2007-06-13
> **Lambert said:**
> These are new devices from d-link for 2006. so there's not much info on these.

Post output of this terminal command.

```
sudo lspci -v
```

This will tell us what chipset is in the device and we can proceed from there.

I have the same issues getting that wireless card to work, so I'll go ahead and post the output of that command:

```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Dell Unknown device 015f
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [40] Vendor Specific Information
        Capabilities: [a0] AGP version 2.0

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Dell Unknown device 015f
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Dell Unknown device 015f
        Flags: bus master, fast devsel, latency 0

00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 015f
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 015f
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at bf40 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 015f
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 015f
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f6000000-fbffffff
        Prefetchable memory behind bridge: 40000000-43ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 015f
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at bfa0 [size=16]
        Memory at 44000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 015f
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at b800 [size=256]
        I/O ports at bc40 [size=64]
        Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Conexant Unknown device 5422
        Flags: medium devsel, IRQ 17
        I/O ports at b400 [size=256]
        I/O ports at b080 [size=128]
        Capabilities: [50] Power Management version 2

01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 015f
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 21
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        [virtual] Expansion ROM at fd000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 3.0

02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Dell Unknown device 015f
        Flags: bus master, fast devsel, latency 32, IRQ 17
        Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
        Subsystem: Dell Unknown device 015f
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at f6000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 48000000-4bfff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        16-bit legacy interface ports at 0001

02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 015f
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at faffd800 (32-bit, non-prefetchable) [size=2K]
        Memory at faff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc Unknown device 3a1c
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at 48000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

```

---

