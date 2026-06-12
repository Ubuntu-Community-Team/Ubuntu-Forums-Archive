---
title: "Wireless won't work but my Wired will"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by TheMzungu on 2009-01-22
I own a Toshiba Satellite A205-S5831, Whenever i download Ubuntu in a dual boot every time i try and use the wireless it gives me absolutely nothing, i can even type in the mac address and the network name and everything and it still won't read the information. But immediately when i connect it to a wired line directly to my router it works fine but besides that i get nothing. Can somebody help?

---

### Post by acimmarusti on 2009-01-23
Do you know your wireless card model, brand and everything? is it a usb device? or a pci device?

This info is necessary to see if you need firmware before actually working under ubuntu.

If you have no clue, do this in a terminal:

lspci -v 

and in the output look for the word wireless and paste that info here.

if your device works by usb, then do

lsusb -v 

and also look for wireless

---

### Post by TheMzungu on 2009-01-23
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0
	Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fc504800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0000000-f3ffffff
	Prefetchable memory behind bridge: 00000000ce000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f4000000-f7ffffff
	Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000ca000000-00000000cbffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: c4000000-c7ffffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000c9ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fc504c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=10, sec-latency=32
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: fc200000-fc2fffff
	Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 217
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fc504000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: medium devsel, IRQ 10
	Memory at 54000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]
	Kernel modules: i2c-i801

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 218
	I/O ports at 3000 [size=256]
	Memory at f4000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at cc000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7128
	Flags: fast devsel, IRQ 18
	Memory at f8000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci

0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at fc204000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0c, secondary=0d, subordinate=10, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 58000000-5bfff000
	I/O window 0: 00006000-000060ff
	I/O window 1: 00006400-000064ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fc206000 (32-bit, non-prefetchable) [size=2K]
	Memory at fc200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Toshiba America Info Systems Device ff02
	Flags: bus master, medium devsel, latency 57, IRQ 18
	Memory at fc205000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff02
	Flags: bus master, medium devsel, latency 57, IRQ 18
	Memory at fc206800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

---

### Post by TheMzungu on 2009-01-23
Okay how does that work?

---

### Post by Stoneface on 2009-01-23
I don't want to hijack this post, but maybe I can contribute and get some help at the same time here.. I have an Atheros wireless card as well. I got it to work on my Acer Aspire using a madwifi.org driver. Their site seems to be different today and I can't seem to find updates for the driver that I need. 
And every time I do a new kernel update wireless is gone and I I have to do everything all over again. Isn't there a way to keep the driver working after kernel updates?

Here are my details:
```
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f2000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

```

At Madwifi they mentioned my wirless card is a AR5007EG and that I need a snapshot with the latest HAL for this to work.

---

### Post by Stoneface on 2009-01-23
See post [http://ubuntuforums.org/showthread.php?p=5711824#post5711824](http://ubuntuforums.org/showthread.php?p=5711824#post5711824) . Explanation worked brillaintly for me. I did have to reinstall the madwifi driver so had to do a full compilation again but this guy explained it all step for step. He even explained how to fix the domain name issue. :-)

---

### Post by acimmarusti on 2009-01-23
TheMzungu,

This is your wireless card:

05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7128
    Flags: fast devsel, IRQ 18
    Memory at f8000000 (64-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel modules: ath_pci

Notice it says it's disabled. That probably means you need a driver for it. Follow that suggestion made by Stoneface. Unfortunately I have no previous experience with that type of card. If it doesn't work for you trying carefully reading "the stickies". They provide detailed info.

---

