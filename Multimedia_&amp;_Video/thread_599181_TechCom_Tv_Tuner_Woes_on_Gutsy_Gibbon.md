---
title: "TechCom Tv Tuner Woes on Gutsy Gibbon"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by BijuMathew on 2007-11-01
Hi all, 
 Ive been in the process of migrating to Ubuntu Gutsy Gibbon. I have installed the AMD64 DVD edition of Gutsy on my computer. 

My system specification is given here

AMD 4400 AM2 
Asus M2N MX-SE
2 GB Ram
SATA 80 GB Drive
IDE 80 GB Drive
TechCom Tv Tuner Card
17 ' LG 700E Monitor
56k External Modem. 

The install process went through quite easy. Im having problems with the Tv Tuner Card as you might have guessed. I can't get it to work on any TV Program on my system. 

Ive tried TvTime , ScanTv and MythTv . I dont know what I am doing wrong or if I havent configured something correctly. I don't need any fancy functionality. Just want to watch the occasional movie on my Computer if possible. The best I was able to get was TvTime to display a constant blue screen which said "No Signal" Frames too short for saa7134 . Cannot open capture device /dev/video0 . 

Here is lspci 
```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

```

Here is lsmod | grep saa7134 

```

saa7134_alsa           17440  0 
saa7134               148308  1 saa7134_alsa
snd_pcm                94344  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
video_buf              30084  2 saa7134_alsa,saa7134
compat_ioctl32         11136  1 saa7134
ir_kbd_i2c             11536  1 saa7134
ir_common              38916  2 saa7134,ir_kbd_i2c
videodev               31360  1 saa7134
v4l2_common            21888  4 saa7134,tuner,compat_ioctl32,videodev
v4l1_compat            15364  2 saa7134,videodev
snd                    69288  12 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               30208  5 saa7134,tuner,ir_kbd_i2c,nvidia,i2c_nforce2

```

