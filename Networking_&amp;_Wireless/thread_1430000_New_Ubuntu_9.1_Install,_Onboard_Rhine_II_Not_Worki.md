---
title: "New Ubuntu 9.1 Install, Onboard Rhine II Not Working"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by FlyingMonkey38 on 2010-03-14
Hi.  This is my first attempt switching to Ubuntu from Windows, and I am having some trouble getting the _on-board ethernet_ to work in _Ubuntu 9.1_.  I have a MSI KM2M Combo-L VIA KM266 and VT8235 Chipset which uses the_ Rhine II chipset_.  I am trying to use the onboard ethernet, however it does not connect to the network after installing Ubuntu, although the driver appears to have been automatically installed.  I also tried this with several other network cards (Intel, Dlink, Netgear) with various chipsets, but none seem to work.  Any help is appreciated.  

Our network Netgear switch/router has DCHP enabled, and all of the Windows computers connect just fine.  This is true even when we plug another computer into the ethernet cable serving the Ubuntu computer.

When I manually configure the IP address, it shows the network connection as connected, but it is unable to ping and/or connect to the internet (except for localhost and the assigned IP address).  I used 192.168.11 as the IP, 255.255.255.0 as the netmask, and 192.168.1.1 as the gateway.

Below are several commands, that I've run to provide some additional information (using auto eth1).  Please let me know if any more information is needed.

**ifconfig -a:**
```

eth1      Link encap:Ethernet  HWaddr 00:10:dc:fa:5a:f3  
          inet6 addr: fe80::210:dcff:fefa:5af3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:238 (238.0 B)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```[B]

[/B]**iwconfig:**
```

lo        no wireless extensions.

eth1      no wireless extensions.

```

**sudo dhclient eth1:**
```

Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:10:dc:fa:5a:f3
Sending on   LPF/eth1/00:10:dc:fa:5a:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

**sudo ifdown eth1:**
```

ifdown: interface eth1 not configured

```[B]

sudo ifup eth1:[/B]
```

Ignoring unknown interface eth1=eth1.

```[B]

sudo lshw -C network:[/B]
```

 *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 74
       serial: 00:10:dc:fa:5a:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half 
latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:b400(size=256) memory:e0101000-e01010ff

```[B]

cat /etc/network/interfaces:[/B]
```

auto lo
iface lo inet loopback

```[B]

ping -c 10 ubuntu.com:[/B]
```

ping: unknown host ubuntu.com

```[B]

lspci:[/B]
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

```[B]

dmesg:[/B]
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) 

