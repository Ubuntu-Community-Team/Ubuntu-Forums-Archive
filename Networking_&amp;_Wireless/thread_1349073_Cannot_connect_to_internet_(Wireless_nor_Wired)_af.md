---
title: "Cannot connect to internet (Wireless nor Wired) after Hard Reset"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by boaty on 2009-12-07
Hey everybody,

After some wonderful times in using my laptop running ubuntu as a router for my xbox, I had to do a hard reset after a freeze.

Unfortunately, now I cannot connect to the internet using a wireless nor a wired connection!

Any ideas...I have a feeling I'm not the first person to whom this has happened...:P

Thanks in advance,
B.

---

### Post by uncaspi on 2009-12-07
Will you post

sudo /sbin/ifconfig
lshw -C network
/etc/network/interfaces
dmesg

---

### Post by boaty on 2009-12-07
Sure.  One moment, I'll need to boot up into ubuntu.

Edit:
Okay...Here we go.

sudo /sbin/ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:03:25:52:de:38  
          inet6 addr: fe80::203:25ff:fe52:de38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2222 (2.2 KB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:f7:95:72  
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fef7:9572/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1470 (1.4 KB)  TX bytes:3816 (3.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-F7-95-72-35-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

(As root) lshw -C network
```

root@ubuntu:~# lshw -C network
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       logical name: wmaster0
       version: 20
       serial: 00:c0:a8:f7:95:72
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.40 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d6:67:ad:3f:8c:95
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

/etc/network/interfaces
```

auto lo
iface lo inet loopback


```

dmesg
```

[    0.000000] BIOS EBDA/lowmem at: 0009dc00/0009dc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-16-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #57-Ubuntu SMP Wed Nov 11 09:47:24 UTC 2009 (Ubuntu 2.6.28-16.57-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf10000 (usable)
[    0.000000]  BIOS-e820: 000000007bf10000 - 000000007bf17000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bf17000 - 000000007bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7bf10 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007bf10000 (usable)
[    0.000000]  modified: 000000007bf10000 - 000000007bf17000 (ACPI data)
[    0.000000]  modified: 000000007bf17000 - 000000007bf80000 (ACPI NVS)
[    0.000000]  modified: 000000007bf80000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 7b789000 - 7beff3c6
[    0.000000] Allocated new RAMDISK: 0087d000 - 00ff33c6
[    0.000000] Move RAMDISK from 000000007b789000 - 000000007beff3c5 to 0087d000 - 00ff33c5
[    0.000000] ACPI: RSDP 000F8E40, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 7BF12821, 0040 (r1 GATEWA SYSTEM    6040000  LTP        0)
[    0.000000] ACPI: FACP 7BF16B62, 0074 (r1 NVIDIA MCP51M    6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 7BF12861, 4301 (r1 GATEWA SYSTEM    6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 7BF17FC0, 0040
[    0.000000] ACPI: SSDT 7BF16BD6, 01C4 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: SLIC 7BF16D9A, 0176 (r1 GATEWA SYSTEM    6040000 Kevi        1)
[    0.000000] ACPI: MCFG 7BF16F10, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 7BF16F4C, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 7BF16F84, 0054 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7BF16FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1099MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000ff33c6]      NEW RAMDISK ==> [000087d000 - 0000ff33c6]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f8da0] 000f8da0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007bf10
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007bf10
[    0.000000] On node 0 totalpages: 507549
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2199 pages used for memmap
[    0.000000]   HighMem zone: 279163 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503582
[    0.000000] Kernel command line: root=UUID=26C6BB79C6BB4837 loop=/ubuntu/disks/root.disk ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1703.609 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10152960 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1987340k/2030656k available (4116k kernel code, 42048k reserved, 2199k data, 532k init, 1125448k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05051fd - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05051fd   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3407.21 BogoMIPS (lpj=6814436)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018339] ACPI: Core revision 20080926
[    0.019939] ACPI: Checking initramfs for custom DSDT
[    0.368686] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.376001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.376001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.376001] ..... (found apic 0 pin 0) ...
[    0.384001] ....... failed.
[    0.384001] ...trying to set up timer as Virtual Wire IRQ...
[    0.384001] ..... failed.
[    0.384001] ...trying to set up timer as ExtINT IRQ...
[    0.425444] ..... works.
[    0.425445] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 stepping 01
[    0.428001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3407.14 BogoMIPS (lpj=6814287)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.512232] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 stepping 01
[    0.512297] Brought up 2 CPUs
[    0.512300] Total of 2 processors activated (6814.36 BogoMIPS).
[    0.512295] System has AMD C1E enabled
[    0.512295] Switch to broadcast mode on CPU1
[    0.512424] CPU0 attaching sched-domain:
[    0.512427]  domain 0: span 0-1 level CPU
[    0.512430]   groups: 0 1
[    0.512437] CPU1 attaching sched-domain:
[    0.512439]  domain 0: span 0-1 level CPU
[    0.512441]   groups: 1 0
[    0.512523] Switch to broadcast mode on CPU0
[    0.512523] net_namespace: 776 bytes
[    0.512523] Booting paravirtualized kernel on bare hardware
[    0.512523] Time: 21:32:13  Date: 12/07/09
[    0.512523] regulator: core version 0.5
[    0.512523] NET: Registered protocol family 16
[    0.512523] EISA bus registered
[    0.512523] ACPI: bus type pci registered
[    0.512523] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 5
[    0.512523] PCI: MCFG area at e0000000 reserved in E820
[    0.512523] PCI: Using MMCONFIG for extended config space
[    0.512523] PCI: Using configuration type 1 for base access
[    0.513198] ACPI: EC: Look up EC in DSDT
[    0.517747] ACPI: Interpreter enabled
[    0.517751] ACPI: (supports S0 S3 S4 S5)
[    0.517771] ACPI: Using IOAPIC for interrupt routing
[    0.516061] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.523462] ACPI: EC: GPE = 0x5b, I/O: command/status = 0x66, data = 0x62
[    0.523465] ACPI: EC: driver started in interrupt mode
[    0.523632] ACPI: No dock devices found.
[    0.523643] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.524092] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524096] pci 0000:00:03.0: PME# disabled
[    0.524117] pci 0000:00:05.0: reg 10 32bit mmio: [0xb2000000-0xb2ffffff]
[    0.524123] pci 0000:00:05.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.524129] pci 0000:00:05.0: reg 1c 64bit mmio: [0xb1000000-0xb1ffffff]
[    0.524135] pci 0000:00:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.524349] pci 0000:00:0a.1: reg 20 io port: [0x3040-0x307f]
[    0.524355] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.524369] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.524375] pci 0000:00:0a.1: PME# disabled
[    0.524408] pci 0000:00:0a.3: reg 10 32bit mmio: [0xb0040000-0xb007ffff]
[    0.524495] pci 0000:00:0b.0: reg 10 32bit mmio: [0xb0004000-0xb0004fff]
[    0.524519] pci 0000:00:0b.0: supports D1 D2
[    0.524521] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524525] pci 0000:00:0b.0: PME# disabled
[    0.524552] pci 0000:00:0b.1: reg 10 32bit mmio: [0xb0005000-0xb00050ff]
[    0.524576] pci 0000:00:0b.1: supports D1 D2
[    0.524578] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524582] pci 0000:00:0b.1: PME# disabled
[    0.524620] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.524695] pci 0000:00:10.1: reg 10 32bit mmio: [0xb0000000-0xb0003fff]
[    0.524719] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.524723] pci 0000:00:10.1: PME# disabled
[    0.524755] pci 0000:00:14.0: reg 10 32bit mmio: [0xb0006000-0xb0006fff]
[    0.524761] pci 0000:00:14.0: reg 14 io port: [0x3090-0x3097]
[    0.524780] pci 0000:00:14.0: supports D1 D2
[    0.524782] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524786] pci 0000:00:14.0: PME# disabled
[    0.524898] pci 0000:00:03.0: bridge io port: [0x9000-0x9fff]
[    0.524902] pci 0000:00:03.0: bridge 32bit mmio: [0xfa100000-0xfa8fffff]
[    0.524906] pci 0000:00:03.0: bridge 64bit mmio pref: [0xbdf00000-0xbfefffff]
[    0.524944] pci 0000:06:09.0: reg 10 io port: [0x6000-0x60ff]
[    0.524950] pci 0000:06:09.0: reg 14 32bit mmio: [0xb3400000-0xb34001ff]
[    0.524978] pci 0000:06:09.0: supports D1 D2
[    0.524981] pci 0000:06:09.0: PME# supported from D1 D2 D3hot D3cold
[    0.524985] pci 0000:06:09.0: PME# disabled
[    0.525013] pci 0000:00:10.0: transparent bridge
[    0.525017] pci 0000:00:10.0: bridge io port: [0x6000-0x6fff]
[    0.525021] pci 0000:00:10.0: bridge 32bit mmio: [0xb3400000-0xb34fffff]
[    0.525030] bus 00 -> node 0
[    0.525037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.525159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.525187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.546678] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.546886] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15)
[    0.547089] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.547293] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.547496] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.547700] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.547909] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.548139] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.548344] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.548548] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.548757] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.548961] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.549166] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.549371] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.549576] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.549781] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.549995] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.550200] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.550405] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.550609] ACPI: WMI: Mapper loaded
[    0.552137] SCSI subsystem initialized
[    0.552145] libata version 3.00 loaded.
[    0.552145] usbcore: registered new interface driver usbfs
[    0.552145] usbcore: registered new interface driver hub
[    0.552145] usbcore: registered new device driver usb
[    0.552145] PCI: Using ACPI for IRQ routing
[    0.556014] Bluetooth: Core ver 2.13
[    0.556021] NET: Registered protocol family 31
[    0.556021] Bluetooth: HCI device and connection manager initialized
[    0.556021] Bluetooth: HCI socket layer initialized
[    0.556023] NET: Registered protocol family 8
[    0.556025] NET: Registered protocol family 20
[    0.556038] NetLabel: Initializing
[    0.556040] NetLabel:  domain hash size = 128
[    0.556042] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.556057] NetLabel:  unlabeled traffic allowed by default
[    0.556077] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.556083] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.564095] AppArmor: AppArmor Filesystem Enabled
[    0.568044] Switched to high resolution mode on CPU 1
[    0.568053] Switched to high resolution mode on CPU 0
[    0.569052] pnp: PnP ACPI init
[    0.569066] ACPI: bus type pnp registered
[    0.572233] pnp: PnP ACPI: found 12 devices
[    0.572236] ACPI: ACPI bus type pnp unregistered
[    0.572240] PnPBIOS: Disabled by ACPI PNP
[    0.572254] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.572258] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.572261] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.572265] system 00:00: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.572272] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.572279] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.572282] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.572285] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.572289] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.572292] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.572295] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.572298] system 00:03: ioport range 0x3040-0x307f has been reserved
[    0.572301] system 00:03: ioport range 0x3000-0x303f has been reserved
[    0.572304] system 00:03: ioport range 0x2000-0x203f has been reserved
[    0.572312] system 00:04: ioport range 0x200-0x20f has been reserved
[    0.572315] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.572318] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.607079] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.607082] pci 0000:00:03.0:   IO window: 0x9000-0x9fff
[    0.607086] pci 0000:00:03.0:   MEM window: 0xfa100000-0xfa8fffff
[    0.607090] pci 0000:00:03.0:   PREFETCH window: 0x000000bdf00000-0x000000bfefffff
[    0.607095] pci 0000:00:10.0: PCI bridge, secondary bus 0000:06
[    0.607098] pci 0000:00:10.0:   IO window: 0x6000-0x6fff
[    0.607102] pci 0000:00:10.0:   MEM window: 0xb3400000-0xb34fffff
[    0.607106] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.607119] pci 0000:00:03.0: setting latency timer to 64
[    0.607124] pci 0000:00:10.0: setting latency timer to 64
[    0.607128] bus: 00 index 0 io port: [0x00-0xffff]
[    0.607131] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.607134] bus: 03 index 0 io port: [0x9000-0x9fff]
[    0.607136] bus: 03 index 1 mmio: [0xfa100000-0xfa8fffff]
[    0.607139] bus: 03 index 2 mmio: [0xbdf00000-0xbfefffff]
[    0.607141] bus: 03 index 3 mmio: [0x0-0x0]
[    0.607144] bus: 06 index 0 io port: [0x6000-0x6fff]
[    0.607147] bus: 06 index 1 mmio: [0xb3400000-0xb34fffff]
[    0.607150] bus: 06 index 2 mmio: [0x0-0x0]
[    0.607152] bus: 06 index 3 io port: [0x00-0xffff]
[    0.607154] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.607170] NET: Registered protocol family 2
[    0.617120] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.617455] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.618283] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.618715] TCP: Hash tables configured (established 131072 bind 65536)
[    0.618718] TCP reno registered
[    0.621146] NET: Registered protocol family 1
[    0.621298] checking if image is initramfs... it is
[    1.338653] Freeing initrd memory: 7640k freed
[    1.338693] Simple Boot Flag at 0x31 set to 0x1
[    1.338892] cpufreq: No nForce2 chipset.
[    1.339048] audit: initializing netlink socket (disabled)
[    1.339064] type=2000 audit(1260221534.336:1): initialized
[    1.348446] highmem bounce pool size: 64 pages
[    1.348452] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.350019] VFS: Disk quotas dquot_6.5.1
[    1.350088] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.350807] fuse init (API version 7.10)
[    1.350904] msgmni has been set to 1699
[    1.351157] alg: No test for stdrng (krng)
[    1.351171] io scheduler noop registered
[    1.351174] io scheduler anticipatory registered
[    1.351176] io scheduler deadline registered
[    1.351193] io scheduler cfq registered (default)
[    1.351212] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.351255] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.351265] pci 0000:00:05.0: Boot video device
[    1.351288] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.553721] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.553735] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.557035] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.557061] pcieport-driver 0000:00:03.0: found MSI capability
[    1.557081] pcieport-driver 0000:00:03.0: irq 2303 for MSI/MSI-X
[    1.557089] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.557108] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.557167] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.557182] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.557981] ACPI: AC Adapter [AC] (on-line)
[    1.604373] ACPI: Battery Slot [BAT0] (battery present)
[    1.604460] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.604463] ACPI: Power Button (FF) [PWRF]
[    1.604509] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.604512] ACPI: Power Button (CM) [PWRB]
[    1.604558] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.604568] ACPI: Sleep Button (CM) [SLPB]
[    1.604618] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.605140] ACPI: Lid Switch [LID]
[    1.605400] ACPI: processor limited to max C-state 1
[    1.605435] processor ACPI_CPU:00: registered as cooling_device0
[    1.605477] processor ACPI_CPU:01: registered as cooling_device1
[    1.607607] isapnp: Scanning for PnP cards...
[    1.960391] isapnp: No Plug & Play device found
[    1.968602] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.969720] brd: module loaded
[    1.970056] loop: module loaded
[    1.970158] Fixed MDIO Bus: probed
[    1.970165] PPP generic driver version 2.4.2
[    1.970234] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.970273] Driver 'sd' needs updating - please use bus_type methods
[    1.970283] Driver 'sr' needs updating - please use bus_type methods
[    1.970585] pata_amd 0000:00:0d.0: version 0.3.10
[    1.970647] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.970751] scsi0 : pata_amd
[    1.971001] scsi1 : pata_amd
[    1.971802] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.971806] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    2.132542] ata1.00: ATA-6: ST9160821A, 3.ALC, max UDMA/100
[    2.132546] ata1.00: 312581808 sectors, multi 16: LBA48 
[    2.132572] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc600c000) ACPI=0x3f01f (20:600:0x13)
[    2.148455] ata1.00: configured for UDMA/100
[    2.312359] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WG02, max UDMA/33
[    2.312384] ata2: nv_mode_filter: 0x739f&0x7001->0x7001, BIOS=0x7000 (0xc600c000) ACPI=0x7001 (60:600:0x11)
[    2.328378] ata2.00: configured for UDMA/33
[    2.330627] scsi 0:0:0:0: Direct-Access     ATA      ST9160821A       3.AL PQ: 0 ANSI: 5
[    2.330737] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.330757] sd 0:0:0:0: [sda] Write Protect is off
[    2.330760] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.330787] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.330873] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.330888] sd 0:0:0:0: [sda] Write Protect is off
[    2.330891] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.330916] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.330921]  sda: sda2 sda4
[    2.345855] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.345916] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.348973] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WG02 PQ: 0 ANSI: 5
[    2.352538] sr0: scsi3-mmc drive: 31x/31x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.352543] Uniform CD-ROM driver Revision: 3.20
[    2.352655] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.352699] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.353289] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.353670] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 23
[    2.353683] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 23 (level, high) -> IRQ 23
[    2.353719] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.353722] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.353794] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    2.353828] ehci_hcd 0000:00:0b.1: debug port 1
[    2.353833] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    2.353858] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xb0005000
[    2.364069] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    2.364160] usb usb1: configuration #1 chosen from 1 choice
[    2.364191] hub 1-0:1.0: USB hub found
[    2.364213] hub 1-0:1.0: 8 ports detected
[    2.364344] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.364704] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    2.364715] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    2.364735] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.364738] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.364792] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    2.364824] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xb0004000
[    2.422132] usb usb2: configuration #1 chosen from 1 choice
[    2.422162] hub 2-0:1.0: USB hub found
[    2.422173] hub 2-0:1.0: 8 ports detected
[    2.422287] uhci_hcd: USB Universal Host Controller Interface driver
[    2.422392] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.425945] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.425953] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.428101] mice: PS/2 mouse device common for all mice
[    2.448133] rtc_cmos 00:07: RTC can wake from S4
[    2.448176] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.448217] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    2.448291] device-mapper: uevent: version 1.0.3
[    2.448428] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.448651] device-mapper: multipath: version 1.0.5 loaded
[    2.448654] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.448795] EISA: Probing bus 0 at eisa.0
[    2.448803] Cannot allocate resource for EISA slot 1
[    2.448806] Cannot allocate resource for EISA slot 2
[    2.448808] Cannot allocate resource for EISA slot 3
[    2.448817] Cannot allocate resource for EISA slot 6
[    2.448825] EISA: Detected 0 cards.
[    2.448972] cpuidle: using governor ladder
[    2.448975] cpuidle: using governor menu
[    2.449576] TCP cubic registered
[    2.449689] NET: Regist

