---
title: "Can't Connect with Netgear WG111T card"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by kurowoof on 2009-04-05
I've been having a great deal of trouble trying to connect my computer to the internet. I installed Ubuntu 8.10 the other day. I'm using dual boot with XP (sp3) so I can still connect. I installed using Wubi, so I don't have the files on an install CD or anything. I have a Netgear WG111T wireless card which works just fine on XP. Do I need to install ndiswrapper? How could I even install that if I can't connect to the internet?

Thanks, cheers.

I noticed that in the following data, it mentions that the network is disabled. I hope this is all the data you need, if you need more just holler:

**1) Machine Brand and Model (PC)**
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to CSA Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
03:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
03:0e.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

**2) Wireless Brand, Model, and Wireless Chipset:**
Bus 005 Device 003: ID 054c:0174 Sony Corp. 
Bus 005 Device 002: ID 1385:4251 Netgear, Inc WG111T (no firmware)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**3)Check interface:**
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)

00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)

00:03.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to CSA Bridge [8086:2573] (rev 02)

00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)

00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)

00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)

00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)

00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)

00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)

00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)

00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)

00:1f.6 Modem [0703]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller [8086:24d6] (rev 02)

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5200] [10de:0322] (rev a1)

02:01.0 Ethernet controller [0200]: Intel Corporation 82547EI Gigabit Ethernet Controller [8086:1019]

03:09.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder [4444:0016] (rev 01)

03:0a.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 03)

03:0a.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 03)

03:0e.0 FireWire (IEEE 1394) [0c00]: NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr [1033:00f2] (rev 01)


**4) Check for modules:**
Module                  Size  Used by

ipv6                  263972  10 

binfmt_misc            16904  1 

rfcomm                 44432  0 

sco                    18308  2 

bridge                 56980  0 

stp                    10628  1 bridge

bnep                   20480  2 

l2cap                  30464  6 rfcomm,bnep

bluetooth              61924  6 rfcomm,sco,bnep,l2cap

ppdev                  15620  0 

speedstep_lib          12676  0 

cpufreq_powersave       9856  0 

cpufreq_stats          13188  0 

cpufreq_conservative    14600  0 

cpufreq_ondemand       14988  0 

freq_table             12672  2 cpufreq_stats,cpufreq_ondemand

cpufreq_userspace      11396  0 

video                  25104  0 

output                 11008  1 video

container              11520  0 

pci_slot               12552  0 

wmi                    14504  0 

sbs                    19464  0 

sbshc                  13440  1 sbs

battery                18436  0 

iptable_filter         10752  0 

ip_tables              19600  1 iptable_filter

x_tables               22916  1 ip_tables

ac                     12292  0 

sbp2                   29324  0 

lp                     17156  0 

snd_emu10k1_synth      14464  0 

snd_emux_synth         41344  1 snd_emu10k1_synth

snd_seq_virmidi        13568  1 snd_emux_synth

snd_seq_midi_emul      14592  1 snd_emux_synth

snd_emu10k1           146208  4 snd_emu10k1_synth

snd_ac97_codec        111652  1 snd_emu10k1

ac97_bus                9856  1 snd_ac97_codec

snd_pcm_oss            46848  0 

snd_mixer_oss          22784  1 snd_pcm_oss

snd_pcm                83204  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss

snd_page_alloc         16136  2 snd_emu10k1,snd_pcm

snd_util_mem           12416  2 snd_emux_synth,snd_emu10k1

snd_hwdep              15236  2 snd_emux_synth,snd_emu10k1

tea5767                14980  0 

snd_seq_dummy          10884  0 

snd_seq_oss            38528  0 

snd_seq_midi           14336  0 

wm8775                 13740  0 

snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi

cx25840                35760  0 

snd_seq_midi_event     15232  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi

snd_seq                57776  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

tuner                  33096  0 

psmouse                45200  0 

snd_timer              29960  3 snd_emu10k1,snd_pcm,snd_seq

evdev                  17696  6 

ivtv                  151204  0 

serio_raw              13444  0 

snd_seq_device         15116  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

videodev               41344  2 tuner,ivtv

pcspkr                 10624  0 

parport_pc             39204  1 

v4l1_compat            22404  1 videodev

compat_ioctl32          9344  1 ivtv

i2c_algo_bit           14340  1 ivtv

snd                    63268  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

cx2341x                21124  1 ivtv

emu10k1_gp             10880  0 

parport                42604  3 ppdev,lp,parport_pc

v4l2_common            19840  5 wm8775,cx25840,tuner,ivtv,cx2341x

tveeprom               20228  1 ivtv

gameport               19468  2 emu10k1_gp

i2c_core               31892  8 tea5767,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,v4l2_common,tveeprom

soundcore              15328  1 snd

button                 14224  0 

iTCO_wdt               18596  0 

iTCO_vendor_support    11652  1 iTCO_wdt

