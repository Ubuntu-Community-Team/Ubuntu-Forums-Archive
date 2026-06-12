---
title: "GeForce 6150SE, Nouveau graphics"
date: 2014-11-07
forum: Multimedia Software
---

### Post by evilbrent on 2014-11-07
So Nvidia stopped providing linux support to my graphics card when my computer upgraded from Linux 3.5.XXX to 3.13.XXX. (Using Ubuntu 12.04).

In order for me to use the computer I have to boot up into "Previous Versions" so I'm having trouble making changes to the computer. Booting into the current linux 3.13.XXX just sends me to a low-graphics terminal-only mode, and I can't get into the GUI to follow any of the instructions about changing graphics drivers through system-settings. I've tried literally every option presented at bootup to try to just revert to standard graphics but am not able to see the desktop at all unless I boot into "previous version".

This is causing me all sorts of problems in my computer (and therefore my marriage...) because I'm not able to update anything and it's very upsetting. 

Can anyone point me in the direction of how to get nouvaue on the current linux? The instructions at [http://nouveau.freedesktop.org/wiki/UbuntuPackages/](http://nouveau.freedesktop.org/wiki/UbuntuPackages/) don't help me very much because when I try to Install the xserver-xorg-video-nouveau package it gives the error:

```
Package dependencies could not be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

xserver-xorg-video-nouveau: Depends: xorg-video-abi-11 but it is a virtual package
                            Depends: xserver-xorg-core (>= 2:1.10.99.901) but 2:1.11.4-0ubuntu10.14 is to be installed

```
I'm afraid I don't really understand what's going on here. My suspicion is that it won't work because I'm in the "previous version" right now.

---

### Post by Bucky Ball on 2014-11-07
*Thread moved to **Multimedia**.*

That's right. 

When you get to the boot menu (which lists your installs) choose the 12.04 kernel, but DON'T hit enter. Instead, hit 'e' to edit the line.

Find the kernel line that ends in 'quiet splash' or any one or combination of those two words;
At the end of that line, after a space, type 'nomodeset'; 
I think it is ctl+x to save and boot (the instructions are at the bottom of the edit screen).

Any luck?

---

### Post by evilbrent on 2014-11-13
Hi, thanks for your reply. I finally got a chance to try out your suggestion.

I had to do some research to find out if I'm supposed to use ' ' or just the plain text in nomodeset. Turns out just the plain text. But I tried replacing [FONT=courier new]quiet splash $vt_handof[/FONT][FONT=courier new]f[/FONT] with [FONT=courier new]quiet splash nomodeset[/FONT] and it didn't work.

When I next get a chance to fiddle with it I'm going to try to instead replace it with [FONT=courier new]nomodeset $vt_handoff[/FONT] as I read that was the correct edit.

To be honest I'm thiiiis close to fixing my problem with [FONT=courier new]do-release-update[/FONT] and hopefully there just won't be this issue in 14.04 for me but the thing is my computer is getting old and I'm hesitant.

---

### Post by mörgæs on 2014-11-14
A precise hardware list makes it easier for people to help you.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by evilbrent on 2014-11-18
No worries, I never know how much information to include: lshw output below.

(By the way I tried to edit the boot menu but it didn't achieve anything. Still just went through to the "low graphics mode" screen.)


```
computer    description: Desktop Computer
    product: MS-7309 (To Be Filled By O.E.M.)
    vendor: MSI
    version: 1.0
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: chassis=desktop cpus=4 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M.
  *-core
       description: Motherboard
       product: MS-7309
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V9.4
          date: 02/17/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) X4 620 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: 15.5.2
          serial: [REMOVED]
          slot: CPU 1
          size: 2626MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
          configuration: cores=4 enabledcores=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 2GiB
             width: 64 bits
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.5.2
          size: 2600MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:2
          physical id: a
          bus info: cpu@2
          version: 15.5.2
          size: 2600MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:3
          physical id: e
          bus info: cpu@3
          version: 15.5.2
          size: 2600MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:4f00(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP61 SMU
          vendor: NVIDIA Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:d0000000-d007ffff
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:dff7f000-dff7ffff
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:dff7ec00-dff7ecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:dff78000-dff7bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fff0(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: [REMOVED]
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=[REMOVED] latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:43 memory:dff7d000-dff7dfff ioport:ee00(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:ed80(size=8) ioport:ed00(size=4) ioport:ec00(size=8) ioport:eb80(size=4) ioport:eb00(size=16) memory:dff7c000-dff7cfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:23 memory:de000000-deffffff memory:c0000000-cfffffff memory:dd000000-ddffffff memory:dff40000-dff5ffff
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 10
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000DM003-1CH1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: CC49
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00077ca6
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: [REMOVED]
                size: 27GiB
                capacity: 27GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-06-01 19:14:56 filesystem=ext4 lastmountpoint=/ modified=2014-06-01 20:06:29 mounted=2014-10-15 19:26:32 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 4030MiB
                capacity: 4030MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4030MiB
                   capabilities: nofs
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 13GiB
                capacity: 13GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-06-01 20:10:33 filesystem=ext4 label=Root lastmountpoint=/ modified=2014-10-01 18:45:18 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-11-18 16:57:33 state=mounted
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sda4
                logical name: /home
                version: 1.0
                serial: [REMOVED]
                size: 885GiB
                capacity: 885GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-06-01 20:10:36 filesystem=ext4 lastmountpoint=/home modified=2014-11-18 16:57:34 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-11-18 16:57:34 state=mounted
     *-scsi:1
          physical id: 11
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD20EARX-00P
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 51.0
             serial: [REMOVED]
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0000b442
           *-volume
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/2TB_Media
                version: 1.0
                serial: [REMOVED]
                size: 1851GiB
                capacity: 1851GiB
                capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2011-08-11 13:12:56 filesystem=ext3 label=2TB lastmountpoint=/media/2TB_Media modified=2014-11-18 16:57:34 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,barrier=1,data=ordered mounted=2014-11-18 16:57:34 state=mounted
```

---

### Post by mörgæs on 2014-11-18
Not that I am able to advise you better, but now that we know the graphics card maybe someone is...

---

### Post by evilbrent on 2014-11-18
No worries.

I live in hope. It's a nice feeling, to have something to hope for.

---