```

I would really, really appreciate any sort of help anyone can lend.  I hope someone here knows what to do...or what this means...Thanks guys:D

---

### Post by uncaspi on 2009-12-07
From dmesg it seems that the driver rtl8180 for the wireless are not loaded.
Would you please check with lsmod if it is listed there. From dmesg I can't see that any of your if are loaded.

---

### Post by boaty on 2009-12-07
Okay, here is the output from lsmod
```

zach@ubuntu:~$ lsmod
Module                  Size  Used by
udf                    87716  1 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
ipt_LOG                13700  4 
iptable_mangle         10880  0 
iptable_filter         10752  1 
iptable_nat            13700  0 
ip_tables              19600  3 iptable_mangle,iptable_filter,iptable_nat
nf_nat                 25876  1 iptable_nat
x_tables               23044  3 ipt_LOG,iptable_nat,ip_tables
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
vboxnetflt             91016  0 
vboxdrv               117672  1 vboxnetflt
input_polldev          11912  0 
lp                     17156  0 
parport                42220  1 lp
joydev                 18368  0 
arc4                    9856  2 
ecb                    10752  2 
snd_hda_intel         436148  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
rtl8180                36864  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217592  1 rtl8180
video                  25872  4 
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
eeprom_93cx6           10240  1 rtl8180
nvidia               7233756  38 
soundcore              15200  1 snd
i2c_nforce2            14980  0 
serio_raw              13444  0 
pcspkr                 10496  0 
output                 11008  1 video
k8temp                 12416  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
agpgart                42696  1 nvidia
usbhid                 42336  0 
cfg80211               38288  2 rtl8180,mac80211
usb_storage            99648  1 
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
zach@ubuntu:~$ 

