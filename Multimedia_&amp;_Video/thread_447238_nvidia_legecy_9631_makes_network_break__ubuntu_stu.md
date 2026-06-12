---
title: "nvidia legecy 9631 makes network break  ubuntu studio"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by lunaparadox on 2007-05-17
so I've been fighting with this for a week and can't figure out whats up. I install the drivers through the restricted driver app. after reboot everything looks great nvidia splash xserver works yay oh no the network card stops being able to get connection to dhcp no internet. uninstall drivers and revert back to nv driver and everything works. Any ideas.
the nvidia card is a mx 400 and the network card is an realtek RTL-8139/8139C/8139C+ on motherboard
running lshw in my debian install gives me this
debian
    description: Desktop Computer
    product: DA193A-ABA 754N
    vendor: HP Pavilion 06
    version: 06e1201RE101XENO3
    serial: xxxxxxxxxxx
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=E02517B3-9363-D711-A12F-D172A8C58EC7
  *-core
       description: Motherboard
       product: MS-6577
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 020
       slot: PRIMARY IDE
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.25 (09/23/2003)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.53GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: Socket 478
          size: 2533MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 8KB
             capacity: 20KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: d8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d8000000-dbffffff
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: b2
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: iomemory:dc000000-dcffffff iomemory:d0000000-d7ffffff irq:10
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d800-d81f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-rt8 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d000-d01f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-rt8 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d400-d41f irq:3
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-rt8 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:e0000000-e00003ff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-rt8 ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: a
                bus info: pci@02:0a.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
                resources: ioport:c000-c01f irq:5
           *-input
                description: Input device controller
                product: SB Audigy Game Port
                vendor: Creative Labs
                physical id: a.1
                bus info: pci@02:0a.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: ioport:c400-c407
           *-firewire:0
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: a.2
                bus info: pci@02:0a.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: iomemory:df005000-df0057ff iomemory:df000000-df003fff irq:11
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: c
                bus info: pci@02:0c.0
                logical name: eth2
                version: 10
                serial: 00:10:dc:ed:19:8b
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.2 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: ioport:c800-c8ff iomemory:df004000-df0040ff irq:11
           *-firewire:1
                description: FireWire (IEEE 1394)
                product: uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
                vendor: NEC Corporation
                physical id: d
                bus info: pci@02:0d.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=44 mingnt=20
                resources: iomemory:df006000-df006fff irq:11
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
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
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:f000-f00f iomemory:50100000-501003ff irq:3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: SAMSUNG SV0813H
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: RJ100-09
                   serial: 0596J1FW308676
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 45GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux swap / Solaris partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 996MB
                      capabilities: primary nofs
                 *-volume:2
                      description: Linux filesystem partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 28GB
                      capabilities: primary
              *-disk:1
                   description: ATA Disk
                   product: Maxtor 6Y080P0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: YAR41VW0
                   serial: Y30GQHWE
                   size: 76GB
                   capacity: 76GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 46GB
                      capabilities: primary
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.1,2
                      logical name: /dev/hdb2
                      capacity: 29GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: Hewlett-Packard DVD Writer 300
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.25
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-serial
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: ioport:500-51f irq:11
  *-network:0 DISABLED
       description: IEEE1394 interface
       physical id: 1
       logical name: eth0
       serial: 00:02:3c:00:21:02
       capabilities: ieee1394 physical
       configuration: broadcast=yes driver=eth1394 multicast=yes
  *-network:1 DISABLED
       description: IEEE1394 interface
       physical id: 2
       logical name: eth1
       serial: 00:00:00:00:00:22
       capabilities: ieee1394 physical
       configuration: broadcast=yes driver=eth1394 multicast=yes
any help would be most appreciated. :(

---

### Post by lunaparadox on 2007-05-18
so no one else has had this problem? I tried the envy program which hosed the x server so reinstalled with same issue.

---

### Post by jondecker76 on 2007-05-18
do you have the low-latency restricted modules installed?

---

### Post by lunaparadox on 2007-05-19
I've got the ristricted modules but can't seem to find the low-latency restricted modules in synaptic. how would I find them?

---

### Post by lunaparadox on 2007-05-19
ok I found them and yes they are installed.

---

### Post by lunaparadox on 2007-05-19
ok I am now running the nvidia driver and network is working. yay
I reconfigured the network card for static ip and got it to connect to local network but still no internet. I switched it back to DHCP and it connected no problem kinda weird but now works. thanks for the help. and hope this will work if anyone else has similar problems.

---

