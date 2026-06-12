---
title: "Natty Wireless Problem"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by M3VDJ on 2011-07-16
Hi all,

Currently there a lot of threads going round talking about wireless problems with the latest release of Ubuntu (Natty), and i'm afraid this is another one!

I recently brought a new laptop (MSI CR620) and installed Ubuntu 10.10 and then updated it to Ubuntu 11. The wireless was working fine until yesterday when in the process of installing some software, I performed an update... then the problems started.
Initially, all was well, but after shutting the lid on my laptop (consequently putting it into hibernation), and reopening the lid a short while later, the wireless refused to work - a reboot worked fortunately. However since then, the wireless has abruptly refused to work completely; sometimes after turning the laptop on it does not load the driver, others it loads the driver, will ask for the appropriate password for the network and then refuse to establish a solid connection.
On a side note, I have also had the touchpad drop out randomly. Again, a restart appears to fix this problem.
Whilst struggling to get my laptop to work, I used my older desktop (also running the Ubuntu 11), and it popped up saying it needed updating. Having not used it for a few days, I humbly obliged. This turns out to have been a stupid idea as now it displays the same symptons as my laptop.

As the wireless works flawlessly under XP, I feel somewhat confident in determining that an update that both machines received yesterday is the root of the problem. Having looked at what both systems have installed recently (through the history of Ubuntu Software Centre at least), none of the recent updates match, and none appear to be related to the network subsystem.

I guess my questions would be, what else can I do to narrow down the cause of the problem, where can I find a list of recently published updates, and finally, how do I fix it?

I'm relatively new to Linux, so I'd appreciate it if anyone listing commands for me to reel off to explain what they are and what they do and how it will help, so that when my next problem comes around, I can get somewhat closer to fixing it myself!

Many Thanks,
Aiden

---

### Post by ratcheer on 2011-07-16
The first thing I always check is whether the wireless device is being detected and, if yes, what kernel driver is being loaded for it. Please open a Terminal window, run "sudo lspci -v", and post the output in a reply.

Tim

---

