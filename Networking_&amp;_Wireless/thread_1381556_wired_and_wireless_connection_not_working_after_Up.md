---
title: "wired and wireless connection not working after Update"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by cjt66 on 2010-01-14
Hi All, I have a laptop Acer aspire 5100. I installed Ubuntu a while ago and it was working well. Last week I updated it using Update manager and ever since I haven't been able to connect either wireless or wired connection.

I get this:```

carlos@carlos-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:b6:93:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


--------------------------------------------------------------------------------------
carlos@carlos-laptop:~$ sudo lshw
[sudo] password for carlos: 
carlos-laptop             
    description: Notebook
    product: Aspire 5100
    vendor: Acer
    version: V3.10A
    serial: LXAX90C0237050CC211601
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=62353330-3766-6164-3761-0016D4B69373
  *-core
       description: Motherboard
       product: Navarro
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAX90C0237050CC211601
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V3.10A (10/15/2007)
          size: 109KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-52
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          slot: Socket M2/S1G1
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             physical id: 0
             slot: S1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 Synchronous
             physical id: 1
             slot: S2
             size: 512MiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.8.2
          size: 1600MHz
          capacity: 1600MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:9000(size=4096) memory:b0100000-b01fffff ioport:c0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS482 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:c0000000-cfffffff(prefetchable) ioport:9000(size=256) memory:b0100000-b010ffff memory:b0120000-b013ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
        *-pci:2
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom emulated
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:8440(size=8) ioport:8434(size=4) ioport:8438(size=8) ioport:8430(size=4) ioport:8400(size=16) memory:b0004000-b00041ff memory:4a000000-4a07ffff(prefetchable)
           *-disk
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SBDO
                serial: SB2D04E4GWMP4E
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e1062481
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 31cb35c8-caa4-4c66-97f4-36b42ac61004
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-15 13:18:17 filesystem=ext4 lastmountpoint=/&#65533;d}r&#65533;N&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]&#65533;&#65533;iW&#65533;&#65533;M&#65533;&#65533;M&#65533;N&#65533;&#65533;0^&#65533;&#65533;&#65533;]&#65533;&#65533;&#65533;Y&#65533;&#65533;N&#65533;&#65533;&#65533;%&#65533; modified=2010-01-15 13:24:53 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-01-15 13:35:55 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 9538MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:b0005000-b0005fff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:b0006000-b0006fff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:b0007000-b0007fff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 83
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16) memory:4a080000-4a0803ff
        *-ide:1
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:b0000000-b0003fff
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:a000(size=4096) memory:44000000-49ffffff memory:40000000-43ffffff(prefetchable)
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 10
                serial: 00:16:d4:b6:93:73
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:21 ioport:a000(size=256) memory:48011000-480110ff
           *-network:1 UNCLAIMED
                description: Ethernet controller
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:06:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=168 maxlatency=20 mingnt=10
                resources: memory:48000000-4800ffff
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:20 memory:48010000-48010fff ioport:a400(size=256) ioport:a800(size=256) memory:40000000-43ffffff(prefetchable) memory:44000000-47ffffff
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
                resources: memory:48011300-4801137f
           *-generic
                description: Unclassified device
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=64 mingnt=32
                resources: irq:23 memory:48011100-480111ff
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
                resources: memory:48011380-480113ff
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=64 mingnt=32
                resources: irq:23 memory:48011200-480112ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-battery
       description: Lithium Ion Battery
       product: PANASONIC
       vendor: PANASONIC
       physical id: 1
       slot: 1st Battery
       capacity: 3900mWh
       configuration: voltage=14.8V
```

The wireless card seems to have disappeared.
I have tried many solved posts but no success since most of them require internet connection for updates or downloads.

I reinstalled Ubuntu and the problem persists.

would appreciate any help

thanks in advance

---

### Post by quixote on 2010-01-16
I'm afraid I don't have anything useful to suggest, but I noticed this sounds a bit like the problem in this other forum post, "[Internet Problems]("http://ubuntuforums.org/showthread.php?t=1379268")".  That also concerns an Acer, but a different model.  Hmmm.

---

### Post by willowave on 2010-02-01
> **kanna84 said:**
> Just contact your service provides, They will Surelly help you to solve your problom. And after that you can check out the speed test here [http://www.ip-details.com/internet-speed-test/](http://www.ip-details.com/internet-speed-test/)
 This has nothing to do with their service provider. Thats obvious by doing a search. 
This a problem with the kernel itself. A problem with Linux. I've reinstalled several times because my installastion was new and I didn't want to go thru having to compile stuff. I'm on my 5th install. Sometimes my eth0 is there, sometimes its not. Mostly wireless has not worked in the last 3 days ever. It's just not there. 
If you look over the forums you'll see many people with the same problem.

---

