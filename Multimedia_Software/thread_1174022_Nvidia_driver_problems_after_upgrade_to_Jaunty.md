---
title: "Nvidia driver problems after upgrade to Jaunty"
date: 2009-05-30
forum: Multimedia Software
---

### Post by Bearly Able on 2009-05-30
Hi,

I've been looking for help elsewhere on the forums and was advised to try here.

I have a GeForce 7900 GS graphics card, which worked perfectly under Hardy.  I upgraded to Jaunty a couple of weeks ago, and everything was fine for about a week, but then I started to have problems.  Applications would become sluggish, then freeze.  If I logged out, or tried to reboot or shut down, I got an error message ```
Could not start the X server (your graphical environment) due to some internal error.
Please contact your system administrator or check your syslog to diagnose.
In the meantime this display will be disabled.  Please restart GDM when the problem is corrected.
```Booting in recovery mode and choosing "Fix graphics problems" would get the GUI working, but the display is shifted to the right, meaning I lose the edge of the desktop.  (This is also how it displays if running from the Jaunty Live CD.)

When I checked Hardware Drivers, it recommended the Nvidia 180 driver, and showed a message stating "A different version of this driver is in use", leading me to think there might be an earlier version somewhere causing a conflict, but I don't know where or how to find it.  I've installed the "recommended" version and restarted, and it runs fine for a wee while, then the problem occurs again.  I've also tried leaving it without installing the "recommended" driver (i.e. with the message about a different version being in use) but the problem still occurred.

By yesterday, it had become so bad I couldn't run anything for more than about five minutes without a freeze or a crash.

Today, I used Synaptic to completely remove the Nvidia driver, since when (several hours ago) I've had no further trouble, but of course I've lost the right hand edge of my desktop.  When I removed the driver, I noticed Synaptic was showing one package to remain unchanged. This is something called gstreamer0.10-plugins-bad. When I upgraded to Jaunty, this package showed up with updates available, but then I had a message to say it was unable to install updates (or something like that). Could this be contributing to the problems, and if so, should I try again to update it or can I safely remove it? I'm not sure what it does.

I'd like to try reinstalling the recommended Nvidia driver, but still don't know how to check if there's an older version around somewhere that I ought to remove first.  I'm pretty sure I've never installed drivers other than through Synaptic.

My system specs, if needed, are as follows:```
mandela                   
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2
  *-core
       description: Motherboard
       product: P965T-A
       vendor: ELITEGROUP COMPUTER SYSTEM CO.,LTD.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/15/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          slot: Socket 775
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous [empty]
             physical id: 1
             slot: A1
             width: 24832 bits
        *-bank:2
             description: DIMM DDR Synchronous
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM DDR Synchronous [empty]
             physical id: 3
             slot: A3
             width: 24832 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          size: 2400MHz
          capacity: 2400MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G71 [GeForce 7900 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMB361 AHCI/IDE
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMB361 AHCI/IDE
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi6
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0
              *-cdrom
                   description: DVD-RAM writer
                   product: DVDRW LH-20A1H
                   vendor: LITE-ON
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: LL06
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=nodisc
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:04:05.0
                logical name: eth0
                version: 10
                serial: 00:19:21:3d:cd:dd
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.64 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
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
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi4
             logical name: scsi5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk:0
                description: ATA Disk
                product: WDC WD1600JS-00N
                vendor: Western Digital
                physical id: 0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WCANMD777519
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fbc4fbc4
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 92730b41-38cb-dd4c-ae3f-06d071c6a031
                   size: 34GiB
                   capacity: 34GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-04-04 19:08:23 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sda2
                   size: 114GiB
                   capacity: 114GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 29GiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /media/disk
                      capacity: 31GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 32GiB
                 *-logicalvolume:3
                      description: HPFS/NTFS partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 21GiB
           *-disk:1
                description: ATA Disk
                product: WDC WD1600AAJS-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WMAV30402278
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ec031
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 5fd01ebc-10f0-404f-9c20-35fb88570be0
                   size: 143GiB
                   capacity: 143GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-02-03 19:58:49 filesystem=ext3 modified=2009-05-25 21:08:38 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-05-25 12:17:37 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sdb2
                   size: 5930MiB
                   capacity: 5930MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 5930MiB
                      capabilities: nofs
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:66:c7:d6:a3:04
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```Sorry for the long post.  I'd be really grateful for any advice on how to diagnose and fix the problem.  I'm pretty much of a Linux beginner, so please try to keep the instructions simple!  Thanks in advance.

