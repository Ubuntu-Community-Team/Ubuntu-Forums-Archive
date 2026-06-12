---
title: "My sound was working but now it is not"
date: 2009-10-11
forum: Multimedia Software
---

### Post by vvfrn on 2009-10-11
Please I have done everything!
My computer is from the intel family
cpu
          product: Intel(R) Celeron(TM) CPU                1300MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.1
          size: 1300MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82815 Chipset Graphics Controller (CGC)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: b
                bus info: pci@0000:02:0b.0
                logical name: eth0
                version: 10
                serial: 00:40:f4:43:71:4c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.2 latency=66 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-communication
                description: Modem
                product: HSP MicroModem 56
                vendor: PCTel Inc
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: driver=serial latency=0
           *-network:1
                description: Ethernet interface
                product: SMC2-1211TX
                vendor: Accton Technology Corporation
                physical id: f
                bus info: pci@0000:02:0f.0
                logical name: eth1
                version: 10
                serial: 00:30:f1:26:2b:90
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=66 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

### Post by antonkedrov on 2009-10-11
which version of ubuntu do you use?
9.04? or 9.10?

please post here sreenshot configuration your sound applet

---

### Post by vvfrn on 2009-10-11
9.04 ! I never knew 9.10 was aviliable! thanks BTw I just downloaded a new ubuntu and it was solved

---

### Post by Stochastic on 2009-10-11
Moved to Multimedia & Video.

---

### Post by antonkedrov on 2009-10-11
> **vvfrn said:**
> 9.04 ! I never knew 9.10 was aviliable! thanks BTw I just downloaded a new ubuntu and it was solved

))))))
btw ubuntu 9.10 is beta, keep it in your mind ;)

---

