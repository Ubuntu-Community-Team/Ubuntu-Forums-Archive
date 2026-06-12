---
title: "eth0 periodically disconnects"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by camerazn on 2009-02-22
I just installed 8.10 on a client's machine (HP Pavilion 523n, probably about four or five years old), and it acts like I'm unplugging and plugging back in the network cable every ten-or-so seconds, but only when I'm actually downloading something. 

It might be the NIC (onboard card, the computer would not boot before the Ubuntu install, so I couldn't check), or it might be Ubuntu. It's not the router. I've got other machines hooked up to that router with no issues, and I tried my client's machine on several different ports.

I'm considering installing a new network card, as it could be just a wonky NIC. Any configuration tweaks I can try before that?

---

### Post by pytheas22 on 2009-02-23
Did you look at the output of 'dmesg' while the card is being flaky?  It might provide a clue as to what's wrong.

You should also run 'lspci -nn' to get the device ID (a number like XXXX:XXXX) for the card and google it; if anyone else has had trouble with it on Linux, you'll probably find something.  If not, post the device ID here and dmesg output here.

---

### Post by camerazn on 2009-02-23
> **pytheas22 said:**
> Did you look at the output of 'dmesg' while the card is being flaky?  It might provide a clue as to what's wrong.

You should also run 'lspci -nn' to get the device ID (a number like XXXX:XXXX) for the card and google it; if anyone else has had trouble with it on Linux, you'll probably find something.  If not, post the device ID here and dmesg output here.

I google'd the results of lspci -nn, but my reading comprehension is weak.

lspci -nn
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)


I got this out of the dmesg. It looks relevant. 
[    3.312214] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.312255] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.312262] 8139cp 0000:00:0b.0: Try the "8139too" driver instead.
[    3.332288] 8139too Fast Ethernet driver 0.9.28
[    3.332363] 8139too 0000:00:0b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.333026] eth0: RealTek RTL8139 at 0xd800, 00:40:ca:2e:e4:5e, IRQ 18
[    3.333030] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'


