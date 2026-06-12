---
title: "Can this hardware be a backend?"
date: 2012-03-04
forum: Mythbuntu
---

### Post by sami8519 on 2012-03-04
Hello guys,

I have a very old pc lying around in the house and I wonder if it is possible to make a mythtv backend out of it. I have installed debian squeeze headless server on it last night and the command "ishw" reports the hardware being:
```
root@debian:~# lshw
debian                    
    description: Desktop Computer
    product: PVCLE266
    vendor: KOBIAN
    version: 3.0A
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: PVCLE266
       vendor: KOBIAN
       physical id: 0
       version: 3.0A
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: Version 07.00T (04/02/01)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: VIA Samuel 2
          vendor: CentaurHauls
          physical id: 4
          bus info: cpu@0
          version: C3
          slot: Socket-1
          size: 800MHz
          capacity: 3GHz
          width: 32 bits
          clock: 3331MHz
          capabilities: fpu fpu_exception wp de tsc msr cx8 mtrr pge mmx 3dnow
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 64KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 470MiB
     *-pci
          description: Host bridge
          product: VT8623 [Apollo CLE266]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e0000000-e3ffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8633 [Apollo Pro266 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:dde00000-dfefffff memory:d5d00000-ddcfffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: VT8623 [Apollo CLE266] integrated CastleRock graphics
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:d8000000-dbffffff(prefetchable) memory:de000000-deffffff memory:dfef0000-dfefffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:11 ioport:e400(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:5 ioport:e800(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:5 ioport:ec00(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:10 memory:dfffff00-dfffffff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD300AB-00BV
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 21.0
                serial: WD-WMA7H1418608
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003ca26
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: ea0150e8-d9e0-44cd-a152-1ee9e810669d
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2012-03-04 06:51:19 filesystem=ext3 modified=2012-03-04 07:10:04 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2012-03-04 09:40:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 918MiB
                   capacity: 918MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 918MiB
                      capabilities: nofs
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:5 ioport:e000(size=256)
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:11:5b:26:3e:62
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.99 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:11 ioport:dc00(size=256) memory:dffffe00-dffffeff
root@debian:~# 

```Regards,
Sami

---

### Post by newlinux on 2012-03-05
I think it could be to me, but you wouldn't want to do too much commercial skip processing or transcoding with it. What do you want this backend to do?

---

### Post by sami8519 on 2012-03-05
> **newlinux said:**
> I think it could be to me, but you wouldn't want to do too much commercial skip processing or transcoding with it. What do you want this backend to do?

Thanks for your reply. I just want it to be a backend for a laptop using xbmc as a fronted for just watching live tv, as my tuner is PCI and therefore can not be run directly on the laptop. Do you think VDR would be lighter on this machine?


Regards,
Sami

---

### Post by newlinux on 2012-03-05
what kind of signal will you be tuning (analog or digital)? What kind of tuner card will be using?

---

### Post by sami8519 on 2012-03-05
> **newlinux said:**
> what kind of signal will you be tuning (analog or digital)? What kind of tuner card will be using?

Sorry for not providing all relevant info. I am receiving only digital satellite channels and i am going to use a hauppauge wintv-nova s2 pci tvtuner. Thank you.

Regards,
Sami

---

### Post by newlinux on 2012-03-06
Digital signals take very little CPU to record because you are just capturing the signal into a file. A mythbackend for that will be fine. I've never used VDR so I can't compare. If all you care about using a backend to capture recordings you might be able to do something simpler than mythtv.

---

### Post by sami8519 on 2012-03-06
> **newlinux said:**
> Digital signals take very little CPU to record because you are just capturing the signal into a file. A mythbackend for that will be fine. I've never used VDR so I can't compare. If all you care about using a backend to capture recordings you might be able to do something simpler than mythtv.

That was my thought. The reason I was inclined more toward mythtv is its subtitle support as vdr still novice in that area. I will give both of them a try. Thanks a lot for your valuable input.

Best Regards,
Sami

---

