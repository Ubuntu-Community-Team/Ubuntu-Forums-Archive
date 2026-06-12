---
title: "Ethernet and Wireless DISABLED!"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by arnold15 on 2009-09-05
After the successful installation of ubuntu on my computer, some problems occured.. Its pissing me off.. I tried to input on the terminal the code "sudo lshw -c network" then the result is like this:

*-network:0 DISABLED
blah blah blah
*-network:1 DISABLED
blah blah blah

how to enable this crazy network drivers? I am looking forward for your reply.. Thanks!

---

### Post by arnold15 on 2009-09-05
Btw, the wired is broadcom and the wireless is linksys

---

### Post by snowpine on 2009-09-05
Hi Arnold, your post is short on details... ;)

Which Ubuntu release are you using?

Linksys and Broadcom make several products (believe it or not), so which one? The terminal command 'lspci' will give more details.

And can you copy and paste the "blah blah blah"? :)

---

### Post by arnold15 on 2009-09-05
No, i cant.. I dont have internet coz of this error.. Im only using my operamini on mobile.. But the linksys is WPC54GS ver.2 ..

---

### Post by snowpine on 2009-09-05
I am not familiar with that card (sorry) but these forums have an awesome Search feature, try a search for WPC54GS and you should get some help, good luck. :)

---

### Post by arnold15 on 2009-09-05
I understand, but do you know how to enable a network card?

---

### Post by arnold15 on 2009-09-05
Here is the result of sudo lshw -c network

> arnold@arnold-laptop:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:9b:28:0c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:90:26:fc:65:b8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:bf:fa:b5:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by arnold15 on 2009-09-05
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
 Flags: bus master, fast devsel, latency 0
 Memory at e0000000 (32-bit, prefetchable) [size=128M]
 Capabilities: <access denied>
 Kernel driver in use: agpgart-intel
 Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
 Flags: bus master, 66MHz, fast devsel, latency 32
 Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
 I/O behind bridge: 0000c000-0000cfff
 Memory behind bridge: fc000000-fdffffff
 Prefetchable memory behind bridge: e8000000-efffffff
 Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
 Subsystem: Intel Corporation Device 24c0
 Flags: bus master, medium devsel, latency 0, IRQ 11
 I/O ports at bf80 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
 Subsystem: Intel Corporation Device 24c0
 Flags: bus master, medium devsel, latency 0, IRQ 11
 I/O ports at bf40 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
 Subsystem: Intel Corporation Device 24c0
 Flags: bus master, medium devsel, latency 0, IRQ 11
 I/O ports at bf20 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20)
 Subsystem: Intel Corporation Device 24c0
 Flags: bus master, medium devsel, latency 0, IRQ 11
 Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
 Capabilities: <access denied>
 Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
 I/O behind bridge: 0000d000-0000efff
 Memory behind bridge: f6000000-fbffffff
 Prefetchable memory behind bridge: 50000000-53ffffff
 Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
 Flags: bus master, medium devsel, latency 0
 Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
 Subsystem: Intel Corporation Device 24c0
 Flags: bus master, medium devsel, latency 0, IRQ 11
 I/O ports at 01f0 [size=8]
 I/O ports at 03f4 [size=1]
 I/O ports at 0170 [size=8]
 I/O ports at 0374 [size=1]
 I/O ports at bfa0 [size=16]
 Memory at 54000000 (32-bit, non-prefetchable) [size=1K]
 Kernel driver in use: ata_piix
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
 Subsystem: Dell Device 0149
 Flags: bus master, medium devsel, latency 0, IRQ 7
 I/O ports at b800 [size=256]
 I/O ports at bc40 [size=64]
 Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
 Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
 Capabilities: <access denied>
 Kernel driver in use: Intel ICH
 Kernel modules: snd-intel8x0
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
 Subsystem: Conexant Systems, Inc. Device 5422
 Flags: medium devsel, IRQ 7
 I/O ports at b400 [size=256]
 I/O ports at b080 [size=128]
 Capabilities: <access denied>
 Kernel modules: snd-intel8x0m
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
 Subsystem: Dell Device 0149
 Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
 Memory at e8000000 (32-bit, prefetchable) [size=128M]
 I/O ports at c000 [size=256]
 Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
 [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
 Capabilities: <access denied>
 Kernel modules: radeonfb
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
 Subsystem: Dell Device 0149
 Flags: bus master, fast devsel, latency 32, IRQ 7
 Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
 Capabilities: <access denied>
 Kernel driver in use: b44
 Kernel modules: b44
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
 Subsystem: Dell Device 0149
 Flags: bus master, medium devsel, latency 168, IRQ 11
 Memory at f6000000 (32-bit, non-prefetchable) [size=4K]
 Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
 Memory window 0: 50000000-53fff000 (prefetchable)
 Memory window 1: 58000000-5bfff000
 I/O window 0: 0000d000-0000d0ff
 I/O window 1: 0000d400-0000d4ff
 16-bit legacy interface ports at 0001
 Kernel driver in use: yenta_cardbus
 Kernel modules: yenta_socket
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (prog-if 10)
 Subsystem: Dell Device 0149
 Flags: bus master, medium devsel, latency 32, IRQ 11
 Memory at faffd800 (32-bit, non-prefetchable) [size=2K]
 Memory at faff8000 (32-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: ohci1394
 Kernel modules: firewire-ohci, ohci1394
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
 Subsystem: Linksys Device 0049
 Flags: bus master, fast devsel, latency 64, IRQ 11
 Memory at 58000000 (32-bit, non-prefetchable) [size=8K]
 Kernel driver in use: b43-pci-bridge
 Kernel modules: ssb

---

### Post by arnold15 on 2009-09-05
[EMAIL="arnold@arnold-laptop:~$"]arnold@arnold-laptop:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by arnold15 on 2009-09-06
When I plug in my Wireless Card, its says that the Device is not Ready

---

### Post by arnold15 on 2009-09-06
Problem solved!!!!!!!!!!!!!!!!! Thanks to me! :d

---

### Post by m0eman on 2009-09-10
Mind sharing your solution?

---

