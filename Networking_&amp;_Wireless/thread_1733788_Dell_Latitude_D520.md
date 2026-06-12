---
title: "Dell Latitude D520"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by LinXNut on 2011-04-19
Hi, I have been using Linux for awhile now, but I am new to Ubuntu. The laptop my friend recently gave to me is a Dell Latitude D520. It is kinda old, but it works. I installed Xubuntu 10.10 on it perfectly with no problem. The only problem I am having is the networking. I plugged an ethernet cable into it, and for some reason the network manager was not picking it up. I also tried a wireless G notebook card which said "firmware not installed." I really need to install the updates so I can install other things later. :(

Thnx,
LinXnut

---

### Post by josephmills on 2011-04-19
could we please see a ```
lspci
``` thanks

---

### Post by LinXNut on 2011-04-19
I am actually on a seperate computer....:(  

What should I look for?

---

### Post by josephmills on 2011-04-19
the wireless card

---

### Post by gradinaruvasile on 2011-04-19
The 520's wired interface should work out of the box. As for the wireless, if i am not mistaken it has a Intel 2200 b/g card - you need the 
firmware-linux-nonfree (good for the video driver too) package along with firmware for ipw2200 for the wireless to work. But Ubuntu should have it in the kernel.

---

### Post by LinXNut on 2011-04-19
I have Xubuntu installed, would that be the issue? My laptop would be pretty slow with Ubuntu. Is there a way to install the firmware package even without the internet?

---

### Post by josephmills on 2011-04-19
if you have a usb stick or cd or dvd download the tar and tell us when you have it

---

### Post by LinXNut on 2011-04-19
Where can I find the tarball?

---

### Post by gradinaruvasile on 2011-04-19
Paste here the output of 'dmesg' in a terminal.

---

### Post by josephmills on 2011-04-19
we need to know what tar to get first type```
sudo lshw -C network[code]
you will get some code like this [code]
 pci (sysfs)
 *-network DISABLED
 Descriptio: **wireless interface**
** Products: AR928X Wireless Network Adapter (PCI-express)**
 Vendor: Atheros communications IC.
 Physical id: 0
 Bus infor: pci@0000:02:00.0
 logical name: Wlan0
 Versio: 01
 Serial: 70:1a:04:b8:36:f3
 Width: 64bits
 clock33mhz
 Capabilities: bus_master cap_list ethernet physical wireless
 Configuration: broadcast=yes **driver=ath9k** driverversion=2. 6. 35-25-generic firmware=N/A latency = 0 multicast=yes wireless=IEEE 802. 11bgn
 resources: irq: 16 memory: d1100000-d110ffff
```the parts that are in bold are the info that we need

---

### Post by LinXNut on 2011-04-19
Ok I saved into text editor and put it on a flash drive....

Here is the code for "dmesg"

```
jonathan@Xubuntu-Lap:~/Desktop$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6d3400 (usable)
[    0.000000]  BIOS-e820: 000000001f6d3400 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.4 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1f6d3 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 01F800000 mask FFF800000 uncachable
[    0.000000]   2 base 01F700000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001f6d3400 (usable)
[    0.000000]  modified: 000000001f6d3400 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001f6d3000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001f400000 page 2M
[    0.000000]  001f400000 - 001f6d3000 page 4k
[    0.000000] kernel direct mapping tables up to 1f6d3000 @ 15000-1a000
[    0.000000] RAMDISK: 16f1d000 - 1795f000
[    0.000000] ACPI: RSDP 000fc390 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 1f6d3d56 00038 (v01 DELL    M07     27D6071F ASL  00000061)
[    0.000000] ACPI: FACP 1f6d4800 00074 (v01 DELL    M07     27D6071F ASL  00000061)
[    0.000000] ACPI: DSDT 1f6d5400 03E0B (v01 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 1f6e3c00 00040
[    0.000000] ACPI: APIC 1f6d5000 00068 (v01 DELL    M07     27D6071F ASL  00000047)
[    0.000000] ACPI: MCFG 1f6d4fc0 0003E (v16 DELL    M07     27D6071F ASL  00000061)
[    0.000000] ACPI: SSDT 1f6d426a 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.000000] ACPI: SSDT 1f6d3d8e 004DC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1f6d3000
[    0.000000]   low ram: 0 - 1f6d3000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001f6d3
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001f6d3
[    0.000000] On node 0 totalpages: 128611
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 974 pages used for memmap
[    0.000000]   Normal zone: 123653 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127605
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=0c7b9a07-a1ec-4692-b1e4-cfce0acdc315 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2574440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (43 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [0016f1d000 - 001795f000]         RAMDISK
[    0.000000]   #4 [000009f000 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009a1000 - 00009a4188]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 00013f1000]         BOOTMEM
[    0.000000]   #11 [00013f1000 - 00013f1004]         BOOTMEM
[    0.000000]   #12 [00013f1040 - 00013f1100]         BOOTMEM
[    0.000000]   #13 [00013f1100 - 00013f1130]         BOOTMEM
[    0.000000]   #14 [00013f1140 - 00013f2940]         BOOTMEM
[    0.000000]   #15 [00013f2940 - 00013f2967]         BOOTMEM
[    0.000000]   #16 [00013f2980 - 00013f2aec]         BOOTMEM
[    0.000000]   #17 [00013f2b00 - 00013f2b40]         BOOTMEM
[    0.000000]   #18 [00013f2b40 - 00013f2b80]         BOOTMEM
[    0.000000]   #19 [00013f2b80 - 00013f2bc0]         BOOTMEM
[    0.000000]   #20 [00013f2bc0 - 00013f2c00]         BOOTMEM
[    0.000000]   #21 [00013f2c00 - 00013f2c40]         BOOTMEM
[    0.000000]   #22 [00013f2c40 - 00013f2c80]         BOOTMEM
[    0.000000]   #23 [00013f2c80 - 00013f2cc0]         BOOTMEM
[    0.000000]   #24 [00013f2cc0 - 00013f2d00]         BOOTMEM
[    0.000000]   #25 [00013f2d00 - 00013f2d40]         BOOTMEM
[    0.000000]   #26 [00013f2d40 - 00013f2d80]         BOOTMEM
[    0.000000]   #27 [00013f2d80 - 00013f2d90]         BOOTMEM
[    0.000000]   #28 [00013f2dc0 - 00013f2dd0]         BOOTMEM
[    0.000000]   #29 [00013f2e00 - 00013f2e6a]         BOOTMEM
[    0.000000]   #30 [00013f2e80 - 00013f2eea]         BOOTMEM
[    0.000000]   #31 [0001400000 - 000140e000]         BOOTMEM
[    0.000000]   #32 [0001600000 - 000160e000]         BOOTMEM
[    0.000000]   #33 [00013f4f00 - 00013f4f04]         BOOTMEM
[    0.000000]   #34 [00013f4f40 - 00013f4f44]         BOOTMEM
[    0.000000]   #35 [00013f4f80 - 00013f4f88]         BOOTMEM
[    0.000000]   #36 [00013f4fc0 - 00013f4fc8]         BOOTMEM
[    0.000000]   #37 [00013f5000 - 00013f50a8]         BOOTMEM
[    0.000000]   #38 [00013f50c0 - 00013f5128]         BOOTMEM
[    0.000000]   #39 [00013f2f00 - 00013f4f00]         BOOTMEM
[    0.000000]   #40 [000140e000 - 000144e000]         BOOTMEM
[    0.000000]   #41 [000144e000 - 000146e000]         BOOTMEM
[    0.000000]   #42 [000160e000 - 0001882868]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 487992k/514892k available (4928k kernel code, 26452k reserved, 2336k data, 684k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdfed3000 - 0xff7fe000   ( 505 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdf6d3000   ( 502 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1729.246 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3458.49 BogoMIPS (lpj=6916984)
[    0.004022] pid_max: default: 32768 minimum: 301
[    0.004054] Security Framework initialized
[    0.004088] AppArmor: AppArmor initialized
[    0.004092] Yama: becoming mindful.
[    0.004190] Mount-cache hash table entries: 512
[    0.004417] Initializing cgroup subsys ns
[    0.004433] Initializing cgroup subsys cpuacct
[    0.004438] Initializing cgroup subsys memory
[    0.004450] Initializing cgroup subsys devices
[    0.004463] Initializing cgroup subsys freezer
[    0.004466] Initializing cgroup subsys net_cls
[    0.004511] mce: CPU supports 6 MCE banks
[    0.004533] CPU0: Thermal monitoring enabled (TM2)
[    0.004538] using mwait in idle threads.
[    0.004545] Performance Events: Core events, core PMU driver.
[    0.004576] ... version:                1
[    0.004588] ... bit width:              40
[    0.004591] ... generic registers:      2
[    0.004593] ... value mask:             000000ffffffffff
[    0.004596] ... max period:             000000007fffffff
[    0.004599] ... fixed-purpose events:   0
[    0.004601] ... event mask:             0000000000000003
[    0.009238] SMP alternatives: switching to UP code
[    0.022050] ACPI: Core revision 20100428
[    0.033882] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.033901] ftrace: allocating 21758 entries in 43 pages
[    0.036119] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040492] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080254] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 08
[    0.084000] Brought up 1 CPUs
[    0.084000] Total of 1 processors activated (3458.49 BogoMIPS).
[    0.084000] devtmpfs: initialized
[    0.084000] regulator: core version 0.5
[    0.084000] Time: 16:14:59  Date: 04/19/11
[    0.084000] NET: Registered protocol family 16
[    0.084000] EISA bus registered
[    0.084000] ACPI: bus type pci registered
[    0.084000] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.084000] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    0.084000] PCI: Using MMCONFIG for extended config space
[    0.084000] PCI: Using configuration type 1 for base access
[    0.084954] bio: create slab <bio-0> at 0
[    0.086645] ACPI: EC: Look up EC in DSDT
[    0.097564] ACPI: Interpreter enabled
[    0.097569] ACPI: (supports S0 S3 S4 S5)
[    0.097603] ACPI: Using IOAPIC for interrupt routing
[    0.135717] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.135724] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.158182] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.202936] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.202950] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.202954] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.202957] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.202961] pci_root PNP0A03:00: host bridge window [mem 0x20000000-0xdfffffff] (ignored)
[    0.202965] pci_root PNP0A03:00: host bridge window [mem 0xf0007000-0xf0007fff] (ignored)
[    0.202968] pci_root PNP0A03:00: host bridge window [mem 0xf000c000-0xfebfffff] (ignored)
[    0.202982] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfed1ffff] (ignored)
[    0.202986] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xffafffff] (ignored)
[    0.203090] pci 0000:00:02.0: reg 10: [mem 0xdff00000-0xdff7ffff]
[    0.203107] pci 0000:00:02.0: reg 14: [io  0xeff8-0xefff]
[    0.203112] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff pref]
[    0.203118] pci 0000:00:02.0: reg 1c: [mem 0xdfec0000-0xdfefffff]
[    0.203182] pci 0000:00:02.1: reg 10: [mem 0xdff80000-0xdfffffff]
[    0.203347] pci 0000:00:1b.0: reg 10: [mem 0xdfebc000-0xdfebffff 64bit]
[    0.203443] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.203459] pci 0000:00:1b.0: PME# disabled
[    0.203605] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.203621] pci 0000:00:1c.0: PME# disabled
[    0.203726] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
[    0.203823] pci 0000:00:1d.1: reg 20: [io  0xbf60-0xbf7f]
[    0.203921] pci 0000:00:1d.2: reg 20: [io  0xbf40-0xbf5f]
[    0.204015] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
[    0.204110] pci 0000:00:1d.7: reg 10: [mem 0xffa80000-0xffa803ff]
[    0.204209] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.204225] pci 0000:00:1d.7: PME# disabled
[    0.204484] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.204492] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.204497] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.204503] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.204520] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.204618] pci 0000:00:1f.2: reg 10: [io  0x01f0-0x01f7]
[    0.204627] pci 0000:00:1f.2: reg 14: [io  0x03f4-0x03f7]
[    0.204646] pci 0000:00:1f.2: reg 18: [io  0x0170-0x0177]
[    0.204655] pci 0000:00:1f.2: reg 1c: [io  0x0374-0x0377]
[    0.204664] pci 0000:00:1f.2: reg 20: [io  0xbfa0-0xbfaf]
[    0.204723] pci 0000:00:1f.2: PME# supported from D3hot
[    0.204728] pci 0000:00:1f.2: PME# disabled
[    0.204825] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
[    0.204976] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.204983] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.205000] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.205009] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.205112] pci 0000:02:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.205163] pci 0000:02:01.0: supports D1 D2
[    0.205165] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205172] pci 0000:02:01.0: PME# disabled
[    0.205237] pci 0000:02:01.4: reg 10: [mem 0xdfdff000-0xdfdfffff]
[    0.205257] pci 0000:02:01.4: reg 14: [mem 0xdfdfe800-0xdfdfefff]
[    0.205331] pci 0000:02:01.4: supports D1 D2
[    0.205334] pci 0000:02:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205340] pci 0000:02:01.4: PME# disabled
[    0.205453] pci 0000:00:1e.0: PCI bridge to [bus 02-03] (subtractive decode)
[    0.205460] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.205466] pci 0000:00:1e.0:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.205485] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.205489] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.205492] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.205579] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02-03]
[    0.205598] pci_bus 0000:00: on NUMA node 0
[    0.205615] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.206138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.206327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.230779] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.230989] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.231175] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *0, disabled.
[    0.231393] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.231597] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.231818] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.232048] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.232267] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.232365] HEST: Table is not found!
[    0.232495] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.232514] vgaarb: loaded
[    0.232782] SCSI subsystem initialized
[    0.232876] libata version 3.00 loaded.
[    0.232972] usbcore: registered new interface driver usbfs
[    0.232999] usbcore: registered new interface driver hub
[    0.233050] usbcore: registered new device driver usb
[    0.233260] ACPI: WMI: Mapper loaded
[    0.233274] PCI: Using ACPI for IRQ routing
[    0.233277] PCI: pci_cache_line_size set to 64 bytes
[    0.233381] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.233385] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.233388] reserve RAM buffer: 000000001f6d3400 - 000000001fffffff 
[    0.233563] NetLabel: Initializing
[    0.233565] NetLabel:  domain hash size = 128
[    0.233567] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.233593] NetLabel:  unlabeled traffic allowed by default
[    0.233793] hpet clockevent registered
[    0.233798] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.233817] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.233823] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.236035] Switching to clocksource tsc
[    0.254821] AppArmor: AppArmor Filesystem Enabled
[    0.254862] pnp: PnP ACPI init
[    0.254904] ACPI: bus type pnp registered
[    0.307583] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.307589] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.307713] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.307718] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.307722] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.307727] pnp 00:03: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.327865] pnp: PnP ACPI: found 12 devices
[    0.327869] ACPI: ACPI bus type pnp unregistered
[    0.327884] PnPBIOS: Disabled by ACPI PNP
[    0.327899] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.327913] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.327918] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.327922] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.327926] system 00:00: [mem 0x00100000-0x1f6d33ff] could not be reserved
[    0.327929] system 00:00: [mem 0x1f6d3400-0x1f6fffff] has been reserved
[    0.327933] system 00:00: [mem 0x1f700000-0x1f7fffff] has been reserved
[    0.327947] system 00:00: [mem 0x1f700000-0x1fefffff] could not be reserved
[    0.327951] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
[    0.327955] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.327964] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.327978] system 00:00: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.327982] system 00:00: [mem 0xf0000000-0xf0003fff] has been reserved
[    0.327985] system 00:00: [mem 0xf0004000-0xf0004fff] has been reserved
[    0.327989] system 00:00: [mem 0xf0005000-0xf0005fff] has been reserved
[    0.327993] system 00:00: [mem 0xf0006000-0xf0006fff] has been reserved
[    0.327997] system 00:00: [mem 0xf0008000-0xf000bfff] has been reserved
[    0.328011] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.328019] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.328025] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.328029] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.328043] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.328046] system 00:03: [io  0x0809] has been reserved
[    0.328054] system 00:08: [io  0x0c80-0x0cff] could not be reserved
[    0.328058] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.328061] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.328075] system 00:08: [io  0x0930-0x097f] has been reserved
[    0.365282] pci 0000:00:1e.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.365286] pci 0000:00:1c.0: BAR 14: assigned [mem 0x24000000-0x241fffff]
[    0.365301] pci 0000:00:1c.0: BAR 15: assigned [mem 0x24200000-0x243fffff 64bit pref]
[    0.365305] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.365309] pci 0000:00:1e.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.365312] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.365329] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.365337] pci 0000:00:1c.0:   bridge window [mem 0x24000000-0x241fffff]
[    0.365343] pci 0000:00:1c.0:   bridge window [mem 0x24200000-0x243fffff 64bit pref]
[    0.365364] pci 0000:02:01.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.365368] pci 0000:02:01.0: BAR 16: assigned [mem 0x28000000-0x2bffffff]
[    0.365371] pci 0000:02:01.0: BAR 0: assigned [mem 0xdfd00000-0xdfd00fff]
[    0.365379] pci 0000:02:01.0: BAR 0: set to [mem 0xdfd00000-0xdfd00fff] (PCI address [0xdfd00000-0xdfd00fff]
[    0.365394] pci 0000:02:01.0: BAR 13: assigned [io  0x3000-0x30ff]
[    0.365397] pci 0000:02:01.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.365400] pci 0000:02:01.0: CardBus bridge to [bus 03-06]
[    0.365404] pci 0000:02:01.0:   bridge window [io  0x3000-0x30ff]
[    0.365410] pci 0000:02:01.0:   bridge window [io  0x3400-0x34ff]
[    0.365427] pci 0000:02:01.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.365434] pci 0000:02:01.0:   bridge window [mem 0x28000000-0x2bffffff]
[    0.365440] pci 0000:00:1e.0: PCI bridge to [bus 02-03]
[    0.365445] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.365463] pci 0000:00:1e.0:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.365469] pci 0000:00:1e.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.365504]   alloc irq_desc for 16 on node -1
[    0.365507]   alloc kstat_irqs on node -1
[    0.365525] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.365533] pci 0000:00:1c.0: setting latency timer to 64
[    0.365543] pci 0000:00:1e.0: setting latency timer to 64
[    0.365567] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.365571]   alloc irq_desc for 19 on node -1
[    0.365574]   alloc kstat_irqs on node -1
[    0.365589] pci 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.365599] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.365602] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.365605] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.365619] pci_bus 0000:0b: resource 1 [mem 0x24000000-0x241fffff]
[    0.365622] pci_bus 0000:0b: resource 2 [mem 0x24200000-0x243fffff 64bit pref]
[    0.365626] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.365629] pci_bus 0000:02: resource 1 [mem 0xdfd00000-0xdfdfffff]
[    0.365632] pci_bus 0000:02: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.365635] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.365638] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.365652] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.365655] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.365658] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.365661] pci_bus 0000:03: resource 3 [mem 0x28000000-0x2bffffff]
[    0.365730] NET: Registered protocol family 2
[    0.365850] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.366191] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.366351] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.366499] TCP: Hash tables configured (established 16384 bind 16384)
[    0.366512] TCP reno registered
[    0.366516] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.366525] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.366650] NET: Registered protocol family 1
[    0.366678] pci 0000:00:02.0: Boot video device
[    0.366870] PCI: CLS 64 bytes, default 64
[    0.367188] cpufreq-nforce2: No nForce2 chipset.
[    0.367233] Scanning for low memory corruption every 60 seconds
[    0.367502] audit: initializing netlink socket (disabled)
[    0.367516] type=2000 audit(1303229699.360:1): initialized
[    0.389190] Trying to unpack rootfs image as initramfs...
[    0.412067] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.418853] VFS: Disk quotas dquot_6.5.2
[    0.418976] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.424441] fuse init (API version 7.14)
[    0.424630] msgmni has been set to 953
[    0.432426] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.432431] io scheduler noop registered
[    0.432434] io scheduler deadline registered
[    0.432463] io scheduler cfq registered (default)
[    0.432655] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.432731]   alloc irq_desc for 40 on node -1
[    0.432744]   alloc kstat_irqs on node -1
[    0.432761] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.432970] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.433072] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.433212] intel_idle: MWAIT substates: 0x1110
[    0.433225] intel_idle: does not run on family 6 model 14
[    0.433936] ACPI: AC Adapter [AC] (off-line)
[    0.434127] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.434781] ACPI: Lid Switch [LID]
[    0.434855] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.434861] ACPI: Power Button [PBTN]
[    0.434947] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.434952] ACPI: Sleep Button [SBTN]
[    0.435323] ACPI: acpi_idle registered with cpuidle
[    0.435716] Marking TSC unstable due to TSC halts in idle
[    0.439815] Switching to clocksource hpet
[    0.473200] thermal LNXTHERM:01: registered as thermal_zone0
[    0.473212] ACPI: Thermal Zone [THM] (32 C)
[    0.473462] ERST: Table is not found!
[    0.476591] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.476809] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.477611] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.479587] brd: module loaded
[    0.489155] loop: module loaded
[    0.489564] ata_piix 0000:00:1f.2: version 2.13
[    0.489601]   alloc irq_desc for 17 on node -1
[    0.489604]   alloc kstat_irqs on node -1
[    0.489625] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.489632] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.489705] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.492068] isapnp: Scanning for PnP cards...
[    0.500084] scsi0 : ata_piix
[    0.508324] scsi1 : ata_piix
[    0.596465] ACPI: Battery Slot [BAT1] (battery absent)
[    0.598976] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.598981] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.599835] Fixed MDIO Bus: probed
[    0.599904] PPP generic driver version 2.4.2
[    0.600068] tun: Universal TUN/TAP device driver, 1.6
[    0.600081] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.600225] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.600276]   alloc irq_desc for 20 on node -1
[    0.600278]   alloc kstat_irqs on node -1
[    0.600288] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.600320] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.600335] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.600386] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.600433] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.600448] ehci_hcd 0000:00:1d.7: debug port 1
[    0.604332] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.620084] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.632052] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.632360] hub 1-0:1.0: USB hub found
[    0.632367] hub 1-0:1.0: 8 ports detected
[    0.632520] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.632549] uhci_hcd: USB Universal Host Controller Interface driver
[    0.632630] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.632653] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.632658] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.632725] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.632780] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.632999] hub 2-0:1.0: USB hub found
[    0.633004] hub 2-0:1.0: 2 ports detected
[    0.633100]   alloc irq_desc for 21 on node -1
[    0.633103]   alloc kstat_irqs on node -1
[    0.633112] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.633129] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.633134] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.633191] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.633256] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.633451] hub 3-0:1.0: USB hub found
[    0.633456] hub 3-0:1.0: 2 ports detected
[    0.633549]   alloc irq_desc for 22 on node -1
[    0.633551]   alloc kstat_irqs on node -1
[    0.633556] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.633574] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.633579] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.633639] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.633685] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.633901] hub 4-0:1.0: USB hub found
[    0.633906] hub 4-0:1.0: 2 ports detected
[    0.633997]   alloc irq_desc for 23 on node -1
[    0.634000]   alloc kstat_irqs on node -1
[    0.634015] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.634023] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.634028] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.634085] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.634130] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.634341] hub 5-0:1.0: USB hub found
[    0.634347] hub 5-0:1.0: 2 ports detected
[    0.634559] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.644541] ACPI: Battery Slot [BAT0] (battery present)
[    0.648908] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.648920] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.649174] mice: PS/2 mouse device common for all mice
[    0.649459] rtc_cmos 00:06: RTC can wake from S4
[    0.649527] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.649584] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.649860] device-mapper: uevent: version 1.0.3
[    0.652093] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.698740] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.702278] device-mapper: multipath: version 1.1.1 loaded
[    0.702293] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.702592] EISA: Probing bus 0 at eisa.0
[    0.702613] Cannot allocate resource for EISA slot 1
[    0.702615] Cannot allocate resource for EISA slot 2
[    0.702618] Cannot allocate resource for EISA slot 3
[    0.702650] EISA: Detected 0 cards.
[    0.708201] cpuidle: using governor ladder
[    0.708295] cpuidle: using governor menu
[    0.708835] TCP cubic registered
[    0.709088] NET: Registered protocol family 10
[    0.709697] lo: Disabled Privacy Extensions
[    0.710054] NET: Registered protocol family 17
[    0.710147] Using IPI No-Shortcut mode
[    0.710353] PM: Resume from disk failed.
[    0.710367] registered taskstats version 1
[    0.710720]   Magic number: 7:280:237
[    0.710916] rtc_cmos 00:06: setting system clock to 2011-04-19 16:15:00 UTC (1303229700)
[    0.710919] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.710932] EDD information not available.
[    0.801431] ata2.00: ATAPI: PHILIPS DVD-ROM SDR089, TD38, max UDMA/33
[    0.801628] ata1.00: ATA-7: Hitachi HTS541040G9SA00, MB2OC60R, max UDMA/100
[    0.801632] ata1.00: 78140160 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.808838] ata2.00: configured for UDMA/33
[    0.817264] ata1.00: configured for UDMA/100
[    0.973172] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.173444] hub 1-2:1.0: USB hub found
[    1.173525] hub 1-2:1.0: 4 ports detected
[    1.243648] isapnp: No Plug & Play device found
[    1.244074] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54104 MB2O PQ: 0 ANSI: 5
[    1.244297] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.244515] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.244584] sd 0:0:0:0: [sda] Write Protect is off
[    1.244588] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.244618] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.244952]  sda:
[    1.245084] scsi 1:0:0:0: CD-ROM            PHILIPS  DVD-ROM SDR089   TD38 PQ: 0 ANSI: 5
[    1.253157] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    1.253163] Uniform CD-ROM driver Revision: 3.20
[    1.253326] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.253412] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.268685]  sda1 sda2 <
[    1.296140] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.308202]  sda5 >
[    1.308651] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.320426] Freeing initrd memory: 10504k freed
[    1.328112] Freeing unused kernel memory: 684k freed
[    1.328725] Write protecting the kernel text: 4932k
[    1.328768] Write protecting the kernel read-only data: 1976k
[    1.347655] udev[69]: starting version 163
[    1.647670] Initializing USB Mass Storage driver...
[    1.694322] scsi2 : usb-storage 1-6:1.0
[    1.694578] firewire_ohci 0000:02:01.4: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.694659] usbcore: registered new interface driver usb-storage
[    1.694662] USB Mass Storage support registered.
[    1.764032] firewire_ohci: Added fw-ohci device 0000:02:01.4, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x0
[    1.948414] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.264164] firewire_core: created device fw0: GUID 444fc0003cf48161, S400
[    2.692984] scsi 2:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
[    2.693471] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.694334] sd 2:0:0:0: [sdb] 7897088 512-byte logical blocks: (4.04 GB/3.76 GiB)
[    2.694954] sd 2:0:0:0: [sdb] Write Protect is off
[    2.694958] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[    2.694961] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.697342] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.697350]  sdb: sdb1
[    2.830719] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.830727] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   15.649027] udev[339]: starting version 163
[   15.727910] lp: driver loaded but no devices found
[   15.729013] Adding 1531900k swap on /dev/sda5.  Priority:-1 extents:1 across:1531900k 
[   16.082983] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input4
[   16.083064] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.083086] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   16.092766] intel_rng: FWH not detected
[   16.255804] leds_ss4200: no LED devices found
[   16.280663] Linux agpgart interface v0.103
[   16.295179] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   16.295475] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   16.304113] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.346787] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:01d4]
[   16.346816] yenta_cardbus 0000:02:01.0: O2: enabling read prefetch/write burst
[   16.397895] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   16.406196] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.538862] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   16.538869] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   16.538874] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   16.538889] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   16.538894] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: excluding 0x3000-0x30ff 0x3400-0x34ff
[   16.562658] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0xdfd00000-0xdfdfffff]
[   16.562666] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdfd00000-0xdfdfffff: excluding 0xdfd00000-0xdfd0ffff 0xdfdf0000-0xdfdfffff
[   16.562681] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x23ffffff pref]
[   16.562685] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x23ffffff: excluding 0x20000000-0x23ffffff
[   16.692183] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input5
[   16.702558] [drm] Initialized drm 1.1.0 20060810
[   16.710148] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[   16.718816] type=1400 audit(1303229716.503:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=636 comm="apparmor_parser"
[   16.719584] type=1400 audit(1303229716.503:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=636 comm="apparmor_parser"
[   16.720056] type=1400 audit(1303229716.507:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=636 comm="apparmor_parser"
[   16.732467] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   16.734439] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   16.735251] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   16.735946] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc80-0xc87 0xc90-0xc97
[   16.743266] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xf0000-0xfffff
[   16.743355] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   16.743422] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   16.743563] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.922520] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.922528] i915 0000:00:02.0: setting latency timer to 64
[   16.945214] [drm] set up 7M of stolen space
[   17.229918] type=1400 audit(1303229717.015:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=813 comm="apparmor_parser"
[   17.230693] type=1400 audit(1303229717.015:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=813 comm="apparmor_parser"
[   17.231118] type=1400 audit(1303229717.015:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=813 comm="apparmor_parser"
[   17.240037] type=1400 audit(1303229717.023:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=815 comm="apparmor_parser"
[   17.257735] type=1400 audit(1303229717.043:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=815 comm="apparmor_parser"
[   17.267596] type=1400 audit(1303229717.051:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=815 comm="apparmor_parser"
[   17.281297] type=1400 audit(1303229717.067:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=825 comm="apparmor_parser"
[   17.932756] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.933261] [drm] initialized overlay support
[   18.252034] Skipping EDID probe due to cached edid
[   18.676255] Console: switching to colour frame buffer device 128x48
[   18.680295] fb0: inteldrmfb frame buffer device
[   18.680297] drm: registered panic notifier
[   18.680967] Slow work thread pool: Starting up
[   18.681033] Slow work thread pool: Ready
[   18.681048] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.681270] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.681328]   alloc irq_desc for 41 on node -1
[   18.681331]   alloc kstat_irqs on node -1
[   18.681348] HDA Intel 0000:00:1b.0: irq 41 for MSI/MSI-X
[   18.681391] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.784920] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   18.785234] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   18.848067] Skipping EDID probe due to cached edid
[   18.969634] ppdev: user-space parallel port driver
[   19.212527] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   19.696112] Skipping EDID probe due to cached edid
[   20.140095] Skipping EDID probe due to cached edid
[   21.016065] Skipping EDID probe due to cached edid
[   21.468062] Skipping EDID probe due to cached edid
[   21.920060] Skipping EDID probe due to cached edid
[   22.372061] Skipping EDID probe due to cached edid
[   24.704949] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   37.412074] Skipping EDID probe due to cached edid
[   37.908120] Skipping EDID probe due to cached edid
jonathan@Xubuntu-Lap:~/Desktop$ 
```


The only output I got for "sudo lshw -C network" was this....

```
PCI (syfs)
```

And then it quickly disappeared.:confused:

---

### Post by LinXNut on 2011-04-19
Bump...Please I want to get this working! :P

---

### Post by josephmills on 2011-04-19
> **LinXNut said:**
> 


The only output I got for "sudo lshw -C network" was this....

```
PCI (syfs)
```

And then it quickly disappeared.:confused: you have to let it load

---

### Post by gradinaruvasile on 2011-04-19
Use the

```

lspci

```

command. That is quicker.

Also paste the output of 

```

ifconfig -a

```

command.

BTW i dont see anything relevant to network interfaces in your dmesg. Check if they are enabled in the BIOS.

---

### Post by mörgæs on 2011-04-20
Normally I don't answer a thread which has been bumped, but I shall do an exception.

I have a D610, and everything works out of the box with 10.10, also with the Intel 2200 wirefree card.

Always remember to have wired internet access while installing and applying the first batch of updates. This prevents countless problems later.

---

