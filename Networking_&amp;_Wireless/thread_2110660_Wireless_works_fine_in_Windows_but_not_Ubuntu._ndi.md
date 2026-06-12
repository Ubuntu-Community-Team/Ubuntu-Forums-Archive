---
title: "Wireless works fine in Windows but not Ubuntu. ndisgtk did not work."
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by C.Clear on 2013-01-30
Everyone;

Not sure if anyone will reply to this post but I've been having problems with my wireless signal in ubuntu. I've had to restart my computer multiple times before even connecting to a network.

I Bought a new Wireless USB Adapter in hopes of solving the problem. While it works perfect in Windows Not so much in Ubuntu.

I tried installing ndisgtk and adding the inf file for my wireless usb adapter, still no luck.

Copying the results from the lspci command and lshw -C Network. In hopes that someone will have pity on this Noob and offer Assistance.

lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)



lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:07:87:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:17 memory:fe9fe000-fe9fffff memory:fea00000-fea03fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by C.Clear on 2013-01-30
Read the reccommendations for posting Wireless Problems. Thought I would post some more informations in hopes someone would be able to point me in the right direction:


Lspci

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 005: ID 152e:1640 LG (HLDS) 

Bus 003 Device 004: ID 0461:4d0f Primax Electronics, Ltd 

Bus 003 Device 003: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard

Bus 003 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-Port Hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 003: ID 050d:845a Belkin Components 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0d:56:07:87:3b  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:17 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:684 errors:0 dropped:0 overruns:0 frame:0

          TX packets:684 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:53752 (53.7 KB)  TX bytes:53752 (53.7 KB)



iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



vboxnet0  no wireless extensions.

iwconfig wlan 0

iwconfig: unknown command "0"


dmesg

 0.000000]     0: 0x00000100 -> 0x0005fe74

[    0.000000] On node 0 totalpages: 392709

[    0.000000] free_area_init_node: node 0, pgdat c0804040, node_mem_map c13fc020

[    0.000000]   DMA zone: 32 pages used for memmap

[    0.000000]   DMA zone: 0 pages reserved

[    0.000000]   DMA zone: 3953 pages, LIFO batch:0

[    0.000000]   Normal zone: 1744 pages used for memmap

[    0.000000]   Normal zone: 221486 pages, LIFO batch:31

[    0.000000]   HighMem zone: 1293 pages used for memmap

[    0.000000]   HighMem zone: 164201 pages, LIFO batch:31

[    0.000000] Using APIC driver default

[    0.000000] ACPI: PM-Timer IO Port: 0x808

[    0.000000] ACPI: Local APIC address 0xfee00000

[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)

[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)

[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)

[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)

[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])

[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)

[    0.000000] ACPI: IRQ0 used by override.

[    0.000000] ACPI: IRQ2 used by override.

[    0.000000] ACPI: IRQ9 used by override.

[    0.000000] Using ACPI (MADT) for SMP configuration information

