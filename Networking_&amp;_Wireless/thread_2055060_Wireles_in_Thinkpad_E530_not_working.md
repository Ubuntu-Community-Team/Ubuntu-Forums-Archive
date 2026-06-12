---
title: "Wireles in Thinkpad E530 not working"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by svratonzo123 on 2012-09-08
Hi
my laptop Thinkpad E530 with integrated Bluetooth and Wirelees have Xubuntu 12.04

Wireless is not working.
This is lspci, someone could help me?

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
0c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)


Thank you

---

### Post by chili555 on 2012-09-08
Let's have a look at:```
rfkill list all
dmesg | grep iwl
```Thanks.

---

### Post by necs on 2012-09-08
> **chili555 said:**
> Let's have a look at:```
rfkill list all
dmesg | grep iwl
```Thanks.

 root@bt:~# dmesg   root@bt:~# dmesg [    0.000000] Initializing cgroup subsys cpuset  [    0.000000] Initializing cgroup subsys cpu  [    0.000000] Linux version 3.2.6 (root@bt) (gcc version 4.4.3 (Ubuntu  4.4.3-4ubuntu5) ) #1 SMP Fri Feb 17 10:40:05 EST 2012  [    0.000000] KERNEL supported cpus:  [    0.000000]   Intel GenuineIntel  [    0.000000]   AMD AuthenticAMD  [    0.000000]   NSC Geode by NSC  [    0.000000]   Cyrix CyrixInstead  [    0.000000]   Centaur CentaurHauls  [    0.000000]   Transmeta GenuineTMx86  [    0.000000]   Transmeta TransmetaCPU  [    0.000000]   UMC UMC UMC UMC  [    0.000000] BIOS-provided physical RAM map:  [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)  [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)  [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)  [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)  [    0.000000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (ACPI data)  [    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)  [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!  [    0.000000] DMI 2.5 present.  [    0.000000] DMI: innotek GmbH VirtualBox, BIOS VirtualBox 12/01/2006  [    0.000000] e820 update range: 0000000000000000 - 0000000000010000   (usable) ==> (reserved)  [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000  (usable)  [    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000  [    0.000000] MTRR default type: uncachable  [    0.000000] MTRR variable ranges disabled:  [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new  0x7010600070106  [    0.000000] CPU MTRRs all blank - virtualized system.   [    0.000000] initial memory mapped : 0 - 01c00000  [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384  [    0.000000] init_memory_mapping: 0000000000000000-000000001fff0000  [    0.000000]  0000000000 - 0000400000 page 4k  [    0.000000]  0000400000 - 001fc00000 page 2M  [    0.000000]  001fc00000 - 001fff0000 page 4k  [    0.000000] kernel direct mapping tables up to 1fff0000 @  1bfb000-1c00000  [    0.000000] RAMDISK: 1ef0f000 - 1ffc0000  [    0.000000] ACPI: RSDP 000e0000 00024 (v02 VBOX  )  [    0.000000] ACPI: XSDT 1fff0030 00034 (v01 VBOX   VBOXXSDT 00000001  ASL  00000061)  [    0.000000] ACPI: FACP 1fff00f0 000F4 (v04 VBOX   VBOXFACP 00000001  ASL  00000061)  [    0.000000] ACPI: DSDT 1fff0410 01B96 (v01 VBOX   VBOXBIOS 00000002  INTL 20100528)  [    0.000000] ACPI: FACS 1fff0200 00040  [    0.000000] ACPI: SSDT 1fff0240 001CC (v01 VBOX   VBOXCPUT 00000002  INTL 20100528)  [    0.000000] 0MB HIGHMEM available.  [    0.000000] 511MB LOWMEM available.  [    0.000000]   mapped low ram: 0 - 1fff0000  [    0.000000]   low ram: 0 - 1fff0000  [    0.000000] Zone PFN ranges:  [    0.000000]   DMA      0x00000010 -> 0x00001000  [    0.000000]   Normal   0x00001000 -> 0x0001fff0  [    0.000000]   HighMem  empty  [    0.000000] Movable zone start PFN for each node  [    0.000000] early_node_map[2] active PFN ranges  [    0.000000]     0: 0x00000010 -> 0x0000009f  [    0.000000]     0: 0x00000100 -> 0x0001fff0  [    0.000000] On node 0 totalpages: 130943  [    0.000000] free_area_init_node: node 0, pgdat c17cf880, node_mem_map  deb0f200   [    0.000000]   DMA zone: 32 pages used for memmap  [    0.000000]   DMA zone: 0 pages reserved  [    0.000000]   DMA zone: 3951 pages, LIFO batch:0   [    0.000000]   Normal zone: 992 pages used for memmap  [    0.000000]   Normal zone: 125968 pages, LIFO batch:31  [    0.000000] Using APIC driver default  [    0.000000] ACPI: PM-Timer IO Port: 0x4008  [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs  [    0.000000] Found and enabled local APIC!  [    0.000000] nr_irqs_gsi: 16  [    0.000000] PM: Registered nosave memory: 000000000009f000 -  00000000000a0000  [    0.000000] PM: Registered nosave memory: 00000000000a0000 -  00000000000f0000  [    0.000000] PM: Registered nosave memory: 00000000000f0000 -  0000000000100000   [    0.000000] Allocating PCI resources starting at 20000000 (gap:  20000000:dffc0000)  [    0.000000] Booting paravirtualized kernel on bare hardware  [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1  nr_node_ids:1  [    0.000000] PERCPU: Embedded 13 pages/cpu @de400000 s31616 r0 d21632  u4194304  [    0.000000] pcpu-alloc: s31616 r0 d21632 u4194304 alloc=1*4194304  [    0.000000] pcpu-alloc: [0] 0   [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.   Total pages: 129919  [    0.000000] Kernel command line: file=/cdrom/preseed/custom.seed  boot=casper initrd=/casper/initrd.gz text splash vga=791--  BOOT_IMAGE=/casper/vmlinuz   [    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)  [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144  bytes)  [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072  bytes)  [    0.000000] Initializing CPU#0  [    0.000000] allocated 2096640 bytes of page_cgroup  [    0.000000] please try 'cgroup_disable=memory' option if you don't  want memory cgroups  [    0.000000] Initializing HighMem for node 0 (00000000:00000000)  [    0.000000] Memory: 490380k/524224k available (5505k kernel code,  33392k reserved, 2533k data, 704k init, 0k highmem)  [    0.000000] virtual kernel memory layout:  [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)  [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)  [    0.000000]     vmalloc : 0xe07f0000 - 0xff7fe000   ( 496 MB)  [    0.000000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)  [    0.000000]       .init : 0xc17da000 - 0xc188a000   ( 704 kB)  [    0.000000]       .data : 0xc15606d9 - 0xc17d9ec0   (2533 kB)  [    0.000000]       .text : 0xc1000000 - 0xc15606d9   (5505 kB)  [    0.000000] Checking if this processor honours the WP bit even in   supervisor mode...Ok.  [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0,   CPUs=1, Nodes=1  [    0.000000] Hierarchical RCU implementation.  [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.  [    0.000000] NR_IRQS:2304 nr_irqs:256 16  [    0.000000] CPU 0 irqstacks, hard=de008000 soft=de00a000  [    0.000000] Console: colour dummy device 80x25  [    0.000000] console [tty0] enabled  [    0.000000] Fast TSC calibration failed  [    0.000000] TSC: Unable to calibrate against PIT  [    0.000000] TSC: using PMTIMER reference calibration  [    0.000000] Detected 2552.626 MHz processor.  [    0.032225] Calibrating delay loop (skipped), value calculated using  timer frequency.. 5105.25 BogoMIPS (lpj=10210504)  [    0.032774] pid_max: default: 32768 minimum: 301  [    0.033308] Security Framework initialized  [    0.034402] AppArmor: AppArmor initialized  [    0.034800] Mount-cache hash table entries: 512  [    0.041699] Initializing cgroup subsys cpuacct  [    0.042005] Initializing cgroup subsys memory  [    0.042355] Initializing cgroup subsys devices  [    0.042450] Initializing cgroup subsys freezer  [    0.042567] Initializing cgroup subsys net_cls  [    0.042737] Initializing cgroup subsys blkio  [    0.043205] Initializing cgroup subsys perf_event  [    0.043825] mce: CPU supports 0 MCE banks  [    0.044240] using mwait in idle threads.  [    0.049575] SMP alternatives: switching to UP code  [    0.600036] Freeing SMP alternatives: 24k freed  [    0.600639] ACPI: Core revision 20110623  [    0.609272] ACPI: setting ELCR to 0200 (from 0e20)  [    0.609990] ftrace: allocating 22920 entries in 45 pages  [    0.673845] weird, boot CPU (#0) not listed by the BIOS.  [    0.676510] SMP motherboard not detected.  [    0.676747] Enabling APIC mode:  Flat.  Using 0 I/O APICs  [    0.680041] SMP disabled  [    0.680041] Performance Events: unsupported p6 CPU model 23 no PMU  driver, software events only.  [    0.720424] NMI watchdog disabled (cpu0): hardware events not enabled  [    0.721042] Brought up 1 CPUs  [    0.721527] Total of 1 processors activated (5105.25 BogoMIPS).  [    0.737162] devtmpfs: initialized  [    0.737843] EVM: security.selinux  [    0.737929] EVM: security.SMACK64  [    0.738041] EVM: security.capability  [    0.745974] print_constraints: dummy:   [    0.752245] NET: Registered protocol family 16  [    0.755803] EISA bus registered  [    0.756463] ACPI: bus type pci registered  [    0.854583] PCI: PCI BIOS revision 2.10 entry at 0xfc040, last bus=0  [    0.855328] PCI: Using configuration type 1 for base access  [    0.860875] bio: create slab  at 0  [    0.861727] ACPI: Added _OSI(Module Device)  [    0.861753] ACPI: Added _OSI(Processor Device)  [    0.861774] ACPI: Added _OSI(3.0 _SCP Extensions)  [    0.861797] ACPI: Added _OSI(Processor Aggregator Device)  [    0.866486] ACPI: EC: Look up EC in DSDT  [    0.869763] ACPI: Executed 1 blocks of module-level executable AML code  [    0.875661] ACPI: Interpreter enabled  [    0.875700] ACPI: (supports S0 S5)  [    0.875756] ACPI: Using PIC for interrupt routing  [    0.917881] ACPI: No dock devices found.  [    0.918199] HEST: Table not found.  [    0.918440] PCI: Ignoring host bridge windows from ACPI; if necessary,  use "pci=use_crs" and report a bug  [    0.924057] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])  [    0.925174] pci_root PNP0A03:00: host bridge window [io   0x0000-0x0cf7] (ignored)  [    0.925309] pci_root PNP0A03:00: host bridge window [io   0x0d00-0xffff] (ignored)  [    0.925413] pci_root PNP0A03:00: host bridge window [mem  0x000a0000-0x000bffff] (ignored)   [    0.925494] pci_root PNP0A03:00: host bridge window [mem  0x20000000-0xffdfffff] (ignored)  [    0.928508] pci 0000:00:00.0: [8086:1237] type 0 class 0x000600   [    0.929640] pci 0000:00:01.0: [8086:7000] type 0 class 0x000601  [    0.930397] pci 0000:00:01.1: [8086:7111] type 0 class 0x000101  [    0.930940] pci 0000:00:01.1: reg 20: [io  0xd000-0xd00f]  [    0.931325] pci 0000:00:02.0: [80ee:beef] type 0 class 0x000300  [    0.932133] pci 0000:00:02.0: reg 10: [mem 0xe0000000-0xe0ffffff pref]  [    0.938257] pci 0000:00:03.0: [8086:100e] type 0 class 0x000200  [    0.938317] pci 0000:00:03.0: reg 10: [mem 0xf0000000-0xf001ffff]  [    0.938935] pci 0000:00:03.0: reg 18: [io  0xd010-0xd017]  [    0.940836] pci 0000:00:04.0: [80ee:cafe] type 0 class 0x000880  [    0.941296] pci 0000:00:04.0: reg 10: [io  0xd020-0xd03f]  [    0.942009] pci 0000:00:04.0: reg 14: [mem 0xf0400000-0xf07fffff]  [    0.942414] pci 0000:00:04.0: reg 18: [mem 0xf0800000-0xf0803fff pref]  [    0.943943] pci 0000:00:05.0: [8086:2415] type 0 class 0x000401  [    0.944199] pci 0000:00:05.0: reg 10: [io  0xd100-0xd1ff]  [    0.944302] pci 0000:00:05.0: reg 14: [io  0xd200-0xd23f]  [    0.944913] pci 0000:00:06.0: [106b:003f] type 0 class 0x000c03  [    0.945273] pci 0000:00:06.0: reg 10: [mem 0xf0804000-0xf0804fff]  [    0.947222] pci 0000:00:07.0: [8086:7113] type 0 class 0x000680  [    0.948380] pci 0000:00:0d.0: [8086:2829] type 0 class 0x000106  [    0.948805] pci 0000:00:0d.0: reg 10: [io  0xd240-0xd247]  [    0.949441] pci 0000:00:0d.0: reg 18: [io  0xd250-0xd257]  [    0.950109] pci 0000:00:0d.0: reg 20: [io  0xd260-0xd26f]  [    0.950447] pci 0000:00:0d.0: reg 24: [mem 0xf0806000-0xf0807fff]  [    0.951292] pci_bus 0000:00: on NUMA node 0  [    0.951346] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]  [    0.953470]  pci0000:00: Unable to request _OSC control (_OSC support  mask: 0x1e)  [    0.961081] ACPI: PCI Interrupt Link [LNKA] (IRQs *5 9 10 11)  [    0.961404] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 9 10 *11)  [    0.961578] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 9 *10 11)  [    0.961741] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *9 10 11)  [    0.964059] vgaarb: device added:  PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none  [    0.964161] vgaarb: loaded  [    0.964180] vgaarb: bridge control possible 0000:00:02.0  [    0.964964] i2c-core: driver [aat2870] using legacy suspend method  [    0.964990] i2c-core: driver [aat2870] using legacy resume method  [    0.965536] SCSI subsystem initialized  [    0.966210] libata version 3.00 loaded.   [    0.967380] usbcore: registered new interface driver usbfs  [    0.967420] usbcore: registered new interface driver hub  [    0.967772] usbcore: registered new device driver usb  [    0.972884] PCI: Using ACPI for IRQ routing   [    0.972975] PCI: pci_cache_line_size set to 64 bytes  [    0.973612] reserve RAM buffer: 000000000009fc00 - 000000000009ffff   [    0.973669] reserve RAM buffer: 000000001fff0000 - 000000001fffffff   [    0.976914] NetLabel: Initializing  [    0.976993] NetLabel:  domain hash size = 128  [    0.977051] NetLabel:  protocols = UNLABELED CIPSOv4  [    0.977146] NetLabel:  unlabeled traffic allowed by default  [    0.993401] AppArmor: AppArmor Filesystem Enabled [    0.993718] pnp: PnP ACPI init  [    0.993863] ACPI: bus type pnp registered  [    0.994327] pnp 00:00: [bus 00-ff]  \[    0.996278] pnp 00:00: [io  0x0cf8-0x0cff] [     0.996343] pnp 00:00: [io  0x0000-0x0cf7 window]  [    0.996400] pnp 00:00: [io  0x0d00-0xffff window]  [    0.996453] pnp 00:00: [mem 0x000a0000-0x000bffff window]  [    0.996503] pnp 00:00: [mem 0x20000000-0xffdfffff window]  [    0.996806] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)  [    0.996877] pnp 00:01: [io  0x0060]  [    0.996912] pnp 00:01: [io  0x0064]  [    0.996960] pnp 00:01: [irq 1]  [    0.997024] pnp 00:01: Plug and Play ACPI device, IDs PNP0303 (active)  [    0.997070] pnp 00:02: [io  0x0000-0x000f]  [    0.997097] pnp 00:02: [io  0x0080-0x008f]  [    0.997122] pnp 00:02: [io  0x00c0-0x00df]  [    0.997148] pnp 00:02: [dma 4]  [    0.997194] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)  [    0.997286] pnp 00:03: [irq 12]  [    0.997335] pnp 00:03: Plug and Play ACPI device, IDs PNP0f03 (active)  [    0.997387] pnp 00:04: [io  0x0378-0x037f]  [    0.997415] pnp 00:04: [io  0x0778-0x077f]  [    0.997433] pnp 00:04: [irq 7]  [    0.997486] pnp 00:04: Plug and Play ACPI device, IDs PNP0400 (active)  [    0.998244] pnp: PnP ACPI: found 5 devices  [    0.998266] ACPI: ACPI bus type pnp unregistered  [    0.998291] PnPBIOS: Disabled by ACPI PNP  [    1.046034] Switching to clocksource acpi_pm  [    1.047547] PCI: max bus depth: 0 pci_try_num: 1  [    1.047584] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]  [    1.047597] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]  [    1.047745] NET: Registered protocol family 2  [    1.047745] IP route cache hash table entries: 4096 (order: 2, 16384  bytes)  [    1.047960] TCP established hash table entries: 16384 (order: 5,  131072 bytes)  [    1.049030] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)  [    1.049135] TCP: Hash tables configured (established 16384 bind 16384)  [    1.049163] TCP reno registered  [    1.049182] UDP hash table entries: 256 (order: 1, 8192 bytes)  [    1.049214] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)  [    1.049319] NET: Registered protocol family 1  [    1.049393] pci 0000:00:00.0: Limiting direct PCI/PCI transfers  [    1.049468] pci 0000:00:01.0: Activating ISA DMA hang workarounds  [    1.049534] pci 0000:00:02.0: Boot video device  [    1.049795] PCI: CLS 0 bytes, default 64  [    1.050984] Trying to unpack rootfs image as initramfs...  [    1.909841] Freeing initrd memory: 17092k freed  [    1.927761] platform rtc_cmos: registered platform RTC device (no PNP  device found)  [    1.942414] audit: initializing netlink socket (disabled)  [    1.943586] type=2000 audit(1347140191.940:1): initialized  [    1.976981] HugeTLB registered 4 MB page size, pre-allocated 0 pages  [    1.979763] VFS: Disk quotas dquot_6.5.2  [    1.979855] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  [    1.982204] fuse init (API version 7.17)  [    1.982455] msgmni has been set to 991  [    2.018380] Block layer SCSI generic (bsg) driver version 0.4 loaded  (major 253)  [    2.018754] io scheduler noop registered  [    2.018775] io scheduler deadline registered  [    2.018806] io scheduler cfq registered (default)  [    2.019045] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  [    2.019113] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  [    2.019430] vesafb: mode is 1024x768x16, linelength=2048, pages=7  [    2.019457] vesafb: protected mode interface info at c000:7fe6  [    2.019488] vesafb: pmi: set display start = c00c8031, set palette =  c00c80f2  [    2.019515] vesafb: pmi: ports = 1ce 1cf 1cf 1d0   [    2.019558] vesafb: scrolling: redraw  [    2.019580] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0  [    2.020153] vesafb: framebuffer at 0xe0000000, mapped to 0xe0800000,  using 6144k, total 12288k  [    2.026400] fbcon: VESA VGA (fb0) is primary device  [    2.027048] bootsplash 3.1.6-2004/03/31: looking for picture...  [    2.041049]  silentjpeg size 69816 bytes,  [    2.041200] ...found (1024x768, 69708 bytes, v3).  [    2.062421] Console: switching to colour frame buffer device 107x34  [    2.121475] fb0: VESA VGA frame buffer device  [    2.122311] ACPI: Deprecated procfs I/F for AC is loaded, please retry  with CONFIG_ACPI_PROCFS_POWER cleared  [    2.122613] ACPI: AC Adapter [AC] (on-line)  [    2.125161] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00 /input/input0  [    2.125295] ACPI: Power Button [PWRF]  [    2.125463] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00 /input/input1  [    2.125544] ACPI: Sleep Button [SLPF]  [    2.136364] ERST: Table is not found!  [    2.142814] GHES: HEST is not enabled!  [    2.149199] ACPI: Deprecated procfs I/F for battery is loaded, please  retry with CONFIG_ACPI_PROCFS_POWER cleared  [    2.151097] ACPI: Battery Slot [BAT0] (battery present)  [    2.172599] isapnp: Scanning for PnP cards...  [    2.584103] isapnp: No Plug & Play device found  [    2.586230] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled  [    2.603875] Linux agpgart interface v0.103  [    2.614490] brd: module loaded  [    2.621784] loop: module loaded  [    2.624198] ahci 0000:00:0d.0: version 3.0  [    2.625771] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5  [    2.627458] PCI: setting IRQ 5 as level-triggered  [    2.627741] ahci 0000:00:0d.0: PCI INT A -> Link[LNKA] -> GSI 5  (level, low) -> IRQ 5  [    2.631113] ahci: SSS flag set, parallel bus scan disabled  [    2.633129] ahci 0000:00:0d.0: AHCI 0001.0100 32 slots 1 ports 3 Gbps  0x1 impl SATA mode  [    2.634274] ahci 0000:00:0d.0: flags: 64bit ncq stag only ccc   [    2.638174] ahci 0000:00:0d.0: setting latency timer to 64  [    2.644966] scsi0 : ahci  [    2.647240] ata1: SATA max UDMA/133 abar m8192@0xf0806000 port  0xf0806100 irq 5  [    2.667317] ata_piix 0000:00:01.1: version 2.13  [    2.669303] ata_piix 0000:00:01.1: setting latency timer to 64  [    2.676388] scsi1 : ata_piix  [    2.679944] scsi2 : ata_piix  [    2.683908] ata2: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000  irq 14  [    2.685368] ata3: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xd008  irq 15  [    2.687928] Fixed MDIO Bus: probed  [    2.688739] tun: Universal TUN/TAP device driver, 1.6  [    2.690159] tun: (C) 1999-2004 Max Krasnyansky   [    2.702943] arcnet loaded.  [    2.707989] PPP generic driver version 2.4.2  [    2.712180] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  [    2.713520] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  [    2.715170] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11  [    2.716614] PCI: setting IRQ 11 as level-triggered  [    2.716676] ohci_hcd 0000:00:06.0: PCI INT A -> Link[LNKB] -> GSI 11  (level, low) -> IRQ 11  [    2.717954] ohci_hcd 0000:00:06.0: setting latency timer to 64  [    2.717986] ohci_hcd 0000:00:06.0: OHCI Host Controller  [    2.719294] ohci_hcd 0000:00:06.0: new USB bus registered, assigned  bus number 1  [    2.720446] ohci_hcd 0000:00:06.0: irq 11, io mem 0xf0804000  [    2.781231] hub 1-0:1.0: USB hub found  [    2.783570] hub 1-0:1.0: 8 ports detected  [    2.790461] uhci_hcd: USB Universal Host Controller Interface driver  [    2.792524] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at  0x60,0x64 irq 1,12  [    2.803616] serio: i8042 KBD port at 0x60,0x64 irq 1  [    2.807416] serio: i8042 AUX port at 0x60,0x64 irq 12  [    2.810756] mousedev: PS/2 mouse device common for all mice  [    2.826122] input: AT Translated Set 2 keyboard as /devices/platform /i8042/serio0/input/input2  [    2.831046] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0  [    2.834019] rtc0: alarms up to one day, 114 bytes nvram  [    2.835817] device-mapper: uevent: version 1.0.3  [    2.840690] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19)  initialised: [email]dm-devel@redhat.com[/email]  [    2.843357] EISA: Probing bus 0 at eisa.0  [    2.845381] Cannot allocate resource for EISA slot 4  [    2.846679] EISA: Detected 0 cards.  [    2.849624] cpufreq-nforce2: No nForce2 chipset.  [    2.851169] cpuidle: using governor ladder  [    2.851994] cpuidle: using governor menu  [    2.853581] EFI Variables Facility v0.08 2004-May-17  [    2.855233] TCP cubic registered  [    2.871452] NET: Registered protocol family 10  [    2.875311] ata3.00: ATAPI: VBOX CD-ROM, 1.0, max UDMA/133  [    2.879604] ata3.00: configured for UDMA/33  [    2.886580] NET: Registered protocol family 17  [    2.889262] Registering the dns_resolver key type  [    2.890692] Using IPI No-Shortcut mode  [    2.892531] registered taskstats version 1  [    2.932429] Refined TSC clocksource calibration: 2552.575 MHz.  [    2.934731] Switching to clocksource tsc  [    2.954880] rtc_cmos rtc_cmos: setting system clock to 2012-09-08  21:36:34 UTC (1347140194)  [    2.959957] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  [    2.961380] EDD information not available.  [    2.992734] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)  [    2.998256] ata1.00: ATA-6: VBOX HARDDISK, 1.0, max UDMA/133  [    2.999666] ata1.00: 16777216 sectors, multi 128: LBA48 NCQ (depth  31/32)  [    3.005406] ata1.00: configured for UDMA/133  [    3.042902] scsi 0:0:0:0: Direct-Access     ATA      VBOX HARDDISK     1.0  PQ: 0 ANSI: 5  [    3.052652] sd 0:0:0:0: [sda] 16777216 512-byte logical blocks: (8.58  GB/8.00 GiB)  [    3.054937] sd 0:0:0:0: Attached scsi generic sg0 type 0  [    3.067886] sd 0:0:0:0: [sda] Write Protect is off  [    3.070170] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  [    3.070874] sd 0:0:0:0: [sda] Write cache: enabled, read cache:  enabled, doesn't support DPO or FUA  [    3.104434] scsi 2:0:0:0: CD-ROM            VBOX     CD-ROM            1.0  PQ: 0 ANSI: 5  [    3.112829] sr0: scsi3-mmc drive: 32x/32x xa/form2 tray  [    3.114223] cdrom: Uniform CD-ROM driver Revision: 3.20  [    3.117626] sr 2:0:0:0: Attached scsi CD-ROM sr0  [    3.120486] sr 2:0:0:0: Attached scsi generic sg1 type 5  [    3.163723]  sda: unknown partition table  [    3.166247] usb 1-1: new full-speed USB device number 2 using ohci_hcd  [    3.178716] sd 0:0:0:0: [sda] Attached SCSI disk  [    3.181783] Freeing unused kernel memory: 704k freed  [    3.190922] Write protecting the kernel text: 5508k  [    3.200867] Write protecting the kernel read-only data: 2108k  [    3.388959] udev: starting version 151  [    3.424170] udevd (83): /proc/83/oom_adj is deprecated, please use  /proc/83/oom_score_adj instead.  [    4.310524] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21- k8-NAPI  [    4.312684] e1000: Copyright (c) 1999-2006 Intel Corporation.  [    4.380962] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10  [    4.382717] PCI: setting IRQ 10 as level-triggered  [    4.382738] e1000 0000:00:03.0: PCI INT A -> Link[LNKC] -> GSI 10  (level, low) -> IRQ 10  [    4.464761] e1000 0000:00:03.0: setting latency timer to 64  [    4.476101] hrtimer: interrupt took 32418864 ns  [    5.105466] input: VirtualBox USB Tablet as /devices/pci0000:00 /0000:00:06.0/usb1/1-1/1-1:1.0/input/input3  [    5.136891] generic-usb 0003:80EE:0021.0001: input,hidraw0: USB HID  v1.10 Mouse [VirtualBox USB Tablet] on usb-0000:00:06.0-1/input0  [    5.152173] usbcore: registered new interface driver usbhid  [    5.154020] usbhid: USB HID core driver  [    5.246252] e1000 0000:00:03.0: eth0: (PCI:33MHz:32-bit)  08:00:27:33:92:38  [    5.249082] e1000 0000:00:03.0: eth0: Intel(R) PRO/1000 Network  Connection  [    7.057551] aufs 3.2-20120109  [    7.952244] ISO 9660 Extensions: Microsoft Joliet Level 3  [    7.962997] ISO 9660 Extensions: RRIP_1991A  [    8.169728] squashfs: version 4.0 (2009/01/31) Phillip Lougher  [   28.500731] udev: starting version 151  [   29.522281] lp: driver loaded but no devices found  [   30.171970] parport_pc 00:04: reported by Plug and Play ACPI  [   30.569425] piix4_smbus 0000:00:07.0: SMBus base address uninitialized  - upgrade BIOS or use force_addr=0xaddr  [   33.243398] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow  Control: RX  [   33.560499] psmouse serio1: hgpk: ID: 10 00 64  [   33.580277] input: ImExPS/2 Generic Explorer Mouse as /devices/platform /i8042/serio1/input/input4  [   34.785111] ppdev: user-space parallel port driver  [   37.851303] snd_intel8x0 0000:00:05.0: PCI INT A -> Link[LNKA] -> GSI  5 (level, low) -> IRQ 5  [   37.869454] snd_intel8x0 0000:00:05.0: setting latency timer to 64  [   38.708592] intel8x0_measure_ac97_clock: measured 385635 usecs (24276 samples)  [   38.708608] intel8x0: measured clock 62950 rejected   [   39.099608] intel8x0_measure_ac97_clock: measured 64839 usecs (7680  samples)  [   39.099624] intel8x0: measured clock 118447 rejected  [   39.456274] intel8x0_measure_ac97_clock: measured 55766 usecs (7200  samples)  [   39.456289] intel8x0: measured clock 129110 rejected   [   39.456299] intel8x0: clocking to 48000  [   43.512108] eth0: no IPv6 routers present      This is .the result bro

---

### Post by chili555 on 2012-09-08
I can't read that bro. I guess you didn't find the pipe symbol on your keyboard. The pipe symbol | is on the right side of my US keyboard on the same key with \. Please enter these commands one at a time and post the result of each here:```
sudo modprobe iwlwifi
dmesg | grep iwl
rfkill list all
```Some may produce no output. That's fine, just tell me.

---

### Post by necs on 2012-09-09
Thanks........    Non of em worked!!!!  Results are::::  root@bt:~# sudo modprobe iwlwifi  root@bt:~# sudo modprobe iwlwifi  root@bt:~# dmesg | grep iwl  root@bt:~# rfkill list all  What should I do.................................

---

### Post by chili555 on 2012-09-09
Open a terminal using ctrl+alt+t then copy and paste this command:

```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
Then reply back, and attach the netinfo.txt file you'll find in your user directory.

