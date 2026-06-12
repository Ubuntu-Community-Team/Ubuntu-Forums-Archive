---
title: "Tv Tuner Help"
date: 2010-02-08
forum: Multimedia Software
---

### Post by ma5t3rw1tt on 2010-02-08
Hello everyone,
I was wondering if it was possible to watch some tv on linux and if so what software would I need. I have searched google for linux tv and nothing good really shows up.

I am using the following:

Linux Mint 8
This Tv Tuner: [http://www.amazon.com/Sabrent-TV-USB20-Capture-Remote-Control/dp/B0007LBMR2](http://www.amazon.com/Sabrent-TV-USB20-Capture-Remote-Control/dp/B0007LBMR2)

I was wondering if anyone could possibly help me out with this and maybe let me know what kind of software I could use to get this thing up and running. Please & Thank you.

---

### Post by xc3RnbFO8P on 2010-02-08
.

---

### Post by Jose Catre-Vandis on 2010-02-08
1. Plug it in to your linux PC

2. Open up a terminal

3. Type the following commands and post back here the relevant TV output (if any):
```
lsusb
```
```
sudo lspci -v
```
```
dmesg
```
There should be some good stuff from the 3rd command

Don't expect TV to burst into life, we are just finding out what card it has and what firmware we need, if any.

---

### Post by ma5t3rw1tt on 2010-02-08
> **Jose Catre-Vandis said:**
> 1. Plug it in to your linux PC

2. Open up a terminal

3. Type the following commands and post back here the relevant TV output (if any):
```
lsusb
``````
sudo lspci -v
``````
dmesg
```There should be some good stuff from the 3rd command

Don't expect TV to burst into life, we are just finding out what card it has and what firmware we need, if any.

-------
Well here is what you asked for starting with the first command all the way to the 3rd command.

> 
mint@mint ~ $ lsusb
Bus 004 Device 002: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 6000:0001  
Bus 001 Device 004: ID 1058:0702 Western Digital Technologies, Inc. Passport External HDD
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> 
mint@mint ~ $ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Dell Device 01d8
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Dell Device 01d8
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at eff8 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Dell Device 01d8
    Flags: bus master, fast devsel, latency 0
    Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 01d8
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    Memory behind bridge: dfd00000-dfdfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Dell Device 01d8
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dfa00000-dfcfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Dell Device 01d8
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
    Subsystem: Dell Device 01d8
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at bf80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
    Subsystem: Dell Device 01d8
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at bf60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
    Subsystem: Dell Device 01d8
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at bf40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
    Subsystem: Dell Device 01d8
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at bf20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
    Subsystem: Dell Device 01d8
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    Memory behind bridge: df900000-df9fffff
    Capabilities: [50] Subsystem: Dell Device 01d8

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
    Subsystem: Dell Device 01d8
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
    Subsystem: Dell Device 01d8
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at bfa0 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
    Subsystem: Dell Device 01d8
    Flags: medium devsel, IRQ 4
    I/O ports at 10c0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
    Subsystem: Dell Device 01d8
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at df9fe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: b44
    Kernel modules: b44

02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10)
    Subsystem: Dell Device 01d8
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at df9fd800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
    Subsystem: Dell Device 01d8
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at df9fd400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
    Subsystem: Dell Device 01d8
    Flags: medium devsel, IRQ 11
    Memory at df9fd500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc

02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
    Subsystem: Dell Device 01d8
    Flags: medium devsel, IRQ 11
    Memory at df9fd600 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2

02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Dell Device 0007
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at dfdfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 2
    Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb


