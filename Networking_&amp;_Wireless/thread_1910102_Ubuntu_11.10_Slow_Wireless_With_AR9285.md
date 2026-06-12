---
title: "Ubuntu 11.10 Slow Wireless With AR9285"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by kev22257 on 2012-01-16
Hi,

I'm having a problem with getting my wireless working correctly on my machine.  I originally could not get it connect, but after some research found a fix that corrected that issue.

```

echo "options ath9k nohwcrypt=1" >> /etc/modprobe.d/ath9k.conf

```

Now, however, my connection is very slow.  It takes up to 5-10 seconds to load even the simplest of pages.  I see a lot of dropped packets.  On top of this I see that the card refuses to connect at 802.11n speeds even though it and my access point support it.  I'm at a loss as to what the problem is; I see lots of other posts online similar to this, but none with any sort of resolution.

1) Machine Brand and Model (PC/Laptop):

[http://www.zotacusa.com/zotac-ion-itx-a-series-ionitx-a-u.html]("http://www.zotacusa.com/zotac-ion-itx-a-series-ionitx-a-u.html")

2) Wireless Chipset:

```

$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

3) Interface:

```

$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:10.0.1.12  Bcast:10.0.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12503113 (12.5 MB)  TX bytes:984380 (984.3 KB)

$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:xx:xx  
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:68  Invalid misc:4773   Missed beacon:0

```

4) Modules:

```

$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
nvidia              11713772  40 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  1 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 121408  0 
psmouse                73882  0 
mac80211              471589  1 ath9k
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 47198  0 
hid                    95463  1 usbhid
ath9k_common           13839  1 ath9k
ath9k_hw              334961  2 ath9k,ath9k_common
ath                    23780  2 ath9k,ath9k_hw
cfg80211              202604  3 ath9k,mac80211,ath
snd                    68266  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
shpchp                 37345  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
binfmt_misc            17540  1 
i2c_nforce2            13058  0 
wmi                    19256  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
forcedeth              67563  0 

```

5) Messages:

```

