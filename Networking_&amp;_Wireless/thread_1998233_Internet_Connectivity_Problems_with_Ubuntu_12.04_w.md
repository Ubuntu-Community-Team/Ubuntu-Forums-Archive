---
title: "Internet Connectivity Problems with Ubuntu 12.04 with Wired and Wifi Connections"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by ChemMeister on 2012-06-06
Hi,

Ever since I have installed 12.04 (clean install not an upgrade), i have been having a drop in the Internet connection. The drop in the connection can be anything from 15 seconds to about 3 mins, and then the connection comes back. This behavior happens while I am actively browsing the Internet, or if I wake up the computer and open Firefox (sometimes I have connection and sometimes I don't) . Please note that when the internet connection is on, it is not slow (as speedtest.net results show)

In the beginning, I thought it was a problem with the driver r8169 for my RTL8111/8168B Ethernet card, so I downloaded the r8168  from Realtek website, followed the detailed instructions (blacklisted r8169, changed the file to '.bsh' ...), but still the same problem persisted.

So I switched to a wireless connection, and I got the same problem with internet connection dropping randomly. 

Any ideas? Thanks in advance

Output from 'lspci -v'

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Dell Device 04a7
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f8000000-fa0fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dbffffff
    Capabilities: [88] Subsystem: Dell Device 04a7
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f4000000-f60fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cbffffff
    Capabilities: [88] Subsystem: Dell Device 04a7
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Dell Device 04a7
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at f6108000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device 04a7
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f6107000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: Dell Device 04a7
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at f6100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fa400000-fa4fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device 04a7
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Prefetchable memory behind bridge: 00000000dc100000-00000000dc1fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device 04a7
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fa300000-fa3fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device 04a7
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fa200000-fa2fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device 04a7
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device 04a7
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f6106000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
    Subsystem: Dell Device 04a7
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 05)
    Subsystem: Dell Device 04a7
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at f6105000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Dell Device 04a7
    Flags: medium devsel, IRQ 5
    Memory at f6104000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation Device 0dc5 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device 085b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Memory at d8000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at fa000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

01:00.1 Audio device: NVIDIA Corporation GF106 High Definition Audio Controller (rev a1)
    Subsystem: NVIDIA Corporation Device 085b
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fa080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

02:00.0 VGA compatible controller: NVIDIA Corporation Device 0dc5 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device 085b
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f4000000 (32-bit, non-prefetchable) [size=32M]
    Memory at c0000000 (64-bit, prefetchable) [size=128M]
    Memory at c8000000 (64-bit, prefetchable) [size=64M]
    I/O ports at d000 [size=128]
    Expansion ROM at f6000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

02:00.1 Audio device: NVIDIA Corporation GF106 High Definition Audio Controller (rev a1)
    Subsystem: NVIDIA Corporation Device 085b
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f6080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: Dell Device 04a7
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fa400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
    Capabilities: [150] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Dell Device 04a7
    Flags: bus master, fast devsel, latency 0, IRQ 51
    I/O ports at c000 [size=256]
    Memory at dc104000 (64-bit, prefetchable) [size=4K]
    Memory at dc100000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 03-00-00-00-68-4c-e0-00
    Kernel driver in use: r8168
    Kernel modules: r8168

05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (rev 01) (prog-if 10 [OHCI])
    Subsystem: Dell Device 04a7
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fa300000 (64-bit, non-prefetchable) [size=2K]
    I/O ports at b000 [size=256]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable+ 64bit+
    Capabilities: [98] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [130] Device Serial Number 00-10-dc-ff-ff-cf-56-1a
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

06:00.0 SATA controller: JMicron Technology Corp. JMB362 SATA Controller (rev 10) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 04a7
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at a040 [size=8]
    I/O ports at a030 [size=4]
    I/O ports at a020 [size=8]
    I/O ports at a010 [size=4]
    I/O ports at a000 [size=16]
    Memory at fa210000 (32-bit, non-prefetchable) [size=512]
    Capabilities: [8c] Power Management version 3
    Capabilities: [50] Express Legacy Endpoint, MSI 00
    Kernel driver in use: ahci


```

Note that my wireless card is not showing, I have the Ralink 3390 card (which apparently does not show up on Ubuntu for some reason), however I am able to connect to wireless network and connect to the internet (when it is working)

---

### Post by praseodym on 2012-06-06
Uninstall the package "resolvconf" and reboot.

---

