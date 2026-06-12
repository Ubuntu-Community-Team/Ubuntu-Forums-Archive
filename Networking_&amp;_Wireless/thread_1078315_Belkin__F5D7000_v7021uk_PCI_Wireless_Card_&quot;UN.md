---
title: "Belkin  F5D7000 v7021uk PCI Wireless Card &quot;UNCLAIMED&quot;"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by siabost on 2009-02-23
Ubuntu 8.04LTS, Dell Dimension Desktop 2400.
Belkin F5D7000 ver 7021uk Wireless PCI

The card seems to work with Ubuntu 8.10 as per [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCI)

I have had no such luck so far:(

Running lshw (without root privileges) in terminal I get:
>     description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1003MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KiB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0 UNCLAIMED
                description: Ethernet controller
                product: Belkin
                vendor: Belkin
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=64 mingnt=32
           *-communication
                description: Modem
                product: FA82537EP 56K V.92 Data/Fax Modem PCI
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
           *-network:1
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: 00:0f:1f:54:b3:01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

As seen the wireless card comes up as "UNCLAIMED". I have installed the Windows driver "Belkin.inf" (X86 version) via ndiswrapper and it detects the hardware. Card remains "UNCLAIMED" though & doesn't appear in wireless network list for configuration.
By the way, I use WICD instead of Gnome Network Manager.

Any help gladly accepted.

Thanks****

---

### Post by siabost on 2009-02-26
[SOLVED}

 had been messing around with Network Manager, lost it & could not get it back. So I installed WICD.
With correct driver installed (via ndiswrapper)WICD didn't pick up network.

In WICD (not sure where as I only used WICD briefly)there was a menu to set the connection. In mine I noticed that against the Wired connection was entered "eth0" & against the Wireless connection it was blank. I entered the "Logical name" mentioned above, "wlan0" in my case & ticked (I think) a box to enable the connection. Okayed the settings and my network could be seen.

Alas for me...

In the end I couldn't get my security settings to work & ended up reinstalling Ubuntu (using the "manual" partitioning option) and only formatting the / (root) partition. That reinstated Gnome-network-manager, I loaded ndiswrapper, then the drivers, enabled my network (right-click Network Manager Icon), selected my now visible wireless network, entered my pass phrase & HALLELUJAH I was on!

To get the connection to connect to wireless on boot-up I had to go to (Pref or Administration) Menu/Network Tools, click on my network & when asked allow Network Manager access to "Keyring" to retrieve security details. It now connects on boot & seems to be working perfectly.

Hope this helps someone else.

):P

---

