---
title: "Cable TV input not working"
date: 2013-01-09
forum: Multimedia Software
---

### Post by Matt12334 on 2013-01-09
My computer is running Ubuntu 12.04, and doesn't seem to have any graphical issues.  The graphics card installed is (I think) the NVIDIA GEFORCE 7300 LE PCI-E.

I'm attempting to get the cable TV input to work for programs like Kaffeine and TvTime.

Here's the output of lspci:
```

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 LE] (rev a1)
02:00.0 Multimedia controller: Advanced Micro Devices [AMD] nee ATI Device 4d51
03:03.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

```

I have already installed the recommened graphics card driver as well, so any help is greatly appreciated.

---

### Post by TheFu on 2013-01-09
I think that card is only for TV output, not input.

If you want to capture TV or VCR inputs, then you need a TV capture card or USB device of some sort.  Hauppauge is a linux friendly vendor of capture devices.  I like the HD-Homerun network tuners myself, but those are TV tuners, not a generic video input device.

---

### Post by Matt12334 on 2013-01-09
> **TheFu said:**
> I think that card is only for TV output, not input.

If you want to capture TV or VCR inputs, then you need a TV capture card or USB device of some sort.  Hauppauge is a linux friendly vendor of capture devices.  I like the HD-Homerun network tuners myself, but those are TV tuners, not a generic video input device.

Thanks for the reply. I think you're right, which leads me to believe that it's actually a different part of our computer. I believe there is a TV tuner card as well. It works in Windows, so the cable input hardware is apparently there. My first instinct was that it was the AMD multimedia controller, but I ended up going against my gut feeling. How might I get Ubuntu to properly detect and use this card?

---

### Post by TheFu on 2013-01-09
Well, if Ubuntu knows about it, then it will be shown in the **lshw **command.
I don't see a tuner in the **lspci** output.

Run that with:
$ **sudo lshw**
and look through the results for the capture/tuner card. If lshw doesn't see the card, that doesn't mean it isn't supported, just that the driver was not automatically loaded.

If it works in Windows, perhaps you should boot intoWindows and check** device manager** to find the exact model of the capture card/tuner?

Next, I would google "ubuntu driver {insert capture card vendor name, device and model number}" to see the steps to get the driver installed.

---

### Post by Matt12334 on 2013-01-09
Alright, here's the output for sudo lshw:
```
    description: Mini Tower Computer
    product: Dell DM061 ()
    vendor: Winbond Electronics
    serial: DHRZZC1
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=2 power-on_password=enabled uuid=44454C4C-4800-1052-805A-C4C04F5A4331
  *-core
       description: Motherboard
       product: 0WG864
       vendor: Winbond Electronics
       physical id: 0
       serial: ..CN481117420107.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: 2.3.2
          date: 03/30/2007
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6320  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Microprocessor
          size: 1866MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 4MiB
             capacity: 4MiB
             capabilities: internal varies unified
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
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: HYMP512U64CP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: 00006213
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: F6428U61E5667F
             vendor: 7F7F7F7F7FF70000
             physical id: 1
             serial: 00000000
             slot: DIMM_3
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: HYMP512U64BP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             serial: 04004158
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: F6428U61E5667F
             vendor: 7F7F7F7F7FF70000
             physical id: 3
             serial: 00000000
             slot: DIMM_4
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1850MHz
          capabilities: vmx ht
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
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:dd000000-dfefffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G72 [GeForce 7300 LE]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:dd000000-ddffffff memory:c0000000-cfffffff memory:de000000-deffffff memory:dfe00000-dfe1ffff
        *-network
             description: Ethernet interface
             product: 82562V 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:19:d1:65:54:21
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.1-2 ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:43 memory:dffe0000-dfffffff memory:dffdb000-dffdbfff ioport:ecc0(size=32)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff00(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:dffdac00-dffdafff
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:dffdc000-dffdffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:dcf00000-dcffffff ioport:d0000000(size=33554432)
           [COLOR="DarkRed"]*-multimedia UNCLAIMED
                description: Multimedia controller
                product: Advanced Micro Devices [AMD] nee ATI
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0[/COLOR]
                resources: memory:dcf00000-dcffffff memory:d0000000-d1ffffff
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff80(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff60(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ff980800-ff980bff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:dce00000-dcefffff
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: 3
                bus info: pci@0000:03:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:dcef0000-dcefffff ioport:dcf8(size=8)
        *-isa
             description: ISA bridge
             product: 82801HH (ICH8DH) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: 82801 SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fec0(size=32) memory:ff970000-ff9707ff
           *-disk
                description: ATA Disk
                product: ST3250820AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AD
                serial: 5QE3F52W
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=58000000
              *-volume:0
                   description: Windows FAT volume
                   vendor: Winbond Electronics
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   serial: 07d7-0518
                   size: 54MiB
                   capacity: 54MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 802a1d38-64bd-9e43-a8a0-0322fa48ef93
                   size: 10216MiB
                   capacity: 10GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-05-24 09:34:36 filesystem=ntfs label=RECOVERY state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: f270ce5e-12d6-2d47-bc11-94d3d9093876
                   size: 184GiB
                   capacity: 184GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-05-24 09:34:41 filesystem=ntfs label=OS modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 29GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 8191MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW GSA-H31N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: B109
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
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
             resources: memory:dffdab00-dffdabff ioport:ece0(size=32)
     *-scsi
          physical id: 2
          bus info: usb@2:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB   HS-CF Card
             vendor: TEAC
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 4.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: USB   HS-xD/SM
             vendor: TEAC
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             version: 4.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: USB   HS-MS Card
             vendor: TEAC
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             version: 4.00
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: USB   HS-SD Card
             vendor: TEAC
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             version: 4.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde

```
The red portion seems like what I'm looking for, what do you think?

---

### Post by TheFu on 2013-01-10
Perhaps, but a driver definitely is not be loaded automatically. You'll need to **boot Windows** and look in **Device Manager **to get more data about it.  You are looking for the chips used inside it, so you can find a Linux driver.

Good luck!

---