[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs

[    0.000000] nr_irqs_gsi: 40

[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]

[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000

[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000

[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000

[    0.000000] Allocating PCI resources starting at 5ff00000 (gap: 5ff00000:9ed00000)

[    0.000000] Booting paravirtualized kernel on bare hardware

[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1

[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u1048576

[    0.000000] pcpu-alloc: s36416 r0 d20928 u1048576 alloc=1*4194304

[    0.000000] pcpu-alloc: [0] 0 1 2 3 

[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389640

[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-32-generic root=UUID=14245c0d-d9a4-4e3a-9fb9-b142c8c9c642 ro quiet splash

[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)

[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

[    0.000000] Enabling fast FPU save and restore... done.

[    0.000000] Enabling unmasked SIMD FPU exception support... done.

[    0.000000] Initializing CPU#0

[    0.000000] allocated 7856380 bytes of page_cgroup

[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups

[    0.000000] Subtract (50 early reservations)

[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE

[    0.000000]   #2 [0000100000 - 00009a7b1c]   TEXT DATA BSS

[    0.000000]   #3 [00009a8000 - 00009ab1c4]             BRK

[    0.000000]   #4 [00000fe720 - 0000100000]   BIOS reserved

[    0.000000]   #5 [00000fe710 - 00000fe720]    MP-table mpf

[    0.000000]   #6 [000009fc00 - 00000f0000]   BIOS reserved

[    0.000000]   #7 [00000f0198 - 00000fe710]   BIOS reserved

[    0.000000]   #8 [00000f0000 - 00000f0198]    MP-table mpc

[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE

[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP

[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE

[    0.000000]   #12 [00009ac000 - 00013fb000]     NEW RAMDISK

[    0.000000]   #13 [00013fb000 - 00013fc000]         BOOTMEM

[    0.000000]   #14 [00013fc000 - 0001ffc000]         BOOTMEM

[    0.000000]   #15 [0001ffc000 - 0001ffc004]         BOOTMEM

[    0.000000]   #16 [0001ffc040 - 0001ffc100]         BOOTMEM

[    0.000000]   #17 [0001ffc100 - 0001ffc154]         BOOTMEM

[    0.000000]   #18 [0001ffc180 - 0001fff180]         BOOTMEM

[    0.000000]   #19 [0001fff180 - 0001fff1c0]         BOOTMEM

[    0.000000]   #20 [0001fff1c0 - 00020021c0]         BOOTMEM

[    0.000000]   #21 [00020021c0 - 00020021e7]         BOOTMEM

[    0.000000]   #22 [0002002200 - 0002002350]         BOOTMEM

[    0.000000]   #23 [0002002380 - 00020023c0]         BOOTMEM

[    0.000000]   #24 [00020023c0 - 0002002400]         BOOTMEM

[    0.000000]   #25 [0002002400 - 0002002440]         BOOTMEM

[    0.000000]   #26 [0002002440 - 0002002480]         BOOTMEM

[    0.000000]   #27 [0002002480 - 00020024c0]         BOOTMEM

[    0.000000]   #28 [00020024c0 - 0002002500]         BOOTMEM

[    0.000000]   #29 [0002002500 - 0002002540]         BOOTMEM

[    0.000000]   #30 [0002002540 - 0002002580]         BOOTMEM

[    0.000000]   #31 [0002002580 - 00020025c0]         BOOTMEM

[    0.000000]   #32 [00020025c0 - 00020025d0]         BOOTMEM

[    0.000000]   #33 [0002002600 - 0002002610]         BOOTMEM

[    0.000000]   #34 [0002002640 - 00020026aa]         BOOTMEM

[    0.000000]   #35 [00020026c0 - 000200272a]         BOOTMEM

[    0.000000]   #36 [0002400000 - 000240e000]         BOOTMEM

[    0.000000]   #37 [0002500000 - 000250e000]         BOOTMEM

[    0.000000]   #38 [0002600000 - 000260e000]         BOOTMEM

[    0.000000]   #39 [0002700000 - 000270e000]         BOOTMEM

[    0.000000]   #40 [0002004740 - 0002004744]         BOOTMEM

[    0.000000]   #41 [0002004780 - 0002004784]         BOOTMEM

[    0.000000]   #42 [00020047c0 - 00020047d0]         BOOTMEM

[    0.000000]   #43 [0002004800 - 0002004810]         BOOTMEM

[    0.000000]   #44 [0002004840 - 00020048e0]         BOOTMEM

[    0.000000]   #45 [0002004900 - 0002004948]         BOOTMEM

[    0.000000]   #46 [0002004980 - 0002008980]         BOOTMEM

[    0.000000]   #47 [0002008980 - 0002088980]         BOOTMEM

[    0.000000]   #48 [0002088980 - 00020c8980]         BOOTMEM

[    0.000000]   #49 [000270e000 - 0002e8c0fc]         BOOTMEM

[    0.000000] Initializing HighMem for node 0 (000377fe:0005fe74)

[    0.000000] Memory: 1530360k/1571280k available (4944k kernel code, 40476k reserved, 2337k data, 692k init, 661976k highmem)

[    0.000000] virtual kernel memory layout:

[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)

[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)

[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)

[    0.000000]       .init : 0xc081d000 - 0xc08ca000   ( 692 kB)

[    0.000000]       .data : 0xc05d41ae - 0xc081c828   (2337 kB)

[    0.000000]       .text : 0xc0100000 - 0xc05d41ae   (4944 kB)

[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.

[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1

[    0.000000] Hierarchical RCU implementation.

[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.

[    0.000000]     RCU-based detection of stalled CPUs is disabled.

[    0.000000]     Verbose stalled-CPUs detection is disabled.

[    0.000000] NR_IRQS:2304 nr_irqs:712

[    0.000000] Console: colour VGA+ 80x25

[    0.000000] console [tty0] enabled

[    0.000000] Fast TSC calibration using PIT

[    0.000000] Detected 2524.669 MHz processor.

[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 5049.33 BogoMIPS (lpj=10098676)

[    0.004020] pid_max: default: 32768 minimum: 301

[    0.004060] Security Framework initialized

[    0.004097] AppArmor: AppArmor initialized

[    0.004101] Yama: becoming mindful.

[    0.004190] Mount-cache hash table entries: 512

[    0.004425] Initializing cgroup subsys ns

[    0.004433] Initializing cgroup subsys cpuacct

[    0.004441] Initializing cgroup subsys memory

[    0.004456] Initializing cgroup subsys devices

[    0.004460] Initializing cgroup subsys freezer

[    0.004464] Initializing cgroup subsys net_cls

[    0.004511] CPU0: Hyper-Threading is disabled

[    0.004517] mce: CPU supports 4 MCE banks

[    0.004532] CPU0: Thermal monitoring enabled (TM1)

[    0.004550] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.

[    0.004566] ... version:                0

[    0.004569] ... bit width:              40

[    0.004572] ... generic registers:      18

[    0.004575] ... value mask:             000000ffffffffff

[    0.004578] ... max period:             0000007fffffffff

[    0.004581] ... fixed-purpose events:   0

[    0.004584] ... event mask:             000000000003ffff

[    0.005781] SMP alternatives: switching to UP code

[    0.019918] ACPI: Core revision 20100428

[    0.044139] ftrace: converting mcount calls to 0f 1f 44 00 00

[    0.044146] ftrace: allocating 21786 entries in 43 pages

[    0.048128] Enabling APIC mode:  Flat.  Using 1 I/O APICs

[    0.048437] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1

[    0.089258] CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 09

[    0.092004] Brought up 1 CPUs

[    0.092004] Total of 1 processors activated (5049.33 BogoMIPS).

[    0.092004] devtmpfs: initialized

[    0.092004] regulator: core version 0.5

[    0.092004] Time: 21:14:32  Date: 01/30/13

[    0.092004] NET: Registered protocol family 16

[    0.092004] EISA bus registered

[    0.092004] ACPI: bus type pci registered

[    0.092004] PCI: PCI BIOS revision 2.10 entry at 0xfbc86, last bus=1

[    0.092004] PCI: Using configuration type 1 for base access

[    0.093260] bio: create slab <bio-0> at 0

[    0.094013] ACPI: EC: Look up EC in DSDT

[    0.112957] ACPI: Interpreter enabled

[    0.112966] ACPI: (supports S0 S1 S3 S4 S5)

[    0.113003] ACPI: Using IOAPIC for interrupt routing

[    0.144707] ACPI: No dock devices found.

[    0.144714] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug

[    0.146207] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])

[    0.149197] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)

[    0.149201] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)

[    0.149205] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)

[    0.149209] pci_root PNP0A03:00: host bridge window [mem 0x80860000-0xfebfffff] (ignored)

[    0.149237] pci 0000:00:00.0: reg 10: [mem 0xf0000000-0xf7ffffff pref]

[    0.149313] pci 0000:00:02.0: reg 10: [mem 0xe8000000-0xefffffff pref]

[    0.149321] pci 0000:00:02.0: reg 14: [mem 0xfeb80000-0xfebfffff]

[    0.149433] pci 0000:00:1d.0: reg 20: [io  0xff80-0xff9f]

[    0.149491] pci 0000:00:1d.1: reg 20: [io  0xff60-0xff7f]

[    0.149550] pci 0000:00:1d.2: reg 20: [io  0xff40-0xff5f]

[    0.149610] pci 0000:00:1d.7: reg 10: [mem 0xffa80800-0xffa80bff]

[    0.149672] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold

[    0.149678] pci 0000:00:1d.7: PME# disabled

[    0.149731] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,

[    0.149733] * this clock source is slow. If you are sure your timer does not have

[    0.149735] * this bug, please use "acpi_pm_good" to disable the workaround

[    0.149804] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]

[    0.149812] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]

[    0.149820] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]

[    0.149828] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]

[    0.149836] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]

[    0.149844] pci 0000:00:1f.1: reg 24: [mem 0xfeb7fc00-0xfeb7ffff]

[    0.149900] pci 0000:00:1f.3: reg 20: [io  0xeda0-0xedbf]

[    0.149945] pci 0000:00:1f.5: reg 10: [io  0xee00-0xeeff]

[    0.149952] pci 0000:00:1f.5: reg 14: [io  0xedc0-0xedff]

[    0.149960] pci 0000:00:1f.5: reg 18: [mem 0xfeb7fa00-0xfeb7fbff]

[    0.149967] pci 0000:00:1f.5: reg 1c: [mem 0xfeb7f900-0xfeb7f9ff]

[    0.149999] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold

[    0.150004] pci 0000:00:1f.5: PME# disabled

[    0.150060] pci 0000:01:09.0: reg 10: [mem 0xfe9fe000-0xfe9fffff]

[    0.150089] pci 0000:01:09.0: reg 30: [mem 0xfea00000-0xfea03fff pref]

[    0.150108] pci 0000:01:09.0: supports D1 D2

[    0.150111] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.150116] pci 0000:01:09.0: PME# disabled

[    0.150150] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)

[    0.150156] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)

[    0.150162] pci 0000:00:1e.0:   bridge window [mem 0xfe900000-0xfeafffff]

[    0.150168] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)

[    0.150172] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)

[    0.150175] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)

[    0.150186] pci_bus 0000:00: on NUMA node 0

[    0.150192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[    0.150595] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]

[    0.300393] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)

[    0.300739] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)