```

---

### Post by uncaspi on 2009-12-07
Ok thanks. The modules are loaded. Type netstat -r to see if you have the default route to your router. Here is mine:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
 

If you don't have the default route you must add it.

sudo /sbin/route add default gw 192.168.1.1 wlan0

I assume your router gateway is 192.168.1.1 or adjust if I'm wrong

---

### Post by boaty on 2009-12-08
Alright, will do.  I'm off to bed, so I'll post in the morning any changes.

Thanks much guys:D

Edit:

Just decided to post now, so the most current info is up

netstat -r and the sudo route
```

zach@ubuntu:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
zach@ubuntu:~$ sudo /sbin/route add default gw 192.168.1.1 wlan0
[sudo] password for zach: 
zach@ubuntu:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

```

Whether it's relevant or not, I redid ipconfig
```

eth0      Link encap:Ethernet  HWaddr 00:03:25:52:de:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:f7:95:72  
          inet addr:192.168.1.32  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fef7:9572/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21596 (21.5 KB)  TX bytes:4896 (4.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-F7-95-72-35-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

The etc/network/interfaces was exactly the same

the lshw -C network command only had one difference:  a serial number

And this is dmesg after the sudo route command
```

[    0.000000] BIOS EBDA/lowmem at: 0009dc00/0009dc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-16-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #57-Ubuntu SMP Wed Nov 11 09:47:24 UTC 2009 (Ubuntu 2.6.28-16.57-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf10000 (usable)
[    0.000000]  BIOS-e820: 000000007bf10000 - 000000007bf17000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bf17000 - 000000007bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7bf10 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007bf10000 (usable)
[    0.000000]  modified: 000000007bf10000 - 000000007bf17000 (ACPI data)
[    0.000000]  modified: 000000007bf17000 - 000000007bf80000 (ACPI NVS)
[    0.000000]  modified: 000000007bf80000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 7b789000 - 7beff3c6
[    0.000000] Allocated new RAMDISK: 0087d000 - 00ff33c6
[    0.000000] Move RAMDISK from 000000007b789000 - 000000007beff3c5 to 0087d000 - 00ff33c5
[    0.000000] ACPI: RSDP 000F8E40, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 7BF12821, 0040 (r1 GATEWA SYSTEM    6040000  LTP        0)
[    0.000000] ACPI: FACP 7BF16B62, 0074 (r1 NVIDIA MCP51M    6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 7BF12861, 4301 (r1 GATEWA SYSTEM    6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 7BF17FC0, 0040
[    0.000000] ACPI: SSDT 7BF16BD6, 01C4 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: SLIC 7BF16D9A, 0176 (r1 GATEWA SYSTEM    6040000 Kevi        1)
[    0.000000] ACPI: MCFG 7BF16F10, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 7BF16F4C, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 7BF16F84, 0054 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7BF16FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1099MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000ff33c6]      NEW RAMDISK ==> [000087d000 - 0000ff33c6]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f8da0] 000f8da0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007bf10
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007bf10
[    0.000000] On node 0 totalpages: 507549
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2199 pages used for memmap
[    0.000000]   HighMem zone: 279163 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503582
[    0.000000] Kernel command line: root=UUID=26C6BB79C6BB4837 loop=/ubuntu/disks/root.disk ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1703.601 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10152960 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1987340k/2030656k available (4116k kernel code, 42048k reserved, 2199k data, 532k init, 1125448k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05051fd - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05051fd   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3407.20 BogoMIPS (lpj=6814404)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018340] ACPI: Core revision 20080926
[    0.019939] ACPI: Checking initramfs for custom DSDT
[    0.368685] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.376001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.376001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.376001] ..... (found apic 0 pin 0) ...
[    0.384001] ....... failed.
[    0.384001] ...trying to set up timer as Virtual Wire IRQ...
[    0.384001] ..... failed.
[    0.384001] ...trying to set up timer as ExtINT IRQ...
[    0.425427] ..... works.
[    0.425429] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 stepping 01
[    0.428001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3407.14 BogoMIPS (lpj=6814288)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.512232] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 stepping 01
[    0.512296] Brought up 2 CPUs
[    0.512300] Total of 2 processors activated (6814.34 BogoMIPS).
[    0.512295] System has AMD C1E enabled
[    0.512295] Switch to broadcast mode on CPU1
[    0.512423] CPU0 attaching sched-domain:
[    0.512427]  domain 0: span 0-1 level CPU
[    0.512430]   groups: 0 1
[    0.512437] CPU1 attaching sched-domain:
[    0.512439]  domain 0: span 0-1 level CPU
[    0.512441]   groups: 1 0
[    0.512523] Switch to broadcast mode on CPU0
[    0.512523] net_namespace: 776 bytes
[    0.512523] Booting paravirtualized kernel on bare hardware
[    0.512523] Time: 23:21:00  Date: 12/07/09
[    0.512523] regulator: core version 0.5
[    0.512523] NET: Registered protocol family 16
[    0.512523] EISA bus registered
[    0.512523] ACPI: bus type pci registered
[    0.512523] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 5
[    0.512523] PCI: MCFG area at e0000000 reserved in E820
[    0.512523] PCI: Using MMCONFIG for extended config space
[    0.512523] PCI: Using configuration type 1 for base access
[    0.513199] ACPI: EC: Look up EC in DSDT
[    0.517745] ACPI: Interpreter enabled
[    0.517750] ACPI: (supports S0 S3 S4 S5)
[    0.517770] ACPI: Using IOAPIC for interrupt routing
[    0.516061] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.523463] ACPI: EC: GPE = 0x5b, I/O: command/status = 0x66, data = 0x62
[    0.523466] ACPI: EC: driver started in interrupt mode
[    0.523633] ACPI: No dock devices found.
[    0.523644] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.524110] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524114] pci 0000:00:03.0: PME# disabled
[    0.524135] pci 0000:00:05.0: reg 10 32bit mmio: [0xb2000000-0xb2ffffff]
[    0.524141] pci 0000:00:05.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.524147] pci 0000:00:05.0: reg 1c 64bit mmio: [0xb1000000-0xb1ffffff]
[    0.524153] pci 0000:00:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.524368] pci 0000:00:0a.1: reg 20 io port: [0x3040-0x307f]
[    0.524374] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.524388] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.524394] pci 0000:00:0a.1: PME# disabled
[    0.524427] pci 0000:00:0a.3: reg 10 32bit mmio: [0xb0040000-0xb007ffff]
[    0.524514] pci 0000:00:0b.0: reg 10 32bit mmio: [0xb0004000-0xb0004fff]
[    0.524538] pci 0000:00:0b.0: supports D1 D2
[    0.524540] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524544] pci 0000:00:0b.0: PME# disabled
[    0.524571] pci 0000:00:0b.1: reg 10 32bit mmio: [0xb0005000-0xb00050ff]
[    0.524595] pci 0000:00:0b.1: supports D1 D2
[    0.524597] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524601] pci 0000:00:0b.1: PME# disabled
[    0.524639] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.524713] pci 0000:00:10.1: reg 10 32bit mmio: [0xb0000000-0xb0003fff]
[    0.524737] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.524741] pci 0000:00:10.1: PME# disabled
[    0.524774] pci 0000:00:14.0: reg 10 32bit mmio: [0xb0006000-0xb0006fff]
[    0.524779] pci 0000:00:14.0: reg 14 io port: [0x3090-0x3097]
[    0.524799] pci 0000:00:14.0: supports D1 D2
[    0.524801] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524805] pci 0000:00:14.0: PME# disabled
[    0.524918] pci 0000:00:03.0: bridge io port: [0x9000-0x9fff]
[    0.524922] pci 0000:00:03.0: bridge 32bit mmio: [0xfa100000-0xfa8fffff]
[    0.524926] pci 0000:00:03.0: bridge 64bit mmio pref: [0xbdf00000-0xbfefffff]
[    0.524964] pci 0000:06:09.0: reg 10 io port: [0x6000-0x60ff]
[    0.524970] pci 0000:06:09.0: reg 14 32bit mmio: [0xb3400000-0xb34001ff]
[    0.524998] pci 0000:06:09.0: supports D1 D2
[    0.525000] pci 0000:06:09.0: PME# supported from D1 D2 D3hot D3cold
[    0.525005] pci 0000:06:09.0: PME# disabled
[    0.525033] pci 0000:00:10.0: transparent bridge
[    0.525037] pci 0000:00:10.0: bridge io port: [0x6000-0x6fff]
[    0.525041] pci 0000:00:10.0: bridge 32bit mmio: [0xb3400000-0xb34fffff]
[    0.525050] bus 00 -> node 0
[    0.525057] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.525177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.525205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.546694] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.546902] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15)
[    0.547105] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.547309] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.547512] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.547716] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.547926] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.548154] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.548360] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.548564] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.548774] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.548978] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.549183] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.549387] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.549591] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.549797] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.550011] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.550215] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.550421] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.550625] ACPI: WMI: Mapper loaded
[    0.552137] SCSI subsystem initialized
[    0.552145] libata version 3.00 loaded.
[    0.552145] usbcore: registered new interface driver usbfs
[    0.552145] usbcore: registered new interface driver hub
[    0.552145] usbcore: registered new device driver usb
[    0.552145] PCI: Using ACPI for IRQ routing
[    0.556014] Bluetooth: Core ver 2.13
[    0.556021] NET: Registered protocol family 31
[    0.556021] Bluetooth: HCI device and connection manager initialized
[    0.556021] Bluetooth: HCI socket layer initialized
[    0.556023] NET: Registered protocol family 8
[    0.556025] NET: Registered protocol family 20
[    0.556038] NetLabel: Initializing
[    0.556040] NetLabel:  domain hash size = 128
[    0.556042] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.556057] NetLabel:  unlabeled traffic allowed by default
[    0.556076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.556082] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.564096] AppArmor: AppArmor Filesystem Enabled
[    0.568044] Switched to high resolution mode on CPU 1
[    0.568052] Switched to high resolution mode on CPU 0
[    0.569053] pnp: PnP ACPI init
[    0.569067] ACPI: bus type pnp registered
[    0.571988] pnp: PnP ACPI: found 12 devices
[    0.571991] ACPI: ACPI bus type pnp unregistered
[    0.571996] PnPBIOS: Disabled by ACPI PNP
[    0.572023] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.572027] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.572030] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.572034] system 00:00: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.572041] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.572048] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.572051] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.572054] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.572057] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.572061] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.572064] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.572067] system 00:03: ioport range 0x3040-0x307f has been reserved
[    0.572070] system 00:03: ioport range 0x3000-0x303f has been reserved
[    0.572073] system 00:03: ioport range 0x2000-0x203f has been reserved
[    0.572081] system 00:04: ioport range 0x200-0x20f has been reserved
[    0.572084] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.572087] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.606847] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.606850] pci 0000:00:03.0:   IO window: 0x9000-0x9fff
[    0.606855] pci 0000:00:03.0:   MEM window: 0xfa100000-0xfa8fffff
[    0.606859] pci 0000:00:03.0:   PREFETCH window: 0x000000bdf00000-0x000000bfefffff
[    0.606863] pci 0000:00:10.0: PCI bridge, secondary bus 0000:06
[    0.606867] pci 0000:00:10.0:   IO window: 0x6000-0x6fff
[    0.606871] pci 0000:00:10.0:   MEM window: 0xb3400000-0xb34fffff
[    0.606874] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.606886] pci 0000:00:03.0: setting latency timer to 64
[    0.606891] pci 0000:00:10.0: setting latency timer to 64
[    0.606895] bus: 00 index 0 io port: [0x00-0xffff]
[    0.606898] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.606900] bus: 03 index 0 io port: [0x9000-0x9fff]
[    0.606903] bus: 03 index 1 mmio: [0xfa100000-0xfa8fffff]
[    0.606906] bus: 03 index 2 mmio: [0xbdf00000-0xbfefffff]
[    0.606908] bus: 03 index 3 mmio: [0x0-0x0]
[    0.606911] bus: 06 index 0 io port: [0x6000-0x6fff]
[    0.606914] bus: 06 index 1 mmio: [0xb3400000-0xb34fffff]
[    0.606916] bus: 06 index 2 mmio: [0x0-0x0]
[    0.606919] bus: 06 index 3 io port: [0x00-0xffff]
[    0.606921] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.606936] NET: Registered protocol family 2
[    0.617119] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.617456] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.618284] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.618716] TCP: Hash tables configured (established 131072 bind 65536)
[    0.618720] TCP reno registered
[    0.621146] NET: Registered protocol family 1
[    0.621300] checking if image is initramfs... it is
[    1.338667] Freeing initrd memory: 7640k freed
[    1.338706] Simple Boot Flag at 0x31 set to 0x1
[    1.338904] cpufreq: No nForce2 chipset.
[    1.339061] audit: initializing netlink socket (disabled)
[    1.339078] type=2000 audit(1260228060.336:1): initialized
[    1.348462] highmem bounce pool size: 64 pages
[    1.348468] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.350035] VFS: Disk quotas dquot_6.5.1
[    1.350105] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.350822] fuse init (API version 7.10)
[    1.350919] msgmni has been set to 1699
[    1.351171] alg: No test for stdrng (krng)
[    1.351185] io scheduler noop registered
[    1.351188] io scheduler anticipatory registered
[    1.351190] io scheduler deadline registered
[    1.351207] io scheduler cfq registered (default)
[    1.351226] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.351268] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.351279] pci 0000:00:05.0: Boot video device
[    1.351302] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.553742] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.553756] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.557152] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.557179] pcieport-driver 0000:00:03.0: found MSI capability
[    1.557198] pcieport-driver 0000:00:03.0: irq 2303 for MSI/MSI-X
[    1.557205] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.557224] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.557283] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.557297] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.557993] ACPI: AC Adapter [AC] (on-line)
[    1.604201] ACPI: Battery Slot [BAT0] (battery present)
[    1.604289] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.604292] ACPI: Power Button (FF) [PWRF]
[    1.604338] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.604341] ACPI: Power Button (CM) [PWRB]
[    1.604387] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.604397] ACPI: Sleep Button (CM) [SLPB]
[    1.604447] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.605025] ACPI: Lid Switch [LID]
[    1.605278] ACPI: processor limited to max C-state 1
[    1.605312] processor ACPI_CPU:00: registered as cooling_device0
[    1.605355] processor ACPI_CPU:01: registered as cooling_device1
[    1.607494] isapnp: Scanning for PnP cards...
[    1.960327] isapnp: No Plug & Play device found
[    1.968510] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.969630] brd: module loaded
[    1.969965] loop: module loaded
[    1.970067] Fixed MDIO Bus: probed
[    1.970073] PPP generic driver version 2.4.2
[    1.970142] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.970183] Driver 'sd' needs updating - please use bus_type methods
[    1.970193] Driver 'sr' needs updating - please use bus_type methods
[    1.970496] pata_amd 0000:00:0d.0: version 0.3.10
[    1.970558] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.970661] scsi0 : pata_amd
[    1.970909] scsi1 : pata_amd
[    1.971705] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.971708] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    2.132514] ata1.00: ATA-6: ST9160821A, 3.ALC, max UDMA/100
[    2.132517] ata1.00: 312581808 sectors, multi 16: LBA48 
[    2.132543] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc600c000) ACPI=0x3f01f (20:600:0x13)
[    2.148465] ata1.00: configured for UDMA/100
[    2.312358] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WG02, max UDMA/33
[    2.312383] ata2: nv_mode_filter: 0x739f&0x7001->0x7001, BIOS=0x7000 (0xc600c000) ACPI=0x7001 (60:600:0x11)
[    2.328378] ata2.00: configured for UDMA/33
[    2.330627] scsi 0:0:0:0: Direct-Access     ATA      ST9160821A       3.AL PQ: 0 ANSI: 5
[    2.330736] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.330756] sd 0:0:0:0: [sda] Write Protect is off
[    2.330759] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.330786] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.330873] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.330888] sd 0:0:0:0: [sda] Write Protect is off
[    2.330891] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.330916] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.330920]  sda: sda2 sda4
[    2.356754] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.356815] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.359867] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WG02 PQ: 0 ANSI: 5
[    2.363213] sr0: scsi3-mmc drive: 31x/31x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.363218] Uniform CD-ROM driver Revision: 3.20
[    2.363329] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.363373] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.363931] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.364324] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 23
[    2.364337] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 23 (level, high) -> IRQ 23
[    2.364373] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.364377] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.364446] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    2.364480] ehci_hcd 0000:00:0b.1: debug port 1
[    2.364485] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    2.364510] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xb0005000
[    2.376069] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    2.376161] usb usb1: configuration #1 chosen from 1 choice
[    2.376192] hub 1-0:1.0: USB hub found
[    2.376215] hub 1-0:1.0: 8 ports detected
[    2.376345] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.376709] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    2.376720] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    2.376739] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.376743] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.376797] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    2.376829] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xb0004000
[    2.434130] usb usb2: configuration #1 chosen from 1 choice
[    2.434160] hub 2-0:1.0: USB hub found
[    2.434171] hub 2-0:1.0: 8 ports detected
[    2.434283] uhci_hcd: USB Universal Host Controller Interface driver
[    2.434389] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.438314] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.438323] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.440101] mice: PS/2 mouse device common for all mice
[    2.460133] rtc_cmos 00:07: RTC can wake from S4
[    2.460177] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.460219] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    2.460293] device-mapper: uevent: version 1.0.3
[    2.460433] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.460655] device-mapper: multipath: version 1.0.5 loaded
[    2.460659] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.460798] EISA: Probing bus 0 at eisa.0
[    2.460806] Cannot allocate resource for EISA slot 1
[    2.460809] Cannot allocate resource for EISA slot 2
[    2.460811] Cannot allocate resource for EISA slot 3
[    2.460820] Cannot allocate resource for EISA slot 6
[    2.460828] EISA: Detected 0 cards.
[    2.460976] cpuidle: using governor ladder
[    2.460979] cpuidle: using governor menu
[    2.461580] TCP cubic registered
[    2.461692] NET: Regist

```

I'm not really sure what's relevant, so I thought I'd put up what I needed before.  Thanks guys for helping me with this...It's nice to know there's a community for inexperienced ubuntu users like myself:D

Edit:
Good morrow, everyone.  I'm still having issues with this, and I hope someone can still lend a hand:)

---

### Post by boaty on 2009-12-08
Bump:)

