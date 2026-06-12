---
title: "Ndiswrapper Causes Ubuntu To Lock Up | Even LiveCD Locks Up"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by SuperBuntu on 2009-02-07
been using ubuntu since 7.10, i have an unsupported wifi dongle that i used to use ndiswrapper to get to work. 

this morning i woke up booted up my computer, and ubuntu would freeze up at the GDM, i have /home on a separate partition, so when rebooting didn't work i simply reinstalled the system, installed my wifi drivers (that i have been using from 7.10 => 8.10) via ndiswrapper and ubuntu froze immediately, i realized that it was my wifi that was the problem, seeing as i had already reinstalled the system i was clueless as to what could be causing this. I tried the liveCD (using Ethernet) installed ndiswrapper added the driver and the liveCD FROZE!!?? 

 heres the output of **lshw**
```
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 946MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.4
          serial: 
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni monitor ds_cpl cid xtpr
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_sis latency=128 module=pata_sis
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:50:8d:6f:2a:cd
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.64 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=32 module=sata_sis
        *-multimedia
             description: Multimedia audio controller
             product: SB Audigy
             vendor: Creative Labs
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
        *-input
             description: Input device controller
             product: SB Audigy Game Port
             vendor: Creative Labs
             physical id: 9.1
             bus info: pci@0000:00:09.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
        *-firewire
             description: FireWire (IEEE 1394)
             product: SB Audigy FireWire Port
             vendor: Creative Labs
             physical id: 9.2
             bus info: pci@0000:00:09.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage

```

i had been using the wireless perfectly up until yesterday, no new hardware, no removed hardware.

---

### Post by SuperBuntu on 2009-02-07
Bump

---

### Post by kevdog on 2009-02-07
Do you know the chipset contained in your device?  Although ndiswrapper is applicable to the newer releases, with the advent of open source drivers and the like, its support is being phased out.  Possibly time to switch from ndiswrapper to another solution.

---

### Post by SuperBuntu on 2009-02-07
> **kevdog said:**
> Do you know the chipset contained in your device?  Although ndiswrapper is applicable to the newer releases, with the advent of open source drivers and the like, its support is being phased out.  Possibly time to switch from ndiswrapper to another solution.

Your answer doesent help, Ive been usng ndiswrapper for one year without issue, and ive been using the version shipped with intrepid, since intrepid's release without any issues.

suddenly it breaks down, i ask for help, and you tell me to switch to "another solution" which is what exactly? 

why dont I just fix what used to **_work_**? rather than hunting down chipsets.

---

