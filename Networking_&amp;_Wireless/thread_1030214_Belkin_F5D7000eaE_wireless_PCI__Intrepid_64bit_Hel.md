---
title: "Belkin F5D7000eaE wireless PCI  Intrepid 64bit Help please"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Sproty on 2009-01-04
Hi very new user, first time install and enjoying Ubuntu apart from the wireless card.  Tried installing Windows driver from CD supplied with the card, driver install hardware shows as present but network manager shows no wireless connections.  Followed many threads on forum and net in general nothing seems to work.  Tried madwifi following the beginers guide but get a shed full of errors, which I don't have the knowledge to act upon.  The card is a Belkin F5D7000eaE version 1100ea.

> 00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:06.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)


> root@Ubuntu:/home/kevin/Desktop# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:a3:4b:bc  
          inet addr:192.168.1.168  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fea3:4bbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13473263 (13.4 MB)  TX bytes:1079060 (1.0 MB)
          Interrupt:17 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3400 (3.4 KB)  TX bytes:3400 (3.4 KB)



> root@Ubuntu:/home/kevin/Desktop# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:a3:4b:bc  
          inet addr:192.168.1.168  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fea3:4bbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13473263 (13.4 MB)  TX bytes:1079060 (1.0 MB)
          Interrupt:17 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3400 (3.4 KB)  TX bytes:3400 (3.4 KB)

root@Ubuntu:/home/kevin/Desktop# $ iwconfig
bash: $: command not found
root@Ubuntu:/home/kevin/Desktop# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