And finally, the whole dmesg
```


jenny@jenny-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1dff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 1dff0000 @ 10000-16000
[    0.000000] RAMDISK: 1d811000 - 1dfdf324
[    0.000000] ACPI: RSDP 000F7470, 0014 (r0 KM266 )
[    0.000000] ACPI: RSDT 1DFF3000, 002C (r1 KM266  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1DFF3040, 0074 (r1 KM266  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1DFF30C0, 370E (r1 KM266  AWRDACPI     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1DFF0000, 0040
[    0.000000] ACPI: APIC 1DFF6800, 0054 (r1 KM266  AWRDACPI 42302E31 AWRD        0)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1dff0000
[    0.000000]   low ram: 00000000 - 1dff0000
[    0.000000]   bootmap 00012000 - 00015c00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [001d811000 - 001dfdf324]          RAMDISK ==> [001d811000 - 001dfdf324]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] found SMP MP-table at [c00f54a0] 000f54a0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001dff0
[    0.000000]   HighMem  0x0001dff0 -> 0x0001dff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001dff0
[    0.000000] On node 0 totalpages: 122751
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 117724 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121671
[    0.000000] Kernel command line: root=UUID=62686ba4-325f-41a2-871e-97b4a42bba20 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1798.439 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 473096k/491456k available (2576k kernel code, 17684k reserved, 1165k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xde800000 - 0xff3fe000   ( 523 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 3596.87 BogoMIPS (lpj=7193756)
[    0.004049] Security Framework initialized
[    0.004061] SELinux:  Disabled at boot.
[    0.004100] AppArmor: AppArmor initialized
[    0.004113] Mount-cache hash table entries: 512
[    0.004357] Initializing cgroup subsys ns
[    0.004364] Initializing cgroup subsys cpuacct
[    0.004367] Initializing cgroup subsys memory
[    0.004389] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004392] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004413] Checking 'hlt' instruction... OK.
[    0.020432] SMP alternatives: switching to UP code
[    0.026731] Freeing SMP alternatives: 11k freed
[    0.026739] ACPI: Core revision 20080609
[    0.029574] ACPI: Checking initramfs for custom DSDT
[    0.403792] ENABLING IO-APIC IRQs
[    0.404025] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.443835] CPU0: AMD Athlon(tm) XP 2200+ stepping 00
[    0.444027] Brought up 1 CPUs
[    0.444027] Total of 1 processors activated (3596.87 BogoMIPS).
[    0.444027] CPU0 attaching NULL sched-domain.
[    0.444027] net_namespace: 840 bytes
[    0.444027] Booting paravirtualized kernel on bare hardware
[    0.444027] Time:  5:06:07  Date: 02/23/09
[    0.444027] NET: Registered protocol family 16
[    0.444027] EISA bus registered
[    0.444027] ACPI: bus type pci registered
[    0.514446] PCI: PCI BIOS revision 2.10 entry at 0xfb1e0, last bus=1
[    0.514451] PCI: Using configuration type 1 for base access
[    0.516720] ACPI: EC: Look up EC in DSDT
[    0.523447] ACPI: Interpreter enabled
[    0.523454] ACPI: (supports S0 S1 S3 S4 S5)
[    0.523476] ACPI: Using IOAPIC for interrupt routing
[    0.531065] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.531197] PCI: 0000:00:00.0 reg 10 32bit mmio: [e8000000, ebffffff]
[    0.531273] pci 0000:00:01.0: supports D1
[    0.531308] PCI: 0000:00:09.0 reg 10 32bit mmio: [ef001000, ef0010ff]
[    0.531315] PCI: 0000:00:09.0 reg 14 io port: [d000, d007]
[    0.531322] PCI: 0000:00:09.0 reg 18 io port: [d400, d4ff]
[    0.531352] pci 0000:00:09.0: supports D2
[    0.531356] pci 0000:00:09.0: PME# supported from D2 D3hot D3cold
[    0.531361] pci 0000:00:09.0: PME# disabled
[    0.531388] PCI: 0000:00:0b.0 reg 10 io port: [d800, d8ff]
[    0.531395] PCI: 0000:00:0b.0 reg 14 32bit mmio: [ef000000, ef0000ff]
[    0.531418] PCI: 0000:00:0b.0 reg 30 32bit mmio: [0, ffff]
[    0.531432] pci 0000:00:0b.0: supports D1
[    0.531434] pci 0000:00:0b.0: supports D2
[    0.531436] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
[    0.531441] pci 0000:00:0b.0: PME# disabled
[    0.531553] PCI: 0000:00:11.1 reg 20 io port: [dc00, dc0f]
[    0.531616] PCI: 0000:00:11.2 reg 20 io port: [e000, e01f]
[    0.531676] PCI: 0000:00:11.3 reg 20 io port: [e400, e41f]
[    0.531722] PCI: 0000:00:11.5 reg 10 io port: [e800, e8ff]
[    0.531810] PCI: 0000:01:00.0 reg 10 32bit mmio: [ed000000, ed07ffff]
[    0.531816] PCI: 0000:01:00.0 reg 14 32bit mmio: [e0000000, e7ffffff]
[    0.531836] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, ffff]
[    0.531848] pci 0000:01:00.0: supports D1
[    0.531850] pci 0000:01:00.0: supports D2
[    0.531884] PCI: bridge 0000:00:01.0 32bit mmio: [ec000000, edffffff]
[    0.531889] PCI: bridge 0000:00:01.0 32bit mmio pref: [e0000000, e7ffffff]
[    0.531897] bus 00 -> node 0
[    0.531908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.555898] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.556166] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 10 11 12 14 15)
[    0.556424] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[    0.556680] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.556994] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *0
[    0.557275] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *0
[    0.557582] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.557856] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0
[    0.558115] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.558176] pnp: PnP ACPI init
[    0.558202] ACPI: bus type pnp registered
[    0.563981] pnp: PnP ACPI: found 14 devices
[    0.563987] ACPI: ACPI bus type pnp unregistered
[    0.563994] PnPBIOS: Disabled by ACPI PNP
[    0.564668] PCI: Using ACPI for IRQ routing
[    0.564842] NET: Registered protocol family 8
[    0.564842] NET: Registered protocol family 20
[    0.564842] NetLabel: Initializing
[    0.564842] NetLabel:  domain hash size = 128
[    0.564842] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.564842] NetLabel:  unlabeled traffic allowed by default
[    0.564842] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.564842]    actual entries 65620
[    0.564868] AppArmor: AppArmor Filesystem Enabled
[    0.564893] ACPI: RTC can wake from S4
[    0.564911] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[    0.564911] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[    0.564911] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.564911] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.564911] system 00:00: iomem range 0x1dff0000-0x1dffffff could not be reserved
[    0.564911] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.564911] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.564911] system 00:00: iomem range 0x100000-0x1dfeffff could not be reserved
[    0.564911] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.564911] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.564911] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.564911] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.564911] system 00:02: ioport range 0x800-0x805 has been reserved
[    0.564911] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.601362] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.601367] pci 0000:00:01.0:   IO window: disabled
[    0.601375] pci 0000:00:01.0:   MEM window: 0xec000000-0xedffffff
[    0.601380] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000e7ffffff
[    0.601400] pci 0000:00:01.0: setting latency timer to 64
[    0.601405] bus: 00 index 0 io port: [0, ffff]
[    0.601408] bus: 00 index 1 mmio: [0, ffffffff]
[    0.601411] bus: 01 index 0 mmio: [0, 0]
[    0.601413] bus: 01 index 1 mmio: [ec000000, edffffff]
[    0.601416] bus: 01 index 2 mmio: [e0000000, e7ffffff]
[    0.601418] bus: 01 index 3 mmio: [0, 0]
[    0.601444] NET: Registered protocol family 2
[    0.601639] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.601970] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.602290] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.602614] TCP: Hash tables configured (established 16384 bind 16384)
[    0.602619] TCP reno registered
[    0.602796] NET: Registered protocol family 1
[    0.603026] checking if image is initramfs... it is
[    1.104114] Switched to high resolution mode on CPU 0
[    1.448897] Freeing initrd memory: 7992k freed
[    1.450213] audit: initializing netlink socket (disabled)
[    1.450244] type=2000 audit(1235365567.448:1): initialized
[    1.456853] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.460542] VFS: Disk quotas dquot_6.5.1
[    1.460700] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.460896] msgmni has been set to 940
[    1.461118] io scheduler noop registered
[    1.461122] io scheduler anticipatory registered
[    1.461125] io scheduler deadline registered
[    1.461153] io scheduler cfq registered (default)
[    1.461178] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.461225] pci 0000:01:00.0: Boot video device
[    1.461755] isapnp: Scanning for PnP cards...
[    1.815151] isapnp: No Plug & Play device found
[    1.884522] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.884685] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.885933] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.888785] brd: module loaded
[    1.888913] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.889145] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.889613] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.889622] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.890633] mice: PS/2 mouse device common for all mice
[    1.890873] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.890912] rtc0: alarms up to one year, y3k
[    1.891122] EISA: Probing bus 0 at eisa.0
[    1.891145] Cannot allocate resource for EISA slot 4
[    1.891162] EISA: Detected 0 cards.
[    1.891168] cpuidle: using governor ladder
[    1.891172] cpuidle: using governor menu
[    1.891899] TCP cubic registered
[    1.891945] Using IPI No-Shortcut mode
[    1.892376] registered taskstats version 1
[    1.892513]   Magic number: 13:295:113
[    1.892812] rtc_cmos 00:04: setting system clock to 2009-02-23 05:06:09 UTC (1235365569)
[    1.892818] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.892821] EDD information not available.
[    1.893669] Freeing unused kernel memory: 424k freed
[    1.893745] Write protecting the kernel text: 2580k
[    1.893794] Write protecting the kernel read-only data: 940k
[    1.921893] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.216056] fuse init (API version 7.9)
[    2.459514] processor ACPI0007:00: registered as cooling_device0
[    3.312214] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.312255] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.312262] 8139cp 0000:00:0b.0: Try the "8139too" driver instead.
[    3.332288] 8139too Fast Ethernet driver 0.9.28
[    3.332363] 8139too 0000:00:0b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.333026] eth0: RealTek RTL8139 at 0xd800, 00:40:ca:2e:e4:5e, IRQ 18
[    3.333030] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.348311] No dock devices found.
[    3.449089] SCSI subsystem initialized
[    3.491128] usbcore: registered new interface driver usbfs
[    3.491191] usbcore: registered new interface driver hub
[    3.491286] usbcore: registered new device driver usb
[    3.564149] USB Universal Host Controller Interface driver v3.0
[    3.564721] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
[    3.564726] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
[    3.564739] uhci_hcd 0000:00:11.2: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    3.564755] uhci_hcd 0000:00:11.2: UHCI Host Controller
[    3.564845] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[    3.564893] uhci_hcd 0000:00:11.2: irq 21, io base 0x0000e000
[    3.565233] usb usb1: configuration #1 chosen from 1 choice
[    3.565274] hub 1-0:1.0: USB hub found
[    3.565291] hub 1-0:1.0: 2 ports detected
[    3.572168] libata version 3.00 loaded.
[    3.772549] uhci_hcd 0000:00:11.3: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    3.772571] uhci_hcd 0000:00:11.3: UHCI Host Controller
[    3.772609] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[    3.772644] uhci_hcd 0000:00:11.3: irq 21, io base 0x0000e400
[    3.772806] usb usb2: configuration #1 chosen from 1 choice
[    3.772844] hub 2-0:1.0: USB hub found
[    3.772865] hub 2-0:1.0: 2 ports detected
[    3.984449] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 23
[    3.984455] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 23
[    3.984469] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
[    3.984566] pata_acpi 0000:00:11.1: PCI INT A disabled
[    3.988703] pata_via 0000:00:11.1: version 0.3.3
[    3.988737] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
[    3.990096] scsi0 : pata_via
[    3.990387] scsi1 : pata_via
[    3.993838] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xdc00 irq 14
[    3.993844] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xdc08 irq 15
[    4.157436] ata1.00: ATA-5: WDC WD1200BB-53CAA0, 16.06V16, max UDMA/100
[    4.157444] ata1.00: 234441648 sectors, multi 16: LBA
[    4.173261] ata1.00: configured for UDMA/100
[    4.568441] ata2.00: ATAPI: HL-DT-ST GCE-8400B, 1.06, max MWDMA2
[    4.568472] ata2.01: ATAPI: LITEON  DVD-ROM LTD163, GKS3, max UDMA/33
[    4.584343] ata2.00: configured for MWDMA2
[    4.592319] ata2.01: configured for UDMA/33
[    4.592548] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BB-53C 16.0 PQ: 0 ANSI: 5
[    4.592936] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8400B  1.06 PQ: 0 ANSI: 5
[    4.593272] scsi 1:0:1:0: CD-ROM            LITEON   DVD-ROM LTD163   GKS3 PQ: 0 ANSI: 5
[    4.825868] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.825931] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.825986] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    4.875206] Driver 'sd' needs updating - please use bus_type methods
[    4.875433] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.875459] sd 0:0:0:0: [sda] Write Protect is off
[    4.875463] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.875498] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.875606] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.875626] sd 0:0:0:0: [sda] Write Protect is off
[    4.875629] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.875661] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.875668]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.889323]  sda1 sda2 < sda5 >
[    4.909696] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.921854] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.921864] Uniform CD-ROM driver Revision: 3.20
[    4.922063] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.923625] sr1: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[    4.923746] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.246495] PM: Starting manual resume from disk
[    5.246505] PM: Resume from partition 8:5
[    5.246507] PM: Checking hibernation image.
[    5.246776] PM: Resume from disk failed.
[    5.313368] kjournald starting.  Commit interval 5 seconds
[    5.313401] EXT3-fs: mounted filesystem with ordered data mode.
[   11.838091] udevd version 124 started
[   12.632652] Linux agpgart interface v0.103
[   12.704318] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.766274] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.829030] agpgart: Detected VIA PM266/KM266 chipset
[   12.835273] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
[   13.004330] irda_init()
[   13.004366] NET: Registered protocol family 23
[   13.220449] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.232062] ACPI: Power Button (FF) [PWRF]
[   13.232317] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   13.248045] ACPI: Power Button (CM) [PWRB]
[   13.248305] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.264072] ACPI: Sleep Button (CM) [SLPB]
[   14.104447] parport_pc 00:09: reported by Plug and Play ACPI
[   14.104516] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   15.145475] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   15.620994] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   15.621001] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   15.621015] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   15.621172] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   15.874107] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   18.813019] lp0: using parport0 (interrupt-driven).
[   19.029823] Adding 1405648k swap on /dev/sda5.  Priority:-1 extents:1 across:1405648k
[   19.634917] EXT3 FS on sda1, internal journal
[   20.862155] type=1505 audit(1235365588.229:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3770
[   21.176599] type=1505 audit(1235365588.545:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3775
[   21.177190] type=1505 audit(1235365588.545:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3775
[   21.381462] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.344593] ACPI: WMI: Mapper loaded
[   23.640605] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.727953] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   23.727964] apm: overridden by ACPI.
[   23.901460] ppdev: user-space parallel port driver
[   25.936867] Bluetooth: Core ver 2.13
[   25.940124] NET: Registered protocol family 31
[   25.940133] Bluetooth: HCI device and connection manager initialized
[   25.940139] Bluetooth: HCI socket layer initialized
[   25.977272] Bluetooth: L2CAP ver 2.11
[   25.977282] Bluetooth: L2CAP socket layer initialized
[   26.024513] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.024523] Bluetooth: BNEP filters: protocol multicast
[   26.069543] Bluetooth: RFCOMM socket layer initialized
[   26.071088] Bluetooth: RFCOMM TTY layer initialized
[   26.071101] Bluetooth: RFCOMM ver 1.10
[   26.098368] Bridge firewalling registered
[   26.126112] Bluetooth: SCO (Voice Link) ver 0.6
[   26.126122] Bluetooth: SCO socket layer initialized
[   28.068666] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[   29.833179] [drm] Initialized drm 1.1.0 20060810
[   29.915913] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.917378] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   29.918831] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[   29.919529] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   29.919555] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[   29.919602] pci 0000:01:00.0: putting AGP V2 device into 0x mode
[   30.252746] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   30.532308] NET: Registered protocol family 17
[   35.700307] NET: Registered protocol family 10
[   35.701910] lo: Disabled Privacy Extensions
[   45.888038] eth0: no IPv6 routers present
[  119.424281] ppdev0: registered pardevice
[  119.472080] ppdev0: unregistered pardevice
[  119.620483] ppdev0: registered pardevice
[  119.668744] ppdev0: unregistered pardevice
[  121.562881] ppdev0: registered pardevice
[  121.612448] ppdev0: unregistered pardevice
[  127.310313] eth0: link down
[  128.953949] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  139.024764] eth0: link down
[  140.690814] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  163.064808] eth0: link down
[  164.688493] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  174.216555] eth0: link down
[  175.848992] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  185.503912] eth0: link down
[  187.114290] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  216.498726] eth0: link down
[  218.185539] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  235.834127] eth0: link down
[  237.467556] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  278.268278] eth0: link down
[  280.013669] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  289.313888] eth0: link down
[  290.964595] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  327.936867] eth0: link down
[  329.580958] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1355.528505] eth0: link down
[ 1357.174106] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1783.325680] eth0: link down
[ 1785.018954] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1926.312896] eth0: link down
[ 1927.966950] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2518.339440] eth0: link down
[ 2520.082545] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2863.045303] eth0: link down
[ 2864.728411] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

```

