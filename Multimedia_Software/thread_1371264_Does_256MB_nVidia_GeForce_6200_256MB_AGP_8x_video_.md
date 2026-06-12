---
title: "Does 256MB nVidia GeForce 6200 256MB AGP 8x video card work on Ubuntu 9.10?"
date: 2010-01-03
forum: Multimedia Software
---

### Post by resander on 2010-01-03
I have just bought a second hand computer pre-installed with Windows 7 and Ubuntu 9.10 with 2GB ram and a 3.0GHz Pentium 4 cpu. It is for our children who just discovered the current video card (or is it built-in on motherboard?) does not support DirectX 9, so they cannot play games. Otherwise the PC works well for Windows and Ubuntu. The computer is a little bit of age and does not support PCI-Express, so I was told to look for an AGP 8x interface. 

I found 256MB nVidia GeForce 6200 AGP 8x video card on eBay.co.uk (£34 GBP).

Is this compatible with Ubuntu 9.10 (or earlier Ubuntus like 8.10 etc)?
If so, will it run out of the box, or do I need to find (where?) drivers for it?

If not compatible can you recommend a card that is. Not too expensive of course since our children are stepping up from 'no games' to some games.

I know it is off-topic, but does anyone know if this card works on Windows 7? It has to be of course.

Don't know if this is useful, but here are the PC hardware details:
```

pc2@pc2-desktop:~$ sudo lshw
[sudo] password for pc2:
pc2-desktop               
    description: Desktop Computer
    product: P4M90-M4
    vendor: BIOSTAR Group
    version: Ver:1.0
    serial: OEM
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00000000-0000-0000-3412-000078563412
  *-core
       description: Motherboard
       product: P4M90-M4
       vendor: BIOSTAR Group
       physical id: 0
       version: Ver:1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (12/21/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 4GHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2
             physical id: 0
             slot: A0
             size: 2GiB
        *-bank:1
             description: DIMM DDR2 [empty]
             physical id: 1
             slot: A1
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:f8000000-f9ffffff(prefetchable)
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: ioport:c000(size=4096) memory:fb000000-fcffffff memory:f4000000-f7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:f4000000-f7ffffff(prefetchable) memory:fb000000-fbffffff memory:fc000000-fc00ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:b000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:31 ioport:a000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:fc00(size=8) ioport:f800(size=4) ioport:f400(size=8) ioport:f000(size=4) ioport:ec00(size=16) ioport:e800(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             logical name: scsi1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e400(size=16)
           *-disk
                description: ATA Disk
                product: ST3120022A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.54
                serial: 5LJ057EX
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=84e23780
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 2c1a-b801
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-12-07 01:46:31 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: f443cf6e-0b0b-6b4a-84ec-89ce64e98abf
                   size: 56GiB
                   capacity: 56GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-12-07 01:47:35 filesystem=ntfs state=clean
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: a338263d-1bef-4b50-b411-22b605a869e8
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-12-06 18:31:19 filesystem=ext3 modified=2009-12-06 18:47:55 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2010-01-02 16:18:13 state=mounted
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SM-348B
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: T500
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:e000(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:dc00(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:d400(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:fdfff000-fdfff0ff
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:e0:4d:7f:4b:49
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.6 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:23 ioport:d000(size=256) memory:fdffe000-fdffe0ff
        *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323
                vendor: Agere Systems
                physical id: 3
                bus info: pci@0000:04:03.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12
                resources: irq:16 memory:fdaff000-fdafffff
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:dfffc000-dfffffff
pc2@pc2-desktop:~$ ^C
```

---

### Post by cascade9 on 2010-01-03
Yes, that card will run on linux and windows 7 (but areoglass under windows 7 might be a bit 'meh', a newer card might be a better idea). Should work with ubuntu 8.04 and later (and quite possibly earlier versions, not that they are a good idea these days)

You can get the drivers from-

System -> Administration -> Hardware Drivers

Or from nVidias site- 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Its easier to let ubuntu deal with the nVidia drivers rather than doing it manually with the drivers you get from nvidia. 

BTW- it would be a good idea to check your computer (or just post the specifications here) to make sure it has a AGP slot. If it doesnt, you will have to get a PCI version

---