[    0.301077] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)

[    0.301415] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)

[    0.301752] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.

[    0.302087] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.

[    0.302423] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.

[    0.302762] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)

[    0.302866] HEST: Table is not found!

[    0.302971] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none

[    0.302981] vgaarb: loaded

[    0.303221] SCSI subsystem initialized

[    0.303318] libata version 3.00 loaded.

[    0.303400] usbcore: registered new interface driver usbfs

[    0.303418] usbcore: registered new interface driver hub

[    0.303458] usbcore: registered new device driver usb

[    0.303638] ACPI: WMI: Mapper loaded

[    0.303641] PCI: Using ACPI for IRQ routing

[    0.303647] PCI: pci_cache_line_size set to 64 bytes

[    0.303706] reserve RAM buffer: 0000000000002000 - 000000000000ffff 

[    0.303710] reserve RAM buffer: 000000005fe74000 - 000000005fffffff 

[    0.303858] NetLabel: Initializing

[    0.303861] NetLabel:  domain hash size = 128

[    0.303863] NetLabel:  protocols = UNLABELED CIPSOv4

[    0.303880] NetLabel:  unlabeled traffic allowed by default

[    0.303944] Switching to clocksource tsc

[    0.314540] AppArmor: AppArmor Filesystem Enabled

[    0.314573] pnp: PnP ACPI init