### Post by M3VDJ on 2011-07-16
Thanks for your reply. I have just powered the laptop on, the network has picked up and connected me automatically (did I mention it's an intermittent problem?). However, this is the output you requested:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e080 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f680a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f6808000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f6800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f5400000-f67fffff
    Prefetchable memory behind bridge: 00000000bc000000-00000000bc1fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. Device 1033
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f0400000-f2bfffff
    Prefetchable memory behind bridge: 00000000bc200000-00000000bc3fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. Device 1033
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f4000000-f53fffff
    Prefetchable memory behind bridge: 00000000bc400000-00000000bc5fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f2c00000-f3ffffff
    Prefetchable memory behind bridge: 00000000bc600000-00000000bc7fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. Device 1033
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f6807000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
    Capabilities: [50] Subsystem: Micro-Star International Co., Ltd. Device 1033

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at e070 [size=8]
    I/O ports at e060 [size=4]
    I/O ports at e050 [size=8]
    I/O ports at e040 [size=4]
    I/O ports at e020 [size=32]
    Memory at f6806000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: medium devsel, IRQ 11
    Memory at f6805000 (64-bit, non-prefetchable) [size=256]
    I/O ports at e000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f6804000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

05:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
    Subsystem: Micro-Star International Co., Ltd. Device 6891
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-c6-83-1a-6d-62-6c
    Kernel driver in use: rt2800pci
    Kernel modules: rt2860sta, rt2800pci

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 40
    I/O ports at a000 [size=256]
    Memory at f2c10000 (64-bit, prefetchable) [size=4K]
    Memory at f2c00000 (64-bit, prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=2 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-36-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

Regards,

Aiden

---

### Post by M3VDJ on 2011-07-16
Tim, i've found a spanner in the works...

The above output is whilst I had mains power plugged in. The output below is from when I had the mains unplugged, the connection had dropped and then refused to reconnect. I'd appreciate your thoughts on it...

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e080 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f680a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f6808000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f6800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f5400000-f67fffff
    Prefetchable memory behind bridge: 00000000bc000000-00000000bc1fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. Device 1033
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f0400000-f2bfffff
    Prefetchable memory behind bridge: 00000000bc200000-00000000bc3fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. Device 1033
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f4000000-f53fffff
    Prefetchable memory behind bridge: 00000000bc400000-00000000bc5fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f2c00000-f3ffffff
    Prefetchable memory behind bridge: 00000000bc600000-00000000bc7fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. Device 1033
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f6807000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
    Capabilities: [50] Subsystem: Micro-Star International Co., Ltd. Device 1033

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at e070 [size=8]
    I/O ports at e060 [size=4]
    I/O ports at e050 [size=8]
    I/O ports at e040 [size=4]
    I/O ports at e020 [size=32]
    Memory at f6806000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: medium devsel, IRQ 11
    Memory at f6805000 (64-bit, non-prefetchable) [size=256]
    I/O ports at e000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f6804000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

05:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
    Subsystem: Micro-Star International Co., Ltd. Device 6891
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-c6-83-1a-6d-62-6c
    Kernel driver in use: rt2800pci
    Kernel modules: rt2860sta, rt2800pci

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0, IRQ 40
    I/O ports at a000 [size=256]
    Memory at f2c10000 (64-bit, prefetchable) [size=4K]
    Memory at f2c00000 (64-bit, prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=2 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-36-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 1033
    Flags: bus master, fast devsel, latency 0

Thanks,

Aiden

---

### Post by ratcheer on 2011-07-16
I believe that your problem is occurring because the driver the system is using is rt2800pci, where it should be loading rt2860sta.

There are a hundred threads in this forum about this identical problem. I can try to help you fix it or you can look at some of those threads. Let me know your preference.

Tim

---

### Post by M3VDJ on 2011-07-16
what is the difference between the two? I'm somewhat confused as to why with the PSU plugged into my laptop, I have no problems whatsoever; yet, with the supply removed, the connection is unreliable and slow. This has only occured since I updated the system.
I shall attempt to load the sta driver, and will report back.

Thanks,

Aiden

---

### Post by M3VDJ on 2011-07-16
OK, so I found these instructions on this forum:

as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

i had no problems doing that, but wifi still doesn't work without the PSU. Also, it appears still to be loading the pci driver...

AND, what use to be the wired network now appears as a second wifi connection stating device not ready.

Thanks,

Aiden

---

### Post by M3VDJ on 2011-07-16
Ok, so I ran the following commands:

as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

and then modified the blacklist.conf (modprobe.d) file to block loading the pci driver. Unfortunately, lspci reports loading rt2860 as opposed to rt2860sta. I don't know what difference the sta makes, but I can report that I can now use the wifi without having the power plugged in!

If you feel that I really should be using the sta driver, I would appreciate it if you could guide me through it, but I can cope with this as it is.

Many thanks for all your help!

Aiden

---

### Post by nm_geo on 2011-07-16
M3VDJ

Please mark Solved and here is another link where Chili555 worked on this with additional help.

[http://ubuntuforums.org/showthread.php?t=1749179&page=2](http://ubuntuforums.org/showthread.php?t=1749179&page=2)

---

### Post by M3VDJ on 2011-07-16
nm_geo

Thanks for the link. Before I mark it as solved, I would appreciate it if you or someone else would be able to explain what difference the sta driver makes. I understand what the steps I have taken to fix my problem are as suggested by Tim, but I don't know what the difference between the drivers are (pci and sta).

Best Regards,

Aiden

---

### Post by ratcheer on 2011-07-16
I think you are good to go, now. Mine also says rt2860:

```
06:00.0 Network controller: Ralink corp. Device 3062
    Subsystem: Ralink corp. Device 3062
    Flags: bus master, slow devsel, latency 32, IRQ 19
    Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Kernel driver in use: rt2860
    Kernel modules: rt3562sta, rt2800pci

```

Tim

---

### Post by nm_geo on 2011-07-16
> **M3VDJ said:**
> nm_geo

Thanks for the link. Before I mark it as solved, I would appreciate it if you or someone else would be able to explain what difference the sta driver makes. I understand what the steps I have taken to fix my problem are as suggested by Tim, but I don't know what the difference between the drivers are (pci and sta).

Best Regards,

Aiden

While I am not a Ralink expert by any means.  Having both modules loaded may creates conflicts. Here is some interesting reading.

[http://wiki.debian.org/rt2800pci](http://wiki.debian.org/rt2800pci)


[http://wiki.debian.org/rt2860sta#Ralink_RT2760.2C_RT2790.2C_RT2860.2C_RT2890.2C_RT3090.2C_RT3091.2C_RT3092_devices_.28rt2860sta.29](http://wiki.debian.org/rt2860sta#Ralink_RT2760.2C_RT2790.2C_RT2860.2C_RT2890.2C_RT3090.2C_RT3091.2C_RT3092_devices_.28rt2860sta.29)

---

### Post by ratcheer on 2011-07-17
Interesting, indeed, nm_geo.

So, If I am reading the article correctly, rt2800pci is supposed to be the correct module. It seems strange that it does not work, but the module they were trying to get rid of (rt2860) does work.

Also, the Ralink web site states that the rt2860 driver is the driver to use for this card on Linux. Well, not in so many words, but it is the driver that is downloaded whan you click the link for the 3060 card.

What a mess. I am sticking with the driver that works, but will try to find more info.

Thanks,
Tim

---

### Post by M3VDJ on 2011-07-18
Interesting...

As far as I can tell, the sta driver is practically a beta, and was removed from the kernel (leading me to wonder why it is still on my system).

Thanks for all the help guys, atleast now I've got a better idea of what to do when it goes wrong next time!

Thanks,

Aiden

---

### Post by ratcheer on 2011-07-18
More info about the "which driver is correct?" question:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/796230](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/796230)

This was last updated June 26 and specifically is about EEPC systems, but it contains a lot of info about the driver and firmware situation.

It really does seem that rt2800pci is the "correct" driver. Wouldn't it be nice if it actually worked?

Tim

---

