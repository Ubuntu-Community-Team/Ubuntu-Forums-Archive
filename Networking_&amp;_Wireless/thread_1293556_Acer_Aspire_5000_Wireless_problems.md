---
title: "Acer Aspire 5000 Wireless problems"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by solevag on 2009-10-17
Hi 

I have tried every step-by-step solution I can find on the web, but with no luck.
Im a noob.

I have followed the **HOWTO post a Wireless issue (ticket)**

Please help me!

laptop@laptop-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
laptop@laptop-laptop:~$ lsusblaptop@laptop-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:10:d0:5f  
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe10:d05f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:699764 (699.7 KB)  TX bytes:116730 (116.7 KB)
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10544 (10.5 KB)  TX bytes:10544 (10.5 KB)

laptop@laptop-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

laptop@laptop-laptop:~$ 


laptop@laptop-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25872  0 
output                 11008  1 video
acerhk                 33332  0 
sisfb                 251988  1 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
arc4                    9856  2 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
ecb                    10752  2 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
pcmcia                 44748  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
b43                   131484  0 
sis_agp                15360  0 
joydev                 18368  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217592  1 b43
cfg80211               38288  1 mac80211
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
amd64_agp              18184  1 
pcspkr                 10496  0 
input_polldev          11912  1 b43
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
k8temp                 12416  0 
i2c_sis96x             12420  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
agpgart                42696  2 sis_agp,amd64_agp
led_class              12036  1 b43
shpchp                 40212  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                61972  0 
serio_raw              13444  0 
ssb                    41220  1 b43
sis900                 28288  0 
mii                    13312  1 sis900
fbcon                  46112  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
compcache              12876  1 
lzo_decompress         10880  1 compcache
lzo_compress           10880  1 compcache
tlsf                   14092  1 compcache
laptop@laptop-laptop:~$ 