intel_agp              33724  1 

agpgart                42184  1 intel_agp

shpchp                 37908  0 

pci_hotplug            35236  1 shpchp

ext3                  133256  1 

jbd                    55444  1 ext3

mbcache                16004  1 ext3

loop                   23180  2 

usb_storage            81728  0 

libusual               27156  1 usb_storage

sd_mod                 42264  2 

sr_mod                 22212  0 

cdrom                  43168  1 sr_mod

crc_t10dif              9984  1 sd_mod

sg                     39732  0 

pata_acpi              12160  0 

ata_piix               24580  1 

ohci1394               37936  0 

ieee1394               96324  2 sbp2,ohci1394

ata_generic            12932  0 

libata                177312  3 pata_acpi,ata_piix,ata_generic

scsi_mod              155212  6 sbp2,usb_storage,sd_mod,sr_mod,sg,libata

dock                   16656  1 libata

ehci_hcd               43276  0 

uhci_hcd               30736  0 

e1000                 132164  0 

usbcore               148848  5 usb_storage,libusual,ehci_hcd,uhci_hcd

thermal                23708  0 

processor              42156  1 thermal

fan                    12548  0 

fbcon                  47648  0 

tileblit               10880  1 fbcon

font                   16512  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit

fuse                   60828  5 

**5) Kernel boot messages**
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129775

[    0.000000] Kernel command line: root=UUID=6030699C30697A44 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 

[    0.000000] Enabling fast FPU save and restore... done.

[    0.000000] Enabling unmasked SIMD FPU exception support... done.

[    0.000000] Initializing CPU#0

[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)

[    0.000000] TSC: PIT calibration confirmed by PMTIMER.

[    0.000000] TSC: using PIT calibration value

[    0.000000] Detected 2792.978 MHz processor.

[    0.004000] Console: colour VGA+ 80x25

[    0.004000] console [tty0] enabled

[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)

[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)

[    0.004000] Memory: 505284k/524096k available (2572k kernel code, 18256k reserved, 1160k data, 424k init, 0k highmem)

[    0.004000] virtual kernel memory layout:

[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)

[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)

[    0.004000]     vmalloc : 0xe0800000 - 0xff3fe000   ( 491 MB)

[    0.004000]     lowmem  : 0xc0000000 - 0xdffd0000   ( 511 MB)

[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)

[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)

[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)

[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.

[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated

[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1

[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.95 BogoMIPS (lpj=11171912)

[    0.004030] Security Framework initialized

[    0.004039] SELinux:  Disabled at boot.

[    0.004061] AppArmor: AppArmor initialized

[    0.004073] Mount-cache hash table entries: 512

[    0.004274] Initializing cgroup subsys ns

[    0.004279] Initializing cgroup subsys cpuacct

[    0.004283] Initializing cgroup subsys memory

[    0.004301] CPU: Trace cache: 12K uops, L1 D cache: 8K

[    0.004305] CPU: L2 cache: 512K

[    0.004308] CPU: Physical Processor ID: 0

[    0.004323] Checking 'hlt' instruction... OK.

[    0.022426] ACPI: Core revision 20080609

[    0.024414] ACPI: Checking initramfs for custom DSDT

[    0.378278] ENABLING IO-APIC IRQs

[    0.378464] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

[    0.418157] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09

[    0.420026] Booting processor 1/1 ip 6000

[    0.004000] Initializing CPU#1

[    0.004000] Calibrating delay using timer specific routine.. 5586.30 BogoMIPS (lpj=11172600)

[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K

[    0.004000] CPU: L2 cache: 512K

[    0.004000] CPU: Physical Processor ID: 0

[    0.504227] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09

[    0.504253] checking TSC synchronization [CPU#0 -> CPU#1]: passed.

[    0.508065] Brought up 2 CPUs

[    0.508072] Total of 2 processors activated (11172.25 BogoMIPS).

[    0.508096] CPU0 attaching sched-domain:

[    0.508100]  domain 0: span 0-1 level SIBLING

[    0.508104]   groups: 0 1

[    0.508111]   domain 1: span 0-1 level CPU

[    0.508115]    groups: 0-1

[    0.508123] CPU1 attaching sched-domain:

[    0.508125]  domain 0: span 0-1 level SIBLING

[    0.508129]   groups: 1 0

[    0.508135]   domain 1: span 0-1 level CPU

[    0.508138]    groups: 0-1

[    0.508263] net_namespace: 840 bytes

[    0.508263] Booting paravirtualized kernel on bare hardware

[    0.508420] Time: 19:10:27  Date: 04/04/09

[    0.508460] NET: Registered protocol family 16

[    0.508494] EISA bus registered

[    0.508494] ACPI: bus type pci registered

[    0.508494] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3

[    0.508494] PCI: Using configuration type 1 for base access

[    0.512997] ACPI: EC: Look up EC in DSDT

[    0.521356] ACPI: Interpreter enabled

[    0.521361] ACPI: (supports S0 S1 S3 S4 S5)

[    0.521388] ACPI: Using IOAPIC for interrupt routing

[    0.532240] ACPI: PCI Root Bridge [PCI0] (0000:00)

[    0.532240] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff]

[    0.532240] PCI: 0000:00:1d.0 reg 20 io port: [e000, e01f]

[    0.532291] PCI: 0000:00:1d.1 reg 20 io port: [e400, e41f]

[    0.532345] PCI: 0000:00:1d.2 reg 20 io port: [e800, e81f]

[    0.532399] PCI: 0000:00:1d.3 reg 20 io port: [ec00, ec1f]

[    0.532462] PCI: 0000:00:1d.7 reg 10 32bit mmio: [febffc00, febfffff]

[    0.532518] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold

[    0.532524] pci 0000:00:1d.7: PME# disabled

[    0.532612] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000

[    0.532620] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO

[    0.532625] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO

[    0.532646] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]

[    0.532654] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]

[    0.532662] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]

[    0.532669] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]

[    0.532677] PCI: 0000:00:1f.1 reg 20 io port: [fc00, fc0f]

[    0.532685] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]