[    0.314607] ACPI: bus type pnp registered

[    0.336760] pnp: PnP ACPI: found 10 devices

[    0.336764] ACPI: ACPI bus type pnp unregistered

[    0.336771] PnPBIOS: Disabled by ACPI PNP

[    0.336789] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved

[    0.336794] system 00:00: [mem 0x00100000-0x00ffffff] could not be reserved

[    0.336798] system 00:00: [mem 0x01000000-0x5fe73fff] could not be reserved

[    0.336802] system 00:00: [mem 0x000c0000-0x000fffff] could not be reserved

[    0.336807] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved

[    0.336811] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved

[    0.336815] system 00:00: [mem 0xfecf0000-0xfecf0fff] has been reserved

[    0.336819] system 00:00: [mem 0xffb00000-0xffbfffff] has been reserved

[    0.336823] system 00:00: [mem 0xffc00000-0xffffffff] has been reserved

[    0.336835] system 00:09: [io  0x0800-0x085f] has been reserved

[    0.336838] system 00:09: [io  0x0c00-0x0c7f] has been reserved

[    0.336842] system 00:09: [io  0x0860-0x08ff] has been reserved

[    0.373614] pci 0000:00:1e.0: PCI bridge to [bus 01-01]

[    0.373618] pci 0000:00:1e.0:   bridge window [io  disabled]

[    0.373626] pci 0000:00:1e.0:   bridge window [mem 0xfe900000-0xfeafffff]

[    0.373631] pci 0000:00:1e.0:   bridge window [mem pref disabled]

[    0.373650] pci 0000:00:1e.0: setting latency timer to 64

[    0.373656] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]

[    0.373659] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]

[    0.373663] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]

[    0.373666] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]

[    0.373670] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]

[    0.373732] NET: Registered protocol family 2

[    0.373839] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[    0.374270] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

[    0.375482] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[    0.376310] TCP: Hash tables configured (established 131072 bind 65536)

[    0.376316] TCP reno registered

[    0.376329] UDP hash table entries: 512 (order: 2, 16384 bytes)

[    0.376358] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)

[    0.376586] NET: Registered protocol family 1

[    0.376619] pci 0000:00:02.0: Boot video device

[    0.376726] PCI: CLS 0 bytes, default 64

[    0.376874] Simple Boot Flag value 0x87 read from CMOS RAM was invalid

[    0.376877] Simple Boot Flag at 0x7a set to 0x1