---

### Post by pytheas22 on 2009-02-23
> I got this out of the dmesg. It looks relevant.
[ 3.312214] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 3.312255] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[ 3.312262] 8139cp 0000:00:0b.0: Try the "8139too" driver instead.
[ 3.332288] 8139too Fast Ethernet driver 0.9.28
[ 3.332363] 8139too 0000:00:0b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 3.333026] eth0: RealTek RTL8139 at 0xd800, 00:40:ca:2e:e4:5e, IRQ 18
[ 3.333030] eth0: Identified 8139 chip type 'RTL-8100B/8139D'

Unfortunately that's all normal stuff; nothing useful there.
> 
I google'd the results of lspci -nn, but my reading comprehension is weak.

I couldn't find much, but I found [this page]("https://answers.launchpad.net/ubuntu/+question/9543")--see in particular the third post there.  Someone with the same NIC mentions it not working at all originally (not exactly your problem, but similar), but after changing some boot options and loading the 8139too module with a special option, it worked.  Could you give that a try and post the results?  You could also see if blacklisting 8139cp makes a difference, although I doubt it.

If you don't know how to change boot options or load 8139too with the arguments needed, I'll provide instructions.  But I won't be back till tomorrow.

---

### Post by camerazn on 2009-02-23
I added pci=noacpi and acpi=force to the boot options per [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto), 
and I added 
```
options 8139too media=0x01
```
to /etc/modprobe.d/options, based roughly on this thread: [http://ubuntuforums.org/showthread.php?t=85581](http://ubuntuforums.org/showthread.php?t=85581)

The eth0 connection still drops out. I'm fairly sure I did something of the above incorrectly, but I think I'll just drop $15 on a new network adapter so I can get this machine back to my client.

---

### Post by pytheas22 on 2009-02-23
As far as I can tell, you made the changes correctly, so I'm sorry it's still not working.  At this point, it might be worth it to buy another cheap NIC; it's definitely possible that the current one is just dying.  You could try other Linuxes or install Windows to know for sure whether this is a software or hardware problem, but the time involved in that is probably not worth $15...

---

### Post by camerazn on 2009-02-23
I bought a cheapo Dlink NIC today, and it works like a champ. Thanks for all your help; I really learned a few things.

---

