---
title: "Atheros AR5212/AR5213 wireless does not work"
date: 2013-08-09
forum: Networking &amp; Wireless
---

### Post by cddotdot on 2013-08-09
Hi,

I have recently installed Ubuntu 12.04 LTS 32bit on one of my old machines, a Packard Bell Easynote R1004. It works pretty smoothly regardless of it's very low specifications and everything works out of the box except the wireless and the lack of a battery indicator.

All ubuntu updates have been applied via Update Manager.

Here are some commands and their output to help with the troubleshooting:

***lsb_release -d***

> Description:    Ubuntu 12.04.2 LTS

***uname -mr***
> 
3.5.0-37-generic i686

***lspci | grep Atheros***

> 00:06.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Wireless Network Adapter (rev 01)

***lspci -nn | grep 'Ath'***

>  00:06.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)

***iwconfig***

> lo        no wireless extensions.

eth0      no wireless extensions.

***iwconfig wlan0***

>  wlan0     No such device

***lsusb***

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***ifconfig -a*** (I have changed IP and Mac addresses)

> eth0    Link encap:Ethernet  HWaddr 00:30:d4:56:5d:60  
          inet addr:192.168.1.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe56::567:d0tt:tu67:6e78/88 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56852341 (56.8 MB)  TX bytes:5828489 (5.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:232516 (232.5 KB)  TX bytes:232516 (232.5 KB)


***lsmod***

> Module                  Size  Used by
vesafb                 13518  1 
joydev                 17394  0 
snd_via82xx            24725  2 
gameport               15089  1 snd_via82xx
snd_mpu401_uart        13866  1 snd_via82xx
snd_via82xx_modem      18395  0 
snd_ac97_codec        106118  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12671  1 snd_ac97_codec
snd_seq_midi           13133  0 
snd_pcm                81124  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_rawmidi            25426  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
microcode              18396  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 38104  0 
snd_timer              28932  2 snd_pcm,snd_seq
bnep                   17791  2 
parport_pc             32115  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13078  0 
bluetooth             189625  10 rfcomm,bnep
ppdev                  12850  0 
ath5k                 137284  0 
psmouse                91381  0 
ath                    19436  1 ath5k
snd                    62675  13 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13032  0 
i2c_viapro             12970  0 
mac80211              475546  1 ath5k
via_ircc               26789  0 
soundcore              14636  1 snd
irda                  185617  1 via_ircc
snd_page_alloc         14109  3 snd_via82xx,snd_via82xx_modem,snd_pcm
crc_ccitt              12628  1 irda
shpchp                 32326  0 
cfg80211              181041  3 ath5k,ath,mac80211
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
pata_via               13429  2 
via_rhine              27373  0 

***lsmod | grep "ath5k"***

> ath5k                 137284  0 
ath                    19436  1 ath5k
mac80211              475546  1 ath5k
cfg80211              181041  3 ath5k,ath,mac80211

***dmesg***

> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-37-generic (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #58~precise1-Ubuntu SMP Wed Jul 10 17:51:56 UTC 2013 (Ubuntu 3.5.0-37.58~precise1-generic 3.5.7.16)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001efeefff] usable
[    0.000000] BIOS-e820: [mem 0x000000001eff0000-0x000000001effffbf] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000001effffc0-0x000000001effffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000fff80000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: NEC Computers International Packard Bell EasyNote/NEC Versa Premium                , BIOS R1.00  /07/0520\x0d\x0a
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x1efef max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 base 010000000 mask FF8000000 write-back
[    0.000000]   2 base 018000000 mask FFC000000 write-back
[    0.000000]   3 base 01C000000 mask FFE000000 write-back
[    0.000000]   4 base 01E000000 mask FFF000000 write-back
[    0.000000]   5 base 090000000 mask FFF000000 write-combining
[    0.000000]   6 disabled
[    0.000000]   7 base 0A0000000 mask FFE000000 write-combining
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x1efeefff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1edfffff] page 2M
[    0.000000]  [mem 0x1ee00000-0x1efeefff] page 4k
[    0.000000] kernel direct mapping tables up to 0x1efeefff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x1d5c2000-0x1e491fff]
[    0.000000] ACPI: RSDP 000e6010 00014 (v00 OID_00)
[    0.000000] ACPI: RSDT 1effc2d0 0002C (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: FACP 1efffb00 00074 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: DSDT 1effc310 037E2 (v01 INSYDE    PN800 00001000 INTL 02002036)
[    0.000000] ACPI: FACS 1effffc0 00040
[    0.000000] ACPI: APIC 1efffb90 00068 (v01 INSYDE APIC_000 30303030 0000 00010200)
[    0.000000] ACPI: BIOS age (520) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 495MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1efef000
[    0.000000]   low ram: 0 - 1efef000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x1efeefff]
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x1efeefff]
[    0.000000] On node 0 totalpages: 126846
[    0.000000] free_area_init_node: node 0, pgdat c18c6540, node_mem_map dec0e200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 960 pages used for memmap
[    0.000000]   Normal zone: 121903 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.81 [http://simplefirmware.org](http://simplefirmware.org)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] e820: [mem 0x1f000000-0xfff7ffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @debfc000 s34176 r0 d23168 u57344
[    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 125854
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-37-generic root=UUID=b6dee3bf-2f2e-41fa-9977-610078c12f26 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1015544 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 476012k/507836k available (6055k kernel code, 31372k reserved, 2981k data, 760k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xdf7ef000 - 0xffbfe000   ( 516 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdefef000   ( 495 MB)
[    0.000000]       .init : 0xc18d4000 - 0xc1992000   ( 760 kB)
[    0.000000]       .data : 0xc15e9f15 - 0xc18d3400   (2981 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15e9f15   (6055 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=dd008000 soft=dd00a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1393.030 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 2786.06 BogoMIPS (lpj=5572120)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004054] Security Framework initialized
[    0.004090] AppArmor: AppArmor initialized
[    0.004094] Yama: becoming mindful.
[    0.004227] Mount-cache hash table entries: 512
[    0.004692] Initializing cgroup subsys cpuacct
[    0.004699] Initializing cgroup subsys memory
[    0.004718] Initializing cgroup subsys devices
[    0.004723] Initializing cgroup subsys freezer
[    0.004727] Initializing cgroup subsys blkio
[    0.004731] Initializing cgroup subsys perf_event
[    0.004783] Disabled fast string operations
[    0.004796] mce: CPU supports 5 MCE banks
[    0.004811] CPU0: Thermal monitoring enabled (TM1)
[    0.008264] SMP alternatives: switching to UP code
[    0.026665] Freeing SMP alternatives: 24k freed
[    0.026686] ftrace: allocating 27149 entries in 54 pages
[    0.040150] weird, boot CPU (#0) not listed by the BIOS.
[    0.040159] SMP motherboard not detected.
[    0.040165] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.148035] SMP disabled
[    0.148040] Performance Events: p6 PMU driver.
[    0.148051] ... version:                0
[    0.148054] ... bit width:              32
[    0.148056] ... generic registers:      2
[    0.148059] ... value mask:             00000000ffffffff
[    0.148062] ... max period:             000000007fffffff
[    0.148064] ... fixed-purpose events:   0
[    0.148067] ... event mask:             0000000000000003
[    0.148386] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.148475] Brought up 1 CPUs
[    0.148479] Total of 1 processors activated (2786.06 BogoMIPS).
[    0.148807] devtmpfs: initialized
[    0.149208] EVM: security.selinux
[    0.149211] EVM: security.SMACK64
[    0.149214] EVM: security.capability
[    0.149364] PM: Registering ACPI NVS region [mem 0x1effffc0-0x1effffff] (64 bytes)
[    0.151263] dummy: 
[    0.151324] RTC time:  0:23:36, date: 08/10/13
[    0.151417] NET: Registered protocol family 16
[    0.151705] EISA bus registered
[    0.152042] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
[    0.152056] PCI: PCI BIOS revision 2.10 entry at 0xe9b04, last bus=1
[    0.152059] PCI: Using configuration type 1 for base access
[    0.154094] bio: create slab <bio-0> at 0
[    0.154251] ACPI: Interpreter disabled.
[    0.154375] vgaarb: loaded
[    0.154750] SCSI subsystem initialized
[    0.154813] libata version 3.00 loaded.
[    0.154883] usbcore: registered new interface driver usbfs
[    0.154902] usbcore: registered new interface driver hub
[    0.154938] usbcore: registered new device driver usb
[    0.155093] PCI: Probing PCI hardware
[    0.155098] PCI: root bus 00: using default resources
[    0.155102] PCI: Probing PCI hardware (bus 00)
[    0.155153] PCI host bridge to bus 0000:00
[    0.155163] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.155168] pci_bus 0000:00: root bus resource [mem 0x00000000-0xffffffff]
[    0.155195] pci 0000:00:00.0: [1106:0259] type 00 class 0x060000
[    0.155213] pci 0000:00:00.0: reg 10: [mem 0xa0000000-0xa1ffffff pref]
[    0.155316] pci 0000:00:00.1: [1106:1259] type 00 class 0x060000
[    0.155379] pci 0000:00:00.2: [1106:2259] type 00 class 0x060000
[    0.155442] pci 0000:00:00.3: [1106:3259] type 00 class 0x060000
[    0.155505] pci 0000:00:00.4: [1106:4259] type 00 class 0x060000
[    0.155572] pci 0000:00:00.7: [1106:7259] type 00 class 0x060000
[    0.155641] pci 0000:00:01.0: [1106:b198] type 01 class 0x060400
[    0.155712] pci 0000:00:01.0: supports D1
[    0.155742] pci 0000:00:06.0: [168c:0013] type 00 class 0x020000
[    0.155767] pci 0000:00:06.0: reg 10: [mem 0x00000000-0x0000ffff]
[    0.155901] pci 0000:00:10.0: [1106:3038] type 00 class 0x0c0300
[    0.155965] pci 0000:00:10.0: reg 20: [io  0x1200-0x121f]
[    0.156045] pci 0000:00:10.0: supports D1 D2
[    0.156050] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156078] pci 0000:00:10.1: [1106:3038] type 00 class 0x0c0300
[    0.156142] pci 0000:00:10.1: reg 20: [io  0x1220-0x123f]
[    0.156200] pci 0000:00:10.1: supports D1 D2
[    0.156204] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156231] pci 0000:00:10.2: [1106:3038] type 00 class 0x0c0300
[    0.156294] pci 0000:00:10.2: reg 20: [io  0x1240-0x125f]
[    0.156351] pci 0000:00:10.2: supports D1 D2
[    0.156355] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156382] pci 0000:00:10.3: [1106:3104] type 00 class 0x0c0320
[    0.156406] pci 0000:00:10.3: reg 10: [mem 0xf0000000-0xf00000ff]
[    0.156503] pci 0000:00:10.3: supports D1 D2
[    0.156508] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156542] pci 0000:00:11.0: [1106:3177] type 00 class 0x060100
[    0.156629] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.156640] pci 0000:00:11.0: quirk: [io  0x1000-0x107f] claimed by vt8235 PM
[    0.156646] pci 0000:00:11.0: quirk: [io  0x1400-0x140f] claimed by vt8235 SMB
[    0.156703] pci 0000:00:11.1: [1106:0571] type 00 class 0x01018a
[    0.156769] pci 0000:00:11.1: reg 20: [io  0x1100-0x110f]
[    0.156856] pci 0000:00:11.5: [1106:3059] type 00 class 0x040100
[    0.156881] pci 0000:00:11.5: reg 10: [io  0xe000-0xe0ff]
[    0.156981] pci 0000:00:11.5: supports D1 D2
[    0.157006] pci 0000:00:11.6: [1106:3068] type 00 class 0x078000
[    0.157030] pci 0000:00:11.6: reg 10: [io  0xe100-0xe1ff]
[    0.157153] pci 0000:00:12.0: [1106:3065] type 00 class 0x020000
[    0.157176] pci 0000:00:12.0: reg 10: [io  0xe200-0xe2ff]
[    0.157191] pci 0000:00:12.0: reg 14: [mem 0xd0000000-0xd00000ff]
[    0.157280] pci 0000:00:12.0: supports D1 D2
[    0.157284] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.157365] pci 0000:01:00.0: [1106:3118] type 00 class 0x030000
[    0.157387] pci 0000:01:00.0: reg 10: [mem 0x90000000-0x93ffffff pref]
[    0.157400] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xc0ffffff]
[    0.157444] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.157484] pci 0000:01:00.0: supports D1 D2
[    0.157536] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.157544] pci 0000:00:01.0:   bridge window [io  0xc000-0xdfff]
[    0.157552] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff]
[    0.157559] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x9fffffff pref]
[    0.158402] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.158602] pci 0000:00:11.0: VIA IRQ router [1106:3177]
[    0.158663] PCI: pci_cache_line_size set to 64 bytes
[    0.158759] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.158764] e820: reserve RAM buffer [mem 0x1efef000-0x1fffffff]
[    0.158961] NetLabel: Initializing
[    0.158965] NetLabel:  domain hash size = 128
[    0.158967] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.158989] NetLabel:  unlabeled traffic allowed by default
[    0.176636] AppArmor: AppArmor Filesystem Enabled
[    0.176685] pnp: PnP ACPI: disabled
[    0.176693] PnPBIOS: Scanning system for PnP BIOS support...
[    0.176790] PnPBIOS: Found PnP BIOS installation structure at 0xc00ff020
[    0.176794] PnPBIOS: PnP BIOS version 1.0, entry 0xeb000:0x36f8, dseg 0xeb000
[    0.176803] PNPBIOS fault.. attempting recovery.
[    0.176806] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[    0.176808] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[    0.176811] PnPBIOS: Check with your vendor for an updated BIOS
[    0.176814] PnPBIOS: dev_node_info: unexpected status 0x24
[    0.176816] PnPBIOS: Unable to get node info.  Aborting.
[    0.180115] pci 0000:00:06.0: BAR 0: assigned [mem 0x20000000-0x2000ffff]
[    0.180131] pci 0000:01:00.0: BAR 6: assigned [mem 0x94000000-0x9400ffff pref]
[    0.180137] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.180143] pci 0000:00:01.0:   bridge window [io  0xc000-0xdfff]
[    0.180151] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff]
[    0.180158] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x9fffffff pref]
[    0.180182] pci 0000:00:01.0: setting latency timer to 64
[    0.180189] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.180194] pci_bus 0000:00: resource 5 [mem 0x00000000-0xffffffff]
[    0.180199] pci_bus 0000:01: resource 0 [io  0xc000-0xdfff]
[    0.180203] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xcfffffff]
[    0.180208] pci_bus 0000:01: resource 2 [mem 0x90000000-0x9fffffff pref]
[    0.180292] NET: Registered protocol family 2
[    0.180419] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.180627] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.180814] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.181000] TCP: Hash tables configured (established 16384 bind 16384)
[    0.181003] TCP: reno registered
[    0.181009] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.181022] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.181149] NET: Registered protocol family 1
[    0.181199] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.181226] PCI: setting IRQ 11 as level-triggered
[    0.181233] pci 0000:00:10.0: found PCI INT A -> IRQ 11
[    0.181275] pci 0000:00:10.0: sharing IRQ 11 with 0000:00:12.0
[    0.181281] pci 0000:00:10.0: sharing IRQ 11 with 0000:01:00.0
[    0.181316] PCI: setting IRQ 7 as level-triggered
[    0.181322] pci 0000:00:10.1: found PCI INT B -> IRQ 7
[    0.181391] PCI: setting IRQ 5 as level-triggered
[    0.181397] pci 0000:00:10.2: found PCI INT C -> IRQ 5
[    0.181433] pci 0000:00:10.2: sharing IRQ 5 with 0000:00:11.5
[    0.181440] pci 0000:00:10.2: sharing IRQ 5 with 0000:00:11.6
[    0.181475] PCI: setting IRQ 10 as level-triggered
[    0.181481] pci 0000:00:10.3: found PCI INT D -> IRQ 10
[    0.181589] pci 0000:01:00.0: Boot video device
[    0.181595] PCI: CLS 16 bytes, default 64
[    0.181924] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.182425] audit: initializing netlink socket (disabled)
[    0.182448] type=2000 audit(1376094215.180:1): initialized
[    0.220660] Trying to unpack rootfs image as initramfs...
[    0.264632] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.271339] VFS: Disk quotas dquot_6.5.2
[    0.271445] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.272547] fuse init (API version 7.19)
[    0.272704] msgmni has been set to 929
[    0.288292] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.288397] io scheduler noop registered
[    0.288401] io scheduler deadline registered (default)
[    0.288418] io scheduler cfq registered
[    0.288715] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.288748] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.288899] intel_idle: does not run on family 6 model 13
[    0.292373] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.294434] Linux agpgart interface v0.103
[    0.294550] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[    0.297722] isapnp: Scanning for PnP cards...
[    0.303395] agpgart-via 0000:00:00.0: AGP aperture is 32M @ 0xa0000000
[    0.354232] brd: module loaded
[    0.355618] loop: module loaded
[    0.356583] Fixed MDIO Bus: probed
[    0.356680] tun: Universal TUN/TAP device driver, 1.6
[    0.356683] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.356768] PPP generic driver version 2.4.2
[    0.360502] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.360573] ehci_hcd 0000:00:10.3: found PCI INT D -> IRQ 10
[    0.360656] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.360669] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.360739] ehci_hcd 0000:00:10.3: irq 10, io mem 0xf0000000
[    0.372377] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.372451] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.372456] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.372461] usb usb1: Product: EHCI Host Controller
[    0.372465] usb usb1: Manufacturer: Linux 3.5.0-37-generic ehci_hcd
[    0.372469] usb usb1: SerialNumber: 0000:00:10.3
[    0.372709] hub 1-0:1.0: USB hub found
[    0.372720] hub 1-0:1.0: 6 ports detected
[    0.372875] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.372929] uhci_hcd: USB Universal Host Controller Interface driver
[    0.372989] uhci_hcd 0000:00:10.0: found PCI INT A -> IRQ 11
[    0.373031] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:12.0
[    0.373038] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:01:00.0
[    0.373059] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.373071] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.373114] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[    0.373172] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.373177] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.373181] usb usb2: Product: UHCI Host Controller
[    0.373185] usb usb2: Manufacturer: Linux 3.5.0-37-generic uhci_hcd
[    0.373189] usb usb2: SerialNumber: 0000:00:10.0
[    0.373375] hub 2-0:1.0: USB hub found
[    0.373383] hub 2-0:1.0: 2 ports detected
[    0.373493] uhci_hcd 0000:00:10.1: found PCI INT B -> IRQ 7
[    0.373545] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.373554] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.373584] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[    0.373631] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.373636] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.373640] usb usb3: Product: UHCI Host Controller
[    0.373644] usb usb3: Manufacturer: Linux 3.5.0-37-generic uhci_hcd
[    0.373648] usb usb3: SerialNumber: 0000:00:10.1
[    0.373808] hub 3-0:1.0: USB hub found
[    0.373816] hub 3-0:1.0: 2 ports detected
[    0.373922] uhci_hcd 0000:00:10.2: found PCI INT C -> IRQ 5
[    0.373958] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.5
[    0.373965] uhci_hcd 0000:00:10.2: sharing IRQ 5 with 0000:00:11.6
[    0.373982] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.373991] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.374022] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[    0.374075] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.374079] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.374084] usb usb4: Product: UHCI Host Controller
[    0.374088] usb usb4: Manufacturer: Linux 3.5.0-37-generic uhci_hcd
[    0.374092] usb usb4: SerialNumber: 0000:00:10.2
[    0.374251] hub 4-0:1.0: USB hub found
[    0.374259] hub 4-0:1.0: 2 ports detected
[    0.374453] usbcore: registered new interface driver libusual
[    0.374498] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.404034] i8042: Detected active multiplexing controller, rev 1.1
[    0.412034] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.416226] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.416325] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.416366] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.416415] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.416650] mousedev: PS/2 mouse device common for all mice
[    0.417019] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    0.417059] rtc0: alarms up to one day, 114 bytes nvram
[    0.417178] device-mapper: uevent: version 1.0.3
[    0.417331] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.417375] EISA: Probing bus 0 at eisa.0
[    0.417386] Cannot allocate resource for EISA slot 1
[    0.417423] EISA: Detected 0 cards.
[    0.417440] cpuidle: using governor ladder
[    0.417442] cpuidle: using governor menu
[    0.417446] EFI Variables Facility v0.08 2004-May-17
[    0.420595] ashmem: initialized
[    0.420854] TCP: cubic registered
[    0.421068] NET: Registered protocol family 10
[    0.421439] NET: Registered protocol family 17
[    0.421469] Key type dns_resolver registered
[    0.421605] Using IPI No-Shortcut mode
[    0.421758] PM: Hibernation image not present or could not be loaded.
[    0.421789] registered taskstats version 1
[    0.425661] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    0.911732] isapnp: No Plug & Play device found
[    1.182401] Freeing initrd memory: 15168k freed
[    1.205871] Key type trusted registered
[    1.208898] Key type encrypted registered
[    1.212355]   Magic number: 9:581:354
[    1.212368] input event0: hash matches
[    1.212517] rtc_cmos rtc_cmos: setting system clock to 2013-08-10 00:23:37 UTC (1376094217)
[    1.212589] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.212592] EDD information not available.
[    1.212809] Freeing unused kernel memory: 760k freed
[    1.213454] Write protecting the kernel text: 6056k
[    1.213489] Write protecting the kernel read-only data: 2480k
[    1.213491] NX-protecting the kernel data: 4184k
[    1.220143] Switching to clocksource tsc
[    1.241035] udevd[84]: starting version 175
[    1.412573] via_rhine: v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    1.412644] via-rhine 0000:00:12.0: found PCI INT A -> IRQ 11
[    1.412669] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:10.0
[    1.412692] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:01:00.0
[    1.440772] via-rhine 0000:00:12.0: eth0: VIA Rhine II at 0xd0000000, 00:40:d0:85:3d:50, IRQ 11
[    1.441583] via-rhine 0000:00:12.0: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link cde1
[    1.447288] pata_via 0000:00:11.1: version 0.3.4
[    1.451189] scsi0 : pata_via
[    1.455765] scsi1 : pata_via
[    1.455890] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    1.455895] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    1.620700] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    1.620710] ata1.00: 78140160 sectors, multi 16: LBA48 
[    1.636527] ata1.00: configured for UDMA/100
[    1.636742] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    1.637115] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.637195] sd 0:0:0:0: [sda] Write Protect is off
[    1.637201] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.637235] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.637711] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.695579]  sda: sda1 sda2 < sda5 >
[    1.696076] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.111060] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.111071] EXT4-fs (sda1): write access will be enabled during recovery
[    4.306108] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.306131] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 135115
[    4.306274] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 134947
[    4.306296] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 134960
[    4.306315] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 134952
[    4.306334] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 135178
[    4.306354] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 135209
[    4.306398] EXT4-fs (sda1): 6 orphan inodes deleted
[    4.306402] EXT4-fs (sda1): recovery complete
[    4.456298] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   23.589443] Adding 505852k swap on /dev/sda5.  Priority:-1 extents:1 across:505852k 
[   23.607451] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.657703] udevd[283]: starting version 175
[   23.763013] lp: driver loaded but no devices found
[   23.927446] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.960213] cfg80211: Calling CRDA to update world regulatory domain
[   23.965878] irda_init()
[   23.965906] NET: Registered protocol family 23
[   23.973426] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   24.095290] ACPI Exception: AE_BAD_PARAMETER, Thread 3668990160 could not acquire Mutex [0x1] (20120320/utmutex-276)
[   24.350128] type=1400 audit(1376094240.632:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=482 comm="apparmor_parser"
[   24.352995] type=1400 audit(1376094240.636:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=482 comm="apparmor_parser"
[   24.353456] type=1400 audit(1376094240.636:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=482 comm="apparmor_parser"
[   24.536871] Bluetooth: Core ver 2.16
[   24.536908] NET: Registered protocol family 31
[   24.536912] Bluetooth: HCI device and connection manager initialized
[   24.536916] Bluetooth: HCI socket layer initialized
[   24.536919] Bluetooth: L2CAP socket layer initialized
[   24.536935] Bluetooth: SCO socket layer initialized
[   24.538414] ath5k 0000:00:06.0: enabling device (0000 -> 0002)
[   24.538431] ath5k 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   24.538523] ath5k 0000:00:06.0: registered as 'phy0'
[   24.538532] genirq: Flags mismatch irq 0. 00000080 (ath) vs. 00015a20 (timer)
[   24.538539] ath5k: phy0: request_irq failed
[   24.538567] ath5k: probe of 0000:00:06.0 failed with error -16
[   24.554410] ppdev: user-space parallel port driver
[   24.578471] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.578479] Bluetooth: BNEP filters: protocol multicast
[   24.623344] Bluetooth: RFCOMM TTY layer initialized
[   24.623357] Bluetooth: RFCOMM socket layer initialized
[   24.623360] Bluetooth: RFCOMM ver 1.11
[   24.631686] type=1400 audit(1376094240.916:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=549 comm="apparmor_parser"
[   24.632678] type=1400 audit(1376094240.916:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=549 comm="apparmor_parser"
[   24.719030] microcode: CPU0 sig=0x6d8, pf=0x20, revision=0x20
[   24.977941] snd_via82xx_modem 0000:00:11.6: found PCI INT C -> IRQ 5
[   24.977977] snd_via82xx_modem 0000:00:11.6: sharing IRQ 5 with 0000:00:10.2
[   24.977990] snd_via82xx_modem 0000:00:11.6: sharing IRQ 5 with 0000:00:11.5
[   24.980555] snd_via82xx_modem 0000:00:11.6: setting latency timer to 64
[   25.072444] psmouse serio3: synaptics: Touchpad model: 1, fw: 5.9, id: 0xf6eb3, caps: 0xa04713/0x0/0x0
[   25.126122] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input1
[   25.262132] init: failsafe main process (637) killed by TERM signal
[   25.502726] snd_via82xx 0000:00:11.5: found PCI INT C -> IRQ 5
[   25.502762] snd_via82xx 0000:00:11.5: sharing IRQ 5 with 0000:00:10.2
[   25.502776] snd_via82xx 0000:00:11.5: sharing IRQ 5 with 0000:00:11.6
[   25.502933] snd_via82xx 0000:00:11.5: setting latency timer to 64
[   25.559433] type=1400 audit(1376094241.844:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=747 comm="apparmor_parser"
[   25.576291] type=1400 audit(1376094241.860:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=747 comm="apparmor_parser"
[   25.589437] type=1400 audit(1376094241.872:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=748 comm="apparmor_parser"
[   25.600654] type=1400 audit(1376094241.884:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=748 comm="apparmor_parser"
[   25.601121] type=1400 audit(1376094241.884:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=748 comm="apparmor_parser"
[   25.850751] cfg80211: World regulatory domain updated:
[   25.850764] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.850768] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.850772] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.850775] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.850779] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.850782] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.936232] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   26.496427] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   26.496435] vesafb: scrolling: redraw
[   26.496441] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   26.496605] vesafb: framebuffer at 0x90000000, mapped to 0xdfc80000, using 1216k, total 1216k
[   26.497122] Console: switching to colour frame buffer device 80x30
[   26.497150] fb0: VESA VGA frame buffer device
[   27.284166] init: plymouth-stop pre-start process (1029) terminated with status 1


