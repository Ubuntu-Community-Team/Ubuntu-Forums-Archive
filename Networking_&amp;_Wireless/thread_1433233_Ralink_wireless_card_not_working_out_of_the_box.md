---
title: "Ralink wireless card not working out of the box"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by Ukebane on 2010-03-18
Edit: Problem solved, solution:

GRUB_CMDLINE_LINUX=***"acpi=force irqpoll"***

After installing Ubuntu 9.10 today I couldn't get my wireless card to work, I tried several things noted in other threads, but to no avail.

***lspci -v | less*** gives me the following:

```
00:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: RaLink Device 2561
        Flags: bus master, slow devsel, latency 64
        Memory at ffff8000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
        Kernel driver in use: rt61pci
        Kernel modules: rt61pci
```[I]

**ndiswrapper -l**[/I] gives no result

***iwconfig*** shows me the following:

```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```***lshw -C network*** shows me:

```
*-network:0 DISABLED    
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wmaster0
       version: 00
       serial: 00:10:60:64:61:19
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:0 memory:ffff8000-ffffffff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:97:6c:b1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=10.0.0.17 latency=128 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:e200(size=256) memory:d0000000-d00000ff
```Please help me out, if there's any diagnostics you want me to perform let me know.

---

### Post by chili555 on 2010-03-18
Please detach the ethernet cable, reboot and tell us if your wireless is still disabled. If so, run:```
dmesg > dmesg.txt
```After you plug in the cable and get a connection, go to your user directory and post dmesg.txt for our inspection. If the message is that it wants firmware, please do:```
sudo apt-get install linux-firmware
sudo rmmod -f rt61pci && sudo modprobe rt61pci
```Now do you have wireless?

---

### Post by Ukebane on 2010-03-18
I didn't get a message saying it requires firmware, I did find this however: 

[I][B][   16.904607] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).

