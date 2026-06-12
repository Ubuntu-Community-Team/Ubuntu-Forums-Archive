---
title: "Airodump #data problem"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by moonfang on 2012-08-13
hey guys... 

I need some help due to my wlan card is bitching arround when i use airdump-ng

first things first: i use backtrack 5 RC2 
i can connect to networks everything is working perfectly fine but:
i wont recive data packages in airdump-ng
its started in monitor mode, as mon0 and i can see every network with bssid pwr and encryption, injection is working but whatever i do, i wont recive any #data and injection isnt working (arp's wont increase)

its not completly impssible to recive data, the counter will rise when i am already connected to the network and injection is also working when i am connected.

i also tested it with a usb wlan "card", wich works great.

oh yeah by the way: fake auth is working and also deauth is working perfectly

i dont have a clue why it wont recive any data


some specifications:
data sheet of netbook: [www.samsung.com/de/consumer/notebooks-displays/notebook-computers/archive-notebooks/NP-N220-JP01DE-spec]("http://www.samsung.com/de/consumer/notebooks-displays/notebook-computers/archive-notebooks/NP-N220-JP01DE-spec")

31: None 00.0: 10700 Loopback                                   
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.CZq_uBiCANA
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.2/0000:09:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "sky2"
  Driver Modules: "sky2"
  Device File: eth0
  HW Address: 00:24:54:b3:0c:f3
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (Ethernet controller)

33: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: y9sn.3dzvUmOhw4D
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.0/0000:05:00.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "brcmsmac"
  Driver Modules: "brcmsmac"
  Device File: wlan0
  HW Address: 00:1b:b1:48:fc:cf
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (Network controller)
-------------------------------------------------------------------------------------------------
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information <?>
        Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, fast devsel, latency 0, IRQ 47
        Memory at f0300000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 18d0 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, fast devsel, latency 0
        Memory at f0380000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f0100000-f01fffff
        Prefetchable memory behind bridge: 0000000040a00000-0000000040bfffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c072
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [180] Root Complex Link <?>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: 40600000-407fffff
        Prefetchable memory behind bridge: 0000000040800000-00000000409fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c072
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [180] Root Complex Link <?>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: 0000000040400000-00000000405fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c072
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [180] Root Complex Link <?>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 40000000-401fffff
        Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c072
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [180] Root Complex Link <?>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1820 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1880 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f0604000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=11, subordinate=11, sec-latency=32
        Capabilities: [50] Subsystem: Samsung Electronics Co Ltd Device c072

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information <?>
        Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01)
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
        I/O ports at 18e8 [size=8]
        I/O ports at 18dc [size=4]
        I/O ports at 18e0 [size=8]
        I/O ports at 18d8 [size=4]
        I/O ports at 18c0 [size=16]
        Memory at f0604400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [70] Power Management version 2
        Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: medium devsel, IRQ 10
        I/O ports at 18a0 [size=32]
        Kernel modules: i2c-i801

05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
        Subsystem: Wistron NeWeb Corp. Device 051a
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information <?>
        Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [13c] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 1b-00-48-ff-ff-b1-00-00
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: brcmsmac
        Kernel modules: brcmsmac

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
        Subsystem: Samsung Electronics Co Ltd Device c072
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        Capabilities: [48] Power Management version 3
        Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [c0] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [130] Device Serial Number 00-24-54-ff-ff-b3-0c-f3
        Kernel driver in use: sky2
        Kernel modules: sky2

---

### Post by wildmanne39 on 2012-08-14
Hi, this topic is not supported in the forum, your best bet is to use the backtrack forum.
Thanks

---