***sudo lshw -C network***

  > *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212/AR5213 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:20000000-2000ffff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:85:3d:50
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.0.18 latency=128 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 ioport:e200(size=256) memory:d0000000-d00000ff


***iwlist scan***

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

***iwlist scan wlan0***

>  iwlist: unknown command `wlan0' (check 'iwlist --help').

***sudo /etc/init.d/networking restart***

 > * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...  


**Other things that I have tried with no avail:**

***modprobe ath5k*** - blank response and no difference.

***MadWifi drivers ***- also didn't make a difference (I have made a fresh install of Ubuntu 12.04 since this so they are no longer installed).

What can I do to make the wireless work?

Thank you.

---

### Post by chili555 on 2013-08-09
> [ 24.538431] ath5k 0000:00:06.0: [COLOR="#FF0000"]can't find IRQ for PCI INT A[/COLOR]; please try using pci=biosirq
[ 24.538523] ath5k 0000:00:06.0: registered as 'phy0'
[ 24.538532] genirq: Flags mismatch irq 0. 00000080 (ath) vs. 00015a20 (timer)
[ 24.538539][COLOR="#FF0000"] ath5k: phy0: request_irq failed[/COLOR]
[ 24.538567] ath5k: probe of 0000:00:06.0 failed with error -16In the BIOS, how are IRQs set up? Auto-select usually works well. Here is a BIOS page, undoubtedly not yours, but it shows what you are probably looking for.

I suggest you make this change in the BIOS, reboot and let us hear your report.

---

### Post by cddotdot on 2013-08-09
Hi chili55,

Thank you for your quick response.

I have just fixed the issue (which from what you suggest sounds like it's a similar fix), I came back here to detail the steps I took.

As suggested by: [http://www.linuxforums.org/forum/wireless-internet/159283-atheros-ar5001x-8.html](http://www.linuxforums.org/forum/wireless-internet/159283-atheros-ar5001x-8.html) specifically: 

> I got it working now adding these options to the kernel boot parameters, as the BIOS really seems screwed about these:
   
Code:

 *acpi=force irqpoll noapictimer* 
 after that simply typing
   
Code:

 *modprobe ath5k*

was enough to have the wifi networks show up in NetworkManager.


I did the following:

***In terminal:***

> sudo gedit /etc/default/grub

I changed the line which was orginally:

> GRUB_CMDLINE_LINUX=""

To the following:

> GRUB_CMDLINE_LINUX="acpi=force irqpoll noapictimer"

And then typed:

> modprobe ath5k

Thereafter:

> /etc/init.d/networking restart

Finally:

> service network-manager restart

After a reboot both my wireless issue and the lack of a battery indicator are fixed! I am able to see wireless networks in network manager and the battery indicator has reappeared.

I hope this information helps someone with the same issue.

Thanks.

---

### Post by chili555 on 2013-08-10
Awesome! Great job. I am sure this will help quite a few people. I'm glad it's working as expected.

---

