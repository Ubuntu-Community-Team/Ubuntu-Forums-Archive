---
title: "Dumbfounded and frustrated by ubuntu atm, Please help me."
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by XxsydenxX on 2009-04-25
A dear friend of mine had quite a few trojans on his Windows OS, so he agreed for me to format windows and install ubuntu so he would no longer have to deal with such things. Well i install ubuntu 9.04 and everything except networking is up and working...beautifully at that, he loves it.

This is the card he is using, Intel Corporation 82801DB pro/100 VE (LOM) Ethernet controller (rev 82)

I tried something a good friend of mine told me to do, the one whom introduced me to linux actually..hee said RTFM Read the F-ing manual in other words, you guys are better then a manual, thanks to anyone who trys to help swiftly or at all.

---

### Post by XxsydenxX on 2009-04-25
-bump- i am bumping this simply because it is important that i get networking up before i leave his house. Please...ill pay you a dollar >__>;

---

### Post by inobe on 2009-04-25
besides what your buddy told you have you tried the basics.


what exactly is it not doing and what is listed in connection information, also tell me what device is in the list when you right click the network icon and hit edit connections.

---

### Post by XxsydenxX on 2009-04-25
Gentlemen...everything you need to know?


stanford-desktop          
    description: Computer
    product: BrkdlPE-ICH4
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=4262FCA1-7DC9-11D7-B486-00E01884FCE4
  *-core
       description: Motherboard
       product: D845PESV
       vendor: Intel Corporation
       physical id: 0
       version: AAA97671-107
       serial: AZSV31901739
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: SV84510A.86A.0013.P08.0303171920 (03/17/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: J2E1
          size: 2400MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 38
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: J6G1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: J6G2
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon RV100 QY [Radeon 7000/VE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list
                configuration: latency=32 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
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
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
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
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
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
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: ES2838/2839 SuperLink Modem
                vendor: ESS Technology
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 82
                serial: 00:07:e9:77:77:23
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
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
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: WDC WD800JB-00ET
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 77.0
                serial: WD-WMAHL1532442
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=36f136f0
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a7a40d52-010e-4f05-aed4-5edd526c4e94
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-04-25 18:06:01 filesystem=ext3 modified=2009-04-25 14:28:36 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-04-25 14:17:34 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2933MiB
                   capacity: 2933MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2933MiB
                      capabilities: nofs
           *-cdrom:0
                description: SCSI CD-ROM
                product: CD-ROM SC-152A
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CA05
                capabilities: removable audio
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:83:1d:0b:3c:f3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
stanford@stanford-desktop:~$

---

### Post by inobe on 2009-04-26
open terminal and do

```
ethtool -i eth0
```

for example' i get this

```
desktop:~$ ethtool -i eth0
driver: r8169
version: 2.3LK-NAPI
firmware-version: 
bus-info: 0000:03:00.0

```

i then took the driver info and did

```
desktop:~$ dmesg |grep r8169
```

then my results are

```
desktop:~$ dmesg |grep r8169
[    6.522426] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.522451] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.522481] r8169 0000:03:00.0: setting latency timer to 64
[    6.522656] r8169 0000:03:00.0: irq 2299 for MSI/MSI-X
[    6.525153] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.525170] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.525196] r8169 0000:04:00.0: setting latency timer to 64
[    6.525339] r8169 0000:04:00.0: irq 2298 for MSI/MSI-X
[   23.788190] r8169: eth1: link up
[   23.788199] r8169: eth1: link up
[   23.789450] r8169: eth0: link down
```


do the first command to get the driver info, then do **dmesg |grep** and add the driver to the end, post back with that information.


-------------------------------------------------------------------------------------------------------------

edit: please include```
lshw -C network
```

---

### Post by XxsydenxX on 2009-04-26
stanford@stanford-desktop:~$ sudo ethtool -i eth0
[sudo] password for stanford: 
driver: e100
version: 3.5.23-k6-NAPI
firmware-version: N/A
bus-info: 0000:02:08.0
stanford@stanford-desktop:~$ dmesg |grep e100
[    1.325170] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    2.924908] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    2.924913] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.924977] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.947513] e100 0000:02:08.0: PME# disabled
[    2.985687] e100: eth0: e100_probe: addr 0xff9ff000, irq 20, MAC addr 00:07:e9:77:77:23
[   21.900131] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
stanford@stanford-desktop:~$

