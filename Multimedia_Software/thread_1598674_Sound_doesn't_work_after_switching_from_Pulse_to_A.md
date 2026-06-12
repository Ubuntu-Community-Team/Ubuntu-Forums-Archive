---
title: "Sound doesn't work after switching from Pulse to ALSA"
date: 2010-10-16
forum: Multimedia Software
---

### Post by anthony62490 on 2010-10-16
I have made a pretty sizable mistake. I was trying to figure out why my game was having sound issues when I was told to update my sound drivers. After a bit of searching, I came across [this]("http://www.stchman.com/alsa_update.html") website. I downloaded and ran the script in the first link. Minor problem: I was using PulseAudio, not ALSA. Needless to say, the script didn't work. 

After the machine rebooted, I had no sound at all. I was planning on switching to ALSA anyway, so I found [this]("http://ubuntuforums.org/showthread.php?t=1229804") thread and ran the following commands:
```
killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio
sudo apt-get purge pulseaudio

```

So now I have no sound. 

There is no volume control in my top taskbar. 

"System>Preferences>Sound" Brings up a window that says, "Waiting for sound system to respond" and never closes until I hit Cancel.

"esd --help" gives me the following info:
```
anthony@anthony-desktop:~$ esd --help
Esound version 0.2.41

Usage: esd [options]

  -v --version  print version information
  -d DEVICE     force esd to use sound device DEVICE
  -b            run server in 8 bit sound mode
  -r RATE       run server at sample rate of RATE
  -as SECS      free audio device after SECS of inactivity (-1 to disable)
  -unix         use unix domain sockets instead of tcp/ip
  -tcp          use tcp/ip sockets instead of unix domain
  -public       make tcp/ip access public (other than localhost)
  -promiscuous  start unlocked and owned (disable authenticaton) NOT RECOMMENDED
  -terminate    terminate esd daemon after last client exits
  -noterminate  do not terminate esd daemon after last client exits
  -nobeeps      disable startup beeps
  -beeps        enable startup beeps
  -trust        start esd even if use of /tmp/.esd-1000 can be insecure
  -port PORT    listen for connections on PORT (only for tcp/ip)
  -bind ADDRESS binds to ADDRESS (only for tcp/ip)

**Possible devices are:  No available cards found** (this concerns me)

```

"aplay -l" gives me the following:
```
anthony@anthony-desktop:~$ aplay -l
**aplay: device_list:207: no soundcards found...**
```

And I also tried "lspci -v":
```
anthony@anthony-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: ec000000-edffffff
	Prefetchable memory behind bridge: e4000000-ebffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ee100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: ee000000-ee0fffff
	Prefetchable memory behind bridge: 40000000-400fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 40100000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: medium devsel, IRQ 255
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

**00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)**
	Subsystem: Micro-Star International Co., Ltd. Device 5790
	Flags: bus master, medium devsel, latency 0, IRQ 255
	I/O ports at e000 [size=256]
	I/O ports at e400 [size=64]
	Memory at ee101000 (32-bit, non-prefetchable) [size=512]
	Memory at ee102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 03b3
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Memory at e8000000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at e8080000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, rivafb

02:0b.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 05) (prog-if 10)
	Subsystem: Risq Modular Systems, Inc. Device 5811
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at ee011000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Device 577c
	Flags: bus master, medium devsel, latency 32, IRQ 23
	I/O ports at c000 [size=256]
	Memory at ee010000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 40000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: epl, 8139too, 8139cp
```

This confuses me. "esd --help" and "aplay -l" seem to think that I have no sound card, while "lspci - v" seems to think that I do.

Anyway, if you need any more info, just ask and I will provide it. Any help at all would be appreciated. Thanks!

---

### Post by Yellow Pasque on 2010-10-16
> **anthony62490 said:**
> This confuses me. "esd --help" and "aplay -l" seem to think that I have no sound card, while "lspci - v" seems to think that I do.
This means that the hardware is recognized, and a kernel module is loaded, but a sound device is not available to ALSA. Check dmesg to see why.

> "System>Preferences>Sound" Brings up a window that says, "Waiting for sound system to respond" and never closes until I hit Cancel.

