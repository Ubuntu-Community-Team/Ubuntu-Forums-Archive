---
title: "Audio frustrations - need CLI set up help"
date: 2012-05-19
forum: Multimedia Software
---

### Post by MakOwner on 2012-05-19
I have posted several queries on here and yet to get any constructive responses, so I'm hoping to pose the question in a more concise manner.
I know this is possible to do, but I don't seem to be able to find any information on how to do it.

I want to configure a headless server to record audio from the mic jack on a sound card.

I did this with a 10.04 LTS and a Dell PE350 and an Ensoniq PCI sound card.  Plugged in the card, did a fresh install from the 10.04 LTS mini CD using basic server and openssh install selections, did an apt get install alsa after the first boot, and arecord records anything plugged into the mic/line in jack.  It's using mic input as altering the volume on the external input source affects the recorded sound.

I need to replace that server - I have a Dell PE850 with 1 GB of memory. 
I'd like to reproduce the previous configuration with this new hardware and the 12.04 LTS mini CD.  One of the major differences between the old and new hardware is that this server has only PCIe and PCIX I/O slots.


I tried adding what is reported to be a well supported ASUS PCIe Sound card and I get nothing. Alsamixer controls do nothing.

I bought a generic USB sound device that advertises itself as fully USB compliant and not requiring any drivers.  My googling turned up indications that this was the best approach for USB audio.

I still get nothing with arecord.

Everything I turn up with google on troubleshooting sound problems points you to GUI tools for adjusting ..things.  
I really don't want or need a full desktop installation just to get audio recording working and I find it extremely hard to believe that there isn't a way to do this.  

Someone _please_ point me at the obvious stuff I'm missing somewhere.

---

### Post by gordintoronto on 2012-05-19
I couldn't figure out what you were trying to say here: "did an apt get install alsa after the first boot, and arecord records anything plugged into the mic/line in jack. It's using mic input as altering the volume on the external input source affects the recorded sound."

If you run: sudo lshw
does the sound card show up? What sound card, by the way? What USB sound card?

In my experience, when sound is not recorded, it is because the mic is muted, with about 90% reliability. It's really easy to figure out using GUI tools. I also use Audacity for recording....

---

### Post by MakOwner on 2012-05-19
> **gordintoronto said:**
> I couldn't figure out what you were trying to say here: "did an apt get install alsa after the first boot, and arecord records anything plugged into the mic/line in jack. It's using mic input as altering the volume on the external input source affects the recorded sound."

If you run: sudo lshw
does the sound card show up? What sound card, by the way? What USB sound card?

In my experience, when sound is not recorded, it is because the mic is muted, with about 90% reliability. It's really easy to figure out using GUI tools. I also use Audacity for recording....

I meant that very basic steps got this working after the initial installation.

This device is a (very) generic USB device.   

The device shows up on the USB ports, this is lsusb with extraneous stuff removed.

```

$ lsusb
Bus 003 Device 002: ID 1130:f211 Tenx Technology, Inc. TP6911 Audio Headset


```

I'm not as familiar with the output of lshw - not sure what to cut out.

```

    description: Rack Mount Chassis
    product: PowerEdge 850
    vendor: Winbond Electronics
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=rackmount 
  *-core
       description: Motherboard
       product: 0Y8628
       vendor: Winbond Electronics
       physical id: 0
       version: A02
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A04
          date: 08/22/2006
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot socketedrom edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: Intel(R) Pentium(R) 4 CPU 3.00GHz
          slot: PROC
          size: 3GHz
          capacity: 3800MHz
          width: 64 bits
          clock: 800MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl est cid cx16 xtpr
          configuration: cores=1 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 9HTF3272AY-53EB3
             vendor: Micron Technology
             physical id: 0
             slot: DIMM1_A
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 9HTF3272AY-53EB3
             vendor: Micron Technology
             physical id: 1
             slot: DIMM1_B
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: HYMP564U72BP8-C4
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             slot: DIMM2_A
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: HYMP564U72BP8-C4
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 3
             slot: DIMM2_B
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: E7230/3000/3010 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=i3000_edac
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: E7230/3000/3010 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:72
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:73 memory:fea00000-feafffff
           *-pci
                description: PCI bridge
                product: 6702PXH PCI Express-to-PCI Bridge A
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 09
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress msi pm pcix normal_decode bus_master cap_list
        *-pci:2
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:74 ioport:e000(size=4096) memory:fe800000-fe9fffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 11
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5721-v3.47a, ASFIPMI v6.10 ip= latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:16 memory:fe8f0000-fe8fffff
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:75 ioport:d000(size=4096) memory:fe600000-fe7fffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 11
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5721-v3.47a, ASFIPMI v6.10 ip= latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:17 memory:fe6f0000-fe6fffff
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:bce0(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:bcc0(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:bca0(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:feb00400-feb007ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:fe400000-fe5fffff ioport:fd000000(size=16777216)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Z7/Z9 (XG20 core)
                vendor: XGI Technology Inc. (eXtreme Graphics Innovation)
                physical id: 5
                bus info: pci@0000:06:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller vga_palette cap_list
                configuration: latency=0
                resources: memory:fd000000-fdffffff memory:fe4c0000-fe4fffff ioport:cc80(size=128)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
           *-cdrom
                description: SCSI CD-ROM
                product: CD-ROM CD-224E-N
                vendor: TEAC
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/sr0
                version: 3.AB
                capabilities: removable audio
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:bc98(size=8) ioport:bc90(size=4) ioport:bc80(size=8) ioport:bc78(size=4) ioport:bc60(size=16) memory:feb00000-feb003ff
           *-disk:0
                description: ATA Disk
                product: ST3500320AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: SD15
                size: 465GiB (500GB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=f5a6f78e-31e8-43ac-8199-953e19bdeed4
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   size: 953MiB
                   capacity: 953MiB
                   capabilities: boot fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   size: 8678MiB
                   capacity: 8678MiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-05-19 20:40:33 filesystem=ext4 lastmountpoint=/ modified=2012-05-19 21:27:28 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-05-19 21:28:21 state=mounted
              *-volume:2
                   description: Linux RAID partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 456GiB
                   capabilities: multi
           *-disk:1
                description: ATA Disk
                product: ST3500320AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: SD15
                size: 465GiB (500GB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=1d816837-f811-497d-9203-059fd6018987
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1
                   size: 953MiB
                   capacity: 953MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   logical name: /usr
                   version: 1.0
                   size: 8678MiB
                   capacity: 8678MiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-05-19 20:40:35 filesystem=ext4 lastmountpoint=/target/usr modified=2012-05-19 21:28:22 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered mounted=2012-05-19 21:28:22 state=mounted
              *-volume:2
                   description: Linux RAID partition
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sdb3
                   capacity: 456GiB
                   capabilities: multi
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:8c0(size=32)

```

---

