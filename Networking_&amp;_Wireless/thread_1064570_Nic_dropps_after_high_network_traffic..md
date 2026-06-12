---
title: "Nic dropps after high network traffic."
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by kilowhisky on 2009-02-09
Ever since the 2.6.27-11-generic kernel update i have had a recurring problem with my network connection and after 2 days of googling i have found nothing on how to fix the problem.  Only repair the connection after it has gone down.  I did find some references to a problem in very old kernels involving the forcedeth nvidia driver.  But i can not find any sort of fix that would apply to my 8.10 system.  I have also already tried removing the kernel and i'm still having the issue.  

What happens is after a moving alot of data over the nic. It will abruptly stop responding.  Pings will respond but it takes several minutes to come back.  Nothing else will respond. The only way to bring the connection back is to run "rmmod forcedeth" and modprobe forcedeth back in.  

EDIt: as i'm writing this my network connection is now dropping at random times. 

Another symptom is that the whole system freezes for a couple seconds as the nic dies.  

I've never asked for help like this so i'll post all the relevant logs.  

ifconfig
```


eth0      Link encap:Ethernet  HWaddr 00:22:15:a1:21:22  
          inet addr:10.0.1.5  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: 2002:4408:e361:0:222:15ff:fea1:2122/64 Scope:Global
          inet6 addr: fe80::222:15ff:fea1:2122/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22321403 (22.3 MB)  TX bytes:78859084 (78.8 MB)
          Interrupt:218 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:760056 (760.0 KB)  TX bytes:760056 (760.0 KB)

```

dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7ee0000 (usable)
[    0.000000]  BIOS-e820: 00000000b7ee0000 - 00000000b7ee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7ee3000 - 00000000b7ef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7ef0000 - 00000000b7f00000 (reserved)
[    0.000000]  BIOS-e820: 00000000b8000000 - 00000000d8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000128000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xb7ee0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 37827000 - 37fef52d
[    0.000000] ACPI: RSDP 000F7230, 0024 (r2 Nvidia)
[    0.000000] ACPI: XSDT B7EE3100, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP B7EED480, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080609]
[    0.000000] ACPI: DSDT B7EE3280, A1B2 (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS B7EE0A80, 0040
[    0.000000] ACPI: HPET B7EED6C0, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG B7EED740, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC B7EED5C0, 008E (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] 2046MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [0037827000 - 0037fef52d]          RAMDISK ==> [0037827000 - 0037fef52d]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f56a0] 000f56a0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000b7ee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000b7ee0
[    0.000000] On node 0 totalpages: 753262
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3946 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 519394 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at da000000 (gap: d8000000:18000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 746640
[    0.000000] Kernel command line: root=UUID=278f5e54-7e1d-42f9-a7df-5d5a7777aa48 ro quiet splash acpi=force irqpoll 
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2371.808 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2971904k/3013504k available (2576k kernel code, 40384k reserved, 1165k data, 424k init, 2096000k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4743.61 BogoMIPS (lpj=9487232)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(4) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017375] ACPI: Core revision 20080609
[    0.020859] ACPI: Checking initramfs for custom DSDT
[    0.296343] ENABLING IO-APIC IRQs
[    0.296569] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.338628] CPU0: AMD Phenom(tm) 9600 Quad-Core Processor stepping 02
[    0.340021] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4743.73 BogoMIPS (lpj=9487479)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(4) -> Core 1
[    0.424384] CPU1: AMD Phenom(tm) 9600 Quad-Core Processor stepping 02
[    0.424403] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.428084] Booting processor 2/2 ip 6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4743.83 BogoMIPS (lpj=9487671)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 2(4) -> Core 2
[    0.516422] CPU2: AMD Phenom(tm) 9600 Quad-Core Processor stepping 02
[    0.516442] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.520086] Booting processor 3/3 ip 6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4743.75 BogoMIPS (lpj=9487517)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 3(4) -> Core 3
[    0.608356] CPU3: AMD Phenom(tm) 9600 Quad-Core Processor stepping 02
[    0.608379] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.612039] Brought up 4 CPUs
[    0.612041] Total of 4 processors activated (18974.94 BogoMIPS).
[    0.612080] CPU0 attaching sched-domain:
[    0.612083]  domain 0: span 0-3 level CPU
[    0.612085]   groups: 0 1 2 3
[    0.612091] CPU1 attaching sched-domain:
[    0.612092]  domain 0: span 0-3 level CPU
[    0.612094]   groups: 1 2 3 0
[    0.612098] CPU2 attaching sched-domain:
[    0.612100]  domain 0: span 0-3 level CPU
[    0.612101]   groups: 2 3 0 1
[    0.612105] CPU3 attaching sched-domain:
[    0.612107]  domain 0: span 0-3 level CPU
[    0.612108]   groups: 3 0 1 2
[    0.612184] net_namespace: 840 bytes
[    0.612184] Booting paravirtualized kernel on bare hardware
[    0.612280] Time: 18:16:47  Date: 02/08/09
[    0.612304] NET: Registered protocol family 16
[    0.612321] EISA bus registered
[    0.612321] ACPI: bus type pci registered
[    0.612321] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.612321] PCI: MCFG area at f0000000 reserved in E820
[    0.612321] PCI: Using MMCONFIG for extended config space
[    0.612321] PCI: Using configuration type 1 for base access
[    0.613326] ACPI: EC: Look up EC in DSDT
[    0.634393] ACPI: Interpreter enabled
[    0.634400] ACPI: (supports S0 S1 S3 S4 S5)
[    0.634417] ACPI: Using IOAPIC for interrupt routing
[    0.660248] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.660258] PCI: 0000:00:01.1 reg 10 io port: [ff00, ff3f]
[    0.660269] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
[    0.660273] PCI: 0000:00:01.1 reg 24 io port: [1c40, 1c7f]
[    0.660288] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.660294] pci 0000:00:01.1: PME# disabled
[    0.660342] PCI: 0000:00:01.3 reg 10 32bit mmio: [fdf80000, fdffffff]
[    0.660459] PCI: 0000:00:02.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.660479] pci 0000:00:02.0: supports D1
[    0.660481] pci 0000:00:02.0: supports D2
[    0.660483] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.660485] pci 0000:00:02.0: PME# disabled
[    0.660504] PCI: 0000:00:02.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    0.660528] pci 0000:00:02.1: supports D1
[    0.660529] pci 0000:00:02.1: supports D2
[    0.660531] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.660534] pci 0000:00:02.1: PME# disabled
[    0.660554] PCI: 0000:00:04.0 reg 10 32bit mmio: [fe02d000, fe02dfff]
[    0.660574] pci 0000:00:04.0: supports D1
[    0.660575] pci 0000:00:04.0: supports D2
[    0.660577] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.660580] pci 0000:00:04.0: PME# disabled
[    0.660598] PCI: 0000:00:04.1 reg 10 32bit mmio: [fe02c000, fe02c0ff]
[    0.660622] pci 0000:00:04.1: supports D1
[    0.660623] pci 0000:00:04.1: supports D2
[    0.660625] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.660628] pci 0000:00:04.1: PME# disabled
[    0.660656] PCI: 0000:00:06.0 reg 20 io port: [fc00, fc0f]
[    0.660687] PCI: 0000:00:07.0 reg 10 32bit mmio: [fe020000, fe023fff]
[    0.660710] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.660713] pci 0000:00:07.0: PME# disabled
[    0.660753] PCI: 0000:00:09.0 reg 10 io port: [9f0, 9f7]
[    0.660757] PCI: 0000:00:09.0 reg 14 io port: [bf0, bf3]
[    0.660760] PCI: 0000:00:09.0 reg 18 io port: [970, 977]
[    0.660763] PCI: 0000:00:09.0 reg 1c io port: [b70, b73]
[    0.660766] PCI: 0000:00:09.0 reg 20 io port: [f700, f70f]
[    0.660769] PCI: 0000:00:09.0 reg 24 32bit mmio: [fe026000, fe027fff]
[    0.660797] PCI: 0000:00:0a.0 reg 10 32bit mmio: [fe02b000, fe02bfff]
[    0.660801] PCI: 0000:00:0a.0 reg 14 io port: [f600, f607]
[    0.660804] PCI: 0000:00:0a.0 reg 18 32bit mmio: [fe02a000, fe02a0ff]
[    0.660808] PCI: 0000:00:0a.0 reg 1c 32bit mmio: [fe029000, fe02900f]
[    0.660823] pci 0000:00:0a.0: supports D1
[    0.660824] pci 0000:00:0a.0: supports D2
[    0.660826] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.660829] pci 0000:00:0a.0: PME# disabled
[    0.660851] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.660853] pci 0000:00:0b.0: PME# disabled
[    0.661025] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.661032] pci 0000:00:10.0: PME# disabled
[    0.661202] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.661209] pci 0000:00:12.0: PME# disabled
[    0.661376] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.661383] pci 0000:00:13.0: PME# disabled
[    0.661550] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.661557] pci 0000:00:14.0: PME# disabled
[    0.661654] PCI: 0000:01:08.0 reg 10 32bit mmio: [ec000000, efffffff]
[    0.661704] PCI: 0000:01:09.0 reg 10 32bit mmio: [fdeff000, fdeff7ff]
[    0.661735] pci 0000:01:09.0: supports D1
[    0.661736] pci 0000:01:09.0: supports D2
[    0.661755] PCI: 0000:01:0a.0 reg 10 32bit mmio: [fdefe000, fdefefff]
[    0.661785] pci 0000:01:0a.0: supports D1
[    0.661786] pci 0000:01:0a.0: supports D2
[    0.661788] pci 0000:01:0a.0: PME# supported from D0 D1 D2 D3hot
[    0.661791] pci 0000:01:0a.0: PME# disabled
[    0.661811] PCI: 0000:01:0b.0 reg 10 32bit mmio: [e8000000, ebffffff]
[    0.661861] pci 0000:00:08.0: transparent bridge
[    0.661863] PCI: bridge 0000:00:08.0 io port: [e000, efff]
[    0.661866] PCI: bridge 0000:00:08.0 32bit mmio: [fde00000, fdefffff]
[    0.661869] PCI: bridge 0000:00:08.0 32bit mmio pref: [e8000000, efffffff]
[    0.661885] PCI: 0000:02:00.0 reg 10 32bit mmio: [fb000000, fbffffff]
[    0.661890] PCI: 0000:02:00.0 reg 14 64bit mmio: [d8000000, dfffffff]
[    0.661895] PCI: 0000:02:00.0 reg 1c 64bit mmio: [e6000000, e7ffffff]
[    0.661898] PCI: 0000:02:00.0 reg 24 io port: [dc00, dc7f]
[    0.661902] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.661922] PCI: bridge 0000:00:0b.0 io port: [d000, dfff]
[    0.661924] PCI: bridge 0000:00:0b.0 32bit mmio: [fb000000, fcffffff]
[    0.661927] PCI: bridge 0000:00:0b.0 64bit mmio pref: [d8000000, e7ffffff]
[    0.661978] PCI: bridge 0000:00:10.0 io port: [c000, cfff]
[    0.661985] PCI: bridge 0000:00:10.0 32bit mmio: [fdd00000, fddfffff]
[    0.661998] PCI: bridge 0000:00:10.0 64bit mmio pref: [fdc00000, fdcfffff]
[    0.662051] PCI: bridge 0000:00:12.0 io port: [b000, bfff]
[    0.662059] PCI: bridge 0000:00:12.0 32bit mmio: [fdb00000, fdbfffff]
[    0.662072] PCI: bridge 0000:00:12.0 64bit mmio pref: [fda00000, fdafffff]
[    0.662115] PCI: 0000:05:00.0 reg 10 64bit mmio: [fd400000, fd5fffff]
[    0.664032] pci 0000:05:00.0: supports D1
[    0.664034] pci 0000:05:00.0: supports D2
[    0.664035] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot
[    0.664040] pci 0000:05:00.0: PME# disabled
[    0.664080] PCI: bridge 0000:00:13.0 io port: [a000, afff]
[    0.664087] PCI: bridge 0000:00:13.0 32bit mmio: [fd400000, fd5fffff]
[    0.664100] PCI: bridge 0000:00:13.0 64bit mmio pref: [fd900000, fd9fffff]
[    0.664153] PCI: bridge 0000:00:14.0 io port: [9000, 9fff]
[    0.664160] PCI: bridge 0000:00:14.0 32bit mmio: [fd800000, fd8fffff]
[    0.664173] PCI: bridge 0000:00:14.0 64bit mmio pref: [fd700000, fd7fffff]
[    0.664225] bus 00 -> node 0
[    0.664231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.664836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.905204] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 *10 11 14 15)
[    0.905204] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 *7 9 10 11 14 15)
[    0.905204] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 *7 9 10 11 14 15)
[    0.905310] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[    0.905629] ACPI: PCI Interrupt Link [LE0A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.905946] ACPI: PCI Interrupt Link [LE0B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.908047] ACPI: PCI Interrupt Link [LE0C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.908361] ACPI: PCI Interrupt Link [LE0D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.908688] ACPI: PCI Interrupt Link [LE1A] (IRQs 5 7 9 10 *11 14 15)
[    0.909012] ACPI: PCI Interrupt Link [LE1B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.909343] ACPI: PCI Interrupt Link [LE1C] (IRQs *5 7 9 10 11 14 15)
[    0.909674] ACPI: PCI Interrupt Link [LE1D] (IRQs 5 7 9 *10 11 14 15)
[    0.909994] ACPI: PCI Interrupt Link [LE2A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.910318] ACPI: PCI Interrupt Link [LE2B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.910636] ACPI: PCI Interrupt Link [LE2C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.910959] ACPI: PCI Interrupt Link [LE2D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.911282] ACPI: PCI Interrupt Link [LE3A] (IRQs 5 7 9 10 *11 14 15)
[    0.911603] ACPI: PCI Interrupt Link [LE3B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.911922] ACPI: PCI Interrupt Link [LE3C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.912255] ACPI: PCI Interrupt Link [LE3D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.912569] ACPI: PCI Interrupt Link [LE4A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.912887] ACPI: PCI Interrupt Link [LE4B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.913211] ACPI: PCI Interrupt Link [LE4C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.913531] ACPI: PCI Interrupt Link [LE4D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.913855] ACPI: PCI Interrupt Link [LE5A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.914179] ACPI: PCI Interrupt Link [LE5B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.914504] ACPI: PCI Interrupt Link [LE5C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.914821] ACPI: PCI Interrupt Link [LE5D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.915149] ACPI: PCI Interrupt Link [LE6A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.915464] ACPI: PCI Interrupt Link [LE6B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.915784] ACPI: PCI Interrupt Link [LE6C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.916111] ACPI: PCI Interrupt Link [LE6D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.916432] ACPI: PCI Interrupt Link [LE7A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.916755] ACPI: PCI Interrupt Link [LE7B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.917074] ACPI: PCI Interrupt Link [LE7C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.917402] ACPI: PCI Interrupt Link [LE7D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.917727] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.918065] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[    0.918395] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.918724] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 *7 9 10 11 14 15)
[    0.919049] ACPI: PCI Interrupt Link [LU1B] (IRQs *5 7 9 10 11 14 15)
[    0.919376] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 *10 11 14 15)
[    0.919704] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[    0.920043] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[    0.920376] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 *7 9 10 11 14 15)
[    0.920702] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.921032] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.921361] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.921720] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.922081] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.922446] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.922810] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.923165] ACPI: PCI Interrupt Link [AE0A] (IRQs 16) *0, disabled.
[    0.923511] ACPI: PCI Interrupt Link [AE0B] (IRQs 16) *0, disabled.
[    0.923865] ACPI: PCI Interrupt Link [AE0C] (IRQs 16) *0, disabled.
[    0.924233] ACPI: PCI Interrupt Link [AE0D] (IRQs 16) *0, disabled.
[    0.924578] ACPI: PCI Interrupt Link [AE1A] (IRQs 16) *0
[    0.924928] ACPI: PCI Interrupt Link [AE1B] (IRQs 16) *0, disabled.
[    0.925280] ACPI: PCI Interrupt Link [AE1C] (IRQs 16) *0
[    0.925626] ACPI: PCI Interrupt Link [AE1D] (IRQs 16) *0
[    0.925979] ACPI: PCI Interrupt Link [AE2A] (IRQs 16) *0, disabled.
[    0.926329] ACPI: PCI Interrupt Link [AE2B] (IRQs 16) *0, disabled.
[    0.926676] ACPI: PCI Interrupt Link [AE2C] (IRQs 16) *0, disabled.
[    0.927029] ACPI: PCI Interrupt Link [AE2D] (IRQs 16) *0, disabled.
[    0.927377] ACPI: PCI Interrupt Link [AE3A] (IRQs 16) *0
[    0.927725] ACPI: PCI Interrupt Link [AE3B] (IRQs 16) *0, disabled.
[    0.928084] ACPI: PCI Interrupt Link [AE3C] (IRQs 16) *0, disabled.
[    0.928434] ACPI: PCI Interrupt Link [AE3D] (IRQs 16) *0, disabled.
[    0.928782] ACPI: PCI Interrupt Link [AE4A] (IRQs 16) *0, disabled.
[    0.929129] ACPI: PCI Interrupt Link [AE4B] (IRQs 16) *0, disabled.
[    0.929477] ACPI: PCI Interrupt Link [AE4C] (IRQs 16) *0, disabled.
[    0.929827] ACPI: PCI Interrupt Link [AE4D] (IRQs 16) *0, disabled.
[    0.930176] ACPI: PCI Interrupt Link [AE5A] (IRQs 16) *0, disabled.
[    0.930531] ACPI: PCI Interrupt Link [AE5B] (IRQs 16) *0, disabled.
[    0.930878] ACPI: PCI Interrupt Link [AE5C] (IRQs 16) *0, disabled.
[    0.931224] ACPI: PCI Interrupt Link [AE5D] (IRQs 16) *0, disabled.
[    0.931576] ACPI: PCI Interrupt Link [AE6A] (IRQs 16) *0, disabled.
[    0.931926] ACPI: PCI Interrupt Link [AE6B] (IRQs 16) *0, disabled.
[    0.932284] ACPI: PCI Interrupt Link [AE6C] (IRQs 16) *0, disabled.
[    0.932636] ACPI: PCI Interrupt Link [AE6D] (IRQs 16) *0, disabled.
[    0.932984] ACPI: PCI Interrupt Link [AE7A] (IRQs 16) *0, disabled.
[    0.933338] ACPI: PCI Interrupt Link [AE7B] (IRQs 16) *0, disabled.
[    0.933688] ACPI: PCI Interrupt Link [AE7C] (IRQs 16) *0, disabled.
[    0.934034] ACPI: PCI Interrupt Link [AE7D] (IRQs 16) *0, disabled.
[    0.934387] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.934744] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[    0.935103] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
[    0.935463] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
[    0.935819] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
[    0.936191] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.936544] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[    0.936903] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.937263] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.937619] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.937981] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.938340] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.938442] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.938442] pnp: PnP ACPI init
[    0.938442] ACPI: bus type pnp registered
[    0.950660] pnp: PnP ACPI: found 12 devices
[    0.950660] ACPI: ACPI bus type pnp unregistered
[    0.950660] PnPBIOS: Disabled by ACPI PNP
[    0.950660] PCI: Using ACPI for IRQ routing
[    0.956037] NET: Registered protocol family 8
[    0.956039] NET: Registered protocol family 20
[    0.956051] NetLabel: Initializing
[    0.956051] NetLabel:  domain hash size = 128
[    0.956051] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.956051] NetLabel:  unlabeled traffic allowed by default
[    0.956056] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.956060] hpet0: 3 32-bit timers, 25000000 Hz
[    0.957935] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.957937]    actual entries 65620
[    0.958018] AppArmor: AppArmor Filesystem Enabled
[    0.958043] ACPI: RTC can wake from S4
[    0.960040] Switched to high resolution mode on CPU 0
[    0.960405] Switched to high resolution mode on CPU 3
[    0.960429] Switched to high resolution mode on CPU 1
[    0.960464] Switched to high resolution mode on CPU 2
[    0.964029] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.964032] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.964034] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.964037] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.964039] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.964041] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.964044] system 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[    0.964047] system 00:01: iomem range 0xb8000000-0xd7ffffff could not be reserved
[    0.964052] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.964055] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.964059] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.964067] system 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.964072] system 00:0b: iomem range 0xd2a00-0xd3fff has been reserved
[    0.964075] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[    0.964077] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[    0.964079] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    0.964082] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
[    0.964084] system 00:0b: iomem range 0xb7ee0000-0xb7efffff could not be reserved
[    0.964086] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.964089] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.964091] system 00:0b: iomem range 0x100000-0xb7edffff could not be reserved
[    0.964094] system 00:0b: iomem range 0xb7ff0000-0xd7feffff could not be reserved
[    0.964096] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.964099] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.964101] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
[    0.964104] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.964106] system 00:0b: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.964109] system 00:0b: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.999203] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.999206] pci 0000:00:08.0:   IO window: 0xe000-0xefff
[    0.999210] pci 0000:00:08.0:   MEM window: 0xfde00000-0xfdefffff
[    0.999213] pci 0000:00:08.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.999219] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.999222] pci 0000:00:0b.0:   IO window: 0xd000-0xdfff
[    0.999224] pci 0000:00:0b.0:   MEM window: 0xfb000000-0xfcffffff
[    0.999227] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000e7ffffff
[    0.999231] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.999235] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.999244] pci 0000:00:10.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.999251] pci 0000:00:10.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.999264] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
[    0.999268] pci 0000:00:12.0:   IO window: 0xb000-0xbfff
[    0.999278] pci 0000:00:12.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.999285] pci 0000:00:12.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.999297] pci 0000:00:13.0: PCI bridge, secondary bus 0000:05
[    0.999301] pci 0000:00:13.0:   IO window: 0xa000-0xafff
[    0.999311] pci 0000:00:13.0:   MEM window: 0xfd400000-0xfd5fffff
[    0.999318] pci 0000:00:13.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.999330] pci 0000:00:14.0: PCI bridge, secondary bus 0000:06
[    0.999335] pci 0000:00:14.0:   IO window: 0x9000-0x9fff
[    0.999344] pci 0000:00:14.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.999351] pci 0000:00:14.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.999368] pci 0000:00:08.0: setting latency timer to 64
[    0.999372] pci 0000:00:0b.0: setting latency timer to 64
[    0.999902] ACPI: PCI Interrupt Link [AE0A] enabled at IRQ 16
[    0.999910] pci 0000:00:10.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    0.999918] pci 0000:00:10.0: setting latency timer to 64
[    1.000444] ACPI: PCI Interrupt Link [AE2A] enabled at IRQ 16
[    1.000446] pci 0000:00:12.0: PCI INT A -> Link[AE2A] -> GSI 16 (level, low) -> IRQ 16
[    1.000454] pci 0000:00:12.0: setting latency timer to 64
[    1.000945] ACPI: PCI Interrupt Link [AE3A] enabled at IRQ 16
[    1.000948] pci 0000:00:13.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
[    1.000955] pci 0000:00:13.0: setting latency timer to 64
[    1.001450] ACPI: PCI Interrupt Link [AE4A] enabled at IRQ 16
[    1.001452] pci 0000:00:14.0: PCI INT A -> Link[AE4A] -> GSI 16 (level, low) -> IRQ 16
[    1.001460] pci 0000:00:14.0: setting latency timer to 64
[    1.001465] bus: 00 index 0 io port: [0, ffff]
[    1.001467] bus: 00 index 1 mmio: [0, ffffffff]
[    1.001469] bus: 01 index 0 io port: [e000, efff]
[    1.001471] bus: 01 index 1 mmio: [fde00000, fdefffff]
[    1.001472] bus: 01 index 2 mmio: [e8000000, efffffff]
[    1.001474] bus: 01 index 3 io port: [0, ffff]
[    1.001476] bus: 01 index 4 mmio: [0, ffffffff]
[    1.001477] bus: 02 index 0 io port: [d000, dfff]
[    1.001479] bus: 02 index 1 mmio: [fb000000, fcffffff]
[    1.001481] bus: 02 index 2 mmio: [d8000000, e7ffffff]
[    1.001482] bus: 02 index 3 mmio: [0, 0]
[    1.001484] bus: 03 index 0 io port: [c000, cfff]
[    1.001486] bus: 03 index 1 mmio: [fdd00000, fddfffff]
[    1.001487] bus: 03 index 2 mmio: [fdc00000, fdcfffff]
[    1.001489] bus: 03 index 3 mmio: [0, 0]
[    1.001490] bus: 04 index 0 io port: [b000, bfff]
[    1.001492] bus: 04 index 1 mmio: [fdb00000, fdbfffff]
[    1.001494] bus: 04 index 2 mmio: [fda00000, fdafffff]
[    1.001495] bus: 04 index 3 mmio: [0, 0]
[    1.001497] bus: 05 index 0 io port: [a000, afff]
[    1.001498] bus: 05 index 1 mmio: [fd400000, fd5fffff]
[    1.001500] bus: 05 index 2 mmio: [fd900000, fd9fffff]
[    1.001501] bus: 05 index 3 mmio: [0, 0]
[    1.001503] bus: 06 index 0 io port: [9000, 9fff]
[    1.001505] bus: 06 index 1 mmio: [fd800000, fd8fffff]
[    1.001506] bus: 06 index 2 mmio: [fd700000, fd7fffff]
[    1.001508] bus: 06 index 3 mmio: [0, 0]
[    1.001518] NET: Registered protocol family 2
[    1.016055] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.016263] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.016591] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.016789] TCP: Hash tables configured (established 131072 bind 65536)
[    1.016791] TCP reno registered
[    1.020078] NET: Registered protocol family 1
[    1.020176] checking if image is initramfs... it is
[    1.570003] Freeing initrd memory: 7969k freed
[    1.571370] audit: initializing netlink socket (disabled)
[    1.571387] type=2000 audit(1234117007.569:1): initialized
[    1.575984] highmem bounce pool size: 64 pages
[    1.575989] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.578261] VFS: Disk quotas dquot_6.5.1
[    1.578344] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.578435] msgmni has been set to 1727
[    1.578540] io scheduler noop registered
[    1.578542] io scheduler anticipatory registered
[    1.578543] io scheduler deadline registered
[    1.578555] io scheduler cfq registered (default)
[    1.579041] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.579070] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.579098] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.579128] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.579155] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.579210] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.579275] pci 0000:00:12.0: Enabling HT MSI Mapping
[    1.579341] pci 0000:00:13.0: Enabling HT MSI Mapping
[    1.579406] pci 0000:00:14.0: Enabling HT MSI Mapping
[    1.579452] pci 0000:02:00.0: Boot video device
[    1.579605] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.579772] pcieport-driver 0000:00:10.0: found MSI capability
[    1.579884] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.580123] pcieport-driver 0000:00:12.0: setting latency timer to 64
[    1.580288] pcieport-driver 0000:00:12.0: found MSI capability
[    1.580402] pci_express 0000:00:12.0:pcie00: allocate port service
[    1.580644] pcieport-driver 0000:00:13.0: setting latency timer to 64
[    1.580808] pcieport-driver 0000:00:13.0: found MSI capability
[    1.580922] pci_express 0000:00:13.0:pcie00: allocate port service
[    1.581159] pcieport-driver 0000:00:14.0: setting latency timer to 64
[    1.581323] pcieport-driver 0000:00:14.0: found MSI capability
[    1.581437] pci_express 0000:00:14.0:pcie00: allocate port service
[    1.581864] isapnp: Scanning for PnP cards...
[    1.934626] isapnp: No Plug & Play device found
[    1.969014] hpet_resources: 0xfeff0000 is busy
[    1.969133] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.969249] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.969884] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.971519] brd: module loaded
[    1.971582] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.971750] PNP: No PS/2 controller found. Probing ports directly.
[    2.006217] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    2.006219] If AUX port is really absent please use the 'i8042.noaux' option.
[    2.256102] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.257633] mice: PS/2 mouse device common for all mice
[    2.257745] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.257798] rtc0: alarms up to one year, y3k, hpet irqs
[    2.257920] EISA: Probing bus 0 at eisa.0
[    2.257925] Cannot allocate resource for EISA slot 1
[    2.257943] EISA: Detected 0 cards.
[    2.257946] cpuidle: using governor ladder
[    2.257948] cpuidle: using governor menu
[    2.258416] TCP cubic registered
[    2.258439] Using IPI No-Shortcut mode
[    2.258613] registered taskstats version 1
[    2.258740]   Magic number: 13:204:291
[    2.258751] tty ttyz5: hash matches
[    2.258785] tty tty24: hash matches
[    2.258878] rtc_cmos 00:05: setting system clock to 2009-02-08 18:16:49 UTC (1234117009)
[    2.258880] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.258882] EDD information not available.
[    2.259076] Freeing unused kernel memory: 424k freed
[    2.259133] Write protecting the kernel text: 2580k
[    2.259173] Write protecting the kernel read-only data: 940k
[    2.389317] fuse init (API version 7.9)
[    2.406996] fan PNP0C0B:00: registered as cooling_device0
[    2.407001] ACPI: Fan [FAN] (on)
[    2.412434] processor ACPI0007:00: registered as cooling_device1
[    2.412488] processor ACPI0007:01: registered as cooling_device2
[    2.412540] processor ACPI0007:02: registered as cooling_device3
[    2.412592] processor ACPI0007:03: registered as cooling_device4
[    2.414947] ACPI: Expecting a [Reference] package element, found type 0
[    2.415365] thermal LNXTHERM:01: registered as thermal_zone0
[    2.416073] ACPI: Thermal Zone [THRM] (40 C)
[    2.864555] usbcore: registered new interface driver usbfs
[    2.864576] usbcore: registered new interface driver hub
[    2.864602] usbcore: registered new device driver usb
[    2.866110] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.866653] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[    2.866664] ohci_hcd 0000:00:02.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
[    2.866674] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.866677] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.868890] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.868911] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[    2.890985] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.892521] No dock devices found.
[    2.909427] SCSI subsystem initialized
[    2.926643] usb usb1: configuration #1 chosen from 1 choice
[    2.926668] hub 1-0:1.0: USB hub found
[    2.926677] hub 1-0:1.0: 6 ports detected
[    2.940294] libata version 3.00 loaded.
[    3.132829] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 22
[    3.132841] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AU1B] -> GSI 22 (level, low) -> IRQ 22
[    3.132854] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    3.132857] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    3.132882] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    3.132903] ohci_hcd 0000:00:04.0: irq 22, io mem 0xfe02d000
[    3.190079] usb usb2: configuration #1 chosen from 1 choice
[    3.190103] hub 2-0:1.0: USB hub found
[    3.190111] hub 2-0:1.0: 6 ports detected
[    3.293251] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 21
[    3.293260] ehci_hcd 0000:00:02.1: PCI INT B -> Link[AUB2] -> GSI 21 (level, low) -> IRQ 21
[    3.293269] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.293272] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.293291] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    3.293312] ehci_hcd 0000:00:02.1: debug port 1
[    3.293315] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.293328] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfe02e000
[    3.308023] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    3.320020] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.320092] usb usb3: configuration #1 chosen from 1 choice
[    3.320114] hub 3-0:1.0: USB hub found
[    3.320119] hub 3-0:1.0: 6 ports detected
[    3.376036] hub 1-0:1.0: unable to enumerate USB device on port 1
[    3.529172] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 20
[    3.529180] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AU2B] -> GSI 20 (level, low) -> IRQ 20
[    3.529188] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    3.529190] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    3.529211] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[    3.529233] ehci_hcd 0000:00:04.1: debug port 1
[    3.529236] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    3.529249] ehci_hcd 0000:00:04.1: irq 20, io mem 0xfe02c000
[    3.596017] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.596103] usb usb4: configuration #1 chosen from 1 choice
[    3.596124] hub 4-0:1.0: USB hub found
[    3.596135] hub 4-0:1.0: 6 ports detected
[    3.804224] ahci 0000:00:09.0: version 3.0
[    3.804733] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    3.804737] ahci 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    3.804815] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    3.804819] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    3.804822] ahci 0000:00:09.0: setting latency timer to 64
[    3.805109] scsi0 : ahci
[    3.805505] scsi1 : ahci
[    3.805806] scsi2 : ahci
[    3.806119] scsi3 : ahci
[    3.806454] scsi4 : ahci
[    3.806822] scsi5 : ahci
[    3.806938] ata1: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 219
[    3.806941] ata2: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 219
[    3.806943] ata3: SATA max UDMA/133 irq_stat 0x00000040,  irq 219
[    3.806945] ata4: SATA max UDMA/133 irq_stat 0x00000040, connection status changed
[    3.806947] ata5: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026300 irq 219
[    3.806950] ata6: SATA max UDMA/133 irq_stat 0x00000040, connection status changed
[    4.048019] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    4.263877] usb 1-1: configuration #1 chosen from 1 choice
[    4.377519] usb 4-1: new high speed USB device using ehci_hcd and address 2
[    4.513826] usb 4-1: configuration #1 chosen from 1 choice
[    4.692020] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.720615] ata1.00: ATA-8: ST31000333AS, CC1F, max UDMA/133
[    4.720617] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.762458] ata1.00: configured for UDMA/133
[    5.648017] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.649532] ata2.00: ATA-8: ST31000340AS, SD15, max UDMA/133
[    5.649534] ata2.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.651473] ata2.00: configured for UDMA/133
[    6.536017] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.572919] ata3.00: ATA-7: ST3320620AS, 3.AAD, max UDMA/133
[    6.572921] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.631237] ata3.00: configured for UDMA/133
[    7.516018] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.529440] ata4.00: ATAPI: ATAPI   BD  O  DH4O1S, CP51, max UDMA/100, ATAPI AN
[    7.543031] ata4.00: configured for UDMA/100
[    7.860019] ata5: SATA link down (SStatus 0 SControl 300)
[    8.748017] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.748886] ata6.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100, ATAPI AN
[    8.749833] ata6.00: configured for UDMA/100
[    8.749929] scsi 0:0:0:0: Direct-Access     ATA      ST31000333AS     CC1F PQ: 0 ANSI: 5
[    8.750031] scsi 1:0:0:0: Direct-Access     ATA      ST31000340AS     SD15 PQ: 0 ANSI: 5
[    8.750117] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    8.750809] scsi 3:0:0:0: CD-ROM            ATAPI    BD  O  DH4O1S    CP51 PQ: 0 ANSI: 5
[    8.751373] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5
[    8.751444] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    8.751952] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    8.751956] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    8.751960] forcedeth 0000:00:0a.0: setting latency timer to 64
[    8.813584] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:a1:21:22
[    8.813587] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[    8.814747] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    8.814756] ohci1394 0000:01:0a.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    8.866600] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdefe000-fdefe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    8.877042] pata_acpi 0000:00:06.0: setting latency timer to 64
[    8.888025] pata_amd 0000:00:06.0: version 0.3.10
[    8.888067] pata_amd 0000:00:06.0: setting latency timer to 64
[    8.888138] scsi6 : pata_amd
[    8.888203] scsi7 : pata_amd
[    8.888891] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    8.888894] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    8.890583] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    8.890616] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    8.890650] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    8.890679] scsi 3:0:0:0: Attached scsi generic sg3 type 5
[    8.890710] scsi 5:0:0:0: Attached scsi generic sg4 type 5
[    8.899762] usbcore: registered new interface driver hiddev
[    8.902904] Driver 'sd' needs updating - please use bus_type methods
[    8.903250] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    8.903266] sd 0:0:0:0: [sda] Write Protect is off
[    8.903268] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.903285] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.903341] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    8.903351] sd 0:0:0:0: [sda] Write Protect is off
[    8.903353] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.903368] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.903371]  sda:<6>input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input1
[    8.912160] input,hidraw0: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:02.0-1
[    8.914141] Driver 'sr' needs updating - please use bus_type methods
[    8.920116] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.1/input/input2
[    8.925802]  sda1
[    8.925888] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.925955] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[    8.925966] sd 1:0:0:0: [sdb] Write Protect is off
[    8.925969] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    8.925990] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.926035] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[    8.926047] sd 1:0:0:0: [sdb] Write Protect is off
[    8.926049] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    8.926069] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.926072]  sdb:<6>input,hiddev96,hidraw1: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:02.0-1
[    8.926910] usbcore: registered new interface driver usbhid
[    8.926913] usbhid: v2.6:USB HID core driver
[    8.940617]  sdb1 sdb2 < sdb5 sdb6 >
[    8.956924] sd 1:0:0:0: [sdb] Attached SCSI disk
[    8.956982] sd 2:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[    8.956993] sd 2:0:0:0: [sdc] Write Protect is off
[    8.956996] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    8.957017] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.957057] sd 2:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[    8.957071] sd 2:0:0:0: [sdc] Write Protect is off
[    8.957075] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    8.957095] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.957102]  sdc: sdc1 sdc2
[    8.978405] sd 2:0:0:0: [sdc] Attached SCSI disk
[    8.980142] sr0: scsi3-mmc drive: 62x/62x cd/rw xa/form2 cdda tray
[    8.980146] Uniform CD-ROM driver Revision: 3.20
[    8.980209] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    8.983277] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.983335] sr 5:0:0:0: Attached scsi CD-ROM sr1
[    9.055146] ata8: port disabled. ignoring.
[    9.299856] PM: Starting manual resume from disk
[    9.299860] PM: Resume from partition 8:17
[    9.299862] PM: Checking hibernation image.
[    9.300111] PM: Resume from disk failed.
[    9.308248] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[    9.310519] SGI XFS Quota Management subsystem
[    9.415597] XFS mounting filesystem sdb6
[    9.590659] Starting XFS recovery on filesystem: sdb6 (logdev: internal)
[   10.144142] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00017726e7]
[   10.864388] Ending XFS recovery on filesystem: sdb6 (logdev: internal)
[   14.866838] udevd version 124 started
[   15.286430] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   15.309534] ACPI: Power Button (FF) [PWRF]
[   15.309602] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   15.341521] ACPI: Power Button (CM) [PWRB]
[   15.821690] Linux video capture interface: v2.00
[   15.976184] saa7130/34: v4l2 driver version 0.2.14 loaded
[   15.976971] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   15.976982] saa7134 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   15.976988] saa7133[0]: found at 0000:01:09.0, rev: 209, irq: 17, latency: 32, mmio: 0xfdeff000
[   15.976994] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]
[   15.977003] saa7133[0]: board init: gpio is 110400
[   16.018273] ivtv:  Start initialization, version 1.4.0
[   16.044001] ACPI: WMI: Mapper loaded
[   16.133508] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   16.133517] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   16.133524] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[   16.133531] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.133537] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   16.133544] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133550] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133556] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133563] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133569] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133575] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133582] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133588] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133595] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133601] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.133607] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.154577] saa7133[0]: registered device video0 [v4l2]
[   16.154609] saa7133[0]: registered device vbi0
[   16.162069] ivtv0: Initializing card #0
[   16.162074] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   16.163610] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   16.163615] ivtv 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   16.163622] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   16.216218] tveeprom 1-0050: Hauppauge model 26032, rev C199, serial# 7774094
[   16.216221] tveeprom 1-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   16.216224] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   16.216226] tveeprom 1-0050: audio processor is CX25841 (idx 35)
[   16.216228] tveeprom 1-0050: decoder processor is CX25841 (idx 28)
[   16.216230] tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
[   16.216233] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   16.216235] ivtv0: Reopen i2c bus for IR-blaster support
[   16.216340] em28xx v4l2 driver version 0.1.0 loaded
[   16.216368] em28xx new video device (2040:6513): interface 0, class 255
[   16.216373] em28xx Doesn't have usb audio class
[   16.216374] em28xx #0: Alternate settings: 8
[   16.216376] em28xx #0: Alternate setting 0, max size= 0
[   16.216378] em28xx #0: Alternate setting 1, max size= 0
[   16.216380] em28xx #0: Alternate setting 2, max size= 1448
[   16.216382] em28xx #0: Alternate setting 3, max size= 2048
[   16.216384] em28xx #0: Alternate setting 4, max size= 2304
[   16.216386] em28xx #0: Alternate setting 5, max size= 2580
[   16.216387] em28xx #0: Alternate setting 6, max size= 2892
[   16.216389] em28xx #0: Alternate setting 7, max size= 3072
[   16.217044] em28xx #0: chip ID is em2882/em2883
[   16.250668] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.371248] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   16.405633] tuner' 2-0061: chip found @ 0xc2 (em28xx #0)
[   16.442008] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 13 65 d0 12 5c 03 82 1e 6a 18
[   16.442017] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00
[   16.442024] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00
[   16.442031] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 01 01 00 00 00 00
[   16.442037] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.442043] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.442050] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00
[   16.442056] em28xx #0: i2c eeprom 70: 32 00 37 00 38 00 37 00 34 00 34 00 39 00 38 00
[   16.442062] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00
[   16.442069] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 38 00 30 00 00 00
[   16.442075] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
[   16.442082] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 c2 7c
[   16.442088] em28xx #0: i2c eeprom c0: 14 f0 74 02 01 00 01 79 54 00 00 00 00 00 00 00
[   16.442094] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
[   16.442102] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 c2 7c
[   16.442108] em28xx #0: i2c eeprom f0: 14 f0 74 02 01 00 01 79 54 00 00 00 00 00 00 00
[   16.442116] EEPROM ID= 0x9567eb1a, hash = 0x39b323dd
[   16.442118] Vendor/Product ID= 2040:6513
[   16.442120] AC97 audio (5 sample rates)
[   16.442121] 500mA max power
[   16.442122] Table at 0x24, strings=0x1e82, 0x186a, 0x0000
[   16.470414] tveeprom 2-0050: Hauppauge model 65201, rev A1C0, serial# 1342658
[   16.470418] tveeprom 2-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[   16.470422] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[   16.470424] tveeprom 2-0050: audio processor is None (idx 0)
[   16.470426] tveeprom 2-0050: has radio
[   16.529033] cx25840 1-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[   16.541181] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   16.541198] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   16.688006] xc2028 2-0061: creating new instance
[   16.688010] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   16.688021] firmware: requesting xc3028-v27.fw
[   16.691065] tuner-simple 1-0061: creating new instance
[   16.691069] tuner-simple 1-0061: type set to 50 (TCL 2002N)
[   16.692392] ivtv0: Registered device video1 for encoder MPG (4096 kB)
[   16.692441] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   16.692473] ivtv0: Registered device vbi1 for encoder VBI (1024 kB)
[   16.692505] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   16.692508] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   16.692577] ivtv1: Initializing card #1
[   16.692580] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   16.693179] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   16.693189] ivtv 0000:01:0b.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   16.693197] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   16.705395] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   16.705401] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   16.705419] HDA Intel 0000:00:07.0: setting latency timer to 64
[   16.747907] tveeprom 3-0050: Hauppauge model 26552, rev F068, serial# 8962639
[   16.747911] tveeprom 3-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   16.747913] tveeprom 3-0050: TV standards NTSC(M) (eeprom 0x08)
[   16.747915] tveeprom 3-0050: audio processor is CX25843 (idx 37)
[   16.747917] tveeprom 3-0050: decoder processor is CX25843 (idx 30)
[   16.747919] tveeprom 3-0050: has radio
[   16.747922] ivtv1: Autodetected Hauppauge WinTV PVR-150
[   16.750775] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   16.753132] saa7134 ALSA driver for DMA sound loaded
[   16.753166] saa7133[0]/alsa: saa7133[0] at 0xfdeff000 irq 17 registered as card -2
[   16.781472] cx25840 3-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   16.825764] tuner 3-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   16.856990] tda9887 3-0043: creating new instance
[   16.856994] tda9887 3-0043: tda988[5/6/7] found
[   16.858298] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   16.858319] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   16.860556] nxt200x: NXT2004 Detected
[   16.866989] tuner-simple 3-0061: creating new instance
[   16.866992] tuner-simple 3-0061: type set to 47 (LG NTSC (TAPE series))
[   16.883796] firmware: requesting v4l-cx25840.fw
[   16.919472] DVB: registering new adapter (saa7133[0])
[   16.919476] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   16.928019] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   16.928023] firmware: requesting dvb-fe-nxt2004.fw
[   17.051121] xc2028 2-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   17.055382] nxt2004: Waiting for firmware upload(2)...
[   17.109514] xc2028 2-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
[   18.043426] xc2028 2-0061: Loading firmware for type=MTS (4), id 000000000000b700.
[   18.058799] xc2028 2-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.
[   18.334057] tvp5150 2-005c: tvp5150am1 detected.
[   18.482812] em28xx #0: V4L2 device registered as /dev/video2 and /dev/vbi2
[   18.482816] em28xx #0: Found Hauppauge WinTV HVR 950
[   18.482843] usbcore: registered new interface driver em28xx
[   18.502510] em28xx-audio.c: probing for em28x1 non standard usbaudio
[   18.502514] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[   18.502933] Em28xx: Initialized (Em28xx Audio Extension) extension
[   18.600531] nxt2004: Firmware upload complete
[   18.640366] xc2028 2-0061: attaching existing instance
[   18.640369] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   18.640371] em28xx #0/2: xc3028 attached
[   18.640373] DVB: registering new adapter (em28xx #0)
[   18.640376] DVB: registering frontend 1 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   18.640687] Successfully loaded em28xx-dvb
[   18.640689] Em28xx: Initialized (Em28xx dvb Extension) extension
[   20.511850] cx25840 3-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.581712] ivtv1: Registered device video3 for encoder MPG (4096 kB)
[   20.581753] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   20.581795] ivtv1: Registered device vbi3 for encoder VBI (1024 kB)
[   20.581855] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   20.581899] ivtv1: Registered device radio1 for encoder radio
[   20.581902] ivtv1: Initialized card #1: Hauppauge WinTV PVR-150
[   20.581932] ivtv:  End initialization
[   20.581989] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.665493] Linux agpgart interface v0.103
[   20.766836] nvidia: module license 'NVIDIA' taints kernel.
[   21.020068] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
[   21.020073] nvidia 0000:02:00.0: PCI INT A -> Link[AIGP] -> GSI 20 (level, low) -> IRQ 20
[   21.020080] nvidia 0000:02:00.0: setting latency timer to 64
[   21.020231] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
[   21.043402] cx23885 driver version 0.0.1 loaded
[   21.043454] cx23885 0000:05:00.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
[   21.043521] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   21.146003] cx23885[0]: i2c bus 0 registered
[   21.150280] tuner' 5-0043: chip found @ 0x86 (cx23885[0])
[   21.150337] tda9887 5-0043: creating new instance
[   21.150339] tda9887 5-0043: tda988[5/6/7] found
[   21.153622] cx23885[0]: i2c bus 1 registered
[   21.154612] cx25840' 6-0044: cx25  0-21 found @ 0x88 (cx23885[0])
[   21.155060] cx23885[0]: i2c bus 2 registered
[   21.181621] tveeprom 4-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[   21.181624] cx23885[0]: warning: unknown hauppauge model #0
[   21.181626] cx23885[0]: hauppauge eeprom: model=0
[   21.181628] cx23885[0]: cx23885 based dvb card
[   21.259776] MT2131: successfully identified at address 0x61
[   21.259780] DVB: registering new adapter (cx23885[0])
[   21.259783] DVB: registering frontend 2 (Samsung S5H1409 QAM/8VSB Frontend)...
[   21.260163] cx23885_dev_checkrevision() Hardware revision = 0xc0
[   21.260170] cx23885[0]/0: found at 0000:05:00.0, rev: 3, irq: 16, latency: 0, mmio: 0xfd400000
[   21.260176] cx23885 0000:05:00.0: setting latency timer to 64
[   22.151150] end_request: I/O error, dev sr0, sector 15944832
[   22.151156] Buffer I/O error on device sr0, logical block 1993104
[   22.186273] end_request: I/O error, dev sr0, sector 15944832
[   22.186275] Buffer I/O error on device sr0, logical block 1993104
[   22.365117] end_request: I/O error, dev sr0, sector 15944968
[   22.365120] Buffer I/O error on device sr0, logical block 1993121
[   22.389307] end_request: I/O error, dev sr0, sector 15944968
[   22.389310] Buffer I/O error on device sr0, logical block 1993121
[   22.876164] lp: driver loaded but no devices found
[   23.026349] Adding 4000144k swap on /dev/sdb1.  Priority:-1 extents:1 across:4000144k
[   23.950895] kjournald starting.  Commit interval 5 seconds
[   23.951361] EXT3 FS on sdb5, internal journal
[   23.951365] EXT3-fs: mounted filesystem with ordered data mode.
[   24.132848] type=1505 audit(1234145831.438:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5529
[   24.286915] type=1505 audit(1234145831.593:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5534
[   24.287078] type=1505 audit(1234145831.593:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5534
[   24.344968] type=1505 audit(1234145831.650:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=5538
[   24.482868] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.989522] RPC: Registered udp transport module.
[   24.989525] RPC: Registered tcp transport module.
[   25.965575] powernow-k8: Found 1 AMD Phenom(tm) 9600 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[   25.965595] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   25.965616] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   25.965638] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   25.965657] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   26.635221] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   26.775794] NET: Registered protocol family 10
[   26.776223] lo: Disabled Privacy Extensions
[   28.641195] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   28.641201] apm: disabled - APM is not SMP safe.
[   28.862795] ppdev: user-space parallel port driver
[   30.903290] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   30.991036] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   31.000356] NFSD: starting 90-second grace period
[   32.860590] tvp5150 2-005c: tvp5150am1 detected.
[   33.620017] firmware: requesting v4l-cx2341x-enc.fw
[   33.656205] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   33.856143] ivtv0: Encoder revision: 0x02060039
[   33.872657] firmware: requesting v4l-cx25840.fw
[   37.285806] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   38.180019] firmware: requesting v4l-cx2341x-enc.fw
[   38.201495] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   38.400136] ivtv1: Encoder revision: 0x02060039
[   41.254434] Bluetooth: Core ver 2.13
[   41.254611] NET: Registered protocol family 31
[   41.254614] Bluetooth: HCI device and connection manager initialized
[   41.254618] Bluetooth: HCI socket layer initialized
[   41.271428] Bluetooth: L2CAP ver 2.11
[   41.271433] Bluetooth: L2CAP socket layer initialized
[   41.324135] Bluetooth: SCO (Voice Link) ver 0.6
[   41.324141] Bluetooth: SCO socket layer initialized
[   41.371297] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   41.371303] Bluetooth: BNEP filters: protocol multicast
[   41.425336] Bluetooth: RFCOMM socket layer initialized
[   41.425350] Bluetooth: RFCOMM TTY layer initialized
[   41.425352] Bluetooth: RFCOMM ver 1.10
[   41.464405] Bridge firewalling registered
[   42.565342] tvp5150 2-005c: tvp5150am1 detected.
[   42.920464] xc2028 2-0061: Loading firmware for type=D2633 DTV6 ATSC (10030), id 0000000000000000.
[   44.384412] lirc_dev: IR Remote Control driver registered, major 61 
[   44.491604] bttv: driver version 0.9.17 loaded
[   44.491611] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   44.617424] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   44.641424] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
[   44.641448] lirc_dev: lirc_register_plugin: sample_rate: 10
[   45.894507] NET: Registered protocol family 17
[   59.608521] UDF-fs: Partition marked readonly; forcing readonly mount
[   59.634301] UDF-fs INFO UDF: Mounting volume 'EAGLE_EYE_D1_AC', timestamp 2008/10/21 22:02 (1e20)
[  971.020170] forcedeth 0000:00:0a.0: PCI INT A disabled
[  979.759855] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[  979.759878] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[  979.759883] forcedeth 0000:00:0a.0: setting latency timer to 64
[  979.826088] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:a1:21:22
[  979.826095] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[ 8130.890044] forcedeth 0000:00:0a.0: PCI INT A disabled
[ 8139.229388] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[ 8139.229409] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[ 8139.229414] forcedeth 0000:00:0a.0: setting latency timer to 64
[ 8139.294871] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:a1:21:22
[ 8139.294877] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[ 8521.576724] UDF-fs: Partition marked readonly; forcing readonly mount
[ 8521.602965] UDF-fs INFO UDF: Mounting volume 'EAGLE_EYE_D1_AC', timestamp 2008/10/21 22:02 (1e20)

