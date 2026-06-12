---
title: "[SOLVED] complete noob at audio configuration"
date: 2007-09-20
forum: Multimedia Production
---

### Post by Tyke91 on 2007-09-20
Neither audacity nor recordMyDesktop are recieving any audio output from my computer.

here's what i get from sudo lshw
```
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=normal chassis=mini-tower power-on_password=enabled uuid=44454C4C-3900-104B-8047-B8C04F384331
  *-core
       description: Motherboard
       product: 0WG864
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN4811168K021F.
       slot: SLOT3
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 2.1.2 (12/01/2006)
          size: 64KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Microprocessor
          size: 2133MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MB
             capacity: 2MB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GB
          capacity: 1GB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 64T64000HU3.7A
             vendor: 7F7F7F7F7F510000
             physical id: 0
             serial: 091B8C13
             slot: DIMM_1
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns) [empty]
             vendor: FFFFFFFFFFFFFFFF
             physical id: 1
             serial: FFFFFFFF
             slot: DIMM_3
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 64T64000HU3.7A
             vendor: 7F7F7F7F7F510000
             physical id: 2
             serial: 091B9717
             slot: DIMM_2
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR Synchronous 533 MHz (1.9 ns) [empty]
             vendor: FFFFFFFFFFFFFFFF
             physical id: 3
             serial: FFFFFFFF
             slot: DIMM_4
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 7300 LE
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:dd000000-ddffffff iomemory:c0000000-cfffffff iomemory:de000000-deffffff irq:16
        *-network
             description: Ethernet interface
             product: 82562V 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@00:19.0
             logical name: eth0
             version: 02
             serial: 00:16:76:ae:65:35
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=1.1-2 ip=192.168.0.105 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
             resources: iomemory:dffe0000-dfffffff iomemory:dffdb000-dffdbfff ioport:ecc0-ecdf irq:17
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff20-ff3f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff00-ff1f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: Flash Disk
                   vendor: USB
                   physical id: 1
                   bus info: usb@4:1
                   logical name: scsi4
                   version: 1.10
                   serial: 230760A43FE0F532
                   capabilities: usb-1.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: HardDrive
                      vendor: 64MB
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/sdb
                      version: 1.88
                      size: 62MB
                      capabilities: removable
                      configuration: ansiversion=2
                    *-disc
                         physical id: 0
                         logical name: /dev/sdb
                         size: 62MB
                         capabilities: partitioned partitioned:dos
                       *-volume
                            description: W95 FAT32 partition
                            physical id: 1
                            logical name: /dev/sdb1
                            capacity: 62MB
                            capabilities: primary bootable
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:dffdac00-dffdafff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:dffdc000-dffdffff irq:16
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff80-ff9f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff60-ff7f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff40-ff5f irq:22
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Dell USB Mouse
                   vendor: Dell
                   physical id: 1
                   bus info: usb@7:1
                   version: 29.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=50mA speed=1.5MB/s
              *-usb:1
                   description: Keyboard
                   product: Dell USB Keyboard
                   vendor: Dell
                   physical id: 2
                   bus info: usb@7:2
                   version: 2.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=70mA speed=1.5MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ff980800-ff980bff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant
                physical id: 3
                bus info: pci@03:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: iomemory:dcef0000-dcefffff ioport:dcf8-dcff irq:5
        *-isa
             description: ISA bridge
             product: 82801HH (ICH8DH) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:fe00-fe07 ioport:fe10-fe13 ioport:fe20-fe27 ioport:fe30-fe33 ioport:fec0-fecf ioport:eca0-ecaf irq:20
           *-disk
                description: SCSI Disk
                product: SAMSUNG HD160JJ/
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: ZM10
                serial: S0DFJ1QLC01320
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: FreeBSD partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 30GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 114GB
                   capabilities: primary
              *-volume:2
                   description: Linux swap / Solaris partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 4714MB
                   capabilities: primary nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW TS-H653A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D300
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:dffdab00-dffdabff ioport:ece0-ecff irq:10
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:fe40-fe47 ioport:fe50-fe53 ioport:fe60-fe67 ioport:fe70-fe73 ioport:fed0-fedf ioport:ecb0-ecbf irq:20
mykola@MykolaUbuntu:~$

```how do i fix this? i think it has to do with an unidentified device.

---

### Post by Tyke91 on 2007-09-20
SOLVED: 

you must run your sound files though a mixer. audacity and recordMyDesktop don't have access to your sound card. if you get a program like Gnome Mixer, and make sure that there is nothing muted, you will be able to record every sound from your computer... if you don't want EVERY sound, then playing around with your mixer will yield results.

---

