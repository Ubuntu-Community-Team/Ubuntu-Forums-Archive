---
title: "No sound; AMD Unknown device 2093 (rev 01)"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by neocorate on 2007-09-30
Hello,

  I have installed Xubuntu Dapper on a [fit-pc]("http://www.fit-pc.com").  Everything is working except for sound.  Can anybody help me?

Here are the results of trying to go through the  [comprehensive sound problem solution guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=2093"):

```
$ aplay -l
aplay: device_list:221: no soundcards found...

$ lspci -v
0000:00:01.0 Host bridge: Advanced Micro Devices [AMD]: Unknown dev ice 2080 (rev 31)
        Subsystem: Advanced Micro Devices [AMD]: Unknown device 208 0
        Flags: bus master, 66MHz, medium devsel, latency 248

0000:00:01.1 VGA compatible controller: Advanced Micro Devices [AMD ]: Unknown device 2081 (prog-if 00 [VGA])
        Subsystem: Advanced Micro Devices [AMD]: Unknown device 208 1
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
        Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e1000000 (32-bit, non-prefetchable) [size=16K]
        Memory at e1004000 (32-bit, non-prefetchable) [size=16K]
        Memory at e1008000 (32-bit, non-prefetchable) [size=16K]
        Memory at e100c000 (32-bit, non-prefetchable) [size=16K]

0000:00:01.2 Entertainment encryption device: Advanced Micro Device s [AMD]: Unknown device 2082
        Subsystem: Advanced Micro Devices [AMD]: Unknown device 208 2
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
        Memory at e1010000 (32-bit, non-prefetchable) [size=16K]

0000:00:09.0 CardBus bridge: Texas Instruments PCI1520 PC card Card bus Controller (rev 01)
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=01, subordinate=04, sec-latency= 176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

0000:00:09.1 CardBus bridge: Texas Instruments PCI1520 PC card Card bus Controller (rev 01)
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 90001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=05, subordinate=08, sec-latency= 176
        Memory window 0: 24000000-25fff000 (prefetchable)
        Memory window 1: 26000000-27fff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. R TL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at f800 [size=256]
        Memory at e1014000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. R TL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at f400 [size=256]
        Memory at e1014100 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:0f.0 ISA bridge: Advanced Micro Devices [AMD]: Unknown devi ce 2090 (rev 03)
        Subsystem: Advanced Micro Devices [AMD]: Unknown device 209 0
        Flags: 66MHz, medium devsel
        I/O ports at f000 [size=8]
        I/O ports at ec00 [size=256]
        I/O ports at e800 [size=64]
        I/O ports at e400 [size=32]
        I/O ports at e000 [size=128]
        I/O ports at 9c40 [size=64]

0000:00:0f.2 IDE interface: Advanced Micro Devices [AMD]: Unknown d evice 209a (rev 01) (prog-if 80 [Master])
        Subsystem: Advanced Micro Devices [AMD]: Unknown device 209 a
        Flags: bus master, 66MHz, medium devsel, latency 0
        I/O ports at d800 [size=16]

0000:00:0f.3 Multimedia audio controller: Advanced Micro Devices [A MD]: Unknown device 2093 (rev 01)
        Subsystem: Advanced Micro Devices [AMD]: Unknown device 209 3
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 10
        I/O ports at d400 [size=128]

0000:00:0f.4 USB Controller: Advanced Micro Devices [AMD]: Unknown device 2094 (rev 02) (prog-if 10 [OHCI])
        Subsystem: Advanced Micro Devices [AMD]: Unknown device 209 4
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
        Memory at e1015000 (32-bit, non-prefetchable) [size=4K]

0000:00:0f.5 USB Controller: Advanced Micro Devices [AMD]: Unknown device 2095 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Advanced Micro Devices [AMD]: Unknown device 209 5
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
        Memory at e1016000 (32-bit, non-prefetchable) [size=4K]

0000:00:11.0 Bridge: Integrated Technology Express, Inc. IT8888F PC I to ISA Bridge with SMB (rev 03)
        Flags: bus master, medium devsel, latency 0


```

---

### Post by neocorate on 2007-10-02
Pretty please with a cherry on top?](*,)

---

