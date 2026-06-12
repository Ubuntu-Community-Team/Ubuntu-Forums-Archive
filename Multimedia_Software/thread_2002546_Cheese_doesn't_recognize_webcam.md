---
title: "Cheese doesn't recognize webcam"
date: 2012-06-12
forum: Multimedia Software
---

### Post by AmadeusOK on 2012-06-12
The built-in webcam is not working with Cheese. I get the message 'No device found'. Last time I used it, more than 2 years ago, it worked just fine. Any help would be appreciated.

---

### Post by hansdown on 2012-06-12
Hi AmadeusOK.

Can you please post back with the make and model, and which version of ubuntu you are running?

Also, post the output of

```
sudo lshw
```

Thanks.

---

### Post by AmadeusOK on 2012-06-13
Thanks for replying to my post. My laptop is a Pangolin Performance pan7 running Ubuntu 10.10 64-bit. The output of 'lshw' is

```
          physical id: 4
          bus info: cpu@0
          version: Genuine Intel(R) CPU
          slot: CPU 1
          size: 2133MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: burst internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 3MiB
             capacity: 8MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: 78.A2GC6.9L1&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
             vendor: 017A
             physical id: 0
             serial: 02309503
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: 78.A2GC6.BS1&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
             vendor: 017A
             physical id: 1
             serial: 02309273
             slot: M2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: SODIMM Synchronous [empty]
             physical id: 2
             slot: M3
        *-bank:3
             description: SODIMM Synchronous [empty]
             physical id: 3
             slot: M4
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 12
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:cfe00000-cfefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M92 [Mobility Radeon HD 4500 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:16 memory:d0000000-dfffffff ioport:2000(size=256) memory:cfef0000-cfefffff memory:cfe00000-cfe1ffff
           *-multimedia
                description: Audio device
                product: RV710/730
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:48 memory:cfeec000-cfeeffff
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f0704000-f070400f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f0706000-f07063ff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:f0700000-f0703fff
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
             resources: irq:41 ioport:5000(size=4096) memory:c0100000-c02fffff ioport:c0300000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:f0200000-f02fffff ioport:f0000000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:6000(size=4096) memory:f0300000-f03fffff ioport:c0500000(size=2097152)
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 00
                serial: 00:24:d6:5f:07:08
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-32-generic firmware=8.83.5.1 build 33692 ip=10.198.117.129 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:47 memory:f0300000-f0301fff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:4000(size=4096) memory:f0400000-f04fffff ioport:c0700000(size=2097152)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f0404000-f04040ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:07:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f0405000-f04050ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:07:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:17 memory:f0406000-f04060ff
           *-network
                description: Ethernet interface
                product: JMC250 PCI Express Gigabit Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0.5
                bus info: pci@0000:07:00.5
                logical name: eth1
                version: 03
                serial: 00:90:f5:9f:cf:b2
                size: 10MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.6 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:49 memory:f0400000-f0403fff ioport:4400(size=128) ioport:4000(size=256)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0707000-f07073ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
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
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
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
             resources: irq:45 ioport:1830(size=8) ioport:1824(size=4) ioport:1828(size=8) ioport:1820(size=4) ioport:1800(size=32) memory:f0708000-f07087ff
           *-disk
                description: ATA Disk
                product: WDC WD5000BEVT-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXG0AA9H0921
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00068c1c
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 2c20b79b-bb2c-4422-9d48-d1cc487b189f
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary bootable journaled recover ext3 ext2 initialized
                   configuration: created=2010-01-02 03:57:18 filesystem=ext3 modified=2012-04-22 08:54:54 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=5,barrier=0,data=ordered mounted=2012-05-30 20:29:06 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 4dcb7a74-0f73-4f1f-9215-a1dcef29549e
                   size: 3648MiB
                   capacity: 3648MiB
                   capabilities: primary swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 46ad1127-89ed-4d27-886e-3ad3898f9243
                   size: 448GiB
                   capacity: 448GiB
                   capabilities: primary journaled large_files recover ext3 ext2 initialized
                   configuration: created=2010-01-02 03:57:24 filesystem=ext3 modified=2012-05-30 20:29:06 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,commit=5,barrier=0,data=ordered mounted=2012-05-30 20:29:06 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T50N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RH03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             resources: memory:f0709000-f07090ff ioport:1840(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@2:1.2
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Dell Memory Key
             vendor: M-SysT5
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdb
             version: 5.00
             serial: u
             size: 243MiB (255MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 243MiB (255MB)
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Windows FAT volume
                   vendor: DOK01.01
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/USB MEMORY
                   version: FAT16
                   serial: 2167-9256
                   size: 243MiB
                   capacity: 243MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=USB MEMORY mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-power UNCLAIMED
       description: To Be Defined By O.E.M
       product: To Be Defined By O.E.M
       vendor: To Be Defined By O.E.M
       physical id: 1
       version: 2.50
       serial: To Be Defined By O.E.M
       capacity: 32768mWh

```

---

### Post by hansdown on 2012-06-13
If you click 

```
edit>preferences
```

Does your cam show under device?

---

### Post by AmadeusOK on 2012-06-13
I cannot click on Preferences because it's not activated.

---

### Post by hansdown on 2012-06-13
> **AmadeusOK said:**
> I cannot click on Preferences because it's not activated.

May I ask how cheese was installed?

eg: software center, synaptic, ppa.

---

### Post by AmadeusOK on 2012-06-13
It was pre-installed when I bought the laptop. As I said before I used the webcam long ago and it worked fine. Stopped using it and forgot about it. I upgraded the system at least once since then.

---

### Post by hansdown on 2012-06-13
Two things come to mind.

Update drivers, and/or reinstall cheese.

---

### Post by AmadeusOK on 2012-06-14
Thanks a lot for your help. I tried to update drivers and reinstall Cheese. But there were some errors in the configuration files. So out of frustration I decided to make a fresh install of Ubuntu (which was long overdue). After that everything is working fine again including the webcam.

Thanks again and have a good one!

---

### Post by hansdown on 2012-06-14
Glad you fixed it,AmadeusOK.

The upgrade option sometimes borks things.

Good job.

---

