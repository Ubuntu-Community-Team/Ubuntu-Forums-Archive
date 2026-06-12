---
title: "Ubuntu 9.04 - Cannot activate Atheros AR9285 Wireless Adapter"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by Mezzoforte on 2009-06-06
I have installed Ubuntu 9.04 but have problems get it connected to the wireless network - or rather, there seems to be a problem actually activating the wireless adapter. The laptop has a touch control for activating the wireless, but nothing happens when touching (this works fine in Windows though).

I am grateful for any help! Information about the adapter and my setup:

Computer: HP Pavilion DV6 (laptop)
OS: Ubuntu 9.04
Kernel/architecture: 2.6.28-11-generic i686

Output from lspci -v: (I only include the wireless adapter here)

```
08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 3040
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d1200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
	Capabilities: [170] Power Budgeting <?>

```

ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:23:8b:ac:63:ca  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:feac:63ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4460368 (4.4 MB)  TX bytes:497573 (497.5 KB)
          Interrupt:249 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

iwconfig output:

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

lsmod output:

```
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
leds_hp_disk           10756  0 
led_class              12036  1 leds_hp_disk
uvcvideo               63240  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  25360  0 
fglrx                2081668  33 
psmouse                61972  0 
compat_ioctl32          9344  1 uvcvideo
joydev                 18368  0 
soundcore              15200  1 snd
output                 11008  1 video
agpgart                42696  1 fglrx
serio_raw              13316  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
lis3lv02d              17848  0 
pcspkr                 10496  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i2c_piix4              18448  0 
usbhid                 42336  0 
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Output from dmesg:

```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfb90000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb90000 - 00000000bfc3c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfc3c000 - 00000000bfd70000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd70000 - 00000000bfdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfdbf000 - 00000000bfe58000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe58000 - 00000000bfebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfebf000 - 00000000bfeed000 (usable)
[    0.000000]  BIOS-e820: 00000000bfeed000 - 00000000bfeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbff00 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfb90000 (usable)
[    0.000000]  modified: 00000000bfb90000 - 00000000bfc3c000 (ACPI NVS)
[    0.000000]  modified: 00000000bfc3c000 - 00000000bfd70000 (usable)
[    0.000000]  modified: 00000000bfd70000 - 00000000bfdbf000 (reserved)
[    0.000000]  modified: 00000000bfdbf000 - 00000000bfe58000 (usable)
[    0.000000]  modified: 00000000bfe58000 - 00000000bfebf000 (ACPI NVS)
[    0.000000]  modified: 00000000bfebf000 - 00000000bfeed000 (usable)
[    0.000000]  modified: 00000000bfeed000 - 00000000bfeff000 (ACPI data)
[    0.000000]  modified: 00000000bfeff000 - 00000000bff00000 (usable)
[    0.000000]  modified: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bd000 - 37fef890
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb3890
[    0.000000] Move RAMDISK from 00000000378bd000 - 0000000037fef88f to 00881000 - 00fb388f
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT BFEFE120, 005C (r1 HPQOEM SLIC-MPC        3       1000013)
[    0.000000] ACPI: FACP BFEFD000, 00F4 (r4 HP     3060            3 MSFT  1000013)
[    0.000000] ACPI: DSDT BFEF0000, 931E (r1 HP     3060     F0000000 MSFT  1000013)
[    0.000000] ACPI: FACS BFE61000, 0040
[    0.000000] ACPI: HPET BFEFC000, 0038 (r1 HP     3060            1 MSFT  1000013)
[    0.000000] ACPI: APIC BFEFB000, 0084 (r2 HP     3060            1 MSFT  1000013)
[    0.000000] ACPI: MCFG BFEFA000, 003C (r1 HP     3060            1 MSFT  1000013)
[    0.000000] ACPI: BOOT BFEEF000, 0028 (r1 HP     3060            1 MSFT  1000013)
[    0.000000] ACPI: SLIC BFEEE000, 0176 (r1 HPQOEM SLIC-MPC  6040000 MSFT  1000013)
[    0.000000] ACPI: SSDT BFEED000, 0386 (r1 AMD    PowerNow        1 AMD         1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2187MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb3890]      NEW RAMDISK ==> [0000881000 - 0000fb3890]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bff00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x000bfb90
[    0.000000]     0: 0x000bfc3c -> 0x000bfd70
[    0.000000]     0: 0x000bfdbf -> 0x000bfe58
[    0.000000]     0: 0x000bfebf -> 0x000bfeed
[    0.000000]     0: 0x000bfeff -> 0x000bff00
[    0.000000] On node 0 totalpages: 785681
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4375 pages used for memmap
[    0.000000]   HighMem zone: 555127 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: bff00000:20100000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779538
[    0.000000] Kernel command line: root=UUID=d4f4ae6b-6157-48c7-b887-8a9b1865adb7 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2200.057 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15723520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3085744k/3144704k available (4126k kernel code, 56060k reserved, 2208k data, 532k init, 2238008k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 4400.11 BogoMIPS (lpj=8800228)
[    0.004054] Security Framework initialized
[    0.004063] SELinux:  Disabled at boot.
[    0.004088] AppArmor: AppArmor initialized
[    0.004102] Mount-cache hash table entries: 512
[    0.004324] Initializing cgroup subsys ns
[    0.004331] Initializing cgroup subsys cpuacct
[    0.004336] Initializing cgroup subsys memory
[    0.004343] Initializing cgroup subsys freezer
[    0.004363] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004368] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004372] CPU: Physical Processor ID: 0
[    0.004376] CPU: Processor Core ID: 0
[    0.004381] using C1E aware idle routine
[    0.004397] Checking 'hlt' instruction... OK.
[    0.024013] ACPI: Core revision 20080926
[    0.028502] ACPI: Checking initramfs for custom DSDT
[    0.548649] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.589304] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-75 stepping 01
[    0.592002] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4389.07 BogoMIPS (lpj=8778146)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.680244] CPU1: AMD Turion(tm) X2 Dual-Core Mobile RM-75 stepping 01
[    0.680276] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.684002] Measured 65558947 cycles TSC warp between CPUs, turning off TSC clock.
[    0.684002] Marking TSC unstable due to check_tsc_sync_source failed
[    0.684044] Brought up 2 CPUs
[    0.684048] Total of 2 processors activated (8789.18 BogoMIPS).
[    0.684141] CPU0 attaching sched-domain:
[    0.684145]  domain 0: span 0-1 level CPU
[    0.684150]   groups: 0 1
[    0.684160] CPU1 attaching sched-domain:
[    0.684163]  domain 0: span 0-1 level CPU
[    0.684167]   groups: 1 0
[    0.684278] net_namespace: 776 bytes
[    0.684290] Booting paravirtualized kernel on bare hardware
[    0.684596] Time: 12:36:38  Date: 06/06/09
[    0.684596] regulator: core version 0.5
[    0.684596] NET: Registered protocol family 16
[    0.684596] EISA bus registered
[    0.684596] ACPI: bus type pci registered
[    0.684596] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.684596] PCI: MCFG area at e0000000 reserved in E820
[    0.684596] PCI: Using MMCONFIG for extended config space
[    0.684596] PCI: Using configuration type 1 for base access
[    0.689293] ACPI: EC: Look up EC in DSDT
[    0.697972] ACPI: BIOS _OSI(Linux) query ignored
[    0.708016] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.712082] ACPI: Interpreter enabled
[    0.712088] ACPI: (supports S0 S3 S4 S5)
[    0.712117] ACPI: Using IOAPIC for interrupt routing
[    0.724429] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.724432] ACPI: EC: driver started in interrupt mode
[    0.724572] ACPI: No dock devices found.
[    0.724581] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.724712] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.724717] pci 0000:00:02.0: PME# disabled
[    0.724751] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.724754] pci 0000:00:04.0: PME# disabled
[    0.724786] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.724789] pci 0000:00:05.0: PME# disabled
[    0.724821] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.724824] pci 0000:00:06.0: PME# disabled
[    0.724861] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.724864] pci 0000:00:0a.0: PME# disabled
[    0.724922] pci 0000:00:11.0: reg 10 io port: [0x6038-0x603f]
[    0.724930] pci 0000:00:11.0: reg 14 io port: [0x604c-0x604f]
[    0.724938] pci 0000:00:11.0: reg 18 io port: [0x6030-0x6037]
[    0.724946] pci 0000:00:11.0: reg 1c io port: [0x6048-0x604b]
[    0.724953] pci 0000:00:11.0: reg 20 io port: [0x6010-0x601f]
[    0.724961] pci 0000:00:11.0: reg 24 32bit mmio: [0xd2408000-0xd24083ff]
[    0.725004] pci 0000:00:12.0: reg 10 32bit mmio: [0xd2407000-0xd2407fff]
[    0.725064] pci 0000:00:12.1: reg 10 32bit mmio: [0xd2406000-0xd2406fff]
[    0.725143] pci 0000:00:12.2: reg 10 32bit mmio: [0xd2408500-0xd24085ff]
[    0.725187] pci 0000:00:12.2: supports D1 D2
[    0.725189] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.725193] pci 0000:00:12.2: PME# disabled
[    0.725229] pci 0000:00:13.0: reg 10 32bit mmio: [0xd2405000-0xd2405fff]
[    0.725288] pci 0000:00:13.1: reg 10 32bit mmio: [0xd2404000-0xd2404fff]
[    0.725367] pci 0000:00:13.2: reg 10 32bit mmio: [0xd2408400-0xd24084ff]
[    0.725411] pci 0000:00:13.2: supports D1 D2
[    0.725413] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.725418] pci 0000:00:13.2: PME# disabled
[    0.728124] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.728132] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.728139] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.728146] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.728154] pci 0000:00:14.1: reg 20 io port: [0x6000-0x600f]
[    0.728220] pci 0000:00:14.2: reg 10 64bit mmio: [0xd2400000-0xd2403fff]
[    0.728259] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.728264] pci 0000:00:14.2: PME# disabled
[    0.728566] pci 0000:01:00.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.728573] pci 0000:01:00.0: reg 14 io port: [0x5000-0x50ff]
[    0.728580] pci 0000:01:00.0: reg 18 32bit mmio: [0xd2300000-0xd230ffff]
[    0.728598] pci 0000:01:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.728606] pci 0000:01:00.0: supports D1 D2
[    0.728640] pci 0000:01:00.1: reg 10 32bit mmio: [0xd2310000-0xd2313fff]
[    0.728672] pci 0000:01:00.1: supports D1 D2
[    0.728769] pci 0000:00:02.0: bridge io port: [0x5000-0x5fff]
[    0.728773] pci 0000:00:02.0: bridge 32bit mmio: [0xd2300000-0xd23fffff]
[    0.728778] pci 0000:00:02.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.728832] pci 0000:00:04.0: bridge io port: [0x3000-0x4fff]
[    0.728836] pci 0000:00:04.0: bridge 32bit mmio: [0xd1300000-0xd22fffff]
[    0.728841] pci 0000:00:04.0: bridge 64bit mmio pref: [0xd0000000-0xd0ffffff]
[    0.728886] pci 0000:08:00.0: reg 10 64bit mmio: [0xd1200000-0xd120ffff]
[    0.728922] pci 0000:08:00.0: supports D1
[    0.728924] pci 0000:08:00.0: PME# supported from D0 D1 D3hot
[    0.728928] pci 0000:08:00.0: PME# disabled
[    0.729024] pci 0000:00:05.0: bridge 32bit mmio: [0xd1200000-0xd12fffff]
[    0.729067] pci 0000:09:00.0: reg 10 io port: [0x2000-0x20ff]
[    0.729085] pci 0000:09:00.0: reg 18 64bit mmio: [0xd1004000-0xd1004fff]
[    0.729097] pci 0000:09:00.0: reg 20 64bit mmio: [0xd1000000-0xd1003fff]
[    0.729105] pci 0000:09:00.0: reg 30 32bit mmio: [0xffff0000-0xffffffff]
[    0.729115] pci 0000:09:00.0: supports D1 D2
[    0.729117] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.729121] pci 0000:09:00.0: PME# disabled
[    0.729220] pci 0000:00:06.0: bridge io port: [0x2000-0x2fff]
[    0.729226] pci 0000:00:06.0: bridge 64bit mmio pref: [0xd1000000-0xd10fffff]
[    0.729281] pci 0000:00:0a.0: bridge 32bit mmio: [0xd1100000-0xd11fffff]
[    0.729348] pci 0000:00:14.4: transparent bridge
[    0.729353] pci 0000:00:14.4: bridge io port: [0x1000-0x1fff]
[    0.729380] bus 00 -> node 0
[    0.729390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.729828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB2_._PRT]
[    0.729984] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.730134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.730287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.730439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB10._PRT]
[    0.730618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.744305] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.744454] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.744669] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.744884] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.745064] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.745278] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.745454] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.745668] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.745930] ACPI: WMI: Mapper loaded
[    0.745975] SCSI subsystem initialized
[    0.745975] libata version 3.00 loaded.
[    0.745975] usbcore: registered new interface driver usbfs
[    0.745975] usbcore: registered new interface driver hub
[    0.745975] usbcore: registered new device driver usb
[    0.745975] PCI: Using ACPI for IRQ routing
[    0.748013] Bluetooth: Core ver 2.13
[    0.748023] NET: Registered protocol family 31
[    0.748023] Bluetooth: HCI device and connection manager initialized
[    0.748023] Bluetooth: HCI socket layer initialized
[    0.748023] NET: Registered protocol family 8
[    0.748023] NET: Registered protocol family 20
[    0.748031] NetLabel: Initializing
[    0.748033] NetLabel:  domain hash size = 128
[    0.748034] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.748048] NetLabel:  unlabeled traffic allowed by default
[    0.748098] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 2303, 0
[    0.748104] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.752065] hpet: hpet2 irq 2303 for MSI
[    0.752088] AppArmor: AppArmor Filesystem Enabled
[    0.756033] Switched to high resolution mode on CPU 0
[    0.756326] Switched to high resolution mode on CPU 1
[    0.756336] pnp: PnP ACPI init
[    0.756348] ACPI: bus type pnp registered
[    0.761729] pnp: PnP ACPI: found 13 devices
[    0.761731] ACPI: ACPI bus type pnp unregistered
[    0.761735] PnPBIOS: Disabled by ACPI PNP
[    0.761745] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.761748] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.761758] system 00:09: ioport range 0x400-0x4cf has been reserved
[    0.761760] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.761763] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[    0.761765] system 00:09: ioport range 0x680-0x6ff has been reserved
[    0.761768] system 00:09: ioport range 0x77a-0x77a has been reserved
[    0.761771] system 00:09: ioport range 0xc00-0xc01 has been reserved
[    0.761773] system 00:09: ioport range 0xc14-0xc14 has been reserved
[    0.761775] system 00:09: ioport range 0xc50-0xc52 has been reserved
[    0.761778] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[    0.761780] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[    0.761783] system 00:09: ioport range 0xcd0-0xcdb has been reserved
[    0.761785] system 00:09: ioport range 0x380-0x387 has been reserved
[    0.761791] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[    0.761794] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.796711] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.796715] pci 0000:00:02.0:   IO window: 0x5000-0x5fff
[    0.796720] pci 0000:00:02.0:   MEM window: 0xd2300000-0xd23fffff
[    0.796724] pci 0000:00:02.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.796729] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.796732] pci 0000:00:04.0:   IO window: 0x3000-0x4fff
[    0.796736] pci 0000:00:04.0:   MEM window: 0xd1300000-0xd22fffff
[    0.796740] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000d0ffffff
[    0.796745] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08
[    0.796746] pci 0000:00:05.0:   IO window: disabled
[    0.796750] pci 0000:00:05.0:   MEM window: 0xd1200000-0xd12fffff
[    0.796753] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.796758] pci 0000:00:06.0: PCI bridge, secondary bus 0000:09
[    0.796761] pci 0000:00:06.0:   IO window: 0x2000-0x2fff
[    0.796764] pci 0000:00:06.0:   MEM window: 0xd2500000-0xd25fffff
[    0.796768] pci 0000:00:06.0:   PREFETCH window: 0x000000d1000000-0x000000d10fffff
[    0.796772] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:0a
[    0.796774] pci 0000:00:0a.0:   IO window: disabled
[    0.796778] pci 0000:00:0a.0:   MEM window: 0xd1100000-0xd11fffff
[    0.796781] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.796786] pci 0000:00:14.4: PCI bridge, secondary bus 0000:80
[    0.796823] pci 0000:00:14.4:   IO window: 0x1000-0x1fff
[    0.796829] pci 0000:00:14.4:   MEM window: disabled
[    0.796834] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.796849] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.796855] pci 0000:00:02.0: setting latency timer to 64
[    0.796862] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.796865] pci 0000:00:04.0: setting latency timer to 64
[    0.796872] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.796876] pci 0000:00:05.0: setting latency timer to 64
[    0.796882] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.796885] pci 0000:00:06.0: setting latency timer to 64
[    0.796892] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.796895] pci 0000:00:0a.0: setting latency timer to 64
[    0.796904] bus: 00 index 0 io port: [0x00-0xffff]
[    0.796906] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.796908] bus: 01 index 0 io port: [0x5000-0x5fff]
[    0.796911] bus: 01 index 1 mmio: [0xd2300000-0xd23fffff]
[    0.796913] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.796915] bus: 01 index 3 mmio: [0x0-0x0]
[    0.796917] bus: 02 index 0 io port: [0x3000-0x4fff]
[    0.796919] bus: 02 index 1 mmio: [0xd1300000-0xd22fffff]
[    0.796921] bus: 02 index 2 mmio: [0xd0000000-0xd0ffffff]
[    0.796924] bus: 02 index 3 mmio: [0x0-0x0]
[    0.796925] bus: 08 index 0 mmio: [0x0-0x0]
[    0.796928] bus: 08 index 1 mmio: [0xd1200000-0xd12fffff]
[    0.796929] bus: 08 index 2 mmio: [0x0-0x0]
[    0.796931] bus: 08 index 3 mmio: [0x0-0x0]
[    0.796933] bus: 09 index 0 io port: [0x2000-0x2fff]
[    0.796935] bus: 09 index 1 mmio: [0xd2500000-0xd25fffff]
[    0.796938] bus: 09 index 2 mmio: [0xd1000000-0xd10fffff]
[    0.796939] bus: 09 index 3 mmio: [0x0-0x0]
[    0.796941] bus: 0a index 0 mmio: [0x0-0x0]
[    0.796943] bus: 0a index 1 mmio: [0xd1100000-0xd11fffff]
[    0.796945] bus: 0a index 2 mmio: [0x0-0x0]
[    0.796946] bus: 0a index 3 mmio: [0x0-0x0]
[    0.796949] bus: 80 index 0 io port: [0x1000-0x1fff]
[    0.796951] bus: 80 index 1 mmio: [0x0-0x0]
[    0.796952] bus: 80 index 2 mmio: [0x0-0x0]
[    0.796954] bus: 80 index 3 io port: [0x00-0xffff]
[    0.796956] bus: 80 index 4 mmio: [0x000000-0xffffffff]
[    0.796967] NET: Registered protocol family 2
[    0.808596] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.808857] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.809442] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.809704] TCP: Hash tables configured (established 131072 bind 65536)
[    0.809707] TCP reno registered
[    0.812631] NET: Registered protocol family 1
[    0.812757] checking if image is initramfs... it is
[    1.348669] Freeing initrd memory: 7370k freed
[    1.348701] Simple Boot Flag at 0x44 set to 0x1
[    1.348952] cpufreq: No nForce2 chipset.
[    1.349075] audit: initializing netlink socket (disabled)
[    1.349089] type=2000 audit(1244291798.348:1): initialized
[    1.356545] highmem bounce pool size: 64 pages
[    1.356551] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.357794] VFS: Disk quotas dquot_6.5.1
[    1.357850] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.358469] fuse init (API version 7.10)
[    1.358549] msgmni has been set to 1671
[    1.358809] alg: No test for stdrng (krng)
[    1.358828] io scheduler noop registered
[    1.358830] io scheduler anticipatory registered
[    1.358832] io scheduler deadline registered
[    1.358846] io scheduler cfq registered (default)
[    1.532107] pci 0000:01:00.0: Boot video device
[    1.532327] _OSC request fails
[    1.534708] _OSC request fails
[    1.538550] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.538584] pcieport-driver 0000:00:02.0: found MSI capability
[    1.538609] pcieport-driver 0000:00:02.0: irq 2302 for MSI/MSI-X
[    1.538620] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.538640] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.538687] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.538716] pcieport-driver 0000:00:04.0: found MSI capability
[    1.538736] pcieport-driver 0000:00:04.0: irq 2301 for MSI/MSI-X
[    1.538746] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.538759] pci_express 0000:00:04.0:pcie02: allocate port service
[    1.538771] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.538816] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.538845] pcieport-driver 0000:00:05.0: found MSI capability
[    1.538865] pcieport-driver 0000:00:05.0: irq 2300 for MSI/MSI-X
[    1.538875] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.538888] pci_express 0000:00:05.0:pcie03: allocate port service
[    1.538933] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.538962] pcieport-driver 0000:00:06.0: found MSI capability
[    1.538982] pcieport-driver 0000:00:06.0: irq 2299 for MSI/MSI-X
[    1.538992] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.539005] pci_express 0000:00:06.0:pcie03: allocate port service
[    1.539049] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.539079] pcieport-driver 0000:00:0a.0: found MSI capability
[    1.539098] pcieport-driver 0000:00:0a.0: irq 2298 for MSI/MSI-X
[    1.539108] pci_express 0000:00:0a.0:pcie00: allocate port service
[    1.539124] pci_express 0000:00:0a.0:pcie03: allocate port service
[    1.539184] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.539278] _OSC request fails
[    1.539316] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.541363] ACPI: AC Adapter [ACAD] (on-line)
[    1.580872] ACPI: Battery Slot [BAT0] (battery present)
[    1.580982] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.580986] ACPI: Power Button (FF) [PWRF]
[    1.581025] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.581028] ACPI: Power Button (CM) [PWRB]
[    1.581068] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.581071] ACPI: Sleep Button (CM) [SLPB]
[    1.581126] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.583101] ACPI: Lid Switch [LID]
[    1.583501] processor ACPI_CPU:00: registered as cooling_device0
[    1.583513] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.583593] processor ACPI_CPU:01: registered as cooling_device1
[    1.591314] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080926]
[    1.591367] isapnp: Scanning for PnP cards...
[    1.975419] isapnp: No Plug & Play device found
[    1.988886] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.989925] brd: module loaded
[    1.990257] loop: module loaded
[    1.990328] Fixed MDIO Bus: probed
[    1.990335] PPP generic driver version 2.4.2
[    1.990395] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.990426] Driver 'sd' needs updating - please use bus_type methods
[    1.990436] Driver 'sr' needs updating - please use bus_type methods
[    1.990475] ahci 0000:00:11.0: version 3.0
[    1.990531] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.990725] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.990728] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.991611] scsi0 : ahci
[    1.991803] scsi1 : ahci
[    1.991906] scsi2 : ahci
[    1.992011] scsi3 : ahci
[    1.992116] scsi4 : ahci
[    1.992218] scsi5 : ahci
[    1.992308] ata1: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408100 irq 22
[    1.992311] ata2: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408180 irq 22
[    1.992315] ata3: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408200 irq 22
[    1.992319] ata4: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408280 irq 22
[    1.992322] ata5: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408300 irq 22
[    1.992326] ata6: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408380 irq 22
[    2.476316] ata1: softreset failed (device not ready)
[    2.476375] ata1: failed due to HW bug, retry pmp=0
[    2.640321] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.641832] ata1.00: ATA-8: ST9320320AS, HP07, max UDMA/100
[    2.641835] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.643675] ata1.00: configured for UDMA/100
[    3.140250] ata2: softreset failed (device not ready)
[    3.140300] ata2: failed due to HW bug, retry pmp=0
[    3.304258] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.318380] ata2.00: ATAPI: Optiarc DVD RW AD-7581S, 4H03, max UDMA/100
[    3.333546] ata2.00: configured for UDMA/100
[    3.668272] ata3: SATA link down (SStatus 0 SControl 300)
[    4.004580] ata4: SATA link down (SStatus 0 SControl 300)
[    4.340270] ata5: SATA link down (SStatus 0 SControl 300)
[    4.676270] ata6: SATA link down (SStatus 0 SControl 300)
[    4.692358] scsi 0:0:0:0: Direct-Access     ATA      ST9320320AS      HP07 PQ: 0 ANSI: 5
[    4.692459] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.692478] sd 0:0:0:0: [sda] Write Protect is off
[    4.692481] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.692550] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.692625] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.692639] sd 0:0:0:0: [sda] Write Protect is off
[    4.692641] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.692663] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.692667]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    4.809619] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.809669] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.812046] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7581S  4H03 PQ: 0 ANSI: 5
[    4.824105] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.824109] Uniform CD-ROM driver Revision: 3.20
[    4.824206] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.824242] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.824586] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.824623] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    4.824726] scsi6 : pata_atiixp
[    4.824815] scsi7 : pata_atiixp
[    4.825982] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6000 irq 14
[    4.825985] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6008 irq 15
[    5.136915] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.136970] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.136993] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    5.136998] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    5.137055] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    5.137114] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    5.137136] ehci_hcd 0000:00:12.2: debug port 1
[    5.137157] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2408500
[    5.148072] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    5.148150] usb usb1: configuration #1 chosen from 1 choice
[    5.148179] hub 1-0:1.0: USB hub found
[    5.148187] hub 1-0:1.0: 6 ports detected
[    5.148367] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.148380] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    5.148384] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    5.148434] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    5.148488] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    5.148521] ehci_hcd 0000:00:13.2: debug port 1
[    5.148537] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2408400
[    5.160070] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    5.160119] usb usb2: configuration #1 chosen from 1 choice
[    5.160143] hub 2-0:1.0: USB hub found
[    5.160150] hub 2-0:1.0: 6 ports detected
[    5.160277] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.160327] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.160340] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    5.160343] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    5.160384] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    5.160445] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2407000
[    5.220278] usb usb3: configuration #1 chosen from 1 choice
[    5.220304] hub 3-0:1.0: USB hub found
[    5.220314] hub 3-0:1.0: 3 ports detected
[    5.220431] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.220443] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    5.220447] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    5.220560] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    5.220576] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2406000
[    5.280090] usb usb4: configuration #1 chosen from 1 choice
[    5.280113] hub 4-0:1.0: USB hub found
[    5.280156] hub 4-0:1.0: 3 ports detected
[    5.280274] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.280286] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    5.280290] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.280332] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    5.280395] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2405000
[    5.336079] usb usb5: configuration #1 chosen from 1 choice
[    5.336105] hub 5-0:1.0: USB hub found
[    5.336157] hub 5-0:1.0: 3 ports detected
[    5.336273] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.336286] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    5.336289] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.336331] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    5.336384] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2404000
[    5.392083] usb usb6: configuration #1 chosen from 1 choice
[    5.392106] hub 6-0:1.0: USB hub found
[    5.392115] hub 6-0:1.0: 3 ports detected
[    5.392238] uhci_hcd: USB Universal Host Controller Interface driver
[    5.392318] usbcore: registered new interface driver libusual
[    5.392350] usbcore: registered new interface driver usbserial
[    5.392360] USB Serial support registered for generic
[    5.516093] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    5.682916] usb 1-3: configuration #1 chosen from 1 choice
[    5.684862] usbcore: registered new interface driver usbserial_generic
[    5.684864] usbserial: USB Serial Driver core
[    5.684908] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.712107] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.712114] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.712598] mice: PS/2 mouse device common for all mice
[    5.732643] rtc_cmos 00:05: RTC can wake from S4
[    5.732679] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    5.732754] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    5.732814] device-mapper: uevent: version 1.0.3
[    5.732974] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    5.733250] device-mapper: multipath: version 1.0.5 loaded
[    5.733253] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.733382] EISA: Probing bus 0 at eisa.0
[    5.733392] Cannot allocate resource for EISA slot 1
[    5.733395] Cannot allocate resource for EISA slot 2
[    5.733397] Cannot allocate resource for EISA slot 3
[    5.733399] Cannot allocate resource for EISA slot 4
[    5.733401] Cannot allocate resource for EISA slot 5
[    5.733403] Cannot allocate resource for EISA slot 6
[    5.733414] EISA: Detected 0 cards.
[    5.733575] cpuidle: using governor ladder
[    5.733578] cpuidle: using governor menu
[    5.734048] TCP cubic registered
[    5.734145] NET: Registered protocol family 10
[    5.734541] lo: Disabled Privacy Extensions
[    5.734826] NET: Registered protocol family 17
[    5.734845] Bluetooth: L2CAP ver 2.11
[    5.734847] Bluetooth: L2CAP socket layer initialized
[    5.734850] Bluetooth: SCO (Voice Link) ver 0.6
[    5.734852] Bluetooth: SCO socket layer initialized
[    5.734955] Bluetooth: RFCOMM socket layer initialized
[    5.734961] Bluetooth: RFCOMM TTY layer initialized
[    5.734963] Bluetooth: RFCOMM ver 1.10
[    5.735026] powernow-k8: Found 1 AMD Turion(tm) X2 Dual-Core Mobile RM-75 processors (2 cpu cores) (version 2.20.00)
[    5.735096] powernow-k8:    0 : pstate 0 (2200 MHz)
[    5.735100] powernow-k8:    1 : pstate 1 (1100 MHz)
[    5.735104] powernow-k8:    2 : pstate 2 (550 MHz)
[    5.736307] Using IPI No-Shortcut mode
[    5.736377] registered taskstats version 1
[    5.736580]   Magic number: 13:302:632
[    5.736723] rtc_cmos 00:05: setting system clock to 2009-06-06 12:36:43 UTC (1244291803)
[    5.736726] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.736728] EDD information not available.
[    5.737087] Freeing unused kernel memory: 532k freed
[    5.737274] Write protecting the kernel text: 4128k
[    5.737323] Write protecting the kernel read-only data: 1532k
[    5.751192] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    5.932157] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.932179] r8169 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.932199] r8169 0000:09:00.0: setting latency timer to 64
[    5.932287] r8169 0000:09:00.0: irq 2297 for MSI/MSI-X
[    5.932915] eth0: RTL8168d/8111d at 0xf7cae000, 00:23:8b:ac:63:ca, XID 281000c0 IRQ 2297
[    5.976110] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    6.154397] usb 3-1: configuration #1 chosen from 1 choice
[    6.234706] usbcore: registered new interface driver hiddev
[    6.239645] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input6
[    6.244625] generic-usb 0003:046D:C03F.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-1/input0
[    6.244653] usbcore: registered new interface driver usbhid
[    6.244658] usbhid: v2.6:USB HID core driver
[    6.730807] PM: Starting manual resume from disk
[    6.730810] PM: Resume from partition 8:6
[    6.730813] PM: Checking hibernation image.
[    6.731161] PM: Resume from disk failed.
[    6.786696] kjournald starting.  Commit interval 5 seconds
[    6.786707] EXT3-fs: mounted filesystem with ordered data mode.
[   14.481697] udev: starting version 141
[   14.999968] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SMBI [0xb00-0xb0f]
[   14.999971] ACPI: Device needs an ACPI driver
[   14.999980] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   15.098119] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   15.107087] lis3lv02d: laptop model unknown, using default axes configuration
[   15.123032] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   15.129197] lis3lv02d driver loaded.
[   15.272375] Linux video capture interface: v2.00
[   15.326652] Linux agpgart interface v0.103
[   15.657696] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   15.711873] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.741441] [fglrx] Maximum main memory to use for locked dma buffers: 2876 MBytes.
[   15.741638] [fglrx]   vendor: 1002 device: 9553 count: 1
[   15.741907] [fglrx] ioport: bar 1, base 0x5000, size: 0x100
[   15.741926] pci 0000:01:00.0: power state changed by ACPI to D0
[   15.741938] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.741945] pci 0000:01:00.0: setting latency timer to 64
[   15.742372] [fglrx] Driver built-in PAT support is enabled successfully
[   15.742406] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
[   16.007126] acpi device:0c: registered as cooling_device2
[   16.007535] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:09/input/input9
[   16.026209] ACPI: Video Device [DVGA] (multi-head: yes  rom: no  post: no)
[   16.054641] uvcvideo: Found UVC 1.00 device HP Webcam (064e:c107)
[   16.057900] input: HP Webcam as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input10
[   16.060696] usbcore: registered new interface driver uvcvideo
[   16.060719] USB Video Class driver (v0.1.0)
[   16.114590] leds-hp-disk driver loaded.
[   16.471427] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.471673] HDA Intel 0000:00:14.2: setting latency timer to 64
[   16.503186] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input11
[   16.554234] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   16.554317] HDA Intel 0000:01:00.1: setting latency timer to 64
[   16.772556] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000
[   16.860845] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[   16.895667] lp: driver loaded but no devices found
[   16.979349] Adding 4305380k swap on /dev/sda6.  Priority:-1 extents:1 across:4305380k
[   17.539282] EXT3 FS on sda5, internal journal
[   18.791317] type=1505 audit(1244284616.551:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2153
[   18.843993] type=1505 audit(1244284616.603:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2157
[   18.844169] type=1505 audit(1244284616.607:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2157
[   18.844223] type=1505 audit(1244284616.607:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2157
[   18.844275] type=1505 audit(1244284616.607:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2157
[   18.996337] type=1505 audit(1244284616.759:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2162
[   18.996533] type=1505 audit(1244284616.759:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2162
[   19.038453] type=1505 audit(1244284616.799:9): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=2166
[   19.067938] type=1505 audit(1244284616.827:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2170
[   22.426165] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.426168] Bluetooth: BNEP filters: protocol multicast
[   22.520128] Bridge firewalling registered
[   25.316574] ppdev: user-space parallel port driver
[   26.458296] fglrx_pci 0000:01:00.0: irq 2296 for MSI/MSI-X
[   26.472012] [fglrx] Firegl kernel thread PID: 3123
[   26.524554] [fglrx] Gart USWC size:1447 M.
[   26.524558] [fglrx] Gart cacheable size:60 M.
[   26.524564] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   26.524567] [fglrx] Reserved FB block: Unshared offset:fd03000, size:2fd000 
[   26.524570] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   29.237442] r8169: eth0: link up
[   29.237449] r8169: eth0: link up
[   39.664066] eth0: no IPv6 routers present
[   51.844553] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x021f000a
[   52.848518] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x021f000a
[   54.664307] CPU0 attaching NULL sched-domain.
[   54.664314] CPU1 attaching NULL sched-domain.
[   54.680109] CPU0 attaching sched-domain:
[   54.680113]  domain 0: span 0-1 level CPU
[   54.680116]   groups: 0 1
[   54.680122] CPU1 attaching sched-domain:
[   54.680124]  domain 0: span 0-1 level CPU
[   54.680126]   groups: 1 0

```

Now, here is something that I don't if it's related to the wireless problem, but every time I boot up Ubuntu I see the two different "softreset failed" messages. These (although the explanatory lines after each aren't visible at boot-up):
```

[    2.476316] ata1: softreset failed (device not ready)
[    2.476375] ata1: failed due to HW bug, retry pmp=0
[    2.640321] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.641832] ata1.00: ATA-8: ST9320320AS, HP07, max UDMA/100
[    2.641835] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.643675] ata1.00: configured for UDMA/100
[    3.140250] ata2: softreset failed (device not ready)
[    3.140300] ata2: failed due to HW bug, retry pmp=0
[    3.304258] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.318380] ata2.00: ATAPI: Optiarc DVD RW AD-7581S, 4H03, max UDMA/100
[    3.333546] ata2.00: configured for UDMA/100
```

Could this be something?

Network configuration:

```
*-network UNCLAIMED     
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:23:8b:ac:63:ca
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1a:7a:24:02:c2:0c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Scan for networks (can't try "iwlist scan wlan0" because I have no wlan0 recognised):

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

Restarting the network:

```
erik@erik-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
```

So, that's all info I have at the moment. Sorry for the extensive post!

---

### Post by SuperSonic4 on 2009-06-06
> **Mezzoforte said:**
> I have installed Ubuntu 9.04 but have problems get it connected to the wireless network - or rather, there seems to be a problem actually activating the wireless adapter. The laptop has a touch control for activating the wireless, but nothing happens when touching (this works fine in Windows though).

I am grateful for any help! Information about the adapter and my setup:

Computer: HP Pavilion DV6 (laptop)
OS: Ubuntu 9.04
Kernel/architecture: 2.6.28-11-generic i686

**snip**

So, that's all info I have at the moment. Sorry for the extensive post!

Your problem is that your kernel is not new enough. The ath9k driver which handles the AR9285 chipset is standard in kernel 2.6.29 and greater.

[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k) supported chipsets include AR9285 (>= 2.6.29) 

    
You can upgrade the wireless parts of the kernel only which can be found here: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

although I'd be quite careful as you're playing with the kernel now. The compat-wireless tools seem to be the way to go and the above link contains a method for installing them.

Edit 1: For ubuntu jaunty you can run the following command: ```
sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by Mezzoforte on 2009-06-06
Thank you! It worked like a charm. I ran the code "sudo apt-get install linux-backports-modules-jaunty" then restarted the computer and presto. Now I am quite a bit closer to using Ubuntu as my everyday OS.

---

### Post by Knightofathousandlaughs on 2009-08-07
I had the same problem. i ran the command 
sudo apt-get install linux-backports-modules-jauntyand gave a loud scream of accomplishment.  3 weeks and finally i get my wireless working. now it is time to tackle the sound. Ubuntu has rejuvenated my fighting spirit

---

### Post by kozzeluc on 2009-08-08
Worked for me too - many thanks !!

---

### Post by AggravatedGestalt on 2009-08-19
I hope I aint cluttering the forum by expressing my joy at your fix. Thanks a bunch! It actually fixed multiple problems with other wifi cards too, including my RTL8187 USB, which was suffering a terribly weak signal until I installed the backports you have suggested. That was a very nice surprise.

---

### Post by robintu on 2009-08-20
I have the same problem it seems from your description, but I do not have an internet connection for my linux machine. I checked the site but I can't figure out how to get it without the apt-get install command. Any explanation for it?
 
Thanks. :)

---

### Post by tck on 2009-09-08
> **robintu said:**
> I have the same problem it seems from your description, but I do not have an internet connection for my linux machine. I checked the site but I can't figure out how to get it without the apt-get install command. Any explanation for it?
 
Thanks. :)

well you seem to have internet access, all you do is download this file

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.15.20_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.15.20_i386.deb)

and put it on a usb key and then copy it to your linux machine.

Open a terminal and change to the directory of the file and type..

```

sudo dpkg -i linux-backports-modules-jaunty_2.6.28.15.20_i386.deb

```

and after it's finished installing you simply reboot!

---

### Post by gtoro on 2009-09-19
I have the same problem as the fellow above. so i copied the file (after downloading it through windows) to ubuntu and put in the suggested comand line.  This is what i get.

pat@pat-laptop:~$ cd Desktop
pat@pat-laptop:~/Desktop$ sudo dpkg -i linux-backports-modules-jaunty_2.6.28.15.20_i386.deb
Selecting previously deselected package linux-backports-modules-jaunty.
(Reading database ... 101998 files and directories currently installed.)
Unpacking linux-backports-modules-jaunty (from linux-backports-modules-jaunty_2.6.28.15.20_i386.deb) ...
dpkg: dependency problems prevent configuration of linux-backports-modules-jaunty:
 linux-backports-modules-jaunty depends on linux-backports-modules-jaunty-generic (= 2.6.28.15.20); however:
  Package linux-backports-modules-jaunty-generic is not installed.
dpkg: error processing linux-backports-modules-jaunty (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-backports-modules-jaunty
pat@pat-laptop:~/Desktop$


Any  help would be appreciated.  Asus X5 DIN with ATheros wifi as described above.

Thanks,

Giorgio

---

### Post by AarDvarCk on 2009-09-27
Hi gtoro,

The problem are easy to fix. It's just a dependency problems.
You will need some other files to fix this problems.

linux-backports-modules-jaunty are dependent of linux-backports-modules-jaunty-generic,
linux-backports-modules-jaunty-generic are dependent of linux-backports-modules and linux-backports-modules depend of linux-image-generic ! 

So now just download and install this files in this order :

1 - (Linux-image-generic) [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb)
2 - (linux-backports-module) [http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_i386.deb)
3 - (linux-backports-modules-jauntry-generic) [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty-generic_2.6.28.15.20_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty-generic_2.6.28.15.20_i386.deb)
4 - (linux-backports-modules-jauntry) [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.15.20_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.15.20_i386.deb)

Simply use the same command : 

```
sudo dpkg -i "package"
```Reboot and it's done !

I hope that can be helpfull !

AarDvarCk

---

### Post by gtoro on 2009-09-29
Thanks AarDvarCk, works great

giorgio

---

### Post by elijabaley on 2009-09-30
> **gtoro said:**
> Thanks AarDvarCk, works great

giorgio

Hi giorgio.

Now that you have installed these drivers, do the wireless card works with Wep too?
And wpa?
And ad-hoc mode?

I ask because i'm probably going to buy a notebook with this wifi card and criptations are not always supported in drivers that have been released recently

Thanks

Riccardo

---

### Post by AarDvarCk on 2009-09-30
Yes, for me all works very well, so I hope that's the same thing for the other people ! :)

AarDvarCk

---

### Post by elijabaley on 2009-10-02
> **AarDvarCk said:**
> Yes, for me all works very well, so I hope that's the same thing for the other people ! :)

AarDvarCk

Ok, i have bought the notebook.
I will refer the working state.

Byez

(P.S.: are you Italian, Giorgio?)

---

### Post by matthew.ball on 2009-10-02
Ummm, I don't know how different this card is to the Atheros AR928X chipset, but I am using the latter, and until last night the wireless worked well enough (possibly not to maximum strength), this morning I turn it on and it now doesn't work at all (doesn't show me any wireless network in NetworkManager).

From about 12:00 this afternoon I have been trying to work out what's going on, everything from going to the Atheros web-site, downloading latest drivers etc. Nothing has worked so far. I initially had ndiswrapper installed, but didn't realise it was actually doing anything (I did have a driver loaded, but it had always had a red cross on top of it, I didn't think it worked, but apparantly so? - I removed this last night, so...), tried wicd, nothing, tried madwifi, nothing, now I'm completely lost.

This is really frustrating me (after a day's investigation I'd be surprised to find someone who wasn't getting annoyed), I have got nowhere. A few sites all mention I should see some driver in Hardware Drivers, however all I have listed there is display drivers.

Argh, any help is appreciated.

---

### Post by donmatas on 2009-10-04
> **SuperSonic4 said:**
> Your problem is that your kernel is not new enough. The ath9k driver which handles the AR9285 chipset is standard in kernel 2.6.29 and greater.

[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k) supported chipsets include AR9285 (>= 2.6.29) 

    
You can upgrade the wireless parts of the kernel only which can be found here: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

although I'd be quite careful as you're playing with the kernel now. The compat-wireless tools seem to be the way to go and the above link contains a method for installing them.

Edit 1: For ubuntu jaunty you can run the following command: ```
sudo apt-get install linux-backports-modules-jaunty
```

dude:

it doesn't works on my Toshiba NB 200. what I can do?

---

### Post by elijabaley on 2009-10-07
> **donmatas said:**
> dude:

it doesn't works on my Toshiba NB 200. what I can do?

You could update the kernel.
(Maybe it works)

Or You could wait a couple of weeks for the lounch of ubuntu 9.10 that will have the new kernel included.

I've heard that someone have used this wifi card successfully with madwifi drivers

---

### Post by donmatas on 2009-10-08
i will wait for de Koala. 
I think that my problem was that I didn't turn on the device with windows (before installing ubuntu), some one have written that in a web that I cant remember

saludos
DM

---

### Post by elijabaley on 2009-10-08
> **donmatas said:**
> i will wait for de Koala. 
I think that my problem was that I didn't turn on the device with windows (before installing ubuntu), some one have written that in a web that I cant remember

saludos
DM

very strange.

I've always thought that net devices can be activated under linux with the commands "ifup"/"ifdown".

But, haven't you tried with madwifi drivers?


P.S.: excuse me for my inperfect english ;)

---

### Post by donmatas on 2009-10-08
my english is worst!!!

i haven's try with madwifi becouse I had read that it doesn't work

saludos
DM

---

### Post by Wrathe on 2009-10-08
>  
I also get an error.
I downloaded *_linux-backports-modules-jaunty_2.6.28.15.20_i286.deb_*
 
Typed the following in Terminal:
[quote] 
cd Desktop
sudo dpkg -i linux-backports-modules-jaunty_2.6.28.15.20_i286.deb

I get the following error:
>  
dpkg: error processing linux-backports-modules-jaunty_2.6.28.15.20_i286.deb (--install):
package architecture (i386) does not match system (amd64)
Errors were encounted when processing:
linux-backports-modules-jaunty_2.6.28.15.20_i286.deb

 
Do I need a amd64 version of the file? Is there one?
 
Wow. Had to type that linux-backport.......... so much that I actually remember it now. ^.-
 
Hope someone can help. :D
[/quote]
 
EDIT: Got it working! 
 
[http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)

---

### Post by Hiddenbanana on 2009-10-21
i don't get it guys why don't you just connect your netbook to ya router and 

type
```

# Sudo apt-get update
# Sudo ap-get install linux-backports-modules-jaunty

```as i have seen every one has issues with dependencies

and to a side note anyone Using a Virgin media freedom netbook and having issues with sound goto 

**[http://ubuntuforums.org/showthread.php?t=1243256](http://ubuntuforums.org/showthread.php?t=1243256)**

---
:popcorn:

---

### Post by blackmajik2021 on 2009-11-12
> **tck said:**
> well you seem to have internet access, all you do is download this file

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.15.20_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.15.20_i386.deb)

and put it on a usb key and then copy it to your linux machine.

Open a terminal and change to the directory of the file and type..

```

sudo dpkg -i linux-backports-modules-jaunty_2.6.28.15.20_i386.deb

```

and after it's finished installing you simply reboot!

problem is that link is broken...its a desktop computer and I cant move it to be near a wired connection...where can i get the file?

---

### Post by blackmajik2021 on 2009-11-12
I found the files but I get "error dependency is not satisfiable" every time i try to install the package.

---

### Post by jeannacav on 2009-11-25
> **Hiddenbanana said:**
> i don't get it guys why don't you just connect your netbook to ya router and 

type
```

# Sudo apt-get update
# Sudo ap-get install linux-backports-modules-jaunty

```as i have seen every one has issues with dependencies

and to a side note anyone Using a Virgin media freedom netbook and having issues with sound goto 

**[http://ubuntuforums.org/showthread.php?t=1243256](http://ubuntuforums.org/showthread.php?t=1243256)**

---
:popcorn:

we will see.
I just went through it and since I now know to ignore the fact that the password appears to be non functional and I know to type it anyway... thanks to  somebody...
I watched a bunch of stuff go on, and I guess now I will reboot, cuz it still looks the same.

jeanna

===============================yeay!===================
OMG it works!!!!!!

kissey poo thank you sooo much banana.

j

---

### Post by bean1945 on 2009-11-27
Super Sonic 4, 

I want to personally thank you for your excellent solution to the wireless adaptor problem.
I had added a D-Link DWA 552  wireless adaptor to my Dell 3000  Desktop and although recognized by 9.04, the signal and speed were both poor. I was able to use ndiswrapper to obtain better speeds, but ndiswrapper would not recognize that the adaptor was n capable. Using your suggestion to try back ports, the adapter is now showing signal of 
70% (~ 20 % before) and faster download speeds compared to upload speeds (just the reverse earlier). Thank you again!

bean1945

---

### Post by drpjkurian on 2009-11-29
> **donmatas said:**
> my english is worst!!!

i haven's try with madwifi becouse I had read that it doesn't work

saludos
DM

Hi Guys
Please note that Madwifi is one of the robust driver for Atheros wireless cards. I have been using it since the time of Hardy heron. If any guys wish to have an installation of Madwifi, Please visit my thread and solve it with charm

The thread is [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Best of luck

---

### Post by cstgwr on 2009-12-02
Thank you Jean,
 
I plugged my cat-5 cable in, downloaded updates, rebuilt/rebooted and ALL is good. Your advice was a real time saver for me.
 
Regards,
Winston

---

### Post by HotForLinux on 2010-02-27
I'm using a Hardy.
I would like to know what are the

linux-backports-modules-hardy-generic,
linux-backports-modules-*

and similar packages for, when should one install them and how to undo changes.
Thank you

---

### Post by allankelly on 2010-09-22
Hi, I spent ages trying the solutions described here and elsewhere for my AR9285 on a Toshiba C650-194. I finally solved it with a kernel argument:
```
acpi=ht
```

That is the same as acpi=off but "just enough ACPI to enable HyperThreading".

It seems the Toshiba BIOS is buggy.

To make it permanent (as root, use sudo) -

1. In /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=ht quiet splash"
```

2. Install:
```
update-grub
```

Cheers, al.

---

### Post by saimonek on 2010-11-04
Hi guys, please help me! I've got ubuntu 10.10 (that's why I can't use your how-to), HP machine and I have the same problem - I can't run my wireless AR9285 card... I don't understand the system very much, so I don't know how to solve it.
here is lspci -v output:
"
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Hewlett-Packard Company Device 3040
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f1000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k
"

---

### Post by b1tchacked on 2011-07-10
I am on ubuntu 11.04 installed the lasted package from that linuxwireless thingy, and i still cant go wireles.....:(:(

---

