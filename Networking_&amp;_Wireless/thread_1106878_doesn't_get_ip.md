---
title: "doesn't get ip"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by ahac on 2009-03-26
I have VDSL with dynamic IP and I can't connect to the internet. 
The network manager just says "disconnected" and when I tried "sudo dhclient" I got this:
[http://www.shrani.si/f/L/FU/1jku1qe7/screenshot.png](http://www.shrani.si/f/L/FU/1jku1qe7/screenshot.png)
so I think it doesn't get the ip from dhcp.
:confused:
XP, Vista and PClinuxOS connect without any special settings.

---

### Post by ahac on 2009-03-27
Any ideas? :confused:

---

### Post by coutts99 on 2009-03-27
Can you output ifconfig and dmesg please

---

### Post by Iowan on 2009-03-27
As you mentioned, it didn't seem to get an IP address.  
Also post results of **lshw -C network**... but since dhclient is trying eth0, it is probably recognized.

---

### Post by ahac on 2009-03-29
ifconfig :
```
eth0      Link encap:Ethernet  HWaddr 00:c0:26:c4:02:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:40:33:e2:9b:e2  
          inet6 addr: fe80::240:33ff:fee2:9be2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30080 (30.0 KB)  TX bytes:30080 (30.0 KB)
 
```

dmesg :

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37826000 - 37fef1d9
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP 000F75C0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF30C0, 43E7 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF74C0, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037826000 - 0037fef1d9]          RAMDISK ==> [0037826000 - 0037fef1d9]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262032
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32464 pages, LIFO batch:7
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259728
[    0.000000] Kernel command line: root=UUID=35438d1e-de83-4b81-9589-7432b7072944 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1913.142 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1024868k/1048512k available (2572k kernel code, 22956k reserved, 1160k data, 424k init, 131008k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 3826.28 BogoMIPS (lpj=7652568)
[    0.004043] Security Framework initialized
[    0.004054] SELinux:  Disabled at boot.
[    0.004089] AppArmor: AppArmor initialized
[    0.004100] Mount-cache hash table entries: 512
[    0.004314] Initializing cgroup subsys ns
[    0.004320] Initializing cgroup subsys cpuacct
[    0.004323] Initializing cgroup subsys memory
[    0.004342] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004345] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004363] Checking 'hlt' instruction... OK.
[    0.020348] SMP alternatives: switching to UP code
[    0.026078] Freeing SMP alternatives: 11k freed
[    0.026083] ACPI: Core revision 20080609
[    0.027618] ACPI: Checking initramfs for custom DSDT
[    0.374947] ENABLING IO-APIC IRQs
[    0.375138] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.414828] CPU0: AMD Athlon(tm) XP 2600+ stepping 00
[    0.416026] APIC calibration not consistent with PM Timer: 96ms instead of 100ms
[    0.416026] APIC delta adjusted to PM-Timer: 2079543 (1996467)
[    0.416026] Brought up 1 CPUs
[    0.416026] Total of 1 processors activated (3826.28 BogoMIPS).
[    0.416026] CPU0 attaching sched-domain:
[    0.416026]  domain 0: span 0 level CPU
[    0.416026]   groups: 0
[    0.416026] net_namespace: 840 bytes
[    0.416026] Booting paravirtualized kernel on bare hardware
[    0.416026] Time:  9:13:42  Date: 03/29/09
[    0.416026] NET: Registered protocol family 16
[    0.416026] EISA bus registered
[    0.416026] ACPI: bus type pci registered
[    0.445129] PCI: PCI BIOS revision 2.10 entry at 0xfb4a0, last bus=2
[    0.445132] PCI: Using configuration type 1 for base access
[    0.447352] ACPI: EC: Look up EC in DSDT
[    0.455580] ACPI: Interpreter enabled
[    0.455585] ACPI: (supports S0 S1 S4 S5)
[    0.455603] ACPI: Using IOAPIC for interrupt routing
[    0.468176] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.468269] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e3ffffff]
[    0.468290] pci 0000:00:00.0: nForce2 C1 Halt Disconnect fixup
[    0.468467] PCI: 0000:00:01.1 reg 10 io port: [e400, e41f]
[    0.468500] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.468506] pci 0000:00:01.1: PME# disabled
[    0.468533] PCI: 0000:00:02.0 reg 10 32bit mmio: [e8001000, e8001fff]
[    0.468566] pci 0000:00:02.0: supports D1
[    0.468568] pci 0000:00:02.0: supports D2
[    0.468570] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.468575] pci 0000:00:02.0: PME# disabled
[    0.468597] PCI: 0000:00:02.1 reg 10 32bit mmio: [e8002000, e8002fff]
[    0.468629] pci 0000:00:02.1: supports D1
[    0.468631] pci 0000:00:02.1: supports D2
[    0.468634] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.468638] pci 0000:00:02.1: PME# disabled
[    0.468667] PCI: 0000:00:02.2 reg 10 32bit mmio: [e8003000, e80030ff]
[    0.468704] pci 0000:00:02.2: supports D1
[    0.468706] pci 0000:00:02.2: supports D2
[    0.468708] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.468713] pci 0000:00:02.2: PME# disabled
[    0.468777] PCI: 0000:00:09.0 reg 20 io port: [f000, f00f]
[    0.468876] PCI: 0000:01:07.0 reg 10 32bit mmio: [e7101000, e7101fff]
[    0.468884] PCI: 0000:01:07.0 reg 14 32bit mmio: [e7000000, e70fffff]
[    0.468926] pci 0000:01:07.0: supports D1
[    0.468928] pci 0000:01:07.0: supports D2
[    0.468959] PCI: 0000:01:09.0 reg 10 io port: [c000, c0ff]
[    0.468967] PCI: 0000:01:09.0 reg 14 32bit mmio: [e7100000, e71003ff]
[    0.468996] PCI: 0000:01:09.0 reg 30 32bit mmio: [0, 1ffff]
[    0.469011] pci 0000:01:09.0: supports D1
[    0.469013] pci 0000:01:09.0: supports D2
[    0.469016] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469021] pci 0000:01:09.0: PME# disabled
[    0.469051] PCI: 0000:01:0a.0 reg 10 io port: [c400, c4ff]
[    0.469059] PCI: 0000:01:0a.0 reg 14 32bit mmio: [e7102000, e71020ff]
[    0.469100] pci 0000:01:0a.0: supports D1
[    0.469102] pci 0000:01:0a.0: supports D2
[    0.469105] pci 0000:01:0a.0: PME# supported from D1 D2 D3hot
[    0.469110] pci 0000:01:0a.0: PME# disabled
[    0.469142] PCI: bridge 0000:00:08.0 io port: [c000, cfff]
[    0.469147] PCI: bridge 0000:00:08.0 32bit mmio: [e6000000, e7ffffff]
[    0.469192] PCI: 0000:02:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.469200] PCI: 0000:02:00.0 reg 14 io port: [d000, d0ff]
[    0.469208] PCI: 0000:02:00.0 reg 18 32bit mmio: [e5000000, e500ffff]
[    0.469229] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.469248] pci 0000:02:00.0: supports D1
[    0.469250] pci 0000:02:00.0: supports D2
[    0.469282] PCI: 0000:02:00.1 reg 10 32bit mmio: [e5010000, e5013fff]
[    0.469326] pci 0000:02:00.1: supports D1
[    0.469328] pci 0000:02:00.1: supports D2
[    0.469366] PCI: bridge 0000:00:1e.0 io port: [d000, dfff]
[    0.469370] PCI: bridge 0000:00:1e.0 32bit mmio: [e4000000, e5ffffff]
[    0.469374] PCI: bridge 0000:00:1e.0 32bit mmio pref: [d0000000, dfffffff]
[    0.469385] bus 00 -> node 0
[    0.469394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.469664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.470058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.529471] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.529701] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[    0.529928] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.530156] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.530382] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.530610] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.530843] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[    0.531072] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.531299] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.531525] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.531751] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.531979] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.532217] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.532446] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.532674] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.532901] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.533098] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
[    0.533276] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
[    0.533453] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[    0.533631] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[    0.533808] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.534065] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.534323] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[    0.534579] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[    0.534836] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[    0.535092] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[    0.535349] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[    0.535529] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[    0.535792] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.536059] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[    0.536319] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[    0.536576] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.536805] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.536855] pnp: PnP ACPI init
[    0.536865] ACPI: bus type pnp registered
[    0.544561] pnp: PnP ACPI: found 16 devices
[    0.544564] ACPI: ACPI bus type pnp unregistered
[    0.544569] PnPBIOS: Disabled by ACPI PNP
[    0.545091] PCI: Using ACPI for IRQ routing
[    0.545238] NET: Registered protocol family 8
[    0.545238] NET: Registered protocol family 20
[    0.545238] NetLabel: Initializing
[    0.545238] NetLabel:  domain hash size = 128
[    0.545238] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.545238] NetLabel:  unlabeled traffic allowed by default
[    0.545238] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.545238]    actual entries 65620
[    0.545238] AppArmor: AppArmor Filesystem Enabled
[    0.545238] ACPI: RTC can wake from S4
[    0.545238] system 00:00: ioport range 0x4000-0x407f has been reserved
[    0.545238] system 00:00: ioport range 0x4080-0x40ff has been reserved
[    0.545238] system 00:00: ioport range 0x4400-0x447f has been reserved
[    0.545238] system 00:00: ioport range 0x4480-0x44ff has been reserved
[    0.545238] system 00:00: ioport range 0x4200-0x427f has been reserved
[    0.545238] system 00:00: ioport range 0x4280-0x42ff has been reserved
[    0.545238] system 00:01: ioport range 0x5000-0x503f has been reserved
[    0.545238] system 00:01: ioport range 0x5500-0x553f has been reserved
[    0.545238] system 00:02: iomem range 0xcf000-0xcffff has been reserved
[    0.545238] system 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[    0.545238] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[    0.545238] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[    0.545238] system 00:02: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.545238] system 00:02: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.545238] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    0.545238] system 00:02: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.545238] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.545238] system 00:02: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.545238] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.581326] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.581331] pci 0000:00:08.0:   IO window: 0xc000-0xcfff
[    0.581337] pci 0000:00:08.0:   MEM window: 0xe6000000-0xe7ffffff
[    0.581342] pci 0000:00:08.0:   PREFETCH window: 0x00000050000000-0x000000500fffff
[    0.581351] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.581354] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.581359] pci 0000:00:1e.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.581364] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.581379] pci 0000:00:08.0: setting latency timer to 64
[    0.581387] bus: 00 index 0 io port: [0, ffff]
[    0.581390] bus: 00 index 1 mmio: [0, ffffffff]
[    0.581392] bus: 01 index 0 io port: [c000, cfff]
[    0.581395] bus: 01 index 1 mmio: [e6000000, e7ffffff]
[    0.581398] bus: 01 index 2 mmio: [50000000, 500fffff]
[    0.581400] bus: 01 index 3 mmio: [0, 0]
[    0.581402] bus: 02 index 0 io port: [d000, dfff]
[    0.581405] bus: 02 index 1 mmio: [e4000000, e5ffffff]
[    0.581407] bus: 02 index 2 mmio: [d0000000, dfffffff]
[    0.581410] bus: 02 index 3 mmio: [0, 0]
[    0.581422] NET: Registered protocol family 2
[    0.581574] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.581969] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.583440] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.584255] TCP: Hash tables configured (established 131072 bind 65536)
[    0.584259] TCP reno registered
[    0.584396] NET: Registered protocol family 1
[    0.584553] checking if image is initramfs... it is
[    1.084056] Switched to high resolution mode on CPU 0
[    1.331009] Freeing initrd memory: 7972k freed
[    1.332116] audit: initializing netlink socket (disabled)
[    1.332138] type=2000 audit(1238318022.332:1): initialized
[    1.338256] highmem bounce pool size: 64 pages
[    1.338265] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.341401] VFS: Disk quotas dquot_6.5.1
[    1.341513] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.341653] msgmni has been set to 1762
[    1.341812] io scheduler noop registered
[    1.341815] io scheduler anticipatory registered
[    1.341818] io scheduler deadline registered
[    1.341831] io scheduler cfq registered (default)
[    1.341984] pci 0000:02:00.0: Boot video device
[    1.342443] isapnp: Scanning for PnP cards...
[    1.696715] isapnp: No Plug & Play device found
[    1.750088] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.750258] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.750451] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.751274] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.751660] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.754398] brd: module loaded
[    1.754500] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.754660] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.754664] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.755138] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.755644] mice: PS/2 mouse device common for all mice
[    1.755837] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.755862] rtc0: alarms up to one year, y3k
[    1.756043] EISA: Probing bus 0 at eisa.0
[    1.756067] Cannot allocate resource for EISA slot 4
[    1.756070] Cannot allocate resource for EISA slot 5
[    1.756085] EISA: Detected 0 cards.
[    1.756090] cpuidle: using governor ladder
[    1.756092] cpuidle: using governor menu
[    1.756714] TCP cubic registered
[    1.756749] Using IPI No-Shortcut mode
[    1.757009] registered taskstats version 1
[    1.757140]   Magic number: 1:282:223
[    1.757200] tty ttyu7: hash matches
[    1.757214] tty ttyra: hash matches
[    1.757368] rtc_cmos 00:06: setting system clock to 2009-03-29 09:13:43 UTC (1238318023)
[    1.757373] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.757376] EDD information not available.
[    1.757881] Freeing unused kernel memory: 424k freed
[    1.757945] Write protecting the kernel text: 2576k
[    1.757986] Write protecting the kernel read-only data: 936k
[    1.782418] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.989669] fuse init (API version 7.9)
[    2.261031] processor ACPI0007:00: registered as cooling_device0
[    3.410583] usbcore: registered new interface driver usbfs
[    3.410616] usbcore: registered new interface driver hub
[    3.425479] No dock devices found.
[    3.449476] usbcore: registered new device driver usb
[    3.473752] SCSI subsystem initialized
[    3.474301] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    3.474629] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    3.474641] tulip 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, high) -> IRQ 17
[    3.475483] tulip0:  MII transceiver #1 config 3100 status 7849 advertising 05e1.
[    3.476566] tulip0:  MII transceiver #2 config 1000 status 7849 advertising 05e1.
[    3.477381] tulip0:  MII transceiver #3 config 1000 status 7849 advertising 05e1.
[    3.478194] tulip0:  MII transceiver #4 config 1000 status 7849 advertising 05e1.
[    3.478492] eth0: ADMtek Comet rev 17 at Port 0xc000, 00:c0:26:c4:02:8b, IRQ 17.
[    3.483487] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    3.483501] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
[    3.483517] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    3.483521] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    3.483583] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    3.483626] ehci_hcd 0000:00:02.2: debug port 1
[    3.483632] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    3.483650] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe8003000
[    3.486334] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.490396] 8139too Fast Ethernet driver 0.9.28
[    3.492120] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.492389] usb usb1: configuration #1 chosen from 1 choice
[    3.492445] hub 1-0:1.0: USB hub found
[    3.492460] hub 1-0:1.0: 6 ports detected
[    3.548808] libata version 3.00 loaded.
[    3.700966] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    3.700979] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
[    3.701000] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.701004] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.701036] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    3.701070] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe8001000
[    3.758310] usb usb2: configuration #1 chosen from 1 choice
[    3.758348] hub 2-0:1.0: USB hub found
[    3.758364] hub 2-0:1.0: 3 ports detected
[    3.860935] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[    3.860948] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
[    3.860966] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    3.860971] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    3.861003] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    3.861033] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe8002000
[    3.918275] usb usb3: configuration #1 chosen from 1 choice
[    3.918322] hub 3-0:1.0: USB hub found
[    3.918339] hub 3-0:1.0: 3 ports detected
[    4.124403] pata_amd 0000:00:09.0: version 0.3.10
[    4.124482] pata_amd 0000:00:09.0: setting latency timer to 64
[    4.124601] scsi0 : pata_amd
[    4.124780] scsi1 : pata_amd
[    4.125959] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    4.125963] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.300016] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    4.305662] ata1.00: ATA-6: WDC WD1200JB-00GVA0, 08.02D08, max UDMA/100
[    4.305667] ata1.00: 234441648 sectors, multi 16: LBA48 
[    4.320668] ata1.01: HPA unlocked: 361879967 -> 361882080, native 361882080
[    4.320674] ata1.01: ATA-6: IC35L180AVV207-1, V26OA63A, max UDMA/100
[    4.320678] ata1.01: 361882080 sectors, multi 16: LBA48 
[    4.320694] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6c6c0c0) ACPI=0x3f01f (20:20:0x1f)
[    4.320701] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6c6c0c0) ACPI=0x3f01f (20:20:0x1f)
[    4.337563] ata1.00: configured for UDMA/100
[    4.360786] ata1.01: configured for UDMA/100
[    4.515455] usb 3-1: configuration #1 chosen from 1 choice
[    4.700360] ata2.00: ATAPI: Optiarc DVD RW AD-7173A, 1-01, max UDMA/66
[    4.700380] ata2.01: ATAPI: LITE-ON LTR-40125S, ZS0K, max UDMA/33
[    4.700396] ata2: nv_mode_filter: 0x1f39f&0x701f->0x701f, BIOS=0x7000 (0xc6c6c0c0) ACPI=0x701f (60:60:0x1f)
[    4.700402] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc6c6c0c0) ACPI=0x701f (60:60:0x1f)
[    4.716281] ata2.00: configured for UDMA/33
[    4.732259] ata2.01: configured for UDMA/33
[    4.732406] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200JB-00G 08.0 PQ: 0 ANSI: 5
[    4.733119] scsi 0:0:1:0: Direct-Access     ATA      IC35L180AVV207-1 V26O PQ: 0 ANSI: 5
[    4.734195] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7173A  1-01 PQ: 0 ANSI: 5
[    4.739823] scsi 1:0:1:0: CD-ROM            LITE-ON  LTR-40125S       ZS0K PQ: 0 ANSI: 5
[    4.740745] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    4.740757] 8139too 0000:01:0a.0: PCI INT A -> Link[APC1] -> GSI 16 (level, high) -> IRQ 16
[    4.741634] eth1: RealTek RTL8139 at 0xc400, 00:40:33:e2:9b:e2, IRQ 16
[    4.741638] eth1:  Identified 8139 chip type 'RTL-8139B'
[    4.747914] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.806249] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.806316] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[    4.806374] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    4.806424] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[    4.834124] usbcore: registered new interface driver hiddev
[    4.841402] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input2
[    4.848349] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.1-1
[    4.848379] usbcore: registered new interface driver usbhid
[    4.848384] usbhid: v2.6:USB HID core driver
[    4.867142] Driver 'sd' needs updating - please use bus_type methods
[    4.867304] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.867330] sd 0:0:0:0: [sda] Write Protect is off
[    4.867334] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.867372] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.867466] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.867487] sd 0:0:0:0: [sda] Write Protect is off
[    4.867491] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.867528] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.867534]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.887176]  sda1
[    4.887326] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.887465] sd 0:0:1:0: [sdb] 361882080 512-byte hardware sectors (185284 MB)
[    4.887493] sd 0:0:1:0: [sdb] Write Protect is off
[    4.887497] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.887538] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.887626] sd 0:0:1:0: [sdb] 361882080 512-byte hardware sectors (185284 MB)
[    4.887649] sd 0:0:1:0: [sdb] Write Protect is off
[    4.887653] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.887693] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.887699]  sdb: sdb1 < sdb5 sdb6 sdb7 >
[    4.945173] sd 0:0:1:0: [sdb] Attached SCSI disk
[    4.955536] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.955543] Uniform CD-ROM driver Revision: 3.20
[    4.955692] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.004428] sr1: scsi3-mmc drive: 178x/48x writer cd/rw xa/form2 cdda tray
[    5.004574] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.343507] PM: Starting manual resume from disk
[    5.343512] PM: Resume from partition 8:22
[    5.343515] PM: Checking hibernation image.
[    5.343670] PM: Resume from disk failed.
[    5.391076] kjournald starting.  Commit interval 5 seconds
[    5.391098] EXT3-fs: mounted filesystem with ordered data mode.
[   11.215795] udevd version 124 started
[   11.943423] Linux agpgart interface v0.103
[   11.989941] agpgart: Detected NVIDIA nForce2 chipset
[   11.995066] agpgart-nvidia 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   12.327304] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   12.327349] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5500
[   12.360035] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   12.375320] ACPI: Power Button (FF) [PWRF]
[   12.375508] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   12.388032] ACPI: Power Button (CM) [PWRB]
[   12.744664] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.797768] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.080042] parport_pc 00:0c: reported by Plug and Play ACPI
[   13.080104] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   15.335526] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   15.787925] HDA Intel 0000:02:00.1: can't derive routing for PCI INT B
[   15.787931] HDA Intel 0000:02:00.1: PCI INT B: no GSI - using IRQ 11
[   16.810265] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   16.840942] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   16.840955] Sound Fusion CS46xx 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, high) -> IRQ 19
[   17.336853] irq 19: nobody cared (try booting with the "irqpoll" option)
[   17.336863] Pid: 2997, comm: udevd Not tainted 2.6.27-7-generic #1
[   17.336867]  [<c037c3f6>] ? printk+0x1d/0x1f
[   17.336881]  [<c01781bc>] __report_bad_irq+0x2c/0xa0
[   17.336890]  [<c0178344>] note_interrupt+0x114/0x140
[   17.336896]  [<c01770b1>] ? handle_IRQ_event+0x41/0x80
[   17.336901]  [<c0178993>] handle_fasteoi_irq+0xb3/0xe0
[   17.336905]  [<c01b5993>] ? sys_readlinkat+0x33/0xa0
[   17.336913]  [<c0106c15>] do_IRQ+0x45/0x80
[   17.336920]  [<c01b5a2c>] ? sys_readlink+0x2c/0x30
[   17.336924]  [<c0105003>] common_interrupt+0x23/0x30
[   17.336929]  =======================
[   17.336931] handlers:
[   17.336934] [<f8b297d0>] (snd_cs46xx_interrupt+0x0/0x1f0 [snd_cs46xx])
[   17.336950] Disabling IRQ #19
[   17.405516] gameport: CS46xx Gameport is pci0000:01:07.0/gameport0, speed 59659kHz
[   19.651354] lp0: using parport0 (interrupt-driven).
[   19.946493] Adding 1003988k swap on /dev/sdb6.  Priority:-1 extents:1 across:1003988k
[   20.521672] EXT3 FS on sdb7, internal journal
[   21.524398] type=1505 audit(1238310843.422:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4294
[   21.770699] type=1505 audit(1238310843.666:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4299
[   21.771077] type=1505 audit(1238310843.666:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4299
[   21.923700] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.456473] ACPI: WMI: Mapper loaded
[   23.554724] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.609053] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   23.609062] apm: overridden by ACPI.
[   23.771420] ppdev: user-space parallel port driver
[   25.125022] Bluetooth: Core ver 2.13
[   25.127376] NET: Registered protocol family 31
[   25.127384] Bluetooth: HCI device and connection manager initialized
[   25.127389] Bluetooth: HCI socket layer initialized
[   25.147434] Bluetooth: L2CAP ver 2.11
[   25.147443] Bluetooth: L2CAP socket layer initialized
[   25.163105] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.163114] Bluetooth: BNEP filters: protocol multicast
[   25.212927] Bridge firewalling registered
[   25.213874] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   25.228613] Bluetooth: SCO (Voice Link) ver 0.6
[   25.228622] Bluetooth: SCO socket layer initialized
[   25.272047] Bluetooth: RFCOMM socket layer initialized
[   25.272385] Bluetooth: RFCOMM TTY layer initialized
[   25.272392] Bluetooth: RFCOMM ver 1.10
[   27.051458] pci 0000:02:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, high) -> IRQ 19
[   29.376666] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   29.616542] NET: Registered protocol family 17
[   29.995254] irq 16: nobody cared (try booting with the "irqpoll" option)
[   29.995276] Pid: 5461, comm: grep Not tainted 2.6.27-7-generic #1
[   29.995280]  [<c037c3f6>] ? printk+0x1d/0x1f
[   29.995294]  [<c01781bc>] __report_bad_irq+0x2c/0xa0
[   29.995303]  [<c0178344>] note_interrupt+0x114/0x140
[   29.995308]  [<c01770b1>] ? handle_IRQ_event+0x41/0x80
[   29.995313]  [<c0178993>] handle_fasteoi_irq+0xb3/0xe0
[   29.995318]  [<c01b3578>] ? fput+0x8/0x30
[   29.995324]  [<c0106c15>] do_IRQ+0x45/0x80
[   29.995330]  [<c01aff3f>] ? sys_close+0x7f/0xd0
[   29.995334]  [<c0105003>] common_interrupt+0x23/0x30
[   29.995339]  =======================
[   29.995341] handlers:
[   29.995344] [<f88ffed0>] (rtl8139_interrupt+0x0/0x190 [8139too])
[   29.995375] Disabling IRQ #16
[   71.816024] ------------[ cut here ]------------
[   71.816034] WARNING: at /build/buildd/linux-2.6.27/net/sched/sch_generic.c:219 dev_watchdog+0x21a/0x230()
[   71.816037] NETDEV WATCHDOG: eth1 (8139too): transmit timed out
[   71.816040] Modules linked in: af_packet binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev cpufreq_powersave cpufreq_userspace cpufreq_ondemand cpufreq_conservative cpufreq_stats freq_table container pci_slot sbs sbshc wmi video output battery iptable_filter ip_tables x_tables ac lp snd_cs46xx gameport snd_ac97_codec snd_hda_intel ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm evdev snd_seq_dummy pcspkr snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc parport_pc parport shpchp pci_hotplug button i2c_nforce2 i2c_core nvidia_agp agpgart ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif usbhid hid sg pata_acpi ata_generic 8139cp pata_amd libata 8139too mii ohci_hcd ehci_hcd tulip scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   71.816115] Pid: 0, comm: swapper Not tainted 2.6.27-7-generic #1
[   71.816120]  [<c0131d65>] warn_slowpath+0x65/0x90
[   71.816129]  [<c012b6ab>] ? default_wake_function+0xb/0x10
[   71.816135]  [<c0121670>] ? __wake_up_common+0x40/0x70
[   71.816143]  [<c037df9e>] ? account_scheduler_latency+0xe/0x220
[   71.816149]  [<c037df9e>] ? account_scheduler_latency+0xe/0x220
[   71.816153]  [<c0150502>] ? clocksource_get_next+0x42/0x50
[   71.816162]  [<c014f082>] ? update_wall_time+0x442/0x890
[   71.816167]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
[   71.816171]  [<c0136976>] ? set_normalized_timespec+0x16/0x90
[   71.816176]  [<c0154387>] ? timer_stats_update_stats+0x17/0x250
[   71.816182]  [<c0254299>] ? strlen+0x9/0x20
[   71.816190]  [<c025231d>] ? strlcpy+0x1d/0x60
[   71.816194]  [<c02f0967>] ? netdev_drivername+0x37/0x40
[   71.816199]  [<c0305b6a>] dev_watchdog+0x21a/0x230
[   71.816203]  [<c01136c0>] ? lapic_next_event+0x20/0x30
[   71.816212]  [<c0151d0f>] ? clockevents_program_event+0x9f/0x150
[   71.816216]  [<c013bf88>] run_timer_softirq+0x138/0x210
[   71.816222]  [<c0305950>] ? dev_watchdog+0x0/0x230
[   71.816227]  [<c0305950>] ? dev_watchdog+0x0/0x230
[   71.816231]  [<c0137682>] __do_softirq+0x92/0x120
[   71.816235]  [<c013776d>] do_softirq+0x5d/0x60
[   71.816239]  [<c01378e5>] irq_exit+0x55/0x90
[   71.816242]  [<c0113f8d>] smp_apic_timer_interrupt+0x5d/0x90
[   71.816247]  [<c01050f8>] apic_timer_interrupt+0x28/0x30
[   71.816253]  [<c011aba5>] ? native_safe_halt+0x5/0x10
[   71.816260]  [<c010aaed>] default_idle+0x5d/0x60
[   71.816266]  [<c010288d>] cpu_idle+0x7d/0x140
[   71.816270]  [<c036edc3>] rest_init+0x53/0x60
[   71.816278]  =======================
[   71.816280] ---[ end trace 17cc072b9d690b5e ]---
[   74.816063] eth1: Transmit timeout, status 0c 0005 c07f media 00.
[   74.816073] eth1: Tx queue start entry 4  dirty entry 0.
[   74.816078] eth1:  Tx descriptor 0 is 0008a156. (queue head)
[   74.816082] eth1:  Tx descriptor 1 is 0008a156.
[   74.816085] eth1:  Tx descriptor 2 is 0008a156.
[   74.816088] eth1:  Tx descriptor 3 is 0008a156.
[   74.816112] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[  110.608099] ppdev0: registered pardevice
[  110.656026] ppdev0: unregistered pardevice
[  111.320287] ppdev0: registered pardevice
[  111.368314] ppdev0: unregistered pardevice
[  111.467515] type=1503 audit(1238310933.362:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5737/net/" pid=5737 profile="/usr/sbin/cupsd"
[  111.542029] NET: Registered protocol family 10
[  111.544394] lo: Disabled Privacy Extensions
[  111.545823] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  111.547680] type=1503 audit(1238310933.442:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5737 profile="/usr/sbin/cupsd"
[  111.547694] type=1503 audit(1238310933.442:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5737 profile="/usr/sbin/cupsd"
[  111.547702] type=1503 audit(1238310933.442:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5737 profile="/usr/sbin/cupsd"
[  111.547710] type=1503 audit(1238310933.442:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5737 profile="/usr/sbin/cupsd"
[  111.547718] type=1503 audit(1238310933.442:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5737 profile="/usr/sbin/cupsd"
[  111.547726] type=1503 audit(1238310933.442:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5737 profile="/usr/sbin/cupsd"
[  111.547734] type=1503 audit(1238310933.442:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5737 profile="/usr/sbin/cupsd"
[  111.547742] type=1503 audit(1238310933.442:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5737 profile="/usr/sbin/cupsd"
[  111.547832] type=1503 audit(1238310933.442:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5737/net/dev" pid=5737 profile="/usr/sbin/cupsd"
[  112.655125] ppdev0: registered pardevice
[  112.704251] ppdev0: unregistered pardevice
[  122.280011] eth1: no IPv6 routers present
[  122.816025] eth1: Transmit timeout, status 0c 0005 c07f media 00.
[  122.816035] eth1: Tx queue start entry 4  dirty entry 0.
[  122.816040] eth1:  Tx descriptor 0 is 0008a156. (queue head)
[  122.816044] eth1:  Tx descriptor 1 is 0008a05a.
[  122.816047] eth1:  Tx descriptor 2 is 0008a04e.
[  122.816051] eth1:  Tx descriptor 3 is 0008a046.
[  122.816074] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1 
```

lshw -C network :

```
  *-network:0
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 11
       serial: 00:c0:26:c4:02:8b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: eth1
       version: 10
       serial: 00:40:33:e2:9b:e2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:f9:9a:e4:4f:9a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
```


ps. eth1 is the one that should connect.

---

### Post by ahac on 2009-04-02
So... does anyone see why it doesn't work?

---

### Post by superprash2003 on 2009-04-02
have you tried inserting static ip?

---

