---
title: "[SOLVED] harldy not picking up my video card??"
date: 2008-07-29
forum: Multimedia Software
---

### Post by jjensen564 on 2008-07-29
cant set my screen res higher than 800 x 600  i have a on board video card =( any ideas?

---

### Post by overdrank on 2008-07-29
> **jjensen564 said:**
> cant set my screen res higher than 800 x 600  i have a on board video card =( any ideas?

Hi and welcome, if you could give us some system info, like the graphics and memory?

---

### Post by Pro-reason on 2008-07-29
> **jjensen564 said:**
> cant set my screen res higher than 800 x 600  i have a on board video card =( any ideas?

Please go to the terminal, and paste the following commands, each on its own line.  Post the output back here, using [noparse]```
...
```[/noparse] to format it.

```

sudo lshw -C video
cat /etc/lsb/release
uname -a

```

That will give us the information we need.  If you like, you can give even more system info by putting just "sudo lshw" instead of "sudo lshw -C video".

---

### Post by jjensen564 on 2008-07-29
here is the info requested... thanks for the welcome and help!! 

```

 description: Desktop Computer
    product: VT8361
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 8361-686X
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (12/24/2001)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 1800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.6.2
          slot: Socket A
          size: 1533MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: Flash Memory
          physical id: 17
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 512MiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: BANK_1
             size: 512MiB
     *-pci
          description: Host bridge
          product: VT8361 [KLE133] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8361 [KLE133] AGP Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CyberBlade/i1
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-1.0 pm vga_controller bus_master cap_list
                configuration: latency=32
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: ST380013A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.01
                serial: 5JVT8VVS
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9cf09cf0
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: ac928ffa-f095-4cf9-8dcf-8a919ccb061a
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-28 23:09:40 filesystem=ext3 modified=2008-07-29 19:29:27 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-28 19:25:27 state=mounted
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
                product: CD-ROM CRD-8521B
                vendor: LG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.04
                capabilities: removable audio
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: IDE5224
                vendor: CDWRITER
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 001H
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.6
             bus info: pci@0000:00:07.6
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0 module=snd_via82xx_modem
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: a.2
             bus info: pci@0000:00:0a.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: USB 2.0 Controller
             vendor: ALi Corporation
             physical id: a.3
             bus info: pci@0000:00:0a.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 10
             serial: 00:e0:4c:7c:eb:03
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

---

### Post by Pro-reason on 2008-07-29
OK, great.  That's your hardware info.

It would be nice to get your software info too.  The other two commands provide that.  It might also be helpful to try "*cat /etc/X11/xorg.conf*".

It seems that your onboard card is a Trident CyberBlade.  I've done a quick search, and it seems that it has low capabilities.  You may find helpful information if you search Ubuntuforums or Google for mentions of your card.

The Ubuntu driver for your card is *xserver-xorg-video-trident*, which you almost certainly already have installed.

Have you managed to get good resolution before with this hardware?

---

### Post by jjensen564 on 2008-07-29
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by overdrank on 2008-07-30
Hi and you may thy the command using the alt, F2 keys and enter 
```
gksu displayconfig-gtk
``` and adjust there.
You graphics card is 
```
display UNCLAIMED
                description: VGA compatible controller
                product: CyberBlade/i1
                vendor: Trident Microsystems
                physical id: 0

```
and I have no experiences with this graphics:(.

---

### Post by jjensen564 on 2008-08-02
i changed the settings to the trident in that window but still no good infact now im stuck at 600x480

---

### Post by jjensen564 on 2008-08-03
i wanted to thank everyone for thier help....i did get the problem fixed. here is the post that helped....

```

http://ubuntuforums.org/showthread.php?t=763964&highlight=trident+cyberblade

```

---