Here is dmesg 
```
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
biju@Venom:~$ lsmod | grep saa7134
saa7134_alsa           17440  0 
saa7134               148308  1 saa7134_alsa
snd_pcm                94344  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
video_buf              30084  2 saa7134_alsa,saa7134
compat_ioctl32         11136  1 saa7134
ir_kbd_i2c             11536  1 saa7134
ir_common              38916  2 saa7134,ir_kbd_i2c
videodev               31360  1 saa7134
v4l2_common            21888  4 saa7134,tuner,compat_ioctl32,videodev
v4l1_compat            15364  2 saa7134,videodev
snd                    69288  12 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               30208  5 saa7134,tuner,ir_kbd_i2c,nvidia,i2c_nforce2
biju@Venom:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=879689aa-1698-45c9-b944-4d4761fb3376 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fc0000 (usable)
[    0.000000]  BIOS-e820: 0000000077fc0000 - 0000000077fce000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077fce000 - 0000000077ff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077ff0000 - 0000000078000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 491456) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FB810 checksum 0
[    0.000000] ACPI: RSDP 000FB810, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 77FC0000, 0038 (r1 A_M_I_ OEMRSDT   5000701 MSFT       97)
[    0.000000] ACPI: FACP 77FC0200, 0084 (r2 A_M_I_ OEMFACP   5000701 MSFT       97)
[    0.000000] ACPI: DSDT 77FC0440, 6768 (r1  A0785 A0785000        0 INTL  2002026)
[    0.000000] ACPI: FACS 77FCE000, 0040
[    0.000000] ACPI: APIC 77FC0390, 0070 (r1 A_M_I_ OEMAPIC   5000701 MSFT       97)
[    0.000000] ACPI: MCFG 77FC0400, 003C (r1 A_M_I_ OEMMCFG   5000701 MSFT       97)
[    0.000000] ACPI: OEMB 77FCE040, 0060 (r1 A_M_I_ AMI_OEM   5000701 MSFT       97)
[    0.000000] ACPI: HPET 77FC6BB0, 0038 (r1 A_M_I_ OEMHPET0  5000701 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000077fc0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 491456) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000077fc0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   491456
[    0.000000] On node 0 totalpages: 491359
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6663 pages used for memmap
[    0.000000]   DMA32 zone: 480697 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:86c00000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 483515
[    0.000000] Kernel command line: root=UUID=879689aa-1698-45c9-b944-4d4761fb3376 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   12.771120] time.c: Detected 2310.479 MHz processor.
[   12.774076] Console: colour VGA+ 80x25
[   12.774090] Checking aperture...
[   12.774093] CPU 0: aperture @ 4040000000 size 32 MB
[   12.774095] Aperture too small (32 MB)
[   12.779979] No AGP bridge found
[   12.800598] Memory: 1926132k/1965824k available (2274k kernel code, 39304k reserved, 1181k data, 296k init)
[   12.800637] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   12.879789] Calibrating delay using timer specific routine.. 4625.36 BogoMIPS (lpj=9250739)
[   12.879814] Security Framework v1.0.0 initialized
[   12.879819] SELinux:  Disabled at boot.
[   12.879964] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   12.880982] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.881501] Mount-cache hash table entries: 256
[   12.881607] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.881610] CPU: L2 Cache: 512K (64 bytes/line)
[   12.881612] CPU 0/0 -> Node 0
[   12.881614] CPU: Physical Processor ID: 0
[   12.881615] CPU: Processor Core ID: 0
[   12.881630] SMP alternatives: switching to UP code
[   12.881853] Early unpacking initramfs... done
[   13.149724] ACPI: Core revision 20070126
[   13.149778] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.192854] Using local APIC timer interrupts.
[   13.236118] result 12556942
[   13.236120] Detected 12.556 MHz APIC timer.
[   13.239680] SMP alternatives: switching to SMP code
[   13.239789] Booting processor 1/2 APIC 0x1
[   13.249606] Initializing CPU#1
[   13.327323] Calibrating delay using timer specific routine.. 4621.04 BogoMIPS (lpj=9242096)
[   13.327329] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   13.327331] CPU: L2 Cache: 512K (64 bytes/line)
[   13.327333] CPU 1/1 -> Node 0
[   13.327335] CPU: Physical Processor ID: 0
[   13.327336] CPU: Processor Core ID: 1
[   13.327424] AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 01
[   13.331590] Brought up 2 CPUs
[   13.900135] migration_cost=269
[   13.900569] NET: Registered protocol family 16
[   13.900646] ACPI: bus type pci registered
[   13.900651] PCI: Using configuration type 1
[   13.903834] ACPI: EC: Look up EC in DSDT
[   13.909144] ACPI: Interpreter enabled
[   13.909147] ACPI: (supports S0 S1 S3 S4 S5)
[   13.909163] ACPI: Using IOAPIC for interrupt routing
[   13.918336] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.918345] PCI: Probing PCI hardware (bus 00)
[   13.918853] PCI: Transparent bridge - 0000:00:04.0
[   13.919037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.919219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   13.919334] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   13.919420] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[   13.919506] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[   13.926028] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11
[   13.926218] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[   13.926406] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   13.926593] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[   13.926781] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[   13.926968] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   13.927161] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[   13.927385] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   13.927575] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11
[   13.927763] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[   13.927951] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[   13.928139] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[   13.928327] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[   13.928515] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *11
[   13.928703] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[   13.928891] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[   13.929079] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *15
[   13.929267] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[   13.929491] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   13.929574] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.929583] pnp: PnP ACPI init
[   13.929592] ACPI: bus type pnp registered
[   13.935550] pnp: PnP ACPI: found 16 devices
[   13.935552] ACPI: ACPI bus type pnp unregistered
[   13.935604] PCI: Using ACPI for IRQ routing
[   13.935606] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.935668] NET: Registered protocol family 8
[   13.935670] NET: Registered protocol family 20
[   13.935731] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   13.935735] hpet0: 3 32-bit timers, 25000000 Hz
[   13.936789] pnp: 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   13.936792] pnp: 00:07: iomem range 0xfefe1000-0xfefe1fff has been reserved
[   13.936795] pnp: 00:07: iomem range 0xfee01000-0xfeefffff has been reserved
[   13.936798] pnp: 00:07: iomem range 0xffb80000-0xffffffff could not be reserved
[   13.936804] pnp: 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[   13.936807] pnp: 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   13.936810] pnp: 00:09: iomem range 0x78000000-0x7fffffff has been reserved
[   13.936815] pnp: 00:0c: ioport range 0x230-0x23f has been reserved
[   13.936818] pnp: 00:0c: ioport range 0x290-0x29f has been reserved
[   13.936820] pnp: 00:0c: ioport range 0xa00-0xa0f has been reserved
[   13.936823] pnp: 00:0c: ioport range 0xa10-0xa1f has been reserved
[   13.936828] pnp: 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   13.936833] pnp: 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   13.936835] pnp: 00:0f: iomem range 0xc0000-0xcffff has been reserved
[   13.936838] pnp: 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   13.936841] pnp: 00:0f: iomem range 0x100000-0x77ffffff could not be reserved
[   13.937088] PCI: Bridge: 0000:00:04.0
[   13.937090]   IO window: disabled.
[   13.937094]   MEM window: dff00000-dfffffff
[   13.937096]   PREFETCH window: disabled.
[   13.937099] PCI: Bridge: 0000:00:09.0
[   13.937100]   IO window: disabled.
[   13.937101]   MEM window: disabled.
[   13.937103]   PREFETCH window: disabled.
[   13.937105] PCI: Bridge: 0000:00:0b.0
[   13.937106]   IO window: disabled.
[   13.937108]   MEM window: disabled.
[   13.937110]   PREFETCH window: disabled.
[   13.937112] PCI: Bridge: 0000:00:0c.0
[   13.937113]   IO window: disabled.
[   13.937115]   MEM window: disabled.
[   13.937116]   PREFETCH window: disabled.
[   13.937125] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   13.937132] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   13.937137] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   13.937142] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   13.937186] NET: Registered protocol family 2
[   13.939049] Time: hpet clocksource has been installed.
[   13.983344] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   13.984025] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   13.987728] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   13.988341] TCP: Hash tables configured (established 262144 bind 65536)
[   13.988345] TCP reno registered
[   14.003389] checking if image is initramfs... it is
[   14.532178] Freeing initrd memory: 7724k freed
[   14.537110] audit: initializing netlink socket (disabled)
[   14.537125] audit(1193911946.728:1): initialized
[   14.539020] VFS: Disk quotas dquot_6.5.1
[   14.539065] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   14.539140] io scheduler noop registered
[   14.539142] io scheduler anticipatory registered
[   14.539144] io scheduler deadline registered
[   14.539224] io scheduler cfq registered (default)
[   14.978944] Boot video device is 0000:00:0d.0
[   14.979088] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   14.979106] assign_interrupt_mode Found MSI capability
[   14.979109] Allocate Port Service[0000:00:09.0:pcie00]
[   14.979168] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   14.979185] assign_interrupt_mode Found MSI capability
[   14.979187] Allocate Port Service[0000:00:0b.0:pcie00]
[   14.979238] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   14.979255] assign_interrupt_mode Found MSI capability
[   14.979257] Allocate Port Service[0000:00:0c.0:pcie00]
[   15.003119] Real Time Clock Driver v1.12ac
[   15.003300] hpet_resources: 0xfed00000 is busy
[   15.003329] Linux agpgart interface v0.102 (c) Dave Jones
[   15.003332] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.003426] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.004022] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.004695] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.004816] input: Macintosh mouse button emulation as /class/input/input0
[   15.004891] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   15.005212] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.005216] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.005359] mice: PS/2 mouse device common for all mice
[   15.005475] TCP cubic registered
[   15.005528] NET: Registered protocol family 1
[   15.005710] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   15.005721] Freeing unused kernel memory: 296k freed
[   15.034567] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.180440] AppArmor: AppArmor initialized<5>audit(1193911948.376:2):  type=1505 info="AppArmor initialized" pid=1235
[   16.186470] fuse init (API version 7.8)
[   16.190355] Failure registering capabilities with primary security module.
[   16.663081] usbcore: registered new interface driver usbfs
[   16.663105] usbcore: registered new interface driver hub
[   16.663126] usbcore: registered new device driver usb
[   16.663792] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.664135] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[   16.664146] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 23 (level, low) -> IRQ 23
[   16.664313] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   16.664319] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   16.664491] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   16.664509] ohci_hcd 0000:00:02.0: irq 23, io mem 0xdfeff000
[   16.704799] SCSI subsystem initialized
[   16.709830] libata version 2.21 loaded.
[   16.713661] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   16.717359] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.717365] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.745368] usb usb1: configuration #1 chosen from 1 choice
[   16.745393] hub 1-0:1.0: USB hub found
[   16.745402] hub 1-0:1.0: 8 ports detected
[   16.766396] Floppy drive(s): fd0 is 1.44M
[   16.796075] FDC 0 is a post-1991 82077
[   16.850046] sata_nv 0000:00:08.0: version 3.4
[   16.850382] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[   16.850392] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LSA0] -> GSI 22 (level, low) -> IRQ 22
[   16.850603] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   16.850734] scsi0 : sata_nv
[   16.851684] scsi1 : sata_nv
[   16.851773] ata1: SATA max UDMA/133 cmd 0x000000000001e400 ctl 0x000000000001e082 bmdma 0x000000000001d880 irq 22
[   16.851777] ata2: SATA max UDMA/133 cmd 0x000000000001e000 ctl 0x000000000001dc02 bmdma 0x000000000001d888 irq 22
[   17.321458] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   17.383622] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
[   17.383625] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   17.458554] ata1.00: configured for UDMA/133
[   17.773244] ata2: SATA link down (SStatus 0 SControl 300)
[   17.783593] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
[   17.785856] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[   17.785867] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LMAC] -> GSI 21 (level, low) -> IRQ 21
[   17.785873] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   17.785881] forcedeth: using HIGHDMA
[   18.309592] eth0: forcedeth.c: subsystem: 01043:8234 bound to 0000:00:07.0
[   18.309729] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
[   18.309746] NFORCE-MCP61: chipset revision 162
[   18.309748] NFORCE-MCP61: not 100% native mode: will probe irqs later
[   18.309752] NFORCE-MCP61: BIOS didn't set cable bits correctly. Enabling workaround.
[   18.309756] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
[   18.309764]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[   18.309772] Probing IDE interface ide0...
[   18.713177] hda: SONY DVD RW DRU-720A, ATAPI CD/DVD-ROM drive
[   18.997044] hdb: ST380011A, ATA DISK drive
[   19.058046] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   19.063265] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 20
[   19.063277] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 20 (level, low) -> IRQ 20
[   19.063426] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   19.063433] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   19.063707] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   19.063734] ehci_hcd 0000:00:02.1: debug port 1
[   19.063738] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   19.063749] ehci_hcd 0000:00:02.1: irq 20, io mem 0xdfefec00
[   19.063756] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.064088] usb usb2: configuration #1 chosen from 1 choice
[   19.064243] hub 2-0:1.0: USB hub found
[   19.064249] hub 2-0:1.0: 8 ports detected
[   19.175428] hdb: max request size: 512KiB
[   19.176648] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   19.176816] hdb: cache flushes supported
[   19.176868]  hdb:
[   19.184645] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[   19.184656] Uniform CD-ROM driver Revision: 3.20
[   19.189211] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   19.192598] sd 0:0:0:0: [sda] Write Protect is off
[   19.192601] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.194320] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.196070] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   19.196589] sd 0:0:0:0: [sda] Write Protect is off
[   19.196591] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.197253] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.197256]  sda: sda1 sda2 sda3
[   19.232985] sd 0:0:0:0: [sda] Attached SCSI disk
[   19.236072] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.612235] Attempting manual resume
[   19.612238] swsusp: Resume From Partition 8:2
[   19.612240] PM: Checking swsusp image.
[   19.612439] PM: Resume from disk failed.
[   19.645738] kjournald starting.  Commit interval 5 seconds
[   19.645748] EXT3-fs: mounted filesystem with ordered data mode.
[   26.308065] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   26.308097] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   26.382227] nvidia: module license 'NVIDIA' taints kernel.
[   26.636979] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.638481] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 23
[   26.638486] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LMC9] -> GSI 23 (level, low) -> IRQ 23
[   26.638493] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   26.638660] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   26.667520] shpchp: Unknown symbol acpi_run_oshp
[   26.667572] shpchp: Unknown symbol pci_hp_change_slot_info
[   26.667632] shpchp: Unknown symbol pci_hp_register
[   26.667787] shpchp: Unknown symbol pci_hp_deregister
[   26.667913] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   26.671629] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.746491] Linux video capture interface: v2.00
[   26.883124] saa7130/34: v4l2 driver version 0.2.14 loaded
[   26.883523] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[   26.883532] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [LNKA] -> GSI 19 (level, low) -> IRQ 19
[   26.883539] saa7130[0]: found at 0000:01:06.0, rev: 1, irq: 19, latency: 64, mmio: 0xdffffc00
[   26.883545] saa7130[0]: subsystem: 1131:2005, board: UNKNOWN/GENERIC [card=0,autodetected]
[   26.883553] saa7130[0]: board init: gpio is 131ff
[   27.030762] saa7130[0]: i2c eeprom 00: 31 11 05 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   27.030772] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[   27.030779] saa7130[0]: i2c eeprom 20: 54 05 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[   27.030785] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.030792] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.030798] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.030805] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.030812] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.030907] saa7130[0]: registered device video0 [v4l2]
[   27.030937] saa7130[0]: registered device vbi0
[   27.043799] saa7134 ALSA driver for DMA sound loaded
[   27.043832] saa7130[0]/alsa: saa7130[0] at 0xdffffc00 irq 19 registered as card -2
[   27.157874] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   27.157879] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [LAZA] -> GSI 22 (level, low) -> IRQ 22
[   27.158112] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   27.368745] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   27.400213] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[   27.403666] parport_pc 00:06: reported by Plug and Play ACPI
[   27.403712] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   27.404641] input: PC Speaker as /class/input/input3
[   28.496338] lp0: using parport0 (interrupt-driven).
[   28.559476] Adding 2931852k swap on /dev/sda2.  Priority:-1 extents:1 across:2931852k
[   28.831895] EXT3 FS on sda1, internal journal
[   29.381141] kjournald starting.  Commit interval 5 seconds
[   29.380982] EXT3 FS on sda3, internal journal
[   29.380988] EXT3-fs: mounted filesystem with ordered data mode.
[   29.987254] PPP generic driver version 2.4.2
[   30.052101] NET: Registered protocol family 10
[   30.052191] lo: Disabled Privacy Extensions
[   30.500284] No dock devices found.
[   30.506294] input: Power Button (FF) as /class/input/input4
[   30.506315] ACPI: Power Button (FF) [PWRF]
[   30.506379] input: Power Button (CM) as /class/input/input5
[   30.506395] ACPI: Power Button (CM) [PWRB]
[   30.836495] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (version 2.00.00)
[   30.836791] powernow-k8: MP systems not supported by PSB BIOS structure
[   30.836530] powernow-k8: MP systems not supported by PSB BIOS structure
[   31.932624] eth0: no link during initialization.
[   31.934663] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.962751] ppdev: user-space parallel port driver
[   32.088877] audit(1193911964.741:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5057 profile="/usr/sbin/cupsd"
[   35.309119] Failure registering capabilities with primary security module.
[   35.474390] Bluetooth: Core ver 2.11
[   35.474503] NET: Registered protocol family 31
[   35.474506] Bluetooth: HCI device and connection manager initialized
[   35.474509] Bluetooth: HCI socket layer initialized
[   35.485641] Bluetooth: L2CAP ver 2.8
[   35.485646] Bluetooth: L2CAP socket layer initialized
[   35.534068] Bluetooth: RFCOMM socket layer initialized
[   35.534140] Bluetooth: RFCOMM TTY layer initialized
[   35.534142] Bluetooth: RFCOMM ver 1.8
[ 1151.987548] eth0: no link during initialization.
[ 1151.989615] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1198.397004] PPP BSD Compression module registered
[ 1198.436559] PPP Deflate Compression module registered
[ 4542.068666] saa7134 ALSA driver for DMA sound unloaded
[ 4682.156737] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 4682.156788] saa7130[0]: found at 0000:01:06.0, rev: 1, irq: 19, latency: 64, mmio: 0xdffffc00
[ 4682.156794] saa7130[0]: subsystem: 1131:2005, board: UNKNOWN/GENERIC [card=0,insmod option]
[ 4682.156803] saa7130[0]: board init: gpio is 131ff
[ 4682.291399] saa7130[0]: i2c eeprom 00: 31 11 05 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[ 4682.291411] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[ 4682.291424] saa7130[0]: i2c eeprom 20: 54 05 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[ 4682.291436] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4682.291442] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4682.291448] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4682.291457] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4682.291469] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4682.331357] tuner 2-0060: All bytes are equal. It is not a TEA5767
[ 4682.331365] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
[ 4682.331405] tuner 2-0060: type set to 55 (TCL 2002MB)
[ 4682.331409] tuner 2-0060: type set to 55 (TCL 2002MB)
[ 4682.333860] saa7130[0]: registered device video0 [v4l2]
[ 4682.333879] saa7130[0]: registered device vbi0
[ 4682.347156] saa7134 ALSA driver for DMA sound loaded
[ 4682.347189] saa7130[0]/alsa: saa7130[0] at 0xdffffc00 irq 19 registered as card -2
[ 4816.798797] saa7134 ALSA driver for DMA sound unloaded
[ 4846.579955] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 4846.581769] saa7130[0]: found at 0000:01:06.0, rev: 1, irq: 19, latency: 64, mmio: 0xdffffc00
[ 4846.581778] saa7130[0]: subsystem: 1131:2005, board: UNKNOWN/GENERIC [card=0,autodetected]
[ 4846.581789] saa7130[0]: board init: gpio is 131ff
[ 4846.707814] tuner 2-0060: All bytes are equal. It is not a TEA5767
[ 4846.707820] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
[ 4846.708301] tuner 2-0060: type set to 55 (TCL 2002MB)
[ 4846.708305] tuner 2-0060: type set to 55 (TCL 2002MB)
[ 4846.744852] saa7130[0]: i2c eeprom 00: 31 11 05 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[ 4846.744863] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[ 4846.744870] saa7130[0]: i2c eeprom 20: 54 05 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[ 4846.744876] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4846.744882] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4846.744887] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4846.744893] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4846.744899] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4846.749762] saa7130[0]: registered device video0 [v4l2]
[ 4846.749843] saa7130[0]: registered device vbi0
[ 4846.782905] saa7134 ALSA driver for DMA sound loaded
[ 4846.782939] saa7130[0]/alsa: saa7130[0] at 0xdffffc00 irq 19 registered as card -2
[ 5196.085524] saa7134 ALSA driver for DMA sound unloaded
[ 5223.718756] card: expects arguments
[ 5223.718765] saa7134: `' invalid for parameter `card'
[ 5435.843596] card: expects arguments
[ 5435.843604] saa7134: `' invalid for parameter `card'
[ 5458.157403] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 5458.159456] saa7130[0]: found at 0000:01:06.0, rev: 1, irq: 19, latency: 64, mmio: 0xdffffc00
[ 5458.159465] saa7130[0]: subsystem: 1131:2005, board: UNKNOWN/GENERIC [card=0,autodetected]
[ 5458.159475] saa7130[0]: board init: gpio is 131ff
[ 5458.280750] tuner 2-0060: All bytes are equal. It is not a TEA5767
[ 5458.280756] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
[ 5458.316746] saa7130[0]: i2c eeprom 00: 31 11 05 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[ 5458.316755] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[ 5458.316761] saa7130[0]: i2c eeprom 20: 54 05 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[ 5458.316767] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5458.316773] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5458.316779] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5458.316784] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5458.316790] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 5458.317981] saa7130[0]: registered device video0 [v4l2]
[ 5458.318552] saa7130[0]: registered device vbi0
[ 5458.348209] saa7134 ALSA driver for DMA sound loaded
[ 5458.348492] saa7130[0]/alsa: saa7130[0] at 0xdffffc00 irq 19 registered as card -2
 