#48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1dff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 01E000000 mask FFE000000 uncachable
[    0.000000]   2 base 0D0000000 mask FF8000000 write-combining
[    0.000000]   3 base 0D0000000 mask FF8000000 write-combining
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  modified: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[    0.000000]  modified: 000000001dff3000 - 000000001e000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001dff0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001dc00000 page 2M
[    0.000000]  001dc00000 - 001dff0000 page 4k
[    0.000000] kernel direct mapping tables up to 1dff0000 @ 10000-15000
[    0.000000] RAMDISK: 160e9000 - 16833450
[    0.000000] ACPI: RSDP 000f8250 00014 (v00 VT8375)
[    0.000000] ACPI: RSDT 1dff3000 0002C (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 1dff3040 00074 (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 1dff30c0 039ED (v01 VT8375 AWRDACPI 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 1dff0000 00040
[    0.000000] ACPI: APIC 1dff6ac0 0005A (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1dff0000
[    0.000000]   low ram: 0 - 1dff0000
[    0.000000]   node 0 low ram: 00000000 - 1dff0000
[    0.000000]   node 0 bootmap 00011000 - 00014c00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [00160e9000 - 0016833450]          RAMDISK ==> [00160e9000 - 0016833450]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac0b2]              BRK ==> [00008a9000 - 00008ac0b2]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000015000]          BOOTMAP ==> [0000011000 - 0000015000]
[    0.000000] found SMP MP-table at [c00f6750] f6750
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001dff0
[    0.000000]   HighMem  0x0001dff0 -> 0x0001dff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001dff0
[    0.000000] On node 0 totalpages: 122751
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 928 pages used for memmap
[    0.000000]   Normal zone: 117840 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1e000000 (gap: 1e000000:e0c00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c13c2000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121791
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic 

root=UUID=dde4ca3b-23a1-4059-a680-5f621cd6e4d2 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2456960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 468720k/491456k available (4565k kernel code, 22052k reserved, 2143k data, 540k init, 

0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xde7f0000 - 0xff7fe000   ( 528 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1532.672 MHz processor.
[    0.001479] Console: colour VGA+ 80x25
[    0.001486] console [tty0] enabled
[    0.004017] Calibrating delay loop (skipped), value calculated using timer frequency.. 3065.34 BogoMIPS 

(lpj=6130688)
[    0.004063] Security Framework initialized
[    0.004116] AppArmor: AppArmor initialized
[    0.004129] Mount-cache hash table entries: 512
[    0.004389] Initializing cgroup subsys ns
[    0.004399] Initializing cgroup subsys cpuacct
[    0.004406] Initializing cgroup subsys memory
[    0.004422] Initializing cgroup subsys freezer
[    0.004426] Initializing cgroup subsys net_cls
[    0.004448] CPU: CLK_CTL MSR was 60031223. Reprogramming to 20031223
[    0.004453] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004458] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004465] mce: CPU supports 4 MCE banks
[    0.004497] Performance Counters: AMD PMU driver.
[    0.004516] ... version:                 0
[    0.004519] ... bit width:               48
[    0.004522] ... generic counters:        4
[    0.004525] ... value mask:              0000ffffffffffff
[    0.004528] ... max period:              00007fffffffffff
[    0.004531] ... fixed-purpose counters:  0
[    0.004534] ... counter mask:            000000000000000f
[    0.004542] Checking 'hlt' instruction... OK.
[    0.020892] SMP alternatives: switching to UP code
[    0.028049] Freeing SMP alternatives: 19k freed
[    0.028119] ACPI: Core revision 20090521
[    0.048587] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.088302] CPU0: AMD Athlon(tm) XP 1800+ stepping 01
[    0.092001] Brought up 1 CPUs
[    0.092001] Total of 1 processors activated (3065.34 BogoMIPS).
[    0.092001] CPU0 attaching NULL sched-domain.
[    0.092001] Booting paravirtualized kernel on bare hardware
[    0.092001] regulator: core version 0.5
[    0.092001] Time:  6:31:29  Date: 03/14/10
[    0.092001] NET: Registered protocol family 16
[    0.092001] EISA bus registered
[    0.092001] ACPI: bus type pci registered
[    0.098528] PCI: PCI BIOS revision 2.10 entry at 0xfbd30, last bus=1
[    0.098532] PCI: Using configuration type 1 for base access
[    0.100044] bio: create slab <bio-0> at 0
[    0.100804] ACPI: EC: Look up EC in DSDT
[    0.107471] ACPI: Interpreter enabled
[    0.107484] ACPI: (supports S0 S1 S4 S5)
[    0.107517] ACPI: Using IOAPIC for interrupt routing
[    0.112773] ACPI: No dock devices found.
[    0.112931] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.113015] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.113116] pci 0000:00:01.0: supports D1
[    0.113183] pci 0000:00:10.0: reg 20 io port: [0xa000-0xa01f]
[    0.113209] pci 0000:00:10.0: supports D1 D2
[    0.113214] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.113220] pci 0000:00:10.0: PME# disabled
[    0.113271] pci 0000:00:10.1: reg 20 io port: [0xa400-0xa41f]
[    0.113297] pci 0000:00:10.1: supports D1 D2
[    0.113301] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.113306] pci 0000:00:10.1: PME# disabled
[    0.113357] pci 0000:00:10.2: reg 20 io port: [0xa800-0xa81f]
[    0.113384] pci 0000:00:10.2: supports D1 D2
[    0.113387] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.113393] pci 0000:00:10.2: PME# disabled
[    0.113460] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.113471] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
[    0.113477] pci 0000:00:11.0: quirk: region 5000-500f claimed by vt8235 SMB
[    0.113547] pci 0000:00:11.1: reg 20 io port: [0xac00-0xac0f]
[    0.113613] pci 0000:00:11.5: reg 10 io port: [0xb000-0xb0ff]
[    0.113658] pci 0000:00:11.5: supports D1 D2
[    0.113696] pci 0000:00:12.0: reg 10 io port: [0xb400-0xb4ff]
[    0.113705] pci 0000:00:12.0: reg 14 32bit mmio: [0xe0101000-0xe01010ff]
[    0.113744] pci 0000:00:12.0: supports D1 D2
[    0.113747] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.113753] pci 0000:00:12.0: PME# disabled
[    0.113813] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe007ffff]
[    0.113821] pci 0000:01:00.0: reg 14 32bit mmio: [0xd8000000-0xdfffffff]
[    0.113842] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.113861] pci 0000:01:00.0: supports D1 D2
[    0.113901] pci 0000:00:01.0: bridge 32bit mmio: [0xe0000000-0xe00fffff]
[    0.113907] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.113917] pci_bus 0000:00: on NUMA node 0
[    0.113924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.129605] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.129861] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.130108] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[    0.130353] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[    0.130589] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.130816] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.131076] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.131303] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.131683] SCSI subsystem initialized
[    0.131885] libata version 3.00 loaded.
[    0.132064] usbcore: registered new interface driver usbfs
[    0.132094] usbcore: registered new interface driver hub
[    0.132144] usbcore: registered new device driver usb
[    0.132394] ACPI: WMI: Mapper loaded
[    0.132397] PCI: Using ACPI for IRQ routing
[    0.132643] Bluetooth: Core ver 2.15
[    0.132700] NET: Registered protocol family 31
[    0.132703] Bluetooth: HCI device and connection manager initialized
[    0.132709] Bluetooth: HCI socket layer initialized
[    0.132713] NetLabel: Initializing
[    0.132715] NetLabel:  domain hash size = 128
[    0.132718] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.132746] NetLabel:  unlabeled traffic allowed by default
[    0.137055] pnp: PnP ACPI init
[    0.137110] ACPI: bus type pnp registered
[    0.141776] pnp: PnP ACPI: found 13 devices
[    0.141781] ACPI: ACPI bus type pnp unregistered
[    0.141788] PnPBIOS: Disabled by ACPI PNP
[    0.141815] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.141820] system 00:02: ioport range 0x294-0x297 has been reserved
[    0.176587] AppArmor: AppArmor Filesystem Enabled
[    0.176623] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.176627] pci 0000:00:01.0:   IO window: disabled
[    0.176636] pci 0000:00:01.0:   MEM window: 0xe0000000-0xe00fffff
[    0.176642] pci 0000:00:01.0:   PREFETCH window: 0xd8000000-0xdfffffff
[    0.176663] pci 0000:00:01.0: setting latency timer to 64
[    0.176675] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.176679] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.176684] pci_bus 0000:01: resource 1 mem: [0xe0000000-0xe00fffff]
[    0.176689] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xdfffffff]
[    0.176763] NET: Registered protocol family 2
[    0.176930] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.177399] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.177758] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.178125] TCP: Hash tables configured (established 16384 bind 16384)
[    0.178129] TCP reno registered
[    0.178303] NET: Registered protocol family 1
[    0.178464] Trying to unpack rootfs image as initramfs...
[    0.502194] Freeing initrd memory: 7465k freed
[    0.526264] cpufreq-nforce2: No nForce2 chipset.
[    0.526319] Scanning for low memory corruption every 60 seconds
[    0.526538] audit: initializing netlink socket (disabled)
[    0.526571] type=2000 audit(1268548288.523:1): initialized
[    0.538729] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.541076] VFS: Disk quotas dquot_6.5.2
[    0.541167] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.542052] fuse init (API version 7.12)
[    0.542183] msgmni has been set to 930
[    0.542602] alg: No test for stdrng (krng)
[    0.542633] io scheduler noop registered
[    0.542637] io scheduler anticipatory registered
[    0.542640] io scheduler deadline registered
[    0.542705] io scheduler cfq registered (default)
[    0.542732] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.542792] pci 0000:01:00.0: Boot video device
[    0.542927] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.542967] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.543217] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.543226] ACPI: Power Button [PWRF]
[    0.543310] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.543315] ACPI: Power Button [PWRB]
[    0.543403] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.543414] ACPI: Sleep Button [SLPB]
[    0.543493] fan PNP0C0B:00: registered as cooling_device0
[    0.543501] ACPI: Fan [FAN] (on)
[    0.543874] Marking TSC unstable due to TSC halts in idle
[    0.543916] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.543944] processor LNXCPU:00: registered as cooling_device1
[    0.543989] thermal LNXTHERM:01: registered as thermal_zone0
[    0.543989] ACPI: Thermal Zone [THRM] (38 C)
[    0.543989] isapnp: Scanning for PnP cards...
[    0.547956] Switched to high resolution mode on CPU 0
[    0.900950] isapnp: No Plug & Play device found
[    0.902752] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.902911] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.903012] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.903355] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.903493] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.905205] brd: module loaded
[    0.905972] loop: module loaded
[    0.906158] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.907000] pata_via 0000:00:11.1: version 0.3.4
[    0.907534] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.907539] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.907551]   alloc irq_desc for 20 on node -1
[    0.907555]   alloc kstat_irqs on node -1
[    0.907572] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.907969] scsi0 : pata_via
[    0.908283] scsi1 : pata_via
[    0.912570] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xac00 irq 14
[    0.912577] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xac08 irq 15
[    0.913209] Fixed MDIO Bus: probed
[    0.913271] PPP generic driver version 2.4.2
[    0.913509] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.913537] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.913557] uhci_hcd: USB Universal Host Controller Interface driver
[    0.914050] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    0.914055] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.914067]   alloc irq_desc for 21 on node -1
[    0.914070]   alloc kstat_irqs on node -1
[    0.914086] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.914104] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.914224] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    0.914283] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000a000
[    0.914463] usb usb1: configuration #1 chosen from 1 choice
[    0.914526] hub 1-0:1.0: USB hub found
[    0.914548] hub 1-0:1.0: 2 ports detected
[    0.914628] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.914638] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.914692] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    0.914717] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000a400
[    0.914882] usb usb2: configuration #1 chosen from 1 choice
[    0.914921] hub 2-0:1.0: USB hub found
[    0.914938] hub 2-0:1.0: 2 ports detected
[    0.915004] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.915014] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.915068] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    0.915092] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000a800
[    0.915244] usb usb3: configuration #1 chosen from 1 choice
[    0.915282] hub 3-0:1.0: USB hub found
[    0.915311] hub 3-0:1.0: 2 ports detected
[    0.915466] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.916204] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.916216] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.916330] mice: PS/2 mouse device common for all mice
[    0.916513] rtc_cmos 00:04: RTC can wake from S4
[    0.916597] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.916634] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.916815] device-mapper: uevent: version 1.0.3
[    0.916991] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.917151] device-mapper: multipath: version 1.1.0 loaded
[    0.917157] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.917387] EISA: Probing bus 0 at eisa.0
[    0.917411] Cannot allocate resource for EISA slot 4
[    0.917415] Cannot allocate resource for EISA slot 5
[    0.917430] EISA: Detected 0 cards.
[    0.917576] cpuidle: using governor ladder
[    0.917644] cpuidle: using governor menu
[    0.918454] TCP cubic registered
[    0.918691] NET: Registered protocol family 10
[    0.919401] lo: Disabled Privacy Extensions
[    0.919881] NET: Registered protocol family 17
[    0.919922] Bluetooth: L2CAP ver 2.13
[    0.919925] Bluetooth: L2CAP socket layer initialized
[    0.919930] Bluetooth: SCO (Voice Link) ver 0.6
[    0.919933] Bluetooth: SCO socket layer initialized
[    0.920122] Bluetooth: RFCOMM TTY layer initialized
[    0.920128] Bluetooth: RFCOMM socket layer initialized
[    0.920131] Bluetooth: RFCOMM ver 1.11
[    0.920166] powernow-k8: Processor cpuid 681 not supported
[    0.920217] Using IPI No-Shortcut mode
[    0.920358] PM: Resume from disk failed.
[    0.920388] registered taskstats version 1
[    0.920538]   Magic number: 2:145:519
[    0.920742] rtc_cmos 00:04: setting system clock to 2010-03-14 06:31:29 UTC (1268548289)
[    0.920748] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.920751] EDD information not available.
[    0.941330] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.080551] ata1.00: ATA-5: ST380021A, 3.19, max UDMA/100
[    1.080556] ata1.00: 156301488 sectors, multi 16: LBA 
[    1.088424] ata1.00: configured for UDMA/100
[    1.088703] scsi 0:0:0:0: Direct-Access     ATA      ST380021A        3.19 PQ: 0 ANSI: 5
[    1.088924] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.089007] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.089086] sd 0:0:0:0: [sda] Write Protect is off
[    1.089091] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.089131] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.089373]  sda: sda1 sda2 < sda5 >
[    1.131038] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.260527] ata2.00: ATAPI: SONY    DVD RW DRU-510A, 1.0d, max UDMA/33
[    1.260572] ata2.01: ATAPI:         48X12X50 CD-RW    1.01 20020904, 1.01, max UDMA/33
[    1.276414] ata2.00: configured for UDMA/33
[    1.292281] ata2.01: configured for UDMA/33
[    1.294563] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DRU-510A  1.0d PQ: 0 ANSI: 5
[    1.298321] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    1.298327] Uniform CD-ROM driver Revision: 3.20
[    1.298523] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.298629] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.300274] scsi 1:0:1:0: CD-ROM                     48X12X50 CD-RW   1.01 PQ: 0 ANSI: 5
[    1.303349] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.303472] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.303550] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.303596] Freeing unused kernel memory: 540k freed
[    1.305107] Write protecting the kernel text: 4568k
[    1.305158] Write protecting the kernel read-only data: 1836k
[    1.609782] Linux agpgart interface v0.103
[    1.613870] agpgart: Detected VIA PM266/KM266 chipset
[    1.628900] Floppy drive(s): fd0 is 1.44M
[    1.666022] FDC 0 is a post-1991 82077
[    1.716402] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.716412] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    1.716893] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[    1.717804] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    1.717809] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    1.717822]   alloc irq_desc for 23 on node -1
[    1.717826]   alloc kstat_irqs on node -1
[    1.717841] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    1.841483] eth0: VIA Rhine II at 0xe0101000, 00:10:dc:fa:5a:f3, IRQ 23.
[    1.842200] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 0081.
[    3.093163] PM: Starting manual resume from disk
[    3.093175] PM: Resume from partition 8:5
[    3.093178] PM: Checking hibernation image.
[    3.093579] PM: Resume from disk failed.
[    3.125202] EXT4-fs (sda1): barriers enabled
[    3.146191] kjournald2 starting: pid 325, dev sda1:8, commit interval 5 seconds
[    3.146233] EXT4-fs (sda1): delayed allocation enabled
[    3.146239] EXT4-fs: file extents enabled
[    3.164577] EXT4-fs: mballoc enabled
[    3.164621] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.896300] type=1505 audit(1268548292.475:2): operation="profile_load" pid=348 