$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=20e4bbe0-bb21-4a39-bd2f-586785fe4ea0 ro vga=792 splash quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./To be filled by O.E.M., BIOS 080015  08/13/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0xcffa0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0E0000000 mask 0E0000000 uncachable
[    0.000000]   1 base 000000000 mask 000000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 1, base: 0GB, range: 4GB, type WB
[    0.000000] total RAM covered: 3584M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 1G 	num_reg: 2  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000cffa0000
[    0.000000]  0000000000 - 00cffa0000 page 4k
[    0.000000] kernel direct mapping tables up to cffa0000 @ 1f97b000-20000000
[    0.000000] RAMDISK: 365aa000 - 372cd000
[    0.000000] ACPI: RSDP 00000000000faab0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cffa0000 00040 (v01 081309 RSDT0925 20090813 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cffa0200 00084 (v01 081309 FACP0925 20090813 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cffa04a0 070E9 (v01   NVDA NVDAACPI 00001000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cffae000 00040
[    0.000000] ACPI: APIC 00000000cffa0390 00080 (v01 081309 APIC0925 20090813 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cffa0410 0003C (v01 081309 OEMMCFG  20090813 MSFT 00000097)
[    0.000000] ACPI: WDRT 00000000cffa0450 00047 (v01 081309 NV-WDRT  20090813 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffae040 00079 (v01 081309 OEMB0925 20090813 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cffaa4a0 00038 (v01 081309 OEMHPET0 20090813 MSFT 00000097)
[    0.000000] ACPI: NVHD 00000000cffae0c0 00284 (v01 081309  NVHDCP  20090813 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000cffa0000
[    0.000000] Initmem setup node 0 0000000000000000-00000000cffa0000
[    0.000000]   NODE_DATA [00000000cff9b000 - 00000000cff9ffff]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cffa0
[    0.000000] On node 0 totalpages: 851759
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11591 pages used for memmap
[    0.000000]   DMA32 zone: 836185 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff8800cff12000 s79616 r8192 d22784 u110592
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u110592 alloc=27*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 840107
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=20e4bbe0-bb21-4a39-bd2f-586785fe4ea0 ro vga=792 splash quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3326244k/3407488k available (6109k kernel code, 452k absent, 80792k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 27262976 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1600.062 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.12 BogoMIPS (lpj=6400248)
[    0.004022] pid_max: default: 32768 minimum: 301
[    0.004097] Security Framework initialized
[    0.004141] AppArmor: AppArmor initialized
[    0.004145] Yama: becoming mindful.
[    0.005189] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011432] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.013150] Mount-cache hash table entries: 256
[    0.013513] Initializing cgroup subsys cpuacct
[    0.013531] Initializing cgroup subsys memory
[    0.013553] Initializing cgroup subsys devices
[    0.013559] Initializing cgroup subsys freezer
[    0.013565] Initializing cgroup subsys net_cls
[    0.013571] Initializing cgroup subsys blkio
[    0.013592] Initializing cgroup subsys perf_event
[    0.013657] Atom PSE erratum detected, BIOS microcode update recommended
[    0.013665] Disabled fast string operations
[    0.013675] CPU: Physical Processor ID: 0
[    0.013679] CPU: Processor Core ID: 0
[    0.013685] mce: CPU supports 5 MCE banks
[    0.013701] CPU0: Thermal monitoring enabled (TM1)
[    0.013711] using mwait in idle threads.
[    0.016605] ACPI: Core revision 20110413
[    0.028036] ftrace: allocating 25647 entries in 101 pages
[    0.036221] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075921] CPU0: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
[    0.076004] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.076004] ... version:                3
[    0.076004] ... bit width:              40
[    0.076004] ... generic registers:      2
[    0.076004] ... value mask:             000000ffffffffff
[    0.076004] ... max period:             000000007fffffff
[    0.076004] ... fixed-purpose events:   3
[    0.076004] ... event mask:             0000000700000003
[    0.076004] Booting Node   0, Processors  #1
[    0.076004] smpboot cpu 1: start_ip = 9a000
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.008000] Disabled fast string operations
[    0.168258]  #2
[    0.168265] smpboot cpu 2: start_ip = 9a000
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.008000] Disabled fast string operations
[    0.260298]  #3 Ok.
[    0.260304] smpboot cpu 3: start_ip = 9a000
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.008000] Disabled fast string operations
[    0.352046] Brought up 4 CPUs
[    0.352055] Total of 4 processors activated (12800.29 BogoMIPS).
[    0.354472] devtmpfs: initialized
[    0.354472] PM: Registering ACPI NVS region at cffae000 (270336 bytes)
[    0.360248] print_constraints: dummy: 
[    0.360322] Time: 18:38:10  Date: 01/16/12
[    0.360425] NET: Registered protocol family 16
[    0.360453] Trying to unpack rootfs image as initramfs...
[    0.360861] ACPI: bus type pci registered
[    0.361065] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.361075] PCI: not using MMCONFIG
[    0.361082] PCI: Using configuration type 1 for base access
[    0.364114] bio: create slab <bio-0> at 0
[    0.371201] ACPI: EC: Look up EC in DSDT
[    0.377896] ACPI: Executed 1 blocks of module-level executable AML code
[    0.388298] ACPI: Interpreter enabled
[    0.388313] ACPI: (supports S0 S1 S3 S4 S5)
[    0.388390] ACPI: Using IOAPIC for interrupt routing
[    0.388493] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.393160] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
[    0.431455] ACPI: No dock devices found.
[    0.431466] HEST: Table not found.
[    0.431478] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.432494] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.433399] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.433412] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.433423] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.433433] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.433444] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xfbffffff]
[    0.433453] pci_root PNP0A03:00: host bridge window [mem 0xfe000000-0xfebfffff]
[    0.433501] pci 0000:00:00.0: [10de:0a82] type 0 class 0x000600
[    0.433635] pci 0000:00:00.1: [10de:0a88] type 0 class 0x000500
[    0.433822] pci 0000:00:03.0: [10de:0aad] type 0 class 0x000601
[    0.433843] pci 0000:00:03.0: reg 10: [io  0x4f00-0x4fff]
[    0.433928] pci 0000:00:03.1: [10de:0aa4] type 0 class 0x000500
[    0.434061] pci 0000:00:03.2: [10de:0aa2] type 0 class 0x000c05
[    0.434089] pci 0000:00:03.2: reg 10: [io  0x4900-0x493f]
[    0.434129] pci 0000:00:03.2: reg 20: [io  0x4d00-0x4d3f]
[    0.434145] pci 0000:00:03.2: reg 24: [io  0x4e00-0x4e3f]
[    0.434191] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.434206] pci 0000:00:03.2: PME# disabled
[    0.434240] pci 0000:00:03.3: [10de:0a89] type 0 class 0x000500
[    0.434441] pci 0000:00:03.5: [10de:0aa3] type 0 class 0x000b40
[    0.434472] pci 0000:00:03.5: reg 10: [mem 0xfae80000-0xfaefffff]
[    0.434631] pci 0000:00:04.0: [10de:0aa5] type 0 class 0x000c03
[    0.434656] pci 0000:00:04.0: reg 10: [mem 0xfae7f000-0xfae7ffff]
[    0.434729] pci 0000:00:04.0: supports D1 D2
[    0.434737] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.434748] pci 0000:00:04.0: PME# disabled
[    0.434778] pci 0000:00:04.1: [10de:0aa6] type 0 class 0x000c03
[    0.434806] pci 0000:00:04.1: reg 10: [mem 0xfae7ec00-0xfae7ecff]
[    0.434895] pci 0000:00:04.1: supports D1 D2
[    0.434904] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.434914] pci 0000:00:04.1: PME# disabled
[    0.434959] pci 0000:00:06.0: [10de:0aa7] type 0 class 0x000c03
[    0.434984] pci 0000:00:06.0: reg 10: [mem 0xfae7d000-0xfae7dfff]
[    0.435058] pci 0000:00:06.0: supports D1 D2
[    0.435066] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.435076] pci 0000:00:06.0: PME# disabled
[    0.435108] pci 0000:00:06.1: [10de:0aa9] type 0 class 0x000c03
[    0.435135] pci 0000:00:06.1: reg 10: [mem 0xfae7e800-0xfae7e8ff]
[    0.435216] pci 0000:00:06.1: supports D1 D2
[    0.435224] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.435235] pci 0000:00:06.1: PME# disabled
[    0.435279] pci 0000:00:08.0: [10de:0ac0] type 0 class 0x000403
[    0.435303] pci 0000:00:08.0: reg 10: [mem 0xfae78000-0xfae7bfff]
[    0.435378] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.435388] pci 0000:00:08.0: PME# disabled
[    0.435416] pci 0000:00:09.0: [10de:0aab] type 1 class 0x000604
[    0.435495] pci 0000:00:0a.0: [10de:0ab0] type 0 class 0x000200
[    0.435519] pci 0000:00:0a.0: reg 10: [mem 0xfae7c000-0xfae7cfff]
[    0.435535] pci 0000:00:0a.0: reg 14: [io  0xd080-0xd087]
[    0.435551] pci 0000:00:0a.0: reg 18: [mem 0xfae7e400-0xfae7e4ff]
[    0.435567] pci 0000:00:0a.0: reg 1c: [mem 0xfae7e000-0xfae7e00f]
[    0.435617] pci 0000:00:0a.0: supports D1 D2
[    0.435626] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.435640] pci 0000:00:0a.0: PME# disabled
[    0.435685] pci 0000:00:0b.0: [10de:0ab4] type 0 class 0x000101
[    0.435713] pci 0000:00:0b.0: reg 10: [io  0xd000-0xd007]
[    0.435729] pci 0000:00:0b.0: reg 14: [io  0xcc00-0xcc03]
[    0.435744] pci 0000:00:0b.0: reg 18: [io  0xc880-0xc887]
[    0.435760] pci 0000:00:0b.0: reg 1c: [io  0xc800-0xc803]
[    0.435775] pci 0000:00:0b.0: reg 20: [io  0xc480-0xc48f]
[    0.435790] pci 0000:00:0b.0: reg 24: [mem 0xfae76000-0xfae77fff]
[    0.435894] pci 0000:00:0c.0: [10de:0ac4] type 1 class 0x000604
[    0.436136] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.436152] pci 0000:00:0c.0: PME# disabled
[    0.436223] pci 0000:00:10.0: [10de:0aa0] type 1 class 0x000604
[    0.436289] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.436299] pci 0000:00:10.0: PME# disabled
[    0.436383] pci 0000:00:15.0: [10de:0ac6] type 1 class 0x000604
[    0.436589] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.436605] pci 0000:00:15.0: PME# disabled
[    0.436704] pci 0000:00:16.0: [10de:0ac7] type 1 class 0x000604
[    0.436906] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.436921] pci 0000:00:16.0: PME# disabled
[    0.437019] pci 0000:00:17.0: [10de:0ac7] type 1 class 0x000604
[    0.437241] pci 0000:00:17.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437257] pci 0000:00:17.0: PME# disabled
[    0.437358] pci 0000:00:18.0: [10de:0ac7] type 1 class 0x000604
[    0.437560] pci 0000:00:18.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437575] pci 0000:00:18.0: PME# disabled
[    0.437720] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.437732] pci 0000:00:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.437744] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.437756] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.437767] pci 0000:00:09.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.437776] pci 0000:00:09.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.437786] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.437796] pci 0000:00:09.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.437806] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xfbffffff] (subtractive decode)
[    0.437817] pci 0000:00:09.0:   bridge window [mem 0xfe000000-0xfebfffff] (subtractive decode)
[    0.437993] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.438016] pci 0000:00:0c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.438032] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.438055] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.438123] pci 0000:03:00.0: [10de:087d] type 0 class 0x000300
[    0.438152] pci 0000:03:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.438175] pci 0000:03:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.438197] pci 0000:03:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.438215] pci 0000:03:00.0: reg 24: [io  0xec00-0xec7f]
[    0.438232] pci 0000:03:00.0: reg 30: [mem 0xfafe0000-0xfaffffff pref]
[    0.438317] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.438330] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.438341] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.438354] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.438571] pci 0000:04:00.0: [168c:002b] type 0 class 0x000280
[    0.438611] pci 0000:04:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.438714] pci 0000:04:00.0: supports D1
[    0.438722] pci 0000:04:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.438733] pci 0000:04:00.0: PME# disabled
[    0.444103] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.444129] pci 0000:00:15.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.444147] pci 0000:00:15.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.444170] pci 0000:00:15.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.444382] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.444408] pci 0000:00:16.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.444424] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.444446] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.444619] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.444641] pci 0000:00:17.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.444657] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.444680] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.444850] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.444872] pci 0000:00:18.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.444888] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.444911] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.445030] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.445570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBB0._PRT]
[    0.445755] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.445911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.446110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.446266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.446406] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.446547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.447125]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.447958]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0c
[    0.447967] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.482043] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.482516] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.482949] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.483398] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.483822] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *0, disabled.
[    0.484311] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.484747] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.485185] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.485616] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.486059] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.486505] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.486937] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.487404] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
[    0.487840] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.488309] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.488763] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.489213] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *11
[    0.489644] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.490084] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.490528] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.490964] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    0.491456] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.491917] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.492409] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.492869] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.493311] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.493780] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.494226] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.494668] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.495101] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.495538] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.495970] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.496484] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *15
[    0.496939] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.497395] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.497841] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *15
[    0.498277] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.498744] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.499202] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *9
[    0.499640] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.500224] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.500678] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.501121] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *9
[    0.501583] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *10
[    0.502056] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.
[    0.502507] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.
[    0.502973] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *11
[    0.503461] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *9
[    0.503922] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *15
[    0.504440] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *14
[    0.504839] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.504851] vgaarb: loaded
[    0.504856] vgaarb: bridge control possible 0000:03:00.0
[    0.505544] SCSI subsystem initialized
[    0.505759] libata version 3.00 loaded.
[    0.505932] usbcore: registered new interface driver usbfs
[    0.505980] usbcore: registered new interface driver hub
[    0.506079] usbcore: registered new device driver usb
[    0.506079] PCI: Using ACPI for IRQ routing
[    0.506079] PCI: pci_cache_line_size set to 64 bytes
[    0.506079] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.506079] reserve RAM buffer: 00000000cffa0000 - 00000000cfffffff 
[    0.508103] NetLabel: Initializing
[    0.508111] NetLabel:  domain hash size = 128
[    0.508116] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.508149] NetLabel:  unlabeled traffic allowed by default
[    0.508302] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.508316] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.508333] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.520142] Switching to clocksource hpet
[    0.523623] Switched to NOHz mode on CPU #0
[    0.523721] Switched to NOHz mode on CPU #3
[    0.523791] Switched to NOHz mode on CPU #1
[    0.523800] Switched to NOHz mode on CPU #2
[    0.542305] AppArmor: AppArmor Filesystem Enabled
[    0.542391] pnp: PnP ACPI init
[    0.542432] ACPI: bus type pnp registered
[    0.542821] pnp 00:00: [bus 00-ff]
[    0.542829] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.542836] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.542842] pnp 00:00: [io  0x0d00-0xffff window]
[    0.542848] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.542854] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.542861] pnp 00:00: [mem 0xe0000000-0xfbffffff window]
[    0.542867] pnp 00:00: [mem 0xfe000000-0xfebfffff window]
[    0.543048] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.543251] pnp 00:01: [io  0x03f8-0x03ff]
[    0.543277] pnp 00:01: [irq 4]
[    0.543283] pnp 00:01: [dma 0 disabled]
[    0.543379] pnp 00:01: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.543417] pnp 00:02: [dma 4]
[    0.543423] pnp 00:02: [io  0x0000-0x000f]
[    0.543429] pnp 00:02: [io  0x0081-0x0083]
[    0.543434] pnp 00:02: [io  0x0087]
[    0.543439] pnp 00:02: [io  0x0089-0x008b]
[    0.543445] pnp 00:02: [io  0x008f]
[    0.543450] pnp 00:02: [io  0x00c0-0x00df]
[    0.543507] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.543534] pnp 00:03: [io  0x0061]
[    0.543590] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.543618] pnp 00:04: [io  0x00f0-0x00ff]
[    0.543632] pnp 00:04: [irq 13]
[    0.543697] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.545321] pnp 00:05: [mem 0x000d0000-0x000d3fff window]
[    0.545329] pnp 00:05: [mem 0x000d4000-0x000d7fff window]
[    0.545336] pnp 00:05: [mem 0x000de000-0x000dffff window]
[    0.545342] pnp 00:05: [io  0x0010-0x001f]
[    0.545347] pnp 00:05: [io  0x0022-0x003f]
[    0.545353] pnp 00:05: [io  0x0044-0x004d]
[    0.545358] pnp 00:05: [io  0x0050-0x005f]
[    0.545363] pnp 00:05: [io  0x0062-0x0063]
[    0.545369] pnp 00:05: [io  0x0065-0x006f]
[    0.545374] pnp 00:05: [io  0x0072-0x007f]
[    0.545379] pnp 00:05: [io  0x0080]
[    0.545390] pnp 00:05: [io  0x0084-0x0086]
[    0.545396] pnp 00:05: [io  0x0088]
[    0.545401] pnp 00:05: [io  0x008c-0x008e]
[    0.545406] pnp 00:05: [io  0x0090-0x009f]
[    0.545412] pnp 00:05: [io  0x00a2-0x00bf]
[    0.545417] pnp 00:05: [io  0x00e0-0x00ef]
[    0.545422] pnp 00:05: [io  0x04d0-0x04d1]
[    0.545428] pnp 00:05: [io  0x0800-0x080f]
[    0.545433] pnp 00:05: [io  0x4000-0x407f]
[    0.545439] pnp 00:05: [io  0x4080-0x40ff]
[    0.545444] pnp 00:05: [io  0x4400-0x447f]
[    0.545449] pnp 00:05: [io  0x4480-0x44ff]
[    0.545454] pnp 00:05: [io  0x4800-0x487f]
[    0.545460] pnp 00:05: [io  0x4880-0x48ff]
[    0.545466] pnp 00:05: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.545472] pnp 00:05: [mem 0xfefe2000-0xfefe3fff]
[    0.545478] pnp 00:05: [mem 0xfefe1000-0xfefe1fff]
[    0.545484] pnp 00:05: [mem 0xfee01000-0xfeefffff]
[    0.545667] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.545675] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.545683] system 00:05: [io  0x4000-0x407f] has been reserved
[    0.545689] system 00:05: [io  0x4080-0x40ff] has been reserved
[    0.545696] system 00:05: [io  0x4400-0x447f] has been reserved
[    0.545703] system 00:05: [io  0x4480-0x44ff] has been reserved
[    0.545710] system 00:05: [io  0x4800-0x487f] has been reserved
[    0.545717] system 00:05: [io  0x4880-0x48ff] has been reserved
[    0.545726] system 00:05: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.545734] system 00:05: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.545742] system 00:05: [mem 0x000de000-0x000dffff window] has been reserved
[    0.545750] system 00:05: [mem 0xfefe2000-0xfefe3fff] has been reserved
[    0.545757] system 00:05: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.545764] system 00:05: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.545774] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.546088] pnp 00:06: [mem 0xfed00000-0xfed00fff]
[    0.546096] pnp 00:06: [irq 2 disabled]
[    0.546115] pnp 00:06: [irq 8]
[    0.546181] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.546268] pnp 00:07: [io  0x0070-0x0071]
[    0.546332] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.546588] pnp 00:08: [io  0x0060]
[    0.546594] pnp 00:08: [io  0x0064]
[    0.546600] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    0.546606] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    0.546716] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.546725] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.546734] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.547157] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.547164] pnp 00:09: [io  0x0a00-0x0a0f]
[    0.547170] pnp 00:09: [io  0x0a10-0x0a1f]
[    0.547284] system 00:09: [io  0x0a00-0x0a0f] has been reserved
[    0.547292] system 00:09: [io  0x0a10-0x0a1f] has been reserved
[    0.547301] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.547458] pnp 00:0a: [mem 0xfc000000-0xfdffffff]
[    0.547570] system 00:0a: [mem 0xfc000000-0xfdffffff] has been reserved
[    0.547581] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.548150] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.548158] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    0.548164] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    0.548170] pnp 00:0b: [mem 0x00100000-0xdfffffff]
[    0.548176] pnp 00:0b: [mem 0xfec00000-0xffffffff]
[    0.548323] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.548331] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.548339] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.548347] system 00:0b: [mem 0x00100000-0xdfffffff] could not be reserved
[    0.548354] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.548364] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.550585] pnp: PnP ACPI: found 12 devices
[    0.550591] ACPI: ACPI bus type pnp unregistered
[    0.559681] PCI: max bus depth: 1 pci_try_num: 2
[    0.559825] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.559830] pci 0000:00:09.0:   bridge window [io  disabled]
[    0.559839] pci 0000:00:09.0:   bridge window [mem disabled]
[    0.559846] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    0.559857] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.559862] pci 0000:00:0c.0:   bridge window [io  disabled]
[    0.559876] pci 0000:00:0c.0:   bridge window [mem disabled]
[    0.559887] pci 0000:00:0c.0:   bridge window [mem pref disabled]
[    0.559907] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.559915] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.559924] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.559934] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.559944] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.559949] pci 0000:00:15.0:   bridge window [io  disabled]
[    0.559964] pci 0000:00:15.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.559977] pci 0000:00:15.0:   bridge window [mem pref disabled]
[    0.560024] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.560032] pci 0000:00:16.0:   bridge window [io  disabled]
[    0.560048] pci 0000:00:16.0:   bridge window [mem disabled]
[    0.560060] pci 0000:00:16.0:   bridge window [mem pref disabled]
[    0.560078] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.560083] pci 0000:00:17.0:   bridge window [io  disabled]
[    0.560097] pci 0000:00:17.0:   bridge window [mem disabled]
[    0.560108] pci 0000:00:17.0:   bridge window [mem pref disabled]
[    0.560126] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.560131] pci 0000:00:18.0:   bridge window [io  disabled]
[    0.560145] pci 0000:00:18.0:   bridge window [mem disabled]
[    0.560157] pci 0000:00:18.0:   bridge window [mem pref disabled]
[    0.560188] pci 0000:00:09.0: setting latency timer to 64
[    0.560763] ACPI: PCI Interrupt Link [LRP0] enabled at IRQ 23
[    0.560800] pci 0000:00:0c.0: PCI INT A -> Link[LRP0] -> GSI 23 (level, low) -> IRQ 23
[    0.560815] pci 0000:00:0c.0: setting latency timer to 64
[    0.560831] pci 0000:00:10.0: setting latency timer to 64
[    0.561318] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 22
[    0.561340] pci 0000:00:15.0: PCI INT A -> Link[LRP3] -> GSI 22 (level, low) -> IRQ 22
[    0.561354] pci 0000:00:15.0: setting latency timer to 64
[    0.561841] ACPI: PCI Interrupt Link [LRP4] enabled at IRQ 21
[    0.561863] pci 0000:00:16.0: PCI INT A -> Link[LRP4] -> GSI 21 (level, low) -> IRQ 21
[    0.561877] pci 0000:00:16.0: setting latency timer to 64
[    0.562364] ACPI: PCI Interrupt Link [LRP5] enabled at IRQ 20
[    0.562386] pci 0000:00:17.0: PCI INT A -> Link[LRP5] -> GSI 20 (level, low) -> IRQ 20
[    0.562400] pci 0000:00:17.0: setting latency timer to 64
[    0.562888] ACPI: PCI Interrupt Link [LRP6] enabled at IRQ 23
[    0.562898] pci 0000:00:18.0: PCI INT A -> Link[LRP6] -> GSI 23 (level, low) -> IRQ 23
[    0.562912] pci 0000:00:18.0: setting latency timer to 64
[    0.562924] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.562930] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.562937] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.562944] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.562950] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfbffffff]
[    0.562957] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.562964] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.562971] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.562977] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.562983] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.562990] pci_bus 0000:01: resource 8 [mem 0xe0000000-0xfbffffff]
[    0.562996] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.563003] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.563010] pci_bus 0000:03: resource 1 [mem 0xfaf00000-0xfbffffff]
[    0.563017] pci_bus 0000:03: resource 2 [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.563024] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.563141] NET: Registered protocol family 2
[    0.563487] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.566775] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.573764] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.574583] TCP: Hash tables configured (established 524288 bind 65536)
[    0.574590] TCP reno registered
[    0.574625] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.574702] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.575036] NET: Registered protocol family 1
[    0.756343] pci 0000:03:00.0: Boot video device
[    0.756357] PCI: CLS 64 bytes, default 64
[    0.757386] audit: initializing netlink socket (disabled)
[    0.757412] type=2000 audit(1326739090.752:1): initialized
[    0.814644] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.819453] VFS: Disk quotas dquot_6.5.2
[    0.819605] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.821496] fuse init (API version 7.16)
[    0.821772] msgmni has been set to 6496
[    0.823107] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.823218] io scheduler noop registered
[    0.823226] io scheduler deadline registered
[    0.823354] io scheduler cfq registered (default)
[    0.824400] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.824471] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.824591] intel_idle: MWAIT substates: 0x10
[    0.824615] intel_idle: v0.4 model 0x1C
[    0.824620] intel_idle: lapic_timer_reliable_states 0x2
[    0.824900] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.824914] ACPI: Power Button [PWRB]
[    0.825035] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.825044] ACPI: Power Button [PWRF]
[    0.825117] ACPI: acpi_idle yielding to intel_idle
[    0.835128] ERST: Table is not found!
[    0.835377] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.855749] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.084059] Freeing initrd memory: 13452k freed
[    1.169422] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.172847] Linux agpgart interface v0.103
[    1.175876] brd: module loaded
[    1.177350] loop: module loaded
[    1.178327] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[    1.178343] pata_acpi 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    1.178402] pata_acpi 0000:00:0b.0: setting latency timer to 64
[    1.178429] pata_acpi 0000:00:0b.0: PCI INT A disabled
[    1.179234] Fixed MDIO Bus: probed
[    1.179297] PPP generic driver version 2.4.2
[    1.179442] tun: Universal TUN/TAP device driver, 1.6
[    1.179448] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.179672] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.180276] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    1.180290] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    1.180326] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.180334] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.180453] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    1.180496] ehci_hcd 0000:00:04.1: debug port 1
[    1.180510] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.180562] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfae7ec00
[    1.192036] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.192380] hub 1-0:1.0: USB hub found
[    1.192394] hub 1-0:1.0: 6 ports detected
[    1.193075] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 20
[    1.193088] ehci_hcd 0000:00:06.1: PCI INT B -> Link[UB12] -> GSI 20 (level, low) -> IRQ 20
[    1.193122] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    1.193129] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    1.193261] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    1.193304] ehci_hcd 0000:00:06.1: debug port 1
[    1.193319] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
[    1.193359] ehci_hcd 0000:00:06.1: irq 20, io mem 0xfae7e800
[    1.204032] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    1.204347] hub 2-0:1.0: USB hub found
[    1.204366] hub 2-0:1.0: 6 ports detected
[    1.204545] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.205103] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    1.205115] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[    1.205151] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.205159] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.205298] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    1.205356] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfae7f000
[    1.262304] hub 3-0:1.0: USB hub found
[    1.262318] hub 3-0:1.0: 6 ports detected
[    1.262994] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 22
[    1.263006] ohci_hcd 0000:00:06.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
[    1.263041] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    1.263049] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    1.263177] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    1.263242] ohci_hcd 0000:00:06.0: irq 22, io mem 0xfae7d000
[    1.318339] hub 4-0:1.0: USB hub found
[    1.318354] hub 4-0:1.0: 6 ports detected
[    1.318513] uhci_hcd: USB Universal Host Controller Interface driver
[    1.318708] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.320265] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.320283] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.320605] mousedev: PS/2 mouse device common for all mice
[    1.320928] rtc_cmos 00:07: RTC can wake from S4
[    1.321187] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.321252] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.321564] device-mapper: uevent: version 1.0.3
[    1.321771] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.321925] cpuidle: using governor ladder
[    1.322154] cpuidle: using governor menu
[    1.322160] EFI Variables Facility v0.08 2004-May-17
[    1.322764] TCP cubic registered
[    1.323111] NET: Registered protocol family 10
[    1.324352] NET: Registered protocol family 17
[    1.324409] Registering the dns_resolver key type
[    1.324741] PM: Hibernation image not present or could not be loaded.
[    1.324783] registered taskstats version 1
[    1.343767]   Magic number: 12:660:645
[    1.343997] rtc_cmos 00:07: setting system clock to 2012-01-16 18:38:11 UTC (1326739091)
[    1.344101] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.344106] EDD information not available.
[    1.344595] Freeing unused kernel memory: 984k freed
[    1.345238] Write protecting the kernel read-only data: 10240k
[    1.345996] Freeing unused kernel memory: 16k freed
[    1.359155] Freeing unused kernel memory: 1396k freed
[    1.412092] udevd[87]: starting version 173
[    1.607745] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.608743] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    1.608765] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21
[    1.608783] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.674522] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:32:09:7f
[    1.674537] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    1.674629] ahci 0000:00:0b.0: version 3.0
[    1.674684] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    1.674829] ahci 0000:00:0b.0: irq 40 for MSI/MSI-X
[    1.674848] ahci 0000:00:0b.0: controller can't do PMP, turning off CAP_PMP
[    1.675003] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.675017] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pio slum part sxs 
[    1.675032] ahci 0000:00:0b.0: setting latency timer to 64
[    1.679252] scsi0 : ahci
[    1.679768] scsi1 : ahci
[    1.680242] scsi2 : ahci
[    1.680638] scsi3 : ahci
[    1.681003] scsi4 : ahci
[    1.681379] scsi5 : ahci
[    1.682021] ata1: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76100 irq 40
[    1.682034] ata2: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76180 irq 40
[    1.682044] ata3: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76200 irq 40
[    1.682054] ata4: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76280 irq 40
[    1.682063] ata5: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76300 irq 40
[    1.682072] ata6: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76380 irq 40
[    1.756039] Refined TSC clocksource calibration: 1599.992 MHz.
[    1.756054] Switching to clocksource tsc
[    1.808045] usb 3-3: new full speed USB device number 2 using ohci_hcd
[    2.000039] ata3: SATA link down (SStatus 0 SControl 300)
[    2.000082] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.000116] ata4: SATA link down (SStatus 0 SControl 300)
[    2.000149] ata6: SATA link down (SStatus 0 SControl 300)
[    2.000179] ata5: SATA link down (SStatus 0 SControl 300)
[    2.000212] ata2: SATA link down (SStatus 0 SControl 300)
[    2.000396] ata1.00: ATA-8: INTEL SSDSA2CW080G3, 4PC10302, max UDMA/133
[    2.000405] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.000732] ata1.00: configured for UDMA/133
[    2.001037] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSA2CW08 4PC1 PQ: 0 ANSI: 5
[    2.001610] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.001637] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.001885] sd 0:0:0:0: [sda] Write Protect is off
[    2.001895] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.001995] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.003461]  sda: sda1 sda2 < sda5 >
[    2.004445] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.024308] hub 3-3:1.0: USB hub found
[    2.027088] hub 3-3:1.0: 3 ports detected
[    2.118999] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.330093] usb 3-3.1: new low speed USB device number 3 using ohci_hcd
[    2.538247] usb 3-3.3: new full speed USB device number 4 using ohci_hcd
[    2.566033] udevd[323]: starting version 173
[    2.579691] Adding 3405820k swap on /dev/sda5.  Priority:-1 extents:1 across:3405820k SS
[    2.620349] lp: driver loaded but no devices found
[    2.774649] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    2.977682] wmi: Mapper loaded
[    3.060670] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[    3.060953] i2c i2c-1: nForce2 SMBus adapter at 0x4e00
[    3.251807] type=1400 audit(1326739093.403:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=567 comm="apparmor_parser"
[    3.256085] type=1400 audit(1326739093.411:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=567 comm="apparmor_parser"
[    3.257257] type=1400 audit(1326739093.411:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=567 comm="apparmor_parser"
[    3.305016] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.430302] cfg80211: Calling CRDA to update world regulatory domain
[    3.440328] nvidia: module license 'NVIDIA' taints kernel.
[    3.440343] Disabling lock debugging due to kernel taint
[    3.524223] input: Microsoft Microsoft IntelliMouse® Optical as /devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3.1/3-3.1:1.0/input/input2
[    3.524795] generic-usb 0003:045E:0039.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse® Optical] on usb-0000:00:04.0-3.1/input0
[    3.541483] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3.3/3-3.3:1.0/input/input3
[    3.541928] generic-usb 0003:05AC:020B.0002: input,hidraw1: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:04.0-3.3/input0
[    3.667063] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 19
[    3.667109] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[    3.667131] ath9k 0000:04:00.0: setting latency timer to 64
[    3.742373] ath: EEPROM regdomain: 0x60
[    3.742382] ath: EEPROM indicates we should expect a direct regpair map
[    3.742393] ath: Country alpha2 being used: 00
[    3.742398] ath: Regpair used: 0x60
[    3.742408] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.742419] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742427] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.742437] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742445] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.742454] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742462] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.742472] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742480] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.742490] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742498] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.742508] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742516] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.742526] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742533] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.742543] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742551] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.742561] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742569] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.742579] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742587] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.742597] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742605] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.742614] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742623] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.742632] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.742640] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    3.742650] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.750936] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    3.778302] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    3.781550] Registered led device: ath9k-phy0
[    3.781581] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900040a0000, irq=19
[    3.788082] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    3.788101] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    3.788944] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[    3.788961] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[    3.788971] hda_intel: Disabling MSI
[    3.789048] HDA Intel 0000:00:08.0: setting latency timer to 64
[    3.841799] forcedeth 0000:00:0a.0: eth0: no link during initialization
[    3.844277] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.895357] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.056669] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3.3/3-3.3:1.1/input/input4
[    4.057001] generic-usb 0003:05AC:020B.0003: input,hidraw2: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:04.0-3.3/input1
[    4.057064] usbcore: registered new interface driver usbhid
[    4.057071] usbhid: USB HID core driver
[    4.484906] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    4.484919] cfg80211: World regulatory domain updated:
[    4.484925] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.484936] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.484945] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.484955] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.484964] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.484973] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.656098] hda_codec: ALC662 rev1: BIOS auto-probing.
[    5.061597] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input5
[    6.448489] init: failsafe main process (821) killed by TERM signal
[    6.451398] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 23
[    6.451421] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 23 (level, low) -> IRQ 23
[    6.452448] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 22
[    6.452474] nvidia 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 22 (level, low) -> IRQ 22
[    6.452503] nvidia 0000:03:00.0: setting latency timer to 64
[    6.452518] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    6.454477] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[    6.521345] type=1400 audit(1326739096.675:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=871 comm="apparmor_parser"
[    6.521599] type=1400 audit(1326739096.675:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=872 comm="apparmor_parser"
[    6.523115] type=1400 audit(1326739096.675:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=872 comm="apparmor_parser"
[    6.524156] type=1400 audit(1326739096.679:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=872 comm="apparmor_parser"
[    6.531679] type=1400 audit(1326739096.683:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=875 comm="apparmor_parser"
[    6.533105] type=1400 audit(1326739096.687:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=877 comm="apparmor_parser"
[    6.533263] type=1400 audit(1326739096.687:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=875 comm="apparmor_parser"
[    6.534672] type=1400 audit(1326739096.687:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=876 comm="apparmor_parser"
[    6.537103] type=1400 audit(1326739096.691:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=876 comm="apparmor_parser"
[    6.540720] type=1400 audit(1326739096.695:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=873 comm="apparmor_parser"
[    6.627273] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    6.627282] vesafb: scrolling: redraw
[    6.627292] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    6.627314] mtrr: type mismatch for f9000000,400000 old: write-back new: write-combining
[    6.627328] mtrr: type mismatch for f9000000,200000 old: write-back new: write-combining
[    6.627339] mtrr: type mismatch for f9000000,100000 old: write-back new: write-combining
[    6.627351] mtrr: type mismatch for f9000000,80000 old: write-back new: write-combining
[    6.627362] mtrr: type mismatch for f9000000,40000 old: write-back new: write-combining
[    6.627374] mtrr: type mismatch for f9000000,20000 old: write-back new: write-combining
[    6.627386] mtrr: type mismatch for f9000000,10000 old: write-back new: write-combining
[    6.627398] mtrr: type mismatch for f9000000,8000 old: write-back new: write-combining
[    6.627409] mtrr: type mismatch for f9000000,4000 old: write-back new: write-combining
[    6.627420] mtrr: type mismatch for f9000000,2000 old: write-back new: write-combining
[    6.627431] mtrr: type mismatch for f9000000,1000 old: write-back new: write-combining
[    6.629734] vesafb: framebuffer at 0xf9000000, mapped to 0xffffc90003380000, using 3072k, total 3072k
[    6.630325] Console: switching to colour frame buffer device 128x48
[    6.630409] fb0: VESA VGA frame buffer device
[    6.660797] ppdev: user-space parallel port driver
[    6.856618] init: apport pre-start process (931) terminated with status 1
[    6.922477] init: apport post-stop process (967) terminated with status 1
[    7.128572] bluetooth: Unknown symbol security_sk_clone (err 0)
[    7.134736] bluetooth: Unknown symbol security_sk_clone (err 0)
[    7.144995] bluetooth: Unknown symbol security_sk_clone (err 0)
[    7.152653] bluetooth: Unknown symbol security_sk_clone (err 0)
[    7.160349] bluetooth: Unknown symbol security_sk_clone (err 0)
[    7.168481] bluetooth: Unknown symbol security_sk_clone (err 0)
[    7.474292] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[    9.375227] wlan0: authenticate with xx:xx:xx:xx:xx:xx (try 1)
[    9.378342] wlan0: authenticated
[    9.408402] wlan0: associate with xx:xx:xx:xx:xx:xx (try 1)
[    9.414403] wlan0: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x31 status=0 aid=3)
[    9.414416] wlan0: associated
[    9.423474] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    9.424932] cfg80211: Calling CRDA for country: US
[    9.437147] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    9.437158] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437165] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    9.437172] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437178] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    9.437185] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437191] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    9.437197] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437203] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    9.437210] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437216] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    9.437223] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437229] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    9.437236] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437242] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    9.437249] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437255] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    9.437262] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437268] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    9.437275] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437281] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    9.437287] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[    9.437293] cfg80211: Disabling freq 2467 MHz
[    9.437297] cfg80211: Disabling freq 2472 MHz
[    9.437301] cfg80211: Disabling freq 2484 MHz
[    9.437314] cfg80211: Regulatory domain changed to country: US
[    9.437318] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.437325] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    9.437332] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[    9.437338] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.437345] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.437352] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.437358] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[    9.707088] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  568.829162] wlan0: deauthenticated from xx:xx:xx:xx:xx:xx (Reason: 2)
[  568.968385] cfg80211: All devices are disconnected, going to restore regulatory settings
[  568.968403] cfg80211: Restoring regulatory settings
[  568.968417] cfg80211: Calling CRDA to update world regulatory domain
[  568.981266] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  568.981280] cfg80211: World regulatory domain updated:
[  568.981286] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  568.981296] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  568.981305] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  568.981314] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  568.981322] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  568.981331] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  569.695418] wlan0: authenticate with xx:xx:xx:xx:xx:xx (try 1)
[  569.699776] wlan0: authenticated
[  569.719307] wlan0: associate with xx:xx:xx:xx:xx:xx (try 1)
[  569.726552] wlan0: RX ReassocResp from xx:xx:xx:xx:xx:xx (capab=0x31 status=0 aid=2)
[  569.726560] wlan0: associated
[  569.736262] cfg80211: Calling CRDA for country: US
[  569.746636] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  569.746646] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746653] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  569.746660] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746666] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  569.746673] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746679] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  569.746686] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746692] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  569.746699] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746705] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  569.746711] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746717] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  569.746724] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746730] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  569.746737] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746743] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  569.746750] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746756] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  569.746763] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746769] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  569.746775] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  569.746781] cfg80211: Disabling freq 2467 MHz
[  569.746785] cfg80211: Disabling freq 2472 MHz
[  569.746789] cfg80211: Disabling freq 2484 MHz
[  569.746801] cfg80211: Regulatory domain changed to country: US
[  569.746806] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  569.746813] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  569.746820] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  569.746826] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  569.746833] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  569.746839] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  569.746846] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  573.777810] wlan0: deauthenticated from xx:xx:xx:xx:xx:xx (Reason: 2)
[  573.795016] cfg80211: All devices are disconnected, going to restore regulatory settings
[  573.795033] cfg80211: Restoring regulatory settings
[  573.795047] cfg80211: Calling CRDA to update world regulatory domain
[  573.806611] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  573.806622] cfg80211: World regulatory domain updated:
[  573.806627] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  573.806635] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  573.806641] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  573.806648] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  573.806654] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  573.806661] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  574.576709] wlan0: authenticate with xx:xx:xx:xx:xx:xx (try 1)
[  574.580419] wlan0: authenticated
[  574.600057] wlan0: associate with xx:xx:xx:xx:xx:xx (try 1)
[  574.608630] wlan0: RX ReassocResp from xx:xx:xx:xx:xx:xx (capab=0x31 status=0 aid=2)
[  574.608638] wlan0: associated
[  574.617266] cfg80211: Calling CRDA for country: US
[  574.628540] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  574.628552] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628561] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  574.628570] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628577] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  574.628587] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628595] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  574.628603] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628611] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  574.628620] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628628] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  574.628637] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628644] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  574.628653] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628660] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  574.628670] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628678] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  574.628687] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628695] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  574.628705] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628713] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  574.628722] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  574.628728] cfg80211: Disabling freq 2467 MHz
[  574.628733] cfg80211: Disabling freq 2472 MHz
[  574.628739] cfg80211: Disabling freq 2484 MHz
[  574.628754] cfg80211: Regulatory domain changed to country: US
[  574.628761] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  574.628770] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  574.628779] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  574.628787] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  574.628795] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  574.628823] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  574.628832] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  578.658369] wlan0: deauthenticated from xx:xx:xx:xx:xx:xx (Reason: 2)
[  578.702658] cfg80211: All devices are disconnected, going to restore regulatory settings
[  578.702677] cfg80211: Restoring regulatory settings
[  578.702692] cfg80211: Calling CRDA to update world regulatory domain
[  578.712839] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  578.712849] cfg80211: World regulatory domain updated:
[  578.712854] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  578.712861] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  578.712868] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  578.712874] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  578.712881] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  578.712887] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  579.484729] wlan0: authenticate with xx:xx:xx:xx:xx:xx (try 1)
[  579.488461] wlan0: authenticated
[  579.507339] wlan0: associate with xx:xx:xx:xx:xx:xx (try 1)
[  579.514664] wlan0: RX ReassocResp from xx:xx:xx:xx:xx:xx (capab=0x31 status=0 aid=2)
[  579.514674] wlan0: associated
[  579.524262] cfg80211: Calling CRDA for country: US
[  579.535332] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  579.535343] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535350] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  579.535357] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535363] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  579.535370] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535376] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  579.535383] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535389] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  579.535396] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535402] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  579.535409] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535414] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  579.535421] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535427] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  579.535434] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535440] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  579.535447] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535453] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  579.535460] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535466] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  579.535472] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  579.535478] cfg80211: Disabling freq 2467 MHz
[  579.535482] cfg80211: Disabling freq 2472 MHz
[  579.535486] cfg80211: Disabling freq 2484 MHz
[  579.535499] cfg80211: Regulatory domain changed to country: US
[  579.535504] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  579.535510] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  579.535517] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  579.535524] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  579.535530] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  579.535537] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  579.535543] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  583.568768] wlan0: deauthenticated from xx:xx:xx:xx:xx:xx (Reason: 2)
[  583.587210] cfg80211: All devices are disconnected, going to restore regulatory settings
[  583.587223] cfg80211: Restoring regulatory settings
[  583.587237] cfg80211: Calling CRDA to update world regulatory domain
[  583.597639] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  583.597650] cfg80211: World regulatory domain updated:
[  583.597656] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  583.597664] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  583.597671] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  583.597678] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  583.597684] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  583.597691] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  584.362914] wlan0: authenticate with xx:xx:xx:xx:xx:xx (try 1)
[  584.366656] wlan0: authenticated
[  584.386346] wlan0: associate with xx:xx:xx:xx:xx:xx (try 1)
[  584.394869] wlan0: RX ReassocResp from xx:xx:xx:xx:xx:xx (capab=0x31 status=0 aid=2)
[  584.394878] wlan0: associated
[  584.404761] cfg80211: Calling CRDA for country: US
[  584.418942] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  584.418958] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.418968] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  584.418978] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.418987] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  584.418996] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.419005] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  584.419014] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.419023] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  584.419032] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.419041] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  584.419050] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.419058] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  584.419068] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.419077] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  584.419086] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.419095] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  584.419105] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.419113] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  584.419123] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.419131] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  584.419142] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  584.419149] cfg80211: Disabling freq 2467 MHz
[  584.419155] cfg80211: Disabling freq 2472 MHz
[  584.419161] cfg80211: Disabling freq 2484 MHz
[  584.419177] cfg80211: Regulatory domain changed to country: US
[  584.419183] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  584.419193] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  584.419202] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  584.419212] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  584.419221] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  584.419230] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  584.419240] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)