[/B][/I]```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bfef000 (usable)
[    0.000000]  BIOS-e820: 000000003bff0000 - 000000003bffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bffffc0 - 000000003c000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3bfef max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 base 090000000 mask FFC000000 write-combining
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 base 0A0000000 mask FFE000000 write-combining
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003bfef000 (usable)
[    0.000000]  modified: 000000003bff0000 - 000000003bffffc0 (ACPI data)
[    0.000000]  modified: 000000003bffffc0 - 000000003c000000 (ACPI NVS)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2c8ea000 - 2d032e7e
[    0.000000] ACPI: RSDP 000e6010 00014 (v00 OID_00)
[    0.000000] ACPI: RSDT 3bffc2d0 0002C (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: FACP 3bfffb00 00074 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 3bffc310 037E2 (v01 INSYDE    PN800 00001000 INTL 02002036)
[    0.000000] ACPI: FACS 3bffffc0 00040
[    0.000000] ACPI: APIC 3bfffb90 00068 (v01 INSYDE APIC_000 30303030 0000 00010200)
[    0.000000] ACPI: BIOS age (400) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 71MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [002c8ea000 - 002d032e7e]          RAMDISK ==> [002c8ea000 - 002d032e7e]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008ae000 - 00008b11b0]              BRK ==> [00008ae000 - 00008b11b0]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003bfef
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bfef
[    0.000000] On node 0 totalpages: 245642
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 144 pages used for memmap
[    0.000000]   HighMem zone: 18273 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3c000000 (gap: 3c000000:c3f80000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1784000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243722
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=cde18976-7035-4db9-83dd-7ef36a01b12b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4914860 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003bfef)
[    0.000000] Memory: 953480k/982972k available (4578k kernel code, 28712k reserved, 2146k data, 540k init, 73668k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1492.693 MHz processor.
[    0.001475] Console: colour VGA+ 80x25
[    0.001481] console [tty0] enabled
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 2985.38 BogoMIPS (lpj=5970772)
[    0.004044] Security Framework initialized
[    0.004081] AppArmor: AppArmor initialized
[    0.004092] Mount-cache hash table entries: 512
[    0.004283] Initializing cgroup subsys ns
[    0.004292] Initializing cgroup subsys cpuacct
[    0.004298] Initializing cgroup subsys memory
[    0.004310] Initializing cgroup subsys freezer
[    0.004313] Initializing cgroup subsys net_cls
[    0.004338] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004341] CPU: L2 cache: 1024K
[    0.004349] mce: CPU supports 5 MCE banks
[    0.004361] CPU0: Thermal monitoring enabled (TM1)
[    0.004375] Performance Counters: p6 PMU driver.
[    0.004385] ... version:                 0
[    0.004388] ... bit width:               32
[    0.004390] ... generic counters:        2
[    0.004393] ... value mask:              00000000ffffffff
[    0.004396] ... max period:              000000007fffffff
[    0.004399] ... fixed-purpose counters:  0
[    0.004401] ... counter mask:            0000000000000003
[    0.004407] Checking 'hlt' instruction... OK.
[    0.021203] SMP alternatives: switching to UP code
[    0.028022] Freeing SMP alternatives: 20k freed
[    0.028147] weird, boot CPU (#0) not listed by the BIOS.
[    0.028152] SMP motherboard not detected.
[    0.136022] SMP disabled
[    0.136209] Brought up 1 CPUs
[    0.136213] Total of 1 processors activated (2985.38 BogoMIPS).
[    0.136233] CPU0 attaching NULL sched-domain.
[    0.136585] Booting paravirtualized kernel on bare hardware
[    0.136867] regulator: core version 0.5
[    0.136908] Time:  1:04:39  Date: 03/19/10
[    0.136982] NET: Registered protocol family 16
[    0.137172] EISA bus registered
[    0.137356] PCI: PCI BIOS revision 2.10 entry at 0xe9b04, last bus=1
[    0.137359] PCI: Using configuration type 1 for base access
[    0.138738] bio: create slab <bio-0> at 0
[    0.138819] ACPI: Interpreter disabled.
[    0.139000] SCSI subsystem initialized
[    0.139053] libata version 3.00 loaded.
[    0.139148] usbcore: registered new interface driver usbfs
[    0.139165] usbcore: registered new interface driver hub
[    0.139198] usbcore: registered new device driver usb
[    0.139339] PCI: Probing PCI hardware
[    0.139344] PCI: Probing PCI hardware (bus 00)
[    0.139406] pci 0000:00:00.0: reg 10 32bit mmio: [0xa0000000-0xa1ffffff]
[    0.139781] pci 0000:00:01.0: supports D1
[    0.139827] pci 0000:00:06.0: reg 10 32bit mmio: [0xffff8000-0xffffffff]
[    0.139954] pci 0000:00:10.0: reg 20 io port: [0x1200-0x121f]
[    0.139986] pci 0000:00:10.0: supports D1 D2
[    0.139990] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.139996] pci 0000:00:10.0: PME# disabled
[    0.140041] pci 0000:00:10.1: reg 20 io port: [0x1220-0x123f]
[    0.140074] pci 0000:00:10.1: supports D1 D2
[    0.140077] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140083] pci 0000:00:10.1: PME# disabled
[    0.140144] pci 0000:00:10.2: reg 20 io port: [0x1240-0x125f]
[    0.140177] pci 0000:00:10.2: supports D1 D2
[    0.140180] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140185] pci 0000:00:10.2: PME# disabled
[    0.140225] pci 0000:00:10.3: reg 10 32bit mmio: [0xf0000000-0xf00000ff]
[    0.140279] pci 0000:00:10.3: supports D1 D2
[    0.140282] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140288] pci 0000:00:10.3: PME# disabled
[    0.140369] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.140377] pci 0000:00:11.0: quirk: region 1000-107f claimed by vt8235 PM
[    0.140383] pci 0000:00:11.0: quirk: region 1400-140f claimed by vt8235 SMB
[    0.140464] pci 0000:00:11.1: reg 20 io port: [0x1100-0x110f]
[    0.140544] pci 0000:00:11.5: reg 10 io port: [0xe000-0xe0ff]
[    0.140600] pci 0000:00:11.5: supports D1 D2
[    0.140642] pci 0000:00:11.6: reg 10 io port: [0xe100-0xe1ff]
[    0.140738] pci 0000:00:12.0: reg 10 io port: [0xe200-0xe2ff]
[    0.140747] pci 0000:00:12.0: reg 14 32bit mmio: [0xd0000000-0xd00000ff]
[    0.140797] pci 0000:00:12.0: supports D1 D2
[    0.140800] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140806] pci 0000:00:12.0: PME# disabled
[    0.140873] pci 0000:01:00.0: reg 10 32bit mmio: [0x90000000-0x93ffffff]
[    0.140881] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xc0ffffff]
[    0.140906] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.140928] pci 0000:01:00.0: supports D1 D2
[    0.140975] pci 0000:00:01.0: bridge io port: [0xc000-0xdfff]
[    0.140981] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xcfffffff]
[    0.140988] pci 0000:00:01.0: bridge 32bit mmio pref: [0x90000000-0x9fffffff]
[    0.141597] pci 0000:00:11.0: VIA IRQ router [1106:3177]
[    0.141829] Bluetooth: Core ver 2.15
[    0.141884] NET: Registered protocol family 31
[    0.141886] Bluetooth: HCI device and connection manager initialized
[    0.141891] Bluetooth: HCI socket layer initialized
[    0.141894] NetLabel: Initializing
[    0.141897] NetLabel:  domain hash size = 128
[    0.141899] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.141920] NetLabel:  unlabeled traffic allowed by default
[    0.144677] pnp: PnP ACPI: disabled
[    0.144692] PnPBIOS: Scanning system for PnP BIOS support...
[    0.144807] PnPBIOS: Found PnP BIOS installation structure at 0xc00ff020
[    0.144811] PnPBIOS: PnP BIOS version 1.0, entry 0xeb000:0x3536, dseg 0xeb000
[    0.144821] PNPBIOS fault.. attempting recovery.
[    0.144824] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[    0.144827] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[    0.144830] PnPBIOS: Check with your vendor for an updated BIOS
[    0.144834] PnPBIOS: dev_node_info: unexpected status 0x3a
[    0.144837] PnPBIOS: Unable to get node info.  Aborting.
[    0.145108] AppArmor: AppArmor Filesystem Enabled
[    0.145156] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.145161] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.145169] pci 0000:00:01.0:   MEM window: 0xc0000000-0xcfffffff
[    0.145175] pci 0000:00:01.0:   PREFETCH window: 0x90000000-0x9fffffff
[    0.145197] pci 0000:00:01.0: setting latency timer to 64
[    0.145205] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.145208] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.145212] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.145216] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xcfffffff]
[    0.145220] pci_bus 0000:01: resource 2 pref mem [0x90000000-0x9fffffff]
[    0.145276] NET: Registered protocol family 2
[    0.145424] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.145885] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.148118] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.149293] TCP: Hash tables configured (established 131072 bind 65536)
[    0.149299] TCP reno registered
[    0.149539] NET: Registered protocol family 1
[    0.149666] Trying to unpack rootfs image as initramfs...
[    0.438568] Freeing initrd memory: 7459k freed
[    0.449578] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.449706] cpufreq-nforce2: No nForce2 chipset.
[    0.449735] Scanning for low memory corruption every 60 seconds
[    0.449937] audit: initializing netlink socket (disabled)
[    0.449990] type=2000 audit(1268960679.448:1): initialized
[    0.461919] highmem bounce pool size: 64 pages
[    0.461929] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.463832] VFS: Disk quotas dquot_6.5.2
[    0.463908] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.464697] fuse init (API version 7.12)
[    0.464800] msgmni has been set to 1733
[    0.465082] alg: No test for stdrng (krng)
[    0.465098] io scheduler noop registered
[    0.465101] io scheduler anticipatory registered
[    0.465104] io scheduler deadline registered
[    0.465158] io scheduler cfq registered (default)
[    0.465184] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.465268] pci 0000:01:00.0: Boot video device
[    0.465392] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.465425] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.465588] isapnp: Scanning for PnP cards...
[    0.819653] isapnp: No Plug & Play device found
[    0.821035] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.822478] brd: module loaded
[    0.823098] loop: module loaded
[    0.823207] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.823971] pata_via 0000:00:11.1: version 0.3.4
[    0.824170] scsi0 : pata_via
[    0.824290] scsi1 : pata_via
[    0.824338] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    0.824342] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    0.824831] Fixed MDIO Bus: probed
[    0.824879] PPP generic driver version 2.4.2
[    0.824999] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.825025] PCI: setting IRQ 10 as level-triggered
[    0.825031] ehci_hcd 0000:00:10.3: found PCI INT D -> IRQ 10
[    0.825088] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.825128] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.825182] ehci_hcd 0000:00:10.3: irq 10, io mem 0xf0000000
[    0.836020] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.836133] usb usb1: configuration #1 chosen from 1 choice
[    0.836173] hub 1-0:1.0: USB hub found
[    0.836185] hub 1-0:1.0: 6 ports detected
[    0.836260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.836285] uhci_hcd: USB Universal Host Controller Interface driver
[    0.836332] PCI: setting IRQ 11 as level-triggered
[    0.836338] uhci_hcd 0000:00:10.0: found PCI INT A -> IRQ 11
[    0.836372] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:12.0
[    0.836377] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:01:00.0
[    0.836389] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.836435] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.836462] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[    0.836559] usb usb2: configuration #1 chosen from 1 choice
[    0.836592] hub 2-0:1.0: USB hub found
[    0.836602] hub 2-0:1.0: 2 ports detected
[    0.836662] PCI: setting IRQ 7 as level-triggered
[    0.836667] uhci_hcd 0000:00:10.1: found PCI INT B -> IRQ 7
[    0.836709] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.836749] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.836775] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[    0.836892] usb usb3: configuration #1 chosen from 1 choice
[    0.836925] hub 3-0:1.0: USB hub found
[    0.836934] hub 3-0:1.0: 2 ports detected
[    0.836990] PCI: setting IRQ 5 as level-triggered
[    0.836995] uhci_hcd 0000:00:10.2: found PCI INT C -> IRQ 5
[    0.837025] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.5
[    0.837030] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.6
[    0.837043] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.837087] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.837113] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[    0.837210] usb usb4: configuration #1 chosen from 1 choice
[    0.837243] hub 4-0:1.0: USB hub found
[    0.837253] hub 4-0:1.0: 2 ports detected
[    0.837369] PNP: No PS/2 controller found. Probing ports directly.
[    0.847836] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.853045] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.853054] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.853058] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.853061] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.853065] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.853138] mice: PS/2 mouse device common for all mice
[    0.853261] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    0.853292] rtc0: alarms up to one day, 114 bytes nvram
[    0.853430] device-mapper: uevent: version 1.0.3
[    0.853555] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.853654] device-mapper: multipath: version 1.1.0 loaded
[    0.853658] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.853821] EISA: Probing bus 0 at eisa.0
[    0.853830] Cannot allocate resource for EISA slot 1
[    0.853863] EISA: Detected 0 cards.
[    0.853921] cpuidle: using governor ladder
[    0.853924] cpuidle: using governor menu
[    0.854561] TCP cubic registered
[    0.854774] NET: Registered protocol family 10
[    0.855335] lo: Disabled Privacy Extensions
[    0.855731] NET: Registered protocol family 17
[    0.855756] Bluetooth: L2CAP ver 2.13
[    0.855759] Bluetooth: L2CAP socket layer initialized
[    0.855763] Bluetooth: SCO (Voice Link) ver 0.6
[    0.855765] Bluetooth: SCO socket layer initialized
[    0.855834] Bluetooth: RFCOMM TTY layer initialized
[    0.855838] Bluetooth: RFCOMM socket layer initialized
[    0.855841] Bluetooth: RFCOMM ver 1.11
[    0.855867] Using IPI No-Shortcut mode
[    0.855958] PM: Resume from disk failed.
[    0.855977] registered taskstats version 1
[    0.856119]   Magic number: 2:25:54
[    0.856230] rtc_cmos rtc_cmos: setting system clock to 2010-03-19 01:04:40 UTC (1268960680)
[    0.856235] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.856237] EDD information not available.
[    0.861493] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.988592] ata1.00: ATA-6: ST980811A, 3.ALA, max UDMA/100
[    0.988596] ata1.00: 156301488 sectors, multi 16: LBA48 
[    1.004488] ata1.00: configured for UDMA/100
[    1.004715] scsi 0:0:0:0: Direct-Access     ATA      ST980811A        3.AL PQ: 0 ANSI: 5
[    1.004875] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.004931] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.004994] sd 0:0:0:0: [sda] Write Protect is off
[    1.004998] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.005030] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.005203]  sda: sda1 sda2 < sda5 >
[    1.048721] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.168417] ata2.00: ATAPI: Slimtype DVDRW SOSW-833S, V9S2, max UDMA/33
[    1.184313] ata2.00: configured for UDMA/33
[    1.185257] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-833S  V9S2 PQ: 0 ANSI: 5
[    1.188314] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.188319] Uniform CD-ROM driver Revision: 3.20
[    1.188418] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.188484] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.188515] Freeing unused kernel memory: 540k freed
[    1.188976] Write protecting the kernel text: 4580k
[    1.189025] Write protecting the kernel read-only data: 1840k
[    1.348943] Linux agpgart interface v0.103
[    1.382243] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[    1.385152] agpgart-via 0000:00:00.0: AGP aperture is 32M @ 0xa0000000
[    1.423405] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.423488] via-rhine 0000:00:12.0: found PCI INT A -> IRQ 11
[    1.423511] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:10.0
[    1.423532] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:01:00.0
[    1.448058] eth0: VIA Rhine II at 0xd0000000, 00:40:d0:97:6c:b1, IRQ 11.
[    1.448775] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    2.635478] PM: Starting manual resume from disk
[    2.635485] PM: Resume from partition 8:5
[    2.635488] PM: Checking hibernation image.
[    2.635708] PM: Resume from disk failed.
[    2.663051] EXT4-fs (sda1): barriers enabled
[    2.680545] kjournald2 starting: pid 302, dev sda1:8, commit interval 5 seconds
[    2.680593] EXT4-fs (sda1): delayed allocation enabled
[    2.680598] EXT4-fs: file extents enabled
[    2.691984] EXT4-fs: mballoc enabled
[    2.692015] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.549329] type=1505 audit(1268960683.191:2): operation="profile_load" pid=326 name=/usr/share/gdm/guest-session/Xsession
[    3.585109] type=1505 audit(1268960683.227:3): operation="profile_load" pid=327 name=/sbin/dhclient3
[    3.585957] type=1505 audit(1268960683.227:4): operation="profile_load" pid=327 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.586422] type=1505 audit(1268960683.227:5): operation="profile_load" pid=327 name=/usr/lib/connman/scripts/dhclient-script
[    3.675931] type=1505 audit(1268960683.315:6): operation="profile_load" pid=328 name=/usr/bin/evince
[    3.690306] type=1505 audit(1268960683.331:7): operation="profile_load" pid=328 name=/usr/bin/evince-previewer
[    3.698711] type=1505 audit(1268960683.339:8): operation="profile_load" pid=328 name=/usr/bin/evince-thumbnailer
[    3.719108] type=1505 audit(1268960683.359:9): operation="profile_load" pid=330 name=/usr/lib/cups/backend/cups-pdf
[    3.720139] type=1505 audit(1268960683.363:10): operation="profile_load" pid=330 name=/usr/sbin/cupsd
[   15.640763] udev: starting version 147
[   15.655942] Adding 2819368k swap on /dev/sda5.  Priority:-1 extents:1 across:2819368k 
[   15.799853] irda_init()
[   15.799882] NET: Registered protocol family 23
[   15.844926] EXT4-fs (sda1): internal journal on sda1:8
[   15.974054] cfg80211: Calling CRDA to update world regulatory domain
[   16.039942] cfg80211: World regulatory domain updated:
[   16.039949]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.039953]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.039957]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.039961]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.039965]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.039969]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.118542] rt61pci 0000:00:06.0: enabling device (0000 -> 0002)
[   16.118555] rt61pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   16.118565] rt61pci 0000:00:06.0: setting latency timer to 64
[   16.316213] lp: driver loaded but no devices found
[   16.318275] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.350622] phy0: Selected rate control algorithm 'minstrel'
[   16.351492] Registered led device: rt61pci-phy0::radio
[   16.351513] Registered led device: rt61pci-phy0::assoc
[   16.351619] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.351665] VIA 82xx Modem 0000:00:11.6: found PCI INT C -> IRQ 5
[   16.351692] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:10.2
[   16.351704] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:11.5
[   16.745718] rt61pci 0000:00:06.0: firmware: requesting rt2561s.bin
[   16.851155] __ratelimit: 3 callbacks suppressed
[   16.851161] type=1505 audit(1268957096.492:12): operation="profile_replace" pid=774 name=/usr/share/gdm/guest-session/Xsession
[   16.853957] type=1505 audit(1268957096.496:13): operation="profile_replace" pid=775 name=/sbin/dhclient3
[   16.854811] type=1505 audit(1268957096.496:14): operation="profile_replace" pid=775 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   16.855499] type=1505 audit(1268957096.496:15): operation="profile_replace" pid=775 name=/usr/lib/connman/scripts/dhclient-script
[   16.864469] type=1505 audit(1268957096.504:16): operation="profile_replace" pid=776 name=/usr/bin/evince
[   16.864693] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).
[   16.867890] eth0: link down
[   16.868161] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.904607] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).
[   16.909609] type=1505 audit(1268957096.552:17): operation="profile_replace" pid=776 name=/usr/bin/evince-previewer
[   16.922021] type=1505 audit(1268957096.564:18): operation="profile_replace" pid=776 name=/usr/bin/evince-thumbnailer
[   16.942803] type=1505 audit(1268957096.584:19): operation="profile_replace" pid=783 name=/usr/lib/cups/backend/cups-pdf
[   16.943817] type=1505 audit(1268957096.584:20): operation="profile_replace" pid=783 name=/usr/sbin/cupsd
[   16.954647] type=1505 audit(1268957096.596:21): operation="profile_replace" pid=786 name=/usr/sbin/tcpdump
[   17.100632] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   17.237119] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b3, caps: 0xa04713/0x200000
[   17.308231] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input2
[   17.516341] ppdev: user-space parallel port driver
[   17.622271] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   17.623474] VIA 82xx Audio 0000:00:11.5: found PCI INT C -> IRQ 5
[   17.623507] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:10.2
[   17.623521] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:11.6
[   17.623670] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   19.410113] [drm] Initialized drm 1.1.0 20060810
[   19.414493] pci 0000:01:00.0: found PCI INT A -> IRQ 11
[   19.414514] pci 0000:01:00.0: sharing IRQ 11 with 0000:00:10.0
[   19.414533] pci 0000:01:00.0: sharing IRQ 11 with 0000:00:12.0
[   19.414760] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   19.419496] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   19.419525] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   19.419534] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[   19.419618] pci 0000:01:00.0: putting AGP V2 device into 0x mode

```