name=/usr/share/gdm/guest-session/Xsession
[    3.901479] type=1505 audit(1268548292.479:3): operation="profile_load" pid=349 name=/sbin/dhclient3
[    3.901933] type=1505 audit(1268548292.479:4): operation="profile_load" pid=349 

name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.902188] type=1505 audit(1268548292.479:5): operation="profile_load" pid=349 

name=/usr/lib/connman/scripts/dhclient-script
[    3.958273] type=1505 audit(1268548292.535:6): operation="profile_load" pid=350 name=/usr/bin/evince
[    3.967358] type=1505 audit(1268548292.543:7): operation="profile_load" pid=350 

name=/usr/bin/evince-previewer
[    3.972943] type=1505 audit(1268548292.551:8): operation="profile_load" pid=350 

name=/usr/bin/evince-thumbnailer
[    4.006018] type=1505 audit(1268548292.583:9): operation="profile_load" pid=352 

name=/usr/lib/cups/backend/cups-pdf
[    4.006614] type=1505 audit(1268548292.583:10): operation="profile_load" pid=352 name=/usr/sbin/cupsd
[    5.302560] Adding 642560k swap on /dev/sda5.  Priority:-1 extents:1 across:642560k 
[    5.676738] udev: starting version 147
[    5.677222] EXT4-fs (sda1): internal journal on sda1:8
[    6.490694] udev: renamed network interface eth0 to eth1
[    7.468183] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.029114] lp: driver loaded but no devices found
[    8.124209] parport_pc 00:0a: reported by Plug and Play ACPI
[    8.124327] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    8.225838] lp0: using parport0 (interrupt-driven).
[    8.246118] irda_init()
[    8.246158] NET: Registered protocol family 23
[    8.255038] ppdev: user-space parallel port driver
[    8.630579] __ratelimit: 3 callbacks suppressed
[    8.630586] type=1505 audit(1268548297.207:12): operation="profile_replace" pid=664 

