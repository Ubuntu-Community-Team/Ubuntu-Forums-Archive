---
title: "Avermedia AverTV USB 2.0 not working"
date: 2008-11-07
forum: Multimedia Software
---

### Post by grafias3787 on 2008-11-07
Hello guys, I'm using Ubuntu a couple of months ago and since I dug up my TV tuner I connected it on the USB but Ubuntu made nothing, didn't detect it, didn't informed of anything being pluged in the USB.. nothing. I've searched the web for drivers but I got nothing. Please help...

---

### Post by zurih on 2009-05-09
I have AverTV USB 2.0 Plus, same issue.
Would appreciate any assistance.

---

### Post by xc3RnbFO8P on 2009-05-09
Show the output of :
> lsusb
> dmesg

---

### Post by zurih on 2009-05-09
lsusb:

```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 03f0:3611 Hewlett-Packard PSC 2410 Photosmart
Bus 005 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

dmesg:

```
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=0f774edd-2fbd-4592-9945-4c8cadd895d3 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000007fee0000
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fee0000 page 4k
[    0.000000] kernel direct mapping tables up to 7fee0000 @ 10000-14000
[    0.000000] last_map_addr: 7fee0000 end: 7fee0000
[    0.000000] RAMDISK: 3785b000 - 37feff31
[    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FEE3180, 49E4 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: HPET 7FEE7CC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FEE7D40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FEE7BC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT 7FEE7DC0, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 7FEE8250, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003785b000 - 0037feff31]          RAMDISK ==> [003785b000 - 0037feff31]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000f5110] 000f5110
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523877
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2540 pages reserved
[    0.000000]   DMA zone: 1377 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7109 pages used for memmap
[    0.000000]   DMA32 zone: 512795 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 514172
[    0.000000] Kernel command line: root=UUID=0f774edd-2fbd-4592-9945-4c8cadd895d3 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2666.982 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 20971520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2024664k/2096000k available (4760k kernel code, 492k absent, 70164k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.96 BogoMIPS (lpj=10667928)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080926
[    0.004000] ACPI: Checking initramfs for custom DSDT
[    0.252048] Setting APIC routing to flat
[    0.252388] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.293159] CPU0: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.296001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5333.31 BogoMIPS (lpj=10666625)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.380505] CPU1: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.380524] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.384033] Brought up 2 CPUs
[    0.384036] Total of 2 processors activated (10667.27 BogoMIPS).
[    0.384076] CPU0 attaching sched-domain:
[    0.384078]  domain 0: span 0-1 level MC
[    0.384080]   groups: 0 1
[    0.384084] CPU1 attaching sched-domain:
[    0.384085]  domain 0: span 0-1 level MC
[    0.384086]   groups: 1 0
[    0.384137] net_namespace: 1400 bytes
[    0.384137] Booting paravirtualized kernel on bare hardware
[    0.384210] Time: 12:50:54  Date: 05/09/09
[    0.384210] regulator: core version 0.5
[    0.384210] NET: Registered protocol family 16
[    0.384210] ACPI: bus type pci registered
[    0.384210] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.384210] PCI: MCFG area at f0000000 reserved in E820
[    0.386027] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.386028] PCI: Using configuration type 1 for base access
[    0.386040] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.386041] mtrr: probably your BIOS does not setup all CPUs.
[    0.386042] mtrr: corrected configuration.
[    0.386516] ACPI: EC: Look up EC in DSDT
[    0.392373] ACPI: Interpreter enabled
[    0.392377] ACPI: (supports S0 S3 S4 S5)
[    0.392392] ACPI: Using IOAPIC for interrupt routing
[    0.396080] ACPI: No dock devices found.
[    0.396088] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.396152] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.396155] pci 0000:00:01.0: PME# disabled
[    0.396210] pci 0000:00:1a.0: reg 20 io port: [0xe000-0xe01f]
[    0.396259] pci 0000:00:1a.1: reg 20 io port: [0xe100-0xe11f]
[    0.396307] pci 0000:00:1a.2: reg 20 io port: [0xe500-0xe51f]
[    0.396348] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfb105000-0xfb1053ff]
[    0.396405] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfb100000-0xfb103fff]
[    0.396427] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.396430] pci 0000:00:1b.0: PME# disabled
[    0.396464] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.396467] pci 0000:00:1c.0: PME# disabled
[    0.396504] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.396507] pci 0000:00:1c.3: PME# disabled
[    0.396543] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.396546] pci 0000:00:1c.4: PME# disabled
[    0.396589] pci 0000:00:1d.0: reg 20 io port: [0xe200-0xe21f]
[    0.396638] pci 0000:00:1d.1: reg 20 io port: [0xe300-0xe31f]
[    0.396686] pci 0000:00:1d.2: reg 20 io port: [0xe400-0xe41f]
[    0.396727] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfb104000-0xfb1043ff]
[    0.396844] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.396847] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.396879] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.396883] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.396887] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.396891] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.396895] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.396899] pci 0000:00:1f.2: reg 24 io port: [0xfc00-0xfc0f]
[    0.396926] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfb106000-0xfb1060ff]
[    0.396937] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.396969] pci 0000:00:1f.5: reg 10 io port: [0xe700-0xe707]
[    0.396973] pci 0000:00:1f.5: reg 14 io port: [0xe800-0xe803]
[    0.396977] pci 0000:00:1f.5: reg 18 io port: [0xe900-0xe907]
[    0.396981] pci 0000:00:1f.5: reg 1c io port: [0xea00-0xea03]
[    0.396985] pci 0000:00:1f.5: reg 20 io port: [0xeb00-0xeb0f]
[    0.396989] pci 0000:00:1f.5: reg 24 io port: [0xec00-0xec0f]
[    0.397025] pci 0000:01:00.0: reg 10 32bit mmio: [0xf6000000-0xf6ffffff]
[    0.397032] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.397039] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf4000000-0xf5ffffff]
[    0.397043] pci 0000:01:00.0: reg 24 io port: [0xa000-0xa07f]
[    0.397047] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.397083] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.397085] pci 0000:00:01.0: bridge 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.397088] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.397118] pci 0000:00:1c.0: bridge io port: [0x9000-0x9fff]
[    0.397171] pci 0000:03:00.0: reg 10 io port: [0xb000-0xb007]
[    0.397179] pci 0000:03:00.0: reg 14 io port: [0xb100-0xb103]
[    0.397186] pci 0000:03:00.0: reg 18 io port: [0xb200-0xb207]
[    0.397194] pci 0000:03:00.0: reg 1c io port: [0xb300-0xb303]
[    0.397201] pci 0000:03:00.0: reg 20 io port: [0xb400-0xb40f]
[    0.397261] pci 0000:00:1c.3: bridge io port: [0xb000-0xbfff]
[    0.397264] pci 0000:00:1c.3: bridge 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.397316] pci 0000:04:00.0: reg 10 io port: [0xc000-0xc0ff]
[    0.397335] pci 0000:04:00.0: reg 18 64bit mmio: [0xfa000000-0xfa000fff]
[    0.397354] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.397364] pci 0000:04:00.0: supports D1 D2
[    0.397365] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.397370] pci 0000:04:00.0: PME# disabled
[    0.397407] pci 0000:00:1c.4: bridge io port: [0xc000-0xcfff]
[    0.397410] pci 0000:00:1c.4: bridge 32bit mmio: [0xf9000000-0xfaffffff]
[    0.397455] pci 0000:05:00.0: reg 20 io port: [0xd000-0xd01f]
[    0.397470] pci 0000:05:00.0: supports D1 D2
[    0.397471] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot
[    0.397475] pci 0000:05:00.0: PME# disabled
[    0.397517] pci 0000:05:00.1: reg 20 io port: [0xd100-0xd11f]
[    0.397532] pci 0000:05:00.1: supports D1 D2
[    0.397533] pci 0000:05:00.1: PME# supported from D0 D1 D2 D3hot
[    0.397536] pci 0000:05:00.1: PME# disabled
[    0.397562] pci 0000:05:00.2: reg 10 32bit mmio: [0xfb000000-0xfb0000ff]
[    0.397593] pci 0000:05:00.2: supports D1 D2
[    0.397594] pci 0000:05:00.2: PME# supported from D0 D1 D2 D3hot
[    0.397597] pci 0000:05:00.2: PME# disabled
[    0.397640] pci 0000:00:1e.0: transparent bridge
[    0.397643] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.397645] pci 0000:00:1e.0: bridge 32bit mmio: [0xfb000000-0xfb0fffff]
[    0.397664] bus 00 -> node 0
[    0.397668] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.397840] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.397913] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.397987] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.398058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.410559] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.410644] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.410728] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.410810] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.410893] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.410976] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.411058] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.411141] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[    0.411291] ACPI: WMI: Mapper loaded
[    0.411341] SCSI subsystem initialized
[    0.411341] libata version 3.00 loaded.
[    0.411341] usbcore: registered new interface driver usbfs
[    0.411341] usbcore: registered new interface driver hub
[    0.411341] usbcore: registered new device driver usb
[    0.411341] PCI: Using ACPI for IRQ routing
[    0.420008] Bluetooth: Core ver 2.13
[    0.420019] NET: Registered protocol family 31
[    0.420019] Bluetooth: HCI device and connection manager initialized
[    0.420019] Bluetooth: HCI socket layer initialized
[    0.420020] NET: Registered protocol family 8
[    0.420021] NET: Registered protocol family 20
[    0.420031] NetLabel: Initializing
[    0.420032] NetLabel:  domain hash size = 128
[    0.420034] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.420045] NetLabel:  unlabeled traffic allowed by default
[    0.420072] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.420076] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.424060] AppArmor: AppArmor Filesystem Enabled
[    0.436048] pnp: PnP ACPI init
[    0.436055] ACPI: bus type pnp registered
[    0.438072] pnp: PnP ACPI: found 12 devices
[    0.438073] ACPI: ACPI bus type pnp unregistered
[    0.438079] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.438081] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.438083] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.438084] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.438086] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.438091] system 00:08: ioport range 0x400-0x4bf could not be reserved
[    0.438095] system 00:09: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.438099] system 00:0a: iomem range 0xcce00-0xcffff has been reserved
[    0.438101] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
[    0.438102] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.438104] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.438106] system 00:0a: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.438107] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.438109] system 00:0a: iomem range 0x100000-0x7fedffff could not be reserved
[    0.438111] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.438112] system 00:0a: iomem range 0xfed10000-0xfed1dfff has been reserved
[    0.438114] system 00:0a: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.438116] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.438117] system 00:0a: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.438119] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.438120] system 00:0a: iomem range 0xe0000-0xeffff has been reserved
[    0.442744] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.442746] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.442748] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.442750] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.442753] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.442755] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff
[    0.442758] pci 0000:00:1c.0:   MEM window: disabled
[    0.442761] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.442765] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.442767] pci 0000:00:1c.3:   IO window: 0xb000-0xbfff
[    0.442770] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xf8ffffff
[    0.442773] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.442777] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
[    0.442779] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.442782] pci 0000:00:1c.4:   MEM window: 0xf9000000-0xfaffffff
[    0.442785] pci 0000:00:1c.4:   PREFETCH window: 0x00000080000000-0x000000800fffff
[    0.442790] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.442792] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.442795] pci 0000:00:1e.0:   MEM window: 0xfb000000-0xfb0fffff
[    0.442797] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.442806] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442809] pci 0000:00:01.0: setting latency timer to 64
[    0.442814] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442816] pci 0000:00:1c.0: setting latency timer to 64
[    0.442822] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.442825] pci 0000:00:1c.3: setting latency timer to 64
[    0.442829] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442832] pci 0000:00:1c.4: setting latency timer to 64
[    0.442836] pci 0000:00:1e.0: setting latency timer to 64
[    0.442839] bus: 00 index 0 io port: [0x00-0xffff]
[    0.442840] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.442842] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.442843] bus: 01 index 1 mmio: [0xf4000000-0xf7ffffff]
[    0.442844] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.442845] bus: 01 index 3 mmio: [0x0-0x0]
[    0.442847] bus: 02 index 0 io port: [0x9000-0x9fff]
[    0.442848] bus: 02 index 1 mmio: [0x0-0x0]
[    0.442849] bus: 02 index 2 mmio: [0x0-0x0]
[    0.442850] bus: 02 index 3 mmio: [0x0-0x0]
[    0.442851] bus: 03 index 0 io port: [0xb000-0xbfff]
[    0.442852] bus: 03 index 1 mmio: [0xf8000000-0xf8ffffff]
[    0.442853] bus: 03 index 2 mmio: [0x0-0x0]
[    0.442854] bus: 03 index 3 mmio: [0x0-0x0]
[    0.442855] bus: 04 index 0 io port: [0xc000-0xcfff]
[    0.442857] bus: 04 index 1 mmio: [0xf9000000-0xfaffffff]
[    0.442858] bus: 04 index 2 mmio: [0x80000000-0x800fffff]
[    0.442859] bus: 04 index 3 mmio: [0x0-0x0]
[    0.442860] bus: 05 index 0 io port: [0xd000-0xdfff]
[    0.442862] bus: 05 index 1 mmio: [0xfb000000-0xfb0fffff]
[    0.442863] bus: 05 index 2 mmio: [0x0-0x0]
[    0.442864] bus: 05 index 3 io port: [0x00-0xffff]
[    0.442865] bus: 05 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.442871] NET: Registered protocol family 2
[    0.476254] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.476489] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.477569] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.478025] TCP: Hash tables configured (established 262144 bind 65536)
[    0.478026] TCP reno registered
[    0.488363] NET: Registered protocol family 1
[    0.488469] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    0.504265] Switched to high resolution mode on CPU 0
[    0.732121]  it is
[    0.990822] Freeing initrd memory: 7763k freed
[    0.993158] audit: initializing netlink socket (disabled)
[    0.993181] type=2000 audit(1241873453.992:1): initialized
[    0.999317] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.000193] VFS: Disk quotas dquot_6.5.1
[    1.000229] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.000626] fuse init (API version 7.10)
[    1.000680] msgmni has been set to 3970
[    1.000795] alg: No test for stdrng (krng)
[    1.000802] io scheduler noop registered
[    1.000804] io scheduler anticipatory registered
[    1.000805] io scheduler deadline registered
[    1.000832] io scheduler cfq registered (default)
[    1.000960] pci 0000:01:00.0: Boot video device
[    1.002846] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.002868] pcieport-driver 0000:00:01.0: found MSI capability
[    1.002884] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.002890] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.002899] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.002931] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.002956] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.002973] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.002981] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.002989] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.002999] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.003038] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.003063] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.003080] pcieport-driver 0000:00:1c.3: irq 2301 for MSI/MSI-X
[    1.003088] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.003096] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.003104] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.003143] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.003168] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.003185] pcieport-driver 0000:00:1c.4: irq 2300 for MSI/MSI-X
[    1.003193] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.003201] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.003209] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.003258] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.003473] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.003574] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.003576] ACPI: Power Button (FF) [PWRF]
[    1.003605] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.003606] ACPI: Power Button (CM) [PWRB]
[    1.003822] processor ACPI_CPU:00: registered as cooling_device0
[    1.003824] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.003957] ACPI: SSDT 7FEE81C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[    1.004100] processor ACPI_CPU:01: registered as cooling_device1
[    1.004103] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.032626] Linux agpgart interface v0.103
[    1.032634] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.032718] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.032949] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.033465] brd: module loaded
[    1.033676] loop: module loaded
[    1.033717] Fixed MDIO Bus: probed
[    1.033721] PPP generic driver version 2.4.2
[    1.033761] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.033779] Driver 'sd' needs updating - please use bus_type methods
[    1.033785] Driver 'sr' needs updating - please use bus_type methods
[    1.033836] ata_piix 0000:00:1f.2: version 2.12
[    1.033845] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.033848] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.033877] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.033930] scsi0 : ata_piix
[    1.033981] scsi1 : ata_piix
[    1.034471] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.034473] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.508048] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.524190] ata1.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    1.524194] ata1.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    1.524196] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.540297] ata1.00: configured for UDMA/133
[    2.016056] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.024574] ata2.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    2.024576] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.040588] ata2.00: configured for UDMA/133
[    2.040613] isa bounce pool size: 16 pages
[    2.040688] scsi 0:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    2.040769] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.040788] sd 0:0:0:0: [sda] Write Protect is off
[    2.040789] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.040808] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.040852] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.040862] sd 0:0:0:0: [sda] Write Protect is off
[    2.040863] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.040881] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.040883]  sda: sda2 < sda5 >
[    2.065803] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.065838] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.065901] scsi 1:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    2.065963] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.065974] sd 1:0:0:0: [sdb] Write Protect is off
[    2.065975] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.065993] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.066026] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.066036] sd 1:0:0:0: [sdb] Write Protect is off
[    2.066038] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.066055] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.066058]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    2.109624] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.109656] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.109671] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.109675] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.109708] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.109745] scsi2 : ata_piix
[    2.109785] scsi3 : ata_piix
[    2.110225] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[    2.110227] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[    2.584038] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.592185] ata3.00: ATAPI: Optiarc DVD RW AD-7220S, 1.00, max UDMA/100
[    2.608196] ata3.00: configured for UDMA/100
[    2.938568] ata4: SATA link down (SStatus 0 SControl 300)
[    2.939835] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7220S  1.00 PQ: 0 ANSI: 5
[    2.946107] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.946110] Uniform CD-ROM driver Revision: 3.20
[    2.946181] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.946214] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    2.946468] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.946488] pata_jmicron 0000:03:00.0: setting latency timer to 64
[    2.946525] scsi4 : pata_jmicron
[    2.946563] scsi5 : pata_jmicron
[    2.947083] ata5: PATA max UDMA/100 cmd 0xb000 ctl 0xb100 bmdma 0xb400 irq 19
[    2.947085] ata6: PATA max UDMA/100 cmd 0xb200 ctl 0xb300 bmdma 0xb408 irq 19
[    3.256291] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.256304] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.256318] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.256320] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.256363] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.260273] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.260281] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfb105000
[    3.276026] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.276091] usb usb1: configuration #1 chosen from 1 choice
[    3.276114] hub 1-0:1.0: USB hub found
[    3.276120] hub 1-0:1.0: 6 ports detected
[    3.276209] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.276217] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.276220] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.276256] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.280167] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.280175] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfb104000
[    3.296020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.296067] usb usb2: configuration #1 chosen from 1 choice
[    3.296087] hub 2-0:1.0: USB hub found
[    3.296093] hub 2-0:1.0: 6 ports detected
[    3.296175] ehci_hcd 0000:05:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.296183] ehci_hcd 0000:05:00.2: EHCI Host Controller
[    3.296221] ehci_hcd 0000:05:00.2: new USB bus registered, assigned bus number 3
[    3.296257] ehci_hcd 0000:05:00.2: irq 18, io mem 0xfb000000
[    3.308011] ehci_hcd 0000:05:00.2: USB 2.0 started, EHCI 1.00
[    3.308053] usb usb3: configuration #1 chosen from 1 choice
[    3.308076] hub 3-0:1.0: USB hub found
[    3.308081] hub 3-0:1.0: 4 ports detected
[    3.308152] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.308165] uhci_hcd: USB Universal Host Controller Interface driver
[    3.308182] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.308187] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.308189] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.308229] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 4
[    3.308253] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    3.308302] usb usb4: configuration #1 chosen from 1 choice
[    3.308317] hub 4-0:1.0: USB hub found
[    3.308321] hub 4-0:1.0: 2 ports detected
[    3.308376] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.308380] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.308382] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.308407] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 5
[    3.308430] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e100
[    3.308477] usb usb5: configuration #1 chosen from 1 choice
[    3.308493] hub 5-0:1.0: USB hub found
[    3.308497] hub 5-0:1.0: 2 ports detected
[    3.308549] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.308553] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.308555] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.308582] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 6
[    3.308600] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e500
[    3.308648] usb usb6: configuration #1 chosen from 1 choice
[    3.308665] hub 6-0:1.0: USB hub found
[    3.308669] hub 6-0:1.0: 2 ports detected
[    3.308725] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.308729] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.308731] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.308763] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 7
[    3.308781] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e200
[    3.308828] usb usb7: configuration #1 chosen from 1 choice
[    3.308847] hub 7-0:1.0: USB hub found
[    3.308853] hub 7-0:1.0: 2 ports detected
[    3.308907] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.308911] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.308913] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.308939] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 8
[    3.308957] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e300
[    3.309006] usb usb8: configuration #1 chosen from 1 choice
[    3.309021] hub 8-0:1.0: USB hub found
[    3.309025] hub 8-0:1.0: 2 ports detected
[    3.309079] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.309083] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.309085] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.309111] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 9
[    3.309130] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[    3.309178] usb usb9: configuration #1 chosen from 1 choice
[    3.309194] hub 9-0:1.0: USB hub found
[    3.309197] hub 9-0:1.0: 2 ports detected
[    3.309255] uhci_hcd 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.309260] uhci_hcd 0000:05:00.0: UHCI Host Controller
[    3.309288] uhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 10
[    3.309311] uhci_hcd 0000:05:00.0: irq 20, io base 0x0000d000
[    3.309358] usb usb10: configuration #1 chosen from 1 choice
[    3.309376] hub 10-0:1.0: USB hub found
[    3.309379] hub 10-0:1.0: 2 ports detected
[    3.309435] uhci_hcd 0000:05:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.309439] uhci_hcd 0000:05:00.1: UHCI Host Controller
[    3.309466] uhci_hcd 0000:05:00.1: new USB bus registered, assigned bus number 11
[    3.309484] uhci_hcd 0000:05:00.1: irq 19, io base 0x0000d100
[    3.309536] usb usb11: configuration #1 chosen from 1 choice
[    3.309553] hub 11-0:1.0: USB hub found
[    3.309558] hub 11-0:1.0: 2 ports detected
[    3.309652] usbcore: registered new interface driver libusual
[    3.309673] usbcore: registered new interface driver usbserial
[    3.309680] USB Serial support registered for generic
[    3.309692] usbcore: registered new interface driver usbserial_generic
[    3.309694] usbserial: USB Serial Driver core
[    3.309724] PNP: No PS/2 controller found. Probing ports directly.
[    3.309983] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.309987] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.320041] mice: PS/2 mouse device common for all mice
[    3.356063] rtc_cmos 00:03: RTC can wake from S4
[    3.356091] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.356112] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    3.356162] device-mapper: uevent: version 1.0.3
[    3.356237] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.356281] device-mapper: multipath: version 1.0.5 loaded
[    3.356283] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.356338] cpuidle: using governor ladder
[    3.356339] cpuidle: using governor menu
[    3.356612] TCP cubic registered
[    3.356655] NET: Registered protocol family 10
[    3.356922] lo: Disabled Privacy Extensions
[    3.357111] NET: Registered protocol family 17
[    3.357122] Bluetooth: L2CAP ver 2.11
[    3.357123] Bluetooth: L2CAP socket layer initialized
[    3.357125] Bluetooth: SCO (Voice Link) ver 0.6
[    3.357126] Bluetooth: SCO socket layer initialized
[    3.357145] Bluetooth: RFCOMM socket layer initialized
[    3.357151] Bluetooth: RFCOMM TTY layer initialized
[    3.357152] Bluetooth: RFCOMM ver 1.10
[    3.358769] registered taskstats version 1
[    3.358879]   Magic number: 9:727:834
[    3.358954] rtc_cmos 00:03: setting system clock to 2009-05-09 12:50:57 UTC (1241873457)
[    3.358956] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.358957] EDD information not available.
[    3.358984] Freeing unused kernel memory: 536k freed
[    3.359085] Write protecting the kernel read-only data: 6708k
[    3.499505] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.499521] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.499537] r8169 0000:04:00.0: setting latency timer to 64
[    3.499631] r8169 0000:04:00.0: irq 2299 for MSI/MSI-X
[    3.500034] eth0: RTL8168b/8111b at 0xffffc2000005e000, 00:1a:4d:93:1b:75, XID 38000000 IRQ 2299
[    3.836510] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    4.013625] PM: Starting manual resume from disk
[    4.013627] PM: Resume from partition 8:23
[    4.013628] PM: Checking hibernation image.
[    4.013967] PM: Resume from disk failed.
[    4.017267] usb 4-1: configuration #1 chosen from 1 choice
[    4.023325] usbcore: registered new interface driver hiddev
[    4.034333] EXT4-fs: barriers enabled
[    4.039458] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb4/4-1/4-1:1.0/input/input3
[    4.039731] kjournald2 starting.  Commit interval 5 seconds
[    4.039745] EXT4-fs: delayed allocation enabled
[    4.039746] EXT4-fs: file extents enabled
[    4.040570] EXT4-fs: mballoc enabled
[    4.040573] EXT4-fs: mounted filesystem with ordered data mode.
[    4.064082] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-1/input0
[    4.064099] usbcore: registered new interface driver usbhid
[    4.064101] usbhid: v2.6:USB HID core driver
[    4.256510] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    4.431387] usb 5-1: configuration #1 chosen from 1 choice
[    4.449586] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb5/5-1/5-1:1.0/input/input4
[    4.476064] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.1-1/input0
[    7.007874] udev: starting version 141
[    7.078297] parport_pc 00:07: reported by Plug and Play ACPI
[    7.078338] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.195486] nvidia: module license 'NVIDIA' taints kernel.
[    7.447032] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.447040] nvidia 0000:01:00.0: setting latency timer to 64
[    7.447705] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.51  Fri Apr 17 00:08:33 PDT 2009
[    7.459878] iTCO_vendor_support: vendor-support=0
[    7.463110] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    7.463211] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0460)
[    7.463277] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    7.631420] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    7.639165] ppdev: user-space parallel port driver
[    7.994817] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.994866] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.145288] lp0: using parport0 (interrupt-driven).
[    8.217951] Adding 1943792k swap on /dev/sdb7.  Priority:-1 extents:1 across:1943792k
[    8.742248] EXT4 FS on sdb1, internal journal on sdb1:8
[   10.156097] EXT4-fs: barriers enabled
[   10.175301] kjournald2 starting.  Commit interval 5 seconds
[   10.175464] EXT4 FS on sda5, internal journal on sda5:8
[   10.175466] EXT4-fs: delayed allocation enabled
[   10.175467] EXT4-fs: file extents enabled
[   10.180134] EXT4-fs: mballoc enabled
[   10.180136] EXT4-fs: mounted filesystem with ordered data mode.
[   10.200997] EXT4-fs: barriers enabled
[   10.201318] kjournald2 starting.  Commit interval 5 seconds
[   10.204217] EXT4 FS on sdb5, internal journal on sdb5:8
[   10.204219] EXT4-fs: delayed allocation enabled
[   10.204220] EXT4-fs: file extents enabled
[   10.208879] EXT4-fs: mballoc enabled
[   10.208881] EXT4-fs: mounted filesystem with ordered data mode.
[   10.234830] EXT4-fs: barriers enabled
[   10.235155] kjournald2 starting.  Commit interval 5 seconds
[   10.235584] EXT4 FS on sdb6, internal journal on sdb6:8
[   10.235586] EXT4-fs: delayed allocation enabled
[   10.235587] EXT4-fs: file extents enabled
[   10.244564] EXT4-fs: mballoc enabled
[   10.244566] EXT4-fs: mounted filesystem with ordered data mode.
[   10.505069] type=1505 audit(1241873464.645:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2113
[   10.532372] type=1505 audit(1241873464.669:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2117
[   10.532437] type=1505 audit(1241873464.669:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2117
[   10.532465] type=1505 audit(1241873464.669:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2117
[   10.532489] type=1505 audit(1241873464.669:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2117
[   10.607784] type=1505 audit(1241873464.745:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2122
[   10.607899] type=1505 audit(1241873464.745:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2122
[   10.649809] type=1505 audit(1241873464.789:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2126
[   10.666014] type=1505 audit(1241873464.805:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2130
[   14.487277] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   14.487279] vboxdrv: Successfully done.
[   14.487280] vboxdrv: Found 2 processor cores.
[   14.487329] VBoxDrv: dbg - g_abExecMemory=ffffffffa0a0aaa0
[   14.487345] vboxdrv: fAsync=0 offMin=0x1c8 offMax=0x17e0
[   14.487374] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   14.487375] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   14.691301] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0ba9940
[   19.859387] r8169: eth0: link up
[   19.859391] r8169: eth0: link up
[   30.300507] eth0: no IPv6 routers present
[ 1982.932011] usb 2-1: new high speed USB device using ehci_hcd and address 2
[ 1983.065979] usb 2-1: configuration #1 chosen from 1 choice
[ 1983.124227] usbcore: registered new interface driver snd-usb-audio
[ 1987.642928] usb 2-1: USB disconnect, address 2
[ 2058.532016] usb 2-1: new high speed USB device using ehci_hcd and address 3
[ 2058.670156] usb 2-1: configuration #1 chosen from 1 choice
[ 2058.975816] usb 2-1: USB disconnect, address 3
[ 2061.692010] usb 2-1: new high speed USB device using ehci_hcd and address 4
[ 2061.825987] usb 2-1: configuration #1 chosen from 1 choice
[ 2063.083206] usb 2-1: USB disconnect, address 4
[ 2065.472011] usb 2-1: new high speed USB device using ehci_hcd and address 5
[ 2065.605834] usb 2-1: configuration #1 chosen from 1 choice
[ 2066.691527] usb 2-1: USB disconnect, address 5
[ 2903.976016] usb 5-2: new full speed USB device using uhci_hcd and address 3
[ 2904.176409] usb 5-2: configuration #1 chosen from 1 choice
[ 2904.208130] Initializing USB Mass Storage driver...
[ 2904.209173] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2904.209760] usbcore: registered new interface driver usb-storage
[ 2904.209763] USB Mass Storage support registered.
[ 2904.209767] usb-storage: device found at 3
[ 2904.209769] usb-storage: waiting for device to settle before scanning
[ 2904.222284] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3611
[ 2904.222302] usbcore: registered new interface driver usblp
[ 2906.182093] ppdev0: registered pardevice
[ 2906.228658] ppdev0: unregistered pardevice
[ 2907.069925] usblp0: removed
[ 2909.209666] usb-storage: device scan complete
[ 2909.212654] scsi 6:0:0:0: Direct-Access     HP       psc 2410         1.00 PQ: 0 ANSI: 2
[ 2909.220060] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 2909.220127] sd 6:0:0:0: Attached scsi generic sg3 type 0
```

---

### Post by xc3RnbFO8P on 2009-05-09
Is it connected?

---

### Post by zurih on 2009-05-09
> **Ringi said:**
> Is it connected?

Of course it's connected... the device works when I switch to winxp, without changing anything.

---

### Post by xc3RnbFO8P on 2009-05-09
Can you use in XP (warm it up), reboot to Ubuntu and do dmesg.

---

### Post by zurih on 2009-05-09
Ok did it, it seems to change something.

lsusb:

```
Bus 003 Device 003: ID 07ca:0036 AVerMedia Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

dmesg
```
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=0f774edd-2fbd-4592-9945-4c8cadd895d3 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000007fee0000
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fee0000 page 4k
[    0.000000] kernel direct mapping tables up to 7fee0000 @ 10000-14000
[    0.000000] last_map_addr: 7fee0000 end: 7fee0000
[    0.000000] RAMDISK: 3785b000 - 37feff31
[    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FEE3180, 49E4 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: HPET 7FEE7CC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FEE7D40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FEE7BC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT 7FEE7DC0, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 7FEE8250, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003785b000 - 0037feff31]          RAMDISK ==> [003785b000 - 0037feff31]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000f5110] 000f5110
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523877
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2540 pages reserved
[    0.000000]   DMA zone: 1377 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7109 pages used for memmap
[    0.000000]   DMA32 zone: 512795 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 514172
[    0.000000] Kernel command line: root=UUID=0f774edd-2fbd-4592-9945-4c8cadd895d3 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2666.982 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 20971520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2024664k/2096000k available (4760k kernel code, 492k absent, 70164k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.96 BogoMIPS (lpj=10667928)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080926
[    0.004000] ACPI: Checking initramfs for custom DSDT
[    0.252048] Setting APIC routing to flat
[    0.252388] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.293159] CPU0: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.296001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5333.31 BogoMIPS (lpj=10666625)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.380505] CPU1: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.380524] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.384033] Brought up 2 CPUs
[    0.384036] Total of 2 processors activated (10667.27 BogoMIPS).
[    0.384076] CPU0 attaching sched-domain:
[    0.384078]  domain 0: span 0-1 level MC
[    0.384080]   groups: 0 1
[    0.384084] CPU1 attaching sched-domain:
[    0.384085]  domain 0: span 0-1 level MC
[    0.384086]   groups: 1 0
[    0.384137] net_namespace: 1400 bytes
[    0.384137] Booting paravirtualized kernel on bare hardware
[    0.384210] Time: 12:50:54  Date: 05/09/09
[    0.384210] regulator: core version 0.5
[    0.384210] NET: Registered protocol family 16
[    0.384210] ACPI: bus type pci registered
[    0.384210] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.384210] PCI: MCFG area at f0000000 reserved in E820
[    0.386027] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.386028] PCI: Using configuration type 1 for base access
[    0.386040] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.386041] mtrr: probably your BIOS does not setup all CPUs.
[    0.386042] mtrr: corrected configuration.
[    0.386516] ACPI: EC: Look up EC in DSDT
[    0.392373] ACPI: Interpreter enabled
[    0.392377] ACPI: (supports S0 S3 S4 S5)
[    0.392392] ACPI: Using IOAPIC for interrupt routing
[    0.396080] ACPI: No dock devices found.
[    0.396088] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.396152] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.396155] pci 0000:00:01.0: PME# disabled
[    0.396210] pci 0000:00:1a.0: reg 20 io port: [0xe000-0xe01f]
[    0.396259] pci 0000:00:1a.1: reg 20 io port: [0xe100-0xe11f]
[    0.396307] pci 0000:00:1a.2: reg 20 io port: [0xe500-0xe51f]
[    0.396348] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfb105000-0xfb1053ff]
[    0.396405] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfb100000-0xfb103fff]
[    0.396427] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.396430] pci 0000:00:1b.0: PME# disabled
[    0.396464] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.396467] pci 0000:00:1c.0: PME# disabled
[    0.396504] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.396507] pci 0000:00:1c.3: PME# disabled
[    0.396543] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.396546] pci 0000:00:1c.4: PME# disabled
[    0.396589] pci 0000:00:1d.0: reg 20 io port: [0xe200-0xe21f]
[    0.396638] pci 0000:00:1d.1: reg 20 io port: [0xe300-0xe31f]
[    0.396686] pci 0000:00:1d.2: reg 20 io port: [0xe400-0xe41f]
[    0.396727] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfb104000-0xfb1043ff]
[    0.396844] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.396847] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.396879] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.396883] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.396887] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.396891] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.396895] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.396899] pci 0000:00:1f.2: reg 24 io port: [0xfc00-0xfc0f]
[    0.396926] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfb106000-0xfb1060ff]
[    0.396937] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.396969] pci 0000:00:1f.5: reg 10 io port: [0xe700-0xe707]
[    0.396973] pci 0000:00:1f.5: reg 14 io port: [0xe800-0xe803]
[    0.396977] pci 0000:00:1f.5: reg 18 io port: [0xe900-0xe907]
[    0.396981] pci 0000:00:1f.5: reg 1c io port: [0xea00-0xea03]
[    0.396985] pci 0000:00:1f.5: reg 20 io port: [0xeb00-0xeb0f]
[    0.396989] pci 0000:00:1f.5: reg 24 io port: [0xec00-0xec0f]
[    0.397025] pci 0000:01:00.0: reg 10 32bit mmio: [0xf6000000-0xf6ffffff]
[    0.397032] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.397039] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf4000000-0xf5ffffff]
[    0.397043] pci 0000:01:00.0: reg 24 io port: [0xa000-0xa07f]
[    0.397047] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.397083] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.397085] pci 0000:00:01.0: bridge 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.397088] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.397118] pci 0000:00:1c.0: bridge io port: [0x9000-0x9fff]
[    0.397171] pci 0000:03:00.0: reg 10 io port: [0xb000-0xb007]
[    0.397179] pci 0000:03:00.0: reg 14 io port: [0xb100-0xb103]
[    0.397186] pci 0000:03:00.0: reg 18 io port: [0xb200-0xb207]
[    0.397194] pci 0000:03:00.0: reg 1c io port: [0xb300-0xb303]
[    0.397201] pci 0000:03:00.0: reg 20 io port: [0xb400-0xb40f]
[    0.397261] pci 0000:00:1c.3: bridge io port: [0xb000-0xbfff]
[    0.397264] pci 0000:00:1c.3: bridge 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.397316] pci 0000:04:00.0: reg 10 io port: [0xc000-0xc0ff]
[    0.397335] pci 0000:04:00.0: reg 18 64bit mmio: [0xfa000000-0xfa000fff]
[    0.397354] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.397364] pci 0000:04:00.0: supports D1 D2
[    0.397365] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.397370] pci 0000:04:00.0: PME# disabled
[    0.397407] pci 0000:00:1c.4: bridge io port: [0xc000-0xcfff]
[    0.397410] pci 0000:00:1c.4: bridge 32bit mmio: [0xf9000000-0xfaffffff]
[    0.397455] pci 0000:05:00.0: reg 20 io port: [0xd000-0xd01f]
[    0.397470] pci 0000:05:00.0: supports D1 D2
[    0.397471] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot
[    0.397475] pci 0000:05:00.0: PME# disabled
[    0.397517] pci 0000:05:00.1: reg 20 io port: [0xd100-0xd11f]
[    0.397532] pci 0000:05:00.1: supports D1 D2
[    0.397533] pci 0000:05:00.1: PME# supported from D0 D1 D2 D3hot
[    0.397536] pci 0000:05:00.1: PME# disabled
[    0.397562] pci 0000:05:00.2: reg 10 32bit mmio: [0xfb000000-0xfb0000ff]
[    0.397593] pci 0000:05:00.2: supports D1 D2
[    0.397594] pci 0000:05:00.2: PME# supported from D0 D1 D2 D3hot
[    0.397597] pci 0000:05:00.2: PME# disabled
[    0.397640] pci 0000:00:1e.0: transparent bridge
[    0.397643] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.397645] pci 0000:00:1e.0: bridge 32bit mmio: [0xfb000000-0xfb0fffff]
[    0.397664] bus 00 -> node 0
[    0.397668] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.397840] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.397913] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.397987] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.398058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.410559] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.410644] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.410728] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.410810] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.410893] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.410976] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.411058] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.411141] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[    0.411291] ACPI: WMI: Mapper loaded
[    0.411341] SCSI subsystem initialized
[    0.411341] libata version 3.00 loaded.
[    0.411341] usbcore: registered new interface driver usbfs
[    0.411341] usbcore: registered new interface driver hub
[    0.411341] usbcore: registered new device driver usb
[    0.411341] PCI: Using ACPI for IRQ routing
[    0.420008] Bluetooth: Core ver 2.13
[    0.420019] NET: Registered protocol family 31
[    0.420019] Bluetooth: HCI device and connection manager initialized
[    0.420019] Bluetooth: HCI socket layer initialized
[    0.420020] NET: Registered protocol family 8
[    0.420021] NET: Registered protocol family 20
[    0.420031] NetLabel: Initializing
[    0.420032] NetLabel:  domain hash size = 128
[    0.420034] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.420045] NetLabel:  unlabeled traffic allowed by default
[    0.420072] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.420076] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.424060] AppArmor: AppArmor Filesystem Enabled
[    0.436048] pnp: PnP ACPI init
[    0.436055] ACPI: bus type pnp registered
[    0.438072] pnp: PnP ACPI: found 12 devices
[    0.438073] ACPI: ACPI bus type pnp unregistered
[    0.438079] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.438081] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.438083] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.438084] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.438086] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.438091] system 00:08: ioport range 0x400-0x4bf could not be reserved
[    0.438095] system 00:09: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.438099] system 00:0a: iomem range 0xcce00-0xcffff has been reserved
[    0.438101] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
[    0.438102] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.438104] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.438106] system 00:0a: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.438107] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.438109] system 00:0a: iomem range 0x100000-0x7fedffff could not be reserved
[    0.438111] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.438112] system 00:0a: iomem range 0xfed10000-0xfed1dfff has been reserved
[    0.438114] system 00:0a: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.438116] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.438117] system 00:0a: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.438119] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.438120] system 00:0a: iomem range 0xe0000-0xeffff has been reserved
[    0.442744] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.442746] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.442748] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.442750] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.442753] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.442755] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff
[    0.442758] pci 0000:00:1c.0:   MEM window: disabled
[    0.442761] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.442765] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.442767] pci 0000:00:1c.3:   IO window: 0xb000-0xbfff
[    0.442770] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xf8ffffff
[    0.442773] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.442777] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
[    0.442779] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.442782] pci 0000:00:1c.4:   MEM window: 0xf9000000-0xfaffffff
[    0.442785] pci 0000:00:1c.4:   PREFETCH window: 0x00000080000000-0x000000800fffff
[    0.442790] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.442792] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.442795] pci 0000:00:1e.0:   MEM window: 0xfb000000-0xfb0fffff
[    0.442797] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.442806] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442809] pci 0000:00:01.0: setting latency timer to 64
[    0.442814] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442816] pci 0000:00:1c.0: setting latency timer to 64
[    0.442822] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.442825] pci 0000:00:1c.3: setting latency timer to 64
[    0.442829] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442832] pci 0000:00:1c.4: setting latency timer to 64
[    0.442836] pci 0000:00:1e.0: setting latency timer to 64
[    0.442839] bus: 00 index 0 io port: [0x00-0xffff]
[    0.442840] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.442842] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.442843] bus: 01 index 1 mmio: [0xf4000000-0xf7ffffff]
[    0.442844] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.442845] bus: 01 index 3 mmio: [0x0-0x0]
[    0.442847] bus: 02 index 0 io port: [0x9000-0x9fff]
[    0.442848] bus: 02 index 1 mmio: [0x0-0x0]
[    0.442849] bus: 02 index 2 mmio: [0x0-0x0]
[    0.442850] bus: 02 index 3 mmio: [0x0-0x0]
[    0.442851] bus: 03 index 0 io port: [0xb000-0xbfff]
[    0.442852] bus: 03 index 1 mmio: [0xf8000000-0xf8ffffff]
[    0.442853] bus: 03 index 2 mmio: [0x0-0x0]
[    0.442854] bus: 03 index 3 mmio: [0x0-0x0]
[    0.442855] bus: 04 index 0 io port: [0xc000-0xcfff]
[    0.442857] bus: 04 index 1 mmio: [0xf9000000-0xfaffffff]
[    0.442858] bus: 04 index 2 mmio: [0x80000000-0x800fffff]
[    0.442859] bus: 04 index 3 mmio: [0x0-0x0]
[    0.442860] bus: 05 index 0 io port: [0xd000-0xdfff]
[    0.442862] bus: 05 index 1 mmio: [0xfb000000-0xfb0fffff]
[    0.442863] bus: 05 index 2 mmio: [0x0-0x0]
[    0.442864] bus: 05 index 3 io port: [0x00-0xffff]
[    0.442865] bus: 05 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.442871] NET: Registered protocol family 2
[    0.476254] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.476489] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.477569] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.478025] TCP: Hash tables configured (established 262144 bind 65536)
[    0.478026] TCP reno registered
[    0.488363] NET: Registered protocol family 1
[    0.488469] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    0.504265] Switched to high resolution mode on CPU 0
[    0.732121]  it is
[    0.990822] Freeing initrd memory: 7763k freed
[    0.993158] audit: initializing netlink socket (disabled)
[    0.993181] type=2000 audit(1241873453.992:1): initialized
[    0.999317] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.000193] VFS: Disk quotas dquot_6.5.1
[    1.000229] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.000626] fuse init (API version 7.10)
[    1.000680] msgmni has been set to 3970
[    1.000795] alg: No test for stdrng (krng)
[    1.000802] io scheduler noop registered
[    1.000804] io scheduler anticipatory registered
[    1.000805] io scheduler deadline registered
[    1.000832] io scheduler cfq registered (default)
[    1.000960] pci 0000:01:00.0: Boot video device
[    1.002846] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.002868] pcieport-driver 0000:00:01.0: found MSI capability
[    1.002884] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.002890] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.002899] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.002931] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.002956] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.002973] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.002981] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.002989] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.002999] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.003038] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.003063] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.003080] pcieport-driver 0000:00:1c.3: irq 2301 for MSI/MSI-X
[    1.003088] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.003096] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.003104] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.003143] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.003168] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.003185] pcieport-driver 0000:00:1c.4: irq 2300 for MSI/MSI-X
[    1.003193] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.003201] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.003209] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.003258] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.003473] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.003574] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.003576] ACPI: Power Button (FF) [PWRF]
[    1.003605] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.003606] ACPI: Power Button (CM) [PWRB]
[    1.003822] processor ACPI_CPU:00: registered as cooling_device0
[    1.003824] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.003957] ACPI: SSDT 7FEE81C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[    1.004100] processor ACPI_CPU:01: registered as cooling_device1
[    1.004103] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.032626] Linux agpgart interface v0.103
[    1.032634] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.032718] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.032949] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.033465] brd: module loaded
[    1.033676] loop: module loaded
[    1.033717] Fixed MDIO Bus: probed
[    1.033721] PPP generic driver version 2.4.2
[    1.033761] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.033779] Driver 'sd' needs updating - please use bus_type methods
[    1.033785] Driver 'sr' needs updating - please use bus_type methods
[    1.033836] ata_piix 0000:00:1f.2: version 2.12
[    1.033845] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.033848] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.033877] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.033930] scsi0 : ata_piix
[    1.033981] scsi1 : ata_piix
[    1.034471] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.034473] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.508048] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.524190] ata1.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    1.524194] ata1.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    1.524196] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.540297] ata1.00: configured for UDMA/133
[    2.016056] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.024574] ata2.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    2.024576] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.040588] ata2.00: configured for UDMA/133
[    2.040613] isa bounce pool size: 16 pages
[    2.040688] scsi 0:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    2.040769] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.040788] sd 0:0:0:0: [sda] Write Protect is off
[    2.040789] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.040808] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.040852] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.040862] sd 0:0:0:0: [sda] Write Protect is off
[    2.040863] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.040881] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.040883]  sda: sda2 < sda5 >
[    2.065803] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.065838] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.065901] scsi 1:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    2.065963] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.065974] sd 1:0:0:0: [sdb] Write Protect is off
[    2.065975] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.065993] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.066026] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.066036] sd 1:0:0:0: [sdb] Write Protect is off
[    2.066038] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.066055] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.066058]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    2.109624] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.109656] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.109671] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.109675] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.109708] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.109745] scsi2 : ata_piix
[    2.109785] scsi3 : ata_piix
[    2.110225] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[    2.110227] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[    2.584038] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.592185] ata3.00: ATAPI: Optiarc DVD RW AD-7220S, 1.00, max UDMA/100
[    2.608196] ata3.00: configured for UDMA/100
[    2.938568] ata4: SATA link down (SStatus 0 SControl 300)
[    2.939835] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7220S  1.00 PQ: 0 ANSI: 5
[    2.946107] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.946110] Uniform CD-ROM driver Revision: 3.20
[    2.946181] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.946214] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    2.946468] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.946488] pata_jmicron 0000:03:00.0: setting latency timer to 64
[    2.946525] scsi4 : pata_jmicron
[    2.946563] scsi5 : pata_jmicron
[    2.947083] ata5: PATA max UDMA/100 cmd 0xb000 ctl 0xb100 bmdma 0xb400 irq 19
[    2.947085] ata6: PATA max UDMA/100 cmd 0xb200 ctl 0xb300 bmdma 0xb408 irq 19
[    3.256291] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.256304] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.256318] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.256320] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.256363] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.260273] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.260281] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfb105000
[    3.276026] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.276091] usb usb1: configuration #1 chosen from 1 choice
[    3.276114] hub 1-0:1.0: USB hub found
[    3.276120] hub 1-0:1.0: 6 ports detected
[    3.276209] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.276217] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.276220] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.276256] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.280167] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.280175] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfb104000
[    3.296020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.296067] usb usb2: configuration #1 chosen from 1 choice
[    3.296087] hub 2-0:1.0: USB hub found
[    3.296093] hub 2-0:1.0: 6 ports detected
[    3.296175] ehci_hcd 0000:05:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.296183] ehci_hcd 0000:05:00.2: EHCI Host Controller
[    3.296221] ehci_hcd 0000:05:00.2: new USB bus registered, assigned bus number 3
[    3.296257] ehci_hcd 0000:05:00.2: irq 18, io mem 0xfb000000
[    3.308011] ehci_hcd 0000:05:00.2: USB 2.0 started, EHCI 1.00
[    3.308053] usb usb3: configuration #1 chosen from 1 choice
[    3.308076] hub 3-0:1.0: USB hub found
[    3.308081] hub 3-0:1.0: 4 ports detected
[    3.308152] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.308165] uhci_hcd: USB Universal Host Controller Interface driver
[    3.308182] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.308187] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.308189] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.308229] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 4
[    3.308253] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    3.308302] usb usb4: configuration #1 chosen from 1 choice
[    3.308317] hub 4-0:1.0: USB hub found
[    3.308321] hub 4-0:1.0: 2 ports detected
[    3.308376] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.308380] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.308382] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.308407] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 5
[    3.308430] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e100
[    3.308477] usb usb5: configuration #1 chosen from 1 choice
[    3.308493] hub 5-0:1.0: USB hub found
[    3.308497] hub 5-0:1.0: 2 ports detected
[    3.308549] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.308553] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.308555] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.308582] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 6
[    3.308600] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e500
[    3.308648] usb usb6: configuration #1 chosen from 1 choice
[    3.308665] hub 6-0:1.0: USB hub found
[    3.308669] hub 6-0:1.0: 2 ports detected
[    3.308725] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.308729] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.308731] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.308763] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 7
[    3.308781] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e200
[    3.308828] usb usb7: configuration #1 chosen from 1 choice
[    3.308847] hub 7-0:1.0: USB hub found
[    3.308853] hub 7-0:1.0: 2 ports detected
[    3.308907] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.308911] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.308913] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.308939] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 8
[    3.308957] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e300
[    3.309006] usb usb8: configuration #1 chosen from 1 choice
[    3.309021] hub 8-0:1.0: USB hub found
[    3.309025] hub 8-0:1.0: 2 ports detected
[    3.309079] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.309083] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.309085] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.309111] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 9
[    3.309130] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[    3.309178] usb usb9: configuration #1 chosen from 1 choice
[    3.309194] hub 9-0:1.0: USB hub found
[    3.309197] hub 9-0:1.0: 2 ports detected
[    3.309255] uhci_hcd 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.309260] uhci_hcd 0000:05:00.0: UHCI Host Controller
[    3.309288] uhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 10
[    3.309311] uhci_hcd 0000:05:00.0: irq 20, io base 0x0000d000
[    3.309358] usb usb10: configuration #1 chosen from 1 choice
[    3.309376] hub 10-0:1.0: USB hub found
[    3.309379] hub 10-0:1.0: 2 ports detected
[    3.309435] uhci_hcd 0000:05:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.309439] uhci_hcd 0000:05:00.1: UHCI Host Controller
[    3.309466] uhci_hcd 0000:05:00.1: new USB bus registered, assigned bus number 11
[    3.309484] uhci_hcd 0000:05:00.1: irq 19, io base 0x0000d100
[    3.309536] usb usb11: configuration #1 chosen from 1 choice
[    3.309553] hub 11-0:1.0: USB hub found
[    3.309558] hub 11-0:1.0: 2 ports detected
[    3.309652] usbcore: registered new interface driver libusual
[    3.309673] usbcore: registered new interface driver usbserial
[    3.309680] USB Serial support registered for generic
[    3.309692] usbcore: registered new interface driver usbserial_generic
[    3.309694] usbserial: USB Serial Driver core
[    3.309724] PNP: No PS/2 controller found. Probing ports directly.
[    3.309983] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.309987] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.320041] mice: PS/2 mouse device common for all mice
[    3.356063] rtc_cmos 00:03: RTC can wake from S4
[    3.356091] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.356112] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    3.356162] device-mapper: uevent: version 1.0.3
[    3.356237] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.356281] device-mapper: multipath: version 1.0.5 loaded
[    3.356283] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.356338] cpuidle: using governor ladder
[    3.356339] cpuidle: using governor menu
[    3.356612] TCP cubic registered
[    3.356655] NET: Registered protocol family 10
[    3.356922] lo: Disabled Privacy Extensions
[    3.357111] NET: Registered protocol family 17
[    3.357122] Bluetooth: L2CAP ver 2.11
[    3.357123] Bluetooth: L2CAP socket layer initialized
[    3.357125] Bluetooth: SCO (Voice Link) ver 0.6
[    3.357126] Bluetooth: SCO socket layer initialized
[    3.357145] Bluetooth: RFCOMM socket layer initialized
[    3.357151] Bluetooth: RFCOMM TTY layer initialized
[    3.357152] Bluetooth: RFCOMM ver 1.10
[    3.358769] registered taskstats version 1
[    3.358879]   Magic number: 9:727:834
[    3.358954] rtc_cmos 00:03: setting system clock to 2009-05-09 12:50:57 UTC (1241873457)
[    3.358956] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.358957] EDD information not available.
[    3.358984] Freeing unused kernel memory: 536k freed
[    3.359085] Write protecting the kernel read-only data: 6708k
[    3.499505] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.499521] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.499537] r8169 0000:04:00.0: setting latency timer to 64
[    3.499631] r8169 0000:04:00.0: irq 2299 for MSI/MSI-X
[    3.500034] eth0: RTL8168b/8111b at 0xffffc2000005e000, 00:1a:4d:93:1b:75, XID 38000000 IRQ 2299
[    3.836510] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    4.013625] PM: Starting manual resume from disk
[    4.013627] PM: Resume from partition 8:23
[    4.013628] PM: Checking hibernation image.
[    4.013967] PM: Resume from disk failed.
[    4.017267] usb 4-1: configuration #1 chosen from 1 choice
[    4.023325] usbcore: registered new interface driver hiddev
[    4.034333] EXT4-fs: barriers enabled
[    4.039458] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb4/4-1/4-1:1.0/input/input3
[    4.039731] kjournald2 starting.  Commit interval 5 seconds
[    4.039745] EXT4-fs: delayed allocation enabled
[    4.039746] EXT4-fs: file extents enabled
[    4.040570] EXT4-fs: mballoc enabled
[    4.040573] EXT4-fs: mounted filesystem with ordered data mode.
[    4.064082] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-1/input0
[    4.064099] usbcore: registered new interface driver usbhid
[    4.064101] usbhid: v2.6:USB HID core driver
[    4.256510] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    4.431387] usb 5-1: configuration #1 chosen from 1 choice
[    4.449586] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb5/5-1/5-1:1.0/input/input4
[    4.476064] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.1-1/input0
[    7.007874] udev: starting version 141
[    7.078297] parport_pc 00:07: reported by Plug and Play ACPI
[    7.078338] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.195486] nvidia: module license 'NVIDIA' taints kernel.
[    7.447032] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.447040] nvidia 0000:01:00.0: setting latency timer to 64
[    7.447705] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.51  Fri Apr 17 00:08:33 PDT 2009
[    7.459878] iTCO_vendor_support: vendor-support=0
[    7.463110] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    7.463211] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0460)
[    7.463277] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    7.631420] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    7.639165] ppdev: user-space parallel port driver
[    7.994817] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.994866] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.145288] lp0: using parport0 (interrupt-driven).
[    8.217951] Adding 1943792k swap on /dev/sdb7.  Priority:-1 extents:1 across:1943792k
[    8.742248] EXT4 FS on sdb1, internal journal on sdb1:8
[   10.156097] EXT4-fs: barriers enabled
[   10.175301] kjournald2 starting.  Commit interval 5 seconds
[   10.175464] EXT4 FS on sda5, internal journal on sda5:8
[   10.175466] EXT4-fs: delayed allocation enabled
[   10.175467] EXT4-fs: file extents enabled
[   10.180134] EXT4-fs: mballoc enabled
[   10.180136] EXT4-fs: mounted filesystem with ordered data mode.
[   10.200997] EXT4-fs: barriers enabled
[   10.201318] kjournald2 starting.  Commit interval 5 seconds
[   10.204217] EXT4 FS on sdb5, internal journal on sdb5:8
[   10.204219] EXT4-fs: delayed allocation enabled
[   10.204220] EXT4-fs: file extents enabled
[   10.208879] EXT4-fs: mballoc enabled
[   10.208881] EXT4-fs: mounted filesystem with ordered data mode.
[   10.234830] EXT4-fs: barriers enabled
[   10.235155] kjournald2 starting.  Commit interval 5 seconds
[   10.235584] EXT4 FS on sdb6, internal journal on sdb6:8
[   10.235586] EXT4-fs: delayed allocation enabled
[   10.235587] EXT4-fs: file extents enabled
[   10.244564] EXT4-fs: mballoc enabled
[   10.244566] EXT4-fs: mounted filesystem with ordered data mode.
[   10.505069] type=1505 audit(1241873464.645:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2113
[   10.532372] type=1505 audit(1241873464.669:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2117
[   10.532437] type=1505 audit(1241873464.669:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2117
[   10.532465] type=1505 audit(1241873464.669:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2117
[   10.532489] type=1505 audit(1241873464.669:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2117
[   10.607784] type=1505 audit(1241873464.745:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2122
[   10.607899] type=1505 audit(1241873464.745:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2122
[   10.649809] type=1505 audit(1241873464.789:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2126
[   10.666014] type=1505 audit(1241873464.805:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2130
[   14.487277] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   14.487279] vboxdrv: Successfully done.
[   14.487280] vboxdrv: Found 2 processor cores.
[   14.487329] VBoxDrv: dbg - g_abExecMemory=ffffffffa0a0aaa0
[   14.487345] vboxdrv: fAsync=0 offMin=0x1c8 offMax=0x17e0
[   14.487374] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   14.487375] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   14.691301] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0ba9940
[   19.859387] r8169: eth0: link up
[   19.859391] r8169: eth0: link up
[   30.300507] eth0: no IPv6 routers present
[ 1982.932011] usb 2-1: new high speed USB device using ehci_hcd and address 2
[ 1983.065979] usb 2-1: configuration #1 chosen from 1 choice
[ 1983.124227] usbcore: registered new interface driver snd-usb-audio
[ 1987.642928] usb 2-1: USB disconnect, address 2
[ 2058.532016] usb 2-1: new high speed USB device using ehci_hcd and address 3
[ 2058.670156] usb 2-1: configuration #1 chosen from 1 choice
[ 2058.975816] usb 2-1: USB disconnect, address 3
[ 2061.692010] usb 2-1: new high speed USB device using ehci_hcd and address 4
[ 2061.825987] usb 2-1: configuration #1 chosen from 1 choice
[ 2063.083206] usb 2-1: USB disconnect, address 4
[ 2065.472011] usb 2-1: new high speed USB device using ehci_hcd and address 5
[ 2065.605834] usb 2-1: configuration #1 chosen from 1 choice
[ 2066.691527] usb 2-1: USB disconnect, address 5
[ 2903.976016] usb 5-2: new full speed USB device using uhci_hcd and address 3
[ 2904.176409] usb 5-2: configuration #1 chosen from 1 choice
[ 2904.208130] Initializing USB Mass Storage driver...
[ 2904.209173] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2904.209760] usbcore: registered new interface driver usb-storage
[ 2904.209763] USB Mass Storage support registered.
[ 2904.209767] usb-storage: device found at 3
[ 2904.209769] usb-storage: waiting for device to settle before scanning
[ 2904.222284] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3611
[ 2904.222302] usbcore: registered new interface driver usblp
[ 2906.182093] ppdev0: registered pardevice
[ 2906.228658] ppdev0: unregistered pardevice
[ 2907.069925] usblp0: removed
[ 2909.209666] usb-storage: device scan complete
[ 2909.212654] scsi 6:0:0:0: Direct-Access     HP       psc 2410         1.00 PQ: 0 ANSI: 2
[ 2909.220060] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 2909.220127] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 3422.988505] cdrom: This disc doesn't have any tracks I recognize!
[ 3423.039121] end_request: I/O error, dev sr0, sector 0
[ 3423.039125] Buffer I/O error on device sr0, logical block 0
[ 3423.045556] end_request: I/O error, dev sr0, sector 0
[ 3423.045559] Buffer I/O error on device sr0, logical block 0
[ 3642.422372] UDF-fs: No VRS found
[ 3642.505881] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 3642.553463] ISOFS: changing to secondary root
[ 3890.865454] uhci_hcd 0000:05:00.1: host system error, PCI problems?
[ 3890.865458] uhci_hcd 0000:05:00.1: host controller process error, something bad happened!
[ 3890.865498] uhci_hcd 0000:05:00.1: host system error, PCI problems?
[ 3890.865501] uhci_hcd 0000:05:00.1: host controller process error, something bad happened!
[ 3890.869400] uhci_hcd 0000:05:00.1: host system error, PCI problems?
[ 3890.869402] uhci_hcd 0000:05:00.1: host controller process error, something bad happened!
[ 3890.870627] uhci_hcd 0000:05:00.1: host system error, PCI problems?
[ 3890.870629] uhci_hcd 0000:05:00.1: host controller process error, something bad happened!
[ 3890.907018] uhci_hcd 0000:05:00.1: host system error, PCI problems?
[ 3890.907021] uhci_hcd 0000:05:00.1: host controller halted, very bad!
[ 3890.907036] uhci_hcd 0000:05:00.1: HC died; cleaning up
[ 4042.432595] usb 5-2: USB disconnect, address 3
[ 4042.434473] scsi 6:0:0:0: rejecting I/O to dead device
[ 4042.434480] scsi 6:0:0:0: rejecting I/O to dead device
[ 4042.434484] scsi 6:0:0:0: [sdc] READ CAPACITY failed
[ 4042.434485] scsi 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4042.434489] scsi 6:0:0:0: [sdc] Sense not available.
[ 4042.434493] scsi 6:0:0:0: rejecting I/O to dead device
[ 4042.434496] scsi 6:0:0:0: [sdc] Write Protect is off
[ 4042.434498] scsi 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 4042.434500] scsi 6:0:0:0: [sdc] Assuming drive cache: write through
[ 4042.434505] scsi 6:0:0:0: rejecting I/O to dead device
[ 4042.434510] scsi 6:0:0:0: rejecting I/O to dead device
[ 4042.434514] scsi 6:0:0:0: rejecting I/O to dead device
[ 4042.434519] scsi 6:0:0:0: rejecting I/O to dead device
[ 4042.434522] scsi 6:0:0:0: [sdc] READ CAPACITY failed
[ 4042.434523] scsi 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4042.434526] scsi 6:0:0:0: [sdc] Sense not available.
[ 4042.434529] scsi 6:0:0:0: rejecting I/O to dead device
[ 4042.434533] scsi 6:0:0:0: [sdc] Write Protect is off
[ 4042.434534] scsi 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 4042.434536] scsi 6:0:0:0: [sdc] Assuming drive cache: write through
[ 5049.204518] usb 3-4: new high speed USB device using ehci_hcd and address 2
[ 5049.260280] hub 3-0:1.0: unable to enumerate USB device on port 4
[ 5071.604020] usb 3-4: new high speed USB device using ehci_hcd and address 3
[ 5071.737992] usb 3-4: configuration #1 chosen from 1 choice
```

---

### Post by xc3RnbFO8P on 2009-05-09
It seems to be unsupported.

If you want we can try to install V4L drivers and see if that make any differences.

---

### Post by zurih on 2009-05-09
> **Ringi said:**
> It seems to be unsupported.

If you want we can try to install V4L drivers and see if that make any differences.

I appreciate your help on this

---

### Post by xc3RnbFO8P on 2009-05-09
Here:
> sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
> cd  /home/**your_folder**/v4l-dvb
> make all
> sudo make install
reboot and dmeg.

---

### Post by zurih on 2009-05-09
dmesg after reboot:

```
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=0f774edd-2fbd-4592-9945-4c8cadd895d3 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000007fee0000
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fee0000 page 4k
[    0.000000] kernel direct mapping tables up to 7fee0000 @ 10000-14000
[    0.000000] last_map_addr: 7fee0000 end: 7fee0000
[    0.000000] RAMDISK: 3785b000 - 37feff31
[    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FEE3180, 49E4 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: HPET 7FEE7CC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FEE7D40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FEE7BC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT 7FEE7DC0, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 7FEE8250, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003785b000 - 0037feff31]          RAMDISK ==> [003785b000 - 0037feff31]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000f5110] 000f5110
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523877
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2540 pages reserved
[    0.000000]   DMA zone: 1377 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7109 pages used for memmap
[    0.000000]   DMA32 zone: 512795 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 514172
[    0.000000] Kernel command line: root=UUID=0f774edd-2fbd-4592-9945-4c8cadd895d3 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2666.691 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 20971520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2024664k/2096000k available (4760k kernel code, 492k absent, 70164k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.38 BogoMIPS (lpj=10666764)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080926
[    0.004000] ACPI: Checking initramfs for custom DSDT
[    0.252048] Setting APIC routing to flat
[    0.252388] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.292314] CPU0: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.296001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5333.31 BogoMIPS (lpj=10666624)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.380505] CPU1: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.380523] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.384034] Brought up 2 CPUs
[    0.384036] Total of 2 processors activated (10666.69 BogoMIPS).
[    0.384077] CPU0 attaching sched-domain:
[    0.384079]  domain 0: span 0-1 level MC
[    0.384081]   groups: 0 1
[    0.384085] CPU1 attaching sched-domain:
[    0.384086]  domain 0: span 0-1 level MC
[    0.384087]   groups: 1 0
[    0.384138] net_namespace: 1400 bytes
[    0.384138] Booting paravirtualized kernel on bare hardware
[    0.384208] Time: 16:19:01  Date: 05/09/09
[    0.384208] regulator: core version 0.5
[    0.384208] NET: Registered protocol family 16
[    0.384208] ACPI: bus type pci registered
[    0.384208] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.384208] PCI: MCFG area at f0000000 reserved in E820
[    0.386026] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.386027] PCI: Using configuration type 1 for base access
[    0.386039] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.386040] mtrr: probably your BIOS does not setup all CPUs.
[    0.386041] mtrr: corrected configuration.
[    0.386514] ACPI: EC: Look up EC in DSDT
[    0.392372] ACPI: Interpreter enabled
[    0.392376] ACPI: (supports S0 S3 S4 S5)
[    0.392390] ACPI: Using IOAPIC for interrupt routing
[    0.396065] ACPI: No dock devices found.
[    0.396072] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.396138] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.396140] pci 0000:00:01.0: PME# disabled
[    0.396195] pci 0000:00:1a.0: reg 20 io port: [0xe000-0xe01f]
[    0.396243] pci 0000:00:1a.1: reg 20 io port: [0xe100-0xe11f]
[    0.396292] pci 0000:00:1a.2: reg 20 io port: [0xe500-0xe51f]
[    0.396332] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfb105000-0xfb1053ff]
[    0.396389] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfb100000-0xfb103fff]
[    0.396411] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.396414] pci 0000:00:1b.0: PME# disabled
[    0.396448] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.396451] pci 0000:00:1c.0: PME# disabled
[    0.396487] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.396490] pci 0000:00:1c.3: PME# disabled
[    0.396527] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.396529] pci 0000:00:1c.4: PME# disabled
[    0.396572] pci 0000:00:1d.0: reg 20 io port: [0xe200-0xe21f]
[    0.396620] pci 0000:00:1d.1: reg 20 io port: [0xe300-0xe31f]
[    0.396669] pci 0000:00:1d.2: reg 20 io port: [0xe400-0xe41f]
[    0.396709] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfb104000-0xfb1043ff]
[    0.396826] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.396829] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.396860] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.396864] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.396868] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.396872] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.396876] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.396880] pci 0000:00:1f.2: reg 24 io port: [0xfc00-0xfc0f]
[    0.396907] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfb106000-0xfb1060ff]
[    0.396918] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.396949] pci 0000:00:1f.5: reg 10 io port: [0xe700-0xe707]
[    0.396953] pci 0000:00:1f.5: reg 14 io port: [0xe800-0xe803]
[    0.396958] pci 0000:00:1f.5: reg 18 io port: [0xe900-0xe907]
[    0.396962] pci 0000:00:1f.5: reg 1c io port: [0xea00-0xea03]
[    0.396966] pci 0000:00:1f.5: reg 20 io port: [0xeb00-0xeb0f]
[    0.396970] pci 0000:00:1f.5: reg 24 io port: [0xec00-0xec0f]
[    0.397006] pci 0000:01:00.0: reg 10 32bit mmio: [0xf6000000-0xf6ffffff]
[    0.397012] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.397019] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf4000000-0xf5ffffff]
[    0.397023] pci 0000:01:00.0: reg 24 io port: [0xa000-0xa07f]
[    0.397027] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.397063] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.397065] pci 0000:00:01.0: bridge 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.397068] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.397098] pci 0000:00:1c.0: bridge io port: [0x9000-0x9fff]
[    0.397151] pci 0000:03:00.0: reg 10 io port: [0xb000-0xb007]
[    0.397159] pci 0000:03:00.0: reg 14 io port: [0xb100-0xb103]
[    0.397166] pci 0000:03:00.0: reg 18 io port: [0xb200-0xb207]
[    0.397174] pci 0000:03:00.0: reg 1c io port: [0xb300-0xb303]
[    0.397181] pci 0000:03:00.0: reg 20 io port: [0xb400-0xb40f]
[    0.397241] pci 0000:00:1c.3: bridge io port: [0xb000-0xbfff]
[    0.397243] pci 0000:00:1c.3: bridge 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.397295] pci 0000:04:00.0: reg 10 io port: [0xc000-0xc0ff]
[    0.397314] pci 0000:04:00.0: reg 18 64bit mmio: [0xfa000000-0xfa000fff]
[    0.397333] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.397344] pci 0000:04:00.0: supports D1 D2
[    0.397345] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.397349] pci 0000:04:00.0: PME# disabled
[    0.397386] pci 0000:00:1c.4: bridge io port: [0xc000-0xcfff]
[    0.397389] pci 0000:00:1c.4: bridge 32bit mmio: [0xf9000000-0xfaffffff]
[    0.397434] pci 0000:05:00.0: reg 20 io port: [0xd000-0xd01f]
[    0.397449] pci 0000:05:00.0: supports D1 D2
[    0.397450] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot
[    0.397454] pci 0000:05:00.0: PME# disabled
[    0.397495] pci 0000:05:00.1: reg 20 io port: [0xd100-0xd11f]
[    0.397511] pci 0000:05:00.1: supports D1 D2
[    0.397512] pci 0000:05:00.1: PME# supported from D0 D1 D2 D3hot
[    0.397515] pci 0000:05:00.1: PME# disabled
[    0.397541] pci 0000:05:00.2: reg 10 32bit mmio: [0xfb000000-0xfb0000ff]
[    0.397572] pci 0000:05:00.2: supports D1 D2
[    0.397573] pci 0000:05:00.2: PME# supported from D0 D1 D2 D3hot
[    0.397576] pci 0000:05:00.2: PME# disabled
[    0.397618] pci 0000:00:1e.0: transparent bridge
[    0.397621] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.397624] pci 0000:00:1e.0: bridge 32bit mmio: [0xfb000000-0xfb0fffff]
[    0.397642] bus 00 -> node 0
[    0.397646] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.397817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.397891] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.397964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.398036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.410531] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.410615] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.410699] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.410782] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.410865] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.410948] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.411031] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.411114] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[    0.411265] ACPI: WMI: Mapper loaded
[    0.411314] SCSI subsystem initialized
[    0.411314] libata version 3.00 loaded.
[    0.411314] usbcore: registered new interface driver usbfs
[    0.411314] usbcore: registered new interface driver hub
[    0.411314] usbcore: registered new device driver usb
[    0.411314] PCI: Using ACPI for IRQ routing
[    0.420008] Bluetooth: Core ver 2.13
[    0.420019] NET: Registered protocol family 31
[    0.420019] Bluetooth: HCI device and connection manager initialized
[    0.420019] Bluetooth: HCI socket layer initialized
[    0.420020] NET: Registered protocol family 8
[    0.420021] NET: Registered protocol family 20
[    0.420031] NetLabel: Initializing
[    0.420032] NetLabel:  domain hash size = 128
[    0.420034] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.420045] NetLabel:  unlabeled traffic allowed by default
[    0.420072] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.420076] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.424060] AppArmor: AppArmor Filesystem Enabled
[    0.436049] pnp: PnP ACPI init
[    0.436056] ACPI: bus type pnp registered
[    0.438073] pnp: PnP ACPI: found 12 devices
[    0.438075] ACPI: ACPI bus type pnp unregistered
[    0.438081] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.438083] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.438084] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.438086] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.438087] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.438092] system 00:08: ioport range 0x400-0x4bf could not be reserved
[    0.438096] system 00:09: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.438100] system 00:0a: iomem range 0xcce00-0xcffff has been reserved
[    0.438102] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
[    0.438103] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.438105] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.438107] system 00:0a: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.438109] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.438110] system 00:0a: iomem range 0x100000-0x7fedffff could not be reserved
[    0.438112] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.438114] system 00:0a: iomem range 0xfed10000-0xfed1dfff has been reserved
[    0.438115] system 00:0a: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.438117] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.438119] system 00:0a: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.438120] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.438122] system 00:0a: iomem range 0xe0000-0xeffff has been reserved
[    0.442745] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.442747] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.442749] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.442752] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.442755] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.442756] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff
[    0.442760] pci 0000:00:1c.0:   MEM window: disabled
[    0.442762] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.442766] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.442768] pci 0000:00:1c.3:   IO window: 0xb000-0xbfff
[    0.442772] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xf8ffffff
[    0.442774] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.442778] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
[    0.442780] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.442784] pci 0000:00:1c.4:   MEM window: 0xf9000000-0xfaffffff
[    0.442786] pci 0000:00:1c.4:   PREFETCH window: 0x00000080000000-0x000000800fffff
[    0.442791] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.442793] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.442796] pci 0000:00:1e.0:   MEM window: 0xfb000000-0xfb0fffff
[    0.442799] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.442807] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442810] pci 0000:00:01.0: setting latency timer to 64
[    0.442815] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442817] pci 0000:00:1c.0: setting latency timer to 64
[    0.442823] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.442826] pci 0000:00:1c.3: setting latency timer to 64
[    0.442830] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442833] pci 0000:00:1c.4: setting latency timer to 64
[    0.442837] pci 0000:00:1e.0: setting latency timer to 64
[    0.442840] bus: 00 index 0 io port: [0x00-0xffff]
[    0.442841] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.442843] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.442844] bus: 01 index 1 mmio: [0xf4000000-0xf7ffffff]
[    0.442845] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.442847] bus: 01 index 3 mmio: [0x0-0x0]
[    0.442848] bus: 02 index 0 io port: [0x9000-0x9fff]
[    0.442849] bus: 02 index 1 mmio: [0x0-0x0]
[    0.442850] bus: 02 index 2 mmio: [0x0-0x0]
[    0.442851] bus: 02 index 3 mmio: [0x0-0x0]
[    0.442852] bus: 03 index 0 io port: [0xb000-0xbfff]
[    0.442853] bus: 03 index 1 mmio: [0xf8000000-0xf8ffffff]
[    0.442854] bus: 03 index 2 mmio: [0x0-0x0]
[    0.442855] bus: 03 index 3 mmio: [0x0-0x0]
[    0.442857] bus: 04 index 0 io port: [0xc000-0xcfff]
[    0.442858] bus: 04 index 1 mmio: [0xf9000000-0xfaffffff]
[    0.442859] bus: 04 index 2 mmio: [0x80000000-0x800fffff]
[    0.442861] bus: 04 index 3 mmio: [0x0-0x0]
[    0.442862] bus: 05 index 0 io port: [0xd000-0xdfff]
[    0.442863] bus: 05 index 1 mmio: [0xfb000000-0xfb0fffff]
[    0.442864] bus: 05 index 2 mmio: [0x0-0x0]
[    0.442865] bus: 05 index 3 io port: [0x00-0xffff]
[    0.442867] bus: 05 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.442872] NET: Registered protocol family 2
[    0.476259] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.476494] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.477569] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.478029] TCP: Hash tables configured (established 262144 bind 65536)
[    0.478030] TCP reno registered
[    0.488370] NET: Registered protocol family 1
[    0.488477] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    0.504273] Switched to high resolution mode on CPU 0
[    0.732933]  it is
[    0.990771] Freeing initrd memory: 7763k freed
[    0.993153] audit: initializing netlink socket (disabled)
[    0.993175] type=2000 audit(1241885940.992:1): initialized
[    0.999310] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.000187] VFS: Disk quotas dquot_6.5.1
[    1.000222] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.000620] fuse init (API version 7.10)
[    1.000675] msgmni has been set to 3970
[    1.000789] alg: No test for stdrng (krng)
[    1.000797] io scheduler noop registered
[    1.000799] io scheduler anticipatory registered
[    1.000800] io scheduler deadline registered
[    1.000827] io scheduler cfq registered (default)
[    1.000955] pci 0000:01:00.0: Boot video device
[    1.002838] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.002860] pcieport-driver 0000:00:01.0: found MSI capability
[    1.002876] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.002882] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.002891] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.002923] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.002947] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.002965] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.002973] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.002981] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.002990] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.003030] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.003054] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.003071] pcieport-driver 0000:00:1c.3: irq 2301 for MSI/MSI-X
[    1.003079] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.003087] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.003095] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.003134] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.003159] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.003176] pcieport-driver 0000:00:1c.4: irq 2300 for MSI/MSI-X
[    1.003184] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.003192] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.003200] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.003248] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.003464] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.003565] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.003567] ACPI: Power Button (FF) [PWRF]
[    1.003596] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.003598] ACPI: Power Button (CM) [PWRB]
[    1.003813] processor ACPI_CPU:00: registered as cooling_device0
[    1.003816] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.003948] ACPI: SSDT 7FEE81C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[    1.004091] processor ACPI_CPU:01: registered as cooling_device1
[    1.004093] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.032626] Linux agpgart interface v0.103
[    1.032634] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.032717] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.032947] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.033463] brd: module loaded
[    1.033674] loop: module loaded
[    1.033715] Fixed MDIO Bus: probed
[    1.033719] PPP generic driver version 2.4.2
[    1.033760] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.033777] Driver 'sd' needs updating - please use bus_type methods
[    1.033783] Driver 'sr' needs updating - please use bus_type methods
[    1.033834] ata_piix 0000:00:1f.2: version 2.12
[    1.033843] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.033846] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.033875] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.033928] scsi0 : ata_piix
[    1.033980] scsi1 : ata_piix
[    1.034467] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.034470] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.508049] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.524189] ata1.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    1.524193] ata1.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    1.524195] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.540297] ata1.00: configured for UDMA/133
[    2.016058] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.024568] ata2.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    2.024570] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.040556] ata2.00: configured for UDMA/133
[    2.040580] isa bounce pool size: 16 pages
[    2.040655] scsi 0:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    2.040736] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.040755] sd 0:0:0:0: [sda] Write Protect is off
[    2.040756] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.040775] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.040818] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.040828] sd 0:0:0:0: [sda] Write Protect is off
[    2.040830] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.040847] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.040849]  sda: sda2 < sda5 >
[    2.061650] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.061685] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.061748] scsi 1:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    2.061811] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.061821] sd 1:0:0:0: [sdb] Write Protect is off
[    2.061823] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.061840] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.061874] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.061884] sd 1:0:0:0: [sdb] Write Protect is off
[    2.061885] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.061903] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.061905]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    2.109307] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.109339] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.109354] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.109358] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.109392] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.109428] scsi2 : ata_piix
[    2.109468] scsi3 : ata_piix
[    2.109906] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[    2.109909] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[    2.584041] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.592184] ata3.00: ATAPI: Optiarc DVD RW AD-7220S, 1.00, max UDMA/100
[    2.608196] ata3.00: configured for UDMA/100
[    2.938566] ata4: SATA link down (SStatus 0 SControl 300)
[    2.939800] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7220S  1.00 PQ: 0 ANSI: 5
[    2.946076] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.946078] Uniform CD-ROM driver Revision: 3.20
[    2.946148] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.946184] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    2.946438] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.946459] pata_jmicron 0000:03:00.0: setting latency timer to 64
[    2.946498] scsi4 : pata_jmicron
[    2.946534] scsi5 : pata_jmicron
[    2.947048] ata5: PATA max UDMA/100 cmd 0xb000 ctl 0xb100 bmdma 0xb400 irq 19
[    2.947050] ata6: PATA max UDMA/100 cmd 0xb200 ctl 0xb300 bmdma 0xb408 irq 19
[    3.256301] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.256314] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.256328] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.256330] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.256368] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.260250] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.260260] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfb105000
[    3.272527] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.272582] usb usb1: configuration #1 chosen from 1 choice
[    3.272604] hub 1-0:1.0: USB hub found
[    3.272610] hub 1-0:1.0: 6 ports detected
[    3.272699] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.272707] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.272710] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.272753] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.276647] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.276655] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfb104000
[    3.292022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.292065] usb usb2: configuration #1 chosen from 1 choice
[    3.292088] hub 2-0:1.0: USB hub found
[    3.292093] hub 2-0:1.0: 6 ports detected
[    3.292173] ehci_hcd 0000:05:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.292181] ehci_hcd 0000:05:00.2: EHCI Host Controller
[    3.292219] ehci_hcd 0000:05:00.2: new USB bus registered, assigned bus number 3
[    3.292252] ehci_hcd 0000:05:00.2: irq 18, io mem 0xfb000000
[    3.304012] ehci_hcd 0000:05:00.2: USB 2.0 started, EHCI 1.00
[    3.304054] usb usb3: configuration #1 chosen from 1 choice
[    3.304077] hub 3-0:1.0: USB hub found
[    3.304081] hub 3-0:1.0: 4 ports detected
[    3.304153] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.304166] uhci_hcd: USB Universal Host Controller Interface driver
[    3.304183] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.304188] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.304191] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.304229] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 4
[    3.304253] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    3.304302] usb usb4: configuration #1 chosen from 1 choice
[    3.304317] hub 4-0:1.0: USB hub found
[    3.304321] hub 4-0:1.0: 2 ports detected
[    3.304375] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.304379] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.304381] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.304409] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 5
[    3.304433] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e100
[    3.304478] usb usb5: configuration #1 chosen from 1 choice
[    3.304495] hub 5-0:1.0: USB hub found
[    3.304499] hub 5-0:1.0: 2 ports detected
[    3.304561] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.304565] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.304567] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.304597] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 6
[    3.304615] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e500
[    3.304664] usb usb6: configuration #1 chosen from 1 choice
[    3.304680] hub 6-0:1.0: USB hub found
[    3.304683] hub 6-0:1.0: 2 ports detected
[    3.304737] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.304741] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.304743] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.304771] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 7
[    3.304789] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e200
[    3.304836] usb usb7: configuration #1 chosen from 1 choice
[    3.304852] hub 7-0:1.0: USB hub found
[    3.304856] hub 7-0:1.0: 2 ports detected
[    3.304910] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.304914] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.304916] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.304941] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 8
[    3.304959] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e300
[    3.305007] usb usb8: configuration #1 chosen from 1 choice
[    3.305022] hub 8-0:1.0: USB hub found
[    3.305027] hub 8-0:1.0: 2 ports detected
[    3.305081] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.305085] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.305087] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.305114] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 9
[    3.305133] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[    3.305180] usb usb9: configuration #1 chosen from 1 choice
[    3.305197] hub 9-0:1.0: USB hub found
[    3.305201] hub 9-0:1.0: 2 ports detected
[    3.305261] uhci_hcd 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.305265] uhci_hcd 0000:05:00.0: UHCI Host Controller
[    3.305292] uhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 10
[    3.305315] uhci_hcd 0000:05:00.0: irq 20, io base 0x0000d000
[    3.305365] usb usb10: configuration #1 chosen from 1 choice
[    3.305380] hub 10-0:1.0: USB hub found
[    3.305384] hub 10-0:1.0: 2 ports detected
[    3.305442] uhci_hcd 0000:05:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.305447] uhci_hcd 0000:05:00.1: UHCI Host Controller
[    3.305480] uhci_hcd 0000:05:00.1: new USB bus registered, assigned bus number 11
[    3.305498] uhci_hcd 0000:05:00.1: irq 19, io base 0x0000d100
[    3.305552] usb usb11: configuration #1 chosen from 1 choice
[    3.305567] hub 11-0:1.0: USB hub found
[    3.305571] hub 11-0:1.0: 2 ports detected
[    3.305663] usbcore: registered new interface driver libusual
[    3.305686] usbcore: registered new interface driver usbserial
[    3.305692] USB Serial support registered for generic
[    3.305703] usbcore: registered new interface driver usbserial_generic
[    3.305704] usbserial: USB Serial Driver core
[    3.305735] PNP: No PS/2 controller found. Probing ports directly.
[    3.305996] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.306000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.316044] mice: PS/2 mouse device common for all mice
[    3.352063] rtc_cmos 00:03: RTC can wake from S4
[    3.352094] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.352115] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    3.352163] device-mapper: uevent: version 1.0.3
[    3.352235] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.352276] device-mapper: multipath: version 1.0.5 loaded
[    3.352278] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.352329] cpuidle: using governor ladder
[    3.352330] cpuidle: using governor menu
[    3.352602] TCP cubic registered
[    3.352646] NET: Registered protocol family 10
[    3.352916] lo: Disabled Privacy Extensions
[    3.353106] NET: Registered protocol family 17
[    3.353118] Bluetooth: L2CAP ver 2.11
[    3.353119] Bluetooth: L2CAP socket layer initialized
[    3.353121] Bluetooth: SCO (Voice Link) ver 0.6
[    3.353122] Bluetooth: SCO socket layer initialized
[    3.353142] Bluetooth: RFCOMM socket layer initialized
[    3.353146] Bluetooth: RFCOMM TTY layer initialized
[    3.353147] Bluetooth: RFCOMM ver 1.10
[    3.354767] registered taskstats version 1
[    3.354881]   Magic number: 9:636:337
[    3.354907] tty tty58: hash matches
[    3.354959] rtc_cmos 00:03: setting system clock to 2009-05-09 16:19:04 UTC (1241885944)
[    3.354961] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.354962] EDD information not available.
[    3.354990] Freeing unused kernel memory: 536k freed
[    3.355090] Write protecting the kernel read-only data: 6708k
[    3.485176] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.485192] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.485208] r8169 0000:04:00.0: setting latency timer to 64
[    3.485297] r8169 0000:04:00.0: irq 2299 for MSI/MSI-X
[    3.485693] eth0: RTL8168b/8111b at 0xffffc2000005e000, 00:1a:4d:93:1b:75, XID 38000000 IRQ 2299
[    3.828510] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    3.863428] PM: Starting manual resume from disk
[    3.863430] PM: Resume from partition 8:23
[    3.863431] PM: Checking hibernation image.
[    3.863774] PM: Resume from disk failed.
[    3.879156] EXT4-fs: barriers enabled
[    3.889689] kjournald2 starting.  Commit interval 5 seconds
[    3.889700] EXT4-fs: delayed allocation enabled
[    3.889702] EXT4-fs: file extents enabled
[    3.890453] EXT4-fs: mballoc enabled
[    3.890456] EXT4-fs: mounted filesystem with ordered data mode.
[    4.005342] usb 4-1: configuration #1 chosen from 1 choice
[    4.248510] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    4.422513] usb 5-1: configuration #1 chosen from 1 choice
[    6.841517] udev: starting version 141
[    6.928478] usbcore: registered new interface driver hiddev
[    6.944482] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb4/4-1/4-1:1.0/input/input3
[    6.968600] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-1/input0
[    6.983657] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb5/5-1/5-1:1.0/input/input4
[    7.006446] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.1-1/input0
[    7.006464] usbcore: registered new interface driver usbhid
[    7.006479] usbhid: v2.6:USB HID core driver
[    7.257940] nvidia: module license 'NVIDIA' taints kernel.
[    7.509455] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.509461] nvidia 0000:01:00.0: setting latency timer to 64
[    7.510078] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.51  Fri Apr 17 00:08:33 PDT 2009
[    7.694826] parport_pc 00:07: reported by Plug and Play ACPI
[    7.694870] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.715016] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    7.743339] iTCO_vendor_support: vendor-support=0
[    7.746566] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    7.746667] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0460)
[    7.746721] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    7.757189] ppdev: user-space parallel port driver
[    7.878529] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.878579] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.011810] lp0: using parport0 (interrupt-driven).
[    8.084997] Adding 1943792k swap on /dev/sdb7.  Priority:-1 extents:1 across:1943792k
[    8.609262] EXT4 FS on sdb1, internal journal on sdb1:8
[   10.027879] EXT4-fs: barriers enabled
[   10.047084] kjournald2 starting.  Commit interval 5 seconds
[   10.047249] EXT4 FS on sda5, internal journal on sda5:8
[   10.047251] EXT4-fs: delayed allocation enabled
[   10.047252] EXT4-fs: file extents enabled
[   10.051921] EXT4-fs: mballoc enabled
[   10.051923] EXT4-fs: mounted filesystem with ordered data mode.
[   10.058369] EXT4-fs: barriers enabled
[   10.058654] kjournald2 starting.  Commit interval 5 seconds
[   10.059117] EXT4 FS on sdb5, internal journal on sdb5:8
[   10.059119] EXT4-fs: delayed allocation enabled
[   10.059120] EXT4-fs: file extents enabled
[   10.063746] EXT4-fs: mballoc enabled
[   10.063748] EXT4-fs: mounted filesystem with ordered data mode.
[   10.093805] EXT4-fs: barriers enabled
[   10.094129] kjournald2 starting.  Commit interval 5 seconds
[   10.094558] EXT4 FS on sdb6, internal journal on sdb6:8
[   10.094560] EXT4-fs: delayed allocation enabled
[   10.094562] EXT4-fs: file extents enabled
[   10.103492] EXT4-fs: mballoc enabled
[   10.103495] EXT4-fs: mounted filesystem with ordered data mode.
[   10.405845] type=1505 audit(1241885951.549:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2116
[   10.432899] type=1505 audit(1241885951.577:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2120
[   10.432965] type=1505 audit(1241885951.577:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2120
[   10.432992] type=1505 audit(1241885951.577:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2120
[   10.433016] type=1505 audit(1241885951.577:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2120
[   10.508522] type=1505 audit(1241885951.653:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2125
[   10.508631] type=1505 audit(1241885951.653:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2125
[   10.550429] type=1505 audit(1241885951.693:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2129
[   10.566819] type=1505 audit(1241885951.709:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2133
[   14.243558] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   14.243561] vboxdrv: Successfully done.
[   14.243562] vboxdrv: Found 2 processor cores.
[   14.244226] VBoxDrv: dbg - g_abExecMemory=ffffffffa09feaa0
[   14.244240] vboxdrv: fAsync=0 offMin=0x190 offMax=0x890
[   14.244272] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   14.244273] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   14.448163] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0b9d940
[   19.855076] r8169: eth0: link up
[   19.855081] r8169: eth0: link up
[   30.824016] eth0: no IPv6 routers present
[  136.392011] usb 3-4: new high speed USB device using ehci_hcd and address 2
[  136.448272] hub 3-0:1.0: unable to enumerate USB device on port 4
[  138.244009] usb 3-4: new high speed USB device using ehci_hcd and address 3
[  138.378014] usb 3-4: configuration #1 chosen from 1 choice
[  138.456788] usbcore: registered new interface driver snd-usb-audio
[  138.793195] usb 3-4: USB disconnect, address 3
[  141.868014] usb 3-4: new high speed USB device using ehci_hcd and address 4
[  142.006025] usb 3-4: configuration #1 chosen from 1 choice
[  142.707134] usb 3-4: USB disconnect, address 4
[  148.052010] usb 3-4: new high speed USB device using ehci_hcd and address 5
[  148.185874] usb 3-4: configuration #1 chosen from 1 choice
[  148.464371] usb 3-4: USB disconnect, address 5
[  150.904011] usb 3-4: new high speed USB device using ehci_hcd and address 6
[  151.037951] usb 3-4: configuration #1 chosen from 1 choice
[  151.806961] usb 3-4: USB disconnect, address 6
[  152.592015] usb 3-4: new high speed USB device using ehci_hcd and address 7
[  152.725996] usb 3-4: configuration #1 chosen from 1 choice
```

What should I look for here?

Thanks

---

### Post by xc3RnbFO8P on 2009-05-09
Can you see it if you do lsusb?

---

### Post by zurih on 2009-05-09
> **Ringi said:**
> Can you see it if you do lsusb?

Yes, I do:

```
Bus 003 Device 007: ID 07ca:0036 AVerMedia Technologies, Inc.
```

---

### Post by xc3RnbFO8P on 2009-05-09
Then it dosnt work, sorry :(

---

### Post by zurih on 2009-05-09
> **Ringi said:**
> Then it dosnt work, sorry :(

meh... :(
Can you please tell me how can I uninstall what I just installed? Hate to have unnecessary files..

Thank you

---

### Post by xc3RnbFO8P on 2009-05-09
Before you do that try:
> sudo modprobe dvb-usb-avertv-a800-02.fw
and chech if you see the driver loaded (in dmesg).

---

### Post by zurih on 2009-05-09
> **Ringi said:**
> Before you do that try:

and chech if you see the driver loaded (in dmesg).

I'm getting this:
```
FATAL: Module dvb_usb_avertv_a800_02.fw not found.
```

---

### Post by xc3RnbFO8P on 2009-05-09
Lol, my mistake
> sudo modprobe saa7134

---

### Post by zurih on 2009-05-09
I'm seeing this in dmesg:

```
[ 1291.908418] ppdev0: registered pardevice
[ 1291.956153] ppdev0: unregistered pardevice
[ 1293.117927] ppdev0: registered pardevice
[ 1293.164020] ppdev0: unregistered pardevice
[ 1293.433810] ppdev0: registered pardevice
[ 1293.480628] ppdev0: unregistered pardevice
[ 2429.119271] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 2429.348016] usb 3-4: new high speed USB device using ehci_hcd and address 2
[ 2429.868510] usb 3-4: device not accepting address 2, error -71
[ 2429.984021] usb 3-4: new high speed USB device using ehci_hcd and address 3
[ 2430.114060] usb 3-4: configuration #1 chosen from 1 choice
[ 2430.166677] usbcore: registered new interface driver snd-usb-audio
[ 3894.406650] Linux video capture interface: v2.00
[ 3894.444619] saa7130/34: v4l2 driver version 0.2.15 loaded
[ 3894.449713] saa7134 ALSA driver for DMA sound loaded
[ 3894.449715] saa7134 ALSA: no saa7134 cards found

```

---

### Post by xc3RnbFO8P on 2009-05-09
Install Tvtime in Add/Remove (all available application)
> sudo rmmod saa7134
> sudo modprobe saa7134 card=46
You can try more card from this list (just use sudo rmmod saa7134 before you new card) and try to scan channels in Tvtime (avermedia,  Compro VideoMate) :
```
saa7134: card=0 -> UNKNOWN/GENERIC
saa7134: card=1 -> Proteus Pro [philips reference design] 1131:2001 1131:2001
saa7134: card=2 -> LifeView FlyVIDEO3000 5168:0138 4e42:0138
saa7134: card=3 -> LifeView/Typhoon FlyVIDEO2000 5168:0138 4e42:0138
saa7134: card=4 -> EMPRESS 1131:6752
saa7134: card=5 -> SKNet Monster TV 1131:4e85
saa7134: card=6 -> Tevion MD 9717
saa7134: card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
saa7134: card=8 -> Terratec Cinergy 400 TV 153b:1142
saa7134: card=9 -> Medion 5044
saa7134: card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI
saa7134: card=11 -> Terratec Cinergy 600 TV 153b:1143
saa7134: card=12 -> Medion 7134 16be:0003
saa7134: card=13 -> Typhoon TV+Radio 90031
saa7134: card=14 -> ELSA EX-VISION 300TV 1048:226b
saa7134: card=15 -> ELSA EX-VISION 500TV 1048:226a
saa7134: card=16 -> ASUS TV-FM 7134 1043:4842 1043:4830 1043:4840
saa7134: card=17 -> AOPEN VA1000 POWER 1131:7133
saa7134: card=18 -> BMK MPEX No Tuner
saa7134: card=19 -> Compro VideoMate TV 185b:c100
saa7134: card=20 -> Matrox CronosPlus 102b:48d0
saa7134: card=21 -> 10MOONS PCI TV CAPTURE CARD 1131:2001
saa7134: card=22 -> AverMedia M156 / Medion 2819 1461:a70b
saa7134: card=23 -> BMK MPEX Tuner
saa7134: card=24 -> KNC One TV-Station DVR 1894:a006
saa7134: card=25 -> ASUS TV-FM 7133 1043:4843
saa7134: card=26 -> Pinnacle PCTV Stereo (saa7134) 11bd:002b
saa7134: card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM
saa7134: card=28 -> Manli MuchTV M-TV001/Behold TV 401
saa7134: card=29 -> Nagase Sangyo TransGear 3000TV 1461:050c
saa7134: card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
saa7134: card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card 1019:4cb5
saa7134: card=32 -> AVACS SmartTV
saa7134: card=33 -> AVerMedia DVD EZMaker 1461:10ff
saa7134: card=34 -> Noval Prime TV 7133
saa7134: card=35 -> AverMedia AverTV Studio 305 1461:2115
saa7134: card=36 -> UPMOST PURPLE TV 12ab:0800
saa7134: card=37 -> Items MuchTV Plus / IT-005
saa7134: card=38 -> Terratec Cinergy 200 TV 153b:1152
saa7134: card=39 -> LifeView FlyTV Platinum Mini 5168:0212 4e42:0212
saa7134: card=40 -> Compro VideoMate TV PVR/FM 185b:c100
saa7134: card=41 -> Compro VideoMate TV Gold+ 185b:c100
saa7134: card=42 -> Sabrent SBT-TVFM (saa7130)
saa7134: card=43 -> :Zolid Xpert TV7134
saa7134: card=44 -> Empire PCI TV-Radio LE
saa7134: card=45 -> Avermedia AVerTV Studio 307 1461:9715
saa7134: card=46 -> AVerMedia Cardbus TV/Radio (E500) 1461:d6ee
saa7134: card=47 -> Terratec Cinergy 400 mobile 153b:1162
saa7134: card=48 -> Terratec Cinergy 600 TV MK3 153b:1158
saa7134: card=49 -> Compro VideoMate Gold+ Pal 185b:c200
saa7134: card=50 -> Pinnacle PCTV 300i DVB-T + PAL 11bd:002d
saa7134: card=51 -> ProVideo PV952 1540:9524
saa7134: card=52 -> AverMedia AverTV/305 1461:2108
saa7134: card=53 -> ASUS TV-FM 7135 1043:4845
saa7134: card=54 -> LifeView FlyTV Platinum FM / Gold 5168:0214 5168:5214 1489:0214 5168:0304
[ 35.706519] saa7134: card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
saa7134: card=56 -> Avermedia AVerTV 307 1461:a70a
saa7134: card=57 -> Avermedia AVerTV GO 007 FM 1461:f31f
saa7134: card=58 -> ADS Tech Instant TV (saa7135) 1421:0350 1421:0351 1421:0370 1421:1370
saa7134: card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
saa7134: card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
saa7134: card=61 -> Philips TOUGH DVB-T reference design 1131:2004
saa7134: card=62 -> Compro VideoMate TV Gold+II
saa7134: card=63 -> Kworld Xpert TV PVR7134
saa7134: card=64 -> FlyTV mini Asus Digimatrix 1043:0210
saa7134: card=65 -> V-Stream Studio TV Terminator
saa7134: card=66 -> Yuan TUN-900 (saa7135)
saa7134: card=67 -> Beholder BeholdTV 409 FM 0000:4091
saa7134: card=68 -> GoTView 7135 PCI 5456:7135
saa7134: card=69 -> Philips EUROPA V3 reference design 1131:2004
saa7134: card=70 -> Compro Videomate DVB-T300 185b:c900
saa7134: card=71 -> Compro Videomate DVB-T200 185b:c901
saa7134: card=72 -> RTD Embedded Technologies VFG7350 1435:7350
saa7134: card=73 -> RTD Embedded Technologies VFG7330 1435:7330
saa7134: card=74 -> LifeView FlyTV Platinum Mini2 14c0:1212
saa7134: card=75 -> AVerMedia AVerTVHD MCE A180 1461:1044
saa7134: card=76 -> SKNet MonsterTV Mobile 1131:4ee9
saa7134: card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133) 11bd:002e
saa7134: card=78 -> ASUSTeK P7131 Dual 1043:4862 1043:4857
saa7134: card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
saa7134: card=80 -> ASUS Digimatrix TV 1043:0210
saa7134: card=81 -> Philips Tiger reference design 1131:2018
saa7134: card=82 -> MSI TV@Anywhere plus 1462:6231
saa7134: card=83 -> Terratec Cinergy 250 PCI TV 153b:1160
saa7134: card=84 -> LifeView FlyDVB Trio 5168:0319
saa7134: card=85 -> AverTV DVB-T 777 1461:2c05 1461:2c05
saa7134: card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
saa7134: card=87 -> ADS Instant TV Duo Cardbus PTV331 0331:1421
saa7134: card=88 -> Tevion/KWorld DVB-T 220RF 17de:7201
saa7134: card=89 -> ELSA EX-VISION 700TV 1048:226c
saa7134: card=90 -> Kworld ATSC110 17de:7350
saa7134: card=91 -> AVerMedia A169 B 1461:7360
saa7134: card=92 -> AVerMedia A169 B1 1461:6360
saa7134: card=93 -> Medion 7134 Bridge #2 16be:0005
saa7134: card=94 -> LifeView FlyDVB-T Hybrid Cardbus 5168:3306 5168:3502
saa7134: card=95 -> LifeView FlyVIDEO3000 (NTSC) 5169:0138
saa7134: card=96 -> Medion Md8800 Quadro 16be:0007 16be:0008
saa7134: card=97 -> LifeView FlyDVB-S /Acorp TV134DS 5168:0300 4e42:0300
saa7134: card=98 -> Proteus Pro 2309 0919:2003
saa7134: card=99 -> AVerMedia TV Hybrid A16AR 1461:2c00
saa7134: card=100 -> Asus Europa2 OEM 1043:4860
saa7134: card=101 -> Pinnacle PCTV 310i 11bd:002f
saa7134: card=102 -> Avermedia AVerTV Studio 507 1461:9715
saa7134: card=103 -> Compro Videomate DVB-T200A
saa7134: card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid 0070:6701
saa7134: card=105 -> Terratec Cinergy HT PCMCIA 153b:1172
saa7134: card=106 -> Encore ENLTV 1131:2342 1131:2341 3016:2344
saa7134: card=107 -> Encore ENLTV-FM 1131:230f
saa7134: card=108 -> Terratec Cinergy HT PCI 153b:1175
saa7134: card=109 -> Philips Tiger - S Reference design
saa7134: card=110 -> Avermedia M102 1461:f31e
saa7134: card=111 -> ASUS P7131 4871 1043:4871
saa7134: card=112 -> ASUSTeK P7131 Hybrid 1043:4876
saa7134: card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card 1019:4cb6
saa7134: card=114 -> KWorld DVB-T 210 17de:7250
saa7134: card=115 -> Sabrent PCMCIA TV-PCB05 0919:2003
```

---

### Post by zurih on 2009-05-09
I will try it.
Can you recommend any other tv card that works good on ubuntu? But not a cheap one... I would like to buy something good this time.

Thank you

---

### Post by xc3RnbFO8P on 2009-05-09
Look here for information:
[http://www.linuxtv.org/]("http://www.linuxtv.org/")

---

### Post by zurih on 2009-05-09
> **Ringi said:**
> Look here for information:
[http://www.linuxtv.org/]("http://www.linuxtv.org/")

Thank you for all the help.
This is for you :popcorn:

---

### Post by robertltux on 2009-05-15
i have an ads mini tv usb and a dual boot with XP (driver and standard tv ap installed)

has anybody gotten that combo to work??


already done a fresh compile of the driver set and have tvtime installed

---

