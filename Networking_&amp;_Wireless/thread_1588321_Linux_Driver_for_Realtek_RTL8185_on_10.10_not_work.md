---
title: "Linux Driver for Realtek RTL8185 on 10.10 not working"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by happysadhu on 2010-10-04
Hi,
when I updated from 10.04 to 10.10 beta, I lost my wireless on my Gateway  MX3410 laptop. In 10.04, the wireless Realtek RTL8185 card was auto-detected, worked with the default driver. 

So I installed the linux driver version of Realtek RTL8185. Although the driver shows up in the "Additional Drivers" panel under "Administration", the computer is not recognising the driver.

Below is all the specs of the current situation. Thanks in advance for the help. 

Gateway MX3410 Computer
OS: Ubuntu maverick (development branch)
2.6.35-22-generic x86_64

lspci:
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

lsusb:
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:03:25:3c:28:32  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe3c:2832/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3796997 (3.7 MB)  TX bytes:521027 (521.0 KB)
          Interrupt:21 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7540 (7.5 KB)  TX bytes:7540 (7.5 KB)


iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.

lsmod:
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_idt      64667  1 
binfmt_misc             7984  1 
nvidia              11087157  30 
joydev                 11363  0 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           245044  0 
snd                    64117  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  22176  0 
psmouse                62080  0 
output                  2527  1 video
edac_core              46822  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
k8temp                  4064  0 
serio_raw               4910  0 
edac_mce_amd            9387  0 
i2c_nforce2             6155  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
pata_amd               12050  2 
forcedeth              55649  0 

