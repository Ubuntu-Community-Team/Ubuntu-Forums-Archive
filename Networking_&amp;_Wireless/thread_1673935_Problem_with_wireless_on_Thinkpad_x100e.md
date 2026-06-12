---
title: "Problem with wireless on Thinkpad x100e"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by tejas.deshpande on 2011-01-23
Hi,

My house has a WPA secured wifi network running with WDS. 
The wifi works excellent on startup but after a while (ranging from 5 mins to 30 mins) it disconnects and is not able to reconnect.

The error it gives (i'm assuming this, I haven't checked any logs) is wrong password, since it asks me to re-enter my wifi password.

This problem sometime goes away when I do rmmod rtl8192se_pci and then modprobe rtl8192se_pci, but sometimes this just gives me an error that rtl8192se_pci does not exist.

This Problem only occurs on WPA, and not on WEP. Since my house is in a very busy place, It is not wise to use WEP. 

My WDS router uses Tomato firmware.

Can you tell me how to fix this?

Thanks! :)
lspci
```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
```
ifconfig
```


wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:b6:63:fb  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:feb6:63fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6223728 (6.2 MB)  TX bytes:398153 (398.1 KB)
          Interrupt:18 Memory:f8098000-f8098100 

```

lsmod

```

Module                  Size  Used by
michael_mic             1744  8 
arc4                    1165  4 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_hda_codec_conexant    29971  1 
snd_hda_intel          22107  2 
radeon                828445  3 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
thinkpad_acpi          67659  0 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
ttm                    56633  1 radeon
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
r8192se_pci           468428  0 
snd                    49038  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,thinkpad_acpi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
led_class               2633  1 thinkpad_acpi
psmouse                59033  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
video                  18712  0 
nvram                   6342  1 thinkpad_acpi
agpgart                32011  2 ttm,drm
i2c_algo_bit            5168  1 radeon
serio_raw               4022  0 
i2c_piix4               8635  0 
k8temp                  3228  0 
shpchp                 29886  0 
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  3 
usb_storage            40172  0 
libahci                21664  1 ahci
r8169                  36489  0 
mii                     4425  1 r8169

```

