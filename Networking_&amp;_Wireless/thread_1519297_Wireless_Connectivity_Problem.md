---
title: "Wireless Connectivity Problem"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by RCasiU on 2010-06-27
Hi,
 
I am trying to set up Linux Ubuntu 10.04 for the first time and I am having a problem with my usb wireless adapter. The adapter doesn't light up at all, so it seems like Ubuntu isn't recognizing it. Below you will find all the information that you may need:
 
**[COLOR=black]1.[/COLOR]** Dell Dimension 2400
 
**2.** Belkin Wireless N USB Adapter Model F5D8053 v6
 
**3.**  [EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:29:2f:4c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)
[EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] 
 
[EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
[EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] 
 
**4.** [EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
vga16fb                11385  1 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vgastate                8961  1 vga16fb
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  1 
drm_kms_helper         29297  1 i915
ppdev                   5259  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
dell_wmi                1793  0 
drm                   162471  3 i915,drm_kms_helper
dcdbas                  5422  0 
i2c_algo_bit            5028  1 i915
intel_agp              24177  2 i915
psmouse                63245  0 
lp                      7028  0 
soundcore               6620  1 snd
video                  17375  1 i915
hid_logitech            7388  0 
shpchp                 28820  0 
serio_raw               3978  0 
agpgart                31724  3 drm,intel_agp
output                  1871  1 video
joydev                  8708  0 
ff_memless              4093  1 hid_logitech
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  1 hid_logitech
b44                    25542  0 
usb_storage            39425  2 
hid                    67032  2 hid_logitech,usbhid
ssb                    37336  1 b44
mii                     4381  1 b44
floppy                 53016  0 
[EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] 
 
**5.** [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000b77d000 - 000bf16919]          RAMDISK ==> [000b77d000 - 000bf16919]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd1c4]              BRK ==> [00008da000 - 00008dd1c4]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000a000]          BOOTMAP ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fe74
[    0.000000]   HighMem  0x0000fe74 -> 0x0000fe74
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0000fe74
[    0.000000] On node 0 totalpages: 65040
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 477 pages used for memmap
[    0.000000]   Normal zone: 60567 pages, LIFO batch:15
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at ff00000 (gap: ff00000:eed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36024 r0 d21320 u1048576
[    0.000000] pcpu-alloc: s36024 r0 d21320 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64531
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=ce3442f8-7889-454a-b75b-6a9f402f633a ro quiet splash
[    0.000000] PID hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1302800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 240196k/260560k available (4673k kernel code, 19640k reserved, 2122k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd0674000 - 0xff7fe000   ( 753 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xcfe74000   ( 254 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2392.177 MHz processor.
[    0.008009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4784.35 BogoMIPS (lpj=9568708)
[    0.008045] Security Framework initialized
[    0.008085] AppArmor: AppArmor initialized
[    0.008108] Mount-cache hash table entries: 512
[    0.008411] Initializing cgroup subsys ns
[    0.008424] Initializing cgroup subsys cpuacct
[    0.008433] Initializing cgroup subsys memory
[    0.008446] Initializing cgroup subsys devices
[    0.008452] Initializing cgroup subsys freezer
[    0.008456] Initializing cgroup subsys net_cls
[    0.008509] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.008516] CPU: L2 cache: 128K
[    0.008520] CPU: Hyper-Threading is disabled
[    0.008527] mce: CPU supports 4 MCE banks
[    0.008544] CPU0: Thermal monitoring enabled (TM1)
[    0.008565] Performance Events: no PMU driver, software events only.
[    0.008579] Checking 'hlt' instruction... OK.
[    0.025172] SMP alternatives: switching to UP code
[    0.038217] ACPI: Core revision 20090903
[    0.074598] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.074613] ftrace: allocating 21771 entries in 43 pages
[    0.076176] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.076498] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.116860] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 09
[    0.120001] Brought up 1 CPUs
[    0.120001] Total of 1 processors activated (4784.35 BogoMIPS).
[    0.120001] CPU0 attaching NULL sched-domain.
[    0.120001] devtmpfs: initialized
[    0.120001] regulator: core version 0.5
[    0.120001] Time: 11:47:50  Date: 06/27/10
[    0.120001] NET: Registered protocol family 16
[    0.120001] EISA bus registered
[    0.120001] ACPI: bus type pci registered
[    0.120001] PCI: PCI BIOS revision 2.10 entry at 0xfbbbf, last bus=1
[    0.120001] PCI: Using configuration type 1 for base access
[    0.120538] bio: create slab <bio-0> at 0
[    0.121336] ACPI: EC: Look up EC in DSDT
[    0.151072] ACPI: Interpreter enabled
[    0.151093] ACPI: (supports S0 S1 S3 S4 S5)
[    0.151136] ACPI: Using IOAPIC for interrupt routing
[    0.186659] ACPI: No dock devices found.
[    0.188297] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.188398] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.188498] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.188507] pci 0000:00:02.0: reg 14 32bit mmio: [0xfeb80000-0xfebfffff]
[    0.188638] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.188704] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.188770] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.188844] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]
[    0.188912] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.188919] pci 0000:00:1d.7: PME# disabled
[    0.188982] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.188984] * this clock source is slow. If you are sure your timer does not have
[    0.188986] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.189039] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.189045] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.189077] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.189086] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.189095] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.189103] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.189112] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.189121] pci 0000:00:1f.1: reg 24 32bit mmio: [0xfeb7fc00-0xfeb7ffff]
[    0.189184] pci 0000:00:1f.3: reg 20 io port: [0xeda0-0xedbf]
[    0.189239] pci 0000:00:1f.5: reg 10 io port: [0xee00-0xeeff]
[    0.189247] pci 0000:00:1f.5: reg 14 io port: [0xedc0-0xedff]
[    0.189256] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfeb7fa00-0xfeb7fbff]
[    0.189264] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfeb7f900-0xfeb7f9ff]
[    0.189300] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.189306] pci 0000:00:1f.5: PME# disabled
[    0.189371] pci 0000:01:09.0: reg 10 32bit mmio: [0xfe9fe000-0xfe9fffff]
[    0.189404] pci 0000:01:09.0: reg 30 32bit mmio pref: [0xfea00000-0xfea03fff]
[    0.189425] pci 0000:01:09.0: supports D1 D2
[    0.189428] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.189433] pci 0000:01:09.0: PME# disabled
[    0.189470] pci 0000:00:1e.0: transparent bridge
[    0.189479] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe900000-0xfeafffff]
[    0.189493] pci_bus 0000:00: on NUMA node 0
[    0.189506] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.189926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.355146] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.355547] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.356138] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.356526] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.356910] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.357290] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.357675] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.358064] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.358358] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.358375] vgaarb: loaded
[    0.358648] SCSI subsystem initialized
[    0.358849] libata version 3.00 loaded.
[    0.359090] usbcore: registered new interface driver usbfs
[    0.359120] usbcore: registered new interface driver hub
[    0.359237] usbcore: registered new device driver usb
[    0.359690] ACPI: WMI: Mapper loaded
[    0.359696] PCI: Using ACPI for IRQ routing
[    0.359947] NetLabel: Initializing
[    0.359953] NetLabel:  domain hash size = 128
[    0.359955] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.359977] NetLabel:  unlabeled traffic allowed by default
[    0.360121] Switching to clocksource tsc
[    0.363831] AppArmor: AppArmor Filesystem Enabled
[    0.363880] pnp: PnP ACPI init
[    0.363917] ACPI: bus type pnp registered
[    0.386722] pnp 00:09: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.386730] pnp 00:09: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.387620] pnp: PnP ACPI: found 10 devices
[    0.387627] ACPI: ACPI bus type pnp unregistered
[    0.387634] PnPBIOS: Disabled by ACPI PNP
[    0.387664] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.387670] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    0.387674] system 00:00: iomem range 0x1000000-0xfe73fff could not be reserved
[    0.387679] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
[    0.387685] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.387690] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.387695] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
[    0.387699] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.387704] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
[    0.387751] system 00:09: ioport range 0xc00-0xc7f has been reserved
[    0.422825] pci 0000:01:09.0: BAR 6: address space collision on of device [0xfea00000-0xfea03fff]
[    0.422852] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.422855] pci 0000:00:1e.0:   IO window: disabled
[    0.422863] pci 0000:00:1e.0:   MEM window: 0xfe900000-0xfeafffff
[    0.422870] pci 0000:00:1e.0:   PREFETCH window: 0x10000000-0x100fffff
[    0.422892] pci 0000:00:1e.0: setting latency timer to 64
[    0.422899] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.422905] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.422909] pci_bus 0000:01: resource 1 mem: [0xfe900000-0xfeafffff]
[    0.422913] pci_bus 0000:01: resource 2 pref mem [0x10000000-0x100fffff]
[    0.422916] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.422919] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.422989] NET: Registered protocol family 2
[    0.423170] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.423626] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.423689] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.423820] TCP: Hash tables configured (established 8192 bind 8192)
[    0.423826] TCP reno registered
[    0.424080] NET: Registered protocol family 1
[    0.424124] pci 0000:00:02.0: Boot video device
[    0.424370] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    0.424376] Simple Boot Flag at 0x7a set to 0x1
[    0.424542] cpufreq-nforce2: No nForce2 chipset.
[    0.424610] Scanning for low memory corruption every 60 seconds
[    0.424897] audit: initializing netlink socket (disabled)
[    0.424923] type=2000 audit(1277639269.423:1): initialized
[    0.434554] Trying to unpack rootfs image as initramfs...
[    0.448346] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.451023] VFS: Disk quotas dquot_6.5.2
[    0.451165] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.452615] fuse init (API version 7.13)
[    0.452875] msgmni has been set to 469
[    0.456352] alg: No test for stdrng (krng)
[    0.456545] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.456553] io scheduler noop registered
[    0.456556] io scheduler anticipatory registered
[    0.456559] io scheduler deadline registered
[    0.456651] io scheduler cfq registered (default)
[    0.456864] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.456914] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.457083] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.457097] ACPI: Power Button [VBTN]
[    0.457203] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.457210] ACPI: Power Button [PWRF]
[    0.457648] processor LNXCPU:00: registered as cooling_device0
[    0.515779] isapnp: Scanning for PnP cards...
[    0.524261] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.524420] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.525144] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.527710] brd: module loaded
[    0.576810] loop: module loaded
[    0.577078] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.577303] ata_piix 0000:00:1f.1: version 2.13
[    0.577332]   alloc irq_desc for 18 on node -1
[    0.577336]   alloc kstat_irqs on node -1
[    0.577348] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.577427] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.579955] scsi0 : ata_piix
[    0.580260] scsi1 : ata_piix
[    0.580361] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.580367] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.581212] Fixed MDIO Bus: probed
[    0.581311] PPP generic driver version 2.4.2
[    0.581479] tun: Universal TUN/TAP device driver, 1.6
[    0.581485] tun: (C) 1999-2004 Max Krasnyansky <[EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL]>
[    0.581756] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.581810]   alloc irq_desc for 23 on node -1
[    0.581815]   alloc kstat_irqs on node -1
[    0.581828] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.581857] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.581863] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.581998] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.582049] ehci_hcd 0000:00:1d.7: debug port 1
[    0.585929] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.592335] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[    0.611889] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.612175] usb usb1: configuration #1 chosen from 1 choice
[    0.612246] hub 1-0:1.0: USB hub found
[    0.612273] hub 1-0:1.0: 6 ports detected
[    0.612393] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.612427] uhci_hcd: USB Universal Host Controller Interface driver
[    0.612518]   alloc irq_desc for 16 on node -1
[    0.612523]   alloc kstat_irqs on node -1
[    0.612536] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.612553] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.612558] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.612709] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.612764] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    0.612996] usb usb2: configuration #1 chosen from 1 choice
[    0.613063] hub 2-0:1.0: USB hub found
[    0.613087] hub 2-0:1.0: 2 ports detected
[    0.613185]   alloc irq_desc for 19 on node -1
[    0.613191]   alloc kstat_irqs on node -1
[    0.613204] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.613218] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.613223] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.613357] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.613410] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    0.613633] usb usb3: configuration #1 chosen from 1 choice
[    0.613700] hub 3-0:1.0: USB hub found
[    0.613726] hub 3-0:1.0: 2 ports detected
[    0.613835] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.613852] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.613858] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.613982] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.614047] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.614290] usb usb4: configuration #1 chosen from 1 choice
[    0.614355] hub 4-0:1.0: USB hub found
[    0.614384] hub 4-0:1.0: 2 ports detected
[    0.614591] PNP: No PS/2 controller found. Probing ports directly.
[    0.621578] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.621597] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.622040] mice: PS/2 mouse device common for all mice
[    0.628093] rtc_cmos 00:05: RTC can wake from S4
[    0.628253] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.628294] rtc0: alarms up to one day, 242 bytes nvram
[    0.628549] device-mapper: uevent: version 1.0.3
[    0.628896] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.629114] device-mapper: multipath: version 1.1.0 loaded
[    0.629121] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.629487] EISA: Probing bus 0 at eisa.0
[    0.629529] EISA: Detected 0 cards.
[    0.631953] cpuidle: using governor ladder
[    0.631960] cpuidle: using governor menu
[    0.632772] TCP cubic registered
[    0.633092] NET: Registered protocol family 10
[    0.633974] lo: Disabled Privacy Extensions
[    0.634512] NET: Registered protocol family 17
[    0.634652] Using IPI No-Shortcut mode
[    0.634952] PM: Resume from disk failed.
[    0.634985] registered taskstats version 1
[    0.635242]   Magic number: 14:430:783
[    0.635352] rtc_cmos 00:05: setting system clock to 2010-06-27 11:47:50 UTC (1277639270)
[    0.635358] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.635361] EDD information not available.
[    0.784770] ata2.00: ATAPI: HL-DT-ST GCE-8483B, B105, max UDMA/33
[    0.784951] ata1.00: ATA-6: WDC WD400BB-75JHC0, 06.01C06, max UDMA/100
[    0.784956] ata1.00: 78125000 sectors, multi 8: LBA 
[    0.785575] ata2.00: configured for UDMA/33
[    0.792379] ata1.00: configured for UDMA/100
[    0.951642] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.159867] usb 1-2: configuration #1 chosen from 1 choice
[    1.215691] isapnp: No Plug & Play device found
[    1.216002] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-75JH 06.0 PQ: 0 ANSI: 5
[    1.216398] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.217104] sd 0:0:0:0: [sda] 78125000 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.217262] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8483B  B105 PQ: 0 ANSI: 5
[    1.218010] sd 0:0:0:0: [sda] Write Protect is off
[    1.218018] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.218220] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.219249]  sda:sr0: scsi3-mmc drive: 40x/48x writer cd/rw xa/form2 cdda tray
[    1.220728] Uniform CD-ROM driver Revision: 3.20
[    1.221024] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.221183] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.232304] Freeing initrd memory: 7782k freed
[    1.250257]  sda1 sda2 < sda5 sda6 sda7 >
[    1.295468] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.295506] Freeing unused kernel memory: 656k freed
[    1.296710] Write protecting the kernel text: 4676k
[    1.296754] Write protecting the kernel read-only data: 1840k
[    1.347510] udev: starting version 151
[    1.440133] usb 1-5: new high speed USB device using ehci_hcd and address 5
[    1.575233] usb 1-5: configuration #1 chosen from 1 choice
[    1.723889] FDC 0 is a post-1991 82077
[    1.816121] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    1.900246] Initializing USB Mass Storage driver...
[    1.921155]   alloc irq_desc for 17 on node -1
[    1.921161]   alloc kstat_irqs on node -1
[    1.921174] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.925786] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.930380] usbcore: registered new interface driver usb-storage
[    1.930391] USB Mass Storage support registered.
[    1.930828] usb-storage: device found at 2
[    1.930833] usb-storage: waiting for device to settle before scanning
[    1.933410] usbcore: registered new interface driver hiddev
[    1.939122] generic-usb 0003:1058:0404.0001: hiddev96,hidraw0: USB HID v1.10 Device [Western Digital External HDD] on usb-0000:00:1d.7-2/input1
[    1.939220] usbcore: registered new interface driver usbhid
[    1.939628] usbhid: v2.6:USB HID core driver
[    1.980357] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
[    1.980957] b44.c:v2.0
[    1.999512] usb 3-1: configuration #1 chosen from 1 choice
[    2.001783] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:29:2f:4c
[    2.008947] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    2.009894] generic-usb 0003:046D:C51A.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    2.021009] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input4
[    2.023167] generic-usb 0003:046D:C51A.0003: input,hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    2.246049] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    2.260082] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    2.434411] usb 3-2: configuration #1 chosen from 1 choice
[    6.932524] usb-storage: device scan complete
[    6.963713] scsi 2:0:0:0: Direct-Access     WD       2500JB External  0602 PQ: 0 ANSI: 0
[    6.965230] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.968935] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    6.970047] sd 2:0:0:0: [sdb] Write Protect is off
[    6.970054] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    6.970059] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.972302] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.972365]  sdb:
[    6.978237] Adding 720888k swap on /dev/sda7.  Priority:-1 extents:1 across:720888k 
[    6.995836]  sdb1 sdb2 < sdb5 sdb6 >
[    7.032672] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.032731] sd 2:0:0:0: [sdb] Attached SCSI disk
[    7.241985] udev: starting version 151
[    7.962051] intel_rng: FWH not detected
[    8.103262] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.103527] Linux agpgart interface v0.103
[    8.117802] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    8.118088] logitech 0003:046D:C512.0004: input,hidraw3: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2/input0
[    8.157688] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input6
[    8.158264] logitech 0003:046D:C512.0005: input,hidraw4: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2/input1
[    8.304974] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    8.305205] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[    8.307747] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    8.308212] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.323689] lp: driver loaded but no devices found
[    8.743183] dell-wmi: No known WMI GUID found
[    8.749601] [drm] Initialized drm 1.1.0 20060810
[    8.794965] parport_pc 00:08: reported by Plug and Play ACPI
[    8.795086] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[    8.892397] lp0: using parport0 (interrupt-driven).
[    8.908667] ppdev: user-space parallel port driver
[    9.344427] [drm] i915 disabling kernel modesetting for known bad device.
[    9.344471] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.344481] pci 0000:00:02.0: setting latency timer to 64
[    9.392282] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.504752] type=1505 audit(1277639279.369:2):  operation="profile_load" pid=522 name="/sbin/dhclient3"
[    9.505455] type=1505 audit(1277639279.369:3):  operation="profile_load" pid=522 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.505847] type=1505 audit(1277639279.369:4):  operation="profile_load" pid=522 name="/usr/lib/connman/scripts/dhclient-script"
[    9.736578] vga16fb: initializing
[    9.736589] vga16fb: mapped to 0xc00a0000
[    9.737061] fb0: VGA16 VGA frame buffer device
[   10.032056] Console: switching to colour frame buffer device 80x30
[   10.980519] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.980598] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   11.400045] intel8x0_measure_ac97_clock: measured 53266 usecs (2567 samples)
[   11.400051] intel8x0: clocking to 48000
[   12.586783] type=1505 audit(1277639282.448:5):  operation="profile_load" pid=687 name="/usr/share/gdm/guest-session/Xsession"
[   12.596156] type=1505 audit(1277639282.460:6):  operation="profile_replace" pid=690 name="/sbin/dhclient3"
[   12.596909] type=1505 audit(1277639282.460:7):  operation="profile_replace" pid=690 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.597315] type=1505 audit(1277639282.460:8):  operation="profile_replace" pid=690 name="/usr/lib/connman/scripts/dhclient-script"
[   12.813251] type=1505 audit(1277639282.676:9):  operation="profile_load" pid=692 name="/usr/bin/evince"
[   12.822743] type=1505 audit(1277639282.684:10):  operation="profile_load" pid=692 name="/usr/bin/evince-previewer"
[   12.843378] type=1505 audit(1277639282.704:11):  operation="profile_load" pid=692 name="/usr/bin/evince-thumbnailer"
[   12.860519] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.516175] EXT4-fs (sdb5): mounted filesystem with ordered data mode
[   89.610311] EXT4-fs (sda1): mounted filesystem with ordered data mode
[EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] 

**6.** [EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] sudo lshw -C network
[sudo] password for owner: 
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: [EMAIL="pci@0000:01:09.0"]pci@0000:01:09.0[/EMAIL]
       logical name: eth0
       version: 01
       serial: 00:12:3f:29:2f:4c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:fe9fe000-fe9fffff memory:10000000-10003fff(prefetchable)
[EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] 
 
**7.** [EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
[EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL]

**8.** Ubuntu 10.04 LTS

**9.** [EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] uname -mr
2.6.32-21-generic i686
[EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL]

**10.** [EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL] sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
[EMAIL="owner@owner-desktop:~$"]owner@owner-desktop:~$[/EMAIL]
 
I'd appreciate any help on this matter. 
 
Thanks!

---

### Post by RCasiU on 2010-06-28
Bump...

---

### Post by spikoley on 2010-06-30
Whats the output of lspci.  Sorry if its there and I missed it.  There is a lot there!

---

### Post by RCasiU on 2010-07-01
The output of that was number two.

---