[    0.377042] cpufreq-nforce2: No nForce2 chipset.

[    0.377084] Scanning for low memory corruption every 60 seconds

[    0.377293] audit: initializing netlink socket (disabled)

[    0.377310] type=2000 audit(1359580472.376:1): initialized

[    0.387212] Trying to unpack rootfs image as initramfs...

[    0.400306] highmem bounce pool size: 64 pages

[    0.400317] HugeTLB registered 4 MB page size, pre-allocated 0 pages

[    0.408179] VFS: Disk quotas dquot_6.5.2

[    0.408313] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[    0.409259] fuse init (API version 7.14)

[    0.409397] msgmni has been set to 1696

[    0.777246] Freeing initrd memory: 10556k freed

[    0.798942] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)

[    0.798947] io scheduler noop registered

[    0.798950] io scheduler deadline registered

[    0.798976] io scheduler cfq registered (default)

[    0.799132] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[    0.799163] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

[    0.799409] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0

[    0.799420] ACPI: Power Button [VBTN]

[    0.799489] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1

[    0.799494] ACPI: Power Button [PWRF]

[    0.799769] ACPI: acpi_idle registered with cpuidle

[    0.823405] ERST: Table is not found!

[    0.823461] isapnp: Scanning for PnP cards...

[    0.829151] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled

[    0.829268] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    0.829720] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    0.831317] brd: module loaded

[    0.832067] loop: module loaded

[    0.875982] ata_piix 0000:00:1f.1: version 2.13

[    0.876004]   alloc irq_desc for 18 on node -1

[    0.876007]   alloc kstat_irqs on node -1

[    0.876019] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[    0.876089] ata_piix 0000:00:1f.1: setting latency timer to 64

[    0.876240] scsi0 : ata_piix

[    0.876362] scsi1 : ata_piix

[    0.876414] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14

[    0.876419] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15

[    0.876878] Fixed MDIO Bus: probed

[    0.876926] PPP generic driver version 2.4.2

[    0.877014] tun: Universal TUN/TAP device driver, 1.6

[    0.877017] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>

[    0.877128] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver

[    0.877157]   alloc irq_desc for 23 on node -1

[    0.877160]   alloc kstat_irqs on node -1

[    0.877169] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23

[    0.877193] ehci_hcd 0000:00:1d.7: setting latency timer to 64

[    0.877198] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[    0.877248] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1

[    0.877300] ehci_hcd 0000:00:1d.7: debug port 1

[    0.881199] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported

[    0.881267] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800

[    0.928995] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00

[    0.929184] hub 1-0:1.0: USB hub found

[    0.929192] hub 1-0:1.0: 6 ports detected

[    0.929285] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver

[    0.929304] uhci_hcd: USB Universal Host Controller Interface driver

[    0.929359]   alloc irq_desc for 16 on node -1

[    0.929362]   alloc kstat_irqs on node -1

[    0.929370] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    0.929381] uhci_hcd 0000:00:1d.0: setting latency timer to 64

[    0.929385] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[    0.929440] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2

[    0.929479] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80

[    0.929647] hub 2-0:1.0: USB hub found

[    0.929654] hub 2-0:1.0: 2 ports detected

[    0.929720]   alloc irq_desc for 19 on node -1

[    0.929723]   alloc kstat_irqs on node -1

[    0.929729] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19

[    0.929737] uhci_hcd 0000:00:1d.1: setting latency timer to 64

[    0.929741] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[    0.929792] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3

[    0.929827] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60

[    0.929988] hub 3-0:1.0: USB hub found

[    0.929995] hub 3-0:1.0: 2 ports detected

[    0.930062] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[    0.930070] uhci_hcd 0000:00:1d.2: setting latency timer to 64

[    0.930074] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[    0.930121] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4

[    0.930159] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40

[    0.930333] hub 4-0:1.0: USB hub found

[    0.930340] hub 4-0:1.0: 2 ports detected

[    0.930486] PNP: No PS/2 controller found. Probing ports directly.

[    0.977078] serio: i8042 KBD port at 0x60,0x64 irq 1

[    0.977088] serio: i8042 AUX port at 0x60,0x64 irq 12

[    0.977250] mice: PS/2 mouse device common for all mice

[    0.977432] rtc_cmos 00:05: RTC can wake from S4

[    0.977490] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0

[    0.977517] rtc0: alarms up to one day, 242 bytes nvram

[    0.977691] device-mapper: uevent: version 1.0.3

[    0.977866] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]

[    0.977937] device-mapper: multipath: version 1.1.1 loaded

