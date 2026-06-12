---
title: "Tv tuner lv5h"
date: 2010-04-06
forum: Multimedia Software
---

### Post by kounabi on 2010-04-06
hey guys

I try to get my lv5h usb tv stick to work under ubuntu 9.10 but it doesn't recognize it at all.

lsusb:
```
Bus 003 Device 002: ID 046d:c047 Logitech, Inc. Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 6000:0002  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

for further information please ask...thnx!!

---

### Post by kounabi on 2010-11-06
...

---

### Post by xc3RnbFO8P on 2010-11-06
Do have a Windows computer?
Plug it in and get it warm then plug it into your ubuntu computer 
and show the output of:
> lsusb
and
> dmesg

---

### Post by kounabi on 2010-11-08
Hi!

thanks for the reply!!

I've done what you said but nothing changed ....

here 's the output for the device...

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf27c000 (usable)
[    0.000000]  BIOS-e820: 00000000bf27c000 - 00000000bf282000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf282000 - 00000000bf3ea000 (usable)
[    0.000000]  BIOS-e820: 00000000bf3ea000 - 00000000bf40f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf40f000 - 00000000bf46f000 (usable)
[    0.000000]  BIOS-e820: 00000000bf46f000 - 00000000bf470000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf470000 - 00000000bf4f1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf4f1000 - 00000000bf70f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf70f000 - 00000000bf717000 (usable)
[    0.000000]  BIOS-e820: 00000000bf717000 - 00000000bf71f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf71f000 - 00000000bf77e000 (usable)
[    0.000000]  BIOS-e820: 00000000bf77e000 - 00000000bf79f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf79f000 - 00000000bf7e2000 (usable)
[    0.000000]  BIOS-e820: 00000000bf7e2000 - 00000000bf7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf7ff000 - 00000000bf800000 (usable)
[    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0304000 - 00000000f0305000 (reserved)
[    0.000000]  BIOS-e820: 00000000feaff000 - 00000000feb00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xbf800 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 base 138000000 mask FF8000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009c400 (usable)
[    0.000000]  modified: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf27c000 (usable)
[    0.000000]  modified: 00000000bf27c000 - 00000000bf282000 (reserved)
[    0.000000]  modified: 00000000bf282000 - 00000000bf3ea000 (usable)
[    0.000000]  modified: 00000000bf3ea000 - 00000000bf40f000 (reserved)
[    0.000000]  modified: 00000000bf40f000 - 00000000bf46f000 (usable)
[    0.000000]  modified: 00000000bf46f000 - 00000000bf470000 (reserved)
[    0.000000]  modified: 00000000bf470000 - 00000000bf4f1000 (ACPI NVS)
[    0.000000]  modified: 00000000bf4f1000 - 00000000bf70f000 (reserved)
[    0.000000]  modified: 00000000bf70f000 - 00000000bf717000 (usable)
[    0.000000]  modified: 00000000bf717000 - 00000000bf71f000 (reserved)
[    0.000000]  modified: 00000000bf71f000 - 00000000bf77e000 (usable)
[    0.000000]  modified: 00000000bf77e000 - 00000000bf79f000 (ACPI NVS)
[    0.000000]  modified: 00000000bf79f000 - 00000000bf7e2000 (usable)
[    0.000000]  modified: 00000000bf7e2000 - 00000000bf7ff000 (ACPI data)
[    0.000000]  modified: 00000000bf7ff000 - 00000000bf800000 (usable)
[    0.000000]  modified: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000f0304000 - 00000000f0305000 (reserved)
[    0.000000]  modified: 00000000feaff000 - 00000000feb00000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f7260] f7260
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 3707b000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a5000 - 01919806
[    0.000000] Move RAMDISK from 000000003707b000 - 0000000037fef805 to 009a5000 - 01919805
[    0.000000] ACPI: RSDP 000f7180 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bf7f467a 00064 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: FACP bf7e4000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bf7e5000 0A47C (v02 Intel  CALPELLA 06040000 INTL 20060912)
[    0.000000] ACPI: FACS bf79bfc0 00040
[    0.000000] ACPI: HPET bf7fecfa 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bf7fed32 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bf7fed6e 00084 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bf7fedf2 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bf7fee1a 00176 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: OSFR bf7fef90 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: SSDT bf7e3000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2176MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bf800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bf27c
[    0.000000]     0: 0x000bf282 -> 0x000bf3ea
[    0.000000]     0: 0x000bf40f -> 0x000bf46f
[    0.000000]     0: 0x000bf70f -> 0x000bf717
[    0.000000]     0: 0x000bf71f -> 0x000bf77e
[    0.000000]     0: 0x000bf79f -> 0x000bf7e2
[    0.000000]     0: 0x000bf7ff -> 0x000bf800
[    0.000000] On node 0 totalpages: 783484
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c191b020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4353 pages used for memmap
[    0.000000]   HighMem zone: 551920 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] early_res array is doubled to 128 at [16800 - 177ff]
[    0.000000] PERCPU: Embedded 14 pages/cpu @c3400000 s36416 r0 d20928 u1048576
[    0.000000] pcpu-alloc: s36416 r0 d20928 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777355
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=b6e579cc-26ca-4f90-9a8a-4209d430c937 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15687660 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (70 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a1000 - 00009a4170]             BRK
[    0.000000]   #4 [00000f7270 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f7260 - 00000f7270]    MP-table mpf
[    0.000000]   #6 [000009c400 - 000009c971]   BIOS reserved
[    0.000000]   #7 [000009cadd - 00000f7260]   BIOS reserved
[    0.000000]   #8 [000009c971 - 000009cadd]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a5000 - 000191a000]     NEW RAMDISK
[    0.000000]   #13 [000191a000 - 000191b000]         BOOTMEM
[    0.000000]   #14 [000191b000 - 000310b000]         BOOTMEM
[    0.000000]   #15 [000310b000 - 000310b004]         BOOTMEM
[    0.000000]   #16 [000310b040 - 000310b100]         BOOTMEM
[    0.000000]   #17 [000310b100 - 000310b154]         BOOTMEM
[    0.000000]   #18 [000310b180 - 000310e180]         BOOTMEM
[    0.000000]   #19 [000310e180 - 000310e250]         BOOTMEM
[    0.000000]   #20 [000310e280 - 000311a280]         BOOTMEM
[    0.000000]   #21 [000311a280 - 000311a2a5]         BOOTMEM
[    0.000000]   #22 [000311a2c0 - 000311a2e7]         BOOTMEM
[    0.000000]   #23 [000311a300 - 000311a664]         BOOTMEM
[    0.000000]   #24 [000311a680 - 000311a6c0]         BOOTMEM
[    0.000000]   #25 [000311a6c0 - 000311a700]         BOOTMEM
[    0.000000]   #26 [000311a700 - 000311a740]         BOOTMEM
[    0.000000]   #27 [000311a740 - 000311a780]         BOOTMEM
[    0.000000]   #28 [000311a780 - 000311a7c0]         BOOTMEM
[    0.000000]   #29 [000311a7c0 - 000311a800]         BOOTMEM
[    0.000000]   #30 [000311a800 - 000311a840]         BOOTMEM
[    0.000000]   #31 [000311a840 - 000311a880]         BOOTMEM
[    0.000000]   #32 [000311a880 - 000311a8c0]         BOOTMEM
[    0.000000]   #33 [000311a8c0 - 000311a900]         BOOTMEM
[    0.000000]   #34 [000311a900 - 000311a940]         BOOTMEM
[    0.000000]   #35 [000311a940 - 000311a980]         BOOTMEM
[    0.000000]   #36 [000311a980 - 000311a9c0]         BOOTMEM
[    0.000000]   #37 [000311a9c0 - 000311aa00]         BOOTMEM
[    0.000000]   #38 [000311aa00 - 000311aa40]         BOOTMEM
[    0.000000]   #39 [000311aa40 - 000311aa80]         BOOTMEM
[    0.000000]   #40 [000311aa80 - 000311aac0]         BOOTMEM
[    0.000000]   #41 [000311aac0 - 000311ab00]         BOOTMEM
[    0.000000]   #42 [000311ab00 - 000311ab40]         BOOTMEM
[    0.000000]   #43 [000311ab40 - 000311ab80]         BOOTMEM
[    0.000000]   #44 [000311ab80 - 000311abc0]         BOOTMEM
[    0.000000]   #45 [000311abc0 - 000311ac00]         BOOTMEM
[    0.000000]   #46 [000311ac00 - 000311ac40]         BOOTMEM
[    0.000000]   #47 [000311ac40 - 000311ac80]         BOOTMEM
[    0.000000]   #48 [000311ac80 - 000311acc0]         BOOTMEM
[    0.000000]   #49 [000311acc0 - 000311ad00]         BOOTMEM
[    0.000000]   #50 [000311ad00 - 000311ad40]         BOOTMEM
[    0.000000]   #51 [000311ad40 - 000311ad80]         BOOTMEM
[    0.000000]   #52 [000311ad80 - 000311ad90]         BOOTMEM
[    0.000000]   #53 [000311adc0 - 000311add0]         BOOTMEM
[    0.000000]   #54 [000311ae00 - 000311ae6a]         BOOTMEM
[    0.000000]   #55 [000311ae80 - 000311aeea]         BOOTMEM
[    0.000000]   #56 [0003400000 - 000340e000]         BOOTMEM
[    0.000000]   #57 [0003500000 - 000350e000]         BOOTMEM
[    0.000000]   #58 [0003600000 - 000360e000]         BOOTMEM
[    0.000000]   #59 [0003700000 - 000370e000]         BOOTMEM
[    0.000000]   #60 [000311cf00 - 000311cf04]         BOOTMEM
[    0.000000]   #61 [000311cf40 - 000311cf44]         BOOTMEM
[    0.000000]   #62 [000311cf80 - 000311cf90]         BOOTMEM
[    0.000000]   #63 [000311cfc0 - 000311cfd0]         BOOTMEM
[    0.000000]   #64 [000311d000 - 000311d0a0]         BOOTMEM
[    0.000000]   #65 [000311d0c0 - 000311d108]         BOOTMEM
[    0.000000]   #66 [000311d140 - 0003121140]         BOOTMEM
[    0.000000]   #67 [0003121140 - 00031a1140]         BOOTMEM
[    0.000000]   #68 [00031a1140 - 00031e1140]         BOOTMEM
[    0.000000]   #69 [000370e000 - 0004603fec]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:000bf800)
[    0.000000] Memory: 3068312k/3137536k available (4928k kernel code, 65624k reserved, 2336k data, 684k init, 2225092k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2394.042 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.08 BogoMIPS (lpj=9576168)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000021] Security Framework initialized
[    0.000033] AppArmor: AppArmor initialized
[    0.000034] Yama: becoming mindful.
[    0.000073] Mount-cache hash table entries: 512
[    0.000159] Initializing cgroup subsys ns
[    0.000162] Initializing cgroup subsys cpuacct
[    0.000166] Initializing cgroup subsys memory
[    0.000171] Initializing cgroup subsys devices
[    0.000173] Initializing cgroup subsys freezer
[    0.000175] Initializing cgroup subsys net_cls
[    0.000194] CPU: Physical Processor ID: 0
[    0.000195] CPU: Processor Core ID: 0
[    0.000199] mce: CPU supports 9 MCE banks
[    0.000207] CPU0: Thermal monitoring handled by SMI
[    0.000214] using mwait in idle threads.
[    0.000218] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.000224] ... version:                3
[    0.000226] ... bit width:              48
[    0.000227] ... generic registers:      4
[    0.000228] ... value mask:             0000ffffffffffff
[    0.000229] ... max period:             000000007fffffff
[    0.000231] ... fixed-purpose events:   3
[    0.000232] ... event mask:             000000070000000f
[    0.002429] ACPI: Core revision 20100428
[    0.022692] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.022695] ftrace: allocating 21758 entries in 43 pages
[    0.028581] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028985] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068601] CPU0: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz stepping 02
[    0.176097] Booting Node   0, Processors  #1
[    0.186300] Initializing CPU#1
[    0.263861] CPU1: Thermal monitoring handled by SMI
[    0.284002]  #2
[    0.294122] Initializing CPU#2
[    0.371673] CPU2: Thermal monitoring handled by SMI
[    0.391784]  #3 Ok.
[    0.401903] Initializing CPU#3
[    0.479483] CPU3: Thermal monitoring handled by SMI
[    0.499529] Brought up 4 CPUs
[    0.499531] Total of 4 processors activated (19151.75 BogoMIPS).
[    0.501218] devtmpfs: initialized
[    0.502154] regulator: core version 0.5
[    0.502180] Time: 16:09:02  Date: 11/08/10
[    0.502209] NET: Registered protocol family 16
[    0.502292] Trying to unpack rootfs image as initramfs...
[    0.502295] EISA bus registered
[    0.502302] ACPI: bus type pci registered
[    0.502359] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.502362] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.502363] PCI: Using MMCONFIG for extended config space
[    0.502365] PCI: Using configuration type 1 for base access
[    0.503022] bio: create slab <bio-0> at 0
[    0.504644] ACPI: EC: Look up EC in DSDT
[    0.512276] ACPI: BIOS _OSI(Linux) query ignored
[    0.514211] ACPI: SSDT bf71a918 003E2 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.514611] ACPI: Dynamic OEM Table Load:
[    0.514613] ACPI: SSDT (null) 003E2 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.514913] ACPI: SSDT bf718698 005EC (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.515296] ACPI: Dynamic OEM Table Load:
[    0.515298] ACPI: SSDT (null) 005EC (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.515812] ACPI: SSDT bf719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.516260] ACPI: Dynamic OEM Table Load:
[    0.516262] ACPI: SSDT (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.516427] ACPI: SSDT bf717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.516840] ACPI: Dynamic OEM Table Load:
[    0.516842] ACPI: SSDT (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.517932] ACPI: Interpreter enabled
[    0.517935] ACPI: (supports S0 S3 S4 S5)
[    0.517956] ACPI: Using IOAPIC for interrupt routing
[    0.518482] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.524250] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.524308] ACPI: Power Resource [FN00] (off)
[    0.524348] ACPI: Power Resource [FN01] (off)
[    0.524517] ACPI: No dock devices found.
[    0.524520] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.525385] \_SB_.PCI0:_OSC invalid UUID
[    0.525387] _OSC request data:1 8 1f 
[    0.525391] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.526749] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.526751] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.526753] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.526755] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.526757] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.526759] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.526761] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.526764] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.526766] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.526825] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.526827] pci 0000:00:01.0: PME# disabled
[    0.526896] pci 0000:00:16.0: reg 10: [mem 0xf0305800-0xf030580f 64bit]
[    0.526953] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.526957] pci 0000:00:16.0: PME# disabled
[    0.527015] pci 0000:00:1a.0: reg 10: [mem 0xf0306000-0xf03063ff]
[    0.527079] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.527084] pci 0000:00:1a.0: PME# disabled
[    0.527128] pci 0000:00:1b.0: reg 10: [mem 0xf0300000-0xf0303fff 64bit]
[    0.527184] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.527188] pci 0000:00:1b.0: PME# disabled
[    0.527278] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.527283] pci 0000:00:1c.0: PME# disabled
[    0.527374] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.527378] pci 0000:00:1c.1: PME# disabled
[    0.527480] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.527485] pci 0000:00:1c.5: PME# disabled
[    0.527538] pci 0000:00:1d.0: reg 10: [mem 0xf0306400-0xf03067ff]
[    0.527602] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.527607] pci 0000:00:1d.0: PME# disabled
[    0.527801] pci 0000:00:1f.2: reg 10: [io  0x1830-0x1837]
[    0.527808] pci 0000:00:1f.2: reg 14: [io  0x1824-0x1827]
[    0.527815] pci 0000:00:1f.2: reg 18: [io  0x1828-0x182f]
[    0.527822] pci 0000:00:1f.2: reg 1c: [io  0x1820-0x1823]
[    0.527829] pci 0000:00:1f.2: reg 20: [io  0x1800-0x181f]
[    0.527836] pci 0000:00:1f.2: reg 24: [mem 0xf0305000-0xf03057ff]
[    0.527880] pci 0000:00:1f.2: PME# supported from D3hot
[    0.527884] pci 0000:00:1f.2: PME# disabled
[    0.527921] pci 0000:00:1f.3: reg 10: [mem 0xf0306800-0xf03068ff 64bit]
[    0.527938] pci 0000:00:1f.3: reg 20: [io  0x1840-0x185f]
[    0.527997] pci 0000:00:1f.6: reg 10: [mem 0xf0304000-0xf0304fff 64bit]
[    0.528101] pci 0000:02:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.528110] pci 0000:02:00.0: reg 18: [mem 0xcfee0000-0xcfefffff 64bit]
[    0.528116] pci 0000:02:00.0: reg 20: [io  0x2000-0x20ff]
[    0.528126] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.528149] pci 0000:02:00.0: supports D1 D2
[    0.528183] pci 0000:02:00.1: reg 10: [mem 0xcfedc000-0xcfedffff 64bit]
[    0.528224] pci 0000:02:00.1: supports D1 D2
[    0.528261] pci 0000:00:01.0: PCI bridge to [bus 02-02]
[    0.528263] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.528266] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.528269] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.528324] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.528329] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.528334] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.528341] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.529481] pci 0000:04:00.0: reg 10: [mem 0xf0200000-0xf0203fff 64bit]
[    0.531567] pci 0000:04:00.0: supports D1 D2
[    0.531569] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.531661] pci 0000:04:00.0: PME# disabled
[    0.532888] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.532893] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.532898] pci 0000:00:1c.1:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.532905] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.532989] pci 0000:05:00.0: reg 10: [io  0x3000-0x30ff]
[    0.533007] pci 0000:05:00.0: reg 18: [mem 0xf0410000-0xf0410fff 64bit pref]
[    0.533021] pci 0000:05:00.0: reg 20: [mem 0xf0400000-0xf040ffff 64bit pref]
[    0.533029] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.533069] pci 0000:05:00.0: supports D1 D2
[    0.533070] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.533075] pci 0000:05:00.0: PME# disabled
[    0.539385] pci 0000:00:1c.5: PCI bridge to [bus 05-05]
[    0.539391] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
[    0.539396] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.539404] pci 0000:00:1c.5:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.539479] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.539484] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.539489] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.539496] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.539498] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.539500] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.539502] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.539504] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.539506] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.539508] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.539510] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.539512] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.539514] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.539541] pci_bus 0000:00: on NUMA node 0
[    0.539551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.539817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.539887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.540075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.540197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.540318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.540482] \_SB_.PCI0:_OSC invalid UUID
[    0.540483] _OSC request data:1 1f 1f 
[    0.545525] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.545721] pci_bus 0000:ff: on NUMA node 0
[    0.545958] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.546067] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.546171] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.546276] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.546381] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.546487] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.546592] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.546696] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.546745] HEST: Table is not found!
[    0.546805] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.546810] vgaarb: loaded
[    0.546926] SCSI subsystem initialized
[    0.547026] libata version 3.00 loaded.
[    0.547062] usbcore: registered new interface driver usbfs
[    0.547070] usbcore: registered new interface driver hub
[    0.547094] usbcore: registered new device driver usb
[    0.547301] ACPI: WMI: Mapper loaded
[    0.547303] PCI: Using ACPI for IRQ routing
[    0.547305] PCI: pci_cache_line_size set to 64 bytes
[    0.547511] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.547514] reserve RAM buffer: 000000000009c400 - 000000000009ffff 
[    0.547515] reserve RAM buffer: 00000000bf27c000 - 00000000bfffffff 
[    0.547519] reserve RAM buffer: 00000000bf3ea000 - 00000000bfffffff 
[    0.547523] reserve RAM buffer: 00000000bf46f000 - 00000000bfffffff 
[    0.547526] reserve RAM buffer: 00000000bf717000 - 00000000bfffffff 
[    0.547528] reserve RAM buffer: 00000000bf77e000 - 00000000bfffffff 
[    0.547530] reserve RAM buffer: 00000000bf7e2000 - 00000000bfffffff 
[    0.547532] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
[    0.547607] NetLabel: Initializing
[    0.547609] NetLabel:  domain hash size = 128
[    0.547610] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.547620] NetLabel:  unlabeled traffic allowed by default
[    0.547657] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.547663] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.549679] Switching to clocksource tsc
[    0.557119] AppArmor: AppArmor Filesystem Enabled
[    0.557133] pnp: PnP ACPI init
[    0.557150] ACPI: bus type pnp registered
[    0.560037] pnp: PnP ACPI: found 11 devices
[    0.560038] ACPI: ACPI bus type pnp unregistered
[    0.560041] PnPBIOS: Disabled by ACPI PNP
[    0.560055] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.560057] system 00:05: [io  0x0500-0x050f] has been reserved
[    0.560059] system 00:05: [io  0x0600-0x0603] has been reserved
[    0.560061] system 00:05: [io  0xffff] has been reserved
[    0.560062] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.560064] system 00:05: [io  0x1180-0x11ff] has been reserved
[    0.560066] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.560068] system 00:05: [io  0xfe00] has been reserved
[    0.560073] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.560075] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.560077] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.560079] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.560081] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.560083] system 00:09: [mem 0xfeaff000-0xfeafffff] has been reserved
[    0.560085] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.560087] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.560090] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.560092] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.560094] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.595547] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.595552] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.595554] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.595557] pci 0000:00:1c.5: BAR 14: assigned [mem 0xc0600000-0xc09fffff]
[    0.595560] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.595562] pci 0000:00:1c.1: BAR 13: assigned [io  0x5000-0x5fff]
[    0.595565] pci 0000:02:00.0: BAR 6: assigned [mem 0xcfe00000-0xcfe1ffff pref]
[    0.595567] pci 0000:00:01.0: PCI bridge to [bus 02-02]
[    0.595569] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.595572] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.595575] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.595578] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.595581] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.595587] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.595592] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.595600] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.595603] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.595609] pci 0000:00:1c.1:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.595613] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.595621] pci 0000:05:00.0: BAR 6: assigned [mem 0xf0420000-0xf043ffff pref]
[    0.595623] pci 0000:00:1c.5: PCI bridge to [bus 05-05]
[    0.595626] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
[    0.595632] pci 0000:00:1c.5:   bridge window [mem 0xc0600000-0xc09fffff]
[    0.595637] pci 0000:00:1c.5:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.595644] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.595646] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.595651] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.595656] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.595672]   alloc irq_desc for 16 on node -1
[    0.595674]   alloc kstat_irqs on node -1
[    0.595680] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.595684] pci 0000:00:01.0: setting latency timer to 64
[    0.595693] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.595698] pci 0000:00:1c.0: setting latency timer to 64
[    0.595709]   alloc irq_desc for 17 on node -1
[    0.595711]   alloc kstat_irqs on node -1
[    0.595714] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.595718] pci 0000:00:1c.1: setting latency timer to 64
[    0.595728] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.595733] pci 0000:00:1c.5: setting latency timer to 64
[    0.595741] pci 0000:00:1e.0: setting latency timer to 64
[    0.595745] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.595747] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.595749] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.595750] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.595752] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.595754] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.595756] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.595757] pci_bus 0000:00: resource 11 [mem 0xc0000000-0xdfffffff]
[    0.595759] pci_bus 0000:00: resource 12 [mem 0xf0000000-0xfebfffff]
[    0.595761] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.595763] pci_bus 0000:02: resource 1 [mem 0xcfe00000-0xcfefffff]
[    0.595765] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.595767] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.595768] pci_bus 0000:03: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.595770] pci_bus 0000:03: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.595772] pci_bus 0000:04: resource 0 [io  0x5000-0x5fff]
[    0.595774] pci_bus 0000:04: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.595776] pci_bus 0000:04: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.595778] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.595779] pci_bus 0000:05: resource 1 [mem 0xc0600000-0xc09fffff]
[    0.595781] pci_bus 0000:05: resource 2 [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.595783] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.595785] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.595786] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.595788] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.595790] pci_bus 0000:06: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.595791] pci_bus 0000:06: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.595793] pci_bus 0000:06: resource 10 [mem 0x000dc000-0x000dffff]
[    0.595795] pci_bus 0000:06: resource 11 [mem 0xc0000000-0xdfffffff]
[    0.595797] pci_bus 0000:06: resource 12 [mem 0xf0000000-0xfebfffff]
[    0.595828] NET: Registered protocol family 2
[    0.595876] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.596024] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.596575] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.596850] TCP: Hash tables configured (established 131072 bind 65536)
[    0.596852] TCP reno registered
[    0.596854] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.596863] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.596923] NET: Registered protocol family 1
[    0.597004] pci 0000:02:00.0: Boot video device
[    0.597106] PCI: CLS 64 bytes, default 64
[    0.597125] Simple Boot Flag at 0x36 set to 0x1
[    0.597342] cpufreq-nforce2: No nForce2 chipset.
[    0.597362] Scanning for low memory corruption every 60 seconds
[    0.597461] audit: initializing netlink socket (disabled)
[    0.597469] type=2000 audit(1289232541.436:1): initialized
[    0.606155] highmem bounce pool size: 64 pages
[    0.606160] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.607194] VFS: Disk quotas dquot_6.5.2
[    0.607238] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.607674] fuse init (API version 7.14)
[    0.607735] msgmni has been set to 1646
[    0.608000] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.608002] io scheduler noop registered
[    0.608004] io scheduler deadline registered
[    0.608013] io scheduler cfq registered (default)
[    0.608093] pcieport 0000:00:01.0: setting latency timer to 64
[    0.608113]   alloc irq_desc for 40 on node -1
[    0.608114]   alloc kstat_irqs on node -1
[    0.608121] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.608166] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.608207]   alloc irq_desc for 41 on node -1
[    0.608208]   alloc kstat_irqs on node -1
[    0.608216] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.608291] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.608333]   alloc irq_desc for 42 on node -1
[    0.608335]   alloc kstat_irqs on node -1
[    0.608342] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.608421] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.608462]   alloc irq_desc for 43 on node -1
[    0.608463]   alloc kstat_irqs on node -1
[    0.608470] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.608555] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.608678] \_SB_.PCI0:_OSC invalid UUID
[    0.608679] _OSC request data:1 0 1f 
[    0.608771] \_SB_.PCI0:_OSC invalid UUID
[    0.608772] _OSC request data:1 0 1f 
[    0.608860] \_SB_.PCI0:_OSC invalid UUID
[    0.608862] _OSC request data:1 0 1f 
[    0.608960] \_SB_.PCI0:_OSC invalid UUID
[    0.608962] _OSC request data:1 0 1f 
[    0.609049] \_SB_.PCI0:_OSC invalid UUID
[    0.609050] _OSC request data:1 0 1f 
[    0.609137] \_SB_.PCI0:_OSC invalid UUID
[    0.609139] _OSC request data:1 0 1f 
[    0.609155] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.609215] intel_idle: MWAIT substates: 0x1120
[    0.609216] intel_idle: v0.4 model 0x25
[    0.609217] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.609316] ACPI: AC Adapter [ADP1] (on-line)
[    0.609365] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.609370] ACPI: Power Button [PWRB]
[    0.609398] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.609401] ACPI: Sleep Button [SLPB]
[    0.609429] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.610026] ACPI: Lid Switch [LID0]
[    0.610059] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.610061] ACPI: Power Button [PWRF]
[    0.610168] ACPI: Fan [FAN0] (off)
[    0.610250] ACPI: Fan [FAN1] (off)
[    0.610548] ACPI: acpi_idle yielding to intel_idle
[    0.614371] thermal LNXTHERM:01: registered as thermal_zone0
[    0.614377] ACPI: Thermal Zone [TZ00] (27 C)
[    0.614984] thermal LNXTHERM:02: registered as thermal_zone1
[    0.614989] ACPI: Thermal Zone [TZ01] (0 C)
[    0.615058] ERST: Table is not found!
[    0.615099] isapnp: Scanning for PnP cards...
[    0.615885] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.617278] brd: module loaded
[    0.617786] loop: module loaded
[    0.618214] Fixed MDIO Bus: probed
[    0.618244] PPP generic driver version 2.4.2
[    0.618304] tun: Universal TUN/TAP device driver, 1.6
[    0.618306] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.618373] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.618395] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.618409] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.618413] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.618442] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.618483] ehci_hcd 0000:00:1a.0: debug port 2
[    0.622454] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.622475] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0306000
[    0.635291] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.635410] hub 1-0:1.0: USB hub found
[    0.635415] hub 1-0:1.0: 3 ports detected
[    0.635481]   alloc irq_desc for 23 on node -1
[    0.635484]   alloc kstat_irqs on node -1
[    0.635490] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.635504] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.635508] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.635537] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.635565] ehci_hcd 0000:00:1d.0: debug port 2
[    0.639564] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.639580] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0306400
[    0.649214] ACPI: Battery Slot [BAT0] (battery present)
[    0.655258] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.655374] hub 2-0:1.0: USB hub found
[    0.655379] hub 2-0:1.0: 3 ports detected
[    0.655448] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.655462] uhci_hcd: USB Universal Host Controller Interface driver
[    0.655549] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.661086] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.661093] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.661191] mice: PS/2 mouse device common for all mice
[    0.661337] rtc_cmos 00:06: RTC can wake from S4
[    0.661378] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.661408] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.661501] device-mapper: uevent: version 1.0.3
[    0.661605] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.661699] device-mapper: multipath: version 1.1.1 loaded
[    0.661702] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.661802] EISA: Probing bus 0 at eisa.0
[    0.661804] EISA: Cannot allocate resource for mainboard
[    0.661806] Cannot allocate resource for EISA slot 1
[    0.661808] Cannot allocate resource for EISA slot 2
[    0.661810] Cannot allocate resource for EISA slot 3
[    0.661812] Cannot allocate resource for EISA slot 4
[    0.661813] Cannot allocate resource for EISA slot 5
[    0.661815] Cannot allocate resource for EISA slot 6
[    0.661817] Cannot allocate resource for EISA slot 7
[    0.661819] Cannot allocate resource for EISA slot 8
[    0.661820] EISA: Detected 0 cards.
[    0.662048] cpuidle: using governor ladder
[    0.662219] cpuidle: using governor menu
[    0.662491] TCP cubic registered
[    0.662615] NET: Registered protocol family 10
[    0.662934] lo: Disabled Privacy Extensions
[    0.663132] NET: Registered protocol family 17
[    0.664580] Using IPI No-Shortcut mode
[    0.664649] PM: Resume from disk failed.
[    0.664659] registered taskstats version 1
[    0.665532]   Magic number: 2:943:185
[    0.665572] thermal LNXTHERM:01: hash matches
[    0.665614] rtc_cmos 00:06: setting system clock to 2010-11-08 16:09:02 UTC (1289232542)
[    0.665618] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.665620] EDD information not available.
[    0.666182] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.872397] Freeing initrd memory: 15828k freed
[    0.974699] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.982909] isapnp: No Plug & Play device found
[    0.982923] Freeing unused kernel memory: 684k freed
[    0.983177] Write protecting the kernel text: 4932k
[    0.983209] Write protecting the kernel read-only data: 1976k
[    0.997619] udev[102]: starting version 163
[    1.024986] Linux agpgart interface v0.103
[    1.030960] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.030987] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.031029] r8169 0000:05:00.0: setting latency timer to 64
[    1.031078]   alloc irq_desc for 44 on node -1
[    1.031080]   alloc kstat_irqs on node -1
[    1.031095] r8169 0000:05:00.0: irq 44 for MSI/MSI-X
[    1.031568] r8169 0000:05:00.0: eth0: RTL8102e at 0xf8068000, b8:ac:6f:57:49:9d, XID 04e00000 IRQ 44
[    1.044109] ahci 0000:00:1f.2: version 3.0
[    1.044131]   alloc irq_desc for 19 on node -1
[    1.044134]   alloc kstat_irqs on node -1
[    1.044143] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.044192]   alloc irq_desc for 45 on node -1
[    1.044194]   alloc kstat_irqs on node -1
[    1.044205] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.044242] ahci: SSS flag set, parallel bus scan disabled
[    1.044280] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.044284] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems apst 
[    1.044290] ahci 0000:00:1f.2: setting latency timer to 64
[    1.055914] scsi0 : ahci
[    1.057343] scsi1 : ahci
[    1.059241] scsi2 : ahci
[    1.060330] scsi3 : ahci
[    1.060392] ata1: SATA max UDMA/133 abar m2048@0xf0305000 port 0xf0305100 irq 45
[    1.060397] ata2: SATA max UDMA/133 abar m2048@0xf0305000 port 0xf0305180 irq 45
[    1.060400] ata3: DUMMY
[    1.060401] ata4: DUMMY
[    1.061880] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    1.071762] acpi device:02: registered as cooling_device6
[    1.071885] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input5
[    1.071937] ACPI: Video Device [M86] (multi-head: yes  rom: no  post: no)
[    1.110920] hub 1-1:1.0: USB hub found
[    1.111005] hub 1-1:1.0: 6 ports detected
[    1.220856] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.353441] hub 2-1:1.0: USB hub found
[    1.353595] hub 2-1:1.0: 8 ports detected
[    1.382159] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.384096] ata1.00: ATA-8: WDC WD5000BEVT-75A0RT0, 01.01A01, max UDMA/133
[    1.384102] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.386259] ata1.00: configured for UDMA/133
[    1.405263] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-7 01.0 PQ: 0 ANSI: 5
[    1.405451] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.405454] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.405508] sd 0:0:0:0: [sda] Write Protect is off
[    1.405511] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.405527] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.405624]  sda:
[    1.429294] usb 1-1.1: new full speed USB device using ehci_hcd and address 3
[    1.443157]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    1.502779] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.528117] hub 1-1.1:1.0: USB hub found
[    1.528315] hub 1-1.1:1.0: 3 ports detected
[    1.600512] usb 1-1.4: new high speed USB device using ehci_hcd and address 4
[    1.804635] usb 2-1.2: new low speed USB device using ehci_hcd and address 3
[    1.971884] usb 2-1.3: new high speed USB device using ehci_hcd and address 4
[    2.131383] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.133937] ata2.00: ATAPI: HL-DT-STDVD+/-RW GT30N, A101, max UDMA/100
[    2.136940] ata2.00: configured for UDMA/100
[    2.147580] usb 1-1.1.1: new full speed USB device using ehci_hcd and address 5
[    2.153992] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GT30N    A101 PQ: 0 ANSI: 5
[    2.162059] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.162064] Uniform CD-ROM driver Revision: 3.20
[    2.162216] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.162264] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.167584] usbcore: registered new interface driver hiddev
[    2.171122] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input6
[    2.171221] generic-usb 0003:046D:C047.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1.2/input0
[    2.171239] usbcore: registered new interface driver usbhid
[    2.171241] usbhid: USB HID core driver
[    2.246431] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.1/1-1.1.1:1.0/input/input7
[    2.246496] generic-usb 0003:413C:8161.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1a.0-1.1.1/input0
[    2.319268] usb 1-1.1.2: new full speed USB device using ehci_hcd and address 6
[    2.421633] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.2/1-1.1.2:1.0/input/input8
[    2.421702] generic-usb 0003:413C:8162.0003: input,hidraw2: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1a.0-1.1.2/input0
[    3.183021] Btrfs loaded
[    3.186957] xor: automatically using best checksumming function: pIII_sse
[    3.202995]    pIII_sse  : 10961.000 MB/sec
[    3.202997] xor: using function: pIII_sse (10961.000 MB/sec)
[    3.204855] device-mapper: dm-raid45: initialized v0.2594b
[    3.697801] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   15.337004] udev[450]: starting version 163
[   15.350346] lp: driver loaded but no devices found
[   15.387591] lib80211: common routines for IEEE802.11 drivers
[   15.387594] lib80211_crypt: registered algorithm 'NULL'
[   15.406179] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   15.406204]   alloc irq_desc for 18 on node -1
[   15.406207]   alloc kstat_irqs on node -1
[   15.406215] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   15.406360] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   15.427834] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.427838] Disabling lock debugging due to kernel taint
[   15.456128] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.463077] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.463173] wl 0000:04:00.0: setting latency timer to 64
[   15.494424] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[   15.509770] Adding 8476668k swap on /dev/sda7.  Priority:-1 extents:1 across:8476668k 
[   15.533003] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   15.583736] lib80211_crypt: registered algorithm 'TKIP'
[   15.584053] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   15.588256] Linux video capture interface: v2.00
[   15.606360] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:641d)
[   15.625219] [fglrx] Maximum main memory to use for locked dma buffers: 2867 MBytes.
[   15.625436] [fglrx]   vendor: 1002 device: 68e0 count: 1
[   15.625851] [fglrx] ioport: bar 4, base 0x2000, size: 0x100
[   15.625873] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.625879] pci 0000:02:00.0: setting latency timer to 64
[   15.626105] [fglrx] Kernel PAT support is enabled
[   15.626126] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   15.648592] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input10
[   15.648659] usbcore: registered new interface driver uvcvideo
[   15.648662] USB Video Class driver (v0.1.0)
[   15.662262]   alloc irq_desc for 22 on node -1
[   15.662265]   alloc kstat_irqs on node -1
[   15.662273] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.662334]   alloc irq_desc for 46 on node -1
[   15.662336]   alloc kstat_irqs on node -1
[   15.662348] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   15.662388] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.712119] hda_codec: ALC269: BIOS auto-probing.
[   15.716924] HDA Intel 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.716976]   alloc irq_desc for 47 on node -1
[   15.716978]   alloc kstat_irqs on node -1
[   15.716988] HDA Intel 0000:02:00.1: irq 47 for MSI/MSI-X
[   15.717013] HDA Intel 0000:02:00.1: setting latency timer to 64
[   15.873758] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input11
[   15.892252] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12
[   15.908076] usb 1-1.1.3: new full speed USB device using ehci_hcd and address 7
[   16.020839] Bluetooth: Core ver 2.15
[   16.020886] NET: Registered protocol family 31
[   16.020888] Bluetooth: HCI device and connection manager initialized
[   16.020891] Bluetooth: HCI socket layer initialized
[   16.025244] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   16.025716] usbcore: registered new interface driver btusb
[   17.428577] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   17.655733] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   18.540193] ppdev: user-space parallel port driver
[   18.776577] r8169 0000:05:00.0: eth0: link down
[   18.776714] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.003295] [fglrx] ATIF platform detected with notification ID: 0x81
[   19.498518]   alloc irq_desc for 48 on node -1
[   19.498521]   alloc kstat_irqs on node -1
[   19.498533] fglrx_pci 0000:02:00.0: irq 48 for MSI/MSI-X
[   19.499151] [fglrx] Firegl kernel thread PID: 1205
[   19.499382] [fglrx] IRQ 48 Enabled
[   19.616111] [fglrx] Gart USWC size:944 M.
[   19.616115] [fglrx] Gart cacheable size:372 M.
[   19.616120] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   19.616122] [fglrx] Reserved FB block: Unshared offset:fa0b000, size:2f5000 
[   19.616124] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   19.798502] Bluetooth: L2CAP ver 2.14
[   19.798506] Bluetooth: L2CAP socket layer initialized
[   19.803358] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.803361] Bluetooth: BNEP filters: protocol multicast
[   19.807440] Bluetooth: SCO (Voice Link) ver 0.6
[   19.807444] Bluetooth: SCO socket layer initialized
[   19.872122] Bluetooth: RFCOMM TTY layer initialized
[   19.872129] Bluetooth: RFCOMM socket layer initialized
[   19.872131] Bluetooth: RFCOMM ver 1.11
[   20.889361] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=600
[   20.927138] EXT4-fs (sda6): re-mounted. Opts: commit=600
[   22.947724] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=600
[   22.953831] EXT4-fs (sda6): re-mounted. Opts: commit=600
[   23.652310] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=600
[   23.655472] EXT4-fs (sda6): re-mounted. Opts: commit=600
[   24.111724] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   29.732271] eth1: no IPv6 routers present
[ 1146.216354] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe
[ 1146.216361] ata2.00: irq_stat 0x40000001
[ 1146.216366] ata2: SError: { PHYRdyChg }
[ 1146.216370] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 1146.216388] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1146.216390]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 1146.216394] ata2.00: status: { DRDY ERR }
[ 1146.216403] ata2: hard resetting link
[ 1146.938744] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1146.944318] ata2.00: configured for UDMA/100
[ 1146.945086] ata2: EH complete

```

