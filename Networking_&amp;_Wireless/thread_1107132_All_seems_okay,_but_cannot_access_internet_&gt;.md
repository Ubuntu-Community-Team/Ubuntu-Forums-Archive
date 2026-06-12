---
title: "All seems okay, but cannot access internet &gt;"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by DancinHomer on 2009-03-26
Have been repairing Windows based PCs for 12years, but a Newb when it comes to Linux - still learning. :confused:

I've put Ubuntu on my laptop with no problems, but I've also just built a desktop system with Ubuntu on it but I can't access the internet.

All the desktop has on it, is the latest version of Ubuntu - nothing else has been added/configured from the defaults. I am connecting via an ethernet cable connected to a router (the same router my laptop is connecting fine to (wirelessly)). 

From the network icon in the top right it says 'Wired network connection' when I hover the cursor over and when I access the Connection Information all the IP information is what I would expect to see.

But when I open Firefox and try to go to a website I get the 'Address not found' error.

The NIC is onboard on a Gigabyte GA-945GCM-S2L motherboard and is (I think) the Realtek 8169 NIC. I have tried downloading the Linux drivers from Realtek's website, but didn't seem to make a difference.

Any help would be much appreciated.

---

### Post by khelben1979 on 2009-03-26
What does ifconfig report?

```
sudo ifconfig
```

Also, what hardware you have over there might also make things easier to see how it looks like:

```
sudo dmesg
```

---

### Post by DancinHomer on 2009-03-27
Here are results from the commands:

```
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:18:73:01  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1 
          RX packets:6 errors:0 dropped:2779020323 overruns:0 frame:0 
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1973 (1.9 KB)  TX bytes:1939 (1.9 KB) 
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB) 
```

