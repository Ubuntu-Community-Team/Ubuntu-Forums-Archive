---
title: "How i can connect to the internet using Huawei ETS 2552 in jaunty"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by Abbas_Anjum on 2009-06-12
[SIZE=2]Aslam o Alaikum
i am new to jaunty and i want to connect to internet i have Huawei ETS 2552 wireless modem (simple usb modem i.e usb on both end)
ubuntu jaunty has detected this modem and ttyUSB0 is created. Now what i have to do in order to connect to the internet
My internet configurations are
provider name: ptcl
username: [email]vwireless@ptcl.com[/email]
password: ptcl
I have tried to download wvdial but ubuntu donot install it and gives me dependencies error.
i donot know how to add the information in jaunty's default internetconnection manager.
Please help me i will be thankful to you.
i also tried network-admin tool. it connects to the internet.but the firefox gives me error and donot open any website and says that... BE sure are you are connected to internet? while the phone is displaying(....kbs sent and ....kbs recieved) that i am connected to the internet at the same time when firefox gives me such error.
please tell me what i have to do now or how to add the information in jaunty's internet connection manager if needed....
My dmesg file is:
[ 0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[ 0.000000] KERNEL supported cpus:
[ 0.000000] Intel GenuineIntel
[ 0.000000] AMD AuthenticAMD
[ 0.000000] NSC Geode by NSC
[ 0.000000] Cyrix CyrixInstead
[ 0.000000] Centaur CentaurHauls
[ 0.000000] Transmeta GenuineTMx86
[ 0.000000] Transmeta TransmetaCPU
[ 0.000000] UMC UMC UMC UMC
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 0000000027740000 (usable)
[ 0.000000] BIOS-e820: 0000000027740000 - 0000000027750000 (ACPI data)
[ 0.000000] BIOS-e820: 0000000027750000 - 0000000027800000 (ACPI NVS)
[ 0.000000] DMI 2.3 present.
[ 0.000000] last_pfn = 0x27740 max_arch_pfn = 0x100000
[ 0.000000] Scanning 2 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000002000 (usable)
[ 0.000000] modified: 0000000000002000 - 0000000000006000 (reserved)
[ 0.000000] modified: 0000000000006000 - 0000000000007000 (usable)
[ 0.000000] modified: 0000000000007000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 0000000000092c00 (usable)
[ 0.000000] modified: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] modified: 00000000000e0000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 0000000027740000 (usable)
[ 0.000000] modified: 0000000027740000 - 0000000027750000 (ACPI data)
[ 0.000000] modified: 0000000027750000 - 0000000027800000 (ACPI NVS)
[ 0.000000] kernel direct mapping tables up to 27740000 @ 10000-16000
[ 0.000000] RAMDISK: 26ffd000 - 2772f89d
[ 0.000000] ACPI: RSDP 000F6F20, 0014 (r0 ACPIAM)
[ 0.000000] ACPI: RSDT 27740000, 002C (r1 INTEL D845GVFN 20040907 MSFT 97)
[ 0.000000] ACPI: FACP 27740200, 0074 (r1 INTEL D845GVFN 20040907 MSFT 97)
[ 0.000000] ACPI: DSDT 27740370, 3FBF (r1 INTEL D845GVFN 10A MSFT 100000D)
[ 0.000000] ACPI: FACS 27750000, 0040
[ 0.000000] ACPI: APIC 27740300, 0068 (r1 INTEL D845GVFN 20040907 MSFT 97)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 631MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 27740000
[ 0.000000] low ram: 00000000 - 27740000
[ 0.000000] bootmap 00012000 - 00016ee8
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 0027740000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 000087c52c] TEXT DATA BSS ==> [0000100000 - 000087c52c]
[ 0.000000] #4 [0026ffd000 - 002772f89d] RAMDISK ==> [0026ffd000 - 002772f89d]
[ 0.000000] #5 [000087d000 - 0000881000] INIT_PG_TABLE ==> [000087d000 - 0000881000]
[ 0.000000] #6 [000009fc00 - 0000100000] BIOS reserved ==> [000009fc00 - 0000100000]
[ 0.000000] #7 [0000010000 - 0000012000] PGTABLE ==> [0000010000 - 0000012000]
[ 0.000000] #8 [0000012000 - 0000017000] BOOTMAP ==> [0000012000 - 0000017000]
[ 0.000000] found SMP MP-table at [c00ff780] 000ff780
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000000 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x00027740
[ 0.000000] HighMem 0x00027740 -> 0x00027740
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[4] active PFN ranges
[ 0.000000] 0: 0x00000000 -> 0x00000002
[ 0.000000] 0: 0x00000006 -> 0x00000007
[ 0.000000] 0: 0x00000010 -> 0x00000092
[ 0.000000] 0: 0x00000100 -> 0x00027740
[ 0.000000] On node 0 totalpages: 161477
[ 0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3941 pages, LIFO batch:0
[ 0.000000] Normal zone: 1231 pages used for memmap
[ 0.000000] Normal zone: 156273 pages, LIFO batch:31
[ 0.000000] HighMem zone: 0 pages used for memmap
[ 0.000000] Movable zone: 0 pages used for memmap
[ 0.000000] ACPI: PM-Timer IO Port: 0x408
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[ 0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[ 0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[ 0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[ 0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 30000000 (gap: 27800000:d8800000)
[ 0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[ 0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 160214
[ 0.000000] Kernel command line: root=UUID=184e1393-cc43-4591-92d0-740c2782d2e6 ro quiet splash usbserial.vendor=0x12d1 usbserial.product=0x1010
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] TSC: PIT calibration matches PMTIMER. 2 loops
[ 0.000000] Detected 2266.566 MHz processor.
[ 0.004000] Console: colour VGA+ 80x25
[ 0.004000] console [tty0] enabled
[ 0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.004000] allocated 3232000 bytes of page_cgroup
[ 0.004000] please try cgroup_disable=memory option if you don't want
[ 0.004000] Scanning for low memory corruption every 60 seconds
[ 0.004000] Memory: 621416k/646400k available (4126k kernel code, 24204k reserved, 2208k data, 532k init, 0k highmem)
[ 0.004000] virtual kernel memory layout:
[ 0.004000] fixmap : 0xffc77000 - 0xfffff000 (3616 kB)
[ 0.004000] pkmap : 0xff400000 - 0xff800000 (4096 kB)
[ 0.004000] vmalloc : 0xe7f40000 - 0xff3fe000 ( 372 MB)
[ 0.004000] lowmem : 0xc0000000 - 0xe7740000 ( 631 MB)
[ 0.004000] .init : 0xc0737000 - 0xc07bc000 ( 532 kB)
[ 0.004000] .data : 0xc0507a6f - 0xc072fe60 (2208 kB)
[ 0.004000] .text : 0xc0100000 - 0xc0507a6f (4126 kB)
[ 0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[ 0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 4533.13 BogoMIPS (lpj=9066264)
[ 0.004044] Security Framework initialized
[ 0.004053] SELinux: Disabled at boot.
[ 0.004079] AppArmor: AppArmor initialized
[ 0.004095] Mount-cache hash table entries: 512
[ 0.004315] Initializing cgroup subsys ns
[ 0.004323] Initializing cgroup subsys cpuacct
[ 0.004327] Initializing cgroup subsys memory
[ 0.004334] Initializing cgroup subsys freezer
[ 0.004361] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 0.004367] CPU: L2 cache: 256K
[ 0.004372] CPU: Hyper-Threading is disabled
[ 0.004378] using mwait in idle threads.
[ 0.004397] Checking 'hlt' instruction... OK.
[ 0.021144] SMP alternatives: switching to UP code
[ 0.192045] ACPI: Core revision 20080926
[ 0.197025] ACPI: Checking initramfs for custom DSDT
[ 0.576629] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.616331] CPU0: Intel(R) Celeron(R) CPU 2.26GHz stepping 01
[ 0.620002] Brought up 1 CPUs
[ 0.620002] Total of 1 processors activated (4533.13 BogoMIPS).
[ 0.620002] CPU0 attaching NULL sched-domain.
[ 0.620002] net_namespace: 776 bytes
[ 0.620002] Booting paravirtualized kernel on bare hardware
[ 0.620002] Time: 17:05:26 Date: 06/12/09
[ 0.620002] regulator: core version 0.5
[ 0.620002] NET: Registered protocol family 16
[ 0.620002] EISA bus registered
[ 0.620002] ACPI: bus type pci registered
[ 0.620002] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[ 0.620002] PCI: Using configuration type 1 for base access
[ 0.621011] ACPI: EC: Look up EC in DSDT
[ 0.630071] ACPI: Interpreter enabled
[ 0.630082] ACPI: (supports S0 S1 S4 S5)
[ 0.630113] ACPI: Using IOAPIC for interrupt routing
[ 0.639232] ACPI: No dock devices found.
[ 0.639256] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.639335] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[ 0.639413] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[ 0.639421] pci 0000:00:02.0: reg 14 32bit mmio: [0xffa80000-0xffafffff]
[ 0.639539] pci 0000:00:1d.0: reg 20 io port: [0xe800-0xe81f]
[ 0.639599] pci 0000:00:1d.1: reg 20 io port: [0xe880-0xe89f]
[ 0.639659] pci 0000:00:1d.2: reg 20 io port: [0xec00-0xec1f]
[ 0.639729] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa7fc00-0xffa7ffff]
[ 0.639780] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.639787] pci 0000:00:1d.7: PME# disabled
[ 0.639847] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[ 0.639849] * this clock source is slow. If you are sure your timer does not have
[ 0.639850] * this bug, please use "acpi_pm_good" to disable the workaround
[ 0.639897] HPET not enabled in BIOS. You might try hpet=force boot option
[ 0.639906] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[ 0.639911] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[ 0.639936] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[ 0.639945] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[ 0.639953] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[ 0.639961] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[ 0.639970] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[ 0.639978] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[ 0.640067] pci 0000:00:1f.3: reg 20 io port: [0xe000-0xe01f]
[ 0.640118] pci 0000:00:1f.5: reg 10 io port: [0xe400-0xe4ff]
[ 0.640126] pci 0000:00:1f.5: reg 14 io port: [0xe080-0xe0bf]
[ 0.640134] pci 0000:00:1f.5: reg 18 32bit mmio: [0xffa7f800-0xffa7f9ff]
[ 0.640142] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xffa7f400-0xffa7f4ff]
[ 0.640169] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[ 0.640175] pci 0000:00:1f.5: PME# disabled
[ 0.640236] pci 0000:00:1e.0: transparent bridge
[ 0.640242] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[ 0.640248] pci 0000:00:1e.0: bridge 32bit mmio: [0xff800000-0xff8fffff]
[ 0.640255] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xcea00000-0xceafffff]
[ 0.640267] bus 00 -> node 0
[ 0.640278] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.640519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[ 0.642465] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[ 0.642723] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[ 0.642969] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[ 0.643215] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[ 0.643461] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 0.643710] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 0.643957] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[ 0.644242] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[ 0.644432] ACPI: Power Resource [URP1] (off)
[ 0.644492] ACPI: Power Resource [FDDP] (off)
[ 0.644550] ACPI: Power Resource [LPTP] (off)
[ 0.644691] ACPI: WMI: Mapper loaded
[ 0.645072] SCSI subsystem initialized
[ 0.645163] libata version 3.00 loaded.
[ 0.645255] usbcore: registered new interface driver usbfs
[ 0.645293] usbcore: registered new interface driver hub
[ 0.645354] usbcore: registered new device driver usb
[ 0.645573] PCI: Using ACPI for IRQ routing
[ 0.645715] Bluetooth: Core ver 2.13
[ 0.645715] NET: Registered protocol family 31
[ 0.645715] Bluetooth: HCI device and connection manager initialized
[ 0.645715] Bluetooth: HCI socket layer initialized
[ 0.645715] NET: Registered protocol family 8
[ 0.645715] NET: Registered protocol family 20
[ 0.645715] NetLabel: Initializing
[ 0.645715] NetLabel: domain hash size = 128
[ 0.645715] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.645715] NetLabel: unlabeled traffic allowed by default
[ 0.645715] AppArmor: AppArmor Filesystem Enabled
[ 0.645715] pnp: PnP ACPI init
[ 0.645715] ACPI: bus type pnp registered
[ 0.652107] pnp: PnP ACPI: found 14 devices
[ 0.652113] ACPI: ACPI bus type pnp unregistered
[ 0.652120] PnPBIOS: Disabled by ACPI PNP
[ 0.652147] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[ 0.652161] system 00:0c: ioport range 0x400-0x47f has been reserved
[ 0.652165] system 00:0c: ioport range 0x680-0x6ff has been reserved
[ 0.652168] system 00:0c: ioport range 0x480-0x4bf has been reserved
[ 0.652173] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[ 0.652177] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[ 0.652186] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[ 0.652190] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[ 0.652194] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[ 0.652198] system 00:0d: iomem range 0x100000-0x277fffff could not be reserved
[ 0.687050] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[ 0.687056] pci 0000:00:1e.0: IO window: 0xd000-0xdfff
[ 0.687063] pci 0000:00:1e.0: MEM window: 0xff800000-0xff8fffff
[ 0.687069] pci 0000:00:1e.0: PREFETCH window: 0x000000cea00000-0x000000ceafffff
[ 0.687089] pci 0000:00:1e.0: setting latency timer to 64
[ 0.687095] bus: 00 index 0 io port: [0x00-0xffff]
[ 0.687098] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[ 0.687101] bus: 01 index 0 io port: [0xd000-0xdfff]
[ 0.687104] bus: 01 index 1 mmio: [0xff800000-0xff8fffff]
[ 0.687107] bus: 01 index 2 mmio: [0xcea00000-0xceafffff]
[ 0.687110] bus: 01 index 3 io port: [0x00-0xffff]
[ 0.687113] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[ 0.687132] NET: Registered protocol family 2
[ 0.687361] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.687891] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.689607] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.690525] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.690535] TCP reno registered
[ 0.690844] NET: Registered protocol family 1
[ 0.691069] checking if image is initramfs... it is
[ 1.188070] Switched to high resolution mode on CPU 0
[ 1.485842] Freeing initrd memory: 7370k freed
[ 1.486042] cpufreq: No nForce2 chipset.
[ 1.486270] audit: initializing netlink socket (disabled)
[ 1.486305] type=2000 audit(1244826327.484:1): initialized
[ 1.497083] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 1.498842] VFS: Disk quotas dquot_6.5.1
[ 1.498952] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1.500034] fuse init (API version 7.10)
[ 1.500190] msgmni has been set to 1228
[ 1.500534] alg: No test for stdrng (krng)
[ 1.500563] io scheduler noop registered
[ 1.500566] io scheduler anticipatory registered
[ 1.500569] io scheduler deadline registered
[ 1.500620] io scheduler cfq registered (default)
[ 1.500645] pci 0000:00:02.0: Boot video device
[ 1.504766] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1.504783] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 1.504986] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[ 1.504991] ACPI: Power Button (FF) [PWRF]
[ 1.505079] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[ 1.505089] ACPI: Sleep Button (CM) [SLPB]
[ 1.505357] processor ACPI_CPU:00: registered as cooling_device0
[ 1.505363] ACPI: Processor [CPU1] (supports 8 throttling states)
[ 1.507863] isapnp: Scanning for PnP cards...
[ 1.859614] isapnp: No Plug & Play device found
[ 1.861786] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[ 1.861909] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.862440] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.863778] brd: module loaded
[ 1.864406] loop: module loaded
[ 1.864592] Fixed MDIO Bus: probed
[ 1.864603] PPP generic driver version 2.4.2
[ 1.864705] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[ 1.864769] Driver 'sd' needs updating - please use bus_type methods
[ 1.864786] Driver 'sr' needs updating - please use bus_type methods
[ 1.864909] ata_piix 0000:00:1f.1: version 2.12
[ 1.864928] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[ 1.864949] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1.865025] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 1.865220] scsi0 : ata_piix
[ 1.865420] scsi1 : ata_piix
[ 1.867288] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[ 1.867293] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[ 2.084512] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
[ 2.084517] ata1.00: 156301488 sectors, multi 16: LBA48 
[ 2.084556] ata1.00: limited to UDMA/33 due to 40-wire cable
[ 2.100448] ata1.00: configured for UDMA/33
[ 2.264310] ata2.00: ATAPI: ASUS CD-S520/A5, 1.22, max UDMA/33
[ 2.280271] ata2.00: configured for UDMA/33
[ 2.280659] scsi 0:0:0:0: Direct-Access ATA ST380011A 8.01 PQ: 0 ANSI: 5
[ 2.280875] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2.280908] sd 0:0:0:0: [sda] Write Protect is off
[ 2.280912] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2.280959] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.281099] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2.281128] sd 0:0:0:0: [sda] Write Protect is off
[ 2.281132] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2.281180] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.281187] sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
[ 2.391602] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2.391708] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 2.392070] scsi 1:0:0:0: CD-ROM ASUS CD-S520/A5 1.22 PQ: 0 ANSI: 5
[ 2.395008] sr0: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
[ 2.395015] Uniform CD-ROM driver Revision: 3.20
[ 2.395211] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 2.395306] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 2.396230] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 2.396281] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[ 2.396321] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2.396327] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 2.396466] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 2.400404] ehci_hcd 0000:00:1d.7: debug port 1
[ 2.400413] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[ 2.400436] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa7fc00
[ 2.416014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 2.416136] usb usb1: configuration #1 chosen from 1 choice
[ 2.416181] hub 1-0:1.0: USB hub found
[ 2.416200] hub 1-0:1.0: 6 ports detected
[ 2.416401] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 2.416438] uhci_hcd: USB Universal Host Controller Interface driver
[ 2.416517] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2.416530] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2.416535] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 2.416630] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 2.416671] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800
[ 2.416819] usb usb2: configuration #1 chosen from 1 choice
[ 2.416863] hub 2-0:1.0: USB hub found
[ 2.416878] hub 2-0:1.0: 2 ports detected
[ 2.417027] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 2.417039] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2.417043] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 2.417138] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 2.417177] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e880
[ 2.417303] usb usb3: configuration #1 chosen from 1 choice
[ 2.417345] hub 3-0:1.0: USB hub found
[ 2.417358] hub 3-0:1.0: 2 ports detected
[ 2.417507] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 2.417518] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2.417522] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 2.417604] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 2.417643] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[ 2.417773] usb usb4: configuration #1 chosen from 1 choice
[ 2.417830] hub 4-0:1.0: USB hub found
[ 2.417847] hub 4-0:1.0: 2 ports detected
[ 2.418050] usbcore: registered new interface driver libusual
[ 2.418112] usbcore: registered new interface driver usbserial
[ 2.418138] USB Serial support registered for generic
[ 2.418162] usbcore: registered new interface driver usbserial_generic
[ 2.418166] usbserial: USB Serial Driver core
[ 2.418246] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[ 2.421142] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 2.421153] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 2.421396] mice: PS/2 mouse device common for all mice
[ 2.421626] rtc_cmos 00:02: RTC can wake from S4
[ 2.421700] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[ 2.421731] rtc0: alarms up to one month, 114 bytes nvram
[ 2.421870] device-mapper: uevent: version 1.0.3
[ 2.422131] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[ 2.422249] device-mapper: multipath: version 1.0.5 loaded
[ 2.422256] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 2.422446] EISA: Probing bus 0 at eisa.0
[ 2.422491] EISA: Detected 0 cards.
[ 2.422561] cpuidle: using governor ladder
[ 2.422566] cpuidle: using governor menu
[ 2.423347] TCP cubic registered
[ 2.423480] NET: Registered protocol family 10
[ 2.424163] lo: Disabled Privacy Extensions
[ 2.424653] NET: Registered protocol family 17
[ 2.424702] Bluetooth: L2CAP ver 2.11
[ 2.424705] Bluetooth: L2CAP socket layer initialized
[ 2.424709] Bluetooth: SCO (Voice Link) ver 0.6
[ 2.424711] Bluetooth: SCO socket layer initialized
[ 2.424799] Bluetooth: RFCOMM socket layer initialized
[ 2.424821] Bluetooth: RFCOMM TTY layer initialized
[ 2.424825] Bluetooth: RFCOMM ver 1.10
[ 2.424932] Using IPI No-Shortcut mode
[ 2.425112] registered taskstats version 1
[ 2.425244] Magic number: 13:217:87
[ 2.425319] button LNXPWRBN:00: hash matches
[ 2.425356] rtc_cmos 00:02: setting system clock to 2009-06-12 17:05:28 UTC (1244826328)
[ 2.425360] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 2.425363] EDD information not available.
[ 2.426297] Freeing unused kernel memory: 532k freed
[ 2.426468] Write protecting the kernel text: 4128k
[ 2.426521] Write protecting the kernel read-only data: 1532k
[ 2.462733] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[ 3.109880] Floppy drive(s): fd0 is 1.44M
[ 3.127816] FDC 0 is a post-1991 82077
[ 4.613097] PM: Starting manual resume from disk
[ 4.613104] PM: Resume from partition 8:11
[ 4.613106] PM: Checking hibernation image.
[ 4.613480] PM: Resume from disk failed.
[ 4.634661] kjournald starting. Commit interval 5 seconds
[ 4.634687] EXT3-fs: mounted filesystem with ordered data mode.
[ 9.930307] udev: starting version 141
[ 10.199983] parport_pc 00:09: reported by Plug and Play ACPI
[ 10.200046] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[ 10.218432] Linux agpgart interface v0.103
[ 10.227657] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[ 10.227926] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[ 10.230217] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[ 10.282535] intel_rng: Firmware space is locked read-only. If you can't or
[ 10.282539] intel_rng: don't want to disable this in firmware setup, and if
[ 10.282541] intel_rng: you are certain that your system has a functional
[ 10.282542] intel_rng: RNG, try using the 'no_fwh_detect' option.
[ 10.309576] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 10.460955] iTCO_vendor_support: vendor-support=0
[ 10.596102] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[ 10.596390] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[ 10.596556] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 10.649306] input: PC Speaker as /devices/platform/pcspkr/input/input4
[ 10.844108] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 11.196991] ppdev: user-space parallel port driver
[ 11.294918] psmouse serio1: ID: 10 00 64<6>Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 11.611156] Intel ICH 0000:00:1f.5: setting latency timer to 64
[ 11.806192] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[ 11.932024] intel8x0_measure_ac97_clock: measured 54948 usecs
[ 11.932030] intel8x0: clocking to 48000
[ 12.147511] lp0: using parport0 (interrupt-driven).
[ 12.314291] Adding 345356k swap on /dev/sda11. Priority:-1 extents:1 across:345356k
[ 12.895626] EXT3 FS on sda10, internal journal
[ 14.229468] type=1505 audit(1244804740.302:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1862
[ 14.308379] type=1505 audit(1244804740.382:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1866
[ 14.308715] type=1505 audit(1244804740.382:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1866
[ 14.308858] type=1505 audit(1244804740.382:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1866
[ 14.308951] type=1505 audit(1244804740.382:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1866
[ 14.526191] type=1505 audit(1244804740.598:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1871
[ 14.526654] type=1505 audit(1244804740.598:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1871
[ 14.576567] type=1505 audit(1244804740.650:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1875
[ 19.246801] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 19.246808] Bluetooth: BNEP filters: protocol multicast
[ 19.295178] Bridge firewalling registered
[ 21.171231] [drm] Initialized drm 1.1.0 20060810
[ 21.192738] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 21.192748] pci 0000:00:02.0: setting latency timer to 64
[ 21.193045] [drm] Initialized i915 1.6.0 20080730 on minor 0
[ 21.354913] [drm:i915_setparam] *ERROR* unknown parameter 4
[ 21.354970] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 21.906632] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 76.096024] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 76.358883] usb 3-2: configuration #1 chosen from 1 choice
[ 76.361223] usbserial_generic 3-2:1.0: generic converter detected
[ 76.361361] usb 3-2: generic converter now attached to ttyUSB0
[ 76.395346] usbserial_generic 3-2:1.1: generic converter detected
[ 76.395451] usb 3-2: generic converter now attached to ttyUSB1
 
i hope so you will solve my problem...
please help
[/SIZE]

---