[    0.532737] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]

[    0.532782] PCI: 0000:00:1f.6 reg 10 io port: [d800, d8ff]

[    0.532790] PCI: 0000:00:1f.6 reg 14 io port: [dc00, dc7f]

[    0.532827] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold

[    0.532833] pci 0000:00:1f.6: PME# disabled

[    0.532869] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]

[    0.532876] PCI: 0000:01:00.0 reg 14 32bit mmio: [e0000000, e7ffffff]

[    0.532899] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe8e0000, fe8fffff]

[    0.532950] PCI: bridge 0000:00:01.0 32bit mmio: [fc800000, fe8fffff]

[    0.532955] PCI: bridge 0000:00:01.0 32bit mmio pref: [dff00000, efefffff]

[    0.532988] PCI: 0000:02:01.0 reg 10 32bit mmio: [fe9e0000, fe9fffff]

[    0.533000] PCI: 0000:02:01.0 reg 18 io port: [ac00, ac1f]

[    0.533030] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold

[    0.533035] pci 0000:02:01.0: PME# disabled

[    0.533071] PCI: bridge 0000:00:03.0 io port: [a000, afff]

[    0.533076] PCI: bridge 0000:00:03.0 32bit mmio: [fe900000, fe9fffff]

[    0.533127] PCI: 0000:03:09.0 reg 10 32bit mmio: [f0000000, f3ffffff]

[    0.533198] PCI: 0000:03:0a.0 reg 10 io port: [b800, b81f]

[    0.533240] pci 0000:03:0a.0: supports D1

[    0.533243] pci 0000:03:0a.0: supports D2

[    0.533270] PCI: 0000:03:0a.1 reg 10 io port: [bc00, bc07]

[    0.533312] pci 0000:03:0a.1: supports D1

[    0.533314] pci 0000:03:0a.1: supports D2

[    0.533353] PCI: 0000:03:0e.0 reg 10 32bit mmio: [feafe000, feafefff]

[    0.533395] pci 0000:03:0e.0: supports D1

[    0.533398] pci 0000:03:0e.0: supports D2

[    0.533400] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.533406] pci 0000:03:0e.0: PME# disabled

[    0.533429] pci 0000:00:1e.0: transparent bridge

[    0.533434] PCI: bridge 0000:00:1e.0 io port: [b000, bfff]

[    0.533440] PCI: bridge 0000:00:1e.0 32bit mmio: [fea00000, feafffff]

[    0.533445] PCI: bridge 0000:00:1e.0 32bit mmio pref: [eff00000, f7efffff]

[    0.533463] bus 00 -> node 0

[    0.533472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[    0.533684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]

[    0.533947] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]

[    0.544205] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)

[    0.544366] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)

[    0.544526] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)

[    0.544686] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)

[    0.544844] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.

[    0.545007] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)

[    0.545165] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)

[    0.545331] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)

[    0.545417] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 23, should be 17 [20080609]

[    0.545417] Linux Plug and Play Support v0.97 (c) Adam Belay

[    0.545417] pnp: PnP ACPI init

[    0.545417] ACPI: bus type pnp registered

[    0.552363] pnp: PnP ACPI: found 13 devices

[    0.552367] ACPI: ACPI bus type pnp unregistered

[    0.552373] PnPBIOS: Disabled by ACPI PNP

[    0.552405] PCI: Using ACPI for IRQ routing

[    0.560048] NET: Registered protocol family 8

[    0.560051] NET: Registered protocol family 20

[    0.560079] NetLabel: Initializing

[    0.560079] NetLabel:  domain hash size = 128