### Post by ibuclaw on 2010-01-03
As far as I can tell, it is indeed an AGP slot.

```

*-firmware
    description: BIOS
    vendor: Phoenix Technologies, LTD
    physical id: 0
    version: 6.00 PG (12/21/2007)
    size: 128KiB
    capacity: 448KiB
    capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb [COLOR="Blue"]**agp**[/COLOR] ls120boot zipboot biosbootspecification

```
As per above the Motherboard support AGP.

```

*-pci:0
    description: Host bridge
    product: CN896/VN896/P4M900 Host Bridge
    vendor: VIA Technologies, Inc.
    physical id: 100
    bus info: pci@0000:00:00.0
    version: 00
    width: 32 bits
    clock: 33MHz
    configuration: driver=[COLOR="Blue"]**agpgart-via**[/COLOR] latency=8
    resources: irq:0 memory:f8000000-f9ffffff(prefetchable)
  *-display UNCLAIMED
        description: VGA compatible controller
        product: CN896/VN896/P4M900 [Chrome 9 HC]
        vendor: VIA Technologies, Inc.
        physical id: 0
        bus info: pci@0000:01:00.0
        version: 01
        width: 32 bits
        clock: 66MHz
        capabilities: pm [COLOR="Blue"]**agp agp-3.0**[/COLOR] bus_master cap_list
        configuration: latency=32 mingnt=2
        resources: memory:f4000000-f7ffffff(prefetchable) memory:fb000000-fbffffff memory:fc000000-fc00ffff(prefetchable)

```
And as per above, the PCI:0 Host bridge on the motherboard is being controlled by the agpgart driver.
As per wikipedia:
> 
AGPgart is a kernel module for Linux, FreeBSD and Solaris that supports the extra data transfer features of Accelerated Graphics Port (AGP) video cards via the Graphics Address Remapping Table (GART).

The AGPgart driver module uses system memory to enhance the display of graphics &#8212; a useful feature for memoryless graphics devices such as Intel integrated graphics and AGP graphics, which need to use system memory as video buffers.

And attached to this is an unclaimed Display Controller that has AGP 3.0 specification capabilities.
(Basically, any AGP 8x or earlier card can go in there).

Hope this has been useful.

Regards
Iain

---

### Post by cascade9 on 2010-01-03
Nice logic tinivole, but no cigarillo.

"capabilities: agp etc etc"  

"-pci:0
snip!
configuration: driver=agpgart-intel module=intel_agp"

That pops up with my junker p-3 866/intel 810 chipset board. That is totally lacking in a AGP slot (IIRC, there was no 810 chipset that actually had an AGP slot). 

Just because AGP appears in a list of hardware does not mean there is an AGP slot. Even for things that _should_ have an AGP slot, that doesn't mean its soldered in....

BTW, felt like poking around, and checked the P4M90-M4 specifications. It doesnt appear on the official biostar website (which makes me think that its actually not commercially sold to end users, its just something they make/made for a 3rd party). There is a "P4M900-M4", and that one doesnt have an AGP, but it does have PCI-E slots- 

