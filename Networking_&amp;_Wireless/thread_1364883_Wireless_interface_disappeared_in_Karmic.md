---
title: "Wireless interface disappeared in Karmic"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by sot3 on 2009-12-26
Yesterday I booted to a command prompt to fix a problem with my nvidia driver on my Dell Precision M60 laptop, and while there I needed to connect with a wire to download some files.  When I booted back to gdm, I found that the network manager no longer has any "Enable Wireless" option below "Enable Networking" on the dropdown menu.  I doubt that my video driver activities impacted network connectivity, but I'm sure that other updates had been installed since my last reboot, too.  On further investigation, I've found that wlan0 no longer exists, and in fact it no longer seems to recognize my cardbus D-Link WNA-2330 wireless adapter, or maybe it's just not initializing it properly because the power light doesn't even come on anymore.  It does recognize the internal 802.11b wireless adapter that I've had disabled via BIOS ever since I started using the D-Link, but the only reason I mention that is that you're going to see it listed in the info I've provided below; beyond that it does not interest me.  Now that I look closer at dmesg, I don't see any mention of cardbus or pcmcia at all anymore!

Interestingly enough, I booted from my 9.10 live CD and the D-Link comes right up, lights come on and the OS uses it just fine.  But then I boot from HD and there's not even any mention of "ath5k" in the logs anymore.  SO I gather something has been damaged or disabled in my install, but what?  I've tried replacing network manager with WICD and got the same results: no wireless interface or wireless options are displayed.

No sign of wlan0:
```
$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

vboxnet0  no wireless extensions.

$ ifconfig 
eth1      Link encap:Ethernet  HWaddr 00:11:43:60:b3:87  
          inet addr:192.168.0.250  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe60:b387/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2639789 (2.6 MB)  TX bytes:525851 (525.8 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2840 (2.8 KB)  TX bytes:2840 (2.8 KB)

```

And the adapter isn't recognized either (again, the Intel Pro/Wireless 2100 is the built-in adapter that I do not use, have never used, and do not wish to use)
```

$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:11:43:60:b3:87
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5705-v3.11 ip=192.168.0.250 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=34 mingnt=2
       resources: memory:fafee000-fafeefff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


```

I found that lsmod has several references to "ath5k" when I boot from live CD, but there are none when I boot from disk:
```
$ lsmod
Module                  Size  Used by
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
nvidia               7092040  36 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
tg3                   109600  0 
video                  19380  0 
output                  2780  1 video
intel_agp              27484  1 
agpgart                34988  2 nvidia,intel_agp

```


Even lspci doesn't mention it.  Booting from disk, I get this:
```
$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV31 [Quadro FX Go700] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```

But when I boot from live CD I get the same thing plus one additional line:
```
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```

Lastly, here is my dmesg output from both a live CD boot and an HD boot where the D-Link (atheros) card is nowhere to be found.

