---
title: "BCM4306 (Rev. 2) (14e4:4320) - Wireless not functioning"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by YJA-LxDx-do on 2011-05-08
[FONT=Courier New]Ubuntu Community,

I tried using b43-fwcutter in accordance with the Ubuntu Forums and nothing happened, and then I decided to look a little further.  According to LinuxWireless.org, the BCM4306/2 actually uses the b43legacy drivers, so I purged all of b43-fwcutter along with firmware-b43-installer and downloaded firmware-b43legacy-installer.  

$ sudo apt-get install b43-fwcutter firmware-b43legacy-installer

Nothing happened, so I downloaded b43legacy manually per the instructions listed at LinuxWireless.com, and manually extracted from wl_apsta-3.130.20.0.o to my /lib/firmware folder.  Nothing happened again. I made sure to check additional drivers and nothing shows up.  

As per the ticket posting instructions, I've included all the info you guys could need.  from what I can conclude, the wireless isn't even ON, but it's integrated and I have NO IDEA what I have to do to get it up and running.  

At least in OpenSuSE 11.3 LXDE I was able to get the wireless on, although I had some major connection issues, I guess it couldn't resolve the handshake completely, or take my SSID/PSK properly.  

Here goes!  (God bless 2>&1 | tee -a)

#Machine info
MFG: HP
MDL: ZE4800

#OS
Ubuntu 11.04 (Natty Narwhal)

#kernel
32-bit 
2.6.38-8-generic i686


#Wireless info (lspci)
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

#Current iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