[    0.560079] NetLabel:  protocols = UNLABELED CIPSOv4

[    0.560087] NetLabel:  unlabeled traffic allowed by default

[    0.560180] hpet clockevent registered

[    0.560186] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0

[    0.560194] hpet0: 3 64-bit timers, 14318180 Hz

[    0.561996] tracer: 772 pages allocated for 65536 entries of 48 bytes

[    0.561999]    actual entries 65620

[    0.562183] AppArmor: AppArmor Filesystem Enabled

[    0.562204] ACPI: RTC can wake from S4

[    0.568082] system 00:09: ioport range 0x680-0x6ff has been reserved

[    0.568087] system 00:09: ioport range 0x290-0x297 has been reserved

[    0.568098] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved

[    0.568102] system 00:0a: ioport range 0x800-0x87f has been reserved

[    0.568106] system 00:0a: ioport range 0x480-0x4bf has been reserved

[    0.568111] system 00:0a: iomem range 0xfed20000-0xfed8ffff has been reserved

[    0.568116] system 00:0a: iomem range 0xffb00000-0xffbfffff could not be reserved

[    0.568125] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved

[    0.568129] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved

[    0.568144] system 00:0c: iomem range 0x0-0x9ffff could not be reserved

[    0.568148] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved

[    0.568152] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved

[    0.568156] system 00:0c: iomem range 0x100000-0x1fffffff could not be reserved

[    0.568160] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved

[    0.603818] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01

[    0.603822] pci 0000:00:01.0:   IO window: disabled

[    0.603828] pci 0000:00:01.0:   MEM window: 0xfc800000-0xfe8fffff

[    0.603834] pci 0000:00:01.0:   PREFETCH window: 0x000000dff00000-0x000000efefffff

[    0.603842] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02

[    0.603846] pci 0000:00:03.0:   IO window: 0xa000-0xafff

[    0.603852] pci 0000:00:03.0:   MEM window: 0xfe900000-0xfe9fffff

[    0.603857] pci 0000:00:03.0:   PREFETCH window: disabled

[    0.603865] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03

[    0.603869] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff

[    0.603876] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff

[    0.603882] pci 0000:00:1e.0:   PREFETCH window: 0x000000eff00000-0x000000f7efffff

[    0.603908] pci 0000:00:1e.0: setting latency timer to 64

[    0.603913] bus: 00 index 0 io port: [0, ffff]

[    0.603916] bus: 00 index 1 mmio: [0, ffffffff]

[    0.603920] bus: 01 index 0 mmio: [0, 0]

[    0.603923] bus: 01 index 1 mmio: [fc800000, fe8fffff]

[    0.603926] bus: 01 index 2 mmio: [dff00000, efefffff]

[    0.603929] bus: 01 index 3 mmio: [0, 0]

[    0.603932] bus: 02 index 0 io port: [a000, afff]

[    0.603935] bus: 02 index 1 mmio: [fe900000, fe9fffff]

[    0.603937] bus: 02 index 2 mmio: [0, 0]

[    0.603940] bus: 02 index 3 mmio: [0, 0]

[    0.603943] bus: 03 index 0 io port: [b000, bfff]

[    0.603946] bus: 03 index 1 mmio: [fea00000, feafffff]

[    0.603949] bus: 03 index 2 mmio: [eff00000, f7efffff]

[    0.603951] bus: 03 index 3 io port: [0, ffff]

[    0.603954] bus: 03 index 4 mmio: [0, ffffffff]

[    0.603970] NET: Registered protocol family 2

[    0.616113] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)

[    0.616442] TCP established hash table entries: 16384 (order: 5, 131072 bytes)

[    0.616510] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)

[    0.616573] TCP: Hash tables configured (established 16384 bind 16384)

[    0.616577] TCP reno registered

[    0.624130] NET: Registered protocol family 1

[    0.624289] checking if image is initramfs... it is

[    1.060308] Switched to high resolution mode on CPU 1

[    1.064062] Switched to high resolution mode on CPU 0

[    1.364536] Freeing initrd memory: 8237k freed

[    1.366050] audit: initializing netlink socket (disabled)

[    1.366070] type=2000 audit(1238872227.365:1): initialized

[    1.370903] HugeTLB registered 4 MB page size, pre-allocated 0 pages

[    1.375248] VFS: Disk quotas dquot_6.5.1

[    1.375409] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[    1.375579] msgmni has been set to 1003

[    1.375810] io scheduler noop registered

[    1.375814] io scheduler anticipatory registered

[    1.375818] io scheduler deadline registered

[    1.375840] io scheduler cfq registered (default)

[    1.375962] pci 0000:01:00.0: Boot video device

[    1.376731] isapnp: Scanning for PnP cards...

[    1.730313] isapnp: No Plug & Play device found

[    1.807068] Serial: 8250/16550 driver4 ports, IRQ sharing enabled