The script removes the MAC Address, WPA and WEP keys.

Something weird is going on here. Thanks.

---

### Post by svratonzo123 on 2012-09-09
hi
here my ouput. Wireless still not working

simone@x-simone:~$ sudo modprobe iwlwifi
simone@x-simone:~$ dmesg | grep iwl
[    9.459673] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.459703] iwlwifi 0000:03:00.0: setting latency timer to 64
[    9.459723] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    9.459725] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90000678000
[    9.459727] iwlwifi 0000:03:00.0: HW Revision ID = 0xC4
[    9.459862] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[    9.459942] iwlwifi 0000:03:00.0: Detected 2000 Series 2x2 BGN/BT, REV=0xC8
[    9.460051] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    9.478061] iwlwifi 0000:03:00.0: device EEPROM VER=0x81c, CALIB=0x6
[    9.478064] iwlwifi 0000:03:00.0: Device SKU: 0X150
[    9.478065] iwlwifi 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[    9.478512] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    9.482631] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[    9.553098] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[    9.556991] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
simone@x-simone:~$ rfkill list all
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by svratonzo123 on 2012-09-09
mine is NOT hard blocked but is not working........

Hi
netinfo uploaded

thank you again

---

### Post by chili555 on 2012-09-09
> iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.And also:> phy0: Wireless LAN
Soft blocked: yes
[COLOR="Red"]Hard blocked: yes[/COLOR]'Hard' in this case means 'hardware.' Please find the wireless switch on your laptop and turn the wireless on.

