---
title: "Acer E1-531 webcams are not working"
date: 2015-01-18
forum: Multimedia Software
---

### Post by Berduchwal on 2015-01-18
This model as in integrated webcam which worked a while back but then stopped. I have now connected 3 different working webcams all of which were tested on another Ubuntu PC and worked. Sadly none of them do work. Some diagnosis below. Please let me know what can I do to fix this.


```
lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

```

```
lsusb
Bus 002 Device 009: ID 058f:3880 Alcor Micro Corp. 
Bus 002 Device 010: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam
Bus 002 Device 008: ID 18ec:3288 Arkmicro Technologies Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation BCM57765/57785 MS Card Reader (rev 10)
02:00.3 System peripheral: Broadcom Corporation BCM57765/57785 xD-Picture Card Reader (rev 10)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

```

```
sudo lshw -sanitize > lshw.txt
computer
    description: Notebook
    product: Easy Note TE (Easy Note TE_0649_V2.14)
    vendor: Packard Bell
    version: V2.14
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: chassis=notebook family=Type1Family sku=Easy Note TE_0649_V2.14 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: EA50_HC_HR
       vendor: Packard Bell
       physical id: 0
       version: Type2 - Board Version
       serial: [REMOVED]
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: V2.14
          date: 02/19/2013
          size: 128KiB
          capacity: 3520KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU B960 @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU B960 @ 2.20GHz
          serial: [REMOVED]
          slot: U3E1
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm arat epb xsaveopt pln pts dtherm cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: d
             slot: L3 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: a
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: EBJ40UG8BBU0-GN-F
             vendor: ELPIDA
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: EBJ40UG8BBU0-GN-F
             vendor: ELPIDA
             physical id: 2
             serial: [REMOVED]
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 3
             serial: [REMOVED]
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
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
             resources: irq:43 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:2000(size=64)
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:41 memory:c0604000-c060400f
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:c0609000-c06093ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:c0600000-c0603fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:afb00000-afbfffff ioport:c0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: NetLink BCM57785 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=sb latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
           *-generic:0
                description: SD Host controller
                product: BCM57765/57785 SDXC/MMC Card Reader
                vendor: Broadcom Corporation
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:c0400000-c040ffff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: BCM57765/57785 MS Card Reader
                vendor: Broadcom Corporation
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:c0410000-c041ffff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: BCM57765/57785 xD-Picture Card Reader
                vendor: Broadcom Corporation
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:c0420000-c042ffff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:c0500000-c05fffff ioport:afc00000(size=1048576)
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.13.0-44-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:c0500000-c057ffff memory:afc00000-afc0ffff
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:c0608000-c06083ff
        *-isa
             description: ISA bridge
             product: 7 Series Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:2088(size=8) ioport:2094(size=4) ioport:2080(size=8) ioport:2090(size=4) ioport:2060(size=32) memory:c0607000-c06077ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0605000-c06050ff ioport:2040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54505
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: GG2O
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0001765a
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 457GiB
                capacity: 457GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-04-18 12:53:50 filesystem=ext4 lastmountpoint=/ modified=2015-01-18 08:52:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-01-18 08:52:33 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 8007MiB
                capacity: 8007MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8007MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT51N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

```
 cheese
libv4l2: error turning on stream: Brak miejsca na urz&#261;dzeniu

(cheese:6070): cheese-WARNING **: Wewn&#281;trzny b&#322;&#261;d przep&#322;ywu danych.: gstbasesrc.c(2865): gst_base_src_loop (): /GstCameraBin:camerabin/GstWrapperCameraBinSrc:camera_source/GstBin:bin17/GstV4l2Src:video_source:
streaming task paused, reason not-negotiated (-4)
```

---

### Post by westie457 on 2015-01-18
Hello Berduchwal, the first part of the error> [COLOR=#000000][FONT=Ubuntu Mono]cheese
[/FONT][/COLOR]libv4l2: error turning on stream: Brak miejsca na urz&#261;dzeniu
Google translate reports this as "No room on device" and is probably the cause of the second error - Wewn&#281;trzny b&#322;&#261;d przep&#322;ywu danych (Internal data flow error).

Could you post the results of ```
df -h
df -i
``` to give us a starting point to help fix this.

---

### Post by Berduchwal on 2015-01-18
Thank you for your answer. 

Please see outcomes of commands asked for.

```
df -h
/dev/sda1       451G   22G  407G   6% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            3,8G  4,0K  3,8G   1% /dev
tmpfs           781M  1,1M  780M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,9G   80K  3,9G   1% /run/shm
none            100M   32K  100M   1% /run/user

```

```
df -i
/dev/sda1      30015488 347573 29667915    2% /
none             998778      2   998776    1% /sys/fs/cgroup
udev             996081    467   995614    1% /dev
tmpfs            998778    463   998315    1% /run
none             998778      3   998775    1% /run/lock
none             998778      5   998773    1% /run/shm
none             998778     24   998754    1% /run/user

```

---

### Post by westie457 on 2015-01-19
Well, there was me thinking it was a hard drive space issue. Now it obviously is not that.

After a small amount of searching on the error message this was found. [http://superuser.com/questions/431759/using-multiple-usb-webcams-in-linux](http://superuser.com/questions/431759/using-multiple-usb-webcams-in-linux)

Hope this is helpful.

---

