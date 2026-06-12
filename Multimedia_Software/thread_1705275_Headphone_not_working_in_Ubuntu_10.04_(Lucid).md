---
title: "Headphone not working in Ubuntu 10.04 (Lucid)"
date: 2011-03-12
forum: Multimedia Software
---

### Post by azeemj on 2011-03-12
Dear all

I have dell optiplex 380 system and i am using 64 bit ubuntu 10.04 lucid but speaker has sound but headphobe has no sound here is my system info

any help wwill gratly be appriciated



[B]#uname -a
[/B]Linux desktop01 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux


**#aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**#cat /proc/asound/version **

Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Mar  2 2011 for kernel 2.6.32-30-generic (SMP).

**#head -n 1 /proc/asound/card*/codec#***

Codec: Realtek ALC259



**#lshw <<<<<** 	here is the output
 	description: Mini Tower Computer
 	product: OptiPlex 380
 	vendor: Dell Inc.
 	serial: B2RSW1S
 	width: 64 bits
 	capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
 	configuration: administrator_password=enabled boot=normal  chassis=mini-tower power-on_password=enabled  uuid=44454C4C-3200-1052-8053-C2C04F573153
 	*-core
 	description: Motherboard
 	product: 0KP561
 	vendor: Dell Inc.
 	physical id: 0
 	serial: ..CN7082185EG0IC.
 	*-firmware
 	description: BIOS
 	vendor: Dell Inc.
 	physical id: 0
 	version: A03 (02/19/2008)
 	size: 64KiB
 	capacity: 960KiB
 	capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect  edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard  int14serial int17printer acpi usb biosbootspecification netboot
 	*-cpu
 	description: CPU
 	product: Intel(R) Core(TM)2 Duo CPU E6550 @ 2.33GHz
 	vendor: Intel Corp.
 	physical id: 400
 	bus info: cpu@0
 	slot: CPU
 	size: 2333MHz
 	width: 64 bits
 	clock: 1333MHz
 	capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8  apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2  ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts  rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm  lahf_lm tpr_shadow vnmi flexpriority
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
 	*-memory
 	description: System Memory
 	physical id: 1000
 	slot: System board or motherboard
 	size: 1GiB
 	*-bank:0
 	description: DIMM Synchronous 667 MHz (1.5 ns)
 	product: M3 78T2863RZS-CE6
 	vendor: CE00000000000000
 	physical id: 0
 	serial: 2830AA84
 	slot: DIMM_1
 	size: 1GiB
 	width: 64 bits
 	clock: 667MHz (1.5ns)
 	*-bank:1
 	description: DIMM Synchronous 667 MHz (1.5 ns) [empty]
 	vendor: FFFFFFFFFFFFFFFF
 	physical id: 1
 	serial: FFFFFFFF
 	slot: DIMM_2
 	width: 64 bits
 	clock: 667MHz (1.5ns)
 	*-pci
 	description: Host bridge
 	product: 82G33/G31/P35/P31 Express DRAM Controller
 	vendor: Intel Corporation
 	physical id: 100
 	bus info: pci@0000:00:00.0
 	version: 0a
 	width: 32 bits
 	clock: 33MHz
 	configuration: driver=agpgart-intel module=intel_agp
 	*-pci:0
 	description: PCI bridge
 	product: 82G33/G31/P35/P31 Express PCI Express Root Port
 	vendor: Intel Corporation
 	physical id: 1
 	bus info: pci@0000:00:01.0
 	version: 0a
 	width: 32 bits
 	clock: 33MHz
 	capabilities: pci pm msi pciexpress bus_master cap_list
 	configuration: driver=pcieport-driver
 	*-display:0 UNCLAIMED
 	description: VGA compatible controller
 	product: 82G33/G31 Express Integrated Graphics Controller
 	vendor: Intel Corporation
 	physical id: 2
 	bus info: pci@0000:00:02.0
 	version: 0a
 	width: 32 bits
 	clock: 33MHz
 	capabilities: msi pm bus_master cap_list
 	configuration: latency=0
 	*-display:1 UNCLAIMED
 	description: Display controller
 	product: 82G33/G31 Express Integrated Graphics Controller
 	vendor: Intel Corporation
 	physical id: 2.1
 	bus info: pci@0000:00:02.1
 	version: 0a
 	width: 32 bits
 	clock: 33MHz
 	capabilities: pm bus_master cap_list
 	configuration: latency=0
 	*-multimedia
 	description: Audio device
 	product: 82801G (ICH7 Family) High Definition Audio Controller
 	vendor: Intel Corporation
 	physical id: 1b
 	bus info: pci@0000:00:1b.0
 	version: 01
 	width: 64 bits
 	clock: 33MHz
 	capabilities: pm msi pciexpress bus_master cap_list
 	configuration: driver=HDA Intel latency=0 module=snd_hda_intel
 	*-pci:1
 	description: PCI bridge
 	product: 82801G (ICH7 Family) PCI Express Port 1
 	vendor: Intel Corporation
 	physical id: 1c
 	bus info: pci@0000:00:1c.0
 	version: 01
 	width: 32 bits
 	clock: 33MHz
 	capabilities: pci pciexpress msi pm bus_master cap_list
 	configuration: driver=pcieport-driver
 	*-network
 	description: Ethernet interface
 	product: NetLink BCM5787 Gigabit Ethernet PCI Express
 	vendor: Broadcom Corporation
 	physical id: 0
 	bus info: pci@0000:02:00.0
 	logical name: eth0
 	version: 02
 	serial: 00:1e:c9:4f:71:25
 	capacity: 1GB/s
 	width: 64 bits
 	clock: 33MHz
 	capabilities: pm vpd msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
 	configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.94 firmware=5787-v3.23 latency=0 link=no module=tg3  multicast=yes port=twisted pair
 	*-usb:0
 	description: USB Controller
 	product: 82801G (ICH7 Family) USB UHCI Controller #1
 	vendor: Intel Corporation
 	physical id: 1d
 	bus info: pci@0000:00:1d.0
 	version: 01
 	width: 32 bits
 	clock: 33MHz
 	capabilities: bus_master
 	configuration: driver=uhci_hcd latency=0 module=uhci_hcd
 	*-usb:1
 	description: USB Controller
 	product: 82801G (ICH7 Family) USB UHCI Controller #2
 	vendor: Intel Corporation
 	physical id: 1d.1
 	bus info: pci@0000:00:1d.1
 	version: 01
 	width: 32 bits
 	clock: 33MHz
 	capabilities: bus_master
 	configuration: driver=uhci_hcd latency=0 module=uhci_hcd
 	*-usb:2
 	description: USB Controller
 	product: 82801G (ICH7 Family) USB UHCI Controller #3
 	vendor: Intel Corporation
 	physical id: 1d.2
 	bus info: pci@0000:00:1d.2
 	version: 01
 	width: 32 bits
 	clock: 33MHz
 	capabilities: bus_master
 	configuration: driver=uhci_hcd latency=0 module=uhci_hcd
 	*-usb:3
 	description: USB Controller
 	product: 82801G (ICH7 Family) USB UHCI Controller #4
 	vendor: Intel Corporation
 	physical id: 1d.3
 	bus info: pci@0000:00:1d.3
 	version: 01
 	width: 32 bits
 	clock: 33MHz
 	capabilities: bus_master
 	configuration: driver=uhci_hcd latency=0 module=uhci_hcd
 	*-usb:4
 	description: USB Controller
 	product: 82801G (ICH7 Family) USB2 EHCI Controller
 	vendor: Intel Corporation
 	physical id: 1d.7
 	bus info: pci@0000:00:1d.7
 	version: 01
 	width: 32 bits
 	clock: 33MHz
 	capabilities: pm debug bus_master cap_list
 	configuration: driver=ehci_hcd latency=0 module=ehci_hcd
 	*-pci:2
 	description: PCI bridge
 	product: 82801 PCI Bridge
 	vendor: Intel Corporation
 	physical id: 1e
 	bus info: pci@0000:00:1e.0
 	version: e1
 	width: 32 bits
 	clock: 33MHz
 	capabilities: pci bus_master cap_list
 	*-network
 	description: Wireless interface
 	product: RT2561/RT61 rev B 802.11g
 	vendor: RaLink
 	physical id: 2
 	bus info: pci@0000:03:02.0
 	logical name: wmaster0
 	version: 00
 	serial: 00:21:91:7d:c3:c9
 	width: 32 bits
 	clock: 33MHz
 	capabilities: pm bus_master cap_list logical ethernet physical wireless
 	configuration: broadcast=yes driver=rt61pci ip=0.0.0.0 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg
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
 	product: 82801G (ICH7 Family) IDE Controller
 	vendor: Intel Corporation
 	physical id: 1f.1
 	bus info: pci@0000:00:1f.1
 	version: 01
 	width: 32 bits
 	clock: 33MHz
 	capabilities: ide bus_master
 	configuration: driver=ata_piix latency=0
 	*-storage
 	description: SATA controller
 	product: 82801GR/GH (ICH7 Family) SATA AHCI Controller
 	vendor: Intel Corporation
 	physical id: 1f.2
 	bus info: pci@0000:00:1f.2
 	logical name: scsi0
 	logical name: scsi1
 	logical name: scsi2
 	version: 01
 	width: 32 bits
 	clock: 66MHz
 	capabilities: storage msi pm bus_master cap_list emulated
 	configuration: driver=ahci latency=0 module=ahci
 	*-disk:0
 	description: ATA Disk
 	product: WDC WD800JD-75MS
 	vendor: Western Digital
 	physical id: 0
 	bus info: scsi@0:0.0.0
 	logical name: /dev/sda
 	version: 10.0
 	serial: WD-WMAM9CKC0942
 	size: 74GiB (80GB)
 	capabilities: partitioned partitioned:dos
 	configuration: ansiversion=5 signature=000b6688
 	*-volume:0
 	description: EXT3 volume
 	vendor: Linux
 	physical id: 1
 	bus info: scsi@0:0.0.0,1
 	logical name: /dev/sda1
 	logical name: /
 	version: 1.0
 	serial: c4b60e7e-210a-4afa-8316-9c95d274c0cf
 	size: 71GiB
 	capacity: 71GiB
 	capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
 	configuration: created=2009-05-26 10:00:50 filesystem=ext3  modified=2011-01-29 07:59:04 mount.fstype=ext3  mount.options=rw,relatime,errors=remount-ro,data=ordered  mounted=2011-01-29 07:59:04 state=mounted
 	*-volume:1
 	description: Extended partition
 	physical id: 2
 	bus info: scsi@0:0.0.0,2
 	logical name: /dev/sda2
 	size: 3153MiB
 	capacity: 3153MiB
 	capabilities: primary extended partitioned partitioned:extended
 	*-logicalvolume
 	description: Linux swap / Solaris partition
 	physical id: 5
 	logical name: /dev/sda5
 	capacity: 3153MiB
 	capabilities: nofs
 	*-disk:1
 	description: ATA Disk
 	product: WDC WD800JD-75MS
 	vendor: Western Digital
 	physical id: 1
 	bus info: scsi@1:0.0.0
 	logical name: /dev/sdb
 	version: 10.0
 	serial: WD-WMAM9CKP5750
 	size: 74GiB (80GB)
 	capabilities: partitioned partitioned:dos
 	configuration: ansiversion=5 signature=00008ab6
 	*-volume
 	description: EXT3 volume
 	vendor: Linux
 	physical id: 1
 	bus info: scsi@1:0.0.0,1
 	logical name: /dev/sdb1
 	version: 1.0
 	serial: e593edf1-84f4-4eeb-b475-9d28883e82c9
 	size: 74GiB
 	capacity: 74GiB
 	capabilities: primary journaled ext3 ext2 initialized
 	configuration: created=2008-09-17 20:03:28 filesystem=ext3 modified=2010-09-29 12:03:44 mounted=2010-09-29 12:03:44 state=clean
 	*-cdrom
 	description: DVD reader
 	product: CDRWDVD TS-H493B
 	vendor: TSSTcorp
 	physical id: 0.0.0
 	bus info: scsi@2:0.0.0
 	logical name: /dev/cdrom3
 	logical name: /dev/cdrw3
 	logical name: /dev/dvd3
 	logical name: /dev/scd0
 	logical name: /dev/sr0
 	version: D200
 	capabilities: removable audio cd-r cd-rw dvd
 	configuration: ansiversion=5 status=nodisc
 	*-serial UNCLAIMED
 	description: SMBus
 	product: 82801G (ICH7 Family) SMBus Controller
 	vendor: Intel Corporation
 	physical id: 1f.3
 	bus info: pci@0000:00:1f.3
 	version: 01
 	width: 32 bits
 	clock: 33MHz
 	configuration: latency=0
 	*-network DISABLED
 	description: Ethernet interface
 	physical id: 1
 	logical name: pan0
 	serial: 82:91:19:e2:21:b9
 	capabilities: ethernet physical
 	configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes




:popcorn::KS:D:o:(

---

