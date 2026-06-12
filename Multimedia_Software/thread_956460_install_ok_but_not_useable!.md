---
title: "install ok but not useable!"
date: 2008-10-23
forum: Multimedia Software
---

### Post by rootmaster23 on 2008-10-23
Hello!

I read a lot of threads in the last 4 Month since i tried to install my f*****  

           Zhi ling DVB-T stick (with af9015 chip /DTB03)!

Now i got it installed with only 3 errors that some files are in use but i can't find where!
This dvbt problem is why i still got XP running on my other HDD!

PLEASE HELP ME! (with no thread bout this theme my problem was to solve)

I'm working with Intrepid Ibex (formerly i tried with 8.04)
under 8.04 i got an succesfull channel search but only slow motion tv!
My PC is an PCeleron 2,4GH, RAM 1,2GB, ATI Radeon X1550, C-Media Sound

here are my dmesg, lsusb and lsmod

1. LSMOD

pnoid@ubuntu:~$ lsmod
Module                  Size  Used by
af_packet              25728  4 
binfmt_misc            16904  1 
lirc_cmdir             16492  0 
commandir              37584  1 lirc_cmdir
lirc_dev               19892  1 lirc_cmdir
radeon                147616  2 
drm                    86056  3 radeon
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
loop                   23180  0 
ipv6                  263972  10 
snd_cmipci             42400  3 
af9013                 27524  0 
gameport               19468  1 snd_cmipci
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_cmipci,snd_pcm_oss
pcspkr                 10624  0 
snd_page_alloc         16136  1 snd_pcm
snd_opl3_lib           18560  1 snd_cmipci
snd_hwdep              15236  1 snd_opl3_lib
snd_mpu401_uart        15360  1 snd_cmipci
dvb_usb_af9015         31140  0 
dvb_usb                27404  1 dvb_usb_af9015
dvb_core               85760  1 dvb_usb
i2c_core               31892  3 af9013,dvb_usb_af9015,dvb_usb
joydev                 18368  0 
snd_seq_dummy          10884  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
ndiswrapper           196380  0 
evdev                  17696  12 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_timer              29960  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device         15116  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  18 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
button                 14224  0 
intel_agp              33724  1 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  2 drm,intel_agp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  2 
ata_generic            12932  0 
pata_acpi              12160  0 
libata                177312  3 ata_piix,ata_generic,pata_acpi
ohci_hcd               31888  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
ehci_hcd               43276  0 
usbcore               148848  9 commandir,dvb_usb_af9015,dvb_usb,ndiswrapper,usbhid,ohci_hcd,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fuse                   60828  3 
vesafb                 13828  1 
fbcon                  47648  72 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

2.) LSUSB

pnoid@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 1799:8051  
Bus 004 Device 002: ID 15a4:9016  
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0420 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pnoid@ubuntu:~$ 

3.) DMESG

