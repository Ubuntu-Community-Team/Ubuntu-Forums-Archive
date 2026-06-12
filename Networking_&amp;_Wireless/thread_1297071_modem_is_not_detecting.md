---
title: "modem is not detecting"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by shaon3343 on 2009-10-21
**[SIZE=4]Hi , Recently I bought a usb gprs/edge modem But My Ubuntu 9.04 cant detect it . It is a mobidata usb modem . please help me about how can i use this modem in my Ubuntu?[/SIZE]**

---

### Post by pdc on 2009-10-22
if you type

> lsusb into a terminal and then 

> dmesg (with the modem in place)

copy and paste the results from the terminal back here

---

### Post by shaon3343 on 2009-11-07
hi, ive entered "lsusb" and "dmesg" in the terminal and heres the output: 

palash@palash-desktop:~$  lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 10ce:ea6a Silicon Labs MobiData EDGE USB Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
palash@palash-desktop:~$   dmesg

[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0001f7f0
[    0.000000] On node 0 totalpages: 128885
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80,
node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 976 pages used for memmap
[    0.000000]   Normal zone: 123936 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap:
1f800000:d0800000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.
Total pages: 127877
[    0.000000] Kernel command line:
root=UUID=6b7b1b4f-4981-4723-8de7-59f866636216 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 3014.166 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2580160 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 493160k/516032k available (4126k kernel code,
22120k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xdfff0000 - 0xff3fe000   ( 500 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdf7f0000   ( 503 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in
supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3,
MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated
using timer frequency.. 6028.33 BogoMIPS (lpj=12056664)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.019324] ACPI: Core revision 20080926
[    0.021409] ACPI: Checking initramfs for custom DSDT
[    0.306829] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.346519] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 04
[    0.348001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine..
6029.15 BogoMIPS (lpj=12058316)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.432535] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 04
[    0.432553] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.436037] Brought up 2 CPUs
[    0.436041] Total of 2 processors activated (12057.49 BogoMIPS).
[    0.436096] CPU0 attaching sched-domain:
[    0.436099]  domain 0: span 0-1 level CPU
[    0.436103]   groups: 0 1
[    0.436110] CPU1 attaching sched-domain:
[    0.436113]  domain 0: span 0-1 level CPU
[    0.436115]   groups: 1 0
[    0.436187] net_namespace: 776 bytes
[    0.436187] Booting paravirtualized kernel on bare hardware
[    0.436400] Time: 19:28:48  Date: 10/30/09
[    0.436400] regulator: core version 0.5
[    0.436400] NET: Registered protocol family 16
[    0.436400] EISA bus registered
[    0.436400] ACPI: bus type pci registered
[    0.436400] PCI: Found Intel Corporation 945G/GZ/P/PL Express
Memory Controller Hub without MMCONFIG support.
[    0.444155] PCI: PCI BIOS revision 3.00 entry at 0xfab00, last bus=1
[    0.444159] PCI: Using configuration type 1 for base access
[    0.445369] ACPI: EC: Look up EC in DSDT
[    0.453407] ACPI: Interpreter enabled
[    0.453417] ACPI: (supports S0 S1 S4 S5)
[    0.453443] ACPI: Using IOAPIC for interrupt routing
[    0.459243] ACPI: No dock devices found.
[    0.459259] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.459364] pci 0000:00:02.0: reg 10 32bit mmio: [0xe2000000-0xe207ffff]
[    0.459371] pci 0000:00:02.0: reg 14 io port: [0xc000-0xc007]
[    0.459377] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.459383] pci 0000:00:02.0: reg 1c 32bit mmio: [0xe2080000-0xe20bffff]
[    0.459469] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe20c0000-0xe20c3fff]
[    0.459504] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.459509] pci 0000:00:1b.0: PME# disabled
[    0.459559] pci 0000:00:1d.0: reg 20 io port: [0xb000-0xb01f]
[    0.459614] pci 0000:00:1d.1: reg 20 io port: [0xb400-0xb41f]
[    0.459668] pci 0000:00:1d.2: reg 20 io port: [0xb800-0xb81f]
[    0.459722] pci 0000:00:1d.3: reg 20 io port: [0xbc00-0xbc1f]
[    0.459774] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe20c4000-0xe20c43ff]
[    0.459942] pci 0000:00:1f.0: quirk: region 0400-047f claimed by
ICH6 ACPI/GPIO/TCO
[    0.459947] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.459989] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.460009] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.460016] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.460023] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.460030] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.460051] pci 0000:00:1f.2: PME# supported from D3hot
[    0.460056] pci 0000:00:1f.2: PME# disabled
[    0.460107] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.460180] pci 0000:01:05.0: reg 10 io port: [0xa000-0xa0ff]
[    0.460188] pci 0000:01:05.0: reg 14 32bit mmio: [0xe1000000-0xe10000ff]
[    0.460219] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.460230] pci 0000:01:05.0: supports D1 D2
[    0.460233] pci 0000:01:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.460238] pci 0000:01:05.0: PME# disabled
[    0.460283] pci 0000:00:1e.0: transparent bridge
[    0.460288] pci 0000:00:1e.0: bridge io port: [0xa000-0xafff]
[    0.460293] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0000000-0xe1ffffff]
[    0.460307] bus 00 -> node 0
[    0.460314] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.460663] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.469553] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10
11 12 14 15)
[    0.469691] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11
12 14 15) *0, disabled.
[    0.469830] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10
*11 12 14 15)
[    0.469967] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10
*11 12 14 15)
[    0.470102] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11
12 14 15) *0, disabled.
[    0.470237] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10
11 12 14 15)
[    0.470373] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11
12 14 15) *0, disabled.
[    0.470508] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10
11 12 14 15)
[    0.470749] ACPI: WMI: Mapper loaded
[    0.470806] SCSI subsystem initialized
[    0.470806] libata version 3.00 loaded.
[    0.470806] usbcore: registered new interface driver usbfs
[    0.470806] usbcore: registered new interface driver hub
[    0.470806] usbcore: registered new device driver usb
[    0.470806] PCI: Using ACPI for IRQ routing
[    0.476018] Bluetooth: Core ver 2.13
[    0.476042] NET: Registered protocol family 31
[    0.476042] Bluetooth: HCI device and connection manager initialized
[    0.476042] Bluetooth: HCI socket layer initialized
[    0.476042] NET: Registered protocol family 8
[    0.476042] NET: Registered protocol family 20
[    0.476046] NetLabel: Initializing
[    0.476049] NetLabel:  domain hash size = 128
[    0.476052] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.476068] NetLabel:  unlabeled traffic allowed by default
[    0.476087] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.476093] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.480090] AppArmor: AppArmor Filesystem Enabled
[    0.488016] pnp: PnP ACPI init
[    0.488030] ACPI: bus type pnp registered
[    0.491968] pnp: PnP ACPI: found 16 devices
[    0.491971] ACPI: ACPI bus type pnp unregistered
[    0.491976] PnPBIOS: Disabled by ACPI PNP
[    0.491988] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.491992] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.491995] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.492012] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.492016] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.492029] system 00:0c: ioport range 0x400-0x4bf could not be reserved
[    0.492036] system 00:0d: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.492044] system 00:0e: iomem range 0xca800-0xcbfff has been reserved
[    0.492048] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[    0.492051] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[    0.492054] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[    0.492057] system 00:0e: iomem range 0x1f7f0000-0x1f7fffff could
not be reserved
[    0.492061] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.492064] system 00:0e: iomem range 0x100000-0x1f7effff could not
be reserved
[    0.492067] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.492070] system 00:0e: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.492073] system 00:0e: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.492077] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.492080] system 00:0e: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.492083] system 00:0e: iomem range 0xfff00000-0xffffffff has been reserved
[    0.492086] system 00:0e: iomem range 0xe0000-0xeffff has been reserved
[    0.500505] Switched to high resolution mode on CPU 1
[    0.504012] Switched to high resolution mode on CPU 0
[    0.526820] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.526825] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.526831] pci 0000:00:1e.0:   MEM window: 0xe0000000-0xe1ffffff
[    0.526836] pci 0000:00:1e.0:   PREFETCH window:
0x00000020000000-0x000000200fffff
[    0.526851] pci 0000:00:1e.0: setting latency timer to 64
[    0.526856] bus: 00 index 0 io port: [0x00-0xffff]
[    0.526859] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.526861] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.526864] bus: 01 index 1 mmio: [0xe0000000-0xe1ffffff]
[    0.526866] bus: 01 index 2 mmio: [0x20000000-0x200fffff]
[    0.526869] bus: 01 index 3 io port: [0x00-0xffff]
[    0.526871] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.526880] NET: Registered protocol family 2
[    0.540091] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.540373] TCP established hash table entries: 16384 (order: 5,
131072 bytes)
[    0.540432] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.540490] TCP: Hash tables configured (established 16384 bind 16384)
[    0.540492] TCP reno registered
[    0.544105] NET: Registered protocol family 1
[    0.544248] checking if image is initramfs... it is
[    1.130148] Freeing initrd memory: 7344k freed
[    1.130385] cpufreq: No nForce2 chipset.
[    1.130543] audit: initializing netlink socket (disabled)
[    1.130564] type=2000 audit(1256930928.129:1): initialized
[    1.138653] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.140244] VFS: Disk quotas dquot_6.5.1
[    1.140337] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.141173] fuse init (API version 7.10)
[    1.141307] msgmni has been set to 978
[    1.141585] alg: No test for stdrng (krng)
[    1.141612] io scheduler noop registered
[    1.141616] io scheduler anticipatory registered
[    1.141619] io scheduler deadline registered
[    1.141644] io scheduler cfq registered (default)
[    1.141659] pci 0000:00:02.0: Boot video device
[    1.144800] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.144812] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.144969] input: Power Button (FF) as
/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.144972] ACPI: Power Button (FF) [PWRF]
[    1.145047] input: Power Button (CM) as
/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.145051] ACPI: Power Button (CM) [PWRB]
[    1.145407] processor ACPI_CPU:00: registered as cooling_device0
[    1.145413] ACPI: Processor [CPU0] (supports 2 throttling states)
[    1.145705] ACPI: SSDT 1F7F7240, 0087 (r1  PmRef  Cpu1Ist     3000
INTL 20040311)
[    1.146004] processor ACPI_CPU:01: registered as cooling_device1
[    1.146011] ACPI: Processor [CPU1] (supports 2 throttling states)
[    1.147986] isapnp: Scanning for PnP cards...
[    1.499688] isapnp: No Plug & Play device found
[    1.509182] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.509282] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.509385] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.509746] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.509906] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.510938] brd: module loaded
[    1.511366] loop: module loaded
[    1.511456] Fixed MDIO Bus: probed
[    1.511462] PPP generic driver version 2.4.2
[    1.511529] input: Macintosh mouse button emulation as
/devices/virtual/input/input2
[    1.511566] Driver 'sd' needs updating - please use bus_type methods
[    1.511579] Driver 'sr' needs updating - please use bus_type methods
[    1.511662] ata_piix 0000:00:1f.2: version 2.12
[    1.511681] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.511686] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.511732] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.511840] scsi0 : ata_piix
[    1.511968] scsi1 : ata_piix
[    1.512905] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.512909] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.860219] ata1.00: HPA unlocked: 156035242 -> 156301488, native 156301488
[    1.860225] ata1.00: ATA-7: MAXTOR STM380211AS, 3.AAE, max UDMA/133
[    1.860229] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.905428] ata1.00: configured for UDMA/133
[    2.084369] ata2.00: ATAPI: TSSTcorp CDW/DVD SH-M522C, TS08, max UDMA/33
[    2.116322] ata2.00: configured for UDMA/33
[    2.116719] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR
STM380211 3.AA PQ: 0 ANSI: 5
[    2.116845] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors:
(80.0 GB/74.5 GiB)
[    2.116868] sd 0:0:0:0: [sda] Write Protect is off
[    2.116871] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.116910] sd 0:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[    2.116986] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors:
(80.0 GB/74.5 GiB)
[    2.117015] sd 0:0:0:0: [sda] Write Protect is off
[    2.117019] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.117055] sd 0:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[    2.117059]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
[    2.232361] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.232448] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.233073] scsi 1:0:0:0: CD-ROM            TSSTcorp CDW/DVD
SH-M522C TS08 PQ: 0 ANSI: 5
[    2.236140] sr0: scsi3-mmc drive: 8x/52x writer cd/rw xa/form2 cdda tray
[    2.236145] Uniform CD-ROM driver Revision: 3.20
[    2.236275] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.236323] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.237098] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.237134] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.237158] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.237162] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.237236] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned
bus number 1
[    2.241153] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.241171] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe20c4000
[    2.256020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.256115] usb usb1: configuration #1 chosen from 1 choice
[    2.256155] hub 1-0:1.0: USB hub found
[    2.256164] hub 1-0:1.0: 8 ports detected
[    2.256311] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.256330] uhci_hcd: USB Universal Host Controller Interface driver
[    2.256357] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.256365] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.256368] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.256423] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned
bus number 2
[    2.256448] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b000
[    2.256537] usb usb2: configuration #1 chosen from 1 choice
[    2.256570] hub 2-0:1.0: USB hub found
[    2.256584] hub 2-0:1.0: 2 ports detected
[    2.256691] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.256698] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.256702] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.256764] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned
bus number 3
[    2.256797] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    2.256882] usb usb3: configuration #1 chosen from 1 choice
[    2.256918] hub 3-0:1.0: USB hub found
[    2.256927] hub 3-0:1.0: 2 ports detected
[    2.257028] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.257035] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.257039] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.257091] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned
bus number 4
[    2.257122] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b800
[    2.257211] usb usb4: configuration #1 chosen from 1 choice
[    2.257243] hub 4-0:1.0: USB hub found
[    2.257251] hub 4-0:1.0: 2 ports detected
[    2.257355] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.257362] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.257366] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.257421] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned
bus number 5
[    2.257453] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000bc00
[    2.257540] usb usb5: configuration #1 chosen from 1 choice
[    2.257575] hub 5-0:1.0: USB hub found
[    2.257583] hub 5-0:1.0: 2 ports detected
[    2.257736] usbcore: registered new interface driver libusual
[    2.257778] usbcore: registered new interface driver usbserial
[    2.257792] USB Serial support registered for generic
[    2.257813] usbcore: registered new interface driver usbserial_generic
[    2.257816] usbserial: USB Serial Driver core
[    2.257883] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at
0x60,0x64 irq 1,12
[    2.258234] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.258242] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.260085] mice: PS/2 mouse device common for all mice
[    2.260264] rtc_cmos 00:03: RTC can wake from S4
[    2.260319] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.260349] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.260430] device-mapper: uevent: version 1.0.3
[    2.260564] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23)
initialised: [email]dm-devel@redhat.com[/email]
[    2.260698] device-mapper: multipath: version 1.0.5 loaded
[    2.260702] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.260827] EISA: Probing bus 0 at eisa.0
[    2.260863] EISA: Detected 0 cards.
[    2.260957] cpuidle: using governor ladder
[    2.260960] cpuidle: using governor menu
[    2.261624] TCP cubic registered
[    2.261717] NET: Registered protocol family 10
[    2.262252] lo: Disabled Privacy Extensions
[    2.262691] NET: Registered protocol family 17
[    2.262713] Bluetooth: L2CAP ver 2.11
[    2.262716] Bluetooth: L2CAP socket layer initialized
[    2.262720] Bluetooth: SCO (Voice Link) ver 0.6
[    2.262722] Bluetooth: SCO socket layer initialized
[    2.262768] Bluetooth: RFCOMM socket layer initialized
[    2.262778] Bluetooth: RFCOMM TTY layer initialized
[    2.262781] Bluetooth: RFCOMM ver 1.10
[    2.263915] Using IPI No-Shortcut mode
[    2.264021] registered taskstats version 1
[    2.264126]   Magic number: 13:222:497
[    2.264201] rtc_cmos 00:03: setting system clock to 2009-10-30
19:28:50 UTC (1256930930)
[    2.264204] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.264206] EDD information not available.
[    2.264588] Freeing unused kernel memory: 532k freed
[    2.264761] Write protecting the kernel text: 4128k
[    2.264827] Write protecting the kernel read-only data: 1532k
[    2.290153] input: AT Translated Set 2 keyboard as
/devices/platform/i8042/serio0/input/input3
[    2.487756] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.487783] r8169 0000:01:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.487828] r8169 0000:01:05.0: no PCI Express capability
[    2.488674] eth0: RTL8169sc/8110sc at 0xe0048000,
00:1a:4d:6b:1f:7d, XID 18000000 IRQ 21
[    2.515820] Floppy drive(s): fd0 is 1.44M
[    2.532741] FDC 0 is a post-1991 82077
[    4.373764] PM: Starting manual resume from disk
[    4.373768] PM: Resume from partition 8:10
[    4.373770] PM: Checking hibernation image.
[    4.373937] PM: Resume from disk failed.
[    4.394730] EXT4-fs: barriers enabled
[    4.404236] kjournald2 starting.  Commit interval 5 seconds
[    4.404244] EXT4-fs: delayed allocation enabled
[    4.404247] EXT4-fs: file extents enabled
[    4.405545] EXT4-fs: mballoc enabled
[    4.405550] EXT4-fs: mounted filesystem with ordered data mode.
[    8.477342] udev: starting version 141
[    8.575848] Linux agpgart interface v0.103
[    8.635573] intel_rng: FWH not detected
[    8.834508] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[    8.835397] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    8.839001] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    8.925666] parport_pc 00:09: reported by Plug and Play ACPI
[    8.925715] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.028676] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    9.055822] ppdev: user-space parallel port driver
[    9.074481] iTCO_vendor_support: vendor-support=0
[    9.076266] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.076457] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2,
TCOBASE=0x0460)
[    9.076554] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.138374] synaptics was reset on resume, see
synaptics_resume_reset if you have trouble on resume
[    9.806321] psmouse serio1: ID: 10 00 64<6>HDA Intel 0000:00:1b.0:
PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.982539] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.142590] lp0: using parport0 (interrupt-driven).
[   10.225304] Adding 995988k swap on /dev/sda10.  Priority:-1
extents:1 across:995988k
[   10.548919] input: ImPS/2 Generic Wheel Mouse as
/devices/platform/i8042/serio1/input/input5
[   10.775637] EXT4 FS on sda11, internal journal on sda11:8
[   11.760233] type=1505 audit(1256909339.992:2):
operation="profile_load" name="/usr/share/gdm/guest-session/Xsession"
name2="default" pid=1906
[   11.810056] type=1505 audit(1256909340.044:3):
operation="profile_load" name="/sbin/dhclient-script" name2="default"
pid=1910
[   11.810168] type=1505 audit(1256909340.044:4):
operation="profile_load" name="/sbin/dhclient3" name2="default"
pid=1910
[   11.810217] type=1505 audit(1256909340.044:5):
operation="profile_load"
name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default"
pid=1910
[   11.810260] type=1505 audit(1256909340.044:6):
operation="profile_load"
name="/usr/lib/connman/scripts/dhclient-script" name2="default"
pid=1910
[   11.946750] type=1505 audit(1256909340.180:7):
operation="profile_load" name="/usr/lib/cups/backend/cups-pdf"
name2="default" pid=1915
[   11.946946] type=1505 audit(1256909340.180:8):
operation="profile_load" name="/usr/sbin/cupsd" name2="default"
pid=1915
[   11.976553] type=1505 audit(1256909340.208:9):
operation="profile_load" name="/usr/sbin/tcpdump" name2="default"
pid=1919
[   14.302058] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.302062] Bluetooth: BNEP filters: protocol multicast
[   14.340842] Bridge firewalling registered
[   16.080361] [drm] Initialized drm 1.1.0 20060810
[   16.090435] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.090442] pci 0000:00:02.0: setting latency timer to 64
[   16.090611] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   16.094370] [drm:i915_setparam] *ERROR* unknown parameter 4
[   16.094402] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   16.594053] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   19.763943] r8169: eth0: link down
[   19.764023] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.019392] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  574.341015] usb 3-2: new full speed USB device using uhci_hcd and address 2
[  574.507622] usb 3-2: configuration #1 chosen from 1 choice

---

### Post by shaon3343 on 2009-11-07
Bump!!!

---

### Post by shaon3343 on 2009-11-07
Bump!!!

---

### Post by shahan on 2009-11-07
hey shawon....
Actually there is some problem on Mobidata support on LINUX. However...you said u r using 9.04
Please try 9.10...you may get the support. Because I heared that in 9.10 the support will come

**NB. The problem is because of MOBIDATA. They do not submit their Linux driver for their modem. Don't blame LINUX. Wish u good luck**

---

### Post by tedora on 2009-11-22
Ubuntu9.10 do detect the **Mobidata MBD-100EU** modem & work fine.


the bug related to cp2101.c of Ubuntu9.04 has fixed in Ubuntu9.10.
But there is no **wvdial** or **gnome-ppp** in the Ubuntu9.10 live cd.
it's like the joke of a monkey , which each step climb 1 foot and decent 
3 feet.

try with Ubuntu9.10. (Karmic Koala)

---

### Post by d.anup93 on 2009-12-05
Ubuntu9.10 do is not detect the Mobidata MBD-100EU modem & i am not work fine at ubuntu

---