name=/usr/share/gdm/guest-session/Xsession
[    8.635061] type=1505 audit(1268548297.211:13): operation="profile_replace" pid=665 name=/sbin/dhclient3
[    8.635515] type=1505 audit(1268548297.211:14): operation="profile_replace" pid=665 

name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.635781] type=1505 audit(1268548297.211:15): operation="profile_replace" pid=665 

name=/usr/lib/connman/scripts/dhclient-script
[    8.652617] type=1505 audit(1268548297.231:16): operation="profile_replace" pid=666 name=/usr/bin/evince
[    8.675689] type=1505 audit(1268548297.251:17): operation="profile_replace" pid=666 

name=/usr/bin/evince-previewer
[    8.689804] type=1505 audit(1268548297.267:18): operation="profile_replace" pid=666 

name=/usr/bin/evince-thumbnailer
[    8.701487] type=1505 audit(1268548297.279:19): operation="profile_replace" pid=672 

name=/usr/lib/cups/backend/cups-pdf
[    8.702089] type=1505 audit(1268548297.279:20): operation="profile_replace" pid=672 name=/usr/sbin/cupsd
[    8.706665] type=1505 audit(1268548297.283:21): operation="profile_replace" pid=673 name=/usr/sbin/tcpdump
[   11.151017] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.962535] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   11.962543] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   11.962554]   alloc irq_desc for 22 on node -1
[   11.962558]   alloc kstat_irqs on node -1
[   11.962573] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   11.962741] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   12.124150] psmouse serio1: ID: 10 00 64
[   12.737825] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   16.300934] eth1: link up, 100Mbps, half-duplex, lpa 0x0081
[   19.697574] [drm] Initialized drm 1.1.0 20060810
[   19.701244]   alloc irq_desc for 16 on node -1
[   19.701251]   alloc kstat_irqs on node -1
[   19.701269] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.701704] [drm] Initialized savage 2.4.1 20050313 for 0000:01:00.0 on minor 0
[   20.452749] Unknown interrupt or fault at: 00000282 00000060 c0160191
[   20.452768] Pid: 1151, comm: dhclient Not tainted 2.6.31-14-generic #48-Ubuntu
[   20.452773] Call Trace:
[   20.452806]  [<c056e41c>] ? printk+0x18/0x1c
[   20.452814]  [<c0566f2d>] ignore_int+0x3d/0x46
[   20.452835]  [<c0160191>] ? __hrtimer_start_range_ns+0x1/0x320
[   20.452841]  [<c0160191>] ? __hrtimer_start_range_ns+0x1/0x320
[   20.452847]  [<c0160501>] ? hrtimer_start_range_ns+0x21/0x30
[   20.452854]  [<c056fa44>] schedule_hrtimeout_range+0xc4/0x150
[   20.452861]  [<c015f580>] ? hrtimer_wakeup+0x0/0x20
[   20.452872]  [<c01f5b41>] poll_schedule_timeout+0x31/0x50
[   20.452877]  [<c01f6374>] do_select+0x554/0x660
[   20.452888]  [<c030e093>] ? cfq_service_tree_add+0x143/0x270
[   20.452894]  [<c01f6480>] ? __pollwait+0x0/0xd0
[   20.452900]  [<c01f6550>] ? pollwake+0x0/0x60
[   20.452905]  [<c01f6550>] ? pollwake+0x0/0x60
[   20.452915]  [<c013d548>] ? enqueue_task_fair+0x68/0x70
[   20.452923]  [<c014232b>] ? check_preempt_wakeup+0x1db/0x220
[   20.452928]  [<c013c347>] ? try_to_wake_up+0xf7/0x350
[   20.452934]  [<c013c5ab>] ? default_wake_function+0xb/0x10
[   20.452939]  [<c01f659f>] ? pollwake+0x4f/0x60
[   20.452949]  [<c0127c38>] ? default_spin_lock_flags+0x8/0x10
[   20.452955]  [<c05707da>] ? _spin_lock_irqsave+0x2a/0x40
[   20.453006]  [<de82d099>] ? rhine_start_tx+0x169/0x2c0 [via_rhine]
[   20.453017]  [<c049c99d>] ? dev_hard_start_xmit+0x1ad/0x210
[   20.453023]  [<c05708b8>] ? _spin_lock+0x8/0x10
[   20.453036]  [<c04b0227>] ? __qdisc_run+0xd7/0x210
[   20.453043]  [<c048fda3>] ? sock_wmalloc+0x43/0x70
[   20.453049]  [<c049ecab>] ? dev_queue_xmit+0xdb/0x440
[   20.453056]  [<c053b9d4>] ? packet_sendmsg_spkt+0x1c4/0x1e0
[   20.453069]  [<c048d380>] ? sock_sendmsg+0xe0/0x110
[   20.453075]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
[   20.453081]  [<c01f6b76>] core_sys_select+0x146/0x2a0
[   20.453087]  [<c048d92d>] ? sys_sendto+0xdd/0x120
[   20.453094]  [<c01cb5f2>] ? do_wp_page+0xd2/0x7c0
[   20.453102]  [<c012d347>] ? kmap_atomic_prot+0x47/0xf0
[   20.453117]  [<c02c7acf>] ? security_file_permission+0xf/0x20
[   20.453128]  [<c0165316>] ? getnstimeofday+0x56/0x110
[   20.453133]  [<c015fd8c>] ? ktime_get_ts+0x4c/0x60
[   20.453139]  [<c01f6ebc>] sys_select+0x2c/0xb0
[   20.453145]  [<c010336c>] syscall_call+0x7/0xb
[   25.288290] do_IRQ: 0.33 No irq handler for vector (irq -1)
[   26.592043] eth1: no IPv6 routers present
[   30.950382] __ratelimit: 8 callbacks suppressed
[   43.350167] ata2: drained 4 bytes to clear DRQ.
[   43.350191] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   43.350200] ata2.01: ST-ATAPI: DRQ=1 with device error, dev_stat 0x59
[   43.350221] ata2.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 16392 in
[   43.350223]          cdb 46 02 00 00 00 00 00 00  08 00 00 00 00 00 00 00
[   43.350225]          res 59/20:02:00:08:00/00:00:00:00:00/b0 Emask 0x2 (HSM violation)
[   43.350231] ata2.01: status: { DRDY DRQ ERR }
[   43.350274] ata2: soft resetting link
[   43.536529] ata2.00: configured for UDMA/33
[   43.552312] ata2.01: configured for UDMA/33
[   43.552952] ata2: EH complete
[   46.308650] __ratelimit: 6 callbacks suppressed
[   51.888606] __ratelimit: 2 callbacks suppressed
[   94.816075] ------------[ cut here ]------------
[   94.816110] WARNING: at /build/buildd/linux-2.6.31/net/sched/sch_generic.c:246 dev_watchdog+0x1f6/0x210()
[   94.816115] Hardware name: KM266-8235
[   94.816119] NETDEV WATCHDOG: eth1 (via-rhine): transmit queue 0 timed out
[   94.816122] Modules linked in: savage drm binfmt_misc psmouse snd_via82xx gameport serio_raw shpchp 