[    0.977941] device-mapper: multipath round-robin: version 1.0.0 loaded

[    0.978115] EISA: Probing bus 0 at eisa.0

[    0.978155] EISA: Detected 0 cards.

[    1.021796] cpuidle: using governor ladder

[    1.021799] cpuidle: using governor menu

[    1.022206] TCP cubic registered

[    1.022401] NET: Registered protocol family 10

[    1.023217] NET: Registered protocol family 17

[    1.023302] Using IPI No-Shortcut mode

[    1.023447] PM: Resume from disk failed.

[    1.023464] registered taskstats version 1

[    1.023667]   Magic number: 13:619:248

[    1.023759] rtc_cmos 00:05: setting system clock to 2013-01-30 21:14:33 UTC (1359580473)

[    1.023762] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[    1.023765] EDD information not available.

[    1.112080] ata2.00: ATAPI: LITE-ON LTR-24102M, 4DS3, max UDMA/33

[    1.112215] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133

[    1.112220] ata1.00: 156250000 sectors, multi 8: LBA 

[    1.156661] ata2.00: configured for UDMA/33

[    1.200299] isapnp: No Plug & Play device found

[    1.200671] ata1.00: configured for UDMA/100

[    1.200827] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5

[    1.201052] sd 0:0:0:0: Attached scsi generic sg0 type 0

[    1.201265] sd 0:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)

[    1.201346] sd 0:0:0:0: [sda] Write Protect is off

[    1.201350] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    1.201385] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    1.201636]  sda:

[    1.201930] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-24102M       4DS3 PQ: 0 ANSI: 5

[    1.202737] sr0: scsi3-mmc drive: 8x/8x writer cd/rw xa/form2 cdda tray

[    1.202742] Uniform CD-ROM driver Revision: 3.20

[    1.202882] sr 1:0:0:0: Attached scsi CD-ROM sr0

[    1.202963] sr 1:0:0:0: Attached scsi generic sg1 type 5

[    1.218715]  sda1 sda2 < sda5 sda6 sda7 >

[    1.265534] sd 0:0:0:0: [sda] Attached SCSI disk

[    1.265559] Freeing unused kernel memory: 692k freed

[    1.266548] Write protecting the kernel text: 4948k

[    1.266584] Write protecting the kernel read-only data: 1980k

[    1.298494] udev[66]: starting version 163

[    1.424125] usb 1-4: new high speed USB device using ehci_hcd and address 3

[    1.620965] Floppy drive(s): fd0 is 1.44M

[    1.632858]   alloc irq_desc for 17 on node -1

[    1.632863]   alloc kstat_irqs on node -1

[    1.632875] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[    1.638115] FDC 0 is a post-1991 82077

[    1.652072] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)

[    1.652081] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)

[    1.652088] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)

[    1.692233] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0

[    1.692513] b44: b44.c:v2.0

[    1.713124] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:07:87:3b

[    1.796023] usb 3-1: new full speed USB device using uhci_hcd and address 2

[    1.967950] hub 3-1:1.0: USB hub found

[    1.968928] hub 3-1:1.0: 4 ports detected

[    2.249935] usb 3-1.2: new low speed USB device using uhci_hcd and address 3

[    2.425411] usbcore: registered new interface driver hiddev

[    2.440918] input: Dell Dell QuietKey Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.2/3-1.2:1.0/input/input2

[    2.441166] generic-usb 0003:413C:2106.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell QuietKey Keyboard] on usb-0000:00:1d.1-1.2/input0

[    2.441439] usbcore: registered new interface driver usbhid

[    2.441443] usbhid: USB HID core driver

[    2.461531] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)

[    2.465959] usb 3-1.3: new low speed USB device using uhci_hcd and address 4

[    2.619899] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.0/input/input3

[    2.620084] generic-usb 0003:0461:4D0F.0002: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-1.3/input0

[    2.693952] usb 3-1.4: new full speed USB device using uhci_hcd and address 5

[    2.795945] usb 3-1.4: not running at top speed; connect to a high speed hub

[   16.947947] Adding 1534972k swap on /dev/sda7.  Priority:-1 extents:1 across:1534972k 

[   17.009939] udev[263]: starting version 163

[   17.277156] intel_rng: FWH not detected

[   17.302331] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   17.361996] lp: driver loaded but no devices found

[   17.478656] Disabling lock debugging due to kernel taint

[   17.549137] Linux agpgart interface v0.103

[   17.656554] agpgart-intel 0000:00:00.0: Intel 830M Chipset