My liveCD boot (where the wireless is fine):
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffae000 (usable)
[    0.000000]  BIOS-e820: 000000007ffae000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x7ffae max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FEDA0000 mask FFFFE0000 write-through
[    0.000000]   2 disabled
[    0.000000]   3 disabled
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
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffae000 (usable)
[    0.000000]  modified: 000000007ffae000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 7fa02000 - 7ff7f098
[    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
[    0.000000] Move RAMDISK from 000000007fa02000 - 000000007ff7f097 to 008ad000 - 00e2a097
[    0.000000] ACPI: RSDP 000fdf00 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 7fff0000 00030 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: FACP 7fff0400 00074 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: DSDT 7fff0c00 02E30 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 7ffff800 00040
[    0.000000] ACPI: ASF! 7fff0800 0005B (v16 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: BOOT 7fff07c0 00028 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac198]              BRK ==> [00008a9000 - 00008ac198]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffae
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffae
[    0.000000] On node 0 totalpages: 524105
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294560 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7eda0000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c200a000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520009
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10484120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffae)
[    0.000000] Memory: 2054544k/2096824k available (4565k kernel code, 41024k reserved, 2143k data, 540k init, 1187520k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1694.554 MHz processor.
[    0.001517] Console: colour VGA+ 80x25
[    0.001522] console [tty0] enabled
[    0.001582] Calibrating delay loop (skipped), value calculated using timer frequency.. 3389.10 BogoMIPS (lpj=6778216)
[    0.001614] Security Framework initialized
[    0.001655] AppArmor: AppArmor initialized
[    0.001666] Mount-cache hash table entries: 512
[    0.001863] Initializing cgroup subsys ns
[    0.001873] Initializing cgroup subsys cpuacct
[    0.001878] Initializing cgroup subsys memory
[    0.001890] Initializing cgroup subsys freezer
[    0.001893] Initializing cgroup subsys net_cls
[    0.001914] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001917] CPU: L2 cache: 2048K
[    0.001923] mce: CPU supports 5 MCE banks
[    0.001934] ------------[ cut here ]------------
[    0.001950] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()
[    0.001954] Hardware name: Precision M60                   
[    0.001957] Modules linked in:
[    0.001962] Pid: 0, comm: swapper Not tainted 2.6.31-14-generic #48-Ubuntu
[    0.001966] Call Trace:
[    0.001979]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
[    0.001984]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
[    0.001989]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
[    0.001994]  [<c01451d5>] warn_slowpath_null+0x15/0x20
[    0.001998]  [<c011d7e3>] native_apic_write_dummy+0x33/0x40
[    0.002007]  [<c011278c>] intel_init_thermal+0xac/0x1a0
[    0.002012]  [<c0111dbb>] mce_intel_feature_init+0xb/0x60
[    0.002016]  [<c010fcf0>] mce_cpu_features+0x10/0x40
[    0.002025]  [<c056ac3c>] mcheck_init+0x14a/0x188
[    0.002029]  [<c0569078>] ? init_hypervisor+0xb/0x2c
[    0.002034]  [<c0569030>] identify_cpu+0x20e/0x21d
[    0.002042]  [<c0795732>] identify_boot_cpu+0xd/0x23
[    0.002046]  [<c07958c8>] check_bugs+0xb/0xe9
[    0.002054]  [<c078e8c3>] start_kernel+0x2dc/0x2ec
[    0.002059]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
[    0.002064]  [<c078e07c>] i386_start_kernel+0x7c/0x83
[    0.002076] ---[ end trace a7919e7f17c0a725 ]---
[    0.002079] CPU0: Thermal monitoring enabled (TM1)
[    0.002093] Performance Counters: 
[    0.002097] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.002100] no hardware sampling interrupt available.
[    0.002102] p6 PMU driver.
[    0.002109] ... version:                 0
[    0.002111] ... bit width:               32
[    0.002113] ... generic counters:        2
[    0.002115] ... value mask:              00000000ffffffff
[    0.002118] ... max period:              000000007fffffff
[    0.002120] ... fixed-purpose counters:  0
[    0.002122] ... counter mask:            0000000000000003
[    0.002129] Checking 'hlt' instruction... OK.
[    0.016931] SMP alternatives: switching to UP code
[    0.024016] Freeing SMP alternatives: 19k freed
[    0.024027] ACPI: Core revision 20090521
[    0.029395] ACPI: setting ELCR to 0200 (from 0800)
[    0.031750] weird, boot CPU (#0) not listed by the BIOS.
[    0.031752] SMP motherboard not detected.
[    0.031755] Local APIC not detected. Using dummy APIC emulation.
[    0.031757] SMP disabled
[    0.031924] Brought up 1 CPUs
[    0.031927] Total of 1 processors activated (3389.10 BogoMIPS).
[    0.031940] CPU0 attaching NULL sched-domain.
[    0.032204] Booting paravirtualized kernel on bare hardware
[    0.032441] regulator: core version 0.5
[    0.032469] Time: 17:51:45  Date: 12/26/09
[    0.032527] NET: Registered protocol family 16
[    0.032681] EISA bus registered
[    0.032697] ACPI: bus type pci registered
[    0.066485] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    0.066488] PCI: Using configuration type 1 for base access
[    0.067655] bio: create slab <bio-0> at 0
[    0.068213] ACPI: EC: Look up EC in DSDT
[    0.077837] ACPI: Interpreter enabled
[    0.077848] ACPI: (supports S0 S1 S3 S4 S5)
[    0.077873] ACPI: Using PIC for interrupt routing
[    0.097627] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.102423] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.102480] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.102596] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.102649] pci 0000:00:1d.1: reg 20 io port: [0xbf40-0xbf5f]
[    0.102702] pci 0000:00:1d.2: reg 20 io port: [0xbf20-0xbf3f]
[    0.102763] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4fffc00-0xf4ffffff]
[    0.102821] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.102827] pci 0000:00:1d.7: PME# disabled
[    0.102915] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.102920] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.102944] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.102952] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.102959] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.102967] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.102974] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.102982] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.103025] pci 0000:00:1f.5: reg 10 io port: [0xb800-0xb8ff]
[    0.103033] pci 0000:00:1f.5: reg 14 io port: [0xbc40-0xbc7f]
[    0.103040] pci 0000:00:1f.5: reg 18 32bit mmio: [0xf4fff800-0xf4fff9ff]
[    0.103047] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xf4fff400-0xf4fff4ff]
[    0.103077] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.103081] pci 0000:00:1f.5: PME# disabled
[    0.103118] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.103124] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
[    0.103143] pci 0000:01:00.0: reg 30 32bit mmio: [0x80000000-0x8001ffff]
[    0.103192] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.103196] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.103201] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.103256] pci 0000:02:00.0: reg 10 64bit mmio: [0xfaff0000-0xfaffffff]
[    0.103309] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.103314] pci 0000:02:00.0: PME# disabled
[    0.103349] pci 0000:02:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.103368] pci 0000:02:01.0: supports D1 D2
[    0.103371] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.103376] pci 0000:02:01.0: PME# disabled
[    0.103409] pci 0000:02:01.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.103428] pci 0000:02:01.1: supports D1 D2
[    0.103431] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.103436] pci 0000:02:01.1: PME# disabled
[    0.103470] pci 0000:02:01.2: reg 10 32bit mmio: [0xfafef800-0xfafeffff]
[    0.103478] pci 0000:02:01.2: reg 14 32bit mmio: [0xfafe8000-0xfafebfff]
[    0.103518] pci 0000:02:01.2: supports D1 D2
[    0.103520] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot
[    0.103525] pci 0000:02:01.2: PME# disabled
[    0.103555] pci 0000:02:01.3: reg 10 io port: [0xecf8-0xecff]
[    0.103633] pci 0000:02:03.0: reg 10 32bit mmio: [0xfafee000-0xfafeefff]
[    0.103713] pci 0000:00:1e.0: transparent bridge
[    0.103718] pci 0000:00:1e.0: bridge io port: [0xd000-0xefff]
[    0.103723] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6000000-0xfbffffff]
[    0.103766] pci_bus 0000:00: on NUMA node 0
[    0.103771] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.104018] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.104075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.122589] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.122717] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.122840] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.122964] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.123069] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.123198] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.123419] SCSI subsystem initialized
[    0.123472] libata version 3.00 loaded.
[    0.123549] usbcore: registered new interface driver usbfs
[    0.123572] usbcore: registered new interface driver hub
[    0.123601] usbcore: registered new device driver usb
[    0.123743] ACPI: WMI: Mapper loaded
[    0.123745] PCI: Using ACPI for IRQ routing
[    0.124087] Bluetooth: Core ver 2.15
[    0.124117] NET: Registered protocol family 31
[    0.124119] Bluetooth: HCI device and connection manager initialized
[    0.124123] Bluetooth: HCI socket layer initialized
[    0.124125] NetLabel: Initializing
[    0.124127] NetLabel:  domain hash size = 128
[    0.124129] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.124146] NetLabel:  unlabeled traffic allowed by default
[    0.126268] pnp: PnP ACPI init
[    0.126291] ACPI: bus type pnp registered
[    0.136109] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.136114] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.136186] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.136191] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.136195] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.149746] pnp: PnP ACPI: found 12 devices
[    0.149749] ACPI: ACPI bus type pnp unregistered
[    0.149755] PnPBIOS: Disabled by ACPI PNP
[    0.149769] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.149773] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.149777] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.149781] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.149784] system 00:00: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.149788] system 00:00: iomem range 0x7fff0000-0x7fffffff has been reserved
[    0.149792] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.149796] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.149803] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.149810] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.149814] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.149818] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.149821] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.149829] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.184513] AppArmor: AppArmor Filesystem Enabled
[    0.184525] pci 0000:01:00.0: BAR 6: no parent found for of device [0x80000000-0x8001ffff]
[    0.184552] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.184556] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.184561] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.184566] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.184579] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.184582] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.184588] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.184593] pci 0000:02:01.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.184598] pci 0000:02:01.0:   MEM window: 0x8c000000-0x8fffffff
[    0.184603] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
[    0.184606] pci 0000:02:01.1:   IO window: 0x00d800-0x00d8ff
[    0.184611] pci 0000:02:01.1:   IO window: 0x00dc00-0x00dcff
[    0.184616] pci 0000:02:01.1:   PREFETCH window: 0x84000000-0x87ffffff
[    0.184622] pci 0000:02:01.1:   MEM window: 0x90000000-0x93ffffff
[    0.184627] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.184631] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.184637] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.184642] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x87ffffff
[    0.184658] pci 0000:00:1e.0: setting latency timer to 64
[    0.184666] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.184840] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.184843] PCI: setting IRQ 11 as level-triggered
[    0.184849] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.184862] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.184868] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.184872] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.184875] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.184879] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.184882] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.184885] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.184889] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xfbffffff]
[    0.184892] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x87ffffff]
[    0.184895] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.184899] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.184902] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.184905] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.184909] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.184912] pci_bus 0000:03: resource 3 mem: [0x8c000000-0x8fffffff]
[    0.184915] pci_bus 0000:07: resource 0 io:  [0xd800-0xd8ff]
[    0.184919] pci_bus 0000:07: resource 1 io:  [0xdc00-0xdcff]
[    0.184922] pci_bus 0000:07: resource 2 pref mem [0x84000000-0x87ffffff]
[    0.184925] pci_bus 0000:07: resource 3 mem: [0x90000000-0x93ffffff]
[    0.184965] NET: Registered protocol family 2
[    0.185071] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.185463] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.186898] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.187825] TCP: Hash tables configured (established 131072 bind 65536)
[    0.187829] TCP reno registered
[    0.188014] NET: Registered protocol family 1
[    0.188119] Trying to unpack rootfs image as initramfs...
[    0.688009] Switched to high resolution mode on CPU 0
[    1.996108] Freeing initrd memory: 5620k freed
[    2.004007] Simple Boot Flag at 0x79 set to 0x1
[    2.004179] cpufreq-nforce2: No nForce2 chipset.
[    2.004213] Scanning for low memory corruption every 60 seconds
[    2.004370] audit: initializing netlink socket (disabled)
[    2.004404] type=2000 audit(1261849907.004:1): initialized
[    2.014900] highmem bounce pool size: 64 pages
[    2.014908] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.016616] VFS: Disk quotas dquot_6.5.2
[    2.016681] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.017319] fuse init (API version 7.12)
[    2.017417] msgmni has been set to 1706
[    2.017652] alg: No test for stdrng (krng)
[    2.017665] io scheduler noop registered
[    2.017668] io scheduler anticipatory registered
[    2.017670] io scheduler deadline registered
[    2.017718] io scheduler cfq registered (default)
[    2.017809] pci 0000:01:00.0: Boot video device
[    2.017925] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.017954] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.018465] ACPI: AC Adapter [AC] (off-line)
[    2.018570] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    2.018994] ACPI: Lid Switch [LID]
[    2.019047] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.019052] ACPI: Power Button [PBTN]
[    2.019105] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.019108] ACPI: Sleep Button [SBTN]
[    2.019593] Marking TSC unstable due to TSC halts in idle
[    2.019619] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    2.019648] processor LNXCPU:00: registered as cooling_device0
[    2.019652] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.030628] thermal LNXTHERM:01: registered as thermal_zone0
[    2.030640] ACPI: Thermal Zone [THM] (68 C)
[    2.030692] isapnp: Scanning for PnP cards...
[    2.320028] ACPI: Battery Slot [BAT0] (battery present)
[    2.320073] ACPI: Battery Slot [BAT1] (battery absent)
[    2.406924] isapnp: No Plug & Play device found
[    2.408148] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.409593] brd: module loaded
[    2.410111] loop: module loaded
[    2.410191] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.410309] ata_piix 0000:00:1f.1: version 2.13
[    2.410322] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    2.410509] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    2.410514] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.410560] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.410639] scsi0 : ata_piix
[    2.410723] scsi1 : ata_piix
[    2.411864] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    2.411868] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    2.412842] Fixed MDIO Bus: probed
[    2.412882] PPP generic driver version 2.4.2
[    2.412975] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.413159] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    2.413164] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    2.413178] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.413182] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.413243] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.417170] ehci_hcd 0000:00:1d.7: debug port 1
[    2.417176] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.417428] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    2.432034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.432135] usb usb1: configuration #1 chosen from 1 choice
[    2.432171] hub 1-0:1.0: USB hub found
[    2.432187] hub 1-0:1.0: 6 ports detected
[    2.432260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.432280] uhci_hcd: USB Universal Host Controller Interface driver
[    2.432306] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.432313] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.432317] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.432352] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.432374] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    2.432465] usb usb2: configuration #1 chosen from 1 choice
[    2.432495] hub 2-0:1.0: USB hub found
[    2.432503] hub 2-0:1.0: 2 ports detected
[    2.432550] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.432557] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.432561] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.432597] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.432618] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    2.432704] usb usb3: configuration #1 chosen from 1 choice
[    2.432734] hub 3-0:1.0: USB hub found
[    2.432741] hub 3-0:1.0: 2 ports detected
[    2.432954] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    2.432959] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.432966] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.432969] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.433007] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.433028] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    2.433116] usb usb4: configuration #1 chosen from 1 choice
[    2.433145] hub 4-0:1.0: USB hub found
[    2.433158] hub 4-0:1.0: 2 ports detected
[    2.433261] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.438085] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.438092] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.438147] mice: PS/2 mouse device common for all mice
[    2.438309] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.438326] rtc0: alarms up to one day, 114 bytes nvram
[    2.438435] device-mapper: uevent: version 1.0.3
[    2.438527] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.438609] device-mapper: multipath: version 1.1.0 loaded
[    2.438612] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.438740] EISA: Probing bus 0 at eisa.0
[    2.438764] EISA: Detected 0 cards.
[    2.438869] cpuidle: using governor ladder
[    2.438964] cpuidle: using governor menu
[    2.439484] TCP cubic registered
[    2.439672] NET: Registered protocol family 10
[    2.440154] lo: Disabled Privacy Extensions
[    2.440491] NET: Registered protocol family 17
[    2.440517] Bluetooth: L2CAP ver 2.13
[    2.440519] Bluetooth: L2CAP socket layer initialized
[    2.440523] Bluetooth: SCO (Voice Link) ver 0.6
[    2.440525] Bluetooth: SCO socket layer initialized
[    2.440560] Bluetooth: RFCOMM TTY layer initialized
[    2.440564] Bluetooth: RFCOMM socket layer initialized
[    2.440566] Bluetooth: RFCOMM ver 1.11
[    2.476091] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.478398] Using IPI No-Shortcut mode
[    2.478464] PM: Resume from disk failed.
[    2.478478] registered taskstats version 1
[    2.478598]   Magic number: 5:135:897
[    2.478679] rtc_cmos 00:06: setting system clock to 2009-12-26 17:51:47 UTC (1261849907)
[    2.478683] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.478685] EDD information not available.
[    2.580595] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A100, max UDMA/33
[    2.596229] ata2.00: configured for UDMA/33
[    2.930737] ata1.00: ATA-7: WDC WD1600BEVE-00UYT0, 01.04A01, max UDMA/100
[    2.930740] ata1.00: 312581808 sectors, multi 8: LBA48 
[    2.944579] ata1.00: configured for UDMA/100
[    2.944726] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVE-0 01.0 PQ: 0 ANSI: 5
[    2.944856] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.944899] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.944953] sd 0:0:0:0: [sda] Write Protect is off
[    2.944957] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.944984] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.945119]  sda: sda1 sda2 <
[    2.950906] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A100 PQ: 0 ANSI: 5
[    2.953562] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.953566] Uniform CD-ROM driver Revision: 3.20
[    2.953650] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.953699] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.971555]  sda5 >
[    2.971807] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.971825] Freeing unused kernel memory: 540k freed
[    2.972261] Write protecting the kernel text: 4568k
[    2.972303] Write protecting the kernel read-only data: 1836k
[    3.138573] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    3.164827] Linux agpgart interface v0.103
[    3.168942] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    3.264769] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    3.270679] ohci1394 0000:02:01.2: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.301447] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/device:1f/input/input5
[    3.301500] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    3.324063] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fafef800-fafeffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.324281] tg3.c:v3.99 (April 20, 2009)
[    3.324302] tg3 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.332085] tg3 0000:02:00.0: PME# disabled
[    3.400570] eth0: Tigon3 [partno(BCM95705A50) rev 3001] (PCI:33MHz:32-bit) MAC address 00:11:43:60:b3:87
[    3.400575] eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.400579] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.400582] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    3.421347] usb 2-2: configuration #1 chosen from 1 choice
[    3.664898] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.080104] usb 3-1: configuration #1 chosen from 1 choice
[    4.104767] usbcore: registered new interface driver hiddev
[    4.124494] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input6
[    4.124598] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    4.156123] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input7
[    4.156224] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    4.156240] usbcore: registered new interface driver usbhid
[    4.156243] usbhid: v2.6:USB HID core driver
[    4.558845] xor: automatically using best checksumming function: pIII_sse
[    4.576019]    pIII_sse  :  4395.000 MB/sec
[    4.576022] xor: using function: pIII_sse (4395.000 MB/sec)
[    4.579787] device-mapper: dm-raid45: initialized v0.2594b
[    4.645354] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[384fc00011b8a0a1]
[    4.750982] EXT4-fs (sda1): barriers enabled
[    4.770009] kjournald2 starting: pid 409, dev sda1:8, commit interval 5 seconds
[    4.770021] EXT4-fs (sda1): delayed allocation enabled
[    4.770025] EXT4-fs: file extents enabled
[    4.773722] EXT4-fs: mballoc enabled
[    4.773739] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.796345] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[    4.796349] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[    4.796352] EXT4-fs: mballoc: 0 generated and it took 0
[    4.796354] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[    6.038846] ISO 9660 Extensions: Microsoft Joliet Level 3
[    6.085927] ISO 9660 Extensions: RRIP_1991A
[    6.395159] aufs 2-standalone.tree-30-20090727
[    6.638677] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   70.470153] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k 
[   72.270286] udev: starting version 147
[   75.168804] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   75.168932] usbcore: registered new interface driver btusb
[   76.991744] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   76.995483] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   77.117206] intel_rng: FWH not detected
[   77.628595] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input8
[   77.652211] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
[   78.037313] dell-wmi: No known WMI GUID found
[   78.180454] lib80211: common routines for IEEE802.11 drivers
[   78.180459] lib80211_crypt: registered algorithm 'NULL'
[   78.436891] parport_pc 00:0b: reported by Plug and Play ACPI
[   78.436940] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   78.959049] ip_tables: (C) 2000-2006 Netfilter Core Team
[   79.016162] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:013f]
[   79.016180] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   79.016183] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   79.016188] yenta_cardbus 0000:02:01.0: TI: mfunc 0x012c1202, devctl 0x64
[   79.108769] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   79.108774] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   79.248551] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0478, PCI irq 11
[   79.248556] yenta_cardbus 0000:02:01.0: Socket status: 30000820
[   79.248561] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   79.248572] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   79.248577] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: clean.
[   79.249061] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   79.249065] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
[   79.249272] yenta_cardbus 0000:02:01.1: CardBus bridge found [1028:013f]
[   79.376590] yenta_cardbus 0000:02:01.1: ISA IRQ mask 0x0478, PCI irq 11
[   79.376596] yenta_cardbus 0000:02:01.1: Socket status: 30000047
[   79.376601] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   79.376610] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   79.376615] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xd000-0xefff: clean.
[   79.377099] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   79.377103] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
[   79.845362] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   79.845368] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   79.845757] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   79.845761] PCI: setting IRQ 5 as level-triggered
[   79.845768] ipw2100 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   79.846504] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   79.846526] ipw2100 0000:02:03.0: firmware: requesting ipw2100-1.3.fw
[   79.884055] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   79.884101] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[   79.976797] ppdev: user-space parallel port driver
[   81.035383] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   81.036403] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   81.036842] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   81.036897] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   81.037423] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   81.048540] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   81.049537] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   81.049975] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   81.050030] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   81.050552] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   81.268618] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   81.268623] Bluetooth: BNEP filters: protocol multicast
[   82.489088] cfg80211: Calling CRDA to update world regulatory domain
[   82.492780] tg3 0000:02:00.0: firmware: requesting tigon/tg3_tso5.bin
[   82.734843] Bridge firewalling registered
[   83.633193] tg3 0000:02:00.0: PME# disabled
[   84.041792] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   84.064671] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   84.404122] cfg80211: World regulatory domain updated:
[   84.404129] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   84.404133] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.404137] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   84.404140] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   84.404143] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.404147] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.668193] ath5k 0000:03:00.0: enabling device (0000 -> 0002)
[   84.668211] ath5k 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   84.668283] ath5k 0000:03:00.0: registered as 'phy0'
[   84.781837] ath: EEPROM regdomain: 0x10
[   84.781840] ath: EEPROM indicates we should expect a direct regpair map
[   84.781844] ath: Country alpha2 being used: CO
[   84.781846] ath: Regpair used: 0x10
[   85.364589] phy0: Selected rate control algorithm 'minstrel'
[   85.365423] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   85.366998] cfg80211: Calling CRDA for country: CO
[   85.369445] cfg80211: Regulatory domain changed to country: CO
[   85.369449] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   85.369453] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   85.369456] 	(5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   85.369460] 	(5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   85.369463] 	(5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   85.499431] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   85.499487] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   85.572362] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   86.356034] intel8x0_measure_ac97_clock: measured 55423 usecs (2670 samples)
[   86.356039] intel8x0: clocking to 48000
[   87.054862] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[   87.054867] tg3: eth0: Flow control is on for TX and on for RX.
[   87.055100] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   91.263308] lp0: using parport0 (interrupt-driven).
[   97.640026] eth0: no IPv6 routers present
[  163.184060] Clocksource tsc unstable (delta = -202297677 ns)
[  251.893245] RPC: Registered udp transport module.
[  251.893250] RPC: Registered tcp transport module.
[  381.012178] svc: failed to register lockdv1 RPC service (errno 97).
[  537.678604] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  537.678609] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  537.678612] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  537.678679] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xfae00000-0xfb3fffff