```

Is there anyone who could help me with finding out what to do to fix this? Is this a problem with my card, it was autodetected in Ubuntu. ive tried quite a few threads on troubleshooting this so if anyone could help me . I would deeply appreciate it.

Thanks in advance.
Biju

---

### Post by BijuMathew on 2007-11-01
Well Ive managed somehow to get a picture but now I cant hear any Audio from it. Ive checked the Volume Control for 3 different sound devices. SAA7134, HDA nVidia, Realtek ALC662 rev2 and all three of them dont have a Capture tab. I checked the Edit Preferences and made sure that Capture was selected. I cant find a capture tab but I was able to find a recording tab. Ive made sure that every single thing is set to max volume and not muted. Not sure what im doing wrong here. :confused:

---

### Post by BijuMathew on 2007-11-02
Just if it helps anyone out there. I did

sudo rmmod saa7134_alsa
sudo rmmod saa7134

Then 
sudo modprobe saa7134_alsa
sudo modprobe saa7134 card=3 tuner=69
tvtime

This is how I got Video but I dont have sound :(

---

### Post by BijuMathew on 2007-11-03
Well as another update I tried Virtualbox to install WIndows XP to see if I could install the driver and Application to view TV in it and that too fail. (Managed to get Windows XP going but the drivers couldnt start the device. I knew it wouldnt work but just had to try ) I guess I might just buy another Tv Tuner Card :( .

---

### Post by Kuptis on 2007-11-03
I've got an onboard Realtek ALC662 HD audio chip and I haven't been able to get it to work yet.  I get video no problem; just no sound.

---

### Post by BijuMathew on 2007-11-03
> I've got an onboard Realtek ALC662 HD audio chip and I haven't been able to get it to work yet. I get video no problem; just no sound.  

Hold on a second. I have the same thing! Doi you have a capture tab in your Volume Control? Ive heard alot of folks talking about it but even after enabling pretty much every option in my Volume Control I get no Capture Tab. 

Maybe its a problem with the Audio driver then? I can run the test button for everythign other than one of the buttons. I think it was the last test button and it gave me some kind of weird script error. Im not on my Linux system so cant reproduce at the moment. What are your Tv Tuner card settings? Are they 3 and 69 like I did above?

---

### Post by Kuptis on 2007-11-03
I don't have a TV tuner card.

I don't have a Capture tab.  When I right-click the speaker icon and then click "Open Volume Control" it gives me a error message saying "No volume control GStreamer plugins and/or devices found."

I downloaded the audio drivers from the Realtek web site and it does a whole lot of things but at the very end it tells me:

```
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
./install: 100: alsaconf: not found
```I just noticed that it says it needs a curses library.  I'll guess I'll research that next.

Also, here's my lspci output:
```
root@kuptis:/# lspci 
00:00.0 Host bridge: nVidia Corporation Unknown device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation Unknown device 07e3 (rev a2)
01:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
```I wonder if the problem is that on almost everything it says unknown device although my USB, network cards, memory, etc. do work.

Running lshw gives me this for audio.  Was the only "audio" I found.
```
        *-multimedia UNCLAIMED
             description: Audio device
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0 maxlatency=5 mingnt=2
```I just found a [link]("http://ubuntuforums.org/showthread.php?t=195434") to something similar so will try that also.

---

### Post by BijuMathew on 2007-11-03
I dont event think its a problem with my Tv Tuner any more. in fact I cant use the Line in at all. Suddenly it makes me think that there might be something the way Volume is configured. alsamixer by default on my system seems to be 1.0.14 . I think I might have luck installing 1.0.15 which is avilable on alsa's website. i think there aer three files you need to download. Theres a thread on the board with installation instructions a couple of folks have been having luck installing that. I would recommend trying that before the realtek patch :) . Ive so far checked google, #ubuntu on freenode, here on the forums and linuxquestions.org. :mad: something tells me that its something I might have overlooked .

its kind of late here at the moment. Will try the patch and see if it solves my issue. if it does Ill let ya know here :)

Hope this helps.

---

### Post by Kuptis on 2007-11-03
Considering that a few messages have stated no devices found I wonder if for some reason Linux is not seeing the audio chip.

---

### Post by Kuptis on 2007-11-03
For anybody who happens upon this thread:
In order to get the onboard Realtek ALC662 sound on a Biostar GF7050V-M7 motherboard to work I ended up following this [thread]("http://ubuntuforums.org/showthread.php?t=187156") and, instead of the 2.6.16 as it suggests, I used the 2.6.23.1 kernel from [http://www.kernel.org](http://www.kernel.org).

This at least got me to the point that Linux "saw" my sound chip.  I then downloaded and installed the audio drivers from [Realtek]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false").  Before the kernel update and the driver install Linux wouldn't detect/"see" my sound chip which wouldn't let me use the volume controls.  Afterwards, both now work and I'm happy to have sound.

---

### Post by BijuMathew on 2007-11-05
Well confirmed today that it might not even be a problem with my Tv Tuner. But I think that it might be a problem with my Audio card. I cant get Line in to record any sound. Hooked myIpod and found that there is no sound. Also it has a line HDA Codec Unkown ALC662 in there . Anyone any idea on how to fix this. I ran the alsa1.0.15 upgrade and totally lost sound at this point .

---

### Post by BijuMathew on 2007-11-08
Well finally got the Line in to work for my Realtek Audio ALC662 onboard sound. Folowed the instructions here in the How to troubleshoot sound thread with some minor modifactions which were posted on linuxquestions.org

Now just to find the correct card and tuner option for my tv tuner.

---