> root@Ubuntu:/home/kevin/Desktop# lsmod
Module                  Size  Used by
isofs                  44072  1 
binfmt_misc            18700  1 
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,sco,bnep,l2cap
ppdev                  16904  0 
powernow_k8            23812  0 
cpufreq_powersave      10368  0 
cpufreq_ondemand       16400  1 
cpufreq_conservative    16392  0 
cpufreq_stats          14468  0 
freq_table             13568  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      12420  0 
pci_slot               13704  0 
wmi                    15808  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
container              12288  0 
video                  29204  0 
output                 11776  1 video
battery                21128  0 
ipv6                  314312  8 
af_packet              29568  2 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
lp                     19588  0 
serio_raw              14596  0 
snd_intel8x0           43688  3 
snd_ac97_codec        133080  1 snd_intel8x0
evdev                  20512  6 
psmouse                51612  0 
ac97_bus               10368  1 snd_ac97_codec
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
pcspkr                 11136  0 
nvidia               8115824  34 
snd_pcm                99208  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
k8temp                 13568  0 
snd_seq_dummy          11524  0 
parport_pc             44200  1 
parport                50096  3 ppdev,lp,parport_pc
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
ndiswrapper           253696  0 
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_ali15x3            16132  0 
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_ali1535            15492  0 
snd                    79432  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 42140  0 
i2c_ali1563            16132  0 
isp1760                29488  0 
soundcore              16800  1 snd
button                 15904  0 
i2c_core               36128  4 nvidia,i2c_ali15x3,i2c_ali1535,i2c_ali1563
pci_hotplug            39216  1 shpchp
uli526x                26256  0 
snd_page_alloc         17680  2 snd_intel8x0,snd_pcm
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  1 
cdrom                  47784  1 sr_mod
pata_acpi              13568  0 
ata_generic            14212  0 
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
ohci_hcd               35100  0 
ehci_hcd               49548  0 
pata_ali               19332  3 
sata_uli               13444  0 
usbcore               175888  5 ndiswrapper,isp1760,ohci_hcd,ehci_hcd
libata                201312  4 pata_acpi,ata_generic,pata_ali,sata_uli
scsi_mod              183160  4 sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 
[QUOTE]
oot@Ubuntu:/home/kevin/Desktop# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Fri Dec 19 16:29:35 UTC 2008 (Ubuntu 2.6.27-11.22-generic)
[    0.000000] Command line: root=UUID=f6b6d92e-b550-443f-8485-6f5159dc37c7 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3ffb0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 003fe00000 page 2M
[    0.000000]  003fe00000 - 003ffb0000 page 4k
[    0.000000] kernel direct mapping tables up to 3ffb0000 @ 10000-13000
[    0.000000] last_map_addr: 3ffb0000 end: 3ffb0000
[    0.000000] RAMDISK: 377aa000 - 37fef458
[    0.000000] ACPI: RSDP 000FA4A0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFB0000, 0030 (r1 A M I  OEMRSDT  11000415 MSFT       97)
[    0.000000] ACPI: FACP 3FFB0200, 0081 (r1 A M I  OEMFACP  11000415 MSFT       97)
[    0.000000] ACPI: DSDT 3FFB03F0, 3D9D (r1  K1689 K1689120      120 INTL  2002026)
[    0.000000] ACPI: FACS 3FFC0000, 0040
[    0.000000] ACPI: APIC 3FFB0390, 0054 (r1 A M I  OEMAPIC  11000415 MSFT       97)
[    0.000000] ACPI: OEMB 3FFC0040, 0040 (r1 A M I  AMI_OEM  11000415 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003ffb0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ffb0000
[    0.000000]   NODE_DATA [0000000000011000 - 0000000000015fff]
[    0.000000]   bootmap [0000000000016000 -  000000000001dff7] pages 8
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 003ffb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b9f5c]    TEXT DATA BSS ==> [0000200000 - 00008b9f5c]
[    0.000000]   #3 [00377aa000 - 0037fef458]          RAMDISK ==> [00377aa000 - 0037fef458]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]  [ffffe20000000000-ffffe20000ffffff] PMD -> [ffff880001200000-ffff8800021fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ffb0
[    0.000000] On node 0 totalpages: 261951
[    0.000000]   DMA zone: 2097 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 253937 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf7c0000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 256034
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=f6b6d92e-b550-443f-8485-6f5159dc37c7 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2199.918 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] AGP bridge at 00:00:00
[    0.004000] Aperture from AGP @ f8000000 old size 32 MB
[    0.004000] Aperture size 4096 MB (APSIZE 0) is not right, using settings from NB
[    0.004000] Aperture from AGP @ f8000000 size 32 MB (APSIZE 0)
[    0.004000] Node 0: aperture @ f8000000 size 64 MB
[    0.004000] Memory: 1015864k/1048256k available (3116k kernel code, 31940k reserved, 1575k data, 540k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 4399.83 BogoMIPS (lpj=8799672)
[    0.004050] Security Framework initialized
[    0.004063] SELinux:  Disabled at boot.
[    0.004087] AppArmor: AppArmor initialized
[    0.004218] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.005462] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.006064] Mount-cache hash table entries: 256
[    0.006304] Initializing cgroup subsys ns
[    0.006309] Initializing cgroup subsys cpuacct
[    0.006311] Initializing cgroup subsys memory
[    0.006332] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.006334] CPU: L2 Cache: 512K (64 bytes/line)
[    0.006337] CPU 0/0 -> Node 0
[    0.006339] tseg: 0000000000
[    0.006382] SMP alternatives: switching to UP code
[    0.012008] Freeing SMP alternatives: 24k freed
[    0.012031] ACPI: Core revision 20080609
[    0.013505] ACPI: Checking initramfs for custom DSDT
[    0.335866] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.375558] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[    0.375562] Using local APIC timer interrupts.
[    0.376024] APIC timer calibration result 12499551
[    0.376026] Detected 12.499 MHz APIC timer.
[    0.376107] Brought up 1 CPUs
[    0.376109] Total of 1 processors activated (4399.83 BogoMIPS).
[    0.376249] CPU0 attaching NULL sched-domain.
[    0.376545] net_namespace: 1552 bytes
[    0.376550] Booting paravirtualized kernel on bare hardware
[    0.376699] Time: 11:41:51  Date: 01/04/09
[    0.376738] NET: Registered protocol family 16
[    0.377050] node 0 link 0: io port [1000, ffffff]
[    0.377054] TOM: 0000000040000000 aka 1024M
[    0.377057] node 0 link 0: mmio [a0000, bffff]
[    0.377059] node 0 link 0: mmio [40000000, ffffffff]
[    0.377062] bus: [00,ff] on node 0 link 0
[    0.377064] bus: 00 index 0 io port: [0, ffff]
[    0.377065] bus: 00 index 1 mmio: [a0000, bffff]
[    0.377067] bus: 00 index 2 mmio: [40000000, fcffffffff]
[    0.377076] ACPI: bus type pci registered
[    0.377164] PCI: Using configuration type 1 for base access
[    0.378465] ACPI: EC: Look up EC in DSDT
[    0.381276] ACPI Warning (dsobject-0501): Package List length (CA) larger than NumElements count (4), truncated
[    0.381280]  [20080609]
[    0.384818] ACPI: Interpreter enabled
[    0.384821] ACPI: (supports S0 S1 S3 S4 S5)
[    0.384837] ACPI: Using IOAPIC for interrupt routing
[    0.392241] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.392326] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.392454] pci 0000:00:03.1: quirk: region 0800-083f claimed by ali7101 ACPI
[    0.392478] PCI: 0000:00:04.0 reg 10 io port: [d800, d8ff]
[    0.392483] PCI: 0000:00:04.0 reg 14 32bit mmio: [febff000, febfffff]
[    0.392506] pci 0000:00:04.0: supports D1
[    0.392507] pci 0000:00:04.0: supports D2
[    0.392509] pci 0000:00:04.0: PME# supported from D2 D3hot D3cold
[    0.392513] pci 0000:00:04.0: PME# disabled
[    0.392531] PCI: 0000:00:0d.0 reg 10 io port: [d400, d4ff]
[    0.392535] PCI: 0000:00:0d.0 reg 14 32bit mmio: [febfec00, febfecff]
[    0.392549] pci 0000:00:0d.0: PME# supported from D3hot D3cold
[    0.392552] pci 0000:00:0d.0: PME# disabled
[    0.392564] PCI: 0000:00:0e.0 reg 10 io port: [1f0, 1ff]
[    0.392567] PCI: 0000:00:0e.0 reg 14 io port: [3f4, 3f7]
[    0.392570] PCI: 0000:00:0e.0 reg 18 io port: [170, 17f]
[    0.392574] PCI: 0000:00:0e.0 reg 1c io port: [374, 377]
[    0.392577] PCI: 0000:00:0e.0 reg 20 io port: [ff00, ff0f]
[    0.392593] PCI: 0000:00:0e.1 reg 10 io port: [ec00, ec07]
[    0.392596] PCI: 0000:00:0e.1 reg 14 io port: [e800, e803]
[    0.392600] PCI: 0000:00:0e.1 reg 18 io port: [e400, e407]
[    0.392603] PCI: 0000:00:0e.1 reg 1c io port: [e000, e003]
[    0.392607] PCI: 0000:00:0e.1 reg 20 io port: [dc00, dc0f]
[    0.392624] PCI: 0000:00:0f.0 reg 10 32bit mmio: [febfd000, febfdfff]
[    0.392645] PCI: 0000:00:0f.1 reg 10 32bit mmio: [febfc000, febfcfff]
[    0.392667] PCI: 0000:00:0f.2 reg 10 32bit mmio: [febfb000, febfbfff]
[    0.392694] PCI: 0000:00:0f.3 reg 10 32bit mmio: [febfe800, febfe8ff]
[    0.392711] pci 0000:00:0f.3: PME# supported from D0 D3hot D3cold
[    0.392713] pci 0000:00:0f.3: PME# disabled
[    0.392792] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.392796] PCI: 0000:01:00.0 reg 14 32bit mmio: [e0000000, efffffff]
[    0.392808] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe9e0000, fe9fffff]
[    0.392838] PCI: bridge 0000:00:01.0 32bit mmio: [fc900000, fe9fffff]
[    0.392842] PCI: bridge 0000:00:01.0 32bit mmio pref: [d4800000, f47fffff]
[    0.392870] PCI: 0000:02:06.0 reg 10 32bit mmio: [feaf0000, feafffff]
[    0.392915] pci 0000:00:02.0: transparent bridge
[    0.392919] PCI: bridge 0000:00:02.0 32bit mmio: [fea00000, feafffff]
[    0.392934] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.393060] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.393136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HTT_._PRT]
[    0.402090] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.402259] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.402424] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.402589] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.402753] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.402918] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.403082] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.403246] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[    0.403410] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.403568] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - DB, should be CD [20080609]
[    0.403576] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.403610] pnp: PnP ACPI init
[    0.403619] ACPI: bus type pnp registered
[    0.408180] pnp: PnP ACPI: found 15 devices
[    0.408182] ACPI: ACPI bus type pnp unregistered
[    0.408551] PCI: Using ACPI for IRQ routing
[    0.408562] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.416093] NET: Registered protocol family 8
[    0.416095] NET: Registered protocol family 20
[    0.416128] NetLabel: Initializing
[    0.416129] NetLabel:  domain hash size = 128
[    0.416131] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.416149] NetLabel:  unlabeled traffic allowed by default
[    0.416191] agpgart-amd64 0000:00:00.0: AGP bridge [10b9/1689]
[    0.416197] agpgart-amd64 0000:00:00.0: setting up ULi AGP
[    0.418719] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    0.419356] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.419358]    actual entries 65586
[    0.419491] AppArmor: AppArmor Filesystem Enabled
[    0.419508] ACPI: RTC can wake from S4
[    0.428057] system 00:08: ioport range 0x400-0x40f has been reserved
[    0.428059] system 00:08: ioport range 0x480-0x48f has been reserved
[    0.428062] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.428069] system 00:08: ioport range 0x800-0x87f could not be reserved
[    0.428072] system 00:08: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.428079] system 00:09: iomem range 0xffbc0000-0xffbfffff could not be reserved
[    0.428081] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.428084] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.428092] system 00:0d: ioport range 0x680-0x6ff has been reserved
[    0.428094] system 00:0d: ioport range 0x295-0x296 has been reserved
[    0.428101] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.428103] system 00:0e: iomem range 0xc0000-0xdffff has been reserved
[    0.428105] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.428108] system 00:0e: iomem range 0x100000-0x3fffffff could not be reserved
[    0.433122] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.433124] pci 0000:00:01.0:   IO window: disabled
[    0.433129] pci 0000:00:01.0:   MEM window: 0xfc900000-0xfe9fffff
[    0.433132] pci 0000:00:01.0:   PREFETCH window: 0x000000d4800000-0x000000f47fffff
[    0.433138] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.433139] pci 0000:00:02.0:   IO window: disabled
[    0.433143] pci 0000:00:02.0:   MEM window: 0xfea00000-0xfeafffff
[    0.433146] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.433159] pci 0000:00:01.0: setting latency timer to 64
[    0.433164] pci 0000:00:02.0: setting latency timer to 64
[    0.433167] bus: 00 index 0 io port: [0, ffff]
[    0.433169] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.433170] bus: 01 index 0 mmio: [0, 0]
[    0.433172] bus: 01 index 1 mmio: [fc900000, fe9fffff]
[    0.433174] bus: 01 index 2 mmio: [d4800000, f47fffff]
[    0.433175] bus: 01 index 3 mmio: [0, 0]
[    0.433177] bus: 02 index 0 mmio: [0, 0]
[    0.433178] bus: 02 index 1 mmio: [fea00000, feafffff]
[    0.433180] bus: 02 index 2 mmio: [0, 0]
[    0.433181] bus: 02 index 3 io port: [0, ffff]
[    0.433183] bus: 02 index 4 mmio: [0, ffffffffffffffff]
[    0.433199] NET: Registered protocol family 2
[    0.472107] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.472709] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.475086] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.476280] TCP: Hash tables configured (established 131072 bind 65536)
[    0.476284] TCP reno registered
[    0.488130] NET: Registered protocol family 1
[    0.488271] checking if image is initramfs... it is
[    0.936035] Switched to high resolution mode on CPU 0
[    1.155229] Freeing initrd memory: 8469k freed
[    1.165912] audit: initializing netlink socket (disabled)
[    1.165934] type=2000 audit(1231069312.164:1): initialized
[    1.171343] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.173715] VFS: Disk quotas dquot_6.5.1
[    1.173813] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.173934] msgmni has been set to 2000
[    1.174073] io scheduler noop registered
[    1.174075] io scheduler anticipatory registered
[    1.174077] io scheduler deadline registered
[    1.174183] io scheduler cfq registered (default)
[    1.232030] pci 0000:01:00.0: Boot video device
[    1.266362] Linux agpgart interface v0.103
[    1.266369] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.266530] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.267213] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.268954] brd: module loaded
[    1.269024] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.269156] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.271708] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.271714] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.276155] mice: PS/2 mouse device common for all mice
[    1.276272] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.276298] rtc0: alarms up to one month
[    1.276334] cpuidle: using governor ladder
[    1.276336] cpuidle: using governor menu
[    1.276725] TCP cubic registered
[    1.276936] registered taskstats version 1
[    1.277065]   Magic number: 9:565:680
[    1.277210] rtc_cmos 00:02: setting system clock to 2009-01-04 11:41:52 UTC (1231069312)
[    1.277214] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.277215] EDD information not available.
[    1.277249] Freeing unused kernel memory: 540k freed
[    1.277666] Write protecting the kernel read-only data: 4352k
[    1.302957] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.516095] fuse init (API version 7.9)
[    1.679409] processor ACPI0007:00: registered as cooling_device0
[    2.227815] No dock devices found.
[    2.260173] SCSI subsystem initialized
[    2.368034] libata version 3.00 loaded.
[    2.371099] usbcore: registered new interface driver usbfs
[    2.371130] usbcore: registered new interface driver hub
[    2.380213] sata_uli 0000:00:0e.1: version 1.3
[    2.380234] sata_uli 0000:00:0e.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.399127] usbcore: registered new device driver usb
[    2.408040] scsi0 : sata_uli
[    2.432358] scsi1 : sata_uli
[    2.432445] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 19
[    2.432448] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 19
[    2.442386] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.212063] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.220360] ata2.00: ATA-7: Hitachi HDT725040VLA360, V5COA52A, max UDMA/133
[    3.220364] ata2.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.236366] ata2.00: configured for UDMA/133
[    3.236427] isa bounce pool size: 16 pages
[    3.236525] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDT72504 V5CO PQ: 0 ANSI: 5
[    3.236704] pata_ali 0000:00:0e.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.236864] scsi2 : pata_ali
[    3.236924] scsi3 : pata_ali
[    3.239958] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    3.239960] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    3.404439] ata3.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    3.404444] ata3.00: 160086528 sectors, multi 16: LBA 
[    3.420361] ata3.00: configured for UDMA/133
[    3.592539] ata4.00: ATAPI: BENQ    DVD DD DW1620, B7S9, max UDMA/33
[    3.592550] ata4.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    3.592553] ata4.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    3.592564] ata4.01: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-105S 0122, E1.22, max UDMA/33
[    3.592574] ata4.01: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    3.592576] ata4.01: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    3.608473] ata4.00: configured for UDMA/33
[    3.624241] ata4.01: configured for UDMA/33
[    3.624372] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    3.626817] scsi 3:0:0:0: CD-ROM            BENQ     DVD DD DW1620    B7S9 PQ: 0 ANSI: 5
[    3.628791] scsi 3:0:1:0: CD-ROM            PIONEER  DVD-ROM DVD-105F 1.22 PQ: 0 ANSI: 5
[    3.634795] ohci_hcd 0000:00:0f.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.634813] ohci_hcd 0000:00:0f.0: OHCI Host Controller
[    3.634884] ohci_hcd 0000:00:0f.0: new USB bus registered, assigned bus number 1
[    3.634921] ohci_hcd 0000:00:0f.0: irq 20, io mem 0xfebfd000
[    3.637819] scsi 1:0:0:0: Attached scsi generic sg0 type 0
[    3.637855] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    3.637890] scsi 3:0:0:0: Attached scsi generic sg2 type 5
[    3.637925] scsi 3:0:1:0: Attached scsi generic sg3 type 5
[    3.655457] Driver 'sd' needs updating - please use bus_type methods
[    3.655611] sd 1:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[    3.655627] sd 1:0:0:0: [sda] Write Protect is off
[    3.655630] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.655652] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.655722] sd 1:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[    3.655735] sd 1:0:0:0: [sda] Write Protect is off
[    3.655737] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.655758] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.655762]  sda: sda1
[    3.676092] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.676192] sd 2:0:0:0: [sdb] 160086528 512-byte hardware sectors (81964 MB)
[    3.676208] sd 2:0:0:0: [sdb] Write Protect is off
[    3.676211] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.676234] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.676286] sd 2:0:0:0: [sdb] 160086528 512-byte hardware sectors (81964 MB)
[    3.676299] sd 2:0:0:0: [sdb] Write Protect is off
[    3.676301] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.676322] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.676326]  sdb:<6>usb usb1: configuration #1 chosen from 1 choice
[    3.690243] hub 1-0:1.0: USB hub found
[    3.690256] hub 1-0:1.0: 3 ports detected
[    3.693133]  sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    3.719624] sd 2:0:0:0: [sdb] Attached SCSI disk
[    3.792363] ohci_hcd 0000:00:0f.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.792383] ohci_hcd 0000:00:0f.1: OHCI Host Controller
[    3.792408] ohci_hcd 0000:00:0f.1: new USB bus registered, assigned bus number 2
[    3.792445] ohci_hcd 0000:00:0f.1: irq 21, io mem 0xfebfc000
[    3.850196] usb usb2: configuration #1 chosen from 1 choice
[    3.850227] hub 2-0:1.0: USB hub found
[    3.850240] hub 2-0:1.0: 3 ports detected
[    3.952287] ohci_hcd 0000:00:0f.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.952309] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[    3.952334] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 3
[    3.952373] ohci_hcd 0000:00:0f.2: irq 22, io mem 0xfebfb000
[    4.010824] usb usb3: configuration #1 chosen from 1 choice
[    4.011299] hub 3-0:1.0: USB hub found
[    4.011312] hub 3-0:1.0: 3 ports detected
[    4.113384] ehci_hcd 0000:00:0f.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    4.113403] ehci_hcd 0000:00:0f.3: EHCI Host Controller
[    4.113434] ehci_hcd 0000:00:0f.3: new USB bus registered, assigned bus number 4
[    4.136012] ehci_hcd 0000:00:0f.3: debug port 1
[    4.136041] ehci_hcd 0000:00:0f.3: irq 23, io mem 0xfebfe800
[    4.148006] ehci_hcd 0000:00:0f.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.148151] usb usb4: configuration #1 chosen from 1 choice
[    4.148176] hub 4-0:1.0: USB hub found
[    4.148186] hub 4-0:1.0: 8 ports detected
[    4.345036] Driver 'sr' needs updating - please use bus_type methods
[    4.347742] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.347746] Uniform CD-ROM driver Revision: 3.20
[    4.347853] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    4.350610] sr1: scsi3-mmc drive: 16x/40x cd/rw xa/form2 cdda tray
[    4.350731] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    4.730339] PM: Starting manual resume from disk
[    4.730344] PM: Resume from partition 8:23
[    4.730345] PM: Checking hibernation image.
[    4.730537] PM: Resume from disk failed.
[    4.767647] kjournald starting.  Commit interval 5 seconds
[    4.767673] EXT3-fs: mounted filesystem with ordered data mode.
[   11.691654] udevd version 124 started
[   12.513730] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
[   12.513780] uli526x 0000:00:0d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.534866] eth0: ULi M5263 at pci0000:00:0d.0, 00:0b:6a:a3:4b:bc, irq 17.
[   12.560171] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.685250] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.696764] ACPI: Power Button (FF) [PWRF]
[   12.696925] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.712061] ACPI: Power Button (CM) [PWRB]
[   12.744321] isp1760 0000:00:03.1: enabling device (0000 -> 0001)
[   12.801230] ali1563_smbus 0000:00:03.0: Found ALi1563 SMBus at 0x0400
[   12.846597] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.936203] ali1535_smbus 0000:00:03.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   12.936208] ali1535_smbus 0000:00:03.1: ALI1535 not detected, module not inserted.
[   13.074614] ali15x3_smbus 0000:00:03.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   13.074620] ali15x3_smbus 0000:00:03.1: ALI15X3 not detected, module not inserted.
[   13.201515] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   13.401974] parport_pc 00:06: reported by Plug and Play ACPI
[   13.402080] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   13.551322] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   13.551330] ndiswrapper (load_sys_files:206): couldn't prepare driver 'wn6201'
[   13.551977] ndiswrapper (load_wrap_driver:108): couldn't load driver wn6201; check system log for messages from 'loadndisdriver'
[   13.552079] usbcore: registered new interface driver ndiswrapper
[   13.945766] Symbol init_mm is marked as UNUSED, however this module is using it.
[   13.945772] This symbol will go away in the future.
[   13.945774] Please evalute if this is the right api to use and if it really is, submit a report the linux kernel mailinglist together with submitting your code for inclusion.
[   14.284719] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   14.343706] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.343955] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.12  Thu Jul 17 18:10:24 PDT 2008
[   14.517553] Intel ICH 0000:00:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.655715] input: GenPS/2 Genius Mouse as /devices/platform/i8042/serio1/input/input5
[   15.532036] AC'97 1 does not respond - RESET
[   15.532501] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   15.532508] Unable to initialize codec #1
[   15.588038] intel8x0_measure_ac97_clock: measured 54998 usecs
[   15.588043] intel8x0: clocking to 48000
[   17.632249] lp0: using parport0 (interrupt-driven).
[   17.872914] Adding 2996080k swap on /dev/sdb7.  Priority:-1 extents:1 across:2996080k
[   18.454289] EXT3 FS on sdb6, internal journal
[   19.439059] type=1505 audit(1231069330.937:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3948
[   19.613644] type=1505 audit(1231069331.113:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3953
[   19.613946] type=1505 audit(1231069331.113:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3953
[   19.771836] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.069353] NET: Registered protocol family 17
[   22.828362] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex
[   29.092855] NET: Registered protocol family 10
[   29.093293] lo: Disabled Privacy Extensions
[   29.533079] ACPI: WMI: Mapper loaded
[   29.794769] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[   29.794819] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x2
[   29.794821] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x6
[   29.794823] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   29.794825] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0xa
[   30.651397] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   30.886305] ppdev: user-space parallel port driver
[   33.136247] Marking TSC unstable due to cpufreq changes
[   33.932020] Clocksource tsc unstable (delta = -90922473 ns)
[   34.267148] Bluetooth: Core ver 2.13
[   34.269663] NET: Registered protocol family 31
[   34.269669] Bluetooth: HCI device and connection manager initialized
[   34.269674] Bluetooth: HCI socket layer initialized
[   34.283298] Bluetooth: L2CAP ver 2.11
[   34.283304] Bluetooth: L2CAP socket layer initialized
[   34.294806] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.294812] Bluetooth: BNEP filters: protocol multicast
[   34.324918] Bridge firewalling registered
[   34.337852] Bluetooth: SCO (Voice Link) ver 0.6
[   34.337858] Bluetooth: SCO socket layer initialized
[   34.534788] Bluetooth: RFCOMM socket layer initialized
[   34.535844] Bluetooth: RFCOMM TTY layer initialized
[   34.535852] Bluetooth: RFCOMM ver 1.10
[   37.495944] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   37.495967] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   37.496048] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   39.692018] eth0: no IPv6 routers present
[   62.401700] ISO 9660 Extensions: Microsoft Joliet Level 3
[   62.446836] ISOFS: changing to secondary root
[  114.668026] usb 2-2: new full speed USB device using ohci_hcd and address 2
[  114.887198] usb 2-2: configuration #1 chosen from 1 choice
[  136.708143] ppdev0: registered pardevice
[  136.756036] ppdev0: unregistered pardevice
[  139.160355] ppdev0: registered pardevice
[  139.208221] ppdev0: unregistered pardevice
[  139.268575] ppdev0: registered pardevice
[  139.316389] ppdev0: unregistered pardevice
[  933.588330] usb 2-2: USB disconnect, address 2
[/QUOTE]