i2c_viapro via_ircc snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_mpu401_uart 

snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd 

ppdev irda soundcore crc_ccitt parport_pc iptable_filter ip_tables x_tables lp parport via_rhine mii floppy 

via_agp agpgart
[   94.816179] Pid: 1497, comm: polkitd Not tainted 2.6.31-14-generic #48-Ubuntu
[   94.816183] Call Trace:
[   94.816206]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
[   94.816212]  [<c04b07c6>] ? dev_watchdog+0x1f6/0x210
[   94.816218]  [<c04b07c6>] ? dev_watchdog+0x1f6/0x210
[   94.816224]  [<c0145206>] warn_slowpath_fmt+0x26/0x30
[   94.816230]  [<c04b07c6>] dev_watchdog+0x1f6/0x210
[   94.816242]  [<c0157fdb>] ? insert_work+0x5b/0xa0
[   94.816254]  [<c0127c38>] ? default_spin_lock_flags+0x8/0x10
[   94.816262]  [<c05707da>] ? _spin_lock_irqsave+0x2a/0x40
[   94.816268]  [<c0158371>] ? __queue_work+0x31/0x40
[   94.816273]  [<c01501b7>] run_timer_softirq+0x117/0x200
[   94.816287]  [<c016a125>] ? tick_dev_program_event+0x45/0xe0
[   94.816292]  [<c04b05d0>] ? dev_watchdog+0x0/0x210
[   94.816303]  [<c014b3b0>] __do_softirq+0x90/0x1a0
[   94.816314]  [<c015ff63>] ? hrtimer_interrupt+0x183/0x210
[   94.816320]  [<c014b4fd>] do_softirq+0x3d/0x40
[   94.816325]  [<c014b63d>] irq_exit+0x5d/0x70
[   94.816331]  [<c011dcf7>] smp_apic_timer_interrupt+0x57/0x90
[   94.816339]  [<c0103d71>] apic_timer_interrupt+0x31/0x40
[   94.816344] ---[ end trace e33245e2de2c7c7a ]---
[   94.816492] eth1: Transmit timed out, status 0003, PHY status 786d, resetting...
[   94.817250] eth1: link up, 100Mbps, half-duplex, lpa 0x0081
[  132.663913] __ratelimit: 5 callbacks suppressed
[  137.801055] __ratelimit: 11 callbacks suppressed
[  213.010178] __ratelimit: 11 callbacks suppressed
[  415.000190] eth1: Transmit timed out, status 0003, PHY status 786d, resetting...
[  415.000372] via-rhine: Reset not complete yet. Trying harder.
[  415.000952] eth1: link up, 100Mbps, half-duplex, lpa 0x0081
[  427.000230] eth1: Transmit timed out, status 0002, PHY status 786d, resetting...
[  427.000990] eth1: link up, 100Mbps, half-duplex, lpa 0x0081
[  435.000200] eth1: Transmit timed out, status 0002, PHY status 786d, resetting...
[  435.000949] eth1: link up, 100Mbps, half-duplex, lpa 0x0081
[  581.035613] __ratelimit: 11 callbacks suppressed
[  863.000215] eth1: Transmit timed out, status 0003, PHY status 786d, resetting...
[  863.000996] eth1: link up, 100Mbps, half-duplex, lpa 0x0081

