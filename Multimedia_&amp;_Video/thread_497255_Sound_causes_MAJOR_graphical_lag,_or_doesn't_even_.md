---
title: "Sound causes MAJOR graphical lag, or doesn't even work."
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by kavon89 on 2007-07-10
Hi, I have intergrated sound and it is the only thing causing problems in Ubuntu 7.04.

The title explains the main problem, I get graphical lag when I have sound enabled. (Bringing me down to 10 fps or less.) Medal of Honor Allied Assault is probably the only game in which I don't get this sound lag. I rely on Teamspeak 2 RC2 to talk to friends, and when that is running I get no sound anywhere, not even from the system. 
[Here is what happens when I try to test the audio with Teamspeak running.]("http://i14.tinypic.com/4q72oeh.png")

Here are my system specs.

```
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=C023C74A-5F1D-D711-A4D5-0011D8250D83
  *-core
       description: Motherboard
       product: K8N4-E Deluxe
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.XX
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS K8N4-E Deluxe ACPI BIOS Revision 1003 (03/03/2005)
          size: 128KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.12.0
          slot: Socket 754
          size: 2475MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 275MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up ts fid vid ttp
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 3e
          slot: System board or motherboard
          size: 640MB
          capacity: 3GB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 128MB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: ioport:e400-e41f ioport:4c00-4c3f ioport:4c40-4c7f irq:255
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:d4004000-d4004fff irq:16
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.20-16-generic ohci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=10 speed=12.0MB/s
           *-usb:0
                description: Mouse
                product: Microsoft Optical Mouse with Tilt Wheel
                vendor: Microsoft
                physical id: 3
                bus info: usb@1:3
                version: 1.20
                capabilities: usb-2.00
                configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
           *-usb:1
                description: Keyboard
                physical id: 4
                bus info: usb@1:4
                version: 1.01
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:d4005000-d40050ff irq:16
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.20-16-generic ehci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=10 speed=480.0MB/s
           *-usb
                description: Mass storage device
                product: U3 Cruzer Micro
                vendor: SanDisk Corporation
                physical id: 2
                bus info: usb@2:2
                logical name: scsi9
                version: 0.10
                serial: 000018742C60F7E8
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=200mA speed=480.0MB/s
              *-disk
                   description: SCSI Disk
                   product: U3 Cruzer Micro
                   vendor: SanDisk
                   physical id: 0.0.0
                   bus info: scsi@9:0.0.0
                   logical name: /dev/sdb
                   version: 3.21
                   size: 979MB
                   capabilities: removable
                   configuration: ansiversion=2
                 *-disc
                      physical id: 0
                      logical name: /dev/sdb
                      size: 979MB
                      capabilities: partitioned partitioned:dos
                    *-volume
                         description: W95 FAT16 (LBA) partition
                         physical id: 1
                         logical name: /dev/sdb1
                         capacity: 979MB
                         capabilities: primary bootable
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
          resources: ioport:dc00-dcff ioport:e000-e0ff iomemory:d4003000-d4003fff irq:17
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3
          resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:f000-f00f
        *-ide
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM DDU1621
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                version: VER S1.6
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                configuration: mode=udma2
              *-disc
                   physical id: 0
                   logical name: /dev/hdc
           *-cdrom:1
                description: IDE CD-ROM
                product: CRD-8483B
                physical id: 1
                bus info: ide@1.1
                logical name: /dev/hdd
                version: 1.05
                serial: 2000/08/28
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                configuration: mode=udma2
              *-disc
                   physical id: 0
                   logical name: /dev/hdd
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@00:07.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:9f0-9f7 ioport:bf0-bf3 ioport:970-977 ioport:b70-b73 ioport:d800-d80f iomemory:d4002000-d4002fff irq:17
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:9e0-9e7 ioport:be0-be3 ioport:960-967 ioport:b60-b63 ioport:c400-c40f iomemory:d4001000-d4001fff irq:18
        *-disk
             description: SCSI Disk
             product: Maxtor 6Y160M0
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: YAR5
             serial: Y46GD15E
             size: 149GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                capacity: 147GB
                capabilities: primary bootable
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 1843MB
                capacity: 1843MB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1843MB
                   capabilities: nofs
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-storage
             description: RAID bus controller
             product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller
             vendor: Silicon Image, Inc.
             physical id: a
             bus info: pci@05:0a.0
             logical name: scsi5
             logical name: scsi6
             logical name: scsi7
             logical name: scsi8
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list scsi-host
             configuration: driver=sata_sil latency=32
             resources: ioport:8000-8007 ioport:8400-8403 ioport:8800-8807 ioport:8c00-8c03 ioport:9000-900f iomemory:d3005000-d30053ff irq:20
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: b
             bus info: pci@05:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
             resources: iomemory:d3004000-d30047ff iomemory:d3000000-d3003fff irq:21
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          logical name: eth0
          version: a2
          serial: 00:13:d4:0b:d2:08
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 duplex=full ip=192.168.1.45 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: iomemory:d4000000-d4000fff ioport:b000-b007 irq:19
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display:0
             description: VGA compatible controller
             product: RV370 5B60 [Radeon X300 (PCIE)]
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@01:00.0
             version: 00
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=fglrx_pci latency=0
             resources: iomemory:c0000000-cfffffff ioport:a000-a0ff iomemory:d1000000-d100ffff irq:22
        *-display:1 UNCLAIMED
             description: Display controller
             product: RV370 [Radeon X300SE]
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@01:00.1
             version: 00
             size: 64KB
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:d1010000-d101ffff
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

```

Any ideas?

---

### Post by kavon89 on 2007-07-10
*bump* :(

---

