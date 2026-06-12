---
title: "[SOLVED] amixer cannot unmute"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by Arthur Archnix on 2008-02-19
My laptop mute function key (fn+F9) can mute and unmute sound, which is good because after the computer wakes from standby the sound doesn't work. I have to fn mute, fn unmute in order to get it working.

I attempted to write a script to do this automatically upon wake from suspend, when I discovered that I cannot unmute using amixer. That is to say,
```
amixer -D set Master mute
```
Mutes sound, as expected.
```
amixer -D set Master unmute
```
Does not unmute sound. I have to mute and unmute again with fn key in order to get sound back up. This is true from the command line and when using the amixer gui in ubuntu.

Here is output of lshw:
```
             
    description: Notebook
    product: HP 530 Notebook PC(GH641AT#ABA)
    vendor: Hewlett-Packard
    version: F.00
    serial: **************
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=********************
  *-core
       description: Motherboard
       product: 30D5
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 82.11
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68MVU Ver. F.00 (03/30/2007)
          size: 128KB
          capacity: 960KB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: ***********************
          slot: U10
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KB
             capacity: 64KB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: burst external write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: M4 70T6554EZ3-CE6
             vendor: CE00000000000000
             physical id: 0
             serial: ***********************
             slot: DIMM #1
             size: 512MB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: M4 70T6554EZ3-CE6
             vendor: CE00000000000000
             physical id: 1
             serial: ***********************
             slot: DIMM #2
             size: 512MB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
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
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: eth1
                version: 02
                serial: ***********************
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.34 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial:***********************
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
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
             logical name: scsi4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DS8A1P
                vendor: Slimtype
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CH63
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: SCSI Disk
                product: Hitachi HTS54168
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SB2O
                serial: *****************
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 4769MB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 956MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 68GB
                   capabilities: primary
```