dmesg:
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:40000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u1048576
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 629888
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=0cd0e462-188d-4409-8997-3c6a8756f295 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ d19e000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Subtract (47 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [003756f000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d181b4]             BRK
[    0.000000]   #4 [00000f8df0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f8de0 - 00000f8df0]    MP-table mpf
[    0.000000]   #6 [000009dc00 - 000009e171]   BIOS reserved
[    0.000000]   #7 [000009e275 - 00000f8de0]   BIOS reserved
[    0.000000]   #8 [000009e171 - 000009e275]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000019000]         PGTABLE
[    0.000000]   #12 [0001d181c0 - 0001d1d1c0]       NODE_DATA
[    0.000000]   #13 [0001d1d1c0 - 0001d1e1c0]         BOOTMEM
[    0.000000]   #14 [0001d17140 - 0001d17320]         BOOTMEM
[    0.000000]   #15 [000251f000 - 0002520000]         BOOTMEM
[    0.000000]   #16 [0002520000 - 0002521000]         BOOTMEM
[    0.000000]   #17 [0002600000 - 0004a00000]        MEMMAP 0
[    0.000000]   #18 [0001d17340 - 0001d174c0]         BOOTMEM
[    0.000000]   #19 [0001d1e1c0 - 0001d361c0]         BOOTMEM
[    0.000000]   #20 [0001d37000 - 0001d38000]         BOOTMEM
[    0.000000]   #21 [0001d174c0 - 0001d17503]         BOOTMEM
[    0.000000]   #22 [0001d17540 - 0001d177e0]         BOOTMEM
[    0.000000]   #23 [0001d17800 - 0001d17868]         BOOTMEM
[    0.000000]   #24 [0001d17880 - 0001d178e8]         BOOTMEM
[    0.000000]   #25 [0001d17900 - 0001d17968]         BOOTMEM
[    0.000000]   #26 [0001d17980 - 0001d179e8]         BOOTMEM
[    0.000000]   #27 [0001d17a00 - 0001d17a68]         BOOTMEM
[    0.000000]   #28 [0001d17a80 - 0001d17ae8]         BOOTMEM
[    0.000000]   #29 [0001d17b00 - 0001d17b68]         BOOTMEM
[    0.000000]   #30 [0001d17b80 - 0001d17be8]         BOOTMEM
[    0.000000]   #31 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #32 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #33 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #34 [0001d17d80 - 0001d17da0]         BOOTMEM
[    0.000000]   #35 [0001d17dc0 - 0001d17e00]         BOOTMEM
[    0.000000]   #36 [0001d17e00 - 0001d17e40]         BOOTMEM
[    0.000000]   #37 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #38 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #39 [0001d17e40 - 0001d17e48]         BOOTMEM
[    0.000000]   #40 [0001d17e80 - 0001d17e88]         BOOTMEM
[    0.000000]   #41 [0001d17ec0 - 0001d17ec8]         BOOTMEM
[    0.000000]   #42 [0001d17f00 - 0001d17f10]         BOOTMEM
[    0.000000]   #43 [0001d361c0 - 0001d36300]         BOOTMEM
[    0.000000]   #44 [0001d17f40 - 0001d17fa0]         BOOTMEM
[    0.000000]   #45 [0001d36300 - 0001d36360]         BOOTMEM
[    0.000000]   #46 [0001d38000 - 0001d40000]         BOOTMEM
[    0.000000] Memory: 2493012k/2554944k available (5708k kernel code, 460k absent, 61472k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:512
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 26214400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1603.256 MHz processor.
[    0.020008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3206.51 BogoMIPS (lpj=16032560)
[    0.020015] pid_max: default: 32768 minimum: 301
[    0.020049] Security Framework initialized
[    0.020073] AppArmor: AppArmor initialized
[    0.020075] Yama: becoming mindful.
[    0.020765] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.024775] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.026646] Mount-cache hash table entries: 256
[    0.026841] Initializing cgroup subsys ns
[    0.026847] Initializing cgroup subsys cpuacct
[    0.026853] Initializing cgroup subsys memory
[    0.026867] Initializing cgroup subsys devices
[    0.026870] Initializing cgroup subsys freezer
[    0.026874] Initializing cgroup subsys net_cls
[    0.026909] tseg: 009bf80000
[    0.026912] CPU: Physical Processor ID: 0
[    0.026914] CPU: Processor Core ID: 0
[    0.026918] mce: CPU supports 5 MCE banks
[    0.026932] using C1E aware idle routine
[    0.026935] Performance Events: AMD PMU driver.
[    0.026942] ... version:                0
[    0.026945] ... bit width:              48
[    0.026948] ... generic registers:      4
[    0.026950] ... value mask:             0000ffffffffffff
[    0.026953] ... max period:             00007fffffffffff
[    0.026956] ... fixed-purpose events:   0
[    0.026958] ... event mask:             000000000000000f
[    0.030955] ACPI: Core revision 20100428
[    0.040013] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040021] ftrace: allocating 22680 entries in 89 pages
[    0.049509] Setting APIC routing to flat
[    0.050147] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.150172] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.160000] Booting Node   0, Processors  #1 Ok.
[    0.030000] System has AMD C1E enabled
[    0.030000] Switch to broadcast mode on CPU1
[    0.310077] Brought up 2 CPUs
[    0.310080] Total of 2 processors activated (6413.29 BogoMIPS).
[    0.310375] Switch to broadcast mode on CPU0
[    0.310375] devtmpfs: initialized
[    0.311168] regulator: core version 0.5
[    0.311209] Time: 22:17:36  Date: 10/04/10
[    0.311272] NET: Registered protocol family 16
[    0.311447] node 0 link 0: io port [1000, fffff]
[    0.311452] TOM: 00000000a0000000 aka 2560M
[    0.311456] node 0 link 0: mmio [e0000000, efffffff]
[    0.311460] node 0 link 0: mmio [a0000, bffff]
[    0.311465] node 0 link 0: mmio [a0000000, fe0bffff]
[    0.311469] bus: [00, ff] on node 0 link 0
[    0.311473] bus: 00 index 0 [io  0x0000-0xffff]
[    0.311476] bus: 00 index 1 [mem 0xa0000000-0xfcffffffff]
[    0.311479] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.311489] ACPI: bus type pci registered
[    0.311577] PCI: MMCONFIG for domain 0000 [bus 00-05] at [mem 0xe0000000-0xe05fffff] (base 0xe0000000)
[    0.311582] PCI: MMCONFIG at [mem 0xe0000000-0xe05fffff] reserved in E820
[    0.312169] PCI: Using configuration type 1 for base access
[    0.313168] Trying to unpack rootfs image as initramfs...
[    0.313168] bio: create slab <bio-0> at 0
[    0.313168] ACPI: EC: Look up EC in DSDT
[    0.315053] ACPI: Interpreter enabled
[    0.315057] ACPI: (supports S0 S3 S4 S5)
[    0.315080] ACPI: Using IOAPIC for interrupt routing
[    0.323937] ACPI: EC: GPE = 0x5b, I/O: command/status = 0x66, data = 0x62
[    0.324205] ACPI: No dock devices found.
[    0.324210] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.324381] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.324715] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.324719] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.324723] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.324727] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff] (ignored)
[    0.324730] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff] (ignored)
[    0.324734] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000cbfff] (ignored)
[    0.324737] pci_root PNP0A03:00: host bridge window [mem 0x000cc000-0x000cffff] (ignored)
[    0.324741] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.324744] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.324748] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.324752] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    0.324755] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff] (ignored)
[    0.324759] pci_root PNP0A03:00: host bridge window [mem 0x000e4000-0x000e7fff] (ignored)
[    0.324762] pci_root PNP0A03:00: host bridge window [mem 0x000e8000-0x000ebfff] (ignored)
[    0.324766] pci_root PNP0A03:00: host bridge window [mem 0x000ec000-0x000effff] (ignored)
[    0.324769] pci_root PNP0A03:00: host bridge window [mem 0x000f0000-0x000fffff] (ignored)
[    0.324773] pci_root PNP0A03:00: host bridge window [mem 0xa0000000-0xfebfffff] (ignored)
[    0.325058] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325062] pci 0000:00:03.0: PME# disabled
[    0.325085] pci 0000:00:05.0: reg 10: [mem 0xb2000000-0xb2ffffff]
[    0.325092] pci 0000:00:05.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.325099] pci 0000:00:05.0: reg 1c: [mem 0xb1000000-0xb1ffffff 64bit]
[    0.325105] pci 0000:00:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.325306] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.325353] pci 0000:00:0a.1: reg 20: [io  0x3040-0x307f]
[    0.325359] pci 0000:00:0a.1: reg 24: [io  0x3000-0x303f]
[    0.325386] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.325392] pci 0000:00:0a.1: PME# disabled
[    0.325427] pci 0000:00:0a.3: reg 10: [mem 0xb0040000-0xb007ffff]
[    0.325525] pci 0000:00:0b.0: reg 10: [mem 0xb0004000-0xb0004fff]
[    0.325564] pci 0000:00:0b.0: supports D1 D2
[    0.325566] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325571] pci 0000:00:0b.0: PME# disabled
[    0.325601] pci 0000:00:0b.1: reg 10: [mem 0xb0005000-0xb00050ff]
[    0.325639] pci 0000:00:0b.1: supports D1 D2
[    0.325641] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325646] pci 0000:00:0b.1: PME# disabled
[    0.325688] pci 0000:00:0d.0: reg 20: [io  0x3080-0x308f]
[    0.325780] pci 0000:00:10.1: reg 10: [mem 0xb0000000-0xb0003fff]
[    0.325818] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.325822] pci 0000:00:10.1: PME# disabled
[    0.325860] pci 0000:00:14.0: reg 10: [mem 0xb0006000-0xb0006fff]
[    0.325866] pci 0000:00:14.0: reg 14: [io  0x3090-0x3097]
[    0.325894] pci 0000:00:14.0: supports D1 D2
[    0.325897] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325901] pci 0000:00:14.0: PME# disabled
[    0.326017] PCI: peer root bus 00 res updated from pci conf
[    0.326049] pci 0000:00:03.0: PCI bridge to [bus 03-04]
[    0.326054] pci 0000:00:03.0:   bridge window [io  0x9000-0x9fff]
[    0.326058] pci 0000:00:03.0:   bridge window [mem 0xfa100000-0xfa8fffff]
[    0.326064] pci 0000:00:03.0:   bridge window [mem 0xbdf00000-0xbfefffff 64bit pref]
[    0.326117] pci 0000:06:09.0: reg 10: [io  0x6000-0x60ff]
[    0.326124] pci 0000:06:09.0: reg 14: [mem 0xb3400000-0xb34001ff]
[    0.326160] pci 0000:06:09.0: supports D1 D2
[    0.326163] pci 0000:06:09.0: PME# supported from D1 D2 D3hot D3cold
[    0.326167] pci 0000:06:09.0: PME# disabled
[    0.326198] pci 0000:00:10.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.326202] pci 0000:00:10.0:   bridge window [io  0x6000-0x6fff]
[    0.326206] pci 0000:00:10.0:   bridge window [mem 0xb3400000-0xb34fffff]
[    0.326211] pci 0000:00:10.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.326215] pci 0000:00:10.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.326218] pci 0000:00:10.0:   bridge window [mem 0xa0000000-0xfcffffffff] (subtractive decode)
[    0.326222] pci 0000:00:10.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.326234] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.326371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.326416] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.371886] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.372103] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15)
[    0.372311] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.372522] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.372730] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.372942] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.373156] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.373375] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.373585] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.373796] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.374012] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.374220] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.374429] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.374639] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.374852] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.375065] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.375283] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.375496] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.375707] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.375763] HEST: Table is not found!
[    0.375891] vgaarb: device added: PCI:0000:00:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.375909] vgaarb: loaded
[    0.376117] SCSI subsystem initialized
[    0.376247] libata version 3.00 loaded.
[    0.376312] usbcore: registered new interface driver usbfs
[    0.376327] usbcore: registered new interface driver hub
[    0.376367] usbcore: registered new device driver usb
[    0.376562] ACPI: WMI: Mapper loaded
[    0.376565] PCI: Using ACPI for IRQ routing
[    0.376570] PCI: pci_cache_line_size set to 64 bytes
[    0.376679] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.376683] reserve RAM buffer: 000000009bf10000 - 000000009bffffff 
[    0.376812] NetLabel: Initializing
[    0.376815] NetLabel:  domain hash size = 128
[    0.376817] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.376842] NetLabel:  unlabeled traffic allowed by default
[    0.384327] AppArmor: AppArmor Filesystem Enabled
[    0.384349] pnp: PnP ACPI init
[    0.384373] ACPI: bus type pnp registered
[    0.391275] pnp: PnP ACPI: found 11 devices
[    0.391278] ACPI: ACPI bus type pnp unregistered
[    0.391305] system 00:00: [mem 0xffc00000-0xffffffff] could not be reserved
[    0.391310] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.391314] system 00:00: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.391323] system 00:02: [mem 0xe0000000-0xefffffff] has been reserved
[    0.391332] system 00:03: [io  0x1000-0x107f] has been reserved
[    0.391336] system 00:03: [io  0x1080-0x10ff] has been reserved
[    0.391340] system 00:03: [io  0x1400-0x147f] has been reserved
[    0.391344] system 00:03: [io  0x1480-0x14ff] has been reserved
[    0.391348] system 00:03: [io  0x1800-0x187f] has been reserved
[    0.391351] system 00:03: [io  0x1880-0x18ff] has been reserved
[    0.391355] system 00:03: [io  0x3040-0x307f] has been reserved
[    0.391359] system 00:03: [io  0x3000-0x303f] has been reserved
[    0.391363] system 00:03: [io  0x2000-0x203f] has been reserved
[    0.391372] system 00:04: [io  0x0200-0x020f] has been reserved
[    0.391376] system 00:04: [io  0x0360-0x0361] has been reserved
[    0.391379] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.394165] Switching to clocksource acpi_pm
[    0.400092] pci 0000:00:05.0: BAR 6: assigned [mem 0xa0000000-0xa001ffff pref]
[    0.400092] pci 0000:00:03.0: PCI bridge to [bus 03-04]
[    0.400092] pci 0000:00:03.0:   bridge window [io  0x9000-0x9fff]
[    0.400092] pci 0000:00:03.0:   bridge window [mem 0xfa100000-0xfa8fffff]
[    0.400092] pci 0000:00:03.0:   bridge window [mem 0xbdf00000-0xbfefffff 64bit pref]
[    0.400092] pci 0000:00:10.0: PCI bridge to [bus 06-06]
[    0.400092] pci 0000:00:10.0:   bridge window [io  0x6000-0x6fff]
[    0.400092] pci 0000:00:10.0:   bridge window [mem 0xb3400000-0xb34fffff]
[    0.400092] pci 0000:00:10.0:   bridge window [mem pref disabled]
[    0.400092] pci 0000:00:03.0: setting latency timer to 64
[    0.400092] pci 0000:00:10.0: setting latency timer to 64
[    0.400092] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.400092] pci_bus 0000:00: resource 5 [mem 0xa0000000-0xfcffffffff]
[    0.400092] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.400092] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
[    0.400092] pci_bus 0000:03: resource 1 [mem 0xfa100000-0xfa8fffff]
[    0.400092] pci_bus 0000:03: resource 2 [mem 0xbdf00000-0xbfefffff 64bit pref]
[    0.400092] pci_bus 0000:06: resource 0 [io  0x6000-0x6fff]
[    0.400092] pci_bus 0000:06: resource 1 [mem 0xb3400000-0xb34fffff]
[    0.400092] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
[    0.400092] pci_bus 0000:06: resource 5 [mem 0xa0000000-0xfcffffffff]
[    0.400092] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.400092] NET: Registered protocol family 2
[    0.400092] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.400092] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.410400] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.411290] TCP: Hash tables configured (established 524288 bind 65536)
[    0.411294] TCP reno registered
[    0.411316] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.411399] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.411575] NET: Registered protocol family 1
[    0.411611] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    0.411618] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.411676] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.411685] pci 0000:00:05.0: Boot video device
[    0.622601] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.622660] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.622688] PCI: CLS 64 bytes, default 64
[    0.674127] Simple Boot Flag at 0x31 set to 0x1
[    0.674420] Scanning for low memory corruption every 60 seconds
[    0.674608] audit: initializing netlink socket (disabled)
[    0.674623] type=2000 audit(1286230656.669:1): initialized
[    0.693242] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.695303] VFS: Disk quotas dquot_6.5.2
[    0.695394] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.696256] fuse init (API version 7.14)
[    0.696371] msgmni has been set to 4869
[    0.697758] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.697764] io scheduler noop registered
[    0.697767] io scheduler deadline registered
[    0.697821] io scheduler cfq registered (default)
[    0.698048] pcieport 0000:00:03.0: setting latency timer to 64
[    0.698071]   alloc irq_desc for 40 on node 0
[    0.698074]   alloc kstat_irqs on node 0
[    0.698085] pcieport 0000:00:03.0: irq 40 for MSI/MSI-X
[    0.698188] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.698214] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.698867] ACPI: AC Adapter [AC] (on-line)
[    0.698966] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.698974] ACPI: Power Button [PWRB]
[    0.699030] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.699035] ACPI: Sleep Button [SLPB]
[    0.699092] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.699367] ACPI: Lid Switch [LID]
[    0.699451] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.699456] ACPI: Power Button [PWRF]
[    0.699761] ACPI: acpi_idle registered with cpuidle
[    0.699796] ACPI: processor limited to max C-state 1
[    0.702538] ERST: Table is not found!
[    0.702896] Linux agpgart interface v0.103
[    0.702902] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.704748] brd: module loaded
[    0.705489] loop: module loaded
[    0.706074] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.706594] Fixed MDIO Bus: probed
[    0.706641] PPP generic driver version 2.4.2
[    0.706725] tun: Universal TUN/TAP device driver, 1.6
[    0.706728] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.706844] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.707340] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 23
[    0.707347]   alloc irq_desc for 23 on node 0
[    0.707349]   alloc kstat_irqs on node 0
[    0.707365] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 23 (level, high) -> IRQ 23
[    0.707388] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.707392] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.707478] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.707522] ehci_hcd 0000:00:0b.1: debug port 1
[    0.707533] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.707576] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xb0005000
[    0.720243] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.720438] hub 1-0:1.0: USB hub found
[    0.720445] hub 1-0:1.0: 8 ports detected
[    0.720584] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.721190] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.721197]   alloc irq_desc for 22 on node 0
[    0.721200]   alloc kstat_irqs on node 0
[    0.721214] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    0.721239] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.721244] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.721345] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.721389] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xb0004000
[    0.733561] ACPI: Battery Slot [BAT0] (battery present)
[    0.782222] hub 2-0:1.0: USB hub found
[    0.782232] hub 2-0:1.0: 8 ports detected
[    0.782371] uhci_hcd: USB Universal Host Controller Interface driver
[    0.782537] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.785757] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.785768] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.785870] mice: PS/2 mouse device common for all mice
[    0.786071] rtc_cmos 00:07: RTC can wake from S4
[    0.786160] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.786197] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.786350] device-mapper: uevent: version 1.0.3
[    0.786495] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.786594] device-mapper: multipath: version 1.1.1 loaded
[    0.786598] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.786810] cpuidle: using governor ladder
[    0.786813] cpuidle: using governor menu
[    0.787292] TCP cubic registered
[    0.787485] NET: Registered protocol family 10
[    0.788012] lo: Disabled Privacy Extensions
[    0.788312] NET: Registered protocol family 17
[    0.788365] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 (2 cpu cores) (version 2.20.00)
[    0.788416] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[    0.788419] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    0.788612] PM: Resume from disk failed.
[    0.788628] registered taskstats version 1
[    0.788910]   Magic number: 14:378:299
[    0.789033] rtc_cmos 00:07: setting system clock to 2010-10-04 22:17:37 UTC (1286230657)
[    0.789038] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.789040] EDD information not available.
[    0.815071] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.906817] Freeing initrd memory: 10756k freed
[    0.915368] Freeing unused kernel memory: 908k freed
[    0.916009] Write protecting the kernel read-only data: 10240k
[    0.916259] Freeing unused kernel memory: 416k freed
[    0.916747] Freeing unused kernel memory: 1644k freed
[    0.949691] udev[105]: starting version 163
[    1.123049] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.123506] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    1.123513]   alloc irq_desc for 21 on node 0
[    1.123517]   alloc kstat_irqs on node 0
[    1.123533] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, high) -> IRQ 21
[    1.123540] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.123612] nv_probe: set workaround bit for reversed mac addr
[    1.651267] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:03:25:3c:28:32
[    1.651273] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    1.651381] pata_amd 0000:00:0d.0: version 0.4.1
[    1.651443] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.651540] scsi0 : pata_amd
[    1.652028] scsi1 : pata_amd
[    1.653064] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.653068] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.830659] ata1.00: ATA-7: HTS421280H9AT00, HA3OA70S, max UDMA/100
[    1.830665] ata1.00: 156301488 sectors, multi 16: LBA48 
[    1.830697] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c000) ACPI=0x3f01f (20:600:0x13)
[    1.870591] ata1.00: configured for UDMA/100
[    1.870813] scsi 0:0:0:0: Direct-Access     ATA      HTS421280H9AT00  HA3O PQ: 0 ANSI: 5
[    1.871070] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.871204] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.871274] sd 0:0:0:0: [sda] Write Protect is off
[    1.871278] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.871309] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.871544]  sda: sda1 sda2 < sda5 >
[    1.933467] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.070496] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L532U, GA03, max UDMA/33
[    2.070532] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc600c000) ACPI=0x7001 (60:600:0x11)
[    2.110443] ata2.00: configured for UDMA/33
[    2.118107] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L532U GA03 PQ: 0 ANSI: 5
[    2.127819] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.127826] Uniform CD-ROM driver Revision: 3.20
[    2.128002] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.128094] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.483511] EXT3-fs: barriers not enabled
[    2.516980] kjournald starting.  Commit interval 5 seconds
[    2.517060] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   30.766567] udev[360]: starting version 163
[   30.847794] Adding 1269096k swap on /dev/sda5.  Priority:-1 extents:1 across:1269096k 
[   30.926312] Disabling lock debugging due to kernel taint
[   30.940713] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   30.940749] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   30.943476] lp: driver loaded but no devices found
[   31.001464] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
[   31.001814] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   31.001887] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   31.018410] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   31.105563] EDAC MC: Ver: 2.1.0 Sep 19 2010
[   31.118425] type=1400 audit(1286230687.819:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=538 comm="apparmor_parser"
[   31.118808] type=1400 audit(1286230687.819:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=538 comm="apparmor_parser"
[   31.119024] type=1400 audit(1286230687.819:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=538 comm="apparmor_parser"
[   31.154257] EDAC amd64_edac:  Ver: 3.3.0 Sep 19 2010
[   31.192915] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   31.218722] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   31.218736] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   31.218738]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   31.218740]  (Note that use of the override may cause unknown side effects.)
[   31.218774] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   31.513904] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   31.513912]   alloc irq_desc for 20 on node 0
[   31.513916]   alloc kstat_irqs on node 0
[   31.513932] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 20 (level, high) -> IRQ 20
[   31.513937] hda_intel: Disable MSI for Nvidia chipset
[   31.513992] HDA Intel 0000:00:10.1: setting latency timer to 64
[   31.514231] usbcore: registered new interface driver ndiswrapper
[   31.732932] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008/0x0
[   31.772377] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   32.151715] EXT3-fs (sda1): using internal journal
[   32.622577] eth0: no link during initialization.
[   32.623787] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.669558] type=1400 audit(1286230689.369:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=873 comm="apparmor_parser"
[   32.676466] type=1400 audit(1286230689.379:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=875 comm="apparmor_parser"
[   32.676565] type=1400 audit(1286230689.379:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=874 comm="apparmor_parser"
[   32.676954] type=1400 audit(1286230689.379:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=874 comm="apparmor_parser"
[   32.677171] type=1400 audit(1286230689.379:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=874 comm="apparmor_parser"
[   32.682078] type=1400 audit(1286230689.379:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=875 comm="apparmor_parser"
[   32.682146] type=1400 audit(1286230689.379:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=877 comm="apparmor_parser"
[   35.820230] input: HDA NVidia Mic at Ext Front Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input7
[   35.825781] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 19
[   35.825791]   alloc irq_desc for 19 on node 0
[   35.825794]   alloc kstat_irqs on node 0
[   35.825812] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 19 (level, high) -> IRQ 19
[   35.825823] nvidia 0000:00:05.0: setting latency timer to 64
[   35.825830] vgaarb: device changed decodes: PCI:0000:00:05.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   35.826185] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.53  Fri Aug 27 20:27:48 PDT 2010
[   35.916306] ppdev: user-space parallel port driver
[   80.912745] eth0: link up.
[   80.913786] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   81.764835] eth0: link down.
[   83.471264] eth0: link up.
[   91.522571] eth0: no IPv6 routers present
[   95.810033] Clocksource tsc unstable (delta = -245271557 ns)

sudo lshw -C network:

*-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:6000(size=256) memory:b3400000-b34001ff


iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...                                                                                        Ignoring unknown interface eth0=eth0.

---

### Post by happysadhu on 2010-10-12
Hi Me Again,
So I've tried everything under the moon. I even reinstalled the stable version of 10.10. I tried ndiswrapper once again with the vista 64bit driver, tried the linux version for rtl8185 (I get error messages - must be just for 32bit?), tried blacklisting rtl8180, tried removing rtl8180 from the blacklist and sudo modeprobe rtl8180 to try the default driver again. All for nut'n.

Any ideas anyone?

THanks,
Sam

---

### Post by Handssolow on 2010-10-13
Are you aware of Everthon Valadão's advice about installing an edited RTL8185 Linux driver?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275230](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275230)

I installed a RTL8185 based pci wifi card today to replace a probably faulty rt2500 card. The new card works but with an indicated low quality and signal 14/100. My Mavarick's using an 8180 driver I seem to remember. Nice if a working 8185 was available in Maverick.

---

### Post by jonaternet on 2012-05-05
Hello, my wireles card now works out of the box. I posted here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290325)
> 

Hello, I am happy  to announce that this bug seems fixed in Ubuntu 12.04 !  Before I used  to complile the r8185b.ko module, force it to load at startup with an  entry in /etc/modules, and blacklist rtl8180. This worked, but isn't  necessery anymore :-)

              Not sure if it is fixed for all models, here is mine :
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
( the real brand is zyxel )
The mentioned trick works in previous versions of ubuntu, but the wireless card loaded only 1-2  minutes after boot. By the way my signal is now even better now than when I compiled the module manually.

---