---

### Post by necs on 2012-09-09
> **chili555 said:**
> open a terminal using ctrl+alt+t then copy and paste this command:

```
wget -n -t 5 -t 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```then reply back, and attach the netinfo.txt file you'll find in your user directory.

The script removes the mac address, wpa and wep keys.

Something weird is going on here. Thanks.

  results  [quote=necs]   wget -n -t 5 -t 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)    && chmod +x wireless_script && ./wireless_script   --2012-09-09 11:30:03--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)   resolving dl.dropbox.com... Failed: Connection timed out. Wget: Unable to   resolve host address `dl.dropbox.com'  [/quote]

---

### Post by chili555 on 2012-09-09
Now I'm really confused. svratonzo123 has an Intel Centrino Wireless-N 2230 that doesn't work apparently because the switch is off.

necs has...what? Did you chime in here because you also have an Intel Centrino Wireless-N 2230 that doesn't work? Or what? If not, please start your own thread and post netinfo.txt from a working internet connection using this command:```
wget -t10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

---

### Post by necs on 2012-09-09
Check This Out......  I tried some here.......and i want yhu help meh check whether am on line and any other fin i need 2 duu.

---

### Post by chili555 on 2012-09-09
> **necs said:**
> Check This Out......  I tried some here.......and i want yhu help meh check whether am on line and any other fin i need 2 duu.Check what out? Do you have a link to your thread?