[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0003bef0
[    0.000000] On node 0 totalpages: 245365
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1231000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 150 pages used for memmap
[    0.000000]   HighMem zone: 19036 pages, LIFO batch:3
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243447
[    0.000000] Kernel command line: root=UUID=b7639888-064e-4010-bea3-6dbb69337a27 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1800.100 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 4909760 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 950260k/981952k available (4116k kernel code, 30972k reserved, 2199k data, 532k init, 76744k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05050ff - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05050ff   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 3600.20 BogoMIPS (lpj=7200400)
[    0.004039] Security Framework initialized
[    0.004049] SELinux:  Disabled at boot.
[    0.004079] AppArmor: AppArmor initialized
[    0.004088] Mount-cache hash table entries: 512
[    0.004252] Initializing cgroup subsys ns
[    0.004256] Initializing cgroup subsys cpuacct
[    0.004258] Initializing cgroup subsys memory
[    0.004263] Initializing cgroup subsys freezer
[    0.004278] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004281] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004298] Checking 'hlt' instruction... OK.
[    0.020674] SMP alternatives: switching to UP code
[    0.148336] Freeing SMP alternatives: 18k freed
[    0.148341] ACPI: Core revision 20080926
[    0.149898] ACPI: Checking initramfs for custom DSDT
[    0.567443] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.607133] CPU0: AMD Turion(tm) 64 Mobile Technology ML-32 stepping 02
[    0.608002] Brought up 1 CPUs
[    0.608002] Total of 1 processors activated (3600.20 BogoMIPS).
[    0.608002] CPU0 attaching NULL sched-domain.
[    0.608002] net_namespace: 776 bytes
[    0.608002] Booting paravirtualized kernel on bare hardware
[    0.608002] Time: 11:12:44  Date: 10/17/09
[    0.608002] regulator: core version 0.5
[    0.608002] NET: Registered protocol family 16
[    0.608002] EISA bus registered
[    0.608002] ACPI: bus type pci registered
[    0.608002] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
[    0.608002] PCI: Using configuration type 1 for base access
[    0.608002] ACPI: EC: Look up EC in DSDT
[    0.608651] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.632060] ACPI: Interpreter enabled
[    0.632063] ACPI: (supports S0 S3 S4 S5)
[    0.632078] ACPI: Using IOAPIC for interrupt routing
[    0.637036] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.637039] ACPI: EC: driver started in interrupt mode
[    0.637122] ACPI: No dock devices found.
[    0.637131] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.637181] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe1ffffff]
[    0.637261] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.637288] pci 0000:00:02.1: reg 20 io port: [0x8100-0x811f]
[    0.637311] pci 0000:00:02.5: reg 10 io port: [0x1f0-0x1f7]
[    0.637316] pci 0000:00:02.5: reg 14 io port: [0x3f4-0x3f7]
[    0.637321] pci 0000:00:02.5: reg 18 io port: [0x170-0x177]
[    0.637326] pci 0000:00:02.5: reg 1c io port: [0x374-0x377]
[    0.637331] pci 0000:00:02.5: reg 20 io port: [0x2000-0x200f]
[    0.637358] pci 0000:00:02.6: reg 10 io port: [0x1000-0x10ff]
[    0.637363] pci 0000:00:02.6: reg 14 io port: [0x1c00-0x1c7f]
[    0.637385] pci 0000:00:02.6: supports D1 D2
[    0.637388] pci 0000:00:02.6: PME# supported from D3hot D3cold
[    0.637392] pci 0000:00:02.6: PME# disabled
[    0.637413] pci 0000:00:02.7: reg 10 io port: [0x1400-0x14ff]
[    0.637418] pci 0000:00:02.7: reg 14 io port: [0x1c80-0x1cff]
[    0.637439] pci 0000:00:02.7: supports D1 D2
[    0.637442] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.637445] pci 0000:00:02.7: PME# disabled
[    0.637461] pci 0000:00:03.0: reg 10 32bit mmio: [0xe2002000-0xe2002fff]
[    0.637492] pci 0000:00:03.1: reg 10 32bit mmio: [0xe2003000-0xe2003fff]
[    0.637528] pci 0000:00:03.2: reg 10 32bit mmio: [0xe2004000-0xe2004fff]
[    0.637551] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.637554] pci 0000:00:03.2: PME# disabled
[    0.637579] pci 0000:00:04.0: reg 10 io port: [0x1800-0x18ff]
[    0.637585] pci 0000:00:04.0: reg 14 32bit mmio: [0xe2005000-0xe2005fff]
[    0.637602] pci 0000:00:04.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.637609] pci 0000:00:04.0: supports D1 D2
[    0.637611] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.637614] pci 0000:00:04.0: PME# disabled
[    0.637638] pci 0000:00:06.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.637645] pci 0000:00:06.0: supports D1 D2
[    0.637647] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.637651] pci 0000:00:06.0: PME# disabled
[    0.637669] pci 0000:00:0b.0: reg 10 32bit mmio: [0xe2000000-0xe2001fff]
[    0.637776] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.637780] pci 0000:01:00.0: reg 14 32bit mmio: [0xe2100000-0xe211ffff]
[    0.637784] pci 0000:01:00.0: reg 18 io port: [0xa000-0xa07f]
[    0.637795] pci 0000:01:00.0: supports D1 D2
[    0.637813] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.637817] pci 0000:00:01.0: bridge 32bit mmio: [0xe2100000-0xe21fffff]
[    0.637821] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.637839] bus 00 -> node 0
[    0.637844] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.644202] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[    0.644304] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
[    0.644401] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
[    0.644498] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[    0.644620] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[    0.644717] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[    0.644812] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.644912] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[    0.645037] ACPI: WMI: Mapper loaded
[    0.645203] SCSI subsystem initialized
[    0.645245] libata version 3.00 loaded.
[    0.645290] usbcore: registered new interface driver usbfs
[    0.645308] usbcore: registered new interface driver hub
[    0.645333] usbcore: registered new device driver usb
[    0.645443] PCI: Using ACPI for IRQ routing
[    0.645518] Bluetooth: Core ver 2.13
[    0.645518] NET: Registered protocol family 31
[    0.645518] Bluetooth: HCI device and connection manager initialized
[    0.645518] Bluetooth: HCI socket layer initialized
[    0.645518] NET: Registered protocol family 8
[    0.645518] NET: Registered protocol family 20
[    0.645518] NetLabel: Initializing
[    0.645518] NetLabel:  domain hash size = 128
[    0.645518] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.645518] NetLabel:  unlabeled traffic allowed by default
[    0.645518] AppArmor: AppArmor Filesystem Enabled
[    0.645518] pnp: PnP ACPI init
[    0.645518] ACPI: bus type pnp registered
[    0.645756] pnp: PnP ACPI: found 8 devices
[    0.645759] ACPI: ACPI bus type pnp unregistered
[    0.645763] PnPBIOS: Disabled by ACPI PNP
[    0.645773] system 00:04: ioport range 0x8000-0x807f has been reserved
[    0.645776] system 00:04: ioport range 0x8080-0x80ff has been reserved
[    0.645779] system 00:04: ioport range 0x8100-0x811f has been reserved
[    0.645782] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.645785] system 00:04: ioport range 0x3f0-0x3f1 has been reserved
[    0.645788] system 00:04: iomem range 0xfec00000-0xfecfffff has been reserved
[    0.645791] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.645794] system 00:04: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.645797] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.645801] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.645804] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.645807] system 00:04: iomem range 0xfffe0000-0xfffeffff has been reserved
[    0.645810] system 00:04: iomem range 0xffff0000-0xffffffff has been reserved
[    0.682192] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.682195] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.682200] pci 0000:00:01.0:   MEM window: 0xe2100000-0xe21fffff
[    0.682204] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.682210] pci 0000:00:06.0: CardBus bridge, secondary bus 0000:02
[    0.682212] pci 0000:00:06.0:   IO window: 0x002400-0x0024ff
[    0.682216] pci 0000:00:06.0:   IO window: 0x002800-0x0028ff
[    0.682220] pci 0000:00:06.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.682224] pci 0000:00:06.0:   MEM window: 0x54000000-0x57ffffff
[    0.682237] pci 0000:00:06.0: enabling device (0000 -> 0003)
[    0.682245] pci 0000:00:06.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.682250] bus: 00 index 0 io port: [0x00-0xffff]
[    0.682253] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.682255] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.682257] bus: 01 index 1 mmio: [0xe2100000-0xe21fffff]
[    0.682260] bus: 01 index 2 mmio: [0xe8000000-0xefffffff]
[    0.682262] bus: 01 index 3 mmio: [0x0-0x0]
[    0.682264] bus: 02 index 0 io port: [0x2400-0x24ff]
[    0.682266] bus: 02 index 1 io port: [0x2800-0x28ff]
[    0.682268] bus: 02 index 2 mmio: [0x50000000-0x53ffffff]
[    0.682271] bus: 02 index 3 mmio: [0x54000000-0x57ffffff]
[    0.682281] NET: Registered protocol family 2
[    0.682392] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.682751] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.683897] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.684526] TCP: Hash tables configured (established 131072 bind 65536)
[    0.684529] TCP reno registered
[    0.684649] NET: Registered protocol family 1
[    0.684808] checking if image is initramfs... it is
[    1.184028] Switched to high resolution mode on CPU 0
[    1.554538] Freeing initrd memory: 9935k freed
[    1.554587] Simple Boot Flag at 0x38 set to 0x1
[    1.554675] cpufreq: No nForce2 chipset.
[    1.554825] audit: initializing netlink socket (disabled)
[    1.554845] type=2000 audit(1255777964.552:1): initialized
[    1.563445] highmem bounce pool size: 64 pages
[    1.563469] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.564738] VFS: Disk quotas dquot_6.5.1
[    1.564797] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.565394] fuse init (API version 7.10)
[    1.565471] msgmni has been set to 1725
[    1.565642] alg: No test for stdrng (krng)
[    1.565653] io scheduler noop registered
[    1.565655] io scheduler anticipatory registered
[    1.565657] io scheduler deadline registered
[    1.565673] io scheduler cfq registered (default)
[    1.982291] pci 0000:01:00.0: Boot video device
[    1.983176] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.983184] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.985648] ACPI: AC Adapter [ACAD] (on-line)
[    1.985705] ACPI: Battery Slot [BAT1] (battery absent)
[    1.985773] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.985776] ACPI: Power Button (FF) [PWRF]
[    1.985822] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.988550] ACPI: Lid Switch [LID]
[    1.988592] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.988595] ACPI: Power Button (CM) [PWRB]
[    1.988637] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.988640] ACPI: Sleep Button (CM) [SLPB]
[    1.988803] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.988826] processor ACPI_CPU:00: registered as cooling_device0
[    1.992736] thermal LNXTHERM:01: registered as thermal_zone0
[    1.998533] ACPI: Thermal Zone [THRM] (65 C)
[    1.998573] isapnp: Scanning for PnP cards...
[    2.351791] isapnp: No Plug & Play device found
[    2.352890] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.353150] serial 0000:00:02.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.353155] serial 0000:00:02.6: PCI INT C disabled
[    2.353820] brd: module loaded
[    2.354131] loop: module loaded
[    2.354219] Fixed MDIO Bus: probed
[    2.354225] PPP generic driver version 2.4.2
[    2.354286] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.354311] Driver 'sd' needs updating - please use bus_type methods
[    2.354319] Driver 'sr' needs updating - please use bus_type methods
[    2.354848] pata_sis 0000:00:02.5: version 0.5.2
[    2.354858] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.355053] scsi0 : pata_sis
[    2.355151] scsi1 : pata_sis
[    2.355321] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
[    2.355324] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
[    2.516297] ata1.00: ATA-6: TOSHIBA MK1031GAS, AA204A, max UDMA/100
[    2.516300] ata1.00: 195371568 sectors, multi 16: LBA48 
[    2.524301] ata1.00: configured for UDMA/100
[    2.688205] ata2.00: ATAPI: Slimtype DVDRW SOSW-833S, VRS2, max UDMA/33
[    2.704223] ata2.00: configured for UDMA/33
[    2.704633] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1031GA AA20 PQ: 0 ANSI: 5
[    2.704723] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.704740] sd 0:0:0:0: [sda] Write Protect is off
[    2.704742] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.704765] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.704833] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.704846] sd 0:0:0:0: [sda] Write Protect is off
[    2.704848] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.704869] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.704873]  sda: sda1 sda2 < sda5 >
[    2.763512] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.763561] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.764096] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-833S  VRS2 PQ: 0 ANSI: 5
[    2.766910] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.766913] Uniform CD-ROM driver Revision: 3.20
[    2.766997] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.767034] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.767152] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.767178] ehci_hcd 0000:00:03.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.767204] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    2.767264] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 1
[    2.767297] ehci_hcd 0000:00:03.2: cache line size of 64 is not supported
[    2.767315] ehci_hcd 0000:00:03.2: irq 23, io mem 0xe2004000
[    2.776010] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00
[    2.776083] usb usb1: configuration #1 chosen from 1 choice
[    2.776110] hub 1-0:1.0: USB hub found
[    2.776122] hub 1-0:1.0: 6 ports detected
[    2.776229] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.776248] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.776258] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.776297] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    2.776318] ohci_hcd 0000:00:03.0: irq 20, io mem 0xe2002000
[    2.832064] usb usb2: configuration #1 chosen from 1 choice
[    2.832087] hub 2-0:1.0: USB hub found
[    2.832097] hub 2-0:1.0: 3 ports detected
[    2.832190] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.832200] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    2.832247] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    2.832266] ohci_hcd 0000:00:03.1: irq 21, io mem 0xe2003000
[    2.888072] usb usb3: configuration #1 chosen from 1 choice
[    2.888095] hub 3-0:1.0: USB hub found
[    2.888104] hub 3-0:1.0: 3 ports detected
[    2.888183] uhci_hcd: USB Universal Host Controller Interface driver
[    2.888262] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.890335] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.890340] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.890439] mice: PS/2 mouse device common for all mice
[    2.890602] rtc_cmos 00:02: RTC can wake from S4
[    2.890636] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.890662] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.890725] device-mapper: uevent: version 1.0.3
[    2.890838] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.890886] device-mapper: multipath: version 1.0.5 loaded
[    2.890889] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.890965] EISA: Probing bus 0 at eisa.0
[    2.890972] Cannot allocate resource for EISA slot 1
[    2.890975] Cannot allocate resource for EISA slot 2
[    2.890994] Cannot allocate resource for EISA slot 8
[    2.890996] EISA: Detected 0 cards.
[    2.891061] cpuidle: using governor ladder
[    2.891116] cpuidle: using governor menu
[    2.891621] TCP cubic registered
[    2.891721] NET: Registered protocol family 10
[    2.892138] lo: Disabled Privacy Extensions
[    2.892450] NET: Registered protocol family 17
[    2.892467] Bluetooth: L2CAP ver 2.11
[    2.892468] Bluetooth: L2CAP socket layer initialized
[    2.892471] Bluetooth: SCO (Voice Link) ver 0.6
[    2.892473] Bluetooth: SCO socket layer initialized
[    2.892496] Bluetooth: RFCOMM socket layer initialized
[    2.892506] Bluetooth: RFCOMM TTY layer initialized
[    2.892508] Bluetooth: RFCOMM ver 1.10
[    2.892530] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-32 processors (1 cpu cores) (version 2.20.00)
[    2.892573] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[    2.892576] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[    2.892578] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[    2.892618] Using IPI No-Shortcut mode
[    2.892697] registered taskstats version 1
[    2.892807]   Magic number: 13:634:226
[    2.892913] rtc_cmos 00:02: setting system clock to 2009-10-17 11:12:46 UTC (1255777966)
[    2.892916] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.892918] EDD information not available.
[    2.893395] Freeing unused kernel memory: 532k freed
[    2.893534] Write protecting the kernel text: 4120k
[    2.893580] Write protecting the kernel read-only data: 1524k
[    2.938324] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.989692] compcache: Compressed swap size set to: 240244 KB
[    2.990166] TLSF: pool: f7d22000, init_size=16384, max_size=0, grow_size=16384
[    3.611300] sis900.c: v1.08.10 Apr. 2 2006
[    3.611341] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.616111] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[    3.621713] 0000:00:04.0: Using transceiver found at address 13 as default
[    3.623164] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 19, 00:16:36:10:d0:5f
[    3.631283] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.688143] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0b.0
[    3.884903] Adding 240240k swap on /dev/ramzswap0.  Priority:100 extents:1 across:240240k
[    3.979645] Marking TSC unstable due to TSC halts in idle
[    4.033147] PM: Starting manual resume from disk
[    4.033150] PM: Resume from partition 8:5
[    4.033152] PM: Checking hibernation image.
[    4.033337] PM: Resume from disk failed.
[    4.086110] kjournald starting.  Commit interval 5 seconds
[    4.086124] EXT3-fs: mounted filesystem with ordered data mode.
[    4.419142] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[    4.419146] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[    4.429127] atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
[    4.429130] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[   12.231984] udev: starting version 141
[   12.749196] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.138917] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.383773] Linux agpgart interface v0.103
[   13.451554] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[   13.483508] yenta_cardbus 0000:00:06.0: CardBus bridge found [1025:0083]
[   13.483525] yenta_cardbus 0000:00:06.0: Using CSCINT to route CSC interrupts to PCI
[   13.483528] yenta_cardbus 0000:00:06.0: Routing CardBus interrupts to PCI
[   13.483533] yenta_cardbus 0000:00:06.0: TI: mfunc 0x00521d22, devctl 0x64
[   13.533753] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.554123] acer-wmi: Acer Laptop ACPI-WMI Extras
[   13.554139] acer-wmi: No or unsupported WMI interface, unable to load
[   13.616729] cfg80211: Calling CRDA to update world regulatory domain
[   13.629557] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   13.672360] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   13.713019] yenta_cardbus 0000:00:06.0: ISA IRQ mask 0x06f8, PCI irq 19
[   13.713023] yenta_cardbus 0000:00:06.0: Socket status: 30000007
[   13.713478] agpgart-amd64 0000:00:00.0: AGP bridge [1039/0760]
[   13.715039] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xe0000000
[   13.825715] cfg80211: World regulatory domain updated:
[   13.825720]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.825723]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.825726]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.825728]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.825731]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.825734]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.981780] b43-phy0: Broadcom 4318 WLAN found
[   14.049391] phy0: Selected rate control algorithm 'pid'
[   14.196791] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   14.205202] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   14.342813] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   14.344456] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[   14.345161] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   14.345732] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   14.346454] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.032028] intel8x0_measure_ac97_clock: measured 55362 usecs
[   15.032031] intel8x0: clocking to 48000
[   15.246922] lp: driver loaded but no devices found
[   15.311863] sisfb: Video ROM found
[   15.315089] sisfb: Video RAM at 0xe8000000, mapped to 0xf8480000, size 65536k
[   15.315093] sisfb: MMIO at 0xe2100000, mapped to 0xf7e80000, size 128k
[   15.315096] sisfb: Memory heap starting at 64928K, size 32K
[   16.288378] sisfb: Detected SiS302LV video bridge
[   16.350813] sisfb: Detected 1280x800 flat panel
[   16.350820] sisfb: Detected LCD PDC1 0x04 (for LCD=CRT1)
[   16.350827] sisfb: Default mode is 1280x800x8 (60Hz)
[   16.350837] sisfb: Initial vbflags 0x8000012
[   16.354648] Console: switching to colour frame buffer device 160x50
[   16.354657] sisfb: 2D acceleration is enabled, y-panning enabled (auto-max)
[   16.354660] fb0: SiS 760 frame buffer device version 1.8.9
[   16.354663] sisfb: Copyright (C) 2001-2005 Thomas Winischhofer
[   16.412710] input: Acer hotkey driver as /devices/virtual/input/input8
[   16.418362] Acer Travelmate hotkey driver v0.5.34
[   16.528673] Adding 2811332k swap on /dev/sda5.  Priority:-1 extents:1 across:2811332k
[   17.069002] EXT3 FS on sda1, internal journal
[   18.441876] type=1505 audit(1255777982.047:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1952
[   18.501417] type=1505 audit(1255777982.107:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1956
[   18.501614] type=1505 audit(1255777982.107:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1956
[   18.501679] type=1505 audit(1255777982.107:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1956
[   18.501733] type=1505 audit(1255777982.107:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1956
[   18.537029] type=1505 audit(1255777982.143:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=1961
[   18.712533] type=1505 audit(1255777982.319:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1965
[   18.712781] type=1505 audit(1255777982.319:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1965
[   18.746773] type=1505 audit(1255777982.351:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1969
[   24.390875] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.390879] Bluetooth: BNEP filters: protocol multicast
[   24.429327] Bridge firewalling registered
[   27.276030] ppdev: user-space parallel port driver
[   32.392947] eth0: Media Link On 100mbps full-duplex 
[   40.660019] eth0: no IPv6 routers present
[   90.680038] Clocksource tsc unstable (delta = -271406876 ns)
laptop@laptop-laptop:~$ 

laptop@laptop-laptop:~$ sudo lshw -C network
[sudo] password for laptop: 
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:10:d0:5f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.111 latency=173 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:00:9a:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7a:04:1a:61:a1:5b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
laptop@laptop-laptop:~$ 

laptop@laptop-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

laptop@laptop-laptop:~$ 

laptop@laptop-laptop:~$ lsb_release -d
Description:    Ubuntu 9.04
laptop@laptop-laptop:~$ uname -mr
2.6.28-15-generic i686
laptop@laptop-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
laptop@laptop-laptop:~$ 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
laptop@laptop-laptop:~$

---

### Post by chili555 on 2009-10-17
It looks to me like you have a perfectly fine working wireless interface. Check here:> [ 13.981780] b43-phy0: Broadcom 4318 WLAN found
[ 14.049391] phy0: Selected rate control algorithm 'pid'
[ 14.196791] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]and here:> wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
However, Network Manager will not allow a connection through wireless as long as you have a wired connection, which you do:> eth0 Link encap:Ethernet HWaddr 00:16:36:10:d0:5f
inet addr:192.168.0.111
---snip---Please detach the ethernet cable, click the NM icon and see if you can connect.

---

### Post by solevag on 2009-10-17
I tried disconnected ethernet cable, but on my NM under Wireless Network it says: device not managed

---

### Post by chili555 on 2009-10-17
Please show us:```
cat /etc/network/interfaces
```Thanks.

---

### Post by solevag on 2009-10-17
laptop@laptop-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
iface wlan0 inet dhcp
laptop@laptop-laptop:~$

---

### Post by chili555 on 2009-10-17
> iface wlan0 inet dhcpThis line tells Network Manager that you will manage the interface, not NM. Let's see if we can get NM to work correctly. Please do:```
sudo gedit /etc/network/interfaces 
```Add a symbol to make it read:```
auto lo
iface lo inet loopback
#iface wlan0 inet dhcp
```The comment symbol, #, tells the system to ignore the following line. Now please restart NM:```
sudo /etc/init.d/NetworkManager restart
```Now can you see your wireless interface and connect in NM?

---

### Post by solevag on 2009-10-17
No I can not see my wireless interface. The Aspire do have a button on the front to activate the wireless, there are no respons from this button. Is it possible that the wireless chip dont have power?

---

### Post by chili555 on 2009-10-17
> **solevag said:**
> No I can not see my wireless interface. The Aspire do have a button on the front to activate the wireless, there are no respons from this button. Is it possible that the wireless chip dont have power?Doubtful. I don't think an interface would be created if the wireless was turned off. You have wlan0.

I just used Fn+F5 to turn off my wireless and when I ran *sudo ifdown wlan0 && sudo ifup wlan0*, tyhis was the result:> chili@LAPTOP60:~$ sudo ifdown wlan0 && sudo ifup wlan0
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
Failed to bring up wlan0.I turned the wireless back on and here is the result:> chili@LAPTOP60:~$ sudo ifdown wlan0 && sudo ifup wlan0
ifdown: interface wlan0 not configured
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.The interface is recognized with the keyboard swith activated and not otherwise.

Please reboot with the ethernet detached and let's see if NM recognizes your wireless.

---

### Post by chili555 on 2009-10-17
Please see if you have the module *acerhk* loaded with:```
lsmod | grep acer
```If not, please do:```
sudo modprobe acerhk
```Does the wireless LED come to life?

---

### Post by solevag on 2009-10-18
laptop@laptop-laptop:~$ lsmod | grep acer
acerhk                 33332  0 
laptop@laptop-laptop:~$ dj
bash: dj: command not found
laptop@laptop-laptop:~$ 


The wireless works! I dont how or why, but it works. The light in the wireless button is ok and I can see the networks in NM:P

---

### Post by chili555 on 2009-10-18
Great! Glad it's working!

---

### Post by herdoc2005 on 2009-11-14
> **chili555 said:**
> Please see if you have the module *acerhk* loaded with:```
lsmod | grep acer
```If not, please do:```
sudo modprobe acerhk
```Does the wireless LED come to life?
 
 
I am having this same problem, but I don have the acerhk file loaded!
 
I found a download site and loaded it then transfered it to my ubuntu machine.  (I have no way to put it on the internet)
 
Now my problem is that I cant load the .deb file it comes up with an error dependency not satisfiable
 
I also dont belive that network manager is loaded/working.  
 
I have no clue where to go from here!

---