```

And when I boot from my HD and the wireless is "gone":
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffae000 (usable)
[    0.000000]  BIOS-e820: 000000007ffae000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x7ffae max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FEDA0000 mask FFFFE0000 write-through
[    0.000000]   2 disabled
[    0.000000]   3 disabled
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
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffae000 (usable)
[    0.000000]  modified: 000000007ffae000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37869000 - 37fefb2c
[    0.000000] Allocated new RAMDISK: 008ad000 - 01033b2c
[    0.000000] Move RAMDISK from 0000000037869000 - 0000000037fefb2b to 008ad000 - 01033b2b
[    0.000000] ACPI: RSDP 000fdf00 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 7fff0000 00030 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: FACP 7fff0400 00074 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: DSDT 7fff0c00 02E30 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 7ffff800 00040
[    0.000000] ACPI: ASF! 7fff0800 0005B (v16 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: BOOT 7fff07c0 00028 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac198]              BRK ==> [00008a9000 - 00008ac198]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0001033b2c]      NEW RAMDISK ==> [00008ad000 - 0001033b2c]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffae
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffae
[    0.000000] On node 0 totalpages: 524105
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1034000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294560 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7eda0000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c203e000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520009
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=e177426a-bc38-41a4-9635-536ad12e8038 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10484120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffae)
[    0.000000] Memory: 2052412k/2096824k available (4566k kernel code, 43108k reserved, 2142k data, 540k init, 1187520k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1694.433 MHz processor.
[    0.001515] Console: colour VGA+ 80x25
[    0.001522] console [tty0] enabled
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 3388.86 BogoMIPS (lpj=6777732)
[    0.004045] Security Framework initialized
[    0.004085] AppArmor: AppArmor initialized
[    0.004096] Mount-cache hash table entries: 512
[    0.004290] Initializing cgroup subsys ns
[    0.004297] Initializing cgroup subsys cpuacct
[    0.004302] Initializing cgroup subsys memory
[    0.004313] Initializing cgroup subsys freezer
[    0.004316] Initializing cgroup subsys net_cls
[    0.004339] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004342] CPU: L2 cache: 2048K
[    0.004348] mce: CPU supports 5 MCE banks
[    0.004358] ------------[ cut here ]------------
[    0.004376] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()
[    0.004379] Hardware name: Precision M60                   
[    0.004382] Modules linked in:
[    0.004388] Pid: 0, comm: swapper Not tainted 2.6.31-16-generic #53-Ubuntu
[    0.004391] Call Trace:
[    0.004405]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
[    0.004410]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
[    0.004414]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
[    0.004419]  [<c01451d5>] warn_slowpath_null+0x15/0x20
[    0.004424]  [<c011d7e3>] native_apic_write_dummy+0x33/0x40
[    0.004433]  [<c011278c>] intel_init_thermal+0xac/0x1a0
[    0.004437]  [<c0111dbb>] mce_intel_feature_init+0xb/0x60
[    0.004442]  [<c010fcf0>] mce_cpu_features+0x10/0x40
[    0.004450]  [<c056b29c>] mcheck_init+0x14a/0x188
[    0.004455]  [<c05696d8>] ? init_hypervisor+0xb/0x2c
[    0.004459]  [<c0569690>] identify_cpu+0x20e/0x21d
[    0.004468]  [<c0795732>] identify_boot_cpu+0xd/0x23
[    0.004472]  [<c07958c8>] check_bugs+0xb/0xe9
[    0.004480]  [<c078e8c3>] start_kernel+0x2dc/0x2ec
[    0.004485]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
[    0.004490]  [<c078e07c>] i386_start_kernel+0x7c/0x83
[    0.004501] ---[ end trace a7919e7f17c0a725 ]---
[    0.004505] CPU0: Thermal monitoring enabled (TM1)
[    0.004520] Performance Counters: 
[    0.004524] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.004526] no hardware sampling interrupt available.
[    0.004529] p6 PMU driver.
[    0.004535] ... version:                 0
[    0.004537] ... bit width:               32
[    0.004540] ... generic counters:        2
[    0.004542] ... value mask:              00000000ffffffff
[    0.004544] ... max period:              000000007fffffff
[    0.004547] ... fixed-purpose counters:  0
[    0.004549] ... counter mask:            0000000000000003
[    0.004555] Checking 'hlt' instruction... OK.
[    0.020931] SMP alternatives: switching to UP code
[    0.027967] Freeing SMP alternatives: 19k freed
[    0.027978] ACPI: Core revision 20090521
[    0.033350] ACPI: setting ELCR to 0200 (from 0800)
[    0.034421] weird, boot CPU (#0) not listed by the BIOS.
[    0.034424] SMP motherboard not detected.
[    0.034427] Local APIC not detected. Using dummy APIC emulation.
[    0.034429] SMP disabled
[    0.034599] Brought up 1 CPUs
[    0.034602] Total of 1 processors activated (3388.86 BogoMIPS).
[    0.034616] CPU0 attaching NULL sched-domain.
[    0.034869] Booting paravirtualized kernel on bare hardware
[    0.035106] regulator: core version 0.5
[    0.035135] Time: 18:16:43  Date: 12/26/09
[    0.035192] NET: Registered protocol family 16
[    0.035342] EISA bus registered
[    0.035359] ACPI: bus type pci registered
[    0.070527] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    0.070530] PCI: Using configuration type 1 for base access
[    0.071706] bio: create slab <bio-0> at 0
[    0.072261] ACPI: EC: Look up EC in DSDT
[    0.082261] ACPI: Interpreter enabled
[    0.082273] ACPI: (supports S0 S1 S3 S4 S5)
[    0.082297] ACPI: Using PIC for interrupt routing
[    0.101786] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.106591] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.106646] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.106762] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.106816] pci 0000:00:1d.1: reg 20 io port: [0xbf40-0xbf5f]
[    0.106868] pci 0000:00:1d.2: reg 20 io port: [0xbf20-0xbf3f]
[    0.106929] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4fffc00-0xf4ffffff]
[    0.106987] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.106993] pci 0000:00:1d.7: PME# disabled
[    0.107082] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.107086] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.107111] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.107118] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.107126] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.107133] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.107141] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.107149] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.107192] pci 0000:00:1f.5: reg 10 io port: [0xb800-0xb8ff]
[    0.107199] pci 0000:00:1f.5: reg 14 io port: [0xbc40-0xbc7f]
[    0.107206] pci 0000:00:1f.5: reg 18 32bit mmio: [0xf4fff800-0xf4fff9ff]
[    0.107213] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xf4fff400-0xf4fff4ff]
[    0.107243] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.107248] pci 0000:00:1f.5: PME# disabled
[    0.107285] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.107292] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
[    0.107310] pci 0000:01:00.0: reg 30 32bit mmio: [0x80000000-0x8001ffff]
[    0.107360] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.107364] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.107368] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.107423] pci 0000:02:00.0: reg 10 64bit mmio: [0xfaff0000-0xfaffffff]
[    0.107476] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.107480] pci 0000:02:00.0: PME# disabled
[    0.107516] pci 0000:02:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.107535] pci 0000:02:01.0: supports D1 D2
[    0.107537] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.107542] pci 0000:02:01.0: PME# disabled
[    0.107576] pci 0000:02:01.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.107595] pci 0000:02:01.1: supports D1 D2
[    0.107598] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.107603] pci 0000:02:01.1: PME# disabled
[    0.107637] pci 0000:02:01.2: reg 10 32bit mmio: [0xfafef800-0xfafeffff]
[    0.107644] pci 0000:02:01.2: reg 14 32bit mmio: [0xfafe8000-0xfafebfff]
[    0.107684] pci 0000:02:01.2: supports D1 D2
[    0.107687] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot
[    0.107692] pci 0000:02:01.2: PME# disabled
[    0.107722] pci 0000:02:01.3: reg 10 io port: [0xecf8-0xecff]
[    0.107800] pci 0000:02:03.0: reg 10 32bit mmio: [0xfafee000-0xfafeefff]
[    0.107879] pci 0000:00:1e.0: transparent bridge
[    0.107884] pci 0000:00:1e.0: bridge io port: [0xd000-0xefff]
[    0.107889] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6000000-0xfbffffff]
[    0.107932] pci_bus 0000:00: on NUMA node 0
[    0.107938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.108186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.108242] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.126535] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.126661] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.126784] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.126907] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.127012] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.127139] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.127361] SCSI subsystem initialized
[    0.127414] libata version 3.00 loaded.
[    0.127492] usbcore: registered new interface driver usbfs
[    0.127516] usbcore: registered new interface driver hub
[    0.127545] usbcore: registered new device driver usb
[    0.127686] ACPI: WMI: Mapper loaded
[    0.127688] PCI: Using ACPI for IRQ routing
[    0.128036] Bluetooth: Core ver 2.15
[    0.128065] NET: Registered protocol family 31
[    0.128068] Bluetooth: HCI device and connection manager initialized
[    0.128072] Bluetooth: HCI socket layer initialized
[    0.128074] NetLabel: Initializing
[    0.128076] NetLabel:  domain hash size = 128
[    0.128078] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.128094] NetLabel:  unlabeled traffic allowed by default
[    0.130245] pnp: PnP ACPI init
[    0.130265] ACPI: bus type pnp registered
[    0.140111] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.140116] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.140188] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.140193] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.140197] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.153720] pnp: PnP ACPI: found 12 devices
[    0.153723] ACPI: ACPI bus type pnp unregistered
[    0.153729] PnPBIOS: Disabled by ACPI PNP
[    0.153742] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.153746] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.153750] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.153753] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.153757] system 00:00: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.153761] system 00:00: iomem range 0x7fff0000-0x7fffffff has been reserved
[    0.153765] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.153768] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.153776] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.153783] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.153787] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.153790] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.153794] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.153801] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.188491] AppArmor: AppArmor Filesystem Enabled
[    0.188504] pci 0000:01:00.0: BAR 6: no parent found for of device [0x80000000-0x8001ffff]
[    0.188532] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.188536] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.188541] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.188545] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.188559] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.188562] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.188567] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.188572] pci 0000:02:01.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.188578] pci 0000:02:01.0:   MEM window: 0x8c000000-0x8fffffff
[    0.188583] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
[    0.188586] pci 0000:02:01.1:   IO window: 0x00d800-0x00d8ff
[    0.188591] pci 0000:02:01.1:   IO window: 0x00dc00-0x00dcff
[    0.188596] pci 0000:02:01.1:   PREFETCH window: 0x84000000-0x87ffffff
[    0.188601] pci 0000:02:01.1:   MEM window: 0x90000000-0x93ffffff
[    0.188606] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.188610] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.188616] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.188621] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x87ffffff
[    0.188638] pci 0000:00:1e.0: setting latency timer to 64
[    0.188646] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.188820] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.188823] PCI: setting IRQ 11 as level-triggered
[    0.188828] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.188841] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.188848] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.188851] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.188854] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.188858] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.188861] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.188865] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.188868] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xfbffffff]
[    0.188871] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x87ffffff]
[    0.188874] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.188878] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.188881] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.188884] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.188887] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.188891] pci_bus 0000:03: resource 3 mem: [0x8c000000-0x8fffffff]
[    0.188894] pci_bus 0000:07: resource 0 io:  [0xd800-0xd8ff]
[    0.188897] pci_bus 0000:07: resource 1 io:  [0xdc00-0xdcff]
[    0.188901] pci_bus 0000:07: resource 2 pref mem [0x84000000-0x87ffffff]
[    0.188904] pci_bus 0000:07: resource 3 mem: [0x90000000-0x93ffffff]
[    0.188946] NET: Registered protocol family 2
[    0.189051] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.189444] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.190872] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.191806] TCP: Hash tables configured (established 131072 bind 65536)
[    0.191810] TCP reno registered
[    0.191951] NET: Registered protocol family 1
[    0.192091] Trying to unpack rootfs image as initramfs...
[    0.452352] Freeing initrd memory: 7706k freed
[    0.463323] Simple Boot Flag at 0x79 set to 0x1
[    0.463450] cpufreq-nforce2: No nForce2 chipset.
[    0.463483] Scanning for low memory corruption every 60 seconds
[    0.463647] audit: initializing netlink socket (disabled)
[    0.463684] type=2000 audit(1261851403.460:1): initialized
[    0.474236] highmem bounce pool size: 64 pages
[    0.474244] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.475926] VFS: Disk quotas dquot_6.5.2
[    0.475991] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.476665] fuse init (API version 7.12)
[    0.476760] msgmni has been set to 1706
[    0.476998] alg: No test for stdrng (krng)
[    0.477012] io scheduler noop registered
[    0.477015] io scheduler anticipatory registered
[    0.477017] io scheduler deadline registered
[    0.477066] io scheduler cfq registered (default)
[    0.477156] pci 0000:01:00.0: Boot video device
[    0.477273] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.477300] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.477819] ACPI: AC Adapter [AC] (off-line)
[    0.477924] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.478417] ACPI: Lid Switch [LID]
[    0.478470] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.478475] ACPI: Power Button [PBTN]
[    0.478527] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.478530] ACPI: Sleep Button [SBTN]
[    0.479016] Marking TSC unstable due to TSC halts in idle
[    0.479041] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    0.479070] processor LNXCPU:00: registered as cooling_device0
[    0.479074] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.480057] Switched to high resolution mode on CPU 0
[    0.490087] thermal LNXTHERM:01: registered as thermal_zone0
[    0.490097] ACPI: Thermal Zone [THM] (57 C)
[    0.500200] isapnp: Scanning for PnP cards...
[    0.822565] ACPI: Battery Slot [BAT0] (battery present)
[    0.822610] ACPI: Battery Slot [BAT1] (battery absent)
[    0.866083] isapnp: No Plug & Play device found
[    0.867283] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.868749] brd: module loaded
[    0.869263] loop: module loaded
[    0.869341] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.869460] ata_piix 0000:00:1f.1: version 2.13
[    0.869473] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.869656] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.869662] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.869709] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.869789] scsi0 : ata_piix
[    0.869876] scsi1 : ata_piix
[    0.870962] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.870966] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.871905] Fixed MDIO Bus: probed
[    0.871945] PPP generic driver version 2.4.2
[    0.872306] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.872490] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.872494] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.872509] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.872513] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.872568] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.876485] ehci_hcd 0000:00:1d.7: debug port 1
[    0.876492] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.876501] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    0.892036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.892136] usb usb1: configuration #1 chosen from 1 choice
[    0.892178] hub 1-0:1.0: USB hub found
[    0.892187] hub 1-0:1.0: 6 ports detected
[    0.892260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.892280] uhci_hcd: USB Universal Host Controller Interface driver
[    0.892305] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.892312] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.892316] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.892358] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.892379] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    0.892470] usb usb2: configuration #1 chosen from 1 choice
[    0.892501] hub 2-0:1.0: USB hub found
[    0.892508] hub 2-0:1.0: 2 ports detected
[    0.892555] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.892562] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.892565] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.892596] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.892617] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    0.892703] usb usb3: configuration #1 chosen from 1 choice
[    0.892732] hub 3-0:1.0: USB hub found
[    0.892739] hub 3-0:1.0: 2 ports detected
[    0.892950] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.892955] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.892961] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.892965] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.893009] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.893030] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    0.893118] usb usb4: configuration #1 chosen from 1 choice
[    0.893147] hub 4-0:1.0: USB hub found
[    0.893155] hub 4-0:1.0: 2 ports detected
[    0.893259] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.898182] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.898188] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.898244] mice: PS/2 mouse device common for all mice
[    0.898407] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.898424] rtc0: alarms up to one day, 114 bytes nvram
[    0.898537] device-mapper: uevent: version 1.0.3
[    0.898630] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.898725] device-mapper: multipath: version 1.1.0 loaded
[    0.898728] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.898855] EISA: Probing bus 0 at eisa.0
[    0.898879] EISA: Detected 0 cards.
[    0.898983] cpuidle: using governor ladder
[    0.899078] cpuidle: using governor menu
[    0.899596] TCP cubic registered
[    0.899779] NET: Registered protocol family 10
[    0.900284] lo: Disabled Privacy Extensions
[    0.900622] NET: Registered protocol family 17
[    0.900640] Bluetooth: L2CAP ver 2.13
[    0.900642] Bluetooth: L2CAP socket layer initialized
[    0.900645] Bluetooth: SCO (Voice Link) ver 0.6
[    0.900647] Bluetooth: SCO socket layer initialized
[    0.900681] Bluetooth: RFCOMM TTY layer initialized
[    0.900685] Bluetooth: RFCOMM socket layer initialized
[    0.900687] Bluetooth: RFCOMM ver 1.11
[    0.938038] Using IPI No-Shortcut mode
[    0.938106] PM: Resume from disk failed.
[    0.938120] registered taskstats version 1
[    0.938234]   Magic number: 5:620:292
[    0.938252] tty tty25: hash matches
[    0.938314] rtc_cmos 00:06: setting system clock to 2009-12-26 18:16:44 UTC (1261851404)
[    0.938318] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.938320] EDD information not available.
[    0.938431] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.036595] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A100, max UDMA/33
[    1.052229] ata2.00: configured for UDMA/33
[    1.089900] ata1.00: ATA-7: WDC WD1600BEVE-00UYT0, 01.04A01, max UDMA/100
[    1.089903] ata1.00: 312581808 sectors, multi 8: LBA48 
[    1.104742] ata1.00: configured for UDMA/100
[    1.104890] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVE-0 01.0 PQ: 0 ANSI: 5
[    1.105018] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.105061] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.105115] sd 0:0:0:0: [sda] Write Protect is off
[    1.105118] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.105146] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.105284]  sda: sda1 sda2 <
[    1.110590] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A100 PQ: 0 ANSI: 5
[    1.123686] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.123690] Uniform CD-ROM driver Revision: 3.20
[    1.123782] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.123832] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.141821]  sda5 >
[    1.142077] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.142095] Freeing unused kernel memory: 540k freed
[    1.142502] Write protecting the kernel text: 4568k
[    1.142544] Write protecting the kernel read-only data: 1836k
[    1.313930] Linux agpgart interface v0.103
[    1.318049] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    1.330549] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/device:1f/input/input5
[    1.330598] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.375473] tg3.c:v3.99 (April 20, 2009)
[    1.375499] tg3 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.389122] tg3 0000:02:00.0: PME# disabled
[    1.491731] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    1.528145] eth0: Tigon3 [partno(BCM95705A50) rev 3001] (PCI:33MHz:32-bit) MAC address 00:11:43:60:b3:87
[    1.528151] eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.528155] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.528158] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    1.528546] ohci1394 0000:02:01.2: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.584059] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fafef800-fafeffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.662668] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    1.900124] usb 2-2: configuration #1 chosen from 1 choice
[    2.336025] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.684104] usb 3-1: configuration #1 chosen from 1 choice
[    2.701201] usbcore: registered new interface driver hiddev
[    2.703830] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input6
[    2.703938] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    2.708460] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input7
[    2.708559] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    2.708573] usbcore: registered new interface driver usbhid
[    2.708577] usbhid: v2.6:USB HID core driver
[    2.849239] xor: automatically using best checksumming function: pIII_sse
[    2.868019]    pIII_sse  :  4394.000 MB/sec
[    2.868022] xor: using function: pIII_sse (4394.000 MB/sec)
[    2.868160] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[384fc00011b8a0a1]
[    2.872156] device-mapper: dm-raid45: initialized v0.2594b
[    3.225664] PM: Starting manual resume from disk
[    3.225669] PM: Resume from partition 8:5
[    3.225671] PM: Checking hibernation image.
[    3.225912] PM: Resume from disk failed.
[    3.254513] EXT4-fs (sda1): barriers enabled
[    3.273538] kjournald2 starting: pid 372, dev sda1:8, commit interval 5 seconds
[    3.273550] EXT4-fs (sda1): delayed allocation enabled
[    3.273554] EXT4-fs: file extents enabled
[    3.277270] EXT4-fs: mballoc enabled
[    3.277288] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.010987] type=1505 audit(1261851407.571:2): operation="profile_load" pid=395 name=/usr/share/gdm/guest-session/Xsession
[    4.013833] type=1505 audit(1261851407.573:3): operation="profile_load" pid=396 name=/sbin/dhclient3
[    4.014574] type=1505 audit(1261851407.573:4): operation="profile_load" pid=396 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.014977] type=1505 audit(1261851407.573:5): operation="profile_load" pid=396 name=/usr/lib/connman/scripts/dhclient-script
[    4.087427] type=1505 audit(1261851407.646:6): operation="profile_load" pid=397 name=/usr/bin/evince
[    4.099689] type=1505 audit(1261851407.657:7): operation="profile_load" pid=397 name=/usr/bin/evince-previewer
[    4.106864] type=1505 audit(1261851407.665:8): operation="profile_load" pid=397 name=/usr/bin/evince-thumbnailer
[    4.137056] type=1505 audit(1261851407.697:9): operation="profile_load" pid=399 name=/usr/lib/cups/backend/cups-pdf
[    4.137937] type=1505 audit(1261851407.697:10): operation="profile_load" pid=399 name=/usr/sbin/cupsd
[    5.415866] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k 
[    5.810500] EXT4-fs (sda1): internal journal on sda1:8
[    7.325598] udev: starting version 147
[    8.970822] udev: renamed network interface eth0 to eth1
[   10.921369] nvidia: module license 'NVIDIA' taints kernel.
[   10.921377] Disabling lock debugging due to kernel taint
[   11.180027] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.180252] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
[   13.018979] tg3 0000:02:00.0: firmware: requesting tigon/tg3_tso5.bin
[   13.227417] tg3 0000:02:00.0: PME# disabled
[   13.560554] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   14.855795] __ratelimit: 6 callbacks suppressed
[   14.855801] type=1505 audit(1261851418.413:13): operation="profile_replace" pid=986 name=/usr/share/gdm/guest-session/Xsession
[   14.862711] type=1505 audit(1261851418.421:14): operation="profile_replace" pid=989 name=/sbin/dhclient3
[   14.863458] type=1505 audit(1261851418.421:15): operation="profile_replace" pid=989 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.863866] type=1505 audit(1261851418.421:16): operation="profile_replace" pid=989 name=/usr/lib/connman/scripts/dhclient-script
[   14.869800] type=1505 audit(1261851418.429:17): operation="profile_replace" pid=990 name=/usr/bin/evince
[   14.900158] type=1505 audit(1261851418.461:18): operation="profile_replace" pid=990 name=/usr/bin/evince-previewer
[   14.907306] type=1505 audit(1261851418.465:19): operation="profile_replace" pid=990 name=/usr/bin/evince-thumbnailer
[   14.917757] type=1505 audit(1261851418.477:20): operation="profile_replace" pid=995 name=/usr/lib/cups/backend/cups-pdf
[   14.918638] type=1505 audit(1261851418.477:21): operation="profile_replace" pid=995 name=/usr/sbin/cupsd
[   14.921102] type=1505 audit(1261851418.481:22): operation="profile_replace" pid=996 name=/usr/sbin/ntpd
[   16.691041] tg3: eth1: Link is up at 1000 Mbps, full duplex.
[   16.691046] tg3: eth1: Flow control is on for TX and on for RX.
[   16.691277] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   19.783566] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   19.783583] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   19.783615] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   26.928026] eth1: no IPv6 routers present
[   28.188785] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   28.188790] vboxdrv: Successfully done.
[   28.188792] vboxdrv: Found 1 processor cores.
[   28.188912] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   28.188915] vboxdrv: Successfully loaded version 3.0.8_OSE (interface 0x000e0000).
[   94.188043] Clocksource tsc unstable (delta = -161504008 ns)
[  218.160055] spurious 8259A interrupt: IRQ7.

```

