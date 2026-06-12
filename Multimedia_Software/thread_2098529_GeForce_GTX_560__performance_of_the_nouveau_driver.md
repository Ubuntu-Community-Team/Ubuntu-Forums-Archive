---
title: "GeForce GTX 560  performance of the nouveau driver ?"
date: 2012-12-26
forum: Multimedia Software
---

### Post by bretonfou on 2012-12-26
I wonder if I should install nvidia own drivers. 

I use the x86 kernel : 3.2.0-35-generic-pae #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 i686 i686 i386 GNU/Linux 

lsmod tells me that i use the "nouveau" driver, xorg,xonf is nowhere to be found and there is no xorg.conf.d neither. 

The performance is not great (i have a I5 ) , as example my browser is not really more fluid than mozilla in the mid 90´s on a 50mghz 486.

```

newbiak
    description: Desktop Computer
    product: H55N-USB3 ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-1C6F65545C3D
  *-core
       description: Motherboard
       product: H55N-USB3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F5
          date: 08/20/2010
          size: 128KiB
          capacity: 8128KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          slot: Socket 1156
          size: 1197MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 4MiB
             capabilities: synchronous internal write-back
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
        *-logicalcpu:2
             description: Logical CPU
             physical id: 1.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 1.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 1.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 1.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 1.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 1.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 1.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 1.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 1.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 1.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 1.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 1.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 1.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 1.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 196 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 2
             slot: A2
             size: 2GiB
             width: 196 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          size: 1197MHz
          capacity: 1197MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 1.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 1.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 1.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 1.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 1.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 1.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 1.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 1.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 1.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 1.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 1.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 1.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 1.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 1.10
             capabilities: logical
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 18
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:f6000000-f9ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: GF110 [GeForce GTX 560 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:f6000000-f7ffffff memory:e0000000-e7ffffff memory:ec000000-efffffff ioport:df00(size=128) memory:e8000000-e807ffff
           *-multimedia
                description: Audio device
                product: GF110 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f9ffc000-f9ffffff
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:43 memory:fbfff000-fbfff00f
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff00(size=32)
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:fe00(size=32)
        *-usb:2
             description: USB controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fd00(size=32)
        *-usb:3
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fbffe000-fbffe3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:fbff4000-fbff7fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:dfc00000-dfdfffff ioport:dfe00000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:e000(size=4096) memory:df800000-dfbfffff ioport:fbe00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: 1c:6f:65:54:5c:3d
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.0.14 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff
        *-usb:4
             description: USB controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fc00(size=32)
        *-usb:5
             description: USB controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fb00(size=32)
        *-usb:6
             description: USB controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fa00(size=32)
        *-usb:7
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fbffd000-fbffd3ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:f900(size=8) ioport:f800(size=4) ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=32) memory:fbffc000-fbffc7ff
           *-cdrom
                description: DVD-RAM writer
                product: iHAS122
                vendor: ATAPI
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: ZL08
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: ST9500420AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 0002
                serial: 5VJB5P6A
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3981218b
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: c129a4c8-4e66-4aec-93d0-7248f60b3f1f
                   size: 8084MiB
                   capacity: 8084MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 337GiB
                   capacity: 337GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /mint
                      capacity: 15GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /datas
                      capacity: 322GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered state=mounted
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 18025144-5816-4359-970c-ce7d9c2db8a6
                   size: 63GiB
                   capacity: 63GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-12-25 22:30:20 filesystem=ext4 lastmountpoint=/ modified=2012-12-25 22:42:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-12-26 16:11:34 state=mounted
              *-volume:3
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@1:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /Public
                   version: 1.0
                   serial: 80a6c54c-4981-41eb-9055-3fc2d64c2414
                   size: 56GiB
                   capacity: 56GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2012-12-22 01:44:18 filesystem=ext3 label=Public lastmountpoint=/Public modified=2012-12-26 16:11:35 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered mounted=2012-12-26 16:11:35 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fbffb000-fbffb0ff ioport:500(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:02.3
          version: 05
          width: 32 bits
          clock: 33MHz



```

---

### Post by oldfred on 2012-12-26
I have a 6 year old core duo with 4GB of RAM and have run the 64bit version of Ubuntu with the nVidia drivers. I only install the ones offered by Ubuntu not downloading the nVidia. If you had an extremely new nVidia card, then you might need the newest drive direct from nVidia.

I do run fallback or gnome-panel as I prefer the menus, but have no issues with my 9600gt video card. That card was an upgrade about 3 years ago as my 7600GS blew all the capacitors out. :)

I show several versions available and have installed current-updates to be a little newer than default. Do not install 295.40 as that did have some issues, but only on older cards.

```
fred@fred-Precise:~$ dpkg -l | grep -i nvidia*
rc  nvidia-173                             173.14.30-0ubuntu8                                  NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                          1:0.2.44.2                                          Find obsolete NVIDIA drivers
rc  nvidia-current                         295.40-0ubuntu1                                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                 304.43-0ubuntu0.1                                   NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-settings                        295.33-0ubuntu1                                     Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                304.43-0ubuntu0.2                                   Tool of configuring the NVIDIA graphics driver


```

---

### Post by bretonfou on 2012-12-27
It worked but now my PC freeze really often and mpd stopped to work. 

The internal audio sound card is still detected and vlc, mplayer are seen by pulsuaudio but mpd is not. 

There is no error is the log file of mpd. 

Moreover now the sound card part of the nvidia card is not seen anymoe
and moreover the sound rear  output get shut down when i plug and headphone 
(and it do not want that). Before in analog duplex i was able to get both on. 

This is quite riduclous, 12,04 is a LTS and  it does not even afford basic capabilities : sound server and decent 2d performance. 


Why is it that i cannot edit my x11 file ? Where is gone xorg.conf ?
It is supposed to be now in xorg.conf.d but the no such repertory. 

I m trying to purge nvidia-* and to reinstal nouveau*
==> praying.

---

### Post by bretonfou on 2012-12-27
It actually worked. 

I reinstaled xorg-nouveau, purged all nvidia packages, reinstaled ubunut-desktop
and now i m back with 2 sounds cards and the computer don t freeze anymore.

mpd is still buggy but this may be unrelated since it probably broke by getting updated.

---

