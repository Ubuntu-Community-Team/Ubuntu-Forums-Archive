---
title: "Very slow wireless internet with lag spikes"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by MagedKadri on 2012-12-23
Hi everyone :)
So I'm new to linux(loving it so far) and im using ubuntu 12.04 but i've been getting problems with the internet connection, (there was no problem with windows 8 or my sisters laptop...)

[http://www.speedtest.net/result/2390969211.png](http://www.speedtest.net/result/2390969211.png)

I'm getting very unusual lag spikes, i had them before but now i can't even use my computer properly... any ideas?

also im using firefox... so anyhting i can do??

---

### Post by MagedKadri on 2012-12-26
i switched to chrome it was fast at first, (or it felt like it) then the lag kicked in. i also noticed every time i load up a youtube video it buffers the first part very quickly then the internet drops... and sometimes it wont even load at all... since i get crazy spikes on speedtest...

PLZ SOMEONE HELP ME THIS LAPTOP IS BECOMING UNUSABLE AND I DONT WANT WINDOWS BACK ON IT.

---

### Post by thenox on 2013-01-03
Have you had any luck with this? I definitely understand. It's really frustrating when you're trying to go w/ Linux and get away from Windows, but one or two issues make it difficult. 
In a terminal window (same as Windows Command Prompt), try "lshw"  (w/o the quotes).
Copy and paste the output here. 

You could also type "ping google.com" (again, no quotations) and post the result here. 
I'm having similar issues with Firefox, so I feel your pain.

---

### Post by MagedKadri on 2013-01-07
maged-vpceb3afd           
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3620MiB
     *-cpu
          product: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:e080(size=8)
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:42 memory:f600a000-f600a00f
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f6008000-f60083ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f6000000-f6003fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:f4c00000-f5ffffff ioport:f6700000(size=2097152)
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 00:26:c7:7c:f2:64
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-35-generic firmware=39.31.5.1 build 35138 ip=192.168.0.12 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:45 memory:f4c00000-f4c01fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:c000(size=4096) memory:f3800000-f4bfffff ioport:f6500000(size=2097152)
           *-generic:0
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:f3802000-f38020ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: Memory Stick Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:f3801000-f38010ff
           *-generic:2
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:03:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:19 memory:f3800000-f38000ff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:b000(size=4096) memory:f2400000-f37fffff ioport:f6300000(size=2097152)
           *-network
                description: Ethernet interface
                product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 11
                serial: 54:42:49:76:f1:8b
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 multicast=yes port=twisted pair
                resources: irq:41 memory:f2420000-f2423fff ioport:b000(size=256) memory:f2400000-f241ffff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:a000(size=4096) memory:f0400000-f23fffff ioport:f6100000(size=2097152)
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f6007000-f60073ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:e070(size=8) ioport:e060(size=4) ioport:e050(size=8) ioport:e040(size=4) ioport:e020(size=32) memory:f6006000-f60067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6005000-f60050ff ioport:e000(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:18 memory:f6004000-f6004fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by MagedKadri on 2013-01-07
PING google.com (173.194.74.113) 56(84) bytes of data.
64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=1 ttl=49 time=9.84 ms
    64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=2 ttl=49 time=9.78 ms
64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=3 ttl=49 time=9.93 ms
64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=4 ttl=49 time=9.86 ms
64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=5 ttl=49 time=9.90 ms
64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=6 ttl=49 time=10.0 ms
64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=7 ttl=49 time=9.86 ms
64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=8 ttl=49 time=9.92 ms
64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=9 ttl=49 time=9.84 ms
64 bytes from qe-in-f113.1e100.net (173.194.74.113): icmp_seq=10 ttl=49 time=9.96 ms

I  have tried switching to chrome, everything seemed good but now the  problem is back and its worst than before... could it be a virus or  something?

And thank you for trying to help me thenox!! :)

---

### Post by thenox on 2013-01-08
Glad to offer some assistance, but I'm still an "intermediate novice." 
Well, it looks like it's getting to the net, seeing as the ping returns that output.

Oh, btw, could you paste any further code using the code tags? Makes it easier to read. Just select the code and hit the # button when replying. (Not in the Quick Reply.)
That way your code would be tidied up like this:

```
maged-vpceb3afd           
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3620MiB
     *-cpu
          product: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon  pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64  monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2  popcnt lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid  cpufreq
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:e080(size=8)
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:42 memory:f600a000-f600a00f
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f6008000-f60083ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f6000000-f6003fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:f4c00000-f5ffffff ioport:f6700000(size=2097152)
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 00:26:c7:7c:f2:64
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi  driverversion=3.2.0-35-generic firmware=39.31.5.1 build 35138  ip=192.168.0.12 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:45 memory:f4c00000-f4c01fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:c000(size=4096) memory:f3800000-f4bfffff ioport:f6500000(size=2097152)
           *-generic:0
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:f3802000-f38020ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: Memory Stick Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:f3801000-f38010ff
           *-generic:2
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:03:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:19 memory:f3800000-f38000ff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:b000(size=4096) memory:f2400000-f37fffff ioport:f6300000(size=2097152)
           *-network
                description: Ethernet interface
                product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 11
                serial: 54:42:49:76:f1:8b
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical  tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes  driver=sky2 driverversion=1.30 firmware=N/A latency=0 multicast=yes  port=twisted pair
                resources: irq:41 memory:f2420000-f2423fff ioport:b000(size=256) memory:f2400000-f241ffff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:a000(size=4096) memory:f0400000-f23fffff ioport:f6100000(size=2097152)
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f6007000-f60073ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:e070(size=8) ioport:e060(size=4)  ioport:e050(size=8) ioport:e040(size=4) ioport:e020(size=32)  memory:f6006000-f60067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6005000-f60050ff ioport:e000(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:18 memory:f6004000-f6004fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
WARNING: output may be incomplete or inaccurate, you should run this program as super-user. 	
```

I'm still learning my commands, but you could try these and post the output:
netstat -tup
ifconfig

---

### Post by thenox on 2013-01-08
Oh, and here are some links for Linux commands. The first link is nice because you can look up a task you want to do, such as "How do I compare two files?", and get the appropriate commands.

[http://www.perpetualpc.net/srtd_commands_rev.html#reference](http://www.perpetualpc.net/srtd_commands_rev.html#reference)

[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)

[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

[http://community.linuxmint.com/tutorial/view/244](http://community.linuxmint.com/tutorial/view/244)

A-Z List of Bash CLI
[http://ss64.com/bash/](http://ss64.com/bash/)

Hope that helps.

---

### Post by MagedKadri on 2013-01-08
Thx!!

```
maged@maged-VPCEB3AFD:~$ netstat -tup
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 maged-VPCEB3AFD.l:59729 yyz06s06-in-f12.1:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:43160 CRL.VERISIGN.NET:http   ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:36808 ob-in-f94.1e100.n:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:45722 yyz06s07-in-f15.1:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:52553 66.185.85.178:https     ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:46137 yyz06s06-in-f7.1e:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:41885 yyz06s06-in-f9.1e:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:43150 yyz06s06-in-f15.1e:http ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:32816 l1.ycs.vip.nyc.yah:http TIME_WAIT   -               
tcp        1      0 maged-VPCEB3AFD.l:49851 mistletoe.canonica:http CLOSE_WAIT  2274/ubuntu-geoip-p
tcp        0      0 maged-VPCEB3AFD.l:43147 yyz06s06-in-f15.1e:http ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:55248 kwaimuk.canonical:https ESTABLISHED 2666/python     
tcp        0      0 maged-VPCEB3AFD.l:52555 66.185.85.178:https     ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:43156 CRL.VERISIGN.NET:http   ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:39798 channel-ecmp-13-p:https ESTABLISHED 2289/chromium-brows
tcp        1      1 maged-VPCEB3AFD.l:41887 yyz06s06-in-f9.1e:https LAST_ACK    -               
tcp        0      0 maged-VPCEB3AFD.l:56838 ob-in-f106.1e100.:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:40483 yyz06s06-in-f6.1e:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:43157 CRL.VERISIGN.NET:http   ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:53280 yyz06s06-in-f3.1e:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:43148 yyz06s06-in-f15.1e:http ESTABLISHED 2289/chromium-brows
tcp        1      1 maged-VPCEB3AFD.l:53285 yyz06s06-in-f3.1e:https LAST_ACK    -               
tcp        0      0 maged-VPCEB3AFD.l:36185 jujube.canonical.c:http ESTABLISHED 2303/firefox    
tcp        0      0 maged-VPCEB3AFD.l:43152 yyz06s06-in-f15.1e:http ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:43159 CRL.VERISIGN.NET:http   ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:38297 OCSP.SFO1.VERISIGN:http ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:43162 CRL.VERISIGN.NET:http   ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:32817 l1.ycs.vip.nyc.yah:http TIME_WAIT   -               
tcp        0      0 maged-VPCEB3AFD.l:41889 yyz06s06-in-f9.1e:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:47721 ie-in-f95.1e100.n:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:52554 66.185.85.178:https     ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:43151 yyz06s06-in-f15.1e:http ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:52552 66.185.85.178:https     ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:46911 ie-in-f84.1e100.n:https ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:43149 yyz06s06-in-f15.1e:http ESTABLISHED 2289/chromium-brows
tcp        0      0 maged-VPCEB3AFD.l:53287 yyz06s06-in-f3.1e:https ESTABLISHED 2289/chromium-brows

```

---

### Post by MagedKadri on 2013-01-08
```
maged@maged-VPCEB3AFD:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 54:42:49:76:f1:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3860 (3.8 KB)  TX bytes:3860 (3.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:7c:f2:64  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c7ff:fe7c:f264/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2311526 (2.3 MB)  TX bytes:451125 (451.1 KB)


```

---

### Post by MagedKadri on 2013-01-08
i noticed something rather unusual... when i play a youtube video, it would buffer the first 10% of the video very very quickly then the internet would just stop.

---

### Post by MagedKadri on 2013-01-08
i noticed something rather unusual... when i play a youtube video, it would buffer the first 10% of the video very very quickly then the internet would just stop. The computer is almost unusable now...

---

### Post by thenox on 2013-01-08
> **MagedKadri said:**
> i noticed something rather unusual... when i play a youtube video, it would buffer the first 10% of the video very very quickly then the internet would just stop.

Interesting. I'm not sure what that would mean. You could try disabling IPv6 and see if that helps. I'm not in front of my Ubuntu machine so I can't recall where it is. 
You might try these links:
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

[http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html](http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html)

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

---

### Post by MagedKadri on 2013-01-08
OMG fixed it finally :P it was the stupid internet provider that messed up, but thank you very much!!!

---

### Post by thenox on 2013-01-09
Great! Glad to hear it's fixed.

---