So can anyone tell me how I can get it to recognize my cardbus adapter for wireless again?

---

### Post by FuManShu on 2009-12-26
Something very similar just happened to me, but I did not make any unusual changes to my computer.  One minute I had Wireless, then rebooted, and then my Wireless disappeared.  However, upon wiring up I found that there was a long list of updates available, most of which I already had installed.  The 2.6.31-16 kernel (which I was already using) was among them.  I simply reinstalled the updates and BAM! WiFi was back.  I have no real good explanation for this but this is how it worked.  Wire up and check to see if you have any redundant updates.

---

### Post by Gemu on 2010-01-02
> **sot3 said:**
> Yesterday I booted to a command prompt to fix a problem with my nvidia driver on my Dell Precision M60 laptop, and while there I needed to connect with a wire to download some files.  When I booted back to gdm, I found that the network manager no longer has any "Enable Wireless" option below "Enable Networking" on the dropdown menu.  I doubt that my video driver activities impacted network connectivity, but I'm sure that other updates had been installed since my last reboot, too.  On further investigation, I've found that wlan0 no longer exists, and in fact it no longer seems to recognize my cardbus D-Link WNA-2330 wireless adapter, or maybe it's just not initializing it properly because the power light doesn't even come on anymore.  It does recognize the internal 802.11b wireless adapter that I've had disabled via BIOS ever since I started using the D-Link, but the only reason I mention that is that you're going to see it listed in the info I've provided below; beyond that it does not interest me.  Now that I look closer at dmesg, I don't see any mention of cardbus or pcmcia at all anymore!




 

