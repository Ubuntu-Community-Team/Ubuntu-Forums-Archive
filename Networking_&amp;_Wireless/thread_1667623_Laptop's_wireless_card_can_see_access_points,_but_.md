---
title: "Laptop's wireless card can see access points, but can't connect"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by Lugkhast on 2011-01-15
I'm not exactly sure if this should be here and not in the Hardware & Laptops section, but seeing as my only problem is with WiFi, I'm guessing this is the right place.

Under Ubuntu, my laptop (an Asus K42Ja, more details below) can see wireless networks normally. However, when I attempt to connect, it fails to establish a connection. Under Windows on the same laptop (dual boot), no problems are experienced.

According to [this]("http://www.thinkwiki.org/wiki/Intel_Centrino_Wireless-N_1000"), there's a firmware bug in my wireless chip which causes connections to get dropped. I'm not getting connections at all, but I still tried the workarounds on that page with no luck.

The router is a TP-Link TL-WR340G. My previous laptop, a really old one from 2003 running Ubuntu 9.10 was able to connect to that router without problems. The wireless card was Intel on that as well (but, of course, much older).

The router is set up to use WPA for security. I didn't use WPA2 as I read something a while ago about problems with WPA2 and some Linux distros. Please correct me if I'm wrong here.

If anyone's curious, I'm posting this on Ubuntu, via an ethernet cable to the router mentioned earlier.

Some tasty technical bits:

dmesg (the latter half of the "timed out" messages is me retrying after double-checking the WPA key)
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=de823113-6707-4a2c-ac05-775455a62e22 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007adf1000 (usable)
[    0.000000]  BIOS-e820: 000000007adf1000 - 000000007ae88000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ae88000 - 000000007ae99000 (reserved)
[    0.000000]  BIOS-e820: 000000007ae99000 - 000000007aeae000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007aeae000 - 000000007aed7000 (reserved)
[    0.000000]  BIOS-e820: 000000007aed7000 - 000000007aee8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007aee8000 - 000000007aeeb000 (reserved)
[    0.000000]  BIOS-e820: 000000007aeeb000 - 000000007aeed000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007aeed000 - 000000007af05000 (reserved)
[    0.000000]  BIOS-e820: 000000007af05000 - 000000007af06000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007af06000 - 000000007af0a000 (reserved)
[    0.000000]  BIOS-e820: 000000007af0a000 - 000000007af0d000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007af0d000 - 000000007af12000 (reserved)
[    0.000000]  BIOS-e820: 000000007af12000 - 000000007af21000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007af21000 - 000000007c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x7adf1 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07C000000 mask FFC000000 uncachable
[    0.000000]   2 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009bc00 (usable)
[    0.000000]  modified: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007adf1000 (usable)
[    0.000000]  modified: 000000007adf1000 - 000000007ae88000 (ACPI NVS)
[    0.000000]  modified: 000000007ae88000 - 000000007ae99000 (reserved)
[    0.000000]  modified: 000000007ae99000 - 000000007aeae000 (ACPI NVS)
[    0.000000]  modified: 000000007aeae000 - 000000007aed7000 (reserved)
[    0.000000]  modified: 000000007aed7000 - 000000007aee8000 (ACPI NVS)
[    0.000000]  modified: 000000007aee8000 - 000000007aeeb000 (reserved)
[    0.000000]  modified: 000000007aeeb000 - 000000007aeed000 (ACPI NVS)
[    0.000000]  modified: 000000007aeed000 - 000000007af05000 (reserved)
[    0.000000]  modified: 000000007af05000 - 000000007af06000 (ACPI NVS)
[    0.000000]  modified: 000000007af06000 - 000000007af0a000 (reserved)
[    0.000000]  modified: 000000007af0a000 - 000000007af0d000 (ACPI data)
[    0.000000]  modified: 000000007af0d000 - 000000007af12000 (reserved)
[    0.000000]  modified: 000000007af12000 - 000000007af21000 (ACPI NVS)
[    0.000000]  modified: 000000007af21000 - 000000007c000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000fcab0] fcab0
[    0.000000] init_memory_mapping: 0000000000000000-000000007adf1000
[    0.000000]  0000000000 - 007ac00000 page 2M
[    0.000000]  007ac00000 - 007adf1000 page 4k
[    0.000000] kernel direct mapping tables up to 7adf1000 @ 16000-1a000
[    0.000000] RAMDISK: 37000000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 000000007af0be18 0005C (v01 _ASUS_   _ASUS_ 06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 000000007aeebc18 000F4 (v04 _ASUS_   _ASUS_ 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20100428/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0x7AF1DF40/0x000000007AF20D40, using 32 (20100428/tbfadt-486)
[    0.000000] ACPI: DSDT 000000007aea1018 0C917 (v01 _ASUS_   _ASUS_ 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 000000007af1df40 00040
[    0.000000] ACPI: APIC 000000007af0af18 0008C (v02 _ASUS_   _ASUS_ 06222004 MSFT 00010013)
[    0.000000] ACPI: MCFG 000000007af1fd18 0003C (v01 _ASUS_   _ASUS_ 06222004 MSFT 00000097)
[    0.000000] ACPI: HPET 000000007af1fc98 00038 (v01 _ASUS_   _ASUS_ 06222004 AMI. 00000003)
[    0.000000] ACPI: ECDT 000000007af20b18 000C1 (v01 _ASUS_   _ASUS_ 06222004 AMI  00000000)
[    0.000000] ACPI: SSDT 000000007aeec618 005BE (v01  PmRef     Nvga 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000007af05018 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007adf1000
[    0.000000] Initmem setup node 0 0000000000000000-000000007adf1000
[    0.000000]   NODE_DATA [0000000001d181c0 - 0000000001d1d1bf]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880002600000-ffff8800041fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0007adf1
[    0.000000] On node 0 totalpages: 503164
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3923 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6825 pages used for memmap
[    0.000000]   DMA32 zone: 492360 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [18000 - 187ff]
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7c000000 (gap: 7c000000:7c000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] early_res array is doubled to 128 at [18800 - 197ff]
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 496283
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=de823113-6707-4a2c-ac05-775455a62e22 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (69 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037000000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d1819d]             BRK
[    0.000000]   #4 [00000fcac0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000fcab0 - 00000fcac0]    MP-table mpf
[    0.000000]   #6 [000009bc00 - 00000fc830]   BIOS reserved
[    0.000000]   #7 [00000fca40 - 00000fcab0]   BIOS reserved
[    0.000000]   #8 [00000fc830 - 00000fca40]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000018000]         PGTABLE
[    0.000000]   #12 [0001d181c0 - 0001d1d1c0]       NODE_DATA
[    0.000000]   #13 [0001d1d1c0 - 0001d1e1c0]         BOOTMEM
[    0.000000]   #14 [0001d17140 - 0001d172c0]         BOOTMEM
[    0.000000]   #15 [000251f000 - 0002520000]         BOOTMEM
[    0.000000]   #16 [0002520000 - 0002521000]         BOOTMEM
[    0.000000]   #17 [0002600000 - 0004200000]        MEMMAP 0
[    0.000000]   #18 [0001d172c0 - 0001d17440]         BOOTMEM
[    0.000000]   #19 [0001d1e1c0 - 0001d2a1c0]         BOOTMEM
[    0.000000]   #20 [0001d2b000 - 0001d2c000]         BOOTMEM
[    0.000000]   #21 [0001d17440 - 0001d17481]         BOOTMEM
[    0.000000]   #22 [0001d174c0 - 0001d17503]         BOOTMEM
[    0.000000]   #23 [0001d17540 - 0001d17b28]         BOOTMEM
[    0.000000]   #24 [0001d17b40 - 0001d17ba8]         BOOTMEM
[    0.000000]   #25 [0001d17bc0 - 0001d17c28]         BOOTMEM
[    0.000000]   #26 [0001d17c40 - 0001d17ca8]         BOOTMEM
[    0.000000]   #27 [0001d17cc0 - 0001d17d28]         BOOTMEM
[    0.000000]   #28 [0001d17d40 - 0001d17da8]         BOOTMEM
[    0.000000]   #29 [0001d17dc0 - 0001d17e28]         BOOTMEM
[    0.000000]   #30 [0001d17e40 - 0001d17ea8]         BOOTMEM
[    0.000000]   #31 [0001d17ec0 - 0001d17f28]         BOOTMEM
[    0.000000]   #32 [0001d17f40 - 0001d17fa8]         BOOTMEM
[    0.000000]   #33 [0001d2a1c0 - 0001d2a228]         BOOTMEM
[    0.000000]   #34 [0001d2a240 - 0001d2a2a8]         BOOTMEM
[    0.000000]   #35 [0001d2a2c0 - 0001d2a328]         BOOTMEM
[    0.000000]   #36 [0001d2a340 - 0001d2a3a8]         BOOTMEM
[    0.000000]   #37 [0001d2a3c0 - 0001d2a428]         BOOTMEM
[    0.000000]   #38 [0001d2a440 - 0001d2a4a8]         BOOTMEM
[    0.000000]   #39 [0001d2a4c0 - 0001d2a528]         BOOTMEM
[    0.000000]   #40 [0001d2a540 - 0001d2a5a8]         BOOTMEM
[    0.000000]   #41 [0001d2a5c0 - 0001d2a628]         BOOTMEM
[    0.000000]   #42 [0001d2a640 - 0001d2a6a8]         BOOTMEM
[    0.000000]   #43 [0001d2a6c0 - 0001d2a728]         BOOTMEM
[    0.000000]   #44 [0001d2a740 - 0001d2a7a8]         BOOTMEM
[    0.000000]   #45 [0001d2a7c0 - 0001d2a828]         BOOTMEM
[    0.000000]   #46 [0001d2a840 - 0001d2a8a8]         BOOTMEM
[    0.000000]   #47 [0001d2a8c0 - 0001d2a928]         BOOTMEM
[    0.000000]   #48 [0001d2a940 - 0001d2a9a8]         BOOTMEM
[    0.000000]   #49 [0001d2a9c0 - 0001d2aa28]         BOOTMEM
[    0.000000]   #50 [0001d17fc0 - 0001d17fe0]         BOOTMEM
[    0.000000]   #51 [0001d2aa40 - 0001d2aaaa]         BOOTMEM
[    0.000000]   #52 [0001d2aac0 - 0001d2ab2a]         BOOTMEM
[    0.000000]   #53 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #54 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #55 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #56 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #57 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #58 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #59 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #60 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #61 [0001d2ab40 - 0001d2ab48]         BOOTMEM
[    0.000000]   #62 [0001d2ab80 - 0001d2ab88]         BOOTMEM
[    0.000000]   #63 [0001d2abc0 - 0001d2abe0]         BOOTMEM
[    0.000000]   #64 [0001d2ac00 - 0001d2ac40]         BOOTMEM
[    0.000000]   #65 [0001d2ac40 - 0001d2ad60]         BOOTMEM
[    0.000000]   #66 [0001d2ad80 - 0001d2adc8]         BOOTMEM
[    0.000000]   #67 [0001d2ae00 - 0001d2ae48]         BOOTMEM
[    0.000000]   #68 [0001d2c000 - 0001d34000]         BOOTMEM
[    0.000000] Memory: 1953144k/2013124k available (5711k kernel code, 468k absent, 59512k reserved, 5379k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:744
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 20971520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2526.935 MHz processor.
[    0.000008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.87 BogoMIPS (lpj=25269350)
[    0.000011] pid_max: default: 32768 minimum: 301
[    0.000030] Security Framework initialized
[    0.000045] AppArmor: AppArmor initialized
[    0.000046] Yama: becoming mindful.
[    0.000240] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000913] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.001197] Mount-cache hash table entries: 256
[    0.001301] Initializing cgroup subsys ns
[    0.001305] Initializing cgroup subsys cpuacct
[    0.001308] Initializing cgroup subsys memory
[    0.001314] Initializing cgroup subsys devices
[    0.001316] Initializing cgroup subsys freezer
[    0.001318] Initializing cgroup subsys net_cls
[    0.001338] CPU: Physical Processor ID: 0
[    0.001339] CPU: Processor Core ID: 0
[    0.001344] mce: CPU supports 9 MCE banks
[    0.001354] CPU0: Thermal monitoring enabled (TM1)
[    0.001361] using mwait in idle threads.
[    0.001363] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.001369] ... version:                3
[    0.001370] ... bit width:              48
[    0.001371] ... generic registers:      4
[    0.001373] ... value mask:             0000ffffffffffff
[    0.001374] ... max period:             000000007fffffff
[    0.001375] ... fixed-purpose events:   3
[    0.001376] ... event mask:             000000070000000f
[    0.003200] ACPI: Core revision 20100428
[    0.021730] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.021734] ftrace: allocating 22678 entries in 89 pages
[    0.028185] Setting APIC routing to flat
[    0.028500] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.128450] CPU0: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz stepping 05
[    0.243657] Booting Node   0, Processors  #1 #2 #3
[    0.783329] Brought up 4 CPUs
[    0.783332] Total of 4 processors activated (20215.77 BogoMIPS).
[    0.784972] devtmpfs: initialized
[    0.785793] regulator: core version 0.5
[    0.785820] Time: 17:01:24  Date: 01/15/11
[    0.785846] NET: Registered protocol family 16
[    0.785928] Trying to unpack rootfs image as initramfs...
[    0.785935] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.785937] ACPI: bus type pci registered
[    0.785994] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.785997] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.793969] PCI: Using configuration type 1 for base access
[    0.794625] bio: create slab <bio-0> at 0
[    0.796560] ACPI: EC: EC description table is found, configuring boot EC
[    0.798480] ACPI: Executed 1 blocks of module-level executable AML code
[    0.804880] ACPI: BIOS _OSI(Linux) query ignored
[    0.826163] ACPI: SSDT 000000007af09918 0043D (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.826635] ACPI: Dynamic OEM Table Load:
[    0.826637] ACPI: SSDT (null) 0043D (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.826937] ACPI: SSDT 000000007af07618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.827409] ACPI: Dynamic OEM Table Load:
[    0.827411] ACPI: SSDT (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.827970] ACPI: SSDT 000000007af08a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.828506] ACPI: Dynamic OEM Table Load:
[    0.828508] ACPI: SSDT (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.828691] ACPI: SSDT 000000007af06d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.829191] ACPI: Dynamic OEM Table Load:
[    0.829193] ACPI: SSDT (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.830501] ACPI: Interpreter enabled
[    0.830504] ACPI: (supports S0 S3 S4 S5)
[    0.830524] ACPI: Using IOAPIC for interrupt routing
[    0.841763] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.842262] ACPI: No dock devices found.
[    0.842265] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.842993] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.844159] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.844161] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.844163] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.844165] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.844167] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.844168] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.844170] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.844172] pci_root PNP0A08:00: host bridge window [mem 0x7c000000-0xfeafffff]
[    0.844230] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.844232] pci 0000:00:01.0: PME# disabled
[    0.844298] pci 0000:00:16.0: reg 10: [mem 0xf7a0a000-0xf7a0a00f 64bit]
[    0.844355] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.844359] pci 0000:00:16.0: PME# disabled
[    0.844417] pci 0000:00:1a.0: reg 10: [mem 0xf7a08000-0xf7a083ff]
[    0.844479] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.844483] pci 0000:00:1a.0: PME# disabled
[    0.844526] pci 0000:00:1b.0: reg 10: [mem 0xf7a00000-0xf7a03fff 64bit]
[    0.844582] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.844585] pci 0000:00:1b.0: PME# disabled
[    0.844673] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.844678] pci 0000:00:1c.0: PME# disabled
[    0.844768] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.844772] pci 0000:00:1c.1: PME# disabled
[    0.844862] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.844867] pci 0000:00:1c.2: PME# disabled
[    0.844959] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.844963] pci 0000:00:1c.3: PME# disabled
[    0.845052] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.845057] pci 0000:00:1c.4: PME# disabled
[    0.845148] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.845152] pci 0000:00:1c.5: PME# disabled
[    0.845205] pci 0000:00:1d.0: reg 10: [mem 0xf7a07000-0xf7a073ff]
[    0.845268] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.845272] pci 0000:00:1d.0: PME# disabled
[    0.845463] pci 0000:00:1f.2: reg 10: [io  0xe070-0xe077]
[    0.845469] pci 0000:00:1f.2: reg 14: [io  0xe060-0xe063]
[    0.845476] pci 0000:00:1f.2: reg 18: [io  0xe050-0xe057]
[    0.845483] pci 0000:00:1f.2: reg 1c: [io  0xe040-0xe043]
[    0.845489] pci 0000:00:1f.2: reg 20: [io  0xe020-0xe03f]
[    0.845496] pci 0000:00:1f.2: reg 24: [mem 0xf7a06000-0xf7a067ff]
[    0.845539] pci 0000:00:1f.2: PME# supported from D3hot
[    0.845543] pci 0000:00:1f.2: PME# disabled
[    0.845580] pci 0000:00:1f.3: reg 10: [mem 0xf7a05000-0xf7a050ff 64bit]
[    0.845598] pci 0000:00:1f.3: reg 20: [io  0xe000-0xe01f]
[    0.845658] pci 0000:00:1f.6: reg 10: [mem 0xf7a04000-0xf7a04fff 64bit]
[    0.845756] pci 0000:01:00.0: reg 10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.845765] pci 0000:01:00.0: reg 18: [mem 0xf0020000-0xf003ffff 64bit]
[    0.845770] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.845778] pci 0000:01:00.0: reg 30: [mem 0xf0000000-0xf001ffff pref]
[    0.845795] pci 0000:01:00.0: supports D1 D2
[    0.845821] pci 0000:01:00.1: reg 10: [mem 0xf0040000-0xf0043fff 64bit]
[    0.845850] pci 0000:01:00.1: supports D1 D2
[    0.845866] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.845869] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.845871] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf00fffff]
[    0.845874] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.845928] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.845932] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.845937] pci 0000:00:1c.0:   bridge window [mem 0xf6600000-0xf79fffff]
[    0.845944] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.846055] pci 0000:03:00.0: reg 10: [mem 0xf5200000-0xf5201fff 64bit]
[    0.846163] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.846170] pci 0000:03:00.0: PME# disabled
[    0.846205] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.846209] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.846213] pci 0000:00:1c.1:   bridge window [mem 0xf5200000-0xf65fffff]
[    0.846220] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.846275] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.846279] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    0.846283] pci 0000:00:1c.2:   bridge window [mem 0xf3e00000-0xf51fffff]
[    0.846290] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.846345] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.846350] pci 0000:00:1c.3:   bridge window [io  0x9000-0x9fff]
[    0.846354] pci 0000:00:1c.3:   bridge window [mem 0xf2a00000-0xf3dfffff]
[    0.846361] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.846417] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.846421] pci 0000:00:1c.4:   bridge window [io  0x8000-0x8fff]
[    0.846425] pci 0000:00:1c.4:   bridge window [mem 0xf1600000-0xf29fffff]
[    0.846432] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.846522] pci 0000:07:00.0: reg 10: [mem 0xf0205000-0xf02050ff]
[    0.846673] pci 0000:07:00.2: reg 10: [mem 0xf0204000-0xf02040ff]
[    0.846824] pci 0000:07:00.5: reg 10: [mem 0xf0200000-0xf0203fff]
[    0.846843] pci 0000:07:00.5: reg 18: [io  0x7100-0x717f]
[    0.846853] pci 0000:07:00.5: reg 1c: [io  0x7000-0x70ff]
[    0.846928] pci 0000:07:00.5: PME# supported from D0 D3hot D3cold
[    0.846934] pci 0000:07:00.5: PME# disabled
[    0.846970] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
[    0.846974] pci 0000:00:1c.5:   bridge window [io  0x7000-0x7fff]
[    0.846979] pci 0000:00:1c.5:   bridge window [mem 0xf0200000-0xf15fffff]
[    0.846986] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.847057] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[    0.847062] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.847066] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.847073] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.847076] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.847077] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.847079] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.847081] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.847083] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.847084] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.847086] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.847088] pci 0000:00:1e.0:   bridge window [mem 0x7c000000-0xfeafffff] (subtractive decode)
[    0.847135] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.847373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.847555] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.847696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.847837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.847978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.848117] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.848259] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.848373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGR._PRT]
[    0.865888] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 3f])
[    0.866375] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.866507] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.866636] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    0.866764] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.866895] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.867021] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.867144] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.867266] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.867323] HEST: Table is not found!
[    0.867384] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.867389] vgaarb: loaded
[    0.867491] SCSI subsystem initialized
[    0.867602] libata version 3.00 loaded.
[    0.867644] usbcore: registered new interface driver usbfs
[    0.867651] usbcore: registered new interface driver hub
[    0.867678] usbcore: registered new device driver usb
[    0.867779] ACPI: WMI: Mapper loaded
[    0.867781] PCI: Using ACPI for IRQ routing
[    0.867783] PCI: pci_cache_line_size set to 64 bytes
[    0.867896] reserve RAM buffer: 000000000009bc00 - 000000000009ffff 
[    0.867899] reserve RAM buffer: 000000007adf1000 - 000000007bffffff 
[    0.867989] NetLabel: Initializing
[    0.867991] NetLabel:  domain hash size = 128
[    0.867992] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.868002] NetLabel:  unlabeled traffic allowed by default
[    0.868040] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.868044] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.870063] Switching to clocksource tsc
[    0.876734] AppArmor: AppArmor Filesystem Enabled
[    0.876749] pnp: PnP ACPI init
[    0.876769] ACPI: bus type pnp registered
[    0.879327] pnp: PnP ACPI: found 11 devices
[    0.879329] ACPI: ACPI bus type pnp unregistered
[    0.879339] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.879342] system 00:05: [io  0xff00-0xff0f] has been reserved
[    0.879343] system 00:05: [io  0xffff] has been reserved
[    0.879345] system 00:05: [io  0xffff] has been reserved
[    0.879347] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.879348] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.879350] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.879355] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.879357] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.879359] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.879360] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.879363] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.879364] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.879366] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.879368] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.879370] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.879372] system 00:09: [mem 0xf7fff000-0xf7ffffff] has been reserved
[    0.884925] pci 0000:00:1c.0: BAR 15: assigned [mem 0x7c000000-0x7c1fffff 64bit pref]
[    0.884929] pci 0000:00:1c.1: BAR 15: assigned [mem 0x7c200000-0x7c3fffff 64bit pref]
[    0.884931] pci 0000:00:1c.2: BAR 15: assigned [mem 0x7c400000-0x7c5fffff 64bit pref]
[    0.884934] pci 0000:00:1c.3: BAR 15: assigned [mem 0x7c600000-0x7c7fffff 64bit pref]
[    0.884936] pci 0000:00:1c.4: BAR 15: assigned [mem 0x7c800000-0x7c9fffff 64bit pref]
[    0.884939] pci 0000:00:1c.5: BAR 15: assigned [mem 0x7ca00000-0x7cbfffff 64bit pref]
[    0.884941] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.884943] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.884946] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf00fffff]
[    0.884949] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    0.884952] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.884955] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.884961] pci 0000:00:1c.0:   bridge window [mem 0xf6600000-0xf79fffff]
[    0.884966] pci 0000:00:1c.0:   bridge window [mem 0x7c000000-0x7c1fffff 64bit pref]
[    0.884973] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.884976] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.884982] pci 0000:00:1c.1:   bridge window [mem 0xf5200000-0xf65fffff]
[    0.884987] pci 0000:00:1c.1:   bridge window [mem 0x7c200000-0x7c3fffff 64bit pref]
[    0.884995] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.884998] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    0.885004] pci 0000:00:1c.2:   bridge window [mem 0xf3e00000-0xf51fffff]
[    0.885008] pci 0000:00:1c.2:   bridge window [mem 0x7c400000-0x7c5fffff 64bit pref]
[    0.885015] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.885018] pci 0000:00:1c.3:   bridge window [io  0x9000-0x9fff]
[    0.885024] pci 0000:00:1c.3:   bridge window [mem 0xf2a00000-0xf3dfffff]
[    0.885029] pci 0000:00:1c.3:   bridge window [mem 0x7c600000-0x7c7fffff 64bit pref]
[    0.885037] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.885040] pci 0000:00:1c.4:   bridge window [io  0x8000-0x8fff]
[    0.885046] pci 0000:00:1c.4:   bridge window [mem 0xf1600000-0xf29fffff]
[    0.885050] pci 0000:00:1c.4:   bridge window [mem 0x7c800000-0x7c9fffff 64bit pref]
[    0.885058] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
[    0.885061] pci 0000:00:1c.5:   bridge window [io  0x7000-0x7fff]
[    0.885066] pci 0000:00:1c.5:   bridge window [mem 0xf0200000-0xf15fffff]
[    0.885071] pci 0000:00:1c.5:   bridge window [mem 0x7ca00000-0x7cbfffff 64bit pref]
[    0.885078] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    0.885080] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.885085] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.885089] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.885105]   alloc irq_desc for 16 on node -1
[    0.885106]   alloc kstat_irqs on node -1
[    0.885113] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.885116] pci 0000:00:01.0: setting latency timer to 64
[    0.885125] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.885129] pci 0000:00:1c.0: setting latency timer to 64
[    0.885139]   alloc irq_desc for 17 on node -1
[    0.885140]   alloc kstat_irqs on node -1
[    0.885143] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.885148] pci 0000:00:1c.1: setting latency timer to 64
[    0.885158]   alloc irq_desc for 18 on node -1
[    0.885159]   alloc kstat_irqs on node -1
[    0.885162] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.885166] pci 0000:00:1c.2: setting latency timer to 64
[    0.885176]   alloc irq_desc for 19 on node -1
[    0.885177]   alloc kstat_irqs on node -1
[    0.885180] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.885184] pci 0000:00:1c.3: setting latency timer to 64
[    0.885193] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.885197] pci 0000:00:1c.4: setting latency timer to 64
[    0.885207] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.885211] pci 0000:00:1c.5: setting latency timer to 64
[    0.885219] pci 0000:00:1e.0: setting latency timer to 64
[    0.885224] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.885225] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.885227] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.885229] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.885230] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.885232] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.885233] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.885235] pci_bus 0000:00: resource 11 [mem 0x7c000000-0xfeafffff]
[    0.885237] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.885239] pci_bus 0000:01: resource 1 [mem 0xe0000000-0xf00fffff]
[    0.885240] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.885242] pci_bus 0000:02: resource 1 [mem 0xf6600000-0xf79fffff]
[    0.885244] pci_bus 0000:02: resource 2 [mem 0x7c000000-0x7c1fffff 64bit pref]
[    0.885245] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.885247] pci_bus 0000:03: resource 1 [mem 0xf5200000-0xf65fffff]
[    0.885249] pci_bus 0000:03: resource 2 [mem 0x7c200000-0x7c3fffff 64bit pref]
[    0.885250] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    0.885252] pci_bus 0000:04: resource 1 [mem 0xf3e00000-0xf51fffff]
[    0.885254] pci_bus 0000:04: resource 2 [mem 0x7c400000-0x7c5fffff 64bit pref]
[    0.885255] pci_bus 0000:05: resource 0 [io  0x9000-0x9fff]
[    0.885257] pci_bus 0000:05: resource 1 [mem 0xf2a00000-0xf3dfffff]
[    0.885259] pci_bus 0000:05: resource 2 [mem 0x7c600000-0x7c7fffff 64bit pref]
[    0.885260] pci_bus 0000:06: resource 0 [io  0x8000-0x8fff]
[    0.885262] pci_bus 0000:06: resource 1 [mem 0xf1600000-0xf29fffff]
[    0.885264] pci_bus 0000:06: resource 2 [mem 0x7c800000-0x7c9fffff 64bit pref]
[    0.885265] pci_bus 0000:07: resource 0 [io  0x7000-0x7fff]
[    0.885267] pci_bus 0000:07: resource 1 [mem 0xf0200000-0xf15fffff]
[    0.885269] pci_bus 0000:07: resource 2 [mem 0x7ca00000-0x7cbfffff 64bit pref]
[    0.885271] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    0.885272] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    0.885274] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.885275] pci_bus 0000:08: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.885277] pci_bus 0000:08: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.885279] pci_bus 0000:08: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.885280] pci_bus 0000:08: resource 10 [mem 0x000dc000-0x000dffff]
[    0.885282] pci_bus 0000:08: resource 11 [mem 0x7c000000-0xfeafffff]
[    0.885316] NET: Registered protocol family 2
[    0.885411] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.885959] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.887224] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.887533] TCP: Hash tables configured (established 262144 bind 65536)
[    0.887535] TCP reno registered
[    0.887543] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.887557] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.887661] NET: Registered protocol family 1
[    0.943361] pci 0000:01:00.0: Boot video device
[    0.943392] PCI: CLS 64 bytes, default 64
[    0.943645] Scanning for low memory corruption every 60 seconds
[    0.943754] audit: initializing netlink socket (disabled)
[    0.943764] type=2000 audit(1295110883.800:1): initialized
[    0.955460] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.956617] VFS: Disk quotas dquot_6.5.2
[    0.956664] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.957141] fuse init (API version 7.14)
[    0.957207] msgmni has been set to 3814
[    0.957485] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.957487] io scheduler noop registered
[    0.957489] io scheduler deadline registered
[    0.957515] io scheduler cfq registered (default)
[    0.957613] pcieport 0000:00:01.0: setting latency timer to 64
[    0.957632]   alloc irq_desc for 40 on node -1
[    0.957633]   alloc kstat_irqs on node -1
[    0.957642] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.957687] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.957728]   alloc irq_desc for 41 on node -1
[    0.957729]   alloc kstat_irqs on node -1
[    0.957737] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.957813] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.957854]   alloc irq_desc for 42 on node -1
[    0.957855]   alloc kstat_irqs on node -1
[    0.957863] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.957945] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.957985]   alloc irq_desc for 43 on node -1
[    0.957986]   alloc kstat_irqs on node -1
[    0.957997] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.958073] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.958113]   alloc irq_desc for 44 on node -1
[    0.958114]   alloc kstat_irqs on node -1
[    0.958123] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.958200] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.958241]   alloc irq_desc for 45 on node -1
[    0.958242]   alloc kstat_irqs on node -1
[    0.958249] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
[    0.958324] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.958365]   alloc irq_desc for 46 on node -1
[    0.958366]   alloc kstat_irqs on node -1
[    0.958373] pcieport 0000:00:1c.5: irq 46 for MSI/MSI-X
[    0.958456] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.958666] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.958720] intel_idle: MWAIT substates: 0x1120
[    0.958722] intel_idle: v0.4 model 0x25
[    0.958723] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.958856] ACPI: AC Adapter [AC0] (on-line)
[    0.958919] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.960627] ACPI: Lid Switch [LID]
[    0.960659] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.960663] ACPI: Sleep Button [SLPB]
[    0.960689] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.960692] ACPI: Power Button [PWRB]
[    0.960717] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.960720] ACPI: Power Button [PWRF]
[    0.961343] ACPI: acpi_idle yielding to intel_idle
[    0.965576] thermal LNXTHERM:01: registered as thermal_zone0
[    0.965582] ACPI: Thermal Zone [TZ00] (64 C)
[    0.965642] ERST: Table is not found!
[    0.966400] Linux agpgart interface v0.103
[    0.966426] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.967211] ACPI: Battery Slot [BAT0] (battery present)
[    0.967626] brd: module loaded
[    0.967956] loop: module loaded
[    0.968290] Fixed MDIO Bus: probed
[    0.968311] PPP generic driver version 2.4.2
[    0.968333] tun: Universal TUN/TAP device driver, 1.6
[    0.968335] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.968384] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.968411] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.968425] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.968429] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.968462] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.968492] ehci_hcd 0000:00:1a.0: debug port 2
[    0.972393] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.972411] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7a08000
[    0.993197] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.993331] hub 1-0:1.0: USB hub found
[    0.993337] hub 1-0:1.0: 2 ports detected
[    0.993411]   alloc irq_desc for 23 on node -1
[    0.993412]   alloc kstat_irqs on node -1
[    0.993420] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.993445] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.993448] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.993478] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.993504] ehci_hcd 0000:00:1d.0: debug port 2
[    0.997401] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.997418] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7a07000
[    1.013186] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.013320] hub 2-0:1.0: USB hub found
[    1.013325] hub 2-0:1.0: 2 ports detected
[    1.013389] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.013401] uhci_hcd: USB Universal Host Controller Interface driver
[    1.013504] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.015011] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.015852] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.015858] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.015860] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.015862] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.015864] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.015921] mice: PS/2 mouse device common for all mice
[    1.016035] rtc_cmos 00:06: RTC can wake from S4
[    1.016066] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.016095] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.016164] device-mapper: uevent: version 1.0.3
[    1.016234] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.016331] device-mapper: multipath: version 1.1.1 loaded
[    1.016334] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.016570] cpuidle: using governor ladder
[    1.016678] cpuidle: using governor menu
[    1.016888] TCP cubic registered
[    1.016973] NET: Registered protocol family 10
[    1.017229] lo: Disabled Privacy Extensions
[    1.017368] NET: Registered protocol family 17
[    1.019117] PM: Resume from disk failed.
[    1.019129] registered taskstats version 1
[    1.019567]   Magic number: 11:858:36
[    1.019579] bdi 7:1: hash matches
[    1.019680] rtc_cmos 00:06: setting system clock to 2011-01-15 17:01:24 UTC (1295110884)
[    1.019683] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.019684] EDD information not available.
[    1.049942] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.125091] Freeing initrd memory: 16320k freed
[    1.128779] Freeing unused kernel memory: 908k freed
[    1.128987] Write protecting the kernel read-only data: 10240k
[    1.129199] Freeing unused kernel memory: 412k freed
[    1.129440] Freeing unused kernel memory: 1644k freed
[    1.143670] udev[101]: starting version 163
[    1.185915] jme: JMicron JMC2XX ethernet driver version 1.0.6
[    1.185964] jme 0000:07:00.5: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.185980] jme 0000:07:00.5: setting latency timer to 64
[    1.187010] jme 0000:07:00.5: eth0: JMC250 Gigabit Ethernet ver:23 rev:3 macaddr:20:cf:30:5d:d0:8a
[    1.199092] sdhci: Secure Digital Host Controller Interface driver
[    1.199095] sdhci: Copyright(c) Pierre Ossman
[    1.201667] sdhci-pci 0000:07:00.0: SDHCI controller found [197b:2382] (rev 80)
[    1.201696] sdhci-pci 0000:07:00.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.201788] sdhci-pci 0000:07:00.0: setting latency timer to 64
[    1.215723] acpi device:1a: registered as cooling_device4
[    1.216009] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:17/LNXVIDEO:00/input/input5
[    1.216068] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.226476] Registered led device: mmc0::
[    1.226528] mmc0: SDHCI controller on PCI [0000:07:00.0] using ADMA
[    1.226549] sdhci-pci 0000:07:00.2: SDHCI controller found [197b:2381] (rev 80)
[    1.226579] sdhci-pci 0000:07:00.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.226589] sdhci-pci 0000:07:00.2: Refusing to bind to secondary interface.
[    1.226598] sdhci-pci 0000:07:00.2: PCI INT B disabled
[    1.232082] [drm] Initialized drm 1.1.0 20060810
[    1.244769] ahci 0000:00:1f.2: version 3.0
[    1.244790] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.244840]   alloc irq_desc for 47 on node -1
[    1.244842]   alloc kstat_irqs on node -1
[    1.244856] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
[    1.244895] ahci: SSS flag set, parallel bus scan disabled
[    1.244949] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.244953] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    1.244960] ahci 0000:00:1f.2: setting latency timer to 64
[    1.265168] [drm] radeon defaulting to kernel modesetting.
[    1.265170] [drm] radeon kernel modesetting enabled.
[    1.265223] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.265228] radeon 0000:01:00.0: setting latency timer to 64
[    1.266522] [drm] initializing kernel modesetting (REDWOOD 0x1002:0x68C0).
[    1.266735] [drm] register mmio base: 0xF0020000
[    1.266738] [drm] register mmio size: 131072
[    1.266879] ATOM BIOS: MADISON
[    1.266897] [drm] Clocks initialized !
[    1.266914] radeon 0000:01:00.0: VRAM: 2048M 0x00000000 - 0x7FFFFFFF (256M used)
[    1.266916] radeon 0000:01:00.0: GTT: 512M 0x80000000 - 0x9FFFFFFF
[    1.267980] [drm] Detected VRAM RAM=2048M, BAR=256M
[    1.267983] [drm] RAM width 128bits DDR
[    1.268101] [TTM] Zone  kernel: Available graphics memory: 986214 kiB.
[    1.268105] [TTM] Initializing pool allocator.
[    1.268133] [drm] radeon: 256M of VRAM memory ready
[    1.268136] [drm] radeon: 512M of GTT memory ready.
[    1.268209]   alloc irq_desc for 48 on node -1
[    1.268212]   alloc kstat_irqs on node -1
[    1.268230] radeon 0000:01:00.0: irq 48 for MSI/MSI-X
[    1.268236] radeon 0000:01:00.0: radeon: using MSI.
[    1.268272] [drm] radeon: irq initialized.
[    1.268275] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.268740] [drm] Loading REDWOOD Microcode
[    1.291089] [drm] ring test succeeded in 1 usecs
[    1.291187] [drm] radeon: ib pool ready.
[    1.291300] [drm] ib test succeeded in 0 usecs
[    1.291440] [drm] Radeon Display Connectors
[    1.291441] [drm] Connector 0:
[    1.291442] [drm]   LVDS
[    1.291444] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[    1.291445] [drm]   Encoders:
[    1.291446] [drm]     LCD1: INTERNAL_UNIPHY
[    1.291447] [drm] Connector 1:
[    1.291448] [drm]   HDMI-A
[    1.291449] [drm]   HPD1
[    1.291450] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    1.291451] [drm]   Encoders:
[    1.291452] [drm]     DFP1: INTERNAL_UNIPHY1
[    1.291453] [drm] Connector 2:
[    1.291454] [drm]   VGA
[    1.291455] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    1.291456] [drm]   Encoders:
[    1.291458] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    1.310644] scsi0 : ahci
[    1.310768] scsi1 : ahci
[    1.310834] scsi2 : ahci
[    1.310896] scsi3 : ahci
[    1.310957] scsi4 : ahci
[    1.311016] scsi5 : ahci
[    1.311066] ata1: SATA max UDMA/133 abar m2048@0xf7a06000 port 0xf7a06100 irq 47
[    1.311071] ata2: SATA max UDMA/133 abar m2048@0xf7a06000 port 0xf7a06180 irq 47
[    1.311072] ata3: DUMMY
[    1.311073] ata4: DUMMY
[    1.311076] ata5: SATA max UDMA/133 abar m2048@0xf7a06000 port 0xf7a06300 irq 47
[    1.311079] ata6: SATA max UDMA/133 abar m2048@0xf7a06000 port 0xf7a06380 irq 47
[    1.330589] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.481719] hub 1-1:1.0: USB hub found
[    1.481815] hub 1-1:1.0: 6 ports detected
[    1.523922] [drm] Internal thermal controller with fan control
[    1.523938] [drm] radeon: power management initialized
[    1.600997] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.651622] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.704931] ata1.00: ATA-8: ST9320325AS, 0003SDM1, max UDMA/133
[    1.704933] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.707117] ata1.00: configured for UDMA/133
[    1.720457] scsi 0:0:0:0: Direct-Access     ATA      ST9320325AS      0003 PQ: 0 ANSI: 5
[    1.720602] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.720626] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.720715] sd 0:0:0:0: [sda] Write Protect is off
[    1.720717] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.720738] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.720881]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    1.751336] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.751447] hub 2-1:1.0: USB hub found
[    1.751539] hub 2-1:1.0: 8 ports detected
[    1.831675] usb 1-1.2: new high speed USB device using ehci_hcd and address 3
[    2.031933] [drm] fb mappable at 0xE0140000
[    2.031935] [drm] vram apper at 0xE0000000
[    2.031936] [drm] size 4325376
[    2.031937] [drm] fb depth is 24
[    2.031938] [drm]    pitch is 5632
[    2.050359] usb 1-1.5: new full speed USB device using ehci_hcd and address 4
[    2.469326] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.475458] ata2.00: ATAPI: Slimtype DVD A  DS8A4S, JA22, max UDMA/100
[    2.476867] ata2.00: configured for UDMA/100
[    2.503326] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A4S    JA22 PQ: 0 ANSI: 5
[    2.513796] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.513800] Uniform CD-ROM driver Revision: 3.20
[    2.513936] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.514005] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.860959] ata5: SATA link down (SStatus 0 SControl 300)
[    3.208306] Console: switching to colour frame buffer device 170x48
[    3.210663] fb0: radeondrmfb frame buffer device
[    3.210664] drm: registered panic notifier
[    3.210668] Slow work thread pool: Starting up
[    3.210844] Slow work thread pool: Ready
[    3.210860] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[    3.230749] ata6: SATA link down (SStatus 0 SControl 300)
[    4.788739] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    4.788743] EXT4-fs (sda5): write access will be enabled during recovery
[    6.879044] EXT4-fs (sda5): orphan cleanup on readonly fs
[    6.879053] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1969773
[    6.879110] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1969769
[    6.879129] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1969766
[    6.879138] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1969764
[    6.879148] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1969761
[    6.879157] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1969760
[    6.879168] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1969753
[    6.879196] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1969746
[    6.879206] EXT4-fs (sda5): 8 orphan inodes deleted
[    6.879208] EXT4-fs (sda5): recovery complete
[    7.220523] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    9.570739] Adding 5117948k swap on /dev/sda6.  Priority:-1 extents:1 across:5117948k 
[   10.631039] udev[493]: starting version 163
[   10.631766] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   12.629828] Bluetooth: Core ver 2.15
[   12.629883] NET: Registered protocol family 31
[   12.629885] Bluetooth: HCI device and connection manager initialized
[   12.629887] Bluetooth: HCI socket layer initialized
[   12.764372] lp: driver loaded but no devices found
[   12.832787] cfg80211: Calling CRDA to update world regulatory domain
[   12.894299] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   12.894607] usbcore: registered new interface driver btusb
[   13.151381] elantech: assuming hardware version 2, firmware version 4.1.1
[   13.170258] Linux video capture interface: v2.00
[   13.179668] elantech: Synaptics capabilities query result 0x7e, 0x13, 0x0d.
[   13.183147] asus_laptop: Asus Laptop Support version 0.42
[   13.186093] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   13.186115] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.186224] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   13.186306] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[   13.188803] asus_laptop:   K42JA model detected
[   13.189471] asus_laptop: Backlight controlled by ACPI video driver
[   13.189517] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input6
[   13.257037] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input7
[   13.518216] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:5130)
[   13.525547] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input8
[   13.525620] usbcore: registered new interface driver uvcvideo
[   13.525622] USB Video Class driver (v0.1.0)
[   13.788574] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.788578] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   13.788645] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.788653] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.788686] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   13.809349] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.809447]   alloc irq_desc for 49 on node -1
[   13.809448]   alloc kstat_irqs on node -1
[   13.809489] iwlagn 0000:03:00.0: irq 49 for MSI/MSI-X
[   14.072395] type=1400 audit(1295082097.543:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=683 comm="apparmor_parser"
[   14.072404] type=1400 audit(1295082097.543:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=664 comm="apparmor_parser"
[   14.072858] type=1400 audit(1295082097.543:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=683 comm="apparmor_parser"
[   14.072867] type=1400 audit(1295082097.543:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=664 comm="apparmor_parser"
[   14.073117] type=1400 audit(1295082097.543:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=683 comm="apparmor_parser"
[   14.073126] type=1400 audit(1295082097.543:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=664 comm="apparmor_parser"
[   14.287482] cfg80211: World regulatory domain updated:
[   14.287485]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.287487]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.287489]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.287491]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.287492]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.287494]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.368729] iwlagn 0000:03:00.0: loaded firmware version 128.50.3.1 build 13488
[   14.852249] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.650324]   alloc irq_desc for 22 on node -1
[   15.650327]   alloc kstat_irqs on node -1
[   15.650336] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.650393]   alloc irq_desc for 50 on node -1
[   15.650395]   alloc kstat_irqs on node -1
[   15.650407] HDA Intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[   15.650547] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.940376] hda_codec: ALC259: BIOS auto-probing.
[   15.944769] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.944819]   alloc irq_desc for 51 on node -1
[   15.944820]   alloc kstat_irqs on node -1
[   15.944832] HDA Intel 0000:01:00.1: irq 51 for MSI/MSI-X
[   15.944856] HDA Intel 0000:01:00.1: setting latency timer to 64
[   17.505192] type=1400 audit(1295082100.983:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1070 comm="apparmor_parser"
[   17.505686] type=1400 audit(1295082100.983:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1070 comm="apparmor_parser"
[   17.733379] ppdev: user-space parallel port driver
[   17.832761] type=1400 audit(1295082101.313:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1138 comm="apparmor_parser"
[   17.833256] type=1400 audit(1295082101.313:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1138 comm="apparmor_parser"
[   20.749874] Bluetooth: L2CAP ver 2.14
[   20.749879] Bluetooth: L2CAP socket layer initialized
[   20.820793] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.843572] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.843574] Bluetooth: BNEP filters: protocol multicast
[   20.851639]   alloc irq_desc for 52 on node -1
[   20.851641]   alloc kstat_irqs on node -1
[   20.851659] jme 0000:07:00.5: irq 52 for MSI/MSI-X
[   20.852047] jme 0000:07:00.5: eth0: Link is down.
[   20.852181] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.345163] Bluetooth: SCO (Voice Link) ver 0.6
[   21.345166] Bluetooth: SCO socket layer initialized
[   21.564368] Bluetooth: RFCOMM TTY layer initialized
[   21.564373] Bluetooth: RFCOMM socket layer initialized
[   21.564374] Bluetooth: RFCOMM ver 1.11
[   23.595010] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   32.678834] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   33.990680] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   40.343928] Intel AES-NI instructions are not detected.
[   40.382688] padlock: VIA PadLock not detected.
[   46.895646] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[   47.103446] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[   47.295269] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[   47.495153] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[   63.207226] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[   63.404064] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[   63.603941] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[   63.803860] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[   73.844885] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[   74.037943] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[   74.237830] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[   74.439571] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[   84.511911] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[   84.722393] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[   84.921652] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[   85.123392] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[   95.151984] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[   95.345594] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[   95.545475] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[   95.745367] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  105.819604] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  106.009455] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  106.209360] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  106.411073] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  107.376254] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  107.569184] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  107.769047] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  107.968932] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  160.789414] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  160.987660] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  161.187562] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  161.387421] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  171.420572] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  171.621537] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  171.811405] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  172.011331] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  182.094407] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  182.285358] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  182.486477] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  182.685145] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  198.405838] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  198.595921] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  198.795805] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  198.995695] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  209.041223] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  209.239765] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  209.439697] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  209.639539] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  219.715182] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  219.915490] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  220.113524] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  220.313362] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  221.045231] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  221.244029] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  221.443957] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  221.642581] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  231.715952] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  231.907233] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  232.108394] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  232.306441] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  242.346852] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  242.541091] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  242.742256] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  242.940230] wlan0: direct probe to 00:27:19:14:c2:ca timed out
[  253.020753] wlan0: direct probe to 00:27:19:14:c2:ca (try 1)
[  253.214333] wlan0: direct probe to 00:27:19:14:c2:ca (try 2)
[  253.414248] wlan0: direct probe to 00:27:19:14:c2:ca (try 3)
[  253.614110] wlan0: direct probe to 00:27:19:14:c2:ca timed out

