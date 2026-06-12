---
title: "no more wi-fi after upgrade to 12.04"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by YannT on 2012-09-19
Hi, 

I upgraded from 11.04 to 11.10 my Acer Aspire 7745G the wi-fi that was running fine in 11.04 started to disconnect very often.

I then decided to upgrade to 12.04 and the wi-fi does not work at all. in system parameters / additional drivers it says that there is a Broadcom STA available but it fails to activate when I try.

Could not find a solution on french forum so I post here.

here is the result of iwconfig, ifconfig and lshw :
```

yann@ERERDU:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

yann@ERERDU:~$ ifconfig
eth0 Link encap:Ethernet HWaddr c8:0a:a9:5e:ca:31 
inet adr:192.168.0.45 Bcast:192.168.0.255 Masque:255.255.255.0
adr inet6: fe80::ca0a:a9ff:fe5e:ca31/64 Scope:Lien
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Packets reçus:61252 erreurs:0 :0 overruns:0 frame:0
TX packets:44105 errors:0 dropped:0 overruns:0 carrier:1
collisions:0 lg file transmission:1000 
Octets reçus:82419778 (82.4 MB) Octets transmis:4976900 (4.9 MB)
Interruption:50

lo Link encap:Boucle locale 
inet adr:127.0.0.1 Masque:255.0.0.0
adr inet6: ::1/128 Scope:Hôte
UP LOOPBACK RUNNING MTU:16436 Metric:1
Packets reçus:979 erreurs:0 :0 overruns:0 frame:0
TX packets:979 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 lg file transmission:0 
Octets reçus:114077 (114.0 KB) Octets transmis:114077 (114.0 KB)

---------------

ererdu
description: Ordinateur Bloc-notes
produit: Aspire 7745G ()
fabriquant: Acer
version: Not Applicable
numéro de série: LXPUM0210602309FE92500
bits: 32 bits
fonctionnalités: smbios-2.6 dmi-2.6 smp-1.4 smp
configuration: administrator_password=disabled boot=normal chassis=notebook cpus=4 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=CAA0BEF7-262A-43F7-B7D5-C80AA95ECA31
*-core
description: Carte mère
produit: JV71-CP
fabriquant: Acer
identifiant matériel: 0
version: Not Applicable
numéro de série: 014IZXMBQTF00617
*-firmware
description: BIOS
fabriquant: Phoenix
identifiant matériel: 0
version: V1.03
date: 04/27/2010
taille: 113KiB
capacité: 960KiB
fonctionnalités: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
*-cpu:0
description: CPU
produit: Intel(R) Core(TM) i7 CPU Q 720 @ 1.60GHz
fabriquant: Intel Corp.
identifiant matériel: 4
information bus: cpu@0
version: 6.14.5
numéro de série: 0001-06E5-0000-0000-0000-0000
emplacement: CPU 1
taille: 933MHz
capacité: 3200MHz
bits: 64 bits
horloge: 133MHz
fonctionnalités: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
configuration: cores=4 enabledcores=4 id=1 threads=8
*-cache:0
description: L1 cache
identifiant matériel: 5
emplacement: L1 Cache
taille: 64KiB
capacité: 64KiB
fonctionnalités: asynchronous internal write-through data
*-cache:1
description: L2 cache
identifiant matériel: 6
emplacement: L2 Cache
taille: 256KiB
capacité: 4MiB
fonctionnalités: burst internal write-through unified
*-cache:2
description: L3 cache
identifiant matériel: 7
emplacement: L3 Cache
taille: 6MiB
capacité: 8MiB
fonctionnalités: burst internal write-back
*-logicalcpu:0
description: CPU Logique
identifiant matériel: 1.1
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:1
description: CPU Logique
identifiant matériel: 1.2
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:2
description: CPU Logique
identifiant matériel: 1.3
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:3
description: CPU Logique
identifiant matériel: 1.4
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:4
description: CPU Logique
identifiant matériel: 1.5
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:5
description: CPU Logique
identifiant matériel: 1.6
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:6
description: CPU Logique
identifiant matériel: 1.7
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:7
description: CPU Logique
identifiant matériel: 1.8
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:8
description: CPU Logique
identifiant matériel: 1.9
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:9
description: CPU Logique
identifiant matériel: 1.a
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:10
description: CPU Logique
identifiant matériel: 1.b
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:11
description: CPU Logique
identifiant matériel: 1.c
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:12
description: CPU Logique
identifiant matériel: 1.d
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:13
description: CPU Logique
identifiant matériel: 1.e
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:14
description: CPU Logique
identifiant matériel: 1.f
bits: 64 bits
fonctionnalités: logical
*-logicalcpu:15
description: CPU Logique
identifiant matériel: 1.10
bits: 64 bits
fonctionnalités: logical
*-memory
description: Mémoire Système
identifiant matériel: 10
emplacement: Carte mère
taille: 8GiB
*-bank:0
description: SODIMM DDR3 Synchrone 667 MHz (1,5 ns)
produit: M471B5673FH0-CH9
fabriquant: Samsung
identifiant matériel: 0
numéro de série: 95CC4B4F
emplacement: M1
taille: 2GiB
bits: 64 bits
horloge: 667MHz (1.5ns)
*-bank:1
description: SODIMM DDR3 Synchrone 667 MHz (1,5 ns)
produit: M471B5673FH0-CH9
fabriquant: Samsung
identifiant matériel: 1
numéro de série: 95CC4B11
emplacement: M2
taille: 2GiB
bits: 64 bits
horloge: 667MHz (1.5ns)
*-bank:2
description: SODIMM DDR3 Synchrone 667 MHz (1,5 ns)
produit: M471B5673FH0-CH9
fabriquant: Samsung
identifiant matériel: 2
numéro de série: 95CC4B11
emplacement: M3
taille: 2GiB
bits: 64 bits
horloge: 667MHz (1.5ns)
*-bank:3
description: SODIMM DDR3 Synchrone 667 MHz (1,5 ns)
produit: M471B5673FH0-CH9
fabriquant: Samsung
identifiant matériel: 3
numéro de série: 95CC4B11
emplacement: M4
taille: 2GiB
bits: 64 bits
horloge: 667MHz (1.5ns)
*-cpu:1
identifiant matériel: 1
information bus: cpu@1
version: 6.14.5
numéro de série: 0001-06E5-0000-0000-0000-0000
taille: 933MHz
capacité: 933MHz
fonctionnalités: vmx ht cpufreq
configuration: id=1
*-logicalcpu:0
description: CPU Logique
identifiant matériel: 1.1
fonctionnalités: logical
*-logicalcpu:1
description: CPU Logique
identifiant matériel: 1.2
fonctionnalités: logical
*-logicalcpu:2
description: CPU Logique
identifiant matériel: 1.3
fonctionnalités: logical
*-logicalcpu:3
description: CPU Logique
identifiant matériel: 1.4
fonctionnalités: logical
*-logicalcpu:4
description: CPU Logique
identifiant matériel: 1.5
fonctionnalités: logical
*-logicalcpu:5
description: CPU Logique
identifiant matériel: 1.6
fonctionnalités: logical
*-logicalcpu:6
description: CPU Logique
identifiant matériel: 1.7
fonctionnalités: logical
*-logicalcpu:7
description: CPU Logique
identifiant matériel: 1.8
fonctionnalités: logical
*-logicalcpu:8
description: CPU Logique
identifiant matériel: 1.9
fonctionnalités: logical
*-logicalcpu:9
description: CPU Logique
identifiant matériel: 1.a
fonctionnalités: logical
*-logicalcpu:10
description: CPU Logique
identifiant matériel: 1.b
fonctionnalités: logical
*-logicalcpu:11
description: CPU Logique
identifiant matériel: 1.c
fonctionnalités: logical
*-logicalcpu:12
description: CPU Logique
identifiant matériel: 1.d
fonctionnalités: logical
*-logicalcpu:13
description: CPU Logique
identifiant matériel: 1.e
fonctionnalités: logical
*-logicalcpu:14
description: CPU Logique
identifiant matériel: 1.f
fonctionnalités: logical
*-logicalcpu:15
description: CPU Logique
identifiant matériel: 1.10
fonctionnalités: logical
*-cpu:2
identifiant matériel: 2
information bus: cpu@2
version: 6.14.5
numéro de série: 0001-06E5-0000-0000-0000-0000
taille: 933MHz
capacité: 933MHz
fonctionnalités: vmx ht cpufreq
configuration: id=1
*-logicalcpu:0
description: CPU Logique
identifiant matériel: 1.1
fonctionnalités: logical
*-logicalcpu:1
description: CPU Logique
identifiant matériel: 1.2
fonctionnalités: logical
*-logicalcpu:2
description: CPU Logique
identifiant matériel: 1.3
fonctionnalités: logical
*-logicalcpu:3
description: CPU Logique
identifiant matériel: 1.4
fonctionnalités: logical
*-logicalcpu:4
description: CPU Logique
identifiant matériel: 1.5
fonctionnalités: logical
*-logicalcpu:5
description: CPU Logique
identifiant matériel: 1.6
fonctionnalités: logical
*-logicalcpu:6
description: CPU Logique
identifiant matériel: 1.7
fonctionnalités: logical
*-logicalcpu:7
description: CPU Logique
identifiant matériel: 1.8
fonctionnalités: logical
*-logicalcpu:8
description: CPU Logique
identifiant matériel: 1.9
fonctionnalités: logical
*-logicalcpu:9
description: CPU Logique
identifiant matériel: 1.a
fonctionnalités: logical
*-logicalcpu:10
description: CPU Logique
identifiant matériel: 1.b
fonctionnalités: logical
*-logicalcpu:11
description: CPU Logique
identifiant matériel: 1.c
fonctionnalités: logical
*-logicalcpu:12
description: CPU Logique
identifiant matériel: 1.d
fonctionnalités: logical
*-logicalcpu:13
description: CPU Logique
identifiant matériel: 1.e
fonctionnalités: logical
*-logicalcpu:14
description: CPU Logique
identifiant matériel: 1.f
fonctionnalités: logical
*-logicalcpu:15
description: CPU Logique
identifiant matériel: 1.10
fonctionnalités: logical
*-cpu:3
identifiant matériel: 3
information bus: cpu@3
version: 6.14.5
numéro de série: 0001-06E5-0000-0000-0000-0000
taille: 933MHz
capacité: 933MHz
fonctionnalités: vmx ht cpufreq
configuration: id=1
*-logicalcpu:0
description: CPU Logique
identifiant matériel: 1.1
fonctionnalités: logical
*-logicalcpu:1
description: CPU Logique
identifiant matériel: 1.2
fonctionnalités: logical
*-logicalcpu:2
description: CPU Logique
identifiant matériel: 1.3
fonctionnalités: logical
*-logicalcpu:3
description: CPU Logique
identifiant matériel: 1.4
fonctionnalités: logical
*-logicalcpu:4
description: CPU Logique
identifiant matériel: 1.5
fonctionnalités: logical
*-logicalcpu:5
description: CPU Logique
identifiant matériel: 1.6
fonctionnalités: logical
*-logicalcpu:6
description: CPU Logique
identifiant matériel: 1.7
fonctionnalités: logical
*-logicalcpu:7
description: CPU Logique
identifiant matériel: 1.8
fonctionnalités: logical
*-logicalcpu:8
description: CPU Logique
identifiant matériel: 1.9
fonctionnalités: logical
*-logicalcpu:9
description: CPU Logique
identifiant matériel: 1.a
fonctionnalités: logical
*-logicalcpu:10
description: CPU Logique
identifiant matériel: 1.b
fonctionnalités: logical
*-logicalcpu:11
description: CPU Logique
identifiant matériel: 1.c
fonctionnalités: logical
*-logicalcpu:12
description: CPU Logique
identifiant matériel: 1.d
fonctionnalités: logical
*-logicalcpu:13
description: CPU Logique
identifiant matériel: 1.e
fonctionnalités: logical
*-logicalcpu:14
description: CPU Logique
identifiant matériel: 1.f
fonctionnalités: logical
*-logicalcpu:15
description: CPU Logique
identifiant matériel: 1.10
fonctionnalités: logical
*-pci:0
description: Host bridge
produit: Core Processor DMI
fabriquant: Intel Corporation
identifiant matériel: 100
information bus: pci@0000:00:00.0
version: 11
bits: 32 bits
horloge: 33MHz
*-pci:0
description: PCI bridge
produit: Core Processor PCI Express Root Port 1
fabriquant: Intel Corporation
identifiant matériel: 3
information bus: pci@0000:00:03.0
version: 11
bits: 32 bits
horloge: 33MHz
fonctionnalités: pci msi pciexpress pm normal_decode bus_master cap_list
configuration: driver=pcieport
ressources: irq:16 portE/S:2000(taille=4096) mémoire:f8100000-f81fffff portE/S:f0000000(taille=13421772
*-display
description: VGA compatible controller
produit: Broadway PRO [Mobility Radeon HD 5800 Series]
fabriquant: Hynix Semiconductor (Hyundai Electronics)
identifiant matériel: 0
information bus: pci@0000:01:00.0
version: 00
bits: 64 bits
horloge: 33MHz
fonctionnalités: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
ressources: irq:46 mémoire:f0000000-f7ffffff mémoire:f8100000-f811ffff portE/S:2000(taille=256) mémoire:f8140000-f815ffff
*-multimedia
description: Audio device
produit: Juniper HDMI Audio [Radeon HD 5700 Series]
fabriquant: Hynix Semiconductor (Hyundai Electronics)
identifiant matériel: 0.1
information bus: pci@0000:01:00.1
version: 00
bits: 64 bits
horloge: 33MHz
fonctionnalités: pm pciexpress msi bus_master cap_list
configuration: driver=snd_hda_intel latency=0
ressources: irq:49 mémoire:f8120000-f8123fff
*-generic:0 NON-RÉCLAMÉ
description: System peripheral
produit: Core Processor System Management Registers
fabriquant: Intel Corporation
identifiant matériel: 8
information bus: pci@0000:00:08.0
version: 11
bits: 32 bits
horloge: 33MHz
fonctionnalités: pciexpress cap_list
configuration: latency=0
*-generic:1 NON-RÉCLAMÉ
description: System peripheral
produit: Core Processor Semaphore and Scratchpad Registers
fabriquant: Intel Corporation
identifiant matériel: 8.1
information bus: pci@0000:00:08.1
version: 11
bits: 32 bits
horloge: 33MHz
fonctionnalités: pciexpress cap_list
configuration: latency=0
*-generic:2 NON-RÉCLAMÉ
description: System peripheral
produit: Core Processor System Control and Status Registers
fabriquant: Intel Corporation
identifiant matériel: 8.2
information bus: pci@0000:00:08.2
version: 11
bits: 32 bits
horloge: 33MHz
fonctionnalités: pciexpress cap_list
configuration: latency=0
*-generic:3 NON-RÉCLAMÉ
description: System peripheral
produit: Core Processor Miscellaneous Registers
fabriquant: Intel Corporation
identifiant matériel: 8.3
information bus: pci@0000:00:08.3
version: 11
bits: 32 bits
horloge: 33MHz
configuration: latency=0
*-generic:4 NON-RÉCLAMÉ
description: System peripheral
produit: Core Processor QPI Link
fabriquant: Intel Corporation
identifiant matériel: 10
information bus: pci@0000:00:10.0
version: 11
bits: 32 bits
horloge: 33MHz
configuration: latency=0
*-generic:5 NON-RÉCLAMÉ
description: System peripheral
produit: Core Processor QPI Routing and Protocol Registers
fabriquant: Intel Corporation
identifiant matériel: 10.1
information bus: pci@0000:00:10.1
version: 11
bits: 32 bits
horloge: 33MHz
configuration: latency=0
*-communication
description: Communication controller
produit: 5 Series/3400 Series Chipset HECI Controller
fabriquant: Intel Corporation
identifiant matériel: 16
information bus: pci@0000:00:16.0
version: 06
bits: 64 bits
horloge: 33MHz
fonctionnalités: pm msi bus_master cap_list
configuration: driver=mei latency=0
ressources: irq:47 mémoire:f8505800-f850580f
*-usb:0
description: USB controller
produit: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
fabriquant: Intel Corporation
identifiant matériel: 1a
information bus: pci@0000:00:1a.0
version: 06
bits: 32 bits
horloge: 33MHz
fonctionnalités: pm debug ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0
ressources: irq:16 mémoire:f8506000-f85063ff
*-multimedia
description: Audio device
produit: 5 Series/3400 Series Chipset High Definition Audio
fabriquant: Intel Corporation
identifiant matériel: 1b
information bus: pci@0000:00:1b.0
version: 06
bits: 64 bits
horloge: 33MHz
fonctionnalités: pm msi pciexpress bus_master cap_list
configuration: driver=snd_hda_intel latency=0
ressources: irq:48 mémoire:f8500000-f8503fff
*-pci:1
description: PCI bridge
produit: 5 Series/3400 Series Chipset PCI Express Root Port 1
fabriquant: Intel Corporation
identifiant matériel: 1c
information bus: pci@0000:00:1c.0
version: 06
bits: 32 bits
horloge: 33MHz
fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
configuration: driver=pcieport
ressources: irq:16 portE/S:3000(taille=4096) mémoire:f8000000-f80fffff portE/S:c0300000(taille=2097152)
*-network
description: Ethernet interface
produit: AR8151 v1.0 Gigabit Ethernet
fabriquant: Atheros Communications Inc.
identifiant matériel: 0
information bus: pci@0000:02:00.0
nom logique: eth0
version: c0
numéro de série: c8:0a:a9:5e:ca:31
taille: 1Gbit/s
capacité: 1Gbit/s
bits: 64 bits
horloge: 33MHz
fonctionnalités: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.45 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
ressources: irq:50 mémoire:f8000000-f803ffff portE/S:3000(taille=12
*-pci:2
description: PCI bridge
produit: 5 Series/3400 Series Chipset PCI Express Root Port 6
fabriquant: Intel Corporation
identifiant matériel: 1c.5
information bus: pci@0000:00:1c.5
version: 06
bits: 32 bits
horloge: 33MHz
fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
configuration: driver=pcieport
ressources: irq:17 portE/S:4000(taille=4096) mémoire:f8200000-f82fffff portE/S:c0100000(taille=2097152)
*-network NON-RÉCLAMÉ
description: Network controller
produit: BCM43225 802.11b/g/n
fabriquant: Broadcom Corporation
identifiant matériel: 0
information bus: pci@0000:09:00.0
version: 01
bits: 64 bits
horloge: 33MHz
fonctionnalités: pm msi pciexpress bus_master cap_list
configuration: latency=0
ressources: mémoire:f8200000-f8203fff
*-usb:1
description: USB controller
produit: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
fabriquant: Intel Corporation
identifiant matériel: 1d
information bus: pci@0000:00:1d.0
version: 06
bits: 32 bits
horloge: 33MHz
fonctionnalités: pm debug ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0
ressources: irq:23 mémoire:f8506400-f85067ff
*-pci:3
description: PCI bridge
produit: 82801 Mobile PCI Bridge
fabriquant: Intel Corporation
identifiant matériel: 1e
information bus: pci@0000:00:1e.0
version: a6
bits: 32 bits
horloge: 33MHz
fonctionnalités: pci subtractive_decode bus_master cap_list
*-isa
description: ISA bridge
produit: Mobile 5 Series Chipset LPC Interface Controller
fabriquant: Intel Corporation
identifiant matériel: 1f
information bus: pci@0000:00:1f.0
version: 06
bits: 32 bits
horloge: 33MHz
fonctionnalités: isa bus_master cap_list
configuration: latency=0
*-storage
description: SATA controller
produit: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
fabriquant: Intel Corporation
identifiant matériel: 1f.2
information bus: pci@0000:00:1f.2
nom logique: scsi0
nom logique: scsi1
nom logique: scsi5
version: 06
bits: 32 bits
horloge: 66MHz
fonctionnalités: storage msi pm ahci_1.0 bus_master cap_list emulated
configuration: driver=ahci latency=0
ressources: irq:45 portE/S:1830(taille= portE/S:1824(taille=4) portE/S:1828(taille= portE/S:1820(taille=4) portE/S:1800(taille=32) mémoire:f8505000-f85057ff
*-disk:0
description: ATA Disk
produit: WDC WD5000BEVT-2
fabriquant: Western Digital
identifiant matériel: 0
information bus: scsi@0:0.0.0
nom logique: /dev/sda
version: 01.0
numéro de série: WD-WXH1A40U0645
taille: 465GiB (500GB)
fonctionnalités: partitioned partitioned:dos
configuration: ansiversion=5 signature=26a4d0c2
*-volume:0
description: Windows NTFS volume
identifiant matériel: 1
information bus: scsi@0:0.0.0,1
nom logique: /dev/sda1
version: 3.1
numéro de série: 1046-3276
taille: 13GiB
capacité: 14GiB
fonctionnalités: primary ntfs initialized
configuration: clustersize=4096 created=2010-06-12 10:50:12 filesystem=ntfs label=PQSERVICE state=clean
*-volume:1
description: Windows NTFS volume
identifiant matériel: 2
information bus: scsi@0:0.0.0,2
nom logique: /dev/sda2
version: 3.1
numéro de série: e447-92d7
taille: 98MiB
capacité: 100MiB
fonctionnalités: primary bootable ntfs initialized
configuration: clustersize=4096 created=2010-06-12 10:50:16 filesystem=ntfs label=SYSTEM RESERVED state=clean
*-volume:2
description: Windows NTFS volume
identifiant matériel: 3
information bus: scsi@0:0.0.0,3
nom logique: /dev/sda3
version: 3.1
numéro de série: b8561c00-e720-a841-9c84-d9bac5e05a07
taille: 244GiB
capacité: 244GiB
fonctionnalités: primary ntfs initialized
configuration: clustersize=4096 created=2010-06-12 10:50:18 filesystem=ntfs label=Acer state=clean
*-volume:3
description: Extended partition
identifiant matériel: 4
information bus: scsi@0:0.0.0,4
nom logique: /dev/sda4
taille: 207GiB
capacité: 207GiB
fonctionnalités: primary extended partitioned partitioned:extended
*-logicalvolume:0
description: Linux swap / Solaris partition
identifiant matériel: 5
nom logique: /dev/sda5
capacité: 11GiB
fonctionnalités: nofs
*-logicalvolume:1
description: Linux filesystem partition
identifiant matériel: 6
nom logique: /dev/sda6
nom logique: /
capacité: 196GiB
configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
*-cdrom
description: DVD-RAM writer
produit: BDDVDRW CT21N
fabriquant: HL-DT-ST
identifiant matériel: 1
information bus: scsi@1:0.0.0
nom logique: /dev/cdrom
nom logique: /dev/cdrw
nom logique: /dev/dvd
nom logique: /dev/dvdrw
nom logique: /dev/sr0
version: 1.00
fonctionnalités: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=nodisc
*-disk:1
description: ATA Disk
produit: WDC WD5000BEVT-2
fabriquant: Western Digital
identifiant matériel: 0.0.0
information bus: scsi@5:0.0.0
nom logique: /dev/sdb
version: 01.0
numéro de série: WD-WXP1A30N5007
taille: 465GiB (500GB)
fonctionnalités: partitioned partitioned:dos
configuration: ansiversion=5 signature=26a4d0a0
*-volume
description: Windows NTFS volume
identifiant matériel: 1
information bus: scsi@5:0.0.0,1
nom logique: /dev/sdb1
nom logique: /home/data
version: 3.1
numéro de série: 18c12b11-e981-e349-9b3d-cacbe1b55eff
taille: 465GiB
capacité: 465GiB
fonctionnalités: primary ntfs initialized
configuration: clustersize=4096 created=2010-06-12 11:24:54 filesystem=ntfs label=DATA mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,g roup_id=0,default_permissions,allow_other,blksize= 4096 state=mounted
*-serial NON-RÉCLAMÉ
description: SMBus
produit: 5 Series/3400 Series Chipset SMBus Controller
fabriquant: Intel Corporation
identifiant matériel: 1f.3
information bus: pci@0000:00:1f.3
version: 06
bits: 64 bits
horloge: 33MHz
configuration: latency=0
ressources: mémoire:f8506800-f85068ff portE/S:1840(taille=32)
*-pci:1
description: Host bridge
produit: Core Processor QuickPath Architecture Generic Non-Core Registers
fabriquant: Intel Corporation
identifiant matériel: 101
information bus: pci@0000:ff:00.0
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:2
description: Host bridge
produit: Core Processor QuickPath Architecture System Address Decoder
fabriquant: Intel Corporation
identifiant matériel: 102
information bus: pci@0000:ff:00.1
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:3
description: Host bridge
produit: Core Processor QPI Link 0
fabriquant: Intel Corporation
identifiant matériel: 103
information bus: pci@0000:ff:02.0
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:4
description: Host bridge
produit: Core Processor QPI Physical 0
fabriquant: Intel Corporation
identifiant matériel: 104
information bus: pci@0000:ff:02.1
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:5
description: Host bridge
produit: Core Processor Integrated Memory Controller
fabriquant: Intel Corporation
identifiant matériel: 105
information bus: pci@0000:ff:03.0
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:6
description: Host bridge
produit: Core Processor Integrated Memory Controller Target Address Decoder
fabriquant: Intel Corporation
identifiant matériel: 106
information bus: pci@0000:ff:03.1
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:7
description: Host bridge
produit: Core Processor Integrated Memory Controller Test Registers
fabriquant: Intel Corporation
identifiant matériel: 107
information bus: pci@0000:ff:03.4
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:8
description: Host bridge
produit: Core Processor Integrated Memory Controller Channel 0 Control Registers
fabriquant: Intel Corporation
identifiant matériel: 108
information bus: pci@0000:ff:04.0
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:9
description: Host bridge
produit: Core Processor Integrated Memory Controller Channel 0 Address Registers
fabriquant: Intel Corporation
identifiant matériel: 109
information bus: pci@0000:ff:04.1
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:10
description: Host bridge
produit: Core Processor Integrated Memory Controller Channel 0 Rank Registers
fabriquant: Intel Corporation
identifiant matériel: 10a
information bus: pci@0000:ff:04.2
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:11
description: Host bridge
produit: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
fabriquant: Intel Corporation
identifiant matériel: 10b
information bus: pci@0000:ff:04.3
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:12
description: Host bridge
produit: Core Processor Integrated Memory Controller Channel 1 Control Registers
fabriquant: Intel Corporation
identifiant matériel: 10c
information bus: pci@0000:ff:05.0
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:13
description: Host bridge
produit: Core Processor Integrated Memory Controller Channel 1 Address Registers
fabriquant: Intel Corporation
identifiant matériel: 10d
information bus: pci@0000:ff:05.1
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:14
description: Host bridge
produit: Core Processor Integrated Memory Controller Channel 1 Rank Registers
fabriquant: Intel Corporation
identifiant matériel: 10e
information bus: pci@0000:ff:05.2
version: 04
bits: 32 bits
horloge: 33MHz
*-pci:15
description: Host bridge
produit: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
fabriquant: Intel Corporation
identifiant matériel: 10f
information bus: pci@0000:ff:05.3
version: 04
bits: 32 bits
horloge: 33MHz
*-battery
description: Lithium Ion Battery
produit: Intel Corporation
fabriquant: Intel Corporation
identifiant matériel: 1
emplacement: Rear
capacité: 1000mWh
configuration: voltage=0,0V
*-remoteaccess NON-RÉCLAMÉ
fabriquant: Intel
identifiant matériel: 2
fonctionnalités: outbound

```

---