Interestingly enough, I booted from my 9.10 live CD and the D-Link comes right up, lights come on and the OS uses it just fine.  But then I boot from HD and there's not even any mention of "ath5k" in the logs anymore.  SO I gather something has been damaged or disabled in my install, but what?  I've tried replacing network manager with WICD and got the same results: no wireless interface or wireless options are displayed.

No sign of wlan0:
```
$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

vboxnet0  no wireless extensions.

$ ifconfig 
eth1      Link encap:Ethernet  HWaddr 00:11:43:60:b3:87  
          inet addr:192.168.0.250  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe60:b387/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2639789 (2.6 MB)  TX bytes:525851 (525.8 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2840 (2.8 KB)  TX bytes:2840 (2.8 KB)

```

And the adapter isn't recognized either (again, the Intel Pro/Wireless 2100 is the built-in adapter that I do not use, have never used, and do not wish to use)
```

$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:11:43:60:b3:87
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5705-v3.11 ip=192.168.0.250 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=34 mingnt=2
       resources: memory:fafee000-fafeefff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


```

I found that lsmod has several references to "ath5k" when I boot from live CD, but there are none when I boot from disk:
```
$ lsmod
Module                  Size  Used by
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
nvidia               7092040  36 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
tg3                   109600  0 
video                  19380  0 
output                  2780  1 video
intel_agp              27484  1 
agpgart                34988  2 nvidia,intel_agp

```


Even lspci doesn't mention it.  Booting from disk, I get this:
```
$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV31 [Quadro FX Go700] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```

But when I boot from live CD I get the same thing plus one additional line:
```
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```

Lastly, here is my dmesg output from both a live CD boot and an HD boot where the D-Link (atheros) card is nowhere to be found.

