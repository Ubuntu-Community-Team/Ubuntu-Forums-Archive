---
title: "Unable to make the IP address static"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by japtar10101 on 2009-01-02
I attempted to make my network IP address static by editting */etc/network/interfaces* to below:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.0.121
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

```

Note: the file originally said:
```

auto lo
iface lo inet loopback

```

When I do this, I cannot connect to the internet.  Change the settings back to roaming on NMapplet, and everything returns back to normal.

What may be the cause of this?  Does it have to do with the network service that we have?  Is it a network card issue?  Or is it simply because my computer is old?

Some stats that may (or may not) help:
```

~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801AA AC'97 Modem Controller (rev 02)
01:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
```
~$ sudo lshw
PCI (sysfs)  
omiyat-server             
    description: Desktop Computer
    product: Emachines
    vendor: TriGem Computer, Inc.
    version: 100
    serial: 0000000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=desktop cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: TriGem System Board
       vendor: TriGem Computer, Inc.
       physical id: 0
       version: 000000
       serial: 000000000000000000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: Ver 5.02 (10/17/2001)
          size: 99KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.10
          slot: U1
          size: 900MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 256MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 128MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 128MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 82810 GMCH (Graphics Memory Controller Hub)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82810 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-pci
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: e
                bus info: pci@0000:01:0e.0
                logical name: eth0
                version: 10
                serial: 00:1e:2a:ba:45:f1
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.46 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
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
             product: 82801AA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST320410A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.34
                serial: 5FG0W8BP
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ee08ee08
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 73c14ef3-0a2b-4e39-a44a-b62b24f956bc
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-19 15:58:37 filesystem=ext3 modified=2008-12-28 12:54:49 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-12-28 12:54:49 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: ef11b1f6-9a11-4727-9741-910c15f46482
                   size: 4769MiB
                   capacity: 4769MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-R/RW 48X16
                vendor: ATAPI
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 9.EK
                serial: ATAPI   CD-R/RW 48X16   9.EK
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
        *-usb
             description: USB Controller
             product: 82801AA USB Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801AA AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801AA AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0

```

---

### Post by damis648 on 2009-01-02
What if you make the modification using nm-applet and set it to static there?

---

### Post by gg234 on 2009-01-03
try this [http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

---

### Post by tonytnnt on 2009-01-03
I followed Solution 1 to the letter (and I went back and checked it) but now I have no internet access on that machine at all. Before I could manually enter everything. Now auto eth0 doesn't even show up under ifconfig.:confused:

Suffice to say, installing Wicd is out of the question as well until I regain network connectivity on my Ubuntu box. And since Network Manager is uninstalled, I can't try solution three either.

Ugh, I've been working on this all night, any help would be appreciated. (Btw I'm running Ubuntu with Gnome, however this appears to be the same problem. Or at least gg234's solution was targeted toward my problem.) Can anyone tell me how to at least get Network Manager back up and running so I can manually enter it every time? I mean, a full fix would be ideal, but that's better than nothing. :frown:

---

### Post by superprash2003 on 2009-01-03
you dont need to add the network and broadcast line in that file

---

### Post by Iowan on 2009-01-04
Dunno if NM has been fixed, and this is obsolete... but [here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround for static addresses.

---

