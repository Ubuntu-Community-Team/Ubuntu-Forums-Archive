---
title: "Running wifi adapter on HP Pavilion g6 Notebook PC"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by himanshum83 on 2011-06-12
I have just installed ubuntu 11.04 on my new HP Pavilion g6 Notebook PC.
I am experiencing the issue with the Wifi network.
I have attached the screenshot for it.
Please help me in troubleshooting these setup.

Also, please find below the output for lshw cmd:
[INDENT]himanshu-hp-pavilion-g6-notebook-pc
    description: Notebook
    product: HP Pavilion g6 Notebook PC 
    vendor: Hewlett-Packard
    version: 0592110000204620000620100
    serial: 
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PAV X=MIN sku=LU897AV uuid=1CA723EA-C2D1-C8C2-1D4C-6E99C71DB949
  *-core
       description: Motherboard
       product: 1693
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 14.13
       serial: PCEVF00WB0T8EO
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.17
          date: 05/13/2011
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5773DH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 962AD3E4
             slot: Bottom-Slot 1 (top)
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5773DH0-CH9
             vendor: Samsung
             physical id: 1
             serial: 962AD3FD
             slot: Bottom-Slot 2 (under)
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1c
          bus info: cpu@0
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          slot: CPU
          size: 933MHz
          capacity: 4GHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 id=4 threads=4
        *-cache:0
             description: L3 cache
             physical id: 1d
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 1f
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 20
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 4.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 4.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 4.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 4.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 4.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 4.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 4.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 4.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 4.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 4.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 4.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 4.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 4.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 4.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 4.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 4.10
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 1e
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
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
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:4050(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:b6406100-b640610f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:b6405c00-b6405fff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:b6400000-b6403fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:b5400000-b63fffff ioport:b0400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 05
                serial: 78:e3:b5:4f:ea:c9
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.37 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:40 ioport:3000(size=256) memory:b0404000-b0404fff memory:b0400000-b0403fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:b4400000-b53fffff ioport:b1400000(size=16777216)
           *-network UNCLAIMED
                description: Network controller
                product: Ralink corp.
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:b4400000-b440ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:b3400000-b43fffff ioport:b2400000(size=16777216)
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: scsi4
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list emulated scsi-host
                configuration: driver=rts_pstor latency=0
                resources: irq:16 memory:b3400000-b3400fff
              *-disk
                   description: SCSI Disk
                   product: xD/SD/M.S.
                   vendor: Generic-
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/sdb
                   version: 1.00
                   serial: 3
                   capabilities: removable
                 *-medium
                      physical id: 0
                      logical name: /dev/sdb
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:b6405800-b6405bff
        *-pci:3
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
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:4048(size=8) ioport:405c(size=4) ioport:4040(size=8) ioport:4058(size=4) ioport:4020(size=32) memory:b6405000-b64057ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PB4O
                serial: 110428PBN408P7CXD3YE
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003315b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 3b0ca917-7d18-416d-a49a-5d144029fa43
                   size: 461GiB
                   capacity: 461GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-06-12 11:53:18 filesystem=ext4 lastmountpoint=/ modified=2011-06-12 12:16:57 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-12 13:49:35 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3893MiB
                   capacity: 3893MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3893MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: BD ROM BC-5541H
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 2.81
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             resources: memory:b6406000-b64060ff ioport:4000(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:21 memory:b6404000-b6404fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: MU06047
       vendor: Dynapack
       physical id: 1
       slot: Primary
       capacity: 47520mWh
       configuration: voltage=10.8V
[/INDENT]Regards
Himanshu

---

### Post by chili555 on 2011-06-12
> *-network UNCLAIMED
description: Network controller
product: Ralink corp.
vendor: Ralink corp.
physical id: 0
bus info: pci@0000:02:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:b4400000-b440ffffWe need more information. Please run and post:```
lspci -nn | grep Ralink
```Thanks.

---

### Post by himanshum83 on 2011-06-12
Here is the output:

lspci -nn | grep Ralink
02:00.0 Network controller [0280]: Ralink corp. Device [1814:539f]

---

### Post by chili555 on 2011-06-12
Please see post #24 here. You have the same device.

[http://ubuntuforums.org/showthread.php?t=1740963](http://ubuntuforums.org/showthread.php?t=1740963)

---

### Post by himanshum83 on 2011-06-13
Thanks Chilli555.
Now my Wifi is working fine.

I have one more issue. The bluetooth is not able to find my bluetooth head set.
Can you please guide me on that as well.

I have attached a scrn shot for it. When I click on Set up new device and search for a bluetooth device, it is not able to find my headset.

Regards
Himanshu

---

### Post by chili555 on 2011-06-14
> **himanshum83 said:**
> Thanks Chilli555.
Now my Wifi is working fine.

I have one more issue. The bluetooth is not able to find my bluetooth head set.
Can you please guide me on that as well.

I have attached a scrn shot for it. When I click on Set up new device and search for a bluetooth device, it is not able to find my headset.

Regards
HimanshuI know next to nothing about bluetooth. I suggest you start a new thread.

---

### Post by STUPID USERNAME on 2011-06-16
> **chili555 said:**
> Please see post #24 here. You have the same device.

[http://ubuntuforums.org/showthread.php?t=1740963](http://ubuntuforums.org/showthread.php?t=1740963)

Hi!
I have just installed ubuntu 11.04 on my mothers HP Pavilion G6. It's the same Notebook and obviously it has the same network controller (I even checked).

Since I installed 11.04, it can't connect to the internet, wired or wireless. (It can on my desktop pc with ubuntu 11.04 (wired and wireless) which I'm using right now to write this).

I clicked on the link you posted and went to the post 24:
I have a few questions:

1. Can I download it on this computer and then transfer it to my mother's computer with a USB stick? (I'm a noob btw, just in case you wonder why such a question).
2. Should I only download the .patch files or also the .spec, .changes and preamble files?

Thank you very much for your time!

(After convincing my mother to let me install ubuntu on her computer, replacing windows 7, I must not fail her! Internet is the only reason she has a computer!)

---

### Post by chili555 on 2011-06-16
> 1. Can I download it on this computer and then transfer it to my mother's computer with a USB stick? (I'm a noob btw, just in case you wonder why such a question).Yes, you can. Installation requires prerequisites, linux-headers and build-essential. They are difficult to grab and transfer. Can't we troubleshoot the wired first?> 2. Should I only download the .patch files or also the .spec, .changes and preamble files?Just the patch files.> After convincing my mother to let me install ubuntu on her computer, replacing windows 7, I must not fail her! Internet is the only reason she has a computer!I hear ya, man! A certain lady in this house of a certain age feels the same way! However, she has a live-in wireless d00d.

---

### Post by STUPID USERNAME on 2011-06-16
> Just the patch files.
Thank you!
> Can't we troubleshoot the wired first?
ALright!

_**Here is some info from running lshw:**_

 *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 05
                serial: 64:31:50:8e:6e:e6
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff




 *-network UNCLAIMED
                description: Network controller
                product: Ralink corp.
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f0200000-f020ffff


_**And here some info from running lspci:**_

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Network controller: Ralink corp. Device 539f


I don't know if that wast helpful!

---

### Post by chili555 on 2011-06-16
> driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=noYou have a driver but link=no. Was the ethernet attached at the time? Are you, by chance, dual-booting with that other OS?

---

### Post by STUPID USERNAME on 2011-06-17
> You have a driver but link=no. Was the ethernet attached at the time? Are you, by chance, dual-booting with that other OS?
No it wasn't. And, no, there's only ubuntu...

---

### Post by chili555 on 2011-06-17
> **STUPID USERNAME said:**
> No it wasn't. And, no, there's only ubuntu...> Can't we troubleshoot the wired first? It will be very difficult to get the wired going without the ethernet cable attached.

---

### Post by STUPID USERNAME on 2011-06-17
> It will be very difficult to get the wired going without the ethernet cable attached.
Ok I'm sorry I'll run the command again while connected and come back.
should I connect it to the router or directly to the modem?

---

### Post by chili555 on 2011-06-17
It will be very difficult to get the wired going without the ethernet cable attached. I thought we were troubleshooting the wired connection. No?

---

### Post by chili555 on 2011-06-17
> should I connect it to the router or directly to the modem?
The router, preferably.

---

### Post by STUPID USERNAME on 2011-06-17
Ok I did both.
First directly to the modem. I could see the network and click on it, and the computer would try to connect to it for several seconds, but failed everytime (I tried thrice).

Then I tried directly to the router. I could see the network and connect to it. so when wired to the router I have access to the internet. The reason I didn't mention this before is that I thought that it didn't work because that what's my brother told me (I ask him to check if we could access the internet if we wired the computer to the modem or router).
I'm sorry about that.
This is what i get from running the command lshw, first when wired to the modem, then when wired to the router. The only difference seems to be the IP appears in the second one.

*-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 05
                serial: 64:31:50:8e:6e:e6
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff



 *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 05
                serial: 64:31:50:8e:6e:e6
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

---

### Post by chili555 on 2011-06-17
Now that you have internet access, please do:```
sudo apt-get install build-essential linux-headers-generic
```Then follow the instructions linked in your post #7 above. Post back if you get stuck or need help.

---

### Post by STUPID USERNAME on 2011-06-17
> **chili555 said:**
> Now that you have internet access, please do:```
sudo apt-get install build-essential linux-headers-generic
```Then follow the instructions linked in your post #7 above. Post back if you get stuck or need help.

Ok, I did and the terminal told me that I already had the latest version of build-essential and linux-headers-generic.
Then I downloaded the patch files, put them in my '2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO' folder (which is in the 'downloads' folder).
Then I entered the code and that's what I got:

maria@princesa:~$ patch -p0 < rt5390sta-2.4.0.4-config.patch 
bash: rt5390sta-2.4.0.4-config.patch: No such file or directory
maria@princesa:~$ patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
bash: rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch: No such file or directory
maria@princesa:~$ patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
bash: rt5390sta-2.4.0.4-reduce_debug_output.patch: No such file or directory
maria@princesa:~$ patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
bash: rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch: No such file or directory
maria@princesa:~$ patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
bash: rt5390sta-2.4.0.4-return_nonvoid_function.patch: No such file or directory
maria@princesa:~$ patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
bash: rt5390sta-2.4.0.4-WPA-mixed.patch: No such file or directory
maria@princesa:~$ sudo su 
[sudo] password for maria: 
Sorry, try again.
[sudo] password for maria: 
root@princesa:/home/maria# cp RT2860STA.dat RT5390STA.dat
cp: cannot stat `RT2860STA.dat': No such file or directory
root@princesa:/home/maria# mkdir -p /etc/Wireless/RT5390STA
root@princesa:/home/maria# cp RT5390STA.dat /etc/Wireless/RT5390STA
cp: cannot stat `RT5390STA.dat': No such file or directory
root@princesa:/home/maria# make clean
make: *** No rule to make target `clean'.  Stop.
root@princesa:/home/maria# make
make: *** No targets specified and no makefile found.  Stop.
root@princesa:/home/maria# make install
make: *** No rule to make target `install'.  Stop.
root@princesa:/home/maria# modprobe rt5390sta
FATAL: Module rt5390sta not found.
root@princesa:/home/maria# exit
exit
maria@princesa:~$ 


That doesn't look to good :S

---

### Post by chili555 on 2011-06-17
> maria@princesa:**[COLOR="Red"]~[/COLOR]**$ patch -p0 < rt5390sta-2.4.0.4-config.patch The little ~ symbol is Linux-land code for your home directory. That's not where the Makefile and patch files are. > put them in my '2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DP O' folder (which is in the 'downloads' folder).In the terminal, change directories (cd) to the location of these files:```
cd Downloads/2010
```Press Tab and the remainder of the name will fill in magically. Press Enter. You will know you are in the right location if you list (ls) the contents of the directory and see all the patch files, Makefile, etc. listed:```
ls
```If so, run the patch commands and continue the process.

---

### Post by STUPID USERNAME on 2011-06-18
Ok I did it all. The cd Téléchargements/2010... (Téléchargements means Downloads) command, then the ls command, and finally the patch commands. 
That'S what I got, and at the end (At the word 'exit') I pressed enter.
(After restarting the computer, I still coudn't connect wireless).

maria@princesa:~$ cd Téléchargements/2010
bash: cd: Téléchargements/2010: No such file or directory
maria@princesa:~$ cd Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
maria@princesa:~/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_
DPO$ 
Display all 2289 possibilities? (y or n)
maria@princesa:~/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_
DPO$ ls
chips
common
include
iwpriv_usage.txt
Makefile
os
README_STA_pci
RT2860STACard.dat
RT2860STA.dat
rt5390sta-2.4.0.4-config.patch
rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch
rt5390sta-2.4.0.4-reduce_debug_output.patch
rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch
rt5390sta-2.4.0.4-return_nonvoid_function.patch
rt5390sta-2.4.0.4-WPA-mixed.patch
sta
sta_ate_iwpriv_usage.txt
tools
maria@princesa:~/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_
DPO$ patch -p0 < rt5390sta-2.4.0.4-config.patch 
patching file Makefile
patching file os/linux/config.mk
maria@princesa:~/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_
DPO$ patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patching file include/rtmp_def.h
maria@princesa:~/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_
DPO$ patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patching file include/os/rt_linux.h
maria@princesa:~/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_
DPO$ patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patching file include/os/rt_linux.h
patching file os/linux/pci_main_dev.c
patching file os/linux/rt_main_dev.c
maria@princesa:~/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_
DPO$ patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patching file os/linux/rt_main_dev.c
maria@princesa:~/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_
DPO$ patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
patching file common/cmm_wpa.c
maria@princesa:~/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_
DPO$ sudo su 
[sudo] password for maria: 
Sorry, try again.
[sudo] password for maria: 
root@princesa:/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiF
iBTCombo_DPO# cp RT2860STA.dat RT5390STA.dat
root@princesa:/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiF
iBTCombo_DPO# mkdir -p /etc/Wireless/RT5390STA
root@princesa:/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiF
iBTCombo_DPO# cp RT5390STA.dat /etc/Wireless/RT5390STA
root@princesa:/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiF
iBTCombo_DPO# make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -rf os/linux/Makefile
root@princesa:/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiF
iBTCombo_DPO# make
make -C tools
make[1]: Entering directory `/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function &#8216;WscEncryptData&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function &#8216;WscDecryptData&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1096 bytes is larger than 1024 bytes
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c: In function &#8216;InitLookupTable&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:635:2: warning: missing braces around initializer
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:635:2: warning: (near initialization for &#8216;WordStruct.field&#8217;)
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c: In function &#8216;BssTableSetEntry&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:6019:39: warning: operation on &#8216;Tab->BssOverlapNr&#8217; may be undefined
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c: In function &#8216;BssTableSortByRssi&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:6380:1: warning: the frame size of 1724 bytes is larger than 1024 bytes
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/action.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitAsicFromEEPROM&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init.c:1558:9: warning: unused variable &#8216;EfuseData&#8217;
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.c: In function &#8216;PeerPairMsg4Action&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.c:1109:11: warning: unused variable &#8216;group_cipher&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.c: In function &#8216;PeerGroupMsg2Action&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.c:1454:11: warning: unused variable &#8216;group_cipher&#8217;
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/dfs.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/spectrum.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicSwitchChannel&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1243:15: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1384:17: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1392:17: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1403:16: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicEnableIbssSync&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5431:11: warning: unused variable &#8216;beaconLen&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicAddPairwiseKeyEntry&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:6159:9: warning: unused variable &#8216;CipherAlg&#8217;
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtScanAction&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:755:1: warning: the frame size of 1244 bytes is larger than 1024 bytes
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtJoinAction&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:1085:1: warning: the frame size of 1296 bytes is larger than 1024 bytes
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function &#8216;MlmeStartReqAction&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:571:1: warning: the frame size of 1064 bytes is larger than 1024 bytes
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:1755:1: warning: the frame size of 1304 bytes is larger than 1024 bytes
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/connect.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/connect.c: In function &#8216;CntlOidScanProc&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/connect.c:314:1: warning: the frame size of 1748 bytes is larger than 1024 bytes
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/ags.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sta_cfg.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sta_cfg.c: In function &#8216;Set_Antenna_Proc&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sta_cfg.c:1387:11: warning: &#8216;UsedAnt&#8217; may be used uninitialized in this function
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c: In function &#8216;FrequencyCalibration&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:214:18: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:227:18: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:242:18: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:264:18: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:277:18: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:292:18: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_iwaplist&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c:592:1: warning: the frame size of 1288 bytes is larger than 1024 bytes
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_siwmlme&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c:1962:1: warning: the frame size of 1652 bytes is larger than 1024 bytes
In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess.h:571:0,
                 from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:211,
                 from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/os/rt_linux.h:40,
                 from /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp_os.h:32,
                 from /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rt_config.h:60,
                 from /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c:28:
In function &#8216;copy_from_user&#8217;,
    inlined from &#8216;RTMPSetInformation&#8217; at /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c:3046:28:
/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to &#8216;copy_from_user_overflow&#8217; declared with attribute warning: copy_from_user() buffer size is not provably correct
In function &#8216;copy_from_user&#8217;,
    inlined from &#8216;RTMPSetInformation&#8217; at /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c:3522:28:
/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to &#8216;copy_from_user_overflow&#8217; declared with attribute warning: copy_from_user() buffer size is not provably correct
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlMAC&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c:5835:1: warning: the frame size of 1336 bytes is larger than 1024 bytes
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlE2PROM&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/sta_ioctl.c:6034:1: warning: the frame size of 1344 bytes is larger than 1024 bytes
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/rt_linux.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevDetach&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/rt_linux.c:1701:38: warning: initialization discards qualifiers from pointer target type
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/rt_linux.c:1738:38: warning: initialization discards qualifiers from pointer target type
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ba_action.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:463:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type
include/linux/pci.h:736:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;INT *&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:482:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type
include/linux/pci.h:736:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;INT *&#8217;
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt30xx.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt3090.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt33xx.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt3390.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt5390.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/pci_main_dev.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/pci_main_dev.c: In function &#8216;rt2860_probe&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/pci_main_dev.c:305:13: warning: assignment discards qualifiers from pointer target type
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.o
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function &#8216;ATETxPwrHandler&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:1802:45: warning: unused variable &#8216;CfgOfTxPwrCtrlOverMAC&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function &#8216;ATEAsicSwitchChannel&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5076:15: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5230:16: warning: comparison of distinct pointer types lacks a cast
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5007:21: warning: unused variable &#8216;RFValue2&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5002:16: warning: unused variable &#8216;RFRegTable&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5001:43: warning: unused variable &#8216;R4&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5001:17: warning: unused variable &#8216;R3&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5001:9: warning: unused variable &#8216;R2&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_Proc&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7564:5: warning: passing argument 3 of &#8216;eFuseWrite&#8217; from incompatible pointer type
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp.h:5889:10: note: expected &#8216;PUSHORT&#8217; but argument is of type &#8216;UCHAR *&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7477:42: warning: unused variable &#8216;ChannelPower&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7649:5: warning: passing argument 3 of &#8216;eFuseWrite&#8217; from incompatible pointer type
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp.h:5889:10: note: expected &#8216;PUSHORT&#8217; but argument is of type &#8216;UCHAR *&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_READ_EXTERNAL_TSSI_Proc&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:8011:9: warning: passing argument 3 of &#8216;eFuseWrite&#8217; from incompatible pointer type
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp.h:5889:10: note: expected &#8216;PUSHORT&#8217; but argument is of type &#8216;UCHAR *&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7965:18: warning: unused variable &#8216;EEPTemp&#8217;
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_Proc&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7477:9: warning: &#8216;BbpData&#8217; may be used uninitialized in this function
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7584:17: warning: &#8216;BbpData&#8217; may be used uninitialized in this function
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function &#8216;RTATEGetTssiByChannel&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7708:8: warning: &#8216;BbpData&#8217; may be used uninitialized in this function
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_READ_EXTERNAL_TSSI_Proc&#8217;:
/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7964:28: warning: &#8216;BbpData&#8217; may be used uninitialized in this function
  CC [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.o
  LD [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/rt5390sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/rt5390sta.mod.o
  LD [M]  /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/rt5390sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
root@princesa:/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiF
iBTCombo_DPO# make install
make -C /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-8-generic
make[1]: Leaving directory `/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
root@princesa:/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiF
iBTCombo_DPO# modprobe rt5390sta
root@princesa:/home/maria/Téléchargements/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiF
iBTCombo_DPO# exit

Something I did wrong?

---

### Post by chili555 on 2011-06-18
> Something I did wrong?Not that I see. Sure, there are several warnings but no errors that prevent your wireless from working. It looks like you did a very nice job!

Let's do some additional diagnostics:```
rfkill list all
dmesg | grep 539
```

---

### Post by STUPID USERNAME on 2011-06-19
> Let's do some additional diagnostics:
Ok! Here it is:

maria@princesa:~$ rfkill list all
maria@princesa:~$ dmesg | grep 539
[    0.000000]   HighMem zone: 5391 pages used for memmap
[    0.412162] pci 0000:03:00.0: [1814:539f] type 0 class 0x000280
[   12.666549] rt5390 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.666608] rt5390 0000:03:00.0: setting latency timer to 64
maria@princesa:~$

---

### Post by chili555 on 2011-06-19
It looks promising. > [ 0.412162] pci[COLOR="Red"] 0000:03:00.0[/COLOR]: [1814:539f] type 0 class 0x000280
[ 12.666549] rt5390 [COLOR="Red"]0000:03:00.0[/COLOR]: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 12.666608] rt5390 [COLOR="Red"]0000:03:00.0[/COLOR]: setting latency timer to 64It seems as if the driver and the hardware associate. Is there no wireless interface?```
iwconfig
dmesg | grep wlan
```

---

### Post by STUPID USERNAME on 2011-06-20
OK here it is

maria@princesa:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

maria@princesa:~$ dmesg | grep wlan
[   23.984081] wlan0: no IPv6 routers present
maria@princesa:~$

---

### Post by chili555 on 2011-06-20
Looks pretty good! Does it see networks when you click the Network Manager icon? How about this?```
sudo iwlist wlan0 scan
```

---

### Post by STUPID USERNAME on 2011-06-20
> Does it see networks when you click the Network Manager icon? 
No! I don't know why!
Here's what I get from the comand:

maria@princesa:~$ sudo iwlist wlan0 scan
[sudo] password for maria: 
wlan0     No scan results

---

### Post by chili555 on 2011-06-20
Something's wacky. Let's see your entire dmesg and other details. Let's create a big text file, zip it and please post it as an attachment to your reply:```
dmesg > maria.txt
lspci -nn >> maria.txt
lsmod >> maria.txt
modinfo rt5390sta >> maria.txt
zip maria.zip maria.txt
```Please attach the file maria.zip to your reply using the paperclip tool at the top of the reply box.

---

### Post by STUPID USERNAME on 2011-06-20
Good news! I saw your last post from my computer, so I came to my mother's computer and turned it on. Like everytime I start it to reply to your last post, I first disconnected it from the router to see if the wireless problem was solved. It was. I can now see all the wireless networks available, included ours, and connect to it. I restarted the computer twice, just to be sure it wasn't a temporary benevolent bug. It's not! That's damn mysterious! Amazing!

I must say, I'm very thankful for people like you, who freely help others (most likely strangers most of the time) in need.
I admire you people. MUCH respect.
Thank you!
If I get another network problem in the next few days I'll be sure to come to you for help! :D

---

### Post by chili555 on 2011-06-20
> **STUPID USERNAME said:**
> Good news! I saw your last post from my computer, so I came to my mother's computer and turned it on. Like everytime I start it to reply to your last post, I first disconnected it from the router to see if the wireless problem was solved. It was. I can now see all the wireless networks available, included ours, and connect to it. I restarted the computer twice, just to be sure it wasn't a temporary benevolent bug. It's not! That's damn mysterious! Amazing!

I must say, I'm very thankful for people like you, who freely help others (most likely strangers most of the time) in need.
I admire you people. MUCH respect.
Thank you!
If I get another network problem in the next few days I'll be sure to come to you for help! :DAwesome indeed! I'm glad it's working. Have fun!

Thank you for your very kind comments.

---

### Post by maberalc on 2011-07-21
How can i change the configuration of my pavilion g6-1070es to ahci?

---

### Post by chili555 on 2011-07-21
> **maberalc said:**
> How can i change the configuration of my pavilion g6-1070es to ahci?I'm not sure but I suspect in the BIOS.

---