This dialog was dependent upon pulseaudio, so this behavior is expected. If you do get your system working without pulse, use this PPA to get a native GNOME volume control that doesn't depend on pulse: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by anthony62490 on 2010-10-17
> **Temüjin said:**
> This means that the hardware is recognized, and a kernel module is loaded, but a sound device is not available to ALSA. Check dmesg to see why.

Okay, "dmesg" gives me this. I see nothing, but maybe you can find something in there.
```
anthony@anthony-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-22-generic (buildd@roseapple) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #65-Ubuntu SMP Thu Sep 16 15:48:58 UTC 2010 (Ubuntu 2.6.31-22.65-generic)
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
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  modified: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  modified: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2f8ab000 - 30033f98
[    0.000000] ACPI: RSDP 000f7800 00014 (v00 IntelR)
[    0.000000] ACPI: RSDT 3fff3000 0002C (v01 IntelR AWRDACPI 42302E31 AWRD 00000001)
[    0.000000] ACPI: FACP 3fff3040 00074 (v01 IntelR AWRDACPI 42302E31 AWRD 00000001)
[    0.000000] ACPI: DSDT 3fff30c0 03852 (v01 INTELR AWRDACPI 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 3fff0000 00040
[    0.000000] ACPI: APIC 3fff6940 00054 (v01 IntelR AWRDACPI 42302E31 AWRD 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008b0160]    TEXT DATA BSS ==> [0000100000 - 00008b0160]
[    0.000000]   #4 [002f8ab000 - 0030033f98]          RAMDISK ==> [002f8ab000 - 0030033f98]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008b1000 - 00008b4159]              BRK ==> [00008b1000 - 00008b4159]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f5950] f5950
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262015
[    0.000000] free_area_init_node: node 0, pgdat c078ad40, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34530 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1805000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259967
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic root=UUID=6c1ea016-c372-470b-8045-cb1ede515ab8 ro splash quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5242240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003fff0)
[    0.000000] Memory: 1017848k/1048512k available (4583k kernel code, 29808k reserved, 2150k data, 544k init, 139208k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0794000 - 0xc081c000   ( 544 kB)
[    0.000000]       .data : 0xc0579f08 - 0xc0793848   (2150 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0579f08   (4583 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2532.878 MHz processor.
[    0.001570] Console: colour VGA+ 80x25
[    0.001576] console [tty0] enabled
[    0.004017] Calibrating delay loop (skipped), value calculated using timer frequency.. 5065.75 BogoMIPS (lpj=10131512)
[    0.004051] Security Framework initialized
[    0.004097] AppArmor: AppArmor initialized
[    0.004109] Mount-cache hash table entries: 512
[    0.004336] Initializing cgroup subsys ns
[    0.004344] Initializing cgroup subsys cpuacct
[    0.004350] Initializing cgroup subsys memory
[    0.004365] Initializing cgroup subsys devices
[    0.004369] Initializing cgroup subsys freezer
[    0.004372] Initializing cgroup subsys net_cls
[    0.004401] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004405] CPU: L2 cache: 512K
[    0.004409] CPU: Hyper-Threading is disabled
[    0.004417] mce: CPU supports 4 MCE banks
[    0.004432] CPU0: Thermal monitoring enabled (TM1)
[    0.004449] Performance Counters: no PMU driver, software counters only.
[    0.004459] Checking 'hlt' instruction... OK.
[    0.020998] SMP alternatives: switching to UP code
[    0.032035] Freeing SMP alternatives: 20k freed
[    0.032073] ACPI: Core revision 20090521
[    0.040419] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082826] CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 07
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (5065.75 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] Booting paravirtualized kernel on bare hardware
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 21:38:54  Date: 10/16/10
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.105954] PCI: PCI BIOS revision 2.10 entry at 0xfb920, last bus=2
[    0.105957] PCI: Using configuration type 1 for base access
[    0.107261] bio: create slab <bio-0> at 0
[    0.107915] ACPI: EC: Look up EC in DSDT
[    0.113951] ACPI: Interpreter enabled
[    0.113964] ACPI: (supports S0 S1 S3 S4 S5)
[    0.113999] ACPI: Using IOAPIC for interrupt routing
[    0.118459] ACPI: No dock devices found.
[    0.118583] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.118645] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.118805] pci 0000:00:1d.0: reg 20 io port: [0xd800-0xd81f]
[    0.118864] pci 0000:00:1d.1: reg 20 io port: [0xd000-0xd01f]
[    0.118922] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]
[    0.118980] pci 0000:00:1d.7: reg 10 32bit mmio: [0xee100000-0xee1003ff]
[    0.119035] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.119041] pci 0000:00:1d.7: PME# disabled
[    0.119098] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.119100] * this clock source is slow. If you are sure your timer does not have
[    0.119101] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.119147] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.119151] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.119180] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.119189] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.119196] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.119204] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.119211] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
[    0.119219] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.119277] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.119326] pci 0000:00:1f.5: reg 10 io port: [0xe000-0xe0ff]
[    0.119333] pci 0000:00:1f.5: reg 14 io port: [0xe400-0xe43f]
[    0.119340] pci 0000:00:1f.5: reg 18 32bit mmio: [0xee101000-0xee1011ff]
[    0.119348] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xee102000-0xee1020ff]
[    0.119379] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.119384] pci 0000:00:1f.5: PME# disabled
[    0.119428] pci 0000:01:00.0: reg 10 32bit mmio: [0xec000000-0xecffffff]
[    0.119435] pci 0000:01:00.0: reg 14 32bit mmio: [0xe4000000-0xe7ffffff]
[    0.119442] pci 0000:01:00.0: reg 18 32bit mmio: [0xe8000000-0xe807ffff]
[    0.119459] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.119516] pci 0000:00:01.0: bridge 32bit mmio: [0xec000000-0xedffffff]
[    0.119521] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe4000000-0xebffffff]
[    0.119572] pci 0000:02:0b.0: reg 10 32bit mmio: [0xee011000-0xee011fff]
[    0.119617] pci 0000:02:0b.0: supports D1 D2
[    0.119620] pci 0000:02:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.119625] pci 0000:02:0b.0: PME# disabled
[    0.119660] pci 0000:02:0c.0: reg 10 io port: [0xc000-0xc0ff]
[    0.119668] pci 0000:02:0c.0: reg 14 32bit mmio: [0xee010000-0xee0100ff]
[    0.119693] pci 0000:02:0c.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.119712] pci 0000:02:0c.0: supports D1 D2
[    0.119715] pci 0000:02:0c.0: PME# supported from D1 D2 D3hot D3cold
[    0.119720] pci 0000:02:0c.0: PME# disabled
[    0.119749] pci 0000:00:1e.0: transparent bridge
[    0.119754] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.119760] pci 0000:00:1e.0: bridge 32bit mmio: [0xee000000-0xee0fffff]
[    0.119775] pci_bus 0000:00: on NUMA node 0
[    0.119782] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.119964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.139452] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.139591] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.139727] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.139863] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.140007] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.140145] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.140281] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.140416] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.140696] SCSI subsystem initialized
[    0.140792] libata version 3.00 loaded.
[    0.140903] usbcore: registered new interface driver usbfs
[    0.140921] usbcore: registered new interface driver hub
[    0.140954] usbcore: registered new device driver usb
[    0.141134] ACPI: WMI: Mapper loaded
[    0.141137] PCI: Using ACPI for IRQ routing
[    0.141329] Bluetooth: Core ver 2.15
[    0.141372] NET: Registered protocol family 31
[    0.141375] Bluetooth: HCI device and connection manager initialized
[    0.141379] Bluetooth: HCI socket layer initialized
[    0.141381] NetLabel: Initializing
[    0.141384] NetLabel:  domain hash size = 128
[    0.141386] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.141403] NetLabel:  unlabeled traffic allowed by default
[    0.143887] pnp: PnP ACPI init
[    0.143929] ACPI: bus type pnp registered
[    0.147459] pnp: PnP ACPI: found 14 devices
[    0.147464] ACPI: ACPI bus type pnp unregistered
[    0.147471] PnPBIOS: Disabled by ACPI PNP
[    0.147487] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[    0.147493] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.147497] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.147501] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.147505] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.147509] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.147513] system 00:00: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.147517] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.147521] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.147525] system 00:00: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.147529] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.147532] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[    0.147542] system 00:03: ioport range 0x400-0x4bf could not be reserved
[    0.147550] system 00:04: ioport range 0xb78-0xb7b has been reserved
[    0.147554] system 00:04: ioport range 0xf78-0xf7b has been reserved
[    0.147563] system 00:04: ioport range 0xa78-0xa7b has been reserved
[    0.147567] system 00:04: ioport range 0xe78-0xe7b has been reserved
[    0.147571] system 00:04: ioport range 0xbbc-0xbbf has been reserved
[    0.147575] system 00:04: ioport range 0xfbc-0xfbf has been reserved
[    0.147578] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.147582] system 00:04: ioport range 0x294-0x297 has been reserved
[    0.182363] AppArmor: AppArmor Filesystem Enabled
[    0.182404] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.182408] pci 0000:00:01.0:   IO window: disabled
[    0.182414] pci 0000:00:01.0:   MEM window: 0xec000000-0xedffffff
[    0.182419] pci 0000:00:01.0:   PREFETCH window: 0xe4000000-0xebffffff
[    0.182425] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.182430] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.182436] pci 0000:00:1e.0:   MEM window: 0xee000000-0xee0fffff
[    0.182441] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x400fffff
[    0.182461] pci 0000:00:1e.0: setting latency timer to 64
[    0.182467] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.182471] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.182474] pci_bus 0000:01: resource 1 mem: [0xec000000-0xedffffff]
[    0.182478] pci_bus 0000:01: resource 2 pref mem [0xe4000000-0xebffffff]
[    0.182481] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.182484] pci_bus 0000:02: resource 1 mem: [0xee000000-0xee0fffff]
[    0.182488] pci_bus 0000:02: resource 2 pref mem [0x40000000-0x400fffff]
[    0.182491] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.182494] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.182549] NET: Registered protocol family 2
[    0.182678] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.183208] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.184695] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.185585] TCP: Hash tables configured (established 131072 bind 65536)
[    0.185591] TCP reno registered
[    0.185805] NET: Registered protocol family 1
[    0.185930] Trying to unpack rootfs image as initramfs...
[    0.458497] Freeing initrd memory: 7715k freed
[    0.473901] cpufreq-nforce2: No nForce2 chipset.
[    0.473943] Scanning for low memory corruption every 60 seconds
[    0.474127] audit: initializing netlink socket (disabled)
[    0.474160] type=2000 audit(1287265133.472:1): initialized
[    0.483311] highmem bounce pool size: 64 pages
[    0.483320] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.485080] VFS: Disk quotas dquot_6.5.2
[    0.485155] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.485873] fuse init (API version 7.12)
[    0.485987] msgmni has been set to 1732
[    0.486268] alg: No test for stdrng (krng)
[    0.486286] io scheduler noop registered
[    0.486289] io scheduler anticipatory registered
[    0.486292] io scheduler deadline registered
[    0.486358] io scheduler cfq registered (default)
[    0.486461] pci 0000:01:00.0: Boot video device
[    0.486574] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.486609] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.486780] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.486786] ACPI: Power Button [PWRF]
[    0.486850] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.486854] ACPI: Power Button [PWRB]
[    0.487223] processor LNXCPU:00: registered as cooling_device0
[    0.487228] ACPI: Processor [CPU0] (supports 2 throttling states)
[    0.489349] isapnp: Scanning for PnP cards...
[    0.684031] Switched to high resolution mode on CPU 0
[    0.843221] isapnp: No Plug & Play device found
[    0.844691] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.844825] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.845256] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.846550] brd: module loaded
[    0.847125] loop: module loaded
[    0.847242] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.847393] ata_piix 0000:00:1f.1: version 2.13
[    0.847421]   alloc irq_desc for 18 on node -1
[    0.847424]   alloc kstat_irqs on node -1
[    0.847436] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.847503] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.847650] scsi0 : ata_piix
[    0.847789] scsi1 : ata_piix
[    0.848966] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.848970] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.849983] Fixed MDIO Bus: probed
[    0.850030] PPP generic driver version 2.4.2
[    0.850184] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.850216]   alloc irq_desc for 23 on node -1
[    0.850220]   alloc kstat_irqs on node -1
[    0.850228] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.850251] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.850257] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.850298] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.854215] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.854538] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee100000
[    0.868011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.868130] usb usb1: configuration #1 chosen from 1 choice
[    0.868170] hub 1-0:1.0: USB hub found
[    0.868184] hub 1-0:1.0: 6 ports detected
[    0.868266] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.868293] uhci_hcd: USB Universal Host Controller Interface driver
[    0.868353]   alloc irq_desc for 16 on node -1
[    0.868357]   alloc kstat_irqs on node -1
[    0.868365] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.868376] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.868381] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.868433] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.868467] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[    0.868571] usb usb2: configuration #1 chosen from 1 choice
[    0.868605] hub 2-0:1.0: USB hub found
[    0.868617] hub 2-0:1.0: 2 ports detected
[    0.868670]   alloc irq_desc for 19 on node -1
[    0.868673]   alloc kstat_irqs on node -1
[    0.868679] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.868686] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.868690] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.868728] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.868762] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    0.868877] usb usb3: configuration #1 chosen from 1 choice
[    0.868911] hub 3-0:1.0: USB hub found
[    0.868923] hub 3-0:1.0: 2 ports detected
[    0.868975] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.868983] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.868987] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.869024] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.869055] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    0.869153] usb usb4: configuration #1 chosen from 1 choice
[    0.869187] hub 4-0:1.0: USB hub found
[    0.869201] hub 4-0:1.0: 2 ports detected
[    0.869319] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.871562] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.871570] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.871654] mice: PS/2 mouse device common for all mice
[    0.871774] rtc_cmos 00:06: RTC can wake from S4
[    0.871826] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.871853] rtc0: alarms up to one month, 242 bytes nvram
[    0.872023] device-mapper: uevent: version 1.0.3
[    0.872162] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.872264] device-mapper: multipath: version 1.1.0 loaded
[    0.872268] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.872425] EISA: Probing bus 0 at eisa.0
[    0.872463] EISA: Detected 0 cards.
[    0.872523] cpuidle: using governor ladder
[    0.872526] cpuidle: using governor menu
[    0.873212] TCP cubic registered
[    0.873382] NET: Registered protocol family 10
[    0.873902] lo: Disabled Privacy Extensions
[    0.874293] NET: Registered protocol family 17
[    0.874321] Bluetooth: L2CAP ver 2.13
[    0.874324] Bluetooth: L2CAP socket layer initialized
[    0.874327] Bluetooth: SCO (Voice Link) ver 0.6
[    0.874329] Bluetooth: SCO socket layer initialized
[    0.874390] Bluetooth: RFCOMM TTY layer initialized
[    0.874394] Bluetooth: RFCOMM socket layer initialized
[    0.874396] Bluetooth: RFCOMM ver 1.11
[    0.874445] Using IPI No-Shortcut mode
[    0.874549] PM: Resume from disk failed.
[    0.874567] registered taskstats version 1
[    0.874691]   Magic number: 14:37:652
[    0.874784] rtc_cmos 00:06: setting system clock to 2010-10-16 21:38:55 UTC (1287265135)
[    0.874788] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.874790] EDD information not available.
[    0.894247] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.024297] ata1.00: ATA-5: ExcelStor Technology ES3220, ES6CA24A, max UDMA/66
[    1.024302] ata1.00: 39078194 sectors, multi 16: LBA 
[    1.024481] ata1.01: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/133
[    1.024485] ata1.01: 80293248 sectors, multi 16: LBA 
[    1.040198] ata1.00: configured for UDMA/66
[    1.056325] ata1.01: configured for UDMA/100
[    1.056489] scsi 0:0:0:0: Direct-Access     ATA      ExcelStor Techno ES6C PQ: 0 ANSI: 5
[    1.056654] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.056751] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[    1.056873] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.056928] sd 0:0:0:0: [sda] 39078194 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.056989] sd 0:0:0:0: [sda] Write Protect is off
[    1.056994] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.057026] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.057199]  sda: sda1 sda2 < sda5 >
[    1.092676] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.092692] sd 0:0:1:0: [sdb] 80293248 512-byte logical blocks: (41.1 GB/38.2 GiB)
[    1.092750] sd 0:0:1:0: [sdb] Write Protect is off
[    1.092755] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.092786] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.092947]  sdb:
[    1.416295] ata2.00: ATAPI: Hewlett-Packard DVD Writer 200, 1.36, max UDMA/33
[    1.416344] ata2.01: ATAPI: LITEON  DVD-ROM LTD163, GKS3, max UDMA/33
[    1.420012] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    1.432199] ata2.00: configured for UDMA/33
[    1.440196] ata2.01: configured for UDMA/33
[    1.443041] scsi 1:0:0:0: CD-ROM            HP       DVD Writer 200j  1.36 PQ: 0 ANSI: 5
[    1.445591] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    1.445597] Uniform CD-ROM driver Revision: 3.20
[    1.445715] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.445789] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.446068] scsi 1:0:1:0: CD-ROM            LITEON   DVD-ROM LTD163   GKS3 PQ: 0 ANSI: 5
[    1.447688] sr1: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[    1.447780] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.447844] sr 1:0:1:0: Attached scsi generic sg3 type 5
[    1.589453] usb 2-2: configuration #1 chosen from 1 choice
[    1.592421] hub 2-2:1.0: USB hub found
[    1.594391] hub 2-2:1.0: 4 ports detected
[    1.802602]  sdb1 sdb2 < sdb5 >
[    1.825904] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.825927] Freeing unused kernel memory: 544k freed
[    1.826822] Write protecting the kernel text: 4584k
[    1.826856] Write protecting the kernel read-only data: 1844k
[    2.073453] Linux agpgart interface v0.103
[    2.124233] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    2.127360] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[    2.130345] Floppy drive(s): fd0 is 1.44M
[    2.135881] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.135933] 8139cp 0000:02:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.153213] FDC 0 is a post-1991 82077
[    2.251863] ohci1394 0000:02:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.255739] 8139too Fast Ethernet driver 0.9.28
[    2.350038] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[ee011000-ee0117ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    2.360389] 8139too 0000:02:0c.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.361531] eth0: RealTek RTL8139 at 0xc000, 00:10:dc:7b:f1:b2, IRQ 23
[    3.311805] xor: automatically using best checksumming function: pIII_sse
[    3.328008]    pIII_sse  :  3235.000 MB/sec
[    3.328011] xor: using function: pIII_sse (3235.000 MB/sec)
[    3.332357] device-mapper: dm-raid45: initialized v0.2594b
[    3.636188] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000516000051cd92]
[    3.952659] PM: Starting manual resume from disk
[    3.952666] PM: Resume from partition 8:5
[    3.952669] PM: Checking hibernation image.
[    3.952932] PM: Resume from disk failed.
[    3.978229] EXT4-fs (sda1): barriers enabled
[    4.000518] kjournald2 starting: pid 369, dev sda1:8, commit interval 5 seconds
[    4.000571] EXT4-fs (sda1): delayed allocation enabled
[    4.000576] EXT4-fs: file extents enabled
[    4.000793] EXT4-fs: mballoc enabled
[    4.000814] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.279580] type=1505 audit(1287265139.904:2): operation="profile_load" pid=393 name=/usr/share/gdm/guest-session/Xsession
[    5.314420] type=1505 audit(1287265139.937:3): operation="profile_load" pid=394 name=/sbin/dhclient3
[    5.315072] type=1505 audit(1287265139.937:4): operation="profile_load" pid=394 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.315430] type=1505 audit(1287265139.937:5): operation="profile_load" pid=394 name=/usr/lib/connman/scripts/dhclient-script
[    5.437922] type=1505 audit(1287265140.061:6): operation="profile_load" pid=395 name=/usr/bin/evince
[    5.448819] type=1505 audit(1287265140.073:7): operation="profile_load" pid=395 name=/usr/bin/evince-previewer
[    5.455216] type=1505 audit(1287265140.077:8): operation="profile_load" pid=395 name=/usr/bin/evince-thumbnailer
[    5.527397] type=1505 audit(1287265140.149:9): operation="profile_load" pid=397 name=/usr/lib/cups/backend/cups-pdf
[    5.528185] type=1505 audit(1287265140.153:10): operation="profile_load" pid=397 name=/usr/sbin/cupsd
[    5.532035] type=1505 audit(1287265140.153:11): operation="profile_load" pid=398 name=/usr/sbin/tcpdump
[    7.107809] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k 
[    8.309038] EXT4-fs (sda1): internal journal on sda1:8
[   10.147062] udev: starting version 147
[   12.168585] lp: driver loaded but no devices found
[   12.194654] parport_pc 00:0b: reported by Plug and Play ACPI
[   12.194756] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   12.210872] ppdev: user-space parallel port driver
[   12.284259] lp0: using parport0 (interrupt-driven).
[   13.434126] type=1505 audit(1287265148.057:12): operation="profile_replace" pid=688 name=/usr/share/gdm/guest-session/Xsession
[   13.437115] type=1505 audit(1287265148.061:13): operation="profile_replace" pid=689 name=/sbin/dhclient3
[   13.437775] type=1505 audit(1287265148.061:14): operation="profile_replace" pid=689 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   13.438135] type=1505 audit(1287265148.061:15): operation="profile_replace" pid=689 name=/usr/lib/connman/scripts/dhclient-script
[   13.448211] type=1505 audit(1287265148.073:16): operation="profile_replace" pid=690 name=/usr/bin/evince
[   13.459613] type=1505 audit(1287265148.081:17): operation="profile_replace" pid=690 name=/usr/bin/evince-previewer
[   13.469144] type=1505 audit(1287265148.093:18): operation="profile_replace" pid=690 name=/usr/bin/evince-thumbnailer
[   13.480680] type=1505 audit(1287265148.105:19): operation="profile_replace" pid=693 name=/usr/lib/cups/backend/cups-pdf
[   13.481456] type=1505 audit(1287265148.105:20): operation="profile_replace" pid=693 name=/usr/sbin/cupsd
[   13.485434] type=1505 audit(1287265148.109:21): operation="profile_replace" pid=694 name=/usr/sbin/tcpdump
[   13.633726] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.696076] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.708471] intel_rng: FWH not detected
[   13.969965] psmouse serio1: ID: 10 00 64
[   14.483719] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   15.777787] nvidia: module license 'NVIDIA' taints kernel.
[   15.777794] Disabling lock debugging due to kernel taint
[   16.047162] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.047636] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[   23.492980] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   33.612011] eth0: no IPv6 routers present
[   39.545221] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   39.545244] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   39.545279] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[ 3555.405054] kjournald starting.  Commit interval 5 seconds
[ 3555.405456] EXT3 FS on sdb1, internal journal
[ 3555.405465] EXT3-fs: mounted filesystem with ordered data mode.
[ 7211.396027] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 7211.556112] usb 4-2: configuration #1 chosen from 1 choice
[ 7211.644467] cdc_acm 4-2:1.0: ttyACM0: USB ACM device
[ 7211.647097] usbcore: registered new interface driver cdc_acm
[ 7211.647104] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 7215.232053] usb 4-2: USB disconnect, address 2
[ 7216.464025] usb 4-2: new full speed USB device using uhci_hcd and address 3
[ 7216.640264] usb 4-2: configuration #1 chosen from 1 choice
[ 7324.600053] usb 4-2: USB disconnect, address 3
[ 7326.080038] usb 4-2: new full speed USB device using uhci_hcd and address 4
[ 7326.245369] usb 4-2: configuration #1 chosen from 1 choice
[ 7326.248309] cdc_acm 4-2:1.0: ttyACM0: USB ACM device
[ 7581.382477] sr0: Hmm, seems the drive doesn't support multisession CD's **(is it trying to say that my CD drive sucks?)**
[ 7581.450083] cdrom: This disc doesn't have any tracks I recognize!
[ 7581.495432] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7581.495439] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 7581.495445] sr 1:0:0:0: [sr0] Add. Sense: Invalid packet size
[ 7581.495453] end_request: I/O error, dev sr0, sector 0
[ 7581.495461] Buffer I/O error on device sr0, logical block 0
[ 7581.506767] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7581.506775] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 7581.506781] sr 1:0:0:0: [sr0] Add. Sense: Invalid packet size
[ 7581.506790] end_request: I/O error, dev sr0, sector 0
[ 7581.506797] Buffer I/O error on device sr0, logical block 0
[ 7856.545428] /usr/bin/serpen[6261]: segfault at 465 ip 00ada293 sp bfa45df0 error 4 in libgobject-2.0.so.0.2200.2[ab7000+3c000]
[ 8845.724683] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8845.724690] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8845.724696] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8845.724705] end_request: I/O error, dev sr0, sector 0
[ 8845.724712] Buffer I/O error on device sr0, logical block 0
[ 8845.724721] Buffer I/O error on device sr0, logical block 1
[ 8845.724725] Buffer I/O error on device sr0, logical block 2
[ 8845.724729] Buffer I/O error on device sr0, logical block 3
[ 8845.724733] Buffer I/O error on device sr0, logical block 4
[ 8845.724736] Buffer I/O error on device sr0, logical block 5
[ 8845.724740] Buffer I/O error on device sr0, logical block 6
[ 8845.724743] Buffer I/O error on device sr0, logical block 7
[ 8845.724747] Buffer I/O error on device sr0, logical block 8
[ 8845.730205] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8845.730214] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8845.730220] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8845.730229] end_request: I/O error, dev sr0, sector 0
[ 8845.821554] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8845.821561] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8845.821567] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8845.821575] end_request: I/O error, dev sr0, sector 0
[ 8845.822982] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8845.822987] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8845.822992] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8845.822998] end_request: I/O error, dev sr0, sector 0
[ 8845.824236] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8845.824242] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8845.824246] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8845.824253] end_request: I/O error, dev sr0, sector 0
[ 9347.040061] usb 4-2: USB disconnect, address 4
```

