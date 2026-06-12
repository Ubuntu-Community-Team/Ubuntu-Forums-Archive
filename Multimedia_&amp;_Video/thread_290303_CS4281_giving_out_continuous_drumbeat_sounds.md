---
title: "CS4281 giving out continuous drumbeat sounds"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by moufranica on 2006-11-01
I have a problem with a CS4281 chipset (Fujitsu). I have followed the "Comprehensive Sound Problems Solution Guide", but it didn't help. I have all the setting correctly done. 

This is the out put of 'aplay -l'
```

**** List of PLAYBACK Hardware Devices ****
card 0: CS4281 [Cirrus Logic CS4281], device 0: CS4281 [CS4281]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

This is output of lspci -v
```

0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
        Subsystem: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub]
        Flags: bus master, fast devsel, latency 0

0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: Fujitsu Limited.: Unknown device 10a5
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 9
        Memory at 14000000 (32-bit, prefetchable) [size=64M]
        Memory at 11600000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [dc] Power Management version 1

0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=09, sec-latency=32
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: 11000000-112fffff
        Prefetchable memory behind bridge: 18000000-1bffffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Intel Corporation 82801AA IDE
        Flags: bus master, medium devsel, latency 0
        I/O ports at 8080 [size=16]

0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation 82801AA USB
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 8040 [size=32]

0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
        Subsystem: Intel Corporation 82801AA SMBus
        Flags: medium devsel, IRQ 11
        I/O ports at 8000 [size=16]

0000:01:00.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
        Subsystem: Fujitsu Limited.: Unknown device 1070
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at 11000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 7000 [size=64]
        Memory at 11100000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [dc] Power Management version 2

0000:01:01.0 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Fujitsu Limited. Lifebook C6155
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at f0000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 18000000-19fff000 (prefetchable)
        Memory window 1: 12000000-13fff000
        I/O window 0: 00007400-000074ff
        I/O window 1: 00007800-000078ff
        16-bit legacy interface ports at 0001

0000:01:01.1 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Fujitsu Limited. Lifebook C6155
        Flags: bus master, medium devsel, latency 168, IRQ 255
        Memory at f1000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 1a000000-1bfff000 (prefetchable)
        Memory window 1: 1c000000-1dfff000
        I/O window 0: 00007c00-00007cff
        I/O window 1: 00001000-000010ff
        16-bit legacy interface ports at 0001

0000:01:07.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
        Subsystem: Fujitsu Limited. Crystal CS4281 PCI Audio
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at 11001000 (32-bit, non-prefetchable) [size=4K]
        Memory at 11010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2

```

My mic however works, and I can hear back what I say very cleary in the headphone. Totem doesn't work, neither does rhymebox. Sound recorder doesnt' work. I get a message "Your audio capture settings are invalid. Please correct them in the Multimedia settings.". Which is not helpfull at all. Please help

---

