---
title: "second BRCM5723 not seen"
date: 2012-02-16
forum: Networking &amp; Wireless
---

### Post by shadowryder on 2012-02-16
I have an HP Proliant server with the remote access card installed which gives me a second Broadcom 5723 ethernet device.

I installed Ubuntu server 11.10 x64 bit and see only one device is listed.
lspci -v reveals only a single device, but discover shows the second.  How can I get the second 5723 enumerated?

output from lspci and discover below:

Thanks, in advance.

-Eric

eric@server:/sys/bus/pci/devices/0000:03:00.0$ sudo lspci -v
[sudo] password for eric: 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe000000-fe8fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 1609
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [110] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe900000-fe9fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 1609
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [110] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 42
	I/O ports at d000 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at b000 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at 9000 [size=16]
	Memory at fdfffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] MSI: Enable+ Count=1/4 Maskable- 64bit+
	Capabilities: [70] SATA HBA v1.0
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fdffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fdfff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fdffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fdfff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fdffc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Flags: fast devsel
	Kernel driver in use: amd64_edac
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Flags: fast devsel

01:00.0 PCI bridge: ASPEED Technology, Inc. AST1150 PCI-to-PCI Bridge (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=01, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe000000-fe8fffff
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Power Management version 3
	Capabilities: [80] Express PCI/PCI-X Bridge, MSI 00
	Capabilities: [a4] Subsystem: ASPEED Technology, Inc. AST1150 PCI-to-PCI Bridge
	Capabilities: [100] Virtual Channel
	Kernel modules: shpchp

02:00.0 VGA compatible controller: ASPEED Technology, Inc. ASPEED Graphics Family (rev 10) (prog-if 00 [VGA controller])
	Subsystem: ASPEED Technology, Inc. ASPEED Graphics Family
	Flags: medium devsel, IRQ 10
	Memory at fe000000 (32-bit, non-prefetchable) [size=8M]
	Memory at fe8e0000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at e800 [size=128]
	Expansion ROM at fe8d0000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3

03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)
	Subsystem: Hewlett-Packard Company NC107i Integrated PCI Express Gigabit Server Adapter
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
	Capabilities: [40] Vital Product Data
	Capabilities: [60] Vendor Specific Information: Len=6c <?>
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [cc] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 2c-76-8a-ff-fe-ab-dc-ba
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

eric@server:/sys/bus/pci/devices/0000:03:00.0$ sudo discover -v
Loading XML data... ata pci pcmcia scsi usb Done
Scanning buses... ata pci pcmcia scsi usb Done
Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe 
Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe 
ASPEED Technology, Inc. ASPEED Graphics Family 
unknown unknown 
Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control 
Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control 
Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller 
Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map 
Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration 
ATI Technologies Inc SB700/SB800 USB EHCI Controller 
ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
ATI Technologies Inc SBx00 PCI to PCI Bridge 
ATI Technologies Inc SB700/SB800 LPC host controller 
ATI Technologies Inc SB700/SB800 IDE Controller 
ATI Technologies Inc SBx00 SMBus Controller 
ATI Technologies Inc SBx00 SMBus Controller 
ATI Technologies Inc SBx00 SMBus Controller 
ATI Technologies Inc SBx00 SMBus Controller 
ATI Technologies Inc SBx00 SMBus Controller 
ATI Technologies Inc SB700/SB800 USB EHCI Controller 
ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
ATI Technologies Inc SB700/SB800 USB EHCI Controller 
ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] 
Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) 
Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) 
Advanced Micro Devices [AMD] RS780 Host Bridge Alternate 

jic:

eric@server:/sys/bus/pci/devices/0000:03:00.0$ discover --version
discover 2.1.2
eric@server:/sys/bus/pci/devices/0000:03:00.0$ lspci --version
lspci version 3.1.7

---

### Post by mörgæs on 2012-02-17
Moved to the network forum.

---

### Post by shadowryder on 2012-02-18
ok - so looks like I'm not setting off any ah ha ideas for anyone.  Let me ask a different question:

Is there anyone with this setup with two of these Broadcom Ethernet ports that has them both working?

BTW - I did come up with one idea: BIOS issue, but I've verified I have the latest BIOS so that did not the resolve problem.

I'll wait a little longer and see if anyone has any ideas.  Since this is a new install, it wont hurt to try new things.  Perhaps I'll try the 32 bit version and see if I see different results.

Thanks again.

-Eric

---

### Post by shadowryder on 2012-02-19
Same results with the 11.10 32 bit server edition. :(

---

### Post by shadowryder on 2012-02-20
Not resolved but at least understood.  Second port is an IPMI remote access port.

---