------------------------
------------------------

 > **Temüjin said:**
> If you do get your system working without pulse, use this PPA to get a native GNOME volume control that doesn't depend on pulse: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

Okay, I'm confused. I followed the instructions to install the software. But as soon as it says that I am capable of installing, it stops giving directions. It doesn't actually say how to install it. 

Here's what I got:
```
anthony@anthony-desktop:~$ sudo add-apt-repository ppa:dtl131/ppa
[sudo] password for anthony: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4D140B0620B0474CDA69B8A0AD70EA6AF76FFEBE
gpg: requesting key F76FFEBE from hkp server keyserver.ubuntu.com
gpg: key F76FFEBE: public key "Launchpad audiohacks" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```
The package is not in Synaptic, but under Settings>Repositories>Authentication, I can see the Audiohacks key. What do I need to do to finish the installation?

---

### Post by anthony62490 on 2010-10-17
bump

---

### Post by anthony62490 on 2010-10-17
Okay, maybe I can be a bit more helpful. I went through the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") page, but when I got to checking if ALSA is using the correct model, the Driver Version section is blank.
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun Oct 17 21:32:33 UTC 2010

!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"

!!DMI Information
!!---------------

Manufacturer:      HP Pavilion 05
Product Name:      P9924A-ABA 783c

!!Kernel Information
!!------------------