And still no wireless I'm afraid.
Thank you for the quick reply.

---

### Post by chili555 on 2010-03-18
dmesg has given us a hint:> rt61pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirqLet's edit "/etc/default/grub":
```
sudo gedit /etc/default/grub
```

Change this line:```
GRUB_CMDLINE_LINUX=""
```
To this:

```
GRUB_CMDLINE_LINUX="pci=biosirq"
```

After saving changes to the file, update your GRUB configuration by typing the following into the command line:
```
sudo update-grub
```Reboot and let's see if it's healed.

---

### Post by Ukebane on 2010-03-18
Performed the actions listed above, the only change is that the network manager now shows ***Device not ready***.

---

### Post by chili555 on 2010-03-18
What does *iwconfig* say? And how about?```
dmesg | grep rt61
```Thanks.

---

### Post by Ukebane on 2010-03-18
***iwconfig***:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

***dmesg | grep rt61***:

```
[   17.295123] rt61pci 0000:00:06.0: enabling device (0000 -> 0002)
[   17.295136] rt61pci 0000:00:06.0: can't find IRQ for PCI INT A
[   17.295146] rt61pci 0000:00:06.0: setting latency timer to 64
[   17.332443] Registered led device: rt61pci-phy0::radio
[   17.332467] Registered led device: rt61pci-phy0::assoc
[   17.376037] rt61pci 0000:00:06.0: firmware: requesting rt2561s.bin

```