#Current ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:20:21:31:93  
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe21:3193/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30209 (30.2 KB)  TX bytes:9200 (9.2 KB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

#Current lsmod
Module                  Size  Used by
snd_ali5451            23506  2 
snd_ac97_codec        105614  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
radeon                896428  2 
snd_pcm                80244  2 snd_ali5451,snd_ac97_codec
binfmt_misc            13213  1 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 radeon
ppdev                  12849  0 
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  4 radeon,ttm,drm_kms_helper
pcmcia                 39671  0 
yenta_socket           27230  0 
i2c_algo_bit           13184  1 radeon
psmouse                73312  0 
i2c_ali15x3            12878  0 
snd                    55295  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
parport_pc             32111  1 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
video                  18951  0 
i2c_ali1535            12777  0 
soundcore              12600  1 snd
shpchp                 32345  0 
ati_agp                13202  1 
snd_page_alloc         14073  1 snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0 
natsemi                35814  0 
pata_ali               13564  2 

#Current dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003beff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003beff000 - 000000003bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf00000 - 000000003c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Hewlett-Packard           Pavilion ze4800 (PF175UA)/0024                     , BIOS KAM1.60   05/04/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3bef0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DAFFF uncachable
[    0.000000]   DB000-DBFFF write-protect
[    0.000000]   DC000-DFFFF write-back
[    0.000000]   E0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3677c000 - 373b6000
[    0.000000] ACPI: RSDP 000f7290 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3bef8b70 00030 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3befee2b 00074 (v01 ATI    Raptor   06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 3bef8ba0 0628B (v01    ATI U1_M1535 06040000 MSFT 0100000D)
[    0.000000] ACPI: FACS 3befffc0 00040
[    0.000000] ACPI: BOOT 3befee9f 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3befeec7 00139 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] 70MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003bef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bef0
[    0.000000] On node 0 totalpages: 245375
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f5ffc200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 142 pages used for memmap
[    0.000000]   HighMem zone: 18020 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3c000000 (gap: 3c000000:c3fc0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5800000 s28800 r0 d24448 u4194304
[    0.000000] pcpu-alloc: s28800 r0 d24448 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243457
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=6e67744d-ba7e-45ce-a9b1-41d73b3bccdd ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4909440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003bef0)
[    0.000000] Memory: 946264k/981952k available (5188k kernel code, 35236k reserved, 2540k data, 700k init, 72648k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5406000 soft=f5408000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2120.456 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4240.91 BogoMIPS (lpj=8481824)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004066] Security Framework initialized
[    0.004129] AppArmor: AppArmor initialized
[    0.004133] Yama: becoming mindful.
[    0.004248] Mount-cache hash table entries: 512
[    0.004548] Initializing cgroup subsys ns
[    0.004555] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004561] Initializing cgroup subsys cpuacct
[    0.004568] Initializing cgroup subsys memory
[    0.004587] Initializing cgroup subsys devices
[    0.004592] Initializing cgroup subsys freezer
[    0.004596] Initializing cgroup subsys net_cls
[    0.004600] Initializing cgroup subsys blkio
[    0.004672] mce: CPU supports 4 MCE banks
[    0.005356] SMP alternatives: switching to UP code
[    0.014726] Freeing SMP alternatives: 20k freed
[    0.014765] ACPI: Core revision 20110112
[    0.019175] ACPI: setting ELCR to 0200 (from 0e28)
[    0.020121] ftrace: allocating 23640 entries in 47 pages
[    0.024220] weird, boot CPU (#0) not listed by the BIOS.
[    0.024227] SMP motherboard not detected.
[    0.024232] Local APIC not detected. Using dummy APIC emulation.
[    0.024234] SMP disabled
[    0.024237] Performance Events: 
[    0.024242] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.024244] no hardware sampling interrupt available.
[    0.024249] AMD PMU driver.
[    0.024255] ... version:                0
[    0.024257] ... bit width:              48
[    0.024259] ... generic registers:      4
[    0.024261] ... value mask:             0000ffffffffffff
[    0.024263] ... max period:             00007fffffffffff
[    0.024265] ... fixed-purpose events:   0
[    0.024267] ... event mask:             000000000000000f
[    0.028804] Brought up 1 CPUs
[    0.028808] Total of 1 processors activated (4240.91 BogoMIPS).
[    0.029023] devtmpfs: initialized
[    0.030934] print_constraints: dummy: 
[    0.030979] Time: 12:53:19  Date: 05/08/11
[    0.031057] NET: Registered protocol family 16
[    0.031274] EISA bus registered
[    0.031291] ACPI: bus type pci registered
[    0.043579] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
[    0.043582] PCI: Using configuration type 1 for base access
[    0.045036] bio: create slab <bio-0> at 0
[    0.046284] ACPI: EC: Look up EC in DSDT
[    0.056538] ACPI: Interpreter enabled
[    0.056547] ACPI: (supports S0 S3 S4 S5)
[    0.056571] ACPI: Using PIC for interrupt routing
[    0.064418] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.064543] ACPI: No dock devices found.
[    0.064546] HEST: Table not found.
[    0.064553] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.064701] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.064961] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.064966] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff] (ignored)
[    0.064970] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff] (ignored)
[    0.064973] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000cbfff] (ignored)
[    0.064977] pci_root PNP0A03:00: host bridge window [mem 0x000cc000-0x000cffff] (ignored)
[    0.064980] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d7fff] (ignored)
[    0.064983] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000cefff] (ignored)
[    0.064987] pci_root PNP0A03:00: host bridge window [mem 0x3c000000-0xfff7ffff] (ignored)
[    0.064990] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.064993] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.065016] pci 0000:00:00.0: [1002:cab0] type 0 class 0x000600
[    0.065029] pci 0000:00:00.0: reg 10: [mem 0xd4000000-0xd7ffffff pref]
[    0.065036] pci 0000:00:00.0: reg 14: [mem 0xd0400000-0xd0400fff pref]
[    0.065042] pci 0000:00:00.0: reg 18: [io  0x8090-0x8093]
[    0.065088] pci 0000:00:01.0: [1002:700f] type 1 class 0x000604
[    0.065124] pci 0000:00:02.0: [10b9:5237] type 0 class 0x000c03
[    0.068009] pci 0000:00:02.0: reg 10: [mem 0xd0002000-0xd0002fff]
[    0.068055] pci 0000:00:02.0: PME# supported from D3cold
[    0.068061] pci 0000:00:02.0: PME# disabled
[    0.068082] pci 0000:00:06.0: [10b9:5451] type 0 class 0x000401
[    0.068095] pci 0000:00:06.0: reg 10: [io  0x8400-0x84ff]
[    0.068103] pci 0000:00:06.0: reg 14: [mem 0xd0003000-0xd0003fff]
[    0.068144] pci 0000:00:06.0: supports D1 D2
[    0.068147] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.068151] pci 0000:00:06.0: PME# disabled
[    0.068173] pci 0000:00:07.0: [10b9:1533] type 0 class 0x000601
[    0.068250] pci 0000:00:08.0: [10b9:5457] type 0 class 0x000703
[    0.068263] pci 0000:00:08.0: reg 10: [mem 0xd0004000-0xd0004fff]
[    0.068272] pci 0000:00:08.0: reg 14: [io  0x8800-0x88ff]
[    0.068311] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.068315] pci 0000:00:08.0: PME# disabled
[    0.068332] pci 0000:00:09.0: [14e4:4320] type 0 class 0x000280
[    0.068345] pci 0000:00:09.0: reg 10: [mem 0xd0000000-0xd0001fff]
[    0.068389] pci 0000:00:09.0: supports D1 D2
[    0.068391] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.068396] pci 0000:00:09.0: PME# disabled
[    0.068414] pci 0000:00:0a.0: [104c:ac50] type 2 class 0x000607
[    0.068428] pci 0000:00:0a.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.068443] pci 0000:00:0a.0: supports D1 D2
[    0.068446] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.068450] pci 0000:00:0a.0: PME# disabled
[    0.068473] pci 0000:00:10.0: [10b9:5229] type 0 class 0x000101
[    0.068506] pci 0000:00:10.0: reg 20: [io  0x8080-0x808f]
[    0.068544] pci 0000:00:11.0: [10b9:7101] type 0 class 0x000680
[    0.068598] pci 0000:00:11.0: quirk: [io  0x8000-0x803f] claimed by ali7101 ACPI
[    0.068602] pci 0000:00:11.0: quirk: [io  0x8040-0x805f] claimed by ali7101 SMB
[    0.068622] pci 0000:00:12.0: [100b:0020] type 0 class 0x000200
[    0.068635] pci 0000:00:12.0: reg 10: [io  0x8c00-0x8cff]
[    0.068644] pci 0000:00:12.0: reg 14: [mem 0xd0005000-0xd0005fff]
[    0.068675] pci 0000:00:12.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.068689] pci 0000:00:12.0: supports D1 D2
[    0.068691] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.068696] pci 0000:00:12.0: PME# disabled
[    0.068740] pci 0000:01:05.0: [1002:4336] type 0 class 0x000300
[    0.068754] pci 0000:01:05.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    0.068762] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.068770] pci 0000:01:05.0: reg 18: [mem 0xd0100000-0xd010ffff]
[    0.068793] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.068810] pci 0000:01:05.0: supports D1 D2
[    0.068838] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.068844] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.068849] pci 0000:00:01.0:   bridge window [mem 0xd0100000-0xd01fffff]
[    0.068854] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.068888] pci_bus 0000:00: on NUMA node 0
[    0.068892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.068963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.071033] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[    0.071118] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[    0.071200] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) *0, disabled.
[    0.071282] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *9
[    0.071363] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[    0.071445] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 11) *0, disabled.
[    0.071526] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[    0.071608] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[    0.071687] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[    0.071854] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.071858] vgaarb: loaded
[    0.072233] SCSI subsystem initialized
[    0.072356] libata version 3.00 loaded.
[    0.072453] usbcore: registered new interface driver usbfs
[    0.072471] usbcore: registered new interface driver hub
[    0.072520] usbcore: registered new device driver usb
[    0.072686] wmi: Mapper loaded
[    0.072689] PCI: Using ACPI for IRQ routing
[    0.072695] PCI: pci_cache_line_size set to 32 bytes
[    0.072735] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.072739] reserve RAM buffer: 000000003bef0000 - 000000003bffffff 
[    0.072923] NetLabel: Initializing
[    0.072926] NetLabel:  domain hash size = 128
[    0.072927] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.072952] NetLabel:  unlabeled traffic allowed by default
[    0.073011] Switching to clocksource pit
[    0.085654] AppArmor: AppArmor Filesystem Enabled
[    0.085735] pnp: PnP ACPI init
[    0.085772] ACPI: bus type pnp registered
[    0.086050] pnp 00:00: [bus 00-ff]
[    0.086055] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.086059] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.086062] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.086065] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.086068] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.086071] pnp 00:00: [mem 0x000d0000-0x000d7fff window]
[    0.086074] pnp 00:00: [mem 0x000a0000-0x000cefff window]
[    0.086077] pnp 00:00: [mem 0x3c000000-0xfff7ffff window]
[    0.086081] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.086084] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.086086] pnp 00:00: [io  0x0d00-0xffff window]
[    0.086196] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.086399] pnp 00:01: [io  0x0000-0x000f]
[    0.086403] pnp 00:01: [io  0x0081-0x008f]
[    0.086406] pnp 00:01: [io  0x00c0-0x00df]
[    0.086410] pnp 00:01: [dma 4]
[    0.086449] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.086476] pnp 00:02: [io  0x0070-0x0073]
[    0.086484] pnp 00:02: [irq 8]
[    0.086522] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.086536] pnp 00:03: [io  0x00f0-0x00fe]
[    0.086539] pnp 00:03: [irq 13]
[    0.086587] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.086600] pnp 00:04: [io  0x0061]
[    0.086638] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.086651] pnp 00:05: [io  0x0060]
[    0.086654] pnp 00:05: [io  0x0064]
[    0.086657] pnp 00:05: [irq 1]
[    0.086694] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.086707] pnp 00:06: [irq 12]
[    0.086748] pnp 00:06: Plug and Play ACPI device, IDs SYN0104 SYN0100 SYN0002 PNP0f13 (active)
[    0.086766] pnp 00:07: [io  0x0080]
[    0.086769] pnp 00:07: [io  0x00b0-0x00b3]
[    0.086771] pnp 00:07: [io  0x0092]
[    0.086774] pnp 00:07: [io  0x040b]
[    0.086776] pnp 00:07: [io  0x0480-0x048f]
[    0.086779] pnp 00:07: [io  0x04d0-0x04d1]
[    0.086781] pnp 00:07: [io  0x04d6]
[    0.086784] pnp 00:07: [io  0x8000-0x807f]
[    0.086786] pnp 00:07: [io  0xff00-0xff01]
[    0.086789] pnp 00:07: [io  0x8004-0x8005]
[    0.086791] pnp 00:07: [io  0xfe00-0xfefe]
[    0.086794] pnp 00:07: [mem 0xd0400000-0xd0400fff]
[    0.086832] pnp 00:07: disabling [io  0x8004-0x8005] because it overlaps 0000:00:11.0 BAR 13 [io  0x8000-0x803f]
[    0.086897] system 00:07: [io  0x040b] has been reserved
[    0.086901] system 00:07: [io  0x0480-0x048f] has been reserved
[    0.086904] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.086908] system 00:07: [io  0x04d6] has been reserved
[    0.086911] system 00:07: [io  0x8000-0x807f] could not be reserved
[    0.086915] system 00:07: [io  0xff00-0xff01] has been reserved
[    0.086918] system 00:07: [io  0xfe00-0xfefe] has been reserved
[    0.086923] system 00:07: [mem 0xd0400000-0xd0400fff] has been reserved
[    0.086928] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.087314] pnp 00:08: [io  0x03f0-0x03f5]
[    0.087318] pnp 00:08: [io  0x03f7]
[    0.087321] pnp 00:08: [irq 6]
[    0.087323] pnp 00:08: [dma 2]
[    0.087383] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.087745] pnp 00:09: [io  0x0378-0x037f]
[    0.087748] pnp 00:09: [io  0x0778-0x077f]
[    0.087752] pnp 00:09: [irq 7]
[    0.087754] pnp 00:09: [dma 0]
[    0.088037] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.088282] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.088285] pnp 00:0a: [irq 4]
[    0.088375] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.088684] pnp: PnP ACPI: found 11 devices
[    0.088687] ACPI: ACPI bus type pnp unregistered
[    0.088693] PnPBIOS: Disabled by ACPI PNP
[    0.125904] Switching to clocksource acpi_pm
[    0.125980] pci 0000:00:0a.0: BAR 15: assigned [mem 0x3c000000-0x3fffffff pref]
[    0.125986] pci 0000:00:0a.0: BAR 16: assigned [mem 0x40000000-0x43ffffff]
[    0.125991] pci 0000:00:12.0: BAR 6: assigned [mem 0x44000000-0x4400ffff pref]
[    0.125997] pci 0000:00:0a.0: BAR 0: assigned [mem 0x44010000-0x44010fff]
[    0.126004] pci 0000:00:0a.0: BAR 0: set to [mem 0x44010000-0x44010fff] (PCI address [0x44010000-0x44010fff])
[    0.126010] pci 0000:00:0a.0: BAR 13: assigned [io  0x1000-0x10ff]
[    0.126014] pci 0000:00:0a.0: BAR 14: assigned [io  0x1400-0x14ff]
[    0.126020] pci 0000:01:05.0: BAR 6: assigned [mem 0xd0120000-0xd013ffff pref]
[    0.126024] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.126029] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.126034] pci 0000:00:01.0:   bridge window [mem 0xd0100000-0xd01fffff]
[    0.126039] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.126046] pci 0000:00:0a.0: CardBus bridge to [bus 02-05]
[    0.126050] pci 0000:00:0a.0:   bridge window [io  0x1000-0x10ff]
[    0.126055] pci 0000:00:0a.0:   bridge window [io  0x1400-0x14ff]
[    0.126059] pci 0000:00:0a.0:   bridge window [mem 0x3c000000-0x3fffffff pref]
[    0.126064] pci 0000:00:0a.0:   bridge window [mem 0x40000000-0x43ffffff]
[    0.126083] pci 0000:00:0a.0: enabling device (0000 -> 0003)
[    0.126236] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    0.126241] PCI: setting IRQ 11 as level-triggered
[    0.126247] pci 0000:00:0a.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    0.126253] pci 0000:00:0a.0: setting latency timer to 64
[    0.126259] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.126262] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.126266] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.126269] pci_bus 0000:01: resource 1 [mem 0xd0100000-0xd01fffff]
[    0.126272] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff pref]
[    0.126276] pci_bus 0000:02: resource 0 [io  0x1000-0x10ff]
[    0.126279] pci_bus 0000:02: resource 1 [io  0x1400-0x14ff]
[    0.126282] pci_bus 0000:02: resource 2 [mem 0x3c000000-0x3fffffff pref]
[    0.126286] pci_bus 0000:02: resource 3 [mem 0x40000000-0x43ffffff]
[    0.126371] NET: Registered protocol family 2
[    0.126476] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.127004] Switched to NOHz mode on CPU #0
[    0.127156] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.130004] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.131431] TCP: Hash tables configured (established 131072 bind 65536)
[    0.131435] TCP reno registered
[    0.131442] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.131482] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.131701] NET: Registered protocol family 1
[    0.131728] pci 0000:00:00.0: ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb
[    0.348069] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    0.348101] pci 0000:01:05.0: Boot video device
[    0.348105] PCI: CLS 64 bytes, default 32
[    0.348277] Simple Boot Flag at 0x36 set to 0x1
[    0.348595] cpufreq-nforce2: No nForce2 chipset.
[    0.348820] audit: initializing netlink socket (disabled)
[    0.348841] type=2000 audit(1304859199.345:1): initialized
[    0.359405] Trying to unpack rootfs image as initramfs...
[    0.376980] highmem bounce pool size: 64 pages
[    0.376994] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.384750] VFS: Disk quotas dquot_6.5.2
[    0.384849] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.385852] fuse init (API version 7.16)
[    0.385981] msgmni has been set to 1706
[    0.392513] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.392567] io scheduler noop registered
[    0.392570] io scheduler deadline registered
[    0.392589] io scheduler cfq registered (default)
[    0.392818] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.392858] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.393251] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.393379] ACPI: AC Adapter [ACAD] (on-line)
[    0.393478] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.393491] ACPI: Power Button [PWRB]
[    0.393546] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.394747] ACPI: Lid Switch [LID]
[    0.394820] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.394825] ACPI: Power Button [PWRF]
[    0.394945] ACPI: acpi_idle registered with cpuidle
[    0.394987] Marking TSC unstable due to TSC halts in idle
[    0.400918] thermal LNXTHERM:00: registered as thermal_zone0
[    0.400925] ACPI: Thermal Zone [THRM] (58 C)
[    0.401015] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.401076] ERST: Table is not found!
[    0.401291] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.421876] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.424389] ACPI: Battery Slot [BAT1] (battery absent)
[    0.424432] isapnp: Scanning for PnP cards...
[    0.514191] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.536969] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[    0.536978] PCI: setting IRQ 3 as level-triggered
[    0.536986] serial 0000:00:08.0: PCI INT A -> Link[LNKG] -> GSI 3 (level, low) -> IRQ 3
[    0.536995] serial 0000:00:08.0: PCI INT A disabled
[    0.537266] Linux agpgart interface v0.103
[    0.539173] brd: module loaded
[    0.544225] loop: module loaded
[    0.544556] i2c-core: driver [adp5520] using legacy suspend method
[    0.544559] i2c-core: driver [adp5520] using legacy resume method
[    0.544886] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    0.545009] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    0.545540] Fixed MDIO Bus: probed
[    0.545610] PPP generic driver version 2.4.2
[    0.545674] tun: Universal TUN/TAP device driver, 1.6
[    0.545676] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.545799] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.545820] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.546098] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[    0.546103] PCI: setting IRQ 10 as level-triggered
[    0.546110] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LNKU] -> GSI 10 (level, low) -> IRQ 10
[    0.546142] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.546209] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    0.546257] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0002000
[    0.602490] hub 1-0:1.0: USB hub found
[    0.602505] hub 1-0:1.0: 4 ports detected
[    0.602629] uhci_hcd: USB Universal Host Controller Interface driver
[    0.602818] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.608453] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.608482] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.608814] mousedev: PS/2 mouse device common for all mice
[    0.609179] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.609211] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    0.609399] device-mapper: uevent: version 1.0.3
[    0.609501] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.612089] device-mapper: multipath: version 1.2.0 loaded
[    0.612096] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.612296] EISA: Probing bus 0 at eisa.0
[    0.612312] Cannot allocate resource for EISA slot 1
[    0.612343] Cannot allocate resource for EISA slot 8
[    0.612346] EISA: Detected 0 cards.
[    0.616272] cpuidle: using governor ladder
[    0.616332] cpuidle: using governor menu
[    0.616767] TCP cubic registered
[    0.616992] NET: Registered protocol family 10
[    0.617693] NET: Registered protocol family 17
[    0.617748] Registering the dns_resolver key type
[    0.617793] powernow-k8: Processor cpuid 6a0 not supported
[    0.617906] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[    0.624288] powernow: No PST tables match this cpuid (0x7a0)
[    0.624291] powernow: This is indicative of a broken BIOS.
[    0.624293] powernow: Trying ACPI perflib
[    0.624361] powernow: Minimum speed 530 MHz. Maximum speed 2120 MHz.
[    0.624417] Using IPI No-Shortcut mode
[    0.624657] PM: Hibernation image not present or could not be loaded.
[    0.624692] registered taskstats version 1
[    0.624906]   Magic number: 11:205:885
[    0.625133] rtc_cmos 00:02: setting system clock to 2011-05-08 12:53:22 UTC (1304859202)
[    0.625139] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.625141] EDD information not available.
[    0.643051] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.959924] isapnp: No Plug & Play device found
[    1.107754] Freeing initrd memory: 12520k freed
[    1.135745] Freeing unused kernel memory: 700k freed
[    1.137342] Write protecting the kernel text: 5192k
[    1.137387] Write protecting the kernel read-only data: 2148k
[    1.178750] <30>udev[59]: starting version 167
[    1.415269] pata_ali 0000:00:10.0: can't derive routing for PCI INT A
[    1.486269] scsi0 : pata_ali
[    1.488665] scsi1 : pata_ali
[    1.488940] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8080 irq 14
[    1.488945] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8088 irq 15
[    1.507459] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[    1.507463]   originally by Donald Becker <becker@scyld.com>
[    1.507465]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[    1.507782] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    1.507792] natsemi 0000:00:12.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.543574] FDC 0 is a post-1991 82077
[    1.544489] natsemi eth0: NatSemi DP8381[56] at 0xd0005000 (0000:00:12.0), 00:0f:20:21:31:93, IRQ 11, port TP.
[    1.652500] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD5A, max UDMA/100
[    1.652505] ata1.00: 117210240 sectors, multi 16: LBA48 
[    1.668370] ata1.00: configured for UDMA/100
[    1.668619] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[    1.668937] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.669194] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.669273] sd 0:0:0:0: [sda] Write Protect is off
[    1.669277] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.669311] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.718284]  sda: sda1 sda2 < sda5 >
[    1.718756] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.832341] ata2.00: ATAPI: SD-R2512, 1A04, max MWDMA2
[    1.832347] ata2.00: WARNING: ATAPI DMA disabled for reliability issues.  It can be enabled
[    1.832351] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    1.848235] ata2.00: configured for MWDMA2
[    1.854158] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2512 1A04 PQ: 0 ANSI: 5
[    1.858667] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.858673] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.858863] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.858985] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.310885] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.049409] ACPI: EC: GPE storm detected, transactions will use polling mode
[   17.422083] Adding 979964k swap on /dev/sda5.  Priority:-1 extents:1 across:979964k 
[   17.461596] <30>udev[254]: starting version 167
[   17.542082] lp: driver loaded but no devices found
[   17.618231] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.029765] agpgart-ati 0000:00:00.0: Ati IGP320/M chipset
[   18.030086] reserve_ram_pages_type failed 0x33743000-0x33744000, track 0x10, req 0x10
[   18.059581] reserve_ram_pages_type failed 0x337e2000-0x337e3000, track 0x10, req 0x10
[   18.060206] reserve_ram_pages_type failed 0x337f3000-0x337f4000, track 0x10, req 0x10
[   18.119631] type=1400 audit(1304859219.988:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=402 comm="apparmor_parser"
[   18.129741] type=1400 audit(1304859220.000:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=402 comm="apparmor_parser"
[   18.130086] type=1400 audit(1304859220.000:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=402 comm="apparmor_parser"
[   18.194297] reserve_ram_pages_type failed 0x30c77000-0x30c78000, track 0x10, req 0x10
[   18.194770] reserve_ram_pages_type failed 0x30ceb000-0x30cec000, track 0x10, req 0x10
[   18.195255] reserve_ram_pages_type failed 0x30cec000-0x30ced000, track 0x10, req 0x10
[   18.195742] reserve_ram_pages_type failed 0x30ced000-0x30cee000, track 0x10, req 0x10
[   18.362001] reserve_ram_pages_type failed 0x30d66000-0x30d67000, track 0x10, req 0x10
[   18.362490] reserve_ram_pages_type failed 0x30d88000-0x30d89000, track 0x10, req 0x10
[   18.362981] reserve_ram_pages_type failed 0x30d8d000-0x30d8e000, track 0x10, req 0x10
[   18.363470] reserve_ram_pages_type failed 0x30d8c000-0x30d8d000, track 0x10, req 0x10
[   18.363958] reserve_ram_pages_type failed 0x30d8b000-0x30d8c000, track 0x10, req 0x10
[   18.487999] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input4
[   18.489704] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   18.508687] reserve_ram_pages_type failed 0x30c07000-0x30c08000, track 0x10, req 0x10
[   18.509176] reserve_ram_pages_type failed 0x30c06000-0x30c07000, track 0x10, req 0x10
[   18.509665] reserve_ram_pages_type failed 0x30c05000-0x30c06000, track 0x10, req 0x10
[   18.510154] reserve_ram_pages_type failed 0x33754000-0x33755000, track 0x10, req 0x10
[   18.510632] reserve_ram_pages_type failed 0x336af000-0x336b0000, track 0x10, req 0x10
[   18.582024] eth0: DSPCFG accepted after 0 usec.
[   18.582037] eth0: link up.
[   18.582050] eth0: Setting full-duplex based on negotiated link capability.
[   18.600936] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[   18.601263] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.683373] parport_pc 00:09: reported by Plug and Play ACPI
[   18.683451] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   18.840453] lp0: using parport0 (interrupt-driven).
[   18.867060] yenta_cardbus 0000:00:0a.0: CardBus bridge found [103c:0024]
[   18.867083] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
[   18.867087] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
[   18.867093] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01111112, devctl 0x64
[   19.103031] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0038, PCI irq 11
[   19.103039] yenta_cardbus 0000:00:0a.0: Socket status: 30000006
[   19.386425] type=1400 audit(1304859221.256:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=569 comm="apparmor_parser"
[   19.399125] type=1400 audit(1304859221.268:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=570 comm="apparmor_parser"
[   19.400620] type=1400 audit(1304859221.272:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=570 comm="apparmor_parser"
[   19.400951] type=1400 audit(1304859221.272:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=570 comm="apparmor_parser"
[   19.450395] type=1400 audit(1304859221.320:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=571 comm="apparmor_parser"
[   19.462664] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008/0x0
[   19.502017] type=1400 audit(1304859221.372:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=571 comm="apparmor_parser"
[   19.514754] type=1400 audit(1304859221.384:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=571 comm="apparmor_parser"
[   19.575349] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   19.577167] [drm] Initialized drm 1.1.0 20060810
[   20.282808] ppdev: user-space parallel port driver
[   20.291902] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   20.295231] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   20.331293] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   20.341100] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   20.342008] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   20.342071] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   20.342134] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   20.342199] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   20.774888] [drm] radeon defaulting to kernel modesetting.
[   20.774900] [drm] radeon kernel modesetting enabled.
[   20.775059] radeon 0000:01:05.0: power state changed by ACPI to D0
[   20.775065] radeon 0000:01:05.0: power state changed by ACPI to D0
[   20.775320] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   20.775328] radeon 0000:01:05.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   20.794647] [drm] initializing kernel modesetting (RS100 0x1002:0x4336).
[   20.794713] [drm] register mmio base: 0xD0100000
[   20.794715] [drm] register mmio size: 65536
[   20.795074] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   20.795096] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   20.795137] radeon 0000:01:05.0: putting AGP V2 device into 4x mode
[   20.795142] radeon 0000:01:05.0: GTT: 64M 0xD4000000 - 0xD7FFFFFF
[   20.795153] radeon 0000:01:05.0: VRAM: 64M 0x000000003C000000 - 0x000000003FFFFFFF (64M used)
[   20.795166] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   20.795168] [drm] Driver supports precise vblank timestamp query.
[   20.795186] [drm] radeon: irq initialized.
[   20.795497] [drm] Detected VRAM RAM=64M, BAR=256M
[   20.795507] [drm] RAM width 64bits DDR
[   20.802371] [TTM] Zone  kernel: Available graphics memory: 443428 kiB.
[   20.802379] [TTM] Zone highmem: Available graphics memory: 479752 kiB.
[   20.802382] [TTM] Initializing pool allocator.
[   20.802442] [drm] radeon: 64M of VRAM memory ready
[   20.802446] [drm] radeon: 64M of GTT memory ready.
[   20.841751] radeon 0000:01:05.0: WB disabled
[   20.867177] [drm] Loading R100 Microcode
[   20.925027] [drm] radeon: ring at 0x00000000D4001000
[   20.925056] [drm] ring test succeeded in 1 usecs
[   20.927547] [drm] radeon: ib pool ready.
[   20.927676] [drm] ib test succeeded in 0 usecs
[   20.958706] [drm] Panel ID String: LGP                     
[   20.958714] [drm] Panel Size 1024x768
[   20.981321] [drm] Radeon Display Connectors
[   20.981328] [drm] Connector 0:
[   20.981330] [drm]   VGA
[   20.981334] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   20.981337] [drm]   Encoders:
[   20.981339] [drm]     CRT1: INTERNAL_DAC1
[   20.981341] [drm] Connector 1:
[   20.981343] [drm]   LVDS
[   20.981346] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   20.981348] [drm]   Encoders:
[   20.981350] [drm]     LCD1: INTERNAL_LVDS
[   20.981352] [drm] Connector 2:
[   20.981354] [drm]   S-video
[   20.981355] [drm]   Encoders:
[   20.981357] [drm]     TV1: INTERNAL_DAC2
[   21.052777] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   21.052787] PCI: setting IRQ 5 as level-triggered
[   21.052795] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNKH] -> GSI 5 (level, low) -> IRQ 5
[   21.316158] [drm] fb mappable at 0xE0040000
[   21.316165] [drm] vram apper at 0xE0000000
[   21.316167] [drm] size 3145728
[   21.316169] [drm] fb depth is 24
[   21.316171] [drm]    pitch is 4096
[   21.318773] Console: switching to colour frame buffer device 128x48
[   21.318841] fb0: radeondrmfb frame buffer device
[   21.318844] drm: registered panic notifier
[   21.318867] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[   22.120150] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.148040] AC'97 1 does not respond - RESET
[   24.164043] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   24.164057] ali mixer 1 creating error.
[   24.445773] audit_printk_skb: 15 callbacks suppressed
[   24.445780] type=1400 audit(1304859226.316:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1057 comm="apparmor_parser"
[   24.446521] type=1400 audit(1304859226.316:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1057 comm="apparmor_parser"
[   26.986767] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   28.848039] eth0: no IPv6 routers present

#Current sudo lshw -C network

  *-network:0 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:d0000000-d0001fff
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:21:31:93
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.0.198 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 ioport:8c00(size=256) memory:d0005000-d0005fff memory:44000000-4400ffff

#Current iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

#Current sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.


[/FONT]

---

### Post by YJA-LxDx-do on 2011-05-08
If I missed anything, please let me know.  Any advice would be very welcome.

---

### Post by Bernmeister on 2011-12-15
This may help: [http://ubuntuforums.org/showthread.php?p=11539545#post11539545]("http://ubuntuforums.org/showthread.php?p=11539545#post11539545")

---

### Post by praseodym on 2011-12-15
The driver is not loaded:

```
sudo modprobe -v b43legacy
```
Check:
```
iwconfig
sudo iwlist scan
rfkill list
dmesg | grep b43
```
If it works, force the driver being loaded at boot-up:

```
echo b43legacy | sudo tee -a /etc/modules
```

---

