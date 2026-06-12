---
title: "the not fun, of having 2 graphic boards"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by metaloid on 2006-08-27
I've a sony vaio sz2HP. This piece of hardware has 2 graphic boards: one nvidia and one i915. I can make the switching between xorg configurations at boot time, no problem.The problem seems to be that, the i810 driver doesn't have glx support when I install the nvidia-glx package. When I remove the nvidia-glx and reinstall libgl1-mesa-dri and libgl1-mesa glx extensions are brought back to the i915 card. Is there any way of having a peaceful coexistence? :confused: ]

---

### Post by tseliot on 2006-08-27
Sure. Can you post the ouput of this command?
```
lspci -v
```

---

### Post by metaloid on 2006-08-28
Here it is:
> 0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at dc200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, fast devsel, latency 0
        Memory at dc280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at dc340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1f00000
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Memory behind bridge: dc100000-dc1fffff
        Capabilities: <available only to root>

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3f00000
        Capabilities: <available only to root>

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5f00000
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 1860 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 1880 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 0, IRQ 66
        Memory at dc544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=09, subordinate=0d, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000051f00000
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]

0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 58
        I/O ports at 18d0 [size=8]
        I/O ports at 18c4 [size=4]
        I/O ports at 18c8 [size=8]
        I/O ports at 18c0 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at dc544400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: medium devsel
        I/O ports at 18e0 [size=32]

0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)        Subsystem: Intel Corporation: Unknown device 1051
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at dc100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 15)
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, fast devsel, latency 0, IRQ 185
        Memory at d8000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 3000 [size=256]
        Capabilities: <available only to root>

0000:09:04.0 CardBus bridge: Texas Instruments: Unknown device 8039
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 168, IRQ 201
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 52000000-53fff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

0000:09:04.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a (prog-if 10 [OHCI])
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 32, IRQ 74
        Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:09:04.2 Mass storage controller: Texas Instruments: Unknown device 803b
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, medium devsel, latency 57, IRQ 10
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>


---