---

### Post by startrekker on 2010-03-18
You might try the driver on Ralink's page.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

look for your model

I've got a different model but I used the instructions here:

[http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/](http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/)

I've got WiFi now. :)

---

### Post by Ukebane on 2010-03-18
Thanks for the help, but when I attempt to compile the driver I get tons of errors.

```

root@NoFailxD2:/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module# make
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.o
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;rt61_get_drvinfo&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:78: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:78: warning: unused variable &#8216;pAd&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;rt61_get_regs_len&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:97: warning: no return statement in function returning non-void
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;rt61_get_regs&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:103: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:104: warning: unused variable &#8216;counter&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:103: warning: unused variable &#8216;pAd&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;rt61_ethtool_get_link&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:120: warning: unused variable &#8216;pAd&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:130: warning: no return statement in function returning non-void
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;rt61_get_eeprom_len&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:139: warning: no return statement in function returning non-void
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;rt61_get_eeprom&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:145: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:146: warning: unused variable &#8216;counter&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:145: warning: unused variable &#8216;pAd&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:159: warning: no return statement in function returning non-void
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: At top level:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:169: warning: initialization from incompatible pointer type
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;RT61_probe&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:238: warning: assignment discards qualifiers from pointer target type
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:287: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:290: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:290: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:290: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:290: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:294: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:305: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:306: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:307: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:308: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:317: error: &#8216;struct net_device&#8217; has no member named &#8216;set_multicast_list&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:318: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:328: error: &#8216;struct net_device&#8217; has no member named &#8216;validate_addr&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:344: warning: ISO C90 forbids mixed declarations and code
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;RT61_open&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:422: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:472: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
include/linux/interrupt.h:116: note: expected &#8216;irq_handler_t&#8217; but argument is of type &#8216;enum irqreturn_t (*)(int,  void *, struct pt_regs *)&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;RTMPSendPackets&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:627: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;RTMPIsr&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:713: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;RT61_get_wireless_stats&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:825: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;RT61_get_ether_stats&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:873: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;RT61_close&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:942: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c: In function &#8216;RT61_remove_one&#8217;:
/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.c:1002: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
make[2]: *** [/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/ukebane/Downloads/2009_0123_RT61_Linux_STA_v1.1.2.3/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [all] Error 2

```

---

### Post by startrekker on 2010-03-18
did you do this step

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by Ukebane on 2010-03-19
Yes I did do that and it gave me the same as it's giving me now:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.31-20-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Ukebane on 2010-03-19
Quick update:

I tried getting ndiswrapper to work, but that only resulted in my wireless card not being detected at all, reverted to previous state.

Update 2:

I ran ***airdriver-ng installed ***to see which drivers I had installed:

