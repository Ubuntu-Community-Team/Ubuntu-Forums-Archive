---
title: "frun xubuntu to ubuntu studio upgrade lost wireless"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by dpugh5 on 2013-05-15
so i upgraded from xubuntu 12.04 x64 to ubuntu studio 13.04. on xubuntu i had wireless after i upgraded I lost wireless. I am a beginner and I have went through other posts and tried different things with no result. If possible I would like to learn how to do this rather than using google. I have an acer aspire 7750g

---

### Post by dpugh5 on 2013-05-15
~$ lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c0300000-c12fffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at c1304000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at c130a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at c1300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: c0200000-c02fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: c0100000-c01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Memory behind bridge: c0000000-c00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c1309000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 49
    I/O ports at 4048 [size=8]
    I/O ports at 405c [size=4]
    I/O ports at 4040 [size=8]
    I/O ports at 4058 [size=4]
    I/O ports at 4020 [size=32]
    Memory at c1308000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: medium devsel, IRQ 7
    Memory at c1306000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4000 [size=32]

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [Radeon HD 6600M/6700M/7600M Series] (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at c0300000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 3000 [size=256]
    Expansion ROM at c0340000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at c0320000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

02:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 54
    Memory at c0200000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c

03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n
    Subsystem: Foxconn International, Inc. Device e040
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at c0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Acer Incorporated [ALI] Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at c0000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

---