---

### Post by necs on 2012-09-09
> **chili555 said:**
> Check what out? Do you have a link to your thread?

 Am aving problem posting when attaching a notepad wch i du copy all the    result i got 4rm the installation command datz y am pretty messed up in   repling well....4 give meh pls.

---

### Post by necs on 2012-09-09
> **necs said:**
> Am aving problem posting when attaching a notepad wch i du copy all the    result i got 4rm the installation command datz y am pretty messed up in   repling well....4 give meh pls.

 Check This Out
necs: apt-get install ndiswrapper-common 
   # apt-get install ndiswrapper-common    Reading package lists... 
Done     Building dependency tree            Reading state information... 
Done     Suggested packages:       ndiswrapper-source
 The following NEW packages will be installed:       ndiswrapper-common    0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.    Need to get 21.7kB of archives.    After this operation, 98.3kB of additional disk space will be used.
 Get:1 [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/main    ndiswrapper-common 1.54-2ubuntu1 [21.7kB]    Fetched 21.7kB in 9s (2,300B/s)                Selecting previously deselected package ndiswrapper-common.
 (Reading database ... 238113 files and directories currently installed.) 
Unpacking ndiswrapper-common (from .../ndiswrapper-  common_1.54-2ubuntu1_all.deb) ...   
Processing triggers for man-db ...   Setting up ndiswrapper-common (1.54-2ubuntu1) ...

necs:lspci -nn 
  00:00.0 Host bridge [0600]: 
Intel Corporation 440FX - 82441FX PMC    [Natoma] [8086:1237] (rev 02)    00:01.0 ISA bridge [0601]:
 Intel Corporation 82371SB PIIX3 ISA    [Natoma/Triton II] [8086:7000]    00:01.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE    [8086:7111] (rev 01)    00:02.0 VGA compatible controller [0300]: 
InnoTek Systemberatung GmbH    VirtualBox Graphics Adapter [80ee:beef]    00:03.0 Ethernet controller [0200]: 
Intel Corporation 82540EM Gigabit    Ethernet Controller [8086:100e] (rev 02)    00:04.0 System peripheral [0880]:
 InnoTek Systemberatung GmbH VirtualBox    Guest Service [80ee:cafe]   00:05.0 Multimedia audio controller [0401]: 
Intel Corporation 82801AA    AC'97 Audio Controller [8086:2415] (rev 01)    00:06.0 USB Controller [0c03]:
 Apple Computer Inc. KeyLargo/Intrepid USB    [106b:003f]    00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI    [8086:7113] (rev 08)    00:0d.0 SATA controller [0106]:
 Intel Corporation 82801HBM/HEM    (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)

 necs: lshw -C network
    *-network                         description: 
Ethernet interface          product: 82540EM Gigabit Ethernet Controller          vendor:
 Intel Corporation          physical id: 3          
bus info: pci@0000:00:03.0
 logical name: eth0          
version: 02
 serial: 08:00:27:33:92:38          
size: 1GB/s          capacity: 1GB/s 
         width: 32 bits            clock: 66MHz          capabilities: pm pcix bus_master cap_list ethernet physical tp     10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation          configuration: autonegotiation=on broadcast=yes driver=e1000    driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=10.0.2.15    latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1GB/s           resources: irq:10 memory:f0000000-f001ffff ioport:d010(size=8)

---

### Post by chili555 on 2012-09-09
I asked you politely to start your own new thread.

---

### Post by svratonzo123 on 2012-09-10
Hi
no one could help me please?

---

### Post by chili555 on 2012-09-10
> **svratonzo123 said:**
> Hi
no one could help me please?You said:> mine is NOT hard blocked but is not working........

Hi
netinfo uploadedBut your netinfo.txt says it *is* hard blocked. Is there any change if you press F9 and then do:```
rfkill list all
sudo rfkill unblock all
rfkill list all
```Are there any settings in the BIOS that enable or disable wireless?

---

### Post by svratonzo123 on 2012-09-10
Hi
radio wireless were set to off by BIOS.
Now is working....

Thank you

---

### Post by chili555 on 2012-09-10
Awesome! Glad it's working. Have fun.

---