```

---

### Post by kilowhisky on 2009-02-09
/var/log/messages
```

Feb  8 18:17:38 knome-mythtv pulseaudio[8134]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb  8 18:17:38 knome-mythtv pulseaudio[8136]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  8 18:17:38 knome-mythtv pulseaudio[8136]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  8 18:17:39 knome-mythtv pulseaudio[8136]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Feb  8 18:17:39 knome-mythtv pulseaudio[8136]: alsa-util.c: Cannot find fallback mixer control "Mic".
Feb  8 18:17:46 knome-mythtv kernel: [   59.608521] UDF-fs: Partition marked readonly; forcing readonly mount
Feb  8 18:17:46 knome-mythtv kernel: [   59.634301] UDF-fs INFO UDF: Mounting volume 'EAGLE_EYE_D1_AC', timestamp 2008/10/21 22:02 (1e20)
Feb  8 18:32:58 knome-mythtv kernel: [  971.020170] forcedeth 0000:00:0a.0: PCI INT A disabled
Feb  8 18:33:07 knome-mythtv kernel: [  979.759855] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Feb  8 18:33:07 knome-mythtv kernel: [  979.759878] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
Feb  8 18:33:07 knome-mythtv kernel: [  979.826088] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:a1:21:22
Feb  8 18:33:07 knome-mythtv kernel: [  979.826095] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
Feb  8 18:57:13 knome-mythtv -- MARK --
Feb  8 19:17:13 knome-mythtv -- MARK --
Feb  8 19:37:13 knome-mythtv -- MARK --
Feb  8 19:57:13 knome-mythtv -- MARK --
Feb  8 20:17:13 knome-mythtv -- MARK --
Feb  8 20:32:18 knome-mythtv kernel: [ 8130.890044] forcedeth 0000:00:0a.0: PCI INT A disabled
Feb  8 20:32:26 knome-mythtv kernel: [ 8139.229388] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Feb  8 20:32:26 knome-mythtv kernel: [ 8139.229409] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
Feb  8 20:32:26 knome-mythtv kernel: [ 8139.294871] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:a1:21:22
Feb  8 20:32:26 knome-mythtv kernel: [ 8139.294877] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
Feb  8 20:38:48 knome-mythtv kernel: [ 8521.576724] UDF-fs: Partition marked readonly; forcing readonly mount
Feb  8 20:38:48 knome-mythtv kernel: [ 8521.602965] UDF-fs INFO UDF: Mounting volume 'EAGLE_EYE_D1_AC', timestamp 2008/10/21 22:02 (1e20)