My liveCD boot (where the wireless is fine):
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffae000 (usable)
[    0.000000]  BIOS-e820: 000000007ffae000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x7ffae max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FEDA0000 mask FFFFE0000 write-through
[    0.000000]   2 disabled
[    0.000000]   3 disabled
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
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffae000 (usable)
[    0.000000]  modified: 000000007ffae000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 7fa02000 - 7ff7f098
[    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
[    0.000000] Move RAMDISK from 000000007fa02000 - 000000007ff7f097 to 008ad000 - 00e2a097
[    0.000000] ACPI: RSDP 000fdf00 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 7fff0000 00030 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: FACP 7fff0400 00074 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: DSDT 7fff0c00 02E30 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 7ffff800 00040
[    0.000000] ACPI: ASF! 7fff0800 0005B (v16 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: BOOT 7fff07c0 00028 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac198]              BRK ==> [00008a9000 - 00008ac198]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffae
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffae
[    0.000000] On node 0 totalpages: 524105
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294560 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7eda0000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c200a000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520009
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10484120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffae)
[    0.000000] Memory: 2054544k/2096824k available (4565k kernel code, 41024k reserved, 2143k data, 540k init, 1187520k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1694.554 MHz processor.
[    0.001517] Console: colour VGA+ 80x25
[    0.001522] console [tty0] enabled
[    0.001582] Calibrating delay loop (skipped), value calculated using timer frequency.. 3389.10 BogoMIPS (lpj=6778216)
[    0.001614] Security Framework initialized
[    0.001655] AppArmor: AppArmor initialized
[    0.001666] Mount-cache hash table entries: 512
[    0.001863] Initializing cgroup subsys ns
[    0.001873] Initializing cgroup subsys cpuacct
[    0.001878] Initializing cgroup subsys memory
[    0.001890] Initializing cgroup subsys freezer
[    0.001893] Initializing cgroup subsys net_cls
[    0.001914] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001917] CPU: L2 cache: 2048K
[    0.001923] mce: CPU supports 5 MCE banks
[    0.001934] ------------[ cut here ]------------
[    0.001950] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()
[    0.001954] Hardware name: Precision M60                   
[    0.001957] Modules linked in:
[    0.001962] Pid: 0, comm: swapper Not tainted 2.6.31-14-generic #48-Ubuntu
[    0.001966] Call Trace:
[    0.001979]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
[    0.001984]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
[    0.001989]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
[    0.001994]  [<c01451d5>] warn_slowpath_null+0x15/0x20
[    0.001998]  [<c011d7e3>] native_apic_write_dummy+0x33/0x40
[    0.002007]  [<c011278c>] intel_init_thermal+0xac/0x1a0
[    0.002012]  [<c0111dbb>] mce_intel_feature_init+0xb/0x60
[    0.002016]  [<c010fcf0>] mce_cpu_features+0x10/0x40
[    0.002025]  [<c056ac3c>] mcheck_init+0x14a/0x188
[    0.002029]  [<c0569078>] ? init_hypervisor+0xb/0x2c
[    0.002034]  [<c0569030>] identify_cpu+0x20e/0x21d
[    0.002042]  [<c0795732>] identify_boot_cpu+0xd/0x23
[    0.002046]  [<c07958c8>] check_bugs+0xb/0xe9
[    0.002054]  [<c078e8c3>] start_kernel+0x2dc/0x2ec
[    0.002059]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
[    0.002064]  [<c078e07c>] i386_start_kernel+0x7c/0x83
[    0.002076] ---[ end trace a7919e7f17c0a725 ]---
[    0.002079] CPU0: Thermal monitoring enabled (TM1)
[    0.002093] Performance Counters: 
[    0.002097] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.002100] no hardware sampling interrupt available.
[    0.002102] p6 PMU driver.
[    0.002109] ... version:                 0
[    0.002111] ... bit width:               32
[    0.002113] ... generic counters:        2
[    0.002115] ... value mask:              00000000ffffffff
[    0.002118] ... max period:              000000007fffffff
[    0.002120] ... fixed-purpose counters:  0
[    0.002122] ... counter mask:            0000000000000003
[    0.002129] Checking 'hlt' instruction... OK.
[    0.016931] SMP alternatives: switching to UP code
[    0.024016] Freeing SMP alternatives: 19k freed
[    0.024027] ACPI: Core revision 20090521
[    0.029395] ACPI: setting ELCR to 0200 (from 0800)
[    0.031750] weird, boot CPU (#0) not listed by the BIOS.
[    0.031752] SMP motherboard not detected.
[    0.031755] Local APIC not detected. Using dummy APIC emulation.
[    0.031757] SMP disabled
[    0.031924] Brought up 1 CPUs
[    0.031927] Total of 1 processors activated (3389.10 BogoMIPS).
[    0.031940] CPU0 attaching NULL sched-domain.
[    0.032204] Booting paravirtualized kernel on bare hardware
[    0.032441] regulator: core version 0.5
[    0.032469] Time: 17:51:45  Date: 12/26/09
[    0.032527] NET: Registered protocol family 16
[    0.032681] EISA bus registered
[    0.032697] ACPI: bus type pci registered
[    0.066485] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    0.066488] PCI: Using configuration type 1 for base access
[    0.067655] bio: create slab <bio-0> at 0
[    0.068213] ACPI: EC: Look up EC in DSDT
[    0.077837] ACPI: Interpreter enabled
[    0.077848] ACPI: (supports S0 S1 S3 S4 S5)
[    0.077873] ACPI: Using PIC for interrupt routing
[    0.097627] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.102423] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.102480] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.102596] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.102649] pci 0000:00:1d.1: reg 20 io port: [0xbf40-0xbf5f]
[    0.102702] pci 0000:00:1d.2: reg 20 io port: [0xbf20-0xbf3f]
[    0.102763] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4fffc00-0xf4ffffff]
[    0.102821] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.102827] pci 0000:00:1d.7: PME# disabled
[    0.102915] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.102920] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.102944] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.102952] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.102959] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.102967] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.102974] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.102982] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.103025] pci 0000:00:1f.5: reg 10 io port: [0xb800-0xb8ff]
[    0.103033] pci 0000:00:1f.5: reg 14 io port: [0xbc40-0xbc7f]
[    0.103040] pci 0000:00:1f.5: reg 18 32bit mmio: [0xf4fff800-0xf4fff9ff]
[    0.103047] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xf4fff400-0xf4fff4ff]
[    0.103077] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.103081] pci 0000:00:1f.5: PME# disabled
[    0.103118] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.103124] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
[    0.103143] pci 0000:01:00.0: reg 30 32bit mmio: [0x80000000-0x8001ffff]
[    0.103192] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.103196] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.103201] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.103256] pci 0000:02:00.0: reg 10 64bit mmio: [0xfaff0000-0xfaffffff]
[    0.103309] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.103314] pci 0000:02:00.0: PME# disabled
[    0.103349] pci 0000:02:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.103368] pci 0000:02:01.0: supports D1 D2
[    0.103371] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.103376] pci 0000:02:01.0: PME# disabled
[    0.103409] pci 0000:02:01.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.103428] pci 0000:02:01.1: supports D1 D2
[    0.103431] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.103436] pci 0000:02:01.1: PME# disabled
[    0.103470] pci 0000:02:01.2: reg 10 32bit mmio: [0xfafef800-0xfafeffff]
[    0.103478] pci 0000:02:01.2: reg 14 32bit mmio: [0xfafe8000-0xfafebfff]
[    0.103518] pci 0000:02:01.2: supports D1 D2
[    0.103520] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot
[    0.103525] pci 0000:02:01.2: PME# disabled
[    0.103555] pci 0000:02:01.3: reg 10 io port: [0xecf8-0xecff]
[    0.103633] pci 0000:02:03.0: reg 10 32bit mmio: [0xfafee000-0xfafeefff]
[    0.103713] pci 0000:00:1e.0: transparent bridge
[    0.103718] pci 0000:00:1e.0: bridge io port: [0xd000-0xefff]
[    0.103723] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6000000-0xfbffffff]
[    0.103766] pci_bus 0000:00: on NUMA node 0
[    0.103771] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.104018] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.104075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.122589] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.122717] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.122840] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.122964] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.123069] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.123198] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.123419] SCSI subsystem initialized
[    0.123472] libata version 3.00 loaded.
[    0.123549] usbcore: registered new interface driver usbfs
[    0.123572] usbcore: registered new interface driver hub
[    0.123601] usbcore: registered new device driver usb
[    0.123743] ACPI: WMI: Mapper loaded
[    0.123745] PCI: Using ACPI for IRQ routing
[    0.124087] Bluetooth: Core ver 2.15
[    0.124117] NET: Registered protocol family 31
[    0.124119] Bluetooth: HCI device and connection manager initialized
[    0.124123] Bluetooth: HCI socket layer initialized
[    0.124125] NetLabel: Initializing
[    0.124127] NetLabel:  domain hash size = 128
[    0.124129] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.124146] NetLabel:  unlabeled traffic allowed by default
[    0.126268] pnp: PnP ACPI init
[    0.126291] ACPI: bus type pnp registered
[    0.136109] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.136114] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.136186] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.136191] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.136195] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.149746] pnp: PnP ACPI: found 12 devices
[    0.149749] ACPI: ACPI bus type pnp unregistered
[    0.149755] PnPBIOS: Disabled by ACPI PNP
[    0.149769] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.149773] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.149777] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.149781] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.149784] system 00:00: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.149788] system 00:00: iomem range 0x7fff0000-0x7fffffff has been reserved
[    0.149792] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.149796] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.149803] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.149810] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.149814] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.149818] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.149821] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.149829] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.184513] AppArmor: AppArmor Filesystem Enabled
[    0.184525] pci 0000:01:00.0: BAR 6: no parent found for of device [0x80000000-0x8001ffff]
[    0.184552] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.184556] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.184561] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.184566] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.184579] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.184582] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.184588] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.184593] pci 0000:02:01.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.184598] pci 0000:02:01.0:   MEM window: 0x8c000000-0x8fffffff
[    0.184603] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
[    0.184606] pci 0000:02:01.1:   IO window: 0x00d800-0x00d8ff
[    0.184611] pci 0000:02:01.1:   IO window: 0x00dc00-0x00dcff
[    0.184616] pci 0000:02:01.1:   PREFETCH window: 0x84000000-0x87ffffff
[    0.184622] pci 0000:02:01.1:   MEM window: 0x90000000-0x93ffffff
[    0.184627] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.184631] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.184637] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.184642] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x87ffffff
[    0.184658] pci 0000:00:1e.0: setting latency timer to 64
[    0.184666] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.184840] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.184843] PCI: setting IRQ 11 as level-triggered
[    0.184849] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.184862] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.184868] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.184872] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.184875] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.184879] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.184882] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.184885] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.184889] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xfbffffff]
[    0.184892] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x87ffffff]
[    0.184895] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.184899] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.184902] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.184905] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.184909] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.184912] pci_bus 0000:03: resource 3 mem: [0x8c000000-0x8fffffff]
[    0.184915] pci_bus 0000:07: resource 0 io:  [0xd800-0xd8ff]
[    0.184919] pci_bus 0000:07: resource 1 io:  [0xdc00-0xdcff]
[    0.184922] pci_bus 0000:07: resource 2 pref mem [0x84000000-0x87ffffff]
[    0.184925] pci_bus 0000:07: resource 3 mem: [0x90000000-0x93ffffff]
[    0.184965] NET: Registered protocol family 2
[    0.185071] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.185463] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.186898] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.187825] TCP: Hash tables configured (established 131072 bind 65536)
[    0.187829] TCP reno registered
[    0.188014] NET: Registered protocol family 1
[    0.188119] Trying to unpack rootfs image as initramfs...
[    0.688009] Switched to high resolution mode on CPU 0
[    1.996108] Freeing initrd memory: 5620k freed
[    2.004007] Simple Boot Flag at 0x79 set to 0x1
[    2.004179] cpufreq-nforce2: No nForce2 chipset.
[    2.004213] Scanning for low memory corruption every 60 seconds
[    2.004370] audit: initializing netlink socket (disabled)
[    2.004404] type=2000 audit(1261849907.004:1): initialized
[    2.014900] highmem bounce pool size: 64 pages
[    2.014908] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.016616] VFS: Disk quotas dquot_6.5.2
[    2.016681] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.017319] fuse init (API version 7.12)
[    2.017417] msgmni has been set to 1706
[    2.017652] alg: No test for stdrng (krng)
[    2.017665] io scheduler noop registered
[    2.017668] io scheduler anticipatory registered
[    2.017670] io scheduler deadline registered
[    2.017718] io scheduler cfq registered (default)
[    2.017809] pci 0000:01:00.0: Boot video device
[    2.017925] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.017954] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.018465] ACPI: AC Adapter [AC] (off-line)
[    2.018570] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    2.018994] ACPI: Lid Switch [LID]
[    2.019047] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.019052] ACPI: Power Button [PBTN]
[    2.019105] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.019108] ACPI: Sleep Button [SBTN]
[    2.019593] Marking TSC unstable due to TSC halts in idle
[    2.019619] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    2.019648] processor LNXCPU:00: registered as cooling_device0
[    2.019652] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.030628] thermal LNXTHERM:01: registered as thermal_zone0
[    2.030640] ACPI: Thermal Zone [THM] (68 C)
[    2.030692] isapnp: Scanning for PnP cards...
[    2.320028] ACPI: Battery Slot [BAT0] (battery present)
[    2.320073] ACPI: Battery Slot [BAT1] (battery absent)
[    2.406924] isapnp: No Plug & Play device found
[    2.408148] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.409593] brd: module loaded
[    2.410111] loop: module loaded
[    2.410191] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.410309] ata_piix 0000:00:1f.1: version 2.13
[    2.410322] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    2.410509] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    2.410514] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.410560] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.410639] scsi0 : ata_piix
[    2.410723] scsi1 : ata_piix
[    2.411864] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    2.411868] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    2.412842] Fixed MDIO Bus: probed
[    2.412882] PPP generic driver version 2.4.2
[    2.412975] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.413159] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    2.413164] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    2.413178] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.413182] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.413243] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.417170] ehci_hcd 0000:00:1d.7: debug port 1
[    2.417176] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.417428] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    2.432034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.432135] usb usb1: configuration #1 chosen from 1 choice
[    2.432171] hub 1-0:1.0: USB hub found
[    2.432187] hub 1-0:1.0: 6 ports detected
[    2.432260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.432280] uhci_hcd: USB Universal Host Controller Interface driver
[    2.432306] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.432313] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.432317] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.432352] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.432374] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    2.432465] usb usb2: configuration #1 chosen from 1 choice
[    2.432495] hub 2-0:1.0: USB hub found
[    2.432503] hub 2-0:1.0: 2 ports detected
[    2.432550] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.432557] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.432561] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.432597] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.432618] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    2.432704] usb usb3: configuration #1 chosen from 1 choice
[    2.432734] hub 3-0:1.0: USB hub found
[    2.432741] hub 3-0:1.0: 2 ports detected
[    2.432954] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    2.432959] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.432966] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.432969] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.433007] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.433028] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    2.433116] usb usb4: configuration #1 chosen from 1 choice
[    2.433145] hub 4-0:1.0: USB hub found
[    2.433158] hub 4-0:1.0: 2 ports detected
[    2.433261] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.438085] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.438092] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.438147] mice: PS/2 mouse device common for all mice
[    2.438309] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.438326] rtc0: alarms up to one day, 114 bytes nvram
[    2.438435] device-mapper: uevent: version 1.0.3
[    2.438527] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.438609] device-mapper: multipath: version 1.1.0 loaded
[    2.438612] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.438740] EISA: Probing bus 0 at eisa.0
[    2.438764] EISA: Detected 0 cards.
[    2.438869] cpuidle: using governor ladder
[    2.438964] cpuidle: using governor menu
[    2.439484] TCP cubic registered
[    2.439672] NET: Registered protocol family 10
[    2.440154] lo: Disabled Privacy Extensions
[    2.440491] NET: Registered protocol family 17
[    2.440517] Bluetooth: L2CAP ver 2.13
[    2.440519] Bluetooth: L2CAP socket layer initialized
[    2.440523] Bluetooth: SCO (Voice Link) ver 0.6
[    2.440525] Bluetooth: SCO socket layer initialized
[    2.440560] Bluetooth: RFCOMM TTY layer initialized
[    2.440564] Bluetooth: RFCOMM socket layer initialized
[    2.440566] Bluetooth: RFCOMM ver 1.11
[    2.476091] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.478398] Using IPI No-Shortcut mode
[    2.478464] PM: Resume from disk failed.
[    2.478478] registered taskstats version 1
[    2.478598]   Magic number: 5:135:897
[    2.478679] rtc_cmos 00:06: setting system clock to 2009-12-26 17:51:47 UTC (1261849907)
[    2.478683] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.478685] EDD information not available.
[    2.580595] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A100, max UDMA/33
[    2.596229] ata2.00: configured for UDMA/33
[    2.930737] ata1.00: ATA-7: WDC WD1600BEVE-00UYT0, 01.04A01, max UDMA/100
[    2.930740] ata1.00: 312581808 sectors, multi 8: LBA48 
[    2.944579] ata1.00: configured for UDMA/100
[    2.944726] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVE-0 01.0 PQ: 0 ANSI: 5
[    2.944856] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.944899] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.944953] sd 0:0:0:0: [sda] Write Protect is off
[    2.944957] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.944984] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.945119]  sda: sda1 sda2 <
[    2.950906] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A100 PQ: 0 ANSI: 5
[    2.953562] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.953566] Uniform CD-ROM driver Revision: 3.20
[    2.953650] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.953699] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.971555]  sda5 >
[    2.971807] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.971825] Freeing unused kernel memory: 540k freed
[    2.972261] Write protecting the kernel text: 4568k
[    2.972303] Write protecting the kernel read-only data: 1836k
[    3.138573] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    3.164827] Linux agpgart interface v0.103
[    3.168942] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    3.264769] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    3.270679] ohci1394 0000:02:01.2: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.301447] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/device:1f/input/input5
[    3.301500] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    3.324063] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fafef800-fafeffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.324281] tg3.c:v3.99 (April 20, 2009)
[    3.324302] tg3 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.332085] tg3 0000:02:00.0: PME# disabled
[    3.400570] eth0: Tigon3 [partno(BCM95705A50) rev 3001] (PCI:33MHz:32-bit) MAC address 00:11:43:60:b3:87
[    3.400575] eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.400579] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.400582] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    3.421347] usb 2-2: configuration #1 chosen from 1 choice
[    3.664898] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.080104] usb 3-1: configuration #1 chosen from 1 choice
[    4.104767] usbcore: registered new interface driver hiddev
[    4.124494] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input6
[    4.124598] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    4.156123] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input7
[    4.156224] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    4.156240] usbcore: registered new interface driver usbhid
[    4.156243] usbhid: v2.6:USB HID core driver
[    4.558845] xor: automatically using best checksumming function: pIII_sse
[    4.576019]    pIII_sse  :  4395.000 MB/sec
[    4.576022] xor: using function: pIII_sse (4395.000 MB/sec)
[    4.579787] device-mapper: dm-raid45: initialized v0.2594b
[    4.645354] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[384fc00011b8a0a1]
[    4.750982] EXT4-fs (sda1): barriers enabled
[    4.770009] kjournald2 starting: pid 409, dev sda1:8, commit interval 5 seconds
[    4.770021] EXT4-fs (sda1): delayed allocation enabled
[    4.770025] EXT4-fs: file extents enabled
[    4.773722] EXT4-fs: mballoc enabled
[    4.773739] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.796345] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[    4.796349] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[    4.796352] EXT4-fs: mballoc: 0 generated and it took 0
[    4.796354] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[    6.038846] ISO 9660 Extensions: Microsoft Joliet Level 3
[    6.085927] ISO 9660 Extensions: RRIP_1991A
[    6.395159] aufs 2-standalone.tree-30-20090727
[    6.638677] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   70.470153] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k 
[   72.270286] udev: starting version 147
[   75.168804] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   75.168932] usbcore: registered new interface driver btusb
[   76.991744] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   76.995483] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   77.117206] intel_rng: FWH not detected
[   77.628595] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input8
[   77.652211] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
[   78.037313] dell-wmi: No known WMI GUID found
[   78.180454] lib80211: common routines for IEEE802.11 drivers
[   78.180459] lib80211_crypt: registered algorithm 'NULL'
[   78.436891] parport_pc 00:0b: reported by Plug and Play ACPI
[   78.436940] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   78.959049] ip_tables: (C) 2000-2006 Netfilter Core Team
[   79.016162] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:013f]
[   79.016180] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   79.016183] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   79.016188] yenta_cardbus 0000:02:01.0: TI: mfunc 0x012c1202, devctl 0x64
[   79.108769] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   79.108774] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   79.248551] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0478, PCI irq 11
[   79.248556] yenta_cardbus 0000:02:01.0: Socket status: 30000820
[   79.248561] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   79.248572] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   79.248577] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: clean.
[   79.249061] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   79.249065] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
[   79.249272] yenta_cardbus 0000:02:01.1: CardBus bridge found [1028:013f]
[   79.376590] yenta_cardbus 0000:02:01.1: ISA IRQ mask 0x0478, PCI irq 11
[   79.376596] yenta_cardbus 0000:02:01.1: Socket status: 30000047
[   79.376601] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   79.376610] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   79.376615] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xd000-0xefff: clean.
[   79.377099] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   79.377103] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
[   79.845362] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   79.845368] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   79.845757] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   79.845761] PCI: setting IRQ 5 as level-triggered
[   79.845768] ipw2100 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   79.846504] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   79.846526] ipw2100 0000:02:03.0: firmware: requesting ipw2100-1.3.fw
[   79.884055] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   79.884101] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[   79.976797] ppdev: user-space parallel port driver
[   81.035383] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   81.036403] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   81.036842] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   81.036897] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   81.037423] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   81.048540] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   81.049537] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   81.049975] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   81.050030] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   81.050552] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   81.268618] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   81.268623] Bluetooth: BNEP filters: protocol multicast
[   82.489088] cfg80211: Calling CRDA to update world regulatory domain
[   82.492780] tg3 0000:02:00.0: firmware: requesting tigon/tg3_tso5.bin
[   82.734843] Bridge firewalling registered
[   83.633193] tg3 0000:02:00.0: PME# disabled
[   84.041792] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   84.064671] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   84.404122] cfg80211: World regulatory domain updated:
[   84.404129] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   84.404133] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.404137] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   84.404140] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   84.404143] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.404147] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.668193] ath5k 0000:03:00.0: enabling device (0000 -> 0002)
[   84.668211] ath5k 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   84.668283] ath5k 0000:03:00.0: registered as 'phy0'
[   84.781837] ath: EEPROM regdomain: 0x10
[   84.781840] ath: EEPROM indicates we should expect a direct regpair map
[   84.781844] ath: Country alpha2 being used: CO
[   84.781846] ath: Regpair used: 0x10
[   85.364589] phy0: Selected rate control algorithm 'minstrel'
[   85.365423] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   85.366998] cfg80211: Calling CRDA for country: CO
[   85.369445] cfg80211: Regulatory domain changed to country: CO
[   85.369449] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   85.369453] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   85.369456] 	(5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   85.369460] 	(5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   85.369463] 	(5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   85.499431] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   85.499487] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   85.572362] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   86.356034] intel8x0_measure_ac97_clock: measured 55423 usecs (2670 samples)
[   86.356039] intel8x0: clocking to 48000
[   87.054862] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[   87.054867] tg3: eth0: Flow control is on for TX and on for RX.
[   87.055100] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   91.263308] lp0: using parport0 (interrupt-driven).
[   97.640026] eth0: no IPv6 routers present
[  163.184060] Clocksource tsc unstable (delta = -202297677 ns)
[  251.893245] RPC: Registered udp transport module.
[  251.893250] RPC: Registered tcp transport module.
[  381.012178] svc: failed to register lockdv1 RPC service (errno 97).
[  537.678604] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  537.678609] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  537.678612] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  537.678679] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xfae00000-0xfb3fffff