```

lshw -C network
```

  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:5c:d1:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-24-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:49 memory:f5200000-f5201fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:07:00.5
       logical name: eth0
       version: 03
       serial: 20:cf:30:5d:d0:8a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.6 duplex=full ip=192.168.1.103 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:51 memory:f0200000-f0203fff ioport:7100(size=128) ioport:7000(size=256)

```

lspci
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
**03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000**
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
07:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

I've tried Linux Mint Debian Edition, and had the same results.

If additional information is necessary, please ask. I'm a CS student who has dabbled a bit in Linux, so I'm willing to do some technical stuff. I like learning :)

---

### Post by grahammechanical on 2011-01-15
If when you left click the wireless icon you see a list of available wireless networks, then we can assume that the wireless adapter is recognized by Ubuntu and is working.

Failure to connect when you select a network can be caused by using the wrong pass phrase in the request for authentication. Network manager will remember the password that you use even if it is the wrong one. All attempts to connect will fail because the password is wrong.

You say this:

> The router is set up to use WPA for security. I didn't use WPA2 as I read something

If the router is set for WPA security, then Network Manager must also be set to connect using WPA security. And you will need the wireless key, also called WPA-PSK. It should be typed on a label on the bottom of the router. Do not use your login password. Even with the right pass phrase the connection will fail because there is conflict over the transmission encryption method. It is the wireless transmissions between the modem and the computer that are encrypted and not the password.

Regards.

By the way, I am using WPA. I do not have any problems.

---

### Post by Lugkhast on 2011-01-15
Interestingly, I've just tried Natty Alpha 1, and WiFi works from a live USB. I'm currently installing it, as I've been wanting to test-drive Unity, anyway :)

---

### Post by yoneal on 2011-01-30
> Interestingly, I've just tried Natty Alpha 1, and WiFi works from a live USB. I'm currently installing it, as I've been wanting to test-drive Unity, anyway

I installed the latest kernel version from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/"); and now the wireless works! Just download the generic kernel header, desired architecture specific header, and desired architecture specific kernel image; then install simply by using ```
dpkg -i *file.deb*
``` You can also add the ppa to your package manager.

Proprietary drivers won't work though (fglrx) because it is not compiled for 2.6.37 kernel. I'll work on it again once I have time.

---

### Post by Bucky Ball on 2011-01-30
You don't need to use code, just double click the .deb file.

You must install in the correct order; headers first, image second.

---