[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0004fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0004fff0
[    0.000000] On node 0 totalpages: 327568
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 97424 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324688
[    0.000000] Kernel command line: root=UUID=8e442dce-c790-40aa-979d-a000f5f774c8 ro quiet splash vga=791 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2399.713 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1284180k/1310656k available (2572k kernel code, 25304k reserved, 1160k data, 424k init, 393152k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004020] Calibrating delay loop (skipped), value calculated using timer frequency.. 4799.42 BogoMIPS (lpj=9598852)
[    0.004061] Security Framework initialized
[    0.004079] SELinux:  Disabled at boot.
[    0.004116] AppArmor: AppArmor initialized
[    0.004136] Mount-cache hash table entries: 512
[    0.004473] Initializing cgroup subsys ns
[    0.004485] Initializing cgroup subsys cpuacct
[    0.004490] Initializing cgroup subsys memory
[    0.004524] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004530] CPU: L2 cache: 128K
[    0.004534] CPU: Hyper-Threading is disabled
[    0.004560] Checking 'hlt' instruction... OK.
[    0.020647] SMP alternatives: switching to UP code
[    0.028025] ACPI: Core revision 20080609
[    0.032348] ACPI: Checking initramfs for custom DSDT
[    0.436284] ENABLING IO-APIC IRQs
[    0.436480] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.479001] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 09
[    0.480030] Brought up 1 CPUs
[    0.480030] Total of 1 processors activated (4799.42 BogoMIPS).
[    0.480030] CPU0 attaching sched-domain:
[    0.480030]  domain 0: span 0 level CPU
[    0.480030]   groups: 0
[    0.480030] net_namespace: 840 bytes
[    0.480030] Booting paravirtualized kernel on bare hardware
[    0.480030] Time: 14:56:47  Date: 10/23/08
[    0.480030] NET: Registered protocol family 16
[    0.480030] EISA bus registered
[    0.480030] ACPI: bus type pci registered
[    0.481070] PCI: PCI BIOS revision 2.10 entry at 0xfb690, last bus=2
[    0.481077] PCI: Using configuration type 1 for base access
[    0.486384] ACPI: EC: Look up EC in DSDT
[    0.493793] ACPI: Interpreter enabled
[    0.493803] ACPI: (supports S0 S3 S4 S5)
[    0.493836] ACPI: Using IOAPIC for interrupt routing
[    0.507625] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.507880] PCI: 0000:00:00.0 reg 10 32bit mmio: [b0000000, bfffffff]
[    0.508077] PCI: 0000:00:1d.0 reg 20 io port: [b800, b81f]
[    0.508140] PCI: 0000:00:1d.1 reg 20 io port: [b000, b01f]
[    0.508198] PCI: 0000:00:1d.2 reg 20 io port: [b400, b41f]
[    0.508257] PCI: 0000:00:1d.7 reg 10 32bit mmio: [e0100000, e01003ff]
[    0.508313] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.508320] pci 0000:00:1d.7: PME# disabled
[    0.508363] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.508365] * this clock source is slow. If you are sure your timer does not have
[    0.508367] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.508413] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.508423] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.508428] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.508451] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.508459] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.508468] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.508476] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.508484] PCI: 0000:00:1f.1 reg 20 io port: [f000, f00f]
[    0.508492] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.508548] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f]
[    0.508627] PCI: 0000:01:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
[    0.508646] PCI: 0000:01:00.0 reg 18 64bit mmio: [d1000000, d100ffff]
[    0.508654] PCI: 0000:01:00.0 reg 20 io port: [9000, 90ff]
[    0.508667] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.508690] pci 0000:01:00.0: supports D1
[    0.508692] pci 0000:01:00.0: supports D2
[    0.508730] PCI: 0000:01:00.1 reg 10 64bit mmio: [d1010000, d101ffff]
[    0.508772] pci 0000:01:00.1: supports D1
[    0.508775] pci 0000:01:00.1: supports D2
[    0.508819] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.508824] PCI: bridge 0000:00:01.0 32bit mmio: [c0000000, dfffffff]
[    0.508867] PCI: 0000:02:00.0 reg 10 io port: [a000, a0ff]
[    0.508914] pci 0000:02:00.0: supports D1
[    0.508917] pci 0000:02:00.0: supports D2
[    0.508961] PCI: 0000:02:01.0 reg 10 32bit mmio: [e0000000, e0000fff]
[    0.509007] pci 0000:02:01.0: supports D1
[    0.509010] pci 0000:02:01.0: supports D2
[    0.509012] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot
[    0.509018] pci 0000:02:01.0: PME# disabled
[    0.509050] PCI: 0000:02:01.1 reg 10 32bit mmio: [e0001000, e0001fff]
[    0.509095] pci 0000:02:01.1: supports D1
[    0.509097] pci 0000:02:01.1: supports D2
[    0.509099] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot
[    0.509105] pci 0000:02:01.1: PME# disabled
[    0.509135] PCI: 0000:02:01.2 reg 10 32bit mmio: [e0002000, e00020ff]
[    0.509180] pci 0000:02:01.2: supports D1
[    0.509183] pci 0000:02:01.2: supports D2
[    0.509185] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot
[    0.509191] pci 0000:02:01.2: PME# disabled
[    0.509238] pci 0000:00:1e.0: transparent bridge
[    0.509244] PCI: bridge 0000:00:1e.0 io port: [a000, afff]
[    0.509249] PCI: bridge 0000:00:1e.0 32bit mmio: [e0000000, e00fffff]
[    0.509268] bus 00 -> node 0
[    0.509293] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.509706] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.524759] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *11 12 14 15)
[    0.524996] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 11 12 14 15)
[    0.525226] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 11 *12 14 15)
[    0.525456] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 11 12 14 15)
[    0.525684] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 11 *12 14 15)
[    0.525917] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *11 12 14 15)
[    0.526149] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 *9 11 12 14 15)
[    0.526380] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 11 12 14 15)
[    0.526972] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.527146] pnp: PnP ACPI init
[    0.527173] ACPI: bus type pnp registered
[    0.535352] pnp: PnP ACPI: found 14 devices
[    0.535359] ACPI: ACPI bus type pnp unregistered
[    0.535366] PnPBIOS: Disabled by ACPI PNP
[    0.537163] PCI: Using ACPI for IRQ routing
[    0.537508] NET: Registered protocol family 8
[    0.537508] NET: Registered protocol family 20
[    0.537508] NetLabel: Initializing
[    0.537508] NetLabel:  domain hash size = 128
[    0.537508] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.537508] NetLabel:  unlabeled traffic allowed by default
[    0.537508] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.537508]    actual entries 65620
[    0.537508] AppArmor: AppArmor Filesystem Enabled
[    0.537508] ACPI: RTC can wake from S4
[    0.537508] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.537508] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.537508] system 00:0a: ioport range 0x280-0x287 has been reserved
[    0.537508] system 00:0b: ioport range 0x400-0x4bf could not be reserved
[    0.537508] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[    0.537508] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.537508] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.537508] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.537508] system 00:0c: iomem range 0x4fff0000-0x4fffffff could not be reserved
[    0.537508] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.537508] system 00:0c: iomem range 0x100000-0x4ffeffff could not be reserved
[    0.537508] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.537508] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.537508] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.537508] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.537508] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.576323] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.576331] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.576339] pci 0000:00:01.0:   MEM window: 0xc0000000-0xdfffffff
[    0.576346] pci 0000:00:01.0:   PREFETCH window: 0x00000060000000-0x000000600fffff
[    0.576356] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.576360] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.576367] pci 0000:00:1e.0:   MEM window: 0xe0000000-0xe00fffff
[    0.576373] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.576398] pci 0000:00:1e.0: setting latency timer to 64
[    0.576403] bus: 00 index 0 io port: [0, ffff]
[    0.576406] bus: 00 index 1 mmio: [0, ffffffff]
[    0.576409] bus: 01 index 0 io port: [9000, 9fff]
[    0.576412] bus: 01 index 1 mmio: [c0000000, dfffffff]
[    0.576415] bus: 01 index 2 mmio: [60000000, 600fffff]
[    0.576417] bus: 01 index 3 mmio: [0, 0]
[    0.576420] bus: 02 index 0 io port: [a000, afff]
[    0.576423] bus: 02 index 1 mmio: [e0000000, e00fffff]
[    0.576426] bus: 02 index 2 mmio: [0, 0]
[    0.576428] bus: 02 index 3 io port: [0, ffff]
[    0.576431] bus: 02 index 4 mmio: [0, ffffffff]
[    0.576455] NET: Registered protocol family 2
[    0.576760] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.577338] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.579007] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.579870] TCP: Hash tables configured (established 131072 bind 65536)
[    0.579876] TCP reno registered
[    0.580177] NET: Registered protocol family 1
[    0.580383] checking if image is initramfs... it is
[    1.080085] Switched to high resolution mode on CPU 0
[    1.477657] Freeing initrd memory: 7971k freed
[    1.480222] audit: initializing netlink socket (disabled)
[    1.480249] type=2000 audit(1224773807.480:1): initialized
[    1.486190] highmem bounce pool size: 64 pages
[    1.486212] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.494854] VFS: Disk quotas dquot_6.5.1
[    1.495155] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.495541] msgmni has been set to 1757
[    1.495928] io scheduler noop registered
[    1.495936] io scheduler anticipatory registered
[    1.495939] io scheduler deadline registered
[    1.495987] io scheduler cfq registered (default)
[    1.496130] pci 0000:01:00.0: Boot video device
[    1.497551] isapnp: Scanning for PnP cards...
[    1.851324] isapnp: No Plug & Play device found
[    2.079917] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.080309] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.080905] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.083510] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.084798] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.093073] brd: module loaded
[    2.093341] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.094113] PNP: No PS/2 controller found. Probing ports directly.
[    2.348436] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.349897] mice: PS/2 mouse device common for all mice
[    2.350613] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.350651] rtc0: alarms up to one month
[    2.351240] EISA: Probing bus 0 at eisa.0
[    2.351283] EISA: Detected 0 cards.
[    2.351290] cpuidle: using governor ladder
[    2.351293] cpuidle: using governor menu
[    2.352257] TCP cubic registered
[    2.352342] Using IPI No-Shortcut mode
[    2.353564] registered taskstats version 1
[    2.353726]   Magic number: 12:129:941
[    2.353817] tty ptyyc: hash matches
[    2.353918] rtc_cmos 00:03: setting system clock to 2008-10-23 14:56:49 UTC (1224773809)
[    2.353924] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.353927] EDD information not available.
[    2.354662] Freeing unused kernel memory: 424k freed
[    2.354744] Write protecting the kernel text: 2576k
[    2.354790] Write protecting the kernel read-only data: 936k
[    2.516658] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 3072k, total 16384k
[    2.516666] vesafb: mode is 1024x768x16, linelength=2048, pages=9
[    2.516669] vesafb: protected mode interface info at c000:a12e
[    2.516674] vesafb: pmi: set display start = c00ca1bc, set palette = c00ca27e
[    2.516677] vesafb: scrolling: redraw
[    2.516681] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    2.517387] Console: switching to colour frame buffer device 128x48
[    2.545626] fb0: VESA VGA frame buffer device
[    2.690133] fuse init (API version 7.9)
[    2.818673] processor ACPI0007:00: registered as cooling_device0
[    2.858733] thermal LNXTHERM:01: registered as thermal_zone0
[    2.888273] ACPI: Thermal Zone [THRM] (40 C)
[    3.872913] usbcore: registered new interface driver usbfs
[    3.872967] usbcore: registered new interface driver hub
[    3.876365] usbcore: registered new device driver usb
[    3.898933] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.898958] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.898964] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.899080] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.903016] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.903044] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe0100000
[    3.907145] USB Universal Host Controller Interface driver v3.0
[    3.933277] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.933605] usb usb1: configuration #1 chosen from 1 choice
[    3.933682] hub 1-0:1.0: USB hub found
[    3.933709] hub 1-0:1.0: 6 ports detected
[    3.944626] No dock devices found.
[    4.024619] SCSI subsystem initialized
[    4.024825] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.125498] libata version 3.00 loaded.
[    4.156912] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.156931] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.156937] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.157012] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.157061] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000b800
[    4.157400] usb usb2: configuration #1 chosen from 1 choice
[    4.157474] hub 2-0:1.0: USB hub found
[    4.157497] hub 2-0:1.0: 2 ports detected
[    4.364757] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.364774] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.364780] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.364857] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.364905] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b000
[    4.365263] usb usb3: configuration #1 chosen from 1 choice
[    4.365333] hub 3-0:1.0: USB hub found
[    4.365356] hub 3-0:1.0: 2 ports detected
[    4.476127] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.572731] ehci_hcd 0000:02:01.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    4.572760] ehci_hcd 0000:02:01.2: EHCI Host Controller
[    4.572839] ehci_hcd 0000:02:01.2: new USB bus registered, assigned bus number 4
[    4.572949] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.572967] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.572972] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.573060] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    4.573111] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[    4.573453] usb usb5: configuration #1 chosen from 1 choice
[    4.573524] hub 5-0:1.0: USB hub found
[    4.573550] hub 5-0:1.0: 2 ports detected
[    4.596129] ehci_hcd 0000:02:01.2: irq 23, io mem 0xe0002000
[    4.608068] ehci_hcd 0000:02:01.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.658358] usb 2-1: configuration #1 chosen from 1 choice
[    4.676955] usb usb4: configuration #1 chosen from 1 choice
[    4.677029] hub 4-0:1.0: USB hub found
[    4.677058] hub 4-0:1.0: 5 ports detected
[    4.772131] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    4.884807] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.884882] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    4.884908] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    4.885024] ohci_hcd 0000:02:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.885050] ohci_hcd 0000:02:01.0: OHCI Host Controller
[    4.885140] ohci_hcd 0000:02:01.0: new USB bus registered, assigned bus number 6
[    4.885185] ohci_hcd 0000:02:01.0: irq 21, io mem 0xe0000000
[    4.973858] usb usb6: configuration #1 chosen from 1 choice
[    4.973944] hub 6-0:1.0: USB hub found
[    4.973971] hub 6-0:1.0: 3 ports detected
[    5.009194] usb 3-1: configuration #1 chosen from 1 choice
[    5.076789] ohci_hcd 0000:02:01.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    5.076813] ohci_hcd 0000:02:01.1: OHCI Host Controller
[    5.076895] ohci_hcd 0000:02:01.1: new USB bus registered, assigned bus number 7
[    5.076940] ohci_hcd 0000:02:01.1: irq 22, io mem 0xe0001000
[    5.124117] usb 4-2: new high speed USB device using ehci_hcd and address 2
[    5.165759] usb usb7: configuration #1 chosen from 1 choice
[    5.165836] hub 7-0:1.0: USB hub found
[    5.165864] hub 7-0:1.0: 2 ports detected
[    5.262210] usb 4-2: configuration #1 chosen from 1 choice
[    5.282840] ata_piix 0000:00:1f.1: version 2.12
[    5.282867] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.282964] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.284812] scsi0 : ata_piix
[    5.285087] scsi1 : ata_piix
[    5.286572] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    5.286579] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    5.376118] usb 4-3: new high speed USB device using ehci_hcd and address 3
[    5.456691] ata1.00: ATA-7: ExcelStor Technology J8160, P22OA85A, max UDMA/133
[    5.456698] ata1.00: 321672960 sectors, multi 16: LBA48 
[    5.504161] ata1.01: ATA-7: ST3802110A, 3.AAE, max UDMA/100
[    5.504168] ata1.01: 156301488 sectors, multi 16: LBA48 
[    5.513904] usb 4-3: configuration #1 chosen from 1 choice
[    5.520628] ata1.00: configured for UDMA/100
[    5.587357] ata1.01: configured for UDMA/100
[    5.759587] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB00, max UDMA/66
[    5.759618] ata2.01: ATAPI: TOSHIBA DVD-ROM SD-R1202, 1026, max UDMA/33
[    5.759635] ata2.00: limited to UDMA/33 due to 40-wire cable
[    5.768209] usbcore: registered new interface driver hiddev
[    5.772358] ata2.00: configured for UDMA/33
[    5.783737] input: Microsoft Microsoft Wheel Mouse Optical&#65533; as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input1
[    5.788427] ata2.01: configured for UDMA/33
[    5.788711] scsi 0:0:0:0: Direct-Access     ATA      ExcelStor Techno P22O PQ: 0 ANSI: 5
[    5.789093] scsi 0:0:1:0: Direct-Access     ATA      ST3802110A       3.AA PQ: 0 ANSI: 5
[    5.790171] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB00 PQ: 0 ANSI: 5
[    5.795861] scsi 1:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-R1202 1026 PQ: 0 ANSI: 5
[    5.796561] input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical&#65533;] on usb-0000:00:1d.0-1
[    5.827604] input: Chicony USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2
[    5.840397] input,hidraw1: USB HID v1.11 Keyboard [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.1-1
[    5.906013] input: Chicony USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input3
[    5.920598] input,hiddev96,hidraw2: USB HID v1.11 Device [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.1-1
[    5.945500] input: Chicony USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2/input/input4
[    5.960544] input,hidraw3: USB HID v1.11 Mouse [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.1-1
[    5.963090] TurboSight DTB03: Fixing fullspeed to highspeed interval: 16 -> 8
[    5.964395] input: TurboSight DTB03 as /devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb4/4-2/4-2:1.1/input/input5
[    5.976680] input,hidraw4: USB HID v1.01 Keyboard [TurboSight DTB03] on usb-0000:02:01.2-2
[    5.976731] usbcore: registered new interface driver usbhid
[    5.976740] usbhid: v2.6:USB HID core driver
[    6.010604] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.010837] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[    6.011070] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    6.011295] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[    6.115161] Driver 'sd' needs updating - please use bus_type methods
[    6.115434] sd 0:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
[    6.115519] sd 0:0:0:0: [sda] Write Protect is off
[    6.115526] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.115671] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.115915] sd 0:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
[    6.116030] sd 0:0:0:0: [sda] Write Protect is off
[    6.116036] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.116201] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.116216]  sda: sda1 sda2 sda3
[    6.149929] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.150189] sd 0:0:1:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[    6.150274] sd 0:0:1:0: [sdb] Write Protect is off
[    6.150280] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    6.150429] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.150671] sd 0:0:1:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[    6.150754] sd 0:0:1:0: [sdb] Write Protect is off
[    6.150760] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    6.150900] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.150914]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
[    6.176178]  sdb1 sdb2
[    6.176456] sd 0:0:1:0: [sdb] Attached SCSI disk
[    6.204170] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.204180] Uniform CD-ROM driver Revision: 3.20
[    6.204378] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.212653] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    6.212845] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    6.811861] PM: Starting manual resume from disk
[    6.811871] PM: Resume from partition 8:3
[    6.811873] PM: Checking hibernation image.
[    6.812158] PM: Resume from disk failed.
[    6.867602] kjournald starting.  Commit interval 5 seconds
[    6.867640] EXT3-fs: mounted filesystem with ordered data mode.
[   12.992175] udevd version 124 started
[   13.905449] Linux agpgart interface v0.103
[   13.968902] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.045320] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.096816] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   14.114973] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[   14.341865] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input6
[   14.352094] ACPI: Power Button (FF) [PWRF]
[   14.352446] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input7
[   14.370538] ACPI: Power Button (CM) [PWRB]
[   15.945126] parport_pc 00:09: reported by Plug and Play ACPI
[   15.945162] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   17.117891] intel_rng: FWH not detected
[   17.251141] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.305584] iTCO_vendor_support: vendor-support=0
[   17.363241] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   17.363549] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   17.363933] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.808401] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
[   17.808604] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   17.809027] DVB: registering new adapter (Afatech AF9015 DVB-T USB2.0 stick)
[   17.868066] usb 4-3: reset high speed USB device using ehci_hcd and address 3
[   17.992601] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   18.091595] ndiswrapper: driver netmw245 (Belkin,11/09/2006,1.0.4.6) loaded
[   18.595725] C-Media PCI 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.600189] af9013: firmware version:4.65.0
[   18.607408] af9015: recv bulk message failed:-71
[   18.607420] af9013: I2C write failed reg:d736 len:1
[   18.607563] dvb-usb: no frontend was attached by 'Afatech AF9015 DVB-T USB2.0 stick'
[   18.607571] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
[   18.607794] af9015: bulk message failed:-71 (8/0)
[   18.607801] af9015: endpoint init failed:-71
[   18.607824] dvb_usb_af9015: probe of 4-2:1.0 failed with error -71
[   19.176749] wlan0: ethernet device 00:17:3f:40:be:a4 using NDIS driver: netmw245, version: 0x1000305, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1799:8051.F.conf
[   19.176822] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.177052] usbcore: registered new interface driver dvb_usb_af9015
[   19.178110] usbcore: registered new interface driver ndiswrapper
[   22.792141] NET: Registered protocol family 10
[   22.792927] lo: Disabled Privacy Extensions
[   23.459635] loop: module loaded
[   23.486610] lp0: using parport0 (interrupt-driven).
[   24.299869] Adding 489972k swap on /dev/sda3.  Priority:-1 extents:1 across:489972k
[   24.927492] EXT3 FS on sda2, internal journal
[   26.514178] type=1505 audit(1224766633.727:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4249
[   26.786300] type=1505 audit(1224766633.999:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4254
[   26.786857] type=1505 audit(1224766633.999:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4254
[   27.048609] ip_tables: (C) 2000-2006 Netfilter Core Team
[   28.375351] ACPI: WMI: Mapper loaded
[   30.167516] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   30.497495] ppdev: user-space parallel port driver
[   36.964924] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   37.211463] [drm] Initialized drm 1.1.0 20060810
[   37.236426] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   37.466085] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   37.466138] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[   37.466175] pci 0000:01:00.0: putting AGP V2 device into 1x mode
[   37.524917] [drm] Setting GART location based on new memory map
[   37.524951] [drm] Loading R500 Microcode
[   37.525012] [drm] Num pipes: 1
[   37.525023] [drm] writeback test succeeded in 1 usecs
[   38.098504] lirc_dev: IR Remote Control driver registered, major 61 
[   38.131816] usbcore: registered new interface driver commandir
[   38.140061] lirc_dev: lirc_register_plugin: sample_rate: 20
[   38.146134] lirc_cmdir: freq set to 38000Hz
[   39.181536] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.769946] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.924414] NET: Registered protocol family 17
[   50.828039] wlan0: no IPv6 routers present
[  152.563330] ppdev0: registered pardevice
[  152.612488] ppdev0: unregistered pardevice
[  153.976543] type=1503 audit(1224766761.191:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6053/net/" pid=6053 profile="/usr/sbin/cupsd"
[  155.013049] type=1503 audit(1224766762.227:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6057/net/" pid=6057 profile="/usr/sbin/cupsd"
[  155.021327] type=1503 audit(1224766762.235:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6057 profile="/usr/sbin/cupsd"
[  155.028098] type=1503 audit(1224766762.243:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6057 profile="/usr/sbin/cupsd"
[  155.028132] type=1503 audit(1224766762.243:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6057 profile="/usr/sbin/cupsd"
[  155.028141] type=1503 audit(1224766762.243:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6057 profile="/usr/sbin/cupsd"
[  155.028149] type=1503 audit(1224766762.243:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6057 profile="/usr/sbin/cupsd"
[  155.028157] type=1503 audit(1224766762.243:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6057 profile="/usr/sbin/cupsd"
[  155.028165] type=1503 audit(1224766762.243:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6057 profile="/usr/sbin/cupsd"
[  155.028173] type=1503 audit(1224766762.243:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6057 profile="/usr/sbin/cupsd"
[  155.400685] ppdev0: registered pardevice
[  155.464693] ppdev0: unregistered pardevice
[  155.519938] ppdev0: registered pardevice
[  155.572077] ppdev0: unregistered pardevice
pnoid@ubuntu:~$ 

I'm just moving in circles and with every circle i make i start to hate my DVB-T more and more!

Thank you for your Help!
Have a nice day!

---

### Post by xc3RnbFO8P on 2008-10-23
Read this:
[http://www.linuxtv.org/wiki/index.php/Afatech_AF9015]("http://www.linuxtv.org/wiki/index.php/Afatech_AF9015")

---

### Post by rootmaster23 on 2008-10-23
What a Tip!

I checked this page earlier today and about 10 times in the last months --> no help!
I told you! i checked nearly every thread bout this f***** dvb-t stick and i tried a 100 theories and nothing worked!
Maybe I'm nearly blind(not maybe - it is!8) and i overread the solve! 

Please help me!

---

### Post by cariboo on 2008-10-23
I know you said you tried 100's of solutions, but have you had a look ath this page:

[http://www.linuxtv.org/v4lwiki/index.php/MSI_DigiVox_mini_II_V3.0](http://www.linuxtv.org/v4lwiki/index.php/MSI_DigiVox_mini_II_V3.0)

I see you are not the politest person in the world, how about explaining a little better what you have done. All the listings are wonderful, but if you look in your dmesg output your device is failing to be initialized.

Jim

---

### Post by rootmaster23 on 2008-11-08
i think the last link given isn't working any more!

Yeah! i know, theat my answer wasn't that nice, but it was after workin' 48 hours on that prob without a pause and an illnes commin'! After reading my own answer I felt ashamed about my kind of reacting and hope you guys can forgive me! 

I had a little distance to this and now i'm restrenght and optimistic and i hope more polite 8)! 

So i hope keepin in contact with me would be more fun! 

Sorry for my ****** bad english but my brain is still a little bit dizzy from the medication! It'll get better during the days! 8)

---

### Post by rootmaster23 on 2008-11-08
A new beginning with a totally new installation of 8.10!

i checked the driver and the firmware and had a

make

these are the errors during the installation:

/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/cx18-driver.c: In function 'cx18_request_module': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/cx18-driver.c:568: warning: format not a string literal and no format arguments 

/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/anysee.c: In function 'anysee_master_xfer': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/anysee.c:191: warning: 'ret' may be used uninitialized in this function 

/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/ivtv-driver.c: In function 'ivtv_request_module': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/ivtv-driver.c:866: warning: format not a string literal and no format arguments 

/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/pvrusb2-hdw.c: In function 'pvr2_hdw_setup_low': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/pvrusb2-hdw.c:1987: warning: format not a string literal and no format arguments 

/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/pvrusb2-std.c: In function 'pvr2_std_id_to_str': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/pvrusb2-std.c:220: warning: format not a string literal and no format arguments 

/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/zoran_card.c: In function 'find_zr36057': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/zoran_card.c:1439: warning: format not a string literal and no format arguments 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/zoran_card.c:1459: warning: format not a string literal and no format arguments 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/zoran_card.c:1482: warning: format not a string literal and no format arguments 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/zoran_card.c:1492: warning: format not a string literal and no format arguments 

/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/v4l2-common.c: In function 'v4l2_ctrl_query_fill': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/v4l2-common.c:492: warning: format not a string literal and no format arguments 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/v4l2-common.c: In function 'v4l2_ctrl_query_menu': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/v4l2-common.c:657: warning: format not a string literal and no format arguments 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/v4l2-common.c: In function 'v4l2_ctrl_query_menu_valid_items': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/v4l2-common.c:675: warning: format not a string literal and no format arguments 

/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/tvaudio.c: In function 'chip_probe': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/tvaudio.c:1539: warning: format not a string literal and no format arguments 

/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/cx2341x.c: In function 'cx2341x_ctrl_query_fill': 
/usr/src/af9015/af9015-e0e0e4ee5b33/v4l/cx2341x.c:475: warning: format not a string literal and no format arguments 

then came stage 2

 Building modules, stage 2. 
  MODPOST 290 modules

no unexpected action!

make install --> all fine

then restart

the light was not flashing so i had an dmesg

here is what it sayd about the af9015!

[   16.685900] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)

[   17.106011] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.

[   17.106263] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.

[   17.110529] DVB: registering new adapter (Afatech AF9015 DVB-T USB2.0 stick)

[   17.196067] usb 4-3: reset high speed USB device using ehci_hcd and address 3

[   17.378856] ndiswrapper: driver netmw245 (Belkin,11/09/2006,1.0.4.6) loaded

[   17.732892] input: PC Speaker as /devices/platform/pcspkr/input/input8

[   17.819912] af9013: firmware version:4.63.6

[   17.825986] af9015: recv bulk message failed:-71

[   17.826005] af9013: I2C write failed reg:d736 len:1

[   17.826137] dvb-usb: no frontend was attached by 'Afatech AF9015 DVB-T USB2.0 stick'

[   17.826145] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.

[   17.826288] af9015: bulk message failed:-71 (8/0)

[   17.826295] af9015: endpoint init failed:-71

[   17.826321] dvb_usb_af9015: probe of 4-2:1.0 failed with error -71

[   18.400701] wlan0: ethernet device 00:17:3f:40:be:a4 using NDIS driver: netmw...blablabla....


anybody knows the answer? Please?

Good night!

---

### Post by xc3RnbFO8P on 2008-11-09
> [ 17.826145] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
Did you try Kaffeine?

---

### Post by rootmaster23 on 2008-11-10
Hey!

First of all, thank you!

Yeah! I tried a lot o progs (kaffeine, digital Television, and a lot more) but they don't even show the symbol for digi tv in the menu!

It's like recognizing that there is a stick but unable to activate completely! (the blue light, normaly on, isn't flashing)

Any further plans? 

I think there was a HP telling that i have to deactivate the modules listed in my error list so that i can correct install but i can't find it any more? Could that be the reason why it doesn't work! And how can i do so?

Thnx!

---

### Post by xc3RnbFO8P on 2008-11-10
> no frontend was attached by
Where did you get this driver (link)?

---

### Post by rootmaster23 on 2008-11-10
Hello again! 8)

Sounds funny but i got the driver from the link you gave me! (i was so fast with setting up a new system that i forgot to save all my links collected on my quest for the solve!) 8)

I'm not able to find the HP i mentioned in the thread before but i'm sure they wrote that there are all v4l, dvb and the usbdvbstick mdules to set inactive but i need the manual to do so! Could you tell me how to do? 
i think that could be right because there were some errors with the probe files and there are mentioned errors on my dmesg with the probe to! I don't know if one error depends on the other? 

Thnx!

---

