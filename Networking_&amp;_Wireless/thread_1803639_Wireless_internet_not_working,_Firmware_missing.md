---
title: "Wireless internet not working, Firmware missing?"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by bigrthau on 2011-07-13
I am using a hp pavilion zd7000, computer says firmware is missing for  wireless controller. i also have a wirless g notebook card made by belkin which will scan for networks but wont connect to them for some unknown reason. if i can get either the wireless g card to work or the built in wireless to work thata be great. I am well experienced in windows but very new to  linux and how everything works. if anyone can help me. It will be  greatly appreciated, i typed in "sudo lspci -v" into the terminal and  this is what i got.






00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, fast devsel, latency 0
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    Capabilities: [e4] Vendor Specific Information: Len=06 <?>
    Capabilities: [a0] AGP version 3.0
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 96
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=80
    Memory behind bridge: d1000000-d1ffffff
    Prefetchable memory behind bridge: e0000000-efffffff
    Kernel modules: shpchp

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev ff) (prog-if ff)
    !!! Unknown header type 7f

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1cc0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1ce0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 2000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d0000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d2000000-d23fffff
    Prefetchable memory behind bridge: 20000000-23ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 2040 [size=16]
    Memory at 24000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 006a
    Flags: medium devsel, IRQ 10
    I/O ports at 2020 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1400 [size=256]
    I/O ports at 1c80 [size=64]
    Memory at d0000c00 (32-bit, non-prefetchable) [size=512]
    Memory at d0000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: medium devsel, IRQ 17
    I/O ports at 1800 [size=256]
    I/O ports at 1c00 [size=128]
    Capabilities: [50] Power Management version 2
    Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5600] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 006a
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
    Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [60] Power Management version 2
    Capabilities: [44] AGP version 3.0
    Kernel driver in use: nvidia
    Kernel modules: nvidia-173, nouveau, nvidiafb

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 32, IRQ 20
    I/O ports at 3000 [size=256]
    Memory at d2007800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at d2006000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 28000000-2bfff000
    I/O window 0: 00003400-000034ff
    I/O window 1: 00003800-000038ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
    Subsystem: Hewlett-Packard Company NX9500
    Flags: medium devsel, IRQ 18
    I/O ports at 3c00 [size=128]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: cb710
    Kernel modules: cb710

02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at d2007000 (32-bit, non-prefetchable) [size=2K]
    Memory at d2000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
    Subsystem: Compaq Computer Corporation Device 00e7
    Flags: bus master, fast devsel, latency 32, IRQ 21
    Memory at d2004000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

me@ubuntu:~$

---

### Post by chili555 on 2011-07-14
Please detach the USB wireless, walk the laptop over to the router and get a temporary wired ethernet connection. Open a terminal and do:```
sudo apt-get install firmware-b43-installer b43-fwcutter
```After it concludes, detach the ethernet, reboot and use your new wireless to post and tell us how it's working.

---