```
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes) 
[    0.000000] TSC: PIT calibration confirmed by PMTIMER. 
[    0.000000] TSC: using PMTIMER calibration value 
[    0.000000] Detected 2199.992 MHz processor. 
[    0.004000] Console: colour VGA+ 80x25 
[    0.004000] console [tty0] enabled 
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) 
[    0.004000] Memory: 1016692k/1040320k available (2572k kernel code, 22944k reserved, 1160k data, 424k init, 122816k highmem) 
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
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1 
[    0.004000] hpet clockevent registered 
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4399.98 BogoMIPS (lpj=8799968) 
[    0.004000] Security Framework initialized 
[    0.004000] SELinux:  Disabled at boot. 
[    0.004000] AppArmor: AppArmor initialized 
[    0.004000] Mount-cache hash table entries: 512 
[    0.004000] Initializing cgroup subsys ns 
[    0.004000] Initializing cgroup subsys cpuacct 
[    0.004000] Initializing cgroup subsys memory 
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K 
[    0.004000] CPU: L2 cache: 1024K 
[    0.004000] CPU: Physical Processor ID: 0 
[    0.004000] CPU: Processor Core ID: 0 
[    0.004000] using mwait in idle threads. 
[    0.004000] Checking 'hlt' instruction... OK. 
[    0.017792] ACPI: Core revision 20080609 
[    0.019102] ACPI: Checking initramfs for custom DSDT 
[    0.320210] ENABLING IO-APIC IRQs 
[    0.320383] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
[    0.360879] CPU0: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d 
[    0.364022] Booting processor 1/1 ip 6000 
[    0.004000] Initializing CPU#1 
[    0.004000] Calibrating delay using timer specific routine.. 4399.96 BogoMIPS (lpj=8799931) 
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K 
[    0.004000] CPU: L2 cache: 1024K 
[    0.004000] CPU: Physical Processor ID: 0 
[    0.004000] CPU: Processor Core ID: 1 
[    0.448396] CPU1: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d 
[    0.448411] checking TSC synchronization [CPU#0 -> CPU#1]: passed. 
[    0.452049] Brought up 2 CPUs 
[    0.452052] Total of 2 processors activated (8799.94 BogoMIPS). 
[    0.452074] CPU0 attaching sched-domain: 
[    0.452077]  domain 0: span 0-1 level MC 
[    0.452079]   groups: 0 1 
[    0.452085] CPU1 attaching sched-domain: 
[    0.452087]  domain 0: span 0-1 level MC 
[    0.452089]   groups: 1 0 
[    0.452161] net_namespace: 840 bytes 
[    0.452161] Booting paravirtualized kernel on bare hardware 
[    0.452272] Time: 10:12:30  Date: 03/27/09 
[    0.452298] NET: Registered protocol family 16 
[    0.452316] EISA bus registered 
[    0.452316] ACPI: bus type pci registered 
[    0.452316] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support. 
[    0.459535] PCI: PCI BIOS revision 3.00 entry at 0xfac30, last bus=3 
[    0.459537] PCI: Using configuration type 1 for base access 
[    0.460555] ACPI: EC: Look up EC in DSDT 
[    0.465924] ACPI: Interpreter enabled 
[    0.465928] ACPI: (supports S0 S1 S4 S5) 
[    0.465942] ACPI: Using IOAPIC for interrupt routing 
[    0.468708] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[    0.468708] PCI: 0000:00:02.0 reg 10 32bit mmio: [d1100000, d117ffff] 
[    0.468708] PCI: 0000:00:02.0 reg 14 io port: [b000, b007] 
[    0.468708] PCI: 0000:00:02.0 reg 18 32bit mmio: [c0000000, cfffffff] 
[    0.468708] PCI: 0000:00:02.0 reg 1c 32bit mmio: [d1180000, d11bffff] 
[    0.468708] PCI: 0000:00:1b.0 reg 10 64bit mmio: [d11c0000, d11c3fff] 
[    0.468708] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
[    0.468708] pci 0000:00:1b.0: PME# disabled 
[    0.468708] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold 
[    0.468708] pci 0000:00:1c.0: PME# disabled 
[    0.468708] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold 
[    0.468708] pci 0000:00:1c.1: PME# disabled 
[    0.468708] PCI: 0000:00:1d.0 reg 20 io port: [b400, b41f] 
[    0.468708] PCI: 0000:00:1d.1 reg 20 io port: [b800, b81f] 
[    0.468708] PCI: 0000:00:1d.2 reg 20 io port: [bc00, bc1f] 
[    0.468708] PCI: 0000:00:1d.3 reg 20 io port: [c000, c01f] 
[    0.468708] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d11c4000, d11c43ff] 
[    0.468708] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO 
[    0.468708] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO 
[    0.468723] PCI: 0000:00:1f.2 reg 10 io port: [0, 7] 
[    0.468729] PCI: 0000:00:1f.2 reg 14 io port: [0, 3] 
[    0.468734] PCI: 0000:00:1f.2 reg 18 io port: [0, 7] 
[    0.468740] PCI: 0000:00:1f.2 reg 1c io port: [0, 3] 
[    0.468746] PCI: 0000:00:1f.2 reg 20 io port: [f000, f00f] 
[    0.468766] pci 0000:00:1f.2: PME# supported from D3hot 
[    0.468770] pci 0000:00:1f.2: PME# disabled 
[    0.468811] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f] 
[    0.468871] PCI: bridge 0000:00:1c.0 io port: [9000, 9fff] 
[    0.468921] PCI: 0000:02:00.0 reg 10 io port: [a000, a0ff] 
[    0.468936] PCI: 0000:02:00.0 reg 18 32bit mmio: [d1010000, d1010fff] 
[    0.468950] PCI: 0000:02:00.0 reg 20 32bit mmio: [d1000000, d100ffff] 
[    0.468964] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, ffff] 
[    0.468993] pci 0000:02:00.0: supports D1 
[    0.468994] pci 0000:02:00.0: supports D2 
[    0.468996] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.469001] pci 0000:02:00.0: PME# disabled 
[    0.469035] PCI: bridge 0000:00:1c.1 io port: [a000, afff] 
[    0.469039] PCI: bridge 0000:00:1c.1 32bit mmio: [d0000000, d0ffffff] 
[    0.469045] PCI: bridge 0000:00:1c.1 64bit mmio pref: [d1000000, d10fffff] 
[    0.469095] pci 0000:00:1e.0: transparent bridge 
[    0.469098] PCI: bridge 0000:00:1e.0 io port: [8000, 8fff] 
[    0.469119] bus 00 -> node 0 
[    0.469125] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.469379] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT] 
[    0.469475] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT] 
[    0.472128] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT] 
[    0.480196] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15) 
[    0.480230] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
[    0.480332] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
[    0.480434] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
[    0.480538] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[    0.480645] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[    0.480748] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[    0.480851] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
[    0.480904] Linux Plug and Play Support v0.97 (c) Adam Belay 
[    0.480904] pnp: PnP ACPI init 
[    0.480904] ACPI: bus type pnp registered 
[    0.484248] pnp: PnP ACPI: found 14 devices 
[    0.484248] ACPI: ACPI bus type pnp unregistered 
[    0.484248] PnPBIOS: Disabled by ACPI PNP 
[    0.484248] PCI: Using ACPI for IRQ routing 
[    0.492044] NET: Registered protocol family 8 
[    0.492049] NET: Registered protocol family 20 
[    0.492074] NetLabel: Initializing 
[    0.492074] NetLabel:  domain hash size = 128 
[    0.492074] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.492084] NetLabel:  unlabeled traffic allowed by default 
[    0.492092] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
[    0.492101] hpet0: 3 64-bit timers, 14318180 Hz 
[    0.493539] tracer: 772 pages allocated for 65536 entries of 48 bytes 
[    0.493542]    actual entries 65620 
[    0.493632] AppArmor: AppArmor Filesystem Enabled 
[    0.493653] ACPI: RTC can wake from S4 
[    0.500087] system 00:01: ioport range 0x4d0-0x4d1 has been reserved 
[    0.500093] system 00:01: ioport range 0x290-0x29f has been reserved 
[    0.500097] system 00:01: ioport range 0x800-0x87f has been reserved 
[    0.500102] system 00:01: ioport range 0x290-0x294 has been reserved 
[    0.500107] system 00:01: ioport range 0x880-0x88f has been reserved 
[    0.500127] system 00:0a: ioport range 0x400-0x4bf could not be reserved 
[    0.500138] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved 
[    0.500149] system 00:0c: iomem range 0xca800-0xcbfff has been reserved 
[    0.500154] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved 
[    0.500159] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved 
[    0.500164] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved 
[    0.500169] system 00:0c: iomem range 0x3f7f0000-0x3f7fffff could not be reserved 
[    0.500174] system 00:0c: iomem range 0x0-0x9ffff could not be reserved 
[    0.500179] system 00:0c: iomem range 0x100000-0x3f7effff could not be reserved 
[    0.500184] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved 
[    0.500190] system 00:0c: iomem range 0xfed13000-0xfed1dfff could not be reserved 
[    0.500195] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved 
[    0.500200] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved 
[    0.500205] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved 
[    0.500210] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved 
[    0.500215] system 00:0c: iomem range 0xe0000-0xeffff has been reserved 
[    0.500459] Switched to high resolution mode on CPU 1 
[    0.504058] Switched to high resolution mode on CPU 0 
[    0.535235] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01 
[    0.535238] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff 
[    0.535243] pci 0000:00:1c.0:   MEM window: disabled 
[    0.535247] pci 0000:00:1c.0:   PREFETCH window: disabled 
[    0.535254] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02 
[    0.535257] pci 0000:00:1c.1:   IO window: 0xa000-0xafff 
[    0.535262] pci 0000:00:1c.1:   MEM window: 0xd0000000-0xd0ffffff 
[    0.535266] pci 0000:00:1c.1:   PREFETCH window: 0x000000d1000000-0x000000d10fffff 
[    0.535272] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03 
[    0.535275] pci 0000:00:1e.0:   IO window: 0x8000-0x8fff 
[    0.535280] pci 0000:00:1e.0:   MEM window: disabled 
[    0.535283] pci 0000:00:1e.0:   PREFETCH window: disabled 
[    0.535300] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.535305] pci 0000:00:1c.0: setting latency timer to 64 
[    0.535313] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    0.535317] pci 0000:00:1c.1: setting latency timer to 64 
[    0.535323] pci 0000:00:1e.0: setting latency timer to 64 
[    0.535326] bus: 00 index 0 io port: [0, ffff] 
[    0.535328] bus: 00 index 1 mmio: [0, ffffffff] 
[    0.535330] bus: 01 index 0 io port: [9000, 9fff] 
[    0.535332] bus: 01 index 1 mmio: [0, 0] 
[    0.535334] bus: 01 index 2 mmio: [0, 0] 
[    0.535335] bus: 01 index 3 mmio: [0, 0] 
[    0.535337] bus: 02 index 0 io port: [a000, afff] 
[    0.535339] bus: 02 index 1 mmio: [d0000000, d0ffffff] 
[    0.535341] bus: 02 index 2 mmio: [d1000000, d10fffff] 
[    0.535343] bus: 02 index 3 mmio: [0, 0] 
[    0.535345] bus: 03 index 0 io port: [8000, 8fff] 
[    0.535346] bus: 03 index 1 mmio: [0, 0] 
[    0.535348] bus: 03 index 2 mmio: [0, 0] 
[    0.535350] bus: 03 index 3 io port: [0, ffff] 
[    0.535352] bus: 03 index 4 mmio: [0, ffffffff] 
[    0.535360] NET: Registered protocol family 2 
[    0.548110] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.548363] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.548862] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.549203] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.549207] TCP reno registered 
[    0.556165] NET: Registered protocol family 1 
[    0.556305] checking if image is initramfs... it is 
[    1.176768] Freeing initrd memory: 7994k freed 
[    1.177877] audit: initializing netlink socket (disabled) 
[    1.177901] type=2000 audit(1238148750.177:1): initialized 
[    1.183220] highmem bounce pool size: 64 pages 
[    1.183226] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    1.185364] VFS: Disk quotas dquot_6.5.1 
[    1.185452] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    1.185554] msgmni has been set to 1762 
[    1.185674] io scheduler noop registered 
[    1.185677] io scheduler anticipatory registered 
[    1.185679] io scheduler deadline registered 
[    1.185690] io scheduler cfq registered (default) 
[    1.185705] pci 0000:00:02.0: Boot video device 
[    1.185878] pcieport-driver 0000:00:1c.0: setting latency timer to 64 
[    1.185909] pcieport-driver 0000:00:1c.0: found MSI capability 
[    1.185944] pci_express 0000:00:1c.0:pcie00: allocate port service 
[    1.185987] pci_express 0000:00:1c.0:pcie02: allocate port service 
[    1.186075] pcieport-driver 0000:00:1c.1: setting latency timer to 64 
[    1.186106] pcieport-driver 0000:00:1c.1: found MSI capability 
[    1.186138] pci_express 0000:00:1c.1:pcie00: allocate port service 
[    1.186182] pci_express 0000:00:1c.1:pcie02: allocate port service 
[    1.186483] isapnp: Scanning for PnP cards... 
[    1.539417] isapnp: No Plug & Play device found 
[    1.570137] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    1.570262] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    1.570958] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    1.572591] brd: module loaded 
[    1.572654] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[    1.572771] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1 
[    1.572774] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp 
[    1.572913] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    1.573157] mice: PS/2 mouse device common for all mice 
[    1.573281] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[    1.573303] rtc0: alarms up to one month, hpet irqs 
[    1.573420] EISA: Probing bus 0 at eisa.0 
[    1.573445] Cannot allocate resource for EISA slot 8 
[    1.573447] EISA: Detected 0 cards. 
[    1.573451] cpuidle: using governor ladder 
[    1.573453] cpuidle: using governor menu 
[    1.573930] TCP cubic registered 
[    1.573957] Using IPI No-Shortcut mode 
[    1.574131] registered taskstats version 1 
[    1.574221]   Magic number: 1:238:225 
[    1.574250] tty ttyu9: hash matches 
[    1.574257] tty ttyrc: hash matches 
[    1.574342] rtc_cmos 00:03: setting system clock to 2009-03-27 10:12:31 UTC (1238148751) 
[    1.574345] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.574347] EDD information not available. 
[    1.574538] Freeing unused kernel memory: 424k freed 
[    1.574572] Write protecting the kernel text: 2576k 
[    1.574595] Write protecting the kernel read-only data: 936k 
[    1.591757] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[    1.689996] fuse init (API version 7.9) 
[    1.720182] processor ACPI0007:00: registered as cooling_device0 
[    1.720187] ACPI: Processor [CPU0] (supports 8 throttling states) 
[    1.720366] ACPI: SSDT 3F7F7040, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311) 
[    1.762138] processor ACPI0007:01: registered as cooling_device1 
[    1.762143] ACPI: Processor [CPU1] (supports 8 throttling states) 
[    2.030016] usbcore: registered new interface driver usbfs 
[    2.030043] usbcore: registered new interface driver hub 
[    2.030255] usbcore: registered new device driver usb 
[    2.049044] USB Universal Host Controller Interface driver v3.0 
[    2.049118] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    2.049130] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    2.049133] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    2.049184] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
[    2.049219] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b400 
[    2.049393] usb usb1: configuration #1 chosen from 1 choice 
[    2.049421] hub 1-0:1.0: USB hub found 
[    2.049429] hub 1-0:1.0: 2 ports detected 
[    2.085192] No dock devices found. 
[    2.098314] SCSI subsystem initialized 
[    2.113768] libata version 3.00 loaded. 
[    2.152294] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    2.152308] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    2.152313] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    2.152338] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
[    2.152380] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b800 
[    2.152468] usb usb2: configuration #1 chosen from 1 choice 
[    2.152495] hub 2-0:1.0: USB hub found 
[    2.152501] hub 2-0:1.0: 2 ports detected 
[    2.256324] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    2.256335] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[    2.256338] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    2.256363] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
[    2.256394] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bc00 
[    2.256483] usb usb3: configuration #1 chosen from 1 choice 
[    2.256508] hub 3-0:1.0: USB hub found 
[    2.256514] hub 3-0:1.0: 2 ports detected 
[    2.360264] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16 
[    2.360274] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
[    2.360278] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[    2.360302] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4 
[    2.360334] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c000 
[    2.360423] usb usb4: configuration #1 chosen from 1 choice 
[    2.360448] hub 4-0:1.0: USB hub found 
[    2.360459] hub 4-0:1.0: 2 ports detected 
[    2.568375] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    2.568393] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    2.568397] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    2.568429] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5 
[    2.572341] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[    2.572352] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd11c4000 
[    2.680048] usb 4-1: new low speed USB device using uhci_hcd and address 2 
[    2.692101] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[    2.692283] usb usb5: configuration #1 chosen from 1 choice 
[    2.692310] hub 5-0:1.0: USB hub found 
[    2.692319] hub 5-0:1.0: 8 ports detected 
[    2.748066] hub 4-0:1.0: unable to enumerate USB device on port 1 
[    2.901268] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    2.901283] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    2.901299] r8169 0000:02:00.0: setting latency timer to 64 
[    2.901608] eth0: RTL8168c/8111c at 0xf8834000, 00:1f:d0:18:73:01, XID 3c4000c0 IRQ 221 
[    2.907782] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    2.907814] pata_acpi 0000:00:1f.2: setting latency timer to 64 
[    2.907827] pata_acpi 0000:00:1f.2: PCI INT B disabled 
[    2.915808] ata_piix 0000:00:1f.2: version 2.12 
[    2.915827] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    2.915831] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ] 
[    2.915876] ata_piix 0000:00:1f.2: setting latency timer to 64 
[    2.917271] scsi0 : ata_piix 
[    2.917375] scsi1 : ata_piix 
[    2.918074] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14 
[    2.918078] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15 
[    3.088205] ata1.00: HPA unlocked: 156299375 -> 156301488, native 156301488 
[    3.088211] ata1.00: ATA-7: Hitachi HDS721680PLA380, P21OABEA, max UDMA/133 
[    3.088213] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[    3.104425] ata1.00: configured for UDMA/133 
[    3.260186] ata2.01: NODEV after polling detection 
[    3.268222] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100 
[    3.284224] ata2.00: configured for UDMA/100 
[    3.284334] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72168 P21O PQ: 0 ANSI: 5 
[    3.285057] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5 
[    3.291190] scsi 0:0:0:0: Attached scsi generic sg0 type 0 
[    3.291223] scsi 1:0:0:0: Attached scsi generic sg1 type 5 
[    3.304466] Driver 'sd' needs updating - please use bus_type methods 
[    3.304589] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[    3.304609] sd 0:0:0:0: [sda] Write Protect is off 
[    3.304612] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    3.304641] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    3.304736] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[    3.304753] sd 0:0:0:0: [sda] Write Protect is off 
[    3.304755] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    3.304785] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    3.304789]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[    3.320413]  sda1 sda2 < sda5 sda6 > 
[    3.352919] sd 0:0:0:0: [sda] Attached SCSI disk 
[    3.357707] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray 
[    3.357712] Uniform CD-ROM driver Revision: 3.20 
[    3.357816] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[    3.368049] usb 4-1: new low speed USB device using uhci_hcd and address 3 
[    3.568370] usb 4-1: configuration #1 chosen from 1 choice 
[    3.593226] usbcore: registered new interface driver hiddev 
[    3.593735] PM: Starting manual resume from disk 
[    3.593738] PM: Resume from partition 8:6 
[    3.593740] PM: Checking hibernation image. 
[    3.593880] PM: Resume from disk failed. 
[    3.631664] input: HID 1241:1111 as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input2 
[    3.631952] input,hidraw0: USB HID v1.10 Mouse [HID 1241:1111] on usb-0000:00:1d.3-1 
[    3.631975] usbcore: registered new interface driver usbhid 
[    3.631979] usbhid: v2.6:USB HID core driver 
[    3.640875] kjournald starting.  Commit interval 5 seconds 
[    3.640891] EXT3-fs: mounted filesystem with ordered data mode. 
[    9.140968] udevd version 124 started 
[    9.532575] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    9.562105] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[    9.588528] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3 
[    9.602155] ACPI: Power Button (FF) [PWRF] 
[    9.602237] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4 
[    9.621037] ACPI: Power Button (CM) [PWRB] 
[    9.694889] Linux agpgart interface v0.103 
[    9.775667] agpgart-intel 0000:00:00.0: Intel 945G Chipset 
[    9.775915] agpgart-intel 0000:00:00.0: detected 7932K stolen memory 
[    9.807299] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000 
[    9.876700] iTCO_vendor_support: vendor-support=0 
[    9.894202] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008) 
[    9.897106] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460) 
[    9.897199] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[    9.950882] parport_pc 00:08: reported by Plug and Play ACPI 
[    9.950929] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE] 
[   10.047769] intel_rng: FWH not detected 
[   10.213714] input: PC Speaker as /devices/platform/pcspkr/input/input5 
[   10.423025] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   10.423052] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[   10.455337] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS... 
[   12.106220] lp0: using parport0 (interrupt-driven). 
[   12.225106] Adding 1662688k swap on /dev/sda6.  Priority:-1 extents:1 across:1662688k 
[   12.784988] EXT3 FS on sda5, internal journal 
[   13.698471] type=1505 audit(1238148763.689:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3967 
[   13.849327] type=1505 audit(1238148763.842:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3972 
[   13.849528] type=1505 audit(1238148763.842:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3972 
[   13.966312] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   14.467381] ACPI: WMI: Mapper loaded 
[   15.250552] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use) 
[   15.293329] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac) 
[   15.293336] apm: disabled - APM is not SMP safe. 
[   15.467452] ppdev: user-space parallel port driver 
[   16.543560] Bluetooth: Core ver 2.13 
[   16.544377] NET: Registered protocol family 31 
[   16.544386] Bluetooth: HCI device and connection manager initialized 
[   16.544392] Bluetooth: HCI socket layer initialized 
[   16.561835] Bluetooth: L2CAP ver 2.11 
[   16.561844] Bluetooth: L2CAP socket layer initialized 
[   16.576087] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   16.576098] Bluetooth: BNEP filters: protocol multicast 
[   16.603094] Bridge firewalling registered 
[   16.603312] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature. 
[   16.617735] Bluetooth: SCO (Voice Link) ver 0.6 
[   16.617744] Bluetooth: SCO socket layer initialized 
[   16.693994] Bluetooth: RFCOMM socket layer initialized 
[   16.694015] Bluetooth: RFCOMM TTY layer initialized 
[   16.694019] Bluetooth: RFCOMM ver 1.10 
[   19.394181] [drm] Initialized drm 1.1.0 20060810 
[   19.401569] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   19.401583] pci 0000:00:02.0: setting latency timer to 64 
[   19.401771] [drm] Initialized i915 1.6.0 20060119 on minor 0 
[   20.808707] r8169: eth0: link up 
[   20.808722] r8169: eth0: link up 
[   21.109084] NET: Registered protocol family 17 
[  112.026551] type=1503 audit(1238148862.017:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5476/net/" pid=5476 profile="/usr/sbin/cupsd" 
[  112.100103] NET: Registered protocol family 10 
[  112.101018] lo: Disabled Privacy Extensions 
[  112.103284] type=1503 audit(1238148862.093:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5476 profile="/usr/sbin/cupsd" 
[  112.103784] type=1503 audit(1238148862.093:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5476 profile="/usr/sbin/cupsd" 
[  112.104285] type=1503 audit(1238148862.097:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5476 profile="/usr/sbin/cupsd" 
[  112.104745] type=1503 audit(1238148862.097:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5476 profile="/usr/sbin/cupsd" 
[  112.105200] type=1503 audit(1238148862.097:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5476 profile="/usr/sbin/cupsd" 
[  112.105672] type=1503 audit(1238148862.097:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5476 profile="/usr/sbin/cupsd" 
[  112.106134] type=1503 audit(1238148862.097:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5476 profile="/usr/sbin/cupsd" 
[  112.106148] type=1503 audit(1238148862.097:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5476 profile="/usr/sbin/cupsd" 
[  112.106236] type=1503 audit(1238148862.097:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5476/net/dev" pid=5476 profile="/usr/sbin/cupsd" 
[  112.940280] ppdev0: registered pardevice 
[  112.988178] ppdev0: unregistered pardevice 
[  114.059865] ppdev0: registered pardevice 
[  114.108272] ppdev0: unregistered pardevice 
[  114.120436] ppdev0: registered pardevice 
[  114.168021] ppdev0: unregistered pardevice 
```

