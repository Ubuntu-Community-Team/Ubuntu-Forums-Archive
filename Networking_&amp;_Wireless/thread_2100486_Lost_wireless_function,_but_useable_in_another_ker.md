---
title: "Lost wireless function, but useable in another kernel"
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by circa on 2013-01-01
I #$%# up (royally, I might add) and compiled a Compat Wireless driver. The worse part was that I didn't have the need for anything Compat, however, I went ahead on some misinformation that related to a prior issue. BTW, the wireless card works on any other kernel, such as the 3.2.0-34 or 3.2.0-29. I have uninstalled the the Compat compilation, but the damage is done and I'm just trying to work this out as a learning experience.

I have already tried uninstalling the 3.2.0-35 kernel which, included the meta files, and rebuilding it through synaptic. This changed nothing. 

```
#rfkill list all
produces nothing but another prompt.
``````
#lspci -v
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3084
    Flags: bus master, fast devsel, latency 0
    Memory at <unassigned> (32-bit, prefetchable)
    Capabilities: [40] Vendor Specific Information: Len=05 <?>
    Kernel driver in use: agpgart-intel


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: e0200000-e02fffff
    Prefetchable memory behind bridge: 54000000-57ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 3084
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Memory at 50000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3084
    Flags: medium devsel, IRQ 5
    I/O ports at 1880 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 3084
    Flags: bus master, medium devsel, latency 64, IRQ 10
    I/O ports at 3000 [size=256]
    Memory at e0202000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3084
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at 58000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 54000000-57fff000 (prefetchable)
    Memory window 1: 5c000000-5ffff000
    I/O window 0: 00003800-000038ff
    I/O window 1: 00003400-000034ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN
    Flags: bus master, fast devsel, latency 64, IRQ 11
    Memory at e0200000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

``````
# modprobe b43
WARNING: Error inserting cfg80211 (/lib/modules/3.2.0-35-generic/kernel/net/wireless/cfg80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/3.2.0-35-generic/kernel/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting b43 (/lib/modules/3.2.0-35-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
``````
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
``````
#ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:54:c7:22  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe54:c722/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19225 (19.2 KB)  TX bytes:11260 (11.2 KB)
          Interrupt:10 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2076 (2.0 KB)  TX bytes:2076 (2.0 KB)
```I do have b43-fw cutter and the correct b43 driver. Here the card is visible...
```
#lshw -c network
 *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:e0200000-e0201fff
```The wireless card has lost it's logical name in the 3.2.0.35 kernel version, but it's name is allocated in file /etc/udev/rules.d/70-persistant-net.rule
```
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:06.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:90:4b:96:7b:f4", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

``````
#lsmod
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39826  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                96718  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
serio_raw              13027  0 
parport_pc             32114  0 
ppdev                  12849  0 
shpchp                 32325  0 
binfmt_misc            17292  1 
wmi                    18744  0 
video                  19068  0 #Unreleated, but I have i915 listed here on the 3.2.0-34 kernel
ssb                    50691  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 22633  0
```Comparing #lsmod to my 3.2.0-34 kernel, I'm missing the following entries... 
```
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43

```And lastly...There are a lot of bluetooth errors in this. The Compat compilation had a lot of bluetooth files, but unsure if this is related.
```
# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-35-generic (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #55-Ubuntu SMP Wed Dec 5 17:45:18 UTC 2012 (Ubuntu 3.2.0-35.55-generic 3.2.34)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004dee0000 (usable)
[    0.000000]  BIOS-e820: 000000004dee0000 - 000000004deec000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004deec000 - 000000004df00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004df00000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Hewlett-Packard  hp pavilion ze4900 (PM039UA#ABA)  /3084, BIOS F.10     08/18/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x4dee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FF0000000 write-back
[    0.000000]   2 base 04DF00000 mask FFFF00000 uncachable
[    0.000000]   3 base 04E000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1GB, range: 256MB, type WB
[    0.000000] reg 2, base: 1247MB, range: 1MB, type UC
[    0.000000] reg 3, base: 1248MB, range: 32MB, type UC
[    0.000000] total RAM covered: 1247M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1GB, range: 256MB, type WB
[    0.000000] reg 2, base: 1247MB, range: 1MB, type UC
[    0.000000] reg 3, base: 1248MB, range: 32MB, type UC
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 364f0000 - 37270000
[    0.000000] ACPI: RSDP 000f6560 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 4dee674d 00030 (v01 HP     3084     06040000  LTP 00000000)
[    0.000000] ACPI: FACP 4deebed2 00074 (v01 HP     3084     06040000 PTL  00000050)
[    0.000000] ACPI: DSDT 4dee6c96 0523C (v01 HP     3084     06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 4defcfc0 00040
[    0.000000] ACPI: BOOT 4deebfd8 00028 (v01 HP     3084     06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 4dee6b84 0010A (v01 HP     3084     00000001 INTL 20030224)
[    0.000000] 358MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0004dee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004dee0
[    0.000000] On node 0 totalpages: 319087
[    0.000000] free_area_init_node: node 0, pgdat c1827580, node_mem_map f5b30200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 718 pages used for memmap
[    0.000000]   HighMem zone: 91156 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 50000000:af800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77e9000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 316593
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic root=UUID=9f243f19-ff0c-49b0-9676-f35faf33a265 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5106944 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0004dee0)
[    0.000000] Memory: 1236632k/1276800k available (5624k kernel code, 39716k reserved, 2774k data, 716k init, 367496k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1834000 - 0xc18e7000   ( 716 kB)
[    0.000000]       .data : 0xc157e384 - 0xc1833c80   (2774 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157e384   (5624 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5008000 soft=f500a000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1296.620 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 2593.24 BogoMIPS (lpj=5186480)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004058] Security Framework initialized
[    0.004105] AppArmor: AppArmor initialized
[    0.004109] Yama: becoming mindful.
[    0.004225] Mount-cache hash table entries: 512
[    0.004483] Initializing cgroup subsys cpuacct
[    0.004494] Initializing cgroup subsys memory
[    0.008023] Initializing cgroup subsys devices
[    0.008028] Initializing cgroup subsys freezer
[    0.008032] Initializing cgroup subsys blkio
[    0.008046] Initializing cgroup subsys perf_event
[    0.008101] mce: CPU supports 5 MCE banks
[    0.008456] SMP alternatives: switching to UP code
[    0.019381] Freeing SMP alternatives: 24k freed
[    0.019405] ACPI: Core revision 20110623
[    0.023677] ACPI: setting ELCR to 0200 (from 0c20)
[    0.024027] ftrace: allocating 25920 entries in 51 pages
[    0.028149] weird, boot CPU (#0) not listed by the BIOS.
[    0.028155] SMP motherboard not detected.
[    0.028159] Local APIC not detected. Using dummy APIC emulation.
[    0.028162] SMP disabled
[    0.028166] Performance Events: 
[    0.028171] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.028174] no hardware sampling interrupt available.
[    0.028179] p6 PMU driver.
[    0.028186] ... version:                0
[    0.028189] ... bit width:              32
[    0.028192] ... generic registers:      2
[    0.028195] ... value mask:             00000000ffffffff
[    0.028198] ... max period:             000000007fffffff
[    0.028201] ... fixed-purpose events:   0
[    0.028204] ... event mask:             0000000000000003
[    0.028515] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[    0.028588] Brought up 1 CPUs
[    0.028592] Total of 1 processors activated (2593.24 BogoMIPS).
[    0.028967] devtmpfs: initialized
[    0.029217] EVM: security.selinux
[    0.029221] EVM: security.SMACK64
[    0.029224] EVM: security.capability
[    0.029287] PM: Registering ACPI NVS region at 4deec000 (81920 bytes)
[    0.033678] print_constraints: dummy: 
[    0.033715] RTC time: 22:40:35, date: 01/01/13
[    0.033795] NET: Registered protocol family 16
[    0.034026] EISA bus registered
[    0.034092] ACPI: bus type pci registered
[    0.035486] PCI: PCI BIOS revision 2.10 entry at 0xfd9a2, last bus=2
[    0.035489] PCI: Using configuration type 1 for base access
[    0.037879] bio: create slab <bio-0> at 0
[    0.038048] ACPI: Added _OSI(Module Device)
[    0.038053] ACPI: Added _OSI(Processor Device)
[    0.038057] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.038061] ACPI: Added _OSI(Processor Aggregator Device)
[    0.039503] ACPI: EC: Look up EC in DSDT
[    0.044185] ACPI: Interpreter enabled
[    0.044206] ACPI: (supports S0 S3 S4 S5)
[    0.044238] ACPI: Using PIC for interrupt routing
[    0.048470] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.053535] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.053752] ACPI: No dock devices found.
[    0.053756] HEST: Table not found.
[    0.053766] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.056496] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.057632] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.057638] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.057643] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.057649] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.057654] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.057659] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.057665] pci_root PNP0A03:00: host bridge window [mem 0x50000000-0xfebfffff] (ignored)
[    0.057684] pci 0000:00:00.0: [8086:3580] type 0 class 0x000600
[    0.057740] pci 0000:00:00.1: [8086:3584] type 0 class 0x000880
[    0.057791] pci 0000:00:00.3: [8086:3585] type 0 class 0x000880
[    0.057846] pci 0000:00:02.0: [8086:3582] type 0 class 0x000300
[    0.057860] pci 0000:00:02.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.057870] pci 0000:00:02.0: reg 14: [mem 0xe0000000-0xe007ffff]
[    0.057878] pci 0000:00:02.0: reg 18: [io  0x1800-0x1807]
[    0.057914] pci 0000:00:02.0: supports D1
[    0.057929] pci 0000:00:02.1: [8086:3582] type 0 class 0x000380
[    0.057941] pci 0000:00:02.1: reg 10: [mem 0xf0000000-0xf7ffffff pref]
[    0.057950] pci 0000:00:02.1: reg 14: [mem 0xe0080000-0xe00fffff]
[    0.057990] pci 0000:00:02.1: supports D1
[    0.058039] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
[    0.058085] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.058126] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
[    0.058171] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.058209] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
[    0.058254] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.058302] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
[    0.058326] pci 0000:00:1d.7: reg 10: [mem 0xe0100000-0xe01003ff]
[    0.058421] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.058428] pci 0000:00:1d.7: PME# disabled
[    0.058448] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.058494] pci 0000:00:1f.0: [8086:24cc] type 0 class 0x000601
[    0.058564] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH4 ACPI/GPIO/TCO
[    0.058572] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH4 GPIO
[    0.058592] pci 0000:00:1f.1: [8086:24ca] type 0 class 0x000101
[    0.058608] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.058620] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.058631] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.058643] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.058655] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.058667] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.058699] pci 0000:00:1f.3: [8086:24c3] type 0 class 0x000c05
[    0.058745] pci 0000:00:1f.3: reg 20: [io  0x1880-0x189f]
[    0.058786] pci 0000:00:1f.5: [8086:24c5] type 0 class 0x000401
[    0.058803] pci 0000:00:1f.5: reg 10: [io  0x1c00-0x1cff]
[    0.058814] pci 0000:00:1f.5: reg 14: [io  0x18c0-0x18ff]
[    0.058825] pci 0000:00:1f.5: reg 18: [mem 0xe0100c00-0xe0100dff]
[    0.058837] pci 0000:00:1f.5: reg 1c: [mem 0xe0100800-0xe01008ff]
[    0.058883] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.058889] pci 0000:00:1f.5: PME# disabled
[    0.058908] pci 0000:00:1f.6: [8086:24c6] type 0 class 0x000703
[    0.058926] pci 0000:00:1f.6: reg 10: [io  0x2400-0x24ff]
[    0.058937] pci 0000:00:1f.6: reg 14: [io  0x2000-0x207f]
[    0.058997] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.059003] pci 0000:00:1f.6: PME# disabled
[    0.059036] pci 0000:02:00.0: [10ec:8139] type 0 class 0x000200
[    0.059054] pci 0000:02:00.0: reg 10: [io  0x3000-0x30ff]
[    0.059066] pci 0000:02:00.0: reg 14: [mem 0xe0202000-0xe02020ff]
[    0.059128] pci 0000:02:00.0: supports D1 D2
[    0.059132] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.059138] pci 0000:02:00.0: PME# disabled
[    0.059162] pci 0000:02:05.0: [104c:ac50] type 2 class 0x000607
[    0.059181] pci 0000:02:05.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.059209] pci 0000:02:05.0: supports D1 D2
[    0.059213] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.059219] pci 0000:02:05.0: PME# disabled
[    0.059235] pci 0000:02:06.0: [14e4:4320] type 0 class 0x000280
[    0.059249] pci 0000:02:06.0: reg 10: [mem 0xe0200000-0xe0201fff]
[    0.059330] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.059337] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.059344] pci 0000:00:1e.0:   bridge window [mem 0xe0200000-0xe02fffff]
[    0.059351] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.059356] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.059362] pci 0000:02:05.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[    0.059400] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02-02]
[    0.059413] pci_bus 0000:00: on NUMA node 0
[    0.059419] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.059616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.059865]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.064335] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.064425] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.064510] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[    0.064594] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    0.064679] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[    0.064765] ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
[    0.064851] ACPI: PCI Interrupt Link [LNKG] (IRQs 11) *0, disabled.
[    0.064939] ACPI: PCI Interrupt Link [LNKH] (IRQs *11)
[    0.065148] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.065162] vgaarb: loaded
[    0.065165] vgaarb: bridge control possible 0000:00:02.0
[    0.065416] i2c-core: driver [aat2870] using legacy suspend method
[    0.065420] i2c-core: driver [aat2870] using legacy resume method
[    0.065603] SCSI subsystem initialized
[    0.065713] libata version 3.00 loaded.
[    0.065808] usbcore: registered new interface driver usbfs
[    0.065830] usbcore: registered new interface driver hub
[    0.065882] usbcore: registered new device driver usb
[    0.066051] PCI: Using ACPI for IRQ routing
[    0.066087] PCI: pci_cache_line_size set to 64 bytes
[    0.066171] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.066176] reserve RAM buffer: 000000004dee0000 - 000000004fffffff 
[    0.066382] NetLabel: Initializing
[    0.066386] NetLabel:  domain hash size = 128
[    0.066389] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.066409] NetLabel:  unlabeled traffic allowed by default
[    0.066524] Switching to clocksource pit
[    0.079628] AppArmor: AppArmor Filesystem Enabled
[    0.079701] pnp: PnP ACPI init
[    0.079739] ACPI: bus type pnp registered
[    0.081143] pnp 00:00: [bus 00-ff]
[    0.081149] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.081154] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.081158] pnp 00:00: [io  0x0d00-0xffff window]
[    0.081162] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.081167] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.081171] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.081176] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.081180] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.081185] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.081189] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.081193] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.081198] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.081202] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.081207] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.081211] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.081216] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.081220] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.081225] pnp 00:00: [mem 0x50000000-0xfebfffff window]
[    0.081229] pnp 00:00: [mem 0x00000000 window]
[    0.081345] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.081671] pnp 00:01: [io  0x0070-0x0077]
[    0.081679] pnp 00:01: [irq 8]
[    0.081749] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.081767] pnp 00:02: [io  0x00f0]
[    0.081771] pnp 00:02: [irq 13]
[    0.081830] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.081848] pnp 00:03: [io  0x0000-0x001f]
[    0.081852] pnp 00:03: [io  0x0081-0x008f]
[    0.081856] pnp 00:03: [io  0x0090-0x0091]
[    0.081860] pnp 00:03: [io  0x0093-0x009f]
[    0.081864] pnp 00:03: [io  0x00c0-0x00df]
[    0.081868] pnp 00:03: [dma 4]
[    0.081930] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.081955] pnp 00:04: [io  0x002e-0x002f]
[    0.081959] pnp 00:04: [io  0x004e-0x004f]
[    0.081963] pnp 00:04: [io  0x0068]
[    0.081966] pnp 00:04: [io  0x006c]
[    0.081970] pnp 00:04: [io  0x0061]
[    0.081973] pnp 00:04: [io  0x0063]
[    0.081977] pnp 00:04: [io  0x0065]
[    0.081980] pnp 00:04: [io  0x0067]
[    0.081983] pnp 00:04: [io  0x0080]
[    0.081987] pnp 00:04: [io  0x0092]
[    0.081991] pnp 00:04: [io  0x00b2-0x00b3]
[    0.081994] pnp 00:04: [io  0x0600-0x060f]
[    0.081998] pnp 00:04: [io  0x0800-0x080f]
[    0.082002] pnp 00:04: [io  0x1000-0x107f]
[    0.082006] pnp 00:04: [io  0x1180-0x11bf]
[    0.082010] pnp 00:04: [mem 0xfec10000-0xfec1ffff]
[    0.082131] system 00:04: [io  0x0600-0x060f] has been reserved
[    0.082136] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.082141] system 00:04: [io  0x1000-0x107f] has been reserved
[    0.082146] system 00:04: [io  0x1180-0x11bf] has been reserved
[    0.082152] system 00:04: [mem 0xfec10000-0xfec1ffff] has been reserved
[    0.082158] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.082424] pnp 00:05: [io  0x0060]
[    0.082429] pnp 00:05: [io  0x0064]
[    0.082433] pnp 00:05: [irq 1]
[    0.082517] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.082557] pnp 00:06: [irq 12]
[    0.082642] pnp 00:06: Plug and Play ACPI device, IDs SYN0117 SYN0100 SYN0002 PNP0f13 (active)
[    0.082716] pnp: PnP ACPI: found 7 devices
[    0.082720] ACPI: ACPI bus type pnp unregistered
[    0.082727] PnPBIOS: Disabled by ACPI PNP
[    0.120879] Switching to clocksource acpi_pm
[    0.120929] PCI: max bus depth: 2 pci_try_num: 3
[    0.120967] pci 0000:00:1f.1: BAR 5: assigned [mem 0x50000000-0x500003ff]
[    0.120977] pci 0000:00:1f.1: BAR 5: set to [mem 0x50000000-0x500003ff] (PCI address [0x50000000-0x500003ff])
[    0.120984] pci 0000:00:1e.0: BAR 15: assigned [mem 0x54000000-0x57ffffff pref]
[    0.120993] pci 0000:02:05.0: BAR 0: assigned [mem 0x58000000-0x58000fff]
[    0.121001] pci 0000:02:05.0: BAR 0: set to [mem 0x58000000-0x58000fff] (PCI address [0x58000000-0x58000fff])
[    0.121008] pci 0000:02:05.0: BAR 16: assigned [mem 0x5c000000-0x5fffffff]
[    0.121013] pci 0000:02:05.0: BAR 15: assigned [mem 0x54000000-0x57ffffff pref]
[    0.121019] pci 0000:02:05.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.121024] pci 0000:02:05.0: BAR 13: assigned [io  0x3800-0x38ff]
[    0.121029] pci 0000:02:05.0: CardBus bridge to [bus 03-06]
[    0.121033] pci 0000:02:05.0:   bridge window [io  0x3800-0x38ff]
[    0.121040] pci 0000:02:05.0:   bridge window [io  0x3400-0x34ff]
[    0.121046] pci 0000:02:05.0:   bridge window [mem 0x54000000-0x57ffffff pref]
[    0.121053] pci 0000:02:05.0:   bridge window [mem 0x5c000000-0x5fffffff]
[    0.121060] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.121065] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.121073] pci 0000:00:1e.0:   bridge window [mem 0xe0200000-0xe02fffff]
[    0.121080] pci 0000:00:1e.0:   bridge window [mem 0x54000000-0x57ffffff pref]
[    0.121100] pci 0000:00:1e.0: setting latency timer to 64
[    0.121291] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    0.121297] PCI: setting IRQ 11 as level-triggered
[    0.121305] pci 0000:02:05.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    0.121314] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.121319] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.121324] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.121329] pci_bus 0000:02: resource 1 [mem 0xe0200000-0xe02fffff]
[    0.121334] pci_bus 0000:02: resource 2 [mem 0x54000000-0x57ffffff pref]
[    0.121339] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.121343] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.121348] pci_bus 0000:03: resource 0 [io  0x3800-0x38ff]
[    0.121353] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.121357] pci_bus 0000:03: resource 2 [mem 0x54000000-0x57ffffff pref]
[    0.121362] pci_bus 0000:03: resource 3 [mem 0x5c000000-0x5fffffff]
[    0.121451] NET: Registered protocol family 2
[    0.121620] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.122060] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.123961] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.125096] TCP: Hash tables configured (established 131072 bind 65536)
[    0.125103] TCP reno registered
[    0.125117] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.125155] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.125388] NET: Registered protocol family 1
[    0.125430] pci 0000:00:02.0: Boot video device
[    0.125658] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    0.125665] PCI: setting IRQ 10 as level-triggered
[    0.125673] pci 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    0.125694] pci 0000:00:1d.0: PCI INT A disabled
[    0.125819] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.125825] pci 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.125843] pci 0000:00:1d.1: PCI INT B disabled
[    0.125961] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.125967] pci 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.125985] pci 0000:00:1d.2: PCI INT C disabled
[    0.126106] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.126112] pci 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.126147] pci 0000:00:1d.7: PCI INT D disabled
[    0.126181] PCI: CLS 0 bytes, default 64
[    0.126315] Simple Boot Flag at 0x36 set to 0x1
[    0.126880] audit: initializing netlink socket (disabled)
[    0.126902] type=2000 audit(1357080035.120:1): initialized
[    0.166544] Trying to unpack rootfs image as initramfs...
[    0.212696] highmem bounce pool size: 64 pages
[    0.212708] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.220673] VFS: Disk quotas dquot_6.5.2
[    0.220821] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.228627] fuse init (API version 7.17)
[    0.228876] msgmni has been set to 1697
[    0.236439] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.240436] io scheduler noop registered
[    0.240444] io scheduler deadline registered
[    0.240487] io scheduler cfq registered (default)
[    0.240799] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.240855] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.241976] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.242923] ACPI: AC Adapter [ACAD] (on-line)
[    0.243385] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.243419] ACPI: Lid Switch [LID0]
[    0.243727] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.243736] ACPI: Power Button [PWRB]
[    0.243837] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.243843] ACPI: Power Button [PWRF]
[    0.244104] Marking TSC unstable due to TSC halts in idle
[    0.244117] ACPI: acpi_idle registered with cpuidle
[    0.251419] thermal LNXTHERM:00: registered as thermal_zone0
[    0.251426] ACPI: Thermal Zone [THRM] (42 C)
[    0.251495] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.251516] ACPI: Battery Slot [BAT0] (battery present)
[    0.251642] ERST: Table is not found!
[    0.251646] GHES: HEST is not enabled!
[    0.251844] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.257798] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    0.257806] PCI: setting IRQ 5 as level-triggered
[    0.257814] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.257845] serial 0000:00:1f.6: PCI INT B disabled
[    0.258457] Linux agpgart interface v0.103
[    0.258561] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[    0.258591] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.258900] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.259192] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.259925] isapnp: Scanning for PnP cards...
[    0.313878] brd: module loaded
[    0.317687] loop: module loaded
[    0.318021] ata_piix 0000:00:1f.1: version 2.13
[    0.318044] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.318059] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.318120] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.320064] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.324127] scsi0 : ata_piix
[    0.324376] scsi1 : ata_piix
[    0.325480] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.325486] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.326327] Fixed MDIO Bus: probed
[    0.326375] tun: Universal TUN/TAP device driver, 1.6
[    0.326379] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.326505] PPP generic driver version 2.4.2
[    0.326873] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.326915] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.326942] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.326948] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.327030] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.327072] ehci_hcd 0000:00:1d.7: debug port 1
[    0.330953] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.330971] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[    0.352466] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.352915] hub 1-0:1.0: USB hub found
[    0.352925] hub 1-0:1.0: 6 ports detected
[    0.353081] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.353125] uhci_hcd: USB Universal Host Controller Interface driver
[    0.353186] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    0.353203] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.353209] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.353323] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.353366] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001820
[    0.353623] hub 2-0:1.0: USB hub found
[    0.353631] hub 2-0:1.0: 2 ports detected
[    0.353740] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.353752] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.353757] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.353835] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.353862] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    0.354104] hub 3-0:1.0: USB hub found
[    0.354111] hub 3-0:1.0: 2 ports detected
[    0.354219] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.354231] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.354236] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.354309] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.354338] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    0.354588] hub 4-0:1.0: USB hub found
[    0.354595] hub 4-0:1.0: 2 ports detected
[    0.354795] usbcore: registered new interface driver libusual
[    0.354881] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PSM1] at 0x60,0x64 irq 1,12
[    0.361196] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.361216] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.361534] mousedev: PS/2 mouse device common for all mice
[    0.361868] rtc_cmos 00:01: RTC can wake from S4
[    0.362032] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.362055] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    0.362231] device-mapper: uevent: version 1.0.3
[    0.364668] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.364777] EISA: Probing bus 0 at eisa.0
[    0.364789] Cannot allocate resource for EISA slot 1
[    0.364795] Cannot allocate resource for EISA slot 2
[    0.364799] Cannot allocate resource for EISA slot 3
[    0.364825] EISA: Detected 0 cards.
[    0.364842] cpufreq-nforce2: No nForce2 chipset.
[    0.364910] cpuidle: using governor ladder
[    0.365007] cpuidle: using governor menu
[    0.365010] EFI Variables Facility v0.08 2004-May-17
[    0.365518] TCP cubic registered
[    0.365776] NET: Registered protocol family 10
[    0.366877] NET: Registered protocol family 17
[    0.366887] Registering the dns_resolver key type
[    0.366935] Using IPI No-Shortcut mode
[    0.368432] PM: Hibernation image not present or could not be loaded.
[    0.368457] registered taskstats version 1
[    0.596546] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.597434] ata2.00: ATAPI: SD-R2512, 1A04, max MWDMA2
[    0.605293] ata1.00: ATA-6: FUJITSU MHT2030AR, 959C, max UDMA/100
[    0.605301] ata1.00: 58605120 sectors, multi 16: LBA 
[    0.612595] ata2.00: configured for MWDMA2
[    0.660316] ata1.00: configured for UDMA/100
[    0.755814] isapnp: No Plug & Play device found
[    0.756123] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2030A 959C PQ: 0 ANSI: 5
[    0.756473] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.756766] sd 0:0:0:0: [sda] 58605120 512-byte logical blocks: (30.0 GB/27.9 GiB)
[    0.756852] sd 0:0:0:0: [sda] Write Protect is off
[    0.756857] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.756894] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.818873]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    0.819751] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.839166] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2512 1A04 PQ: 0 ANSI: 5
[    0.843997] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.844051] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.844341] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.844594] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.157188] Freeing initrd memory: 13824k freed
[    1.184759]   Magic number: 13:509:703
[    1.184930] rtc_cmos 00:01: setting system clock to 2013-01-01 22:40:36 UTC (1357080036)
[    1.184964] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.184967] EDD information not available.
[    1.300149] ACPI: Battery Slot [BAT0] (battery present)
[    1.300236] Freeing unused kernel memory: 716k freed
[    1.300822] Write protecting the kernel text: 5628k
[    1.300892] Write protecting the kernel read-only data: 2328k
[    1.337362] udevd[85]: starting version 175
[    1.658550] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.658600] 8139cp 0000:02:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.659505] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.659571] 8139too 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    1.678168] 8139too 0000:02:00.0: eth0: RealTek RTL8139 at 0x3000, 00:c0:9f:54:c7:22, IRQ 10
[    2.279694] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.279701] EXT4-fs (sda1): write access will be enabled during recovery
[    2.538540] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.538555] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13367
[    2.538674] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13081
[    2.538694] EXT4-fs (sda1): 2 orphan inodes deleted
[    2.538698] EXT4-fs (sda1): recovery complete
[    3.048734] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   26.709427] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.755228] udevd[293]: starting version 175
[   26.866108] lp: driver loaded but no devices found
[   26.975082] Adding 1274876k swap on /dev/sda5.  Priority:-1 extents:1 across:1274876k 
[   27.035780] b43-pci-bridge 0000:02:06.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   27.035821] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[   27.035829] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[   27.035836] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[   27.035844] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[   27.035851] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[   27.039317] ssb: Sonics Silicon Backplane found on PCI device 0000:02:06.0
[   27.073168] bcma: Unknown symbol compat_dependency_symbol (err 0)
[   27.077012] bcma: Unknown symbol compat_dependency_symbol (err 0)
[   27.193102] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   27.226816] acpi device:04: registered as cooling_device1
[   27.229079] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input4
[   27.229375] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   27.238521] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   27.538462] wmi: Mapper loaded
[   27.578665] drm: Unknown symbol ktime_get_monotonic_offset (err 0)
[   27.578923] drm: Unknown symbol compat_dependency_symbol (err 0)
[   27.579310] drm: Unknown symbol from_kuid_munged (err 0)
[   27.590675] drm: Unknown symbol ktime_get_monotonic_offset (err 0)
[   27.590938] drm: Unknown symbol compat_dependency_symbol (err 0)
[   27.591335] drm: Unknown symbol from_kuid_munged (err 0)
[   27.688264] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   27.688530] bluetooth: Unknown symbol __pskb_copy (err 0)
[   27.688550] bluetooth: Unknown symbol from_kuid (err 0)
[   27.704841] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   27.705092] bluetooth: Unknown symbol __pskb_copy (err 0)
[   27.705113] bluetooth: Unknown symbol from_kuid (err 0)
[   27.715148] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   27.715400] bluetooth: Unknown symbol __pskb_copy (err 0)
[   27.715420] bluetooth: Unknown symbol from_kuid (err 0)
[   27.754698] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   27.754950] bluetooth: Unknown symbol __pskb_copy (err 0)
[   27.754969] bluetooth: Unknown symbol from_kuid (err 0)
[   27.755797] intel_rng: FWH not detected
[   27.770286] ppdev: user-space parallel port driver
[   27.807548] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   27.807799] bluetooth: Unknown symbol __pskb_copy (err 0)
[   27.807819] bluetooth: Unknown symbol from_kuid (err 0)
[   27.824076] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.863622] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   27.863875] bluetooth: Unknown symbol __pskb_copy (err 0)
[   27.863895] bluetooth: Unknown symbol from_kuid (err 0)
[   27.885498] init: bluetooth main process (502) terminated with status 1
[   27.885561] init: bluetooth main process ended, respawning
[   27.963555] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   27.963810] bluetooth: Unknown symbol __pskb_copy (err 0)
[   27.963831] bluetooth: Unknown symbol from_kuid (err 0)
[   27.994611] type=1400 audit(1357080063.303:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=547 comm="apparmor_parser"
[   28.002165] type=1400 audit(1357080063.311:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=547 comm="apparmor_parser"
[   28.007122] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.007376] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.007398] bluetooth: Unknown symbol from_kuid (err 0)
[   28.015944] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.036581] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.036606] bluetooth: Unknown symbol from_kuid (err 0)
[   28.051827] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.056213] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.056240] bluetooth: Unknown symbol from_kuid (err 0)
[   28.071718] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.071972] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.071993] bluetooth: Unknown symbol from_kuid (err 0)
[   28.094922] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.095176] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.095197] bluetooth: Unknown symbol from_kuid (err 0)
[   28.096910] yenta_cardbus 0000:02:05.0: CardBus bridge found [103c:3084]
[   28.096932] yenta_cardbus 0000:02:05.0: Using CSCINT to route CSC interrupts to PCI
[   28.096937] yenta_cardbus 0000:02:05.0: Routing CardBus interrupts to PCI
[   28.096944] yenta_cardbus 0000:02:05.0: TI: mfunc 0x01111112, devctl 0x64
[   28.106772] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.107026] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.107047] bluetooth: Unknown symbol from_kuid (err 0)
[   28.116975] init: bluetooth main process (555) terminated with status 1
[   28.117031] init: bluetooth main process ended, respawning
[   28.168828] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.169095] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.169118] bluetooth: Unknown symbol from_kuid (err 0)
[   28.220845] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.221099] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.221121] bluetooth: Unknown symbol from_kuid (err 0)
[   28.234153] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.234420] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.234443] bluetooth: Unknown symbol from_kuid (err 0)
[   28.245776] type=1400 audit(1357080063.555:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=600 comm="apparmor_parser"
[   28.249238] type=1400 audit(1357080063.559:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=600 comm="apparmor_parser"
[   28.249760] type=1400 audit(1357080063.559:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=600 comm="apparmor_parser"
[   28.253550] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.253806] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.253828] bluetooth: Unknown symbol from_kuid (err 0)
[   28.282083] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.282339] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.282362] bluetooth: Unknown symbol from_kuid (err 0)
[   28.299847] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.308178] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.308206] bluetooth: Unknown symbol from_kuid (err 0)
[   28.332522] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.332776] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.332800] bluetooth: Unknown symbol from_kuid (err 0)
[   28.333986] yenta_cardbus 0000:02:05.0: ISA IRQ mask 0x00d8, PCI irq 11
[   28.333993] yenta_cardbus 0000:02:05.0: Socket status: 30000006
[   28.334001] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   28.334017] yenta_cardbus 0000:02:05.0: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   28.334024] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: excluding 0x3000-0x30ff
[   28.337204] init: bluetooth main process (590) terminated with status 1
[   28.337258] init: bluetooth main process ended, respawning
[   28.349295]  0x3400-0x34ff 0x3800-0x38ff
[   28.374226] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.374483] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.374507] bluetooth: Unknown symbol from_kuid (err 0)
[   28.407999] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.415903] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.415930] bluetooth: Unknown symbol from_kuid (err 0)
[   28.419661] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.419944] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.419968] bluetooth: Unknown symbol from_kuid (err 0)
[   28.430628] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.430884] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.430907] bluetooth: Unknown symbol from_kuid (err 0)
[   28.433470] 
[   28.433483] yenta_cardbus 0000:02:05.0: pcmcia: parent PCI bridge window: [mem 0xe0200000-0xe02fffff]
[   28.433491] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0200000-0xe02fffff: excluding 0xe0200000-0xe020ffff
[   28.433511] yenta_cardbus 0000:02:05.0: pcmcia: parent PCI bridge window: [mem 0x54000000-0x57ffffff pref]
[   28.433516] pcmcia_socket pcmcia_socket0: cs: memory probe 0x54000000-0x57ffffff: excluding 0x54000000-0x57ffffff
[   28.458268] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.458526] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.458551] bluetooth: Unknown symbol from_kuid (err 0)
[   28.488480] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.488737] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.488761] bluetooth: Unknown symbol from_kuid (err 0)
[   28.503172] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.503429] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.503454] bluetooth: Unknown symbol from_kuid (err 0)
[   28.512576] init: bluetooth main process (622) terminated with status 1
[   28.512632] init: bluetooth main process ended, respawning
[   28.557278] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.557537] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.557561] bluetooth: Unknown symbol from_kuid (err 0)
[   28.587027] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.587284] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.587309] bluetooth: Unknown symbol from_kuid (err 0)
[   28.593952] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.594210] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.594234] bluetooth: Unknown symbol from_kuid (err 0)
[   28.609153] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.609408] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.609433] bluetooth: Unknown symbol from_kuid (err 0)
[   28.630930] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.631187] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.631211] bluetooth: Unknown symbol from_kuid (err 0)
[   28.643844] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.646697] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.646726] bluetooth: Unknown symbol from_kuid (err 0)
[   28.658683] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.658942] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.658966] bluetooth: Unknown symbol from_kuid (err 0)
[   28.663715] init: bluetooth main process (664) terminated with status 1
[   28.663772] init: bluetooth main process ended, respawning
[   28.701497] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.701753] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.701777] bluetooth: Unknown symbol from_kuid (err 0)
[   28.732322] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.732580] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.732605] bluetooth: Unknown symbol from_kuid (err 0)
[   28.737288] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.737565] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.737590] bluetooth: Unknown symbol from_kuid (err 0)
[   28.753933] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.754191] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.754216] bluetooth: Unknown symbol from_kuid (err 0)
[   28.769753] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.770010] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.770034] bluetooth: Unknown symbol from_kuid (err 0)
[   28.785753] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.786011] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.786035] bluetooth: Unknown symbol from_kuid (err 0)
[   28.790873] psmouse serio1: synaptics: Touchpad model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008/0x0
[   28.804300] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.805085] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.805112] bluetooth: Unknown symbol from_kuid (err 0)
[   28.808535] init: bluetooth main process (712) terminated with status 1
[   28.808589] init: bluetooth main process ended, respawning
[   28.823535] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   28.854868] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.855141] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.855166] bluetooth: Unknown symbol from_kuid (err 0)
[   28.878274] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.878532] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.878556] bluetooth: Unknown symbol from_kuid (err 0)
[   28.888883] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.889139] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.889164] bluetooth: Unknown symbol from_kuid (err 0)
[   28.903710] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.903969] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.903993] bluetooth: Unknown symbol from_kuid (err 0)
[   28.923612] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.923869] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.923894] bluetooth: Unknown symbol from_kuid (err 0)
[   28.938818] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.939075] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.939100] bluetooth: Unknown symbol from_kuid (err 0)
[   28.955989] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   28.964417] bluetooth: Unknown symbol __pskb_copy (err 0)
[   28.964447] bluetooth: Unknown symbol from_kuid (err 0)
[   28.966082] init: bluetooth main process (741) terminated with status 1
[   28.966137] init: bluetooth main process ended, respawning
[   29.002641] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   29.002900] bluetooth: Unknown symbol __pskb_copy (err 0)
[   29.002924] bluetooth: Unknown symbol from_kuid (err 0)
[   29.038329] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   29.038588] bluetooth: Unknown symbol __pskb_copy (err 0)
[   29.038613] bluetooth: Unknown symbol from_kuid (err 0)
[   29.043426] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   29.043686] bluetooth: Unknown symbol __pskb_copy (err 0)
[   29.043711] bluetooth: Unknown symbol from_kuid (err 0)
[   29.057898] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   29.058157] bluetooth: Unknown symbol __pskb_copy (err 0)
[   29.058182] bluetooth: Unknown symbol from_kuid (err 0)
[   29.077829] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   29.088574] bluetooth: Unknown symbol __pskb_copy (err 0)
[   29.088602] bluetooth: Unknown symbol from_kuid (err 0)
[   29.096142] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   29.101115] bluetooth: Unknown symbol __pskb_copy (err 0)
[   29.101144] bluetooth: Unknown symbol from_kuid (err 0)
[   29.135624] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   29.135884] bluetooth: Unknown symbol __pskb_copy (err 0)
[   29.135909] bluetooth: Unknown symbol from_kuid (err 0)
[   29.317574] init: bluetooth main process (769) terminated with status 1
[   29.317631] init: bluetooth main process ended, respawning
[   29.332138] init: Failed to spawn smbd main process: unable to execute: No such file or directory
[   29.355767] snd_intel8x0 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   29.355809] snd_intel8x0 0000:00:1f.5: setting latency timer to 64
[   29.499658] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   29.499916] bluetooth: Unknown symbol __pskb_copy (err 0)
[   29.499943] bluetooth: Unknown symbol from_kuid (err 0)
[   29.632805] init: failsafe main process (801) killed by TERM signal
[   29.756053] intel8x0_measure_ac97_clock: measured 54444 usecs (2623 samples)
[   29.756059] intel8x0: clocking to 48000
[   29.983252] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   29.986176] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   29.986883] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   29.987462] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   29.992232] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   29.992282] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   29.992327] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   29.992372] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   30.133927] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.134188] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.134214] bluetooth: Unknown symbol from_kuid (err 0)
[   30.173134] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.173395] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.173421] bluetooth: Unknown symbol from_kuid (err 0)
[   30.187083] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.187345] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.187372] bluetooth: Unknown symbol from_kuid (err 0)
[   30.220003] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.244419] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.244450] bluetooth: Unknown symbol from_kuid (err 0)
[   30.267479] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.267740] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.267766] bluetooth: Unknown symbol from_kuid (err 0)
[   30.316764] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.317029] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.317055] bluetooth: Unknown symbol from_kuid (err 0)
[   30.337554] init: bluetooth main process (914) terminated with status 1
[   30.337608] init: bluetooth main process ended, respawning
[   30.339696] init: udev-fallback-graphics main process (946) terminated with status 1
[   30.468759] type=1400 audit(1357080065.779:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=972 comm="apparmor_parser"
[   30.506584] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.506846] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.506872] bluetooth: Unknown symbol from_kuid (err 0)
[   30.509181] type=1400 audit(1357080065.819:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=978 comm="apparmor_parser"
[   30.513179] type=1400 audit(1357080065.823:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=978 comm="apparmor_parser"
[   30.513716] type=1400 audit(1357080065.823:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=978 comm="apparmor_parser"
[   30.583056] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.583316] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.583342] bluetooth: Unknown symbol from_kuid (err 0)
[   30.591809] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.604746] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.604778] bluetooth: Unknown symbol from_kuid (err 0)
[   30.606590] 8139too 0000:02:00.0: eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   30.617031] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.617292] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.617318] bluetooth: Unknown symbol from_kuid (err 0)
[   30.637099] type=1400 audit(1357080065.947:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=982 comm="apparmor_parser"
[   30.665624] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.665907] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.665934] bluetooth: Unknown symbol from_kuid (err 0)
[   30.694984] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.695245] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.695272] bluetooth: Unknown symbol from_kuid (err 0)
[   30.736385] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.736641] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.736668] bluetooth: Unknown symbol from_kuid (err 0)
[   30.742654] init: bluetooth main process (984) terminated with status 1
[   30.742710] init: bluetooth main process ended, respawning
[   30.781945] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.782207] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.782234] bluetooth: Unknown symbol from_kuid (err 0)
[   30.814429] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.814691] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.814718] bluetooth: Unknown symbol from_kuid (err 0)
[   30.819542] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.819804] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.819830] bluetooth: Unknown symbol from_kuid (err 0)
[   30.835817] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.839500] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.839531] bluetooth: Unknown symbol from_kuid (err 0)
[   30.850871] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.851132] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.851159] bluetooth: Unknown symbol from_kuid (err 0)
[   30.866185] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.866449] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.866475] bluetooth: Unknown symbol from_kuid (err 0)
[   30.878718] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.878979] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.879005] bluetooth: Unknown symbol from_kuid (err 0)
[   30.886298] init: bluetooth main process (1015) terminated with status 1
[   30.886353] init: bluetooth respawning too fast, stopped
[   30.922614] bluetooth: Unknown symbol compat_dependency_symbol (err 0)
[   30.922876] bluetooth: Unknown symbol __pskb_copy (err 0)
[   30.922902] bluetooth: Unknown symbol from_kuid (err 0)
[   31.477196] drm: Unknown symbol ktime_get_monotonic_offset (err 0)
[   31.477467] drm: Unknown symbol compat_dependency_symbol (err 0)
[   31.477862] drm: Unknown symbol from_kuid_munged (err 0)
[   32.088053] mtrr: base(0xe8000000) is not aligned on a size(0x1fd0000) boundary
[   32.335164] init: plymouth-upstart-bridge main process (501) killed by TERM signal
[   33.327483] init: Failed to spawn nmbd main process: unable to execute: No such file or directory
[   41.360033] eth0: no IPv6 routers present
[ 3074.241192] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[ 3074.241199] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
[ 3076.403282] atkbd serio0: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[ 3076.403289] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
[ 3076.803641] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[ 3076.803648] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
[ 3077.204049] atkbd serio0: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[ 3077.204056] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
```

---

### Post by circa on 2013-01-10
Well, obviously no one has any idea nor can anyone direct me to someone who might, so I'll just mark this as solved and drop down to another kernel. ](*,)

---