---

### Post by uncaspi on 2009-12-08
The problem is that none of your cards shows up in dmesg. But the drivers are loaded so it seems that the cards are not assigned logical names at boot. Please post the contest of /etc/udev/rules.d/70-persistent-net.rules

---

### Post by boaty on 2009-12-08
Okay, here's that file
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:03:25:52:de:38", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8185 (rtl8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:c0:a8:f7:95:72", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

---

### Post by teward on 2009-12-08
If I may ask:

Hard resets can easily kill hardware components.  Is it at all possible the cards/system got damaged by the hard reset, and thus caused issues with detection?

I'd actually like to see the output of the command 
```
lspci
``` to confirm if the system is detecting/loading the device.

---

### Post by boaty on 2009-12-08
I don't think my hardware is shot.  I'm using my internet on vista without a problem, so I think the problem lies in ubuntu.

Give me a minute, and I'll switch over and get the output.

Edit:
Okay, here's output from lspci.

```

zach@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
zach@ubuntu:~$ 

```

Does anybody have any ideas...?  Thanks to anyone who can help; I've been dealing with this for the past four days or so...

---

### Post by boaty on 2009-12-09
Bump.  I'm off to bed.  Hope someone can help me with this...Thanks.  Good night.

---

### Post by boaty on 2009-12-09
Another bump...I really, really need help with this.  I know next to nothing about ubuntu, and this is the first time I've had this problem.  Anyone?

Really?  No one has any idea?  No one here has had this problem before?  I'm begging for help.  Literally (not really though), I am on my internet knees, begging.

---

### Post by boaty on 2009-12-10
Bump:D

---

### Post by boaty on 2009-12-12
Another Bump...I really want to get back on Ubuntu as soon as possible, so any help would be largely appreciated.

---

### Post by boaty on 2009-12-20
Bump.  Sorry for all the double+ posts, but it's the only way it will actually bump (to my knowledge)

---