[    1.808239] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17

[    1.808247] serial 0000:00:1f.6: PCI INT B disabled

[    1.811543] brd: module loaded

[    1.811682] input: Macintosh mouse button emulation as /devices/virtual/input/input0

[    1.811921] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12

[    1.814710] serio: i8042 KBD port at 0x60,0x64 irq 1

[    1.814721] serio: i8042 AUX port at 0x60,0x64 irq 12

[    1.816269] mice: PS/2 mouse device common for all mice

[    1.816545] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0

[    1.816572] rtc0: alarms up to one month, hpet irqs

[    1.816853] EISA: Probing bus 0 at eisa.0

[    1.816894] EISA: Detected 0 cards.

[    1.816899] cpuidle: using governor ladder

[    1.816902] cpuidle: using governor menu

[    1.817734] TCP cubic registered

[    1.817774] Using IPI No-Shortcut mode

[    1.818216] registered taskstats version 1

[    1.818384]   Magic number: 5:917:191

[    1.818428] tty ttys3: hash matches

[    1.818536] rtc_cmos 00:02: setting system clock to 2009-04-04 19:10:28 UTC (1238872228)

[    1.818541] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[    1.818544] EDD information not available.

[    1.818933] Freeing unused kernel memory: 424k freed

[    1.818995] Write protecting the kernel text: 2576k

[    1.819033] Write protecting the kernel read-only data: 936k

[    1.844111] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1

[    1.995141] fuse init (API version 7.9)

[    2.084068] processor ACPI0007:00: registered as cooling_device0

[    2.088064] processor ACPI0007:01: registered as cooling_device1

[    2.730289] usbcore: registered new interface driver usbfs

[    2.730349] usbcore: registered new interface driver hub

[    2.730522] usbcore: registered new device driver usb

[    2.730709] Intel(R) PRO/1000 Network Driver - version 7.3.20-k3-NAPI

[    2.730717] Copyright (c) 1999-2006 Intel Corporation.

[    2.730801] e1000 0000:02:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[    2.730817] e1000 0000:02:01.0: setting latency timer to 64

[    2.739766] USB Universal Host Controller Interface driver v3.0

[    2.817610] No dock devices found.

[    2.851248] SCSI subsystem initialized

[    3.088905] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0c:6e:d9:99:a8

[    3.099013] libata version 3.00 loaded.

[    3.378638] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection

[    3.378767] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    3.378785] uhci_hcd 0000:00:1d.0: setting latency timer to 64

[    3.378792] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[    3.378892] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1

[    3.378941] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000

[    3.379277] usb usb1: configuration #1 chosen from 1 choice

[    3.379355] hub 1-0:1.0: USB hub found

[    3.379389] hub 1-0:1.0: 2 ports detected

[    3.481698] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19

[    3.481719] uhci_hcd 0000:00:1d.1: setting latency timer to 64

[    3.481727] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[    3.481817] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2

[    3.481865] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400

[    3.482205] usb usb2: configuration #1 chosen from 1 choice

[    3.482274] hub 2-0:1.0: USB hub found

[    3.482296] hub 2-0:1.0: 2 ports detected

[    3.689504] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[    3.689516] uhci_hcd 0000:00:1d.2: setting latency timer to 64

[    3.689521] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[    3.689560] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3

[    3.689596] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800

[    3.689742] usb usb3: configuration #1 chosen from 1 choice

[    3.689786] hub 3-0:1.0: USB hub found

[    3.689798] hub 3-0:1.0: 2 ports detected

[    3.800021] usb 2-1: new full speed USB device using uhci_hcd and address 2

[    3.896348] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    3.896360] uhci_hcd 0000:00:1d.3: setting latency timer to 64

[    3.896365] uhci_hcd 0000:00:1d.3: UHCI Host Controller

[    3.896404] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4

[    3.896432] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00

[    3.896586] usb usb4: configuration #1 chosen from 1 choice

[    3.896627] hub 4-0:1.0: USB hub found

[    3.896639] hub 4-0:1.0: 2 ports detected

[    3.964301] usb 2-1: configuration #1 chosen from 1 choice

[    4.000408] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23

[    4.000428] ehci_hcd 0000:00:1d.7: setting latency timer to 64

[    4.000433] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[    4.000475] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5

[    4.004401] ehci_hcd 0000:00:1d.7: debug port 1

[    4.004409] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported

[    4.004428] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00

[    4.080023] usb 3-1: new full speed USB device using uhci_hcd and address 2

