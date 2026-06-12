---
title: "D-Link DSL-2640B wireless network NOT detected"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by jdackle on 2009-04-10
Hi,

Here's a short description:

The said router was configured through it's web-interface in Linux. To connect to this in-built interface, I connected the router to the PC through an Ethernet cable.

The conection is fine in Linux, BUT ONLY through the said Ethernet cable.

The network is detected WIRELESS in Windows Vista (no cable pluged in) and connection is made and sustained normally.

The wireless network is NOT detected in Ubuntu (nor, consequently, possible to connect to it).
HOWEVER, other wireless networks (say in several coffee-shops) ARE detected automatically and I connect to them effortlessly, FROM Ubuntu! (usually with Thomson wireless-routers).

Hence, I am assuming this is NOT a problem with my PC's Atheros wireless receptor (see details below) NOR hardware incompatibility, *per se*, between the DSL-2640B wireless-router and the Atheros ... wireless-receptor.
There should be something I should configure differently in that connection though.

Any clues (or direct sollution... :lolflag:) aprecciated.


Infos according to the forum's specified canon follow:

_1 ) Machine Brand and Model (PC/Laptop):_
HP Pavilion dv6710ep Notebook
P/N (Product Number, NOT Serial Number): KN078EA#AB9

_2 ) Wireless Brand, Model and Wireless Chipset:_
From *$ lspci*:
```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```
**NOTE: Chipset setup (and properly working as stated above) according to: [http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/)**

