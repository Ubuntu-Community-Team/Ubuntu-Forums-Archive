---
title: "RTL8192 WiFi not working"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by merlin1012 on 2011-10-31
Hoping someone can help.
Starting with a fresh install of 10.04; 
copied the supplied .tar.gz file to the desktop; 
extracted to a directory "beneath" the desktop; 
ran make (got some ERROR that was corrected by changing line 712 to 0); 
re-ran make; 
sudo make install; 
restart;
iwconfig yields:
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
sudo modprobe r8192se_pci (no change)

any more details that might be helpful please ask.

I've tried following the advice of others & this is as far as I've gotten. (What step on what Thread am I missing?)

Thanks in advance if you can help!

merl

---

### Post by hailtothethief on 2011-10-31
```
sudo lshw -C network
```

The output will help determine if the proper kernel module has been loaded.

'Not working' is a very vague assessment of the situation. What specifically did you try to do and what was the result?

Also, the output of
```
cat /var/log/dmesg
```
could be very helpful

---

### Post by merlin1012 on 2011-11-01
Hi Hailtothethief & thanks for responding;

When I wrote the initial message the "not working" seemed to make sense but after rereading it, it does seem too broad.

The output from lshw command:
```
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:67:80:4e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.101 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:41200000-41200fff ioport:3400(size=64) memory:41100000-4111ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 24:3c:20:07:88:d4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=unassociated
```