[    4.093023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[    4.093261] usb usb5: configuration #1 chosen from 1 choice

[    4.093303] hub 5-0:1.0: USB hub found

[    4.093319] hub 5-0:1.0: 8 ports detected

[    4.148048] hub 3-0:1.0: unable to enumerate USB device on port 1

[    4.148076] usb 2-1: USB disconnect, address 2

[    4.308093] ohci1394 0000:03:0e.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[    4.359920] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[feafe000-feafe7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]

[    4.391298] ata_piix 0000:00:1f.1: version 2.12

[    4.391322] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[    4.391409] ata_piix 0000:00:1f.1: setting latency timer to 64

[    4.392072] scsi0 : ata_piix

[    4.392303] scsi1 : ata_piix

[    4.396000] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14

[    4.396083] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15

[    4.424038] usb 5-3: new high speed USB device using ehci_hcd and address 2

[    4.553445] usb 5-3: configuration #1 chosen from 1 choice

[    4.557549] ata1.00: ATA-6: WDC WD1600BB-98DWA0, 15.05R15, max UDMA/100

[    4.557558] ata1.00: 312581808 sectors, multi 16: LBA48 

[    4.573358] ata1.00: configured for UDMA/100

[    4.664025] usb 5-5: new high speed USB device using ehci_hcd and address 3

[    4.744314] ata2.00: ATAPI: PIONEER DVD-RW  DVR-106D, 1.00, max UDMA/33

[    4.744339] ata2.01: ATAPI: SAMSUNG CD-ROM  SC-140C, A101, max UDMA/33

[    4.752235] ata2.00: configured for UDMA/33

[    4.760247] ata2.01: configured for UDMA/33

[    4.760418] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BB-98D 15.0 PQ: 0 ANSI: 5

[    4.767134] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-106D 1.00 PQ: 0 ANSI: 5

[    4.767532] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-140C   A101 PQ: 0 ANSI: 5

[    4.786646] scsi 0:0:0:0: Attached scsi generic sg0 type 0

[    4.786721] scsi 1:0:0:0: Attached scsi generic sg1 type 5

[    4.786776] scsi 1:0:1:0: Attached scsi generic sg2 type 5

[    4.822899] Driver 'sr' needs updating - please use bus_type methods

[    4.829961] Driver 'sd' needs updating - please use bus_type methods

[    4.830188] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)

[    4.830241] sd 0:0:0:0: [sda] Write Protect is off

[    4.830247] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    4.830331] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    4.830578] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)

[    4.830624] sd 0:0:0:0: [sda] Write Protect is off

[    4.830632] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    4.830722] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    4.830732]  sda:sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray

[    4.841521] Uniform CD-ROM driver Revision: 3.20

[    4.841663] sr 1:0:0:0: Attached scsi CD-ROM sr0

[    4.844422] sr1: scsi3-mmc drive: 1x/40x cd/rw xa/form2 cdda tray

[    4.844563] sr 1:0:1:0: Attached scsi CD-ROM sr1

[    4.853752]  sda1 sda2 sda3 < sda5 >

[    4.862004] sd 0:0:0:0: [sda] Attached SCSI disk

[    4.868929] usb 5-5: configuration #1 chosen from 1 choice

[    4.912783] usbcore: registered new interface driver libusual

[    4.929976] Initializing USB Mass Storage driver...

[    4.930203] scsi2 : SCSI emulation for USB Mass Storage devices

[    4.932550] usbcore: registered new interface driver usb-storage

[    4.932560] USB Mass Storage support registered.

[    4.941731] usb-storage: device found at 3

[    4.941738] usb-storage: waiting for device to settle before scanning

[    5.662198] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603017e46ce]

[    7.285858] loop: module loaded

[    7.340928] kjournald starting.  Commit interval 5 seconds

[    7.340947] EXT3-fs: mounted filesystem with ordered data mode.

[    9.945739] usb-storage: device scan complete

[    9.949938] scsi 2:0:0:0: Direct-Access     Sony     UMH-U HS-MS      2.12 PQ: 0 ANSI: 0

[    9.952814] scsi 2:0:0:1: Direct-Access     Sony     UMH-U HS-CF      2.12 PQ: 0 ANSI: 0

[    9.955949] scsi 2:0:0:2: Direct-Access     Sony     UMH-U HS-SM      2.12 PQ: 0 ANSI: 0

[    9.960576] sd 2:0:0:0: [sdb] Attached SCSI removable disk

[    9.960751] sd 2:0:0:0: Attached scsi generic sg3 type 0

[    9.964268] sd 2:0:0:1: [sdc] Attached SCSI removable disk

[    9.964371] sd 2:0:0:1: Attached scsi generic sg4 type 0

[    9.968337] sd 2:0:0:2: [sdd] Attached SCSI removable disk

[    9.968517] sd 2:0:0:2: Attached scsi generic sg5 type 0

[   14.518801] udevd version 124 started

[   15.266288] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   15.432899] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   15.539689] Linux agpgart interface v0.103

[   15.627937] agpgart-intel 0000:00:00.0: Intel 865 Chipset

[   15.630941] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000

[   15.726096] iTCO_vendor_support: vendor-support=0

[   15.737682] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)

[   15.737861] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware

