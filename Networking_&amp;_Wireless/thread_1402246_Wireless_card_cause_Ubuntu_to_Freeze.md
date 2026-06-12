---
title: "Wireless card cause Ubuntu to Freeze?"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by AquaFusion on 2010-02-08
Hello hello, I have this annoying problem I hope anyone would help me at this point. Let say that I regularly play online game though Ubuntu because it handle connection better with 2wire router/gateway than my window xp. Here the thing, everytime when I play online with WINE (with opengl api), there a possiblity that my Ubuntu will freeze while I am playing the game. I just assumed it was my graphic card that is overheated but it impossible since I kept my case well-vent. And I thought it was WINE that have issue but I used it in the past and never encounter this kind of problem. So after it froze, I have to hard reboot through power button. And then I got on the desktop and went to Log Viewer to see what is going on. I check the time and the date and come to where it the point that it froze. I found out the Log stop recording after the wireless connection. In almost all log (sys.log, messages.log, kern.log, debug.log, daemon.log) comfirmed this. Everytime it froze, it always end at what the wireless is doing. The sys.log said it was going through 5 stages to re-enable the connection, and it seem it keep repeating the stage from 1 to 3 until a few times then finally made a connection to my router, then it froze there. Other log than sys.log didn't said exact what sys.log said, but it always said wireless connection at the end of the log. So all I am aware that my Linksys WMP54G PCI Wireless card or Network Manager have something to do with this. or possible should i use nsdiwrapper to prevent this kind of problem?

And I remember last year, I replaced my wireless card, it believe it was Airlink 101 card, but I replaced it because it was having problem with signal strength. So I upgraded it to WMP54G.

Here the sys.log, That log is my entire session from boot to freeze moment, so you can help out what is wrong. Hate to sound needy on this, but please help me on this, it been plaguing on me for a month. And for the record I am using 9.04 with updated Linux kernal

