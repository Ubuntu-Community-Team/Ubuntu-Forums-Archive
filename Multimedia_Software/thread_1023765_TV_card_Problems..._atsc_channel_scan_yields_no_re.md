---
title: "TV card Problems... atsc channel scan yields no results with Hauppauge WinTV-HVR 1800"
date: 2008-12-28
forum: Multimedia Software
---

### Post by donavan on 2008-12-28
I have been at this for about a week now and I can't seem to get past the point where you do the scan for the channel frequencies. I have tried running the scan using 'scan' , kaffeine, and tvtime, and and get no static or channels. I have also upgrade the v4l packs and nothing came of it ...Here is my setup:

Rig;
Ubuntu 8.10 (fully patched)
pentium d 2.4
2 GB ram
120gb primary HD
ati radeon x1650pro
*Hauppauge WinTV-HVR 1800*

I have 3 devices attached to a Comcast cable line ( cable modem/phone, 1 cable box w/ tv , the TVcard)
I have tried to use both the analog and the the digital inputs on the card and I get the same results (or lack of results).


When I scan I get something similar to this no matter what I use as my frequency list.

/*scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-CA-SF-Bay-Area*
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-CA-SF-Bay-Area
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 503000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 503000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 551000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 551000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 563000000:8VSB
^Z
[1]+ Stopped scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-CA-SF-Bay-Area/

and this will continue for the entirety of the list if I don't stop it

If I run it with more parameters I get this

/*scan -v -5 -A 2 /usr/share/doc/dvb-utils/examples/scan/atsc/us-CA-SF-Bay-Area*
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-CA-SF-Bay-Area
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 503000000:8VSB
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
>>> tune to: 503000000:8VSB (tuning failed)
/
This again continues till its done with the list.

Here is all the stuff that everyone asks me for in the IRC channel, If anyone can please tell me where I am going wrong or what I missed along the way it would be awesome and save me a major headache.

/
*ls -l /dev/dvb/adapter0/*
total 0
crw-rw----+ 1 root video 212, 1 2008-12-27 00:05 demux0
crw-rw----+ 1 root video 212, 2 2008-12-27 00:05 dvr0
crw-rw----+ 1 root video 212, 0 2008-12-27 00:05 frontend0
crw-rw----+ 1 root video 212, 3 2008-12-27 00:05 net0/*
*
/*dmesg*
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000007ffc0000 (usable)
[ 0.000000] BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[ 0.000000] BIOS-e820: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[ 0.000000] last_pfn = 0x7ffc0 max_arch_pfn = 0x100000
[ 0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[ 0.000000] RAMDISK: 377d2000 - 37fef54d
[ 0.000000] DMI 2.3 present.
[ 0.000000] ACPI: RSDP 000F90A0, 0014 (r0 ACPIAM)
[ 0.000000] ACPI: RSDT 7FFC0000, 0034 (r1 A M I OEMRSDT 1000627 MSFT 97)
[ 0.000000] ACPI: FACP 7FFC0200, 0084 (r2 A M I OEMFACP 1000627 MSFT 97)
[ 0.000000] ACPI: DSDT 7FFC0430, 42CC (r1 945P 945PA 0 INTL 2002026)
[ 0.000000] ACPI: FACS 7FFCE000, 0040
[ 0.000000] ACPI: APIC 7FFC0390, 005C (r1 A M I OEMAPIC 1000627 MSFT 97)
[ 0.000000] ACPI: MCFG 7FFC03F0, 003C (r1 A M I OEMMCFG 1000627 MSFT 97)
[ 0.000000] ACPI: OEMB 7FFCE040, 0046 (r1 A M I AMI_OEM 1000627 MSFT 97)
[ 0.000000] 1151MB HIGHMEM available.
[ 0.000000] 896MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 38000000
[ 0.000000] low ram: 00000000 - 38000000
[ 0.000000] bootmap 00008000 - 0000f000
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 00005c0a20] TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[ 0.000000] #4 [00377d2000 - 0037fef54d] RAMDISK ==> [00377d2000 - 0037fef54d]
[ 0.000000] #5 [00005c1000 - 00005c4000] INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[ 0.000000] #6 [000009fc00 - 0000100000] BIOS reserved ==> [000009fc00 - 0000100000]
[ 0.000000] #7 [0000007000 - 0000008000] PGTABLE ==> [0000007000 - 0000008000]
[ 0.000000] #8 [0000008000 - 000000f000] BOOTMAP ==> [0000008000 - 000000f000]
[ 0.000000] found SMP MP-table at [c00ff780] 000ff780
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000000 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x00038000
[ 0.000000] HighMem 0x00038000 -> 0x0007ffc0
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[2] active PFN ranges
[ 0.000000] 0: 0x00000000 -> 0x0000009f
[ 0.000000] 0: 0x00000100 -> 0x0007ffc0
[ 0.000000] On node 0 totalpages: 524127
[ 0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[ 0.000000] DMA zone: 3963 pages, LIFO batch:0
[ 0.000000] Normal zone: 223300 pages, LIFO batch:31
[ 0.000000] HighMem zone: 292256 pages, LIFO batch:31
[ 0.000000] ACPI: PM-Timer IO Port: 0x808
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[ 0.000000] mapped APIC to ffffb000 (fee00000)
[ 0.000000] mapped IOAPIC to ffffa000 (fec00000)
[ 0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[ 0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[ 0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[ 0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 519519
[ 0.000000] Kernel command line: root=UUID=847ea380-3918-4522-8f3e-35cc7f082b26 ro quiet splash
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] TSC: PIT calibration confirmed by PMTIMER.
[ 0.000000] TSC: using PMTIMER calibration value
[ 0.000000] Detected 2959.026 MHz processor.
[ 0.004000] Console: colour VGA+ 80x25
[ 0.004000] console [tty0] enabled
[ 0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.004000] Memory: 2063040k/2096896k available (2572k kernel code, 32572k reserved, 1160k data, 424k init, 1179392k highmem)
[ 0.004000] virtual kernel memory layout:
[ 0.004000] fixmap : 0xffc77000 - 0xfffff000 (3616 kB)
[ 0.004000] pkmap : 0xff400000 - 0xff800000 (4096 kB)
[ 0.004000] vmalloc : 0xf8800000 - 0xff3fe000 ( 107 MB)
[ 0.004000] lowmem : 0xc0000000 - 0xf8000000 ( 896 MB)
[ 0.004000] .init : 0xc04ab000 - 0xc0515000 ( 424 kB)
[ 0.004000] .data : 0xc038335a - 0xc04a5680 (1160 kB)
[ 0.004000] .text : 0xc0100000 - 0xc038335a (2572 kB)
[ 0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[ 0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[ 0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 5918.05 BogoMIPS (lpj=11836104)
[ 0.004034] Security Framework initialized
[ 0.004041] SELinux: Disabled at boot.
[ 0.004065] AppArmor: AppArmor initialized
[ 0.004079] Mount-cache hash table entries: 512
[ 0.004281] Initializing cgroup subsys ns
[ 0.004287] Initializing cgroup subsys cpuacct
[ 0.004290] Initializing cgroup subsys memory
[ 0.004312] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 0.004316] CPU: L2 cache: 1024K
[ 0.004319] CPU: Physical Processor ID: 0
[ 0.004321] CPU: Processor Core ID: 0
[ 0.004325] using mwait in idle threads.
[ 0.004339] Checking 'hlt' instruction... OK.
[ 0.022609] ACPI: Core revision 20080609
[ 0.024916] ACPI: Checking initramfs for custom DSDT
[ 0.364229] ENABLING IO-APIC IRQs
[ 0.364412] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.407484] CPU0: Intel(R) Pentium(R) D CPU 2.66GHz stepping 07
[ 0.408025] Booting processor 1/1 ip 6000
[ 0.004000] Initializing CPU#1
[ 0.004000] Calibrating delay using timer specific routine.. 8285.96 BogoMIPS (lpj=16571926)
[ 0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 0.004000] CPU: L2 cache: 1024K
[ 0.004000] CPU: Physical Processor ID: 0
[ 0.004000] CPU: Processor Core ID: 1
[ 0.492385] CPU1: Intel(R) Pentium(R) D CPU 2.66GHz stepping 07
[ 0.492404] checking TSC synchronization [CPU#0 -> CPU#1]:
[ 0.496031] Measured 831258480 cycles TSC warp between CPUs, turning off TSC clock.
[ 0.496031] Marking TSC unstable due to check_tsc_sync_source failed
[ 0.496042] Brought up 2 CPUs
[ 0.496047] Total of 2 processors activated (14204.01 BogoMIPS).
[ 0.496070] CPU0 attaching sched-domain:
[ 0.496074] domain 0: span 0-1 level CPU
[ 0.496077] groups: 0 1
[ 0.496085] CPU1 attaching sched-domain:
[ 0.496087] domain 0: span 0-1 level CPU
[ 0.496090] groups: 1 0
[ 0.496168] net_namespace: 840 bytes
[ 0.496168] Booting paravirtualized kernel on bare hardware
[ 0.496368] Time: 5:05:41 Date: 12/27/08
[ 0.496403] NET: Registered protocol family 16
[ 0.496441] EISA bus registered
[ 0.496441] ACPI: bus type pci registered
[ 0.496441] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support.
[ 0.496441] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[ 0.496441] PCI: Using configuration type 1 for base access
[ 0.500640] ACPI: EC: Look up EC in DSDT
[ 0.550364] ACPI: Interpreter enabled
[ 0.550369] ACPI: (supports S0 S1 S3 S4 S5)
[ 0.550396] ACPI: Using IOAPIC for interrupt routing
[ 0.564214] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.564214] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[ 0.564214] pci 0000:00:01.0: PME# disabled
[ 0.564222] PCI: 0000:00:1b.0 reg 10 64bit mmio: [ffafc000, ffafffff]
[ 0.564270] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[ 0.564275] pci 0000:00:1b.0: PME# disabled
[ 0.564335] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[ 0.564340] pci 0000:00:1c.0: PME# disabled
[ 0.564400] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[ 0.564405] pci 0000:00:1c.1: PME# disabled
[ 0.564454] PCI: 0000:00:1d.0 reg 20 io port: [ec00, ec1f]
[ 0.564513] PCI: 0000:00:1d.1 reg 20 io port: [e880, e89f]
[ 0.564571] PCI: 0000:00:1d.2 reg 20 io port: [e800, e81f]
[ 0.564629] PCI: 0000:00:1d.3 reg 20 io port: [e480, e49f]
[ 0.564693] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffafbc00, ffafbfff]
[ 0.564749] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.564755] pci 0000:00:1d.7: PME# disabled
[ 0.564894] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[ 0.564901] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[ 0.564906] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[ 0.564944] PCI: 0000:00:1f.2 reg 10 io port: [0, 7]
[ 0.564952] PCI: 0000:00:1f.2 reg 14 io port: [0, 3]
[ 0.564960] PCI: 0000:00:1f.2 reg 18 io port: [0, 7]
[ 0.564967] PCI: 0000:00:1f.2 reg 1c io port: [0, 3]
[ 0.564975] PCI: 0000:00:1f.2 reg 20 io port: [ffa0, ffaf]
[ 0.565002] pci 0000:00:1f.2: PME# supported from D3hot
[ 0.565007] pci 0000:00:1f.2: PME# disabled
[ 0.565056] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[ 0.565115] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[ 0.565131] PCI: 0000:01:00.0 reg 18 64bit mmio: [ff4f0000, ff4fffff]
[ 0.565139] PCI: 0000:01:00.0 reg 20 io port: [c000, c0ff]
[ 0.565151] PCI: 0000:01:00.0 reg 30 32bit mmio: [ff4c0000, ff4dffff]
[ 0.565170] pci 0000:01:00.0: supports D1
[ 0.565173] pci 0000:01:00.0: supports D2
[ 0.565203] PCI: 0000:01:00.1 reg 10 64bit mmio: [ff4e0000, ff4effff]
[ 0.565243] pci 0000:01:00.1: supports D1
[ 0.565245] pci 0000:01:00.1: supports D2
[ 0.565294] PCI: bridge 0000:00:01.0 io port: [a000, cfff]
[ 0.565299] PCI: bridge 0000:00:01.0 32bit mmio: [ff400000, ff4fffff]
[ 0.565306] PCI: bridge 0000:00:01.0 64bit mmio pref: [cff00000, efefffff]
[ 0.565420] PCI: 0000:03:00.0 reg 10 64bit mmio: [ff600000, ff7fffff]
[ 0.565502] pci 0000:03:00.0: supports D1
[ 0.565504] pci 0000:03:00.0: supports D2
[ 0.565507] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[ 0.565514] pci 0000:03:00.0: PME# disabled
[ 0.565559] PCI: bridge 0000:00:1c.1 32bit mmio: [ff500000, ff8fffff]
[ 0.565633] PCI: 0000:04:02.0 reg 20 io port: [dc00, dc1f]
[ 0.565663] pci 0000:04:02.0: supports D1
[ 0.565665] pci 0000:04:02.0: supports D2
[ 0.565668] pci 0000:04:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.565673] pci 0000:04:02.0: PME# disabled
[ 0.565732] PCI: 0000:04:02.1 reg 20 io port: [d880, d89f]
[ 0.565762] pci 0000:04:02.1: supports D1
[ 0.565764] pci 0000:04:02.1: supports D2
[ 0.565766] pci 0000:04:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.565772] pci 0000:04:02.1: PME# disabled
[ 0.565807] PCI: 0000:04:02.2 reg 10 32bit mmio: [ff9ffc00, ff9ffcff]
[ 0.565861] pci 0000:04:02.2: supports D1
[ 0.565863] pci 0000:04:02.2: supports D2
[ 0.565865] pci 0000:04:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.565871] pci 0000:04:02.2: PME# disabled
[ 0.565906] PCI: 0000:04:02.3 reg 10 32bit mmio: [ff9fe000, ff9fefff]
[ 0.565959] pci 0000:04:02.3: supports D1
[ 0.565961] pci 0000:04:02.3: supports D2
[ 0.565964] pci 0000:04:02.3: PME# supported from D0 D1 D2 D3hot
[ 0.565969] pci 0000:04:02.3: PME# disabled
[ 0.565997] PCI: 0000:04:03.0 reg 10 32bit mmio: [ff9fc000, ff9fdfff]
[ 0.566075] PCI: 0000:04:05.0 reg 10 io port: [d400, d4ff]
[ 0.566084] PCI: 0000:04:05.0 reg 14 32bit mmio: [ff9ff800, ff9ff8ff]
[ 0.566117] PCI: 0000:04:05.0 reg 30 32bit mmio: [ff9c0000, ff9dffff]
[ 0.566136] pci 0000:04:05.0: supports D1
[ 0.566138] pci 0000:04:05.0: supports D2
[ 0.566140] pci 0000:04:05.0: PME# supported from D1 D2 D3hot D3cold
[ 0.566146] pci 0000:04:05.0: PME# disabled
[ 0.568054] pci 0000:00:1e.0: transparent bridge
[ 0.568060] PCI: bridge 0000:00:1e.0 io port: [d000, dfff]
[ 0.568065] PCI: bridge 0000:00:1e.0 32bit mmio: [ff900000, ff9fffff]
[ 0.568094] bus 00 -> node 0
[ 0.568103] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.568417] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[ 0.568687] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[ 0.568838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[ 0.580868] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[ 0.580868] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[ 0.580868] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[ 0.580868] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[ 0.580949] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[ 0.581137] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[ 0.581326] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[ 0.581516] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[ 0.581606] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 98, should be 8D [20080609]
[ 0.581606] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 0.581606] pnp: PnP ACPI init
[ 0.581606] ACPI: bus type pnp registered
[ 0.588927] pnp: PnP ACPI: found 14 devices
[ 0.588927] ACPI: ACPI bus type pnp unregistered
[ 0.588927] PnPBIOS: Disabled by ACPI PNP
[ 0.588927] PCI: Using ACPI for IRQ routing
[ 0.596045] NET: Registered protocol family 8
[ 0.596048] NET: Registered protocol family 20
[ 0.596076] NetLabel: Initializing
[ 0.596080] NetLabel: domain hash size = 128
[ 0.596082] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.596100] NetLabel: unlabeled traffic allowed by default
[ 0.596183] hpet clockevent registered
[ 0.596189] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 0.596196] hpet0: 3 64-bit timers, 14318180 Hz
[ 0.597904] tracer: 772 pages allocated for 65536 entries of 48 bytes
[ 0.597907] actual entries 65620
[ 0.598035] AppArmor: AppArmor Filesystem Enabled
[ 0.598059] ACPI: RTC can wake from S4
[ 0.600044] Switched to high resolution mode on CPU 0
[ 0.600443] Switched to high resolution mode on CPU 1
[ 0.604041] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[ 0.604058] system 00:08: ioport range 0x200-0x207 has been reserved
[ 0.604062] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[ 0.604066] system 00:08: ioport range 0x800-0x87f has been reserved
[ 0.604069] system 00:08: ioport range 0x480-0x4bf has been reserved
[ 0.604073] system 00:08: iomem range 0xffb80000-0xfffffffe could not be reserved
[ 0.604077] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[ 0.604080] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[ 0.604088] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[ 0.604092] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[ 0.604100] system 00:0a: ioport range 0x290-0x29f has been reserved
[ 0.604109] system 00:0c: iomem range 0xf0000000-0xf3ffffff has been reserved
[ 0.604118] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[ 0.604121] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[ 0.604125] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[ 0.604128] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[ 0.639738] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[ 0.639743] pci 0000:00:01.0: IO window: 0xa000-0xcfff
[ 0.639749] pci 0000:00:01.0: MEM window: 0xff400000-0xff4fffff
[ 0.639754] pci 0000:00:01.0: PREFETCH window: 0x000000cff00000-0x000000efefffff
[ 0.639761] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[ 0.639764] pci 0000:00:1c.0: IO window: disabled
[ 0.639770] pci 0000:00:1c.0: MEM window: disabled
[ 0.639775] pci 0000:00:1c.0: PREFETCH window: disabled
[ 0.639783] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[ 0.639785] pci 0000:00:1c.1: IO window: disabled
[ 0.639792] pci 0000:00:1c.1: MEM window: 0xff500000-0xff8fffff
[ 0.639797] pci 0000:00:1c.1: PREFETCH window: disabled
[ 0.639806] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[ 0.639810] pci 0000:00:1e.0: IO window: 0xd000-0xdfff
[ 0.639817] pci 0000:00:1e.0: MEM window: 0xff900000-0xff9fffff
[ 0.639822] pci 0000:00:1e.0: PREFETCH window: 0x00000088000000-0x000000880fffff
[ 0.639843] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 0.639849] pci 0000:00:01.0: setting latency timer to 64
[ 0.639859] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 0.639864] pci 0000:00:1c.0: setting latency timer to 64
[ 0.639875] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 0.639881] pci 0000:00:1c.1: setting latency timer to 64
[ 0.639889] pci 0000:00:1e.0: setting latency timer to 64
[ 0.639894] bus: 00 index 0 io port: [0, ffff]
[ 0.639897] bus: 00 index 1 mmio: [0, ffffffff]
[ 0.639900] bus: 01 index 0 io port: [a000, cfff]
[ 0.639903] bus: 01 index 1 mmio: [ff400000, ff4fffff]
[ 0.639905] bus: 01 index 2 mmio: [cff00000, efefffff]
[ 0.639908] bus: 01 index 3 mmio: [0, 0]
[ 0.639910] bus: 02 index 0 mmio: [0, 0]
[ 0.639913] bus: 02 index 1 mmio: [0, 0]
[ 0.639915] bus: 02 index 2 mmio: [0, 0]
[ 0.639917] bus: 02 index 3 mmio: [0, 0]
[ 0.639920] bus: 03 index 0 mmio: [0, 0]
[ 0.639922] bus: 03 index 1 mmio: [ff500000, ff8fffff]
[ 0.639925] bus: 03 index 2 mmio: [0, 0]
[ 0.639927] bus: 03 index 3 mmio: [0, 0]
[ 0.639930] bus: 04 index 0 io port: [d000, dfff]
[ 0.639932] bus: 04 index 1 mmio: [ff900000, ff9fffff]
[ 0.639935] bus: 04 index 2 mmio: [88000000, 880fffff]
[ 0.639937] bus: 04 index 3 io port: [0, ffff]
[ 0.639940] bus: 04 index 4 mmio: [0, ffffffff]
[ 0.639953] NET: Registered protocol family 2
[ 0.652085] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.652441] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.652841] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.653138] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.653141] TCP reno registered
[ 0.660118] NET: Registered protocol family 1
[ 0.660283] checking if image is initramfs... it is
[ 1.368105] Freeing initrd memory: 8309k freed
[ 1.369718] audit: initializing netlink socket (disabled)
[ 1.369742] type=2000 audit(1230354341.368:1): initialized
[ 1.375164] highmem bounce pool size: 64 pages
[ 1.375174] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 1.378902] VFS: Disk quotas dquot_6.5.1
[ 1.379038] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1.379185] msgmni has been set to 1743
[ 1.379362] io scheduler noop registered
[ 1.379366] io scheduler anticipatory registered
[ 1.379369] io scheduler deadline registered
[ 1.379384] io scheduler cfq registered (default)
[ 1.379503] pci 0000:01:00.0: Boot video device
[ 1.379730] pcieport-driver 0000:00:01.0: setting latency timer to 64
[ 1.379777] pcieport-driver 0000:00:01.0: found MSI capability
[ 1.379818] pci_express 0000:00:01.0:pcie00: allocate port service
[ 1.379954] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[ 1.379994] pcieport-driver 0000:00:1c.0: found MSI capability
[ 1.380038] pci_express 0000:00:1c.0:pcie00: allocate port service
[ 1.380109] pci_express 0000:00:1c.0:pcie02: allocate port service
[ 1.380244] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[ 1.380284] pcieport-driver 0000:00:1c.1: found MSI capability
[ 1.380326] pci_express 0000:00:1c.1:pcie00: allocate port service
[ 1.380398] pci_express 0000:00:1c.1:pcie02: allocate port service
[ 1.380963] isapnp: Scanning for PnP cards...
[ 1.597008] Clocksource tsc unstable (delta = 280933512 ns)
[ 1.873234] isapnp: No Plug & Play device found
[ 1.929222] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[ 1.929383] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.929578] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 1.930390] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 1.930792] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.933642] brd: module loaded
[ 1.933745] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 1.934042] PNP: No PS/2 controller found. Probing ports directly.
[ 1.936718] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1.936730] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1.937179] mice: PS/2 mouse device common for all mice
[ 1.937378] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[ 1.937405] rtc0: alarms up to one month, hpet irqs
[ 1.937625] EISA: Probing bus 0 at eisa.0
[ 1.937660] EISA: Detected 0 cards.
[ 1.937664] cpuidle: using governor ladder
[ 1.937667] cpuidle: using governor menu
[ 1.938407] TCP cubic registered
[ 1.938442] Using IPI No-Shortcut mode
[ 1.938725] registered taskstats version 1
[ 1.938881] Magic number: 4:108:63
[ 1.939003] rtc_cmos 00:03: setting system clock to 2008-12-27 05:05:42 UTC (1230354342)
[ 1.939007] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1.939010] EDD information not available.
[ 1.939308] Freeing unused kernel memory: 424k freed
[ 1.939375] Write protecting the kernel text: 2576k
[ 1.939416] Write protecting the kernel read-only data: 936k
[ 2.016558] compcache: Compressed swap size set to: 518168 KB
[ 2.017367] TLSF: pool: f8826000, init_size=16384, max_size=0, grow_size=16384
[ 2.169153] fuse init (API version 7.9)
[ 2.285281] ACPI: &#65533; FFFF0000, 0000 (r0 0 0)
[ 2.285300] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU1._PDC] (Node f7012150), AE_BAD_HEADER
[ 2.285486] processor ACPI0007:00: registered as cooling_device0
[ 2.285493] ACPI: Processor [CPU1] (supports 8 throttling states)
[ 2.342564] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU2._PDC] (Node f70121e0), AE_ALREADY_EXISTS
[ 2.342574] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
[ 2.396029] processor ACPI0007:01: registered as cooling_device1
[ 2.396035] ACPI: Processor [CPU2] (supports 8 throttling states)
[ 2.399351] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080609]
[ 2.734047] usbcore: registered new interface driver usbfs
[ 2.734080] usbcore: registered new interface driver hub
[ 2.743689] usbcore: registered new device driver usb
[ 2.757654] USB Universal Host Controller Interface driver v3.0
[ 2.757721] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 2.757734] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2.757739] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 2.757808] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[ 2.757848] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ec00
[ 2.758062] usb usb1: configuration #1 chosen from 1 choice
[ 2.758100] hub 1-0:1.0: USB hub found
[ 2.758112] hub 1-0:1.0: 2 ports detected
[ 2.880300] No dock devices found.
[ 2.900156] SCSI subsystem initialized
[ 2.925243] Adding 518164k swap on /dev/ramzswap0. Priority:100 extents:1 across:518164k
[ 2.938621] libata version 3.00 loaded.
[ 2.964383] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 2.964395] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2.964401] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 2.964436] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[ 2.964472] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e880
[ 2.964593] usb usb2: configuration #1 chosen from 1 choice
[ 2.964633] hub 2-0:1.0: USB hub found
[ 2.964644] hub 2-0:1.0: 2 ports detected
[ 3.068401] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3.068415] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 3.068421] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 3.068464] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[ 3.068505] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[ 3.068638] usb usb3: configuration #1 chosen from 1 choice
[ 3.068678] hub 3-0:1.0: USB hub found
[ 3.068689] hub 3-0:1.0: 2 ports detected
[ 3.076038] usb 1-2: new low speed USB device using uhci_hcd and address 2
[ 3.254090] usb 1-2: configuration #1 chosen from 1 choice
[ 3.276400] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[ 3.276413] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 3.276418] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 3.276457] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[ 3.276496] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e480
[ 3.276628] usb usb4: configuration #1 chosen from 1 choice
[ 3.276667] hub 4-0:1.0: USB hub found
[ 3.276677] hub 4-0:1.0: 2 ports detected
[ 3.380560] uhci_hcd 0000:04:02.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3.380575] uhci_hcd 0000:04:02.0: UHCI Host Controller
[ 3.380603] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 3.380624] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 3.380632] uhci_hcd 0000:04:02.0: new USB bus registered, assigned bus number 5
[ 3.380645] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 3.380671] uhci_hcd 0000:04:02.0: irq 19, io base 0x0000dc00
[ 3.380706] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 6
[ 3.380822] usb usb5: configuration #1 chosen from 1 choice
[ 3.380861] hub 5-0:1.0: USB hub found
[ 3.380871] hub 5-0:1.0: 2 ports detected
[ 3.384611] ehci_hcd 0000:00:1d.7: debug port 1
[ 3.384619] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[ 3.384629] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffafbc00
[ 3.388027] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 3.400021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 3.456046] hub 3-0:1.0: unable to enumerate USB device on port 1
[ 3.588216] uhci_hcd 0000:04:02.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[ 3.588227] uhci_hcd 0000:04:02.1: UHCI Host Controller
[ 3.588397] usb usb6: configuration #1 chosen from 1 choice
[ 3.588439] hub 6-0:1.0: USB hub found
[ 3.588451] hub 6-0:1.0: 8 ports detected
[ 3.624074] usb 1-2: USB disconnect, address 2
[ 3.796783] uhci_hcd 0000:04:02.1: new USB bus registered, assigned bus number 7
[ 3.796822] uhci_hcd 0000:04:02.1: irq 20, io base 0x0000d880
[ 3.796955] usb usb7: configuration #1 chosen from 1 choice
[ 3.796997] hub 7-0:1.0: USB hub found
[ 3.797007] hub 7-0:1.0: 2 ports detected
[ 3.964022] usb 6-5: new high speed USB device using ehci_hcd and address 3
[ 4.006277] ata_piix 0000:00:1f.2: version 2.12
[ 4.006298] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 4.006304] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[ 4.160039] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 4.160142] scsi0 : ata_piix
[ 4.160648] scsi1 : ata_piix
[ 4.184837] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[ 4.184841] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[ 4.536366] ata2.00: HPA unlocked: 241253376 -> 241254720, native 241254720
[ 4.536373] ata2.00: ATA-6: IC35L120AVV207-0, V24OA66A, max UDMA/100
[ 4.536377] ata2.00: 241254720 sectors, multi 16: LBA48
[ 4.560531] ata2.00: configured for UDMA/100
[ 4.560682] scsi 1:0:0:0: Direct-Access ATA IC35L120AVV207-0 V24O PQ: 0 ANSI: 5
[ 4.560827] ehci_hcd 0000:04:02.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[ 4.560847] ehci_hcd 0000:04:02.2: EHCI Host Controller
[ 4.560889] ehci_hcd 0000:04:02.2: new USB bus registered, assigned bus number 8
[ 4.560947] ehci_hcd 0000:04:02.2: irq 21, io mem 0xff9ffc00
[ 4.572022] ehci_hcd 0000:04:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 4.572214] usb usb8: configuration #1 chosen from 1 choice
[ 4.572256] hub 8-0:1.0: USB hub found
[ 4.572268] hub 8-0:1.0: 4 ports detected
[ 4.676409] ohci1394 0000:04:02.3: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 4.687372] usb 6-5: configuration #1 chosen from 1 choice
[ 4.748788] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19] MMIO=[ff9fe000-ff9fe7ff] Max Packet=[2048] IR/IT contexts=[4/4]
[ 4.757211] b43-pci-bridge 0000:04:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 4.760622] ssb: Sonics Silicon Backplane found on PCI device 0000:04:03.0
[ 4.760826] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 4.760840] r8169 0000:04:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 4.761272] eth0: RTL8110s at 0xf897c800, 00:16:ec:19:35:5e, XID 04000000 IRQ 21
[ 4.803304] usbcore: registered new interface driver hiddev
[ 4.803405] usbcore: registered new interface driver libusual
[ 4.811483] scsi 1:0:0:0: Attached scsi generic sg0 type 0
[ 4.811640] Initializing USB Mass Storage driver...
[ 4.833159] Driver 'sd' needs updating - please use bus_type methods
[ 4.833298] sd 1:0:0:0: [sda] 241254720 512-byte hardware sectors (123522 MB)
[ 4.833328] sd 1:0:0:0: [sda] Write Protect is off
[ 4.833332] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4.833384] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.833482] sd 1:0:0:0: [sda] 241254720 512-byte hardware sectors (123522 MB)
[ 4.833510] sd 1:0:0:0: [sda] Write Protect is off
[ 4.833514] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4.833564] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.833570] sda: sda1 sda2 < sda5 >
[ 4.867817] sd 1:0:0:0: [sda] Attached SCSI disk
[ 5.040026] usb 1-2: new low speed USB device using uhci_hcd and address 3
[ 5.218374] usb 1-2: configuration #1 chosen from 1 choice
[ 5.222254] scsi2 : SCSI emulation for USB Mass Storage devices
[ 5.222376] usb-storage: device found at 3
[ 5.222381] usb-storage: waiting for device to settle before scanning
[ 5.236336] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input1
[ 5.238111] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-2
[ 5.270565] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input2
[ 5.270948] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[ 5.271010] usbcore: registered new interface driver usb-storage
[ 5.271015] USB Mass Storage support registered.
[ 5.271210] usbcore: registered new interface driver usbhid
[ 5.271215] usbhid: v2.6:USB HID core driver
[ 5.383569] PM: Starting manual resume from disk
[ 5.383574] PM: Resume from partition 8:5
[ 5.383577] PM: Checking hibernation image.
[ 5.383762] PM: Resume from disk failed.
[ 5.428282] kjournald starting. Commit interval 5 seconds
[ 5.428306] EXT3-fs: mounted filesystem with ordered data mode.
[ 5.460037] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 5.610807] usb 3-2: configuration #1 chosen from 1 choice
[ 6.028243] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00004c0107004a84]
[ 10.220219] usb-storage: device scan complete
[ 10.226654] scsi 2:0:0:0: Direct-Access Generic- Compact Flash 1.00 PQ: 0 ANSI: 0 CCS
[ 10.232930] scsi 2:0:0:1: Direct-Access Generic- SM/xD-Picture 1.00 PQ: 0 ANSI: 0 CCS
[ 10.239179] scsi 2:0:0:2: Direct-Access Generic- SD/MMC 1.00 PQ: 0 ANSI: 0 CCS
[ 10.245430] scsi 2:0:0:3: Direct-Access Generic- MS/MS-Pro 1.00 PQ: 0 ANSI: 0 CCS
[ 10.247139] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 10.247300] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 10.248325] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[ 10.248402] sd 2:0:0:1: Attached scsi generic sg2 type 0
[ 10.249365] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[ 10.249439] sd 2:0:0:2: Attached scsi generic sg3 type 0
[ 10.250363] sd 2:0:0:3: [sde] Attached SCSI removable disk
[ 10.250433] sd 2:0:0:3: Attached scsi generic sg4 type 0
[ 11.654342] udevd version 124 started
[ 12.399186] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 12.453509] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 12.512737] Linux agpgart interface v0.103
[ 12.593339] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[ 12.612073] ACPI: Power Button (FF) [PWRF]
[ 12.612255] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[ 12.640037] ACPI: Power Button (CM) [PWRB]
[ 13.240643] Linux video capture interface: v2.00
[ 13.452831] iTCO_vendor_support: vendor-support=0
[ 13.540323] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[ 13.540432] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[ 13.540560] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 13.676353] prism2usb_init: prism2_usb.o: 0.2.9 Loaded
[ 13.676358] prism2usb_init: dev_info is: prism2_usb
[ 13.782550] intel_rng: FWH not detected
[ 13.816450] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 13.816483] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 13.853729] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[ 13.854182] hda_codec: Cannot set up configuration from BIOS. Using 3-stack mode...
[ 13.869296] input: PC Speaker as /devices/platform/pcspkr/input/input5
[ 14.188281] cx23885 driver version 0.0.1 loaded
[ 14.190363] cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 14.190447] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
[ 14.395681] tveeprom 0-0050: Hauppauge model 78521, rev C1E9, serial# 2727400
[ 14.395687] tveeprom 0-0050: MAC address is 00-0D-FE-29-9D-E8
[ 14.395691] tveeprom 0-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[ 14.395695] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 14.395698] tveeprom 0-0050: audio processor is CX23887 (idx 42)
[ 14.395701] tveeprom 0-0050: decoder processor is CX23887 (idx 37)
[ 14.395704] tveeprom 0-0050: has radio
[ 14.395707] cx23885[0]: hauppauge eeprom: model=78521
[ 14.435703] cx25840' 2-0044: cx25 0-21 found @ 0x88 (cx23885[0])
[ 14.458063] cx23885[0]/0: registered device video0 [v4l2]
[ 14.465462] cx23885[0]: registered device video1 [mpeg]
[ 14.465465] cx23885_dvb_register() allocating 1 frontend(s)
[ 14.465470] cx23885[0]: cx23885 based dvb card
[ 14.474918] b43-phy0: Broadcom 4306 WLAN found
[ 14.524789] phy0: Selected rate control algorithm 'pid'
[ 14.630666] MT2131: successfully identified at address 0x61
[ 14.630675] DVB: registering new adapter (cx23885[0])
[ 14.630679] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[ 14.631313] cx23885_dev_checkrevision() Hardware revision = 0xb1
[ 14.631324] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xff600000
[ 14.631334] cx23885 0000:03:00.0: setting latency timer to 64
[ 14.729665] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[ 15.134985] ident: nic h/w: id=0x8026 1.0.0
[ 15.135980] ident: pri f/w: id=0x15 1.1.3
[ 15.136973] ident: sta f/w: id=0x1f 1.7.0
[ 15.138118] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[ 15.139046] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[ 15.139983] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[ 15.140982] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/12
[ 15.141977] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[ 15.142970] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[ 15.143966] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[ 15.144966] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
[ 15.149011] usbcore: registered new interface driver prism2_usb
[ 15.574411] lp: driver loaded but no devices found
[ 15.773344] Adding 4939948k swap on /dev/sda5. Priority:-1 extents:1 across:4939948k
[ 16.354177] EXT3 FS on sda1, internal journal
[ 17.491861] type=1505 audit(1230354358.075:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4306
[ 17.550443] type=1505 audit(1230354358.134:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4311
[ 17.740434] type=1505 audit(1230354358.326:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4315
[ 17.740636] type=1505 audit(1230354358.326:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4315
[ 17.786551] type=1505 audit(1230354358.370:6): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4319
[ 17.921241] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 18.512080] linkstatus=CONNECTED
[ 19.297071] NET: Registered protocol family 17
[ 20.277441] ACPI: WMI: Mapper loaded
[ 20.406622] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
[ 23.909530] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 23.909539] apm: disabled - APM is not SMP safe.
[ 24.958597] ppdev: user-space parallel port driver
[ 30.236647] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 30.236660] vboxdrv: Successfully done.
[ 30.236664] vboxdrv: Found 2 processor cores.
[ 30.236821] vboxdrv: fAsync=1 offMin=0x318bdd4c offMax=0x318bdd4c
[ 30.236836] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[ 30.236839] vboxdrv: Successfully loaded version 2.0.6 (interface 0x00090000).
[ 36.569303] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 36.788123] [drm] Initialized drm 1.1.0 20060810
[ 36.803424] pci 0000:01:00.0: setting latency timer to 64
[ 36.804975] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[ 37.144074] [drm] Setting GART location based on new memory map
[ 37.145540] [drm] Loading R500 Microcode
[ 37.145592] [drm] Num pipes: 1
[ 37.145600] [drm] writeback test succeeded in 1 usecs
[ 38.740577] r8169: eth0: link down
[ 38.845751] input: b43-phy0 as /devices/virtual/input/input6
[ 38.913043] firmware: requesting b43/ucode5.fw
[ 39.058486] firmware: requesting b43/pcm5.fw
[ 39.201833] firmware: requesting b43/b0g0initvals5.fw
[ 39.294982] firmware: requesting b43/b0g0bsinitvals5.fw
[ 39.448039] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 39.601945] Registered led device: b43-phy0::tx
[ 39.601976] Registered led device: b43-phy0::rx
[ 39.602008] Registered led device: b43-phy0::radio
[ 40.420147] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 40.620043] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 40.820021] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 41.020036] wlan1: authentication with AP 00:1a:70:f6:ad:df timed out
[ 103.404154] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 103.405421] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 103.604024] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 103.804029] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 104.004028] wlan1: authentication with AP 00:1a:70:f6:ad:df timed out
[ 114.200087] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 114.200914] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 114.400026] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 114.600023] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 114.800026] wlan1: authentication with AP 00:1a:70:f6:ad:df timed out
[ 124.988171] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 124.988599] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 125.188027] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 125.388026] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 125.588025] wlan1: authentication with AP 00:1a:70:f6:ad:df timed out
[ 135.780224] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 135.781486] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 135.980026] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 136.180026] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 136.380023] wlan1: authentication with AP 00:1a:70:f6:ad:df timed out
[ 146.572226] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 146.572479] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 146.772021] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 146.972021] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 147.172093] wlan1: authentication with AP 00:1a:70:f6:ad:df timed out
[ 157.364371] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 157.365698] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 157.564020] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 157.764027] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 157.964021] wlan1: authentication with AP 00:1a:70:f6:ad:df timed out
[ 162.626934] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 162.824027] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 163.024037] wlan1: authenticate with AP 00:1a:70:f6:ad:df
[ 163.224234] wlan1: authentication with AP 00:1a:70:f6:ad:df timed out
[ 2236.532039] usb 6-5: reset high speed USB device using ehci_hcd and address 3
[ 2236.588901] usb 6-5: USB disconnect, address 3
[ 2236.592862] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593491] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593509] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593519] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593525] scsi 2:0:0:1: [sdc] READ CAPACITY failed
[ 2236.593528] scsi 2:0:0:1: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2236.593534] scsi 2:0:0:1: [sdc] Sense not available.
[ 2236.593541] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593548] scsi 2:0:0:1: [sdc] Write Protect is off
[ 2236.593551] scsi 2:0:0:1: [sdc] Mode Sense: 00 00 00 00
[ 2236.593555] scsi 2:0:0:1: [sdc] Assuming drive cache: write through
[ 2236.593566] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593575] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593585] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593595] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593600] scsi 2:0:0:1: [sdc] READ CAPACITY failed
[ 2236.593603] scsi 2:0:0:1: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2236.593607] scsi 2:0:0:1: [sdc] Sense not available.
[ 2236.593614] scsi 2:0:0:1: rejecting I/O to dead device
[ 2236.593620] scsi 2:0:0:1: [sdc] Write Protect is off
[ 2236.593623] scsi 2:0:0:1: [sdc] Mode Sense: 00 00 00 00
[ 2236.593625] scsi 2:0:0:1: [sdc] Assuming drive cache: write through
[ 2236.603767] scsi 2:0:0:0: rejecting I/O to dead device
[ 2236.603786] scsi 2:0:0:0: rejecting I/O to dead device
[ 2236.603797] scsi 2:0:0:0: rejecting I/O to dead device
[ 2236.603803] scsi 2:0:0:0: [sdb] READ CAPACITY failed
[ 2236.603806] scsi 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2236.603811] scsi 2:0:0:0: [sdb] Sense not available.
[ 2236.603818] scsi 2:0:0:0: rejecting I/O to dead device
[ 2236.603825] scsi 2:0:0:0: [sdb] Write Protect is off
[ 2236.603828] scsi 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 2236.603831] scsi 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2236.603846] scsi 2:0:0:0: rejecting I/O to dead device
[ 2236.603855] scsi 2:0:0:0: rejecting I/O to dead device
[ 2236.603864] scsi 2:0:0:0: rejecting I/O to dead device
[ 2236.603874] scsi 2:0:0:0: rejecting I/O to dead device
[ 2236.603879] scsi 2:0:0:0: [sdb] READ CAPACITY failed
[ 2236.603882] scsi 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2236.603886] scsi 2:0:0:0: [sdb] Sense not available.
[ 2236.603892] scsi 2:0:0:0: rejecting I/O to dead device
[ 2236.603898] scsi 2:0:0:0: [sdb] Write Protect is off
[ 2236.603901] scsi 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 2236.603904] scsi 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2236.608514] scsi 2:0:0:2: rejecting I/O to dead device// lsmod/
/[ 2236.608531] scsi 2:0:0:2: rejecting I/O to dead device
[ 2236.608538] scsi 2:0:0:2: [sdd] READ CAPACITY failed
[ 2236.608541] scsi 2:0:0:2: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2236.608545] scsi 2:0:0:2: [sdd] Sense not available.
[ 2236.608552] scsi 2:0:0:2: rejecting I/O to dead device
[ 2236.608559] scsi 2:0:0:2: [sdd] Write Protect is off
[ 2236.608562] scsi 2:0:0:2: [sdd] Mode Sense: 00 00 00 00
[ 2236.608564] scsi 2:0:0:2: [sdd] Assuming drive cache: write through
[ 2236.608574] scsi 2:0:0:2: rejecting I/O to dead device
[ 2236.608583] scsi 2:0:0:2: rejecting I/O to dead device
[ 2236.608592] scsi 2:0:0:2: rejecting I/O to dead device
[ 2236.608601] scsi 2:0:0:2: rejecting I/O to dead device
[ 2236.608607] scsi 2:0:0:2: [sdd] READ CAPACITY failed
[ 2236.608610] scsi 2:0:0:2: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2236.608614] scsi 2:0:0:2: [sdd] Sense not available.
[ 2236.608620] scsi 2:0:0:2: rejecting I/O to dead device
[ 2236.608626] scsi 2:0:0:2: [sdd] Write Protect is off
[ 2236.608629] scsi 2:0:0:2: [sdd] Mode Sense: 00 00 00 00
[ 2236.608632] scsi 2:0:0:2: [sdd] Assuming drive cache: write through
[ 2236.624365] scsi 2:0:0:3: rejecting I/O to dead device
[ 2236.624384] scsi 2:0:0:3: rejecting I/O to dead device
[ 2236.624395] scsi 2:0:0:3: rejecting I/O to dead device
[ 2236.624405] scsi 2:0:0:3: [sde] READ CAPACITY failed
[ 2236.624408] scsi 2:0:0:3: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2236.624413] scsi 2:0:0:3: [sde] Sense not available.
[ 2236.624421] scsi 2:0:0:3: rejecting I/O to dead device
[ 2236.624427] scsi 2:0:0:3: [sde] Write Protect is off
[ 2236.624430] scsi 2:0:0:3: [sde] Mode Sense: 00 00 00 00
[ 2236.624433] scsi 2:0:0:3: [sde] Assuming drive cache: write through
[ 2236.624450] scsi 2:0:0:3: rejecting I/O to dead device
[ 2236.624459] scsi 2:0:0:3: rejecting I/O to dead device
[ 2236.624468] scsi 2:0:0:3: rejecting I/O to dead device
[ 2236.624478] scsi 2:0:0:3: rejecting I/O to dead device
[ 2236.624484] scsi 2:0:0:3: [sde] READ CAPACITY failed
[ 2236.624486] scsi 2:0:0:3: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2236.624491] scsi 2:0:0:3: [sde] Sense not available.
[ 2236.624501] scsi 2:0:0:3: rejecting I/O to dead device
[ 2236.624507] scsi 2:0:0:3: [sde] Write Protect is off
[ 2236.624510] scsi 2:0:0:3: [sde] Mode Sense: 00 00 00 00
[ 2236.624513] scsi 2:0:0:3: [sde] Assuming drive cache: write through
[ 2236.744035] usb 6-5: new high speed USB device using ehci_hcd and address 5
[ 2237.921967] usb 6-5: configuration #1 chosen from 1 choice
[ 2237.923682] scsi3 : SCSI emulation for USB Mass Storage devices
[ 2237.929369] usb-storage: device found at 5
[ 2237.929378] usb-storage: waiting for device to settle before scanning
[ 2242.928215] usb-storage: device scan complete
[ 2242.934818] scsi 3:0:0:0: Direct-Access Generic- Compact Flash 1.00 PQ: 0 ANSI: 0 CCS
[ 2242.941064] scsi 3:0:0:1: Direct-Access Generic- SM/xD-Picture 1.00 PQ: 0 ANSI: 0 CCS
[ 2242.947433] scsi 3:0:0:2: Direct-Access Generic- SD/MMC 1.00 PQ: 0 ANSI: 0 CCS
[ 2242.954059] scsi 3:0:0:3: Direct-Access Generic- MS/MS-Pro 1.00 PQ: 0 ANSI: 0 CCS
[ 2242.958444] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 2242.958628] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 2242.959783] sd 3:0:0:1: [sdc] Attached SCSI removable disk
[ 2242.959890] sd 3:0:0:1: Attached scsi generic sg2 type 0
[ 2242.961703] sd 3:0:0:2: [sdd] Attached SCSI removable disk
[ 2242.961867] sd 3:0:0:2: Attached scsi generic sg3 type 0
[ 2242.962893] sd 3:0:0:3: [sde] Attached SCSI removable disk
[ 2242.963000] sd 3:0:0:3: Attached scsi generic sg4 type 0
[ 2521.533628] usb 6-5: reset high speed USB device using ehci_hcd and address 5
[ 7917.536030] usb 6-5: reset high speed USB device using ehci_hcd and address 5
[20445.536116] usb 6-5: reset high speed USB device using ehci_hcd and address 5
[21597.540187] usb 6-5: reset high speed USB device using ehci_hcd and address 5
[21755.536027] usb 6-5: reset high speed USB device using ehci_hcd and address 5
[21755.592397] usb 6-5: USB disconnect, address 5
[21755.592877] sd 3:0:0:1: [sdc] READ CAPACITY failed
[21755.592882] sd 3:0:0:1: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21755.592892] sd 3:0:0:1: [sdc] Sense not available.
[21755.597109] sd 3:0:0:1: [sdc] Write Protect is off
[21755.597113] sd 3:0:0:1: [sdc] Mode Sense: 00 00 00 00
[21755.597116] sd 3:0:0:1: [sdc] Assuming drive cache: write through
[21755.597450] sd 3:0:0:1: [sdc] READ CAPACITY failed
[21755.597453] sd 3:0:0:1: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[21755.597457] sd 3:0:0:1: [sdc] Sense not available.
[21755.597549] sd 3:0:0:1: [sdc] Write Protect is off
[21755.597553] sd 3:0:0:1: [sdc] Mode Sense: 00 00 00 00
[21755.597555] sd 3:0:0:1: [sdc] Assuming drive cache: write through
[21755.724049] usb 6-5: new high speed USB device using ehci_hcd and address 6
[21756.204341] hub 6-0:1.0: unable to enumerate USB device on port 5
[21756.448038] usb 6-5: new high speed USB device using ehci_hcd and address 7
[21756.504332] hub 6-0:1.0: unable to enumerate USB device on port 5
[21756.952027] usb 3-1: new full speed USB device using uhci_hcd and address 4
[21757.739283] usb 3-1: not running at top speed; connect to a high speed hub
[21757.771465] usb 3-1: configuration #1 chosen from 1 choice
[21757.778665] scsi4 : SCSI emulation for USB Mass Storage devices
[21757.780348] usb-storage: device found at 4
[21757.780359] usb-storage: waiting for device to settle before scanning
[21762.777632] usb-storage: device scan complete
[21762.785609] scsi 4:0:0:0: Direct-Access Generic- Compact Flash 1.00 PQ: 0 ANSI: 0 CCS
[21762.793601] scsi 4:0:0:1: Direct-Access Generic- SM/xD-Picture 1.00 PQ: 0 ANSI: 0 CCS
[21762.801604] scsi 4:0:0:2: Direct-Access Generic- SD/MMC 1.00 PQ: 0 ANSI: 0 CCS
[21762.809596] scsi 4:0:0:3: Direct-Access Generic- MS/MS-Pro 1.00 PQ: 0 ANSI: 0 CCS
[21762.817158] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[21762.817357] sd 4:0:0:0: Attached scsi generic sg1 type 0
[21762.822700] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[21762.822844] sd 4:0:0:1: Attached scsi generic sg2 type 0
[21762.827710] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[21762.827878] sd 4:0:0:2: Attached scsi generic sg3 type 0
[21762.832811] sd 4:0:0:3: [sde] Attached SCSI removable disk
[21762.832988] sd 4:0:0:3: Attached scsi generic sg4 type 0
[35523.577614] NET: Registered protocol family 10
[35523.578457] lo: Disabled Privacy Extensions
[35523.580305] ADDRCONF(NETDEV_UP): eth0: link is not ready
[35523.582096] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[35533.752022] wlan0: no IPv6 routers present


* lsmod*
Module Size Used by
ipv6 263972 10
rfkill_input 12672 0
binfmt_misc 16904 1
radeon 147616 2
drm 86056 3 radeon
vboxdrv 71576 0
ppdev 15620 0
speedstep_lib 12676 0
cpufreq_ondemand 14988 0
cpufreq_userspace 11396 0
cpufreq_powersave 9856 0
cpufreq_conservative 14600 0
cpufreq_stats 13188 0
freq_table 12672 2 cpufreq_ondemand,cpufreq_stats
wmi 14504 0
video 25104 0
output 11008 1 video
sbs 19464 0
pci_slot 12552 0
container 11520 0
sbshc 13440 1 sbs
battery 18436 0
af_packet 25728 4
iptable_filter 10752 0
ip_tables 19600 1 iptable_filter
x_tables 22916 1 ip_tables
ac 12292 0
sbp2 29324 0
parport_pc 39204 0
lp 17156 0
parport 42604 3 ppdev,parport_pc,lp
arc4 9984 2
ecb 10880 2
crypto_blkcipher 25476 1 ecb
mt2131 13572 1
s5h1409 16900 1
b43 131356 0
cx25840 36656 0
rfkill 17176 3 rfkill_input,b43
cx23885 94936 0
mac80211 216820 1 b43
compat_ioctl32 9344 1 cx23885
cx2341x 20996 1 cx23885
videobuf_dma_sg 20612 1 cx23885
cfg80211 32392 1 mac80211
videobuf_dvb 15236 1 cx23885
serio_raw 13444 0
dvb_core 94720 1 videobuf_dvb
led_class 12164 1 b43
pcspkr 10624 0
snd_hda_intel 381488 5
evdev 17696 8
input_polldev 11912 1 b43
psmouse 45200 0
prism2_usb 80260 0
snd_pcm_oss 46848 0
iTCO_wdt 18596 0
iTCO_vendor_support 11652 1 iTCO_wdt
videobuf_core 26372 3 cx23885,videobuf_dma_sg,videobuf_dvb
snd_mixer_oss 22784 1 snd_pcm_oss
p80211 38536 1 prism2_usb
v4l2_common 24576 3 cx25840,cx23885,cx2341x
videodev 49024 3 cx25840,cx23885,v4l2_common
v4l1_compat 21892 1 videodev
snd_pcm 83204 3 snd_hda_intel,snd_pcm_oss
btcx_risc 12552 1 cx23885
tveeprom 20228 1 cx23885
snd_seq_dummy 10884 0
i2c_core 31892 6 mt2131,s5h1409,cx25840,cx23885,v4l2_common,tveeprom
snd_seq_oss 38528 0
snd_seq_midi 14336 0
snd_rawmidi 29824 1 snd_seq_midi
snd_seq_midi_event 15232 2 snd_seq_oss,snd_seq_midi
snd_seq 57776 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 29960 2 snd_pcm,snd_seq
snd_seq_device 15116 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button 14224 0
intel_agp 33724 0
agpgart 42184 2 drm,intel_agp
shpchp 37908 0
pci_hotplug 35236 1 shpchp
snd 63268 18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 15328 1 snd
snd_page_alloc 16136 2 snd_hda_intel,snd_pcm
ext3 133384 1
jbd 55444 1 ext3
mbcache 16004 1 ext3
sd_mod 42264 3
crc_t10dif 9984 1 sd_mod
usb_storage 81728 0
sg 39732 0
libusual 27156 1 usb_storage
pata_acpi 12160 0
ata_generic 12932 0
usbhid 35840 0
hid 50560 1 usbhid
ata_piix 24580 2
ohci1394 37936 0
libata 177312 3 pata_acpi,ata_generic,ata_piix
scsi_mod 155212 5 sbp2,sd_mod,usb_storage,sg,libata
dock 16656 1 libata
ieee1394 96324 2 sbp2,ohci1394
r8169 35972 0
ssb 40580 1 b43
ehci_hcd 43276 0
uhci_hcd 30736 0
usbcore 148848 7 prism2_usb,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal 23708 0
processor 42156 1 thermal
fan 12548 0
fbcon 47648 0
tileblit 10880 1 fbcon
font 16512 1 fbcon
bitblit 13824 1 fbcon
softcursor 9984 1 bitblit
fuse 60828 3
compcache 13004 1
lzo_decompress 10880 1 compcache
lzo_compress 10880 1 compcache
tlsf 14220 1 compcache


*sudo lshw*
description: Desktop Computer
product: 945P-A
vendor: ECS
version: 1.X
serial: 00000000
width: 32 bits
capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
configuration: boot=normal chassis=desktop cpus=2 uuid=00020003-0004-0005-0006-000700080009
*-core
description: Motherboard
product: 945P-A
vendor: ECS
physical id: 0
version: 1.X
serial: 00000000
slot: To Be Filled By O.E.M.
*-firmware
description: BIOS
vendor: American Megatrends Inc.
physical id: 0
version: 080012 (01/27/2006)
size: 64KiB
capacity: 448KiB
capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
*-cpu:0
description: CPU
product: Intel(R) Pentium(R) D CPU 2.66GHz
vendor: Intel Corp.
physical id: 4
bus info: cpu@0
version: 15.4.7
serial: 0000-0F47-0000-0000-0000-0000
slot: CPU 1
size: 2660MHz
capacity: 2660MHz
width: 64 bits
clock: 133MHz
capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
configuration: id=1
*-cache:0
description: L1 cache
physical id: 5
slot: L1-Cache
size: 32KiB
capacity: 32KiB
capabilities: internal write-back data
*-cache:1
description: L2 cache
physical id: 6
slot: L2-Cache
size: 2MiB
capacity: 2MiB
capabilities: internal write-back unified
*-cache:2 DISABLED
description: L3 cache
physical id: 7
slot: L3-Cache
capabilities: internal
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
physical id: e
slot: System board or motherboard
size: 2GiB
*-bank:0
description: DIMM [empty]
product: PartNum0
vendor: Manufacturer0
physical id: 0
serial: SerNum0
slot: DIMM0
*-bank:1
description: DIMM SDRAM Synchronous
product: PartNum1
vendor: Manufacturer1
physical id: 1
serial: SerNum1
slot: DIMM1
size: 1GiB
width: 64 bits
*-bank:2
description: DIMM [empty]
product: PartNum2
vendor: Manufacturer2
physical id: 2
serial: SerNum2
slot: DIMM2
*-bank:3
description: DIMM SDRAM Synchronous
product: PartNum3
vendor: Manufacturer3
physical id: 3
serial: SerNum3
slot: DIMM3
size: 1GiB
width: 64 bits
*-cpu:1
physical id: 1
bus info: cpu@1
version: 15.4.7
serial: 0000-0F47-0000-0000-0000-0000
size: 18EHz
capabilities: ht
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
product: 82945G/GZ/P/PL Memory Controller Hub
vendor: Intel Corporation
physical id: 100
bus info: pci@0000:00:00.0
version: 81
width: 32 bits
clock: 33MHz
*-pci:0
description: PCI bridge
product: 82945G/GZ/P/PL PCI Express Root Port
vendor: Intel Corporation
physical id: 1
bus info: pci@0000:00:01.0
version: 81
width: 32 bits
clock: 33MHz
capabilities: pci pm msi pciexpress bus_master cap_list
configuration: driver=pcieport-driver
*-display:0 UNCLAIMED
description: VGA compatible controller
product: RV535 [Radeon X1650 Series]
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 9e
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list
configuration: latency=0
*-display:1 UNCLAIMED
description: Display controller
product: RV535 [Radeon X1650 Series]
vendor: ATI Technologies Inc
physical id: 0.1
bus info: pci@0000:01:00.1
version: 9e
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress bus_master cap_list
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
*-pci:2
description: PCI bridge
product: 82801G (ICH7 Family) PCI Express Port 2
vendor: Intel Corporation
physical id: 1c.1
bus info: pci@0000:00:1c.1
version: 01
width: 32 bits
clock: 33MHz
capabilities: pci pciexpress msi pm bus_master cap_list
configuration: driver=pcieport-driver
*-multimedia
description: Multimedia video controller
product: Conexant Systems, Inc.
vendor: Conexant Systems, Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 0f
width: 64 bits
clock: 33MHz
capabilities: pciexpress pm vpd msi bus_master cap_list
configuration: driver=cx23885 latency=0 module=cx23885
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
*-pci:3
description: PCI bridge
product: 82801 PCI Bridge
vendor: Intel Corporation
physical id: 1e
bus info: pci@0000:00:1e.0
version: e1
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
*-usb:0
description: USB Controller
product: VT82xxxxx UHCI USB 1.1 Controller
vendor: VIA Technologies, Inc.
physical id: 2
bus info: pci@0000:04:02.0
version: 61
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=uhci_hcd latency=64 module=uhci_hcd
*-usb:1
description: USB Controller
product: VT82xxxxx UHCI USB 1.1 Controller
vendor: VIA Technologies, Inc.
physical id: 2.1
bus info: pci@0000:04:02.1
version: 61
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=uhci_hcd latency=64 module=uhci_hcd
*-usb:2
description: USB Controller
product: USB 2.0
vendor: VIA Technologies, Inc.
physical id: 2.2
bus info: pci@0000:04:02.2
version: 63
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=ehci_hcd latency=64 module=ehci_hcd
*-firewire
description: FireWire (IEEE 1394)
product: uPD72873 IEEE1394 OHCI 1.1 2-port Host Controller
vendor: NEC Corporation
physical id: 2.3
bus info: pci@0000:04:02.3
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=ohci1394 latency=64 module=ohci1394
*-network:0
description: Network controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0000:04:03.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:1
description: Ethernet interface
product: RTL-8169 Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.
physical id: 5
bus info: pci@0000:04:05.0
logical name: eth0
version: 10
serial: 00:16:ec:19:35:5e
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
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
product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
vendor: Intel Corporation
physical id: 1f.2
bus info: pci@0000:00:1f.2
logical name: scsi1
version: 01
width: 32 bits
clock: 66MHz
capabilities: ide pm bus_master cap_list emulated
configuration: driver=ata_piix latency=0 module=ata_piix
*-disk
description: ATA Disk
product: IC35L120AVV207-0
vendor: Hitachi
physical id: 0.0.0
bus info: scsi@1:0.0.0
logical name: /dev/sda
version: V24O
serial: VNVD02G4H41X4T
size: 115GiB (123GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=0008941a
*-volume:0
description: EXT3 volume
vendor: Linux
physical id: 1
bus info: scsi@1:0.0.0,1
logical name: /dev/sda1
logical name: /
logical name: /dev/.static/dev
version: 1.0
serial: 847ea380-3918-4522-8f3e-35cc7f082b26
size: 110GiB
capacity: 110GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
configuration: created=2008-09-26 17:37:23 filesystem=ext3 modified=2008-12-27 00:05:11 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-12-26 22:49:20 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@1:0.0.0,2
logical name: /dev/sda2
size: 4824MiB
capacity: 4824MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 4824MiB
capabilities: nofs
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
*-scsi
physical id: 2
bus info: usb@3:1
logical name: scsi4
capabilities: emulated scsi-host
configuration: driver=usb-storage
*-disk:0
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@4:0.0.0
logical name: /dev/sdb
*-disk:1
description: SCSI Disk
physical id: 0.0.1
bus info: scsi@4:0.0.1
logical name: /dev/sdc
*-disk:2
description: SCSI Disk
physical id: 0.0.2
bus info: scsi@4:0.0.2
logical name: /dev/sdd
*-disk:3
description: SCSI Disk
physical id: 0.0.3
bus info: scsi@4:0.0.3
logical name: /dev/sde
*-network:0
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:09:5b:90:c2:89
capabilities: ethernet physical wireless
configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11-DS
*-network:1
description: Wireless interface
physical id: 2
logical name: wlan1
serial: 00:0f:66:1d:da:32
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