[   15.737888] iTCO_wdt: No card detected

[   16.030414] intel_rng: FWH not detected

[   16.176071] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2

[   16.204040] ACPI: Power Button (FF) [PWRF]

[   16.204293] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3

[   16.220034] ACPI: Power Button (CM) [PWRB]

[   17.387791] gameport: EMU10K1 is pci0000:03:0a.1/gameport0, io 0xbc00, speed 1147kHz

[   17.643456] parport_pc 00:08: reported by Plug and Play ACPI

[   17.643504] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]

[   17.666495] input: PC Speaker as /devices/platform/pcspkr/input/input4

[   17.699560] Linux video capture interface: v2.00

[   17.853623] ivtv:  Start initialization, version 1.4.0

[   17.902806] ivtv0: Initializing card #0

[   17.902821] ivtv0: Unknown card: vendor/device: 4444/0016

[   17.902828] ivtv0:               subsystem vendor/device: 104d/813d

[   17.902835] ivtv0:               cx23416 based

[   17.902840] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card

[   17.902845] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of

[   17.902852] ivtv0: card you have to the ivtv-devel mailinglist ([www.ivtvdriver.org](www.ivtvdriver.org))

[   17.902857] ivtv0: Prefix your subject line with [UNKNOWN IVTV CARD].

[   17.902999] ivtv 0000:03:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21

[   17.956156] tveeprom 0-0050: Encountered bad packet header [aa]. Corrupt or not a Hauppauge eeprom.

[   17.956166] ivtv0: Invalid EEPROM

[   18.424189] cx25840 0-0044: cx25  0-21 found @ 0x88 (ivtv i2c driver #0)

[   18.778753] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5

[   18.868498] All bytes are equal. It is not a TEA5767

[   18.868707] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)

[   18.868881] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)

[   18.872030] wm8775 0-001b: I2C: cannot write 000 to register R23

[   18.875142] wm8775 0-001b: I2C: cannot write 000 to register R7

[   18.878230] wm8775 0-001b: I2C: cannot write 021 to register R11

[   18.881319] wm8775 0-001b: I2C: cannot write 102 to register R12

[   18.884377] wm8775 0-001b: I2C: cannot write 000 to register R13

[   18.887487] wm8775 0-001b: I2C: cannot write 1d4 to register R14

[   18.890581] wm8775 0-001b: I2C: cannot write 1d4 to register R15

[   18.893697] wm8775 0-001b: I2C: cannot write 1bf to register R16

[   18.896767] wm8775 0-001b: I2C: cannot write 185 to register R17

[   18.899852] wm8775 0-001b: I2C: cannot write 0a2 to register R18

[   18.902933] wm8775 0-001b: I2C: cannot write 005 to register R19

[   18.906029] wm8775 0-001b: I2C: cannot write 07a to register R20

[   18.909118] wm8775 0-001b: I2C: cannot write 102 to register R21

[   18.910136] ivtv0: Registered device video0 for encoder MPG (4096 kB)

[   18.910342] ivtv0: Registered device video32 for encoder YUV (2048 kB)

[   18.919368] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)

[   18.919713] ivtv0: Registered device video24 for encoder PCM (320 kB)

[   18.919938] ivtv0: Registered device radio0 for encoder radio

[   18.919949] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150

[   18.920075] ivtv:  End initialization

[   19.252515] EMU10K1_Audigy 0000:03:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22

[   21.555700] lp0: using parport0 (interrupt-driven).

[   22.320742] EXT3 FS on loop0, internal journal

[  167.934471] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k

[  168.126587] type=1505 audit(1238897594.723:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4337

[  168.320425] type=1505 audit(1238897594.915:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4342

[  168.320728] type=1505 audit(1238897594.915:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4342

[  168.469304] ip_tables: (C) 2000-2006 Netfilter Core Team

[  169.031630] ACPI: WMI: Mapper loaded

[  170.226744] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)

[  170.278679] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)

[  170.278687] apm: disabled - APM is not SMP safe.

[  170.425660] ppdev: user-space parallel port driver

[  171.900016] firmware: requesting v4l-cx2341x-enc.fw

[  171.974863] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)

[  172.172130] ivtv0: Encoder revision: 0x02060039

[  172.195643] firmware: requesting v4l-cx23885-avcore-01.fw

[  172.199210] cx25840 0-0044: unable to open firmware v4l-cx23885-avcore-01.fw

[  172.318721] wm8775 0-001b: I2C: cannot write 0c0 to register R21

[  172.321821] wm8775 0-001b: I2C: cannot write 1d4 to register R14

[  172.324883] wm8775 0-001b: I2C: cannot write 1d4 to register R15

[  172.327933] wm8775 0-001b: I2C: cannot write 102 to register R21

[  172.369058] tuner 0-0060: tuner type not set

[  172.372085] wm8775 0-001b: I2C: cannot write 0c0 to register R21