```
Feb  8 15:28:30 sean-desktop syslogd 1.5.0#5ubuntu3: restart.
Feb  8 15:28:30 sean-desktop kernel: Inspecting /boot/System.map-2.6.28-18-generic
Feb  8 15:28:30 sean-desktop kernel: Cannot find map file.
Feb  8 15:28:30 sean-desktop kernel: Loaded 63294 symbols from 154 modules.
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Linux version 2.6.28-18-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #59-Ubuntu SMP Thu Jan 28 01:40:19 UTC 2010 (Ubuntu 2.6.28-18.59-generic)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Command line: root=UUID=af5e596c-35fa-4804-8cfc-82dcdd6e391a ro quiet splash 
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] KERNEL supported cpus:
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   Intel GenuineIntel
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   AMD AuthenticAMD
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   Centaur CentaurHauls
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfd43000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfd43000 - 00000000bfd4f000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfd4f000 - 00000000bfe2f000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfe2f000 - 00000000bfee8000 (ACPI NVS)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfee8000 - 00000000bfeeb000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfeeb000 - 00000000bfef0000 (ACPI data)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bfef1000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfef1000 - 00000000bfeff000 (ACPI data)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] DMI 2.4 present.
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] last_pfn = 0xbff00 max_arch_pfn = 0x3ffffffff
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Scanning 2 areas for low memory corruption
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] modified physical RAM map:
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 0000000000010000 - 0000000000082000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 000000000008f000 - 00000000000a0000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000bfd43000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000bfd43000 - 00000000bfd4f000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000bfd4f000 - 00000000bfe2f000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000bfe2f000 - 00000000bfee8000 (ACPI NVS)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000bfee8000 - 00000000bfeeb000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000bfeeb000 - 00000000bfef0000 (ACPI data)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000bfef0000 - 00000000bfef1000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000bfef1000 - 00000000bfeff000 (ACPI data)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000bfeff000 - 00000000bff00000 (usable)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000bff00000 - 00000000c0000000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bff00000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  0000000000 - 00bfe00000 page 2M
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  00bfe00000 - 00bff00000 page 4k
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] kernel direct mapping tables up to bff00000 @ 10000-15000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] last_map_addr: bff00000 end: bff00000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] RAMDISK: 37857000 - 37fef229
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: RSDT BFEFD038, 0050 (r1 INTEL  ECG3510M       73       1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: FACP BFEFC000, 0074 (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: DSDT BFEF6000, 5BEB (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: FACS BFE96000, 0040
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: APIC BFEF5000, 0078 (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: WDDT BFEF4000, 0040 (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: MCFG BFEF3000, 003C (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: ASF! BFEF2000, 00A6 (r32 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: HPET BFEF1000, 0038 (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEEF000, 020C (r1 INTEL     CpuPm       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEEE000, 0175 (r1 INTEL   Cpu0Ist       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEED000, 0175 (r1 INTEL   Cpu1Ist       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEEC000, 0175 (r1 INTEL   Cpu2Ist       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEEB000, 0175 (r1 INTEL   Cpu3Ist       73 MSFT  1000013)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] (6 early reservations) ==> bootmem [0000000000 - 00bff00000]
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   #2 [0000200000 - 0000b7cbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7cbb0]
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   #3 [0037857000 - 0037fef229]          RAMDISK ==> [0037857000 - 0037fef229]
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   #5 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000fe200] 000fe200
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]  [ffffe20000000000-ffffe200029fffff] PMD -> [ffff880001200000-ffff880003bfffff] on node 0
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Zone PFN ranges:
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Movable zone start PFN for each node
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] early_node_map[8] active PFN ranges
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x00000008
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x00000082
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000bfd43
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]     0: 0x000bfd4f -> 0x000bfe2f
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]     0: 0x000bfee8 -> 0x000bfeeb
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]     0: 0x000bfef0 -> 0x000bfef1
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]     0: 0x000bfeff -> 0x000bff00
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] On node 0 totalpages: 785821
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   DMA zone: 2532 pages reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   DMA zone: 1369 pages, LIFO batch:0
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   DMA32 zone: 10693 pages used for memmap
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   DMA32 zone: 771171 pages, LIFO batch:31
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Feb  8 15:28:30 sean-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000082000 - 000000000008f000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfd43000 - 00000000bfd4f000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfe2f000 - 00000000bfee8000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfeeb000 - 00000000bfef0000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfef1000 - 00000000bfeff000
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ff00000)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 772540
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Kernel command line: root=UUID=af5e596c-35fa-4804-8cfc-82dcdd6e391a ro quiet splash 
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Initializing CPU#0
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
Feb  8 15:28:30 sean-desktop kernel: [    0.000000] Detected 2651.404 MHz processor.
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] console [tty0] enabled
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] allocated 31457280 bytes of page_cgroup
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Checking aperture...
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] No AGP bridge found
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Calgary: detecting Calgary via BIOS EBDA area
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Memory: 3044784k/3144704k available (4750k kernel code, 1420k absent, 97848k reserved, 2523k data, 536k init)
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] hpet clockevent registered
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5302.80 BogoMIPS (lpj=10605616)
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Security Framework initialized
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] SELinux:  Disabled at boot.
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] AppArmor: AppArmor initialized
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Mount-cache hash table entries: 256
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Initializing cgroup subsys ns
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Initializing cgroup subsys memory
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Initializing cgroup subsys freezer
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: Processor Core ID: 0
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] using mwait in idle threads.
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] ACPI: Core revision 20080926
Feb  8 15:28:30 sean-desktop kernel: [    0.004395] ACPI: Checking initramfs for custom DSDT
Feb  8 15:28:30 sean-desktop kernel: [    0.256043] Setting APIC routing to flat
Feb  8 15:28:30 sean-desktop kernel: [    0.256394] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb  8 15:28:30 sean-desktop kernel: [    0.296849] CPU0: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Feb  8 15:28:30 sean-desktop kernel: [    0.300001] Booting processor 1 APIC 0x2 ip 0x6000
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Initializing CPU#1
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 4882.67 BogoMIPS (lpj=9765343)
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: Processor Core ID: 2
Feb  8 15:28:30 sean-desktop kernel: [    0.384668] CPU1: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Feb  8 15:28:30 sean-desktop kernel: [    0.384685] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Feb  8 15:28:30 sean-desktop kernel: [    0.388077] Booting processor 2 APIC 0x1 ip 0x6000
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Initializing CPU#2
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 5302.83 BogoMIPS (lpj=10605674)
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: Processor Core ID: 1
Feb  8 15:28:30 sean-desktop kernel: [    0.476503] CPU2: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Feb  8 15:28:30 sean-desktop kernel: [    0.476520] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Feb  8 15:28:30 sean-desktop kernel: [    0.480114] Booting processor 3 APIC 0x3 ip 0x6000
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Initializing CPU#3
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 5302.86 BogoMIPS (lpj=10605738)
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:28:30 sean-desktop kernel: [    0.004000] CPU: Processor Core ID: 3
Feb  8 15:28:30 sean-desktop kernel: [    0.568672] CPU3: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Feb  8 15:28:30 sean-desktop kernel: [    0.568689] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Feb  8 15:28:30 sean-desktop kernel: [    0.572028] Brought up 4 CPUs
Feb  8 15:28:30 sean-desktop kernel: [    0.572030] Total of 4 processors activated (20791.18 BogoMIPS).
Feb  8 15:28:30 sean-desktop kernel: [    0.572074] CPU0 attaching sched-domain:
Feb  8 15:28:30 sean-desktop kernel: [    0.572076]  domain 0: span 0,2 level MC
Feb  8 15:28:30 sean-desktop kernel: [    0.572077]   groups: 0 2
Feb  8 15:28:30 sean-desktop kernel: [    0.572080]   domain 1: span 0-3 level CPU
Feb  8 15:28:30 sean-desktop kernel: [    0.572081]    groups: 0,2 1,3
Feb  8 15:28:30 sean-desktop kernel: [    0.572085] CPU1 attaching sched-domain:
Feb  8 15:28:30 sean-desktop kernel: [    0.572086]  domain 0: span 1,3 level MC
Feb  8 15:28:30 sean-desktop kernel: [    0.572087]   groups: 1 3
Feb  8 15:28:30 sean-desktop kernel: [    0.572089]   domain 1: span 0-3 level CPU
Feb  8 15:28:30 sean-desktop kernel: [    0.572090]    groups: 1,3 0,2
Feb  8 15:28:30 sean-desktop kernel: [    0.572093] CPU2 attaching sched-domain:
Feb  8 15:28:30 sean-desktop kernel: [    0.572094]  domain 0: span 0,2 level MC
Feb  8 15:28:30 sean-desktop kernel: [    0.572095]   groups: 2 0
Feb  8 15:28:30 sean-desktop kernel: [    0.572097]   domain 1: span 0-3 level CPU
Feb  8 15:28:30 sean-desktop kernel: [    0.572098]    groups: 0,2 1,3
Feb  8 15:28:30 sean-desktop kernel: [    0.572101] CPU3 attaching sched-domain:
Feb  8 15:28:30 sean-desktop kernel: [    0.572102]  domain 0: span 1,3 level MC
Feb  8 15:28:30 sean-desktop kernel: [    0.572103]   groups: 3 1
Feb  8 15:28:30 sean-desktop kernel: [    0.572105]   domain 1: span 0-3 level CPU
Feb  8 15:28:30 sean-desktop kernel: [    0.572106]    groups: 1,3 0,2
Feb  8 15:28:30 sean-desktop kernel: [    0.572190] net_namespace: 1400 bytes
Feb  8 15:28:30 sean-desktop kernel: [    0.572190] Booting paravirtualized kernel on bare hardware
Feb  8 15:28:30 sean-desktop kernel: [    0.572273] Time: 15:28:15  Date: 02/08/10
Feb  8 15:28:30 sean-desktop kernel: [    0.572273] regulator: core version 0.5
Feb  8 15:28:30 sean-desktop kernel: [    0.572273] NET: Registered protocol family 16
Feb  8 15:28:30 sean-desktop kernel: [    0.572273] ACPI: bus type pci registered
Feb  8 15:28:30 sean-desktop kernel: [    0.572273] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
Feb  8 15:28:30 sean-desktop kernel: [    0.572273] PCI: Not using MMCONFIG.
Feb  8 15:28:30 sean-desktop kernel: [    0.572273] PCI: Using configuration type 1 for base access
Feb  8 15:28:30 sean-desktop kernel: [    0.572715] ACPI: EC: Look up EC in DSDT
Feb  8 15:28:30 sean-desktop kernel: [    0.577601] ACPI: Interpreter enabled
Feb  8 15:28:30 sean-desktop kernel: [    0.577603] ACPI: (supports S0 S1 S3 S4 S5)
Feb  8 15:28:30 sean-desktop kernel: [    0.577618] ACPI: Using IOAPIC for interrupt routing
Feb  8 15:28:30 sean-desktop kernel: [    0.577652] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
Feb  8 15:28:30 sean-desktop kernel: [    0.578281] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
Feb  8 15:28:30 sean-desktop kernel: [    0.582597] PCI: Using MMCONFIG at f0000000 - f7ffffff
Feb  8 15:28:30 sean-desktop kernel: [    0.585932] ACPI: No dock devices found.
Feb  8 15:28:30 sean-desktop kernel: [    0.585940] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  8 15:28:30 sean-desktop kernel: [    0.586001] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Feb  8 15:28:30 sean-desktop kernel: [    0.586003] pci 0000:00:01.0: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586047] pci 0000:00:19.0: reg 10 32bit mmio: [0xd0200000-0xd021ffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586051] pci 0000:00:19.0: reg 14 32bit mmio: [0xd0224000-0xd0224fff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586056] pci 0000:00:19.0: reg 18 io port: [0x30c0-0x30df]
Feb  8 15:28:30 sean-desktop kernel: [    0.586075] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Feb  8 15:28:30 sean-desktop kernel: [    0.586077] pci 0000:00:19.0: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586108] pci 0000:00:1a.0: reg 20 io port: [0x30a0-0x30bf]
Feb  8 15:28:30 sean-desktop kernel: [    0.586144] pci 0000:00:1a.1: reg 20 io port: [0x3080-0x309f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586185] pci 0000:00:1a.7: reg 10 32bit mmio: [0xd0225400-0xd02257ff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586215] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Feb  8 15:28:30 sean-desktop kernel: [    0.586219] pci 0000:00:1a.7: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586248] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd0220000-0xd0223fff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586270] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Feb  8 15:28:30 sean-desktop kernel: [    0.586272] pci 0000:00:1b.0: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586307] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Feb  8 15:28:30 sean-desktop kernel: [    0.586309] pci 0000:00:1c.0: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586345] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Feb  8 15:28:30 sean-desktop kernel: [    0.586347] pci 0000:00:1c.1: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586383] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Feb  8 15:28:30 sean-desktop kernel: [    0.586385] pci 0000:00:1c.2: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586421] pci 0000:00:1d.0: reg 20 io port: [0x3060-0x307f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586459] pci 0000:00:1d.1: reg 20 io port: [0x3040-0x305f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586495] pci 0000:00:1d.2: reg 20 io port: [0x3020-0x303f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586536] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0225000-0xd02253ff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586566] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Feb  8 15:28:30 sean-desktop kernel: [    0.586569] pci 0000:00:1d.7: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586659] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Feb  8 15:28:30 sean-desktop kernel: [    0.586661] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
Feb  8 15:28:30 sean-desktop kernel: [    0.586689] pci 0000:00:1f.2: reg 10 io port: [0x3438-0x343f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586693] pci 0000:00:1f.2: reg 14 io port: [0x344c-0x344f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586697] pci 0000:00:1f.2: reg 18 io port: [0x3430-0x3437]
Feb  8 15:28:30 sean-desktop kernel: [    0.586701] pci 0000:00:1f.2: reg 1c io port: [0x3448-0x344b]
Feb  8 15:28:30 sean-desktop kernel: [    0.586705] pci 0000:00:1f.2: reg 20 io port: [0x3410-0x341f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586709] pci 0000:00:1f.2: reg 24 io port: [0x3400-0x340f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586719] pci 0000:00:1f.2: PME# supported from D3hot
Feb  8 15:28:30 sean-desktop kernel: [    0.586721] pci 0000:00:1f.2: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586735] pci 0000:00:1f.3: reg 10 32bit mmio: [0xd0225800-0xd02258ff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586748] pci 0000:00:1f.3: reg 20 io port: [0x3000-0x301f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586776] pci 0000:00:1f.5: reg 10 io port: [0x3428-0x342f]
Feb  8 15:28:30 sean-desktop kernel: [    0.586780] pci 0000:00:1f.5: reg 14 io port: [0x3444-0x3447]
Feb  8 15:28:30 sean-desktop kernel: [    0.586784] pci 0000:00:1f.5: reg 18 io port: [0x3420-0x3427]
Feb  8 15:28:30 sean-desktop kernel: [    0.586788] pci 0000:00:1f.5: reg 1c io port: [0x3440-0x3443]
Feb  8 15:28:30 sean-desktop kernel: [    0.586792] pci 0000:00:1f.5: reg 20 io port: [0x30f0-0x30ff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586796] pci 0000:00:1f.5: reg 24 io port: [0x30e0-0x30ef]
Feb  8 15:28:30 sean-desktop kernel: [    0.586806] pci 0000:00:1f.5: PME# supported from D3hot
Feb  8 15:28:30 sean-desktop kernel: [    0.586808] pci 0000:00:1f.5: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.586834] pci 0000:01:00.0: reg 10 64bit mmio: [0xc0000000-0xcfffffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586841] pci 0000:01:00.0: reg 18 64bit mmio: [0xd0100000-0xd010ffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586845] pci 0000:01:00.0: reg 20 io port: [0x2000-0x20ff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586852] pci 0000:01:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586857] pci 0000:01:00.0: supports D1 D2
Feb  8 15:28:30 sean-desktop kernel: [    0.586882] pci 0000:01:00.1: reg 10 64bit mmio: [0xd0110000-0xd0113fff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586901] pci 0000:01:00.1: supports D1 D2
Feb  8 15:28:30 sean-desktop kernel: [    0.586935] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586937] pci 0000:00:01.0: bridge 32bit mmio: [0xd0100000-0xd01fffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.586940] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.587054] pci 0000:04:00.0: reg 10 io port: [0x1018-0x101f]
Feb  8 15:28:30 sean-desktop kernel: [    0.587062] pci 0000:04:00.0: reg 14 io port: [0x1024-0x1027]
Feb  8 15:28:30 sean-desktop kernel: [    0.587069] pci 0000:04:00.0: reg 18 io port: [0x1010-0x1017]
Feb  8 15:28:30 sean-desktop kernel: [    0.587077] pci 0000:04:00.0: reg 1c io port: [0x1020-0x1023]
Feb  8 15:28:30 sean-desktop kernel: [    0.587084] pci 0000:04:00.0: reg 20 io port: [0x1000-0x100f]
Feb  8 15:28:30 sean-desktop kernel: [    0.587098] pci 0000:04:00.0: reg 30 32bit mmio: [0xffff0000-0xffffffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.587148] pci 0000:00:1c.2: bridge io port: [0x1000-0x1fff]
Feb  8 15:28:30 sean-desktop kernel: [    0.587183] pci 0000:05:03.0: reg 10 32bit mmio: [0xd0000000-0xd0007fff]
Feb  8 15:28:30 sean-desktop kernel: [    0.587241] pci 0000:05:05.0: reg 10 32bit mmio: [0xd0008000-0xd0008fff]
Feb  8 15:28:30 sean-desktop kernel: [    0.587271] pci 0000:05:05.0: supports D1 D2
Feb  8 15:28:30 sean-desktop kernel: [    0.587272] pci 0000:05:05.0: PME# supported from D0 D1 D2 D3hot
Feb  8 15:28:30 sean-desktop kernel: [    0.587276] pci 0000:05:05.0: PME# disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.587307] pci 0000:00:1e.0: transparent bridge
Feb  8 15:28:30 sean-desktop kernel: [    0.587311] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0000000-0xd00fffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.587330] bus 00 -> node 0
Feb  8 15:28:30 sean-desktop kernel: [    0.587334] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb  8 15:28:30 sean-desktop kernel: [    0.587650] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
Feb  8 15:28:30 sean-desktop kernel: [    0.587772] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Feb  8 15:28:30 sean-desktop kernel: [    0.587868] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
Feb  8 15:28:30 sean-desktop kernel: [    0.587964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
Feb  8 15:28:30 sean-desktop kernel: [    0.590979] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 15:28:30 sean-desktop kernel: [    0.591072] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
Feb  8 15:28:30 sean-desktop kernel: [    0.591163] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12)
Feb  8 15:28:30 sean-desktop kernel: [    0.591254] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 15:28:30 sean-desktop kernel: [    0.591345] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12)
Feb  8 15:28:30 sean-desktop kernel: [    0.591436] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 15:28:30 sean-desktop kernel: [    0.591527] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
Feb  8 15:28:30 sean-desktop kernel: [    0.591617] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 15:28:30 sean-desktop kernel: [    0.591796] ACPI: WMI: Mapper loaded
Feb  8 15:28:30 sean-desktop kernel: [    0.591826] SCSI subsystem initialized
Feb  8 15:28:30 sean-desktop kernel: [    0.592018] libata version 3.00 loaded.
Feb  8 15:28:30 sean-desktop kernel: [    0.592031] usbcore: registered new interface driver usbfs
Feb  8 15:28:30 sean-desktop kernel: [    0.592045] usbcore: registered new interface driver hub
Feb  8 15:28:30 sean-desktop kernel: [    0.592056] usbcore: registered new device driver usb
Feb  8 15:28:30 sean-desktop kernel: [    0.592056] PCI: Using ACPI for IRQ routing
Feb  8 15:28:30 sean-desktop kernel: [    0.604010] Bluetooth: Core ver 2.13
Feb  8 15:28:30 sean-desktop kernel: [    0.604024] NET: Registered protocol family 31
Feb  8 15:28:30 sean-desktop kernel: [    0.604024] Bluetooth: HCI device and connection manager initialized
Feb  8 15:28:30 sean-desktop kernel: [    0.604024] Bluetooth: HCI socket layer initialized
Feb  8 15:28:30 sean-desktop kernel: [    0.604024] NET: Registered protocol family 8
Feb  8 15:28:30 sean-desktop kernel: [    0.604024] NET: Registered protocol family 20
Feb  8 15:28:30 sean-desktop kernel: [    0.604031] NetLabel: Initializing
Feb  8 15:28:30 sean-desktop kernel: [    0.604032] NetLabel:  domain hash size = 128
Feb  8 15:28:30 sean-desktop kernel: [    0.604034] NetLabel:  protocols = UNLABELED CIPSOv4
Feb  8 15:28:30 sean-desktop kernel: [    0.604046] NetLabel:  unlabeled traffic allowed by default
Feb  8 15:28:30 sean-desktop kernel: [    0.604076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Feb  8 15:28:30 sean-desktop kernel: [    0.604080] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Feb  8 15:28:30 sean-desktop kernel: [    0.612060] AppArmor: AppArmor Filesystem Enabled
Feb  8 15:28:30 sean-desktop kernel: [    0.616010] Switched to high resolution mode on CPU 0
Feb  8 15:28:30 sean-desktop kernel: [    0.616553] Switched to high resolution mode on CPU 2
Feb  8 15:28:30 sean-desktop kernel: [    0.616727] Switched to high resolution mode on CPU 1
Feb  8 15:28:30 sean-desktop kernel: [    0.616730] Switched to high resolution mode on CPU 3
Feb  8 15:28:30 sean-desktop kernel: [    0.624009] pnp: PnP ACPI init
Feb  8 15:28:30 sean-desktop kernel: [    0.624017] ACPI: bus type pnp registered
Feb  8 15:28:30 sean-desktop kernel: [    0.625986] pnp: PnP ACPI: found 11 devices
Feb  8 15:28:30 sean-desktop kernel: [    0.625988] ACPI: ACPI bus type pnp unregistered
Feb  8 15:28:30 sean-desktop kernel: [    0.625994] system 00:01: iomem range 0xf0000000-0xf7ffffff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.625995] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.625997] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.625999] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626000] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626002] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626003] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626005] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626007] system 00:01: iomem range 0xc0000-0xdffff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626010] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626015] system 00:06: ioport range 0x500-0x53f has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626016] system 00:06: ioport range 0x400-0x47f has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626018] system 00:06: ioport range 0x360-0x361 has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.626019] system 00:06: ioport range 0x680-0x6ff has been reserved
Feb  8 15:28:30 sean-desktop kernel: [    0.630644] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Feb  8 15:28:30 sean-desktop kernel: [    0.630645] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
Feb  8 15:28:30 sean-desktop kernel: [    0.630648] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
Feb  8 15:28:30 sean-desktop kernel: [    0.630650] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Feb  8 15:28:30 sean-desktop kernel: [    0.630653] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Feb  8 15:28:30 sean-desktop kernel: [    0.630654] pci 0000:00:1c.0:   IO window: disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.630658] pci 0000:00:1c.0:   MEM window: disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.630660] pci 0000:00:1c.0:   PREFETCH window: disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.630664] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Feb  8 15:28:30 sean-desktop kernel: [    0.630665] pci 0000:00:1c.1:   IO window: disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.630669] pci 0000:00:1c.1:   MEM window: disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.630671] pci 0000:00:1c.1:   PREFETCH window: disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.630675] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Feb  8 15:28:30 sean-desktop kernel: [    0.630677] pci 0000:00:1c.2:   IO window: 0x1000-0x1fff
Feb  8 15:28:30 sean-desktop kernel: [    0.630681] pci 0000:00:1c.2:   MEM window: disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.630683] pci 0000:00:1c.2:   PREFETCH window: 0x000000d0300000-0x000000d03fffff
Feb  8 15:28:30 sean-desktop kernel: [    0.630688] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Feb  8 15:28:30 sean-desktop kernel: [    0.630689] pci 0000:00:1e.0:   IO window: disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.630692] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff
Feb  8 15:28:30 sean-desktop kernel: [    0.630695] pci 0000:00:1e.0:   PREFETCH window: disabled
Feb  8 15:28:30 sean-desktop kernel: [    0.630704] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:28:30 sean-desktop kernel: [    0.630707] pci 0000:00:01.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    0.630712] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb  8 15:28:30 sean-desktop kernel: [    0.630715] pci 0000:00:1c.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    0.630720] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:28:30 sean-desktop kernel: [    0.630722] pci 0000:00:1c.1: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    0.630728] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  8 15:28:30 sean-desktop kernel: [    0.630730] pci 0000:00:1c.2: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    0.630735] pci 0000:00:1e.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    0.630737] bus: 00 index 0 io port: [0x00-0xffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630739] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630740] bus: 01 index 0 io port: [0x2000-0x2fff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630741] bus: 01 index 1 mmio: [0xd0100000-0xd01fffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630743] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630744] bus: 01 index 3 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630745] bus: 02 index 0 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630746] bus: 02 index 1 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630747] bus: 02 index 2 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630748] bus: 02 index 3 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630749] bus: 03 index 0 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630750] bus: 03 index 1 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630751] bus: 03 index 2 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630752] bus: 03 index 3 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630753] bus: 04 index 0 io port: [0x1000-0x1fff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630754] bus: 04 index 1 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630755] bus: 04 index 2 mmio: [0xd0300000-0xd03fffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630756] bus: 04 index 3 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630757] bus: 05 index 0 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630759] bus: 05 index 1 mmio: [0xd0000000-0xd00fffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630760] bus: 05 index 2 mmio: [0x0-0x0]
Feb  8 15:28:30 sean-desktop kernel: [    0.630761] bus: 05 index 3 io port: [0x00-0xffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630762] bus: 05 index 4 mmio: [0x000000-0xffffffffffffffff]
Feb  8 15:28:30 sean-desktop kernel: [    0.630768] NET: Registered protocol family 2
Feb  8 15:28:30 sean-desktop kernel: [    0.664050] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Feb  8 15:28:30 sean-desktop kernel: [    0.664462] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Feb  8 15:28:30 sean-desktop kernel: [    0.667214] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb  8 15:28:30 sean-desktop kernel: [    0.668138] TCP: Hash tables configured (established 262144 bind 65536)
Feb  8 15:28:30 sean-desktop kernel: [    0.668141] TCP reno registered
Feb  8 15:28:30 sean-desktop kernel: [    0.680145] NET: Registered protocol family 1
Feb  8 15:28:30 sean-desktop kernel: [    0.680255] checking if image is initramfs... it is
Feb  8 15:28:30 sean-desktop kernel: [    1.187788] Freeing initrd memory: 7776k freed
Feb  8 15:28:30 sean-desktop kernel: [    1.191303] audit: initializing netlink socket (disabled)
Feb  8 15:28:30 sean-desktop kernel: [    1.191322] type=2000 audit(1265642895.188:1): initialized
Feb  8 15:28:30 sean-desktop kernel: [    1.199736] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb  8 15:28:30 sean-desktop kernel: [    1.200934] VFS: Disk quotas dquot_6.5.1
Feb  8 15:28:30 sean-desktop kernel: [    1.200982] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb  8 15:28:30 sean-desktop kernel: [    1.201476] fuse init (API version 7.10)
Feb  8 15:28:30 sean-desktop kernel: [    1.201552] msgmni has been set to 5963
Feb  8 15:28:30 sean-desktop kernel: [    1.201725] alg: No test for stdrng (krng)
Feb  8 15:28:30 sean-desktop kernel: [    1.201738] io scheduler noop registered
Feb  8 15:28:30 sean-desktop kernel: [    1.201740] io scheduler anticipatory registered
Feb  8 15:28:30 sean-desktop kernel: [    1.201742] io scheduler deadline registered
Feb  8 15:28:30 sean-desktop kernel: [    1.201777] io scheduler cfq registered (default)
Feb  8 15:28:30 sean-desktop kernel: [    1.202095] pci 0000:01:00.0: Boot video device
Feb  8 15:28:30 sean-desktop kernel: [    1.203787] pcieport-driver 0000:00:01.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    1.203814] pcieport-driver 0000:00:01.0: found MSI capability
Feb  8 15:28:30 sean-desktop kernel: [    1.203832] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
Feb  8 15:28:30 sean-desktop kernel: [    1.203840] pci_express 0000:00:01.0:pcie00: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.203852] pci_express 0000:00:01.0:pcie03: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.203890] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    1.203917] pcieport-driver 0000:00:1c.0: found MSI capability
Feb  8 15:28:30 sean-desktop kernel: [    1.203937] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
Feb  8 15:28:30 sean-desktop kernel: [    1.203946] pci_express 0000:00:1c.0:pcie00: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.203957] pci_express 0000:00:1c.0:pcie02: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.203969] pci_express 0000:00:1c.0:pcie03: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.204017] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    1.204052] pcieport-driver 0000:00:1c.1: found MSI capability
Feb  8 15:28:30 sean-desktop kernel: [    1.204076] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
Feb  8 15:28:30 sean-desktop kernel: [    1.204088] pci_express 0000:00:1c.1:pcie00: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.204098] pci_express 0000:00:1c.1:pcie02: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.204109] pci_express 0000:00:1c.1:pcie03: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.204170] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    1.204209] pcieport-driver 0000:00:1c.2: found MSI capability
Feb  8 15:28:30 sean-desktop kernel: [    1.204228] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
Feb  8 15:28:30 sean-desktop kernel: [    1.204238] pci_express 0000:00:1c.2:pcie00: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.204248] pci_express 0000:00:1c.2:pcie02: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.204258] pci_express 0000:00:1c.2:pcie03: allocate port service
Feb  8 15:28:30 sean-desktop kernel: [    1.204315] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  8 15:28:30 sean-desktop kernel: [    1.204388] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb  8 15:28:30 sean-desktop kernel: [    1.204510] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Feb  8 15:28:30 sean-desktop kernel: [    1.204513] ACPI: Power Button (FF) [PWRF]
Feb  8 15:28:30 sean-desktop kernel: [    1.204552] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Feb  8 15:28:30 sean-desktop kernel: [    1.204559] ACPI: Sleep Button (CM) [SLPB]
Feb  8 15:28:30 sean-desktop kernel: [    1.204862] processor ACPI_CPU:00: registered as cooling_device0
Feb  8 15:28:30 sean-desktop kernel: [    1.204868] ACPI: Processor [CPU0] (supports 8 throttling states)
Feb  8 15:28:30 sean-desktop kernel: [    1.205020] processor ACPI_CPU:01: registered as cooling_device1
Feb  8 15:28:30 sean-desktop kernel: [    1.205023] ACPI: Processor [CPU1] (supports 8 throttling states)
Feb  8 15:28:30 sean-desktop kernel: [    1.205134] processor ACPI_CPU:02: registered as cooling_device2
Feb  8 15:28:30 sean-desktop kernel: [    1.205139] ACPI: Processor [CPU2] (supports 8 throttling states)
Feb  8 15:28:30 sean-desktop kernel: [    1.205252] processor ACPI_CPU:03: registered as cooling_device3
Feb  8 15:28:30 sean-desktop kernel: [    1.205256] ACPI: Processor [CPU3] (supports 8 throttling states)
Feb  8 15:28:30 sean-desktop kernel: [    1.233622] Linux agpgart interface v0.103
Feb  8 15:28:30 sean-desktop kernel: [    1.233630] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Feb  8 15:28:30 sean-desktop kernel: [    1.233713] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  8 15:28:30 sean-desktop kernel: [    1.234018] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  8 15:28:30 sean-desktop kernel: [    1.234658] brd: module loaded
Feb  8 15:28:30 sean-desktop kernel: [    1.234929] loop: module loaded
Feb  8 15:28:30 sean-desktop kernel: [    1.234986] Fixed MDIO Bus: probed
Feb  8 15:28:30 sean-desktop kernel: [    1.234991] PPP generic driver version 2.4.2
Feb  8 15:28:30 sean-desktop kernel: [    1.235039] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Feb  8 15:28:30 sean-desktop kernel: [    1.235062] Driver 'sd' needs updating - please use bus_type methods
Feb  8 15:28:30 sean-desktop kernel: [    1.235070] Driver 'sr' needs updating - please use bus_type methods
Feb  8 15:28:30 sean-desktop kernel: [    1.235134] ata_piix 0000:00:1f.2: version 2.12
Feb  8 15:28:30 sean-desktop kernel: [    1.235147] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb  8 15:28:30 sean-desktop kernel: [    1.235150] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Feb  8 15:28:30 sean-desktop kernel: [    1.388019] ata_piix 0000:00:1f.2: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    1.388078] scsi0 : ata_piix
Feb  8 15:28:30 sean-desktop kernel: [    1.388156] scsi1 : ata_piix
Feb  8 15:28:30 sean-desktop kernel: [    1.389017] ata1: SATA max UDMA/133 cmd 0x3438 ctl 0x344c bmdma 0x3410 irq 19
Feb  8 15:28:30 sean-desktop kernel: [    1.389022] ata2: SATA max UDMA/133 cmd 0x3430 ctl 0x3448 bmdma 0x3418 irq 19
Feb  8 15:28:30 sean-desktop kernel: [    2.184052] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb  8 15:28:30 sean-desktop kernel: [    2.184061] ata1.01: SATA link down (SStatus 4 SControl 300)
Feb  8 15:28:30 sean-desktop kernel: [    2.220439] ata1.00: ATA-7: WDC WD2500YS-01SHB0, 20.06C06, max UDMA/133
Feb  8 15:28:30 sean-desktop kernel: [    2.220442] ata1.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
Feb  8 15:28:30 sean-desktop kernel: [    2.236354] ata1.00: configured for UDMA/133
Feb  8 15:28:30 sean-desktop kernel: [    2.886561] ata2.00: SATA link down (SStatus 0 SControl 300)
Feb  8 15:28:30 sean-desktop kernel: [    2.886569] ata2.01: SATA link down (SStatus 4 SControl 300)
Feb  8 15:28:30 sean-desktop kernel: [    2.886600] isa bounce pool size: 16 pages
Feb  8 15:28:30 sean-desktop kernel: [    2.886672] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
Feb  8 15:28:30 sean-desktop kernel: [    2.886758] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors: (251 GB/233 GiB)
Feb  8 15:28:30 sean-desktop kernel: [    2.886773] sd 0:0:0:0: [sda] Write Protect is off
Feb  8 15:28:30 sean-desktop kernel: [    2.886775] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb  8 15:28:30 sean-desktop kernel: [    2.886799] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  8 15:28:30 sean-desktop kernel: [    2.886853] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors: (251 GB/233 GiB)
Feb  8 15:28:30 sean-desktop kernel: [    2.886867] sd 0:0:0:0: [sda] Write Protect is off
Feb  8 15:28:30 sean-desktop kernel: [    2.886869] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb  8 15:28:30 sean-desktop kernel: [    2.886892] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  8 15:28:30 sean-desktop kernel: [    2.886895]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
Feb  8 15:28:30 sean-desktop kernel: [    2.938939] sd 0:0:0:0: [sda] Attached SCSI disk
Feb  8 15:28:30 sean-desktop kernel: [    2.938986] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb  8 15:28:30 sean-desktop kernel: [    2.939020] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb  8 15:28:30 sean-desktop kernel: [    2.939023] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Feb  8 15:28:30 sean-desktop kernel: [    2.939062] ata_piix 0000:00:1f.5: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    2.939096] scsi2 : ata_piix
Feb  8 15:28:30 sean-desktop kernel: [    2.939134] scsi3 : ata_piix
Feb  8 15:28:30 sean-desktop kernel: [    2.939806] ata3: SATA max UDMA/133 cmd 0x3428 ctl 0x3444 bmdma 0x30f0 irq 19
Feb  8 15:28:30 sean-desktop kernel: [    2.939809] ata4: SATA max UDMA/133 cmd 0x3420 ctl 0x3440 bmdma 0x30f8 irq 19
Feb  8 15:28:30 sean-desktop kernel: [    3.266508] ata3: SATA link down (SStatus 0 SControl 300)
Feb  8 15:28:30 sean-desktop kernel: [    3.594507] ata4: SATA link down (SStatus 0 SControl 300)
Feb  8 15:28:30 sean-desktop kernel: [    3.594739] pata_jmicron 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  8 15:28:30 sean-desktop kernel: [    3.594762] pata_jmicron 0000:04:00.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    3.594826] scsi4 : pata_jmicron
Feb  8 15:28:30 sean-desktop kernel: [    3.594887] scsi5 : pata_jmicron
Feb  8 15:28:30 sean-desktop kernel: [    3.595372] ata5: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 18
Feb  8 15:28:30 sean-desktop kernel: [    3.595373] ata6: PATA max UDMA/100 cmd 0x1010 ctl 0x1020 bmdma 0x1008 irq 18
Feb  8 15:28:30 sean-desktop kernel: [    3.756494] ata5.00: ATAPI: DVD-ROM BDV316G, VER 0015, max UDMA/66
Feb  8 15:28:30 sean-desktop kernel: [    3.772502] ata5.00: configured for UDMA/66
Feb  8 15:28:30 sean-desktop kernel: [    3.928730] scsi 4:0:0:0: CD-ROM            DVD-16X  DVD-ROM BDV316G  0015 PQ: 0 ANSI: 5
Feb  8 15:28:30 sean-desktop kernel: [    3.933434] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
Feb  8 15:28:30 sean-desktop kernel: [    3.933437] Uniform CD-ROM driver Revision: 3.20
Feb  8 15:28:30 sean-desktop kernel: [    3.933520] sr 4:0:0:0: Attached scsi CD-ROM sr0
Feb  8 15:28:30 sean-desktop kernel: [    3.933552] sr 4:0:0:0: Attached scsi generic sg1 type 5
Feb  8 15:28:30 sean-desktop kernel: [    3.933757] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb  8 15:28:30 sean-desktop kernel: [    3.933770] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  8 15:28:30 sean-desktop kernel: [    3.933794] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    3.933797] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Feb  8 15:28:30 sean-desktop kernel: [    3.933850] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Feb  8 15:28:30 sean-desktop kernel: [    3.937746] ehci_hcd 0000:00:1a.7: debug port 1
Feb  8 15:28:30 sean-desktop kernel: [    3.937751] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Feb  8 15:28:30 sean-desktop kernel: [    3.937754] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xd0225400
Feb  8 15:28:30 sean-desktop kernel: [    3.952008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Feb  8 15:28:30 sean-desktop kernel: [    3.952063] usb usb1: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    3.952089] hub 1-0:1.0: USB hub found
Feb  8 15:28:30 sean-desktop kernel: [    3.952096] hub 1-0:1.0: 4 ports detected
Feb  8 15:28:30 sean-desktop kernel: [    3.952184] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb  8 15:28:30 sean-desktop kernel: [    3.952191] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    3.952193] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb  8 15:28:30 sean-desktop kernel: [    3.952222] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Feb  8 15:28:30 sean-desktop kernel: [    3.956120] ehci_hcd 0000:00:1d.7: debug port 1
Feb  8 15:28:30 sean-desktop kernel: [    3.956124] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Feb  8 15:28:30 sean-desktop kernel: [    3.956134] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0225000
Feb  8 15:28:30 sean-desktop kernel: [    3.972007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Feb  8 15:28:30 sean-desktop kernel: [    3.972062] usb usb2: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    3.972083] hub 2-0:1.0: USB hub found
Feb  8 15:28:30 sean-desktop kernel: [    3.972088] hub 2-0:1.0: 6 ports detected
Feb  8 15:28:30 sean-desktop kernel: [    3.972170] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb  8 15:28:30 sean-desktop kernel: [    3.972180] uhci_hcd: USB Universal Host Controller Interface driver
Feb  8 15:28:30 sean-desktop kernel: [    3.972195] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:28:30 sean-desktop kernel: [    3.972200] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    3.972202] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Feb  8 15:28:30 sean-desktop kernel: [    3.972227] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Feb  8 15:28:30 sean-desktop kernel: [    3.972253] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000030a0
Feb  8 15:28:30 sean-desktop kernel: [    3.972306] usb usb3: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    3.972321] hub 3-0:1.0: USB hub found
Feb  8 15:28:30 sean-desktop kernel: [    3.972325] hub 3-0:1.0: 2 ports detected
Feb  8 15:28:30 sean-desktop kernel: [    3.972381] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Feb  8 15:28:30 sean-desktop kernel: [    3.972385] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    3.972387] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Feb  8 15:28:30 sean-desktop kernel: [    3.972423] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Feb  8 15:28:30 sean-desktop kernel: [    3.972446] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00003080
Feb  8 15:28:30 sean-desktop kernel: [    3.972492] usb usb4: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    3.972510] hub 4-0:1.0: USB hub found
Feb  8 15:28:30 sean-desktop kernel: [    3.972513] hub 4-0:1.0: 2 ports detected
Feb  8 15:28:30 sean-desktop kernel: [    3.972569] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb  8 15:28:30 sean-desktop kernel: [    3.972573] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    3.972575] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb  8 15:28:30 sean-desktop kernel: [    3.972601] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Feb  8 15:28:30 sean-desktop kernel: [    3.972619] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003060
Feb  8 15:28:30 sean-desktop kernel: [    3.972670] usb usb5: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    3.972685] hub 5-0:1.0: USB hub found
Feb  8 15:28:30 sean-desktop kernel: [    3.972689] hub 5-0:1.0: 2 ports detected
Feb  8 15:28:30 sean-desktop kernel: [    3.972744] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Feb  8 15:28:30 sean-desktop kernel: [    3.972748] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    3.972750] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb  8 15:28:30 sean-desktop kernel: [    3.972783] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Feb  8 15:28:30 sean-desktop kernel: [    3.972801] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003040
Feb  8 15:28:30 sean-desktop kernel: [    3.972850] usb usb6: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    3.972865] hub 6-0:1.0: USB hub found
Feb  8 15:28:30 sean-desktop kernel: [    3.972869] hub 6-0:1.0: 2 ports detected
Feb  8 15:28:30 sean-desktop kernel: [    3.972922] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  8 15:28:30 sean-desktop kernel: [    3.972926] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    3.972928] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb  8 15:28:30 sean-desktop kernel: [    3.972955] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Feb  8 15:28:30 sean-desktop kernel: [    3.972973] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003020
Feb  8 15:28:30 sean-desktop kernel: [    3.973021] usb usb7: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    3.973042] hub 7-0:1.0: USB hub found
Feb  8 15:28:30 sean-desktop kernel: [    3.973045] hub 7-0:1.0: 2 ports detected
Feb  8 15:28:30 sean-desktop kernel: [    3.973137] PNP: No PS/2 controller found. Probing ports directly.
Feb  8 15:28:30 sean-desktop kernel: [    3.975337] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  8 15:28:30 sean-desktop kernel: [    3.975341] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  8 15:28:30 sean-desktop kernel: [    3.984034] mice: PS/2 mouse device common for all mice
Feb  8 15:28:30 sean-desktop kernel: [    4.020062] rtc_cmos 00:03: RTC can wake from S4
Feb  8 15:28:30 sean-desktop kernel: [    4.020097] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Feb  8 15:28:30 sean-desktop kernel: [    4.020119] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Feb  8 15:28:30 sean-desktop kernel: [    4.020173] device-mapper: uevent: version 1.0.3
Feb  8 15:28:30 sean-desktop kernel: [    4.020253] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Feb  8 15:28:30 sean-desktop kernel: [    4.020368] device-mapper: multipath: version 1.0.5 loaded
Feb  8 15:28:30 sean-desktop kernel: [    4.020371] device-mapper: multipath round-robin: version 1.0.0 loaded
Feb  8 15:28:30 sean-desktop kernel: [    4.020499] cpuidle: using governor ladder
Feb  8 15:28:30 sean-desktop kernel: [    4.020501] cpuidle: using governor menu
Feb  8 15:28:30 sean-desktop kernel: [    4.020789] TCP cubic registered
Feb  8 15:28:30 sean-desktop kernel: [    4.020835] NET: Registered protocol family 10
Feb  8 15:28:30 sean-desktop kernel: [    4.021115] lo: Disabled Privacy Extensions
Feb  8 15:28:30 sean-desktop kernel: [    4.021304] NET: Registered protocol family 17
Feb  8 15:28:30 sean-desktop kernel: [    4.021317] Bluetooth: L2CAP ver 2.11
Feb  8 15:28:30 sean-desktop kernel: [    4.021318] Bluetooth: L2CAP socket layer initialized
Feb  8 15:28:30 sean-desktop kernel: [    4.021320] Bluetooth: SCO (Voice Link) ver 0.6
Feb  8 15:28:30 sean-desktop kernel: [    4.021321] Bluetooth: SCO socket layer initialized
Feb  8 15:28:30 sean-desktop kernel: [    4.021351] Bluetooth: RFCOMM socket layer initialized
Feb  8 15:28:30 sean-desktop kernel: [    4.021359] Bluetooth: RFCOMM TTY layer initialized
Feb  8 15:28:30 sean-desktop kernel: [    4.021360] Bluetooth: RFCOMM ver 1.10
Feb  8 15:28:30 sean-desktop kernel: [    4.022157] registered taskstats version 1
Feb  8 15:28:30 sean-desktop kernel: [    4.022265]   Magic number: 14:92:487
Feb  8 15:28:30 sean-desktop kernel: [    4.022344] rtc_cmos 00:03: setting system clock to 2010-02-08 15:28:19 UTC (1265642899)
Feb  8 15:28:30 sean-desktop kernel: [    4.022351] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb  8 15:28:30 sean-desktop kernel: [    4.022352] EDD information not available.
Feb  8 15:28:30 sean-desktop kernel: [    4.022389] Freeing unused kernel memory: 536k freed
Feb  8 15:28:30 sean-desktop kernel: [    4.022510] Write protecting the kernel read-only data: 6688k
Feb  8 15:28:30 sean-desktop kernel: [    4.140527] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Feb  8 15:28:30 sean-desktop kernel: [    4.140530] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Feb  8 15:28:30 sean-desktop kernel: [    4.140586] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  8 15:28:30 sean-desktop kernel: [    4.140594] e1000e 0000:00:19.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [    4.140680] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
Feb  8 15:28:30 sean-desktop kernel: [    4.169963] ohci1394 0000:05:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  8 15:28:30 sean-desktop kernel: [    4.220689] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[d0008000-d00087ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
Feb  8 15:28:30 sean-desktop kernel: [    4.316022] usb 2-2: new high speed USB device using ehci_hcd and address 2
Feb  8 15:28:30 sean-desktop kernel: [    4.366390] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:c0:6c:42:c9
Feb  8 15:28:30 sean-desktop kernel: [    4.366392] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Feb  8 15:28:30 sean-desktop kernel: [    4.366414] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: ffffff-0ff
Feb  8 15:28:30 sean-desktop kernel: [    4.449031] usb 2-2: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    4.452323] Initializing USB Mass Storage driver...
Feb  8 15:28:30 sean-desktop kernel: [    4.452416] scsi6 : SCSI emulation for USB Mass Storage devices
Feb  8 15:28:30 sean-desktop kernel: [    4.452474] usb-storage: device found at 2
Feb  8 15:28:30 sean-desktop kernel: [    4.452475] usb-storage: waiting for device to settle before scanning
Feb  8 15:28:30 sean-desktop kernel: [    4.452481] usbcore: registered new interface driver usb-storage
Feb  8 15:28:30 sean-desktop kernel: [    4.452483] USB Mass Storage support registered.
Feb  8 15:28:30 sean-desktop kernel: [    4.750653] PM: Starting manual resume from disk
Feb  8 15:28:30 sean-desktop kernel: [    4.750656] PM: Resume from partition 8:8
Feb  8 15:28:30 sean-desktop kernel: [    4.750657] PM: Checking hibernation image.
Feb  8 15:28:30 sean-desktop kernel: [    4.750826] PM: Resume from disk failed.
Feb  8 15:28:30 sean-desktop kernel: [    4.752979] EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  8 15:28:30 sean-desktop kernel: [    4.752981] EXT3-fs: write access will be enabled during recovery.
Feb  8 15:28:30 sean-desktop kernel: [    4.856012] usb 6-1: new low speed USB device using uhci_hcd and address 2
Feb  8 15:28:30 sean-desktop kernel: [    5.036912] usb 6-1: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    5.043315] usbcore: registered new interface driver hiddev
Feb  8 15:28:30 sean-desktop kernel: [    5.058104] input: NOVATEK Kensington U+P Keyboard as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input3
Feb  8 15:28:30 sean-desktop kernel: [    5.084077] generic-usb 0003:047D:2043.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK Kensington U+P Keyboard] on usb-0000:00:1d.1-1/input0
Feb  8 15:28:30 sean-desktop kernel: [    5.114927] input: NOVATEK Kensington U+P Keyboard as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input4
Feb  8 15:28:30 sean-desktop kernel: [    5.140077] generic-usb 0003:047D:2043.0002: input,hidraw1: USB HID v1.10 Device [NOVATEK Kensington U+P Keyboard] on usb-0000:00:1d.1-1/input1
Feb  8 15:28:30 sean-desktop kernel: [    5.140097] usbcore: registered new interface driver usbhid
Feb  8 15:28:30 sean-desktop kernel: [    5.140100] usbhid: v2.6:USB HID core driver
Feb  8 15:28:30 sean-desktop kernel: [    5.276020] usb 6-2: new low speed USB device using uhci_hcd and address 3
Feb  8 15:28:30 sean-desktop kernel: [    5.452923] usb 6-2: configuration #1 chosen from 1 choice
Feb  8 15:28:30 sean-desktop kernel: [    5.470093] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input5
Feb  8 15:28:30 sean-desktop kernel: [    5.492049] generic-usb 0003:046D:C01B.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
Feb  8 15:28:30 sean-desktop kernel: [    5.500132] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270002240b61]
Feb  8 15:28:30 sean-desktop kernel: [    5.798916] kjournald starting.  Commit interval 5 seconds
Feb  8 15:28:30 sean-desktop kernel: [    5.798929] EXT3-fs: recovery complete.
Feb  8 15:28:30 sean-desktop kernel: [    5.799329] EXT3-fs: mounted filesystem with ordered data mode.
Feb  8 15:28:30 sean-desktop kernel: [    9.448170] usb-storage: device scan complete
Feb  8 15:28:30 sean-desktop kernel: [    9.448628] scsi 6:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
Feb  8 15:28:30 sean-desktop kernel: [    9.449486] sd 6:0:0:0: [sdb] 7856127 512-byte hardware sectors: (4.02 GB/3.74 GiB)
Feb  8 15:28:30 sean-desktop kernel: [    9.449985] sd 6:0:0:0: [sdb] Write Protect is off
Feb  8 15:28:30 sean-desktop kernel: [    9.449987] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
Feb  8 15:28:30 sean-desktop kernel: [    9.449989] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Feb  8 15:28:30 sean-desktop kernel: [    9.451110] sd 6:0:0:0: [sdb] 7856127 512-byte hardware sectors: (4.02 GB/3.74 GiB)
Feb  8 15:28:30 sean-desktop kernel: [    9.451609] sd 6:0:0:0: [sdb] Write Protect is off
Feb  8 15:28:30 sean-desktop kernel: [    9.451611] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
Feb  8 15:28:30 sean-desktop kernel: [    9.451613] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Feb  8 15:28:30 sean-desktop kernel: [    9.451615]  sdb: sdb1
Feb  8 15:28:30 sean-desktop kernel: [    9.452537] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Feb  8 15:28:30 sean-desktop kernel: [    9.452593] sd 6:0:0:0: Attached scsi generic sg2 type 0
Feb  8 15:28:30 sean-desktop kernel: [   11.232801] udev: starting version 141
Feb  8 15:28:30 sean-desktop kernel: [   11.604661] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb  8 15:28:30 sean-desktop kernel: [   11.618575] [fglrx] Maximum main memory to use for locked dma buffers: 2837 MBytes.
Feb  8 15:28:30 sean-desktop kernel: [   11.618707] [fglrx]   vendor: 1002 device: 954f count: 1
Feb  8 15:28:30 sean-desktop kernel: [   11.618955] [fglrx] ioport: bar 4, base 0x2000, size: 0x100
Feb  8 15:28:30 sean-desktop kernel: [   11.618965] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:28:30 sean-desktop kernel: [   11.618969] pci 0000:01:00.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [   11.620819] [fglrx] Driver built-in PAT support is enabled successfully
Feb  8 15:28:30 sean-desktop kernel: [   11.620846] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
Feb  8 15:28:30 sean-desktop kernel: [   11.623026] input: PC Speaker as /devices/platform/pcspkr/input/input6
Feb  8 15:28:30 sean-desktop kernel: [   12.089657] iTCO_vendor_support: vendor-support=0
Feb  8 15:28:30 sean-desktop kernel: [   12.113085] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Feb  8 15:28:30 sean-desktop kernel: [   12.113210] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
Feb  8 15:28:30 sean-desktop kernel: [   12.113275] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Feb  8 15:28:30 sean-desktop kernel: [   12.160054] cfg80211: Calling CRDA to update world regulatory domain
Feb  8 15:28:30 sean-desktop kernel: [   12.226962] cfg80211: World regulatory domain updated:
Feb  8 15:28:30 sean-desktop kernel: [   12.226964] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb  8 15:28:30 sean-desktop kernel: [   12.226966] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:28:30 sean-desktop kernel: [   12.226967] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:28:30 sean-desktop kernel: [   12.226969] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:28:30 sean-desktop kernel: [   12.226970] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:28:30 sean-desktop kernel: [   12.226971] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:28:30 sean-desktop kernel: [   12.356666] rt61pci 0000:05:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb  8 15:28:30 sean-desktop kernel: [   12.364116] phy0: Selected rate control algorithm 'pid'
Feb  8 15:28:30 sean-desktop kernel: [   12.416210] Registered led device: rt61pci-phy0:radio
Feb  8 15:28:30 sean-desktop kernel: [   12.416236] Registered led device: rt61pci-phy0:assoc
Feb  8 15:28:30 sean-desktop kernel: [   12.449847] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Feb  8 15:28:30 sean-desktop kernel: [   12.449903] HDA Intel 0000:00:1b.0: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [   12.481912] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Feb  8 15:28:30 sean-desktop kernel: [   12.515084] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  8 15:28:30 sean-desktop kernel: [   12.515133] HDA Intel 0000:01:00.1: setting latency timer to 64
Feb  8 15:28:30 sean-desktop kernel: [   12.779326] lp: driver loaded but no devices found
Feb  8 15:28:30 sean-desktop kernel: [   12.889575] Adding 2216928k swap on /dev/sda8.  Priority:-1 extents:1 across:2216928k
Feb  8 15:28:30 sean-desktop kernel: [   13.416131] EXT3 FS on sda7, internal journal
Feb  8 15:28:30 sean-desktop kernel: [   14.197299] type=1505 audit(1265671709.673:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2213
Feb  8 15:28:30 sean-desktop kernel: [   14.224330] type=1505 audit(1265671709.698:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2217
Feb  8 15:28:30 sean-desktop kernel: [   14.224416] type=1505 audit(1265671709.698:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2217
Feb  8 15:28:30 sean-desktop kernel: [   14.224446] type=1505 audit(1265671709.698:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2217
Feb  8 15:28:30 sean-desktop kernel: [   14.224471] type=1505 audit(1265671709.698:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2217
Feb  8 15:28:30 sean-desktop kernel: [   14.301340] type=1505 audit(1265671709.778:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2222
Feb  8 15:28:30 sean-desktop kernel: [   14.301494] type=1505 audit(1265671709.778:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2222
Feb  8 15:28:30 sean-desktop kernel: [   14.319065] type=1505 audit(1265671709.794:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2226
Feb  8 15:28:32 sean-desktop acpid: client connected from 2886[111:122] 
Feb  8 15:28:32 sean-desktop bluetoothd[2913]: Bluetooth daemon
Feb  8 15:28:32 sean-desktop bluetoothd[2913]: Starting SDP server
Feb  8 15:28:32 sean-desktop bluetoothd[2913]: Starting experimental netlink support
Feb  8 15:28:32 sean-desktop bluetoothd[2913]: Failed to find Bluetooth netlink family
Feb  8 15:28:32 sean-desktop bluetoothd[2913]: Registered interface org.bluez.Service on path /org/bluez/2913/any
Feb  8 15:28:32 sean-desktop kernel: [   16.685042] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb  8 15:28:32 sean-desktop kernel: [   16.685045] Bluetooth: BNEP filters: protocol multicast
Feb  8 15:28:32 sean-desktop bluetoothd[2913]: bridge pan0 created
Feb  8 15:28:32 sean-desktop kernel: [   16.701891] Bridge firewalling registered
Feb  8 15:28:33 sean-desktop acpid: client connected from 2958[0:0] 
Feb  8 15:28:33 sean-desktop atieventsd[2979]: ATI External Events Daemon started... 
Feb  8 15:28:33 sean-desktop atieventsd[2979]: Event daemon control socket created 
Feb  8 15:28:33 sean-desktop acpid: client connected from 2979[0:0] 
Feb  8 15:28:33 sean-desktop atieventsd[2979]: acpid connection established 
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  starting... 
Feb  8 15:28:33 sean-desktop avahi-daemon[3030]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Feb  8 15:28:33 sean-desktop avahi-daemon[3030]: Successfully dropped root privileges.
Feb  8 15:28:33 sean-desktop avahi-daemon[3030]: avahi-daemon 0.6.23 starting up.
Feb  8 15:28:33 sean-desktop avahi-daemon[3030]: Successfully called chroot().
Feb  8 15:28:33 sean-desktop avahi-daemon[3030]: Successfully dropped remaining capabilities.
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000e') 
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_c0_6c_42_c9 
Feb  8 15:28:33 sean-desktop avahi-daemon[3030]: No service file found in /etc/avahi/services.
Feb  8 15:28:33 sean-desktop avahi-daemon[3030]: Network interface enumeration completed.
Feb  8 15:28:33 sean-desktop avahi-daemon[3030]: Registering HINFO record with values 'X86_64'/'LINUX'.
Feb  8 15:28:33 sean-desktop avahi-daemon[3030]: Server startup complete. Host name is sean-desktop.local. Local service cookie is 828293207.
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt61pci') 
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_23_69_e4_98_0d 
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  Trying to start the supplicant... 
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  Trying to start the system settings daemon... 
Feb  8 15:28:33 sean-desktop kernel: [   18.442570] ppdev: user-space parallel port driver
Feb  8 15:28:33 sean-desktop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
Feb  8 15:28:34 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: init!
Feb  8 15:28:34 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Feb  8 15:28:34 sean-desktop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Feb  8 15:28:34 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_c0_6c_42_c9, iface: eth0): not well known
Feb  8 15:28:34 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_23_69_e4_98_0d, iface: wlan0): not well known
Feb  8 15:28:34 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Feb  8 15:28:34 sean-desktop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb  8 15:28:34 sean-desktop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb  8 15:28:34 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: (19329488) ... get_connections.
Feb  8 15:28:34 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: (19329488) ... get_connections (managed=false): return empty list.
Feb  8 15:28:34 sean-desktop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Feb  8 15:28:34 sean-desktop anacron[3149]: Anacron 2.3 started on 2010-02-08
Feb  8 15:28:34 sean-desktop anacron[3149]: Normal exit (0 jobs run)
Feb  8 15:28:34 sean-desktop /usr/sbin/cron[3192]: (CRON) INFO (pidfile fd = 3)
Feb  8 15:28:34 sean-desktop /usr/sbin/cron[3193]: (CRON) STARTUP (fork ok)
Feb  8 15:28:34 sean-desktop /usr/sbin/cron[3193]: (CRON) INFO (Running @reboot jobs)
Feb  8 15:28:34 sean-desktop kernel: [   19.458309] fglrx_pci 0000:01:00.0: irq 2298 for MSI/MSI-X
Feb  8 15:28:34 sean-desktop kernel: [   19.469888] [fglrx] Firegl kernel thread PID: 3281
Feb  8 15:28:34 sean-desktop kernel: [   19.476134] [fglrx] Gart USWC size:1427 M.
Feb  8 15:28:34 sean-desktop kernel: [   19.476136] [fglrx] Gart cacheable size:60 M.
Feb  8 15:28:34 sean-desktop kernel: [   19.476140] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Feb  8 15:28:34 sean-desktop kernel: [   19.476143] [fglrx] Reserved FB block: Unshared offset:fd0d000, size:2f3000 
Feb  8 15:28:34 sean-desktop kernel: [   19.476145] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (eth0): bringing up device. 
Feb  8 15:28:38 sean-desktop nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_c0_6c_42_c9
Feb  8 15:28:38 sean-desktop kernel: [   22.652685] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (eth0): preparing device. 
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (wlan0): bringing up device. 
Feb  8 15:28:38 sean-desktop kernel: [   22.708537] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
Feb  8 15:28:38 sean-desktop kernel: [   22.709427] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  8 15:28:38 sean-desktop kernel: [   22.710069] rt61pci 0000:05:03.0: firmware: requesting rt2561s.bin
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (wlan0): preparing device. 
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Feb  8 15:28:38 sean-desktop kernel: [   22.810397] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  8 15:28:38 sean-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
Feb  8 15:28:39 sean-desktop kernel: [   24.256543] wlan0: authenticate with AP 00:09:5b:eb:3e:5c
Feb  8 15:28:39 sean-desktop kernel: [   24.258038] wlan0: authenticated
Feb  8 15:28:39 sean-desktop kernel: [   24.258043] wlan0: associate with AP 00:09:5b:eb:3e:5c
Feb  8 15:28:39 sean-desktop kernel: [   24.260359] wlan0: RX AssocResp from 00:09:5b:eb:3e:5c (capab=0x421 status=0 aid=2)
Feb  8 15:28:39 sean-desktop kernel: [   24.260362] wlan0: associated
Feb  8 15:28:39 sean-desktop kernel: [   24.260495] wlan0: disassociating by local choice (reason=3)
Feb  8 15:29:08 sean-desktop console-kit-daemon[2748]: WARNING: Couldn't read /proc/2747/environ: Failed to open file '/proc/2747/environ': No such file or directory 
Feb  8 15:29:14 sean-desktop pulseaudio[3510]: module-x11-xsmp.c: X11 session manager not running.
Feb  8 15:29:14 sean-desktop pulseaudio[3510]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 2WIRE932' 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 2WIRE932' has security, but secrets are required. 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Feb  8 15:29:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 2WIRE932' has security, and secrets exist.  No new secrets needed. 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Config: added 'ssid' value '2WIRE932' 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Feb  8 15:29:16 sean-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Feb  8 15:29:16 sean-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  Config: set interface ap_scan to 1 
Feb  8 15:29:16 sean-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning 
Feb  8 15:29:17 sean-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Feb  8 15:29:17 sean-desktop hald: mounted /dev/sdb1 on behalf of uid 1000
Feb  8 15:29:18 sean-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Feb  8 15:29:18 sean-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed 
Feb  8 15:29:18 sean-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '2WIRE932'. 
Feb  8 15:29:18 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb  8 15:29:18 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Feb  8 15:29:18 sean-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Feb  8 15:29:18 sean-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Feb  8 15:29:18 sean-desktop kernel: [   63.497559] wlan0: authenticate with AP 00:22:a4:5f:d6:19
Feb  8 15:29:18 sean-desktop kernel: [   63.498786] wlan0: authenticated
Feb  8 15:29:18 sean-desktop kernel: [   63.498789] wlan0: associate with AP 00:22:a4:5f:d6:19
Feb  8 15:29:18 sean-desktop kernel: [   63.500747] wlan0: RX AssocResp from 00:22:a4:5f:d6:19 (capab=0x431 status=0 aid=2)
Feb  8 15:29:18 sean-desktop kernel: [   63.500750] wlan0: associated
Feb  8 15:29:18 sean-desktop kernel: [   63.502214] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb  8 15:29:19 sean-desktop NetworkManager: <info>  dhclient started with pid 3714 
Feb  8 15:29:19 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Feb  8 15:29:19 sean-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  8 15:29:19 sean-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  8 15:29:19 sean-desktop dhclient: All rights reserved.
Feb  8 15:29:19 sean-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  8 15:29:19 sean-desktop dhclient: 
Feb  8 15:29:19 sean-desktop dhclient: wmaster0: unknown hardware address type 801
Feb  8 15:29:19 sean-desktop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Feb  8 15:29:19 sean-desktop dhclient: wmaster0: unknown hardware address type 801
Feb  8 15:29:19 sean-desktop dhclient: Listening on LPF/wlan0/00:23:69:e4:98:0d
Feb  8 15:29:19 sean-desktop dhclient: Sending on   LPF/wlan0/00:23:69:e4:98:0d
Feb  8 15:29:19 sean-desktop dhclient: Sending on   Socket/fallback
Feb  8 15:29:20 sean-desktop avahi-daemon[3030]: Registering new address record for fe80::223:69ff:fee4:980d on wlan0.*.
Feb  8 15:29:22 sean-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Feb  8 15:29:22 sean-desktop dhclient: DHCPOFFER of 192.168.1.105 from 192.168.1.254
Feb  8 15:29:22 sean-desktop dhclient: DHCPREQUEST of 192.168.1.105 on wlan0 to 255.255.255.255 port 67
Feb  8 15:29:23 sean-desktop dhclient: DHCPACK of 192.168.1.105 from 192.168.1.254
Feb  8 15:29:23 sean-desktop dhclient: bound to 192.168.1.105 -- renewal in 37742 seconds.
Feb  8 15:29:23 sean-desktop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>    address 192.168.1.105 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>    gateway 192.168.1.254 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>    nameserver '192.168.1.254' 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>    domain name 'gateway.2wire.net' 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Feb  8 15:29:23 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Feb  8 15:29:23 sean-desktop avahi-daemon[3030]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.105.
Feb  8 15:29:23 sean-desktop avahi-daemon[3030]: New relevant interface wlan0.IPv4 for mDNS.
Feb  8 15:29:23 sean-desktop avahi-daemon[3030]: Registering new address record for 192.168.1.105 on wlan0.IPv4.
Feb  8 15:29:24 sean-desktop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Feb  8 15:29:24 sean-desktop NetworkManager: <info>  Policy set 'Auto 2WIRE932' (wlan0) as default for routing and DNS. 
Feb  8 15:29:24 sean-desktop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Feb  8 15:29:24 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb  8 15:29:26 sean-desktop ntpdate[3791]: adjust time server 91.189.94.4 offset 0.189208 sec
Feb  8 15:29:29 sean-desktop kernel: [   74.096047] wlan0: no IPv6 routers present
Feb  8 15:30:01 sean-desktop /USR/SBIN/CRON[3840]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb  8 15:34:11 sean-desktop console-kit-daemon[2748]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Feb  8 15:34:11 sean-desktop last message repeated 6 times
Feb  8 15:34:11 sean-desktop init: tty5 main process (2365) killed by TERM signal
Feb  8 15:34:11 sean-desktop init: tty6 main process (2372) killed by TERM signal
Feb  8 15:34:11 sean-desktop init: tty1 main process (3302) killed by TERM signal
Feb  8 15:34:11 sean-desktop init: tty3 main process (2371) killed by TERM signal
Feb  8 15:34:11 sean-desktop init: tty2 main process (2370) killed by TERM signal
Feb  8 15:34:11 sean-desktop init: tty4 main process (2364) killed by TERM signal
Feb  8 15:34:11 sean-desktop console-kit-daemon[2748]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Feb  8 15:34:11 sean-desktop console-kit-daemon[2748]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Feb  8 15:34:12 sean-desktop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Feb  8 15:34:12 sean-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
Feb  8 15:34:12 sean-desktop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 3714 
Feb  8 15:34:12 sean-desktop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Feb  8 15:34:12 sean-desktop kernel: [  356.717562] wlan0: authenticate with AP 00:22:a4:5f:d6:19
Feb  8 15:34:12 sean-desktop kernel: [  356.718745] wlan0: authenticated
Feb  8 15:34:12 sean-desktop kernel: [  356.718747] wlan0: associate with AP 00:22:a4:5f:d6:19
Feb  8 15:34:12 sean-desktop avahi-daemon[3030]: Withdrawing address record for 192.168.1.105 on wlan0.
Feb  8 15:34:12 sean-desktop avahi-daemon[3030]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.105.
Feb  8 15:34:12 sean-desktop kernel: [  356.720308] wlan0: disassociating by local choice (reason=3)
Feb  8 15:34:12 sean-desktop kernel: [  356.720550] wlan0: RX AssocResp from 00:22:a4:5f:d6:19 (capab=0x431 status=0 aid=2)
Feb  8 15:34:12 sean-desktop kernel: [  356.720552] wlan0: associated
Feb  8 15:34:12 sean-desktop kernel: [  356.721387] wlan0: disassociating by local choice (reason=3)
Feb  8 15:34:12 sean-desktop avahi-daemon[3030]: Interface wlan0.IPv4 no longer relevant for mDNS.
Feb  8 15:34:15 sean-desktop bluetoothd[2913]: bridge pan0 removed
Feb  8 15:34:15 sean-desktop bluetoothd[2913]: Stopping SDP server
Feb  8 15:34:15 sean-desktop bluetoothd[2913]: Exit
Feb  8 15:34:16 sean-desktop exiting on signal 15
Feb  8 15:34:49 sean-desktop syslogd 1.5.0#5ubuntu3: restart.
Feb  8 15:34:49 sean-desktop kernel: Inspecting /boot/System.map-2.6.28-18-generic
Feb  8 15:34:49 sean-desktop kernel: Cannot find map file.
Feb  8 15:34:49 sean-desktop kernel: Loaded 63294 symbols from 154 modules.
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Linux version 2.6.28-18-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #59-Ubuntu SMP Thu Jan 28 01:40:19 UTC 2010 (Ubuntu 2.6.28-18.59-generic)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Command line: root=UUID=af5e596c-35fa-4804-8cfc-82dcdd6e391a ro quiet splash 
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] KERNEL supported cpus:
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   Intel GenuineIntel
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   AMD AuthenticAMD
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   Centaur CentaurHauls
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfd43000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfd43000 - 00000000bfd4f000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfd4f000 - 00000000bfe2f000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfe2f000 - 00000000bfee8000 (ACPI NVS)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfee8000 - 00000000bfeeb000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfeeb000 - 00000000bfef0000 (ACPI data)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bfef1000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfef1000 - 00000000bfeff000 (ACPI data)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] DMI 2.4 present.
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] last_pfn = 0xbff00 max_arch_pfn = 0x3ffffffff
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Scanning 2 areas for low memory corruption
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] modified physical RAM map:
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 0000000000010000 - 0000000000082000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 000000000008f000 - 00000000000a0000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000bfd43000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000bfd43000 - 00000000bfd4f000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000bfd4f000 - 00000000bfe2f000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000bfe2f000 - 00000000bfee8000 (ACPI NVS)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000bfee8000 - 00000000bfeeb000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000bfeeb000 - 00000000bfef0000 (ACPI data)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000bfef0000 - 00000000bfef1000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000bfef1000 - 00000000bfeff000 (ACPI data)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000bfeff000 - 00000000bff00000 (usable)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000bff00000 - 00000000c0000000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bff00000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  0000000000 - 00bfe00000 page 2M
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  00bfe00000 - 00bff00000 page 4k
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] kernel direct mapping tables up to bff00000 @ 10000-15000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] last_map_addr: bff00000 end: bff00000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] RAMDISK: 37857000 - 37fef229
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: RSDT BFEFD038, 0050 (r1 INTEL  ECG3510M       73       1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: FACP BFEFC000, 0074 (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: DSDT BFEF6000, 5BEB (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: FACS BFE96000, 0040
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: APIC BFEF5000, 0078 (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: WDDT BFEF4000, 0040 (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: MCFG BFEF3000, 003C (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: ASF! BFEF2000, 00A6 (r32 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: HPET BFEF1000, 0038 (r1 INTEL  ECG3510M       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEEF000, 020C (r1 INTEL     CpuPm       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEEE000, 0175 (r1 INTEL   Cpu0Ist       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEED000, 0175 (r1 INTEL   Cpu1Ist       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEEC000, 0175 (r1 INTEL   Cpu2Ist       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: SSDT BFEEB000, 0175 (r1 INTEL   Cpu3Ist       73 MSFT  1000013)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] (6 early reservations) ==> bootmem [0000000000 - 00bff00000]
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   #2 [0000200000 - 0000b7cbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7cbb0]
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   #3 [0037857000 - 0037fef229]          RAMDISK ==> [0037857000 - 0037fef229]
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   #5 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000fe200] 000fe200
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]  [ffffe20000000000-ffffe200029fffff] PMD -> [ffff880001200000-ffff880003bfffff] on node 0
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Zone PFN ranges:
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Movable zone start PFN for each node
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] early_node_map[8] active PFN ranges
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x00000008
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x00000082
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000bfd43
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]     0: 0x000bfd4f -> 0x000bfe2f
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]     0: 0x000bfee8 -> 0x000bfeeb
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]     0: 0x000bfef0 -> 0x000bfef1
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]     0: 0x000bfeff -> 0x000bff00
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] On node 0 totalpages: 785821
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   DMA zone: 2532 pages reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   DMA zone: 1369 pages, LIFO batch:0
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   DMA32 zone: 10693 pages used for memmap
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   DMA32 zone: 771171 pages, LIFO batch:31
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Feb  8 15:34:49 sean-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000082000 - 000000000008f000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfd43000 - 00000000bfd4f000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfe2f000 - 00000000bfee8000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfeeb000 - 00000000bfef0000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfef1000 - 00000000bfeff000
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ff00000)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 772540
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Kernel command line: root=UUID=af5e596c-35fa-4804-8cfc-82dcdd6e391a ro quiet splash 
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Initializing CPU#0
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Feb  8 15:34:49 sean-desktop kernel: [    0.000000] Detected 2651.391 MHz processor.
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] console [tty0] enabled
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] allocated 31457280 bytes of page_cgroup
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Checking aperture...
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] No AGP bridge found
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Calgary: detecting Calgary via BIOS EBDA area
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Memory: 3044784k/3144704k available (4750k kernel code, 1420k absent, 97848k reserved, 2523k data, 536k init)
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] hpet clockevent registered
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5302.78 BogoMIPS (lpj=10605564)
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Security Framework initialized
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] SELinux:  Disabled at boot.
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] AppArmor: AppArmor initialized
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Mount-cache hash table entries: 256
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Initializing cgroup subsys ns
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Initializing cgroup subsys memory
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Initializing cgroup subsys freezer
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: Processor Core ID: 0
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] using mwait in idle threads.
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] ACPI: Core revision 20080926
Feb  8 15:34:49 sean-desktop kernel: [    0.004392] ACPI: Checking initramfs for custom DSDT
Feb  8 15:34:49 sean-desktop kernel: [    0.256041] Setting APIC routing to flat
Feb  8 15:34:49 sean-desktop kernel: [    0.256393] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb  8 15:34:49 sean-desktop kernel: [    0.296844] CPU0: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Feb  8 15:34:49 sean-desktop kernel: [    0.300001] Booting processor 1 APIC 0x2 ip 0x6000
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Initializing CPU#1
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 5421.04 BogoMIPS (lpj=10842084)
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: Processor Core ID: 2
Feb  8 15:34:49 sean-desktop kernel: [    0.384674] CPU1: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Feb  8 15:34:49 sean-desktop kernel: [    0.384691] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Feb  8 15:34:49 sean-desktop kernel: [    0.388078] Booting processor 2 APIC 0x1 ip 0x6000
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Initializing CPU#2
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 5302.88 BogoMIPS (lpj=10605760)
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: Processor Core ID: 1
Feb  8 15:34:49 sean-desktop kernel: [    0.476511] CPU2: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Feb  8 15:34:49 sean-desktop kernel: [    0.476528] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Feb  8 15:34:49 sean-desktop kernel: [    0.480114] Booting processor 3 APIC 0x3 ip 0x6000
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Initializing CPU#3
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 5302.86 BogoMIPS (lpj=10605735)
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Feb  8 15:34:49 sean-desktop kernel: [    0.004000] CPU: Processor Core ID: 3
Feb  8 15:34:49 sean-desktop kernel: [    0.568682] CPU3: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Feb  8 15:34:49 sean-desktop kernel: [    0.568698] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Feb  8 15:34:49 sean-desktop kernel: [    0.572028] Brought up 4 CPUs
Feb  8 15:34:49 sean-desktop kernel: [    0.572030] Total of 4 processors activated (21329.57 BogoMIPS).
Feb  8 15:34:49 sean-desktop kernel: [    0.572074] CPU0 attaching sched-domain:
Feb  8 15:34:49 sean-desktop kernel: [    0.572076]  domain 0: span 0,2 level MC
Feb  8 15:34:49 sean-desktop kernel: [    0.572077]   groups: 0 2
Feb  8 15:34:49 sean-desktop kernel: [    0.572080]   domain 1: span 0-3 level CPU
Feb  8 15:34:49 sean-desktop kernel: [    0.572081]    groups: 0,2 1,3
Feb  8 15:34:49 sean-desktop kernel: [    0.572085] CPU1 attaching sched-domain:
Feb  8 15:34:49 sean-desktop kernel: [    0.572086]  domain 0: span 1,3 level MC
Feb  8 15:34:49 sean-desktop kernel: [    0.572087]   groups: 1 3
Feb  8 15:34:49 sean-desktop kernel: [    0.572089]   domain 1: span 0-3 level CPU
Feb  8 15:34:49 sean-desktop kernel: [    0.572090]    groups: 1,3 0,2
Feb  8 15:34:49 sean-desktop kernel: [    0.572093] CPU2 attaching sched-domain:
Feb  8 15:34:49 sean-desktop kernel: [    0.572094]  domain 0: span 0,2 level MC
Feb  8 15:34:49 sean-desktop kernel: [    0.572095]   groups: 2 0
Feb  8 15:34:49 sean-desktop kernel: [    0.572097]   domain 1: span 0-3 level CPU
Feb  8 15:34:49 sean-desktop kernel: [    0.572098]    groups: 0,2 1,3
Feb  8 15:34:49 sean-desktop kernel: [    0.572101] CPU3 attaching sched-domain:
Feb  8 15:34:49 sean-desktop kernel: [    0.572102]  domain 0: span 1,3 level MC
Feb  8 15:34:49 sean-desktop kernel: [    0.572103]   groups: 3 1
Feb  8 15:34:49 sean-desktop kernel: [    0.572105]   domain 1: span 0-3 level CPU
Feb  8 15:34:49 sean-desktop kernel: [    0.572106]    groups: 1,3 0,2
Feb  8 15:34:49 sean-desktop kernel: [    0.572190] net_namespace: 1400 bytes
Feb  8 15:34:49 sean-desktop kernel: [    0.572190] Booting paravirtualized kernel on bare hardware
Feb  8 15:34:49 sean-desktop kernel: [    0.572273] Time: 15:34:36  Date: 02/08/10
Feb  8 15:34:49 sean-desktop kernel: [    0.572273] regulator: core version 0.5
Feb  8 15:34:49 sean-desktop kernel: [    0.572273] NET: Registered protocol family 16
Feb  8 15:34:49 sean-desktop kernel: [    0.572273] ACPI: bus type pci registered
Feb  8 15:34:49 sean-desktop kernel: [    0.572273] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
Feb  8 15:34:49 sean-desktop kernel: [    0.572273] PCI: Not using MMCONFIG.
Feb  8 15:34:49 sean-desktop kernel: [    0.572273] PCI: Using configuration type 1 for base access
Feb  8 15:34:49 sean-desktop kernel: [    0.572715] ACPI: EC: Look up EC in DSDT
Feb  8 15:34:49 sean-desktop kernel: [    0.577610] ACPI: Interpreter enabled
Feb  8 15:34:49 sean-desktop kernel: [    0.577612] ACPI: (supports S0 S1 S3 S4 S5)
Feb  8 15:34:49 sean-desktop kernel: [    0.577627] ACPI: Using IOAPIC for interrupt routing
Feb  8 15:34:49 sean-desktop kernel: [    0.577661] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
Feb  8 15:34:49 sean-desktop kernel: [    0.578290] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
Feb  8 15:34:49 sean-desktop kernel: [    0.582610] PCI: Using MMCONFIG at f0000000 - f7ffffff
Feb  8 15:34:49 sean-desktop kernel: [    0.585947] ACPI: No dock devices found.
Feb  8 15:34:49 sean-desktop kernel: [    0.585955] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  8 15:34:49 sean-desktop kernel: [    0.586016] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Feb  8 15:34:49 sean-desktop kernel: [    0.586018] pci 0000:00:01.0: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586062] pci 0000:00:19.0: reg 10 32bit mmio: [0xd0200000-0xd021ffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586066] pci 0000:00:19.0: reg 14 32bit mmio: [0xd0224000-0xd0224fff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586071] pci 0000:00:19.0: reg 18 io port: [0x30c0-0x30df]
Feb  8 15:34:49 sean-desktop kernel: [    0.586090] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Feb  8 15:34:49 sean-desktop kernel: [    0.586092] pci 0000:00:19.0: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586123] pci 0000:00:1a.0: reg 20 io port: [0x30a0-0x30bf]
Feb  8 15:34:49 sean-desktop kernel: [    0.586159] pci 0000:00:1a.1: reg 20 io port: [0x3080-0x309f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586200] pci 0000:00:1a.7: reg 10 32bit mmio: [0xd0225400-0xd02257ff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586231] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Feb  8 15:34:49 sean-desktop kernel: [    0.586234] pci 0000:00:1a.7: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586263] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd0220000-0xd0223fff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586285] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Feb  8 15:34:49 sean-desktop kernel: [    0.586288] pci 0000:00:1b.0: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586322] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Feb  8 15:34:49 sean-desktop kernel: [    0.586324] pci 0000:00:1c.0: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586360] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Feb  8 15:34:49 sean-desktop kernel: [    0.586362] pci 0000:00:1c.1: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586398] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Feb  8 15:34:49 sean-desktop kernel: [    0.586400] pci 0000:00:1c.2: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586437] pci 0000:00:1d.0: reg 20 io port: [0x3060-0x307f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586474] pci 0000:00:1d.1: reg 20 io port: [0x3040-0x305f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586510] pci 0000:00:1d.2: reg 20 io port: [0x3020-0x303f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586551] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0225000-0xd02253ff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586581] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Feb  8 15:34:49 sean-desktop kernel: [    0.586584] pci 0000:00:1d.7: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586674] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Feb  8 15:34:49 sean-desktop kernel: [    0.586677] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
Feb  8 15:34:49 sean-desktop kernel: [    0.586704] pci 0000:00:1f.2: reg 10 io port: [0x3438-0x343f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586708] pci 0000:00:1f.2: reg 14 io port: [0x344c-0x344f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586712] pci 0000:00:1f.2: reg 18 io port: [0x3430-0x3437]
Feb  8 15:34:49 sean-desktop kernel: [    0.586716] pci 0000:00:1f.2: reg 1c io port: [0x3448-0x344b]
Feb  8 15:34:49 sean-desktop kernel: [    0.586720] pci 0000:00:1f.2: reg 20 io port: [0x3410-0x341f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586724] pci 0000:00:1f.2: reg 24 io port: [0x3400-0x340f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586734] pci 0000:00:1f.2: PME# supported from D3hot
Feb  8 15:34:49 sean-desktop kernel: [    0.586736] pci 0000:00:1f.2: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586750] pci 0000:00:1f.3: reg 10 32bit mmio: [0xd0225800-0xd02258ff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586764] pci 0000:00:1f.3: reg 20 io port: [0x3000-0x301f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586791] pci 0000:00:1f.5: reg 10 io port: [0x3428-0x342f]
Feb  8 15:34:49 sean-desktop kernel: [    0.586795] pci 0000:00:1f.5: reg 14 io port: [0x3444-0x3447]
Feb  8 15:34:49 sean-desktop kernel: [    0.586799] pci 0000:00:1f.5: reg 18 io port: [0x3420-0x3427]
Feb  8 15:34:49 sean-desktop kernel: [    0.586803] pci 0000:00:1f.5: reg 1c io port: [0x3440-0x3443]
Feb  8 15:34:49 sean-desktop kernel: [    0.586807] pci 0000:00:1f.5: reg 20 io port: [0x30f0-0x30ff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586811] pci 0000:00:1f.5: reg 24 io port: [0x30e0-0x30ef]
Feb  8 15:34:49 sean-desktop kernel: [    0.586821] pci 0000:00:1f.5: PME# supported from D3hot
Feb  8 15:34:49 sean-desktop kernel: [    0.586823] pci 0000:00:1f.5: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.586849] pci 0000:01:00.0: reg 10 64bit mmio: [0xc0000000-0xcfffffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586856] pci 0000:01:00.0: reg 18 64bit mmio: [0xd0100000-0xd010ffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586860] pci 0000:01:00.0: reg 20 io port: [0x2000-0x20ff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586867] pci 0000:01:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586872] pci 0000:01:00.0: supports D1 D2
Feb  8 15:34:49 sean-desktop kernel: [    0.586897] pci 0000:01:00.1: reg 10 64bit mmio: [0xd0110000-0xd0113fff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586916] pci 0000:01:00.1: supports D1 D2
Feb  8 15:34:49 sean-desktop kernel: [    0.586950] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586952] pci 0000:00:01.0: bridge 32bit mmio: [0xd0100000-0xd01fffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.586955] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.587069] pci 0000:04:00.0: reg 10 io port: [0x1018-0x101f]
Feb  8 15:34:49 sean-desktop kernel: [    0.587076] pci 0000:04:00.0: reg 14 io port: [0x1024-0x1027]
Feb  8 15:34:49 sean-desktop kernel: [    0.587084] pci 0000:04:00.0: reg 18 io port: [0x1010-0x1017]
Feb  8 15:34:49 sean-desktop kernel: [    0.587091] pci 0000:04:00.0: reg 1c io port: [0x1020-0x1023]
Feb  8 15:34:49 sean-desktop kernel: [    0.587099] pci 0000:04:00.0: reg 20 io port: [0x1000-0x100f]
Feb  8 15:34:49 sean-desktop kernel: [    0.587113] pci 0000:04:00.0: reg 30 32bit mmio: [0xffff0000-0xffffffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.587163] pci 0000:00:1c.2: bridge io port: [0x1000-0x1fff]
Feb  8 15:34:49 sean-desktop kernel: [    0.587198] pci 0000:05:03.0: reg 10 32bit mmio: [0xd0000000-0xd0007fff]
Feb  8 15:34:49 sean-desktop kernel: [    0.587256] pci 0000:05:05.0: reg 10 32bit mmio: [0xd0008000-0xd0008fff]
Feb  8 15:34:49 sean-desktop kernel: [    0.587286] pci 0000:05:05.0: supports D1 D2
Feb  8 15:34:49 sean-desktop kernel: [    0.587288] pci 0000:05:05.0: PME# supported from D0 D1 D2 D3hot
Feb  8 15:34:49 sean-desktop kernel: [    0.587291] pci 0000:05:05.0: PME# disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.587322] pci 0000:00:1e.0: transparent bridge
Feb  8 15:34:49 sean-desktop kernel: [    0.587326] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0000000-0xd00fffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.587345] bus 00 -> node 0
Feb  8 15:34:49 sean-desktop kernel: [    0.587349] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb  8 15:34:49 sean-desktop kernel: [    0.587664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
Feb  8 15:34:49 sean-desktop kernel: [    0.587785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Feb  8 15:34:49 sean-desktop kernel: [    0.587880] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
Feb  8 15:34:49 sean-desktop kernel: [    0.587975] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
Feb  8 15:34:49 sean-desktop kernel: [    0.590990] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 15:34:49 sean-desktop kernel: [    0.591083] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
Feb  8 15:34:49 sean-desktop kernel: [    0.591175] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12)
Feb  8 15:34:49 sean-desktop kernel: [    0.591265] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 15:34:49 sean-desktop kernel: [    0.591356] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12)
Feb  8 15:34:49 sean-desktop kernel: [    0.591447] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 15:34:49 sean-desktop kernel: [    0.591538] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
Feb  8 15:34:49 sean-desktop kernel: [    0.591629] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
Feb  8 15:34:49 sean-desktop kernel: [    0.591808] ACPI: WMI: Mapper loaded
Feb  8 15:34:49 sean-desktop kernel: [    0.591838] SCSI subsystem initialized
Feb  8 15:34:49 sean-desktop kernel: [    0.592018] libata version 3.00 loaded.
Feb  8 15:34:49 sean-desktop kernel: [    0.592031] usbcore: registered new interface driver usbfs
Feb  8 15:34:49 sean-desktop kernel: [    0.592044] usbcore: registered new interface driver hub
Feb  8 15:34:49 sean-desktop kernel: [    0.592056] usbcore: registered new device driver usb
Feb  8 15:34:49 sean-desktop kernel: [    0.592056] PCI: Using ACPI for IRQ routing
Feb  8 15:34:49 sean-desktop kernel: [    0.604010] Bluetooth: Core ver 2.13
Feb  8 15:34:49 sean-desktop kernel: [    0.604024] NET: Registered protocol family 31
Feb  8 15:34:49 sean-desktop kernel: [    0.604024] Bluetooth: HCI device and connection manager initialized
Feb  8 15:34:49 sean-desktop kernel: [    0.604024] Bluetooth: HCI socket layer initialized
Feb  8 15:34:49 sean-desktop kernel: [    0.604024] NET: Registered protocol family 8
Feb  8 15:34:49 sean-desktop kernel: [    0.604024] NET: Registered protocol family 20
Feb  8 15:34:49 sean-desktop kernel: [    0.604031] NetLabel: Initializing
Feb  8 15:34:49 sean-desktop kernel: [    0.604032] NetLabel:  domain hash size = 128
Feb  8 15:34:49 sean-desktop kernel: [    0.604034] NetLabel:  protocols = UNLABELED CIPSOv4
Feb  8 15:34:49 sean-desktop kernel: [    0.604046] NetLabel:  unlabeled traffic allowed by default
Feb  8 15:34:49 sean-desktop kernel: [    0.604075] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Feb  8 15:34:49 sean-desktop kernel: [    0.604079] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Feb  8 15:34:49 sean-desktop kernel: [    0.612060] AppArmor: AppArmor Filesystem Enabled
Feb  8 15:34:49 sean-desktop kernel: [    0.616009] Switched to high resolution mode on CPU 0
Feb  8 15:34:49 sean-desktop kernel: [    0.616561] Switched to high resolution mode on CPU 2
Feb  8 15:34:49 sean-desktop kernel: [    0.616735] Switched to high resolution mode on CPU 1
Feb  8 15:34:49 sean-desktop kernel: [    0.616737] Switched to high resolution mode on CPU 3
Feb  8 15:34:49 sean-desktop kernel: [    0.624009] pnp: PnP ACPI init
Feb  8 15:34:49 sean-desktop kernel: [    0.624017] ACPI: bus type pnp registered
Feb  8 15:34:49 sean-desktop kernel: [    0.625983] pnp: PnP ACPI: found 11 devices
Feb  8 15:34:49 sean-desktop kernel: [    0.625984] ACPI: ACPI bus type pnp unregistered
Feb  8 15:34:49 sean-desktop kernel: [    0.625990] system 00:01: iomem range 0xf0000000-0xf7ffffff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.625992] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.625993] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.625995] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.625996] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.625998] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.626000] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.626001] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.626003] system 00:01: iomem range 0xc0000-0xdffff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.626006] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.626011] system 00:06: ioport range 0x500-0x53f has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.626012] system 00:06: ioport range 0x400-0x47f has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.626014] system 00:06: ioport range 0x360-0x361 has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.626015] system 00:06: ioport range 0x680-0x6ff has been reserved
Feb  8 15:34:49 sean-desktop kernel: [    0.630639] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Feb  8 15:34:49 sean-desktop kernel: [    0.630641] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
Feb  8 15:34:49 sean-desktop kernel: [    0.630644] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
Feb  8 15:34:49 sean-desktop kernel: [    0.630646] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Feb  8 15:34:49 sean-desktop kernel: [    0.630649] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Feb  8 15:34:49 sean-desktop kernel: [    0.630650] pci 0000:00:1c.0:   IO window: disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.630653] pci 0000:00:1c.0:   MEM window: disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.630656] pci 0000:00:1c.0:   PREFETCH window: disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.630660] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Feb  8 15:34:49 sean-desktop kernel: [    0.630661] pci 0000:00:1c.1:   IO window: disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.630664] pci 0000:00:1c.1:   MEM window: disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.630667] pci 0000:00:1c.1:   PREFETCH window: disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.630671] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Feb  8 15:34:49 sean-desktop kernel: [    0.630673] pci 0000:00:1c.2:   IO window: 0x1000-0x1fff
Feb  8 15:34:49 sean-desktop kernel: [    0.630676] pci 0000:00:1c.2:   MEM window: disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.630679] pci 0000:00:1c.2:   PREFETCH window: 0x000000d0300000-0x000000d03fffff
Feb  8 15:34:49 sean-desktop kernel: [    0.630683] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Feb  8 15:34:49 sean-desktop kernel: [    0.630684] pci 0000:00:1e.0:   IO window: disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.630688] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff
Feb  8 15:34:49 sean-desktop kernel: [    0.630690] pci 0000:00:1e.0:   PREFETCH window: disabled
Feb  8 15:34:49 sean-desktop kernel: [    0.630700] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:34:49 sean-desktop kernel: [    0.630703] pci 0000:00:01.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    0.630708] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb  8 15:34:49 sean-desktop kernel: [    0.630711] pci 0000:00:1c.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    0.630715] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:34:49 sean-desktop kernel: [    0.630718] pci 0000:00:1c.1: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    0.630723] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  8 15:34:49 sean-desktop kernel: [    0.630726] pci 0000:00:1c.2: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    0.630731] pci 0000:00:1e.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    0.630733] bus: 00 index 0 io port: [0x00-0xffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630734] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630736] bus: 01 index 0 io port: [0x2000-0x2fff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630737] bus: 01 index 1 mmio: [0xd0100000-0xd01fffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630738] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630740] bus: 01 index 3 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630741] bus: 02 index 0 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630742] bus: 02 index 1 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630743] bus: 02 index 2 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630744] bus: 02 index 3 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630745] bus: 03 index 0 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630746] bus: 03 index 1 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630746] bus: 03 index 2 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630747] bus: 03 index 3 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630749] bus: 04 index 0 io port: [0x1000-0x1fff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630750] bus: 04 index 1 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630751] bus: 04 index 2 mmio: [0xd0300000-0xd03fffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630752] bus: 04 index 3 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630753] bus: 05 index 0 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630754] bus: 05 index 1 mmio: [0xd0000000-0xd00fffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630755] bus: 05 index 2 mmio: [0x0-0x0]
Feb  8 15:34:49 sean-desktop kernel: [    0.630756] bus: 05 index 3 io port: [0x00-0xffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630758] bus: 05 index 4 mmio: [0x000000-0xffffffffffffffff]
Feb  8 15:34:49 sean-desktop kernel: [    0.630764] NET: Registered protocol family 2
Feb  8 15:34:49 sean-desktop kernel: [    0.664050] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Feb  8 15:34:49 sean-desktop kernel: [    0.664461] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Feb  8 15:34:49 sean-desktop kernel: [    0.667227] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb  8 15:34:49 sean-desktop kernel: [    0.668151] TCP: Hash tables configured (established 262144 bind 65536)
Feb  8 15:34:49 sean-desktop kernel: [    0.668154] TCP reno registered
Feb  8 15:34:49 sean-desktop kernel: [    0.680144] NET: Registered protocol family 1
Feb  8 15:34:49 sean-desktop kernel: [    0.680255] checking if image is initramfs... it is
Feb  8 15:34:49 sean-desktop kernel: [    1.187780] Freeing initrd memory: 7776k freed
Feb  8 15:34:49 sean-desktop kernel: [    1.191296] audit: initializing netlink socket (disabled)
Feb  8 15:34:49 sean-desktop kernel: [    1.191314] type=2000 audit(1265643276.188:1): initialized
Feb  8 15:34:49 sean-desktop kernel: [    1.199727] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb  8 15:34:49 sean-desktop kernel: [    1.200919] VFS: Disk quotas dquot_6.5.1
Feb  8 15:34:49 sean-desktop kernel: [    1.200967] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb  8 15:34:49 sean-desktop kernel: [    1.201459] fuse init (API version 7.10)
Feb  8 15:34:49 sean-desktop kernel: [    1.201535] msgmni has been set to 5963
Feb  8 15:34:49 sean-desktop kernel: [    1.201709] alg: No test for stdrng (krng)
Feb  8 15:34:49 sean-desktop kernel: [    1.201723] io scheduler noop registered
Feb  8 15:34:49 sean-desktop kernel: [    1.201725] io scheduler anticipatory registered
Feb  8 15:34:49 sean-desktop kernel: [    1.201726] io scheduler deadline registered
Feb  8 15:34:49 sean-desktop kernel: [    1.201762] io scheduler cfq registered (default)
Feb  8 15:34:49 sean-desktop kernel: [    1.202080] pci 0000:01:00.0: Boot video device
Feb  8 15:34:49 sean-desktop kernel: [    1.203772] pcieport-driver 0000:00:01.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    1.203799] pcieport-driver 0000:00:01.0: found MSI capability
Feb  8 15:34:49 sean-desktop kernel: [    1.203817] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
Feb  8 15:34:49 sean-desktop kernel: [    1.203825] pci_express 0000:00:01.0:pcie00: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.203837] pci_express 0000:00:01.0:pcie03: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.203875] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    1.203902] pcieport-driver 0000:00:1c.0: found MSI capability
Feb  8 15:34:49 sean-desktop kernel: [    1.203922] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
Feb  8 15:34:49 sean-desktop kernel: [    1.203931] pci_express 0000:00:1c.0:pcie00: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.203942] pci_express 0000:00:1c.0:pcie02: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.203954] pci_express 0000:00:1c.0:pcie03: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.204000] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    1.204034] pcieport-driver 0000:00:1c.1: found MSI capability
Feb  8 15:34:49 sean-desktop kernel: [    1.204058] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
Feb  8 15:34:49 sean-desktop kernel: [    1.204070] pci_express 0000:00:1c.1:pcie00: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.204081] pci_express 0000:00:1c.1:pcie02: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.204090] pci_express 0000:00:1c.1:pcie03: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.204148] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    1.204188] pcieport-driver 0000:00:1c.2: found MSI capability
Feb  8 15:34:49 sean-desktop kernel: [    1.204215] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
Feb  8 15:34:49 sean-desktop kernel: [    1.204224] pci_express 0000:00:1c.2:pcie00: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.204235] pci_express 0000:00:1c.2:pcie02: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.204245] pci_express 0000:00:1c.2:pcie03: allocate port service
Feb  8 15:34:49 sean-desktop kernel: [    1.204301] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  8 15:34:49 sean-desktop kernel: [    1.204374] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb  8 15:34:49 sean-desktop kernel: [    1.204496] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Feb  8 15:34:49 sean-desktop kernel: [    1.204499] ACPI: Power Button (FF) [PWRF]
Feb  8 15:34:49 sean-desktop kernel: [    1.204538] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Feb  8 15:34:49 sean-desktop kernel: [    1.204545] ACPI: Sleep Button (CM) [SLPB]
Feb  8 15:34:49 sean-desktop kernel: [    1.204848] processor ACPI_CPU:00: registered as cooling_device0
Feb  8 15:34:49 sean-desktop kernel: [    1.204853] ACPI: Processor [CPU0] (supports 8 throttling states)
Feb  8 15:34:49 sean-desktop kernel: [    1.205009] processor ACPI_CPU:01: registered as cooling_device1
Feb  8 15:34:49 sean-desktop kernel: [    1.205011] ACPI: Processor [CPU1] (supports 8 throttling states)
Feb  8 15:34:49 sean-desktop kernel: [    1.205123] processor ACPI_CPU:02: registered as cooling_device2
Feb  8 15:34:49 sean-desktop kernel: [    1.205127] ACPI: Processor [CPU2] (supports 8 throttling states)
Feb  8 15:34:49 sean-desktop kernel: [    1.205241] processor ACPI_CPU:03: registered as cooling_device3
Feb  8 15:34:49 sean-desktop kernel: [    1.205245] ACPI: Processor [CPU3] (supports 8 throttling states)
Feb  8 15:34:49 sean-desktop kernel: [    1.233623] Linux agpgart interface v0.103
Feb  8 15:34:49 sean-desktop kernel: [    1.233630] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Feb  8 15:34:49 sean-desktop kernel: [    1.233714] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  8 15:34:49 sean-desktop kernel: [    1.234019] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  8 15:34:49 sean-desktop kernel: [    1.234659] brd: module loaded
Feb  8 15:34:49 sean-desktop kernel: [    1.234931] loop: module loaded
Feb  8 15:34:49 sean-desktop kernel: [    1.234987] Fixed MDIO Bus: probed
Feb  8 15:34:49 sean-desktop kernel: [    1.234992] PPP generic driver version 2.4.2
Feb  8 15:34:49 sean-desktop kernel: [    1.235039] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Feb  8 15:34:49 sean-desktop kernel: [    1.235062] Driver 'sd' needs updating - please use bus_type methods
Feb  8 15:34:49 sean-desktop kernel: [    1.235070] Driver 'sr' needs updating - please use bus_type methods
Feb  8 15:34:49 sean-desktop kernel: [    1.235134] ata_piix 0000:00:1f.2: version 2.12
Feb  8 15:34:49 sean-desktop kernel: [    1.235146] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb  8 15:34:49 sean-desktop kernel: [    1.235150] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Feb  8 15:34:49 sean-desktop kernel: [    1.388019] ata_piix 0000:00:1f.2: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    1.388078] scsi0 : ata_piix
Feb  8 15:34:49 sean-desktop kernel: [    1.388155] scsi1 : ata_piix
Feb  8 15:34:49 sean-desktop kernel: [    1.389014] ata1: SATA max UDMA/133 cmd 0x3438 ctl 0x344c bmdma 0x3410 irq 19
Feb  8 15:34:49 sean-desktop kernel: [    1.389019] ata2: SATA max UDMA/133 cmd 0x3430 ctl 0x3448 bmdma 0x3418 irq 19
Feb  8 15:34:49 sean-desktop kernel: [    2.184052] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb  8 15:34:49 sean-desktop kernel: [    2.184061] ata1.01: SATA link down (SStatus 4 SControl 300)
Feb  8 15:34:49 sean-desktop kernel: [    2.222061] ata1.00: ATA-7: WDC WD2500YS-01SHB0, 20.06C06, max UDMA/133
Feb  8 15:34:49 sean-desktop kernel: [    2.222064] ata1.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
Feb  8 15:34:49 sean-desktop kernel: [    2.229045] ata1.00: configured for UDMA/133
Feb  8 15:34:49 sean-desktop kernel: [    2.878561] ata2.00: SATA link down (SStatus 0 SControl 300)
Feb  8 15:34:49 sean-desktop kernel: [    2.878569] ata2.01: SATA link down (SStatus 4 SControl 300)
Feb  8 15:34:49 sean-desktop kernel: [    2.878600] isa bounce pool size: 16 pages
Feb  8 15:34:49 sean-desktop kernel: [    2.878673] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
Feb  8 15:34:49 sean-desktop kernel: [    2.878758] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors: (251 GB/233 GiB)
Feb  8 15:34:49 sean-desktop kernel: [    2.878773] sd 0:0:0:0: [sda] Write Protect is off
Feb  8 15:34:49 sean-desktop kernel: [    2.878775] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb  8 15:34:49 sean-desktop kernel: [    2.878798] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  8 15:34:49 sean-desktop kernel: [    2.878853] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors: (251 GB/233 GiB)
Feb  8 15:34:49 sean-desktop kernel: [    2.878866] sd 0:0:0:0: [sda] Write Protect is off
Feb  8 15:34:49 sean-desktop kernel: [    2.878868] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb  8 15:34:49 sean-desktop kernel: [    2.878890] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  8 15:34:49 sean-desktop kernel: [    2.878893]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
Feb  8 15:34:49 sean-desktop kernel: [    2.932233] sd 0:0:0:0: [sda] Attached SCSI disk
Feb  8 15:34:49 sean-desktop kernel: [    2.932281] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb  8 15:34:49 sean-desktop kernel: [    2.932314] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb  8 15:34:49 sean-desktop kernel: [    2.932317] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Feb  8 15:34:49 sean-desktop kernel: [    2.932355] ata_piix 0000:00:1f.5: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    2.932389] scsi2 : ata_piix
Feb  8 15:34:49 sean-desktop kernel: [    2.932428] scsi3 : ata_piix
Feb  8 15:34:49 sean-desktop kernel: [    2.933100] ata3: SATA max UDMA/133 cmd 0x3428 ctl 0x3444 bmdma 0x30f0 irq 19
Feb  8 15:34:49 sean-desktop kernel: [    2.933103] ata4: SATA max UDMA/133 cmd 0x3420 ctl 0x3440 bmdma 0x30f8 irq 19
Feb  8 15:34:49 sean-desktop kernel: [    3.262508] ata3: SATA link down (SStatus 0 SControl 300)
Feb  8 15:34:49 sean-desktop kernel: [    3.590506] ata4: SATA link down (SStatus 0 SControl 300)
Feb  8 15:34:49 sean-desktop kernel: [    3.590740] pata_jmicron 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  8 15:34:49 sean-desktop kernel: [    3.590763] pata_jmicron 0000:04:00.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    3.590826] scsi4 : pata_jmicron
Feb  8 15:34:49 sean-desktop kernel: [    3.590887] scsi5 : pata_jmicron
Feb  8 15:34:49 sean-desktop kernel: [    3.591378] ata5: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 18
Feb  8 15:34:49 sean-desktop kernel: [    3.591380] ata6: PATA max UDMA/100 cmd 0x1010 ctl 0x1020 bmdma 0x1008 irq 18
Feb  8 15:34:49 sean-desktop kernel: [    3.752493] ata5.00: ATAPI: DVD-ROM BDV316G, VER 0015, max UDMA/66
Feb  8 15:34:49 sean-desktop kernel: [    3.768503] ata5.00: configured for UDMA/66
Feb  8 15:34:49 sean-desktop kernel: [    3.924737] scsi 4:0:0:0: CD-ROM            DVD-16X  DVD-ROM BDV316G  0015 PQ: 0 ANSI: 5
Feb  8 15:34:49 sean-desktop kernel: [    3.929426] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
Feb  8 15:34:49 sean-desktop kernel: [    3.929429] Uniform CD-ROM driver Revision: 3.20
Feb  8 15:34:49 sean-desktop kernel: [    3.929512] sr 4:0:0:0: Attached scsi CD-ROM sr0
Feb  8 15:34:49 sean-desktop kernel: [    3.929544] sr 4:0:0:0: Attached scsi generic sg1 type 5
Feb  8 15:34:49 sean-desktop kernel: [    3.929749] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb  8 15:34:49 sean-desktop kernel: [    3.929763] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  8 15:34:49 sean-desktop kernel: [    3.929787] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    3.929789] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Feb  8 15:34:49 sean-desktop kernel: [    3.929841] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Feb  8 15:34:49 sean-desktop kernel: [    3.933742] ehci_hcd 0000:00:1a.7: debug port 1
Feb  8 15:34:49 sean-desktop kernel: [    3.933746] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Feb  8 15:34:49 sean-desktop kernel: [    3.933750] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xd0225400
Feb  8 15:34:49 sean-desktop kernel: [    3.948008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Feb  8 15:34:49 sean-desktop kernel: [    3.948063] usb usb1: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    3.948090] hub 1-0:1.0: USB hub found
Feb  8 15:34:49 sean-desktop kernel: [    3.948096] hub 1-0:1.0: 4 ports detected
Feb  8 15:34:49 sean-desktop kernel: [    3.948184] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb  8 15:34:49 sean-desktop kernel: [    3.948191] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    3.948193] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb  8 15:34:49 sean-desktop kernel: [    3.948222] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Feb  8 15:34:49 sean-desktop kernel: [    3.952116] ehci_hcd 0000:00:1d.7: debug port 1
Feb  8 15:34:49 sean-desktop kernel: [    3.952120] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Feb  8 15:34:49 sean-desktop kernel: [    3.952129] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0225000
Feb  8 15:34:49 sean-desktop kernel: [    3.968007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Feb  8 15:34:49 sean-desktop kernel: [    3.968062] usb usb2: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    3.968083] hub 2-0:1.0: USB hub found
Feb  8 15:34:49 sean-desktop kernel: [    3.968088] hub 2-0:1.0: 6 ports detected
Feb  8 15:34:49 sean-desktop kernel: [    3.968171] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb  8 15:34:49 sean-desktop kernel: [    3.968180] uhci_hcd: USB Universal Host Controller Interface driver
Feb  8 15:34:49 sean-desktop kernel: [    3.968196] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:34:49 sean-desktop kernel: [    3.968200] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    3.968202] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Feb  8 15:34:49 sean-desktop kernel: [    3.968228] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Feb  8 15:34:49 sean-desktop kernel: [    3.968253] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000030a0
Feb  8 15:34:49 sean-desktop kernel: [    3.968306] usb usb3: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    3.968321] hub 3-0:1.0: USB hub found
Feb  8 15:34:49 sean-desktop kernel: [    3.968325] hub 3-0:1.0: 2 ports detected
Feb  8 15:34:49 sean-desktop kernel: [    3.968381] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Feb  8 15:34:49 sean-desktop kernel: [    3.968385] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    3.968387] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Feb  8 15:34:49 sean-desktop kernel: [    3.968423] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Feb  8 15:34:49 sean-desktop kernel: [    3.968446] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00003080
Feb  8 15:34:49 sean-desktop kernel: [    3.968492] usb usb4: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    3.968510] hub 4-0:1.0: USB hub found
Feb  8 15:34:49 sean-desktop kernel: [    3.968514] hub 4-0:1.0: 2 ports detected
Feb  8 15:34:49 sean-desktop kernel: [    3.968569] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb  8 15:34:49 sean-desktop kernel: [    3.968573] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    3.968575] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb  8 15:34:49 sean-desktop kernel: [    3.968601] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Feb  8 15:34:49 sean-desktop kernel: [    3.968619] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003060
Feb  8 15:34:49 sean-desktop kernel: [    3.968670] usb usb5: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    3.968685] hub 5-0:1.0: USB hub found
Feb  8 15:34:49 sean-desktop kernel: [    3.968689] hub 5-0:1.0: 2 ports detected
Feb  8 15:34:49 sean-desktop kernel: [    3.968744] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Feb  8 15:34:49 sean-desktop kernel: [    3.968748] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    3.968750] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb  8 15:34:49 sean-desktop kernel: [    3.968783] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Feb  8 15:34:49 sean-desktop kernel: [    3.968801] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003040
Feb  8 15:34:49 sean-desktop kernel: [    3.968850] usb usb6: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    3.968865] hub 6-0:1.0: USB hub found
Feb  8 15:34:49 sean-desktop kernel: [    3.968869] hub 6-0:1.0: 2 ports detected
Feb  8 15:34:49 sean-desktop kernel: [    3.968922] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb  8 15:34:49 sean-desktop kernel: [    3.968926] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    3.968928] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb  8 15:34:49 sean-desktop kernel: [    3.968955] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Feb  8 15:34:49 sean-desktop kernel: [    3.968973] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003020
Feb  8 15:34:49 sean-desktop kernel: [    3.969022] usb usb7: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    3.969043] hub 7-0:1.0: USB hub found
Feb  8 15:34:49 sean-desktop kernel: [    3.969046] hub 7-0:1.0: 2 ports detected
Feb  8 15:34:49 sean-desktop kernel: [    3.969139] PNP: No PS/2 controller found. Probing ports directly.
Feb  8 15:34:49 sean-desktop kernel: [    3.971791] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  8 15:34:49 sean-desktop kernel: [    3.971796] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  8 15:34:49 sean-desktop kernel: [    3.980035] mice: PS/2 mouse device common for all mice
Feb  8 15:34:49 sean-desktop kernel: [    4.016062] rtc_cmos 00:03: RTC can wake from S4
Feb  8 15:34:49 sean-desktop kernel: [    4.016097] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Feb  8 15:34:49 sean-desktop kernel: [    4.016118] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Feb  8 15:34:49 sean-desktop kernel: [    4.016172] device-mapper: uevent: version 1.0.3
Feb  8 15:34:49 sean-desktop kernel: [    4.016256] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Feb  8 15:34:49 sean-desktop kernel: [    4.016375] device-mapper: multipath: version 1.0.5 loaded
Feb  8 15:34:49 sean-desktop kernel: [    4.016377] device-mapper: multipath round-robin: version 1.0.0 loaded
Feb  8 15:34:49 sean-desktop kernel: [    4.016509] cpuidle: using governor ladder
Feb  8 15:34:49 sean-desktop kernel: [    4.016511] cpuidle: using governor menu
Feb  8 15:34:49 sean-desktop kernel: [    4.016799] TCP cubic registered
Feb  8 15:34:49 sean-desktop kernel: [    4.016845] NET: Registered protocol family 10
Feb  8 15:34:49 sean-desktop kernel: [    4.017125] lo: Disabled Privacy Extensions
Feb  8 15:34:49 sean-desktop kernel: [    4.017314] NET: Registered protocol family 17
Feb  8 15:34:49 sean-desktop kernel: [    4.017327] Bluetooth: L2CAP ver 2.11
Feb  8 15:34:49 sean-desktop kernel: [    4.017328] Bluetooth: L2CAP socket layer initialized
Feb  8 15:34:49 sean-desktop kernel: [    4.017330] Bluetooth: SCO (Voice Link) ver 0.6
Feb  8 15:34:49 sean-desktop kernel: [    4.017330] Bluetooth: SCO socket layer initialized
Feb  8 15:34:49 sean-desktop kernel: [    4.017361] Bluetooth: RFCOMM socket layer initialized
Feb  8 15:34:49 sean-desktop kernel: [    4.017367] Bluetooth: RFCOMM TTY layer initialized
Feb  8 15:34:49 sean-desktop kernel: [    4.017369] Bluetooth: RFCOMM ver 1.10
Feb  8 15:34:49 sean-desktop kernel: [    4.018167] registered taskstats version 1
Feb  8 15:34:49 sean-desktop kernel: [    4.018275]   Magic number: 14:195:588
Feb  8 15:34:49 sean-desktop kernel: [    4.018279] usb_endpoint usbdev7.1_ep00: hash matches
Feb  8 15:34:49 sean-desktop kernel: [    4.018355] rtc_cmos 00:03: setting system clock to 2010-02-08 15:34:40 UTC (1265643280)
Feb  8 15:34:49 sean-desktop kernel: [    4.018362] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb  8 15:34:49 sean-desktop kernel: [    4.018363] EDD information not available.
Feb  8 15:34:49 sean-desktop kernel: [    4.018400] Freeing unused kernel memory: 536k freed
Feb  8 15:34:49 sean-desktop kernel: [    4.018520] Write protecting the kernel read-only data: 6688k
Feb  8 15:34:49 sean-desktop kernel: [    4.138860] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Feb  8 15:34:49 sean-desktop kernel: [    4.138863] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Feb  8 15:34:49 sean-desktop kernel: [    4.138909] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  8 15:34:49 sean-desktop kernel: [    4.138917] e1000e 0000:00:19.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    4.138997] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
Feb  8 15:34:49 sean-desktop kernel: [    4.163217] ohci1394 0000:05:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  8 15:34:49 sean-desktop kernel: [    4.213956] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[d0008000-d00087ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
Feb  8 15:34:49 sean-desktop kernel: [    4.292518] usb 2-2: new high speed USB device using ehci_hcd and address 2
Feb  8 15:34:49 sean-desktop kernel: [    4.343088] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:c0:6c:42:c9
Feb  8 15:34:49 sean-desktop kernel: [    4.343090] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Feb  8 15:34:49 sean-desktop kernel: [    4.343113] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: ffffff-0ff
Feb  8 15:34:49 sean-desktop kernel: [    4.424880] usb 2-2: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    4.428079] Initializing USB Mass Storage driver...
Feb  8 15:34:49 sean-desktop kernel: [    4.440060] scsi6 : SCSI emulation for USB Mass Storage devices
Feb  8 15:34:49 sean-desktop kernel: [    4.440138] usbcore: registered new interface driver usb-storage
Feb  8 15:34:49 sean-desktop kernel: [    4.440140] USB Mass Storage support registered.
Feb  8 15:34:49 sean-desktop kernel: [    4.440219] usb-storage: device found at 2
Feb  8 15:34:49 sean-desktop kernel: [    4.440220] usb-storage: waiting for device to settle before scanning
Feb  8 15:34:49 sean-desktop kernel: [    4.752701] PM: Starting manual resume from disk
Feb  8 15:34:49 sean-desktop kernel: [    4.752704] PM: Resume from partition 8:8
Feb  8 15:34:49 sean-desktop kernel: [    4.752705] PM: Checking hibernation image.
Feb  8 15:34:49 sean-desktop kernel: [    4.752853] PM: Resume from disk failed.
Feb  8 15:34:49 sean-desktop kernel: [    4.780797] kjournald starting.  Commit interval 5 seconds
Feb  8 15:34:49 sean-desktop kernel: [    4.780804] EXT3-fs: mounted filesystem with ordered data mode.
Feb  8 15:34:49 sean-desktop kernel: [    4.856013] usb 6-1: new low speed USB device using uhci_hcd and address 2
Feb  8 15:34:49 sean-desktop kernel: [    5.036912] usb 6-1: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    5.280015] usb 6-2: new low speed USB device using uhci_hcd and address 3
Feb  8 15:34:49 sean-desktop kernel: [    5.456924] usb 6-2: configuration #1 chosen from 1 choice
Feb  8 15:34:49 sean-desktop kernel: [    5.496138] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270002240b61]
Feb  8 15:34:49 sean-desktop kernel: [    9.285636] udev: starting version 141
Feb  8 15:34:49 sean-desktop kernel: [    9.440271] usb-storage: device scan complete
Feb  8 15:34:49 sean-desktop kernel: [    9.440659] scsi 6:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
Feb  8 15:34:49 sean-desktop kernel: [    9.442896] sd 6:0:0:0: [sdb] 7856127 512-byte hardware sectors: (4.02 GB/3.74 GiB)
Feb  8 15:34:49 sean-desktop kernel: [    9.443388] sd 6:0:0:0: [sdb] Write Protect is off
Feb  8 15:34:49 sean-desktop kernel: [    9.443391] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
Feb  8 15:34:49 sean-desktop kernel: [    9.443393] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Feb  8 15:34:49 sean-desktop kernel: [    9.444518] sd 6:0:0:0: [sdb] 7856127 512-byte hardware sectors: (4.02 GB/3.74 GiB)
Feb  8 15:34:49 sean-desktop kernel: [    9.445015] sd 6:0:0:0: [sdb] Write Protect is off
Feb  8 15:34:49 sean-desktop kernel: [    9.445017] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
Feb  8 15:34:49 sean-desktop kernel: [    9.445019] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Feb  8 15:34:49 sean-desktop kernel: [    9.445022]  sdb: sdb1
Feb  8 15:34:49 sean-desktop kernel: [    9.446011] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Feb  8 15:34:49 sean-desktop kernel: [    9.446112] sd 6:0:0:0: Attached scsi generic sg2 type 0
Feb  8 15:34:49 sean-desktop kernel: [    9.595145] iTCO_vendor_support: vendor-support=0
Feb  8 15:34:49 sean-desktop kernel: [    9.596284] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Feb  8 15:34:49 sean-desktop kernel: [    9.596373] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
Feb  8 15:34:49 sean-desktop kernel: [    9.596429] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Feb  8 15:34:49 sean-desktop kernel: [    9.625850] input: PC Speaker as /devices/platform/pcspkr/input/input3
Feb  8 15:34:49 sean-desktop kernel: [    9.660394] usbcore: registered new interface driver hiddev
Feb  8 15:34:49 sean-desktop kernel: [    9.675216] input: NOVATEK Kensington U+P Keyboard as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input4
Feb  8 15:34:49 sean-desktop kernel: [    9.704174] generic-usb 0003:047D:2043.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK Kensington U+P Keyboard] on usb-0000:00:1d.1-1/input0
Feb  8 15:34:49 sean-desktop kernel: [    9.734986] input: NOVATEK Kensington U+P Keyboard as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input5
Feb  8 15:34:49 sean-desktop kernel: [    9.760070] generic-usb 0003:047D:2043.0002: input,hidraw1: USB HID v1.10 Device [NOVATEK Kensington U+P Keyboard] on usb-0000:00:1d.1-1/input1
Feb  8 15:34:49 sean-desktop kernel: [    9.774204] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input6
Feb  8 15:34:49 sean-desktop kernel: [    9.800144] generic-usb 0003:046D:C01B.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
Feb  8 15:34:49 sean-desktop kernel: [    9.800175] usbcore: registered new interface driver usbhid
Feb  8 15:34:49 sean-desktop kernel: [    9.800190] usbhid: v2.6:USB HID core driver
Feb  8 15:34:49 sean-desktop kernel: [    9.840653] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb  8 15:34:49 sean-desktop kernel: [    9.854412] [fglrx] Maximum main memory to use for locked dma buffers: 2837 MBytes.
Feb  8 15:34:49 sean-desktop kernel: [    9.854551] [fglrx]   vendor: 1002 device: 954f count: 1
Feb  8 15:34:49 sean-desktop kernel: [    9.854800] [fglrx] ioport: bar 4, base 0x2000, size: 0x100
Feb  8 15:34:49 sean-desktop kernel: [    9.854810] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  8 15:34:49 sean-desktop kernel: [    9.854814] pci 0000:01:00.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [    9.856641] [fglrx] Driver built-in PAT support is enabled successfully
Feb  8 15:34:49 sean-desktop kernel: [    9.856669] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
Feb  8 15:34:49 sean-desktop kernel: [   10.168055] cfg80211: Calling CRDA to update world regulatory domain
Feb  8 15:34:49 sean-desktop kernel: [   10.238144] cfg80211: World regulatory domain updated:
Feb  8 15:34:49 sean-desktop kernel: [   10.238147] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb  8 15:34:49 sean-desktop kernel: [   10.238148] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:34:49 sean-desktop kernel: [   10.238150] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:34:49 sean-desktop kernel: [   10.238151] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:34:49 sean-desktop kernel: [   10.238153] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:34:49 sean-desktop kernel: [   10.238154] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  8 15:34:49 sean-desktop kernel: [   10.399699] rt61pci 0000:05:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb  8 15:34:49 sean-desktop kernel: [   10.406596] phy0: Selected rate control algorithm 'pid'
Feb  8 15:34:49 sean-desktop kernel: [   10.459638] Registered led device: rt61pci-phy0:radio
Feb  8 15:34:49 sean-desktop kernel: [   10.459664] Registered led device: rt61pci-phy0:assoc
Feb  8 15:34:49 sean-desktop kernel: [   10.494337] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Feb  8 15:34:49 sean-desktop kernel: [   10.494392] HDA Intel 0000:00:1b.0: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [   10.525914] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Feb  8 15:34:49 sean-desktop kernel: [   10.559108] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb  8 15:34:49 sean-desktop kernel: [   10.559152] HDA Intel 0000:01:00.1: setting latency timer to 64
Feb  8 15:34:49 sean-desktop kernel: [   10.698890] lp: driver loaded but no devices found
Feb  8 15:34:49 sean-desktop kernel: [   10.809494] Adding 2216928k swap on /dev/sda8.  Priority:-1 extents:1 across:2216928k
Feb  8 15:34:49 sean-desktop kernel: [   11.336916] EXT3 FS on sda7, internal journal
Feb  8 15:34:49 sean-desktop kernel: [   12.247915] type=1505 audit(1265672088.726:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2187
Feb  8 15:34:49 sean-desktop kernel: [   12.274794] type=1505 audit(1265672088.754:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2191
Feb  8 15:34:49 sean-desktop kernel: [   12.274880] type=1505 audit(1265672088.754:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2191
Feb  8 15:34:49 sean-desktop kernel: [   12.274908] type=1505 audit(1265672088.754:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2191
Feb  8 15:34:49 sean-desktop kernel: [   12.274937] type=1505 audit(1265672088.754:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2191
Feb  8 15:34:49 sean-desktop kernel: [   12.351699] type=1505 audit(1265672088.830:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2196
Feb  8 15:34:49 sean-desktop kernel: [   12.351858] type=1505 audit(1265672088.830:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2196
Feb  8 15:34:49 sean-desktop kernel: [   12.368994] type=1505 audit(1265672088.846:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2200
Feb  8 15:34:51 sean-desktop acpid: client connected from 2861[111:122] 
Feb  8 15:34:51 sean-desktop bluetoothd[2888]: Bluetooth daemon
Feb  8 15:34:51 sean-desktop bluetoothd[2888]: Starting SDP server
Feb  8 15:34:51 sean-desktop bluetoothd[2888]: Starting experimental netlink support
Feb  8 15:34:51 sean-desktop bluetoothd[2888]: Failed to find Bluetooth netlink family
Feb  8 15:34:51 sean-desktop bluetoothd[2888]: Registered interface org.bluez.Service on path /org/bluez/2888/any
Feb  8 15:34:51 sean-desktop kernel: [   14.895907] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb  8 15:34:51 sean-desktop kernel: [   14.895910] Bluetooth: BNEP filters: protocol multicast
Feb  8 15:34:51 sean-desktop bluetoothd[2888]: bridge pan0 created
Feb  8 15:34:51 sean-desktop kernel: [   14.918289] Bridge firewalling registered
Feb  8 15:34:52 sean-desktop acpid: client connected from 2933[0:0] 
Feb  8 15:34:52 sean-desktop atieventsd[2956]: ATI External Events Daemon started... 
Feb  8 15:34:52 sean-desktop atieventsd[2956]: Event daemon control socket created 
Feb  8 15:34:52 sean-desktop acpid: client connected from 2956[0:0] 
Feb  8 15:34:52 sean-desktop atieventsd[2956]: acpid connection established 
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  starting... 
Feb  8 15:34:53 sean-desktop avahi-daemon[3008]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Feb  8 15:34:53 sean-desktop avahi-daemon[3008]: Successfully dropped root privileges.
Feb  8 15:34:53 sean-desktop avahi-daemon[3008]: avahi-daemon 0.6.23 starting up.
Feb  8 15:34:53 sean-desktop avahi-daemon[3008]: Successfully called chroot().
Feb  8 15:34:53 sean-desktop avahi-daemon[3008]: Successfully dropped remaining capabilities.
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000e') 
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_c0_6c_42_c9 
Feb  8 15:34:53 sean-desktop avahi-daemon[3008]: No service file found in /etc/avahi/services.
Feb  8 15:34:53 sean-desktop avahi-daemon[3008]: Network interface enumeration completed.
Feb  8 15:34:53 sean-desktop avahi-daemon[3008]: Registering HINFO record with values 'X86_64'/'LINUX'.
Feb  8 15:34:53 sean-desktop avahi-daemon[3008]: Server startup complete. Host name is sean-desktop.local. Local service cookie is 1225632888.
Feb  8 15:34:53 sean-desktop kernel: [   16.661809] ppdev: user-space parallel port driver
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt61pci') 
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_23_69_e4_98_0d 
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  Trying to start the supplicant... 
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  Trying to start the system settings daemon... 
Feb  8 15:34:53 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: init!
Feb  8 15:34:53 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Feb  8 15:34:53 sean-desktop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Feb  8 15:34:53 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_c0_6c_42_c9, iface: eth0): not well known
Feb  8 15:34:53 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_23_69_e4_98_0d, iface: wlan0): not well known
Feb  8 15:34:53 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Feb  8 15:34:53 sean-desktop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb  8 15:34:53 sean-desktop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb  8 15:34:53 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: (25977296) ... get_connections.
Feb  8 15:34:53 sean-desktop nm-system-settings:    SCPlugin-Ifupdown: (25977296) ... get_connections (managed=false): return empty list.
Feb  8 15:34:53 sean-desktop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Feb  8 15:34:53 sean-desktop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
Feb  8 15:34:53 sean-desktop anacron[3126]: Anacron 2.3 started on 2010-02-08
Feb  8 15:34:53 sean-desktop anacron[3126]: Normal exit (0 jobs run)
Feb  8 15:34:53 sean-desktop /usr/sbin/cron[3169]: (CRON) INFO (pidfile fd = 3)
Feb  8 15:34:53 sean-desktop /usr/sbin/cron[3170]: (CRON) STARTUP (fork ok)
Feb  8 15:34:53 sean-desktop /usr/sbin/cron[3170]: (CRON) INFO (Running @reboot jobs)
Feb  8 15:34:54 sean-desktop kernel: [   17.927612] fglrx_pci 0000:01:00.0: irq 2298 for MSI/MSI-X
Feb  8 15:34:54 sean-desktop kernel: [   17.939186] [fglrx] Firegl kernel thread PID: 3281
Feb  8 15:34:54 sean-desktop kernel: [   17.958795] [fglrx] Gart USWC size:1427 M.
Feb  8 15:34:54 sean-desktop kernel: [   17.958798] [fglrx] Gart cacheable size:60 M.
Feb  8 15:34:54 sean-desktop kernel: [   17.958803] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Feb  8 15:34:54 sean-desktop kernel: [   17.958805] [fglrx] Reserved FB block: Unshared offset:fd0d000, size:2f3000 
Feb  8 15:34:54 sean-desktop kernel: [   17.958807] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (eth0): bringing up device. 
Feb  8 15:34:57 sean-desktop nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_c0_6c_42_c9
Feb  8 15:34:57 sean-desktop kernel: [   20.648182] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (eth0): preparing device. 
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (wlan0): bringing up device. 
Feb  8 15:34:57 sean-desktop kernel: [   20.704536] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
Feb  8 15:34:57 sean-desktop kernel: [   20.705397] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  8 15:34:57 sean-desktop kernel: [   20.706020] rt61pci 0000:05:03.0: firmware: requesting rt2561s.bin
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (wlan0): preparing device. 
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Feb  8 15:34:57 sean-desktop kernel: [   20.946514] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Feb  8 15:34:57 sean-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
Feb  8 15:34:58 sean-desktop kernel: [   22.404038] wlan0: authenticate with AP 00:09:5b:eb:3e:5c
Feb  8 15:34:58 sean-desktop kernel: [   22.405474] wlan0: authenticated
Feb  8 15:34:58 sean-desktop kernel: [   22.405477] wlan0: associate with AP 00:09:5b:eb:3e:5c
Feb  8 15:34:58 sean-desktop kernel: [   22.408664] wlan0: RX AssocResp from 00:09:5b:eb:3e:5c (capab=0x421 status=0 aid=2)
Feb  8 15:34:58 sean-desktop kernel: [   22.408666] wlan0: associated
Feb  8 15:34:58 sean-desktop kernel: [   22.409537] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb  8 15:34:58 sean-desktop kernel: [   22.423760] wlan0: disassociating by local choice (reason=3)
Feb  8 15:35:00 sean-desktop avahi-daemon[3008]: Registering new address record for fe80::223:69ff:fee4:980d on wlan0.*.
Feb  8 15:35:05 sean-desktop console-kit-daemon[2722]: WARNING: Couldn't read /proc/2721/environ: Failed to open file '/proc/2721/environ': No such file or directory 
Feb  8 15:35:09 sean-desktop kernel: [   32.552007] wlan0: no IPv6 routers present
Feb  8 15:35:11 sean-desktop pulseaudio[3485]: module-x11-xsmp.c: X11 session manager not running.
Feb  8 15:35:12 sean-desktop pulseaudio[3485]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 2WIRE932' 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 2WIRE932' has security, but secrets are required. 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 2WIRE932' has security, and secrets exist.  No new secrets needed. 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Config: added 'ssid' value '2WIRE932' 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Feb  8 15:35:13 sean-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Feb  8 15:35:13 sean-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  Config: set interface ap_scan to 1 
Feb  8 15:35:13 sean-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning 
Feb  8 15:35:14 sean-desktop hald: mounted /dev/sdb1 on behalf of uid 1000
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed 
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '2WIRE932'. 
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Feb  8 15:35:15 sean-desktop kernel: [   38.901253] wlan0: authenticate with AP 00:22:a4:5f:d6:19
Feb  8 15:35:15 sean-desktop kernel: [   38.902451] wlan0: authenticated
Feb  8 15:35:15 sean-desktop kernel: [   38.902454] wlan0: associate with AP 00:22:a4:5f:d6:19
Feb  8 15:35:15 sean-desktop kernel: [   38.904106] wlan0: RX AssocResp from 00:22:a4:5f:d6:19 (capab=0x431 status=0 aid=2)
Feb  8 15:35:15 sean-desktop kernel: [   38.904109] wlan0: associated
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  dhclient started with pid 3686 
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Feb  8 15:35:15 sean-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  8 15:35:15 sean-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  8 15:35:15 sean-desktop dhclient: All rights reserved.
Feb  8 15:35:15 sean-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  8 15:35:15 sean-desktop dhclient: 
Feb  8 15:35:15 sean-desktop dhclient: wmaster0: unknown hardware address type 801
Feb  8 15:35:15 sean-desktop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Feb  8 15:35:15 sean-desktop dhclient: wmaster0: unknown hardware address type 801
Feb  8 15:35:15 sean-desktop dhclient: Listening on LPF/wlan0/00:23:69:e4:98:0d
Feb  8 15:35:15 sean-desktop dhclient: Sending on   LPF/wlan0/00:23:69:e4:98:0d
Feb  8 15:35:15 sean-desktop dhclient: Sending on   Socket/fallback
Feb  8 15:35:18 sean-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Feb  8 15:35:19 sean-desktop dhclient: DHCPOFFER of 192.168.1.105 from 192.168.1.254
Feb  8 15:35:19 sean-desktop dhclient: DHCPREQUEST of 192.168.1.105 on wlan0 to 255.255.255.255 port 67
Feb  8 15:35:19 sean-desktop dhclient: DHCPACK of 192.168.1.105 from 192.168.1.254
Feb  8 15:35:19 sean-desktop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>    address 192.168.1.105 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>    gateway 192.168.1.254 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>    nameserver '192.168.1.254' 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>    domain name 'gateway.2wire.net' 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Feb  8 15:35:19 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Feb  8 15:35:19 sean-desktop avahi-daemon[3008]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.105.
Feb  8 15:35:19 sean-desktop dhclient: bound to 192.168.1.105 -- renewal in 36619 seconds.
Feb  8 15:35:19 sean-desktop avahi-daemon[3008]: New relevant interface wlan0.IPv4 for mDNS.
Feb  8 15:35:19 sean-desktop avahi-daemon[3008]: Registering new address record for 192.168.1.105 on wlan0.IPv4.
Feb  8 15:35:20 sean-desktop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Feb  8 15:35:20 sean-desktop NetworkManager: <info>  Policy set 'Auto 2WIRE932' (wlan0) as default for routing and DNS. 
Feb  8 15:35:20 sean-desktop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Feb  8 15:35:20 sean-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb  8 15:35:22 sean-desktop ntpdate[3765]: adjust time server 91.189.94.4 offset -0.292783 sec
Feb  8 15:40:01 sean-desktop /USR/SBIN/CRON[3979]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

---

### Post by AquaFusion on 2010-02-09
Anyone still dont know what is going on? i was hoping anyone would found out why my ubuntu keep freezing up

---