```

Thanks again for your help.

---

### Post by FlyingMonkey38 on 2010-03-15
Any guidance is appreciated!

---

### Post by Pastortom on 2010-03-22
I have the same problem with my Asus P7P55Deluxe (i5 cpu + 2x 9500GT + 2x2gb dominator), the built in NIC seems to be acting up really crazy with Ubuntu..

Atm, after 12 hours of this nonsense, I am now installing Windows XP back just to see that Ubuntu hasnt DESTROYeD my built-on network card =/

Oh, and Ive got RealTek 8111/8186B network card

---

### Post by johnson.d on 2010-03-23
You can perform the following checks:
1) If you have another machine in the same network you can try pinging the DHCP server.
2) Check the network connections, and check whether the DHCP requests from your Ubuntu machine reaches the DHCP server.
3) You can try network sniffing tools like wireshark to get more details while running the dhclient command.

---

### Post by dineshs on 2010-03-23
> 

When I manually configure the IP address, it shows the network connection as connected, but it is unable to ping and/or connect to the internet (except for localhost and the assigned IP address).  I used 192.168.11 as the IP, 255.255.255.0 as the netmask, and 192.168.1.1 as the gateway.



Did you try this

```
sudo dhclient
```
How did you manually configure network?I suggest you read
[http://ubuntuforums.org/showthread.php?p=8975701#post8975701](http://ubuntuforums.org/showthread.php?p=8975701#post8975701)

---

### Post by mickoes on 2010-09-30
> **dineshs said:**
> Did you try this

```
sudo dhclient
```How did you manually configure network?I suggest you read
[http://ubuntuforums.org/showthread.php?p=8975701#post8975701](http://ubuntuforums.org/showthread.php?p=8975701#post8975701)

Hello!

Sorry to bring back old thread to life.. but it seems like I'm having the same problem with my Ubuntu 10.04 install.

The following command results:

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:19:66:4c:ab:69
Sending on   LPF/eth0/00:19:66:4c:ab:69
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

At first it seems like my DHCP is not able to get an automatic IP from my gateway (192.168.0.1).  When I attempt to assign a static IP, I get a sucessful connection but however I cannot ping anybody on the network including the gateway.  I checked on my router and it seems that I am not registered as a LAN user (not registered at all actually).

My other computers on the network work fine, including another ubuntu netbook with the same version.  The networking part of this machine seems to be working, well at least for my mobile internet stick!

Hope someone will be able to help!

n.b: I have the same lspci lsmod than the guy above.

---

### Post by Oblong_Cheese on 2010-12-06
I am not sure how to specify this on an existing install (possibly here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)) but booting with "noapic" (disabling APIC) may help.

---