dmesg

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fed0000 (usable)
[    0.000000]  BIOS-e820: 000000006fed0000 - 000000006fedc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fedc000 - 000000006fede000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fede000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x6fed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006fed0000 (usable)
[    0.000000]  modified: 000000006fed0000 - 000000006fedc000 (ACPI data)
[    0.000000]  modified: 000000006fedc000 - 000000006fede000 (ACPI NVS)
[    0.000000]  modified: 000000006fede000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f7df0] f7df0
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375ac000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a7000 - 013ea251
[    0.000000] Move RAMDISK from 00000000375ac000 - 0000000037fef250 to 009a7000 - 013ea250
[    0.000000] ACPI: RSDP 000f7ac0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 6fed1fa9 00054 (v01 LENOVO TP-6X    00001290  LTP 00000000)
[    0.000000] ACPI: FACP 6fedbccf 000F4 (v03 LENOVO TP-6X    00001290 ATI  000F4240)
[    0.000000] ACPI: DSDT 6fed1ffd 09CD2 (v01 LENOVO TP-6X    00001290 MSFT 03000001)
[    0.000000] ACPI: FACS 6feddfc0 00040
[    0.000000] ACPI: TCPA 6fedbe37 00032 (v02 LENOVO TP-6X    00001290 PTEC 00000000)
[    0.000000] ACPI: SSDT 6fedbe69 000D3 (v01 LENOVO TP-6X    00001290 AMD  00000001)
[    0.000000] ACPI: APIC 6fedbf3c 00050 (v01 LENOVO TP-6X    00001290  LTP 00000000)
[    0.000000] ACPI: MCFG 6fedbf8c 0003C (v01 LENOVO TP-6X    00001290  LTP 00000000)
[    0.000000] ACPI: HPET 6fedbfc8 00038 (v01 LENOVO TP-6X    00001290  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 902MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0006fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0006fed0
[    0.000000] On node 0 totalpages: 458334
[    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c13ec020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1806 pages used for memmap
[    0.000000]   HighMem zone: 229316 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454752
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=8863d253-f43b-431d-a339-84e5cc9f8839 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9168940 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (50 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a3000 - 00009a6130]             BRK
[    0.000000]   #4 [00000f7e00 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f7df0 - 00000f7e00]    MP-table mpf
[    0.000000]   #6 [000009dc00 - 000009e071]   BIOS reserved
[    0.000000]   #7 [000009e1b1 - 00000f7df0]   BIOS reserved
[    0.000000]   #8 [000009e071 - 000009e1b1]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a7000 - 00013eb000]     NEW RAMDISK
[    0.000000]   #13 [00013eb000 - 00013ec000]         BOOTMEM
[    0.000000]   #14 [00013ec000 - 00021ec000]         BOOTMEM
[    0.000000]   #15 [00021ec000 - 00021ec004]         BOOTMEM
[    0.000000]   #16 [00021ec040 - 00021ec100]         BOOTMEM
[    0.000000]   #17 [00021ec100 - 00021ec154]         BOOTMEM
[    0.000000]   #18 [00021ec180 - 00021ef180]         BOOTMEM
[    0.000000]   #19 [00021ef180 - 00021ef1d8]         BOOTMEM
[    0.000000]   #20 [00021ef200 - 00021f2200]         BOOTMEM
[    0.000000]   #21 [00021f2200 - 00021f2225]         BOOTMEM
[    0.000000]   #22 [00021f2240 - 00021f2267]         BOOTMEM
[    0.000000]   #23 [00021f2280 - 00021f2408]         BOOTMEM
[    0.000000]   #24 [00021f2440 - 00021f2480]         BOOTMEM
[    0.000000]   #25 [00021f2480 - 00021f24c0]         BOOTMEM
[    0.000000]   #26 [00021f24c0 - 00021f2500]         BOOTMEM
[    0.000000]   #27 [00021f2500 - 00021f2540]         BOOTMEM
[    0.000000]   #28 [00021f2540 - 00021f2580]         BOOTMEM
[    0.000000]   #29 [00021f2580 - 00021f25c0]         BOOTMEM
[    0.000000]   #30 [00021f25c0 - 00021f2600]         BOOTMEM
[    0.000000]   #31 [00021f2600 - 00021f2640]         BOOTMEM
[    0.000000]   #32 [00021f2640 - 00021f2680]         BOOTMEM
[    0.000000]   #33 [00021f2680 - 00021f26c0]         BOOTMEM
[    0.000000]   #34 [00021f26c0 - 00021f2700]         BOOTMEM
[    0.000000]   #35 [00021f2700 - 00021f2710]         BOOTMEM
[    0.000000]   #36 [00021f2740 - 00021f2750]         BOOTMEM
[    0.000000]   #37 [00021f2780 - 00021f27ea]         BOOTMEM
[    0.000000]   #38 [00021f2800 - 00021f286a]         BOOTMEM
[    0.000000]   #39 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #40 [00021f4880 - 00021f4884]         BOOTMEM
[    0.000000]   #41 [00021f48c0 - 00021f48c4]         BOOTMEM
[    0.000000]   #42 [00021f4900 - 00021f4904]         BOOTMEM
[    0.000000]   #43 [00021f4940 - 00021f4944]         BOOTMEM
[    0.000000]   #44 [00021f4980 - 00021f4a30]         BOOTMEM
[    0.000000]   #45 [00021f4a40 - 00021f4ae8]         BOOTMEM
[    0.000000]   #46 [00021f4b00 - 00021f8b00]         BOOTMEM
[    0.000000]   #47 [00021f8b00 - 0002278b00]         BOOTMEM
[    0.000000]   #48 [0002278b00 - 00022b8b00]         BOOTMEM
[    0.000000]   #49 [000240e000 - 0002ccc82c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0006fed0)
[    0.000000] Memory: 1789768k/1833792k available (4931k kernel code, 43568k reserved, 2333k data, 688k init, 924488k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
[    0.000000]       .data : 0xc05d0ebe - 0xc08184e8   (2333 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d0ebe   (4931 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.997 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.99 BogoMIPS (lpj=6383988)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004045] Security Framework initialized
[    0.004072] AppArmor: AppArmor initialized
[    0.004075] Yama: becoming mindful.
[    0.004160] Mount-cache hash table entries: 512
[    0.004325] Initializing cgroup subsys ns
[    0.004330] Initializing cgroup subsys cpuacct
[    0.004338] Initializing cgroup subsys memory
[    0.004350] Initializing cgroup subsys devices
[    0.004355] Initializing cgroup subsys freezer
[    0.004359] Initializing cgroup subsys net_cls
[    0.004393] mce: CPU supports 5 MCE banks
[    0.004405] using C1E aware idle routine
[    0.004414] Performance Events: AMD PMU driver.
[    0.004425] ... version:                0
[    0.004429] ... bit width:              48
[    0.004432] ... generic registers:      4
[    0.004436] ... value mask:             0000ffffffffffff
[    0.004440] ... max period:             00007fffffffffff
[    0.004443] ... fixed-purpose events:   0
[    0.004447] ... event mask:             000000000000000f
[    0.005507] SMP alternatives: switching to UP code
[    0.015753] Freeing SMP alternatives: 24k freed
[    0.015776] ACPI: Core revision 20100428
[    0.036030] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036042] ftrace: allocating 21756 entries in 43 pages
[    0.040081] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040541] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081264] CPU0: AMD Athlon(tm) Neo Processor MV-40 stepping 02
[    0.084000] Brought up 1 CPUs
[    0.084000] Total of 1 processors activated (3191.99 BogoMIPS).
[    0.084000] devtmpfs: initialized
[    0.084000] regulator: core version 0.5
[    0.084000] Time: 16:36:18  Date: 01/23/11
[    0.084000] NET: Registered protocol family 16
[    0.084000] EISA bus registered
[    0.084000] node 0 link 0: io port [1000, ffff]
[    0.084000] TOM: 0000000080000000 aka 2048M
[    0.084000] node 0 link 0: mmio [a0000, bffff]
[    0.084000] node 0 link 0: mmio [80000000, bfffffff]
[    0.084000] node 0 link 0: mmio [c0000000, cfffffff]
[    0.084000] node 0 link 0: mmio [d0000000, d00fffff]
[    0.084000] node 0 link 0: mmio [d0100000, d02fffff]
[    0.084000] node 0 link 0: mmio [d0300000, dfffffff]
[    0.084000] node 0 link 0: mmio [e0000000, efffffff]
[    0.084000] node 0 link 0: mmio [f0000000, ffffffff]
[    0.084000] bus: [00, ff] on node 0 link 0
[    0.084000] bus: 00 index 0 [io  0x0000-0xffff]
[    0.084000] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.084000] bus: 00 index 2 [mem 0x80000000-0xffffffff]
[    0.084000] ACPI: bus type pci registered
[    0.084000] PCI: MMCONFIG for domain 0000 [bus 00-03] at [mem 0xe0000000-0xe03fffff] (base 0xe0000000)
[    0.084000] PCI: MMCONFIG at [mem 0xe0000000-0xe03fffff] reserved in E820
[    0.084000] PCI: Using MMCONFIG for extended config space
[    0.084000] PCI: Using configuration type 1 for base access
[    0.084000] bio: create slab <bio-0> at 0
[    0.085900] ACPI: EC: Look up EC in DSDT
[    0.092049] ACPI: BIOS _OSI(Linux) query ignored
[    0.096218] ACPI: Interpreter enabled
[    0.096223] ACPI: (supports S0 S3 S4 S5)
[    0.096254] ACPI: Using IOAPIC for interrupt routing
[    0.113096] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.116555] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.116864] ACPI: No dock devices found.
[    0.116868] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.118856] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.123068] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.123073] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d1fff]
[    0.123077] pci_root PNP0A08:00: host bridge window [mem 0x000d2000-0x000d3fff]
[    0.123081] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d5fff]
[    0.123085] pci_root PNP0A08:00: host bridge window [mem 0x000d6000-0x000d7fff]
[    0.123088] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000d9fff]
[    0.123092] pci_root PNP0A08:00: host bridge window [mem 0x000da000-0x000dbfff]
[    0.123096] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000ddfff]
[    0.123100] pci_root PNP0A08:00: host bridge window [mem 0x000de000-0x000dffff]
[    0.123105] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.123109] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff]
[    0.123113] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.123117] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.123336] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.123340] pci 0000:00:05.0: PME# disabled
[    0.123398] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.123402] pci 0000:00:06.0: PME# disabled
[    0.123527] pci 0000:00:11.0: reg 10: [io  0x8420-0x8427]
[    0.123536] pci 0000:00:11.0: reg 14: [io  0x8414-0x8417]
[    0.123545] pci 0000:00:11.0: reg 18: [io  0x8418-0x841f]
[    0.123554] pci 0000:00:11.0: reg 1c: [io  0x8410-0x8413]
[    0.123562] pci 0000:00:11.0: reg 20: [io  0x8400-0x840f]
[    0.123571] pci 0000:00:11.0: reg 24: [mem 0xd0607000-0xd06073ff]
[    0.123634] pci 0000:00:12.0: reg 10: [mem 0xd0604000-0xd0604fff]
[    0.123699] pci 0000:00:12.1: reg 10: [mem 0xd0605000-0xd0605fff]
[    0.123777] pci 0000:00:12.2: reg 10: [mem 0xd0607400-0xd06074ff]
[    0.123839] pci 0000:00:12.2: supports D1 D2
[    0.123842] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.123847] pci 0000:00:12.2: PME# disabled
[    0.123885] pci 0000:00:13.0: reg 10: [mem 0xd0606000-0xd0606fff]
[    0.123964] pci 0000:00:13.2: reg 10: [mem 0xd0607800-0xd06078ff]
[    0.124034] pci 0000:00:13.2: supports D1 D2
[    0.124037] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.124042] pci 0000:00:13.2: PME# disabled
[    0.124179] pci 0000:00:14.2: reg 10: [mem 0xd0600000-0xd0603fff 64bit]
[    0.124230] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.124235] pci 0000:00:14.2: PME# disabled
[    0.124477] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.124483] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.124489] pci 0000:01:05.0: reg 18: [mem 0xd0200000-0xd020ffff]
[    0.124499] pci 0000:01:05.0: reg 24: [mem 0xd0100000-0xd01fffff]
[    0.124517] pci 0000:01:05.0: supports D1 D2
[    0.124630] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.124636] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.124640] pci 0000:00:01.0:   bridge window [mem 0xd0100000-0xd02fffff]
[    0.124647] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.124746] pci 0000:02:00.0: reg 10: [io  0xa000-0xa0ff]
[    0.124765] pci 0000:02:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.124784] pci 0000:02:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.124793] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.124833] pci 0000:02:00.0: supports D1 D2
[    0.124836] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124846] pci 0000:02:00.0: PME# disabled
[    0.132054] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.132059] pci 0000:00:05.0:   bridge window [io  0xa000-0xafff]
[    0.132064] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.132071] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.132179] pci 0000:03:00.0: reg 10: [io  0xb000-0xb0ff]
[    0.132187] pci 0000:03:00.0: reg 14: [mem 0xd0300000-0xd0303fff]
[    0.132293] pci 0000:03:00.0: supports D1 D2
[    0.132296] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    0.132353] pci 0000:03:00.0: PME# disabled
[    0.140089] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.140095] pci 0000:00:06.0:   bridge window [io  0xb000-0xbfff]
[    0.140099] pci 0000:00:06.0:   bridge window [mem 0xd0300000-0xd03fffff]
[    0.140105] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.140212] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    0.140219] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.140225] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.140232] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.140236] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.140240] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d1fff] (subtractive decode)
[    0.140244] pci 0000:00:14.4:   bridge window [mem 0x000d2000-0x000d3fff] (subtractive decode)
[    0.140248] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d5fff] (subtractive decode)
[    0.140252] pci 0000:00:14.4:   bridge window [mem 0x000d6000-0x000d7fff] (subtractive decode)
[    0.140256] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000d9fff] (subtractive decode)
[    0.140260] pci 0000:00:14.4:   bridge window [mem 0x000da000-0x000dbfff] (subtractive decode)
[    0.140264] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000ddfff] (subtractive decode)
[    0.140268] pci 0000:00:14.4:   bridge window [mem 0x000de000-0x000dffff] (subtractive decode)
[    0.140272] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.140276] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.140279] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.140283] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.140366] pci_bus 0000:00: on NUMA node 0
[    0.140374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.140646] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.140800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.140986] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.145606] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.145901] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.146194] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.146486] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.146778] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.147071] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.147363] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.147655] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.147785] HEST: Table is not found!
[    0.147893] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.147898] vgaarb: loaded
[    0.148111] SCSI subsystem initialized
[    0.148176] libata version 3.00 loaded.
[    0.148241] usbcore: registered new interface driver usbfs
[    0.148257] usbcore: registered new interface driver hub
[    0.148287] usbcore: registered new device driver usb
[    0.148590] ACPI: WMI: Mapper loaded
[    0.148593] PCI: Using ACPI for IRQ routing
[    0.148597] PCI: pci_cache_line_size set to 64 bytes
[    0.148883] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.148886] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.148890] reserve RAM buffer: 000000006fed0000 - 000000006fffffff 
[    0.148998] NetLabel: Initializing
[    0.149000] NetLabel:  domain hash size = 128
[    0.149002] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.149018] NetLabel:  unlabeled traffic allowed by default
[    0.149096] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.149103] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.151134] Switching to clocksource tsc
[    0.159652] AppArmor: AppArmor Filesystem Enabled
[    0.159672] pnp: PnP ACPI init
[    0.159692] ACPI: bus type pnp registered
[    0.165578] pnp: PnP ACPI: found 11 devices
[    0.165581] ACPI: ACPI bus type pnp unregistered
[    0.165585] PnPBIOS: Disabled by ACPI PNP
[    0.165601] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.165605] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.165615] system 00:08: [io  0x0220-0x022f] has been reserved
[    0.165619] system 00:08: [io  0x040b] has been reserved
[    0.165622] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.165626] system 00:08: [io  0x04d6] has been reserved
[    0.165630] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.165634] system 00:08: [io  0x0700-0x070f] has been reserved
[    0.165637] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.165641] system 00:08: [io  0x0c14] has been reserved
[    0.165645] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.165649] system 00:08: [io  0x0c6c] has been reserved
[    0.165652] system 00:08: [io  0x0c6f] has been reserved
[    0.165656] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.165660] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.165664] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.165668] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.165672] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.165676] system 00:08: [io  0x8000-0x805f] has been reserved
[    0.165680] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.165684] system 00:08: [io  0x8200-0x82ff window] has been reserved
[    0.165688] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.165692] system 00:08: [io  0x087f] has been reserved
[    0.165699] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.165704] system 00:09: [mem 0xfff00000-0xffffffff] has been reserved
[    0.165708] system 00:09: [mem 0xffc00000-0xffefffff] has been reserved
[    0.165712] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.202908] pci 0000:00:05.0: BAR 14: assigned [mem 0x80000000-0x800fffff]
[    0.202914] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.202918] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.202923] pci 0000:00:01.0:   bridge window [mem 0xd0100000-0xd02fffff]
[    0.202928] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.202935] pci 0000:02:00.0: BAR 6: assigned [mem 0xd0020000-0xd003ffff pref]
[    0.202939] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.202943] pci 0000:00:05.0:   bridge window [io  0xa000-0xafff]
[    0.202948] pci 0000:00:05.0:   bridge window [mem 0x80000000-0x800fffff]
[    0.202953] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.202959] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.202963] pci 0000:00:06.0:   bridge window [io  0xb000-0xbfff]
[    0.202968] pci 0000:00:06.0:   bridge window [mem 0xd0300000-0xd03fffff]
[    0.202972] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.202978] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    0.202980] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.203052] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.203057] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.203077]   alloc irq_desc for 17 on node -1
[    0.203080]   alloc kstat_irqs on node -1
[    0.203088] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.203092] pci 0000:00:05.0: setting latency timer to 64
[    0.203099]   alloc irq_desc for 18 on node -1
[    0.203102]   alloc kstat_irqs on node -1
[    0.203107] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.203111] pci 0000:00:06.0: setting latency timer to 64
[    0.203122] pci_bus 0000:00: resource 4 [mem 0x000a0000-0x000bffff]
[    0.203125] pci_bus 0000:00: resource 5 [mem 0x000d0000-0x000d1fff]
[    0.203129] pci_bus 0000:00: resource 6 [mem 0x000d2000-0x000d3fff]
[    0.203132] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d5fff]
[    0.203136] pci_bus 0000:00: resource 8 [mem 0x000d6000-0x000d7fff]
[    0.203139] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000d9fff]
[    0.203143] pci_bus 0000:00: resource 10 [mem 0x000da000-0x000dbfff]
[    0.203147] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000ddfff]
[    0.203150] pci_bus 0000:00: resource 12 [mem 0x000de000-0x000dffff]
[    0.203154] pci_bus 0000:00: resource 13 [mem 0x80000000-0xdfffffff]
[    0.203157] pci_bus 0000:00: resource 14 [mem 0xf0000000-0xffffffff]
[    0.203161] pci_bus 0000:00: resource 15 [io  0x0000-0x0cf7]
[    0.203164] pci_bus 0000:00: resource 16 [io  0x0d00-0xffff]
[    0.203168] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.203171] pci_bus 0000:01: resource 1 [mem 0xd0100000-0xd02fffff]
[    0.203175] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.203179] pci_bus 0000:02: resource 0 [io  0xa000-0xafff]
[    0.203182] pci_bus 0000:02: resource 1 [mem 0x80000000-0x800fffff]
[    0.203186] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.203190] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.203193] pci_bus 0000:03: resource 1 [mem 0xd0300000-0xd03fffff]
[    0.203197] pci_bus 0000:04: resource 4 [mem 0x000a0000-0x000bffff]
[    0.203201] pci_bus 0000:04: resource 5 [mem 0x000d0000-0x000d1fff]
[    0.203204] pci_bus 0000:04: resource 6 [mem 0x000d2000-0x000d3fff]
[    0.203208] pci_bus 0000:04: resource 7 [mem 0x000d4000-0x000d5fff]
[    0.203211] pci_bus 0000:04: resource 8 [mem 0x000d6000-0x000d7fff]
[    0.203215] pci_bus 0000:04: resource 9 [mem 0x000d8000-0x000d9fff]
[    0.203218] pci_bus 0000:04: resource 10 [mem 0x000da000-0x000dbfff]
[    0.203222] pci_bus 0000:04: resource 11 [mem 0x000dc000-0x000ddfff]
[    0.203226] pci_bus 0000:04: resource 12 [mem 0x000de000-0x000dffff]
[    0.203229] pci_bus 0000:04: resource 13 [mem 0x80000000-0xdfffffff]
[    0.203233] pci_bus 0000:04: resource 14 [mem 0xf0000000-0xffffffff]
[    0.203236] pci_bus 0000:04: resource 15 [io  0x0000-0x0cf7]
[    0.203240] pci_bus 0000:04: resource 16 [io  0x0d00-0xffff]
[    0.203287] NET: Registered protocol family 2
[    0.203356] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.203699] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.204423] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.204794] TCP: Hash tables configured (established 131072 bind 65536)
[    0.204798] TCP reno registered
[    0.204802] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.204817] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.204936] NET: Registered protocol family 1
[    0.204952] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.205121] pci 0000:01:05.0: Boot video device
[    0.205182] PCI: CLS 32 bytes, default 64
[    0.205413] cpufreq-nforce2: No nForce2 chipset.
[    0.205449] Scanning for low memory corruption every 60 seconds
[    0.205622] audit: initializing netlink socket (disabled)
[    0.205633] type=2000 audit(1295800578.204:1): initialized
[    0.219738] Trying to unpack rootfs image as initramfs...
[    0.237401] highmem bounce pool size: 64 pages
[    0.237410] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.244882] VFS: Disk quotas dquot_6.5.2
[    0.244976] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.245725] fuse init (API version 7.14)
[    0.245839] msgmni has been set to 1690
[    0.253537] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.253543] io scheduler noop registered
[    0.253545] io scheduler deadline registered
[    0.253564] io scheduler cfq registered (default)
[    0.253702] pcieport 0000:00:05.0: setting latency timer to 64
[    0.253736]   alloc irq_desc for 40 on node -1
[    0.253739]   alloc kstat_irqs on node -1
[    0.253749] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    0.253829] pcieport 0000:00:06.0: setting latency timer to 64
[    0.253859]   alloc irq_desc for 41 on node -1
[    0.253862]   alloc kstat_irqs on node -1
[    0.253868] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    0.253971] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.254002] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.353450] ACPI: AC Adapter [ACAD] (on-line)
[    0.353540] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.353547] ACPI: Power Button [PWRB]
[    0.353601] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.353606] ACPI: Sleep Button [SLPB]
[    0.353681] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.354396] ACPI: Lid Switch [LID]
[    0.354457] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.354461] ACPI: Power Button [PWRF]
[    0.354754] ACPI: acpi_idle registered with cpuidle
[    0.354786] Marking TSC unstable due to TSC halts in idle
[    0.359188] Switching to clocksource hpet
[    0.361609] thermal LNXTHERM:01: registered as thermal_zone0
[    0.361619] ACPI: Thermal Zone [TZ00] (69 C)
[    0.361710] ERST: Table is not found!
[    0.362198] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.364166] brd: module loaded
[    0.364836] loop: module loaded
[    0.365532] Fixed MDIO Bus: probed
[    0.365578] PPP generic driver version 2.4.2
[    0.365628] tun: Universal TUN/TAP device driver, 1.6
[    0.365631] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.365718] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.365813] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.365834] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.365878] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.365986] ehci_hcd 0000:00:12.2: debug port 1
[    0.366016] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd0607400
[    0.372754] isapnp: Scanning for PnP cards...
[    0.378472] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.378633] hub 1-0:1.0: USB hub found
[    0.378640] hub 1-0:1.0: 6 ports detected
[    0.378865]   alloc irq_desc for 19 on node -1
[    0.378869]   alloc kstat_irqs on node -1
[    0.378877] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.378900] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.378951] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.379056] ehci_hcd 0000:00:13.2: debug port 1
[    0.379085] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd0607800
[    0.437283] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.437469] hub 2-0:1.0: USB hub found
[    0.437476] hub 2-0:1.0: 6 ports detected
[    0.437633] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.437709]   alloc irq_desc for 16 on node -1
[    0.437711]   alloc kstat_irqs on node -1
[    0.437720] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.437744] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.437846] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.437884] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd0604000
[    0.500634] hub 3-0:1.0: USB hub found
[    0.500674] hub 3-0:1.0: 3 ports detected
[    0.500827] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.500851] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.500900] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.501000] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd0605000
[    0.564672] hub 4-0:1.0: USB hub found
[    0.564748] hub 4-0:1.0: 3 ports detected
[    0.564834] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.564862] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.564916] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.565020] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd0606000
[    0.676379] hub 5-0:1.0: USB hub found
[    0.676449] hub 5-0:1.0: 3 ports detected
[    0.676539] uhci_hcd: USB Universal Host Controller Interface driver
[    0.676649] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.683685] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.693449] ACPI: Battery Slot [BAT1] (battery present)
[    0.696607] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.696617] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.696658] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.696691] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.696720] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.696872] mice: PS/2 mouse device common for all mice
[    0.697198] rtc_cmos 00:04: RTC can wake from S4
[    0.697258] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.697324] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.697465] device-mapper: uevent: version 1.0.3
[    0.700640] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.704246] device-mapper: multipath: version 1.1.1 loaded
[    0.704251] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.708596] EISA: Probing bus 0 at eisa.0
[    0.708601] EISA: Cannot allocate resource for mainboard
[    0.708605] Cannot allocate resource for EISA slot 1
[    0.708608] Cannot allocate resource for EISA slot 2
[    0.708611] Cannot allocate resource for EISA slot 3
[    0.708614] Cannot allocate resource for EISA slot 4
[    0.708617] Cannot allocate resource for EISA slot 5
[    0.708621] Cannot allocate resource for EISA slot 6
[    0.708624] Cannot allocate resource for EISA slot 7
[    0.708627] Cannot allocate resource for EISA slot 8
[    0.708630] EISA: Detected 0 cards.
[    0.711695] cpuidle: using governor ladder
[    0.711772] cpuidle: using governor menu
[    0.712214] TCP cubic registered
[    0.712373] NET: Registered protocol family 10
[    0.712786] lo: Disabled Privacy Extensions
[    0.713053] NET: Registered protocol family 17
[    0.713087] powernow-k8: Found 1 AMD Athlon(tm) Neo Processor MV-40 (1 cpu cores) (version 2.20.00)
[    0.713140] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x14
[    0.713143] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
[    0.713192] Using IPI No-Shortcut mode
[    0.713312] PM: Resume from disk failed.
[    0.713329] registered taskstats version 1
[    0.713679]   Magic number: 11:973:641
[    0.713840] rtc_cmos 00:04: setting system clock to 2011-01-23 16:36:19 UTC (1295800579)
[    0.713844] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.713847] EDD information not available.
[    0.737354] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.795393] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    0.936557] Freeing initrd memory: 10512k freed
[    1.083245] isapnp: No Plug & Play device found
[    1.083274] Freeing unused kernel memory: 688k freed
[    1.083825] Write protecting the kernel text: 4932k
[    1.083865] Write protecting the kernel read-only data: 1980k
[    1.106654] udev[65]: starting version 163
[    1.359055] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.359111] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.359157] r8169 0000:02:00.0: setting latency timer to 64
[    1.359197]   alloc irq_desc for 42 on node -1
[    1.359200]   alloc kstat_irqs on node -1
[    1.359219] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.359848] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf8092000, c8:0a:a9:b0:a6:65, XID 081000c0 IRQ 42
[    1.464046] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    1.508864] ahci 0000:00:11.0: version 3.0
[    1.508952]   alloc irq_desc for 22 on node -1
[    1.508955]   alloc kstat_irqs on node -1
[    1.508964] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.509057] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    1.509063] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.509340] scsi0 : ahci
[    1.509660] ata1: SATA max UDMA/133 abar m1024@0xd0607000 port 0xd0607100 irq 22
[    1.510354] Initializing USB Mass Storage driver...
[    1.510493] scsi1 : usb-storage 2-1:1.0
[    1.510703] usbcore: registered new interface driver usb-storage
[    1.510706] USB Mass Storage support registered.
[    2.000114] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.055391] ata1.00: ATA-8: ST9250315AS, 0020LVM1, max UDMA/100
[    2.055396] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.057480] ata1.00: configured for UDMA/100
[    2.072218] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0020 PQ: 0 ANSI: 5
[    2.072413] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.072679] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.072740] sd 0:0:0:0: [sda] Write Protect is off
[    2.072744] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.072770] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.072930]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    2.151746] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.510473] scsi 1:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.511832] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.518462] sd 1:0:0:0: [sdb] Attached SCSI removable disk
[    2.856796] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   13.889544] udev[344]: starting version 163
[   13.902114] Adding 2928636k swap on /dev/sda7.  Priority:-1 extents:1 across:2928636k 
[   14.001710] lp: driver loaded but no devices found
[   14.223481] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[   14.223488] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   14.223622] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.297432] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   14.314707] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[   14.395504] Non-volatile memory driver v1.3
[   14.399374] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   14.608162] acpi device:20: registered as cooling_device1
[   14.608372] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1f/LNXVIDEO:00/input/input5
[   14.608438] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.745761] Linux agpgart interface v0.103
[   14.757248] rtllib_crypt: registered algorithm 'NULL'
[   14.757253] rtllib_crypt: registered algorithm 'TKIP'
[   14.757256] rtllib_crypt: registered algorithm 'CCMP'
[   14.757259] rtllib_crypt: registered algorithm 'WEP'
[   14.757261] 
[   14.757262] Linux kernel driver for RTL8192 based WLAN cards
[   14.757264] Copyright (c) 2007-2008, Realsil Wlan Driver
[   14.757361] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.757417] rtl819xSE 0000:03:00.0: setting latency timer to 64
[   14.760733] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   14.775665] Linux video capture interface: v2.00
[   14.790905] Memory mapped space start: 0xd0300000 
[   14.792151] GetPciBusInfo(): Find Device(10EC:8172)  bus=3 dev=0, func=0
[   14.792322] GetPciBridegInfo : Find Device(1022:9606)  bus=0 dev=6, func=0
[   14.792325] Pci Bridge Vendor is found index: 2
[   14.792328] Pci Bridge Vendor is 1022
[   14.808299] =========>dm_InitRateAdaptiveMask: bUseRAMask=0
[   14.820940] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b1b4)
[   14.839631] input: Integrated Camera as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input6
[   14.840547] usbcore: registered new interface driver uvcvideo
[   14.840550] USB Video Class driver (v0.1.0)
[   15.043336] type=1400 audit(1295780793.824:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=638 comm="apparmor_parser"
[   15.043725] type=1400 audit(1295780793.824:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=638 comm="apparmor_parser"
[   15.043949] type=1400 audit(1295780793.824:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=638 comm="apparmor_parser"
[   15.066853] [drm] Initialized drm 1.1.0 20060810
[   15.215214] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   15.336393] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   15.336398] thinkpad_acpi: http://ibm-acpi.sf.net/
[   15.336401] thinkpad_acpi: ThinkPad BIOS 6XET46WW (1.29 ), EC 6XHT42WW-1.182000
[   15.336404] thinkpad_acpi: Lenovo ThinkPad X100e, model 35084CQ
[   15.353160] thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[   15.353302] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   15.353321] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   15.353324] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   15.356335] thinkpad_acpi: asked for hotkey mask 0x040808fc, but firmware forced it to 0x000808fc
[   15.413913] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[   15.416713] Registered led device: tpacpi::thinklight
[   15.418537] Registered led device: tpacpi::power
[   15.418737] Registered led device: tpacpi::standby
[   15.421150] Registered led device: tpacpi::thinkvantage
[   15.485120] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[   15.485243] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   15.495635] [drm] radeon defaulting to kernel modesetting.
[   15.495640] [drm] radeon kernel modesetting enabled.
[   15.495736] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.495743] radeon 0000:01:05.0: setting latency timer to 64
[   15.505130] [drm] initializing kernel modesetting (RS780 0x1002:0x9612).
[   15.515325] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[   15.518859] [drm] register mmio base: 0xD0200000
[   15.518864] [drm] register mmio size: 65536
[   15.519062] ATOM BIOS: Lenovo_FL3B
[   15.519087] [drm] Clocks initialized !
[   15.519101] radeon 0000:01:05.0: VRAM: 336M 0xC0000000 - 0xD4FFFFFF (336M used)
[   15.519105] radeon 0000:01:05.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
[   15.519244] [drm] Detected VRAM RAM=336M, BAR=256M
[   15.519249] [drm] RAM width 32bits DDR
[   15.528248] [TTM] Zone  kernel: Available graphics memory: 438252 kiB.
[   15.528252] [TTM] Zone highmem: Available graphics memory: 900496 kiB.
[   15.528256] [TTM] Initializing pool allocator.
[   15.528281] [drm] radeon: 336M of VRAM memory ready
[   15.528284] [drm] radeon: 512M of GTT memory ready.
[   15.528325] [drm] radeon: irq initialized.
[   15.528329] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   15.530084] [drm] Loading RS780 Microcode
[   15.558430] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.641607] [drm] ring test succeeded in 1 usecs
[   15.641872] [drm] radeon: ib pool ready.
[   15.642144] [drm] ib test succeeded in 0 usecs
[   15.642148] [drm] Enabling audio support
[   15.646889] [drm] Default TV standard: NTSC
[   15.648712] [drm] Radeon Display Connectors
[   15.648717] [drm] Connector 0:
[   15.648719] [drm]   LVDS
[   15.648723] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   15.648726] [drm]   Encoders:
[   15.648728] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[   15.648731] [drm] Connector 1:
[   15.648733] [drm]   VGA
[   15.648736] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   15.648738] [drm]   Encoders:
[   15.648741] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.809452] [drm] radeon: power management initialized
[   15.913730] [drm] fb mappable at 0xC0141000
[   15.913733] [drm] vram apper at 0xC0000000
[   15.913735] [drm] size 4325376
[   15.913737] [drm] fb depth is 24
[   15.913739] [drm]    pitch is 5632
[   15.984681] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd047b1/0xb40000/0xa0000
[   15.984684] Synaptics: Clickpad mode enabled
[   15.984690] serio: Synaptics pass-through port at isa0060/serio4/input0
[   16.031346] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   16.866301] Console: switching to colour frame buffer device 170x48
[   16.882128] fb0: radeondrmfb frame buffer device
[   16.882130] drm: registered panic notifier
[   16.882353] Slow work thread pool: Starting up
[   16.882416] Slow work thread pool: Ready
[   16.882424] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[   18.702173] type=1400 audit(1295780797.484:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=872 comm="apparmor_parser"
[   18.702695] type=1400 audit(1295780797.484:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=872 comm="apparmor_parser"
[   18.809215] type=1400 audit(1295780797.592:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=898 comm="apparmor_parser"
[   18.842742] type=1400 audit(1295780797.624:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=902 comm="apparmor_parser"
[   18.843150] type=1400 audit(1295780797.624:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=902 comm="apparmor_parser"
[   18.843376] type=1400 audit(1295780797.624:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=902 comm="apparmor_parser"
[   18.848866] ppdev: user-space parallel port driver
[   18.902952] r8169 0000:02:00.0: eth0: link down
[   18.903773] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.004551] type=1400 audit(1295780797.788:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=905 comm="apparmor_parser"
[   19.163723] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   19.163728] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   19.163731] HW_VAR_MRC: Turn on 1T1R MRC!
[   19.277060] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.458672] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   19.458677] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   19.458680] HW_VAR_MRC: Turn on 1T1R MRC!
[   19.460212] psmouse serio5: ID: 10 00 64
[   24.034892] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   24.056578] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   24.266072] ===>rtllib_wx_set_power(): power disable
[   24.387283] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   24.662885] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/serio5/input/input9
[   36.321736] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   36.321742] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   36.321745] HW_VAR_MRC: Turn on 1T1R MRC!
[   39.488911] Linking with KDWireless,channel:6, qos:1, myHT:1, networkHT:0, mode:4 cur_net.flags:0x40a
[   39.488927] Linking with KDWireless,channel:6, qos:1, myHT:1, networkHT:0, mode:4 cur_net.flags:0x40a
[   39.489530] rtllib_associate_procedure_wq(), chan:6
[   39.489534] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   39.499612] ==============>rtllib_associate_procedure_wq():ieee->current_network.qos_data.qos_mode is 11,ieee->qos_capability is 1
[   39.502115] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   39.505897] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[   39.505902] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[   39.505905] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[   39.505908] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[   39.512902] RX: IEEE802.1X EAPOL frame!
[   39.549130] Associated successfully
[   39.549135] normal associate
[   39.549147] Using G rates:108
[   39.549150] Successfully associated, ht not enabled(0, 0)
[   39.549158] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[   39.550523] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.563260] RX: IEEE802.1X EAPOL frame!
[   39.563424] alg name:TKIP
[   39.847363] r8192_wx_set_enc_ext() group:0, alg:2, last_pairwise_key_type:0, key_len:32
[   39.847967] set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 2,is_mesh is 0
[   40.572817] RX: IEEE802.1X EAPOL frame!
[   40.572958] alg name:TKIP
[   40.572973] r8192_wx_set_enc_ext() group:1, alg:2, last_pairwise_key_type:2, key_len:32
[   40.573574] set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[   40.801863] DHCP pkt src port:68, dest port:67!!
[   41.390628] dm_check_edca_turbo():iot peer is unknown, bssid:00:1f:33:30:22:44
[   43.336183] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[   49.792087] wlan0: no IPv6 routers present
[   69.375206] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[   71.734273] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[   77.387143] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[   92.992260] lo: Disabled Privacy Extensions
[  111.738236] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[  171.738295] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[  251.738284] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[  351.742320] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[  471.742288] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[  543.787683] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[  543.950064] EXT4-fs (sda6): re-mounted. Opts: commit=600
[  591.738306] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[  656.548809] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  711.742286] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[  716.666833] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  740.719418] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  744.738556] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  760.754710] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  772.778801] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  780.794599] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  784.802705] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  800.854937] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  824.882610] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  831.738225] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[  854.946368] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  866.966399] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  874.998457] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  878.990642] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  887.003149] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  945.122641] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[  951.742325] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[  953.134888] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
[ 1045.323215] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[ 1061.358769] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData

```

iwlist scan

```


wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:30:22:44
                    ESSID:"KDWireless"
                    Protocol:IEEE802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=100/100  Signal level=-45 dBm  Noise level=-120 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 6ms ago

```


I'm using 32 bit ubuntu 10.10

---

### Post by grahammechanical on 2011-01-23
In my opinion, and I could be wrong, network manager is asking you to re-enter the password or authenticate because the connection has become disconnected and not because the password is wrong. Is the connection setup to Automatically Connect?

Regards

---

### Post by tejas.deshpande on 2011-01-23
Yes.

---

### Post by tejas.deshpande on 2011-01-24
Bump - Someone please help. I need reliable wireless on my ubuntu!

---

### Post by pohlipit on 2011-07-13
Hi,

did you ever get this fixed? I am having exactly the same problem on X100e and 11.04. Wireless connects on startup and works at first but then after some time starts disconnecting and asking for the password again. Then it connects for a while and the same happens again.

P!

---

### Post by the_master on 2011-07-14
I have the same problem as well.  someone suggested to use wicd in another thread but that doesn't work.  It just says wrong password, even though i know for sure that it is the right password.  If i discover a solution i'l post it in this thread.

---

### Post by silkworm2.5 on 2011-07-14
Have you trie installing the latest drivers from [www.linuxwireless.org](www.linuxwireless.org) ? I had the performance issues since 10.10 but after installing these drivers it was fixed:
[http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball](http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball)

If you need help, respond to me with the output of "lspci" in a terminal, and I'll list the commands you need to issue to install them.

---

### Post by obie17 on 2011-08-04
try to update your ubuntu 10.10.

---

### Post by juliobahar on 2011-12-03
Ironically I'm on Ubuntu 11.10 64-bit with gnome shell and I'm having this problem quite often now. It used to happen, as well, once in a while on previous version, and a restart would do. 

Any suggestions?

---

