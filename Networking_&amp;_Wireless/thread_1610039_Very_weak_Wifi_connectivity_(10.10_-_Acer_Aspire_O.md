---
title: "Very weak Wifi connectivity (10.10 - Acer Aspire One 110AB)"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by playaz on 2010-10-31
Hi guys,

I have an Acer Aspire One A110AB (bought new in late 2008) - I've since upgraded it Ubuntu Netbook Remix 10.10 (Maverick) and I'm having lots of issues with the wireless, it seems very flaky and unreliable.

I have been told to post the following info to aid in finding a solution (sorry if I've done this wrong, I'm no expert with Ubuntu)

If nobody has a suitable solution, i'd probably just buy a USB wireless adapter - any recommendations?

Express Memory Controller Hub [8086:27ac] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=09 <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 78480000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 60c0 [size=8]
	Memory at 60000000 (32-bit, prefetchable) [size=256M]
	Memory at 78500000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, fast devsel, latency 0
	Memory at 78400000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at 78540000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 77300000-783fffff
	Prefetchable memory behind bridge: 0000000070000000-0000000070ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: 76300000-772fffff
	Prefetchable memory behind bridge: 0000000071000000-00000000720fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 75200000-762fffff
	Prefetchable memory behind bridge: 0000000072100000-00000000730fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 74100000-751fffff
	Prefetchable memory behind bridge: 0000000073100000-00000000740fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 6080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 6060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 6040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 6020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at 78544400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device [1025:015b]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02) (prog-if 80 [Master])
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 60a0 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: medium devsel, IRQ 11
	I/O ports at 6000 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at 3000 [size=256]
	Memory at 71010000 (64-bit, prefetchable) [size=4K]
	Memory at 71000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 71020000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Count=2 Masked-
	Capabilities: [cc] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 04-00-00-00-ff-ff-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e008]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 75200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Count=1 Masked-
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Kernel driver in use: ath5k
	Kernel modules: ath5k

04:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 74100300 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 73100000 [disabled] [size=32K]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: fast devsel, IRQ 19
	Memory at 74100200 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel modules: sdhci-pci

04:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 74100100 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

04:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
	Subsystem: Acer Incorporated [ALI] Device [1025:015b]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 74100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-

---