```

airdriver-ng installed
Found following stacks installed:
2. mac80211

Found following drivers installed:
ERROR: modinfo: could not open kernel/drivers/net/wireless/adm8211.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/adm8211.ko: No such file or directory
3. Atmel at76c50x - IEEE80211
4. Atmel at76_usb - IEEE80211
7. Cisco/Aironet 802.11 - IEEE80211 Softmac
8. HostAP - IEEE80211
9. Intel Pro Wireless 2100 B - IEEE80211
10. Intel Pro Wireless 2200 (B/G)/2915 (A/B/G) - IEEE80211
ERROR: modinfo: could not open kernel/drivers/net/wireless/iwlwifi/iwl3945.ko: No such file or directory
17. Prism54 - IEEE80211
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt2400pci.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt2400pci.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt2500pci.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt2500pci.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt2500usb.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt2500usb.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt61pci.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt61pci.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt73usb.ko: No such file or directory
ERROR: modinfo: could not open kernel/drivers/net/wireless/rt2x00/rt73usb.ko: No such file or directory
36. Realtek rtl8187 - mac80211
38. Xircom Creditcard Netwave - IEEE80211
39. ZyDAS 1201 - IEEE80211 Softmac
41. ZyDAS 1211rw - IEEE80211 Softmac
43. NDIS Wrapper

Found following firmwares installed:
0. ACX100/111 - IEEE80211
3. Atmel at76c50x - IEEE80211
4. Atmel at76_usb - IEEE80211
9. Intel Pro Wireless 2100 B - IEEE80211
10. Intel Pro Wireless 2200 (B/G)/2915 (A/B/G) - IEEE80211
39. ZyDAS 1201 - IEEE80211 Softmac
40. ZyDAS 1211 - IEEE80211 Softmac
41. ZyDAS 1211rw - IEEE80211 Softmac

```

Looks like I've got some errors in there that I don't know what to do with.

---

### Post by Ukebane on 2010-03-19
Tried reinstalling Ubuntu 9.10 completely, got an error message in the dmesg.

***Error message***
```

[   32.835470] rt61pci 0000:00:06.0: firmware: requesting rt2561s.bin
[   32.969366] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).
[   33.016238] eth0: link down
[   33.016509] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.217707] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).

```

