---
title: "How to fix my wireless"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by Jordii on 2009-08-29
My network manager doesn't show wireless internet connections.
 
> lshw
 
ubuntu 
description: Computer
width: 32 bits
*-core
description: Motherboard
physical id: 0
*-memory
description: System memory
physical id: 0
size: 502MiB
*-cpu
product: Intel(R) Celeron(R) M CPU 410 @ 1.46GHz
vendor: Intel Corp.
physical id: 1
bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
version: 6.14.8
serial: 0000-06E8-0000-0000-0000-0000
size: 150MHz
width: 32 bits
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts pni monitor tm2 xtpr pdcm
*-pci
description: Host bridge
product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
vendor: Intel Corporation
physical id: 100
bus info: pci@0000:00:00.0
version: 03
width: 32 bits
clock: 33MHz
configuration: driver=agpgart-intel module=intel_agp
*-display:0 UNCLAIMED
description: VGA compatible controller
product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
*-display:1 UNCLAIMED
description: Display controller
product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
*-multimedia
description: Audio device
product: 82801G (ICH7 Family) High Definition Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=HDA Intel latency=0 module=snd_hda_intel
*-pci:0
description: PCI bridge
product: 82801G (ICH7 Family) PCI Express Port 1
vendor: Intel Corporation
physical id: 1c
bus info: pci@0000:00:1c.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
configuration: driver=pcieport-driver
*-network
description: Ethernet interface
product: 88E8038 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 14
serial: 00:16:36:8c:35:34
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
*-pci:1
description: PCI bridge
product: 82801G (ICH7 Family) PCI Express Port 2
vendor: Intel Corporation
physical id: 1c.1
bus info: pci@0000:00:1c.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
configuration: driver=pcieport-driver
*-pci:2
description: PCI bridge
product: 82801G (ICH7 Family) PCI Express Port 3
vendor: Intel Corporation
physical id: 1c.2
bus info: pci@0000:00:1c.2
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
configuration: driver=pcieport-driver
*-pci:3
description: PCI bridge
product: 82801G (ICH7 Family) PCI Express Port 4
vendor: Intel Corporation
physical id: 1c.3
bus info: pci@0000:00:1c.3
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
configuration: driver=pcieport-driver
*-usb:0
description: USB Controller
product: 82801G (ICH7 Family) USB UHCI Controller #1
vendor: Intel Corporation
physical id: 1d
bus info: pci@0000:00:1d.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:1
description: USB Controller
product: 82801G (ICH7 Family) USB UHCI Controller #2
vendor: Intel Corporation
physical id: 1d.1
bus info: pci@0000:00:1d.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:2
description: USB Controller
product: 82801G (ICH7 Family) USB UHCI Controller #3
vendor: Intel Corporation
physical id: 1d.2
bus info: pci@0000:00:1d.2
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:3
description: USB Controller
product: 82801G (ICH7 Family) USB UHCI Controller #4
vendor: Intel Corporation
physical id: 1d.3
bus info: pci@0000:00:1d.3
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:4
description: USB Controller
product: 82801G (ICH7 Family) USB2 EHCI Controller
vendor: Intel Corporation
physical id: 1d.7
bus info: pci@0000:00:1d.7
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=ehci_hcd latency=0 module=ehci_hcd
*-pci:4
description: PCI bridge
product: 82801 Mobile PCI Bridge
vendor: Intel Corporation
physical id: 1e
bus info: pci@0000:00:1e.0
version: e2
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
*-network
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0000:0a:03.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=96 module=ssb
*-pcmcia
description: CardBus bridge
product: PCIxx12 Cardbus Controller
vendor: Texas Instruments
physical id: 9
bus info: pci@0000:0a:09.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pcmcia bus_master cap_list
configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
*-storage
description: Mass storage controller
product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
vendor: Texas Instruments
physical id: 9.2
bus info: pci@0000:0a:09.2
version: 00
width: 32 bits
clock: 33MHz
capabilities: storage bus_master cap_list
configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
*-isa
description: ISA bridge
product: 82801GBM (ICH7-M) LPC Interface Bridge
vendor: Intel Corporation
physical id: 1f
bus info: pci@0000:00:1f.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: isa bus_master cap_list
configuration: latency=0
*-ide
description: IDE interface
product: 82801G (ICH7 Family) IDE Controller
vendor: Intel Corporation
physical id: 1f.1
bus info: pci@0000:00:1f.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: ide bus_master
configuration: driver=ata_piix latency=0
*-serial UNCLAIMED
description: SMBus
product: 82801G (ICH7 Family) SMBus Controller
vendor: Intel Corporation
physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 02
width: 32 bits
clock: 33MHz
configuration: latency=0
*-network:0 DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:16:cf:7a:3a:b9
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: e6:78:2f:1b:20:bd
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Jordii on 2009-08-29
:eek:Nobody? If you need more information please tell me

