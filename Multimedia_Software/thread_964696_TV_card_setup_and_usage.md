---
title: "TV card setup and usage"
date: 2008-10-31
forum: Multimedia Software
---

### Post by soxs on 2008-10-31
Hi, I just got a shiny "used" tvcard, named ***Terratec Sinergy 1200DVB-S***.

**lspci**:
```
03:05.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
03:06.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
```

Note: the first is my DVB-T TV-card (which unfortunatly won't give me the program I require)
The second one is the one I'd likt to set up.

**lsmod | grep 7146**:
```
saa7146_vv             60928  1 budget_av
videodev               46720  4 tuner,saa7134,compat_ioctl32,saa7146_vv
v4l1_compat            24580  2 saa7146_vv,videodev
videobuf_dma_sg        22788  4 saa7134_alsa,saa7134_dvb,saa7134,saa7146_vv
videobuf_core          29956  4 videobuf_dvb,saa7134,saa7146_vv,videobuf_dma_sg
saa7146                27400  3 budget_av,saa7146_vv,budget_core

```
as far as I can say a bunch of drivers are loaded and the card should just work fine.


What I need to know is how to specify which TV card kaffeine/mplayer/VLC/xine/tvtime(which seems to be sefaulting all the time) should use and how to successfully scan for programs?

How to set up Astra-19... channels.conf

I read 2 or 3 howtos but most didn't work at all and or only got me one little step forward, but not where I wanted to be.

Note: mplayer dummy output works:
```
mplayer -tv driver=dummy:width=640:height=480 -vo aa tv://
```

_**Edit:**_
I only have /dev/video0 and no /dev/video1 (same for vbi0/vbi1) though under /dev/dvb/ there are 2 adapters which seems to be ok.

_**Edit:**_
I found a way (unfortunatly GUI :-S ) to tell VLC which adapter and some other stuff under "Open Media" (Last tab).
But there I get asked for:
- Transponder/Multiplexer-Frequency
- Transponder-Symbolrate

Where do I get them from?

---

### Post by soxs on 2008-11-01
[SIZE="7"]***[color="red"]_[color="yellowgreen"]~bump~[/color]_[/color]***[/SIZE]

---

### Post by soxs on 2008-11-02
Is really nobody out there who can tell what to do, or at least what measures he took to make his DVB-S card running?
Anyone.. plx :_(

---

### Post by steefjeqv on 2008-11-03
Hi,

If you can start Kaffeine, you should have a "digital tv" icon.
In the settings menu you then can select "DVB" and there should be two DVB adapters (one DVB-T and one DVB-S).

If this doesn't work then it's best to check the output of dmesg (and post it here).

I have used the Terratec 1200 (DVB-T version) myself and it should work.
If my memory serves me well, I did have to add firmware to get it up and running.
If this is the case, dmesg should complain about not being able to load the needed files.

Greetings,
Steven

---

### Post by soxs on 2008-11-03
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Oct 30 04:12:22 UTC 2008 (Ubuntu 2.6.27-7.15-generic)
[    0.000000] Command line: root=UUID=1d14f3fb-f958-42b9-a78e-85510b97c442 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfeb0000 - 00000000cfec0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfec0000 - 00000000cfef0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xcfeb0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfeb0000 page 4k
[    0.000000] kernel direct mapping tables up to cfeb0000 @ 8000-e000
[    0.000000] last_map_addr: cfeb0000 end: cfeb0000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ c000-12000
[    0.000000] last_map_addr: 130000000 end: 130000000
[    0.000000] RAMDISK: 3775d000 - 37fef769
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000FAB90, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFEB0000, 003C (r1 082608 RSDT1644 20080826 MSFT       97)
[    0.000000] ACPI: FACP CFEB0200, 0084 (r1 A_M_I  OEMFACP  12000601 MSFT       97)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080609]
[    0.000000] ACPI: DSDT CFEB0440, 8F15 (r1  AS159 AS159013       13 INTL 20051117)
[    0.000000] ACPI: FACS CFEC0000, 0040
[    0.000000] ACPI: APIC CFEB0390, 006C (r1 082608 APIC1644 20080826 MSFT       97)
[    0.000000] ACPI: MCFG CFEB0400, 003C (r1 082608 OEMMCFG  20080826 MSFT       97)
[    0.000000] ACPI: OEMB CFEC0040, 0072 (r1 082608 OEMB1644 20080826 MSFT       97)
[    0.000000] ACPI: HPET CFEBA440, 0038 (r1 082608 OEMHPET  20080826 MSFT       97)
[    0.000000] ACPI: SSDT CFEBA480, 0544 (r1 A M I  POWERNOW        1 AMD         1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000d000 -  0000000000032fff] pages 26
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [003775d000 - 0037fef769]          RAMDISK ==> [003775d000 - 0037fef769]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #6 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20004bfffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfeb0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048143
[    0.000000]   DMA zone: 2109 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 831216 pages, LIFO batch:31
[    0.000000]   Normal zone: 193536 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e7000
[    0.000000] PM: Registered nosave memory: 00000000000e7000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfeb0000 - 00000000cfec0000
[    0.000000] PM: Registered nosave memory: 00000000cfec0000 - 00000000cfef0000
[    0.000000] PM: Registered nosave memory: 00000000cfef0000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:30000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1026861
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=1d14f3fb-f958-42b9-a78e-85510b97c442 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2211.065 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 8b60000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Please enable the IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.004000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.004000] Memory: 4045316k/4980736k available (3112k kernel code, 147256k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 4422.12 BogoMIPS (lpj=8844248)
[    0.004035] Security Framework initialized
[    0.004042] SELinux:  Disabled at boot.
[    0.004056] AppArmor: AppArmor initialized
[    0.004411] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.007026] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008244] Mount-cache hash table entries: 256
[    0.008432] Initializing cgroup subsys ns
[    0.008436] Initializing cgroup subsys cpuacct
[    0.008439] Initializing cgroup subsys memory
[    0.008454] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008456] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008458] CPU 0/0 -> Node 0
[    0.008462] tseg: 0000000000
[    0.008478] CPU: Physical Processor ID: 0
[    0.008479] CPU: Processor Core ID: 0
[    0.008488] using C1E aware idle routine
[    0.009842] ACPI: Core revision 20080609
[    0.013903] ACPI: Checking initramfs for custom DSDT
[    0.324437] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.365822] CPU0: AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[    0.365827] Using local APIC timer interrupts.
[    0.368024] APIC timer calibration result 12562875
[    0.368025] Detected 12.562 MHz APIC timer.
[    0.368162] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4422.39 BogoMIPS (lpj=8844794)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.456468] CPU1: AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[    0.456476] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.460056] System has AMD C1E enabled
[    0.460066] Switch to broadcast mode on CPU1
[    0.460117] Booting processor 2/2 ip 6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4422.34 BogoMIPS (lpj=8844693)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 2/2 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.548447] CPU2: AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[    0.548453] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.552061] Switch to broadcast mode on CPU2
[    0.552123] Booting processor 3/3 ip 6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4422.30 BogoMIPS (lpj=8844619)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 3/3 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.640465] CPU3: AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[    0.640471] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.644060] Brought up 4 CPUs
[    0.644062] Total of 4 processors activated (17689.17 BogoMIPS).
[    0.644059] Switch to broadcast mode on CPU3
[    0.644107] CPU0 attaching sched-domain:
[    0.644110]  domain 0: span 0-3 level CPU
[    0.644112]   groups: 0 1 2 3
[    0.644116]   domain 1: span 0-3 level NODE
[    0.644118]    groups: 0-3
[    0.644122] CPU1 attaching sched-domain:
[    0.644124]  domain 0: span 0-3 level CPU
[    0.644126]   groups: 1 2 3 0
[    0.644129]   domain 1: span 0-3 level NODE
[    0.644130]    groups: 0-3
[    0.644136] CPU2 attaching sched-domain:
[    0.644137]  domain 0: span 0-3 level CPU
[    0.644139]   groups: 2 3 0 1
[    0.644142]   domain 1: span 0-3 level NODE
[    0.644143]    groups: 0-3
[    0.644146] CPU3 attaching sched-domain:
[    0.644148]  domain 0: span 0-3 level CPU
[    0.644149]   groups: 3 0 1 2
[    0.644152]   domain 1: span 0-3 level NODE
[    0.644153]    groups: 0-3
[    0.644278] Switch to broadcast mode on CPU0
[    0.644278] net_namespace: 1552 bytes
[    0.644278] Booting paravirtualized kernel on bare hardware
[    0.644298] Time: 16:56:40  Date: 11/03/08
[    0.644333] NET: Registered protocol family 16
[    0.644353] node 0 link 0: io port [1000, ffffff]
[    0.644353] TOM: 00000000d0000000 aka 3328M
[    0.644353] Fam 10h mmconf [e0000000, e00fffff]
[    0.644353] node 0 link 0: mmio [a0000, bffff]
[    0.644353] node 0 link 0: mmio [d0000000, dfffffff]
[    0.644353] node 0 link 0: mmio [e0000000, efffffff] ==> [e0100000, efffffff]
[    0.644353] node 0 link 0: mmio [f0000000, ffefffff]
[    0.644353] TOM2: 0000000130000000 aka 4864M
[    0.644353] bus: [00,07] on node 0 link 0
[    0.644353] bus: 00 index 0 io port: [0, ffff]
[    0.644353] bus: 00 index 1 mmio: [a0000, bffff]
[    0.644353] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.644353] bus: 00 index 3 mmio: [e0100000, ffffffff]
[    0.644353] bus: 00 index 4 mmio: [130000000, fcffffffff]
[    0.644353] ACPI: bus type pci registered
[    0.644353] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.644353] PCI: Not using MMCONFIG.
[    0.644353] PCI: Using configuration type 1 for base access
[    0.644353] PCI: Using configuration type 1 for extended access
[    0.644692] ACPI: EC: Look up EC in DSDT
[    0.661802] ACPI: Interpreter enabled
[    0.661805] ACPI: (supports S0 S1 S3 S4 S5)
[    0.661823] ACPI: Using IOAPIC for interrupt routing
[    0.661906] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.669121] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.682105] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.692647] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.692647] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.692647] pci 0000:00:02.0: PME# disabled
[    0.692647] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.692647] pci 0000:00:0a.0: PME# disabled
[    0.692647] PCI: 0000:00:11.0 reg 10 io port: [b000, b007]
[    0.692647] PCI: 0000:00:11.0 reg 14 io port: [a000, a003]
[    0.692647] PCI: 0000:00:11.0 reg 18 io port: [9000, 9007]
[    0.692647] PCI: 0000:00:11.0 reg 1c io port: [8000, 8003]
[    0.692647] PCI: 0000:00:11.0 reg 20 io port: [7000, 700f]
[    0.692647] PCI: 0000:00:11.0 reg 24 32bit mmio: [fe8ffc00, fe8fffff]
[    0.692647] PCI: 0000:00:12.0 reg 10 32bit mmio: [fe8fe000, fe8fefff]
[    0.692647] PCI: 0000:00:12.1 reg 10 32bit mmio: [fe8fd000, fe8fdfff]
[    0.692647] PCI: 0000:00:12.2 reg 10 32bit mmio: [fe8ff800, fe8ff8ff]
[    0.692647] pci 0000:00:12.2: supports D1
[    0.692647] pci 0000:00:12.2: supports D2
[    0.692647] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.692647] pci 0000:00:12.2: PME# disabled
[    0.692647] PCI: 0000:00:13.0 reg 10 32bit mmio: [fe8fc000, fe8fcfff]
[    0.692647] PCI: 0000:00:13.1 reg 10 32bit mmio: [fe8f7000, fe8f7fff]
[    0.692647] PCI: 0000:00:13.2 reg 10 32bit mmio: [fe8ff400, fe8ff4ff]
[    0.692647] pci 0000:00:13.2: supports D1
[    0.692647] pci 0000:00:13.2: supports D2
[    0.692647] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.692647] pci 0000:00:13.2: PME# disabled
[    0.692698] PCI: 0000:00:14.1 reg 10 io port: [0, 7]
[    0.692704] PCI: 0000:00:14.1 reg 14 io port: [0, 3]
[    0.692710] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
[    0.692716] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
[    0.692722] PCI: 0000:00:14.1 reg 20 io port: [ff00, ff0f]
[    0.692776] PCI: 0000:00:14.2 reg 10 64bit mmio: [fe8f0000, fe8f3fff]
[    0.692813] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.692817] pci 0000:00:14.2: PME# disabled
[    0.692906] PCI: 0000:00:14.5 reg 10 32bit mmio: [fe8f6000, fe8f6fff]
[    0.693036] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.693047] PCI: 0000:01:00.0 reg 18 64bit mmio: [fe9f0000, fe9fffff]
[    0.693051] PCI: 0000:01:00.0 reg 20 io port: [c000, c0ff]
[    0.693059] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe9c0000, fe9dffff]
[    0.693071] pci 0000:01:00.0: supports D1
[    0.693072] pci 0000:01:00.0: supports D2
[    0.693094] PCI: 0000:01:00.1 reg 10 64bit mmio: [fe9ec000, fe9effff]
[    0.693121] pci 0000:01:00.1: supports D1
[    0.693122] pci 0000:01:00.1: supports D2
[    0.693166] PCI: bridge 0000:00:02.0 io port: [c000, cfff]
[    0.693169] PCI: bridge 0000:00:02.0 32bit mmio: [fe900000, fe9fffff]
[    0.693173] PCI: bridge 0000:00:02.0 64bit mmio pref: [d0000000, dfffffff]
[    0.693205] PCI: 0000:02:00.0 reg 10 io port: [d800, d8ff]
[    0.693214] PCI: 0000:02:00.0 reg 18 32bit mmio: [fdfff000, fdffffff]
[    0.693224] PCI: 0000:02:00.0 reg 20 32bit mmio: [fdfe0000, fdfeffff]
[    0.693234] PCI: 0000:02:00.0 reg 30 32bit mmio: [feaf0000, feafffff]
[    0.693254] pci 0000:02:00.0: supports D1
[    0.693255] pci 0000:02:00.0: supports D2
[    0.693257] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.693260] pci 0000:02:00.0: PME# disabled
[    0.693299] PCI: bridge 0000:00:0a.0 io port: [d000, dfff]
[    0.693301] PCI: bridge 0000:00:0a.0 32bit mmio: [fea00000, feafffff]
[    0.693305] PCI: bridge 0000:00:0a.0 64bit mmio pref: [fdf00000, fdffffff]
[    0.693353] PCI: 0000:03:05.0 reg 10 32bit mmio: [febffc00, febfffff]
[    0.693407] pci 0000:03:05.0: supports D1
[    0.693408] pci 0000:03:05.0: supports D2
[    0.693428] PCI: 0000:03:06.0 reg 10 32bit mmio: [febff800, febff9ff]
[    0.696078] PCI: 0000:03:07.0 reg 10 32bit mmio: [febff000, febff7ff]
[    0.696086] PCI: 0000:03:07.0 reg 14 io port: [e800, e87f]
[    0.696136] pci 0000:03:07.0: supports D2
[    0.696137] pci 0000:03:07.0: PME# supported from D2 D3hot D3cold
[    0.696142] pci 0000:03:07.0: PME# disabled
[    0.696179] pci 0000:00:14.4: transparent bridge
[    0.696183] PCI: bridge 0000:00:14.4 io port: [e000, efff]
[    0.696187] PCI: bridge 0000:00:14.4 32bit mmio: [feb00000, febfffff]
[    0.696206] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.696695] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.696857] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.697020] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.700199] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.700385] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.700574] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.700756] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.700947] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 *10 11 12 14 15)
[    0.701124] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 *10 11 12 14 15)
[    0.701305] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 *11 12 14 15)
[    0.701491] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.701563] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 29, should be 1E [20080609]
[    0.701563] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.701563] pnp: PnP ACPI init
[    0.701563] ACPI: bus type pnp registered
[    0.708872] pnp: PnP ACPI: found 17 devices
[    0.708872] ACPI: ACPI bus type pnp unregistered
[    0.708872] PCI: Using ACPI for IRQ routing
[    0.728042] NET: Registered protocol family 8
[    0.728044] NET: Registered protocol family 20
[    0.728063] NetLabel: Initializing
[    0.728063] NetLabel:  domain hash size = 128
[    0.728063] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.728063] NetLabel:  unlabeled traffic allowed by default
[    0.728148] PCI-DMA: Disabling AGP.
[    0.728707] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.728707] PCI-DMA: using GART IOMMU.
[    0.728707] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.729740] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.729748] hpet0: 4 32-bit timers, 14318180 Hz
[    0.732054] Switched to high resolution mode on CPU 0
[    0.732062] Switched to high resolution mode on CPU 3
[    0.732066] Switched to high resolution mode on CPU 1
[    0.732068] Switched to high resolution mode on CPU 2
[    0.734535] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.734537]    actual entries 65586
[    0.734662] AppArmor: AppArmor Filesystem Enabled
[    0.734688] ACPI: RTC can wake from S4
[    0.752173] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.752176] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.752184] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.752186] system 00:0c: ioport range 0x40b-0x40b has been reserved
[    0.752188] system 00:0c: ioport range 0x4d6-0x4d6 has been reserved
[    0.752190] system 00:0c: ioport range 0xc00-0xc01 has been reserved
[    0.752192] system 00:0c: ioport range 0xc14-0xc14 has been reserved
[    0.752194] system 00:0c: ioport range 0xc50-0xc51 has been reserved
[    0.752196] system 00:0c: ioport range 0xc52-0xc52 has been reserved
[    0.752197] system 00:0c: ioport range 0xc6c-0xc6c has been reserved
[    0.752199] system 00:0c: ioport range 0xc6f-0xc6f has been reserved
[    0.752206] system 00:0c: ioport range 0xcd0-0xcd1 has been reserved
[    0.752208] system 00:0c: ioport range 0xcd2-0xcd3 has been reserved
[    0.752210] system 00:0c: ioport range 0xcd4-0xcd5 has been reserved
[    0.752214] system 00:0c: ioport range 0xcd6-0xcd7 has been reserved
[    0.752216] system 00:0c: ioport range 0xcd8-0xcdf has been reserved
[    0.752218] system 00:0c: ioport range 0x800-0x89f has been reserved
[    0.752220] system 00:0c: ioport range 0xb00-0xb0f has been reserved
[    0.752222] system 00:0c: ioport range 0xb20-0xb3f has been reserved
[    0.752224] system 00:0c: ioport range 0x900-0x90f has been reserved
[    0.752226] system 00:0c: ioport range 0x910-0x91f has been reserved
[    0.752229] system 00:0c: ioport range 0xfe00-0xfefe has been reserved
[    0.752231] system 00:0c: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.752234] system 00:0c: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.752241] system 00:0e: ioport range 0x290-0x29f has been reserved
[    0.752247] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.752253] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.752255] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    0.752257] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.752259] system 00:10: iomem range 0x100000-0xcfefffff could not be reserved
[    0.752261] system 00:10: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.757528] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.757530] pci 0000:00:02.0:   IO window: 0xc000-0xcfff
[    0.757534] pci 0000:00:02.0:   MEM window: 0xfe900000-0xfe9fffff
[    0.757537] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.757541] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.757543] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff
[    0.757546] pci 0000:00:0a.0:   MEM window: 0xfea00000-0xfeafffff
[    0.757548] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.757552] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.757555] pci 0000:00:14.4:   IO window: 0xe000-0xefff
[    0.757559] pci 0000:00:14.4:   MEM window: 0xfeb00000-0xfebfffff
[    0.757563] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.757582] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.757585] pci 0000:00:02.0: setting latency timer to 64
[    0.757591] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.757593] pci 0000:00:0a.0: setting latency timer to 64
[    0.757601] bus: 00 index 0 io port: [0, ffff]
[    0.757603] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.757605] bus: 01 index 0 io port: [c000, cfff]
[    0.757606] bus: 01 index 1 mmio: [fe900000, fe9fffff]
[    0.757608] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.757609] bus: 01 index 3 mmio: [0, 0]
[    0.757611] bus: 02 index 0 io port: [d000, dfff]
[    0.757612] bus: 02 index 1 mmio: [fea00000, feafffff]
[    0.757614] bus: 02 index 2 mmio: [fdf00000, fdffffff]
[    0.757615] bus: 02 index 3 mmio: [0, 0]
[    0.757617] bus: 03 index 0 io port: [e000, efff]
[    0.757618] bus: 03 index 1 mmio: [feb00000, febfffff]
[    0.757619] bus: 03 index 2 mmio: [0, 0]
[    0.757621] bus: 03 index 3 io port: [0, ffff]
[    0.757622] bus: 03 index 4 mmio: [0, ffffffffffffffff]
[    0.757637] NET: Registered protocol family 2
[    0.796315] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.797830] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.802727] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.803321] TCP: Hash tables configured (established 524288 bind 65536)
[    0.803324] TCP reno registered
[    0.812160] NET: Registered protocol family 1
[    0.812286] checking if image is initramfs... it is
[    1.431681] Freeing initrd memory: 8777k freed
[    1.437990] audit: initializing netlink socket (disabled)
[    1.438006] type=2000 audit(1225731400.436:1): initialized
[    1.443032] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.445789] VFS: Disk quotas dquot_6.5.1
[    1.445875] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.445979] msgmni has been set to 7918
[    1.446103] io scheduler noop registered
[    1.446105] io scheduler anticipatory registered
[    1.446106] io scheduler deadline registered
[    1.446228] io scheduler cfq registered (default)
[    1.572111] pci 0000:01:00.0: Boot video device
[    1.572257] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.572278] pcieport-driver 0000:00:02.0: found MSI capability
[    1.572302] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.572378] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.572397] pcieport-driver 0000:00:0a.0: found MSI capability
[    1.572416] pci_express 0000:00:0a.0:pcie00: allocate port service
[    1.609205] hpet_resources: 0xfed00000 is busy
[    1.609325] Linux agpgart interface v0.103
[    1.609330] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.609501] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.609673] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.610332] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.612257] brd: module loaded
[    1.612339] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.612461] PNP: PS/2 Controller [PNP0303:PSKE,PNP0f03:PSMS] at 0x60,0x64 irq 1,12
[    1.614971] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.614980] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.637852] mice: PS/2 mouse device common for all mice
[    1.638018] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.638043] rtc0: alarms up to one month, y3k, hpet irqs
[    1.638092] cpuidle: using governor ladder
[    1.638094] cpuidle: using governor menu
[    1.638479] TCP cubic registered
[    1.638721] registered taskstats version 1
[    1.638892]   Magic number: 0:842:943
[    1.638947] tty ptyye: hash matches
[    1.638989] tty tty0: hash matches
[    1.638991] tty console: hash matches
[    1.639046] rtc_cmos 00:05: setting system clock to 2008-11-03 16:56:41 UTC (1225731401)
[    1.639049] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.639051] EDD information not available.
[    1.639094] Freeing unused kernel memory: 536k freed
[    1.639359] Write protecting the kernel read-only data: 4348k
[    1.758458] fuse init (API version 7.9)
[    1.815176] processor ACPI0007:00: registered as cooling_device0
[    1.815183] ACPI: Processor [P001] (supports 8 throttling states)
[    1.815297] processor ACPI0007:01: registered as cooling_device1
[    1.815372] processor ACPI0007:02: registered as cooling_device2
[    1.815444] processor ACPI0007:03: registered as cooling_device3
[    2.029946] No dock devices found.
[    2.039168] usbcore: registered new interface driver usbfs
[    2.039208] usbcore: registered new interface driver hub
[    2.039727] usbcore: registered new device driver usb
[    2.049993] SCSI subsystem initialized
[    2.059122] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.059160] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.059185] r8169 0000:02:00.0: setting latency timer to 64
[    2.059549] eth0: RTL8168c/8111c at 0xffffc2000063c000, 00:19:66:8e:61:74, XID 3c4000c0 IRQ 2301
[    2.061681] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.061709] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    2.061804] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    2.061861] ehci_hcd 0000:00:12.2: debug port 1
[    2.061886] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
[    2.063716] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.076526] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.076865] usb usb1: configuration #1 chosen from 1 choice
[    2.076925] hub 1-0:1.0: USB hub found
[    2.076949] hub 1-0:1.0: 6 ports detected
[    2.077074] libata version 3.00 loaded.
[    2.284984] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.285012] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.285042] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    2.285083] ehci_hcd 0000:00:13.2: debug port 1
[    2.285104] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8ff400
[    2.352536] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.352745] usb usb2: configuration #1 chosen from 1 choice
[    2.352774] hub 2-0:1.0: USB hub found
[    2.352786] hub 2-0:1.0: 6 ports detected
[    2.456917] ahci 0000:00:11.0: version 3.0
[    2.456962] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.457158] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    2.457162] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.457609] scsi0 : ahci
[    2.457773] scsi1 : ahci
[    2.457844] scsi2 : ahci
[    2.457911] scsi3 : ahci
[    2.457976] scsi4 : ahci
[    2.458044] scsi5 : ahci
[    2.458162] ata1: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd00 irq 22
[    2.458166] ata2: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 22
[    2.458169] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 22
[    2.458171] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 22
[    2.458174] ata5: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8fff00 irq 22
[    2.458177] ata6: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8fff80 irq 22
[    2.517535] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    2.648810] usb 1-5: configuration #1 chosen from 1 choice
[    2.648883] hub 1-5:1.0: USB hub found
[    2.648982] hub 1-5:1.0: 4 ports detected
[    2.944165] ata1: softreset failed (device not ready)
[    2.944173] ata1: failed due to HW bug, retry pmp=0
[    3.112101] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.126897] ata1.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[    3.126901] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.129389] ata1.00: configured for UDMA/133
[    3.464190] ata2: SATA link down (SStatus 0 SControl 300)
[    3.800208] ata3: SATA link down (SStatus 0 SControl 300)
[    4.136084] ata4: SATA link down (SStatus 0 SControl 300)
[    4.472222] ata5: SATA link down (SStatus 0 SControl 300)
[    4.812125] ata6: SATA link down (SStatus 0 SControl 300)
[    4.828370] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    4.828649] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.828679] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    4.828742] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    4.828787] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
[    4.888946] usb usb3: configuration #1 chosen from 1 choice
[    4.889507] hub 3-0:1.0: USB hub found
[    4.889520] hub 3-0:1.0: 3 ports detected
[    5.097482] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.097498] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    5.097527] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    5.097545] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
[    5.156936] usb usb4: configuration #1 chosen from 1 choice
[    5.157533] hub 4-0:1.0: USB hub found
[    5.157545] hub 4-0:1.0: 3 ports detected
[    5.232106] usb 3-3: new low speed USB device using ohci_hcd and address 2
[    5.365561] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.365578] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.365606] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    5.365634] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
[    5.425527] usb usb5: configuration #1 chosen from 1 choice
[    5.426135] hub 5-0:1.0: USB hub found
[    5.426147] hub 5-0:1.0: 3 ports detected
[    5.530321] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.530336] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.530364] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    5.530382] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8f7000
[    5.563182] usb 3-3: configuration #1 chosen from 1 choice
[    5.588318] usb usb6: configuration #1 chosen from 1 choice
[    5.588342] hub 6-0:1.0: USB hub found
[    5.588353] hub 6-0:1.0: 3 ports detected
[    5.693134] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.693185] pata_acpi 0000:00:14.1: setting latency timer to 64
[    5.696658] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.696680] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    5.696726] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    5.696749] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8f6000
[    5.705538] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    5.756892] usb usb7: configuration #1 chosen from 1 choice
[    5.756923] hub 7-0:1.0: USB hub found
[    5.756936] hub 7-0:1.0: 2 ports detected
[    5.862406] ohci1394 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.915663] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.921074] scsi6 : pata_atiixp
[    5.921180] scsi7 : pata_atiixp
[    5.922891] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    5.922893] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    5.927031] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.929385] usb 4-1: configuration #1 chosen from 1 choice
[    5.958720] Driver 'sd' needs updating - please use bus_type methods
[    5.959050] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.959067] sd 0:0:0:0: [sda] Write Protect is off
[    5.959069] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.959090] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.959180] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.959191] sd 0:0:0:0: [sda] Write Protect is off
[    5.959193] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.959212] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.959216]  sda:<6>usbcore: registered new interface driver hiddev
[    5.966677] input: Razer Razer 1600dpi 3 button optical mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input1
[    5.993822] input,hidraw0: USB HID v1.10 Mouse [Razer Razer 1600dpi 3 button optical mouse] on usb-0000:00:12.0-3
[    6.000596] input: Cherry GmbH as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input2
[    6.021540]  sda1 sda2 sda3 <<6>input,hidraw1: USB HID v1.11 Keyboard [Cherry GmbH] on usb-0000:00:12.1-1
[    6.029749] usbcore: registered new interface driver usbhid
[    6.029752] usbhid: v2.6:USB HID core driver
[    6.034238]  sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
[    6.111787] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.240639] ata8.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A103, max UDMA/33
[    6.256594] ata8.00: configured for UDMA/33
[    6.261486] scsi 7:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A103 PQ: 0 ANSI: 5
[    6.261719] scsi 7:0:0:0: Attached scsi generic sg1 type 5
[    6.289568] Driver 'sr' needs updating - please use bus_type methods
[    6.306288] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.306296] Uniform CD-ROM driver Revision: 3.20
[    6.306452] sr 7:0:0:0: Attached scsi CD-ROM sr0
[    6.625075] PM: Starting manual resume from disk
[    6.625080] PM: Resume from partition 8:7
[    6.625081] PM: Checking hibernation image.
[    6.625418] PM: Resume from disk failed.
[    6.682994] kjournald starting.  Commit interval 5 seconds
[    6.683020] EXT3-fs: mounted filesystem with ordered data mode.
[    7.196386] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[008f13007fef0500]
[   11.189004] udevd version 124 started
[   11.423311] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.448878] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.469050] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.488534] ACPI: Power Button (FF) [PWRF]
[   11.488691] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.520537] ACPI: Power Button (CM) [PWRB]
[   11.529774] ACPI: WMI: Mapper loaded
[   11.687208] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.730374] [fglrx] Maximum main memory to use for locked dma buffers: 3797 MBytes.
[   11.730767] [fglrx]   vendor: 1002 device: 9440 count: 1
[   11.731318] [fglrx] ioport: bar 4, base 0xc000, size: 0x100
[   11.731344] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.731353] pci 0000:01:00.0: setting latency timer to 64
[   11.732754] [fglrx] PAT is enabled successfully!
[   11.732853] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   11.959367] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   11.959371] ACPI: Device needs an ACPI driver
[   11.959381] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.026730] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.610090] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.647122] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   12.685149] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.685182] HDA Intel 0000:01:00.1: setting latency timer to 64
[   12.693403] Linux video capture interface: v2.00
[   12.716839] saa7146: register extension 'budget_av'.
[   12.735214] budget_av 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.735261] saa7146: found saa7146 @ mem ffffc20000666800 (revision 1, irq 21) (0x153b,0x1155).
[   12.735270] saa7146 (0): dma buffer size 192512
[   12.735274] DVB: registering new adapter (TerraTec Cinergy 1200 DVB-S)
[   12.770534] adapter failed MAC signature check
[   12.770539] encoded MAC from EEPROM was ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff
[   12.825340] saa7130/34: v4l2 driver version 0.2.14 loaded
[   12.966628] NET: Registered protocol family 10
[   12.967092] lo: Disabled Privacy Extensions
[   13.039701] KNC1-0: MAC addr = 00:0a:ac:12:95:68
[   13.436451] DVB: registering frontend 0 (ST STV0299 DVB-S)...
[   13.436783] budget-av: ci interface initialised.
[   13.436874] saa7134 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   13.436883] saa7134[0]: found at 0000:03:05.0, rev: 1, irq: 20, latency: 32, mmio: 0xfebffc00
[   13.436894] saa7134[0]: subsystem: 11bd:002d, board: Pinnacle PCTV 300i DVB-T + PAL [card=50,autodetected]
[   13.436916] saa7134[0]: board init: gpio is c806000
[   13.592076] saa7134[0]: i2c eeprom 00: bd 11 2d 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[   13.592085] saa7134[0]: i2c eeprom 10: 00 f0 04 04 ff 20 ff ff ff ff ff ff ff ff ff ff
[   13.592092] saa7134[0]: i2c eeprom 20: 01 40 01 02 03 ff 03 01 08 ff 00 25 ff ff ff ff
[   13.592098] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.592105] saa7134[0]: i2c eeprom 40: ff 16 00 c0 86 3c 01 01 ff ff ff ff ff ff ff ff
[   13.592111] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.592119] saa7134[0]: i2c eeprom 60: 0c 22 17 44 02 8e 9f 28 ff ff ff ff ff ff ff ff
[   13.592124] saa7134[0]: i2c eeprom 70: 00 30 8d 14 05 39 ff ff ff ff ff ff ff ff ff ff
[   13.592132] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.592138] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.592144] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.592149] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.592160] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.592165] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.592171] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.592179] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.780154] tuner' 2-0043: chip found @ 0x86 (saa7134[0])
[   13.797521] tda9887 2-0043: creating new instance
[   13.797524] tda9887 2-0043: tda988[5/6/7] found
[   13.837665] Chip ID is not zero. It is not a TEA5767
[   13.837735] tuner' 2-0060: chip found @ 0xc0 (saa7134[0])
[   13.881592] mt20xx 2-0060: microtune: companycode=3cbf part=42 rev=2f
[   13.912102] mt20xx 2-0060: microtune MT2050 found, OK
[   13.968486] saa7134[0]: registered device video0 [v4l2]
[   13.968520] saa7134[0]: registered device vbi0
[   13.999822] saa7134 ALSA driver for DMA sound loaded
[   13.999877] saa7134[0]/alsa: saa7134[0] at 0xfebffc00 irq 20 registered as card -2
[   14.009026] DVB: registering new adapter (saa7134[0])
[   14.009032] DVB: registering frontend 1 (Zarlink MT352 DVB-T)...
[   15.164658] loop: module loaded
[   15.230387] lp: driver loaded but no devices found
[   15.525977] Adding 7815580k swap on /dev/sda7.  Priority:-1 extents:1 across:7815580k
[   16.104283] EXT3 FS on sda2, internal journal
[   16.321813] device-mapper: uevent: version 1.0.3
[   16.324806] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   17.410570] kjournald starting.  Commit interval 5 seconds
[   17.411078] EXT3 FS on sda6, internal journal
[   17.411088] EXT3-fs: mounted filesystem with ordered data mode.
[   17.480256] kjournald starting.  Commit interval 5 seconds
[   17.480616] EXT3 FS on sda5, internal journal
[   17.480625] EXT3-fs: mounted filesystem with ordered data mode.
[   17.852419] type=1505 audit(1225731417.915:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5158
[   18.005753] type=1505 audit(1225731418.069:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5163
[   18.006100] type=1505 audit(1225731418.069:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5163
[   18.059353] type=1505 audit(1225731418.121:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=5167
[   18.207411] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.216931] powernow-k8: Found 1 AMD Phenom(tm) 9500 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[   19.217012] powernow-k8:    0 : pstate 0 (2200 MHz)
[   19.217016] powernow-k8:    1 : pstate 1 (1100 MHz)
[   20.003171] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   22.460925] ppdev: user-space parallel port driver
[   23.660531] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   23.660558] vboxdrv: Successfully done.
[   23.660562] vboxdrv: Found 4 processor cores.
[   23.662383] vboxdrv: fAsync=0 offMin=0x455 offMax=0x4bd6
[   23.662393] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   23.662397] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   28.080491] Bluetooth: Core ver 2.13
[   28.081727] NET: Registered protocol family 31
[   28.081734] Bluetooth: HCI device and connection manager initialized
[   28.081741] Bluetooth: HCI socket layer initialized
[   28.111444] Bluetooth: L2CAP ver 2.11
[   28.111469] Bluetooth: L2CAP socket layer initialized
[   28.138349] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.138375] Bluetooth: BNEP filters: protocol multicast
[   28.199199] Bridge firewalling registered
[   28.199703] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   28.293440] Bluetooth: SCO (Voice Link) ver 0.6
[   28.293466] Bluetooth: SCO socket layer initialized
[   28.390669] Bluetooth: RFCOMM socket layer initialized
[   28.390714] Bluetooth: RFCOMM TTY layer initialized
[   28.390717] Bluetooth: RFCOMM ver 1.10
[   31.835459] /dev/vmmon[6905]: Module vmmon: registered with major=10 minor=165
[   31.835495] /dev/vmmon[6905]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   31.835505] /dev/vmmon[6905]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   31.835511] /dev/vmmon[6905]: Module vmmon: initialized
[   31.857688] /dev/vmci[6919]: VMCI: Driver initialized.
[   31.861309] /dev/vmci[6919]: Module vmci: registered with major=10 minor=58
[   31.861319] /dev/vmci[6919]: Module vmci: initialized
[   32.138923] [fglrx] CMM init INV FB MC:0xf10000000, length:0x10000000
[   32.138947] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   32.138953] [fglrx] Reserved FB block: Unshared offset:ff77000, size:88000 
[   32.558445] r8169: eth0: link up
[   32.558460] r8169: eth0: link up
[   32.616970] /dev/vmnet: open called by PID 6973 (vmnet-bridge)
[   32.616998] /dev/vmnet: hub 0 does not exist, allocating memory.
[   32.617019] /dev/vmnet: port on hub 0 successfully opened
[   32.617054] bridge-eth0: up
[   32.617065] bridge-eth0: attached
[   32.792853] /dev/vmnet: open called by PID 6987 (vmnet-netifup)
[   32.792883] /dev/vmnet: hub 1 does not exist, allocating memory.
[   32.792904] /dev/vmnet: port on hub 1 successfully opened
[   32.862390] NET: Registered protocol family 17
[   32.974226] /dev/vmnet: open called by PID 6985 (vmnet-dhcpd)
[   32.974261] /dev/vmnet: port on hub 1 successfully opened
[   32.990358] /dev/vmnet: open called by PID 7023 (vmnet-netifup)
[   32.990390] /dev/vmnet: hub 8 does not exist, allocating memory.
[   32.990408] /dev/vmnet: port on hub 8 successfully opened
[   33.079922] /dev/vmnet: open called by PID 7024 (vmnet-dhcpd)
[   33.079960] /dev/vmnet: port on hub 8 successfully opened
[   33.115714] /dev/vmnet: open called by PID 7039 (vmnet-natd)
[   33.115751] /dev/vmnet: port on hub 8 successfully opened
[   43.224033] vmnet8: no IPv6 routers present
[   43.433519] vmnet1: no IPv6 routers present
[   54.844001] hda-intel: Invalid position buffer, using LPIB read method instead.
[  138.330514] type=1503 audit(1225731538.394:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/8113/net/" pid=8113 profile="/usr/sbin/cupsd"
[  139.578131] type=1503 audit(1225731539.641:7): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/8118/net/" pid=8118 profile="/usr/sbin/cupsd"
[  139.578193] type=1503 audit(1225731539.641:8): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=8118 profile="/usr/sbin/cupsd"
[  139.578203] type=1503 audit(1225731539.641:9): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=8118 profile="/usr/sbin/cupsd"
[  139.578212] type=1503 audit(1225731539.641:10): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=8118 profile="/usr/sbin/cupsd"
[  139.578222] type=1503 audit(1225731539.641:11): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=8118 profile="/usr/sbin/cupsd"
[  139.578231] type=1503 audit(1225731539.641:12): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=8118 profile="/usr/sbin/cupsd"
[  139.578240] type=1503 audit(1225731539.641:13): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=8118 profile="/usr/sbin/cupsd"
[  139.578249] type=1503 audit(1225731539.641:14): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=8118 profile="/usr/sbin/cupsd"
[  139.578259] type=1503 audit(1225731539.641:15): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=8118 profile="/usr/sbin/cupsd"
```

---

### Post by soxs on 2008-11-03
Kaffeine shows the digital TV icon, and I actually see both devices (DVB-S and DVB-T when setting it up within kaffeine).
There I several options that I'd like to know hwat they do... (other are the different setups for the 4 possible "channels of TV card")
As it seems to be, I nned a program list. Scanning doesn't help at all.
I allready tried mythtv, but as the curren 8.10 ati drive sucks hard, I am not able to preserv mythtv suffering from extreme fullscreendistorsions so this is unusable and I can't even read the menu..)

Btw. I allready baught a new kable to exclude it being the guilty.

Edit: Kaffeine is currently scanning and often jumps over the 50% mark...

Edit: I did not seem to need any firmware at all, at least hardwaremanager did not tell me to get anything except the ati driver.

---

### Post by steefjeqv on 2008-11-03
Hi,

Glad to hear that you're able to do a channelscan with kaffeine.

If, for any reason, there should be a problem with locking down the scanned channels then there's the possiblity that you may need to add firmware.

Does kaffeine mention the tuner used by the card (tda10064) ?

Concerning the fglrx driver : which ATI card are you using ?
The most recent open source ati driver supports Xv (with EXA) upto the R500 cards (ATI 1250, 1300, 1600, 1800).

A good alternative for MythTV is VDR. It has quite a large userbase (mostly German) and there is an up-to-date repository for Ubuntu which is maintained and hosted by e-tobi and hanno.

[http://www.cadsoft.de/vdr/]("http://www.cadsoft.de/vdr/")
[http://www.vdr-wiki.de/wiki/index.php/Hauptseite]("http://www.vdr-wiki.de/wiki/index.php/Hauptseite")
[http://www.vdrportal.de/board/portal.php](http://www.vdrportal.de/board/portal.php)


Greetings,
Steven

---

### Post by soxs on 2008-11-03
I am currently going to install mythbuntu 8.04 (fixing grub issues) with an actually working fglrx video driver.

My gpu is a R770, speak a RadeonHD 4870

While scanning with an setup channel list I always get this:
```

Using DVB device 0:0 "ST STV0299 DVB-S"
tuning DVB-S to 11778000 v 27500000
inv:2 fecH:9
DiSEqC: switch pos 0, 13V, hiband (index 2)
DiSEqC: e0 10 38 f1 00 00
....................

Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
```

Note: Trying an DVB-T firmware won't help me, at least it seems to be absurd to me...

Edit: Note: My primary language is German, so this is not a real obstacle ;-)

---

### Post by steefjeqv on 2008-11-03
Hi,

You're right, it's no use adding DVB-T firmware.

Are you using dvb-utils to perform the scan ?
Did you scan as "user" or "root" (sudo) ?

Greetings,
Steven

---

### Post by soxs on 2008-11-04
> **steefjeqv said:**
> 
Are you using dvb-utils to perform the scan ?
Did you scan as "user" or "root" (sudo) ?

I did both, but no results with ```
scantv -c /dev/vbi0 -C /dev/video0 -n PAL

``` though I am not shure wether it uses the correct device to detect or not (having to specify c and C switch, otherwise it will raise an error about /dev/vbi (the default) not existing.)

I am thinking about removeing the DVB-T temporary...

---

### Post by steefjeqv on 2008-11-04
Hi,

You can install dvb-utils and try scanning.

scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-19.2E > yourchannels.confdirectory

Greetings,
Steven

---

### Post by soxs on 2008-11-05
But how can I make sure which device it will take care off?

Edit: Got it to use a defined adapter, but this won't help either:
```

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 12551500 V 22000000 5
>>> tune to: 12551:v:0:22000
WARNING: >>> tuning failed!!!
>>> tune to: 12551:v:0:22000 (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

---

### Post by soxs on 2008-11-09
Here we go again. I removed the DVB-T card (and with it /dev/video0 and /dev/vbi0), so I can make sure everything concerning TV setup goes to the correct card.

Things I found out during several hours of googeling:
I had to download a firmware package and had to move it's conent (multiple .fw files [http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/) the package) into /lib/firmware/<kernelversion> aka ```
/lib/firmware/`uname -r`
```.
Afterwards I had to compile v4l-dvb by hand, speak: Unpack, cd into unpacked directory and call ```
make
``` and ```
sudo make install
``` (This took some time).
At last I had to load ```
bttv
``` by adding it to /etc/modules via: ```
sudo gedit /etc/modules
``` and add bttv in a new line (bttv is required fot the talk between the card, driver and the kernel, at least I think so/was told so).
-> reboot.

Now I at least got this output from lsmod|grep saa7146
```
lsmod|grep saa7146
saa7146_vv             59392  1 budget_av
videobuf_dma_sg        22788  2 bttv,saa7146_vv
videobuf_core          29700  3 bttv,saa7146_vv,videobuf_dma_sg
videodev               45568  4 bttv,v4l2_compat_ioctl32,tuner,saa7146_vv
v4l1_compat            23940  2 saa7146_vv,videodev
saa7146                27016  3 budget_av,saa7146_vv,budget_core
```The bad thing about not having /dev/video0 is that most TV tools (tvtime, xawtv, ..) won't help me anymore (they need that node), so I had to create it.

I made a new node and a new usergourp named "video" (via GUI).
Node creation:
```
sudo mknod /dev/video0 c 81 0 
``` I read on some forum these values, don't ask me for correctness or not, I didn't bother as I had nothing to loose.
```
sudo chgrp video /dev/video0
```and make it accessable by any user
```
sudo chmod 666 /dev/video0
```Bad result: No change, except tvtime flashing me everytime for a nonexistant /dev/video0 -.-

Edit: Sacnning via scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-19.2E had the same result as before..

_**[COLOR=Red]HELP![/COLOR]**_

---

### Post by soxs on 2008-11-10
Ok, I found a howto which didn't work aswell, but I got where my problem lies borrowed, or at least a hint to where it's grave is located:

[http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)
Case 1 works, I have /dev/dvb/* stuff:```
 ls /dev/dvb/adapter0/
ca0  demux0  dvr0  frontend0  net0
```BUT: ```
dmesg |grep dvb
``` doesn't give me any output??!

I am somewhat exhausted. I thought this card would work just fine, but as it seems mythbuntu database is somewhat out of date or simply unprecise. ()It was stated to should work, though not guranteed :-S bad luck I guess... )[http://www.linuxtv.org/v4lwiki/index.php/Saa7146_devices](http://www.linuxtv.org/v4lwiki/index.php/Saa7146_devices)

Edit: basically my problem is like that (german page) but not solveable by simply installing dvb-utils [http://www.unixboard.de/vb3/showthread.php?t=22047](http://www.unixboard.de/vb3/showthread.php?t=22047)
```

 dvbnet -l

DVB Network Interface Manager
Version 1.1.0-TVF (Build Tue Nov 20 00:53:11 2007)
Copyright (C) 2003, TV Files S.p.A

Device: /dev/dvb/adapter0/net0
Query DVB network interfaces:
-----------------------------
-----------------------------
Found 0 interface(s).

```

---

### Post by soxs on 2008-11-11
[https://bugs.launchpad.net/ubuntu/+bug/296854](https://bugs.launchpad.net/ubuntu/+bug/296854)
Opend a bugreport at launchpad.net

---

