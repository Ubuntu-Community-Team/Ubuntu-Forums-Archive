---
title: "Intel Centrino Wireless-N 1000: HP dv6tqe wireless network won't connect."
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by dtgee on 2013-06-18
I am currently running Windows 7, I'm trying to install Ubuntu 12.04 dual boot from a DVD disk. I'm using the "Try Ubuntu" option to make sure  everything works correctly before I install Ubuntu, but I can't get the wireless network working properly. It repeatedly asks me to authenticate myself, so I type in the password over and over but it never connects. I'm sure the password is correct. Any suggestions?

Edit: I also forgot to mention, but when I tried installing Ubuntu back when I was in school, I used the internet connection over there (there was a different router as well) and the internet worked flawlessly. I'm at home now, using a different internet connection and a different router. So the source of the problem could come from the router/internet connection. I also remember one time I was trying to get my wireless connection working at a sandwich shop, but I ended up disabling some of my network drivers (I think I re enabled them all by now? If not, it could be a problem, but I think I re enabled them all. Anyone know how to check?).

---

### Post by mörgæs on 2013-06-20
Hi, welcome to the fora.

When testing and/or installing it's best to use a wired internet connection.

---

### Post by dtgee on 2013-06-20
Hi morgaes,

I'm trying to get my wireless internet connection working before I install Ubuntu, and what I described above is what is happening. I'm still completely new to Linux/Ubuntu, so I'm not sure what Xubunutu, Lubunutu, and Kubuntu are. I'm just installing Ubuntu. And I'm also not upgrading anything... I think.

---

### Post by mörgæs on 2013-06-21
Again, when testing and/or installing it's best to use a wired internet connection, especially if you are new. Drivers for the wirefree card is a classical problem for a live boot, and the problem is often fixed after installation.

If you want an indication about how compatible your card (and other hardware) is please run ```
sudo lshw > lshw.txt
``` from the live boot and post lshw.txt in CODE tags.

The dv6's sometimes have a problem overheating. Would be good to run it under a heavy load in a live boot to see how it behaves.

---

### Post by dtgee on 2013-06-22
This is the resule of running sudo lshw.
```
ubuntu
    description: Notebook
    product: HP Pavilion dv6 Notebook PC (QJ916AV#ABA)
    vendor: Hewlett-Packard
    version: 0592110000204710000620100
    serial: 2CE1481NVJ
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PAV sku=QJ916AV#ABA uuid=35314544-3346-4530-3143-353131314531
  *-core
       description: Motherboard
       product: 17FB
       vendor: Hewlett-Packard
       physical id: 0
       version: 10.5A
       serial: PCKWA2B2H1U0UL
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.1B
          date: 10/23/2012
          size: 1MiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 0063F0C8
             slot: Bottom-Slot 1(top)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CH9
             vendor: Samsung
             physical id: 1
             serial: 0063F0CD
             slot: Bottom-Slot 2(under)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1b
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
          slot: CPU1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 1333MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 1d
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 1e
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 1f
             slot: L3 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous internal write-through unified
     *-cache
          description: L1 cache
          physical id: 1c
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:c6500000-c74fffff ioport:a0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Whistler XT [AMD Radeon HD 6700M Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:52 memory:a0000000-afffffff memory:c6500000-c651ffff ioport:5000(size=256) memory:c6520000-c653ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:51 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:6000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:53 memory:c7504000-c750400f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c750a000-c750a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:55 memory:c7500000-c7503fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:c5500000-c64fffff ioport:c0400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 06
                serial: 08:2e:5f:7e:96:7b
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:50 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:c4500000-c54fffff ioport:c1400000(size=16777216)
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0d:00.0
                logical name: wlan0
                version: 00
                serial: 74:e5:0b:54:ff:48
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-23-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:54 memory:c4500000-c4501fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:c3500000-c44fffff ioport:c2400000(size=16777216)
           *-generic:0
                description: Unassigned class
                product: RTS5116 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:13:00.0
                logical name: scsi6
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom emulated scsi-host
                configuration: driver=rts_pstor latency=0
                resources: irq:18 memory:c3501000-c3501fff memory:c2400000-c240ffff
              *-disk
                   description: SCSI Disk
                   product: xD/SD/M.S.
                   vendor: Generic-
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/sdb
                   version: 1.00
                   serial: 3
                   capabilities: removable
                 *-medium
                      physical id: 0
                      logical name: /dev/sdb
           *-generic:1
                description: SD Host controller
                product: RTS5116 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:13:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:19 memory:c3500000-c35000ff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:c3400000-c34fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:19:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:c3400000-c3401fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:c7509000-c75093ff
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:6088(size=8) ioport:609c(size=4) ioport:6080(size=8) ioport:6098(size=4) ioport:6060(size=32) memory:c7508000-c75087ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c7506000-c75060ff ioport:6040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9750420AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0003
             serial: 5WS2C3F2
             size: 698GiB (750GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=bf410cf4
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 4c30-005b
                size: 197MiB
                capacity: 199MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2012-09-14 19:57:36 filesystem=ntfs label=SYSTEM state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 9c366342-8a63-d842-93ee-ef2104221839
                size: 569GiB
                capacity: 569GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-09-14 19:43:20 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: 560d59d5-1ae8-8d47-b175-bcdccbedb8b8
                size: 16GiB
                capacity: 16GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-05-01 01:03:31 filesystem=ntfs label=RECOVERY state=clean
           *-volume:3
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: FAT32
                serial: 281a-f4e1
                size: 94MiB
                capacity: 109MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT50N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /cdrom
             version: MP00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /cdrom
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=405a5c85 state=mounted
              *-volume UNCLAIMED
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 2
                   version: FAT12
                   serial: a1ff-1701
                   size: 15EiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat
  *-battery
       description: Lithium Ion Battery
       product: MU06055
       vendor: Conexant (Rockwell)
       physical id: 1
       slot: Primary
       capacity: 55080mWh
       configuration: voltage=10.8V
 

```

---

### Post by mörgæs on 2013-06-22
The N 1000 card should be easy to work with, an in general Intel hardware is Linux-friendly. 

If you want the 12.04-family I would recommend 12.04.2.

---

### Post by dtgee on 2013-06-22
> **mörgæs said:**
> The N 1000 card should be easy to work with, an in general Intel hardware is Linux-friendly. 

If you want the 12.04-family I would recommend 12.04.2.

Can you help me fix the problem with my wireless though? I don't have a wires right now for a wired connection I can't get the wireless to work before I install.

---

### Post by mörgæs on 2013-06-22
Third time: No, you will be better off by finding a place where you can borrow a wired connection. The card is likely to work, but it's also likely to need a few modifications after install. 

Signing out.

---