---

### Post by jquill on 2009-08-29
I'm having a similar problem and I'm wondering if our "Physical id" fields are forcing our network management utility to see only the wired device.  My research to this point has not confirmed that but I'm trying to look at each line until there's one I cannot disprove.  My (LSHW) results are similar in that the wireless device is "Unclaimed."  I posted yesterday and will update you if anyone is kind enough to chime in on my issue.  

   description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 502MiB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        440  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts pni monitor tm2 xtpr pdcm
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8038 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 14
                serial: 00:1b:24:3b:b7:f4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.6 latency=0 module=sky2 multicast=yes
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:0a:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:0a:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:f6:d6:4b:6f:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by bkratz on 2009-08-29
Your listing shows 

description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0000:0a:03.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=96 module=ssb

BCM4318

There was a recent posting on that one,  you can search for it with the above search engine.  I believe it told you how to turn on the drivers.  I will look for it and respond a little later if you don't find it.


Don't forget to unplug the wired connection since network manager only can handle one thing at a time.

---

### Post by bkratz on 2009-08-29
> **bkratz said:**
> Your listing shows 


There was a recent posting on that one,  you can search for it with the above search engine.  I believe it told you how to turn on the drivers.  I will look for it and respond a little later if you don't find it.


Don't forget to unplug the wired connection since network manager only can handle one thing at a time.


Here is the one I was referring to

 [http://ubuntuforums.org/showthread.php?t=1166316&highlight=bcm+4318](http://ubuntuforums.org/showthread.php?t=1166316&highlight=bcm+4318)


Look at the last two or three posting.

Good Luck

---

### Post by Jordii on 2009-08-29
I thought my problem would also be that my b43 driver doesn't activate when I click activate -_- and I don't really get that post.. not concentrated enough for now I think xD

---

### Post by Jordii on 2009-08-29
**KnetworkManager cannot be installed on your computer type (i386)**
 
Either the application requires special hardware features or the vendor decided to not support your computer type.
 
It's in the Add/Remove Applications window, whitout internet,but it was written in those posts you reffered to.
 
So.. Following this steps:
1. Cat5 wired and did all available updates, (restart) Cat5 wired? **I don't understand.**
2. System>Administration>Hardware Drivers, clicked "Activate", (restart) **Because I can't do the fist step, theres only the b43 driver at the hardware drivers, but I can't activate it.**
3. Applications > Add / Remove and Refresh(ed), add KNetworkManager, Wireless Light is ON, (restart) **I seem to need an internet connection for that :confused:**
4. Clicked Network Mgr from Panel, made sure wireless enabled, found my SSID (WPA-PSK), and logged in **That should only work when the rest works.**

---

### Post by bkratz on 2009-08-29
> **Jordii said:**
> I thought my problem would also be that my b43 driver doesn't activate when I click activate -_- and I don't really get that post.. not concentrated enough for now I think xD


Try this one it looks like a good tutorial

[http://ubuntuforums.org/showthread.php?t=1233448](http://ubuntuforums.org/showthread.php?t=1233448)

---

### Post by Jordii on 2009-08-29
I think that helps!

---