_3 ) check interface:_
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:fa:e8:2a  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fefa:e82a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4459682 (4.2 MB)  TX bytes:1236279 (1.1 MB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8200 (8.0 KB)  TX bytes:8200 (8.0 KB)
``````
lo        no wireless extensions.

eth0      no wireless extensions.

```
_4 ) Check for modules:_
*Note: I've boldified the modules *I think* may be related (wlan, eth and ath).*
```
$ lsmod
Module                  Size  Used by
ipv6                  267908  10 
binfmt_misc            12808  1 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         346136  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
**wlan                  236272  0 **
snd_seq_dummy           4868  0 
nvidia               7825536  26 
serio_raw               7940  0 
**ath_hal               192592  0** 
snd_seq_oss            35584  0 
uvcvideo               58116  0 
psmouse                40336  0 
agpgart                34760  1 nvidia
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
k8temp                  6656  0 
snd_seq_midi            9376  0 
pcspkr                  4224  0 
i2c_core               24832  1 nvidia
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
v4l2_common            18304  2 uvcvideo,videodev
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
sdhci                  19076  0 
ricoh_mmc               4352  0 
evdev                  13056  7 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mmc_core               51460  1 sdhci
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
video                  19856  8 
wmi_acer                9644  0 
battery                14212  0 
output                  4736  1 video
button                  9232  0 
ac                      6916  0 
usbserial              35688  0 
iptable_nat             8324  0 
nf_nat                 20396  1 iptable_nat
nf_conntrack_ipv4      19080  2 iptable_nat
nf_conntrack           66752  3 iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
iptable_filter          3840  0 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  2 iptable_nat,ip_tables
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sg                     36880  0 
sd_mod                 30720  6 
pata_amd               14212  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
pata_acpi               8320  0 
ahci                   28548  5 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159600  4 pata_amd,pata_acpi,ahci,ata_generic
**forcedeth              51980  0 **
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ohci_hcd               26640  0 
ehci_hcd               37900  0 
usbcore               146412  6 uvcvideo,usbserial,usbhid,ohci_hcd,ehci_hcd
thermal                16796  0 
processor              36488  4 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  9 
```
*Note:*The two modules (ath_pci and wlan_scan_sta) mentioned in the said howto were NOT present in the listing. Trying to load each one now gave different results:
ath_pci:```
$ sudo modprobe ath_pci
[sudo] password for ******: 
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-23-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
wlan_scan_sta WAS correctly inserted. However, upon reboot was NOT present anymore.

_5 ) Kernel boot messages_
WithOUT ethernet cable pluged into the router:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 21:47:28 UTC 2009 (Ubuntu 2.6.24-23.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf50000 (usable)
[    0.000000]  BIOS-e820: 000000007bf50000 - 000000007bf65000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bf65000 - 000000007bf66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf66000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1087MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8220
[    0.000000] Entering add_active_range(0, 0, 507728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   507728
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   507728
[    0.000000] On node 0 totalpages: 507728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2174 pages used for memmap
[    0.000000]   HighMem zone: 276178 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8250 checksum 0
[    0.000000] ACPI: RSDP 000F8250, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 7BF5C0CE, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 7BF649BA, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 7BF5C13A, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 7BF65FC0, 0040
[    0.000000] ACPI: TCPA 7BF64AAE, 0032 (r1 Phoeni  x        6040000  TL         0)
[    0.000000] ACPI: SRAT 7BF64AE0, 00A0 (r1 AMD    HAMMER    6040000 AMD         1)
[    0.000000] ACPI: SSDT 7BF64B80, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 7BF64D86, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 7BF64DC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 7BF64DFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7BF64E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 7BF64E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503762
[    0.000000] Kernel command line: root=UUID=c7c7e608-a5ad-470e-9a78-19753432fb0b ro quiet splash locale=pt_PT pci=assign-busses
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1900.248 MHz processor.
[   41.559542] spurious 8259A interrupt: IRQ7.
[   41.562856] Console: colour VGA+ 80x25
[   41.562859] console [tty0] enabled
[   41.563136] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   41.563585] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   41.646409] Memory: 2001472k/2030912k available (2179k kernel code, 28208k reserved, 1008k data, 368k init, 1113408k highmem)
[   41.646416] virtual kernel memory layout:
[   41.646417]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   41.646419]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   41.646420]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   41.646421]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   41.646422]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   41.646423]       .data : 0xc0320c78 - 0xc041cdc4   (1008 kB)
[   41.646424]       .text : 0xc0100000 - 0xc0320c78   (2179 kB)
[   41.646427] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   41.646459] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   41.646596] hpet clockevent registered
[   41.726467] Calibrating delay using timer specific routine.. 3804.25 BogoMIPS (lpj=7608503)
[   41.726486] Security Framework initialized
[   41.726491] SELinux:  Disabled at boot.
[   41.726504] AppArmor: AppArmor initialized
[   41.726507] Failure registering capabilities with primary security module.
[   41.726515] Mount-cache hash table entries: 512
[   41.726617] Initializing cgroup subsys ns
[   41.726621] Initializing cgroup subsys cpuacct
[   41.726629] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   41.726638] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   41.726641] CPU: L2 Cache: 256K (64 bytes/line)
[   41.726643] CPU 0(2) -> Core 0
[   41.726645] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   41.726654] Compat vDSO mapped to ffffe000.
[   41.726663] Checking 'hlt' instruction... OK.
[   41.742688] SMP alternatives: switching to UP code
[   41.743804] Early unpacking initramfs... done
[   42.064191] ACPI: Core revision 20070126
[   42.064275] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   42.473256] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[   42.473273] SMP alternatives: switching to SMP code
[   42.473700] Booting processor 1/1 eip 3000
[   42.484061] Initializing CPU#1
[   42.561457] Calibrating delay using timer specific routine.. 3800.39 BogoMIPS (lpj=7600797)
[   42.561463] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   42.561470] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   42.561472] CPU: L2 Cache: 256K (64 bytes/line)
[   42.561474] CPU 1(2) -> Core 1
[   42.561476] AMD C1E detected late. 	Force timer broadcast.
[   42.561477] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   42.561212] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[   42.561228] Total of 2 processors activated (7604.65 BogoMIPS).
[   42.561467] ENABLING IO-APIC IRQs
[   42.561699] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   42.601471] Brought up 2 CPUs
[   42.601517] CPU0 attaching sched-domain:
[   42.601520]  domain 0: span 03
[   42.601521]   groups: 01 02
[   42.601524] CPU1 attaching sched-domain:
[   42.601526]  domain 0: span 03
[   42.601528]   groups: 02 01
[   42.601715] net_namespace: 64 bytes
[   42.601723] Booting paravirtualized kernel on bare hardware
[   42.602172] Time: 14:59:11  Date: 04/10/09
[   42.602195] NET: Registered protocol family 16
[   42.602366] EISA bus registered
[   42.602370] ACPI: bus type pci registered
[   42.623337] PCI: PCI BIOS revision 3.00 entry at 0xfddad, last bus=5
[   42.623339] PCI: Using configuration type 1
[   42.623347] Setting up standard PCI resources
[   42.625049] ACPI: EC: Look up EC in DSDT
[   42.626803] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   42.627369] ACPI: Interpreter enabled
[   42.627372] ACPI: (supports S0 S3 S4 S5)
[   42.627383] ACPI: Using IOAPIC for interrupt routing
[   42.628317] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   42.638167] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   42.638170] ACPI: EC: driver started in interrupt mode
[   42.638226] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   42.639131] PCI: Transparent bridge - 0000:00:08.0
[   42.639308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   42.639391] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   42.639410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   42.639439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   42.670422] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[   42.670618] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[   42.670810] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[   42.671001] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[   42.671193] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[   42.671385] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   42.671576] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[   42.671768] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[   42.671964] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[   42.672155] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[   42.672346] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[   42.672542] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[   42.672733] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[   42.672924] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[   42.673115] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[   42.673307] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[   42.673498] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[   42.673703] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[   42.673900] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[   42.674045] Linux Plug and Play Support v0.97 (c) Adam Belay
[   42.674076] pnp: PnP ACPI init
[   42.674083] ACPI: bus type pnp registered
[   42.678578] pnp: PnP ACPI: found 12 devices
[   42.678580] ACPI: ACPI bus type pnp unregistered
[   42.678583] PnPBIOS: Disabled by ACPI PNP
[   42.678810] PCI: Using ACPI for IRQ routing
[   42.678813] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   42.709595] NET: Registered protocol family 8
[   42.709597] NET: Registered protocol family 20
[   42.709633] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   42.709637] hpet0: 3 32-bit timers, 25000000 Hz
[   42.710678] AppArmor: AppArmor Filesystem Enabled
[   42.713193] Time: hpet clocksource has been installed.
[   42.713198] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   42.713201] Could not switch to high resolution mode on CPU 0
[   42.717577] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   42.717581] Could not switch to high resolution mode on CPU 1
[   42.725602] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[   42.725608] system 00:03: ioport range 0x1000-0x107f has been reserved
[   42.725611] system 00:03: ioport range 0x1080-0x10ff has been reserved
[   42.725614] system 00:03: ioport range 0x1400-0x147f has been reserved
[   42.725616] system 00:03: ioport range 0x1480-0x14ff has been reserved
[   42.725619] system 00:03: ioport range 0x1800-0x187f has been reserved
[   42.725621] system 00:03: ioport range 0x1880-0x18ff has been reserved
[   42.725627] system 00:04: ioport range 0x360-0x361 has been reserved
[   42.725632] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   42.725643] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[   42.725646] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   42.725649] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[   42.725652] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[   42.725655] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   42.725657] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[   42.756031] PCI: Bridge: 0000:00:08.0
[   42.756033]   IO window: disabled.
[   42.756036]   MEM window: f6100000-f61fffff
[   42.756038]   PREFETCH window: disabled.
[   42.756041] PCI: Bridge: 0000:00:0c.0
[   42.756043]   IO window: 4000-4fff
[   42.756046]   MEM window: f2000000-f3ffffff
[   42.756048]   PREFETCH window: f0000000-f1ffffff
[   42.756051] PCI: Bridge: 0000:00:0d.0
[   42.756052]   IO window: disabled.
[   42.756054]   MEM window: f6000000-f60fffff
[   42.756056]   PREFETCH window: disabled.
[   42.756066] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   42.756076] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   42.756083] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   42.756094] NET: Registered protocol family 2
[   42.797510] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   42.797770] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   42.798417] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   42.798750] TCP: Hash tables configured (established 131072 bind 65536)
[   42.798753] TCP reno registered
[   42.813542] checking if image is initramfs... it is
[   43.433530] Freeing initrd memory: 7329k freed
[   43.433625] Simple Boot Flag at 0x36 set to 0x1
[   43.434243] audit: initializing netlink socket (disabled)
[   43.434253] audit(1239375551.384:1): initialized
[   43.434420] highmem bounce pool size: 64 pages
[   43.436225] VFS: Disk quotas dquot_6.5.1
[   43.436291] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   43.436421] io scheduler noop registered
[   43.436424] io scheduler anticipatory registered
[   43.436425] io scheduler deadline registered
[   43.436435] io scheduler cfq registered (default)
[   43.436466] pci 0000:00:00.0: Enabling HT MSI Mapping
[   43.436601] pci 0000:00:07.0: Enabling HT MSI Mapping
[   43.436615] pci 0000:00:08.0: Enabling HT MSI Mapping
[   43.436629] pci 0000:00:09.0: Enabling HT MSI Mapping
[   43.436644] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   43.436658] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   43.436672] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   43.436686] Boot video device is 0000:00:12.0
[   43.436796] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   43.436819] assign_interrupt_mode Found MSI capability
[   43.436838] Allocate Port Service[0000:00:0c.0:pcie00]
[   43.436898] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   43.436919] assign_interrupt_mode Found MSI capability
[   43.436935] Allocate Port Service[0000:00:0d.0:pcie00]
[   43.437147] isapnp: Scanning for PnP cards...
[   43.789144] isapnp: No Plug & Play device found
[   43.816967] Real Time Clock Driver v1.12ac
[   43.817141] hpet_resources: 0xfed00000 is busy
[   43.817174] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   43.818281] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   43.818343] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   43.818433] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   43.845772] serio: i8042 KBD port at 0x60,0x64 irq 1
[   43.845777] serio: i8042 AUX port at 0x60,0x64 irq 12
[   43.859723] mice: PS/2 mouse device common for all mice
[   43.859840] EISA: Probing bus 0 at eisa.0
[   43.859846] Cannot allocate resource for EISA slot 1
[   43.859850] Cannot allocate resource for EISA slot 3
[   43.859852] Cannot allocate resource for EISA slot 4
[   43.859864] EISA: Detected 0 cards.
[   43.859867] cpuidle: using governor ladder
[   43.859869] cpuidle: using governor menu
[   43.859944] NET: Registered protocol family 1
[   43.859966] Using IPI No-Shortcut mode
[   43.859996] registered taskstats version 1
[   43.860106]   Magic number: 5:664:990
[   43.860115]   hash matches device ttyd3
[   43.860234] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   43.860236] EDD information not available.
[   43.860440] Freeing unused kernel memory: 368k freed
[   43.860465] Write protecting the kernel read-only data: 806k
[   43.899640] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   45.086334] fuse init (API version 7.9)
[   45.104080] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   45.104086] ACPI: Processor [CPU0] (supports 8 throttling states)
[   45.104577] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   45.104584] ACPI: Processor [CPU1] (supports 8 throttling states)
[   45.107029] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
[   45.518125] usbcore: registered new interface driver usbfs
[   45.518203] usbcore: registered new interface driver hub
[   45.517900] SCSI subsystem initialized
[   45.524168] usbcore: registered new device driver usb
[   45.525944] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   45.525955] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 16
[   45.525966] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   45.525969] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   45.526237] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   45.526270] ehci_hcd 0000:00:02.1: debug port 1
[   45.526274] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   45.526284] ehci_hcd 0000:00:02.1: irq 16, io mem 0xf6489000
[   45.526335] libata version 3.00 loaded.
[   45.530599] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   45.536487] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   45.536621] usb usb1: configuration #1 chosen from 1 choice
[   45.536643] hub 1-0:1.0: USB hub found
[   45.536650] hub 1-0:1.0: 7 ports detected
[   45.640717] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[   45.640722] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [Z019] -> GSI 22 (level, low) -> IRQ 16
[   45.640734] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   45.640737] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   45.640759] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[   45.640787] ehci_hcd 0000:00:04.1: debug port 1
[   45.640790] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   45.640796] ehci_hcd 0000:00:04.1: irq 16, io mem 0xf6489400
[   45.652286] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   45.652397] usb usb2: configuration #1 chosen from 1 choice
[   45.652424] hub 2-0:1.0: USB hub found
[   45.652430] hub 2-0:1.0: 2 ports detected
[   45.758675] ahci 0000:00:09.0: version 3.0
[   45.759007] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[   45.759016] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 23 (level, low) -> IRQ 17
[   46.063599] usb 2-2: new high speed USB device using ehci_hcd and address 2
[   46.217458] usb 2-2: configuration #1 chosen from 1 choice
[   46.758418] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   46.758423] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[   46.758427] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   46.758751] scsi0 : ahci
[   46.759022] scsi1 : ahci
[   46.759160] scsi2 : ahci
[   46.759290] scsi3 : ahci
[   46.759365] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 221
[   46.759368] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 221
[   46.759371] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 221
[   46.759374] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 221
[   47.397335] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   47.398126] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[   47.398130] ata1.00: 488397168 sectors, multi 16: LBA48 
[   47.398591] ata1.00: configured for UDMA/100
[   47.716796] ata2: SATA link down (SStatus 0 SControl 300)
[   48.036257] ata3: SATA link down (SStatus 0 SControl 300)
[   48.355718] ata4: SATA link down (SStatus 0 SControl 300)
[   48.355824] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[   48.358575] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[   48.358585] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 18 (level, low) -> IRQ 18
[   48.358597] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   48.358601] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   48.358634] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[   48.358650] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[   48.413713] usb usb3: configuration #1 chosen from 1 choice
[   48.413741] hub 3-0:1.0: USB hub found
[   48.413748] hub 3-0:1.0: 7 ports detected
[   48.515856] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[   48.515860] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [Z018] -> GSI 18 (level, low) -> IRQ 18
[   48.515874] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   48.515877] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   48.515901] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[   48.515913] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[   48.573442] usb usb4: configuration #1 chosen from 1 choice
[   48.573467] hub 4-0:1.0: USB hub found
[   48.573474] hub 4-0:1.0: 2 ports detected
[   48.675578] PCI: Enabling device 0000:01:05.0 (0100 -> 0102)
[   48.675888] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   48.675899] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK1] -> GSI 5 (level, low) -> IRQ 5
[   48.727586] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   48.732011] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   48.732355] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   48.732365] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 19
[   48.732371] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   48.823313] usb 3-4: new low speed USB device using ohci_hcd and address 2
[   49.038053] usb 3-4: configuration #1 chosen from 1 choice
[   49.051433] usbcore: registered new interface driver hiddev
[   49.057102] input: USB Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.0/input/input2
[   49.082916] input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:02.0-4
[   49.082934] usbcore: registered new interface driver usbhid
[   49.082938] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   49.251045] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1b:24:fa:e8:2a
[   49.251050] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   49.251400] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   49.254892] pata_amd 0000:00:06.0: version 0.3.10
[   49.254936] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   49.254997] scsi4 : pata_amd
[   49.255052] scsi5 : pata_amd
[   49.255327] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   49.255330] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   49.260218] Driver 'sd' needs updating - please use bus_type methods
[   49.260299] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   49.260311] sd 0:0:0:0: [sda] Write Protect is off
[   49.260314] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   49.260328] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.260370] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   49.260378] sd 0:0:0:0: [sda] Write Protect is off
[   49.260380] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   49.260393] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.260397]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[   49.347588] sd 0:0:0:0: [sda] Attached SCSI disk
[   49.350997] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   49.573931] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[   49.745577] ata5.00: configured for MWDMA2
[   49.745615] ata6: port disabled. ignoring.
[   49.749614] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[   49.749687] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   49.756772] Driver 'sr' needs updating - please use bus_type methods
[   49.774045] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   49.774050] Uniform CD-ROM driver Revision: 3.20
[   49.774104] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   49.909334] Attempting manual resume
[   49.909337] swsusp: Resume From Partition 8:6
[   49.909339] PM: Checking swsusp image.
[   49.909922] PM: Resume from disk failed.
[   49.929812] kjournald starting.  Commit interval 5 seconds
[   49.930205] EXT3-fs: mounted filesystem with ordered data mode.
[   50.001006] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00293da300]
[   56.567087] ip_tables: (C) 2000-2006 Netfilter Core Team
[   56.635966] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   57.208807] usbcore: registered new interface driver usbserial
[   57.208823] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   57.208868] usbcore: registered new interface driver usbserial_generic
[   57.208870] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   57.792122] input: Power Button (FF) as /devices/virtual/input/input3
[   57.811512] ACPI: Power Button (FF) [PWRF]
[   57.811616] input: Sleep Button (CM) as /devices/virtual/input/input4
[   57.843423] ACPI: Sleep Button (CM) [SLPB]
[   57.843532] input: Lid Switch as /devices/virtual/input/input5
[   57.845557] ACPI: Lid Switch [LID]
[   57.845692] input: Power Button (CM) as /devices/virtual/input/input6
[   57.867762] ACPI: Power Button (CM) [PWRB]
[   58.035807] ACPI: AC Adapter [ACAD] (on-line)
[   58.127700] ACPI: Battery Slot [BAT0] (battery absent)
[   58.338220] ACPI: WMI-Acer: Mapper loaded
[   58.651057] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   58.682387] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   59.663483] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   59.703010] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   59.749957] Linux agpgart interface v0.102
[   59.792601] ricoh-mmc: Ricoh MMC Controller disabling driver
[   59.792605] ricoh-mmc: Copyright(c) Philip Langdale
[   59.792682] ricoh-mmc: Ricoh MMC controller found at 0000:01:05.2 [1180:0843] (rev 12)
[   59.792690] ricoh-mmc: Controller is now disabled.
[   60.019120] ath_hal: module license 'Proprietary' taints kernel.
[   60.050509] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   60.088123] sdhci: Secure Digital Host Controller Interface driver
[   60.088127] sdhci: Copyright(c) Pierre Ossman
[   60.088171] sdhci: SDHCI controller found at 0000:01:05.1 [1180:0822] (rev 22)
[   60.088493] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   60.088503] ACPI: PCI Interrupt 0000:01:05.1[B] -> Link [LNK2] -> GSI 7 (level, low) -> IRQ 7
[   60.088520] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   60.088564] mmc0: SDHCI at 0xf6100800 irq 7 DMA
[   60.536336] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   60.536346] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LGPU] -> GSI 16 (level, low) -> IRQ 20
[   60.536354] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   60.536559] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   60.667525] ath_pci: disagrees about version of symbol _ath_hal_attach
[   60.667530] ath_pci: Unknown symbol _ath_hal_attach
[   60.667632] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   60.667634] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   60.668030] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   60.668032] ath_pci: Unknown symbol ath_hal_computetxtime
[   60.668294] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   60.668296] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   60.668483] ath_pci: Unknown symbol _ath_hal_detach
[   60.669071] ath_pci: Unknown symbol ath_hal_print_decoded_register
[   60.669635] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   60.669637] ath_pci: Unknown symbol ath_hal_init_channels
[   60.669881] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   60.669883] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[   60.743777] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   61.515580] Linux video capture interface: v2.00
[   61.681107] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b015)
[   61.683109] usbcore: registered new interface driver uvcvideo
[   61.683114] USB Video Class driver (v0.1.0)
[   61.726359] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   61.726370] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21
[   61.726396] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   62.076579] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   62.151718] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   66.817033] lp: driver loaded but no devices found
[   66.992526] Adding 4000144k swap on /dev/sda6.  Priority:-1 extents:1 across:4000144k
[   67.541397] EXT3 FS on sda7, internal journal
[   70.010714] No dock devices found.
[   70.422228] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 processors (2 cpu cores) (version 2.20.00)
[   70.421949] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x13
[   70.421954] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[   70.421956] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[   70.421958] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1a
[   71.240407] apm: BIOS not found.
[   71.812009] ppdev: user-space parallel port driver
[   72.050458] audit(1239371980.404:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=7496 profile="/usr/sbin/cupsd" namespace="default"
[   73.705957] Clocksource tsc unstable (delta = -289494021 ns)
[   74.444575] eth0: no link during initialization.
[   74.502639] Bluetooth: Core ver 2.11
[   74.502766] NET: Registered protocol family 31
[   74.502768] Bluetooth: HCI device and connection manager initialized
[   74.502773] Bluetooth: HCI socket layer initialized
[   74.528170] Bluetooth: L2CAP ver 2.9
[   74.528175] Bluetooth: L2CAP socket layer initialized
[   74.593565] Bluetooth: RFCOMM socket layer initialized
[   74.593787] Bluetooth: RFCOMM TTY layer initialized
[   74.593791] Bluetooth: RFCOMM ver 1.8
[   93.410342] NET: Registered protocol family 10
[   93.410993] lo: Disabled Privacy Extensions
[   93.411826] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   99.081938] CPU0 attaching NULL sched-domain.
[   99.081947] CPU1 attaching NULL sched-domain.
[   99.103131] CPU0 attaching sched-domain:
[   99.103137]  domain 0: span 03
[   99.103139]   groups: 01 02
[   99.103142] CPU1 attaching sched-domain:
[   99.103143]  domain 0: span 03
[   99.103145]   groups: 02 01
[  138.770244] eth0: link up.
[  138.771404] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  139.685499] NET: Registered protocol family 17
[  150.330348] eth0: no IPv6 routers present
[  261.769979] ath_pci: disagrees about version of symbol _ath_hal_attach
[  261.769989] ath_pci: Unknown symbol _ath_hal_attach
[  261.770101] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  261.770105] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  261.770568] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  261.770573] ath_pci: Unknown symbol ath_hal_computetxtime
[  261.770875] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  261.770878] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  261.771093] ath_pci: Unknown symbol _ath_hal_detach
[  261.771781] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  261.772433] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  261.772435] ath_pci: Unknown symbol ath_hal_init_channels
[  261.772730] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  261.772733] ath_pci: Unknown symbol ath_hal_getwirelessmodes
```
WITH ethernet cable pluged into the router:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 21:47:28 UTC 2009 (Ubuntu 2.6.24-23.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf50000 (usable)
[    0.000000]  BIOS-e820: 000000007bf50000 - 000000007bf65000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bf65000 - 000000007bf66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf66000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1087MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8220
[    0.000000] Entering add_active_range(0, 0, 507728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   507728
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   507728
[    0.000000] On node 0 totalpages: 507728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2174 pages used for memmap
[    0.000000]   HighMem zone: 276178 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8250 checksum 0
[    0.000000] ACPI: RSDP 000F8250, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 7BF5C0CE, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 7BF649BA, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 7BF5C13A, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 7BF65FC0, 0040
[    0.000000] ACPI: TCPA 7BF64AAE, 0032 (r1 Phoeni  x        6040000  TL         0)
[    0.000000] ACPI: SRAT 7BF64AE0, 00A0 (r1 AMD    HAMMER    6040000 AMD         1)
[    0.000000] ACPI: SSDT 7BF64B80, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 7BF64D86, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 7BF64DC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 7BF64DFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7BF64E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 7BF64E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503762
[    0.000000] Kernel command line: root=UUID=c7c7e608-a5ad-470e-9a78-19753432fb0b ro quiet splash locale=pt_PT pci=assign-busses
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1900.197 MHz processor.
[   23.513059] spurious 8259A interrupt: IRQ7.
[   23.516366] Console: colour VGA+ 80x25
[   23.516369] console [tty0] enabled
[   23.516646] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.517095] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.599921] Memory: 2001472k/2030912k available (2179k kernel code, 28208k reserved, 1008k data, 368k init, 1113408k highmem)
[   23.599928] virtual kernel memory layout:
[   23.599929]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   23.599931]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.599932]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.599933]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.599934]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   23.599935]       .data : 0xc0320c78 - 0xc041cdc4   (1008 kB)
[   23.599936]       .text : 0xc0100000 - 0xc0320c78   (2179 kB)
[   23.599939] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.599971] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   23.600108] hpet clockevent registered
[   23.679979] Calibrating delay using timer specific routine.. 3804.25 BogoMIPS (lpj=7608509)
[   23.679998] Security Framework initialized
[   23.680003] SELinux:  Disabled at boot.
[   23.680016] AppArmor: AppArmor initialized
[   23.680020] Failure registering capabilities with primary security module.
[   23.680027] Mount-cache hash table entries: 512
[   23.680130] Initializing cgroup subsys ns
[   23.680133] Initializing cgroup subsys cpuacct
[   23.680142] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   23.680151] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.680153] CPU: L2 Cache: 256K (64 bytes/line)
[   23.680156] CPU 0(2) -> Core 0
[   23.680157] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   23.680167] Compat vDSO mapped to ffffe000.
[   23.680176] Checking 'hlt' instruction... OK.
[   23.696200] SMP alternatives: switching to UP code
[   23.697320] Early unpacking initramfs... done
[   24.017742] ACPI: Core revision 20070126
[   24.017825] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.426801] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[   24.426818] SMP alternatives: switching to SMP code
[   24.427247] Booting processor 1/1 eip 3000
[   24.438546] Initializing CPU#1
[   24.515907] Calibrating delay using timer specific routine.. 3800.37 BogoMIPS (lpj=7600751)
[   24.515914] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   24.515920] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.515922] CPU: L2 Cache: 256K (64 bytes/line)
[   24.515924] CPU 1(2) -> Core 1
[   24.515926] AMD C1E detected late. 	Force timer broadcast.
[   24.515927] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   24.514750] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[   24.514766] Total of 2 processors activated (7604.63 BogoMIPS).
[   24.515006] ENABLING IO-APIC IRQs
[   24.515238] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.555010] Brought up 2 CPUs
[   24.555055] CPU0 attaching sched-domain:
[   24.555058]  domain 0: span 03
[   24.555060]   groups: 01 02
[   24.555063] CPU1 attaching sched-domain:
[   24.555064]  domain 0: span 03
[   24.555066]   groups: 02 01
[   24.555253] net_namespace: 64 bytes
[   24.555261] Booting paravirtualized kernel on bare hardware
[   24.555710] Time: 15:20:28  Date: 04/10/09
[   24.555734] NET: Registered protocol family 16
[   24.555904] EISA bus registered
[   24.555908] ACPI: bus type pci registered
[   24.576921] PCI: PCI BIOS revision 3.00 entry at 0xfddad, last bus=5
[   24.576923] PCI: Using configuration type 1
[   24.576931] Setting up standard PCI resources
[   24.578630] ACPI: EC: Look up EC in DSDT
[   24.580384] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   24.580951] ACPI: Interpreter enabled
[   24.580954] ACPI: (supports S0 S3 S4 S5)
[   24.580965] ACPI: Using IOAPIC for interrupt routing
[   24.582844] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   24.591792] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   24.591795] ACPI: EC: driver started in interrupt mode
[   24.591850] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.592763] PCI: Transparent bridge - 0000:00:08.0
[   24.592940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.593023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   24.593042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   24.593072] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   24.624033] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[   24.624237] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[   24.624430] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[   24.624621] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[   24.624813] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[   24.625005] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   24.625197] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[   24.625389] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[   24.625585] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[   24.625776] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[   24.625967] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[   24.626163] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[   24.626354] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[   24.626545] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[   24.626736] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[   24.626928] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[   24.627120] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[   24.627316] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[   24.627513] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[   24.627657] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.627689] pnp: PnP ACPI init
[   24.627696] ACPI: bus type pnp registered
[   24.631277] pnp: PnP ACPI: found 12 devices
[   24.631280] ACPI: ACPI bus type pnp unregistered
[   24.631283] PnPBIOS: Disabled by ACPI PNP
[   24.631508] PCI: Using ACPI for IRQ routing
[   24.631511] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.664073] NET: Registered protocol family 8
[   24.664074] NET: Registered protocol family 20
[   24.664111] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   24.664115] hpet0: 3 32-bit timers, 25000000 Hz
[   24.665155] AppArmor: AppArmor Filesystem Enabled
[   24.666731] Time: hpet clocksource has been installed.
[   24.666736] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   24.666740] Could not switch to high resolution mode on CPU 0
[   24.672054] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   24.672058] Could not switch to high resolution mode on CPU 1
[   24.680076] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[   24.680082] system 00:03: ioport range 0x1000-0x107f has been reserved
[   24.680085] system 00:03: ioport range 0x1080-0x10ff has been reserved
[   24.680088] system 00:03: ioport range 0x1400-0x147f has been reserved
[   24.680090] system 00:03: ioport range 0x1480-0x14ff has been reserved
[   24.680093] system 00:03: ioport range 0x1800-0x187f has been reserved
[   24.680096] system 00:03: ioport range 0x1880-0x18ff has been reserved
[   24.680102] system 00:04: ioport range 0x360-0x361 has been reserved
[   24.680106] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   24.680118] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[   24.680121] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   24.680124] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[   24.680127] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[   24.680129] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   24.680132] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[   24.710509] PCI: Bridge: 0000:00:08.0
[   24.710510]   IO window: disabled.
[   24.710513]   MEM window: f6100000-f61fffff
[   24.710516]   PREFETCH window: disabled.
[   24.710519] PCI: Bridge: 0000:00:0c.0
[   24.710521]   IO window: 4000-4fff
[   24.710524]   MEM window: f2000000-f3ffffff
[   24.710526]   PREFETCH window: f0000000-f1ffffff
[   24.710528] PCI: Bridge: 0000:00:0d.0
[   24.710530]   IO window: disabled.
[   24.710532]   MEM window: f6000000-f60fffff
[   24.710534]   PREFETCH window: disabled.
[   24.710544] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   24.710555] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   24.710562] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   24.710572] NET: Registered protocol family 2
[   24.755980] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.756243] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.756888] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.757220] TCP: Hash tables configured (established 131072 bind 65536)
[   24.757224] TCP reno registered
[   24.772013] checking if image is initramfs... it is
[   25.391775] Freeing initrd memory: 7329k freed
[   25.391870] Simple Boot Flag at 0x36 set to 0x1
[   25.392484] audit: initializing netlink socket (disabled)
[   25.392494] audit(1239376828.388:1): initialized
[   25.392661] highmem bounce pool size: 64 pages
[   25.394464] VFS: Disk quotas dquot_6.5.1
[   25.394529] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.394646] io scheduler noop registered
[   25.394648] io scheduler anticipatory registered
[   25.394650] io scheduler deadline registered
[   25.394659] io scheduler cfq registered (default)
[   25.394690] pci 0000:00:00.0: Enabling HT MSI Mapping
[   25.394825] pci 0000:00:07.0: Enabling HT MSI Mapping
[   25.394853] pci 0000:00:08.0: Enabling HT MSI Mapping
[   25.394867] pci 0000:00:09.0: Enabling HT MSI Mapping
[   25.394883] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   25.394897] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   25.394911] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   25.394924] Boot video device is 0000:00:12.0
[   25.395031] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   25.395054] assign_interrupt_mode Found MSI capability
[   25.395073] Allocate Port Service[0000:00:0c.0:pcie00]
[   25.395133] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   25.395154] assign_interrupt_mode Found MSI capability
[   25.395170] Allocate Port Service[0000:00:0d.0:pcie00]
[   25.395381] isapnp: Scanning for PnP cards...
[   25.747383] isapnp: No Plug & Play device found
[   25.774840] Real Time Clock Driver v1.12ac
[   25.775016] hpet_resources: 0xfed00000 is busy
[   25.775050] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.776154] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.776216] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.776308] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   25.802740] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.802745] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.818193] mice: PS/2 mouse device common for all mice
[   25.818309] EISA: Probing bus 0 at eisa.0
[   25.818314] Cannot allocate resource for EISA slot 1
[   25.818319] Cannot allocate resource for EISA slot 3
[   25.818321] Cannot allocate resource for EISA slot 4
[   25.818333] EISA: Detected 0 cards.
[   25.818336] cpuidle: using governor ladder
[   25.818338] cpuidle: using governor menu
[   25.818413] NET: Registered protocol family 1
[   25.818435] Using IPI No-Shortcut mode
[   25.818464] registered taskstats version 1
[   25.818575]   Magic number: 5:599:335
[   25.818595]   hash matches device ttyza
[   25.818667]   hash matches device tty56
[   25.818704] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.818706] EDD information not available.
[   25.818909] Freeing unused kernel memory: 368k freed
[   25.818935] Write protecting the kernel read-only data: 806k
[   25.835390] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.039873] fuse init (API version 7.9)
[   27.057794] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   27.057800] ACPI: Processor [CPU0] (supports 8 throttling states)
[   27.059240] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   27.059247] ACPI: Processor [CPU1] (supports 8 throttling states)
[   27.061713] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
[   27.453744] usbcore: registered new interface driver usbfs
[   27.453766] usbcore: registered new interface driver hub
[   27.454475] usbcore: registered new device driver usb
[   27.456338] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   27.456348] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 16
[   27.456360] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   27.456363] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   27.456630] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   27.456660] ehci_hcd 0000:00:02.1: debug port 1
[   27.456664] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   27.456673] ehci_hcd 0000:00:02.1: irq 16, io mem 0xf6489000
[   27.466041] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.466167] usb usb1: configuration #1 chosen from 1 choice
[   27.466192] hub 1-0:1.0: USB hub found
[   27.466198] hub 1-0:1.0: 7 ports detected
[   27.466273] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.486536] SCSI subsystem initialized
[   27.493025] libata version 3.00 loaded.
[   27.570281] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[   27.570286] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [Z019] -> GSI 22 (level, low) -> IRQ 16
[   27.570298] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   27.570302] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   27.570325] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[   27.570351] ehci_hcd 0000:00:04.1: debug port 1
[   27.570355] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   27.570361] ehci_hcd 0000:00:04.1: irq 16, io mem 0xf6489400
[   27.581856] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.581966] usb usb2: configuration #1 chosen from 1 choice
[   27.581989] hub 2-0:1.0: USB hub found
[   27.581995] hub 2-0:1.0: 2 ports detected
[   27.686154] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[   27.686165] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 18 (level, low) -> IRQ 17
[   27.686179] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   27.686182] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   27.686207] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[   27.686223] ohci_hcd 0000:00:02.0: irq 17, io mem 0xf6486000
[   27.743665] usb usb3: configuration #1 chosen from 1 choice
[   27.743690] hub 3-0:1.0: USB hub found
[   27.743697] hub 3-0:1.0: 7 ports detected
[   27.845804] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[   27.845809] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [Z018] -> GSI 18 (level, low) -> IRQ 17
[   27.845821] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   27.845825] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   27.845848] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[   27.845859] ohci_hcd 0000:00:04.0: irq 17, io mem 0xf6487000
[   27.903405] usb usb4: configuration #1 chosen from 1 choice
[   27.903428] hub 4-0:1.0: USB hub found
[   27.903435] hub 4-0:1.0: 2 ports detected
[   27.993171] usb 2-2: new high speed USB device using ehci_hcd and address 2
[   28.005416] ahci 0000:00:09.0: version 3.0
[   28.005748] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[   28.005758] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 23 (level, low) -> IRQ 18
[   28.144102] usb 2-2: configuration #1 chosen from 1 choice
[   28.449708] usb 3-4: new low speed USB device using ohci_hcd and address 2
[   28.664464] usb 3-4: configuration #1 chosen from 1 choice
[   28.678232] usbcore: registered new interface driver hiddev
[   28.683482] input: USB Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.0/input/input2
[   28.701312] input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:02.0-4
[   28.701325] usbcore: registered new interface driver usbhid
[   28.701330] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   29.007436] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   29.007441] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[   29.007445] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   29.007767] scsi0 : ahci
[   29.008019] scsi1 : ahci
[   29.008152] scsi2 : ahci
[   29.008272] scsi3 : ahci
[   29.008348] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 221
[   29.008352] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 221
[   29.008355] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 221
[   29.008357] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 221
[   29.655659] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.656056] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[   29.656060] ata1.00: 488397168 sectors, multi 16: LBA48 
[   29.656521] ata1.00: configured for UDMA/100
[   29.977792] ata2: SATA link down (SStatus 0 SControl 300)
[   30.302560] ata3: SATA link down (SStatus 0 SControl 300)
[   30.630002] ata4: SATA link down (SStatus 0 SControl 300)
[   30.628783] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[   30.629192] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   30.629522] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   30.629531] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 19
[   30.629537] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   31.148252] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1b:24:fa:e8:2a
[   31.148257] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   31.149631] PCI: Enabling device 0000:01:05.0 (0100 -> 0102)
[   31.149952] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   31.149963] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK1] -> GSI 5 (level, low) -> IRQ 5
[   31.151847] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   31.201620] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   31.207661] pata_amd 0000:00:06.0: version 0.3.10
[   31.207720] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   31.209102] scsi4 : pata_amd
[   31.209159] scsi5 : pata_amd
[   31.209437] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   31.209440] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   31.216151] Driver 'sd' needs updating - please use bus_type methods
[   31.216227] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   31.216239] sd 0:0:0:0: [sda] Write Protect is off
[   31.216241] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.216257] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.216304] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   31.216312] sd 0:0:0:0: [sda] Write Protect is off
[   31.216315] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.216328] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.216332]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[   31.302885] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.306063] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.532760] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[   31.708385] ata5.00: configured for MWDMA2
[   31.708419] ata6: port disabled. ignoring.
[   31.712511] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[   31.712594] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   31.718264] Driver 'sr' needs updating - please use bus_type methods
[   31.736456] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   31.736462] Uniform CD-ROM driver Revision: 3.20
[   31.736514] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   31.885658] Attempting manual resume
[   31.885661] swsusp: Resume From Partition 8:6
[   31.885663] PM: Checking swsusp image.
[   31.885844] PM: Resume from disk failed.
[   31.918815] kjournald starting.  Commit interval 5 seconds
[   31.918831] EXT3-fs: mounted filesystem with ordered data mode.
[   32.486947] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00293da300]
[   38.533475] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.602358] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   39.267048] usbcore: registered new interface driver usbserial
[   39.267065] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   39.267109] usbcore: registered new interface driver usbserial_generic
[   39.267111] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   40.105820] input: Power Button (FF) as /devices/virtual/input/input3
[   40.137640] ACPI: Power Button (FF) [PWRF]
[   40.137754] input: Sleep Button (CM) as /devices/virtual/input/input4
[   40.173577] ACPI: Sleep Button (CM) [SLPB]
[   40.173704] input: Lid Switch as /devices/virtual/input/input5
[   40.189639] ACPI: Lid Switch [LID]
[   40.189285] ACPI: Battery Slot [BAT0] (battery absent)
[   40.189433] input: Power Button (CM) as /devices/virtual/input/input6
[   40.220181] ACPI: Power Button (CM) [PWRB]
[   40.221501] ACPI: AC Adapter [ACAD] (on-line)
[   40.348927] ACPI: WMI-Acer: Mapper loaded
[   40.684231] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   40.700711] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   41.911158] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.927679] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.950695] Linux video capture interface: v2.00
[   42.098470] ricoh-mmc: Ricoh MMC Controller disabling driver
[   42.098474] ricoh-mmc: Copyright(c) Philip Langdale
[   42.098522] ricoh-mmc: Ricoh MMC controller found at 0000:01:05.2 [1180:0843] (rev 12)
[   42.098530] ricoh-mmc: Controller is now disabled.
[   42.172097] Linux agpgart interface v0.102
[   42.458842] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b015)
[   42.460870] usbcore: registered new interface driver uvcvideo
[   42.460876] USB Video Class driver (v0.1.0)
[   42.607219] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   42.631364] nvidia: module license 'NVIDIA' taints kernel.
[   43.012972] sdhci: Secure Digital Host Controller Interface driver
[   43.012976] sdhci: Copyright(c) Pierre Ossman
[   43.013022] sdhci: SDHCI controller found at 0000:01:05.1 [1180:0822] (rev 22)
[   43.013350] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   43.013360] ACPI: PCI Interrupt 0000:01:05.1[B] -> Link [LNK2] -> GSI 7 (level, low) -> IRQ 7
[   43.013378] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   43.013425] mmc0: SDHCI at 0xf6100800 irq 7 DMA
[   43.131793] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   43.130819] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   43.130830] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LGPU] -> GSI 16 (level, low) -> IRQ 20
[   43.130838] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   43.167981] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   43.322684] ath_pci: disagrees about version of symbol _ath_hal_attach
[   43.322689] ath_pci: Unknown symbol _ath_hal_attach
[   43.322788] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   43.322791] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   43.323185] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   43.323187] ath_pci: Unknown symbol ath_hal_computetxtime
[   43.323446] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   43.323448] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   43.323636] ath_pci: Unknown symbol _ath_hal_detach
[   43.324220] ath_pci: Unknown symbol ath_hal_print_decoded_register
[   43.324799] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   43.324802] ath_pci: Unknown symbol ath_hal_init_channels
[   43.325045] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   43.325047] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[   43.627917] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   43.627927] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21
[   43.627951] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   44.211401] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   44.286090] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   48.829756] lp: driver loaded but no devices found
[   48.991969] Adding 4000144k swap on /dev/sda6.  Priority:-1 extents:1 across:4000144k
[   49.543872] EXT3 FS on sda7, internal journal
[   52.045103] No dock devices found.
[   52.477548] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 processors (2 cpu cores) (version 2.20.00)
[   52.476275] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x13
[   52.476280] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[   52.476282] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[   52.476285] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1a
[   53.306749] apm: BIOS not found.
[   53.925761] ppdev: user-space parallel port driver
[   54.172382] audit(1239373258.528:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=7501 profile="/usr/sbin/cupsd" namespace="default"
[   55.659429] Clocksource tsc unstable (delta = -289490300 ns)
[   56.504129] Bluetooth: Core ver 2.11
[   56.504245] NET: Registered protocol family 31
[   56.504247] Bluetooth: HCI device and connection manager initialized
[   56.504251] Bluetooth: HCI socket layer initialized
[   56.532029] Bluetooth: L2CAP ver 2.9
[   56.532035] Bluetooth: L2CAP socket layer initialized
[   56.584331] Bluetooth: RFCOMM socket layer initialized
[   56.584346] Bluetooth: RFCOMM TTY layer initialized
[   56.584348] Bluetooth: RFCOMM ver 1.8
[   59.433894] NET: Registered protocol family 17
[   61.616195] NET: Registered protocol family 10
[   61.616465] lo: Disabled Privacy Extensions
[   67.077125] eth0: no IPv6 routers present
[   84.895808] CPU0 attaching NULL sched-domain.
[   84.895818] CPU1 attaching NULL sched-domain.
[   84.905939] CPU0 attaching sched-domain:
[   84.905944]  domain 0: span 03
[   84.905946]   groups: 01 02
[   84.905951] CPU1 attaching sched-domain:
[   84.905953]  domain 0: span 03
[   84.905954]   groups: 02 01
```

