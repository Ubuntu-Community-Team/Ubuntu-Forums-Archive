---
title: "Wireless &quot;UNCLAIMED&quot; in 9.04, worked in 8.10"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by Enfors on 2009-10-18
I have a DLink wireless card. The label on the CD that came with it says AirPlusXtremeG - I don't know if that's the name of the card or not.

It used to work in 8.10. I don't remember if I had to do anything special to get it to work then, or if it worked out of the box.

When I do "lshw -C network", I get this:

```
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:00:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
[ snip ]

```

"sudo lspci -v" shows the following (if it's any help):

```

00:05.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
        Subsystem: D-Link System Inc Device 3a13
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at 58000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [44] Power Management version 2

```

Please advice. I've tried several searches, but I haven't found anything that seemed to apply to this problem.

---

### Post by Enfors on 2009-10-18
Here's some more information that I should have included in the original post, but neglected to do. My apologies.

"uname -mr":
```

2.6.28-11-server i686
```

Perhaps the fact that I'm apparently using some sort of server kernel is a problem?

"dmesg":
```

[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-server (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 (Ubuntu 2.6.28-11.42-server)
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
[    0.000000]  BIOS-e820: 00000000000ec000 - 00000000000f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000030000000 (usable)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.1 present.
[    0.000000] last_pfn = 0x30000 max_arch_pfn = 0x1000000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ec000 - 00000000000f0000 (ACPI NVS)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000030000000 (usable)
[    0.000000]  modified: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 30000000 @ 10000-15000
[    0.000000] RAMDISK: 038ed000 - 03fff8d5
[    0.000000] ACPI: RSDP 000EC010, 0014 (r0 COMPAQ)
[    0.000000] ACPI: RSDT 000EC080, 002C (r1 COMPAQ CARS6S6         1             0)
[    0.000000] ACPI: FACP 000EC0CC, 0074 (r1 COMPAQ CARS6S6         1             0)
[    0.000000] ACPI: DSDT 000EC140, 0037 (r1 COMPAQ DSDTTBL         1 MSFT  1000007)
[    0.000000] ACPI: FACS 000EC040, 0040
[    0.000000] ACPI: SSDT 000EC177, 1E1C (r1 COMPAQ CARS6S6         1 MSFT  1000007)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 768MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 30000000
[    0.000000]   low ram: 00000000 - 30000000
[    0.000000]   bootmap 00012000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0030000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008aae2c]    TEXT DATA BSS ==> [0000100000 - 00008aae2c]
[    0.000000]   #4 [00038ed000 - 0003fff8d5]          RAMDISK ==> [00038ed000 - 0003fff8d5]
[    0.000000]   #5 [00008ab000 - 00008b4000]    INIT_PG_TABLE ==> [00008ab000 - 00008b4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000018000]          BOOTMAP ==> [0000012000 - 0000018000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00030000
[    0.000000]   HighMem  0x00030000 -> 0x00030000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x00030000
[    0.000000] On node 0 totalpages: 196485
[    0.000000] free_area_init_node: node 0, pgdat c06e5480, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1504 pages used for memmap
[    0.000000]   Normal zone: 191008 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0xee08
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ec000
[    0.000000] PM: Registered nosave memory: 00000000000ec000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cffc0000)
[    0.000000] PERCPU: Allocating 49152 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194949
[    0.000000] Kernel command line: auto BOOT_IMAGE=Linux ro root=/dev/sda1
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 999.649 MHz processor.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.010000] allocated 3932160 bytes of page_cgroup
[    0.010000] please try cgroup_disable=memory option if you don't want
[    0.010000] Scanning for low memory corruption every 60 seconds
[    0.010000] Memory: 759708k/786432k available (4180k kernel code, 26016k reserved, 2255k data, 548k init, 0k highmem)
[    0.010000] virtual kernel memory layout:
[    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
[    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
[    0.010000]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[    0.010000]     lowmem  : 0xc0000000 - 0xf0000000   ( 768 MB)
[    0.010000]       .init : 0xc0751000 - 0xc07da000   ( 548 kB)
[    0.010000]       .data : 0xc0515003 - 0xc0748fc0   (2255 kB)
[    0.010000]       .text : 0xc0100000 - 0xc0515003   (4180 kB)
[    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.010000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.010020] Calibrating delay loop (skipped), value calculated using timer frequency.. 1999.29 BogoMIPS (lpj=9996490)
[    0.010162] Security Framework initialized
[    0.010236] SELinux:  Disabled at boot.
[    0.010333] AppArmor: AppArmor initialized
[    0.010402] Mount-cache hash table entries: 512
[    0.010736] Initializing cgroup subsys ns
[    0.010797] Initializing cgroup subsys cpuacct
[    0.010853] Initializing cgroup subsys memory
[    0.010911] Initializing cgroup subsys freezer
[    0.010993] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.011089] CPU: L2 cache: 256K
[    0.011175] Checking 'hlt' instruction... OK.
[    0.051039] SMP alternatives: switching to UP code
[    0.297712] Freeing SMP alternatives: 18k freed
[    0.297794] ACPI: Core revision 20080926
[    0.297982] ACPI: Checking initramfs for custom DSDT
[    0.880131] ACPI: setting ELCR to 0200 (from 0c28)
[    0.886508] weird, boot CPU (#0) not listedby the BIOS.
[    0.886565] SMP motherboard not detected.
[    0.886620] Local APIC not detected. Using dummy APIC emulation.
[    0.886675] SMP disabled
[    0.887308] Brought up 1 CPUs
[    0.887375] Total of 1 processors activated (1999.29 BogoMIPS).
[    0.887458] CPU0 attaching NULL sched-domain.
[    0.888410] net_namespace: 776 bytes
[    0.888495] Booting paravirtualized kernel on bare hardware
[    0.889203] Time: 19:30:51  Date: 10/18/09
[    0.889268] regulator: core version 0.5
[    0.889412] NET: Registered protocol family 16
[    0.889797] EISA bus registered
[    0.889891] ACPI: bus type pci registered
[    0.891339] PCI: PCI BIOS revision 2.10 entry at 0xfa184, last bus=1
[    0.891399] PCI: Using configuration type 1 for base access
[    0.894299] ACPI: EC: Look up EC in DSDT
[    0.897574] ACPI: Interpreter enabled
[    0.897641] ACPI: (supports S0 S1 S5)
[    0.897835] ACPI: Using PIC for interrupt routing
[    0.901752] ACPI: No dock devices found.
[    0.901832] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.901975] pci 0000:00:00.0: reg 10 32bit mmio: [0x60000000-0x63ffffff]
[    0.902074] pci 0000:00:04.0: reg 10 io port: [0x2400-0x241f]
[    0.902109] pci 0000:00:04.0: supports D1 D2
[    0.902139] pci 0000:00:04.1: reg 10 io port: [0x2470-0x2477]
[    0.902172] pci 0000:00:04.1: supports D1 D2
[    0.902210] pci 0000:00:05.0: reg 10 32bit mmio: [0x58000000-0x5800ffff]
[    0.902272] pci 0000:00:06.0: reg 10 io port: [0x2000-0x20ff]
[    0.902282] pci 0000:00:06.0: reg 14 32bit mmio: [0x40500000-0x405000ff]
[    0.902306] pci 0000:00:06.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.902318] pci 0000:00:06.0: supports D1 D2
[    0.902324] pci 0000:00:06.0: PME# supported from D1 D2 D3hot D3cold
[    0.902383] pci 0000:00:06.0: PME# disabled
[    0.902467] pci 0000:00:07.0: reg 10 32bit mmio: [0x40200000-0x4020ffff]
[    0.902477] pci 0000:00:07.0: reg 14 io port: [0x2478-0x247f]
[    0.902506] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.902565] pci 0000:00:07.0: PME# disabled
[    0.902652] pci 0000:00:0c.0: reg 10 32bit mmio: [0x40400000-0x404007ff]
[    0.902663] pci 0000:00:0c.0: reg 14 32bit mmio: [0x40300000-0x40303fff]
[    0.902695] pci 0000:00:0c.0: supports D2
[    0.902700] pci 0000:00:0c.0: PME# supported from D2 D3hot
[    0.902757] pci 0000:00:0c.0: PME# disabled
[    0.902907] pci 0000:00:14.1: reg 20 io port: [0x2460-0x246f]
[    0.902971] pci 0000:00:14.2: reg 20 io port: [0x2420-0x243f]
[    0.903031] pci 0000:00:14.3: reg 20 io port: [0x2440-0x245f]
[    0.903112] pci 0000:00:14.4: quirk: region ee00-eeff claimed by vt82c586 ACPI
[    0.903234] pci 0000:01:00.0: reg 10 32bit mmio: [0x48000000-0x4fffffff]
[    0.903244] pci 0000:01:00.0: reg 14 io port: [0x1000-0x10ff]
[    0.903253] pci 0000:01:00.0: reg 18 32bit mmio: [0x40000000-0x4000ffff]
[    0.903273] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.903286] pci 0000:01:00.0: supports D1 D2
[    0.903320] pci 0000:01:00.1: reg 10 32bit mmio: [0x50000000-0x57ffffff]
[    0.903330] pci 0000:01:00.1: reg 14 32bit mmio: [0x40100000-0x4010ffff]
[    0.903358] pci 0000:01:00.1: supports D1 D2
[    0.903401] pci 0000:00:01.0: bridge io port: [0x1000-0x1fff]
[    0.903408] pci 0000:00:01.0: bridge 32bit mmio: [0x40000000-0x401fffff]
[    0.903416] pci 0000:00:01.0: bridge 32bit mmio pref: [0x48000000-0x57ffffff]
[    0.903427] bus 00 -> node 0
[    0.903442] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.905681] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11)
[    0.906303] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11)
[    0.906918] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11)
[    0.907534] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11)
[    0.908113] ACPI: WMI: Mapper loaded
[    0.908709] SCSI subsystem initialized
[    0.908879] libata version 3.00 loaded.
[    0.909292] usbcore: registered new interface driver usbfs
[    0.909390] usbcore: registered new interface driver hub
[    0.909519] usbcore: registered new device driver usb
[    0.909845] PCI: Using ACPI for IRQ routing
[    0.910149] Bluetooth: Core ver 2.13
[    0.910203] NET: Registered protocol family 31
[    0.910259] Bluetooth: HCI device and connection manager initialized
[    0.910319] Bluetooth: HCI socket layer initialized
[    0.910374] NET: Registered protocol family 8
[    0.910428] NET: Registered protocol family 20
[    0.910507] NetLabel: Initializing
[    0.910560] NetLabel:  domain hash size = 128
[    0.910613] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.910698] NetLabel:  unlabeled traffic allowed by default
[    0.910954] AppArmor: AppArmor Filesystem Enabled
[    0.911039] pnp: PnP ACPI init
[    0.911039] ACPI: bus type pnp registered
[    0.911184] pnp 00:02: io resource (0xee00-0xee7f) overlaps 0000:00:14.4 BAR 7 (0xee00-0xeeff), disabling
[    0.911256] pnp 00:02: io resource (0xee80-0xeeff) overlaps 0000:00:14.4 BAR 7 (0xee00-0xeeff), disabling
[    0.914066] pnp: PnP ACPI: found 12 devices
[    0.914123] ACPI: ACPI bus type pnp unregistered
[    0.914181] PnPBIOS: Disabled by ACPI PNP
[    0.914809] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.914871] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.914931] system 00:00: iomem range 0x100000-0x300fffff could not be reserved
[    0.914997] system 00:00: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.915072] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.915138] system 00:02: ioport range 0x3f7-0x3f7 has been reserved
[    0.915198] system 00:02: ioport range 0xef00-0xef5f has been reserved
[    0.951516] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.951576] pci 0000:00:01.0:   IO window: 0x1000-0x1fff
[    0.951634] pci 0000:00:01.0:   MEM window: 0x40000000-0x401fffff
[    0.951693] pci 0000:00:01.0:   PREFETCH window: 0x00000048000000-0x00000057ffffff
[    0.951775] pci 0000:00:01.0: setting latency timer to 64
[    0.951784] bus: 00 index 0 io port: [0x00-0xffff]
[    0.951839] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.951896] bus: 01 index 0 io port: [0x1000-0x1fff]
[    0.951951] bus: 01 index 1 mmio: [0x40000000-0x401fffff]
[    0.952007] bus: 01 index 2 mmio: [0x48000000-0x57ffffff]
[    0.952062] bus: 01 index 3 mmio: [0x0-0x0]
[    0.952140] NET: Registered protocol family 2
[    0.952522] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.953389] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.959345] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.962504] TCP: Hash tables configured (established 131072 bind 65536)
[    0.962583] TCP reno registered
[    0.963035] NET: Registered protocol family 1
[    0.963453] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.541020]  it is
[    2.251462] Freeing initrd memory: 7242k freed
[    2.251713] cpufreq: No nForce2 chipset.
[    2.252179] audit: initializing netlink socket (disabled)
[    2.252292] type=2000 audit(1255894252.250:1): initialized
[    2.270366] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.273643] VFS: Disk quotas dquot_6.5.1
[    2.273874] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.275656] fuse init (API version 7.10)
[    2.275922] msgmni has been set to 1498
[    2.276544] alg: No test for stdrng (krng)
[    2.276638] io scheduler noop registered
[    2.276692] io scheduler anticipatory registered
[    2.276747] io scheduler deadline registered (default)
[    2.276859] io scheduler cfq registered
[    2.276943] PCI: VIA PCI bridge detected.Disabling DAC.
[    2.277017] pci 0000:00:14.0: Disabling VIA external APIC routing
[    2.277116] pci 0000:01:00.0: Boot video device
[    2.279446] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.279522] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.279864] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.279931] ACPI: Power Button (FF) [PWRF]
[    2.280150] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.280222] ACPI: Power Button (CM) [PBTN]
[    2.280521] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.280743] processor ACPI_CPU:00: registered as cooling_device0
[    2.282293] isapnp: Scanning for PnP cards...
[    2.639404] isapnp: No Plug & Play device found
[    2.642655] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.642903] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.643788] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.645576] brd: module loaded
[    2.646370] loop: module loaded
[    2.646651] Fixed MDIO Bus: probed
[    2.646719] PPP generic driver version 2.4.2
[    2.646930] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.647101] Driver 'sd' needs updating - please use bus_type methods
[    2.647178] Driver 'sr' needs updating - please use bus_type methods
[    2.648528] pata_via 0000:00:14.1: version 0.3.3
[    2.648966] scsi0 : pata_via
[    2.649384] scsi1 : pata_via
[    2.649516] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x2460 irq 14
[    2.649576] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x2468 irq 15
[    2.821242] ata1.00: ATA-5: WDC WD400BB-60BNA1, 18.20D18, max UDMA/100
[    2.821302] ata1.00: 78165360 sectors, multi 8: LBA 
[    2.861205] ata1.00: configured for UDMA/66
[    3.060296] ata2.00: ATAPI: COMPAQ DVD-ROM LTD122, IQH6, max UDMA/33
[    3.060424] ata2.01: ATAPI: LG CD-RW CED-8080B, 1.11, max MWDMA2
[    3.100282] ata2.00: configured for UDMA/33
[    3.140311] ata2.01: configured for MWDMA2
[    3.141254] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-60BN 18.2 PQ: 0 ANSI: 5
[    3.141579] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    3.141682] sd 0:0:0:0: [sda] Write Protect is off
[    3.141739] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.141806] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.142074] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    3.142171] sd 0:0:0:0: [sda] Write Protect is off
[    3.142227] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.142290] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.142362]  sda: sda1 sda2 < sda5 sda6 > sda3
[    3.180316] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.180512] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.181096] scsi 1:0:0:0: CD-ROM            COMPAQ   DVD-ROM LTD122   IQH6 PQ: 0 ANSI: 5
[    3.183803] sr0: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    3.183865] Uniform CD-ROM driver Revision: 3.20
[    3.184173] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.184294] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.184971] scsi 1:0:1:0: CD-ROM            LG       CD-RW CED-8080B  1.11 PQ: 0 ANSI: 5
[    3.188321] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    3.188553] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    3.188666] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    3.189093] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.189195] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.189293] uhci_hcd: USB Universal Host Controller Interface driver
[    3.189947] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.190006] PCI: setting IRQ 11 as level-triggered
[    3.190073] uhci_hcd 0000:00:14.2: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.190154] uhci_hcd 0000:00:14.2: UHCI Host Controller
[    3.190367] uhci_hcd 0000:00:14.2: new USB bus registered, assigned bus number 1
[    3.190464] uhci_hcd 0000:00:14.2: irq 11, io base 0x00002420
[    3.190723] usb usb1: configuration #1 chosen from 1 choice
[    3.190842] hub 1-0:1.0: USB hub found
[    3.190917] hub 1-0:1.0: 2 ports detected
[    3.191209] uhci_hcd 0000:00:14.3: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.191287] uhci_hcd 0000:00:14.3: UHCI Host Controller
[    3.191434] uhci_hcd 0000:00:14.3: new USB bus registered, assigned bus number 2
[    3.191520] uhci_hcd 0000:00:14.3: irq 11, io base 0x00002440
[    3.191760] usb usb2: configuration #1 chosen from 1 choice
[    3.191870] hub 2-0:1.0: USB hub found
[    3.191939] hub 2-0:1.0: 2 ports detected
[    3.192255] usbcore: registered new interface driver libusual
[    3.192435] usbcore: registered new interface driver usbserial
[    3.192513] USB Serial support registered for generic
[    3.192597] usbcore: registered new interface driver usbserial_generic
[    3.192657] usbserial: USB Serial Driver core
[    3.192813] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    3.193276] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.193347] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.193698] mice: PS/2 mouse device common for all mice
[    3.194122] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.194216] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    3.194506] device-mapper: uevent: version 1.0.3
[    3.194863] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.195063] device-mapper: multipath: version 1.0.5 loaded
[    3.195129] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.195431] EISA: Probing bus 0 at eisa.0
[    3.195501] Cannot allocate resource for EISA slot 1
[    3.195557] Cannot allocate resource for EISA slot 2
[    3.195660] EISA: Detected 0 cards.
[    3.195862] cpuidle: using governor ladder
[    3.196020] cpuidle: using governor menu
[    3.197423] TCP cubic registered
[    3.197813] NET: Registered protocol family 10
[    3.198901] lo: Disabled Privacy Extensions
[    3.199759] NET: Registered protocol family 17
[    3.199861] Bluetooth: L2CAP ver 2.11
[    3.199916] Bluetooth: L2CAP socket layer initialized
[    3.199973] Bluetooth: SCO (Voice Link) ver 0.6
[    3.200094] Bluetooth: SCO socket layer initialized
[    3.200269] Bluetooth: RFCOMM socket layer initialized
[    3.200341] Bluetooth: RFCOMM TTY layer initialized
[    3.200395] Bluetooth: RFCOMM ver 1.10
[    3.200581] IO APIC resources could be not be allocated.
[    3.200640] Using IPI No-Shortcut mode
[    3.200946] registered taskstats version 1
[    3.201282]   Magic number: 13:869:546
[    3.201350] scsi_generic sg2: hash matches
[    3.201478] mem null: hash matches
[    3.201622] rtc_cmos 00:05: setting system clock to 2009-10-18 19:30:53 UTC (1255894253)
[    3.201691] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.201747] EDD information not available.
[    3.203013] Freeing unused kernel memory: 548k freed
[    3.203385] Write protecting the kernel text: 4184k
[    3.203608] Write protecting the kernel read-only data: 1552k
[    3.510096] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.711842] usb 2-1: configuration #1 chosen from 1 choice
[    3.724031] Floppy drive(s): fd0 is 1.44M
[    3.742589] FDC 0 is a post-1991 82077
[    3.824268] 8139too Fast Ethernet driver 0.9.28
[    3.824423] 8139too 0000:00:06.0: enabling device (0004 -> 0007)
[    3.824498] 8139too 0000:00:06.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.826290] eth0: RealTek RTL8139 at 0x2000, 00:10:b5:d0:99:66, IRQ 11
[    3.826350] eth0:  Identified 8139 chip type 'RTL-8139C'
[    3.893946] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    3.894021] PCI: setting IRQ 10 as level-triggered
[    3.894032] ohci1394 0000:00:0c.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    3.945502] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[40400000-404007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.862252] usbcore: registered new interface driver hiddev
[    4.862532] usbcore: registered new interface driver usbhid
[    4.862592] usbhid: v2.6:USB HID core driver
[    4.937370] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:14.3/usb2/2-1/2-1:1.0/input/input3
[    4.943535] microsoft 0003:045E:009D.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:14.3-1/input0
[    4.948372] Marking TSC unstable due to TSC halts in idle
[    5.082917] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:14.3/usb2/2-1/2-1:1.1/input/input4
[    5.091700] microsoft 0003:045E:009D.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:14.3-1/input1
[    5.256695] PM: Starting manual resume from disk
[    5.256761] PM: Resume from partition 8:5
[    5.256765] PM: Checking hibernation image.
[    5.257202] PM: Resume from disk failed.
[    5.289693] kjournald starting.  Commit interval 5 seconds
[    5.289796] EXT3-fs: mounted filesystem with ordered data mode.
[    5.300440] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d01200a240fe]
[   11.725522] udev: starting version 141
[   13.768618] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[   13.833428] Adding 746948k swap on /dev/sda6.  Priority:-2 extents:1 across:746948k
[   14.284193] EXT3 FS on sda1, internal journal
[   14.988590] kjournald starting.  Commit interval 5 seconds
[   14.988965] EXT3 FS on sda3, internal journal
[   14.988979] EXT3-fs: mounted filesystem with ordered data mode.
[   15.472024] type=1505 audit(1255894265.768:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1699
[   15.621987] type=1505 audit(1255894265.918:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1703
[   15.622627] type=1505 audit(1255894265.918:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1703
[   15.622930] type=1505 audit(1255894265.918:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1703
[   15.623120] type=1505 audit(1255894265.918:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1703
[   16.045063] type=1505 audit(1255894266.338:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1708
[   16.045975] type=1505 audit(1255894266.338:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1708
[   16.149818] type=1505 audit(1255894266.438:9): operation="profile_load" name="/usr/sbin/named" name2="default" pid=1712
[   16.237226] type=1505 audit(1255894266.528:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1716
[   24.478383] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[   24.478397] PCI: setting IRQ 3 as level-triggered
[   24.478409] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 3 (level, low) -> IRQ 3
[   27.702020] eth0: link down
[   27.702913] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  113.007180] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  113.007947] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  123.480091] eth0: no IPv6 routers present

```

"iwlist scan":
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

I don't seem to have a wireless interface, presumably because "lshw -C network" lists the card as "UNCLAIMED".

"iwconfig":
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

"lsmod":
```

Module                  Size  Used by
hid_microsoft          11780  0 
usbhid                 42464  0 
ohci1394               38704  0 
ieee1394               94660  1 ohci1394
8139too                32256  0 
mii                    13440  1 8139too
floppy                 64196  0 
fbcon                  45856  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13696  1 fbcon
softcursor              9984  1 bitblit

```

Since the wireless worked in 8.10 (but not in 9.04 that I'm using now), tried installing linux-wireless-backports-jaunty and rebooting but that didn't help.

---