```


var/log/syslog
```
8 18:17:13 knome-mythtv kernel: [   25.965616] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
Feb  8 18:17:13 knome-mythtv kernel: [   25.965638] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
Feb  8 18:17:13 knome-mythtv kernel: [   25.965657] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
Feb  8 18:17:13 knome-mythtv kernel: [   26.635221] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Feb  8 18:17:13 knome-mythtv avahi-daemon[6279]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Feb  8 18:17:13 knome-mythtv avahi-daemon[6279]: Successfully dropped root privileges.
Feb  8 18:17:13 knome-mythtv avahi-daemon[6279]: avahi-daemon 0.6.23 starting up.
Feb  8 18:17:13 knome-mythtv avahi-daemon[6279]: Successfully called chroot().
Feb  8 18:17:13 knome-mythtv avahi-daemon[6279]: Successfully dropped remaining capabilities.
Feb  8 18:17:13 knome-mythtv avahi-daemon[6279]: No service file found in /etc/avahi/services.
Feb  8 18:17:13 knome-mythtv avahi-daemon[6279]: Network interface enumeration completed.
Feb  8 18:17:13 knome-mythtv avahi-daemon[6279]: Registering HINFO record with values 'I686'/'LINUX'.
Feb  8 18:17:13 knome-mythtv avahi-daemon[6279]: Server startup complete. Host name is knome-mythtv.local. Local service cookie is 577881226.
Feb  8 18:17:14 knome-mythtv kernel: [   26.775794] NET: Registered protocol family 10
Feb  8 18:17:14 knome-mythtv kernel: [   26.776223] lo: Disabled Privacy Extensions
Feb  8 18:17:14 knome-mythtv mysqld_safe[6411]: started
Feb  8 18:17:14 knome-mythtv mysqld[6414]: 090208 18:17:14 [Warning] option 'net_buffer_length': unsigned value 8388608 adjusted to 1048576
Feb  8 18:17:15 knome-mythtv mysqld[6414]: 090208 18:17:15  InnoDB: Started; log sequence number 0 234942
Feb  8 18:17:15 knome-mythtv mysqld[6414]: 090208 18:17:15 [Note] /usr/sbin/mysqld: ready for connections.
Feb  8 18:17:15 knome-mythtv mysqld[6414]: Version: '5.0.67-0ubuntu6'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Feb  8 18:17:15 knome-mythtv /etc/mysql/debian-start[6453]: Upgrading MySQL tables if necessary.
Feb  8 18:17:15 knome-mythtv kernel: [   28.641195] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Feb  8 18:17:15 knome-mythtv kernel: [   28.641201] apm: disabled - APM is not SMP safe.
Feb  8 18:17:15 knome-mythtv /etc/mysql/debian-start[6458]: Looking for 'mysql' in: /usr/bin/mysql
Feb  8 18:17:15 knome-mythtv /etc/mysql/debian-start[6458]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Feb  8 18:17:15 knome-mythtv /etc/mysql/debian-start[6458]: This installation of MySQL is already upgraded to 5.0.67, use --force if you still need to run mysql_upgrade
Feb  8 18:17:15 knome-mythtv /etc/mysql/debian-start[6484]: Checking for insecure root accounts.
Feb  8 18:17:15 knome-mythtv /etc/mysql/debian-start[6491]: WARNING: mysql.user contains 3 root accounts without password!
Feb  8 18:17:15 knome-mythtv /etc/mysql/debian-start[6492]: Triggering myisam-recover for all MyISAM tables
Feb  8 18:17:16 knome-mythtv kernel: [   28.862795] ppdev: user-space parallel port driver
Feb  8 18:17:18 knome-mythtv kernel: [   30.903290] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Feb  8 18:17:18 knome-mythtv kernel: [   30.991036] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Feb  8 18:17:18 knome-mythtv kernel: [   31.000356] NFSD: starting 90-second grace period
Feb  8 18:17:19 knome-mythtv ntpd[7199]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:54:48 UTC 2009 (1)
Feb  8 18:17:19 knome-mythtv ntpd[7201]: precision = 1.000 usec
Feb  8 18:17:19 knome-mythtv ntpd[7201]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Feb  8 18:17:19 knome-mythtv ntpd[7201]: Listening on interface #1 wildcard, ::#123 Disabled
Feb  8 18:17:19 knome-mythtv ntpd[7201]: Listening on interface #2 lo, ::1#123 Enabled
Feb  8 18:17:19 knome-mythtv ntpd[7201]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Feb  8 18:17:19 knome-mythtv ntpd[7201]: kernel time sync status 0040
Feb  8 18:17:19 knome-mythtv ntpd[7201]: frequency initialized -41.208 PPM from /var/lib/ntp/ntp.drift
Feb  8 18:17:20 knome-mythtv acpid: client connected from 7319[111:122] 
Feb  8 18:17:20 knome-mythtv kernel: [   32.860590] tvp5150 2-005c: tvp5150am1 detected.
Feb  8 18:17:20 knome-mythtv kernel: [   33.620017] firmware: requesting v4l-cx2341x-enc.fw
Feb  8 18:17:20 knome-mythtv kernel: [   33.656205] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Feb  8 18:17:21 knome-mythtv kernel: [   33.856143] ivtv0: Encoder revision: 0x02060039
Feb  8 18:17:21 knome-mythtv kernel: [   33.872657] firmware: requesting v4l-cx25840.fw
Feb  8 18:17:21 knome-mythtv ntpd_initres[7224]: host name not found: ntp.ubuntu.com
Feb  8 18:17:21 knome-mythtv ntpd_initres[7224]: couldn't resolve `ntp.ubuntu.com', giving up on it
Feb  8 18:17:24 knome-mythtv kernel: [   37.285806] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Feb  8 18:17:25 knome-mythtv kernel: [   38.180019] firmware: requesting v4l-cx2341x-enc.fw
Feb  8 18:17:25 knome-mythtv kernel: [   38.201495] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Feb  8 18:17:25 knome-mythtv kernel: [   38.400136] ivtv1: Encoder revision: 0x02060039
Feb  8 18:17:28 knome-mythtv bluetoothd[7476]: Bluetooth daemon
Feb  8 18:17:28 knome-mythtv kernel: [   41.254434] Bluetooth: Core ver 2.13
Feb  8 18:17:28 knome-mythtv kernel: [   41.254611] NET: Registered protocol family 31
Feb  8 18:17:28 knome-mythtv kernel: [   41.254614] Bluetooth: HCI device and connection manager initialized
Feb  8 18:17:28 knome-mythtv kernel: [   41.254618] Bluetooth: HCI socket layer initialized
Feb  8 18:17:28 knome-mythtv bluetoothd[7476]: Starting SDP server
Feb  8 18:17:28 knome-mythtv kernel: [   41.271428] Bluetooth: L2CAP ver 2.11
Feb  8 18:17:28 knome-mythtv kernel: [   41.271433] Bluetooth: L2CAP socket layer initialized
Feb  8 18:17:28 knome-mythtv kernel: [   41.324135] Bluetooth: SCO (Voice Link) ver 0.6
Feb  8 18:17:28 knome-mythtv kernel: [   41.324141] Bluetooth: SCO socket layer initialized
Feb  8 18:17:28 knome-mythtv bluetoothd[7476]: Starting experimental netlink support
Feb  8 18:17:28 knome-mythtv bluetoothd[7476]: Failed to find Bluetooth netlink family
Feb  8 18:17:28 knome-mythtv bluetoothd[7476]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Feb  8 18:17:28 knome-mythtv kernel: [   41.371297] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb  8 18:17:28 knome-mythtv kernel: [   41.371303] Bluetooth: BNEP filters: protocol multicast
Feb  8 18:17:28 knome-mythtv kernel: [   41.425336] Bluetooth: RFCOMM socket layer initialized
Feb  8 18:17:28 knome-mythtv kernel: [   41.425350] Bluetooth: RFCOMM TTY layer initialized
Feb  8 18:17:28 knome-mythtv kernel: [   41.425352] Bluetooth: RFCOMM ver 1.10
Feb  8 18:17:28 knome-mythtv kernel: [   41.464405] Bridge firewalling registered
Feb  8 18:17:28 knome-mythtv bluetoothd[7476]: bridge pan0 created
Feb  8 18:17:28 knome-mythtv NetworkManager: <info>  starting... 
Feb  8 18:17:28 knome-mythtv NetworkManager: <info>  eth0: driver is 'forcedeth'. 
Feb  8 18:17:28 knome-mythtv NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Feb  8 18:17:28 knome-mythtv NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22 
Feb  8 18:17:28 knome-mythtv NetworkManager: <info>  Trying to start the supplicant... 
Feb  8 18:17:28 knome-mythtv NetworkManager: <info>  Trying to start the system settings daemon... 
Feb  8 18:17:29 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: init!
Feb  8 18:17:29 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Feb  8 18:17:29 knome-mythtv nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Feb  8 18:17:29 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22, iface: eth0): not well known
Feb  8 18:17:29 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: end _init.
Feb  8 18:17:29 knome-mythtv nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb  8 18:17:29 knome-mythtv nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb  8 18:17:29 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: (159781096) ... get_connections.
Feb  8 18:17:29 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: (159781096) ... get_connections (managed=false): return empty list.
Feb  8 18:17:29 knome-mythtv nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Feb  8 18:17:29 knome-mythtv kernel: [   42.565342] tvp5150 2-005c: tvp5150am1 detected.
Feb  8 18:17:30 knome-mythtv kernel: [   42.920464] xc2028 2-0061: Loading firmware for type=D2633 DTV6 ATSC (10030), id 0000000000000000.
Feb  8 18:17:30 knome-mythtv gdm[7610]: WARNING: Didn't understand `' (expected true or false) 
Feb  8 18:17:30 knome-mythtv acpid: client connected from 7623[0:0] 
Feb  8 18:17:31 knome-mythtv kernel: [   44.384412] lirc_dev: IR Remote Control driver registered, major 61 
Feb  8 18:17:31 knome-mythtv kernel: [   44.491604] bttv: driver version 0.9.17 loaded
Feb  8 18:17:31 knome-mythtv kernel: [   44.491611] bttv: using 8 buffers with 2080k (520 pages) each for capture
Feb  8 18:17:31 knome-mythtv acpid: client connected from 7623[0:0] 
Feb  8 18:17:31 knome-mythtv kernel: [   44.617424] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
Feb  8 18:17:31 knome-mythtv kernel: [   44.641424] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
Feb  8 18:17:31 knome-mythtv kernel: [   44.641448] lirc_dev: lirc_register_plugin: sample_rate: 10
Feb  8 18:17:32 knome-mythtv lircd-0.8.4a[7766]: lircd(default) ready
Feb  8 18:17:32 knome-mythtv anacron[7767]: Anacron 2.3 started on 2009-02-08
Feb  8 18:17:32 knome-mythtv anacron[7767]: Normal exit (0 jobs run)
Feb  8 18:17:32 knome-mythtv /usr/sbin/cron[7812]: (CRON) INFO (pidfile fd = 3)
Feb  8 18:17:32 knome-mythtv /usr/sbin/cron[7813]: (CRON) STARTUP (fork ok)
Feb  8 18:17:32 knome-mythtv /usr/sbin/cron[7813]: (CRON) INFO (Running @reboot jobs)
Feb  8 18:17:32 knome-mythtv NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Feb  8 18:17:32 knome-mythtv NetworkManager: <info>  (eth0): bringing up device. 
Feb  8 18:17:32 knome-mythtv NetworkManager: <info>  (eth0): preparing device. 
Feb  8 18:17:32 knome-mythtv NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Feb  8 18:17:32 knome-mythtv NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Feb  8 18:17:32 knome-mythtv NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Feb  8 18:17:33 knome-mythtv nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  dhclient started with pid 7859 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Feb  8 18:17:33 knome-mythtv dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  8 18:17:33 knome-mythtv dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  8 18:17:33 knome-mythtv dhclient: All rights reserved.
Feb  8 18:17:33 knome-mythtv dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  8 18:17:33 knome-mythtv dhclient: 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Feb  8 18:17:33 knome-mythtv kernel: [   45.894507] NET: Registered protocol family 17
Feb  8 18:17:33 knome-mythtv dhclient: Listening on LPF/eth0/00:22:15:a1:21:22
Feb  8 18:17:33 knome-mythtv dhclient: Sending on   LPF/eth0/00:22:15:a1:21:22
Feb  8 18:17:33 knome-mythtv dhclient: Sending on   Socket/fallback
Feb  8 18:17:33 knome-mythtv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Feb  8 18:17:33 knome-mythtv dhclient: DHCPOFFER of 10.0.1.5 from 10.0.1.1
Feb  8 18:17:33 knome-mythtv dhclient: DHCPREQUEST of 10.0.1.5 on eth0 to 255.255.255.255 port 67
Feb  8 18:17:33 knome-mythtv dhclient: DHCPACK of 10.0.1.5 from 10.0.1.1
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>    address 10.0.1.5 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>    prefix 24 (255.255.255.0) 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>    gateway 10.0.1.1 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>    nameserver '10.0.1.1' 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>    domain name 'sd.cox.net' 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Feb  8 18:17:33 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Feb  8 18:17:33 knome-mythtv avahi-daemon[6279]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.1.5.
Feb  8 18:17:33 knome-mythtv dhclient: bound to 10.0.1.5 -- renewal in 5899 seconds.
Feb  8 18:17:33 knome-mythtv avahi-daemon[6279]: New relevant interface eth0.IPv4 for mDNS.
Feb  8 18:17:33 knome-mythtv avahi-daemon[6279]: Registering new address record for 10.0.1.5 on eth0.IPv4.
Feb  8 18:17:34 knome-mythtv NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Feb  8 18:17:34 knome-mythtv NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Feb  8 18:17:34 knome-mythtv NetworkManager: <info>  Activation (eth0) successful, device activated. 
Feb  8 18:17:34 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb  8 18:17:34 knome-mythtv avahi-daemon[6279]: Registering new address record for fe80::222:15ff:fea1:2122 on eth0.*.
Feb  8 18:17:34 knome-mythtv ntpd[7201]: ntpd exiting on signal 15
Feb  8 18:17:37 knome-mythtv avahi-daemon[6279]: Registering new address record for 2002:4408:e361:0:222:15ff:fea1:2122 on eth0.*.
Feb  8 18:17:37 knome-mythtv avahi-daemon[6279]: Withdrawing address record for fe80::222:15ff:fea1:2122 on eth0.
Feb  8 18:17:37 knome-mythtv ntpdate[7991]: adjust time server 91.189.94.4 offset -0.002441 sec
Feb  8 18:17:37 knome-mythtv ntpd[8067]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:54:48 UTC 2009 (1)
Feb  8 18:17:37 knome-mythtv ntpd[8068]: precision = 1.000 usec
Feb  8 18:17:37 knome-mythtv ntpd[8068]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Feb  8 18:17:37 knome-mythtv ntpd[8068]: Listening on interface #1 wildcard, ::#123 Disabled
Feb  8 18:17:37 knome-mythtv ntpd[8068]: Listening on interface #2 lo, ::1#123 Enabled
Feb  8 18:17:37 knome-mythtv ntpd[8068]: Listening on interface #3 eth0, 2002:4408:e361:0:222:15ff:fea1:2122#123 Enabled
Feb  8 18:17:37 knome-mythtv ntpd[8068]: Listening on interface #4 eth0, fe80::222:15ff:fea1:2122#123 Enabled
Feb  8 18:17:37 knome-mythtv ntpd[8068]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Feb  8 18:17:37 knome-mythtv ntpd[8068]: Listening on interface #6 eth0, 10.0.1.5#123 Enabled
Feb  8 18:17:37 knome-mythtv ntpd[8068]: kernel time sync status 0040
Feb  8 18:17:37 knome-mythtv ntpd[8068]: frequency initialized -41.208 PPM from /var/lib/ntp/ntp.drift
Feb  8 18:17:38 knome-mythtv pulseaudio[8134]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb  8 18:17:38 knome-mythtv pulseaudio[8136]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  8 18:17:38 knome-mythtv pulseaudio[8136]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  8 18:17:39 knome-mythtv pulseaudio[8136]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Feb  8 18:17:39 knome-mythtv pulseaudio[8136]: alsa-util.c: Cannot find fallback mixer control "Mic".
Feb  8 18:17:46 knome-mythtv kernel: [   59.608521] UDF-fs: Partition marked readonly; forcing readonly mount
Feb  8 18:17:46 knome-mythtv kernel: [   59.634301] UDF-fs INFO UDF: Mounting volume 'EAGLE_EYE_D1_AC', timestamp 2008/10/21 22:02 (1e20)
Feb  8 18:17:53 knome-mythtv gnome-session[8037]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Feb  8 18:17:53 knome-mythtv pulseaudio[8136]: module-x11-xsmp.c: X11 session manager not running.
Feb  8 18:17:53 knome-mythtv pulseaudio[8136]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb  8 18:18:46 knome-mythtv lircd-0.8.4a[7766]: accepted new client on /dev/lircd
Feb  8 18:32:58 knome-mythtv avahi-daemon[6279]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb  8 18:32:58 knome-mythtv avahi-daemon[6279]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.1.5.
Feb  8 18:32:58 knome-mythtv dhclient: receive_packet failed on eth0: Network is down
Feb  8 18:32:58 knome-mythtv avahi-daemon[6279]: Withdrawing address record for 2002:4408:e361:0:222:15ff:fea1:2122 on eth0.
Feb  8 18:32:58 knome-mythtv kernel: [  971.020170] forcedeth 0000:00:0a.0: PCI INT A disabled
Feb  8 18:32:58 knome-mythtv avahi-daemon[6279]: Withdrawing address record for 10.0.1.5 on eth0.
Feb  8 18:32:58 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22)
Feb  8 18:32:58 knome-mythtv NetworkManager: <info>  (eth0): now unmanaged 
Feb  8 18:32:58 knome-mythtv NetworkManager: <info>  (eth0): device state change: 8 -> 1 
Feb  8 18:32:58 knome-mythtv NetworkManager: <info>  (eth0): deactivating device (reason: 36). 
Feb  8 18:32:58 knome-mythtv NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 7859 
Feb  8 18:32:58 knome-mythtv NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Feb  8 18:32:58 knome-mythtv NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Feb  8 18:32:58 knome-mythtv NetworkManager: <info>  (eth0): cleaning up... 
Feb  8 18:32:58 knome-mythtv nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist  
Feb  8 18:33:07 knome-mythtv kernel: [  979.759855] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Feb  8 18:33:07 knome-mythtv kernel: [  979.759878] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
Feb  8 18:33:07 knome-mythtv kernel: [  979.759883] forcedeth 0000:00:0a.0: setting latency timer to 64
Feb  8 18:33:07 knome-mythtv kernel: [  979.826088] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:a1:21:22
Feb  8 18:33:07 knome-mythtv kernel: [  979.826095] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
Feb  8 18:33:07 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22, iface: eth0): not well known
Feb  8 18:33:07 knome-mythtv NetworkManager: <info>  eth0: driver is 'forcedeth'. 
Feb  8 18:33:07 knome-mythtv NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Feb  8 18:33:07 knome-mythtv NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22 
Feb  8 18:33:11 knome-mythtv nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  (eth0): bringing up device. 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  (eth0): preparing device. 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  dhclient started with pid 8655 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Feb  8 18:33:11 knome-mythtv dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  8 18:33:11 knome-mythtv dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  8 18:33:11 knome-mythtv dhclient: All rights reserved.
Feb  8 18:33:11 knome-mythtv dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  8 18:33:11 knome-mythtv dhclient: 
Feb  8 18:33:11 knome-mythtv NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Feb  8 18:33:11 knome-mythtv dhclient: Listening on LPF/eth0/00:22:15:a1:21:22
Feb  8 18:33:11 knome-mythtv dhclient: Sending on   LPF/eth0/00:22:15:a1:21:22
Feb  8 18:33:11 knome-mythtv dhclient: Sending on   Socket/fallback
Feb  8 18:33:12 knome-mythtv avahi-daemon[6279]: Registering new address record for fe80::222:15ff:fea1:2122 on eth0.*.
Feb  8 18:33:14 knome-mythtv avahi-daemon[6279]: Registering new address record for 2002:4408:e361:0:222:15ff:fea1:2122 on eth0.*.
Feb  8 18:33:14 knome-mythtv avahi-daemon[6279]: Withdrawing address record for fe80::222:15ff:fea1:2122 on eth0.
Feb  8 18:33:15 knome-mythtv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Feb  8 18:33:15 knome-mythtv dhclient: DHCPOFFER of 10.0.1.5 from 10.0.1.1
Feb  8 18:33:15 knome-mythtv dhclient: DHCPREQUEST of 10.0.1.5 on eth0 to 255.255.255.255 port 67
Feb  8 18:33:15 knome-mythtv dhclient: DHCPACK of 10.0.1.5 from 10.0.1.1
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>    address 10.0.1.5 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>    prefix 24 (255.255.255.0) 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>    gateway 10.0.1.1 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>    nameserver '10.0.1.1' 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>    domain name 'sd.cox.net' 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Feb  8 18:33:15 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Feb  8 18:33:15 knome-mythtv avahi-daemon[6279]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.1.5.
Feb  8 18:33:15 knome-mythtv avahi-daemon[6279]: New relevant interface eth0.IPv4 for mDNS.
Feb  8 18:33:15 knome-mythtv avahi-daemon[6279]: Registering new address record for 10.0.1.5 on eth0.IPv4.
Feb  8 18:33:15 knome-mythtv dhclient: bound to 10.0.1.5 -- renewal in 5977 seconds.
Feb  8 18:33:16 knome-mythtv NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Feb  8 18:33:16 knome-mythtv NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Feb  8 18:33:16 knome-mythtv NetworkManager: <info>  Activation (eth0) successful, device activated. 
Feb  8 18:33:16 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb  8 18:33:16 knome-mythtv ntpd[8068]: ntpd exiting on signal 15
Feb  8 18:33:16 knome-mythtv ntpdate[8742]: adjust time server 91.189.94.4 offset 0.002949 sec
Feb  8 18:33:16 knome-mythtv ntpd[8771]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:54:48 UTC 2009 (1)
Feb  8 18:33:16 knome-mythtv ntpd[8772]: precision = 1.000 usec
Feb  8 18:33:16 knome-mythtv ntpd[8772]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Feb  8 18:33:16 knome-mythtv ntpd[8772]: Listening on interface #1 wildcard, ::#123 Disabled
Feb  8 18:33:16 knome-mythtv ntpd[8772]: Listening on interface #2 lo, ::1#123 Enabled
Feb  8 18:33:16 knome-mythtv ntpd[8772]: Listening on interface #3 eth0, 2002:4408:e361:0:222:15ff:fea1:2122#123 Enabled
Feb  8 18:33:16 knome-mythtv ntpd[8772]: Listening on interface #4 eth0, fe80::222:15ff:fea1:2122#123 Enabled
Feb  8 18:33:16 knome-mythtv ntpd[8772]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Feb  8 18:33:16 knome-mythtv ntpd[8772]: Listening on interface #6 eth0, 10.0.1.5#123 Enabled
Feb  8 18:33:16 knome-mythtv ntpd[8772]: kernel time sync status 0040
Feb  8 18:33:16 knome-mythtv ntpd[8772]: frequency initialized -41.208 PPM from /var/lib/ntp/ntp.drift
Feb  8 18:33:26 knome-mythtv acpid: client connected from 7623[0:0] 
Feb  8 18:33:26 knome-mythtv acpid: client connected from 7623[0:0] 
Feb  8 18:37:36 knome-mythtv ntpd[8772]: synchronized to 91.189.94.4, stratum 2
Feb  8 18:37:36 knome-mythtv ntpd[8772]: kernel time sync status change 0001
Feb  8 18:39:01 knome-mythtv /USR/SBIN/CRON[8997]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb  8 18:57:13 knome-mythtv -- MARK --
Feb  8 19:09:01 knome-mythtv /USR/SBIN/CRON[9284]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb  8 19:17:01 knome-mythtv /USR/SBIN/CRON[9474]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  8 19:37:13 knome-mythtv -- MARK --
Feb  8 19:39:01 knome-mythtv /USR/SBIN/CRON[9739]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb  8 19:57:13 knome-mythtv -- MARK --
Feb  8 20:09:01 knome-mythtv /USR/SBIN/CRON[10021]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb  8 20:12:52 knome-mythtv dhclient: DHCPREQUEST of 10.0.1.5 on eth0 to 10.0.1.1 port 67
Feb  8 20:12:52 knome-mythtv dhclient: DHCPACK of 10.0.1.5 from 10.0.1.1
Feb  8 20:12:52 knome-mythtv NetworkManager: <info>  DHCP: device eth0 state changed bound -> renew 
Feb  8 20:12:52 knome-mythtv NetworkManager: <info>    address 10.0.1.5 
Feb  8 20:12:52 knome-mythtv NetworkManager: <info>    prefix 24 (255.255.255.0) 
Feb  8 20:12:52 knome-mythtv NetworkManager: <info>    gateway 10.0.1.1 
Feb  8 20:12:52 knome-mythtv NetworkManager: <info>    nameserver '10.0.1.1' 
Feb  8 20:12:52 knome-mythtv NetworkManager: <info>    domain name 'sd.cox.net' 
Feb  8 20:12:52 knome-mythtv dhclient: bound to 10.0.1.5 -- renewal in 6848 seconds.
Feb  8 20:12:52 knome-mythtv avahi-daemon[6279]: Withdrawing address record for 10.0.1.5 on eth0.
Feb  8 20:12:52 knome-mythtv avahi-daemon[6279]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.1.5.
Feb  8 20:12:52 knome-mythtv avahi-daemon[6279]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb  8 20:12:52 knome-mythtv avahi-daemon[6279]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.1.5.
Feb  8 20:12:52 knome-mythtv avahi-daemon[6279]: New relevant interface eth0.IPv4 for mDNS.
Feb  8 20:12:52 knome-mythtv avahi-daemon[6279]: Registering new address record for 10.0.1.5 on eth0.IPv4.
Feb  8 20:12:53 knome-mythtv NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Feb  8 20:17:01 knome-mythtv /USR/SBIN/CRON[10212]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  8 20:31:30 knome-mythtv lircd-0.8.4a[7766]: removed client
Feb  8 20:32:18 knome-mythtv avahi-daemon[6279]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb  8 20:32:18 knome-mythtv avahi-daemon[6279]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.1.5.
Feb  8 20:32:18 knome-mythtv dhclient: receive_packet failed on eth0: Network is down
Feb  8 20:32:18 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22)
Feb  8 20:32:18 knome-mythtv avahi-daemon[6279]: Withdrawing address record for 2002:4408:e361:0:222:15ff:fea1:2122 on eth0.
Feb  8 20:32:18 knome-mythtv avahi-daemon[6279]: Withdrawing address record for 10.0.1.5 on eth0.
Feb  8 20:32:18 knome-mythtv NetworkManager: <info>  (eth0): now unmanaged 
Feb  8 20:32:18 knome-mythtv NetworkManager: <info>  (eth0): device state change: 8 -> 1 
Feb  8 20:32:18 knome-mythtv NetworkManager: <info>  (eth0): deactivating device (reason: 36). 
Feb  8 20:32:18 knome-mythtv kernel: [ 8130.890044] forcedeth 0000:00:0a.0: PCI INT A disabled
Feb  8 20:32:18 knome-mythtv NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 8655 
Feb  8 20:32:18 knome-mythtv NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Feb  8 20:32:18 knome-mythtv NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Feb  8 20:32:18 knome-mythtv NetworkManager: <info>  (eth0): cleaning up... 
Feb  8 20:32:18 knome-mythtv nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist  
Feb  8 20:32:26 knome-mythtv kernel: [ 8139.229388] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Feb  8 20:32:26 knome-mythtv kernel: [ 8139.229409] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
Feb  8 20:32:26 knome-mythtv kernel: [ 8139.229414] forcedeth 0000:00:0a.0: setting latency timer to 64
Feb  8 20:32:26 knome-mythtv kernel: [ 8139.294871] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:a1:21:22
Feb  8 20:32:26 knome-mythtv kernel: [ 8139.294877] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
Feb  8 20:32:26 knome-mythtv nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22, iface: eth0): not well known
Feb  8 20:32:26 knome-mythtv NetworkManager: <info>  eth0: driver is 'forcedeth'. 
Feb  8 20:32:26 knome-mythtv NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Feb  8 20:32:26 knome-mythtv NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22 
Feb  8 20:32:30 knome-mythtv nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_22_15_a1_21_22
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  (eth0): bringing up device. 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  (eth0): preparing device. 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  dhclient started with pid 10662 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Feb  8 20:32:30 knome-mythtv dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  8 20:32:30 knome-mythtv dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  8 20:32:30 knome-mythtv dhclient: All rights reserved.
Feb  8 20:32:30 knome-mythtv dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  8 20:32:30 knome-mythtv dhclient: 
Feb  8 20:32:30 knome-mythtv NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Feb  8 20:32:30 knome-mythtv dhclient: Listening on LPF/eth0/00:22:15:a1:21:22
Feb  8 20:32:30 knome-mythtv dhclient: Sending on   LPF/eth0/00:22:15:a1:21:22
Feb  8 20:32:30 knome-mythtv dhclient: Sending on   Socket/fallback
Feb  8 20:32:32 knome-mythtv avahi-daemon[6279]: Registering new address record for fe80::222:15ff:fea1:2122 on eth0.*.
Feb  8 20:32:34 knome-mythtv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Feb  8 20:32:34 knome-mythtv dhclient: DHCPOFFER of 10.0.1.5 from 10.0.1.1
Feb  8 20:32:34 knome-mythtv dhclient: DHCPREQUEST of 10.0.1.5 on eth0 to 255.255.255.255 port 67
Feb  8 20:32:34 knome-mythtv dhclient: DHCPACK of 10.0.1.5 from 10.0.1.1
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>    address 10.0.1.5 
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>    prefix 24 (255.255.255.0) 
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>    gateway 10.0.1.1 
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>    nameserver '10.0.1.1' 
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>    domain name 'sd.cox.net' 
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Feb  8 20:32:34 knome-mythtv dhclient: bound to 10.0.1.5 -- renewal in 5437 seconds.
Feb  8 20:32:34 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Feb  8 20:32:34 knome-mythtv avahi-daemon[6279]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.1.5.
Feb  8 20:32:34 knome-mythtv avahi-daemon[6279]: New relevant interface eth0.IPv4 for mDNS.
Feb  8 20:32:34 knome-mythtv avahi-daemon[6279]: Registering new address record for 10.0.1.5 on eth0.IPv4.
Feb  8 20:32:34 knome-mythtv avahi-daemon[6279]: Registering new address record for 2002:4408:e361:0:222:15ff:fea1:2122 on eth0.*.
Feb  8 20:32:34 knome-mythtv avahi-daemon[6279]: Withdrawing address record for fe80::222:15ff:fea1:2122 on eth0.
Feb  8 20:32:35 knome-mythtv NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Feb  8 20:32:35 knome-mythtv NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Feb  8 20:32:35 knome-mythtv NetworkManager: <info>  Activation (eth0) successful, device activated. 
Feb  8 20:32:35 knome-mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb  8 20:32:35 knome-mythtv ntpd[8772]: ntpd exiting on signal 15
Feb  8 20:32:36 knome-mythtv ntpdate[10750]: adjust time server 91.189.94.4 offset -0.012907 sec
Feb  8 20:32:36 knome-mythtv ntpd[10780]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:54:48 UTC 2009 (1)
Feb  8 20:32:36 knome-mythtv ntpd[10781]: precision = 1.000 usec
Feb  8 20:32:36 knome-mythtv ntpd[10781]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Feb  8 20:32:36 knome-mythtv ntpd[10781]: Listening on interface #1 wildcard, ::#123 Disabled
Feb  8 20:32:36 knome-mythtv ntpd[10781]: Listening on interface #2 lo, ::1#123 Enabled
Feb  8 20:32:36 knome-mythtv ntpd[10781]: Listening on interface #3 eth0, 2002:4408:e361:0:222:15ff:fea1:2122#123 Enabled
Feb  8 20:32:36 knome-mythtv ntpd[10781]: Listening on interface #4 eth0, fe80::222:15ff:fea1:2122#123 Enabled
Feb  8 20:32:36 knome-mythtv ntpd[10781]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Feb  8 20:32:36 knome-mythtv ntpd[10781]: Listening on interface #6 eth0, 10.0.1.5#123 Enabled
Feb  8 20:32:36 knome-mythtv ntpd[10781]: kernel time sync status 0040
Feb  8 20:32:36 knome-mythtv ntpd[10781]: frequency initialized -41.267 PPM from /var/lib/ntp/ntp.drift
Feb  8 20:36:55 knome-mythtv ntpd[10781]: synchronized to 91.189.94.4, stratum 2
Feb  8 20:36:55 knome-mythtv ntpd[10781]: kernel time sync status change 0001
Feb  8 20:38:40 knome-mythtv lircd-0.8.4a[7766]: accepted new client on /dev/lircd
Feb  8 20:38:48 knome-mythtv kernel: [ 8521.576724] UDF-fs: Partition marked readonly; forcing readonly mount
Feb  8 20:38:48 knome-mythtv kernel: [ 8521.602965] UDF-fs INFO UDF: Mounting volume 'EAGLE_EYE_D1_AC', timestamp 2008/10/21 22:02 (1e20)
Feb  8 20:39:01 knome-mythtv /USR/SBIN/CRON[11098]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

```


I'm about at wits end. I'm using the computer as a mythtv backend and any time i attempt to stream a show from the machine the network dropps.  


EDIT: as i'm writing this my network connection is now dropping at random times.  
Nothing is visible in the logs that i posted.

---

### Post by kilowhisky on 2009-02-09
lspci

```

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:09.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:0a.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:0b.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 (rev a2)
05:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)

```

---

### Post by kilowhisky on 2009-02-12
I figured out that it had to do with a hauppauge 1250 card that i had installed. 


That is one huge failure of a card.

---