***Entire dmesg***
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bfef000 (usable)
[    0.000000]  BIOS-e820: 000000003bff0000 - 000000003bffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bffffc0 - 000000003c000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3bfef max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 base 090000000 mask FFC000000 write-combining
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 base 0A0000000 mask FFE000000 write-combining
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003bfef000 (usable)
[    0.000000]  modified: 000000003bff0000 - 000000003bffffc0 (ACPI data)
[    0.000000]  modified: 000000003bffffc0 - 000000003c000000 (ACPI NVS)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2c8e8000 - 2d032e10
[    0.000000] ACPI: RSDP 000e6010 00014 (v00 OID_00)
[    0.000000] ACPI: RSDT 3bffc2d0 0002C (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: FACP 3bfffb00 00074 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 3bffc310 037E2 (v01 INSYDE    PN800 00001000 INTL 02002036)
[    0.000000] ACPI: FACS 3bffffc0 00040
[    0.000000] ACPI: APIC 3bfffb90 00068 (v01 INSYDE APIC_000 30303030 0000 00010200)
[    0.000000] ACPI: BIOS age (400) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 71MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [002c8e8000 - 002d032e10]          RAMDISK ==> [002c8e8000 - 002d032e10]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac1b0]              BRK ==> [00008a9000 - 00008ac1b0]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003bfef
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bfef
[    0.000000] On node 0 totalpages: 245642
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 144 pages used for memmap
[    0.000000]   HighMem zone: 18273 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3c000000 (gap: 3c000000:c3f80000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1784000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243722
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=efc5e601-f1a7-44e7-bfba-e0ddaa891071 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4914860 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003bfef)
[    0.000000] Memory: 953500k/982972k available (4565k kernel code, 28700k reserved, 2143k data, 540k init, 73668k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1492.318 MHz processor.
[    0.001476] Console: colour VGA+ 80x25
[    0.001482] console [tty0] enabled
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 2984.63 BogoMIPS (lpj=5969272)
[    0.004045] Security Framework initialized
[    0.004083] AppArmor: AppArmor initialized
[    0.004094] Mount-cache hash table entries: 512
[    0.004286] Initializing cgroup subsys ns
[    0.004295] Initializing cgroup subsys cpuacct
[    0.004302] Initializing cgroup subsys memory
[    0.004314] Initializing cgroup subsys freezer
[    0.004317] Initializing cgroup subsys net_cls
[    0.004341] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004345] CPU: L2 cache: 1024K
[    0.004352] mce: CPU supports 5 MCE banks
[    0.004364] CPU0: Thermal monitoring enabled (TM1)
[    0.004377] Performance Counters: p6 PMU driver.
[    0.004387] ... version:                 0
[    0.004389] ... bit width:               32
[    0.004392] ... generic counters:        2
[    0.004394] ... value mask:              00000000ffffffff
[    0.004397] ... max period:              000000007fffffff
[    0.004400] ... fixed-purpose counters:  0
[    0.004402] ... counter mask:            0000000000000003
[    0.004409] Checking 'hlt' instruction... OK.
[    0.021200] SMP alternatives: switching to UP code
[    0.028023] Freeing SMP alternatives: 19k freed
[    0.028147] weird, boot CPU (#0) not listed by the BIOS.
[    0.028152] SMP motherboard not detected.
[    0.136023] SMP disabled
[    0.136202] Brought up 1 CPUs
[    0.136206] Total of 1 processors activated (2984.63 BogoMIPS).
[    0.136225] CPU0 attaching NULL sched-domain.
[    0.136573] Booting paravirtualized kernel on bare hardware
[    0.136857] regulator: core version 0.5
[    0.136899] Time: 15:02:15  Date: 03/19/10
[    0.136974] NET: Registered protocol family 16
[    0.137170] EISA bus registered
[    0.137358] PCI: PCI BIOS revision 2.10 entry at 0xe9b04, last bus=1
[    0.137362] PCI: Using configuration type 1 for base access
[    0.138731] bio: create slab <bio-0> at 0
[    0.138812] ACPI: Interpreter disabled.
[    0.138994] SCSI subsystem initialized
[    0.139048] libata version 3.00 loaded.
[    0.139143] usbcore: registered new interface driver usbfs
[    0.139164] usbcore: registered new interface driver hub
[    0.139197] usbcore: registered new device driver usb
[    0.139339] PCI: Probing PCI hardware
[    0.139344] PCI: Probing PCI hardware (bus 00)
[    0.139405] pci 0000:00:00.0: reg 10 32bit mmio: [0xa0000000-0xa1ffffff]
[    0.139779] pci 0000:00:01.0: supports D1
[    0.139824] pci 0000:00:06.0: reg 10 32bit mmio: [0xffff8000-0xffffffff]
[    0.139951] pci 0000:00:10.0: reg 20 io port: [0x1200-0x121f]
[    0.139985] pci 0000:00:10.0: supports D1 D2
[    0.139988] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.139994] pci 0000:00:10.0: PME# disabled
[    0.140041] pci 0000:00:10.1: reg 20 io port: [0x1220-0x123f]
[    0.140074] pci 0000:00:10.1: supports D1 D2
[    0.140077] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140083] pci 0000:00:10.1: PME# disabled
[    0.140144] pci 0000:00:10.2: reg 20 io port: [0x1240-0x125f]
[    0.140177] pci 0000:00:10.2: supports D1 D2
[    0.140180] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140186] pci 0000:00:10.2: PME# disabled
[    0.140225] pci 0000:00:10.3: reg 10 32bit mmio: [0xf0000000-0xf00000ff]
[    0.140279] pci 0000:00:10.3: supports D1 D2
[    0.140282] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140288] pci 0000:00:10.3: PME# disabled
[    0.140369] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.140378] pci 0000:00:11.0: quirk: region 1000-107f claimed by vt8235 PM
[    0.140384] pci 0000:00:11.0: quirk: region 1400-140f claimed by vt8235 SMB
[    0.140465] pci 0000:00:11.1: reg 20 io port: [0x1100-0x110f]
[    0.140545] pci 0000:00:11.5: reg 10 io port: [0xe000-0xe0ff]
[    0.140601] pci 0000:00:11.5: supports D1 D2
[    0.140643] pci 0000:00:11.6: reg 10 io port: [0xe100-0xe1ff]
[    0.140738] pci 0000:00:12.0: reg 10 io port: [0xe200-0xe2ff]
[    0.140748] pci 0000:00:12.0: reg 14 32bit mmio: [0xd0000000-0xd00000ff]
[    0.140797] pci 0000:00:12.0: supports D1 D2
[    0.140801] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.140806] pci 0000:00:12.0: PME# disabled
[    0.140874] pci 0000:01:00.0: reg 10 32bit mmio: [0x90000000-0x93ffffff]
[    0.140882] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xc0ffffff]
[    0.140907] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.140929] pci 0000:01:00.0: supports D1 D2
[    0.140976] pci 0000:00:01.0: bridge io port: [0xc000-0xdfff]
[    0.140982] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xcfffffff]
[    0.140988] pci 0000:00:01.0: bridge 32bit mmio pref: [0x90000000-0x9fffffff]
[    0.141591] pci 0000:00:11.0: VIA IRQ router [1106:3177]
[    0.141827] Bluetooth: Core ver 2.15
[    0.141881] NET: Registered protocol family 31
[    0.141884] Bluetooth: HCI device and connection manager initialized
[    0.141888] Bluetooth: HCI socket layer initialized
[    0.141892] NetLabel: Initializing
[    0.141894] NetLabel:  domain hash size = 128
[    0.141896] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.141916] NetLabel:  unlabeled traffic allowed by default
[    0.144614] pnp: PnP ACPI: disabled
[    0.144629] PnPBIOS: Scanning system for PnP BIOS support...
[    0.144741] PnPBIOS: Found PnP BIOS installation structure at 0xc00ff020
[    0.144746] PnPBIOS: PnP BIOS version 1.0, entry 0xeb000:0x3536, dseg 0xeb000
[    0.144755] PNPBIOS fault.. attempting recovery.
[    0.144758] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[    0.144761] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[    0.144764] PnPBIOS: Check with your vendor for an updated BIOS
[    0.144768] PnPBIOS: dev_node_info: unexpected status 0x3a
[    0.144771] PnPBIOS: Unable to get node info.  Aborting.
[    0.145040] AppArmor: AppArmor Filesystem Enabled
[    0.145089] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.145093] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.145102] pci 0000:00:01.0:   MEM window: 0xc0000000-0xcfffffff
[    0.145108] pci 0000:00:01.0:   PREFETCH window: 0x90000000-0x9fffffff
[    0.145130] pci 0000:00:01.0: setting latency timer to 64
[    0.145137] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.145141] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.145145] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.145149] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xcfffffff]
[    0.145152] pci_bus 0000:01: resource 2 pref mem [0x90000000-0x9fffffff]
[    0.145214] NET: Registered protocol family 2
[    0.145357] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.145815] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.147945] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.149212] TCP: Hash tables configured (established 131072 bind 65536)
[    0.149219] TCP reno registered
[    0.149491] NET: Registered protocol family 1
[    0.149620] Trying to unpack rootfs image as initramfs...
[    0.438879] Freeing initrd memory: 7467k freed
[    0.449888] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.450014] cpufreq-nforce2: No nForce2 chipset.
[    0.450047] Scanning for low memory corruption every 60 seconds
[    0.450239] audit: initializing netlink socket (disabled)
[    0.450299] type=2000 audit(1269010935.448:1): initialized
[    0.462560] highmem bounce pool size: 64 pages
[    0.462570] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.464487] VFS: Disk quotas dquot_6.5.2
[    0.464564] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.465327] fuse init (API version 7.12)
[    0.465434] msgmni has been set to 1733
[    0.465717] alg: No test for stdrng (krng)
[    0.465732] io scheduler noop registered
[    0.465735] io scheduler anticipatory registered
[    0.465738] io scheduler deadline registered
[    0.465792] io scheduler cfq registered (default)
[    0.465819] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.465903] pci 0000:01:00.0: Boot video device
[    0.466028] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.466062] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.466227] isapnp: Scanning for PnP cards...
[    0.820275] isapnp: No Plug & Play device found
[    0.821657] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.823096] brd: module loaded
[    0.823712] loop: module loaded
[    0.823817] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.824611] pata_via 0000:00:11.1: version 0.3.4
[    0.824786] scsi0 : pata_via
[    0.824899] scsi1 : pata_via
[    0.824950] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    0.824954] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    0.825452] Fixed MDIO Bus: probed
[    0.825501] PPP generic driver version 2.4.2
[    0.825623] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.825649] PCI: setting IRQ 10 as level-triggered
[    0.825655] ehci_hcd 0000:00:10.3: found PCI INT D -> IRQ 10
[    0.825711] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.825789] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.825842] ehci_hcd 0000:00:10.3: irq 10, io mem 0xf0000000
[    0.836194] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.836307] usb usb1: configuration #1 chosen from 1 choice
[    0.836348] hub 1-0:1.0: USB hub found
[    0.836360] hub 1-0:1.0: 6 ports detected
[    0.836439] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.836466] uhci_hcd: USB Universal Host Controller Interface driver
[    0.836513] PCI: setting IRQ 11 as level-triggered
[    0.836518] uhci_hcd 0000:00:10.0: found PCI INT A -> IRQ 11
[    0.836553] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:12.0
[    0.836558] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:01:00.0
[    0.836569] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.836607] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.836635] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[    0.836732] usb usb2: configuration #1 chosen from 1 choice
[    0.836766] hub 2-0:1.0: USB hub found
[    0.836776] hub 2-0:1.0: 2 ports detected
[    0.836837] PCI: setting IRQ 7 as level-triggered
[    0.836843] uhci_hcd 0000:00:10.1: found PCI INT B -> IRQ 7
[    0.836884] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.836928] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.836954] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[    0.837074] usb usb3: configuration #1 chosen from 1 choice
[    0.837108] hub 3-0:1.0: USB hub found
[    0.837116] hub 3-0:1.0: 2 ports detected
[    0.837176] PCI: setting IRQ 5 as level-triggered
[    0.837181] uhci_hcd 0000:00:10.2: found PCI INT C -> IRQ 5
[    0.837211] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.5
[    0.837216] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.6
[    0.837229] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.837271] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.837297] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[    0.837395] usb usb4: configuration #1 chosen from 1 choice
[    0.837429] hub 4-0:1.0: USB hub found
[    0.837438] hub 4-0:1.0: 2 ports detected
[    0.837557] PNP: No PS/2 controller found. Probing ports directly.
[    0.848043] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.853050] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.853059] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.853063] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.853067] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.853071] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.853140] mice: PS/2 mouse device common for all mice
[    0.853258] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    0.853288] rtc0: alarms up to one day, 114 bytes nvram
[    0.853423] device-mapper: uevent: version 1.0.3
[    0.853543] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.853639] device-mapper: multipath: version 1.1.0 loaded
[    0.853643] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.853809] EISA: Probing bus 0 at eisa.0
[    0.853818] Cannot allocate resource for EISA slot 1
[    0.853851] EISA: Detected 0 cards.
[    0.853911] cpuidle: using governor ladder
[    0.853914] cpuidle: using governor menu
[    0.854552] TCP cubic registered
[    0.854763] NET: Registered protocol family 10
[    0.855319] lo: Disabled Privacy Extensions
[    0.855711] NET: Registered protocol family 17
[    0.855739] Bluetooth: L2CAP ver 2.13
[    0.855741] Bluetooth: L2CAP socket layer initialized
[    0.855745] Bluetooth: SCO (Voice Link) ver 0.6
[    0.855747] Bluetooth: SCO socket layer initialized
[    0.855801] Bluetooth: RFCOMM TTY layer initialized
[    0.855805] Bluetooth: RFCOMM socket layer initialized
[    0.855807] Bluetooth: RFCOMM ver 1.11
[    0.855833] Using IPI No-Shortcut mode
[    0.855913] PM: Resume from disk failed.
[    0.855938] registered taskstats version 1
[    0.856065]   Magic number: 2:959:32
[    0.856165] rtc_cmos rtc_cmos: setting system clock to 2010-03-19 15:02:16 UTC (1269010936)
[    0.856171] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.856173] EDD information not available.
[    0.861066] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.988834] ata1.00: ATA-6: ST980811A, 3.ALA, max UDMA/100
[    0.988838] ata1.00: 156301488 sectors, multi 16: LBA48 
[    1.004680] ata1.00: configured for UDMA/100
[    1.004889] scsi 0:0:0:0: Direct-Access     ATA      ST980811A        3.AL PQ: 0 ANSI: 5
[    1.005069] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.005125] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.005188] sd 0:0:0:0: [sda] Write Protect is off
[    1.005192] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.005224] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.005398]  sda: sda1 sda2 < sda5 >
[    1.056386] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.168674] ata2.00: ATAPI: Slimtype DVDRW SOSW-833S, V9S2, max UDMA/33
[    1.184573] ata2.00: configured for UDMA/33
[    1.185519] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-833S  V9S2 PQ: 0 ANSI: 5
[    1.188537] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.188542] Uniform CD-ROM driver Revision: 3.20
[    1.188641] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.188705] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.188735] Freeing unused kernel memory: 540k freed
[    1.189199] Write protecting the kernel text: 4568k
[    1.189248] Write protecting the kernel read-only data: 1836k
[    1.383683] Linux agpgart interface v0.103
[    1.387377] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[    1.395534] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.418888] agpgart-via 0000:00:00.0: AGP aperture is 32M @ 0xa0000000
[    1.419168] via-rhine 0000:00:12.0: found PCI INT A -> IRQ 11
[    1.419192] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:10.0
[    1.419213] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:01:00.0
[    1.424421] eth0: VIA Rhine II at 0xd0000000, 00:40:d0:97:6c:b1, IRQ 11.
[    1.425136] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    2.666309] PM: Starting manual resume from disk
[    2.666316] PM: Resume from partition 8:5
[    2.666319] PM: Checking hibernation image.
[    2.666534] PM: Resume from disk failed.
[    2.693282] EXT4-fs (sda1): barriers enabled
[    2.710775] kjournald2 starting: pid 311, dev sda1:8, commit interval 5 seconds
[    2.710796] EXT4-fs (sda1): delayed allocation enabled
[    2.710801] EXT4-fs: file extents enabled
[    2.722245] EXT4-fs: mballoc enabled
[    2.722270] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.560839] type=1505 audit(1269010939.200:2): operation="profile_load" pid=334 name=/usr/share/gdm/guest-session/Xsession
[    3.778743] type=1505 audit(1269010939.420:3): operation="profile_load" pid=335 name=/sbin/dhclient3
[    3.778865] type=1505 audit(1269010939.420:4): operation="profile_load" pid=335 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.778933] type=1505 audit(1269010939.420:5): operation="profile_load" pid=335 name=/usr/lib/connman/scripts/dhclient-script
[   17.931824] type=1505 audit(1269010953.572:6): operation="profile_load" pid=336 name=/usr/bin/evince
[   17.933279] type=1505 audit(1269010953.576:7): operation="profile_load" pid=336 name=/usr/bin/evince-previewer
[   17.934497] type=1505 audit(1269010953.576:8): operation="profile_load" pid=336 name=/usr/bin/evince-thumbnailer
[   18.331538] type=1505 audit(1269010953.972:9): operation="profile_load" pid=338 name=/usr/lib/cups/backend/cups-pdf
[   18.331851] type=1505 audit(1269010953.972:10): operation="profile_load" pid=338 name=/usr/sbin/cupsd
[   18.445130] type=1505 audit(1269010954.085:11): operation="profile_load" pid=339 name=/usr/sbin/tcpdump
[   19.306476] Adding 2819368k swap on /dev/sda5.  Priority:-1 extents:1 across:2819368k 
[   19.804691] EXT4-fs (sda1): internal journal on sda1:8
[   19.914176] udev: starting version 147
[   22.776461] cfg80211: Calling CRDA to update world regulatory domain
[   22.968384] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b3, caps: 0xa04713/0x200000
[   23.019055] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input2
[   23.221330] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.414391] cfg80211: World regulatory domain updated:
[   23.414398]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.414402]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.414406]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.414410]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.414414]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.414418]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.521947] lp: driver loaded but no devices found
[   23.773318] type=1505 audit(1269010959.414:12): operation="profile_replace" pid=648 name=/usr/share/gdm/guest-session/Xsession
[   24.053881] type=1505 audit(1269010959.694:13): operation="profile_replace" pid=649 name=/sbin/dhclient3
[   24.054108] type=1505 audit(1269010959.694:14): operation="profile_replace" pid=649 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   24.054230] type=1505 audit(1269010959.694:15): operation="profile_replace" pid=649 name=/usr/lib/connman/scripts/dhclient-script
[   24.492697] irda_init()
[   24.492729] NET: Registered protocol family 23
[   24.670296] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.403632] rt61pci 0000:00:06.0: enabling device (0000 -> 0002)
[   25.403645] rt61pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   25.403655] rt61pci 0000:00:06.0: setting latency timer to 64
[   25.779766] phy0: Selected rate control algorithm 'minstrel'
[   25.780639] Registered led device: rt61pci-phy0::radio
[   25.780659] Registered led device: rt61pci-phy0::assoc
[   26.428275] VIA 82xx Modem 0000:00:11.6: found PCI INT C -> IRQ 5
[   26.428305] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:10.2
[   26.428316] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:11.5
[   27.187663] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   27.696041] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   27.697396] VIA 82xx Audio 0000:00:11.5: found PCI INT C -> IRQ 5
[   27.697429] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:10.2
[   27.697442] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:11.6
[   27.697592] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   32.835470] rt61pci 0000:00:06.0: firmware: requesting rt2561s.bin
[   32.969366] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).
[   33.016238] eth0: link down
[   33.016509] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.217707] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).
[   39.055270] [drm] Initialized drm 1.1.0 20060810
[   39.115232] pci 0000:01:00.0: found PCI INT A -> IRQ 11
[   39.115255] pci 0000:01:00.0: sharing IRQ 11 with 0000:00:10.0
[   39.115274] pci 0000:01:00.0: sharing IRQ 11 with 0000:00:12.0
[   39.115520] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   39.427275] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   39.427307] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   39.427317] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[   39.427401] pci 0000:01:00.0: putting AGP V2 device into 0x mode
[   41.197913] type=1505 audit(1269010976.839:16): operation="profile_replace" pid=653 name=/usr/bin/evince
[   41.206960] type=1505 audit(1269010976.847:17): operation="profile_replace" pid=653 name=/usr/bin/evince-previewer
[   41.209848] type=1505 audit(1269010976.851:18): operation="profile_replace" pid=653 name=/usr/bin/evince-thumbnailer
[   41.640974] type=1505 audit(1269010977.283:19): operation="profile_replace" pid=1022 name=/usr/lib/cups/backend/cups-pdf
[   41.641458] type=1505 audit(1269010977.283:20): operation="profile_replace" pid=1022 name=/usr/sbin/cupsd
[   41.760972] type=1505 audit(1269010977.403:21): operation="profile_replace" pid=1023 name=/usr/sbin/tcpdump
[   42.807295] ppdev: user-space parallel port driver