_6 ) Network configuration_
```
$ sudo lshw -C network
[sudo] password for ?????: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:fa:e8:2a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.2 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

```

_7 ) Scan for networks:_
```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

_8 ) Ubuntu Version:_
```
$ lsb_release -d
Description:	Ubuntu 8.04.2

```

_9 ) Kernel/architecture (including 32 vs. 64 bit):_
```
$ uname -mr
2.6.24-23-generic i686
```

_10 ) Restarting the network:_
```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
```

TIA

---

### Post by superprash2003 on 2009-04-10
good job posting the question.. your outputs are just the ones people would want to know your exact problem..try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by jdackle on 2009-04-10
Thanks, superbrash2003! :)

Actually, after opening the link you gently provided, I went back to the other howto I'd followed and noticed: > Keep in mind that every time the Kernel gets updated you have to run these commands again:

sudo apt-get update && sudo aptitude install build-essential

Now run:

make clean

make

sudo make install

sudo modprobe ath_pci

sudo modprobe wlan_scan_sta

Off course in the madwifi folder. You might want to move the folder to your home folder because we’ll need it again after a Kernel update.
Yep, I did update the kernel last week and it was before I turned on the router... And yes, I hadn't recompiled the madwifi driver (nor tried another wireless network)... :p
So... now... it's WORKING perfectly! :lolflag:

However, the link you provided does seem to present a simpler solution. So I'll try that one out too before I mark this as SOLVED (which nonetheless is! :) ).

Thanks!

---

### Post by jdackle on 2009-04-10
Yep, working fine! :)

Of course I had to install linux-backports-modules-**hardy** instead of linux-backports-modules-intrepid. ;)


EDIT:
Erm... can't seem to find neither the "Thanks" link for superprash2003 nor the link to mark the thread as "SOLVED"... Am I missing something... AGAIN?

---

### Post by superprash2003 on 2009-04-11
both features have been disabled for quite a while , due to certain server issues.

---

### Post by jdackle on 2009-04-12
Yeah, haven't been around for quite a while... Thanks for the info. :)

---

