---
title: "Natty (11.04) on T410 network issues"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by doktorOblivion on 2011-05-02
I installed natty finally on my laptop (T410 Lenovo) via an upgrade from maverick.  I tested maverick thoroughly first, since I had to perform the upgrade over the network, due to issues with natty booting from DVD.  The upgrade went fine to natty, the system came up and I was able to get on locally and install other packages, though I did notice from time to time a lag in network performance.  I installed VNC server and started it, as well as other network related services.  However, I am noticing a definite issue with the network support and I suspect the natty kernel.  The configuration looks sound, ifconfig, netstat and other functions appear to display the correct information, at least what I had with maverick (which worked).

Any ideas?   Has anyone else seen issues with natty and networking?  The glass looks okay, though I am using xfce and frankly there is nothing new there to really force me to upgrade, its just that this is a new LT and if I can cold install natty right now, it will save me an upgrade later.

Any help appreciated.

System configuration (lshw) is below, ipaddress removed to protect the guilty..:

[COLOR="Blue"]    description: Notebook
    product: 2522AP1 ()
    vendor: LENOVO
    version: ThinkPad T410
    serial: R8M9B2Z
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 family=ThinkPad T410 frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=61D31E01-50CB-11CB-B2F5-C7F60CDF5DE4
  *-core
       description: Motherboard
       product: 2522AP1
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: 1ZJJ213G5E1
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 6IET75WW (1.35 )
          date: 02/01/2011
          size: 128KiB
          capacity: 8128KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 560  @ 2.67GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          slot: None
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=4
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: burst internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: c
             slot: Internal L3 Cache
             size: 3MiB
             capacity: 8MiB
             capabilities: burst internal write-back
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
          physical id: 2a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1334 MHz (0.7 ns)
             product: M471B5773DH0-CH9
             vendor: Samsung
             physical id: 0
             serial: B302B967
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 1334MHz (0.7ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1334 MHz (0.7 ns)
             product: M471B5773DH0-CH9
             vendor: Samsung
             physical id: 1
             serial: B302B964
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 1334MHz (0.7ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          size: 1199MHz
          capacity: 1199MHz
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
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:cc000000-cdefffff ioport:ce000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT218 [NVS 3100M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:cc000000-ccffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:2000(size=128) memory:cd000000-cd07ffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:cdefc000-cdefffff
        *-communication:0 UNCLAIMED
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
             resources: memory:f2427800-f242780f
        *-communication:1
             description: Serial controller
             product: 5 Series/3400 Series Chipset KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:1800(size=8) memory:f2424000-f2424fff
        *-network
             description: Ethernet interface
             product: 82577LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 06
             serial: f0:de:f1:4d:21:88
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.12-1 ip=x.xx.xxx.xxx latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:41 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)
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
             resources: irq:23 memory:f2428000-f24283ff
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
             resources: irq:45 memory:f2420000-f2423fff
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
             resources: irq:20
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
             resources: irq:21 memory:f2000000-f20fffff
           *-network DISABLED
                description: Wireless interface
                product: Centrino Advanced-N 6200
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 35
                serial: 18:3d:a2:30:6d:cc
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic-pae firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:44 memory:f2000000-f2001fff
        *-pci:3
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
             resources: irq:23 ioport:3000(size=4096) memory:f0000000-f1ffffff ioport:f2500000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:20 memory:f2100000-f21fffff
           *-generic:0
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:0d:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f2100000-f21000ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: Memory Stick Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:0d:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f2100400-f21004ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FireWire Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.3
                bus info: pci@0000:0d:00.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:42 memory:f2100800-f2100fff
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
             resources: irq:19 memory:f2428400-f24287ff
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
             resources: irq:43 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:1840(size=32) memory:f2427000-f24277ff
           *-disk
                description: ATA Disk
                product: ST9500420AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0003
                serial: 5VJBAECJ
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00097e63
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 3fc4e36a-4bed-4233-95ea-d40deb9a2a70
                   size: 454GiB
                   capacity: 454GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-05-02 04:10:21 filesystem=ext4 lastmountpoint=/ modified=2011-05-02 04:22:18 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-05-02 11:23:13 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 11GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7930H
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.D1
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
             resources: memory:f2428800-f24288ff ioport:1860(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel ips latency=0
             resources: irq:19 memory:f2426000-f2426fff
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
  *-battery
       product: 42T4799
       vendor: SANYO
       physical id: 1
       slot: Rear
       capacity: 93240mWh
       configuration: voltage=11.1V
[/COLOR]

---

### Post by chili555 on 2011-05-02
Ooh! I love the T410! How about I tell you it's unfixable and just send it to me? No? OK, let's fix it.

I have two (out of four) machines converted to Natty. Networking is perfect on both.

Please run and post:```
rfkill list all
dmesg | grep -e wlan -e iwl
```Thanks.

---

### Post by ne0genius on 2011-05-15
ok. not to hijack this thread but I just upgraded to Natty I also have the T410 with the 6200N chipset. Ever since I upgraded the wifi has been flaky. It connects, but 5 minutes later I keep connectivity but no internet. here is my output. I only seem to have the problem on one of the routers i use but i have never had an issue prior and no other devices do. router has been rock solid for over a year never had to reboot. Buffalo WZR-HP-G3000NH running OpenWRT 10.03.

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
[    5.144442] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    5.144447] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    5.144532] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.144540] iwlagn 0000:03:00.0: setting latency timer to 64
[    5.144577] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[    5.160905] iwlagn 0000:03:00.0: device EEPROM VER=0x436, CALIB=0x6
[    5.160910] iwlagn 0000:03:00.0: Device SKU: 0Xb
[    5.160942] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    5.161032] iwlagn 0000:03:00.0: irq 43 for MSI/MSI-X
[    5.175360] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[    5.221112] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    6.039630] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.623607] wlan0: direct probe to 00:1d:73:8d:13:67 (try 1/3)
[   19.815149] wlan0: direct probe to 00:1d:73:8d:13:67 (try 2/3)
[   20.014644] wlan0: direct probe to 00:1d:73:8d:13:67 (try 3/3)
[   20.214144] wlan0: direct probe to 00:1d:73:8d:13:67 timed out
[   41.031802] wlan0: direct probe to 00:1d:73:8d:13:67 (try 1/3)
[   41.221474] wlan0: direct probe to 00:1d:73:8d:13:67 (try 2/3)
[   41.420937] wlan0: direct probe to 00:1d:73:8d:13:67 (try 3/3)
[   41.620453] wlan0: direct probe to 00:1d:73:8d:13:67 timed out
[   62.527864] wlan0: authenticate with 00:26:62:69:d1:06 (try 1)
[   62.530367] wlan0: authenticated
[   62.530534] wlan0: associate with 00:26:62:69:d1:06 (try 1)
[   62.533406] wlan0: RX AssocResp from 00:26:62:69:d1:06 (capab=0x431 status=0 aid=1)
[   62.533409] wlan0: associated
[   62.535726] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   72.782301] wlan0: no IPv6 routers present
[  461.717708] wlan0: deauthenticating from 00:26:62:69:d1:06 by local choice (reason=3)
[  462.718763] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  530.564554] wlan0: authenticate with 00:21:29:91:0a:77 (try 1)
[  530.567610] wlan0: authenticated
[  530.567669] wlan0: associate with 00:21:29:91:0a:77 (try 1)
[  530.569855] wlan0: RX AssocResp from 00:21:29:91:0a:77 (capab=0x411 status=0 aid=1)
[  530.569860] wlan0: associated
[  530.572491] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  540.755791] wlan0: no IPv6 routers present
[  721.398461] wlan0: deauthenticating from 00:21:29:91:0a:77 by local choice (reason=3)
[  724.331158] wlan0: authenticate with 00:21:29:91:0a:77 (try 1)
[  724.334009] wlan0: authenticated
[  724.334079] wlan0: associate with 00:21:29:91:0a:77 (try 1)
[  724.343200] wlan0: RX AssocResp from 00:21:29:91:0a:77 (capab=0x411 status=0 aid=1)
[  724.343205] wlan0: associated
[ 2668.722159] wlan0: deauthenticating from 00:21:29:91:0a:77 by local choice (reason=3)
[ 2669.078604] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2681.904009] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2687.367674] wlan0: direct probe to 00:1d:73:8d:13:67 (try 1/3)
[ 2687.563784] wlan0: direct probe to 00:1d:73:8d:13:67 (try 2/3)
[ 2687.763251] wlan0: direct probe to 00:1d:73:8d:13:67 (try 3/3)
[ 2687.962762] wlan0: direct probe to 00:1d:73:8d:13:67 timed out
[ 2718.007714] wlan0: authenticate with 00:26:62:69:d1:06 (try 1)
[ 2718.010440] wlan0: authenticated
[ 2718.010617] wlan0: associate with 00:26:62:69:d1:06 (try 1)
[ 2718.013518] wlan0: RX AssocResp from 00:26:62:69:d1:06 (capab=0x431 status=0 aid=1)
[ 2718.013523] wlan0: associated
[ 2718.016457] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2728.371481] wlan0: no IPv6 routers present
[ 2791.877241] wlan0: deauthenticating from 00:26:62:69:d1:06 by local choice (reason=3)
[ 2792.631143] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2814.689986] iwlagn 0000:03:00.0: Error: Response NULL in 'REPLY_ADD_STA'
[ 2814.689999] iwlagn 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed.
[ 2898.180314] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2903.811912] wlan0: direct probe to 00:1d:73:8d:13:67 (try 1/3)
[ 2904.007764] wlan0: direct probe to 00:1d:73:8d:13:67 (try 2/3)
[ 2904.207368] wlan0: direct probe to 00:1d:73:8d:13:67 (try 3/3)
[ 2904.406978] wlan0: direct probe to 00:1d:73:8d:13:67 timed out
[ 2915.762434] wlan0: authenticate with 00:26:62:69:d1:06 (try 1)
[ 2915.764985] wlan0: authenticated
[ 2915.765143] wlan0: associate with 00:26:62:69:d1:06 (try 1)
[ 2915.768086] wlan0: RX AssocResp from 00:26:62:69:d1:06 (capab=0x431 status=0 aid=1)
[ 2915.768092] wlan0: associated
[ 2915.771052] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2926.143352] wlan0: no IPv6 routers present
[ 5362.485029] wlan0: deauthenticating from 00:26:62:69:d1:06 by local choice (reason=3)
[ 5367.475127] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[ 5368.816830] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5374.420723] wlan0: authenticate with 00:26:62:69:d1:06 (try 1)
[ 5374.423239] wlan0: authenticated
[ 5374.423557] wlan0: associate with 00:26:62:69:d1:06 (try 1)
[ 5374.427699] wlan0: RX AssocResp from 00:26:62:69:d1:06 (capab=0x431 status=0 aid=1)
[ 5374.427704] wlan0: associated
[ 5374.430606] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5384.761072] wlan0: no IPv6 routers present
[ 7488.791795] wlan0: deauthenticating from 00:26:62:69:d1:06 by local choice (reason=3)
[ 7491.682303] wlan0: authenticate with 00:1d:73:8d:13:67 (try 1)
[ 7491.687106] wlan0: authenticated
[ 7491.687227] wlan0: associate with 00:1d:73:8d:13:67 (try 1)
[ 7491.691419] wlan0: RX AssocResp from 00:1d:73:8d:13:67 (capab=0x411 status=0 aid=3)
[ 7491.691426] wlan0: associated
[ 7498.716223] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:1d:73:8d:13:67 tid = 0
[ 7540.133858] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 10
[ 7546.443996] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:1d:73:8d:13:67 tid = 0
[ 7581.067627] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 1
[ 7621.850072] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:1d:73:8d:13:67 tid = 0
[ 7685.637537] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 7739.731917] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 7787.115883] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 7821.377553] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 7858.555700] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 7917.538483] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 7987.155063] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 8125.427643] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 8169.287519] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 8227.199142] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 1
[ 8276.564539] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 8291.546358] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:1d:73:8d:13:67 tid = 0
[ 8396.976769] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 8414.502122] wlan0: deauthenticating from 00:1d:73:8d:13:67 by local choice (reason=3)
[ 8417.619034] wlan0: authenticate with 00:26:62:69:d1:06 (try 1)
[ 8417.621632] wlan0: authenticated
[ 8417.621886] wlan0: associate with 00:26:62:69:d1:06 (try 1)
[ 8417.624951] wlan0: RX AssocResp from 00:26:62:69:d1:06 (capab=0x431 status=0 aid=1)
[ 8417.624959] wlan0: associated
```

---

### Post by chili555 on 2011-05-15
Congratulations! It's a known bug:  [https://bugs.launchpad.net/ubuntu/natty/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/natty/+source/linux-firmware/+bug/630748)

As mentioned in several comments, you might try disabling N speeds:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn 11n_disable50=1 11n_disable=1
```Proofread, save and close gedit. Reboot and tell us if there is any improvement.

---

### Post by ne0genius on 2011-05-15
Thanks. I will try that workaround and report back. The odd thing is that this was not an issues on maverick for me ever on this laptop and it seems that bug goes way back.

---