> root@Ubuntu:/home/kevin/Desktop# sudo lshw -c network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
  *-network
       description: Ethernet interface
       product: ULi 1689,1573 integrated ethernet.
       vendor: ALi Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 40
       serial: 00:0b:6a:a3:4b:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=uli526x driverversion=0.9.3 duplex=full ip=192.168.1.168 latency=32 link=yes maxlatency=40 mingnt=20 module=uli526x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:d2:47:a5:2d:a0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


> root@Ubuntu:/home/kevin/Desktop# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


> root@Ubuntu:/home/kevin/Desktop# lsb_release -d
Description:	Ubuntu 8.10


> root@Ubuntu:/home/kevin/Desktop# uname -mr
2.6.27-11-generic x86_64


> root@Ubuntu:/home/kevin/Desktop# $ lsb_release -d
bash: $: command not found

root@Ubuntu:/home/kevin/Desktop# lsb_release -d
Description:	Ubuntu 8.10
root@Ubuntu:/home/kevin/Desktop# $ uname -mr
bash: $: command not found
root@Ubuntu:/home/kevin/Desktop# uname -mr
2.6.27-11-generic x86_64
root@Ubuntu:/home/kevin/Desktop# $ sudo /etc/init.d/networking restart
bash: $: command not found
root@Ubuntu:/home/kevin/Desktop# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4050
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:6a:a3:4b:bc
Sending on   LPF/eth0/00:0b:6a:a3:4b:bc
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:6a:a3:4b:bc
Sending on   LPF/eth0/00:0b:6a:a3:4b:bc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.168 from 192.168.1.1
DHCPREQUEST of 192.168.1.168 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.168 from 192.168.1.1
bound to 192.168.1.168 -- renewal in 34283 seconds.



Hope somebody can help, I have spent hours trying different things on the forums and still I am stuck.  If you need anything else from me, just let me know.  Thanks kev.

---

