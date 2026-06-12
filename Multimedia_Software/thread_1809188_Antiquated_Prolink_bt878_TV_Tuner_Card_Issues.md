---
title: "Antiquated Prolink bt878 TV Tuner Card Issues"
date: 2011-07-21
forum: Multimedia Software
---

### Post by EvilSupahFly on 2011-07-21
I have an antiquated Prolink Tuner Card (bt878 based) that works fine under Windows XP, and I have just installed Ubuntu 11.04 but cannot get the card to work in the Ubuntu environment (I'm in Canada, so use NTSC). I have seen several posts about these cards (or at least cards with the same basic chipset), but still it doesn't work. So, I have two questions:

1. Is there a script or automated setup/tweak utility I can run natively that will autoconfig my card?
2. If not,  is it possible to use my XP drivers somehow under Ubuntu (like a wrapper of some kind, similar to the wrappers for network cards)?

Addendum: Since my actual TV died, this is my alternative until the funds are available (may be quite a while...) for a new TV.

---

### Post by wkulecz on 2011-07-21
If you do:
    ls /dev/vid*

is /dev/video0 listed?

If so, look at dmsg output shortly after boot up to see what it says about the video drivers.

Tuners are troublesome.  You usually have to scour the web to map your hardware to the magic number to use as an insmod option to get them to work.


A good place to start is:
[http://www.linuxtv.org/](http://www.linuxtv.org/)

Have you installed tvtime application?  Its the best I've found at automatically getting a video card to work.  If it works with composite or SVHS inputs but not your tuner, its likely the driver is not able to guess the tuner correctly so you need the insmod magic number.

HTH.

---

### Post by wolfen69 on 2011-07-21
Perhaps [Online TV]("http://www.watchfomny.com/USA-TV.php") can hold you over until you figure something out. Also, check out [www.vidics.eu](www.vidics.eu) (thank me later) ;)

---

### Post by EvilSupahFly on 2011-07-23
Online TV. Wow. *lol* I can't get Flash working either, so it's not helping. (The x64 version hates me for some reason).

As for the tuner card, after some seriously late nights and exaustive poking around, I managed to at least get a blue box up with [FONT=Courier New]xawtv[/FONT], but the tuner card has multiple inputs (the RF tuner, a Composite, and S-Video), along with an FM Tuner, and I can't get it to switch inputs.

I have some output I piped into a text file to post, if that helps. Maybe I'm missing something because I'm too close to the problem? Below, I have the output from [FONT=Courier New]lsmod[/FONT], [FONT=Courier New]dmesg[/FONT], [FONT=Courier New]lspci[/FONT], [FONT=Courier New]xawtv[/FONT], and the [FONT=Courier New]module[/FONT] listing:

```
Output from lsmod:

Module                  Size  Used by
nvidia              10709116  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
nouveau               682322  0 
ttm                    76664  1 nouveau
drm_kms_helper         42136  1 nouveau
drm                   227495  3 nouveau,ttm,drm_kms_helper
video                  19438  1 nouveau
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  4 
arc4                   12529  2 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
rtl8187                60982  0 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
bttv                  128715  0 
i2c_algo_bit           13400  2 nouveau,bttv
ir_lirc_codec          12898  0 
snd_hwdep              13604  1 snd_hda_codec
lirc_dev               19232  1 ir_lirc_codec
mac80211              294370  1 rtl8187
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ir_sony_decoder        12549  0 
v4l2_common            17647  1 bttv
usbhid                 46956  0 
ir_jvc_decoder         12546  0 
videodev               82052  2 bttv,v4l2_common
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17078  1 videodev
ir_rc6_decoder         12546  0 
hid                    91020  1 usbhid
snd_rawmidi            30486  1 snd_seq_midi
cfg80211              178528  2 rtl8187,mac80211
ir_rc5_decoder         12546  0 
videobuf_dma_sg        19307  1 bttv
snd_seq_midi_event     14899  1 snd_seq_midi
ir_nec_decoder         12546  0 
videobuf_core          26135  2 bttv,videobuf_dma_sg
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
btcx_risc              13640  1 bttv
snd_timer              29602  2 snd_pcm,snd_seq
rc_core                26918  7 bttv,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
eeprom_93cx6           12725  1 rtl8187
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
tveeprom               21249  1 bttv
serio_raw              13166  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  2 
uas                    17996  0 
pata_pdc2027x          13512  0 
r8169                  48022  0 
``````
Output from dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=C2343D86343D7E8B loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffd0000 - 000000007ffde000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffde000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: MICRO-STAR INTERNATIONAL CO.,LTD MS-7267/MS-7267, BIOS V5.2    12/27/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x7ffd0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007ffd0000
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007ffd0000 page 4k
[    0.000000] kernel direct mapping tables up to 7ffd0000 @ 1fffc000-20000000
[    0.000000] RAMDISK: 366de000 - 37367000
[    0.000000] ACPI: RSDP 00000000000f9190 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000007ffd0000 00040 (v01 zt grp ztcisnet 12000627 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007ffd0200 00084 (v02 zt grp ztcisnet 12000627 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007ffd0630 05365 (v01  1AAAA 1AAAA000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 000000007ffde000 00040
[    0.000000] ACPI: APIC 000000007ffd0390 0006C (v01 A M I  OEMAPIC  12000627 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000007ffd0400 0003C (v01 A M I  OEMMCFG  12000627 MSFT 00000097)
[    0.000000] ACPI: SLIT 000000007ffd0440 00030 (v01 A M I  OEMSLIT  12000627 MSFT 00000097)
[    0.000000] ACPI: SPMI 000000007ffd0470 0003D (v01 A M I  OEMSPMI  12000627 MSFT 00000097)
[    0.000000] ACPI: SLIC 000000007ffd04b0 00176 (v01 zt grp ztcisnet 12000627 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007ffde040 00060 (v01 A M I  AMI_OEM  12000627 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: SLIT table looks invalid. Not used.
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ffd0000
[    0.000000] Initmem setup node 0 0000000000000000-000000007ffd0000
[    0.000000]   NODE_DATA [000000007ffcb000 - 000000007ffcffff]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88007d600000-ffff88007f1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffd0
[    0.000000] On node 0 totalpages: 524127
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7112 pages used for memmap
[    0.000000]   DMA32 zone: 513032 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516953
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=C2343D86343D7E8B loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2041084k/2096960k available (5940k kernel code, 452k absent, 55424k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 20971520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1799.915 MHz processor.
[    0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3599.83 BogoMIPS (lpj=17999150)
[    0.000011] pid_max: default: 32768 minimum: 301
[    0.000041] Security Framework initialized
[    0.000063] AppArmor: AppArmor initialized
[    0.000066] Yama: becoming mindful.
[    0.000386] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010759] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.011385] Mount-cache hash table entries: 256
[    0.011577] Initializing cgroup subsys ns
[    0.011584] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.011588] Initializing cgroup subsys cpuacct
[    0.011593] Initializing cgroup subsys memory
[    0.011603] Initializing cgroup subsys devices
[    0.011606] Initializing cgroup subsys freezer
[    0.011609] Initializing cgroup subsys net_cls
[    0.011611] Initializing cgroup subsys blkio
[    0.011656] CPU: Physical Processor ID: 0
[    0.011658] CPU: Processor Core ID: 0
[    0.011660] mce: CPU supports 6 MCE banks
[    0.011670] CPU0: Thermal monitoring enabled (TM1)
[    0.011675] using mwait in idle threads.
[    0.014807] ACPI: Core revision 20110112
[    0.020019] ftrace: allocating 24314 entries in 96 pages
[    0.030072] Setting APIC routing to flat
[    0.030358] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.142854] CPU0: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[    0.150000] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.150000] PEBS disabled due to CPU errata.
[    0.150000] ... version:                2
[    0.150000] ... bit width:              40
[    0.150000] ... generic registers:      2
[    0.150000] ... value mask:             000000ffffffffff
[    0.150000] ... max period:             000000007fffffff
[    0.150000] ... fixed-purpose events:   3
[    0.150000] ... event mask:             0000000700000003
[    0.150000] Booting Node   0, Processors  #1
[    0.310020] Brought up 2 CPUs
[    0.310025] Total of 2 processors activated (7199.91 BogoMIPS).
[    0.310446] devtmpfs: initialized
[    0.311057] print_constraints: dummy: 
[    0.311081] Time:  8:43:09  Date: 07/21/11
[    0.311125] NET: Registered protocol family 16
[    0.311164] Trying to unpack rootfs image as initramfs...
[    0.311283] ACPI: bus type pci registered
[    0.311366] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
[    0.311370] PCI: not using MMCONFIG
[    0.311372] PCI: Using configuration type 1 for base access
[    0.320185] bio: create slab <bio-0> at 0
[    0.321531] ACPI: EC: Detected MSI hardware, enabling workarounds.
[    0.321535] ACPI: EC: Look up EC in DSDT
[    0.323135] ACPI: Executed 1 blocks of module-level executable AML code
[    0.326238] ACPI: Interpreter enabled
[    0.326243] ACPI: (supports S0 S1 S4 S5)
[    0.326267] ACPI: Using IOAPIC for interrupt routing
[    0.326298] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xf0000000-0xffffffff] (base 0xf0000000)
[    0.330042] PCI: MMCONFIG at [mem 0xf0000000-0xffffffff] reserved in ACPI motherboard resources
[    0.330047] PCI: MMCONFIG for 0000 [bus00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000) (size reduced!)
[    0.347164] ACPI: No dock devices found.
[    0.347168] HEST: Table not found.
[    0.347173] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.347368] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.347548] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.347551] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.347555] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.347558] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.347562] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xffffffff] (ignored)
[    0.347576] pci 0000:00:00.0: [8086:2770] type 0 class 0x000600
[    0.347625] pci 0000:00:01.0: [8086:2771] type 1 class 0x000604
[    0.347663] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.347668] pci 0000:00:01.0: PME# disabled
[    0.347714] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.347730] pci 0000:00:1b.0: reg 10: [mem 0xfebfc000-0xfebfffff 64bit]
[    0.347785] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.347790] pci 0000:00:1b.0: PME# disabled
[    0.347811] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.347866] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.347871] pci 0000:00:1c.0: PME# disabled
[    0.347900] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.347940] pci 0000:00:1d.0: reg 20: [io  0xe080-0xe09f]
[    0.347970] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.348010] pci 0000:00:1d.1: reg 20: [io  0xe000-0xe01f]
[    0.348039] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.348079] pci 0000:00:1d.2: reg 20: [io  0xdc00-0xdc1f]
[    0.348108] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.348148] pci 0000:00:1d.3: reg 20: [io  0xd880-0xd89f]
[    0.348186] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.348206] pci 0000:00:1d.7: reg 10: [mem 0xfebfbc00-0xfebfbfff]
[    0.348274] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.348279] pci 0000:00:1d.7: PME# disabled
[    0.348297] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.348354] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    0.348443] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.348454] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.348487] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.348500] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.348510] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.348520] pci 0000:00:1f.1: reg 18: [io  0x08f0-0x08f7]
[    0.348530] pci 0000:00:1f.1: reg 1c: [io  0x08f8-0x08fb]
[    0.348540] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.348579] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    0.348594] pci 0000:00:1f.2: reg 10: [io  0xec00-0xec07]
[    0.348603] pci 0000:00:1f.2: reg 14: [io  0xe880-0xe883]
[    0.348611] pci 0000:00:1f.2: reg 18: [io  0xe800-0xe807]
[    0.348620] pci 0000:00:1f.2: reg 1c: [io  0xe480-0xe483]
[    0.348629] pci 0000:00:1f.2: reg 20: [io  0xe400-0xe40f]
[    0.348658] pci 0000:00:1f.2: PME# supported from D3hot
[    0.348663] pci 0000:00:1f.2: PME# disabled
[    0.348677] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.348727] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.348801] pci 0000:01:00.0: [10de:0de1] type 0 class 0x000300
[    0.348812] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.348825] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xe7ffffff 64bit pref]
[    0.348837] pci 0000:01:00.0: reg 1c: [mem 0xec000000-0xedffffff 64bit pref]
[    0.348845] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
[    0.348854] pci 0000:01:00.0: reg 30: [mem 0xfe980000-0xfe9fffff pref]
[    0.348900] pci 0000:01:00.1: [10de:0bea] type 0 class 0x000403
[    0.348911] pci 0000:01:00.1: reg 10: [mem 0xfe97c000-0xfe97ffff]
[    0.360030] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.360036] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.360040] pci 0000:00:01.0:   bridge window [mem 0xfc800000-0xfe9fffff]
[    0.360046] pci 0000:00:01.0:   bridge window [mem 0xdbe00000-0xefdfffff 64bit pref]
[    0.360092] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.360097] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.360102] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.360108] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.360146] pci 0000:03:00.0: [109e:036e] type 0 class 0x000400
[    0.360167] pci 0000:03:00.0: reg 10: [mem 0xefeff000-0xefefffff pref]
[    0.360261] pci 0000:03:00.1: [109e:0878] type 0 class 0x000480
[    0.360281] pci 0000:03:00.1: reg 10: [mem 0xefefe000-0xefefefff pref]
[    0.360375] pci 0000:03:01.0: [105a:4d68] type 0 class 0x000180
[    0.360393] pci 0000:03:01.0: reg 10: [io  0xcc00-0xcc07]
[    0.360404] pci 0000:03:01.0: reg 14: [io  0xc880-0xc883]
[    0.360415] pci 0000:03:01.0: reg 18: [io  0xc800-0xc807]
[    0.360426] pci 0000:03:01.0: reg 1c: [io  0xc480-0xc483]
[    0.360437] pci 0000:03:01.0: reg 20: [io  0xc400-0xc40f]
[    0.360447] pci 0000:03:01.0: reg 24: [mem 0xfeafc000-0xfeafffff]
[    0.360459] pci 0000:03:01.0: reg 30: [mem 0xfeae0000-0xfeae3fff pref]
[    0.360478] pci 0000:03:01.0: supports D1
[    0.360499] pci 0000:03:04.0: [10ec:8167] type 0 class 0x000200
[    0.360517] pci 0000:03:04.0: reg 10: [io  0xc000-0xc0ff]
[    0.360527] pci 0000:03:04.0: reg 14: [mem 0xfeafbc00-0xfeafbcff]
[    0.360569] pci 0000:03:04.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.360588] pci 0000:03:04.0: supports D1 D2
[    0.360590] pci 0000:03:04.0: PME# supported from D1 D2 D3hot D3cold
[    0.360596] pci 0000:03:04.0: PME# disabled
[    0.360637] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.360642] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.360647] pci 0000:00:1e.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.360654] pci 0000:00:1e.0:   bridge window [mem 0xefe00000-0xefefffff 64bit pref]
[    0.360657] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.360661] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.360683] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.360854] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.360925] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.361118]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.361300]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.364887] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.364952] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.365009] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.365065] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.365122] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.365179] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.365237] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.365295] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.365456] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.365464] vgaarb: loaded
[    0.365692] SCSI subsystem initialized
[    0.365786] libata version 3.00 loaded.
[    0.365842] usbcore: registered new interface driver usbfs
[    0.365855] usbcore: registered new interface driver hub
[    0.365893] usbcore: registered new device driver usb
[    0.366048] wmi: Mapper loaded
[    0.366050] PCI: Using ACPI for IRQ routing
[    0.366054] PCI: pci_cache_line_size set to 64 bytes
[    0.366146] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.366149] reserve RAM buffer: 000000007ffd0000 - 000000007fffffff 
[    0.366274] NetLabel: Initializing
[    0.366277] NetLabel:  domain hash size = 128
[    0.366279] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.366293] NetLabel:  unlabeled traffic allowed by default
[    0.366475] hpet clockevent registered
[    0.366479] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.366484] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.366490] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.380110] Switching to clocksource hpet
[    0.389674] AppArmor: AppArmor Filesystem Enabled
[    0.389714] pnp: PnP ACPI init
[    0.389736] ACPI: bus type pnp registered
[    0.389863] pnp 00:00: [bus 00-ff]
[    0.389866] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.389869] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.389872] pnp 00:00: [io  0x0d00-0xffff window]
[    0.389875] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.389878] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.389881] pnp 00:00: [mem 0x80000000-0xffffffff window]
[    0.389778] Switched to NOHz mode on CPU #0
[    0.389966] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.389978] pnp 00:01: [mem 0xfed13000-0xfed19fff]
[    0.389978] Switched to NOHz mode on CPU #1
[    0.389978] system 00:01: [mem 0xfed13000-0xfed19fff] has been reserved
[    0.389978] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.390011] pnp 00:02: [dma 4]
[    0.390014] pnp 00:02: [io  0x0000-0x000f]
[    0.390016] pnp 00:02: [io  0x0081-0x0083]
[    0.390022] pnp 00:02: [io  0x0087]
[    0.390024] pnp 00:02: [io  0x0089-0x008b]
[    0.390027] pnp 00:02: [io  0x008f]
[    0.390029] pnp 00:02: [io  0x00c0-0x00df]
[    0.390065] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.390080] pnp 00:03: [io  0x0070-0x0071]
[    0.390093] pnp 00:03: [irq 8]
[    0.390125] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.390135] pnp 00:04: [io  0x0061]
[    0.390169] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.390181] pnp 00:05: [io  0x00f0-0x00ff]
[    0.390187] pnp 00:05: [irq 13]
[    0.390219] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.390744] pnp 00:06: [io  0x0060]
[    0.390747] pnp 00:06: [io  0x0064]
[    0.390753] pnp 00:06: [irq 1]
[    0.390794] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.390833] pnp 00:07: [irq 12]
[    0.390874] pnp 00:07: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.390981] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.390984] pnp 00:08: [io  0x0a00-0x0a0f]
[    0.390986] pnp 00:08: [io  0x0a10-0x0a1f]
[    0.391058] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    0.391062] system 00:08: [io  0x0a10-0x0a1f] has been reserved
[    0.391067] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.391194] pnp 00:09: [io  0x0010-0x001f]
[    0.391197] pnp 00:09: [io  0x0022-0x003f]
[    0.391199] pnp 00:09: [io  0x0044-0x005f]
[    0.391202] pnp 00:09: [io  0x0062-0x0063]
[    0.391204] pnp 00:09: [io  0x0065-0x006f]
[    0.391206] pnp 00:09: [io  0x0072-0x007f]
[    0.391209] pnp 00:09: [io  0x0080]
[    0.391211] pnp 00:09: [io  0x0084-0x0086]
[    0.391213] pnp 00:09: [io  0x0088]
[    0.391215] pnp 00:09: [io  0x008c-0x008e]
[    0.391218] pnp 00:09: [io  0x0090-0x009f]
[    0.391220] pnp 00:09: [io  0x00a2-0x00bf]
[    0.391223] pnp 00:09: [io  0x00e0-0x00ef]
[    0.391225] pnp 00:09: [io  0x04d0-0x04d1]
[    0.391228] pnp 00:09: [io  0x0800-0x087f]
[    0.391230] pnp 00:09: [io  0x0400-0x041f]
[    0.391232] pnp 00:09: [io  0x0480-0x04bf]
[    0.391235] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.391238] pnp 00:09: [mem 0xfed20000-0xfed8ffff]
[    0.391323] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.391327] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.391330] system 00:09: [io  0x0400-0x041f] has been reserved
[    0.391333] system 00:09: [io  0x0480-0x04bf] has been reserved
[    0.391337] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.391340] system 00:09: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.391345] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.391443] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.391446] pnp 00:0a: [mem 0xfff80000-0xffffffff]
[    0.391482] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    0.391534] pnp 00:0b: [mem 0xffc00000-0xfff7ffff]
[    0.391598] system 00:0b: [mem 0xffc00000-0xfff7ffff] has been reserved
[    0.391603] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.391663] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.391666] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.391731] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.391735] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.391740] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.391782] pnp 00:0d: [mem 0xf0000000-0xf3ffffff]
[    0.391844] system 00:0d: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.391849] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.392051] pnp 00:0e: [mem 0x00000000-0x0009ffff]
[    0.392057] pnp 00:0e: [mem 0x000c0000-0x000cffff]
[    0.392060] pnp 00:0e: [mem 0x000e0000-0x000fffff]
[    0.392063] pnp 00:0e: [mem 0x00100000-0x7fffffff]
[    0.392066] pnp 00:0e: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.392144] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.392147] system 00:0e: [mem 0x000c0000-0x000cffff] has been reserved
[    0.392151] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.392154] system 00:0e: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.392159] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.392317] pnp: PnP ACPI: found 15 devices
[    0.392319] ACPI: ACPI bus type pnp unregistered
[    0.399103] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.399110] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.399115] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.399119] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.399123] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.399127] pci 0000:00:01.0:   bridge window [mem 0xfc800000-0xfe9fffff]
[    0.399132] pci 0000:00:01.0:   bridge window [mem 0xdbe00000-0xefdfffff 64bit pref]
[    0.399137] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.399140] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.399146] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.399151] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.399159] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.399163] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.399168] pci 0000:00:1e.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.399173] pci 0000:00:1e.0:   bridge window [mem 0xefe00000-0xefefffff 64bit pref]
[    0.399208] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.399213] pci 0000:00:01.0: setting latency timer to 64
[    0.399220] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.399225] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.399229] pci 0000:00:1c.0: setting latency timer to 64
[    0.399237] pci 0000:00:1e.0: setting latency timer to 64
[    0.399242] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.399245] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.399248] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.399251] pci_bus 0000:01: resource 1 [mem 0xfc800000-0xfe9fffff]
[    0.399254] pci_bus 0000:01: resource 2 [mem 0xdbe00000-0xefdfffff 64bit pref]
[    0.399257] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.399260] pci_bus 0000:02: resource 1 [mem 0x80000000-0x801fffff]
[    0.399263] pci_bus 0000:02: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.399266] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.399269] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.399272] pci_bus 0000:03: resource 2 [mem 0xefe00000-0xefefffff 64bit pref]
[    0.399275] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.399278] pci_bus 0000:03: resource 5 [mem 0x00000000-0xfffffffff]
[    0.399330] NET: Registered protocol family 2
[    0.399476] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.400426] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.403075] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.403718] TCP: Hash tables configured (established 262144 bind 65536)
[    0.403722] TCP reno registered
[    0.403738] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.403763] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.403932] NET: Registered protocol family 1
[    0.404071] pci 0000:01:00.0: Boot video device
[    0.404096] PCI: CLS 32 bytes, default 64
[    0.404561] audit: initializing netlink socket (disabled)
[    0.404576] type=2000 audit(1311237789.400:1): initialized
[    0.420595] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.422928] VFS: Disk quotas dquot_6.5.2
[    0.423005] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.423829] fuse init (API version 7.16)
[    0.423948] msgmni has been set to 3986
[    0.424262] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.424299] io scheduler noop registered
[    0.424301] io scheduler deadline registered
[    0.424356] io scheduler cfq registered (default)
[    0.424499] pcieport 0000:00:01.0: setting latency timer to 64
[    0.424538] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.424618] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.424656] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.424791] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.424794] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.424797] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    0.424802] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.424823] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.424828] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.424849] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.424892] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 27d0 ss_vid 1462 ss_did 7267
[    0.424914] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.424922] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.424980] intel_idle: MWAIT substates: 0x220
[    0.424982] intel_idle: does not run on family 6 model 15
[    0.425107] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.425114] ACPI: Power Button [PWRB]
[    0.425172] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.425176] ACPI: Power Button [PWRF]
[    0.425354] ACPI: acpi_idle registered with cpuidle
[    0.427225] ERST: Table is not found!
[    0.427335] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.624260] Freeing initrd memory: 12836k freed
[    0.682413] Linux agpgart interface v0.103
[    0.684031] brd: module loaded
[    0.684702] loop: module loaded
[    0.684826] i2c-core: driver [adp5520] using legacy suspend method
[    0.684829] i2c-core: driver [adp5520] using legacy resume method
[    0.684956] ata_piix 0000:00:1f.1: version 2.13
[    0.684983] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.685027] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.685431] scsi0 : ata_piix
[    0.685552] scsi1 : ata_piix
[    0.686961] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.686965] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.686999] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.687005] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.687053] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.687420] scsi2 : ata_piix
[    0.687506] scsi3 : ata_piix
[    0.688779] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 19
[    0.688783] ata4: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 19
[    0.689207] Fixed MDIO Bus: probed
[    0.689248] PPP generic driver version 2.4.2
[    0.689321] tun: Universal TUN/TAP device driver, 1.6
[    0.689324] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.689433] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.689467] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.689486] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.689490] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.689541] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.689600] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.689611] ehci_hcd 0000:00:1d.7: debug port 1
[    0.693491] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.693510] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebfbc00
[    0.710034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.710236] hub 1-0:1.0: USB hub found
[    0.710242] hub 1-0:1.0: 8 ports detected
[    0.710339] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.710354] uhci_hcd: USB Universal Host Controller Interface driver
[    0.710433] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.710445] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.710449] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.710499] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.710550] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e080
[    0.710703] hub 2-0:1.0: USB hub found
[    0.710708] hub 2-0:1.0: 2 ports detected
[    0.710788] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.710795] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.710799] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.710855] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.710906] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e000
[    0.711052] hub 3-0:1.0: USB hub found
[    0.711057] hub 3-0:1.0: 2 ports detected
[    0.711136] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.711143] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.711147] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.711197] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.720085] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000dc00
[    0.720268] hub 4-0:1.0: USB hub found
[    0.720274] hub 4-0:1.0: 2 ports detected
[    0.720352] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.720360] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.720363] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.720413] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.720471] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    0.720618] hub 5-0:1.0: USB hub found
[    0.720623] hub 5-0:1.0: 2 ports detected
[    0.720800] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.723584] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.723592] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.723755] mousedev: PS/2 mouse device common for all mice
[    0.723901] rtc_cmos 00:03: RTC can wake from S4
[    0.723981] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.724005] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.724139] device-mapper: uevent: version 1.0.3
[    0.724233] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.724327] device-mapper: multipath: version 1.2.0 loaded
[    0.724330] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.724463] cpuidle: using governor ladder
[    0.724466] cpuidle: using governor menu
[    0.724765] TCP cubic registered
[    0.724919] NET: Registered protocol family 10
[    0.725496] NET: Registered protocol family 17
[    0.725520] Registering the dns_resolver key type
[    0.725700] PM: Hibernation image not present or could not be loaded.
[    0.725716] registered taskstats version 1
[    0.725977]   Magic number: 3:116:726
[    0.726000] block loop6: hash matches
[    0.726041] pci 0000:01:00.1: hash matches
[    0.726089] rtc_cmos 00:03: setting system clock to 2011-07-21 08:43:10 UTC (1311237790)
[    0.726093] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.726095] EDD information not available.
[    0.742074] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.907594] ata4.00: ATA-8: ST3320613AS, SD22, max UDMA/133
[    0.907599] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.950404] ata1.00: ATA-7: ST3300831A, 3.02, max UDMA/100
[    0.950408] ata1.00: 586072368 sectors, multi 16: LBA48 
[    0.950417] ata1.01: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.03, max UDMA/66
[    0.970334] ata1.00: configured for UDMA/100
[    0.987570] ata4.00: configured for UDMA/133
[    1.010252] ata1.01: configured for UDMA/66
[    1.011528] scsi 0:0:0:0: Direct-Access     ATA      ST3300831A       3.02 PQ: 0 ANSI: 5
[    1.011741] sd 0:0:0:0: [sda] 586072368 512-byte logical blocks: (300 GB/279 GiB)
[    1.011752] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.011817] sd 0:0:0:0: [sda] Write Protect is off
[    1.011821] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.012429] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.013275] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.03 PQ: 0 ANSI: 5
[    1.036518]  sda: sda1
[    1.038041] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.038046] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.038167] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.038199] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.038273] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.038410] scsi 3:0:0:0: Direct-Access     ATA      ST3320613AS      SD22 PQ: 0 ANSI: 5
[    1.038544] sd 3:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.038581] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.038614] sd 3:0:0:0: [sdb] Write Protect is off
[    1.038618] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.038651] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.060483]  sdb: sdb1
[    1.060787] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.062943] Freeing unused kernel memory: 956k freed
[    1.063234] Write protecting the kernel read-only data: 10240k
[    1.064190] Freeing unused kernel memory: 184k freed
[    1.070548] Freeing unused kernel memory: 1444k freed
[    1.090044] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.096663] <30>udev[72]: starting version 167
[    1.231055] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.231089] r8169 0000:03:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.231115] r8169 0000:03:04.0: (unregistered net_device): no PCI Express capability
[    1.231682] r8169 0000:03:04.0: eth0: RTL8169sc/8110sc at 0xffffc90000314c00, 00:19:db:4a:53:79, XID 18000000 IRQ 20
[    1.260446] pata_pdc2027x 0000:03:01.0: version 1.0
[    1.260493] pata_pdc2027x 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.360547] pata_pdc2027x 0000:03:01.0: PLL input clock 19182 kHz
[    1.390033] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    1.391029] scsi4 : pata_pdc2027x
[    1.391124] scsi5 : pata_pdc2027x
[    1.391185] ata5: PATA max UDMA/100 mmio m16384@0xfeafc000 cmd 0xfeafd7c0 irq 17
[    1.391189] ata6: PATA max UDMA/100 mmio m16384@0xfeafc000 cmd 0xfeafd5c0 irq 17
[    1.400088] Refined TSC clocksource calibration: 1799.999 MHz.
[    1.400094] Switching to clocksource tsc
[    1.549794] usbcore: registered new interface driver uas
[    1.550711] ata5.00: ATAPI: LTN486S, YUS6, max UDMA/33, CDB intr
[    1.570623] ata5.00: configured for UDMA/33
[    1.571198] scsi 4:0:0:0: CD-ROM            LITEON   CD-ROM LTN486S   YUS6 PQ: 0 ANSI: 5
[    1.572918] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.573113] sr 4:0:0:0: Attached scsi CD-ROM sr1
[    1.573219] sr 4:0:0:0: Attached scsi generic sg3 type 5
[    1.660046] usb 1-7: new high speed USB device using ehci_hcd and address 5
[    1.721828] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[    1.749032] Initializing USB Mass Storage driver...
[    1.750095] scsi6 : usb-storage 1-6:1.0
[    1.750371] usbcore: registered new interface driver usb-storage
[    1.750375] USB Mass Storage support registered.
[    1.821355] scsi7 : usb-storage 1-7:1.0
[    1.940077] usb 1-8: new high speed USB device using ehci_hcd and address 6
[    2.070122] usb 1-8: device descriptor read/64, error -71
[    2.310070] usb 1-8: device descriptor read/64, error -71
[    2.540140] usb 1-8: new high speed USB device using ehci_hcd and address 7
[    2.670093] usb 1-8: device descriptor read/64, error -71
[    2.751164] scsi 6:0:0:0: Direct-Access     Sony     Storage Media    0100 PQ: 0 ANSI: 0 CCS
[    2.751731] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    2.752947] sd 6:0:0:0: [sdc] 31326208 512-byte logical blocks: (16.0 GB/14.9 GiB)
[    2.753656] sd 6:0:0:0: [sdc] Write Protect is off
[    2.753662] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[    2.754889] sd 6:0:0:0: [sdc] No Caching mode page present
[    2.754894] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.758262] sd 6:0:0:0: [sdc] No Caching mode page present
[    2.758266] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.758907]  sdc: sdc1
[    2.761137] sd 6:0:0:0: [sdc] No Caching mode page present
[    2.761141] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.761145] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    2.821664] scsi 7:0:0:0: Direct-Access     WDC WD25 00JS-00NCB1      0041 PQ: 0 ANSI: 0
[    2.822260] sd 7:0:0:0: Attached scsi generic sg5 type 0
[    2.823400] sd 7:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.824270] sd 7:0:0:0: [sdd] Write Protect is off
[    2.824276] sd 7:0:0:0: [sdd] Mode Sense: 03 00 00 00
[    2.825037] sd 7:0:0:0: [sdd] No Caching mode page present
[    2.825041] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[    2.827597] sd 7:0:0:0: [sdd] No Caching mode page present
[    2.827602] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[    2.828157]  sdd: sdd1
[    2.830515] sd 7:0:0:0: [sdd] No Caching mode page present
[    2.830519] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[    2.830523] sd 7:0:0:0: [sdd] Attached SCSI disk
[    2.910163] usb 1-8: device descriptor read/64, error -71
[    3.140072] usb 1-8: new high speed USB device using ehci_hcd and address 8
[    3.560029] usb 1-8: device not accepting address 8, error -71
[    3.680116] usb 1-8: new high speed USB device using ehci_hcd and address 9
[    3.975909] <30>udev[319]: starting version 167
[    4.100298] usb 1-8: device not accepting address 9, error -71
[    4.100363] hub 1-0:1.0: unable to enumerate USB device on port 8
[    4.202570] intel_rng: FWH not detected
[    4.236858] lp: driver loaded but no devices found
[    4.364037] leds_ss4200: no LED devices found
[    4.580131] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.984738] IR NEC protocol handler initialized
[    5.040091] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    5.051306] IR RC5(x) protocol handler initialized
[    5.075937] cfg80211: Calling CRDA to update world regulatory domain
[    5.079924] IR RC6 protocol handler initialized
[    5.139713] Linux video capture interface: v2.00
[    5.149883] IR JVC protocol handler initialized
[    5.177235] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    5.177742] generic-usb 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[    5.177905] usbcore: registered new interface driver usbhid
[    5.177908] usbhid: USB HID core driver
[    5.186492] IR Sony protocol handler initialized
[    5.188287] usb 5-2: not running at top speed; connect to a high speed hub
[    5.221483] scsi8 : usb-storage 5-2:1.0
[    5.251292] lirc_dev: IR Remote Control driver registered, major 250 
[    5.294811] IR LIRC bridge handler initialized
[    5.430468] bttv: driver version 0.9.18 loaded
[    5.430473] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    5.430686] bttv: Bt8xx card found (0).
[    5.430704] bttv 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.430715] bttv0: Bt878 (rev 17) at 0000:03:00.0, irq: 16, latency: 64, mmio: 0xefeff000
[    5.430737] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[    5.430768] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[    5.431576] tveeprom 0-0050: Huh, no eeprom present (err=-6)?
[    5.431581] bttv0: tuner type unset
[    5.431741] bttv0: registered device video0
[    5.431833] bttv0: registered device vbi0
[    5.509036] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.509118] HDA Intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[    5.509150] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.646134] cfg80211: World regulatory domain updated:
[    5.646139] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.646143] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.646147] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.646150] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.646153] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.646157] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.689257] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.689264] hda_intel: Disable MSI for Nvidia chipset
[    5.689306] HDA Intel 0000:01:00.1: setting latency timer to 64
[    5.689741] type=1400 audit(1311252195.452:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=606 comm="apparmor_parser"
[    5.690893] type=1400 audit(1311252195.462:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=606 comm="apparmor_parser"
[    5.691590] type=1400 audit(1311252195.462:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=606 comm="apparmor_parser"
[    5.692651] type=1400 audit(1311252195.462:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=605 comm="apparmor_parser"
[    5.693739] type=1400 audit(1311252195.462:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=605 comm="apparmor_parser"
[    5.694424] type=1400 audit(1311252195.462:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=605 comm="apparmor_parser"
[    5.886600] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    5.886606] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886609] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    5.886612] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886615] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    5.886619] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886621] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    5.886625] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886627] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    5.886631] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886633] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    5.886637] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886639] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    5.886643] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886645] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    5.886649] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886651] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    5.886654] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886657] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    5.886660] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886663] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    5.886666] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886668] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    5.886672] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886674] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    5.886677] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.886680] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    5.886683] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[    5.944456] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    5.946002] ieee80211 phy0: hwaddr 00:14:d1:43:d8:3c, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[    5.967495] rtl8187: Customer ID is 0x00
[    5.967712] Registered led device: rtl8187-phy0::radio
[    5.968232] Registered led device: rtl8187-phy0::tx
[    5.968791] Registered led device: rtl8187-phy0::rx
[    5.969608] rtl8187: wireless switch is on
[    5.969779] usbcore: registered new interface driver rtl8187
[    6.224236] scsi 8:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
[    6.954990] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[    7.040949] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[    7.763968] type=1400 audit(1311252197.532:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=839 comm="apparmor_parser"
[    7.765068] type=1400 audit(1311252197.532:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=839 comm="apparmor_parser"
[    7.765748] type=1400 audit(1311252197.532:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=839 comm="apparmor_parser"
[    7.828343] type=1400 audit(1311252197.592:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=838 comm="apparmor_parser"
[    9.834030] ppdev: user-space parallel port driver
[   12.417459] [drm] Initialized drm 1.1.0 20060810
[   12.504605] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   15.002929] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.009803] r8169 0000:03:04.0: eth0: link down
[   15.010216] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.561913] r8169 0000:03:04.0: eth0: link up
[   16.562218] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.271530] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   19.485588] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   20.601349] wlan0: authenticate with 00:25:9c:02:ae:ca (try 1)
[   20.603463] wlan0: authenticated
[   20.802359] wlan0: associate with 00:25:9c:02:ae:ca (try 1)
[   20.811001] wlan0: RX AssocResp from 00:25:9c:02:ae:ca (capab=0x1 status=0 aid=1)
[   20.811006] wlan0: associated
[   20.814430] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.240036] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[   27.500027] eth0: no IPv6 routers present
[   30.530045] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[   31.460028] wlan0: no IPv6 routers present
[   46.820034] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[   47.100051] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[   57.450035] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[   57.609215] scsi 8:0:0:1: Device offlined - not ready after error recovery
[   57.609894] sd 8:0:0:0: Attached scsi generic sg6 type 0
[   88.200031] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[   98.470029] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  114.760038] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  115.040049] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  125.310034] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  125.469492] sd 8:0:0:0: Device offlined - not ready after error recovery
[  125.469527] sd 8:0:0:0: rejecting I/O to offline device
[  125.469542] sd 8:0:0:0: rejecting I/O to offline device
[  125.469551] sd 8:0:0:0: rejecting I/O to offline device
[  125.469558] sd 8:0:0:0: [sde] READ CAPACITY failed
[  125.469561] sd 8:0:0:0: [sde]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  125.469567] sd 8:0:0:0: [sde] Sense not available.
[  125.469575] sd 8:0:0:0: rejecting I/O to offline device
[  125.469581] sd 8:0:0:0: [sde] Write Protect is off
[  125.469586] sd 8:0:0:0: [sde] Mode Sense: 00 00 00 00
[  125.469592] sd 8:0:0:0: rejecting I/O to offline device
[  125.469598] sd 8:0:0:0: [sde] Asking for cache data failed
[  125.469602] sd 8:0:0:0: [sde] Assuming drive cache: write through
[  125.469824] sd 8:0:0:0: [sde] Attached SCSI removable disk
[  774.873802] nvidia: module license 'NVIDIA' taints kernel.
[  774.873809] Disabling lock debugging due to kernel taint
[  775.790398] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  775.790409] nvidia 0000:01:00.0: setting latency timer to 64
[  775.790415] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[  775.790569] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
``````
Output from lspci:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GF108 [GeForce GT 430] (rev a1)
01:00.1 Audio device: nVidia Corporation GF108 High Definition Audio Controller (rev a1)
03:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
03:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
03:01.0 Mass storage controller: Promise Technology, Inc. PDC20268 (Ultra100 TX2) (rev 01)
03:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
``````
Modules:

/lib/modules/2.6.38-8-generic/kernel:
arch
crypto
drivers
fs
lib
net
security
sound
ubuntu

/lib/modules/2.6.38-8-generic/kernel/arch:
x86

/lib/modules/2.6.38-8-generic/kernel/arch/x86:
crypto
kernel
kvm
oprofile

/lib/modules/2.6.38-8-generic/kernel/arch/x86/crypto:
aesni-intel.ko
aes-x86_64.ko
fpu.ko
ghash-clmulni-intel.ko
salsa20-x86_64.ko
twofish-x86_64.ko

/lib/modules/2.6.38-8-generic/kernel/arch/x86/kernel:
cpu
cpuid.ko
microcode.ko
msr.ko

/lib/modules/2.6.38-8-generic/kernel/arch/x86/kernel/cpu:
cpufreq
mcheck

/lib/modules/2.6.38-8-generic/kernel/arch/x86/kernel/cpu/cpufreq:
p4-clockmod.ko
pcc-cpufreq.ko
speedstep-lib.ko

/lib/modules/2.6.38-8-generic/kernel/arch/x86/kernel/cpu/mcheck:
mce-inject.ko
mce-xeon75xx.ko

/lib/modules/2.6.38-8-generic/kernel/arch/x86/kvm:
kvm-amd.ko
kvm-intel.ko
kvm.ko

/lib/modules/2.6.38-8-generic/kernel/arch/x86/oprofile:
oprofile.ko

/lib/modules/2.6.38-8-generic/kernel/crypto:
aes_generic.ko
af_alg.ko
algif_hash.ko
algif_skcipher.ko
ansi_cprng.ko
anubis.ko
arc4.ko
async_tx
authenc.ko
blowfish.ko
camellia.ko
cast5.ko
cast6.ko
ccm.ko
cryptd.ko
crypto_null.ko
ctr.ko
cts.ko
deflate.ko
des_generic.ko
fcrypt.ko
gcm.ko
gf128mul.ko
ghash-generic.ko
khazad.ko
lrw.ko
lzo.ko
md4.ko
michael_mic.ko
pcbc.ko
pcrypt.ko
rmd128.ko
rmd160.ko
rmd256.ko
rmd320.ko
salsa20_generic.ko
seed.ko
seqiv.ko
serpent.ko
sha1_generic.ko
sha256_generic.ko
sha512_generic.ko
tcrypt.ko
tea.ko
tgr192.ko
twofish_common.ko
twofish_generic.ko
vmac.ko
wp512.ko
xcbc.ko
xor.ko
xts.ko
zlib.ko

/lib/modules/2.6.38-8-generic/kernel/crypto/async_tx:
async_memcpy.ko
async_pq.ko
async_raid6_recov.ko
async_tx.ko
async_xor.ko
raid6test.ko

/lib/modules/2.6.38-8-generic/kernel/drivers:
acpi
ata
atm
auxdisplay
block
bluetooth
char
crypto
dca
dma
edac
firewire
firmware
gpio
gpu
hid
hwmon
i2c
idle
infiniband
input
isdn
leds
md
media
memstick
message
mfd
misc
mmc
mtd
net
nfc
parport
pci
pcmcia
platform
power
pps
regulator
rtc
scsi
spi
ssb
staging
target
telephony
tty
uio
usb
uwb
vhost
video
virtio
w1
watchdog
xen

/lib/modules/2.6.38-8-generic/kernel/drivers/acpi:
acpi_ipmi.ko
acpi_pad.ko
apei
ec_sys.ko
hed.ko
power_meter.ko
video.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/acpi/apei:
einj.ko
erst-dbg.ko
ghes.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/ata:
acard-ahci.ko
ahci.ko
ahci_platform.ko
libahci.ko
pata_ali.ko
pata_amd.ko
pata_artop.ko
pata_atiixp.ko
pata_atp867x.ko
pata_cmd640.ko
pata_cmd64x.ko
pata_cs5520.ko
pata_cs5530.ko
pata_cs5536.ko
pata_cypress.ko
pata_efar.ko
pata_hpt366.ko
pata_hpt37x.ko
pata_hpt3x2n.ko
pata_hpt3x3.ko
pata_it8213.ko
pata_it821x.ko
pata_jmicron.ko
pata_legacy.ko
pata_marvell.ko
pata_mpiix.ko
pata_netcell.ko
pata_ninja32.ko
pata_ns87410.ko
pata_ns87415.ko
pata_oldpiix.ko
pata_optidma.ko
pata_opti.ko
pata_pcmcia.ko
pata_pdc2027x.ko
pata_pdc202xx_old.ko
pata_platform.ko
pata_radisys.ko
pata_rdc.ko
pata_rz1000.ko
pata_sc1200.ko
pata_sch.ko
pata_serverworks.ko
pata_sil680.ko
pata_sl82c105.ko
pata_triflex.ko
pata_via.ko
sata_inic162x.ko
sata_mv.ko
sata_nv.ko
sata_promise.ko
sata_qstor.ko
sata_sil24.ko
sata_sil.ko
sata_sis.ko
sata_svw.ko
sata_sx4.ko
sata_uli.ko
sata_via.ko
sata_vsc.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/atm:
ambassador.ko
atmtcp.ko
eni.ko
firestream.ko
fore_200e.ko
he.ko
horizon.ko
idt77252.ko
iphase.ko
lanai.ko
nicstar.ko
solos-pci.ko
suni.ko
uPD98402.ko
zatm.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/auxdisplay:
cfag12864bfb.ko
cfag12864b.ko
ks0108.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/block:
aoe
cciss.ko
cpqarray.ko
cryptoloop.ko
DAC960.ko
drbd
floppy.ko
nbd.ko
osdblk.ko
paride
rbd.ko
sx8.ko
umem.ko
virtio_blk.ko
xen-blkfront.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/block/aoe:
aoe.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/block/drbd:
drbd.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/block/paride:
aten.ko
bpck.ko
comm.ko
dstr.ko
epat.ko
epia.ko
fit2.ko
fit3.ko
friq.ko
frpw.ko
kbic.ko
ktti.ko
on20.ko
on26.ko
paride.ko
pcd.ko
pd.ko
pf.ko
pg.ko
pt.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/bluetooth:
ath3k.ko
bcm203x.ko
bfusb.ko
bluecard_cs.ko
bpa10x.ko
bt3c_cs.ko
btmrvl.ko
btmrvl_sdio.ko
btsdio.ko
btuart_cs.ko
btusb.ko
dtl1_cs.ko
hci_uart.ko
hci_vhci.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/char:
agp
applicom.ko
cyclades.ko
epca.ko
hangcheck-timer.ko
hw_random
i8k.ko
ip2
ipmi
istallion.ko
lp.ko
moxa.ko
mwave
mxser.ko
nozomi.ko
nvram.ko
pcmcia
ppdev.ko
ramoops.ko
raw.ko
riscom8.ko
rocket.ko
specialix.ko
stallion.ko
synclink_gt.ko
synclink.ko
synclinkmp.ko
tlclk.ko
tpm
virtio_console.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/char/agp:
sis-agp.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/char/hw_random:
amd-rng.ko
intel-rng.ko
timeriomem-rng.ko
via-rng.ko
virtio-rng.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/char/ip2:
ip2.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/char/ipmi:
ipmi_devintf.ko
ipmi_msghandler.ko
ipmi_poweroff.ko
ipmi_si.ko
ipmi_watchdog.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/char/mwave:
mwave.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/char/pcmcia:
cm4000_cs.ko
cm4040_cs.ko
ipwireless
synclink_cs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/char/pcmcia/ipwireless:
ipwireless.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/char/tpm:
tpm_atmel.ko
tpm_bios.ko
tpm_infineon.ko
tpm.ko
tpm_nsc.ko
tpm_tis.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/crypto:
hifn_795x.ko
padlock-aes.ko
padlock-sha.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/dca:
dca.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/dma:
intel_mid_dma.ko
ioat
pch_dma.ko
timb_dma.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/dma/ioat:
ioatdma.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/edac:
amd64_edac_mod.ko
e752x_edac.ko
edac_core.ko
edac_mce_amd.ko
i3000_edac.ko
i3200_edac.ko
i5000_edac.ko
i5100_edac.ko
i5400_edac.ko
i7300_edac.ko
i7core_edac.ko
i82975x_edac.ko
mce_amd_inj.ko
x38_edac.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/firewire:
firewire-core.ko
firewire-net.ko
firewire-ohci.ko
firewire-sbp2.ko
nosy.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/firmware:
dcdbas.ko
dell_rbu.ko
iscsi_ibft.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpio:
74x164.ko
adp5520-gpio.ko
adp5588-gpio.ko
basic_mmio_gpio.ko
cs5535-gpio.ko
it8761e_gpio.ko
janz-ttl.ko
max7300.ko
max7301.ko
max730x.ko
max732x.ko
mc33880.ko
mcp23s08.ko
ml_ioh_gpio.ko
pca953x.ko
pcf857x.ko
pch_gpio.ko
rdc321x-gpio.ko
sch_gpio.ko
vx855_gpio.ko
wm831x-gpio.ko
wm8350-gpiolib.ko
wm8994-gpio.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu:
drm
stub

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm:
drm_kms_helper.ko
drm.ko
i2c
i810
i830
i915
mga
nouveau
r128
radeon
savage
sis
tdfx
ttm
via

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/i2c:
ch7006.ko
sil164.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/i810:
i810.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/i830:
i830.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/i915:
i915.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/mga:
mga.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/nouveau:
nouveau.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/r128:
r128.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/radeon:
radeon.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/savage:
savage.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/sis:
sis.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/tdfx:
tdfx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/ttm:
ttm.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/via:
via.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/stub:
poulsbo.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/hid:
hid-3m-pct.ko
hid-a4tech.ko
hid-apple.ko
hid-axff.ko
hid-belkin.ko
hid-cando.ko
hid-cherry.ko
hid-chicony.ko
hid-cypress.ko
hid-drff.ko
hid-egalax.ko
hid-elecom.ko
hid-emsff.ko
hid-ezkey.ko
hid-gaff.ko
hid-gyration.ko
hid-kensington.ko
hid.ko
hid-kye.ko
hid-logitech.ko
hid-magicmouse.ko
hid-microsoft.ko
hid-monterey.ko
hid-mosart.ko
hid-multitouch.ko
hid-ntrig.ko
hid-ortek.ko
hid-petalynx.ko
hid-picolcd.ko
hid-pl.ko
hid-prodikeys.ko
hid-quanta.ko
hid-roccat.ko
hid-roccat-kone.ko
hid-roccat-koneplus.ko
hid-roccat-pyra.ko
hid-samsung.ko
hid-sjoy.ko
hid-sony.ko
hid-stantum.ko
hid-sunplus.ko
hid-tmff.ko
hid-topseed.ko
hid-twinhan.ko
hid-uclogic.ko
hid-wacom.ko
hid-waltop.ko
hid-zpff.ko
hid-zydacron.ko
usbhid

/lib/modules/2.6.38-8-generic/kernel/drivers/hid/usbhid:
usbhid.ko
usbkbd.ko
usbmouse.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/hwmon:
abituguru3.ko
abituguru.ko
ad7414.ko
ad7418.ko
adcxx.ko
adm1021.ko
adm1025.ko
adm1026.ko
adm1029.ko
adm1031.ko
adm9240.ko
ads7828.ko
ads7871.ko
adt7411.ko
adt7462.ko
adt7470.ko
adt7475.ko
amc6821.ko
applesmc.ko
asb100.ko
asc7621.ko
asus_atk0110.ko
atxp1.ko
coretemp.ko
dme1737.ko
ds1621.ko
ds620.ko
emc1403.ko
emc2103.ko
f71805f.ko
f71882fg.ko
f75375s.ko
fschmd.ko
g760a.ko
gl518sm.ko
gl520sm.ko
gpio-fan.ko
hp_accel.ko
hwmon-vid.ko
i5k_amb.ko
ibmaem.ko
ibmpex.ko
it87.ko
jc42.ko
k10temp.ko
k8temp.ko
lis3lv02d_i2c.ko
lis3lv02d.ko
lm63.ko
lm70.ko
lm73.ko
lm75.ko
lm77.ko
lm78.ko
lm80.ko
lm83.ko
lm85.ko
lm87.ko
lm90.ko
lm92.ko
lm93.ko
lm95241.ko
ltc4215.ko
ltc4245.ko
ltc4261.ko
max1111.ko
max1619.ko
max6650.ko
mc13783-adc.ko
pc87360.ko
pc87427.ko
pcf8591.ko
pkgtemp.ko
sht15.ko
sht21.ko
sis5595.ko
smm665.ko
smsc47b397.ko
smsc47m192.ko
smsc47m1.ko
thmc50.ko
tmp102.ko
tmp401.ko
tmp421.ko
via686a.ko
via-cputemp.ko
vt1211.ko
vt8231.ko
w83627ehf.ko
w83627hf.ko
w83781d.ko
w83791d.ko
w83792d.ko
w83793.ko
w83795.ko
w83l785ts.ko
w83l786ng.ko
wm831x-hwmon.ko
wm8350-hwmon.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/i2c:
algos
busses
i2c-dev.ko
i2c-mux.ko
i2c-smbus.ko
muxes

/lib/modules/2.6.38-8-generic/kernel/drivers/i2c/algos:
i2c-algo-bit.ko
i2c-algo-pca.ko
i2c-algo-pcf.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/i2c/busses:
i2c-ali1535.ko
i2c-ali1563.ko
i2c-ali15x3.ko
i2c-amd756.ko
i2c-amd756-s4882.ko
i2c-amd8111.ko
i2c-eg20t.ko
i2c-gpio.ko
i2c-i801.ko
i2c-intel-mid.ko
i2c-isch.ko
i2c-nforce2.ko
i2c-nforce2-s4985.ko
i2c-ocores.ko
i2c-parport.ko
i2c-parport-light.ko
i2c-pca-platform.ko
i2c-piix4.ko
i2c-scmi.ko
i2c-simtec.ko
i2c-sis5595.ko
i2c-sis630.ko
i2c-sis96x.ko
i2c-stub.ko
i2c-taos-evm.ko
i2c-tiny-usb.ko
i2c-via.ko
i2c-viapro.ko
i2c-xiic.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/i2c/muxes:
gpio-i2cmux.ko
pca9541.ko
pca954x.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/idle:
i7300_idle.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband:
core
hw
ulp

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/core:
ib_addr.ko
ib_cm.ko
ib_core.ko
ib_mad.ko
ib_sa.ko
ib_ucm.ko
ib_umad.ko
ib_uverbs.ko
iw_cm.ko
rdma_cm.ko
rdma_ucm.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/hw:
amso1100
cxgb3
cxgb4
ipath
mlx4
mthca
qib

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/hw/amso1100:
iw_c2.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/hw/cxgb3:
iw_cxgb3.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/hw/cxgb4:
iw_cxgb4.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/hw/ipath:
ib_ipath.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/hw/mlx4:
mlx4_ib.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/hw/mthca:
ib_mthca.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/hw/qib:
ib_qib.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/ulp:
ipoib
iser
srp

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/ulp/ipoib:
ib_ipoib.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/ulp/iser:
ib_iser.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/infiniband/ulp/srp:
ib_srp.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input:
evbug.ko
ff-memless.ko
gameport
input-polldev.ko
joydev.ko
joystick
keyboard
misc
mouse
serio
sparse-keymap.ko
tablet
touchscreen
xen-kbdfront.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input/gameport:
emu10k1-gp.ko
fm801-gp.ko
gameport.ko
lightning.ko
ns558.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input/joystick:
a3d.ko
adi.ko
analog.ko
as5011.ko
cobra.ko
db9.ko
gamecon.ko
gf2k.ko
grip.ko
grip_mp.ko
guillemot.ko
iforce
interact.ko
joydump.ko
magellan.ko
sidewinder.ko
spaceball.ko
spaceorb.ko
stinger.ko
tmdc.ko
turbografx.ko
twidjoy.ko
walkera0701.ko
warrior.ko
xpad.ko
zhenhua.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input/joystick/iforce:
iforce.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input/keyboard:
adp5520-keys.ko
adp5588-keys.ko
gpio_keys.ko
gpio_keys_polled.ko
lkkbd.ko
lm8323.ko
matrix_keypad.ko
max7359_keypad.ko
mcs_touchkey.ko
newtonkbd.ko
opencores-kbd.ko
stmpe-keypad.ko
stowaway.ko
sunkbd.ko
tc3589x-keypad.ko
tca6416-keypad.ko
xtkbd.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input/misc:
88pm860x_onkey.ko
ab8500-ponkey.ko
ad714x-i2c.ko
ad714x.ko
ad714x-spi.ko
adxl34x-i2c.ko
adxl34x.ko
adxl34x-spi.ko
ati_remote2.ko
ati_remote.ko
atlas_btns.ko
cm109.ko
cma3000_d0x_i2c.ko
cma3000_d0x.ko
keyspan_remote.ko
max8925_onkey.ko
pcf50633-input.ko
pcf8574_keypad.ko
pcspkr.ko
powermate.ko
rotary_encoder.ko
wm831x-on.ko
yealink.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input/mouse:
appletouch.ko
bcm5974.ko
gpio_mouse.ko
psmouse.ko
sermouse.ko
synaptics_i2c.ko
vsxxxaa.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input/serio:
altera_ps2.ko
ct82c710.ko
parkbd.ko
pcips2.ko
ps2mult.ko
serio_raw.ko
serport.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input/tablet:
acecad.ko
aiptek.ko
gtco.ko
hanwang.ko
kbtab.ko
wacom.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/input/touchscreen:
88pm860x-ts.ko
ad7877.ko
ad7879-i2c.ko
ad7879.ko
ad7879-spi.ko
ads7846.ko
bu21013_ts.ko
cy8ctmg110_ts.ko
da9034-ts.ko
dynapro.ko
eeti_ts.ko
elo.ko
fujitsu_ts.ko
gunze.ko
hampshire.ko
inexio.ko
mc13783_ts.ko
mcs5000_ts.ko
mk712.ko
mtouch.ko
penmount.ko
qt602240_ts.ko
st1232.ko
stmpe-ts.ko
touchit213.ko
touchright.ko
touchwin.ko
tps6507x-ts.ko
tsc2007.ko
ucb1400_ts.ko
usbtouchscreen.ko
wacom_w8001.ko
wm97xx-ts.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn:
capi
divert
gigaset
hardware
hisax
hysdn
i4l
mISDN

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/capi:
capidrv.ko
capifs.ko
capi.ko
kernelcapi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/divert:
dss1_divert.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/gigaset:
bas_gigaset.ko
gigaset.ko
ser_gigaset.ko
usb_gigaset.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/hardware:
avm
eicon
mISDN

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/hardware/avm:
avm_cs.ko
b1dma.ko
b1.ko
b1pci.ko
b1pcmcia.ko
c4.ko
t1pci.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/hardware/eicon:
divacapi.ko
divadidd.ko
diva_idi.ko
diva_mnt.ko
divas.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/hardware/mISDN:
avmfritz.ko
hfcmulti.ko
hfcpci.ko
hfcsusb.ko
mISDNinfineon.ko
mISDNipac.ko
mISDNisar.ko
netjet.ko
speedfax.ko
w6692.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/hisax:
avma1_cs.ko
elsa_cs.ko
hfc4s8s_l1.ko
hfc_usb.ko
hisax_fcpcipnp.ko
hisax_isac.ko
hisax.ko
hisax_st5481.ko
sedlbauer_cs.ko
teles_cs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/hysdn:
hysdn.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/i4l:
isdn_bsdcomp.ko
isdnhdlc.ko
isdn.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/isdn/mISDN:
l1oip.ko
mISDN_core.ko
mISDN_dsp.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/leds:
dell-led.ko
leds-88pm860x.ko
leds-adp5520.ko
leds-alix2.ko
leds-bd2802.ko
leds-da903x.ko
leds-dac124s085.ko
leds-gpio.ko
leds-lp3944.ko
leds-lp5521.ko
leds-lp5523.ko
leds-lt3593.ko
leds-mc13783.ko
leds-net5501.ko
leds-pca9532.ko
leds-pca955x.ko
leds-regulator.ko
leds-ss4200.ko
leds-wm831x-status.ko
leds-wm8350.ko
ledtrig-backlight.ko
ledtrig-default-on.ko
ledtrig-gpio.ko
ledtrig-heartbeat.ko
ledtrig-timer.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/md:
dm-crypt.ko
dm-queue-length.ko
dm-raid.ko
dm-service-time.ko
dm-zero.ko
faulty.ko
linear.ko
multipath.ko
raid0.ko
raid10.ko
raid1.ko
raid456.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media:
common
dvb
radio
rc
video

/lib/modules/2.6.38-8-generic/kernel/drivers/media/common:
saa7146.ko
saa7146_vv.ko
tuners

/lib/modules/2.6.38-8-generic/kernel/drivers/media/common/tuners:
max2165.ko
mc44s803.ko
mt2060.ko
mt20xx.ko
mt2131.ko
mt2266.ko
mxl5005s.ko
mxl5007t.ko
qt1010.ko
tda18218.ko
tda18271.ko
tda827x.ko
tda8290.ko
tda9887.ko
tea5761.ko
tea5767.ko
tuner-simple.ko
tuner-types.ko
tuner-xc2028.ko
xc5000.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb:
b2c2
bt8xx
dm1105
dvb-core
dvb-usb
firewire
frontends
mantis
ngene
pluto2
pt1
siano
ttpci
ttusb-budget
ttusb-dec

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/b2c2:
b2c2-flexcop.ko
b2c2-flexcop-pci.ko
b2c2-flexcop-usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/bt8xx:
bt878.ko
dst_ca.ko
dst.ko
dvb-bt8xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/dm1105:
dm1105.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/dvb-core:
dvb-core.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/dvb-usb:
dvb-usb-a800.ko
dvb-usb-af9005.ko
dvb-usb-af9005-remote.ko
dvb-usb-af9015.ko
dvb-usb-anysee.ko
dvb-usb-au6610.ko
dvb-usb-az6027.ko
dvb-usb-ce6230.ko
dvb-usb-cinergyT2.ko
dvb-usb-cxusb.ko
dvb-usb-dib0700.ko
dvb-usb-dibusb-common.ko
dvb-usb-dibusb-mb.ko
dvb-usb-dibusb-mc.ko
dvb-usb-digitv.ko
dvb-usb-dtt200u.ko
dvb-usb-dtv5100.ko
dvb-usb-dw2102.ko
dvb-usb-friio.ko
dvb-usb-gl861.ko
dvb-usb-gp8psk.ko
dvb-usb.ko
dvb-usb-lmedm04.ko
dvb-usb-m920x.ko
dvb-usb-nova-t-usb2.ko
dvb-usb-opera.ko
dvb-usb-ttusb2.ko
dvb-usb-umt-010.ko
dvb-usb-vp702x.ko
dvb-usb-vp7045.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/firewire:
firedtv.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/frontends:
af9013.ko
atbm8830.ko
au8522.ko
bcm3510.ko
cx22700.ko
cx22702.ko
cx24110.ko
cx24113.ko
cx24116.ko
cx24123.ko
dib0070.ko
dib0090.ko
dib3000mb.ko
dib3000mc.ko
dib7000m.ko
dib7000p.ko
dib8000.ko
dibx000_common.ko
ds3000.ko
dvb-pll.ko
isl6405.ko
isl6421.ko
isl6423.ko
itd1000.ko
ix2505v.ko
l64781.ko
lgdt3305.ko
lgdt330x.ko
lgs8gxx.ko
lnbp21.ko
mb86a16.ko
mb86a20s.ko
mt312.ko
mt352.ko
nxt200x.ko
nxt6000.ko
or51132.ko
or51211.ko
s5h1409.ko
s5h1411.ko
s5h1420.ko
s921.ko
si21xx.ko
sp8870.ko
sp887x.ko
stb0899.ko
stb6000.ko
stb6100.ko
stv0288.ko
stv0297.ko
stv0299.ko
stv0900.ko
stv090x.ko
stv6110.ko
stv6110x.ko
tda10021.ko
tda10023.ko
tda10048.ko
tda1004x.ko
tda10086.ko
tda665x.ko
tda8083.ko
tda8261.ko
tda826x.ko
tua6100.ko
ves1820.ko
ves1x93.ko
zl10036.ko
zl10039.ko
zl10353.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/mantis:
hopper.ko
mantis_core.ko
mantis.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/ngene:
ngene.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/pluto2:
pluto2.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/pt1:
earth-pt1.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/siano:
smsdvb.ko
smsmdtv.ko
smssdio.ko
smsusb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/ttpci:
budget-av.ko
budget-ci.ko
budget-core.ko
budget.ko
budget-patch.ko
dvb-ttpci.ko
ttpci-eeprom.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/ttusb-budget:
dvb-ttusb-budget.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/ttusb-dec:
ttusbdecfe.ko
ttusb_dec.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/radio:
dsbr100.ko
radio-maestro.ko
radio-maxiradio.ko
radio-mr800.ko
radio-si4713.ko
radio-tea5764.ko
radio-timb.ko
radio-wl1273.ko
saa7706h.ko
si470x
si4713-i2c.ko
tef6862.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/radio/si470x:
radio-i2c-si470x.ko
radio-usb-si470x.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/rc:
ene_ir.ko
imon.ko
ir-jvc-decoder.ko
ir-lirc-codec.ko
ir-nec-decoder.ko
ir-rc5-decoder.ko
ir-rc5-sz-decoder.ko
ir-rc6-decoder.ko
ir-sony-decoder.ko
keymaps
lirc_dev.ko
mceusb.ko
nuvoton-cir.ko
rc-core.ko
rc-loopback.ko
streamzap.ko
winbond-cir.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/rc/keymaps:
rc-adstech-dvb-t-pci.ko
rc-alink-dtu-m.ko
rc-anysee.ko
rc-apac-viewcomp.ko
rc-asus-pc39.ko
rc-ati-tv-wonder-hd-600.ko
rc-avermedia-a16d.ko
rc-avermedia-cardbus.ko
rc-avermedia-dvbt.ko
rc-avermedia.ko
rc-avermedia-m135a.ko
rc-avermedia-m733a-rm-k6.ko
rc-avermedia-rm-ks.ko
rc-avertv-303.ko
rc-azurewave-ad-tu700.ko
rc-behold-columbus.ko
rc-behold.ko
rc-budget-ci-old.ko
rc-cinergy-1400.ko
rc-cinergy.ko
rc-dib0700-nec.ko
rc-dib0700-rc5.ko
rc-digitalnow-tinytwin.ko
rc-digittrade.ko
rc-dm1105-nec.ko
rc-dntv-live-dvb-t.ko
rc-dntv-live-dvbt-pro.ko
rc-em-terratec.ko
rc-encore-enltv2.ko
rc-encore-enltv-fm53.ko
rc-encore-enltv.ko
rc-evga-indtube.ko
rc-eztv.ko
rc-flydvb.ko
rc-flyvideo.ko
rc-fusionhdtv-mce.ko
rc-gadmei-rm008z.ko
rc-genius-tvgo-a11mce.ko
rc-gotview7135.ko
rc-hauppauge-new.ko
rc-imon-mce.ko
rc-imon-pad.ko
rc-iodata-bctv7e.ko
rc-kaiomy.ko
rc-kworld-315u.ko
rc-kworld-plus-tv-analog.ko
rc-leadtek-y04g0051.ko
rc-lirc.ko
rc-lme2510.ko
rc-manli.ko
rc-msi-digivox-iii.ko
rc-msi-digivox-ii.ko
rc-msi-tvanywhere.ko
rc-msi-tvanywhere-plus.ko
rc-nebula.ko
rc-nec-terratec-cinergy-xs.ko
rc-norwood.ko
rc-npgtech.ko
rc-pctv-sedna.ko
rc-pinnacle-color.ko
rc-pinnacle-grey.ko
rc-pinnacle-pctv-hd.ko
rc-pixelview-002t.ko
rc-pixelview.ko
rc-pixelview-mk12.ko
rc-pixelview-new.ko
rc-powercolor-real-angel.ko
rc-proteus-2309.ko
rc-purpletv.ko
rc-pv951.ko
rc-rc5-hauppauge-new.ko
rc-rc5-tv.ko
rc-rc6-mce.ko
rc-real-audio-220-32-keys.ko
rc-streamzap.ko
rc-tbs-nec.ko
rc-terratec-cinergy-xs.ko
rc-terratec-slim.ko
rc-tevii-nec.ko
rc-total-media-in-hand.ko
rc-trekstor.ko
rc-tt-1500.ko
rc-twinhan1027.ko
rc-videomate-m1f.ko
rc-videomate-s350.ko
rc-videomate-tv-pvr.ko
rc-winfast.ko
rc-winfast-usbii-deluxe.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video:
adv7170.ko
adv7175.ko
adv7180.ko
au0828
bt819.ko
bt856.ko
bt866.ko
bt8xx
btcx-risc.ko
bw-qcam.ko
cafe_ccic.ko
cpia2
c-qcam.ko
cs5345.ko
cs53l32a.ko
cx18
cx231xx
cx2341x.ko
cx23885
cx25840
cx88
em28xx
et61x251
gspca
hdpvr
hexium_gemini.ko
hexium_orion.ko
imx074.ko
ir-kbd-i2c.ko
ivtv
ks0127.ko
m52790.ko
mem2mem_testdev.ko
meye.ko
msp3400.ko
mt9m001.ko
mt9m111.ko
mt9t031.ko
mt9t112.ko
mt9v011.ko
mt9v022.ko
mxb.ko
ov2640.ko
ov6650.ko
ov7670.ko
ov772x.ko
ov9640.ko
pvrusb2
pwc
rj54n1cb0c.ko
s2255drv.ko
saa6588.ko
saa7110.ko
saa7115.ko
saa7127.ko
saa7134
saa7164
saa717x.ko
saa7185.ko
sn9c102
soc_camera.ko
soc_camera_platform.ko
soc_mediabus.ko
sr030pc30.ko
stkwebcam.ko
tda7432.ko
tda9840.ko
tea6415c.ko
tea6420.ko
timblogiw.ko
tlg2300
tuner.ko
tvaudio.ko
tveeprom.ko
tvp5150.ko
tw9910.ko
upd64031a.ko
upd64083.ko
usbvision
uvc
v4l2-common.ko
v4l2-compat-ioctl32.ko
v4l2-int-device.ko
v4l2-mem2mem.ko
via-camera.ko
videobuf-core.ko
videobuf-dma-contig.ko
videobuf-dma-sg.ko
videobuf-dvb.ko
videobuf-vmalloc.ko
videodev.ko
vivi.ko
vp27smpx.ko
vpx3220.ko
w9966.ko
wm8739.ko
wm8775.ko
zoran
zr364xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/au0828:
au0828.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/bt8xx:
bttv.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/cpia2:
cpia2.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/cx18:
cx18-alsa.ko
cx18.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/cx231xx:
cx231xx-alsa.ko
cx231xx-dvb.ko
cx231xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/cx23885:
cx23885.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/cx25840:
cx25840.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/cx88:
cx8800.ko
cx8802.ko
cx88-alsa.ko
cx88-blackbird.ko
cx88-dvb.ko
cx88-vp3054-i2c.ko
cx88xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/em28xx:
em28xx-alsa.ko
em28xx-dvb.ko
em28xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/et61x251:
et61x251.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/gspca:
gl860
gspca_benq.ko
gspca_conex.ko
gspca_cpia1.ko
gspca_etoms.ko
gspca_finepix.ko
gspca_jeilinj.ko
gspca_konica.ko
gspca_main.ko
gspca_mars.ko
gspca_mr97310a.ko
gspca_ov519.ko
gspca_ov534_9.ko
gspca_ov534.ko
gspca_pac207.ko
gspca_pac7302.ko
gspca_pac7311.ko
gspca_sn9c2028.ko
gspca_sn9c20x.ko
gspca_sonixb.ko
gspca_sonixj.ko
gspca_spca1528.ko
gspca_spca500.ko
gspca_spca501.ko
gspca_spca505.ko
gspca_spca506.ko
gspca_spca508.ko
gspca_spca561.ko
gspca_sq905c.ko
gspca_sq905.ko
gspca_sq930x.ko
gspca_stk014.ko
gspca_stv0680.ko
gspca_sunplus.ko
gspca_t613.ko
gspca_tv8532.ko
gspca_vc032x.ko
gspca_xirlink_cit.ko
gspca_zc3xx.ko
m5602
stv06xx

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/gspca/gl860:
gspca_gl860.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/gspca/m5602:
gspca_m5602.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/gspca/stv06xx:
gspca_stv06xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/hdpvr:
hdpvr.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/ivtv:
ivtvfb.ko
ivtv.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/pvrusb2:
pvrusb2.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/pwc:
pwc.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/saa7134:
saa6752hs.ko
saa7134-alsa.ko
saa7134-dvb.ko
saa7134-empress.ko
saa7134.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/saa7164:
saa7164.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/sn9c102:
sn9c102.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/tlg2300:
poseidon.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/usbvision:
usbvision.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/uvc:
uvcvideo.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/zoran:
videocodec.ko
zr36016.ko
zr36050.ko
zr36060.ko
zr36067.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/memstick:
core
host

/lib/modules/2.6.38-8-generic/kernel/drivers/memstick/core:
memstick.ko
mspro_block.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/memstick/host:
jmb38x_ms.ko
tifm_ms.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/message:
fusion
i2o

/lib/modules/2.6.38-8-generic/kernel/drivers/message/fusion:
mptbase.ko
mptctl.ko
mptfc.ko
mptlan.ko
mptsas.ko
mptscsih.ko
mptspi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/message/i2o:
i2o_block.ko
i2o_bus.ko
i2o_config.ko
i2o_core.ko
i2o_proc.ko
i2o_scsi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mfd:
ab3100-otp.ko
cs5535-mfd.ko
htc-pasic3.ko
janz-cmodio.ko
lpc_sch.ko
mc13xxx-core.ko
pcf50633-adc.ko
pcf50633-gpio.ko
pcf50633.ko
rdc321x-southbridge.ko
sm501.ko
timberdale.ko
tps65010.ko
tps6507x.ko
ucb1400_core.ko
vx855.ko
wl1273-core.ko
wm8400-core.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/misc:
ad525x_dpot-i2c.ko
ad525x_dpot.ko
ad525x_dpot-spi.ko
apds9802als.ko
apds990x.ko
bh1770glc.ko
bh1780gli.ko
bmp085.ko
c2port
cb710
ds1682.ko
eeprom
enclosure.ko
hmc6352.ko
hpilo.ko
ibmasm
ics932s401.ko
ioc4.ko
isl29003.ko
isl29020.ko
iwmc3200top
pch_phub.ko
phantom.ko
ti_dac7512.ko
tifm_7xx1.ko
tifm_core.ko
ti-st
tsl2550.ko
vmw_balloon.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/misc/c2port:
c2port-duramar2150.ko
core.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/misc/cb710:
cb710.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/misc/eeprom:
at24.ko
at25.ko
eeprom_93cx6.ko
eeprom.ko
max6875.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/misc/ibmasm:
ibmasm.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/misc/iwmc3200top:
iwmc3200top.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/misc/ti-st:
st_drv.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mmc:
card
host

/lib/modules/2.6.38-8-generic/kernel/drivers/mmc/card:
mmc_block.ko
sdio_uart.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mmc/host:
cb710-mmc.ko
mmc_spi.ko
sdhci.ko
sdhci-pci.ko
sdhci-platform.ko
sdricoh_cs.ko
tifm_sd.ko
ushc.ko
via-sdmmc.ko
wbsd.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mtd:
ar7part.ko
chips
devices
ftl.ko
inftl.ko
lpddr
maps
mtd_blkdevs.ko
mtdblock.ko
mtdblock_ro.ko
mtdchar.ko
mtdconcat.ko
mtd.ko
mtdoops.ko
nand
nftl.ko
onenand
redboot.ko
rfd_ftl.ko
sm_ftl.ko
ssfdc.ko
tests
ubi

/lib/modules/2.6.38-8-generic/kernel/drivers/mtd/chips:
cfi_cmdset_0001.ko
cfi_cmdset_0002.ko
cfi_cmdset_0020.ko
cfi_probe.ko
cfi_util.ko
chipreg.ko
gen_probe.ko
jedec_probe.ko
map_absent.ko
map_ram.ko
map_rom.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mtd/devices:
block2mtd.ko
doc2000.ko
doc2001.ko
doc2001plus.ko
docecc.ko
docprobe.ko
m25p80.ko
mtd_dataflash.ko
mtdram.ko
phram.ko
pmc551.ko
slram.ko
sst25l.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mtd/lpddr:
lpddr_cmds.ko
qinfo_probe.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mtd/maps:
amd76xrom.ko
ck804xrom.ko
esb2rom.ko
gpio-addr-flash.ko
ichxrom.ko
intel_vr_nor.ko
l440gx.ko
map_funcs.ko
netsc520.ko
nettel.ko
pci.ko
pcmciamtd.ko
physmap.ko
plat-ram.ko
sbc_gxx.ko
sc520cdp.ko
scb2_flash.ko
ts5500_flash.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mtd/nand:
alauda.ko
cafe_nand.ko
denali.ko
diskonchip.ko
nand_ecc.ko
nand_ids.ko
nand.ko
nandsim.ko
plat_nand.ko
r852.ko
sm_common.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mtd/onenand:
generic.ko
onenand.ko
onenand_sim.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mtd/tests:
mtd_nandecctest.ko
mtd_oobtest.ko
mtd_pagetest.ko
mtd_readtest.ko
mtd_speedtest.ko
mtd_stresstest.ko
mtd_subpagetest.ko
mtd_torturetest.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/mtd/ubi:
gluebi.ko
ubi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net:
3c59x.ko
8139cp.ko
8139too.ko
8390.ko
acenic.ko
amd8111e.ko
appletalk
arcnet
atl1c
atl1e
atlx
atp.ko
b44.ko
benet
bna
bnx2.ko
bnx2x
bonding
bsd_comp.ko
caif
can
cassini.ko
chelsio
cnic.ko
cxgb3
cxgb4
cxgb4vf
de600.ko
de620.ko
defxx.ko
dnet.ko
dummy.ko
e1000
e1000e
e100.ko
enic
epic100.ko
eql.ko
ethoc.ko
fealnx.ko
forcedeth.ko
hamachi.ko
hamradio
hp100.ko
ifb.ko
igb
igbvf
ipg.ko
irda
ixgb
ixgbe
ixgbevf
jme.ko
ks8842.ko
ks8851.ko
ks8851_mll.ko
ksz884x.ko
macvlan.ko
mdio.ko
mlx4
myri10ge
natsemi.ko
ne2k-pci.ko
netconsole.ko
netxen
niu.ko
ns83820.ko
pch_gbe
pcmcia
pcnet32.ko
phy
plip.ko
ppp_async.ko
ppp_deflate.ko
ppp_mppe.ko
pppoe.ko
pppox.ko
ppp_synctty.ko
pptp.ko
qla3xxx.ko
qlcnic
qlge
r8169.ko
rrunner.ko
s2io.ko
sb1000.ko
sc92031.ko
sfc
sis190.ko
sis900.ko
skfp
skge.ko
sky2.ko
slip.ko
smsc9420.ko
starfire.ko
stmmac
sundance.ko
sungem.ko
sungem_phy.ko
sunhme.ko
tehuti.ko
tg3.ko
tlan.ko
tokenring
tulip
typhoon.ko
usb
veth.ko
via-rhine.ko
via-velocity.ko
virtio_net.ko
vmxnet3
vxge
wan
wimax
wireless
xen-netfront.ko
yellowfin.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/appletalk:
ipddp.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/arcnet:
arcnet.ko
arc-rawmode.ko
arc-rimi.ko
capmode.ko
com20020.ko
com20020-pci.ko
com90io.ko
com90xx.ko
rfc1051.ko
rfc1201.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/atl1c:
atl1c.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/atl1e:
atl1e.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/atlx:
atl1.ko
atl2.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/benet:
be2net.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/bna:
bna.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/bnx2x:
bnx2x.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/bonding:
bonding.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/caif:
caif_serial.ko
cfspi_slave.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/can:
can-dev.ko
janz-ican3.ko
mcp251x.ko
pch_can.ko
sja1000
slcan.ko
softing
usb
vcan.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/can/sja1000:
ems_pci.ko
kvaser_pci.ko
plx_pci.ko
sja1000.ko
sja1000_platform.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/can/softing:
softing_cs.ko
softing.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/can/usb:
ems_usb.ko
esd_usb2.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/chelsio:
cxgb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/cxgb3:
cxgb3.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/cxgb4:
cxgb4.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/cxgb4vf:
cxgb4vf.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/e1000:
e1000.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/e1000e:
e1000e.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/enic:
enic.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/hamradio:
6pack.ko
baycom_par.ko
baycom_ser_fdx.ko
baycom_ser_hdx.ko
bpqether.ko
hdlcdrv.ko
mkiss.ko
yam.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/igb:
igb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/igbvf:
igbvf.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/irda:
act200l-sir.ko
actisys-sir.ko
ali-ircc.ko
esi-sir.ko
girbil-sir.ko
irda-usb.ko
irtty-sir.ko
kingsun-sir.ko
ks959-sir.ko
ksdazzle-sir.ko
litelink-sir.ko
ma600-sir.ko
mcp2120-sir.ko
mcs7780.ko
nsc-ircc.ko
old_belkin-sir.ko
sir-dev.ko
smsc-ircc2.ko
stir4200.ko
tekram-sir.ko
toim3232-sir.ko
via-ircc.ko
vlsi_ir.ko
w83977af_ir.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/ixgb:
ixgb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/ixgbe:
ixgbe.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/ixgbevf:
ixgbevf.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/mlx4:
mlx4_core.ko
mlx4_en.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/myri10ge:
myri10ge.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/netxen:
netxen_nic.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/pch_gbe:
pch_gbe.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/pcmcia:
3c574_cs.ko
3c589_cs.ko
axnet_cs.ko
com20020_cs.ko
fmvj18x_cs.ko
ibmtr_cs.ko
nmclan_cs.ko
pcnet_cs.ko
smc91c92_cs.ko
xirc2ps_cs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/phy:
bcm63xx.ko
micrel.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/qlcnic:
qlcnic.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/qlge:
qlge.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/sfc:
sfc.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/skfp:
skfp.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/stmmac:
stmmac.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/tokenring:
3c359.ko
abyss.ko
olympic.ko
tms380tr.ko
tmspci.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/tulip:
de2104x.ko
de4x5.ko
dmfe.ko
tulip.ko
uli526x.ko
winbond-840.ko
xircom_cb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/usb:
asix.ko
catc.ko
cdc_eem.ko
cdc_ether.ko
cdc_ncm.ko
cdc-phonet.ko
cdc_subset.ko
cx82310_eth.ko
dm9601.ko
gl620a.ko
hso.ko
int51x1.ko
ipheth.ko
kaweth.ko
mcs7830.ko
net1080.ko
pegasus.ko
plusb.ko
rndis_host.ko
rtl8150.ko
sierra_net.ko
smsc75xx.ko
smsc95xx.ko
usbnet.ko
zaurus.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/vmxnet3:
vmxnet3.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/vxge:
vxge.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wan:
cyclomx.ko
cycx_drv.ko
dlci.ko
dscc4.ko
farsync.ko
hdlc_cisco.ko
hdlc_fr.ko
hdlc.ko
hdlc_ppp.ko
hdlc_raw_eth.ko
hdlc_raw.ko
hdlc_x25.ko
lapbether.ko
lmc
pci200syn.ko
sbni.ko
wanxl.ko
x25_asy.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wan/lmc:
lmc.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wimax:
i2400m

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wimax/i2400m:
i2400m.ko
i2400m-sdio.ko
i2400m-usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless:
adm8211.ko
airo_cs.ko
airo.ko
at76c50x-usb.ko
ath
atmel_cs.ko
atmel.ko
atmel_pci.ko
b43
b43legacy
hostap
ipw2x00
iwlwifi
iwmc3200wifi
libertas
libertas_tf
mac80211_hwsim.ko
mwl8k.ko
orinoco
p54
prism54
ray_cs.ko
rndis_wlan.ko
rt2x00
rtl818x
rtlwifi
wl1251
wl12xx
wl3501_cs.ko
zd1201.ko
zd1211rw

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath:
ar9170
ath5k
ath9k
ath.ko
carl9170

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ar9170:
ar9170usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath5k:
ath5k.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k:
ath9k_common.ko
ath9k_htc.ko
ath9k_hw.ko
ath9k.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/carl9170:
carl9170.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/b43:
b43.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/b43legacy:
b43legacy.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/hostap:
hostap_cs.ko
hostap.ko
hostap_pci.ko
hostap_plx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ipw2x00:
ipw2100.ko
ipw2200.ko
libipw.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwlwifi:
iwl3945.ko
iwlagn.ko
iwlcore.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwmc3200wifi:
iwmc3200wifi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/libertas:
libertas_cs.ko
libertas.ko
libertas_sdio.ko
libertas_spi.ko
usb8xxx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/libertas_tf:
libertas_tf.ko
libertas_tf_usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/orinoco:
orinoco_cs.ko
orinoco.ko
orinoco_nortel.ko
orinoco_plx.ko
orinoco_tmd.ko
orinoco_usb.ko
spectrum_cs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/p54:
p54common.ko
p54pci.ko
p54spi.ko
p54usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/prism54:
prism54.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00:
rt2400pci.ko
rt2500pci.ko
rt2500usb.ko
rt2800lib.ko
rt2800pci.ko
rt2800usb.ko
rt2x00lib.ko
rt2x00pci.ko
rt2x00usb.ko
rt61pci.ko
rt73usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtl818x:
rtl8180
rtl8187

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtl818x/rtl8180:
rtl8180.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtl818x/rtl8187:
rtl8187.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi:
rtl8192ce
rtlwifi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce:
rtl8192ce.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/wl1251:
wl1251.ko
wl1251_sdio.ko
wl1251_spi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/wl12xx:
wl12xx.ko
wl12xx_sdio.ko
wl12xx_spi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/zd1211rw:
zd1211rw.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/nfc:
pn544.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/parport:
parport_ax88796.ko
parport_cs.ko
parport.ko
parport_pc.ko
parport_serial.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/pci:
hotplug
pci-stub.ko
xen-pcifront.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/pci/hotplug:
acpiphp_ibm.ko
acpiphp.ko
cpcihp_generic.ko
cpcihp_zt5550.ko
fakephp.ko
shpchp.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/pcmcia:
i82092.ko
pcmcia_core.ko
pcmcia.ko
pcmcia_rsrc.ko
pd6729.ko
yenta_socket.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/platform:
x86

/lib/modules/2.6.38-8-generic/kernel/drivers/platform/x86:
acerhdf.ko
acer-wmi.ko
asus-laptop.ko
classmate-laptop.ko
compal-laptop.ko
dell-laptop.ko
dell-wmi-aio.ko
dell-wmi.ko
eeepc-laptop.ko
eeepc-wmi.ko
fujitsu-laptop.ko
hdaps.ko
hp-wmi.ko
ibm_rtl.ko
ideapad-laptop.ko
intel_ips.ko
intel_menlow.ko
msi-laptop.ko
msi-wmi.ko
panasonic-laptop.ko
sony-laptop.ko
thinkpad_acpi.ko
topstar-laptop.ko
toshiba_acpi.ko
toshiba_bluetooth.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/power:
bq20z75.ko
bq27x00_battery.ko
da9030_battery.ko
ds2760_battery.ko
ds2782_battery.ko
gpio-charger.ko
isp1704_charger.ko
max17040_battery.ko
max17042_battery.ko
max8925_power.ko
pcf50633-charger.ko
pda_power.ko
test_power.ko
wm831x_backup.ko
wm831x_power.ko
wm8350_power.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/pps:
clients
pps_core.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/pps/clients:
pps-ldisc.ko
pps_parport.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/regulator:
ab3100.ko
ad5398.ko
bq24022.ko
da903x.ko
isl6271a-regulator.ko
lp3971.ko
lp3972.ko
max1586.ko
max8649.ko
max8660.ko
max8925-regulator.ko
max8952.ko
max8998.ko
mc13783-regulator.ko
mc13892-regulator.ko
mc13xxx-regulator-core.ko
pcf50633-regulator.ko
tps65023-regulator.ko
tps6507x-regulator.ko
tps6524x-regulator.ko
tps6586x-regulator.ko
userspace-consumer.ko
virtual.ko
wm831x-dcdc.ko
wm831x-isink.ko
wm831x-ldo.ko
wm8350-regulator.ko
wm8400-regulator.ko
wm8994-regulator.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/rtc:
rtc-ab3100.ko
rtc-ab8500.ko
rtc-bq32k.ko
rtc-bq4802.ko
rtc-ds1286.ko
rtc-ds1305.ko
rtc-ds1307.ko
rtc-ds1374.ko
rtc-ds1390.ko
rtc-ds1511.ko
rtc-ds1553.ko
rtc-ds1672.ko
rtc-ds1742.ko
rtc-ds3232.ko
rtc-ds3234.ko
rtc-fm3130.ko
rtc-isl12022.ko
rtc-isl1208.ko
rtc-m41t80.ko
rtc-m41t94.ko
rtc-m48t35.ko
rtc-m48t59.ko
rtc-m48t86.ko
rtc-max6900.ko
rtc-max6902.ko
rtc-max8925.ko
rtc-max8998.ko
rtc-mc13xxx.ko
rtc-msm6242.ko
rtc-pcf2123.ko
rtc-pcf50633.ko
rtc-pcf8563.ko
rtc-pcf8583.ko
rtc-r9701.ko
rtc-rp5c01.ko
rtc-rs5c348.ko
rtc-rs5c372.ko
rtc-rx8025.ko
rtc-rx8581.ko
rtc-s35390a.ko
rtc-stk17ta8.ko
rtc-test.ko
rtc-v3020.ko
rtc-wm831x.ko
rtc-wm8350.ko
rtc-x1205.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi:
3w-9xxx.ko
3w-sas.ko
3w-xxxx.ko
a100u2w.ko
aacraid
advansys.ko
aic7xxx
aic94xx
arcmsr
atp870u.ko
be2iscsi
bfa
bnx2i
BusLogic.ko
ch.ko
cxgbi
dc395x.ko
device_handler
dmx3191d.ko
dpt_i2o.ko
eata.ko
fcoe
fdomain.ko
fnic
gdth.ko
hpsa.ko
hptiop.ko
imm.ko
initio.ko
ipr.ko
ips.ko
iscsi_boot_sysfs.ko
iscsi_tcp.ko
libfc
libiscsi.ko
libiscsi_tcp.ko
libsas
libsrp.ko
lpfc
megaraid
megaraid.ko
mpt2sas
mvsas
osd
osst.ko
pcmcia
pm8001
pmcraid.ko
ppa.ko
qla1280.ko
qla2xxx
qla4xxx
qlogicfas408.ko
raid_class.ko
scsi_debug.ko
scsi_tgt.ko
scsi_transport_fc.ko
scsi_transport_iscsi.ko
scsi_transport_sas.ko
scsi_transport_spi.ko
scsi_transport_srp.ko
scsi_wait_scan.ko
ses.ko
stex.ko
st.ko
sym53c8xx_2
tmscsim.ko
vmw_pvscsi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/aacraid:
aacraid.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/aic7xxx:
aic79xx.ko
aic7xxx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/aic94xx:
aic94xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/arcmsr:
arcmsr.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/be2iscsi:
be2iscsi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/bfa:
bfa.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/bnx2i:
bnx2i.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/cxgbi:
cxgb3i
cxgb4i
libcxgbi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/cxgbi/cxgb3i:
cxgb3i.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/cxgbi/cxgb4i:
cxgb4i.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/device_handler:
scsi_dh_alua.ko
scsi_dh_emc.ko
scsi_dh_hp_sw.ko
scsi_dh_rdac.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/fcoe:
fcoe.ko
libfcoe.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/fnic:
fnic.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/libfc:
libfc.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/libsas:
libsas.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/lpfc:
lpfc.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/megaraid:
megaraid_mbox.ko
megaraid_mm.ko
megaraid_sas.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/mpt2sas:
mpt2sas.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/mvsas:
mvsas.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/osd:
libosd.ko
osd.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/pcmcia:
aha152x_cs.ko
fdomain_cs.ko
qlogic_cs.ko
sym53c500_cs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/pm8001:
pm8001.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/qla2xxx:
qla2xxx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/qla4xxx:
qla4xxx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/scsi/sym53c8xx_2:
sym53c8xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/spi:
dw_spi_midpci.ko
spi_bitbang.ko
spi_butterfly.ko
spidev.ko
spi_gpio.ko
spi_lm70llp.ko
spi_topcliff_pch.ko
tle62x0.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/ssb:
ssb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging:
asus_oled
autofs
bcm
brcm80211
comedi
cptm1217
crystalhd
cx25821
cxt1e1
dabusb
dt3155v4l
easycap
echo
et131x
frontier
ft1000
go7007
hv
iio
keucr
line6
lirc
panel
phison
pohmelfs
quatech_usb2
quickstart
rt2860
rt2870
rtl8187se
rtl8192e
rtl8192u
rtl8712
rts_pstor
samsung-laptop
sbe-2t3e3
se401
sep
serqt_usb2
slicoss
sm7xx
smbfs
speakup
ste_rmi4
ti-st
tm6000
usbip
usbvideo
vme
vt6656
winbond
wlags49_h2
wlags49_h25
wlan-ng
xgifb
zram

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/asus_oled:
asus_oled.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/autofs:
autofs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/bcm:
bcm_wimax.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/brcm80211:
brcm80211.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/comedi:
comedi.ko
drivers
kcomedilib

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/comedi/drivers:
8255.ko
addi_apci_035.ko
addi_apci_1032.ko
addi_apci_1500.ko
addi_apci_1516.ko
addi_apci_1564.ko
addi_apci_16xx.ko
addi_apci_2016.ko
addi_apci_2032.ko
addi_apci_2200.ko
addi_apci_3001.ko
addi_apci_3120.ko
addi_apci_3501.ko
addi_apci_3xxx.ko
adl_pci6208.ko
adl_pci7230.ko
adl_pci7296.ko
adl_pci7432.ko
adl_pci8164.ko
adl_pci9111.ko
adl_pci9118.ko
adv_pci1710.ko
adv_pci1723.ko
adv_pci_dio.ko
amplc_dio200.ko
amplc_pc236.ko
amplc_pc263.ko
amplc_pci224.ko
amplc_pci230.ko
cb_das16_cs.ko
cb_pcidas64.ko
cb_pcidas.ko
cb_pcidda.ko
cb_pcidio.ko
cb_pcimdas.ko
cb_pcimdda.ko
comedi_bond.ko
comedi_fc.ko
comedi_parport.ko
comedi_test.ko
contec_pci_dio.ko
daqboard2000.ko
das08_cs.ko
das08.ko
dt3000.ko
dt9812.ko
gsc_hpdi.ko
icp_multi.ko
ii_pci20kc.ko
jr3_pci.ko
ke_counter.ko
me4000.ko
me_daq.ko
mite.ko
ni_6527.ko
ni_65xx.ko
ni_660x.ko
ni_670x.ko
ni_daq_700.ko
ni_daq_dio24.ko
ni_labpc_cs.ko
ni_labpc.ko
ni_mio_cs.ko
ni_pcidio.ko
ni_pcimio.ko
ni_tiocmd.ko
ni_tio.ko
pcm_common.ko
quatech_daqp_cs.ko
rtd520.ko
s526.ko
s626.ko
serial2002.ko
skel.ko
ssv_dnp.ko
unioxx5.ko
usbduxfast.ko
usbdux.ko
vmk80xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/comedi/kcomedilib:
kcomedilib.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/cptm1217:
clearpad_tm1217.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/crystalhd:
crystalhd.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/cx25821:
cx25821-alsa.ko
cx25821.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/cxt1e1:
cxt1e1.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/dabusb:
dabusb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/dt3155v4l:
dt3155v4l.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/easycap:
easycap.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/echo:
echo.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/et131x:
et131x.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/frontier:
alphatrack.ko
tranzport.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/ft1000:
ft1000-usb

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/ft1000/ft1000-usb:
ft1000.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/go7007:
go7007.ko
go7007-usb.ko
s2250.ko
s2250-loader.ko
wis-ov7640.ko
wis-saa7113.ko
wis-saa7115.ko
wis-sony-tuner.ko
wis-tw2804.ko
wis-tw9903.ko
wis-uda1342.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/hv:
hv_blkvsc.ko
hv_netvsc.ko
hv_storvsc.ko
hv_timesource.ko
hv_utils.ko
hv_vmbus.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio:
accel
adc
addac
dac
dds
gyro
imu
industrialio.ko
light
magnetometer
meter
resolver
ring_sw.ko
trigger

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/accel:
adis16201.ko
adis16203.ko
adis16204.ko
adis16209.ko
adis16220.ko
adis16240.ko
kxsd9.ko
lis3l02dq.ko
sca3000.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/adc:
ad7150.ko
ad7152.ko
ad7291.ko
ad7298.ko
ad7314.ko
ad7476.ko
ad7745.ko
ad7816.ko
ad7887.ko
ad799x.ko
adt7310.ko
adt7410.ko
adt75.ko
max1363.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/addac:
adt7316-i2c.ko
adt7316.ko
adt7316-spi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/dac:
ad5446.ko
ad5624r_spi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/dds:
ad5930.ko
ad9832.ko
ad9834.ko
ad9850.ko
ad9852.ko
ad9910.ko
ad9951.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/gyro:
adis16060.ko
adis16080.ko
adis16130.ko
adis16251.ko
adis16260.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/imu:
adis16300.ko
adis16350.ko
adis16400.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/light:
isl29018.ko
tsl2563.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/magnetometer:
ak8975.ko
hmc5843.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/meter:
ade7753.ko
ade7754.ko
ade7758.ko
ade7759.ko
ade7854-i2c.ko
ade7854.ko
ade7854-spi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/resolver:
ad2s120x.ko
ad2s1210.ko
ad2s90.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/iio/trigger:
iio-trig-gpio.ko
iio-trig-periodic-rtc.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/keucr:
keucr.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/line6:
line6usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/lirc:
lirc_bt829.ko
lirc_igorplugusb.ko
lirc_imon.ko
lirc_it87.ko
lirc_ite8709.ko
lirc_sasem.ko
lirc_serial.ko
lirc_sir.ko
lirc_ttusbir.ko
lirc_zilog.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/panel:
panel.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/phison:
phison.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/pohmelfs:
pohmelfs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/quatech_usb2:
quatech_usb2.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/quickstart:
quickstart.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860:
rt2860sta.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870:
rt2870sta.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8187se:
r8187se.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8192e:
r8192e_pci.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8192u:
r8192u_usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8712:
r8712u.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rts_pstor:
rts_pstor.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/samsung-laptop:
samsung-laptop.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/sbe-2t3e3:
sbe-2t3e3.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/se401:
se401.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/sep:
sep_driver.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/serqt_usb2:
serqt_usb2.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/slicoss:
slicoss.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/sm7xx:
sm7xx.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/smbfs:
smbfs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/speakup:
speakup_acntpc.ko
speakup_acntsa.ko
speakup_apollo.ko
speakup_audptr.ko
speakup_bns.ko
speakup_decext.ko
speakup_decpc.ko
speakup_dectlk.ko
speakup_dtlk.ko
speakup_dummy.ko
speakup_keypc.ko
speakup.ko
speakup_ltlk.ko
speakup_soft.ko
speakup_spkout.ko
speakup_txprt.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/ste_rmi4:
synaptics_i2c_rmi4.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/ti-st:
bt_drv.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/tm6000:
tm6000-alsa.ko
tm6000-dvb.ko
tm6000.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/usbip:
usbip_common_mod.ko
usbip.ko
vhci-hcd.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/usbvideo:
usbvideo.ko
vicam.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/vme:
boards
bridges
devices
vme.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/vme/boards:
vme_vmivme7805.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/vme/bridges:
vme_ca91cx42.ko
vme_tsi148.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/vme/devices:
vme_user.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/vt6656:
vt6656_stage.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/winbond:
w35und.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/wlags49_h2:
wlags49_h2_cs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/wlags49_h25:
wlags49_h25_cs.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/wlan-ng:
prism2_usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/xgifb:
xgifb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/staging/zram:
zram.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/target:
target_core_file.ko
target_core_iblock.ko
target_core_mod.ko
target_core_pscsi.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/telephony:
ixj.ko
ixj_pcmcia.ko
phonedev.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/tty:
n_hdlc.ko
n_r3964.ko
serial

/lib/modules/2.6.38-8-generic/kernel/drivers/tty/serial:
altera_jtaguart.ko
altera_uart.ko
jsm
max3100.ko
max3107.ko
mfd.ko
mrst_max3110.ko
pch_uart.ko
serial_cs.ko
timbuart.ko
uartlite.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/tty/serial/jsm:
jsm.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/uio:
uio_aec.ko
uio_cif.ko
uio.ko
uio_netx.ko
uio_pci_generic.ko
uio_pdrv_genirq.ko
uio_pdrv.ko
uio_sercos3.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb:
atm
c67x00
class
gadget
host
image
misc
otg
serial
storage
wusbcore

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/atm:
cxacru.ko
speedtch.ko
ueagle-atm.ko
usbatm.ko
xusbatm.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/c67x00:
c67x00.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/class:
cdc-acm.ko
cdc-wdm.ko
usblp.ko
usbtmc.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/gadget:
dummy_hcd.ko
gadgetfs.ko
g_audio.ko
g_cdc.ko
g_dbgp.ko
g_ether.ko
g_ffs.ko
g_file_storage.ko
g_hid.ko
g_mass_storage.ko
g_midi.ko
g_ncm.ko
g_nokia.ko
g_printer.ko
g_serial.ko
g_webcam.ko
g_zero.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/host:
hwa-hc.ko
isp116x-hcd.ko
isp1362-hcd.ko
isp1760.ko
oxu210hp-hcd.ko
r8a66597-hcd.ko
sl811_cs.ko
sl811-hcd.ko
u132-hcd.ko
whci
xhci-hcd.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/host/whci:
whci-hcd.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/image:
mdc800.ko
microtek.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/misc:
adutux.ko
appledisplay.ko
cypress_cy7c63.ko
cytherm.ko
emi26.ko
emi62.ko
ftdi-elan.ko
idmouse.ko
iowarrior.ko
isight_firmware.ko
ldusb.ko
legousbtower.ko
rio500.ko
sisusbvga
trancevibrator.ko
usblcd.ko
usbled.ko
usbsevseg.ko
usbtest.ko
uss720.ko
yurex.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/misc/sisusbvga:
sisusbvga.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/otg:
ab8500-usb.ko
gpio_vbus.ko
nop-usb-xceiv.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/serial:
aircable.ko
ark3116.ko
belkin_sa.ko
ch341.ko
cp210x.ko
cyberjack.ko
cypress_m8.ko
digi_acceleport.ko
empeg.ko
ftdi_sio.ko
funsoft.ko
garmin_gps.ko
hp4x.ko
io_edgeport.ko
io_ti.ko
ipaq.ko
ipw.ko
ir-usb.ko
iuu_phoenix.ko
keyspan.ko
keyspan_pda.ko
kl5kusb105.ko
kobil_sct.ko
mct_u232.ko
mos7720.ko
mos7840.ko
moto_modem.ko
navman.ko
omninet.ko
opticon.ko
option.ko
oti6858.ko
pl2303.ko
qcaux.ko
qcserial.ko
safe_serial.ko
sam-ba.ko
siemens_mpi.ko
sierra.ko
spcp8x5.ko
ssu100.ko
symbolserial.ko
ti_usb_3410_5052.ko
usb_debug.ko
usbserial.ko
usb_wwan.ko
visor.ko
vivopay-serial.ko
whiteheat.ko
zio.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/storage:
uas.ko
ums-alauda.ko
ums-cypress.ko
ums-datafab.ko
ums-freecom.ko
ums-isd200.ko
ums-jumpshot.ko
ums-karma.ko
ums-onetouch.ko
ums-sddr09.ko
ums-sddr55.ko
ums-usbat.ko
usb-storage.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/usb/wusbcore:
wusb-cbaf.ko
wusbcore.ko
wusb-wa.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/uwb:
hwa-rc.ko
i1480
umc.ko
uwb.ko
whci.ko
whc-rc.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/uwb/i1480:
dfu
i1480-est.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/uwb/i1480/dfu:
i1480-dfu-usb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/vhost:
vhost_net.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video:
arcfb.ko
arkfb.ko
aty
backlight
broadsheetfb.ko
carminefb.ko
cirrusfb.ko
cyber2000fb.ko
display
fb_ddc.ko
fb_sys_fops.ko
geode
hecubafb.ko
hgafb.ko
intelfb
kyro
macmodes.ko
matrox
mb862xx
metronomefb.ko
n411.ko
neofb.ko
nvidia
output.ko
pm2fb.ko
pm3fb.ko
riva
s1d13xxxfb.ko
s3fb.ko
savage
sis
sm501fb.ko
sstfb.ko
svgalib.ko
syscopyarea.ko
sysfillrect.ko
sysimgblt.ko
tdfxfb.ko
tmiofb.ko
tridentfb.ko
udlfb.ko
uvesafb.ko
vermilion
vesafb.ko
vga16fb.ko
vgastate.ko
via
vt8623fb.ko
xen-fbfront.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/aty:
aty128fb.ko
atyfb.ko
radeonfb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/backlight:
88pm860x_bl.ko
adp5520_bl.ko
adp8860_bl.ko
cr_bllcd.ko
da903x_bl.ko
generic_bl.ko
ili9320.ko
kb3886_bl.ko
l4f00242t03.ko
lcd.ko
lms283gf05.ko
ltv350qv.ko
max8925_bl.ko
mbp_nvidia_bl.ko
pcf50633-backlight.ko
platform_lcd.ko
progear_bl.ko
s6e63m0.ko
tdo24m.ko
vgg2432a4.ko
wm831x_bl.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/display:
display.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/geode:
gx1fb.ko
gxfb.ko
lxfb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/intelfb:
intelfb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/kyro:
kyrofb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/matrox:
g450_pll.ko
i2c-matroxfb.ko
matroxfb_accel.ko
matroxfb_base.ko
matroxfb_crtc2.ko
matroxfb_DAC1064.ko
matroxfb_g450.ko
matroxfb_maven.ko
matroxfb_misc.ko
matroxfb_Ti3026.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/mb862xx:
mb862xxfb_accel.ko
mb862xxfb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/nvidia:
nvidiafb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/riva:
rivafb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/savage:
savagefb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/sis:
sisfb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/vermilion:
crvml.ko
vmlfb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/video/via:
viafb.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/virtio:
virtio_balloon.ko
virtio.ko
virtio_pci.ko
virtio_ring.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/w1:
masters
slaves
wire.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/w1/masters:
ds2482.ko
ds2490.ko
matrox_w1.ko
w1-gpio.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/w1/slaves:
w1_bq27000.ko
w1_ds2423.ko
w1_ds2431.ko
w1_ds2433.ko
w1_ds2760.ko
w1_smem.ko
w1_therm.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/watchdog:
acquirewdt.ko
advantechwdt.ko
alim1535_wdt.ko
alim7101_wdt.ko
cpu5wdt.ko
eurotechwdt.ko
f71808e_wdt.ko
i6300esb.ko
ib700wdt.ko
ibmasr.ko
it8712f_wdt.ko
it87_wdt.ko
iTCO_vendor_support.ko
iTCO_wdt.ko
machzwd.ko
nv_tco.ko
pc87413_wdt.ko
pcwd_pci.ko
pcwd_usb.ko
sbc60xxwdt.ko
sbc8360.ko
sbc_epx_c3.ko
sbc_fitpc2_wdt.ko
sc1200wdt.ko
sc520_wdt.ko
sch311x_wdt.ko
smsc37b787_wdt.ko
softdog.ko
sp5100_tco.ko
w83627hf_wdt.ko
w83697hf_wdt.ko
w83697ug_wdt.ko
w83877f_wdt.ko
w83977f_wdt.ko
wafer5823wdt.ko
wdt_pci.ko
wm831x_wdt.ko
wm8350_wdt.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/xen:
xenbus
xen-evtchn.ko
xenfs
xen-gntdev.ko
xen-platform-pci.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/xen/xenbus:
xenbus_probe_frontend.ko

/lib/modules/2.6.38-8-generic/kernel/drivers/xen/xenfs:
xenfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs:
9p
adfs
affs
afs
autofs4
befs
bfs
binfmt_misc.ko
btrfs
cachefiles
ceph
cifs
coda
configfs
cramfs
dlm
efs
exofs
exportfs
fat
freevxfs
fscache
fuse
gfs2
hfs
hfsplus
hpfs
isofs
jffs2
jfs
lockd
minix
ncpfs
nfs
nfs_common
nfsd
nilfs2
nls
ntfs
ocfs2
omfs
qnx4
quota
reiserfs
romfs
squashfs
sysv
ubifs
udf
ufs
xfs

/lib/modules/2.6.38-8-generic/kernel/fs/9p:
9p.ko

/lib/modules/2.6.38-8-generic/kernel/fs/adfs:
adfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/affs:
affs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/afs:
kafs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/autofs4:
autofs4.ko

/lib/modules/2.6.38-8-generic/kernel/fs/befs:
befs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/bfs:
bfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/btrfs:
btrfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/cachefiles:
cachefiles.ko

/lib/modules/2.6.38-8-generic/kernel/fs/ceph:
ceph.ko

/lib/modules/2.6.38-8-generic/kernel/fs/cifs:
cifs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/coda:
coda.ko

/lib/modules/2.6.38-8-generic/kernel/fs/configfs:
configfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/cramfs:
cramfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/dlm:
dlm.ko

/lib/modules/2.6.38-8-generic/kernel/fs/efs:
efs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/exofs:
exofs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/exportfs:
exportfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/fat:
fat.ko
msdos.ko
vfat.ko

/lib/modules/2.6.38-8-generic/kernel/fs/freevxfs:
freevxfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/fscache:
fscache.ko

/lib/modules/2.6.38-8-generic/kernel/fs/fuse:
cuse.ko

/lib/modules/2.6.38-8-generic/kernel/fs/gfs2:
gfs2.ko

/lib/modules/2.6.38-8-generic/kernel/fs/hfs:
hfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/hfsplus:
hfsplus.ko

/lib/modules/2.6.38-8-generic/kernel/fs/hpfs:
hpfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/isofs:
isofs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/jffs2:
jffs2.ko

/lib/modules/2.6.38-8-generic/kernel/fs/jfs:
jfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/lockd:
lockd.ko

/lib/modules/2.6.38-8-generic/kernel/fs/minix:
minix.ko

/lib/modules/2.6.38-8-generic/kernel/fs/ncpfs:
ncpfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/nfs:
nfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/nfs_common:
nfs_acl.ko

/lib/modules/2.6.38-8-generic/kernel/fs/nfsd:
nfsd.ko

/lib/modules/2.6.38-8-generic/kernel/fs/nilfs2:
nilfs2.ko

/lib/modules/2.6.38-8-generic/kernel/fs/nls:
nls_ascii.ko
nls_cp1250.ko
nls_cp1251.ko
nls_cp1255.ko
nls_cp437.ko
nls_cp737.ko
nls_cp775.ko
nls_cp850.ko
nls_cp852.ko
nls_cp855.ko
nls_cp857.ko
nls_cp860.ko
nls_cp861.ko
nls_cp862.ko
nls_cp863.ko
nls_cp864.ko
nls_cp865.ko
nls_cp866.ko
nls_cp869.ko
nls_cp874.ko
nls_cp932.ko
nls_cp936.ko
nls_cp949.ko
nls_cp950.ko
nls_euc-jp.ko
nls_iso8859-13.ko
nls_iso8859-14.ko
nls_iso8859-15.ko
nls_iso8859-1.ko
nls_iso8859-2.ko
nls_iso8859-3.ko
nls_iso8859-4.ko
nls_iso8859-5.ko
nls_iso8859-6.ko
nls_iso8859-7.ko
nls_iso8859-9.ko
nls_koi8-r.ko
nls_koi8-ru.ko
nls_koi8-u.ko
nls_utf8.ko

/lib/modules/2.6.38-8-generic/kernel/fs/ntfs:
ntfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/ocfs2:
cluster
dlm
dlmfs
ocfs2.ko
ocfs2_stackglue.ko
ocfs2_stack_o2cb.ko
ocfs2_stack_user.ko

/lib/modules/2.6.38-8-generic/kernel/fs/ocfs2/cluster:
ocfs2_nodemanager.ko

/lib/modules/2.6.38-8-generic/kernel/fs/ocfs2/dlm:
ocfs2_dlm.ko

/lib/modules/2.6.38-8-generic/kernel/fs/ocfs2/dlmfs:
ocfs2_dlmfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/omfs:
omfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/qnx4:
qnx4.ko

/lib/modules/2.6.38-8-generic/kernel/fs/quota:
quota_tree.ko
quota_v1.ko
quota_v2.ko

/lib/modules/2.6.38-8-generic/kernel/fs/reiserfs:
reiserfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/romfs:
romfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/squashfs:
squashfs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/sysv:
sysv.ko

/lib/modules/2.6.38-8-generic/kernel/fs/ubifs:
ubifs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/udf:
udf.ko

/lib/modules/2.6.38-8-generic/kernel/fs/ufs:
ufs.ko

/lib/modules/2.6.38-8-generic/kernel/fs/xfs:
xfs.ko

/lib/modules/2.6.38-8-generic/kernel/lib:
cpu-notifier-error-inject.ko
crc7.ko
crc-ccitt.ko
crc-itu-t.ko
libcrc32c.ko
lru_cache.ko
raid6
reed_solomon
ts_bm.ko
ts_fsm.ko
ts_kmp.ko
xz
zlib_deflate

/lib/modules/2.6.38-8-generic/kernel/lib/raid6:
raid6_pq.ko

/lib/modules/2.6.38-8-generic/kernel/lib/reed_solomon:
reed_solomon.ko

/lib/modules/2.6.38-8-generic/kernel/lib/xz:
xz_dec_test.ko

/lib/modules/2.6.38-8-generic/kernel/lib/zlib_deflate:
zlib_deflate.ko

/lib/modules/2.6.38-8-generic/kernel/net:
802
8021q
9p
appletalk
atm
ax25
batman-adv
bluetooth
bridge
caif
can
ceph
core
dccp
decnet
econet
ieee802154
ipv4
ipv6
ipx
irda
key
l2tp
lapb
llc
mac80211
netfilter
netrom
phonet
rds
rose
rxrpc
sched
sctp
sunrpc
tipc
wanrouter
wimax
wireless
x25
xfrm

/lib/modules/2.6.38-8-generic/kernel/net/802:
garp.ko
p8023.ko
stp.ko

/lib/modules/2.6.38-8-generic/kernel/net/8021q:
8021q.ko

/lib/modules/2.6.38-8-generic/kernel/net/9p:
9pnet.ko
9pnet_rdma.ko
9pnet_virtio.ko

/lib/modules/2.6.38-8-generic/kernel/net/appletalk:
appletalk.ko

/lib/modules/2.6.38-8-generic/kernel/net/atm:
atm.ko
br2684.ko
clip.ko
lec.ko
mpoa.ko
pppoatm.ko

/lib/modules/2.6.38-8-generic/kernel/net/ax25:
ax25.ko

/lib/modules/2.6.38-8-generic/kernel/net/batman-adv:
batman-adv.ko

/lib/modules/2.6.38-8-generic/kernel/net/bluetooth:
bluetooth.ko
bnep
cmtp
hidp
l2cap.ko
rfcomm
sco.ko

/lib/modules/2.6.38-8-generic/kernel/net/bluetooth/bnep:
bnep.ko

/lib/modules/2.6.38-8-generic/kernel/net/bluetooth/cmtp:
cmtp.ko

/lib/modules/2.6.38-8-generic/kernel/net/bluetooth/hidp:
hidp.ko

/lib/modules/2.6.38-8-generic/kernel/net/bluetooth/rfcomm:
rfcomm.ko

/lib/modules/2.6.38-8-generic/kernel/net/bridge:
bridge.ko
netfilter

/lib/modules/2.6.38-8-generic/kernel/net/bridge/netfilter:
ebt_802_3.ko
ebtable_broute.ko
ebtable_filter.ko
ebtable_nat.ko
ebtables.ko
ebt_among.ko
ebt_arp.ko
ebt_arpreply.ko
ebt_dnat.ko
ebt_ip6.ko
ebt_ip.ko
ebt_limit.ko
ebt_log.ko
ebt_mark.ko
ebt_mark_m.ko
ebt_nflog.ko
ebt_pkttype.ko
ebt_redirect.ko
ebt_snat.ko
ebt_stp.ko
ebt_ulog.ko
ebt_vlan.ko

/lib/modules/2.6.38-8-generic/kernel/net/caif:
caif.ko
caif_socket.ko
chnl_net.ko

/lib/modules/2.6.38-8-generic/kernel/net/can:
can-bcm.ko
can.ko
can-raw.ko

/lib/modules/2.6.38-8-generic/kernel/net/ceph:
libceph.ko

/lib/modules/2.6.38-8-generic/kernel/net/core:
pktgen.ko

/lib/modules/2.6.38-8-generic/kernel/net/dccp:
dccp_diag.ko
dccp_ipv4.ko
dccp_ipv6.ko
dccp.ko
dccp_probe.ko

/lib/modules/2.6.38-8-generic/kernel/net/decnet:
decnet.ko
netfilter

/lib/modules/2.6.38-8-generic/kernel/net/decnet/netfilter:
dn_rtmsg.ko

/lib/modules/2.6.38-8-generic/kernel/net/econet:
econet.ko

/lib/modules/2.6.38-8-generic/kernel/net/ieee802154:
af_802154.ko
ieee802154.ko

/lib/modules/2.6.38-8-generic/kernel/net/ipv4:
ah4.ko
esp4.ko
gre.ko
ipcomp.ko
ip_gre.ko
ipip.ko
netfilter
tcp_bic.ko
tcp_highspeed.ko
tcp_htcp.ko
tcp_hybla.ko
tcp_illinois.ko
tcp_lp.ko
tcp_probe.ko
tcp_scalable.ko
tcp_vegas.ko
tcp_veno.ko
tcp_westwood.ko
tcp_yeah.ko
tunnel4.ko
xfrm4_mode_beet.ko
xfrm4_mode_transport.ko
xfrm4_mode_tunnel.ko
xfrm4_tunnel.ko

/lib/modules/2.6.38-8-generic/kernel/net/ipv4/netfilter:
arptable_filter.ko
arp_tables.ko
arpt_mangle.ko
ip_queue.ko
iptable_filter.ko
iptable_mangle.ko
iptable_nat.ko
iptable_raw.ko
iptable_security.ko
ip_tables.ko
ipt_addrtype.ko
ipt_ah.ko
ipt_CLUSTERIP.ko
ipt_ecn.ko
ipt_ECN.ko
ipt_LOG.ko
ipt_MASQUERADE.ko
ipt_NETMAP.ko
ipt_REDIRECT.ko
ipt_REJECT.ko
ipt_ULOG.ko
nf_conntrack_ipv4.ko
nf_defrag_ipv4.ko
nf_nat_amanda.ko
nf_nat_ftp.ko
nf_nat_h323.ko
nf_nat_irc.ko
nf_nat.ko
nf_nat_pptp.ko
nf_nat_proto_dccp.ko
nf_nat_proto_gre.ko
nf_nat_proto_sctp.ko
nf_nat_proto_udplite.ko
nf_nat_sip.ko
nf_nat_snmp_basic.ko
nf_nat_tftp.ko

/lib/modules/2.6.38-8-generic/kernel/net/ipv6:
ah6.ko
esp6.ko
ip6_tunnel.ko
ipcomp6.ko
netfilter
sit.ko
tunnel6.ko
xfrm6_mode_beet.ko
xfrm6_mode_ro.ko
xfrm6_mode_transport.ko
xfrm6_mode_tunnel.ko
xfrm6_tunnel.ko

/lib/modules/2.6.38-8-generic/kernel/net/ipv6/netfilter:
ip6_queue.ko
ip6table_filter.ko
ip6table_mangle.ko
ip6table_raw.ko
ip6table_security.ko
ip6_tables.ko
ip6t_ah.ko
ip6t_eui64.ko
ip6t_frag.ko
ip6t_hbh.ko
ip6t_ipv6header.ko
ip6t_LOG.ko
ip6t_mh.ko
ip6t_REJECT.ko
ip6t_rt.ko
nf_conntrack_ipv6.ko
nf_defrag_ipv6.ko

/lib/modules/2.6.38-8-generic/kernel/net/ipx:
ipx.ko

/lib/modules/2.6.38-8-generic/kernel/net/irda:
ircomm
irda.ko
irlan
irnet

/lib/modules/2.6.38-8-generic/kernel/net/irda/ircomm:
ircomm.ko
ircomm-tty.ko

/lib/modules/2.6.38-8-generic/kernel/net/irda/irlan:
irlan.ko

/lib/modules/2.6.38-8-generic/kernel/net/irda/irnet:
irnet.ko

/lib/modules/2.6.38-8-generic/kernel/net/key:
af_key.ko

/lib/modules/2.6.38-8-generic/kernel/net/l2tp:
l2tp_core.ko
l2tp_debugfs.ko
l2tp_ppp.ko

/lib/modules/2.6.38-8-generic/kernel/net/lapb:
lapb.ko

/lib/modules/2.6.38-8-generic/kernel/net/llc:
llc2.ko

/lib/modules/2.6.38-8-generic/kernel/net/mac80211:
mac80211.ko

/lib/modules/2.6.38-8-generic/kernel/net/netfilter:
ipvs
nf_conntrack_amanda.ko
nf_conntrack_ftp.ko
nf_conntrack_h323.ko
nf_conntrack_irc.ko
nf_conntrack.ko
nf_conntrack_netbios_ns.ko
nf_conntrack_netlink.ko
nf_conntrack_pptp.ko
nf_conntrack_proto_dccp.ko
nf_conntrack_proto_gre.ko
nf_conntrack_proto_sctp.ko
nf_conntrack_proto_udplite.ko
nf_conntrack_sane.ko
nf_conntrack_sip.ko
nf_conntrack_tftp.ko
nfnetlink.ko
nfnetlink_log.ko
nfnetlink_queue.ko
nf_tproxy_core.ko
x_tables.ko
xt_CHECKSUM.ko
xt_CLASSIFY.ko
xt_cluster.ko
xt_comment.ko
xt_connbytes.ko
xt_connlimit.ko
xt_connmark.ko
xt_CONNSECMARK.ko
xt_conntrack.ko
xt_cpu.ko
xt_CT.ko
xt_dccp.ko
xt_dscp.ko
xt_DSCP.ko
xt_esp.ko
xt_hashlimit.ko
xt_helper.ko
xt_hl.ko
xt_HL.ko
xt_IDLETIMER.ko
xt_iprange.ko
xt_ipvs.ko
xt_LED.ko
xt_length.ko
xt_limit.ko
xt_mac.ko
xt_mark.ko
xt_multiport.ko
xt_NFLOG.ko
xt_NFQUEUE.ko
xt_NOTRACK.ko
xt_osf.ko
xt_owner.ko
xt_physdev.ko
xt_pkttype.ko
xt_policy.ko
xt_quota.ko
xt_rateest.ko
xt_RATEEST.ko
xt_realm.ko
xt_recent.ko
xt_sctp.ko
xt_SECMARK.ko
xt_socket.ko
xt_state.ko
xt_statistic.ko
xt_string.ko
xt_tcpmss.ko
xt_TCPMSS.ko
xt_tcpudp.ko
xt_TEE.ko
xt_time.ko
xt_TPROXY.ko
xt_TRACE.ko
xt_u32.ko

/lib/modules/2.6.38-8-generic/kernel/net/netfilter/ipvs:
ip_vs_dh.ko
ip_vs_ftp.ko
ip_vs.ko
ip_vs_lblc.ko
ip_vs_lblcr.ko
ip_vs_lc.ko
ip_vs_nq.ko
ip_vs_pe_sip.ko
ip_vs_rr.ko
ip_vs_sed.ko
ip_vs_sh.ko
ip_vs_wlc.ko
ip_vs_wrr.ko

/lib/modules/2.6.38-8-generic/kernel/net/netrom:
netrom.ko

/lib/modules/2.6.38-8-generic/kernel/net/phonet:
phonet.ko
pn_pep.ko

/lib/modules/2.6.38-8-generic/kernel/net/rds:
rds.ko
rds_rdma.ko
rds_tcp.ko

/lib/modules/2.6.38-8-generic/kernel/net/rose:
rose.ko

/lib/modules/2.6.38-8-generic/kernel/net/rxrpc:
af-rxrpc.ko
rxkad.ko

/lib/modules/2.6.38-8-generic/kernel/net/sched:
act_csum.ko
act_gact.ko
act_ipt.ko
act_mirred.ko
act_nat.ko
act_pedit.ko
act_police.ko
act_simple.ko
act_skbedit.ko
cls_basic.ko
cls_flow.ko
cls_fw.ko
cls_route.ko
cls_rsvp6.ko
cls_rsvp.ko
cls_tcindex.ko
cls_u32.ko
em_cmp.ko
em_meta.ko
em_nbyte.ko
em_text.ko
em_u32.ko
sch_atm.ko
sch_cbq.ko
sch_drr.ko
sch_dsmark.ko
sch_gred.ko
sch_hfsc.ko
sch_htb.ko
sch_ingress.ko
sch_multiq.ko
sch_netem.ko
sch_prio.ko
sch_red.ko
sch_sfq.ko
sch_tbf.ko
sch_teql.ko

/lib/modules/2.6.38-8-generic/kernel/net/sctp:
sctp.ko
sctp_probe.ko

/lib/modules/2.6.38-8-generic/kernel/net/sunrpc:
auth_gss
sunrpc.ko
xprtrdma

/lib/modules/2.6.38-8-generic/kernel/net/sunrpc/auth_gss:
auth_rpcgss.ko
rpcsec_gss_krb5.ko

/lib/modules/2.6.38-8-generic/kernel/net/sunrpc/xprtrdma:
svcrdma.ko
xprtrdma.ko

/lib/modules/2.6.38-8-generic/kernel/net/tipc:
tipc.ko

/lib/modules/2.6.38-8-generic/kernel/net/wanrouter:
wanrouter.ko

/lib/modules/2.6.38-8-generic/kernel/net/wimax:
wimax.ko

/lib/modules/2.6.38-8-generic/kernel/net/wireless:
cfg80211.ko
lib80211_crypt_ccmp.ko
lib80211_crypt_tkip.ko
lib80211_crypt_wep.ko
lib80211.ko

/lib/modules/2.6.38-8-generic/kernel/net/x25:
x25.ko

/lib/modules/2.6.38-8-generic/kernel/net/xfrm:
xfrm_ipcomp.ko
xfrm_user.ko

/lib/modules/2.6.38-8-generic/kernel/security:
keys

/lib/modules/2.6.38-8-generic/kernel/security/keys:
encrypted.ko
trusted.ko

/lib/modules/2.6.38-8-generic/kernel/sound:
ac97_bus.ko
core
drivers
i2c
isa
pci
pcmcia
soc
soundcore.ko
synth
usb

/lib/modules/2.6.38-8-generic/kernel/sound/core:
seq
snd-hrtimer.ko
snd-hwdep.ko
snd.ko
snd-page-alloc.ko
snd-pcm.ko
snd-rawmidi.ko
snd-timer.ko

/lib/modules/2.6.38-8-generic/kernel/sound/core/seq:
snd-seq-device.ko
snd-seq-dummy.ko
snd-seq.ko
snd-seq-midi-emul.ko
snd-seq-midi-event.ko
snd-seq-midi.ko
snd-seq-virmidi.ko

/lib/modules/2.6.38-8-generic/kernel/sound/drivers:
mpu401
opl3
pcsp
snd-aloop.ko
snd-dummy.ko
snd-mtpav.ko
snd-mts64.ko
snd-portman2x4.ko
snd-serial-u16550.ko
snd-virmidi.ko
vx

/lib/modules/2.6.38-8-generic/kernel/sound/drivers/mpu401:
snd-mpu401.ko
snd-mpu401-uart.ko

/lib/modules/2.6.38-8-generic/kernel/sound/drivers/opl3:
snd-opl3-lib.ko
snd-opl3-synth.ko

/lib/modules/2.6.38-8-generic/kernel/sound/drivers/pcsp:
snd-pcsp.ko

/lib/modules/2.6.38-8-generic/kernel/sound/drivers/vx:
snd-vx-lib.ko

/lib/modules/2.6.38-8-generic/kernel/sound/i2c:
other
snd-cs8427.ko
snd-i2c.ko

/lib/modules/2.6.38-8-generic/kernel/sound/i2c/other:
snd-ak4113.ko
snd-ak4114.ko
snd-ak4117.ko
snd-ak4xxx-adda.ko
snd-pt2258.ko
snd-tea575x-tuner.ko

/lib/modules/2.6.38-8-generic/kernel/sound/isa:
sb

/lib/modules/2.6.38-8-generic/kernel/sound/isa/sb:
snd-sb16-dsp.ko
snd-sb-common.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci:
ac97
ali5451
asihpi
au88x0
aw2
ca0106
cs46xx
cs5535audio
ctxfi
echoaudio
emu10k1
hda
ice1712
korg1212
lx6464es
mixart
nm256
oxygen
pcxhr
riptide
rme9652
snd-ad1889.ko
snd-als300.ko
snd-als4000.ko
snd-atiixp.ko
snd-atiixp-modem.ko
snd-azt3328.ko
snd-bt87x.ko
snd-cmipci.ko
snd-cs4281.ko
snd-cs5530.ko
snd-ens1370.ko
snd-ens1371.ko
snd-es1938.ko
snd-es1968.ko
snd-fm801.ko
snd-intel8x0.ko
snd-intel8x0m.ko
snd-maestro3.ko
snd-rme32.ko
snd-rme96.ko
snd-sonicvibes.ko
snd-via82xx.ko
snd-via82xx-modem.ko
trident
vx222
ymfpci

/lib/modules/2.6.38-8-generic/kernel/sound/pci/ac97:
snd-ac97-codec.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/ali5451:
snd-ali5451.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/asihpi:
snd-asihpi.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/au88x0:
snd-au8810.ko
snd-au8820.ko
snd-au8830.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/aw2:
snd-aw2.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/ca0106:
snd-ca0106.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/cs46xx:
snd-cs46xx.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/cs5535audio:
snd-cs5535audio.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/ctxfi:
snd-ctxfi.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/echoaudio:
snd-darla20.ko
snd-darla24.ko
snd-echo3g.ko
snd-gina20.ko
snd-gina24.ko
snd-indigodj.ko
snd-indigodjx.ko
snd-indigoio.ko
snd-indigoiox.ko
snd-indigo.ko
snd-layla20.ko
snd-layla24.ko
snd-mia.ko
snd-mona.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/emu10k1:
snd-emu10k1.ko
snd-emu10k1-synth.ko
snd-emu10k1x.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda:
snd-hda-codec-analog.ko
snd-hda-codec-ca0110.ko
snd-hda-codec-cirrus.ko
snd-hda-codec-cmedia.ko
snd-hda-codec-conexant.ko
snd-hda-codec-hdmi.ko
snd-hda-codec-idt.ko
snd-hda-codec.ko
snd-hda-codec-realtek.ko
snd-hda-codec-si3054.ko
snd-hda-codec-via.ko
snd-hda-intel.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/ice1712:
snd-ice1712.ko
snd-ice1724.ko
snd-ice17xx-ak4xxx.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/korg1212:
snd-korg1212.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/lx6464es:
snd-lx6464es.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/mixart:
snd-mixart.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/nm256:
snd-nm256.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/oxygen:
snd-oxygen.ko
snd-oxygen-lib.ko
snd-virtuoso.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/pcxhr:
snd-pcxhr.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/riptide:
snd-riptide.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/rme9652:
snd-hdsp.ko
snd-hdspm.ko
snd-rme9652.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/trident:
snd-trident.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/vx222:
snd-vx222.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pci/ymfpci:
snd-ymfpci.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pcmcia:
pdaudiocf
vx

/lib/modules/2.6.38-8-generic/kernel/sound/pcmcia/pdaudiocf:
snd-pdaudiocf.ko

/lib/modules/2.6.38-8-generic/kernel/sound/pcmcia/vx:
snd-vxpocket.ko

/lib/modules/2.6.38-8-generic/kernel/sound/soc:
codecs
snd-soc-core.ko

/lib/modules/2.6.38-8-generic/kernel/sound/soc/codecs:
snd-soc-88pm860x.ko
snd-soc-ad1836.ko
snd-soc-ad193x.ko
snd-soc-ad73311.ko
snd-soc-ads117x.ko
snd-soc-ak4104.ko
snd-soc-ak4535.ko
snd-soc-ak4642.ko
snd-soc-ak4671.ko
snd-soc-alc5623.ko
snd-soc-cs4270.ko
snd-soc-cs42l51.ko
snd-soc-cx20442.ko
snd-soc-da7210.ko
snd-soc-l3.ko
snd-soc-max98088.ko
snd-soc-max9877.ko
snd-soc-pcm3008.ko
snd-soc-spdif.ko
snd-soc-ssm2602.ko
snd-soc-tlv320aic23.ko
snd-soc-tlv320aic26.ko
snd-soc-tlv320aic3x.ko
snd-soc-tlv320dac33.ko
snd-soc-tpa6130a2.ko
snd-soc-uda134x.ko
snd-soc-uda1380.ko
snd-soc-wl1273.ko
snd-soc-wm2000.ko
snd-soc-wm8350.ko
snd-soc-wm8400.ko
snd-soc-wm8510.ko
snd-soc-wm8523.ko
snd-soc-wm8580.ko
snd-soc-wm8711.ko
snd-soc-wm8727.ko
snd-soc-wm8728.ko
snd-soc-wm8731.ko
snd-soc-wm8737.ko
snd-soc-wm8741.ko
snd-soc-wm8750.ko
snd-soc-wm8753.ko
snd-soc-wm8770.ko
snd-soc-wm8776.ko
snd-soc-wm8804.ko
snd-soc-wm8900.ko
snd-soc-wm8903.ko
snd-soc-wm8904.ko
snd-soc-wm8940.ko
snd-soc-wm8955.ko
snd-soc-wm8960.ko
snd-soc-wm8961.ko
snd-soc-wm8962.ko
snd-soc-wm8971.ko
snd-soc-wm8974.ko
snd-soc-wm8978.ko
snd-soc-wm8985.ko
snd-soc-wm8988.ko
snd-soc-wm8990.ko
snd-soc-wm8993.ko
snd-soc-wm8994.ko
snd-soc-wm8995.ko
snd-soc-wm9081.ko
snd-soc-wm9090.ko
snd-soc-wm-hubs.ko

/lib/modules/2.6.38-8-generic/kernel/sound/synth:
emux
snd-util-mem.ko

/lib/modules/2.6.38-8-generic/kernel/sound/synth/emux:
snd-emux-synth.ko

/lib/modules/2.6.38-8-generic/kernel/sound/usb:
caiaq
misc
snd-usb-audio.ko
snd-usbmidi-lib.ko
usx2y

/lib/modules/2.6.38-8-generic/kernel/sound/usb/caiaq:
snd-usb-caiaq.ko

/lib/modules/2.6.38-8-generic/kernel/sound/usb/misc:
snd-ua101.ko

/lib/modules/2.6.38-8-generic/kernel/sound/usb/usx2y:
snd-usb-us122l.ko
snd-usb-usx2y.ko

/lib/modules/2.6.38-8-generic/kernel/ubuntu:
aufs
compcache
dm-raid4-5
fsam7400
iscsitarget
ndiswrapper
omnibook
rfkill
rtl8192se

/lib/modules/2.6.38-8-generic/kernel/ubuntu/aufs:
aufs.ko

/lib/modules/2.6.38-8-generic/kernel/ubuntu/compcache:
ramzswap.ko
xvmalloc.ko

/lib/modules/2.6.38-8-generic/kernel/ubuntu/dm-raid4-5:
dm-raid45.ko

/lib/modules/2.6.38-8-generic/kernel/ubuntu/fsam7400:
fsam7400.ko

/lib/modules/2.6.38-8-generic/kernel/ubuntu/iscsitarget:
iscsi_trgt.ko

/lib/modules/2.6.38-8-generic/kernel/ubuntu/ndiswrapper:
ndiswrapper.ko

/lib/modules/2.6.38-8-generic/kernel/ubuntu/omnibook:
omnibook.ko

/lib/modules/2.6.38-8-generic/kernel/ubuntu/rfkill:
av5100.ko
pbe5.ko

/lib/modules/2.6.38-8-generic/kernel/ubuntu/rtl8192se:
r8192se_pci.ko
```
```
Output from xawtv

evilsupahfly@ubuntu:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.38-8-generic)
looking for available devices
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture  

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture  

/dev/video2: No such device or address
/dev/video3: No such device or address

```

---

### Post by BicyclerBoy on 2011-07-23
Recent kernel changes have broken a lot of analogue tuner drivers.

[http://www.kernellabs.com/blog/?cat=66](http://www.kernellabs.com/blog/?cat=66)

I thought analogue TV was almost completely switched off in Canada ?

You may be better of to use ubuntu 10.04 or mythbuntu 10.04 & so avoid the kernel issue until someone (hopefully) rebuilds the tuner driver..

I notice you are using the nouveau driver for the GT430.
It will work much better for HTPC if you use the proprietary driver.

---

### Post by EvilSupahFly on 2011-07-23
> **BicyclerBoy said:**
> Recent kernel changes have broken a lot of analogue tuner drivers.

[http://www.kernellabs.com/blog/?cat=66](http://www.kernellabs.com/blog/?cat=66)

I thought analogue TV was almost completely switched off in Canada ?

You may be better of to use ubuntu 10.04 or mythbuntu 10.04 & so avoid the kernel issue until someone (hopefully) rebuilds the tuner driver..

I notice you are using the nouveau driver for the GT430.
It will work much better for HTPC if you use the proprietary driver.

I actually am using the one from nVidia now. I updated the driver after I collected the details I posted above. Analogue gets sweitched off this summer, but evidently only if you have rabbit ears. I just put WINE on here, so out of morbid curiosity, I'll try the Windows tuner, see what happens. After all, it took some effort and a lot of tweaking, but I managed to get Win32 Quake II to run under WINE on Redhat 3 on a late 486. Of course, that was back in college. Long time ago. :lol:

---

### Post by BicyclerBoy on 2011-07-23
I think you are confusing analogue OTA & cable.
Rabbit ears are not recommended for tv tuner cards.
The basic radio performance of TV tuner cards do not compare to an old portable TV.
 They may do in the future.

Wine is never going to work with tuner card.
The tuner works in windows via a windows kernel mode driver.

The nvidia install method has nothing to recommend it unless you must have the absolute latest...
The install will break with every kernel update.

---

### Post by EvilSupahFly on 2011-08-03
I have basic cable, over the wire (OTW). OTA becomes obsolete this summer in Canada, but as far as I understand, my OTW service should be OK. And yes, I am aware of the differences between OTA-Analog and OTW-Analog. The local cable co left a flyer in the mailbox a few weeks back that said Bunny Ears will become Dinosaur Ears but didn't say anything about OTW service.

At any rate, I can't get the tuner card working under WINE either with the native Windows drivers, and for some reason my sound has crapped out, but that's an issue for the ALSA boards.

---

### Post by new_tolinux on 2011-08-03
I read someone suggesting tvtime, but I didn't read anything back about that from you...
Only I found out that after installing, tvtime makes the ~/.tvtime folder owned by root (which can give you a few strange errors), which you have to correct yourself:
```
sudo chown -R yourusername:yourusername ~/.tvtime
```

---