Edit: Im sorry but i have to unhook his mac and connect all the wires to his pc to turn on that comp and use it...each time you ask for something i have to do exactly that...so i simply missed your edited request.

---

### Post by inobe on 2009-04-26
not a problem, take your time.

we will try to troubleshoot this, so far the device seems to get disabled, i don't know why yet.

don't forget dmesg |grep

---

### Post by XxsydenxX on 2009-04-26
> **inobe said:**
> not a problem, take your time.

we will try to troubleshoot this, so far the device seems to get disabled, i don't know why yet.

don't forget dmesg |grep

"stanford@stanford-desktop:~$ dmesg |grep e100
[ 1.325170] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[ 2.924908] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[ 2.924913] e100: Copyright(c) 1999-2006 Intel Corporation
[ 2.924977] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 2.947513] e100 0000:02:08.0: PME# disabled
[ 2.985687] e100: eth0: e100_probe: addr 0xff9ff000, irq 20, MAC addr 00:07:e9:77:77:23
[ 21.900131] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex"


I do believe i didnt...uhm, is there a resolution for this disabled device shat, or am i up shats creek without a paddle for now?

---

### Post by inobe on 2009-04-26
i don't think your up the river yet.

give me the info to these last commands, they will be the last encase your getting tired.

```
ifconfig eth0
```


and


```
lshw -C network
```

then i will spend a few hours researching, if i find out anything i will certainly reply about it.

---

### Post by XxsydenxX on 2009-04-26
> **inobe said:**
> i don't think your up the river yet.

give me the info to these last commands, they will be the last encase your getting tired.

```
ifconfig eth0
```


and


```
lshw -C network
```

then i will spend a few hours researching, if i find out anything i will certainly reply about it.


Ok thank you but i have to give you them tommorow, if you find a resolution or even if you dont reply here, if this happens i will happily upgrade 7.10 to 8.04 and use the 7.10 kernel in 8.04

---

### Post by inobe on 2009-04-26
i am seriously thinking of having you place the pci ethernet card in another slot "this is a pci card" correct ?


if my assumptions are correct it sounds like an IRQ conflict !

that explains why it's disabling.

in fact' i have seen this before.

---

### Post by inobe on 2009-04-26
> **XxsydenxX said:**
> Ok thank you but i have to give you them tommorow, if you find a resolution or even if you dont reply here, if this happens i will happily upgrade 7.10 to 8.04 and use the 7.10 kernel in 8.04

missed this post, so your gonna take off on me' it was getting good !



j/k

cya tomorrow :)

---

### Post by XxsydenxX on 2009-04-26
ok the slot isnt malfunctioning, it works under ubuntu 7.10 windows..hackintosh ETC. So one can only assume that its a kernel issue seeing as though networking worked in previous versions of ubuntu up until 8.04.

---

### Post by XxsydenxX on 2009-04-26
Sorry for the double post, however for anyone whome wants to help and the kind person who was helping me, here is what i was specifically asked for in said post.

stanford@stanford-desktop:~$ sudo ifconfig eth0
[sudo] password for stanford: 
eth0      Link encap:Ethernet  HWaddr 00:07:e9:77:77:23  
          inet6 addr: fe80::207:e9ff:fe77:7723/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:376818 (376.8 KB)  TX bytes:2178 (2.1 KB)




stanford@stanford-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 82
       serial: 00:07:e9:77:77:23
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:45:cf:9a:37:56
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
stanford@stanford-desktop:~$

---

### Post by inobe on 2009-04-26
restart the machine with cable unplugged and try lshw -C network.


you don't need to give me the output, just see if it disables.

---