```

---

### Post by startrekker on 2010-03-19
FYI I tried to compile that particular from Ralink and I got the same error. It was worth a shot. You might let them know their driver has a compile error.

---

### Post by Ukebane on 2010-03-19
Oh thank you for testing it, will do! (Still need a solution though).

---

### Post by chili555 on 2010-03-19
I don't think any driver old or new is going to fix an IRQ problem. How are IRQs set up in your computer's BIOS?

---

### Post by Ukebane on 2010-03-19
I have no idea, this is a Packard Bell so the bios is pretty much like Fort Knox.
Let me check if the POST shows me anything.

(The wireless card worked fine in windows xp).

I just tried compiling a 2007 RT61 driver and it gave me the following error:

```

make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/ukebane/Downloads/2007_1003_RT61_Linux_STA_v1.1.1.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/ukebane/Downloads/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/ukebane/Downloads/2007_1003_RT61_Linux_STA_v1.1.1.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [all] Error 2

```

---

### Post by Ukebane on 2010-03-19
Alright, as I suspected, I didn't get any wiser from my BIOS.
Isn't there a way to force my wireless card to a different IRQ? (my eth0 IRQ for all I care?)

The BIOS software is : Insyde Software SCU

---

### Post by chili555 on 2010-03-19
In post #4, we did a change to GRUB. Will you please redo it and remove, if you have not already, the previous parameter and substitute this one?```
pci=use_crs
```Here is where I found that little gem: [https://bugzilla.kernel.org/show_bug.cgi?id=14460](https://bugzilla.kernel.org/show_bug.cgi?id=14460)  See comment #18.

Please reboot and let us know.

---

### Post by Ukebane on 2010-03-19
Done, dmesg's error did not change:

```