[   17.656828] agpgart-intel 0000:00:00.0: detected 892K stolen memory

[   17.658755] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000

[   17.775833] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)

[   17.776324] Initializing USB Mass Storage driver...

[   17.776752] parport_pc 00:08: reported by Plug and Play ACPI

[   17.776804] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]

[   17.778509] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro

[   17.841247] scsi2 : usb-storage 3-1.4:1.0

[   17.841996] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)

[   17.865095] lp0: using parport0 (interrupt-driven).

[   17.873940] usbcore: registered new interface driver usb-storage

[   17.873944] USB Mass Storage support registered.

[   17.904611] ppdev: user-space parallel port driver

[   17.945281] [drm] Initialized drm 1.1.0 20060810

[   18.056871] type=1400 audit(1359598490.531:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=507 comm="apparmor_parser"

[   18.059309] type=1400 audit(1359598490.531:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=512 comm="apparmor_parser"

[   18.059980] type=1400 audit(1359598490.531:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=512 comm="apparmor_parser"

[   18.060210] type=1400 audit(1359598490.535:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=507 comm="apparmor_parser"

[   18.060575] type=1400 audit(1359598490.535:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=507 comm="apparmor_parser"

[   18.065137] type=1400 audit(1359598490.539:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=512 comm="apparmor_parser"

[   18.243511] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[   18.243521] i915 0000:00:02.0: setting latency timer to 64

[   18.291187] [drm] set up 7M of stolen space

[   18.345457] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem

[   18.345857] [drm] initialized overlay support

[   18.384140] usb 1-4: reset high speed USB device using ehci_hcd and address 3

[   18.596407] Console: switching to colour frame buffer device 170x48

[   18.601244] fb0: inteldrmfb frame buffer device

[   18.601246] drm: registered panic notifier

[   18.616697] Slow work thread pool: Starting up

[   18.645081] Slow work thread pool: Ready

[   18.645103] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0

[   18.645346] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17

[   18.645387] Intel ICH 0000:00:1f.5: setting latency timer to 64

[   18.892638] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GE20LU11  CL00 PQ: 0 ANSI: 0

[   18.903626] sr1: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray

[   18.906520] sr 2:0:0:0: Attached scsi CD-ROM sr1

[   18.906836] sr 2:0:0:0: Attached scsi generic sg2 type 5

[   19.080053] intel8x0_measure_ac97_clock: measured 52257 usecs (2518 samples)

[   19.080059] intel8x0: clocking to 48000

[   19.462005] ADDRCONF(NETDEV_UP): eth0: link is not ready

[   19.467892] ndiswrapper (check_nt_hdr:147): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B

[   19.467986] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192su'

[   19.468882] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192su; check system log for messages from 'loadndisdriver'

[   19.469058] usbcore: registered new interface driver ndiswrapper

[   19.518758] type=1400 audit(1359598491.991:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=891 comm="apparmor_parser"

[   19.548700] type=1400 audit(1359598492.023:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=893 comm="apparmor_parser"

[   19.549372] type=1400 audit(1359598492.023:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=893 comm="apparmor_parser"

[   19.549742] type=1400 audit(1359598492.023:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=893 comm="apparmor_parser"

[   20.169928] vboxdrv: Trying to deactivate the NMI watchdog permanently...

[   20.169937] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance

[   20.169939] vboxdrv: counter framework which can generate NMIs is active. You have to prevent

[   20.169941] vboxdrv: the usage of hardware performance counters by

[   20.169943] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid

[   20.169948] vboxdrv: Found 1 processor cores.

[   20.173919] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.

[   20.173925] vboxdrv: Successfully loaded version 3.2.8_OSE (interface 0x00140001).

[   22.214484] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0

[   35.726242] UDF-fs: Partition marked readonly; forcing readonly mount

[   35.764706] UDF-fs INFO UDF: Mounting volume 'F9L1002v1', timestamp 2011/03/02 05:46 (1ed4)

[   37.825325] ISO 9660 Extensions: Microsoft Joliet Level 3

[   37.873354] ISO 9660 Extensions: RRIP_1991A


sudo lshw -C network

  *-network               

       description: Ethernet interface

       product: BCM4401 100Base-T

       vendor: Broadcom Corporation

       physical id: 9

       bus info: pci@0000:01:09.0

       logical name: eth0

       version: 01

       serial: 00:0d:56:07:87:3b

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s

       resources: irq:17 memory:fe9fe000-fe9fffff memory:fea00000-fea03fff

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: vboxnet0

       serial: 0a:00:27:00:00:00

       capabilities: ethernet physical

       configuration: broadcast=yes multicast=yes

iwlist scan

\lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



vboxnet0  Interface doesn't support scanning.

lsb_release  -d

Description:    Ubuntu 10.10


uname  -mr

2.6.35-32-generic i686

sudo /etc/intid/networkingrestart

sudo: /etc/intid/networkingrestart: command not found

---

### Post by Bucky Ball on 2013-01-30
All good but please use code tags. [code] before the code and add / before code in the end tag.

Which release are you using?

Take the Belkin dongle out and try working on the internal wireless card first. Have you done an update and checked Additional Drivers?

---

### Post by ahallubuntu on 2013-01-30
> **C.Clear said:**
> 
Description:    Ubuntu 10.10

uname  -mr

2.6.35-32-generic i686


Support for Ubuntu 10.10 (released in October 2010) ended almost a year ago.  You can't even install updates anymore.  Don't waste your time trying to use something obsolete.  My recommendation is to start with Ubuntu 12.04 LTS.

---

### Post by Bucky Ball on 2013-01-30
Description:    Ubuntu 10.10

Cheers. I missed that but did see the kernel was old, which is why I asked.

+1. 10.10 is dead. Try 12.04 LTS, supported until April 2017 and stable. You will hopefully have better luck.

---

### Post by C.Clear on 2013-01-31
did try 12.04, which is why I went back to using 10.10 (that and I prefer 10.10's setup)

thought it was a hardware problem because I got a  "unable to enumerate on port.." message and my connection even on windows was shaky. 

Now it works perfect in windows, but unable to make work in Ubuntu. One trick I used for a while which might be a clue to the problem is that I'd leave the connection on in Windows for about a hour or two then switch to Ubuntu that sometimes did the trick.

---

### Post by Bucky Ball on 2013-01-31
If you mean you don't like 12.04 because of the desktop environment Unity then you can always try something else. Xubuntu is one people have gone to. The other option is to install 12.04 then install xfce4, the DE used by Xubuntu, log out, choose it from 'Sessions' then log in.

10.10 is vulnerable and could be compromised if that machine is online.

---

### Post by ahallubuntu on 2013-01-31
Go back to 12.04, open Ubuntu Software Center, search for "Gnome Shell" and install it, log out, choose "Gnome Classic" as the session, and login.  Takes about two minutes.  Looks almost exactly like the "setup" in 10.10, with the menus at the top etc.  I use Gnome Classic myself in 12.04, not a fan of "Unity."

Once you are back in 12.04, report back the results of "lsusb" and "sudo lshw -C network" again.  Perhaps it is a hardware problem, perhaps not.  USB WiFi dongles are cheap, under $10 USD easily on eBay if you want a very basic one.

---

### Post by C.Clear on 2013-02-01
Hi;

Just wanted to follow up on you and let you know how your suggestion worked out. I installed 12.04 even at the install the drivers on the install disk picked up the network. 

And unlike the first time I updated my video files and other files actually worked. so I guess my problem is solved and thank you for the help. Just in case it might be of help to you or anyone going to post the lsusb and sudo lshw -C network results so you can see what changed from the previous one. Once again thank you for your help.

```

**lsusb**
                                  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 003: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU] 
 Bus 001 Device 004: ID 0781:5530 SanDisk Corp. Cruzer 
 Bus 003 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-Port Hub 
 Bus 003 Device 003: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard 
 Bus 003 Device 004: ID 0461:4d0f Primax Electronics, Ltd  
 Bus 003 Device 005: ID 152e:1640 LG (HLDS) 


``` 

```


 **sudo lshw -C network**
 *-network                
        description: Ethernet interface 
        product: BCM4401 100Base-T 
        vendor: Broadcom Corporation 
        physical id: 9 
        bus info: pci@0000:01:09.0 
        logical name: eth0 
        version: 01 
        serial: 00:0d:56:07:87:3b 
        size: 10Mbit/s 
        capacity: 100Mbit/s 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s 
        resources: irq:17 memory:fe9fe000-fe9fffff memory:fea00000-fea03fff 
   *-network 
        description: Wireless interface 
        physical id: 1 
        bus info: usb@1:4 
        logical name: wlan0 
        serial: 08:86:3b:bc:59:68 
        capabilities: ethernet physical wireless 
        configuration: broadcast=yes driver=r8712u ip=192.168.1.107 multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by Bucky Ball on 2013-02-01
Great news! Best way to help others is to mark the thread as 'Solved' from Thread Tools at top right.

Enjoy and don't hesitate to post a new thread with any other problems/questions. ;)

---