Here is output of dmesg after fresh boot:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7d0000 - 000000003f7e5600 (reserved)
[    0.000000]  BIOS-e820: 000000003f7e5600 - 000000003f7f8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7f8000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 260048) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   260048
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   260048
[    0.000000] On node 0 totalpages: 260048
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30433 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7830 checksum 0
[    0.000000] ACPI: RSDP 000F7830, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 3F7E57C8, 007C (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: FACP 3F7E5684, 00F4 (r4 HP     30D5            3 HP          1)
[    0.000000] ACPI: DSDT 3F7E5ACC, EC49 (r1 HP       hp 520    10000 MSFT  100000E)
[    0.000000] ACPI: FACS 3F7F7E80, 0040
[    0.000000] ACPI: SLIC 3F7E5844, 0176 (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: HPET 3F7E59BC, 0038 (r1 HP     30D5            1 HP          1)
[    0.000000] ACPI: APIC 3F7E59F4, 0068 (r1 HP     30D5            1 HP          1)
[    0.000000] ACPI: MCFG 3F7E5A5C, 003C (r1 HP     30D5            1 HP          1)
[    0.000000] ACPI: TCPA 3F7E5A98, 0032 (r2 HP     30D5            1 HP          1)
[    0.000000] ACPI: SSDT 3F7F4715, 0059 (r1 HP       HPQNLP        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 3F7F476E, 0326 (r1 HP       HPQSAT        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 3F7F52E9, 025F (r1 HP      Cpu0Tst     3000 INTL 20060317)
[    0.000000] ACPI: SSDT 3F7F5548, 00A6 (r1 HP      Cpu1Tst     3000 INTL 20060317)
[    0.000000] ACPI: SSDT 3F7F55EE, 04D7 (r1 HP        CpuPm     3000 INTL 20060317)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:bf400000)
[    0.000000] Built 1 zonelists.  Total pages: 258017
[    0.000000] Kernel command line: root=/dev/sda1 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.022 MHz processor.
[    5.883922] Console: colour VGA+ 80x25
[    5.884224] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    5.884623] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    5.917214] Memory: 1019564k/1040192k available (2015k kernel code, 19908k reserved, 915k data, 364k init, 122688k highmem)
[    5.917224] virtual kernel memory layout:
[    5.917225]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    5.917227]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    5.917228]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    5.917230]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    5.917231]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    5.917232]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    5.917234]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    5.917238] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    5.917274] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    5.917428] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    5.917433] hpet0: 3 64-bit timers, 14318180 Hz
[    5.998377] Calibrating delay using timer specific routine.. 3195.67 BogoMIPS (lpj=6391352)
[    5.998400] Security Framework v1.0.0 initialized
[    5.998407] SELinux:  Disabled at boot.
[    5.998421] Mount-cache hash table entries: 512
[    5.998542] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[    5.998551] monitor/mwait feature present.
[    5.998553] using mwait in idle threads.
[    5.998559] CPU: L1 I cache: 32K, L1 D cache: 32K
[    5.998562] CPU: L2 cache: 2048K
[    5.998565] CPU: Physical Processor ID: 0
[    5.998567] CPU: Processor Core ID: 0
[    5.998569] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[    5.998578] Compat vDSO mapped to ffffe000.
[    5.998590] Checking 'hlt' instruction... OK.
[    6.014475] SMP alternatives: switching to UP code
[    6.014925] Early unpacking initramfs... done
[    6.376530] ACPI: Core revision 20070126
[    6.376658] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    6.416230] CPU0: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[    6.416248] SMP alternatives: switching to SMP code
[    6.416375] Booting processor 1/1 eip 3000
[    6.426617] Initializing CPU#1
[    6.505890] Calibrating delay using timer specific routine.. 3192.07 BogoMIPS (lpj=6384140)
[    6.505898] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[    6.505903] monitor/mwait feature present.
[    6.505907] CPU: L1 I cache: 32K, L1 D cache: 32K
[    6.505909] CPU: L2 cache: 2048K
[    6.505912] CPU: Physical Processor ID: 0
[    6.505914] CPU: Processor Core ID: 1
[    6.505915] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[    6.506491] CPU1: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[    6.506516] Total of 2 processors activated (6387.74 BogoMIPS).
[    6.506716] ENABLING IO-APIC IRQs
[    6.506930] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    6.653851] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    6.673850] Brought up 2 CPUs
[    6.714698] migration_cost=42
[    6.714846] Booting paravirtualized kernel on bare hardware
[    6.714939] Time: 16:03:17  Date: 01/17/108
[    6.714964] NET: Registered protocol family 16
[    6.715057] EISA bus registered
[    6.715062] ACPI: bus type pci registered
[    6.716373] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=16
[    6.716376] PCI: Using configuration type 1
[    6.716378] Setting up standard PCI resources
[    6.718548] ACPI: EC: Look up EC in DSDT
[    6.718980] ACPI: EC: GPE=0x16, ports=0x66, 0x62
[    6.742096] ACPI: Interpreter enabled
[    6.742100] ACPI: (supports S0 S3 S4 S5)
[    6.742115] ACPI: Using IOAPIC for interrupt routing
[    6.750556] ACPI: EC: GPE=0x16, ports=0x66, 0x62
[    6.750629] ACPI: PCI Root Bridge [C002] (0000:00)
[    6.750643] PCI: Probing PCI hardware (bus 00)
[    6.751229] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    6.751234] PCI quirk: region 1100-113f claimed by ICH6 GPIO
[    6.751911] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[    6.752009] PCI: Transparent bridge - 0000:00:1e.0
[    6.752134] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    6.752451] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C098._PRT]
[    6.752625] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C100._PRT]
[    6.752771] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C110._PRT]
[    6.771633] ACPI: PCI Interrupt Link [C10C] (IRQs *10 11)
[    6.771854] ACPI: PCI Interrupt Link [C10D] (IRQs *10 11)
[    6.772071] ACPI: PCI Interrupt Link [C10E] (IRQs 10 *11)
[    6.772281] ACPI: PCI Interrupt Link [C10F] (IRQs 10 11) *0, disabled.
[    6.772502] ACPI: PCI Interrupt Link [C11C] (IRQs 10 11) *5
[    6.772719] ACPI: PCI Interrupt Link [C11D] (IRQs *10 11)
[    6.772927] ACPI: PCI Interrupt Link [C11E] (IRQs 10 11) *0, disabled.
[    6.773031] ACPI Exception (pci_link-0179): AE_NOT_FOUND, Evaluating _PRS [20070126]
[    6.773241] ACPI: Power Resource [C1FE] (on)
[    6.773293] ACPI: Power Resource [C206] (on)
[    6.773409] ACPI: Power Resource [C2FA] (off)
[    6.773512] ACPI: Power Resource [C2FB] (off)
[    6.773615] ACPI: Power Resource [C2FC] (off)
[    6.773721] ACPI: Power Resource [C2FD] (off)
[    6.773735] Linux Plug and Play Support v0.97 (c) Adam Belay
[    6.773747] pnp: PnP ACPI init
[    6.773755] ACPI: bus type pnp registered
[    6.780797] pnp: PnP ACPI: found 12 devices
[    6.780800] ACPI: ACPI bus type pnp unregistered
[    6.780804] PnPBIOS: Disabled by ACPI PNP
[    6.780855] PCI: Using ACPI for IRQ routing
[    6.780857] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    6.837336] NET: Registered protocol family 8
[    6.837338] NET: Registered protocol family 20
[    6.837389] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    6.837392] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    6.837396] pnp: 00:00: iomem range 0x100000-0x3f7fffff could not be reserved
[    6.837406] pnp: 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[    6.837410] pnp: 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    6.837416] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    6.837419] pnp: 00:0a: ioport range 0x1000-0x107f has been reserved
[    6.837422] pnp: 00:0a: ioport range 0x1100-0x113f has been reserved
[    6.837425] pnp: 00:0a: ioport range 0x1200-0x121f has been reserved
[    6.837429] pnp: 00:0a: iomem range 0xf8000000-0xfbffffff has been reserved
[    6.837433] pnp: 00:0a: iomem range 0xfec00000-0xfec000ff could not be reserved
[    6.837436] pnp: 00:0a: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    6.837440] pnp: 00:0a: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    6.837446] pnp: 00:0b: iomem range 0xfeda0000-0xfedbffff could not be reserved
[    6.837449] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    6.837581] Time: tsc clocksource has been installed.
[    6.837596] Switched to high resolution mode on CPU 0
[    6.837687] Switched to high resolution mode on CPU 1
[    6.867832] PCI: Bridge: 0000:00:1c.0
[    6.867834]   IO window: disabled.
[    6.867840]   MEM window: disabled.
[    6.867845]   PREFETCH window: disabled.
[    6.867851] PCI: Bridge: 0000:00:1c.1
[    6.867853]   IO window: disabled.
[    6.867860]   MEM window: f0000000-f00fffff
[    6.867864]   PREFETCH window: disabled.
[    6.867873] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[    6.867875]   IO window: 00002400-000024ff
[    6.867881]   IO window: 00002800-000028ff
[    6.867887]   PREFETCH window: 40000000-43ffffff
[    6.867893]   MEM window: 44000000-47ffffff
[    6.867899] PCI: Bridge: 0000:00:1e.0
[    6.867902]   IO window: 2000-2fff
[    6.867909]   MEM window: f0100000-f03fffff
[    6.867914]   PREFETCH window: 40000000-43ffffff
[    6.867945] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    6.867953] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    6.867978] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    6.867984] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    6.867999] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    6.868019] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[    6.868035] NET: Registered protocol family 2
[    6.913497] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    6.913561] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    6.914694] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    6.915087] TCP: Hash tables configured (established 131072 bind 65536)
[    6.915090] TCP reno registered
[    6.929609] checking if image is initramfs... it is
[    7.651892] Freeing initrd memory: 7064k freed
[    7.652540] audit: initializing netlink socket (disabled)
[    7.652557] audit(1203264197.264:1): initialized
[    7.652672] highmem bounce pool size: 64 pages
[    7.654766] VFS: Disk quotas dquot_6.5.1
[    7.654819] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    7.654921] io scheduler noop registered
[    7.654923] io scheduler anticipatory registered
[    7.654926] io scheduler deadline registered
[    7.654942] io scheduler cfq registered (default)
[    7.654958] Boot video device is 0000:00:02.0
[    7.655085] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    7.655145] assign_interrupt_mode Found MSI capability
[    7.655148] Allocate Port Service[0000:00:1c.0:pcie00]
[    7.655186] Allocate Port Service[0000:00:1c.0:pcie02]
[    7.655290] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    7.655349] assign_interrupt_mode Found MSI capability
[    7.655352] Allocate Port Service[0000:00:1c.1:pcie00]
[    7.655385] Allocate Port Service[0000:00:1c.1:pcie02]
[    7.655552] isapnp: Scanning for PnP cards...
[    8.009203] isapnp: No Plug & Play device found
[    8.033256] Real Time Clock Driver v1.12ac
[    8.033522] hpet_resources: 0xfed00000 is busy
[    8.033585] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    8.034776] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    8.035013] input: Macintosh mouse button emulation as /class/input/input0
[    8.035097] PNP: PS/2 Controller [PNP0303:C1FB,PNP0f13:C1FC] at 0x60,0x64 irq 1,12
[    8.037315] i8042.c: Detected active multiplexing controller, rev 1.1.
[    8.038067] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.038072] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    8.038075] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    8.038078] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    8.038081] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    8.038264] mice: PS/2 mouse device common for all mice
[    8.038472] EISA: Probing bus 0 at eisa.0
[    8.038480] Cannot allocate resource for EISA slot 1
[    8.038484] Cannot allocate resource for EISA slot 2
[    8.038486] Cannot allocate resource for EISA slot 3
[    8.038510] EISA: Detected 0 cards.
[    8.038610] TCP cubic registered
[    8.038625] NET: Registered protocol family 1
[    8.038650] Using IPI No-Shortcut mode
[    8.038804]   Magic number: 12:461:85
[    8.039157] Freeing unused kernel memory: 364k freed
[    8.066177] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.233900] AppArmor: AppArmor initialized<5>audit(1203264198.764:2):  type=1505 info="AppArmor initialized" pid=1180
[    9.242480] fuse init (API version 7.8)
[    9.248345] Failure registering capabilities with primary security module.
[    9.270806] ACPI: Transitioning device [C2FE] to D3
[    9.270809] ACPI: Transitioning device [C2FE] to D3
[    9.270813] ACPI: Fan [C2FE] (off)
[    9.271011] ACPI: Transitioning device [C2FF] to D3
[    9.271013] ACPI: Transitioning device [C2FF] to D3
[    9.271017] ACPI: Fan [C2FF] (off)
[    9.271219] ACPI: Transitioning device [C300] to D3
[    9.271222] ACPI: Transitioning device [C300] to D3
[    9.271225] ACPI: Fan [C300] (off)
[    9.271422] ACPI: Transitioning device [C301] to D3
[    9.271424] ACPI: Transitioning device [C301] to D3
[    9.271427] ACPI: Fan [C301] (off)
[    9.275846] ACPI: SSDT 3F7F4B5C, 023D (r1 HP      Cpu0Ist     3000 INTL 20060317)
[    9.276086] ACPI: SSDT 3F7F4E1E, 04CB (r1 HP      Cpu0Cst     3001 INTL 20060317)
[    9.280146] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    9.280151] ACPI: Processor [CPU0] (supports 8 throttling states)
[    9.280381] ACPI: SSDT 3F7F4A94, 00C8 (r1 HP      Cpu1Ist     3000 INTL 20060317)
[    9.280605] ACPI: SSDT 3F7F4D99, 0085 (r1 HP      Cpu1Cst     3000 INTL 20060317)
[    9.281140] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    9.281144] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.232000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.232000] ACPI: Thermal Zone [TZ0] (29 C)
[    3.236000] Time: hpet clocksource has been installed.
[    3.244000] ACPI: Thermal Zone [TZ1] (53 C)
[    3.260000] ACPI: Thermal Zone [TZ2] (44 C)
[    3.268000] ACPI: Thermal Zone [TZ3] (32 C)
[    3.272000] ACPI: Thermal Zone [TZ4] (50 C)
[    3.708000] usbcore: registered new interface driver usbfs
[    3.708000] usbcore: registered new interface driver hub
[    3.708000] usbcore: registered new device driver usb
[    3.708000] USB Universal Host Controller Interface driver v3.0
[    3.708000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[    3.708000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.708000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.708000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.708000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00003020
[    3.708000] usb usb1: configuration #1 chosen from 1 choice
[    3.708000] hub 1-0:1.0: USB hub found
[    3.708000] hub 1-0:1.0: 2 ports detected
[    3.748000] SCSI subsystem initialized
[    3.800000] libata version 2.21 loaded.
[    3.812000] ata_piix 0000:00:1f.1: version 2.11
[    3.812000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[    3.812000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.812000] scsi0 : ata_piix
[    3.812000] scsi1 : ata_piix
[    3.812000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00013040 irq 14
[    3.812000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00013048 irq 15
[    3.848000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[    3.848000] e100: Copyright(c) 1999-2006 Intel Corporation
[    4.104000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    4.184000] ata1.00: ATAPI: Slimtype DVD A  DS8A1P, CH63, max MWDMA2
[    4.284000] usb 1-2: configuration #1 chosen from 1 choice
[    4.296000] usbcore: registered new interface driver hiddev
[    4.308000] input: Microsoft Basic Optical Mouse as /class/input/input2
[    4.308000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.0-2
[    4.308000] usbcore: registered new interface driver usbhid
[    4.308000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    4.380000] ata1.00: configured for MWDMA2
[    4.380000] ata2: port disabled. ignoring.
[    4.380000] scsi 0:0:0:0: CD-ROM            Slimtype DVD A  DS8A1P    CH63 PQ: 0 ANSI: 5
[    4.380000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    4.380000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.380000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.380000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.380000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.380000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.380000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0584000
[    4.384000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.384000] usb usb2: configuration #1 chosen from 1 choice
[    4.384000] hub 2-0:1.0: USB hub found
[    4.384000] hub 2-0:1.0: 8 ports detected
[    4.488000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 19
[    4.512000] e100: eth0: e100_probe: addr 0xf0101000, irq 19, MAC addr 00:16:D4:E9:ED:44
[    4.512000] ahci 0000:00:1f.2: version 2.2
[    4.512000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 21 (level, low) -> IRQ 20
[    4.676000] usb 1-2: USB disconnect, address 2
[    4.916000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    5.092000] usb 1-2: configuration #1 chosen from 1 choice
[    5.108000] input: Microsoft Basic Optical Mouse as /class/input/input3
[    5.108000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.0-2
[    5.516000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[    5.516000] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    5.516000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.516000] scsi2 : ahci
[    5.516000] scsi3 : ahci
[    5.516000] scsi4 : ahci
[    5.516000] scsi5 : ahci
[    5.516000] ata3: SATA max UDMA/133 cmd 0xf8832100 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.516000] ata4: SATA max UDMA/133 cmd 0xf8832180 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.516000] ata5: SATA max UDMA/133 cmd 0xf8832200 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.516000] ata6: SATA max UDMA/133 cmd 0xf8832280 ctl 0x00000000 bmdma 0x00000000 irq 20
[    6.004000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.004000] ata3.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC7BP, max UDMA/100
[    6.004000] ata3.00: 156301488 sectors, multi 16: LBA48 
[    6.004000] ata3.00: configured for UDMA/100
[    6.320000] ata4: SATA link down (SStatus 0 SControl 0)
[    6.636000] ata5: SATA link down (SStatus 0 SControl 0)
[    6.952000] ata6: SATA link down (SStatus 0 SControl 0)
[    6.952000] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    6.976000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.976000] Uniform CD-ROM driver Revision: 3.20
[    6.976000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.976000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.976000] sd 2:0:0:0: [sda] Write Protect is off
[    6.976000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.976000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.976000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.976000] sd 2:0:0:0: [sda] Write Protect is off
[    6.976000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.976000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.976000]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[    6.980000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    7.376000]  sda1 sda3 sda4
[    7.396000] sd 2:0:0:0: [sda] Attached SCSI disk
[    7.636000] Attempting manual resume
[    7.636000] swsusp: Resume From Partition 8:3
[    7.636000] PM: Checking swsusp image.
[    7.636000] PM: Resume from disk failed.
[    7.664000] kjournald starting.  Commit interval 5 seconds
[    7.664000] EXT3-fs: mounted filesystem with ordered data mode.
[   14.012000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.176000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.220000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.268000] agpgart: Detected an Intel 945GM Chipset.
[   14.268000] agpgart: Detected 7932K stolen memory.
[   14.408000] agpgart: AGP aperture is 256M @ 0xe0000000
[   14.416000] intel_rng: FWH not detected
[   14.452000] Yenta: CardBus bridge found at 0000:02:06.0 [103c:30d5]
[   14.452000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   14.452000] Yenta: Routing CardBus interrupts to PCI
[   14.452000] Yenta TI: socket 0000:02:06.0, mfunc 0x01be1b32, devctl 0x44
[   14.464000] input: PC Speaker as /class/input/input4
[   14.512000] ieee80211_crypt: registered algorithm 'NULL'
[   14.552000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   14.552000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.552000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.592000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
[   14.592000] iTCO_vendor_support: vendor-support=0
[   14.596000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.596000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   14.596000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.632000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   14.632000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.688000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   14.688000] Socket status: 30000006
[   14.688000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   14.688000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   14.688000] cs: IO port probe 0x2000-0x2fff: clean.
[   14.688000] pcmcia: parent PCI bridge Memory window: 0xf0100000 - 0xf03fffff
[   14.688000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   14.704000] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.704000] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   14.704000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   14.948000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.948000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.052000] cs: IO port probe 0x100-0x3af: clean.
[   15.056000] cs: IO port probe 0x3e0-0x4ff: clean.
[   15.056000] cs: IO port probe 0x820-0x8ff: clean.
[   15.056000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.060000] cs: IO port probe 0xa00-0xaff: clean.
[   15.400000] loop: module loaded
[   15.444000] lp: driver loaded but no devices found
[   15.492000] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k
[   15.756000] EXT3 FS on sda1, internal journal
[   16.280000] kjournald starting.  Commit interval 5 seconds
[   16.280000] EXT3 FS on sda4, internal journal
[   16.280000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.580000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   17.164000] ACPI: Battery Slot [C1AC] (battery present)
[   17.184000] ACPI: Video Device [C085] (multi-head: yes  rom: no  post: no)
[   17.212000] ACPI: AC Adapter [C1AB] (on-line)
[   17.296000] No dock devices found.
[   17.376000] input: Power Button (FF) as /class/input/input6
[   17.376000] ACPI: Power Button (FF) [PWRF]
[   17.376000] input: Sleep Button (CM) as /class/input/input7
[   17.376000] ACPI: Sleep Button (CM) [C217]
[   17.376000] input: Lid Switch as /class/input/input8
[   17.376000] ACPI: Lid Switch [C218]
[   18.068000] ppdev: user-space parallel port driver
[   18.208000] audit(1203264213.400:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4832 profile="/usr/sbin/cupsd"
[   18.528000] Failure registering capabilities with primary security module.
[   23.400000] [drm] Initialized drm 1.1.0 20060810
[   23.404000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.404000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   38.916000] NET: Registered protocol family 17
[   44.600000] NET: Registered protocol family 10
[   44.600000] lo: Disabled Privacy Extensions
[   44.600000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.232000] ieee80211_crypt: registered algorithm 'TKIP'
[   63.656000] eth1: no IPv6 routers present
```

Here is output of dmesg after waking from suspend:
```
505 info="AppArmor initialized" pid=1180
[    9.242480] fuse init (API version 7.8)
[    9.248345] Failure registering capabilities with primary security module.
[    9.270806] ACPI: Transitioning device [C2FE] to D3
[    9.270809] ACPI: Transitioning device [C2FE] to D3
[    9.270813] ACPI: Fan [C2FE] (off)
[    9.271011] ACPI: Transitioning device [C2FF] to D3
[    9.271013] ACPI: Transitioning device [C2FF] to D3
[    9.271017] ACPI: Fan [C2FF] (off)
[    9.271219] ACPI: Transitioning device [C300] to D3
[    9.271222] ACPI: Transitioning device [C300] to D3
[    9.271225] ACPI: Fan [C300] (off)
[    9.271422] ACPI: Transitioning device [C301] to D3
[    9.271424] ACPI: Transitioning device [C301] to D3
[    9.271427] ACPI: Fan [C301] (off)
[    9.275846] ACPI: SSDT 3F7F4B5C, 023D (r1 HP      Cpu0Ist     3000 INTL 20060317)
[    9.276086] ACPI: SSDT 3F7F4E1E, 04CB (r1 HP      Cpu0Cst     3001 INTL 20060317)
[    9.280146] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    9.280151] ACPI: Processor [CPU0] (supports 8 throttling states)
[    9.280381] ACPI: SSDT 3F7F4A94, 00C8 (r1 HP      Cpu1Ist     3000 INTL 20060317)
[    9.280605] ACPI: SSDT 3F7F4D99, 0085 (r1 HP      Cpu1Cst     3000 INTL 20060317)
[    9.281140] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    9.281144] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.232000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.232000] ACPI: Thermal Zone [TZ0] (29 C)
[    3.236000] Time: hpet clocksource has been installed.
[    3.244000] ACPI: Thermal Zone [TZ1] (53 C)
[    3.260000] ACPI: Thermal Zone [TZ2] (44 C)
[    3.268000] ACPI: Thermal Zone [TZ3] (32 C)
[    3.272000] ACPI: Thermal Zone [TZ4] (50 C)
[    3.708000] usbcore: registered new interface driver usbfs
[    3.708000] usbcore: registered new interface driver hub
[    3.708000] usbcore: registered new device driver usb
[    3.708000] USB Universal Host Controller Interface driver v3.0
[    3.708000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[    3.708000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.708000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.708000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.708000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00003020
[    3.708000] usb usb1: configuration #1 chosen from 1 choice
[    3.708000] hub 1-0:1.0: USB hub found
[    3.708000] hub 1-0:1.0: 2 ports detected
[    3.748000] SCSI subsystem initialized
[    3.800000] libata version 2.21 loaded.
[    3.812000] ata_piix 0000:00:1f.1: version 2.11
[    3.812000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[    3.812000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.812000] scsi0 : ata_piix
[    3.812000] scsi1 : ata_piix
[    3.812000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00013040 irq 14
[    3.812000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00013048 irq 15
[    3.848000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[    3.848000] e100: Copyright(c) 1999-2006 Intel Corporation
[    4.104000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    4.184000] ata1.00: ATAPI: Slimtype DVD A  DS8A1P, CH63, max MWDMA2
[    4.284000] usb 1-2: configuration #1 chosen from 1 choice
[    4.296000] usbcore: registered new interface driver hiddev
[    4.308000] input: Microsoft Basic Optical Mouse as /class/input/input2
[    4.308000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.0-2
[    4.308000] usbcore: registered new interface driver usbhid
[    4.308000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    4.380000] ata1.00: configured for MWDMA2
[    4.380000] ata2: port disabled. ignoring.
[    4.380000] scsi 0:0:0:0: CD-ROM            Slimtype DVD A  DS8A1P    CH63 PQ: 0 ANSI: 5
[    4.380000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    4.380000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.380000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.380000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.380000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.380000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.380000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0584000
[    4.384000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.384000] usb usb2: configuration #1 chosen from 1 choice
[    4.384000] hub 2-0:1.0: USB hub found
[    4.384000] hub 2-0:1.0: 8 ports detected
[    4.488000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 19
[    4.512000] e100: eth0: e100_probe: addr 0xf0101000, irq 19, MAC addr 00:16:D4:E9:ED:44
[    4.512000] ahci 0000:00:1f.2: version 2.2
[    4.512000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 21 (level, low) -> IRQ 20
[    4.676000] usb 1-2: USB disconnect, address 2
[    4.916000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    5.092000] usb 1-2: configuration #1 chosen from 1 choice
[    5.108000] input: Microsoft Basic Optical Mouse as /class/input/input3
[    5.108000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.0-2
[    5.516000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[    5.516000] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    5.516000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.516000] scsi2 : ahci
[    5.516000] scsi3 : ahci
[    5.516000] scsi4 : ahci
[    5.516000] scsi5 : ahci
[    5.516000] ata3: SATA max UDMA/133 cmd 0xf8832100 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.516000] ata4: SATA max UDMA/133 cmd 0xf8832180 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.516000] ata5: SATA max UDMA/133 cmd 0xf8832200 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.516000] ata6: SATA max UDMA/133 cmd 0xf8832280 ctl 0x00000000 bmdma 0x00000000 irq 20
[    6.004000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.004000] ata3.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC7BP, max UDMA/100
[    6.004000] ata3.00: 156301488 sectors, multi 16: LBA48 
[    6.004000] ata3.00: configured for UDMA/100
[    6.320000] ata4: SATA link down (SStatus 0 SControl 0)
[    6.636000] ata5: SATA link down (SStatus 0 SControl 0)
[    6.952000] ata6: SATA link down (SStatus 0 SControl 0)
[    6.952000] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    6.976000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.976000] Uniform CD-ROM driver Revision: 3.20
[    6.976000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.976000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.976000] sd 2:0:0:0: [sda] Write Protect is off
[    6.976000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.976000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.976000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.976000] sd 2:0:0:0: [sda] Write Protect is off
[    6.976000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.976000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.976000]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[    6.980000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    7.376000]  sda1 sda3 sda4
[    7.396000] sd 2:0:0:0: [sda] Attached SCSI disk
[    7.636000] Attempting manual resume
[    7.636000] swsusp: Resume From Partition 8:3
[    7.636000] PM: Checking swsusp image.
[    7.636000] PM: Resume from disk failed.
[    7.664000] kjournald starting.  Commit interval 5 seconds
[    7.664000] EXT3-fs: mounted filesystem with ordered data mode.
[   14.012000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.176000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.220000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.268000] agpgart: Detected an Intel 945GM Chipset.
[   14.268000] agpgart: Detected 7932K stolen memory.
[   14.408000] agpgart: AGP aperture is 256M @ 0xe0000000
[   14.416000] intel_rng: FWH not detected
[   14.452000] Yenta: CardBus bridge found at 0000:02:06.0 [103c:30d5]
[   14.452000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   14.452000] Yenta: Routing CardBus interrupts to PCI
[   14.452000] Yenta TI: socket 0000:02:06.0, mfunc 0x01be1b32, devctl 0x44
[   14.464000] input: PC Speaker as /class/input/input4
[   14.512000] ieee80211_crypt: registered algorithm 'NULL'
[   14.552000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   14.552000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.552000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.592000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
[   14.592000] iTCO_vendor_support: vendor-support=0
[   14.596000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.596000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   14.596000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.632000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   14.632000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.688000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   14.688000] Socket status: 30000006
[   14.688000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   14.688000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   14.688000] cs: IO port probe 0x2000-0x2fff: clean.
[   14.688000] pcmcia: parent PCI bridge Memory window: 0xf0100000 - 0xf03fffff
[   14.688000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   14.704000] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.704000] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   14.704000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   14.948000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.948000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.052000] cs: IO port probe 0x100-0x3af: clean.
[   15.056000] cs: IO port probe 0x3e0-0x4ff: clean.
[   15.056000] cs: IO port probe 0x820-0x8ff: clean.
[   15.056000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.060000] cs: IO port probe 0xa00-0xaff: clean.
[   15.400000] loop: module loaded
[   15.444000] lp: driver loaded but no devices found
[   15.492000] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k
[   15.756000] EXT3 FS on sda1, internal journal
[   16.280000] kjournald starting.  Commit interval 5 seconds
[   16.280000] EXT3 FS on sda4, internal journal
[   16.280000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.580000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   17.164000] ACPI: Battery Slot [C1AC] (battery present)
[   17.184000] ACPI: Video Device [C085] (multi-head: yes  rom: no  post: no)
[   17.212000] ACPI: AC Adapter [C1AB] (on-line)
[   17.296000] No dock devices found.
[   17.376000] input: Power Button (FF) as /class/input/input6
[   17.376000] ACPI: Power Button (FF) [PWRF]
[   17.376000] input: Sleep Button (CM) as /class/input/input7
[   17.376000] ACPI: Sleep Button (CM) [C217]
[   17.376000] input: Lid Switch as /class/input/input8
[   17.376000] ACPI: Lid Switch [C218]
[   18.068000] ppdev: user-space parallel port driver
[   18.208000] audit(1203264213.400:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4832 profile="/usr/sbin/cupsd"
[   18.528000] Failure registering capabilities with primary security module.
[   23.400000] [drm] Initialized drm 1.1.0 20060810
[   23.404000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.404000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   38.916000] NET: Registered protocol family 17
[   44.600000] NET: Registered protocol family 10
[   44.600000] lo: Disabled Privacy Extensions
[   44.600000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.232000] ieee80211_crypt: registered algorithm 'TKIP'
[   63.656000] eth1: no IPv6 routers present
[  225.592000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  225.832000] ACPI: PCI interrupt for device 0000:02:08.0 disabled
[  226.024000] ACPI: PCI interrupt for device 0000:10:00.0 disabled
[  228.792000] PM: Preparing system for mem sleep
[  228.792000] Stopping tasks ... done.
[  228.800000] Suspending console(s)
[  228.800000] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[  228.948000] sd 2:0:0:0: [sda] Stopping disk
[  229.424000] usb_device usbdev2.1: PM: suspend 0->2, parent usb2 already 2
[  229.424000] usb_endpoint usbdev2.1_ep81: PM: suspend 0->2, parent 2-0:1.0 already 2
[  229.424000] hub 2-0:1.0: PM: suspend 2->2, parent usb2 already 2
[  229.424000] usb_endpoint usbdev2.1_ep00: PM: suspend 0->2, parent usb2 already 2
[  229.564000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[  229.580000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[  229.580000] pci_set_power_state(): 0000:00:1f.1: state=3, current state=5
[  229.580000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[  229.596000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[  229.600000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[  229.620000] ACPI: Transitioning device [C113] to D3
[  229.620000] ACPI: Transitioning device [C113] to D3
[  229.632000] Disabling non-boot CPUs ...
[  229.748000] CPU 1 is now offline
[  229.748000] SMP alternatives: switching to UP code
[  229.748000] CPU1 is down
[  229.748000] PM: Entering mem sleep
[  229.748000] Back to C!
[  229.748000] PM: Finishing wakeup.
[  229.748000] Enabling non-boot CPUs ...
[  229.760000] SMP alternatives: switching to SMP code
[  229.760000] Booting processor 1/1 eip 3000
[  229.768000] Initializing CPU#1
[  229.848000] Calibrating delay using timer specific routine.. 3192.03 BogoMIPS (lpj=6384072)
[  229.848000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[  229.848000] monitor/mwait feature present.
[  229.848000] CPU: L1 I cache: 32K, L1 D cache: 32K
[  229.848000] CPU: L2 cache: 2048K
[  229.848000] CPU: Physical Processor ID: 0
[  229.848000] CPU: Processor Core ID: 1
[  229.848000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[  229.848000] CPU1: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[  229.848000] CPU1 is up
[  229.852000] Switched to high resolution mode on CPU 1
[  229.884000] APIC error on CPU0: 00(40)
[  229.884000] APIC error on CPU1: 00(40)
[  229.972000] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 10a)
[  229.972000] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
[  229.992000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  229.992000] PM: Writing back config space on device 0000:00:02.1 at offset 4 (was 0, writing f0500000)
[  229.992000] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900007)
[  230.008000] PM: Writing back config space on device 0000:00:1b.0 at offset f (was 100, writing 10a)
[  230.008000] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 10)
[  230.008000] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100000, writing 100002)
[  230.008000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[  230.008000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  230.056000] PM: Writing back config space on device 0000:00:1c.0 at offset f (was 100, writing 4010a)
[  230.056000] PM: Writing back config space on device 0000:00:1c.0 at offset 9 (was 10001, writing 1fff1)
[  230.056000] PM: Writing back config space on device 0000:00:1c.0 at offset 8 (was 0, writing fff0)
[  230.056000] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20000000, writing 200000f0)
[  230.056000] PM: Writing back config space on device 0000:00:1c.0 at offset 3 (was 810000, writing 810010)
[  230.056000] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100000, writing 100007)
[  230.056000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[  230.056000] PM: Writing back config space on device 0000:00:1c.1 at offset f (was 200, writing 4020a)
[  230.056000] PM: Writing back config space on device 0000:00:1c.1 at offset 9 (was 10001, writing 1fff1)
[  230.056000] PM: Writing back config space on device 0000:00:1c.1 at offset 8 (was 0, writing f000f000)
[  230.056000] PM: Writing back config space on device 0000:00:1c.1 at offset 7 (was 20000000, writing 200000f0)
[  230.056000] PM: Writing back config space on device 0000:00:1c.1 at offset 3 (was 810000, writing 810010)
[  230.056000] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100000, writing 100007)
[  230.056000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[  230.056000] PCI: Enabling device 0000:00:1d.0 (0000 -> 0001)
[  230.056000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[  230.056000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[  230.056000] PM: Writing back config space on device 0000:00:1d.0 at offset f (was 100, writing 105)
[  230.056000] PM: Writing back config space on device 0000:00:1d.0 at offset 8 (was 1, writing 3021)
[  230.056000] usb usb1: root hub lost power or was reset
[  230.072000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[  230.072000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[  230.072000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[  230.072000] PM: Writing back config space on device 0000:00:1d.7 at offset f (was 100, writing 105)
[  230.072000] PM: Writing back config space on device 0000:00:1d.7 at offset 4 (was 0, writing f0584000)
[  230.072000] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 10001, writing 43f14001)
[  230.072000] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was 0, writing f030f010)
[  230.072000] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 228000f0, writing 22802020)
[  230.072000] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100007, writing 100107)
[  230.072000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[  230.072000] PM: Writing back config space on device 0000:00:1f.1 at offset f (was 100, writing 10a)
[  230.072000] PM: Writing back config space on device 0000:00:1f.1 at offset 8 (was c01, writing 3041)
[  230.072000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[  230.072000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  230.072000] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000005) is beyond end of object [20070126]
[  230.072000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.C21A] (Node df83f648), AE_AML_PACKAGE_LIMIT
[  230.072000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.C002.C0DD.C323._STM] (Node df8424e0), AE_AML_PACKAGE_LIMIT
[  230.072000] ata1: ACPI set timing mode failed (status=0x300d)
[  230.072000] ata2: port disabled. ignoring.
[  230.088000] PM: Writing back config space on device 0000:00:1f.2 at offset 9 (was fec01000, writing f0585000)
[  230.088000] PM: Writing back config space on device 0000:00:1f.2 at offset 8 (was 1301, writing 3071)
[  230.088000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 21 (level, low) -> IRQ 20
[  230.088000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  230.776000] ata1.00: configured for MWDMA2
[  231.092000] PM: Writing back config space on device 0000:10:00.0 at offset f (was 100, writing 10a)
[  231.092000] PM: Writing back config space on device 0000:10:00.0 at offset 4 (was 0, writing f0000000)
[  231.092000] PM: Writing back config space on device 0000:10:00.0 at offset 3 (was 0, writing 10)
[  231.092000] PM: Writing back config space on device 0000:10:00.0 at offset 1 (was 100000, writing 100002)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset f (was 34001ff, writing 5c0010b)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset e (was 0, writing 28fc)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset d (was 0, writing 2800)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset c (was 0, writing 24fc)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset b (was 0, writing 2400)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset a (was 0, writing 47fff000)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset 9 (was 0, writing 44000000)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset 8 (was 0, writing 43fff000)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset 7 (was 0, writing 40000000)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset 6 (was 0, writing b0060302)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset 4 (was 0, writing f0100000)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset 3 (was 20000, writing 2a820)
[  231.092000] PM: Writing back config space on device 0000:02:06.0 at offset 1 (was 2100000, writing 2100007)
[  231.092000] PM: Writing back config space on device 0000:02:08.0 at offset f (was 38080100, writing 38080105)
[  231.092000] PM: Writing back config space on device 0000:02:08.0 at offset 5 (was 1, writing 2001)
[  231.092000] PM: Writing back config space on device 0000:02:08.0 at offset 4 (was 0, writing f0101000)
[  231.092000] PM: Writing back config space on device 0000:02:08.0 at offset 3 (was 0, writing 4010)
[  231.092000] PM: Writing back config space on device 0000:02:08.0 at offset 1 (was 2900000, writing 2900003)
[  231.404000] ata4: SATA link down (SStatus 0 SControl 0)
[  231.404000] ata5: SATA link down (SStatus 0 SControl 0)
[  231.404000] ata6: SATA link down (SStatus 0 SControl 0)
[  231.420000] usb_endpoint usbdev2.1_ep00: PM: resume from 0, parent usb2 still 2
[  231.420000] usb_endpoint usbdev2.1_ep81: PM: resume from 0, parent 2-0:1.0 still 2
[  231.420000] usb_device usbdev2.1: PM: resume from 0, parent usb2 still 2
[  231.420000] usb_endpoint usbdev1.3_ep00: PM: resume from 0, parent 1-2 still 2
[  231.420000] usbhid 1-2:1.0: PM: resume from 2, parent 1-2 still 2
[  231.420000] usb_endpoint usbdev1.3_ep81: PM: resume from 0, parent 1-2:1.0 still 2
[  231.420000] usb_device usbdev1.3: PM: resume from 0, parent 1-2 still 2
[  231.420000] sd 2:0:0:0: [sda] Starting disk
[  231.576000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  231.608000] ata3.00: configured for UDMA/100
[  231.624000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[  231.628000] sd 2:0:0:0: [sda] Write Protect is off
[  231.628000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  231.628000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  231.628000] Restarting tasks ... <6>usb 1-2: USB disconnect, address 3
[  231.628000] done.
[  231.868000] usb 1-2: new low speed USB device using uhci_hcd and address 4
[  232.044000] usb 1-2: configuration #1 chosen from 1 choice
[  232.060000] input: Microsoft Basic Optical Mouse as /class/input/input9
[  232.060000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.0-2
[  232.104000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[  232.104000] e100: Copyright(c) 1999-2006 Intel Corporation
[  232.104000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 19
[  232.132000] e100: eth0: e100_probe: addr 0xf0101000, irq 19, MAC addr 00:16:D4:E9:ED:44
[  232.136000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  232.136000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  232.144000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[  232.144000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[  232.144000] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  232.144000] PCI: Setting latency timer of device 0000:10:00.0 to 64
[  232.144000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[  232.188000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  232.932000] input: Power Button (FF) as /class/input/input10
[  232.932000] ACPI: Power Button (FF) [PWRF]
[  232.932000] input: Sleep Button (CM) as /class/input/input11
[  232.932000] ACPI: Sleep Button (CM) [C217]
[  232.936000] input: Lid Switch as /class/input/input12
[  232.936000] ACPI: Lid Switch [C218]
[  233.156000] ACPI: Transitioning device [C2FE] to D3
[  233.156000] ACPI: Transitioning device [C2FE] to D3
[  233.156000] ACPI: Fan [C2FE] (off)
[  233.156000] ACPI: Transitioning device [C2FF] to D3
[  233.156000] ACPI: Transitioning device [C2FF] to D3
[  233.156000] ACPI: Fan [C2FF] (off)
[  233.156000] ACPI: Transitioning device [C300] to D3
[  233.156000] ACPI: Transitioning device [C300] to D3
[  233.156000] ACPI: Fan [C300] (off)
[  233.156000] ACPI: Transitioning device [C301] to D3
[  233.156000] ACPI: Transitioning device [C301] to D3
[  233.156000] ACPI: Fan [C301] (off)
[  233.176000] ACPI: Thermal Zone [TZ0] (29 C)
[  233.184000] ACPI: Thermal Zone [TZ1] (50 C)
[  233.192000] ACPI: Thermal Zone [TZ2] (44 C)
[  233.200000] ACPI: Thermal Zone [TZ3] (32 C)
[  233.204000] ACPI: Thermal Zone [TZ4] (63 C)
[  233.288000] ACPI: AC Adapter [C1AB] (on-line)
[  233.344000] ACPI: Battery Slot [C1AC] (battery present)
[  233.948000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[  234.168000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  243.712000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  243.808000] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

I have filed a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/192669"), but I would be happy to mark it invalid if someone can help me puzzle out what is happening.

---

### Post by Arthur Archnix on 2008-02-20
Bump.

---

### Post by Arthur Archnix on 2008-02-25
bump

---

### Post by Arthur Archnix on 2008-02-26
cross fingers, last try, bump.

---

### Post by Arthur Archnix on 2008-03-07
I've discovered another  piece to the puzzle: When it wakes from standby I have sound out of my headphone jack, but not laptop speakers.

---

### Post by Arthur Archnix on 2008-03-18
I'm marking this thread as solved. Ubuntu has scripts in /etc/acpi/suspend.d/ and etc/acpi/resume.d/ that shut down, then start up alsa using alsa-utils. I commented out everything in those scripts and now sound works upon resume without having to mute and unmute the channels.

---