[   17.181533] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).
[   17.184758] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   17.222966] type=1505 audit(1269027678.867:21): operation="profile_replace" pid=784 name=/usr/sbin/tcpdump
[   17.295859] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).

```Edit:

How does that patch work they mention in the bugreport?

And another idea, can't I disable some other piece of hardware to free up an IRQ?

---

### Post by Ukebane on 2010-03-20
Here's the output for my cat /proc/interrupts:

```

ukebane@nofailxdw2:/etc/default$ cat /proc/interrupts
           CPU0       
  0:         62    XT-PIC-XT        timer
  1:       2150    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  5:       6892    XT-PIC-XT        uhci_hcd:usb4, VIA8233
  7:          0    XT-PIC-XT        uhci_hcd:usb3
  8:          0    XT-PIC-XT        rtc0
 10:          0    XT-PIC-XT        ehci_hcd:usb1
 11:      42695    XT-PIC-XT        uhci_hcd:usb2, eth0, via@pci:0000:01:00.0
 12:     170709    XT-PIC-XT        i8042
 14:       7561    XT-PIC-XT        pata_via
 15:       9519    XT-PIC-XT        pata_via
NMI:          0   Non-maskable interrupts
LOC:     159282   Local timer interrupts
SPU:          0   Spurious interrupts
CNT:          0   Performance counter interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:          3   Machine check polls
ERR:          0
MIS:          0

```Can't I force an IRQ on my wireless card?

Edit:

Flashed my bios to a newer version, still no additional options.

---

### Post by Ukebane on 2010-03-20
Edit 2:

Somewhat of a breakthrough:

My wireless works after changing my grub:

```

GRUB_CMDLINE_LINUX="acpi=force"

```

New symptoms: my USB doesn't work anymore.

---

### Post by jackwhite on 2010-03-22
Hey,

this has speeded up my wireless, which did work but very slowly. I still don't think its as fast as it should be but its great that it has improved.

I wonder if anybody could explain how the solution works to me? 

The solution has been edited into the original post and it is to edit grub so that 
```
GRUB_CMDLINE_LINUX=""
```
is changed to 
```
GRUB_CMDLINE_LINUX="acpi=force irqpoll"
```

I'm a bit of a n00b so the explanation may have to involve short words. Hopefully diagrams won't be needed however...:P


edited to add:

I may have spoken too soon. It was definately sppeded up last night though. Any ideas?

---

### Post by Ukebane on 2010-03-23
The solution to my problem happened in steps:
```
GRUB_CMDLINE_LINUX=***"acpi=force"***
```This caused my my wireless card that didn't get an IRQ # to get an IRQ #, 
as a side effect my USB didn't work anymore.
```
GRUB_CMDLINE_LINUX=***"acpi=force irqpoll"***
```
Adding irqpoll made my USB work again, but my mouse froze for a few ms during movement.
```
GRUB_CMDLINE_LINUX=***"acpi=force irqpoll noapictimer"***
```Adding noapictimer fixed the last problem.

---