> 
[    0.084770] ACPI: Using IOAPIC for interrupt routing
[    0.093078] ACPI: No dock devices found.
[    0.106095] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.106247] pci 0000:00:02.0: reg 10 32bit mmio: [0xdff00000-0xdff7ffff]
[    0.106253] pci 0000:00:02.0: reg 14 io port: [0xeff8-0xefff]
[    0.106259] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]
[    0.106264] pci 0000:00:02.0: reg 1c 32bit mmio: [0xdfec0000-0xdfefffff]
[    0.106307] pci 0000:00:02.1: reg 10 32bit mmio: [0xdff80000-0xdfffffff]
[    0.106428] pci 0000:00:1b.0: reg 10 64bit mmio: [0xdfebc000-0xdfebffff]
[    0.106491] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.106552] pci 0000:00:1b.0: PME# disabled
[    0.106694] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.106755] pci 0000:00:1c.0: PME# disabled
[    0.106899] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.106960] pci 0000:00:1c.1: PME# disabled
[    0.107106] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.107167] pci 0000:00:1c.3: PME# disabled
[    0.107286] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.107352] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
[    0.107419] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
[    0.107485] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
[    0.107556] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80000-0xffa803ff]
[    0.107621] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.108006] pci 0000:00:1d.7: PME# disabled
[    0.108236] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.108243] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.108320] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.108382] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.108460] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.108601] pci 0000:00:1f.2: reg 10 io port: [0x1f0-0x1f7]
[    0.108610] pci 0000:00:1f.2: reg 14 io port: [0x3f4-0x3f7]
[    0.108618] pci 0000:00:1f.2: reg 18 io port: [0x170-0x177]
[    0.108627] pci 0000:00:1f.2: reg 1c io port: [0x374-0x377]
[    0.108636] pci 0000:00:1f.2: reg 20 io port: [0xbfa0-0xbfaf]
[    0.108673] pci 0000:00:1f.2: PME# supported from D3hot
[    0.108732] pci 0000:00:1f.2: PME# disabled
[    0.108847] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.109117] pci 0000:0c:00.0: reg 10 32bit mmio: [0xdfdfc000-0xdfdfffff]
[    0.109406] pci 0000:0c:00.0: supports D1 D2
[    0.109530] pci 0000:00:1c.1: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]
[    0.109596] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.109602] pci 0000:00:1c.3: bridge 32bit mmio: [0xdfa00000-0xdfcfffff]
[    0.109611] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xd0000000-0xd01fffff]
[    0.109655] pci 0000:02:00.0: reg 10 32bit mmio: [0xdf9fe000-0xdf9fffff]
[    0.109713] pci 0000:02:00.0: supports D1 D2
[    0.109716] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109778] pci 0000:02:00.0: PME# disabled
[    0.109873] pci 0000:02:01.0: reg 10 32bit mmio: [0xdf9fd800-0xdf9fdfff]
[    0.109936] pci 0000:02:01.0: supports D1 D2
[    0.109939] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110000] pci 0000:02:01.0: PME# disabled
[    0.110096] pci 0000:02:01.1: reg 10 32bit mmio: [0xdf9fd400-0xdf9fd4ff]
[    0.110158] pci 0000:02:01.1: supports D1 D2
[    0.110160] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110222] pci 0000:02:01.1: PME# disabled
[    0.110319] pci 0000:02:01.2: reg 10 32bit mmio: [0xdf9fd500-0xdf9fd5ff]
[    0.110378] pci 0000:02:01.2: supports D1 D2
[    0.110381] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110444] pci 0000:02:01.2: PME# disabled
[    0.110540] pci 0000:02:01.3: reg 10 32bit mmio: [0xdf9fd600-0xdf9fd6ff]
[    0.110601] pci 0000:02:01.3: supports D1 D2
[    0.110604] pci 0000:02:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110664] pci 0000:02:01.3: PME# disabled
[    0.110762] pci 0000:02:01.4: reg 10 32bit mmio: [0xdf9fd700-0xdf9fd7ff]
[    0.110823] pci 0000:02:01.4: supports D1 D2
[    0.110826] pci 0000:02:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110888] pci 0000:02:01.4: PME# disabled
[    0.111007] pci 0000:00:1e.0: transparent bridge
[    0.111068] pci 0000:00:1e.0: bridge 32bit mmio: [0xdf900000-0xdf9fffff]
[    0.111101] pci_bus 0000:00: on NUMA node 0
[    0.111106] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.111385] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.112024] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.112100] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.112178] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.121406] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.121745] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
[    0.122080] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.122411] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.122839] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.123441] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.124056] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.124660] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.125331] SCSI subsystem initialized
[    0.125423] libata version 3.00 loaded.
[    0.125496] usbcore: registered new interface driver usbfs
[    0.125566] usbcore: registered new interface driver hub
[    0.125646] usbcore: registered new device driver usb
[    0.125839] ACPI: WMI: Mapper loaded
[    0.125891] PCI: Using ACPI for IRQ routing
[    0.126125] Bluetooth: Core ver 2.15
[    0.126202] NET: Registered protocol family 31
[    0.126255] Bluetooth: HCI device and connection manager initialized
[    0.126314] Bluetooth: HCI socket layer initialized
[    0.126369] NetLabel: Initializing
[    0.126421] NetLabel:  domain hash size = 128
[    0.126475] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.126541] NetLabel:  unlabeled traffic allowed by default
[    0.126746] hpet clockevent registered
[    0.126750] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.126814] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.126996] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.133668] pnp: PnP ACPI init
[    0.133734] ACPI: bus type pnp registered
[    0.164295] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.164376] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.164524] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.164604] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.164682] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.164761] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.165689] pnp: PnP ACPI: found 11 devices
[    0.165744] ACPI: ACPI bus type pnp unregistered
[    0.165800] PnPBIOS: Disabled by ACPI PNP
[    0.165862] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.165921] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.165982] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.166041] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.166102] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
[    0.166177] system 00:00: iomem range 0x7f6d3400-0x7f6fffff has been reserved
[    0.166238] system 00:00: iomem range 0x7f700000-0x7f7fffff has been reserved
[    0.166298] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
[    0.166373] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.166434] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.166508] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.166568] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.166628] system 00:00: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.166689] system 00:00: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.166750] system 00:00: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.166811] system 00:00: iomem range 0xf0006000-0xf0006fff has been reserved
[    0.166871] system 00:00: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.166932] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.166997] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.167059] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.167119] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.167178] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.167238] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.167302] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.167361] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.167420] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.167478] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.167537] system 00:08: ioport range 0x930-0x97f has been reserved
[    0.202273] AppArmor: AppArmor Filesystem Enabled
[    0.202380] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.202438] pci 0000:00:1c.0:   IO window: disabled
[    0.202497] pci 0000:00:1c.0:   MEM window: disabled
[    0.202555] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.202614] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.202671] pci 0000:00:1c.1:   IO window: disabled
[    0.202730] pci 0000:00:1c.1:   MEM window: 0xdfd00000-0xdfdfffff
[    0.202791] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.202850] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.202909] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.202970] pci 0000:00:1c.3:   MEM window: 0xdfa00000-0xdfcfffff
[    0.203030] pci 0000:00:1c.3:   PREFETCH window: 0x000000d0000000-0x000000d01fffff
[    0.203111] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.203168] pci 0000:00:1e.0:   IO window: disabled
[    0.203227] pci 0000:00:1e.0:   MEM window: 0xdf900000-0xdf9fffff
[    0.203288] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.203356]   alloc irq_desc for 16 on node -1
[    0.203358]   alloc kstat_irqs on node -1
[    0.203364] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.203427] pci 0000:00:1c.0: setting latency timer to 64
[    0.203436]   alloc irq_desc for 17 on node -1
[    0.203438]   alloc kstat_irqs on node -1
[    0.203442] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.203503] pci 0000:00:1c.1: setting latency timer to 64
[    0.203512]   alloc irq_desc for 19 on node -1
[    0.203514]   alloc kstat_irqs on node -1
[    0.203518] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.203580] pci 0000:00:1c.3: setting latency timer to 64
[    0.203589] pci 0000:00:1e.0: setting latency timer to 64
[    0.203595] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.203598] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.203601] pci_bus 0000:0c: resource 1 mem: [0xdfd00000-0xdfdfffff]
[    0.203605] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff]
[    0.203607] pci_bus 0000:0d: resource 1 mem: [0xdfa00000-0xdfcfffff]
[    0.203611] pci_bus 0000:0d: resource 2 pref mem [0xd0000000-0xd01fffff]
[    0.203614] pci_bus 0000:02: resource 1 mem: [0xdf900000-0xdf9fffff]
[    0.203617] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.203620] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.203654] NET: Registered protocol family 2
[    0.203801] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.204185] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.204972] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.205387] TCP: Hash tables configured (established 131072 bind 65536)
[    0.205446] TCP reno registered
[    0.205602] NET: Registered protocol family 1
[    0.205724] Trying to unpack rootfs image as initramfs...
[    0.443673] Freeing initrd memory: 8175k freed
[    0.449127] Simple Boot Flag at 0x79 set to 0x1
[    0.449329] cpufreq-nforce2: No nForce2 chipset.
[    0.449415] Scanning for low memory corruption every 60 seconds
[    0.449593] audit: initializing netlink socket (disabled)
[    0.449664] type=2000 audit(1265663093.447:1): initialized
[    0.459169] highmem bounce pool size: 64 pages
[    0.459228] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.460828] VFS: Disk quotas dquot_6.5.2
[    0.460938] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.461588] fuse init (API version 7.12)
[    0.461724] msgmni has been set to 1706
[    0.461984] alg: No test for stdrng (krng)
[    0.462049] io scheduler noop registered
[    0.462103] io scheduler anticipatory registered
[    0.462157] io scheduler deadline registered
[    0.462253] io scheduler cfq registered (default)
[    0.462319] pci 0000:00:02.0: Boot video device
[    0.462565]   alloc irq_desc for 24 on node -1
[    0.462568]   alloc kstat_irqs on node -1
[    0.462581] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.462593] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.462750]   alloc irq_desc for 25 on node -1
[    0.462752]   alloc kstat_irqs on node -1
[    0.462761] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.462772] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.462930]   alloc irq_desc for 26 on node -1
[    0.462932]   alloc kstat_irqs on node -1
[    0.462941] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.462952] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.463057] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.463207] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.463784] ACPI: AC Adapter [AC] (on-line)
[    0.463934] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.464587] ACPI: Lid Switch [LID]
[    0.464685] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.464765] ACPI: Power Button [PBTN]
[    0.464868] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.464943] ACPI: Sleep Button [SBTN]
[    0.465665] Marking TSC unstable due to TSC halts in idle
[    0.465749] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.465952] processor LNXCPU:00: registered as cooling_device0
[    0.466011] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.469763] Switched to high resolution mode on CPU 0
[    0.471460] thermal LNXTHERM:01: registered as thermal_zone0
[    0.471523] ACPI: Thermal Zone [THM] (31 C)
[    0.471624] isapnp: Scanning for PnP cards...
[    0.477257] ACPI: Battery Slot [BAT0] (battery absent)
[    0.825855] isapnp: No Plug & Play device found
[    0.827019] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.828417] brd: module loaded
[    0.828919] loop: module loaded
[    0.829044] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.829225] ata_piix 0000:00:1f.2: version 2.13
[    0.829241] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.829307] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.829528] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.829607] scsi0 : ata_piix
[    0.829736] scsi1 : ata_piix
[    0.830586] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.830647] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.831549] Fixed MDIO Bus: probed
[    0.832760] PPP generic driver version 2.4.2
[    0.832899] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.832974]   alloc irq_desc for 20 on node -1
[    0.832977]   alloc kstat_irqs on node -1
[    0.832983] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.833053] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.833057] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.833167] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.837165] ehci_hcd 0000:00:1d.7: debug port 1
[    0.837225] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.837241] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.852020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.852169] usb usb1: configuration #1 chosen from 1 choice
[    0.852256] hub 1-0:1.0: USB hub found
[    0.852316] hub 1-0:1.0: 8 ports detected
[    0.852436] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.852506] uhci_hcd: USB Universal Host Controller Interface driver
[    0.852586] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.852651] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.852655] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.852736] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.852836] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.852975] usb usb2: configuration #1 chosen from 1 choice
[    0.853056] hub 2-0:1.0: USB hub found
[    0.853114] hub 2-0:1.0: 2 ports detected
[    0.853213]   alloc irq_desc for 21 on node -1
[    0.853215]   alloc kstat_irqs on node -1
[    0.853220] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.853284] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.853288] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.853376] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.853483] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.853616] usb usb3: configuration #1 chosen from 1 choice
[    0.853696] hub 3-0:1.0: USB hub found
[    0.853754] hub 3-0:1.0: 2 ports detected
[    0.853858]   alloc irq_desc for 22 on node -1
[    0.853861]   alloc kstat_irqs on node -1
[    0.853865] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.853928] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.853932] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.854015] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.854121] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.854254] usb usb4: configuration #1 chosen from 1 choice
[    0.854335] hub 4-0:1.0: USB hub found
[    0.854393] hub 4-0:1.0: 2 ports detected
[    0.854493]   alloc irq_desc for 23 on node -1
[    0.854495]   alloc kstat_irqs on node -1
[    0.854499] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.854564] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.854568] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.854655] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.854762] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.854894] usb usb5: configuration #1 chosen from 1 choice
[    0.854976] hub 5-0:1.0: USB hub found
[    0.855033] hub 5-0:1.0: 2 ports detected
[    0.855182] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.858042] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.858102] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.858211] mice: PS/2 mouse device common for all mice
[    0.858377] rtc_cmos 00:06: RTC can wake from S4
[    0.858461] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.858549] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.858712] device-mapper: uevent: version 1.0.3
[    0.858851] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.859002] device-mapper: multipath: version 1.1.0 loaded
[    0.859059] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.859247] EISA: Probing bus 0 at eisa.0
[    0.859307] Cannot allocate resource for EISA slot 1
[    0.859389] EISA: Detected 0 cards.
[    0.859522] cpuidle: using governor ladder
[    0.859637] cpuidle: using governor menu
[    0.860188] TCP cubic registered
[    0.860408] NET: Registered protocol family 10
[    0.860893] lo: Disabled Privacy Extensions
[    0.861253] NET: Registered protocol family 17
[    0.861322] Bluetooth: L2CAP ver 2.13
[    0.861375] Bluetooth: L2CAP socket layer initialized
[    0.861432] Bluetooth: SCO (Voice Link) ver 0.6
[    0.861485] Bluetooth: SCO socket layer initialized
[    0.861573] Bluetooth: RFCOMM TTY layer initialized
[    0.861629] Bluetooth: RFCOMM socket layer initialized
[    0.861691] Bluetooth: RFCOMM ver 1.11
[    0.861932] Using IPI No-Shortcut mode
[    0.862044] PM: Resume from disk failed.
[    0.862055] registered taskstats version 1
[    0.862222]   Magic number: 14:316:95
[    0.862358] rtc_cmos 00:06: setting system clock to 2010-02-08 21:04:54 UTC (1265663094)
[    0.862434] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.862490] EDD information not available.
[    0.863683] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.997211] ata1.00: failed to set max address (err_mask=0x1)
[    0.997280] ata1.00: device aborted resize (114270345 -> 117210240), skipping HPA handling
[    0.997371] ata1.00: ATA-7: Hitachi HTS541060G9SA00, MB3OC60R, max UDMA/100
[    0.997440] ata1.00: 114270345 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.012504] ata1.00: configured for UDMA/100
[    1.012686] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54106 MB3O PQ: 0 ANSI: 5
[    1.012869] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.012964] sd 0:0:0:0: [sda] 114270345 512-byte logical blocks: (58.5 GB/54.4 GiB)
[    1.013086] sd 0:0:0:0: [sda] Write Protect is off
[    1.013141] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.013167] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.013371]  sda:
[    1.020419] ata2.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462C, DE06, max UDMA/33
[    1.036175]  sda1 sda2
[    1.036504] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.052493] ata2.00: configured for UDMA/33
[    1.053919] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462C DE06 PQ: 0 ANSI: 5
[    1.056402] sr0: scsi3-mmc drive: 10x/24x writer cd/rw xa/form2 cdda tray
[    1.056462] Uniform CD-ROM driver Revision: 3.20
[    1.056581] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.056624] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.056697] Freeing unused kernel memory: 540k freed
[    1.057078] Write protecting the kernel text: 4568k
[    1.057168] Write protecting the kernel read-only data: 1836k
[    1.124027] Clocksource tsc unstable (delta = -113560741 ns)
[    1.205228] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:20/input/input5
[    1.205358] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.205458] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    1.205661] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/input/input6
[    1.205758] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    1.211854] Linux agpgart interface v0.103
[    1.262078] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    1.262607] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.331476] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.340055] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    1.351507] ohci1394 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.368878] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.368986] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    1.392195] [drm] Initialized drm 1.1.0 20060810
[    1.410371] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[df9fd800-df9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.415238] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.415316] i915 0000:00:02.0: setting latency timer to 64
[    1.741702] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    1.745502] b44 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.015826] [drm] TV-14: set mode NTSC 480i 0
[    2.036343] usb 1-8: configuration #1 chosen from 1 choice
[    2.044948] Initializing USB Mass Storage driver...
[    2.045094] scsi2 : SCSI emulation for USB Mass Storage devices
[    2.045227] usbcore: registered new interface driver usb-storage
[    2.045284] USB Mass Storage support registered.
[    2.045393] usb-storage: device found at 4
[    2.045395] usb-storage: waiting for device to settle before scanning
[    2.152502] [drm] fb0: inteldrmfb frame buffer device
[    2.152570] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.226588] [drm] DAC-6: set mode 1366x768 26
[    2.226800] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    2.226827] b44.c:v2.0
[    2.287930] [drm] LVDS-8: set mode 1280x800 27
[    2.410537] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:af:e9:41
[    2.417444] Console: switching to colour frame buffer device 160x48
[    2.520212] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    2.628705] xor: automatically using best checksumming function: pIII_sse
[    2.648009]    pIII_sse  :  4741.000 MB/sec
[    2.648012] xor: using function: pIII_sse (4741.000 MB/sec)
[    2.651451] device-mapper: dm-raid45: initialized v0.2594b
[    2.716270] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc0002b812d41]
[    2.725337] usb 4-2: configuration #1 chosen from 1 choice
[    2.964208] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    3.142048] usb 5-1: configuration #1 chosen from 1 choice
[    3.153830] usbcore: registered new interface driver hiddev
[    3.153910] usbcore: registered new interface driver usbhid
[    3.153914] usbhid: v2.6:USB HID core driver
[    3.171395] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input7
[    3.171468] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-1/input0
[    3.202889] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    3.204104] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input8
[    3.204209] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-1/input1
[    7.044308] usb-storage: device scan complete
[    7.044890] scsi 2:0:0:0: Direct-Access     WD       1200BEA External 1.04 PQ: 0 ANSI: 4
[    7.045331] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    7.047115] sd 2:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    7.047861] sd 2:0:0:0: [sdb] Write Protect is off
[    7.047864] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    7.047867] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.049379] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.049387]  sdb: sdb1 sdb2
[    7.101992] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.101997] sd 2:0:0:0: [sdb] Attached SCSI disk
[    9.303556] aufs 2-standalone.tree-30-20090727
[    9.317125] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   11.574468] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[   11.620774] aufs test_add:242:exe[1005]: uid/gid/perm //filesystem.squashfs 0/0/0755, 0/0/0777
[   19.872275] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 500116
[   34.633636] udev: starting version 147
[   35.417881] cfg80211: Calling CRDA to update world regulatory domain
[   35.460365] intel_rng: FWH not detected
[   35.533367] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   35.771688] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   36.157739] Linux video capture interface: v2.00
[   36.215134] ricoh-mmc: Ricoh MMC Controller disabling driver
[   36.215137] ricoh-mmc: Copyright(c) Philip Langdale
[   36.215170] ricoh-mmc: Ricoh MMC controller found at 0000:02:01.2 [1180:0843] (rev 1)
[   36.215185] ricoh-mmc: Controller is now disabled.
[   36.239559] sdhci: Secure Digital Host Controller Interface driver
[   36.239563] sdhci: Copyright(c) Pierre Ossman
[   36.269593] gspca: main v2.6.0 registered
[   36.338522] gspca: probing 046d:08d9
[   36.356162] sdhci-pci 0000:02:01.1: SDHCI controller found [1180:0822] (rev 19)
[   36.356183]   alloc irq_desc for 18 on node -1
[   36.356186]   alloc kstat_irqs on node -1
[   36.356195] sdhci-pci 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   36.358289] Registered led device: mmc0::
[   36.359316] mmc0: SDHCI controller on PCI [0000:02:01.1] using DMA
[   36.361497] dell-wmi: No known WMI GUID found
[   36.424617] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   36.460864] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   36.589826] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.624405] phy0: Selected rate control algorithm 'minstrel'
[   36.625078] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   36.728230] cfg80211: World regulatory domain updated:
[   36.728235]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.728239]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.728242]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   36.728245]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   36.728248]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.728251]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   37.428091] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   37.490302] usplash[346]: segfault at b761d3e8 ip 004eade6 sp bfa14070 error 6 in libusplash.so.0 (deleted)[4c6000+29000]
[   37.749091] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   37.798152] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   37.798190] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   37.799685] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   37.823077] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   37.947951] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   38.012446] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   38.012534] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   38.037321] Registered led device: b43-phy0::tx
[   38.037347] Registered led device: b43-phy0::rx
[   38.037375] Registered led device: b43-phy0::radio
[   38.038252] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.050897] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.173396] zc3xx: probe 2wr ov vga 0x0000
[   38.223232] zc3xx: probe sensor -> 0011
[   38.223237] zc3xx: Find Sensor HV7131R(c)
[   38.227313] gspca: probe ok
[   38.227325] gspca: probing 046d:08d9
[   38.227335] gspca: probing 046d:08d9
[   38.227358] usbcore: registered new interface driver zc3xx
[   38.227362] zc3xx: registered
[   38.473580] usbcore: registered new interface driver snd-usb-audio
[   40.491876] [drm] DAC-6: set mode 1024x768 29
[   40.779112] [drm] LVDS-8: set mode 1024x768 2b
[   50.967850] lp: driver loaded but no devices found
[   51.061663] ppdev: user-space parallel port driver
[   52.798123] [drm] LVDS-8: set mode  28
[   53.307584] [drm] DAC-6: set mode  2f
[   62.376518] EXT2-fs error (device loop1): ext2_lookup: deleted inode referenced: 500116
[   82.489243] wlan0: authenticate with AP 00:1e:e5:eb:c7:7a
[   82.492282] wlan0: authenticated
[   82.492286] wlan0: associate with AP 00:1e:e5:eb:c7:7a
[   82.508456] wlan0: RX AssocResp from 00:1e:e5:eb:c7:7a (capab=0x431 status=0 aid=1)
[   82.508466] wlan0: associated
[   82.509811] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   82.897807] padlock: VIA PadLock not detected.
[   93.428087] wlan0: no IPv6 routers present
[  175.204188] usb 1-5: new high speed USB device using ehci_hcd and address 5
[  175.345909] usb 1-5: configuration #1 chosen from 1 choice