The output from the cat mesg command:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-34-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 (Ubuntu 2.6.32-34.77-generic 2.6.32.44+drm33.19)
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
[    0.000000]  BIOS-e820: 00000000000a00000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000000ffd0000 - 000000000fff0c00 (reserved)
[    0.000000]  BIOS-e820: 000000000fff0c00 - 000000000fffc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000fffc000 - 0000000010000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0xffd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 base 040000000 mask FFFC00000 write-combining
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000ffd0000 (usable)
[    0.000000]  modified: 000000000ffd0000 - 000000000fff0c00 (reserved)
[    0.000000]  modified: 000000000fff0c00 - 000000000fffc000 (ACPI NVS)
[    0.000000]  modified: 000000000fffc000 - 0000000010000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000000ffd0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 000fc00000 page 2M
[    0.000000]  000fc00000 - 000ffd0000 page 4k
[    0.000000] kernel direct mapping tables up to ffd0000 @ 7000-c000
[    0.000000] RAMDISK: 0b87a000 - 0c01bfab
[    0.000000] ACPI: RSDP 000f7380 00014 (v00 COMPAQ)
[    0.000000] ACPI: RSDT 0fff0c84 00028 (v01 COMPAQ CPQ0022  08030420 CPQ  00000001)
[    0.000000] ACPI: FACP 0fff0c00 00084 (v02 COMPAQ CPQ0022  00000002 CPQ  00000001)
[    0.000000] ACPI: DSDT 0fff0cac 06991 (v01 COMPAQ EVON400C 00010000 MSFT 0100000D)
[    0.000000] ACPI: FACS 0fffbe80 00040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0ffd0000
[    0.000000]   low ram: 0 - 0ffd0000
[    0.000000]   node 0 low ram: 00000000 - 0ffd0000
[    0.000000]   node 0 bootmap 00008000 - 00009ffc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000ffd0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e0ed8]    TEXT DATA BSS ==> [0000100000 - 00008e0ed8]
[    0.000000]   #4 [000b87a000 - 000c01bfab]          RAMDISK ==> [000b87a000 - 000c01bfab]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008e1000 - 00008e40cd]              BRK ==> [00008e1000 - 00008e40cd]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000a000]          BOOTMAP ==> [0000008000 - 000000a000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000ffd0
[    0.000000]   HighMem  0x0000ffd0 -> 0x0000ffd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000ffd0
[    0.000000] On node 0 totalpages: 65387
[    0.000000] free_area_init_node: node 0, pgdat c079a800, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60912 pages, LIFO batch:15
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 10000000:f0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36312 r0 d21032 u4194304
[    0.000000] pcpu-alloc: s36312 r0 d21032 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64875
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-34-generic root=UUID=a654417b-9eed-4023-9906-8289efd611a4 ro quiet splash
[    0.000000] PID hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1309760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 241720k/261952k available (4679k kernel code, 19532k reserved, 2124k data, 668k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd07d0000 - 0xff7fe000   ( 752 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xcffd0000   ( 255 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084c000   ( 668 kB)
[    0.000000]       .data : 0xc0591c47 - 0xc07a4dc8   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591c47   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 498.135 MHz processor.
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 996.27 BogoMIPS (lpj=1992540)
[    0.004089] Security Framework initialized
[    0.004190] AppArmor: AppArmor initialized
[    0.004226] Mount-cache hash table entries: 512
[    0.004727] Initializing cgroup subsys ns
[    0.004745] Initializing cgroup subsys cpuacct
[    0.004766] Initializing cgroup subsys memory
[    0.004804] Initializing cgroup subsys devices
[    0.004818] Initializing cgroup subsys freezer
[    0.004830] Initializing cgroup subsys net_cls
[    0.004916] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004932] CPU: L2 cache: 256K
[    0.004951] mce: CPU supports 5 MCE banks
[    0.005012] Performance Events: 
[    0.005024] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.005037] no hardware sampling interrupt available.
[    0.005048] p6 PMU driver.
[    0.005140] ... version:                0
[    0.005150] ... bit width:              32
[    0.005161] ... generic registers:      2
[    0.005172] ... value mask:             00000000ffffffff
[    0.005184] ... max period:             000000007fffffff
[    0.005196] ... fixed-purpose events:   0
[    0.005206] ... event mask:             0000000000000003
[    0.005224] Checking 'hlt' instruction... OK.
[    0.022140] SMP alternatives: switching to UP code
[    0.046005] Freeing SMP alternatives: 19k freed
[    0.046078] ACPI: Core revision 20090903
[    0.068959] ACPI: setting ELCR to 0200 (from 0800)
[    0.072030] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.072067] ftrace: allocating 21731 entries in 43 pages
[    0.076352] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.076373] weird, boot CPU (#0) not listed by the BIOS.
[    0.076384] SMP motherboard not detected.
[    0.076397] Local APIC not detected. Using dummy APIC emulation.
[    0.076407] SMP disabled
[    0.077266] Brought up 1 CPUs
[    0.077286] Total of 1 processors activated (996.27 BogoMIPS).
[    0.077353] CPU0 attaching NULL sched-domain.
[    0.078123] devtmpfs: initialized
[    0.081176] regulator: core version 0.5
[    0.081230] Time: 23:05:55  Date: 11/01/11
[    0.081476] NET: Registered protocol family 16
[    0.082034] EISA bus registered
[    0.082087] ACPI: bus type pci registered
[    0.084034] PCI: PCI BIOS revision 2.10 entry at 0xf0491, last bus=1
[    0.084046] PCI: Using configuration type 1 for base access
[    0.089079] bio: create slab <bio-0> at 0
[    0.091980] ACPI: EC: Look up EC in DSDT
[    0.144029] ACPI: Interpreter enabled
[    0.144050] ACPI: (supports S0 S1 S3 S4 S5)
[    0.144156] ACPI: Using PIC for interrupt routing
[    0.183249] ACPI: Power Resource [C11E] (on)
[    0.183587] ACPI: Power Resource [C132] (on)
[    0.183938] ACPI: Power Resource [C137] (on)
[    0.184307] ACPI: Power Resource [C13A] (on)
[    0.184468] ACPI: Power Resource [C146] (on)
[    0.184784] ACPI: Power Resource [C1C6] (off)
[    0.185076] ACPI: Power Resource [C1C7] (off)
[    0.185367] ACPI: Power Resource [C1C8] (off)
[    0.188776] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.206749] ACPI: PCI Root Bridge [C03A] (0000:00)
[    0.206928] pci 0000:00:00.0: reg 10 32bit mmio pref: [0x50000000-0x53ffffff]
[    0.207112] pci 0000:00:04.0: reg 10 32bit mmio: [0x41180000-0x41180fff]
[    0.207153] pci 0000:00:04.0: supports D1 D2
[    0.207167] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot
[    0.207183] pci 0000:00:04.0: PME# disabled
[    0.207359] pci 0000:00:07.1: reg 20 io port: [0x3460-0x346f]
[    0.207468] pci 0000:00:07.2: reg 20 io port: [0x3440-0x345f]
[    0.207613] pci 0000:00:07.3: quirk: region 1000-103f claimed by PIIX4 ACPI
[    0.207631] pci 0000:00:07.3: quirk: region 1100-110f claimed by PIIX4 SMB
[    0.207651] pci 0000:00:07.3: PIIX4 devres C PIO at 0100-0107
[    0.207667] pci 0000:00:07.3: PIIX4 devres I PIO at 00e0-00e3
[    0.207682] pci 0000:00:07.3: PIIX4 devres J PIO at 00f8-00fb
[    0.207765] pci 0000:00:08.0: reg 10 io port: [0x3000-0x30ff]
[    0.207850] pci 0000:00:08.0: supports D1 D2
[    0.207862] pci 0000:00:08.0: PME# supported from D1 D2 D3hot
[    0.207877] pci 0000:00:08.0: PME# disabled
[    0.207946] pci 0000:00:09.0: reg 10 32bit mmio: [0x41200000-0x41200fff]
[    0.207969] pci 0000:00:09.0: reg 14 io port: [0x3400-0x343f]
[    0.207990] pci 0000:00:09.0: reg 18 32bit mmio: [0x41100000-0x4111ffff]
[    0.208073] pci 0000:00:09.0: supports D1 D2
[    0.208086] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.208102] pci 0000:00:09.0: PME# disabled
[    0.208172] pci 0000:00:09.1: reg 10 io port: [0x3470-0x3477]
[    0.208193] pci 0000:00:09.1: reg 14 32bit mmio: [0x41280000-0x41280fff]
[    0.208264] pci 0000:00:09.1: supports D1 D2
[    0.208277] pci 0000:00:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.208292] pci 0000:00:09.1: PME# disabled
[    0.208437] pci 0000:01:00.0: reg 10 32bit mmio: [0x40000000-0x40ffffff]
[    0.208458] pci 0000:01:00.0: reg 14 io port: [0x2000-0x20ff]
[    0.208479] pci 0000:01:00.0: reg 18 32bit mmio: [0x41000000-0x41000fff]
[    0.208516] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.208561] pci 0000:01:00.0: supports D1 D2
[    0.208636] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.208653] pci 0000:00:01.0: bridge 32bit mmio: [0x40000000-0x410fffff]
[    0.208707] pci_bus 0000:00: on NUMA node 0
[    0.208732] ACPI: PCI Interrupt Routing Table [\_SB_.C03A._PRT]
[    0.208981] ACPI: PCI Interrupt Routing Table [\_SB_.C03A.C03B._PRT]
[    0.243774] ACPI: PCI Interrupt Link [C090] (IRQs 5 10 *11)
[    0.244505] ACPI: PCI Interrupt Link [C091] (IRQs 11) *0, disabled.
[    0.245242] ACPI: PCI Interrupt Link [C092] (IRQs 5 10 *11)
[    0.245978] ACPI: PCI Interrupt Link [C093] (IRQs 5 10 *11)
[    0.246645] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.246660] vgaarb: loaded
[    0.247227] SCSI subsystem initialized
[    0.247524] libata version 3.00 loaded.
[    0.247908] usbcore: registered new interface driver usbfs
[    0.247974] usbcore: registered new interface driver hub
[    0.248161] usbcore: registered new device driver usb
[    0.248877] ACPI: WMI: Mapper loaded
[    0.248889] PCI: Using ACPI for IRQ routing
[    0.249385] NetLabel: Initializing
[    0.249397] NetLabel:  domain hash size = 128
[    0.249406] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.249464] NetLabel:  unlabeled traffic allowed by default
[    0.249645] Switching to clocksource tsc
[    0.257141] AppArmor: AppArmor Filesystem Enabled
[    0.257237] pnp: PnP ACPI init
[    0.257310] ACPI: bus type pnp registered
[    0.314007] pnp: PnP ACPI: found 14 devices
[    0.314021] ACPI: ACPI bus type pnp unregistered
[    0.314036] PnPBIOS: Disabled by ACPI PNP
[    0.314087] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.314106] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.314123] system 00:00: iomem range 0x100000-0xfffffff could not be reserved
[    0.314217] system 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[    0.314235] system 00:0d: ioport range 0x530-0x537 has been reserved
[    0.314252] system 00:0d: ioport range 0x800-0x87f has been reserved
[    0.314268] system 00:0d: ioport range 0x1000-0x103f has been reserved
[    0.314284] system 00:0d: ioport range 0x1100-0x110f has been reserved
[    0.314302] system 00:0d: iomem range 0xfff80000-0xffffffff has been reserved
[    0.349768] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.349784] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.349803] pci 0000:00:01.0:   MEM window: 0x40000000-0x410fffff
[    0.349820] pci 0000:00:01.0:   PREFETCH window: 0x18000000-0x180fffff
[    0.349840] pci 0000:00:04.0: CardBus bridge, secondary bus 0000:02
[    0.349854] pci 0000:00:04.0:   IO window: 0x001400-0x0014ff
[    0.349870] pci 0000:00:04.0:   IO window: 0x001800-0x0018ff
[    0.349886] pci 0000:00:04.0:   PREFETCH window: 0x10000000-0x13ffffff
[    0.349903] pci 0000:00:04.0:   MEM window: 0x14000000-0x17ffffff
[    0.351055] ACPI: PCI Interrupt Link [C090] enabled at IRQ 11
[    0.351070] PCI: setting IRQ 11 as level-triggered
[    0.351090] pci 0000:00:04.0: PCI INT A -> Link[C090] -> GSI 11 (level, low) -> IRQ 11
[    0.351115] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.351130] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.351145] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.351159] pci_bus 0000:01: resource 1 mem: [0x40000000-0x410fffff]
[    0.351174] pci_bus 0000:01: resource 2 pref mem [0x18000000-0x180fffff]
[    0.351189] pci_bus 0000:02: resource 0 io:  [0x1400-0x14ff]
[    0.351202] pci_bus 0000:02: resource 1 io:  [0x1800-0x18ff]
[    0.351217] pci_bus 0000:02: resource 2 pref mem [0x10000000-0x13ffffff]
[    0.351231] pci_bus 0000:02: resource 3 mem: [0x14000000-0x17ffffff]
[    0.351399] NET: Registered protocol family 2
[    0.351874] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.353374] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.353582] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.353775] TCP: Hash tables configured (established 8192 bind 8192)
[    0.353787] TCP reno registered
[    0.354129] NET: Registered protocol family 1
[    0.354282] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.354394] pci 0000:00:09.0: Firmware left e100 interrupts enabled; disabling
[    0.354426] pci 0000:01:00.0: Boot video device
[    0.355037] cpufreq-nforce2: No nForce2 chipset.
[    0.355151] Scanning for low memory corruption every 60 seconds
[    0.355754] audit: initializing netlink socket (disabled)
[    0.355799] type=2000 audit(1320188755.354:1): initialized
[    0.399124] Trying to unpack rootfs image as initramfs...
[    0.446583] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.467591] VFS: Disk quotas dquot_6.5.2
[    0.468018] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.471526] fuse init (API version 7.13)
[    0.472012] msgmni has been set to 472
[    0.478670] alg: No test for stdrng (krng)
[    0.478983] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.478999] io scheduler noop registered
[    0.479009] io scheduler anticipatory registered
[    0.479020] io scheduler deadline registered
[    0.479280] io scheduler cfq registered (default)
[    0.479713] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.479828] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.480553] ACPI: AC Adapter [C179] (off-line)
[    0.480991] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.481018] ACPI: Sleep Button [C17A]
[    0.481220] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.481504] ACPI: Lid Switch [C17B]
[    0.481731] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.481746] ACPI: Power Button [PWRF]
[    0.482553] fan PNP0C0B:00: registered as cooling_device0
[    0.482582] ACPI: Fan [C1C9] (off)
[    0.483184] fan PNP0C0B:01: registered as cooling_device1
[    0.483212] ACPI: Fan [C1CA] (off)
[    0.483796] fan PNP0C0B:02: registered as cooling_device2
[    0.483824] ACPI: Fan [C1CB] (off)
[    0.484664] Marking TSC unstable due to TSC halts in idle
[    0.484915] Switching to clocksource acpi_pm
[    0.485280] processor LNXCPU:00: registered as cooling_device3
[    0.555472] thermal LNXTHERM:01: registered as thermal_zone0
[    0.555522] ACPI: Thermal Zone [TZ1] (21 C)
[    0.570318] ACPI: Battery Slot [C175] (battery absent)
[    0.570672] ACPI: Battery Slot [C176] (battery absent)
[    0.571016] ACPI: Battery Slot [C177] (battery absent)
[    0.571097] isapnp: Scanning for PnP cards...
[    0.586247] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.586450] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.586777] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.587502] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.641500] ACPI: PCI Interrupt Link [C092] enabled at IRQ 11
[    0.641526] serial 0000:00:09.1: PCI INT A -> Link[C092] -> GSI 11 (level, low) -> IRQ 11
[    0.660627] brd: module loaded
[    0.663114] loop: module loaded
[    0.663571] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.670442] ata_piix 0000:00:07.1: version 2.13
[    0.670964] scsi0 : ata_piix
[    0.671468] scsi1 : ata_piix
[    0.675841] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x3460 irq 14
[    0.675859] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x3468 irq 15
[    0.683337] Fixed MDIO Bus: probed
[    0.683525] PPP generic driver version 2.4.2
[    0.683809] tun: Universal TUN/TAP device driver, 1.6
[    0.683821] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.693525] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.693654] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.693720] uhci_hcd: USB Universal Host Controller Interface driver
[    0.697726] ACPI: PCI Interrupt Link [C093] enabled at IRQ 11
[    0.697749] uhci_hcd 0000:00:07.2: PCI INT D -> Link[C093] -> GSI 11 (level, low) -> IRQ 11
[    0.697782] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    0.698014] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    0.698085] uhci_hcd 0000:00:07.2: irq 11, io base 0x00003440
[    0.698598] usb usb1: configuration #1 chosen from 1 choice
[    0.698760] hub 1-0:1.0: USB hub found
[    0.698800] hub 1-0:1.0: 2 ports detected
[    0.699236] PNP: PS/2 Controller [PNP0303:C143,PNP0f0e:C144] at 0x60,0x64 irq 1,12
[    0.701448] i8042.c: Detected active multiplexing controller, rev 1.0.
[    0.705539] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.705576] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.712156] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.712347] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.712491] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.713149] mice: PS/2 mouse device common for all mice
[    0.713827] rtc_cmos 00:09: RTC can wake from S4
[    0.714048] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.714145] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.714628] device-mapper: uevent: version 1.0.3
[    0.716545] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.724005] device-mapper: multipath: version 1.1.0 loaded
[    0.724091] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.724870] EISA: Probing bus 0 at eisa.0
[    0.724892] Cannot allocate resource for EISA slot 1
[    0.724904] Cannot allocate resource for EISA slot 2
[    0.724916] Cannot allocate resource for EISA slot 3
[    0.724954] EISA: Detected 0 cards.
[    0.727797] cpuidle: using governor ladder
[    0.728159] cpuidle: using governor menu
[    0.730508] TCP cubic registered
[    0.731365] NET: Registered protocol family 10
[    0.742559] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.746757] NET: Registered protocol family 17
[    0.748986] Using IPI No-Shortcut mode
[    0.749405] PM: Resume from disk failed.
[    0.749629] registered taskstats version 1
[    0.750192]   Magic number: 3:60:99
[    0.750437] rtc_cmos 00:09: setting system clock to 2011-11-01 23:05:55 UTC (1320188755)
[    0.750454] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.750464] EDD information not available.
[    0.841843] ata2.00: ATAPI: Compaq  DRN8040B, 1.12, max MWDMA2
[    0.841997] ata2.01: ATAPI: SD-R2102, 1A16, max MWDMA2
[    0.852446] ata2.00: configured for MWDMA2
[    0.868493] ata2.01: configured for MWDMA2
[    0.955747] ACPI: Battery Slot [C174] (battery present)
[    1.120846] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    1.380374] isapnp: No Plug & Play device found
[    1.387746] usb 1-2: configuration #1 chosen from 1 choice
[    1.391522] hub 1-2:1.0: USB hub found
[    1.393306] hub 1-2:1.0: 4 ports detected
[    1.531826] ata1.00: ATA-5: IBM-DJSA-220, JS4OAC0A, max UDMA/66
[    1.531845] ata1.00: 39070080 sectors, multi 16: LBA 
[    1.575049] ata1.00: configured for UDMA/33
[    1.575613] scsi 0:0:0:0: Direct-Access     ATA      IBM-DJSA-220     JS4O PQ: 0 ANSI: 5
[    1.576422] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.577115] sd 0:0:0:0: [sda] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.577381] sd 0:0:0:0: [sda] Write Protect is off
[    1.577397] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.577535] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.578236]  sda:
[    1.594182] scsi 1:0:0:0: CD-ROM            COMPAQ   DVD-ROM DRN8040B 1.12 PQ: 0 ANSI: 5
[    1.601453] sr0: scsi3-mmc drive: 0x/24x cd/rw xa/form2 cdda tray
[    1.601472] Uniform CD-ROM driver Revision: 3.20
[    1.601979] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.602258] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.607036] scsi 1:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2102 1A16 PQ: 0 ANSI: 5
[    1.620515] sr1: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.621064] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.621358] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.686352] usb 1-2.1: new full speed USB device using uhci_hcd and address 3
[    1.919183] usb 1-2.1: configuration #1 chosen from 1 choice
[    1.974947]  sda1 sda2 <
[    1.981038] Freeing initrd memory: 7815k freed
[    2.024925]  sda5 >
[    2.026166] usb 1-2.4: new full speed USB device using uhci_hcd and address 4
[    2.026867] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.026945] Freeing unused kernel memory: 668k freed
[    2.031124] Write protecting the kernel text: 4680k
[    2.031301] Write protecting the kernel read-only data: 1844k
[    2.121180] udev: starting version 151
[    2.151468] usb 1-2.4: configuration #1 chosen from 1 choice
[    3.085295] Floppy drive(s): fd0 is 1.44M
[    3.114565] FDC 0 is a post-1991 82077
[    3.321097] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    3.321114] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.321241] e100 0000:00:09.0: PCI INT A -> Link[C092] -> GSI 11 (level, low) -> IRQ 11
[    3.409907] e100 0000:00:09.0: PME# disabled
[    3.429208] e100: eth0: e100_probe: addr 0x41200000, irq 11, MAC addr 00:d0:59:67:80:4e
[    3.542131] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   16.145787] Adding 732152k swap on /dev/sda5.  Priority:-1 extents:1 across:732152k 
[   18.062566] udev: starting version 151
[   20.572849] type=1505 audit(1320188775.321:2):  operation="profile_load" pid=511 name="/sbin/dhclient3"
[   20.575092] type=1505 audit(1320188775.321:3):  operation="profile_load" pid=511 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.644587] type=1505 audit(1320188775.393:4):  operation="profile_load" pid=511 name="/usr/lib/connman/scripts/dhclient-script"
[   20.800770] Linux agpgart interface v0.103
[   20.827494] piix4_smbus 0000:00:07.3: SMBus Host Controller at 0x1100, revision 0
[   20.831370] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.008265] Bluetooth: Core ver 2.15
[   21.008790] NET: Registered protocol family 31
[   21.008801] Bluetooth: HCI device and connection manager initialized
[   21.008815] Bluetooth: HCI socket layer initialized
[   21.351353] rtw driver version=v2.0.1170.20101112
[   21.351537] register rtl8192_netdev_ops to netdev_ops
[   21.351573] 
[   21.351577] 8712_usb_endpoint_descriptor(0):
[   21.351587] bLength=7
[   21.351595] bDescriptorType=5
[   21.351603] bEndpointAddress=81
[   21.351611] wMaxPacketSize=40
[   21.351619] bInterval=0
[   21.351627] 
[   21.351631] 8712_usb_endpoint_descriptor(1):
[   21.351640] bLength=7
[   21.351647] bDescriptorType=5
[   21.351655] bEndpointAddress=2
[   21.351663] wMaxPacketSize=40
[   21.351671] bInterval=0
[   21.351678] 
[   21.351682] 8712_usb_endpoint_descriptor(2):
[   21.351691] bLength=7
[   21.351699] bDescriptorType=5
[   21.351707] bEndpointAddress=3
[   21.351714] wMaxPacketSize=40
[   21.351722] bInterval=0
[   21.351730] 
[   21.351734] 8712_usb_endpoint_descriptor(3):
[   21.351743] bLength=7
[   21.351750] bDescriptorType=5
[   21.351758] bEndpointAddress=84
[   21.351766] wMaxPacketSize=40
[   21.351774] bInterval=1
[   21.351783] nr_endpoint=4, in_num=2, out_num=2
[   21.351789] 
[   21.351796] 8192cu: NON USB_SPEED_HIGH
[   21.364535] Chip Version ID: VERSION_NORMAL_TSMC_CHIP_88C.
[   21.366831] EEPROM type is E-FUSE
[   21.366849] ====> ReadAdapterInfo8192C
[   21.367830] Boot from EFUSE, Autoload Success !
[   21.432021] rtw_efuse_get_max_phy_size...eeprompriv.efuse_phy_max_size(504)
[   21.476915] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   21.482093] usbcore: registered new interface driver btusb
[   21.513597] parport_pc 00:05: reported by Plug and Play ACPI
[   21.513680] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   21.597514] lp: driver loaded but no devices found
[   21.607610] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[   21.666858] lp0: using parport0 (interrupt-driven).
[   21.709804] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0x50000000
[   21.793681] psmouse serio4: ID: 10 00 64
[   21.793835] ppdev: user-space parallel port driver
[   22.197129] IBM TrackPoint firmware: 0x0b, buttons: 3/3
[   22.209989] irda_init()
[   22.210046] NET: Registered protocol family 23
[   22.226934] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/input/input5
[   22.255882] yenta_cardbus 0000:00:04.0: CardBus bridge found [0e11:b103]
[   22.256305] yenta_cardbus 0000:00:04.0: Enabling burst memory read transactions
[   22.256329] yenta_cardbus 0000:00:04.0: Using CSCINT to route CSC interrupts to PCI
[   22.256343] yenta_cardbus 0000:00:04.0: Routing CardBus interrupts to PCI
[   22.256364] yenta_cardbus 0000:00:04.0: TI: mfunc 0x01001002, devctl 0x64
[   22.496811] yenta_cardbus 0000:00:04.0: ISA IRQ mask 0x0438, PCI irq 11
[   22.496829] yenta_cardbus 0000:00:04.0: Socket status: 30000006
[   22.878682] rtllib_crypt: registered algorithm 'NULL'
[   22.878702] rtllib_crypt: registered algorithm 'TKIP'
[   22.878713] rtllib_crypt: registered algorithm 'CCMP'
[   22.878724] rtllib_crypt: registered algorithm 'WEP'
[   22.878734] 
[   22.878738] Linux kernel driver for RTL8192 based WLAN cards
[   22.878748] Copyright (c) 2007-2008, Realsil Wlan Driver
[   22.926022] vga16fb: initializing
[   22.926049] vga16fb: mapped to 0xc00a0000
[   22.927000] fb0: VGA16 VGA frame buffer device
[   22.983624] found SMC SuperIO Chip (devid=0x0a rev=00 base=0x00e0): FDC37N971
[   22.983718] smsc_ircc_present: can't get sir_base of 0x3e8
[   23.034546] Bluetooth: L2CAP ver 2.14
[   23.034562] Bluetooth: L2CAP socket layer initialized
[   23.848798] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.848816] Bluetooth: BNEP filters: protocol multicast
[   23.864204] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[   23.867494] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   23.869888] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   23.870656] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   23.873856] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   24.221867] Console: switching to colour frame buffer device 80x30
[   24.362925] Bridge firewalling registered
[   24.864741] Bluetooth: SCO (Voice Link) ver 0.6
[   24.864758] Bluetooth: SCO socket layer initialized
[   25.165789] e100 0000:00:09.0: firmware: requesting e100/d101s_ucode.bin
[   25.260404] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.264399] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   25.265044] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   25.510619] Maestro3 0000:00:08.0: PCI INT A -> Link[C092] -> GSI 11 (level, low) -> IRQ 11
[   25.510652] Maestro3 0000:00:08.0: firmware: requesting ess/maestro3_assp_kernel.fw
[   25.515702] type=1505 audit(1320188780.261:5):  operation="profile_load" pid=727 name="/usr/share/gdm/guest-session/Xsession"
[   25.566299] type=1505 audit(1320188780.313:6):  operation="profile_replace" pid=732 name="/sbin/dhclient3"
[   25.575357] type=1505 audit(1320188780.321:7):  operation="profile_replace" pid=732 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.577923] type=1505 audit(1320188780.325:8):  operation="profile_replace" pid=732 name="/usr/lib/connman/scripts/dhclient-script"
[   25.602784] Maestro3 0000:00:08.0: firmware: requesting ess/maestro3_assp_minisrc.fw
[   25.845078] EEPROMVID = 0x0bda
[   25.845092] EEPROMPID = 0x8176
[   25.845101] EEPROMCustomerID : 0x00
[   25.845110] EEPROMSubCustomerID: 0x00
[   25.845119] RT_CustomerID: 0x00
[   25.845132] RT_ChannelPlan: 0x02
[   25.845141] _ReadBoardType(0)
[   25.845149] ### AntDivCfg(0)
[   25.845161] BT Coexistance = disable
[   25.845173] _ReadHWPDSelection...bHWPwrPindetect(0) bSupportRemoteWakeup(0)
[   25.845184] <==== ReadAdapterInfo8192C
[   25.845199] MAC Address from efuse= 24:3c:20:07:88:d4
[   25.854493] usbcore: registered new interface driver rtw_usb_drv
[   26.201505] +871x_drv - drv_open, bup=0
[   26.355210] type=1505 audit(1320188781.101:9):  operation="profile_load" pid=733 name="/usr/bin/evince"
[   26.395899] type=1505 audit(1320188781.141:10):  operation="profile_load" pid=733 name="/usr/bin/evince-previewer"
[   26.434034] type=1505 audit(1320188781.181:11):  operation="profile_load" pid=733 name="/usr/bin/evince-thumbnailer"
[   26.531772] type=1505 audit(1320188781.277:12):  operation="profile_load" pid=747 name="/usr/lib/cups/backend/cups-pdf"
[   26.536957] type=1505 audit(1320188781.285:13):  operation="profile_load" pid=747 name="/usr/sbin/cupsd"
[   26.578515] type=1505 audit(1320188781.325:14):  operation="profile_load" pid=748 name="/usr/sbin/tcpdump"
[   26.865936]  ===> FirmwareDownload91C() fw:Rtl819XFwImageArray_TSMC
[   26.866057] fw_ver=v60, fw_subver=0, sig=0x88c0
[   27.153846] fw download ok!
[   27.153863] Set RF Chip ID to RF_6052 and RF type to 1T1R.
[   27.153874] rf_chip=0x4, rf_type=0x3
[   28.705602] IQK:Start!!!
[   28.791587] Path A IQK Success!!
[   28.859567] Path A IQK Success!!
[   28.899575] IQK: final_candidate is 0
[   28.899596] IQK: RegE94=100 RegE9C=12 RegEA4=fe RegEAC=2 RegEB4=0 RegEBC=0 RegEC4=0 RegECC=0
[   28.899605]  Path A IQ Calibration Success !
```

I hope this helps!

As detailed in my original post, I was able to follow information from other threads to get to this point.  Currently the RTL8192 USB adapter is blinking & the iwconfig result is **not** 4 "no connection".

Thanks & appreciate the help;
Merl

---

### Post by hailtothethief on 2011-11-01
Hmm, interesting.

After reading your lshw, I can see your wireless card has no driver associated with it. In your dmesg I can see 8192cu and an rtl driver being loaded, but couldn't see anything except success messages. This is odd.

Reading your modprobe command, you're using the rtl8192se_pci driver. However, you said the Realtek USB adapter is blinking. Reading the info for the rtl8192se (and the name of the driver) I believe that is a PCI device?

This would lead me to believe that you're modprobe'ing for the wrong driver. My _guess_ is that you need rtl8192u, but that's just a wild guess. Running

```
lspci
```

and

```
lsusb
```

will quickly clear things up.

Also of interest are

```
uname -r
```

and

```
lsmod
```

Hang in there, we've almost got it ;)

---

### Post by merlin1012 on 2011-11-03
Hi HTTT;

Thanks again for the help.  Was thinking that maybe if I just typed in the info in Network Connection it might work, but I'm more used to fields getting filled in.

Here's the results...

lspci:
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1211
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 09)
00:09.1 Serial controller: Agere Systems LT WinModem
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
```

