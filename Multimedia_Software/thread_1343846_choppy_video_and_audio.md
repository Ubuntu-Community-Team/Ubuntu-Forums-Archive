---
title: "choppy video and audio"
date: 2009-12-02
forum: Multimedia Software
---

### Post by Kilcaff on 2009-12-02
Hi,

I seem to always find flash problems when I search for this so apologies if this is already posted.

I have 9.04 and 9.10 on different machines but get similar problems on both.  Video playback from a file is choppy and tends to stutter.  I get the same issues on the audio playback through rhythmbox.

I'm using vlc for video and sometimes mp3.  I've followed the media guide sticky but still get this problem.

This problem is annoying as I want to set ubuntu up as a mediacentre with a tv card and if I can't get a nice video stream on movie playback I'm going to have to use windows, and I don't want to head back there!

---

### Post by Kilcaff on 2009-12-03
anybody know about this issue?  I can't believe I'm the only one as it's happening on two separate machines using different versions of ubuntu.

Is it a way that vlc and other programs buffer video?

---

### Post by sites on 2009-12-03
Can you list specs of your hardware?

sudo lshw

---

### Post by Grenage on 2009-12-03
Hi there,

What video card do you have, and what drivers are you using?

---

### Post by Kilcaff on 2009-12-03
Sorry, lot of info but here's the hardware breakdown:
```
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=24F771B4-B168-D911-94BD-77B592DCF0DC
  *-core
       description: Motherboard
       product: K8VSEDX
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: Rev 2.00
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1008.004 (09/08/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3200+
          serial: To Be Filled By O.E.M.
          slot: Socket 754
          size: 2200MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up rep_good
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 3a
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:2
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci:0
          description: Host bridge
          product: VT8385 [K8T800 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=64
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: R420 JK [Radeon X800]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list
                configuration: latency=64 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: R420 [Radeon X800] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 mingnt=8
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-storage:0
             description: RAID bus controller
             product: PDC20378 (FastTrak 378/SATA 378)
             vendor: Promise Technology, Inc.
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_promise latency=96 maxlatency=18 mingnt=4
        *-network:0
             description: Ethernet interface
             product: 88E8001 Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: 13
             serial: 00:11:d8:66:4e:4d
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.81 latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
        *-network:1
             description: Wireless interface
             product: Atheros AR5001X+ Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: e
             bus info: pci@0000:00:0e.0
             logical name: wmaster0
             version: 01
             serial: 00:18:4d:71:4f:94
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.82 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
        *-storage:1
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_via latency=64
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi5
             logical name: scsi6
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
           *-disk:0
                description: ATA Disk
                product: ST3200822A
                vendor: Seagate
                physical id: 0
                bus info: scsi@5:0.0.0
                logical name: /dev/sda
                version: 3.01
                serial: 4LJ0QQWS
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00199173
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0a189dae-851c-7644-a553-55d76565b149
                   size: 110GiB
                   capacity: 110GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-05-08 17:18:40 filesystem=ntfs label=Windows modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sda2
                   size: 75GiB
                   capacity: 75GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 42GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 3200MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      capacity: 29GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 1325MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST330630A
                vendor: Seagate
                physical id: 1
                bus info: scsi@5:0.1.0
                logical name: /dev/sdb
                version: 3.27
                serial: 3CK0FR31
                size: 28GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1cd41cd3
              *-volume
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@5:0.1.0,1
                   logical name: /dev/sdb1
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 28GiB
           *-cdrom:0
                description: DVD writer
                product: DVD_RW ND-2500A
                vendor: _NEC
                physical id: 2
                bus info: scsi@6:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.07
                serial: [_NEC    DVD_RW ND-2500A 1.07HV2B5DLBS 44L3903C
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                physical id: 3
                bus info: scsi@6:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
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
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication UNCLAIMED
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 1
          bus info: usb@1:4.4
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@7:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@7:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@7:0.0.3
             logical name: /dev/sdf
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:e6:df:0e:43:a1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I'm using a radeon x800xt and the on-board sound from the mobo.  Let me know any other info you need.  This machine is using Jaunty 64bit.
I'm not sure if I've ended up with 'too many cooks' syndrome drivers wise as I pretty much followed the media guide on this forum so although it does delete some drivers/libraries in the guide I may have some others conflicting.  Not sure.

Thanks for any help.

---

### Post by Grenage on 2009-12-03
Are you using the open ATI drivers, or the proprietary ones?

---

### Post by Kilcaff on 2009-12-03
I believe it's the open source one, I tried the prop but it killed my display if I remember correctly.  Hardware Drivers shows no prop drivers installed and xserver-xorg-video-radeon and xserver-xorg-video-ati are showing as installed.

Is there a quick and easy way to get driver info on hardware, say through terminal?

---

### Post by Grenage on 2009-12-03
I would try the proprietary ones again if I were you, there have been some revisions of late. Check under *System/Admin/Hardware drivers*.

lspci is a quick way to get hardware info.

---

