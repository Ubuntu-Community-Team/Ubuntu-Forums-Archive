---
title: "Stereo to Mono"
date: 2009-04-11
forum: Multimedia Software
---

### Post by mr_x408 on 2009-04-11
Hi all, i have a hp laptop with ubuntu 8.10 and i use exterior speakers for it. the problem is that one of the speakers stopped working so i only get the sounds that would come out of the main speaker. i was wondering if there was a way to change some settings to make all sounds come out of my one speaker

---

### Post by ianmaxwell on 2009-04-29
yeah. this. anyone know??

---

### Post by jaw1959 on 2009-04-29
I'm having a similar issue.  I have a motherboard with on-board 8 channel surround sound, and I'm trying to output an analog stereo signal to a TV.  I would assume the method for forcing mono output on a stereo card would be similar to forcing stereo out of my front channel.  Please help!

---

### Post by tjefferson on 2009-06-22
Hi. I have the same issue, and the only way I can get around it is in VLC and selecting a mono setting from the audio menu. Does anyone have a better solution?

---

### Post by GNU Fanatic on 2010-02-06
One of my ears isn't working very well due to being blocked with earwax and olive oil, so I'd quite like to be able to make all sound play as mono for a bit.

---

### Post by SchnowdaPowda on 2010-04-05
I'm having this problem as well.

---

### Post by PhoneixS on 2010-07-05
I have the same problem (a break auricular) and then I need to play only in the right channel as mono. No body know how to do it?

---

### Post by robert shearer on 2010-07-05
System=>Preferences=>Sound.

Tab=>Output

Connector=> dropdown menu and select 'analog **mono **output/no amplifier.

or amplifier if you have it ? Lappy ? try it and see.

---

### Post by PhoneixS on 2010-07-05
> **robert shearer said:**
> System=>Preferences=>Sound.

Tab=>Output

Connector=> dropdown menu and select 'analog **mono **output/no amplifier.

or amplifier if you have it ? Lappy ? try it and see.
Didn't worked for me. In Output tab I only have "Analog Speakers", "Analog Output" and "Analog Headphones" but none called mono. In the Hardware tab, I only have Analog Stereo profiles.

---

### Post by robert shearer on 2010-07-05
> In the Hardware tab, I only have Analog Stereo profiles

Mine lists 24 profiles from off through to Stereo duplex though I have to **scroll up** to see them all.
I am using an older (2002) desktop and the mobo's built-in sound so its nothing fancy.

Try running in a terminal (Applications=>Accessories=>Terminal then type in the code below and hit enter.) 
```
sudo lshw 
```
and paste the output so we can see the hardware you have.

---

### Post by PhoneixS on 2010-07-05
This is the output:
```
ubuntu-javier
    description: Desktop Computer
    product: HP Compaq dx2300 Microtower
    vendor: Hewlett-Packard
    serial: HUB7******
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00DD53EF-C6F6-1210-AE84-B965BB7F1EEB
  *-core
       description: Motherboard
       product: 0A90
       vendor: MSI
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: MS7336 1.08 (05/25/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Socket 775
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
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
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82946GZ/PL/GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82946GZ/PL/GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-display
             description: VGA compatible controller
             product: 82946GZ/GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:25 memory:fda00000-fdafffff memory:d0000000-dfffffff(prefetchable) ioport:ff00(size=8)
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fdff8000-fdffbfff
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fe00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fd00(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fc00(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fb00(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdfff000-fdfff3ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
           *-network
                description: Ethernet interface
                product: N10/ICH 7 Family LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial: XX::XX My mac
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.128 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:20 memory:fdcff000-fdcfffff ioport:ef00(size=64)
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
        *-ide
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16) memory:fdffe000-fdffe3ff
           *-disk
                description: ATA Disk
                product: WDC WD2500JS-60M
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WCANKL308960
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f362f362
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /windows
                   version: 3.1
                   serial: 3c0a70d4-bc7e-9544-8123-805060d51fb8
                   size: 83GiB
                   capacity: 83GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-01-11 18:54:49 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 0422ad60-d7c3-4db6-9fa0-a5108d4c44fb
                   size: 83GiB
                   capacity: 83GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-11 18:23:19 filesystem=ext4 lastmountpoint=/Y7.rï¿œï¿œïï¿œï¿œaï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œg ï¿œ-]/ï¿œï¿œï¿œï¿œï¿œï¿œ!ï¿œï¿œï¿œï¿œï¿œrï¿œï¿œïï¿œï¿œï¿œï¿œï¿œï¿œj modified=2010-06-18 12:35:22 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-07-05 16:06:20 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 3906MiB
                   capacity: 3906MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3906MiB
                      capabilities: nofs
              *-volume:3
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /home
                   version: 1.0
                   serial: ba55eef4-b875-4733-91e5-88d0c3049a1e
                   size: 61GiB
                   capacity: 61GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-11 18:23:48 filesystem=ext4 lastmountpoint=/homeï¿œ9ï¿œ4,ï¿œï¿œï¿œïï¿œï¿œgï¿œï¿œï¿œ>1ï¿œï¿œg ï¿œPï¿œï¿œCPï¿œï¿œ1ï¿œï¿œ1ï¿œï¿œ,ï¿œï¿œï¿œ>1ï¿œ> modified=2010-07-05 16:06:20 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2010-07-05 16:06:20 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GSA-H60L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: R90A
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             resources: ioport:500(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

---

### Post by robert shearer on 2010-07-05
>  *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fdff8000-fdffbfff

Looks fine. This is the onboard audio ?.
 Have you had a separate soundcard installed at any time.?

---

### Post by PhoneixS on 2010-07-06
It is the onboard audio. And I haven't had a separate soundcard.

---

### Post by CannibalZerg on 2010-07-06
Create/edit .asoundrc file in your home dir (i.e. ~/.asoundrc ):

```

#channel number:
# 0 - front left
# 1 - front right

[FONT=Arial][SIZE=2]pcm.mono_right {
   type route
   slave.pcm  "cards.pcm.default"
   ttable.0.1 1 [/SIZE][/FONT][FONT=Arial][SIZE=2]#in-channel 0, out-channel 1, 100% volume[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    ttable.1.1 1 [/SIZE][/FONT][FONT=Arial][SIZE=2]#in-channel 1, out-channel 1, 100% volume[/SIZE][/FONT]
[FONT=Arial][SIZE=2] }
[/SIZE][/FONT][FONT=Arial][SIZE=2]
pcm.mono_left {
   type route
   slave.pcm  "cards.pcm.default"
   ttable.0.0 1  #in-channel 0, out-channel 0, 100% volume
[/SIZE][/FONT][FONT=Arial][SIZE=2]    ttable.1.0 1  [/SIZE][/FONT][FONT=Arial][SIZE=2]#in-channel 1, out-channel 0, 100% volume[/SIZE][/FONT]
[FONT=Arial][SIZE=2] }

# Replacing default device
# choose the correct line and comment another one
[/SIZE][/FONT][FONT=Arial][SIZE=2]pcm.!default pcm.mono_right[/SIZE][/FONT]
[FONT=Arial][SIZE=2]#pcm.!default pcm.mono_left[/SIZE][/FONT]

```If you need "mono-to-left" instead of "mono-to-right", uncomment the last line and comment previous one.

---