---

### Post by Jose Catre-Vandis on 2010-02-10
Hmmm...linux not recognising hardware other than giving it an address of id=6000:0001.

Can you get it to work on a Windows PC?

What drivers does it need to get it going under Windows?

More googling required.....

---

### Post by ma5t3rw1tt on 2010-02-10
> **Jose Catre-Vandis said:**
> Hmmm...linux not recognising hardware other than giving it an address of id=6000:0001.

Can you get it to work on a Windows PC?

What drivers does it need to get it going under Windows?

More googling required.....

---------
Well the funny thing is that it works under XP (well use to) but it would often give me the bluescreen of death.

If you go to [http://sabrent.com/#section=Drivers&itemName=&itemID=0](http://sabrent.com/#section=Drivers&itemName=&itemID=0) you will find the drivers. Yet when I download them to my Windows 7 or even Linux Mint, nothing happens. On Windows 7 it says this device is not support thru the Windows Media Player which is ******** cause the driver is clearly there.

And on Linux Mint, I don't even know where to even begin with this. I sorta have a dual boot going on between 7 and linux mint, except linux mint is on my external portable HD that I used a persistant USB install on if that helps any.

---

### Post by Jose Catre-Vandis on 2010-02-10
Seems it might be a chipset: TV Master TM5600

Try this in a terminal and then check dmesg for new output
```
sudo modprobe tm6000
or
sudo modprobe tm6000 card=3
```
```
dmesg
```

Also, possibly some good stuff [here]("http://translate.google.co.uk/translate?hl=en&sl=it&u=http://forum.ubuntu-it.org/index.php%3Ftopic%3D59926.40&ei=rilzS_uWHZL20wSJ8NGpCw&sa=X&oi=translate&ct=result&resnum=6&ved=0CBsQ7gEwBTgK&prev=/search%3Fq%3Dchipset:%2BTV%2BMaster%2BTM5600%2Blinux%2Bdvb%26hl%3Den%26sa%3DN%26start%3D10")

---

### Post by ma5t3rw1tt on 2010-02-12
> **Jose Catre-Vandis said:**
> Seems it might be a chipset: TV Master TM5600

Try this in a terminal and then check dmesg for new output
```
sudo modprobe tm6000
or
sudo modprobe tm6000 card=3
``````
dmesg
```Also, possibly some good stuff [here]("http://translate.google.co.uk/translate?hl=en&sl=it&u=http://forum.ubuntu-it.org/index.php%3Ftopic%3D59926.40&ei=rilzS_uWHZL20wSJ8NGpCw&sa=X&oi=translate&ct=result&resnum=6&ved=0CBsQ7gEwBTgK&prev=/search%3Fq%3Dchipset:%2BTV%2BMaster%2BTM5600%2Blinux%2Bdvb%26hl%3Den%26sa%3DN%26start%3D10")

-------

When I try either of those commands, it says "Module not found"
So I not sure what I would do next.

---

### Post by Jose Catre-Vandis on 2010-02-12
I was hoping it may have made its way into the kernel, but no :( my bad!

Best I can suggest is reading through the link in my previous post. From what I can see installing the specific package from source and loading the module will allow linux to see the device, but I have not found anyone who has had success in "getting a picture".

---

### Post by HandeH on 2010-12-13
There is a bug report: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311659](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311659)

and another forum thread: [http://ubuntuforums.org/showthread.php?p=10233100](http://ubuntuforums.org/showthread.php?p=10233100)

EDIT: and also a Brainstorm: [http://brainstorm.ubuntu.com/idea/15749/](http://brainstorm.ubuntu.com/idea/15749/)

The common denominator of different brand names is TRIDENT TM6000 (and maybe also TM5600/TM6010) Chip: [http://linuxtv.org/wiki/index.php/Trident_TM6000](http://linuxtv.org/wiki/index.php/Trident_TM6000)

---