[http://www.biostar-usa.com/app/en-us/mb/content.php?S_ID=283](http://www.biostar-usa.com/app/en-us/mb/content.php?S_ID=283)

That is probably not exactly what the P4M90-M$ is, but (hopefully) its prettty close. The PCI-E slot would explain this-

"capabilities: pci pciexpress pm msi ht bus_master cap_list" 

Its there for PCI:1 and PCI:2 

I would guess that the OPs board has 2x PCI-E slots, maybe a PCI slot or two, and no AGP. The only way to know for sure it to pull the side off the computer.

---

### Post by resander on 2010-01-03
Many thanks for confirming the card will/may work on Ubuntu and Windows 7. Will order this card from ebay when I know the PC has an AGP slot/connector. Identifying marks? How do I tell it from a PCI-Express slot? 

No problem if it has a PCI-Express slot and no AGP slot, I will just go to ebay again and try to find another card.  

I have never installed a graphics card before (100% ignorant). Ebay says the retail box contains the card and an install CD. For Windows my guess would be to power off and plug the card into a slot where it would fit, then power back on and request boot from the CD via bios. The software on the CD would then do/control the card installation and next normal boot would use the card. Is this so? When installing for Ubuntu the card would be already in its slot. How do I continue then?

Also, if there are several slots free in the PC how do I decide which to choose? Does it matter?

---

### Post by cascade9 on 2010-01-03
Easiest to just link you to a pic- 

[IMG]http://images.anandtech.com/reviews/motherboards/asrock/939dual/slots.jpg[/IMG]

Original article here- 
[http://www.anandtech.com/printarticle.aspx?i=2524](http://www.anandtech.com/printarticle.aspx?i=2524)

In order, from left to right- 

3 white slots- PCI. 
Brown slot (partially covered with pink sticker)- AGP 
Small white slot- PCI-E x1
Long white slot- PCI-E x16
Yellow slot- non-standard, its a unique feature of that motherboard. 

PCI slots are the most common. AGP is set 'further back' from the motherboard edge. PCI-E x1 is tiny, and 'thinner' than a PCI slot. PCI-E x16 is longer than PCI or AGP, and thin like the smaller PCI-E x1 slot.

BTW, colours mean nothing. You can get PCI, AGP and PCI-E slots in whatever colour the manufacturer wants. 

Installing- yes, power off(make sure you disconnect the power lead, if you don't there is still power going through the motherboard..you don't want that). Take the side off, shove the card in, screw it down, put the case back on, reconnect the power cord, boot it. 

You dont need to boot from BIOS. That wont work. With windows, you just start windows up, then install the drivers that are on the CD. From experience, I'd just go to nVidias site and get the newer drivers from there....the drivers on the CDs tend to be outdated, at best. 

With ubuntu, instead of installing the drivers on the CD, you just go 

System -> Administration -> Hardware Drivers

BTW- the only reason why that card might have trouble with win7 is that the 6200 is a very early card to support DX9 (minimum for windows 7). A newer PCI or PCI-E card would have less troubles. It would alos be faster as well. Look for an 8400GS, it should be in a similar price range to the much older 6200.

---

### Post by matt06 on 2010-01-03
> **cascade9 said:**
> BTW, felt like poking around, and checked the P4M90-M4 specifications. It doesnt appear on the official biostar website (which makes me think that its actually not commercially sold to end users, its just something they make/made for a 3rd party). There is a "P4M900-M4", and that one doesnt have an AGP, but it does have PCI-E slots- 

[http://www.biostar-usa.com/app/en-us/mb/content.php?S_ID=283](http://www.biostar-usa.com/app/en-us/mb/content.php?S_ID=283)

That is probably not exactly what the P4M90-M$ is, but (hopefully) its prettty close.

I believe cascade9 is correct.  I have a P4M900-M4 and it reports as P4M90-M4 for motherboard using 'sudo lswh', but later also reports CN896/VN896/P4M900 Host Bridge.  The picture of the board in the link is accurate, but mine has bright orange DDR2, PCI-E x1, and PCI-E x16 slots with bright green PCI slots.  I am not sure of the revision.

See:  [http://evertek.com/imageshare/P/300x300/P4M900-M4-unit.jpg](http://evertek.com/imageshare/P/300x300/P4M900-M4-unit.jpg)

resander, does your board look like the one in the link or do you see P4M900-M4 on the screen anywhere before bootup?  Mine is listed as such in both upper-left corner and bios string at the bottom of the screen.  If so, you will have a PCI-E x16 slot, not AGP.

---

### Post by cascade9 on 2010-01-11
Heh, maybe there is a typo in 'lswh'. :)

---

### Post by llawwehttam on 2010-01-11
> **cascade9 said:**
> Yes, that card will run on linux and windows 7 (but areoglass under windows 7 might be a bit 'meh', a newer card might be a better idea). Should work with ubuntu 8.04 and later (and quite possibly earlier versions, not that they are a good idea these days)

You can get the drivers from-

System -> Administration -> Hardware Drivers

Or from nVidias site- 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Its easier to let ubuntu deal with the nVidia drivers rather than doing it manually with the drivers you get from nvidia. 

BTW- it would be a good idea to check your computer (or just post the specifications here) to make sure it has a AGP slot. If it doesnt, you will have to get a PCI version

Personally I always use Nvidia's drivers. The ubuntu provided ones have caused me a lot of trouble with older cards in the past.

---