[  172.375137] wm8775 0-001b: I2C: cannot write 1d4 to register R14

[  172.378201] wm8775 0-001b: I2C: cannot write 1d4 to register R15

[  172.381262] wm8775 0-001b: I2C: cannot write 102 to register R21

[  172.416566] tuner 0-0060: tuner type not set

[  172.416583] tuner 0-0060: tuner type not set

[  172.419715] wm8775 0-001b: I2C: cannot write 0c0 to register R21

[  172.422782] wm8775 0-001b: I2C: cannot write 1d4 to register R14

[  172.425798] wm8775 0-001b: I2C: cannot write 1d4 to register R15

[  172.428803] wm8775 0-001b: I2C: cannot write 108 to register R21

[  172.501073] tuner 0-0060: tuner type not set

[  172.504038] wm8775 0-001b: I2C: cannot write 0c0 to register R21

[  172.507045] wm8775 0-001b: I2C: cannot write 1d4 to register R14

[  172.510056] wm8775 0-001b: I2C: cannot write 1d4 to register R15

[  172.513069] wm8775 0-001b: I2C: cannot write 102 to register R21

[  173.253838] Bluetooth: Core ver 2.13

[  173.254773] NET: Registered protocol family 31

[  173.254780] Bluetooth: HCI device and connection manager initialized

[  173.254787] Bluetooth: HCI socket layer initialized

[  173.275310] Bluetooth: L2CAP ver 2.11

[  173.275319] Bluetooth: L2CAP socket layer initialized

[  173.291133] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

[  173.291148] Bluetooth: BNEP filters: protocol multicast

[  173.325499] Bridge firewalling registered

[  173.326614] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.

[  173.342811] Bluetooth: SCO (Voice Link) ver 0.6

[  173.342820] Bluetooth: SCO socket layer initialized

[  173.383647] Bluetooth: RFCOMM socket layer initialized

[  173.384258] Bluetooth: RFCOMM TTY layer initialized

[  173.384283] Bluetooth: RFCOMM ver 1.10

[  292.068327] ppdev0: registered pardevice

[  292.116230] ppdev0: unregistered pardevice

[  292.165372] ppdev0: registered pardevice

[  292.212328] ppdev0: unregistered pardevice

[  292.239093] ppdev0: registered pardevice

[  292.284029] ppdev0: unregistered pardevice

[  292.539499] type=1503 audit(1238897719.134:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5776/net/" pid=5776 profile="/usr/sbin/cupsd"

[  292.746230] NET: Registered protocol family 10

[  292.749160] lo: Disabled Privacy Extensions

[  292.750645] ADDRCONF(NETDEV_UP): eth0: link is not ready

[  292.752224] type=1503 audit(1238897719.350:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5776 profile="/usr/sbin/cupsd"

[  292.752247] type=1503 audit(1238897719.350:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5776 profile="/usr/sbin/cupsd"

[  292.752262] type=1503 audit(1238897719.350:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5776 profile="/usr/sbin/cupsd"

[  292.752277] type=1503 audit(1238897719.350:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5776 profile="/usr/sbin/cupsd"

[  292.752292] type=1503 audit(1238897719.350:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5776 profile="/usr/sbin/cupsd"

[  292.752307] type=1503 audit(1238897719.350:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5776 profile="/usr/sbin/cupsd"

[  292.752322] type=1503 audit(1238897719.350:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5776 profile="/usr/sbin/cupsd"

[  292.752338] type=1503 audit(1238897719.350:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5776 profile="/usr/sbin/cupsd"

[  292.752455] type=1503 audit(1238897719.350:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5776/net/dev" pid=5776 profile="/usr/sbin/cupsd"


**6) Network configuration**
brendan@ubuntu:~$ sudo lshw -C network

[sudo] password for brendan: 

  *-network               

       description: Ethernet interface

       product: 82547EI Gigabit Ethernet Controller

       vendor: Intel Corporation

       physical id: 1

       bus info: pci@0000:02:01.0

       logical name: eth0

       version: 00

       serial: 00:0c:6e:d9:99:a8

       capacity: 1GB/s

       width: 32 bits

       clock: 66MHz

       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI firmware=N/A latency=0 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 4a:67:ce:35:72:2f

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


**7) Scan for Networks**
brendan@ubuntu:~$ iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



pan0      Interface doesn't support scanning.


**8) Ubuntu Version**
brendan@ubuntu:~$ lsb_release -d

Description:	Ubuntu 8.10


**9) Kernel/architecture (including 32 vs. 64 bit):**
brendan@ubuntu:~$ lsb_release -d

Description:	Ubuntu 8.10


**10) Restarting the network:**
brendan@ubuntu:~$ sudo /etc/init.d/networking restart

[sudo] password for brendan: 

 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by kurowoof on 2009-04-05
bumpity

---