---

### Post by Quirriff on 2009-05-30
I'm not sure exactly, But I think it has something to do with the Kernel being updated.

This is my understanding:

The driver's aren't downloaded Pre-cooked, they configured on the spot to fit the current Kernel. Should that Kernel change then that driver doesn't work. I'm sorry But I don't know enough to give you a solution.

---

### Post by Bearly Able on 2009-05-30
Hi Quirriff, thanks for your response.

So you think if I download the driver again now, with the new kernel installed, it should be properly configured?

---

### Post by 73ckn797 on 2009-05-30
> **Quirriff said:**
> I'm not sure exactly, But I think it has something to do with the Kernel being updated.

This is my understanding:

The driver's aren't downloaded Pre-cooked, they configured on the spot to fit the current Kernel. Should that Kernel change then that driver doesn't work. I'm sorry But I don't know enough to give you a solution.


If the system was upgraded then the new kernel is installed with the upgrade. After that the driver is made available and recommended. Jaunty currently has the "2.6.28-11-generic" kernel.

---

### Post by Bearly Able on 2009-05-31
OK, so now I'm really getting desperate.

The computer ran fine for several hours yesterday, and apparently closed down without problems.  When my husband tried to boot up today, he could get as far as selecting the entry from the GRUB menu, then nothing; just a black screen with a flashing cursor for several minutes, and eventually the message ```
Error 25 disc read error

Press any key to continue
```which then takes us back to the GRUB menu.

Selecting recovery mode produces the same results.

The only thing I'd done to the system since I posted yesterday was to update the gstreamer0.10-plugins-bad file, as mentioned in my original post.

At the moment, I'm using the Live CD, but I really need my system back up and running as I work from home on this computer.  Any help will be greatly appreciated.

---

### Post by Bearly Able on 2009-05-31
OK, I seem to have fixed the GRUB error problem, although I'm not entirely sure how.

I'd still appreciate some help with the original Nvidia problem.  I will re-install Jaunty if necessary, but I'd like to understand the problem first; I don't want to re-install and find I still have the exact same problem.

---

### Post by Bearly Able on 2009-06-02
The system still seems to be running fine without the Nvidia drivers installed.  If no one has any better suggestions, I'll re-install them later and see what happens.  I really need to get the edge of my desktop back!

---

### Post by Bearly Able on 2009-06-03
Well, what happened is I reinstalled the drivers and Firefox froze within the hour.  Although I was apparently able to shutdown the system normally, when I came to restart just now, I got a message about an unclean shutdown, followed by needing to run fsck manually, etc.  I've got things back up and running and have removed the Nvidia driver again.

My problems are these:

I need this machine to work reliably, as I use it to work from home.  

I would reinstall 8.04, which was working just fine, but I need Open Office 3 to be compatible with files transferred from a Windows computer in someone else's office.  I can't open Open Office 3 password-protected files in Open Office 2.4 (as I think it was).  I tried downloading Open Office 3 from their Web site onto my laptop, which also runs 8.04, but it doesn't run very well.

The system works OK with Jaunty without the Nvidia driver, but I've lost the right-hand edge of the screen, including the scroll bar and almost all the "deleted items" and "shutdown" icons.  There is only a very tiny area of these visible to click, tricky at best, but on a bad day nigh on impossible.  (I have neurological problems.)

If nobody can help with the Nvidia problem, could someone at least make helpful suggestions about the others, in particular, how I access the shutdown/logout menu from the keyboard.

Thank you.

---