```

And when I boot from my HD and the wireless is "gone":
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffae000 (usable)
[    0.000000]  BIOS-e820: 000000007ffae000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x7ffae max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FEDA0000 mask FFFFE0000 write-through
[    0.000000]   2 disabled
[    0.000000]   3 disabled
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
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffae000 (usable)
[    0.000000]  modified: 000000007ffae000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37869000 - 37fefb2c
[    0.000000] Allocated new RAMDISK: 008ad000 - 01033b2c
[    0.000000] Move RAMDISK from 0000000037869000 - 0000000037fefb2b to 008ad000 - 01033b2b
[    0.000000] ACPI: RSDP 000fdf00 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 7fff0000 00030 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: FACP 7fff0400 00074 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: DSDT 7fff0c00 02E30 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 7ffff800 00040
[    0.000000] ACPI: ASF! 7fff0800 0005B (v16 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: BOOT 7fff07c0 00028 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac198]              BRK ==> [00008a9000 - 00008ac198]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0001033b2c]      NEW RAMDISK ==> [00008ad000 - 0001033b2c]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffae
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffae
[    0.000000] On node 0 totalpages: 524105
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1034000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294560 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7eda0000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c203e000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520009
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=e177426a-bc38-41a4-9635-536ad12e8038 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10484120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffae)
[    0.000000] Memory: 2052412k/2096824k available (4566k kernel code, 43108k reserved, 2142k data, 540k init, 1187520k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1694.433 MHz processor.
[    0.001515] Console: colour VGA+ 80x25
[    0.001522] console [tty0] enabled
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 3388.86 BogoMIPS (lpj=6777732)
[    0.004045] Security Framework initialized
[    0.004085] AppArmor: AppArmor initialized
[    0.004096] Mount-cache hash table entries: 512
[    0.004290] Initializing cgroup subsys ns
[    0.004297] Initializing cgroup subsys cpuacct
[    0.004302] Initializing cgroup subsys memory
[    0.004313] Initializing cgroup subsys freezer
[    0.004316] Initializing cgroup subsys net_cls
[    0.004339] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004342] CPU: L2 cache: 2048K
[    0.004348] mce: CPU supports 5 MCE banks
[    0.004358] ------------[ cut here ]------------
[    0.004376] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()
[    0.004379] Hardware name: Precision M60                   
[    0.004382] Modules linked in:
[    0.004388] Pid: 0, comm: swapper Not tainted 2.6.31-16-generic #53-Ubuntu
[    0.004391] Call Trace:
[    0.004405]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
[    0.004410]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
[    0.004414]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
[    0.004419]  [<c01451d5>] warn_slowpath_null+0x15/0x20
[    0.004424]  [<c011d7e3>] native_apic_write_dummy+0x33/0x40
[    0.004433]  [<c011278c>] intel_init_thermal+0xac/0x1a0
[    0.004437]  [<c0111dbb>] mce_intel_feature_init+0xb/0x60
[    0.004442]  [<c010fcf0>] mce_cpu_features+0x10/0x40
[    0.004450]  [<c056b29c>] mcheck_init+0x14a/0x188
[    0.004455]  [<c05696d8>] ? init_hypervisor+0xb/0x2c
[    0.004459]  [<c0569690>] identify_cpu+0x20e/0x21d
[    0.004468]  [<c0795732>] identify_boot_cpu+0xd/0x23
[    0.004472]  [<c07958c8>] check_bugs+0xb/0xe9
[    0.004480]  [<c078e8c3>] start_kernel+0x2dc/0x2ec
[    0.004485]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
[    0.004490]  [<c078e07c>] i386_start_kernel+0x7c/0x83
[    0.004501] ---[ end trace a7919e7f17c0a725 ]---
[    0.004505] CPU0: Thermal monitoring enabled (TM1)
[    0.004520] Performance Counters: 
[    0.004524] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.004526] no hardware sampling interrupt available.
[    0.004529] p6 PMU driver.
[    0.004535] ... version:                 0
[    0.004537] ... bit width:               32
[    0.004540] ... generic counters:        2
[    0.004542] ... value mask:              00000000ffffffff
[    0.004544] ... max period:              000000007fffffff
[    0.004547] ... fixed-purpose counters:  0
[    0.004549] ... counter mask:            0000000000000003
[    0.004555] Checking 'hlt' instruction... OK.
[    0.020931] SMP alternatives: switching to UP code
[    0.027967] Freeing SMP alternatives: 19k freed
[    0.027978] ACPI: Core revision 20090521
[    0.033350] ACPI: setting ELCR to 0200 (from 0800)
[    0.034421] weird, boot CPU (#0) not listed by the BIOS.
[    0.034424] SMP motherboard not detected.
[    0.034427] Local APIC not detected. Using dummy APIC emulation.
[    0.034429] SMP disabled
[    0.034599] Brought up 1 CPUs
[    0.034602] Total of 1 processors activated (3388.86 BogoMIPS).
[    0.034616] CPU0 attaching NULL sched-domain.
[    0.034869] Booting paravirtualized kernel on bare hardware
[    0.035106] regulator: core version 0.5
[    0.035135] Time: 18:16:43  Date: 12/26/09
[    0.035192] NET: Registered protocol family 16
[    0.035342] EISA bus registered
[    0.035359] ACPI: bus type pci registered
[    0.070527] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    0.070530] PCI: Using configuration type 1 for base access
[    0.071706] bio: create slab <bio-0> at 0
[    0.072261] ACPI: EC: Look up EC in DSDT
[    0.082261] ACPI: Interpreter enabled
[    0.082273] ACPI: (supports S0 S1 S3 S4 S5)
[    0.082297] ACPI: Using PIC for interrupt routing
[    0.101786] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.106591] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.106646] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.106762] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.106816] pci 0000:00:1d.1: reg 20 io port: [0xbf40-0xbf5f]
[    0.106868] pci 0000:00:1d.2: reg 20 io port: [0xbf20-0xbf3f]
[    0.106929] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4fffc00-0xf4ffffff]
[    0.106987] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.106993] pci 0000:00:1d.7: PME# disabled
[    0.107082] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.107086] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.107111] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.107118] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.107126] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.107133] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.107141] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.107149] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.107192] pci 0000:00:1f.5: reg 10 io port: [0xb800-0xb8ff]
[    0.107199] pci 0000:00:1f.5: reg 14 io port: [0xbc40-0xbc7f]
[    0.107206] pci 0000:00:1f.5: reg 18 32bit mmio: [0xf4fff800-0xf4fff9ff]
[    0.107213] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xf4fff400-0xf4fff4ff]
[    0.107243] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.107248] pci 0000:00:1f.5: PME# disabled
[    0.107285] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.107292] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
[    0.107310] pci 0000:01:00.0: reg 30 32bit mmio: [0x80000000-0x8001ffff]
[    0.107360] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.107364] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.107368] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.107423] pci 0000:02:00.0: reg 10 64bit mmio: [0xfaff0000-0xfaffffff]
[    0.107476] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.107480] pci 0000:02:00.0: PME# disabled
[    0.107516] pci 0000:02:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.107535] pci 0000:02:01.0: supports D1 D2
[    0.107537] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.107542] pci 0000:02:01.0: PME# disabled
[    0.107576] pci 0000:02:01.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.107595] pci 0000:02:01.1: supports D1 D2
[    0.107598] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.107603] pci 0000:02:01.1: PME# disabled
[    0.107637] pci 0000:02:01.2: reg 10 32bit mmio: [0xfafef800-0xfafeffff]
[    0.107644] pci 0000:02:01.2: reg 14 32bit mmio: [0xfafe8000-0xfafebfff]
[    0.107684] pci 0000:02:01.2: supports D1 D2
[    0.107687] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot
[    0.107692] pci 0000:02:01.2: PME# disabled
[    0.107722] pci 0000:02:01.3: reg 10 io port: [0xecf8-0xecff]
[    0.107800] pci 0000:02:03.0: reg 10 32bit mmio: [0xfafee000-0xfafeefff]
[    0.107879] pci 0000:00:1e.0: transparent bridge
[    0.107884] pci 0000:00:1e.0: bridge io port: [0xd000-0xefff]
[    0.107889] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6000000-0xfbffffff]
[    0.107932] pci_bus 0000:00: on NUMA node 0
[    0.107938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.108186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.108242] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.126535] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.126661] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.126784] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.126907] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.127012] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.127139] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.127361] SCSI subsystem initialized
[    0.127414] libata version 3.00 loaded.
[    0.127492] usbcore: registered new interface driver usbfs
[    0.127516] usbcore: registered new interface driver hub
[    0.127545] usbcore: registered new device driver usb
[    0.127686] ACPI: WMI: Mapper loaded
[    0.127688] PCI: Using ACPI for IRQ routing
[    0.128036] Bluetooth: Core ver 2.15
[    0.128065] NET: Registered protocol family 31
[    0.128068] Bluetooth: HCI device and connection manager initialized
[    0.128072] Bluetooth: HCI socket layer initialized
[    0.128074] NetLabel: Initializing
[    0.128076] NetLabel:  domain hash size = 128
[    0.128078] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.128094] NetLabel:  unlabeled traffic allowed by default
[    0.130245] pnp: PnP ACPI init
[    0.130265] ACPI: bus type pnp registered
[    0.140111] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.140116] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.140188] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.140193] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.140197] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.153720] pnp: PnP ACPI: found 12 devices
[    0.153723] ACPI: ACPI bus type pnp unregistered
[    0.153729] PnPBIOS: Disabled by ACPI PNP
[    0.153742] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.153746] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.153750] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.153753] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.153757] system 00:00: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.153761] system 00:00: iomem range 0x7fff0000-0x7fffffff has been reserved
[    0.153765] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.153768] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.153776] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.153783] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.153787] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.153790] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.153794] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.153801] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.188491] AppArmor: AppArmor Filesystem Enabled
[    0.188504] pci 0000:01:00.0: BAR 6: no parent found for of device [0x80000000-0x8001ffff]
[    0.188532] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.188536] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.188541] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.188545] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.188559] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.188562] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.188567] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.188572] pci 0000:02:01.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.188578] pci 0000:02:01.0:   MEM window: 0x8c000000-0x8fffffff
[    0.188583] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
[    0.188586] pci 0000:02:01.1:   IO window: 0x00d800-0x00d8ff
[    0.188591] pci 0000:02:01.1:   IO window: 0x00dc00-0x00dcff
[    0.188596] pci 0000:02:01.1:   PREFETCH window: 0x84000000-0x87ffffff
[    0.188601] pci 0000:02:01.1:   MEM window: 0x90000000-0x93ffffff
[    0.188606] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.188610] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.188616] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.188621] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x87ffffff
[    0.188638] pci 0000:00:1e.0: setting latency timer to 64
[    0.188646] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.188820] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.188823] PCI: setting IRQ 11 as level-triggered
[    0.188828] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.188841] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.188848] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.188851] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.188854] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.188858] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.188861] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.188865] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.188868] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xfbffffff]
[    0.188871] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x87ffffff]
[    0.188874] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.188878] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.188881] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.188884] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.188887] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.188891] pci_bus 0000:03: resource 3 mem: [0x8c000000-0x8fffffff]
[    0.188894] pci_bus 0000:07: resource 0 io:  [0xd800-0xd8ff]
[    0.188897] pci_bus 0000:07: resource 1 io:  [0xdc00-0xdcff]
[    0.188901] pci_bus 0000:07: resource 2 pref mem [0x84000000-0x87ffffff]
[    0.188904] pci_bus 0000:07: resource 3 mem: [0x90000000-0x93ffffff]
[    0.188946] NET: Registered protocol family 2
[    0.189051] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.189444] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.190872] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.191806] TCP: Hash tables configured (established 131072 bind 65536)
[    0.191810] TCP reno registered
[    0.191951] NET: Registered protocol family 1
[    0.192091] Trying to unpack rootfs image as initramfs...
[    0.452352] Freeing initrd memory: 7706k freed
[    0.463323] Simple Boot Flag at 0x79 set to 0x1
[    0.463450] cpufreq-nforce2: No nForce2 chipset.
[    0.463483] Scanning for low memory corruption every 60 seconds
[    0.463647] audit: initializing netlink socket (disabled)
[    0.463684] type=2000 audit(1261851403.460:1): initialized
[    0.474236] highmem bounce pool size: 64 pages
[    0.474244] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.475926] VFS: Disk quotas dquot_6.5.2
[    0.475991] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.476665] fuse init (API version 7.12)
[    0.476760] msgmni has been set to 1706
[    0.476998] alg: No test for stdrng (krng)
[    0.477012] io scheduler noop registered
[    0.477015] io scheduler anticipatory registered
[    0.477017] io scheduler deadline registered
[    0.477066] io scheduler cfq registered (default)
[    0.477156] pci 0000:01:00.0: Boot video device
[    0.477273] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.477300] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.477819] ACPI: AC Adapter [AC] (off-line)
[    0.477924] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.478417] ACPI: Lid Switch [LID]
[    0.478470] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.478475] ACPI: Power Button [PBTN]
[    0.478527] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.478530] ACPI: Sleep Button [SBTN]
[    0.479016] Marking TSC unstable due to TSC halts in idle
[    0.479041] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    0.479070] processor LNXCPU:00: registered as cooling_device0
[    0.479074] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.480057] Switched to high resolution mode on CPU 0
[    0.490087] thermal LNXTHERM:01: registered as thermal_zone0
[    0.490097] ACPI: Thermal Zone [THM] (57 C)
[    0.500200] isapnp: Scanning for PnP cards...
[    0.822565] ACPI: Battery Slot [BAT0] (battery present)
[    0.822610] ACPI: Battery Slot [BAT1] (battery absent)
[    0.866083] isapnp: No Plug & Play device found
[    0.867283] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.868749] brd: module loaded
[    0.869263] loop: module loaded
[    0.869341] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.869460] ata_piix 0000:00:1f.1: version 2.13
[    0.869473] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.869656] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.869662] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.869709] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.869789] scsi0 : ata_piix
[    0.869876] scsi1 : ata_piix
[    0.870962] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.870966] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.871905] Fixed MDIO Bus: probed
[    0.871945] PPP generic driver version 2.4.2
[    0.872306] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.872490] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.872494] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.872509] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.872513] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.872568] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.876485] ehci_hcd 0000:00:1d.7: debug port 1
[    0.876492] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.876501] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    0.892036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.892136] usb usb1: configuration #1 chosen from 1 choice
[    0.892178] hub 1-0:1.0: USB hub found
[    0.892187] hub 1-0:1.0: 6 ports detected
[    0.892260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.892280] uhci_hcd: USB Universal Host Controller Interface driver
[    0.892305] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.892312] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.892316] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.892358] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.892379] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    0.892470] usb usb2: configuration #1 chosen from 1 choice
[    0.892501] hub 2-0:1.0: USB hub found
[    0.892508] hub 2-0:1.0: 2 ports detected
[    0.892555] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.892562] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.892565] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.892596] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.892617] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    0.892703] usb usb3: configuration #1 chosen from 1 choice
[    0.892732] hub 3-0:1.0: USB hub found
[    0.892739] hub 3-0:1.0: 2 ports detected
[    0.892950] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.892955] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.892961] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.892965] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.893009] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.893030] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    0.893118] usb usb4: configuration #1 chosen from 1 choice
[    0.893147] hub 4-0:1.0: USB hub found
[    0.893155] hub 4-0:1.0: 2 ports detected
[    0.893259] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.898182] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.898188] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.898244] mice: PS/2 mouse device common for all mice
[    0.898407] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.898424] rtc0: alarms up to one day, 114 bytes nvram
[    0.898537] device-mapper: uevent: version 1.0.3
[    0.898630] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.898725] device-mapper: multipath: version 1.1.0 loaded
[    0.898728] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.898855] EISA: Probing bus 0 at eisa.0
[    0.898879] EISA: Detected 0 cards.
[    0.898983] cpuidle: using governor ladder
[    0.899078] cpuidle: using governor menu
[    0.899596] TCP cubic registered
[    0.899779] NET: Registered protocol family 10
[    0.900284] lo: Disabled Privacy Extensions
[    0.900622] NET: Registered protocol family 17
[    0.900640] Bluetooth: L2CAP ver 2.13
[    0.900642] Bluetooth: L2CAP socket layer initialized
[    0.900645] Bluetooth: SCO (Voice Link) ver 0.6
[    0.900647] Bluetooth: SCO socket layer initialized
[    0.900681] Bluetooth: RFCOMM TTY layer initialized
[    0.900685] Bluetooth: RFCOMM socket layer initialized
[    0.900687] Bluetooth: RFCOMM ver 1.11
[    0.938038] Using IPI No-Shortcut mode
[    0.938106] PM: Resume from disk failed.
[    0.938120] registered taskstats version 1
[    0.938234]   Magic number: 5:620:292
[    0.938252] tty tty25: hash matches
[    0.938314] rtc_cmos 00:06: setting system clock to 2009-12-26 18:16:44 UTC (1261851404)
[    0.938318] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.938320] EDD information not available.
[    0.938431] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.036595] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A100, max UDMA/33
[    1.052229] ata2.00: configured for UDMA/33
[    1.089900] ata1.00: ATA-7: WDC WD1600BEVE-00UYT0, 01.04A01, max UDMA/100
[    1.089903] ata1.00: 312581808 sectors, multi 8: LBA48 
[    1.104742] ata1.00: configured for UDMA/100
[    1.104890] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVE-0 01.0 PQ: 0 ANSI: 5
[    1.105018] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.105061] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.105115] sd 0:0:0:0: [sda] Write Protect is off
[    1.105118] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.105146] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.105284]  sda: sda1 sda2 <
[    1.110590] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A100 PQ: 0 ANSI: 5
[    1.123686] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.123690] Uniform CD-ROM driver Revision: 3.20
[    1.123782] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.123832] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.141821]  sda5 >
[    1.142077] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.142095] Freeing unused kernel memory: 540k freed
[    1.142502] Write protecting the kernel text: 4568k
[    1.142544] Write protecting the kernel read-only data: 1836k
[    1.313930] Linux agpgart interface v0.103
[    1.318049] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    1.330549] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/device:1f/input/input5
[    1.330598] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.375473] tg3.c:v3.99 (April 20, 2009)
[    1.375499] tg3 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.389122] tg3 0000:02:00.0: PME# disabled
[    1.491731] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    1.528145] eth0: Tigon3 [partno(BCM95705A50) rev 3001] (PCI:33MHz:32-bit) MAC address 00:11:43:60:b3:87
[    1.528151] eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.528155] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.528158] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    1.528546] ohci1394 0000:02:01.2: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.584059] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fafef800-fafeffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.662668] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    1.900124] usb 2-2: configuration #1 chosen from 1 choice
[    2.336025] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.684104] usb 3-1: configuration #1 chosen from 1 choice
[    2.701201] usbcore: registered new interface driver hiddev
[    2.703830] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input6
[    2.703938] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    2.708460] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input7
[    2.708559] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    2.708573] usbcore: registered new interface driver usbhid
[    2.708577] usbhid: v2.6:USB HID core driver
[    2.849239] xor: automatically using best checksumming function: pIII_sse
[    2.868019]    pIII_sse  :  4394.000 MB/sec
[    2.868022] xor: using function: pIII_sse (4394.000 MB/sec)
[    2.868160] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[384fc00011b8a0a1]
[    2.872156] device-mapper: dm-raid45: initialized v0.2594b
[    3.225664] PM: Starting manual resume from disk
[    3.225669] PM: Resume from partition 8:5
[    3.225671] PM: Checking hibernation image.
[    3.225912] PM: Resume from disk failed.
[    3.254513] EXT4-fs (sda1): barriers enabled
[    3.273538] kjournald2 starting: pid 372, dev sda1:8, commit interval 5 seconds
[    3.273550] EXT4-fs (sda1): delayed allocation enabled
[    3.273554] EXT4-fs: file extents enabled
[    3.277270] EXT4-fs: mballoc enabled
[    3.277288] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.010987] type=1505 audit(1261851407.571:2): operation="profile_load" pid=395 name=/usr/share/gdm/guest-session/Xsession
[    4.013833] type=1505 audit(1261851407.573:3): operation="profile_load" pid=396 name=/sbin/dhclient3
[    4.014574] type=1505 audit(1261851407.573:4): operation="profile_load" pid=396 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.014977] type=1505 audit(1261851407.573:5): operation="profile_load" pid=396 name=/usr/lib/connman/scripts/dhclient-script
[    4.087427] type=1505 audit(1261851407.646:6): operation="profile_load" pid=397 name=/usr/bin/evince
[    4.099689] type=1505 audit(1261851407.657:7): operation="profile_load" pid=397 name=/usr/bin/evince-previewer
[    4.106864] type=1505 audit(1261851407.665:8): operation="profile_load" pid=397 name=/usr/bin/evince-thumbnailer
[    4.137056] type=1505 audit(1261851407.697:9): operation="profile_load" pid=399 name=/usr/lib/cups/backend/cups-pdf
[    4.137937] type=1505 audit(1261851407.697:10): operation="profile_load" pid=399 name=/usr/sbin/cupsd
[    5.415866] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k 
[    5.810500] EXT4-fs (sda1): internal journal on sda1:8
[    7.325598] udev: starting version 147
[    8.970822] udev: renamed network interface eth0 to eth1
[   10.921369] nvidia: module license 'NVIDIA' taints kernel.
[   10.921377] Disabling lock debugging due to kernel taint
[   11.180027] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.180252] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
[   13.018979] tg3 0000:02:00.0: firmware: requesting tigon/tg3_tso5.bin
[   13.227417] tg3 0000:02:00.0: PME# disabled
[   13.560554] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   14.855795] __ratelimit: 6 callbacks suppressed
[   14.855801] type=1505 audit(1261851418.413:13): operation="profile_replace" pid=986 name=/usr/share/gdm/guest-session/Xsession
[   14.862711] type=1505 audit(1261851418.421:14): operation="profile_replace" pid=989 name=/sbin/dhclient3
[   14.863458] type=1505 audit(1261851418.421:15): operation="profile_replace" pid=989 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.863866] type=1505 audit(1261851418.421:16): operation="profile_replace" pid=989 name=/usr/lib/connman/scripts/dhclient-script
[   14.869800] type=1505 audit(1261851418.429:17): operation="profile_replace" pid=990 name=/usr/bin/evince
[   14.900158] type=1505 audit(1261851418.461:18): operation="profile_replace" pid=990 name=/usr/bin/evince-previewer
[   14.907306] type=1505 audit(1261851418.465:19): operation="profile_replace" pid=990 name=/usr/bin/evince-thumbnailer
[   14.917757] type=1505 audit(1261851418.477:20): operation="profile_replace" pid=995 name=/usr/lib/cups/backend/cups-pdf
[   14.918638] type=1505 audit(1261851418.477:21): operation="profile_replace" pid=995 name=/usr/sbin/cupsd
[   14.921102] type=1505 audit(1261851418.481:22): operation="profile_replace" pid=996 name=/usr/sbin/ntpd
[   16.691041] tg3: eth1: Link is up at 1000 Mbps, full duplex.
[   16.691046] tg3: eth1: Flow control is on for TX and on for RX.
[   16.691277] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   19.783566] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   19.783583] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   19.783615] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   26.928026] eth1: no IPv6 routers present
[   28.188785] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   28.188790] vboxdrv: Successfully done.
[   28.188792] vboxdrv: Found 1 processor cores.
[   28.188912] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   28.188915] vboxdrv: Successfully loaded version 3.0.8_OSE (interface 0x000e0000).
[   94.188043] Clocksource tsc unstable (delta = -161504008 ns)
[  218.160055] spurious 8259A interrupt: IRQ7.

```

So can anyone tell me how I can get it to recognize my cardbus adapter for wireless again?



  Hey I had something similar a while back and the simple fix was simply to: 
1.right click lower panel
2. click add to panel
3.drag the "Notification Area icon" to the panel where you want your network applet to show up. It has to have a parking space before it will show up.

---

### Post by sot3 on 2010-01-02
Thanks, but I have a Network Manager icon.  It's the wireless interface that's not appearing where it should.

---

