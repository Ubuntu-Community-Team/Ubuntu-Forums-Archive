---
title: "Switchable graphic-cards Intel/ATI 10.04"
date: 2012-09-27
forum: Multimedia Software
---

### Post by jasch123 on 2012-09-27
Hi

With some help I finally got my WLan working.
But now I've got another problem, well I've got an Laptop with switchable graphic-cards, and for energy saving reasons I would like to switch between them.
Now you'll say this should work with a new ATI driver (Radeon HD 7730M), but i tried to install it and only got an error where i could switch back to the old driver.(Upgrading to a new ubuntu version isn't possible there may be problems with CAElinux based on ubuntu 10.04)

Is there a way to switch manually between the cards? 
How can I see which card is active? (Maybe the internal graphic is enough for me, but first I've got to know which one is active (to test how it works with CAD programs)

lshw shows this with 2 unclaimed VGA compatible controllers... (and many more unclaimed entrys...:mad:)

Anyone an idea? Would be nice thanks.

```
description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 5844MiB
     *-cpu
          product: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:c0000000-c0ffffff ioport:a0000000(size=268435456)
           [B]*-display UNCLAIMED
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:a0000000-afffffff(prefetchable) memory:c0000000-c003ffff ioport:3000(size=256) memory:c0040000-c005ffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:c1000000-c13fffff memory:b0000000-[/B]bfffffff(prefetchable) ioport:4000(size=64)
        *-usb:0
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:21 memory:c1600000-c160ffff
        *-communication UNCLAIMED
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:c1614000-c161400f
        *-usb:1
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c1619000-c16193ff
        *-multimedia UNCLAIMED
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:c1610000-c1613fff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) ioport:c1400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 07
                serial: d4:be:d9:56:21:e0
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
                resources: irq:27 ioport:2000(size=256) memory:c1404000-c1404fff(prefetchable) memory:c1400000-c1403fff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:c1500000-c15fffff
           *-network
                description: Wireless interface
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: c4
                serial: 84:a6:c8:4a:4b:d3
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=2.6.32-43-generic firmware=18.168.6.1 ip=192.168.0.2 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:29 memory:c1500000-c1501fff
        *-usb:2
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:c1618000-c16183ff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:c1617000-c16177ff
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c1615000-c16150ff ioport:4040(size=32)

```

---

### Post by jasch123 on 2012-10-01
Hi

well I tried to update X-server, but this hab no effect still no card is claimed...

There is a driver for my internal INtel HD 4000 from [http://intellinuxgraphics.org/2012.07.html](http://intellinuxgraphics.org/2012.07.html)
But it needs kernel 3.4... so I can forget about that...

Anyone an idea how to get atleast one card running with the right drivers?

---