lsusb:
```
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 049f:0027 Compaq Computer Corp. Bluetooth Multiport Module by Compaq
Bus 001 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

uname -r
```
2.6.32-34-generic
```

lsmod
```
Module                  Size  Used by
binfmt_misc             6587  1 
snd_maestro3           15898  2 
snd_ac97_codec        100646  1 snd_maestro3
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
sco                     7949  2 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
bridge                 45614  0 
snd_page_alloc          7076  1 snd_pcm
snd_seq_dummy           1338  0 
stp                     1655  1 bridge
bnep                    9436  2 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fbcon                  35102  71 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tileblit                1999  1 fbcon
r8192se_pci           447966  0 
l2cap                  30656  3 bnep
font                    7557  1 fbcon
pcmcia                 30784  0 
snd_timer              19098  2 snd_pcm,snd_seq
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vga16fb                11385  1 
yenta_socket           20408  1 
vgastate                8961  1 vga16fb
snd                    54244  14 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                  186844  0 
rsrc_nonstatic         10015  1 yenta_socket
lp                      7028  0 
ppdev                   5259  0 
intel_agp              24375  1 
btusb                  11053  2 
psmouse                63677  0 
crc_ccitt               1339  1 irda
parport_pc             25962  1 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               8335  0 
bluetooth              49892  10 sco,bnep,l2cap,btusb
shpchp                 28835  0 
soundcore               6620  1 snd
agpgart                31724  1 intel_agp
serio_raw               3978  0 
8192cu                309895  0 
parport                32635  3 lp,ppdev,parport_pc
e100                   28211  0 
mii                     4381  1 e100
floppy                 53016  0 
```

If there's anything about the hardware that may matter please ask, this is a Compaq Evo N400c laptop.  The adapter is plugged into the docking station as the usb's on the laptop tend not to function (tested with a flash drive).  Not sure if this matters & I hope it doesn't distract you.

Thanks again!

Merl

---

### Post by merlin1012 on 2011-11-17
I have WiFi!!!

Here's what I did (with the help of someone asking a question on another forum, thread #1329254 on Ubuntu Forums & [http://wiki.debian.org/rtl819x):]("http://wiki.debian.org/rtl819x%29:")
- edited etc/modules: replaced r8192se_pci with r8192s_usb
- using Network Connections (Ubuntu GUI), entered network name (SSID) & key (same as essid & key in iwconfig)
- re-ran (after changing to the driver directory):
   - make clean
   - make
   - make install
- reboot

The adapter still just blinks, but it connects!!!

---