Kernel release:    2.6.31-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes

!!ALSA Version
!!------------

Driver version:     **       (there should be a driver number here)**
Library version:    1.0.16
Utilities version:  1.0.16

!!Loaded ALSA modules
!!-------------------
**(this section is also blank. There should be a module name here)**

!!Sound Servers on this system
!!----------------------------

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

!!Soundcards recognised by ALSA
!!-----------------------------

!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:24c5 (rev 01)
    Subsystem: 1462:5790

!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=3stack
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N

!!Loaded sound module options
!!--------------------------

!!ALSA Device nodes
!!-----------------

!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:207: no soundcards found...

ARECORD

arecord: device_list:207: no soundcards found...

!!Amixer output
!!-------------

!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--

!!All Loaded Modules
!!------------------

Module
binfmt_misc
ppdev
lp
parport_pc
parport
nvidia
iptable_filter
psmouse
ip_tables
serio_raw
shpchp
x_tables
soundcore
dm_raid45
xor
ohci1394
ieee1394
8139too
8139cp
mii
floppy
intel_agp
agpgart

!!ALSA/HDA dmesg
!!------------------
```

The troubleshooting guide doesn't seem to have any answers for this particular problem. Any ideas?

---

### Post by anthony62490 on 2010-10-17
bump

---

### Post by Yellow Pasque on 2010-10-17
Why do you have ALSA 1.0.16?

---

### Post by anthony62490 on 2010-10-17
> **Temüjin said:**
> Why do you have ALSA 1.0.16?
In all honesty? I don't know. That must be what the script from Post 1 installed for me.

---

### Post by anthony62490 on 2010-10-18
bump

---

### Post by Yellow Pasque on 2010-10-18
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by anthony62490 on 2010-10-18
> **Temüjin said:**
> [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Wow. That worked like a dream. I need to keep that link handy. There are still a few things that aren't QUITE working right, but I have sound again. Ill keep the other issues for another thread. Thank you so much.

---