```

6) Network Configuration:

```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: xx:xx:xx:xx:xx:xx
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:21 memory:fae7c000-fae7cfff ioport:d080(size=8) memory:fae7e400-fae7e4ff memory:fae7e000-fae7e00f
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-14-generic firmware=N/A ip=10.0.1.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:febf0000-febfffff

```

7) Network Scan:

```

$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"xxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000026d8a6c3
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00065761796C6F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0103
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010B0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016C0320
                    IE: Unknown: DD0E0017F207000101060026B0FEED42

```

8) Ubuntu Version:

```

$ lsb_release -d
Description:	Ubuntu 11.10

```

9) Kernel:

```

$ uname -mr
3.0.0-14-generic x86_64

```

10) Restart Networking:

```

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                             [ OK ] 

```

---

### Post by spacecheck on 2012-01-16
Just saw this _solved post_, mentions the same driver/wlan module:

[http://ubuntuforums.org/showthread.php?p=11434781#post11434781](http://ubuntuforums.org/showthread.php?p=11434781#post11434781)

If it works, be sure to use the thread tools to mark the thread solved.

Good luck!

---

### Post by kev22257 on 2012-01-16
> **spacecheck said:**
> Just saw this _solved post_, mentions the same driver/wlan module:

[http://ubuntuforums.org/showthread.php?p=11434781#post11434781](http://ubuntuforums.org/showthread.php?p=11434781#post11434781)

If it works, be sure to use the thread tools to mark the thread solved.

Good luck!

Thanks for the reply.  That is what I mentioned I had to do to even get it working, but the speed is still slow and it's not connecting, or even seeing the option from what I can see, at 802.11n rates.

---

### Post by praseodym on 2012-01-16
Try pure WPA2-AES encryption, if possible.

---

### Post by kev22257 on 2012-01-16
> **praseodym said:**
> Try pure WPA2-AES encryption, if possible.

Thanks for your reply.

I have an Apple AirPort Extreme router and it doesn't let me choose between TKIP and AES that I can see, so I'm sure it's running in some TKIP+AES mode.  In any event it was WPA/WPA2 so I tried setting it to purely WPA2, but that didn't seem to make any difference.

---

### Post by kev22257 on 2012-01-18
Does anyone else have a suggestion for my issue?  I'm still not able to resolve it.

---

### Post by praseodym on 2012-01-18
Try Wicd with Add-On instead of the NM:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo apt-get remove --purge network-manager*
sudo service wicd restart
```
Set "wlan0" (or whatever 'iwconfig' shows as interface name), and "wext" as driver. The Add-On brings some more encryption template with it.

---

### Post by kev22257 on 2012-01-19
I was able to solve my problem, at least in regards to speed, by changing the channel on my router from 11 to 1.  It doesn't really make sense to me because the other wireless networks that I can see are all on channel 6, so I'm no further away from them than I was before, but I won't complain.

Thanks everyone for your help.  Now I just need to get it to actually connect at 802.11n speeds.

---