Thanks

---

### Post by coutts99 on 2009-03-27
> **DancinHomer said:**
> Here are results from the commands:

```
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:18:73:01  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1 
          RX packets:6 errors:0 dropped:2779020323 overruns:0 frame:0 
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1973 (1.9 KB)  TX bytes:1939 (1.9 KB) 
          Interrupt:221 Base address:0x4000 


```



eth0 has not got an IP address. Is there a DHCP client running? ps ax| grep dhcp

Hmm, dropped:2779020323 is a bit worrying too!

---

### Post by coutts99 on 2009-03-27
Can you try -:

1) unload driver - rmmod r8169
2) load the driver again - modprobe r8169

And send the output of dmesg again?

---

### Post by DancinHomer on 2009-03-27
> eth0 has not got an IP address

When I right-click network icon and select 'Connection Information' it says IP address is 10.0.0.4 (what I would expect)

[[IMG]http://img14.imageshack.us/img14/5263/screenshottuz.th.png[/IMG]](http://img14.imageshack.us/my.php?image=screenshottuz.png)

Also, when I type 'rmmod r8169' I get message 'ERROR: Removing 'R8169': Operation not permitted'

Thanks for all your help so far..

---

### Post by coutts99 on 2009-03-27
sorry put sudo infront of those commands

---

### Post by DancinHomer on 2009-03-27
No Probs - Looks like it might be cutting off the top part of the report?

Unloaded and reloaded 'R8169':

```
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) 
[    0.004000] Memory: 1016692k/1040320k available (2572k kernel code, 22944k reserved, 1160k data, 424k init, 122816k highmem) 
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
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1 
[    0.004000] hpet clockevent registered 
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4399.98 BogoMIPS (lpj=8799968) 
[    0.004000] Security Framework initialized 
[    0.004000] SELinux:  Disabled at boot. 
[    0.004000] AppArmor: AppArmor initialized 
[    0.004000] Mount-cache hash table entries: 512 
[    0.004000] Initializing cgroup subsys ns 
[    0.004000] Initializing cgroup subsys cpuacct 
[    0.004000] Initializing cgroup subsys memory 
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K 
[    0.004000] CPU: L2 cache: 1024K 
[    0.004000] CPU: Physical Processor ID: 0 
[    0.004000] CPU: Processor Core ID: 0 
[    0.004000] using mwait in idle threads. 
[    0.004000] Checking 'hlt' instruction... OK. 
[    0.017779] ACPI: Core revision 20080609 
[    0.019104] ACPI: Checking initramfs for custom DSDT 
[    0.320211] ENABLING IO-APIC IRQs 
[    0.320386] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
[    0.360819] CPU0: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d 
[    0.364022] Booting processor 1/1 ip 6000 
[    0.004000] Initializing CPU#1 
[    0.004000] Calibrating delay using timer specific routine.. 4399.96 BogoMIPS (lpj=8799931) 
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K 
[    0.004000] CPU: L2 cache: 1024K 
[    0.004000] CPU: Physical Processor ID: 0 
[    0.004000] CPU: Processor Core ID: 1 
[    0.448397] CPU1: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d 
[    0.448412] checking TSC synchronization [CPU#0 -> CPU#1]: passed. 
[    0.452050] Brought up 2 CPUs 
[    0.452053] Total of 2 processors activated (8799.94 BogoMIPS). 
[    0.452075] CPU0 attaching sched-domain: 
[    0.452078]  domain 0: span 0-1 level MC 
[    0.452081]   groups: 0 1 
[    0.452086] CPU1 attaching sched-domain: 
[    0.452088]  domain 0: span 0-1 level MC 
[    0.452090]   groups: 1 0 
[    0.452162] net_namespace: 840 bytes 
[    0.452162] Booting paravirtualized kernel on bare hardware 
[    0.452270] Time: 12:22:52  Date: 03/27/09 
[    0.452296] NET: Registered protocol family 16 
[    0.452316] EISA bus registered 
[    0.452316] ACPI: bus type pci registered 
[    0.452316] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support. 
[    0.459537] PCI: PCI BIOS revision 3.00 entry at 0xfac30, last bus=3 
[    0.459539] PCI: Using configuration type 1 for base access 
[    0.460576] ACPI: EC: Look up EC in DSDT 
[    0.465929] ACPI: Interpreter enabled 
[    0.465933] ACPI: (supports S0 S1 S4 S5) 
[    0.465947] ACPI: Using IOAPIC for interrupt routing 
[    0.468711] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[    0.468711] PCI: 0000:00:02.0 reg 10 32bit mmio: [d1100000, d117ffff] 
[    0.468711] PCI: 0000:00:02.0 reg 14 io port: [b000, b007] 
[    0.468711] PCI: 0000:00:02.0 reg 18 32bit mmio: [c0000000, cfffffff] 
[    0.468711] PCI: 0000:00:02.0 reg 1c 32bit mmio: [d1180000, d11bffff] 
[    0.468711] PCI: 0000:00:1b.0 reg 10 64bit mmio: [d11c0000, d11c3fff] 
[    0.468711] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
[    0.468711] pci 0000:00:1b.0: PME# disabled 
[    0.468711] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold 
[    0.468711] pci 0000:00:1c.0: PME# disabled 
[    0.468711] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold 
[    0.468711] pci 0000:00:1c.1: PME# disabled 
[    0.468711] PCI: 0000:00:1d.0 reg 20 io port: [b400, b41f] 
[    0.468711] PCI: 0000:00:1d.1 reg 20 io port: [b800, b81f] 
[    0.468711] PCI: 0000:00:1d.2 reg 20 io port: [bc00, bc1f] 
[    0.468711] PCI: 0000:00:1d.3 reg 20 io port: [c000, c01f] 
[    0.468711] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d11c4000, d11c43ff] 
[    0.468711] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO 
[    0.468711] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO 
[    0.468723] PCI: 0000:00:1f.2 reg 10 io port: [0, 7] 
[    0.468728] PCI: 0000:00:1f.2 reg 14 io port: [0, 3] 
[    0.468734] PCI: 0000:00:1f.2 reg 18 io port: [0, 7] 
[    0.468740] PCI: 0000:00:1f.2 reg 1c io port: [0, 3] 
[    0.468745] PCI: 0000:00:1f.2 reg 20 io port: [f000, f00f] 
[    0.468766] pci 0000:00:1f.2: PME# supported from D3hot 
[    0.468770] pci 0000:00:1f.2: PME# disabled 
[    0.468810] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f] 
[    0.468870] PCI: bridge 0000:00:1c.0 io port: [9000, 9fff] 
[    0.468924] PCI: 0000:02:00.0 reg 10 io port: [a000, a0ff] 
[    0.468938] PCI: 0000:02:00.0 reg 18 32bit mmio: [d1010000, d1010fff] 
[    0.468953] PCI: 0000:02:00.0 reg 20 32bit mmio: [d1000000, d100ffff] 
[    0.468967] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, ffff] 
[    0.468995] pci 0000:02:00.0: supports D1 
[    0.468997] pci 0000:02:00.0: supports D2 
[    0.468999] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.469004] pci 0000:02:00.0: PME# disabled 
[    0.469037] PCI: bridge 0000:00:1c.1 io port: [a000, afff] 
[    0.469041] PCI: bridge 0000:00:1c.1 32bit mmio: [d0000000, d0ffffff] 
[    0.469048] PCI: bridge 0000:00:1c.1 64bit mmio pref: [d1000000, d10fffff] 
[    0.469095] pci 0000:00:1e.0: transparent bridge 
[    0.469099] PCI: bridge 0000:00:1e.0 io port: [8000, 8fff] 
[    0.469120] bus 00 -> node 0 
[    0.469126] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.469378] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT] 
[    0.472052] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT] 
[    0.472154] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT] 
[    0.480238] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15) 
[    0.480250] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
[    0.480354] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
[    0.480456] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
[    0.480559] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[    0.480667] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[    0.480771] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[    0.480875] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
[    0.480929] Linux Plug and Play Support v0.97 (c) Adam Belay 
[    0.480929] pnp: PnP ACPI init 
[    0.480929] ACPI: bus type pnp registered 
[    0.484336] pnp: PnP ACPI: found 14 devices 
[    0.484336] ACPI: ACPI bus type pnp unregistered 
[    0.484336] PnPBIOS: Disabled by ACPI PNP 
[    0.484336] PCI: Using ACPI for IRQ routing 
[    0.492044] NET: Registered protocol family 8 
[    0.492049] NET: Registered protocol family 20 
[    0.492074] NetLabel: Initializing 
[    0.492074] NetLabel:  domain hash size = 128 
[    0.492074] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.492083] NetLabel:  unlabeled traffic allowed by default 
[    0.492092] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
[    0.492100] hpet0: 3 64-bit timers, 14318180 Hz 
[    0.493538] tracer: 772 pages allocated for 65536 entries of 48 bytes 
[    0.493541]    actual entries 65620 
[    0.493632] AppArmor: AppArmor Filesystem Enabled 
[    0.493652] ACPI: RTC can wake from S4 
[    0.500089] system 00:01: ioport range 0x4d0-0x4d1 has been reserved 
[    0.500094] system 00:01: ioport range 0x290-0x29f has been reserved 
[    0.500099] system 00:01: ioport range 0x800-0x87f has been reserved 
[    0.500103] system 00:01: ioport range 0x290-0x294 has been reserved 
[    0.500108] system 00:01: ioport range 0x880-0x88f has been reserved 
[    0.500129] system 00:0a: ioport range 0x400-0x4bf could not be reserved 
[    0.500140] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved 
[    0.500151] system 00:0c: iomem range 0xca800-0xcbfff has been reserved 
[    0.500156] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved 
[    0.500161] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved 
[    0.500166] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved 
[    0.500171] system 00:0c: iomem range 0x3f7f0000-0x3f7fffff could not be reserved 
[    0.500176] system 00:0c: iomem range 0x0-0x9ffff could not be reserved 
[    0.500181] system 00:0c: iomem range 0x100000-0x3f7effff could not be reserved 
[    0.500187] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved 
[    0.500192] system 00:0c: iomem range 0xfed13000-0xfed1dfff could not be reserved 
[    0.500196] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved 
[    0.500202] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved 
[    0.500207] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved 
[    0.500212] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved 
[    0.500217] system 00:0c: iomem range 0xe0000-0xeffff has been reserved 
[    0.500462] Switched to high resolution mode on CPU 1 
[    0.504060] Switched to high resolution mode on CPU 0 
[    0.535232] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01 
[    0.535236] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff 
[    0.535240] pci 0000:00:1c.0:   MEM window: disabled 
[    0.535244] pci 0000:00:1c.0:   PREFETCH window: disabled 
[    0.535251] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02 
[    0.535254] pci 0000:00:1c.1:   IO window: 0xa000-0xafff 
[    0.535259] pci 0000:00:1c.1:   MEM window: 0xd0000000-0xd0ffffff 
[    0.535263] pci 0000:00:1c.1:   PREFETCH window: 0x000000d1000000-0x000000d10fffff 
[    0.535269] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03 
[    0.535272] pci 0000:00:1e.0:   IO window: 0x8000-0x8fff 
[    0.535277] pci 0000:00:1e.0:   MEM window: disabled 
[    0.535281] pci 0000:00:1e.0:   PREFETCH window: disabled 
[    0.535298] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.535303] pci 0000:00:1c.0: setting latency timer to 64 
[    0.535310] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    0.535314] pci 0000:00:1c.1: setting latency timer to 64 
[    0.535321] pci 0000:00:1e.0: setting latency timer to 64 
[    0.535324] bus: 00 index 0 io port: [0, ffff] 
[    0.535326] bus: 00 index 1 mmio: [0, ffffffff] 
[    0.535328] bus: 01 index 0 io port: [9000, 9fff] 
[    0.535330] bus: 01 index 1 mmio: [0, 0] 
[    0.535332] bus: 01 index 2 mmio: [0, 0] 
[    0.535333] bus: 01 index 3 mmio: [0, 0] 
[    0.535335] bus: 02 index 0 io port: [a000, afff] 
[    0.535337] bus: 02 index 1 mmio: [d0000000, d0ffffff] 
[    0.535339] bus: 02 index 2 mmio: [d1000000, d10fffff] 
[    0.535341] bus: 02 index 3 mmio: [0, 0] 
[    0.535343] bus: 03 index 0 io port: [8000, 8fff] 
[    0.535344] bus: 03 index 1 mmio: [0, 0] 
[    0.535346] bus: 03 index 2 mmio: [0, 0] 
[    0.535348] bus: 03 index 3 io port: [0, ffff] 
[    0.535349] bus: 03 index 4 mmio: [0, ffffffff] 
[    0.535359] NET: Registered protocol family 2 
[    0.548111] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.548361] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.548839] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.549176] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.549180] TCP reno registered 
[    0.556168] NET: Registered protocol family 1 
[    0.556308] checking if image is initramfs... it is 
[    1.176783] Freeing initrd memory: 7994k freed 
[    1.177889] audit: initializing netlink socket (disabled) 
[    1.177912] type=2000 audit(1238156572.177:1): initialized 
[    1.183236] highmem bounce pool size: 64 pages 
[    1.183242] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    1.185327] VFS: Disk quotas dquot_6.5.1 
[    1.185408] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    1.185503] msgmni has been set to 1762 
[    1.185618] io scheduler noop registered 
[    1.185620] io scheduler anticipatory registered 
[    1.185623] io scheduler deadline registered 
[    1.185634] io scheduler cfq registered (default) 
[    1.185649] pci 0000:00:02.0: Boot video device 
[    1.185820] pcieport-driver 0000:00:1c.0: setting latency timer to 64 
[    1.185851] pcieport-driver 0000:00:1c.0: found MSI capability 
[    1.185886] pci_express 0000:00:1c.0:pcie00: allocate port service 
[    1.185925] pci_express 0000:00:1c.0:pcie02: allocate port service 
[    1.186006] pcieport-driver 0000:00:1c.1: setting latency timer to 64 
[    1.186037] pcieport-driver 0000:00:1c.1: found MSI capability 
[    1.186069] pci_express 0000:00:1c.1:pcie00: allocate port service 
[    1.186106] pci_express 0000:00:1c.1:pcie02: allocate port service 
[    1.186382] isapnp: Scanning for PnP cards... 
[    1.539317] isapnp: No Plug & Play device found 
[    1.570430] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    1.570558] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    1.571264] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    1.573020] brd: module loaded 
[    1.573083] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[    1.573200] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1 
[    1.573202] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp 
[    1.573341] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    1.577202] mice: PS/2 mouse device common for all mice 
[    1.577325] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[    1.577347] rtc0: alarms up to one month, hpet irqs 
[    1.577463] EISA: Probing bus 0 at eisa.0 
[    1.577488] Cannot allocate resource for EISA slot 8 
[    1.577490] EISA: Detected 0 cards. 
[    1.577494] cpuidle: using governor ladder 
[    1.577496] cpuidle: using governor menu 
[    1.577976] TCP cubic registered 
[    1.578003] Using IPI No-Shortcut mode 
[    1.578191] registered taskstats version 1 
[    1.578278]   Magic number: 1:106:381 
[    1.578399] rtc_cmos 00:03: setting system clock to 2009-03-27 12:22:53 UTC (1238156573) 
[    1.578402] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.578404] EDD information not available. 
[    1.578592] Freeing unused kernel memory: 424k freed 
[    1.578628] Write protecting the kernel text: 2576k 
[    1.578652] Write protecting the kernel read-only data: 936k 
[    1.595757] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[    1.748054] fuse init (API version 7.9) 
[    1.792269] processor ACPI0007:00: registered as cooling_device0 
[    1.792274] ACPI: Processor [CPU0] (supports 8 throttling states) 
[    1.792452] ACPI: SSDT 3F7F7040, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311) 
[    1.886140] processor ACPI0007:01: registered as cooling_device1 
[    1.886145] ACPI: Processor [CPU1] (supports 8 throttling states) 
[    2.140731] usbcore: registered new interface driver usbfs 
[    2.140755] usbcore: registered new interface driver hub 
[    2.140793] usbcore: registered new device driver usb 
[    2.143152] USB Universal Host Controller Interface driver v3.0 
[    2.143203] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    2.143212] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    2.143215] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    2.143260] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
[    2.143290] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b400 
[    2.143428] usb usb1: configuration #1 chosen from 1 choice 
[    2.143453] hub 1-0:1.0: USB hub found 
[    2.143459] hub 1-0:1.0: 2 ports detected 
[    2.244294] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    2.244304] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    2.244308] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    2.244339] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
[    2.244370] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b800 
[    2.244455] usb usb2: configuration #1 chosen from 1 choice 
[    2.244482] hub 2-0:1.0: USB hub found 
[    2.244488] hub 2-0:1.0: 2 ports detected 
[    2.276322] No dock devices found. 
[    2.318746] SCSI subsystem initialized 
[    2.348363] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    2.348373] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[    2.348376] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    2.348409] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
[    2.348440] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bc00 
[    2.348534] usb usb3: configuration #1 chosen from 1 choice 
[    2.348562] hub 3-0:1.0: USB hub found 
[    2.348569] hub 3-0:1.0: 2 ports detected 
[    2.378389] libata version 3.00 loaded. 
[    2.452373] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16 
[    2.452385] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
[    2.452389] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[    2.452419] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4 
[    2.452453] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c000 
[    2.452559] usb usb4: configuration #1 chosen from 1 choice 
[    2.452586] hub 4-0:1.0: USB hub found 
[    2.452594] hub 4-0:1.0: 2 ports detected 
[    2.661360] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    2.661374] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    2.661377] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    2.661402] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5 
[    2.665294] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[    2.665302] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd11c4000 
[    2.776043] usb 4-1: new low speed USB device using uhci_hcd and address 2 
[    2.784068] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[    2.784258] usb usb5: configuration #1 chosen from 1 choice 
[    2.784289] hub 5-0:1.0: USB hub found 
[    2.784297] hub 5-0:1.0: 8 ports detected 
[    2.840054] hub 4-0:1.0: unable to enumerate USB device on port 1 
[    2.992285] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    2.992300] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    2.992317] r8169 0000:02:00.0: setting latency timer to 64 
[    2.992627] eth0: RTL8168c/8111c at 0xf8834000, 00:1f:d0:18:73:01, XID 3c4000c0 IRQ 221 
[    2.997039] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    2.997066] pata_acpi 0000:00:1f.2: setting latency timer to 64 
[    2.997077] pata_acpi 0000:00:1f.2: PCI INT B disabled 
[    3.000603] ata_piix 0000:00:1f.2: version 2.12 
[    3.000612] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    3.000616] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ] 
[    3.000647] ata_piix 0000:00:1f.2: setting latency timer to 64 
[    3.000703] scsi0 : ata_piix 
[    3.000792] scsi1 : ata_piix 
[    3.001457] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14 
[    3.001460] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15 
[    3.176221] ata1.00: HPA unlocked: 156299375 -> 156301488, native 156301488 
[    3.176227] ata1.00: ATA-7: Hitachi HDS721680PLA380, P21OABEA, max UDMA/133 
[    3.176229] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[    3.188418] ata1.00: configured for UDMA/133 
[    3.344162] ata2.01: NODEV after polling detection 
[    3.352212] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100 
[    3.368074] usb 4-1: new low speed USB device using uhci_hcd and address 3 
[    3.368225] ata2.00: configured for UDMA/100 
[    3.368338] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72168 P21O PQ: 0 ANSI: 5 
[    3.369021] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5 
[    3.374916] scsi 0:0:0:0: Attached scsi generic sg0 type 0 
[    3.374952] scsi 1:0:0:0: Attached scsi generic sg1 type 5 
[    3.384922] Driver 'sd' needs updating - please use bus_type methods 
[    3.385020] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[    3.385036] sd 0:0:0:0: [sda] Write Protect is off 
[    3.385038] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    3.385064] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    3.385128] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[    3.385142] sd 0:0:0:0: [sda] Write Protect is off 
[    3.385145] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    3.385171] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    3.385175]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[    3.403473]  sda1 sda2 < sda5 sda6 > 
[    3.435928] sd 0:0:0:0: [sda] Attached SCSI disk 
[    3.446997] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray 
[    3.447002] Uniform CD-ROM driver Revision: 3.20 
[    3.447089] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[    3.567679] usb 4-1: configuration #1 chosen from 1 choice 
[    3.589592] usbcore: registered new interface driver hiddev 
[    3.628783] input: HID 1241:1111 as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input2 
[    3.629062] input,hidraw0: USB HID v1.10 Mouse [HID 1241:1111] on usb-0000:00:1d.3-1 
[    3.629081] usbcore: registered new interface driver usbhid 
[    3.629085] usbhid: v2.6:USB HID core driver 
[    3.775876] PM: Starting manual resume from disk 
[    3.775880] PM: Resume from partition 8:6 
[    3.775882] PM: Checking hibernation image. 
[    3.776222] PM: Resume from disk failed. 
[    3.823920] kjournald starting.  Commit interval 5 seconds 
[    3.823946] EXT3-fs: mounted filesystem with ordered data mode. 
[    8.349125] udevd version 124 started 
[    8.578231] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    8.662583] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[    8.768606] Linux agpgart interface v0.103 
[    8.815539] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3 
[    8.837056] ACPI: Power Button (FF) [PWRF] 
[    8.837147] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4 
[    8.869036] ACPI: Power Button (CM) [PWRB] 
[    8.890063] agpgart-intel 0000:00:00.0: Intel 945G Chipset 
[    8.890316] agpgart-intel 0000:00:00.0: detected 7932K stolen memory 
[    8.905303] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000 
[    9.019224] parport_pc 00:08: reported by Plug and Play ACPI 
[    9.019269] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE] 
[    9.131901] iTCO_vendor_support: vendor-support=0 
[    9.158694] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008) 
[    9.166483] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460) 
[    9.166580] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[    9.205759] intel_rng: FWH not detected 
[    9.394407] input: PC Speaker as /devices/platform/pcspkr/input/input5 
[    9.438002] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    9.438020] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[    9.470922] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS... 
[   11.330067] lp0: using parport0 (interrupt-driven). 
[   11.449979] Adding 1662688k swap on /dev/sda6.  Priority:-1 extents:1 across:1662688k 
[   12.000748] EXT3 FS on sda5, internal journal 
[   12.923336] type=1505 audit(1238156584.690:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3965 
[   13.074482] type=1505 audit(1238156584.841:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3970 
[   13.074683] type=1505 audit(1238156584.841:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3970 
[   13.191122] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   13.690553] ACPI: WMI: Mapper loaded 
[   14.474697] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use) 
[   14.526175] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac) 
[   14.526180] apm: disabled - APM is not SMP safe. 
[   14.693316] ppdev: user-space parallel port driver 
[   15.751692] Bluetooth: Core ver 2.13 
[   15.753233] NET: Registered protocol family 31 
[   15.753242] Bluetooth: HCI device and connection manager initialized 
[   15.753249] Bluetooth: HCI socket layer initialized 
[   15.770545] Bluetooth: L2CAP ver 2.11 
[   15.770553] Bluetooth: L2CAP socket layer initialized 
[   15.786045] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   15.786053] Bluetooth: BNEP filters: protocol multicast 
[   15.819462] Bridge firewalling registered 
[   15.819668] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature. 
[   15.834988] Bluetooth: SCO (Voice Link) ver 0.6 
[   15.834996] Bluetooth: SCO socket layer initialized 
[   15.902001] Bluetooth: RFCOMM socket layer initialized 
[   15.902023] Bluetooth: RFCOMM TTY layer initialized 
[   15.902026] Bluetooth: RFCOMM ver 1.10 
[   18.773166] [drm] Initialized drm 1.1.0 20060810 
[   18.835265] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   18.835279] pci 0000:00:02.0: setting latency timer to 64 
[   18.837883] [drm] Initialized i915 1.6.0 20060119 on minor 0 
[   20.021702] r8169: eth0: link up 
[   20.021717] r8169: eth0: link up 
[   20.483973] NET: Registered protocol family 17 
[   89.306664] r8169 0000:02:00.0: PCI INT A disabled 
[  111.301145] type=1503 audit(1238156683.070:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5539/net/" pid=5539 profile="/usr/sbin/cupsd" 
[  111.399810] NET: Registered protocol family 10 
[  111.401582] lo: Disabled Privacy Extensions 
[  111.403779] type=1503 audit(1238156683.171:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5539 profile="/usr/sbin/cupsd" 
[  111.404274] type=1503 audit(1238156683.171:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5539 profile="/usr/sbin/cupsd" 
[  111.404746] type=1503 audit(1238156683.171:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5539 profile="/usr/sbin/cupsd" 
[  111.405203] type=1503 audit(1238156683.175:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5539 profile="/usr/sbin/cupsd" 
[  111.405665] type=1503 audit(1238156683.175:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5539 profile="/usr/sbin/cupsd" 
[  111.406136] type=1503 audit(1238156683.175:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5539 profile="/usr/sbin/cupsd" 
[  111.406597] type=1503 audit(1238156683.175:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5539 profile="/usr/sbin/cupsd" 
[  111.407051] type=1503 audit(1238156683.175:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5539 profile="/usr/sbin/cupsd" 
[  111.407606] type=1503 audit(1238156683.175:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5539/net/dev" pid=5539 profile="/usr/sbin/cupsd" 
[  112.268321] ppdev0: registered pardevice 
[  112.316203] ppdev0: unregistered pardevice 
[  113.396175] ppdev0: registered pardevice 
[  113.444355] ppdev0: unregistered pardevice 
[  113.456315] ppdev0: registered pardevice 
[  113.505031] ppdev0: unregistered pardevice 
[  117.078530] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[  117.078559] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[  117.078582] r8169 0000:02:00.0: setting latency timer to 64 
[  117.081454] eth0: RTL8168c/8111c at 0xf8836000, 00:1f:d0:18:73:01, XID 3c4000c0 IRQ 221 
[  121.098879] r8169: eth0: link up 
[  121.098895] r8169: eth0: link up 
```

---

### Post by coutts99 on 2009-03-27
Can you send ifconfig output again?

Can you ping your default gateway?

---

### Post by DancinHomer on 2009-03-27
```
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:18:73:01  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1 
          RX packets:25 errors:0 dropped:3985147215 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:5018 (5.0 KB)  TX bytes:2665 (2.6 KB) 
          Interrupt:221 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB) 
```

I'm using the ping tool from the Network Tool utility and it doesn't seem to ping - I click on ping and nothing happens (all statistics read 0)

---

### Post by coutts99 on 2009-03-27
Something isn't right there, ifconfig should show your ip address, for example -:

```
eth0      Link encap:Ethernet  HWaddr 00:11:43:27:b3:90
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe27:b390/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2292694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:44608 txqueuelen:1000
          RX bytes:443255067 (443.2 MB)  TX bytes:174303558 (174.3 MB)
          Interrupt:16
```

Also I don't like all the drops on your interface.

Can you try -:

```
sudo dhclient eth0
```

---

### Post by DancinHomer on 2009-03-27
Ok I'm confused - out of my comfort zone, thanks for your help.

Strange because I've installed Ubuntu on 2 systems and not done anything to either after completing installation. The laptop connects fine. 

Also I have now dual booted windows on the desktop and the internet is fine in that?!? So HW is okay.

Results from dhclient:

```
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

SIOCSIFADDR: No buffer space available 
Listening on LPF/eth0/00:1f:d0:18:73:01 
Sending on   LPF/eth0/00:1f:d0:18:73:01 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17 
send_packet: Message too long 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
send_packet: Message too long 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
```

---

### Post by coutts99 on 2009-03-27
Can you try removing the option interface-mtu in /etc/dhcp3/dhclient.conf

I'm just going by info in [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/274069]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/274069")

Which mentions the 'send_packet: Message too long' error you are getting.

---

### Post by coutts99 on 2009-03-27
Hmm, your MTU is reported as 64, this is wrong.

You could try -:

```
sudo ifconfig eth0 mtu 1500
sudo dhclient eth0
```

But not sure if that will work, something looks very wrong. Try my suggestion above first though.

---

### Post by coutts99 on 2009-03-27
Some more info on the problem -:

[http://propellerheadadmin.com/tutorials/ubuntu/6-wired-networking-problem-on-a-fresh-ubuntu-810-install]("http://propellerheadadmin.com/tutorials/ubuntu/6-wired-networking-problem-on-a-fresh-ubuntu-810-install")

---

### Post by DancinHomer on 2009-03-27
Sorry, newb question: I went to remove the interface-mtu but it won't let me save the change to the file? Thanks

---

### Post by coutts99 on 2009-03-27
sudo nano -w /etc/dhcp3/dhclient.conf

---

### Post by DancinHomer on 2009-03-27
You're a star :KS - removing the interface-mtu done the trick.

I have internet access now.

Can I ask; did you get taught all this or did you teach yourself?

---

### Post by coutts99 on 2009-03-27
Used linux for years, self taught, and google helps a lot :)

Can you mark the subject with (solved) on the end.

And update your machine, hopefully you'll pull in a newer version of dhclient which hasn't got this bug.

---

### Post by DancinHomer on 2009-03-27
Will do - thanks for all your help.

LOL - how do you put 'solved' in the subject?

---

### Post by pbpersson on 2009-03-27
In a case such as this....where a bug in Ubuntu means that installing the OS will turn a computer into a doorstop with no way to access the Internet....are the installation ISO's updated so Ubuntu will work for people right out of the box?

I am writing a review comparing different distros in 2009 to see which are the easiest to use right out of the box.  There are many people out there who don't change the oil in their cars and also would not want to do sudo nano -w /etc/dhcp3/dhclient.conf, they want things to just work.

On the other hand....threads like this allow me to learn and I have bookmarked this one.  dhclient is cool :)

---

### Post by coutts99 on 2009-03-27
> **DancinHomer said:**
> Will do - thanks for all your help.

LOL - how do you put 'solved' in the subject?

Not sure :)

Edit your first post maybe?

---

### Post by DancinHomer on 2009-03-27
Have got 'SOLVED' in the first post's title, not in subject though, ah well.

---