lsusb:
```
Bus 002 Device 006: ID 6000:0002
```

---

### Post by xc3RnbFO8P on 2010-11-08
Read this:
[http://www.linuxtv.org/wiki/index.php/Trident_TM6000]("http://www.linuxtv.org/wiki/index.php/Trident_TM6000")

---

### Post by kounabi on 2010-11-08
I 've already read this but make did not manage to finish without errors....is it supposed to work or it's experimental?

---

### Post by xc3RnbFO8P on 2010-11-08
> **kounabi said:**
> I 've already read this but make did not manage to finish without errors....is it supposed to work or it's experimental?

What errors did you get?
....I dont know, its experimental.

---

### Post by kounabi on 2010-11-08
...hehe!

this is the output

```

/home/kounabi/v4l-dvb/v4l/firedtv-fw.c: In function 'model_name':
/home/kounabi/v4l-dvb/v4l/firedtv-fw.c:254: warning: assignment discards qualifiers from pointer target type
/home/kounabi/v4l-dvb/v4l/firedtv-fw.c: In function 'node_probe':
/home/kounabi/v4l-dvb/v4l/firedtv-fw.c:280: warning: passing argument 1 of 'model_name' discards qualifiers from pointer target type
/home/kounabi/v4l-dvb/v4l/firedtv-fw.c:244: note: expected 'u32 *' but argument is of type 'const u32 *'
  CC [M]  /home/kounabi/v4l-dvb/v4l/firedtv-1394.o
/home/kounabi/v4l-dvb/v4l/firedtv-1394.c:22: fatal error: dma.h: No such file or directory
compilation terminated.
make[3]: *** [/home/kounabi/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/kounabi/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/kounabi/v4l-dvb/v4l'
make: *** [all] Error 2

```

so this is a buggy code...I can't believe that it can't get through make....

---

### Post by kounabi on 2010-11-08
ok...maybe I'm too dramatic....

somewhere i read this 
> 
look at: [http://ubuntuforums.org/showthread.php?t=1305228](http://ubuntuforums.org/showthread.php?t=1305228)

.config file does not exist if you download v4l with hg.
However, it will be generated if you type "make menuconfig" and Exit saving changes.

These steps worked for me:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make menuconfig  <-- dont change anything, just "Exit" and save changes
gedit v4l/.config <-- change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n
make
sudo make installhowever it complains about not having ncurses-devel...which i can't find....any suggestions?

thnx again!!!

update: I found the .config and changed the parameter....let's see

---

### Post by kounabi on 2010-11-08
I've managed to compile the code and install it but when i try to modprobe tm6000 it says

```
FATAL: Error inserting tm6000 (/lib/modules/2.6.35-22-generic/kernel/drivers/staging/tm6000/tm6000.ko): Invalid argument

```

---

### Post by xc3RnbFO8P on 2010-11-08
Check this:[http://www.google.dk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=FATAL:+Error+inserting+tm6000+(/lib/modules/2.6.35-22-generic/kernel/drivers/staging/tm6000/tm6000.ko):+Invalid+argument]("http://www.google.dk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=FATAL:+Error+inserting+tm6000+(/lib/modules/2.6.35-22-generic/kernel/drivers/staging/tm6000/tm6000.ko):+Invalid+argument")

---

### Post by kounabi on 2010-11-08
ok I managed to run the module but i still get the same output from lsusb...

how can i check if the module is running?

---

### Post by xc3RnbFO8P on 2010-11-08
Try:
> lsmod | grep tm6000
> lsmod | grep dvb

---

### Post by kounabi on 2010-11-08
```

 $ lsmod | grep tm6000
tm6000                 38899  0 
v4l2_common            17329  2 tuner,tm6000
videobuf_vmalloc        4590  1 tm6000
videobuf_core          16955  2 tm6000,videobuf_vmalloc
videodev               43354  4 tuner,tm6000,v4l2_common,uvcvideo

```

```

lsmod | grep dvb
tm6000_dvb              5986  0 
dvb_core               86776  1 tm6000_dvb
tm6000                 38899  1 tm6000_dvb

```

they are running but nothing happens...thnx by the way!!!

---

### Post by xc3RnbFO8P on 2010-11-09
Nothing in dmesg?

---

### Post by kounabi on 2010-11-09
yeap!! now i can see something

```

[11804.115936] usb 2-1.3: new high speed USB device using ehci_hcd and address 9
[11804.216152] tm6000: alt 0, interface 0, class 255
[11804.216156] tm6000: alt 0, interface 0, class 255
[11804.216158] tm6000: Bulk IN endpoint: 0x82 (max size=512 bytes)
[11804.216160] tm6000: alt 0, interface 0, class 255
[11804.216161] tm6000: alt 1, interface 0, class 255
[11804.216163] tm6000: ISOC IN endpoint: 0x81 (max size=3072 bytes)
[11804.216165] tm6000: alt 1, interface 0, class 255
[11804.216167] tm6000: alt 1, interface 0, class 255
[11804.216169] tm6000: alt 2, interface 0, class 255
[11804.216170] tm6000: alt 2, interface 0, class 255
[11804.216172] tm6000: alt 2, interface 0, class 255
[11804.216174] tm6000: alt 3, interface 0, class 255
[11804.216176] tm6000: alt 3, interface 0, class 255
[11804.216178] tm6000: alt 3, interface 0, class 255
[11804.216180] tm6000: New video device @ 480 Mbps (6000:0002, ifnum 0)
[11804.216183] tm6000: Found Generic tm6010 board
[11805.138141] Board version = 0x67980bf4
[11805.529503] board=0x67980bf4
[11805.652400] tm6000 #5: i2c eeprom 00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11805.844065] tm6000 #5: i2c eeprom 10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11806.052643] tm6000 #5: i2c eeprom 20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11806.255354] tm6000 #5: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11806.463971] tm6000 #5: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11806.675624] tm6000 #5: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11806.895255] tm6000 #5: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11807.114911] tm6000 #5: i2c eeprom 70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11807.326560] tm6000 #5: i2c eeprom 80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11807.550363] tm6000 #5: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11807.753071] tm6000 #5: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11807.953535] tm6000 #5: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11808.164314] tm6000 #5: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11808.372850] tm6000 #5: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11808.575635] tm6000 #5: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11808.788166] tm6000 #5: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[11808.966934]   ................
[11808.968114] tuner 0-0061: chip found @ 0xc2 (tm6000 #5)
[11808.968235] xc2028 0-0061: creating new instance
[11808.968238] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[11808.968240] Setting firmware parameters for xc2028
[11808.969320] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.
[11808.970494] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.
[11808.970561] Trident TVMaster TM5600/TM6000/TM6010 USB2 board (Load status: 0)
[11808.971171] tm6000: open called (dev=video1)


```

---

### Post by kounabi on 2010-11-09
i tried to open tvtime but it crashes

```

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/kounabi/.tvtime/tvtime.xml
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument

    Your capture card driver: uvcvideo [Laptop_Integrated_Webcam_1.3M/usb-0000:00:1a.0-1.4/25
    does not support full size studio-quality images required by tvtime.
    This is true for many low-quality webcams.  Please select a
    different video device for tvtime to use with the command line
    option --device.

mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
Segmentation fault

```

i don't know any other program...

---

### Post by kounabi on 2010-11-09
ok i entered tvtime --device=/dev/video1 and it started but i get no signal...

i found this [http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#How_to_Obtain_the_Firmware](http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#How_to_Obtain_the_Firmware)

but i can't exactly understand what is the .sys file....

---

### Post by halj32 on 2010-11-09
have you installed "linux-firmware-nonfree"???? this is needed for the card to work

---

### Post by kounabi on 2010-11-09
ok now i did...

```

[  913.995245] tuner 0-0061: chip found @ 0xc2 (tm6000 #3)
[  913.995475] xc2028 0-0061: creating new instance
[  913.995481] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[  913.995486] Setting firmware parameters for xc2028
[  913.997812] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[  914.292759] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[  931.062637] xc2028 0-0061: i2c output error: rc = -71 (should be 4)
[  931.078640] xc2028 0-0061: -71 returned from send
[  931.078645] xc2028 0-0061: Error -22 while loading base firmware

```

---

### Post by kounabi on 2010-11-09
just to know o only want the analogue tv to work for now...(no digital tv in my area...)

---

