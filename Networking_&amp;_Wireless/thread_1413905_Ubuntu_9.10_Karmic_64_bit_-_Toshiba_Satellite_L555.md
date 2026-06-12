---
title: "Ubuntu 9.10 Karmic 64 bit - Toshiba Satellite L555 - No wireless detected ?"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by WILL_CHAN on 2010-02-23
Just bought a laptop Toshiba, I installed Ubuntu 9.10 Karmic 64 bit version dual-boot with Windows 7. I got wired connected but my wireless did not work. I could not see any network name so I could not enter my password.
I tried:

Solution 1:
> 
I was a completely new user to Ubuntu. Installed on a partition next to XP and everything worked ... apart from wireless !

Must of read and tried a hundred suggestions on the subject and I was clearly going round in circles. It got to the stage where I literally couldn't remember what I'd tried and what I hadn't. Started copying suggestions into a doc so I could at least be methodical. Finally got round to one which suggested installing wicd. This is actually a really friendly GUI alternative to Network Manger ... and it worked perfectly for me. Followed the instructions and ... bingo ! It now all works perfectly.

Excerpt from post is shown below. Apologies to whoever posted it as I didn't keep a record of their name. Like I said, I was getting desperate. After following the steps below, when I opened wicd (Applications/Internet/Wicd Network Manager), my network was shown and I just had to configure the connection under Properties button (put in the key for the router). I also had to set it to "WPA 1/2 (preshared key)" to get it to work (if you try this, you'll see what I mean

Original Post: (bold text is what I followed)

On Jaunty, Wicd is in the Universe Repository. To install:
. First, reintstall network manager in case you wish to switch back.


sudo apt-get install -d --reinstall network-manager network-manager-gnome

This will download the packages for network manager. If you don't do this, you won't be able to do it after you install wicd, because you may not have the packages available, and maybe you can't get the network working either.

    * sudo aptitude install wicd

Aptitude will attempt to remove network-manager and gnome-network-manager. Allow it to do so ... 

Did not work !:(

Solution 2:
> sudo apt-get update && sudo apt-get install bcmwl-kernel-source
Did not work either :( !

My laptop configuration:
```

 id:	
chan-laptop
description: 	Notebook
product: 	Satellite L555D
vendor: 	TOSHIBA
version: 	PSLXJU-00N00C
serial: 	1A022296K
width: 	64 bits
capabilities: 	smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
configuration:	
boot	=	oem-specific
chassis	=	notebook
uuid	=	1EC6C976-E36C-11DE-8E1C-002622F7824D
id:	
core
description: 	Motherboard
product: 	NTWAE
vendor: 	TOSHIBA
physical id: 	
0
version: 	1.00
serial: 	0123456789AB
id:	
firmware
description: 	BIOS
vendor: 	TOSHIBA
physical id: 	
0
version: 	V1.20 (11/26/2009)
size: 	112KiB
capacity: 	960KiB
capabilities: 	pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer int10video acpi usb ieee1394boot smartbattery biosbootspecification
id:	
cpu
description: 	CPU
product: 	AMD Turion(tm) II Dual-Core Mobile M520
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
4
bus info: 	
cpu@0
version: 	New Processor Technology
slot: 	Socket M2/S1G1
size: 	800MHz
capacity: 	2300MHz
width: 	64 bits
clock: 	200MHz
capabilities: 	fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpufreq
id:	
cache:0
description: 	L1 cache
physical id: 	
5
slot: 	L1 Cache
size: 	256KiB
capacity: 	256KiB
clock: 	1GHz (1.0ns)
capabilities: 	pipeline-burst internal write-back unified
id:	
cache:1
description: 	L2 cache
physical id: 	
6
slot: 	L2 Cache
size: 	1MiB
capacity: 	1MiB
clock: 	1GHz (1.0ns)
capabilities: 	pipeline-burst internal write-back unified
id:	
memory
description: 	System Memory
physical id: 	
e
slot: 	System board or motherboard
size: 	4GiB
id:	
bank:0
description: 	DIMM DDR2 Synchronous 800 MHz (1.2 ns)
product: 	8HTF12864HDY-800G1
vendor: 	Toshiba
physical id: 	
0
serial: 	DD456AF3
slot: 	S1
size: 	2GiB
width: 	64 bits
clock: 	800MHz (1.2ns)
id:	
bank:1
description: 	DIMM DDR2 Synchronous 800 MHz (1.2 ns)
product: 	64T128020EDL2.5C2
vendor: 	Toshiba
physical id: 	
1
serial: 	1706DB14
slot: 	S2
size: 	2GiB
width: 	64 bits
clock: 	800MHz (1.2ns)
id:	
pci:0
description: 	Host bridge
product: 	RS780 Host Bridge Alternate
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
100
bus info: 	
pci@0000:00:00.0
version: 	00
width: 	32 bits
clock: 	66MHz
id:	
pci:0
description: 	PCI bridge
product: 	Toshiba America Info Systems
vendor: 	Toshiba America Info Systems
physical id: 	
1
bus info: 	
pci@0000:00:01.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pci ht bus_master cap_list
resources:	
ioport	:	9000(size=4096)
memory	:	cfd00000-cfefffff
ioport	:	d0000000(size=268435456)
id:	
display
description: 	VGA compatible controller
product: 	ATI Technologies Inc
vendor: 	ATI Technologies Inc
physical id: 	
5
bus info: 	
pci@0000:01:05.0
version: 	00
width: 	32 bits
clock: 	33MHz
capabilities: 	pm msi bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	d0000000-dfffffff(prefetchable)
ioport	:	9000(size=256)
memory	:	cfdf0000-cfdfffff
memory	:	cfe00000-cfefffff
id:	
pci:1
description: 	PCI bridge
product: 	RS780 PCI to PCI bridge (PCIE port 0)
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
4
bus info: 	
pci@0000:00:04.0
version: 	00
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pm pciexpress msi ht bus_master cap_list
configuration:	
driver	=	pcieport-driver
resources:	
irq	:	25
id:	
pci:2
description: 	PCI bridge
product: 	RS780 PCI to PCI bridge (PCIE port 2)
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
6
bus info: 	
pci@0000:00:06.0
version: 	00
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pm pciexpress msi ht bus_master cap_list
configuration:	
driver	=	pcieport-driver
resources:	
irq	:	26
ioport	:	a000(size=4096)
memory	:	f0200000-f02fffff
id:	
network
description: 	Network controller
product: 	Realtek Semiconductor Co., Ltd.
vendor: 	Realtek Semiconductor Co., Ltd.
physical id: 	
0
bus info: 	
pci@0000:0e:00.0
version: 	10
width: 	32 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
latency	=	0
resources:	
ioport	:	a000(size=256)
memory	:	f0200000-f0203fff
id:	
pci:3
description: 	PCI bridge
product: 	RS780 PCI to PCI bridge (PCIE port 3)
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
7
bus info: 	
pci@0000:00:07.0
version: 	00
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pm pciexpress msi ht bus_master cap_list
configuration:	
driver	=	pcieport-driver
resources:	
irq	:	27
ioport	:	b000(size=4096)
memory	:	c8000000-c80fffff
ioport	:	f0400000(size=1048576)
id:	
network
description: 	Ethernet interface
product: 	RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: 	Realtek Semiconductor Co., Ltd.
physical id: 	
0
bus info: 	
pci@0000:14:00.0
logical name: 	
eth0
version: 	02
serial: 	00:26:22:f7:82:4d
size: 	10MB/s
capacity: 	100MB/s
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	r8169
driverversion	=	2.3LK-NAPI
duplex	=	half
ip	=	192.168.1.106
latency	=	0
link	=	yes
multicast	=	yes
port	=	MII
speed	=	10MB/s
resources:	
irq	:	28
ioport	:	b000(size=256)
memory	:	f0410000-f0410fff(prefetchable)
memory	:	f0400000-f040ffff(prefetchable)
memory	:	f0420000-f043ffff(prefetchable)
id:	
storage
description: 	SATA controller
product: 	SB700/SB800 SATA Controller [AHCI mode]
vendor: 	ATI Technologies Inc
physical id: 	
11
bus info: 	
pci@0000:00:11.0
logical name: 	
scsi1
logical name: 	
scsi3
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	storage pm bus_master cap_list emulated
configuration:	
driver	=	ahci
latency	=	64
resources:	
irq	:	22
ioport	:	8420(size=8)
ioport	:	8414(size=4)
ioport	:	8418(size=8)
ioport	:	8410(size=4)
ioport	:	8400(size=16)
memory	:	f0308000-f03083ff
id:	
disk
description: 	ATA Disk
product: 	FUJITSU MJA2320B
vendor: 	Fujitsu
physical id: 	
0
bus info: 	
scsi@1:0.0.0
logical name: 	
/dev/sda
version: 	0040
serial: 	K935T9C2BRUK
size: 	298GiB (320GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	d06abea8
id:	
volume:0
description: 	Windows NTFS volume
physical id: 	
1
bus info: 	
scsi@1:0.0.0,1
logical name: 	
/dev/sda1
version: 	3.1
serial: 	d29e-e8ea
size: 	1498MiB
capacity: 	1500MiB
capabilities: 	primary bootable ntfs initialized
configuration:	
clustersize	=	4096
created	=	2009-12-03 06:12:17
filesystem	=	ntfs
label	=	System
state	=	clean
id:	
volume:1
description: 	Windows NTFS volume
physical id: 	
2
bus info: 	
scsi@1:0.0.0,2
logical name: 	
/dev/sda2
version: 	3.1
serial: 	44a6c524-f84b-1747-bd30-58c6d4adcb11
size: 	145GiB
capacity: 	145GiB
capabilities: 	primary ntfs initialized
configuration:	
clustersize	=	4096
created	=	2009-12-03 06:13:18
filesystem	=	ntfs
label	=	TI105757W0A
state	=	clean
id:	
volume:2
description: 	Windows NTFS volume
physical id: 	
3
bus info: 	
scsi@1:0.0.0,3
logical name: 	
/dev/sda3
version: 	3.1
serial: 	02ea-5ff9
size: 	9132MiB
capacity: 	9141MiB
capabilities: 	primary hidden ntfs initialized
configuration:	
clustersize	=	4096
created	=	2009-12-03 06:14:22
filesystem	=	ntfs
label	=	HDDRECOVERY
state	=	clean
id:	
volume:3
description: 	Extended partition
physical id: 	
4
bus info: 	
scsi@1:0.0.0,4
logical name: 	
/dev/sda4
size: 	142GiB
capacity: 	142GiB
capabilities: 	primary extended partitioned partitioned:extended
id:	
logicalvolume:0
description: 	Linux filesystem partition
physical id: 	
5
logical name: 	
/dev/sda5
logical name: 	
/
capacity: 	136GiB
configuration:	
mount.fstype	=	ext4
mount.options	=	rw,relatime,errors=remount-ro,barrier=1,data=ordered
state	=	mounted
id:	
logicalvolume:1
description: 	Linux swap / Solaris partition
physical id: 	
6
logical name: 	
/dev/sda6
capacity: 	5945MiB
capabilities: 	nofs
id:	
cdrom
description: 	DVD-RAM writer
product: 	CDDVDW TS-L633Y
vendor: 	TSSTcorp
physical id: 	
1
bus info: 	
scsi@3:0.0.0
logical name: 	
/dev/cdrom
logical name: 	
/dev/cdrw
logical name: 	
/dev/dvd
logical name: 	
/dev/dvdrw
logical name: 	
/dev/scd0
logical name: 	
/dev/sr0
version: 	TF01
capabilities: 	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
status	=	nodisc
id:	
usb:0
description: 	USB Controller
product: 	SB700/SB800 USB OHCI0 Controller
vendor: 	ATI Technologies Inc
physical id: 	
12
bus info: 	
pci@0000:00:12.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	bus_master
configuration:	
driver	=	ohci_hcd
latency	=	64
resources:	
irq	:	16
memory	:	f0304000-f0304fff
id:	
usb:1
description: 	USB Controller
product: 	SB700 USB OHCI1 Controller
vendor: 	ATI Technologies Inc
physical id: 	
12.1
bus info: 	
pci@0000:00:12.1
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	bus_master
configuration:	
driver	=	ohci_hcd
latency	=	64
resources:	
irq	:	16
memory	:	f0305000-f0305fff
id:	
usb:2
description: 	USB Controller
product: 	SB700/SB800 USB EHCI Controller
vendor: 	ATI Technologies Inc
physical id: 	
12.2
bus info: 	
pci@0000:00:12.2
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pm debug bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	64
resources:	
irq	:	17
memory	:	f0308400-f03084ff
id:	
usb:3
description: 	USB Controller
product: 	SB700/SB800 USB OHCI0 Controller
vendor: 	ATI Technologies Inc
physical id: 	
13
bus info: 	
pci@0000:00:13.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	bus_master
configuration:	
driver	=	ohci_hcd
latency	=	64
resources:	
irq	:	18
memory	:	f0306000-f0306fff
id:	
usb:4
description: 	USB Controller
product: 	SB700 USB OHCI1 Controller
vendor: 	ATI Technologies Inc
physical id: 	
13.1
bus info: 	
pci@0000:00:13.1
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	bus_master
configuration:	
driver	=	ohci_hcd
latency	=	64
resources:	
irq	:	18
memory	:	f0307000-f0307fff
id:	
usb:5
description: 	USB Controller
product: 	SB700/SB800 USB EHCI Controller
vendor: 	ATI Technologies Inc
physical id: 	
13.2
bus info: 	
pci@0000:00:13.2
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pm debug bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	64
resources:	
irq	:	19
memory	:	f0308800-f03088ff
id:	
serial
description: 	SMBus
product: 	SBx00 SMBus Controller
vendor: 	ATI Technologies Inc
physical id: 	
14
bus info: 	
pci@0000:00:14.0
version: 	3c
width: 	32 bits
clock: 	66MHz
capabilities: 	ht cap_list
configuration:	
driver	=	piix4_smbus
latency	=	0
resources:	
irq	:	0
id:	
multimedia
description: 	Audio device
product: 	SBx00 Azalia (Intel HDA)
vendor: 	ATI Technologies Inc
physical id: 	
14.2
bus info: 	
pci@0000:00:14.2
version: 	00
width: 	64 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	64
resources:	
irq	:	16
memory	:	f0300000-f0303fff
id:	
isa
description: 	ISA bridge
product: 	SB700/SB800 LPC host controller
vendor: 	ATI Technologies Inc
physical id: 	
14.3
bus info: 	
pci@0000:00:14.3
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	isa bus_master
configuration:	
latency	=	0
id:	
pci:4
description: 	PCI bridge
product: 	SBx00 PCI to PCI Bridge
vendor: 	ATI Technologies Inc
physical id: 	
14.4
bus info: 	
pci@0000:00:14.4
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pci bus_master
id:	
pci:1
description: 	Host bridge
product: 	K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
101
bus info: 	
pci@0000:00:18.0
version: 	00
width: 	32 bits
clock: 	33MHz
id:	
pci:2
description: 	Host bridge
product: 	K10 [Opteron, Athlon64, Sempron] Address Map
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
102
bus info: 	
pci@0000:00:18.1
version: 	00
width: 	32 bits
clock: 	33MHz
id:	
pci:3
description: 	Host bridge
product: 	K10 [Opteron, Athlon64, Sempron] DRAM Controller
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
103
bus info: 	
pci@0000:00:18.2
version: 	00
width: 	32 bits
clock: 	33MHz
id:	
pci:4
description: 	Host bridge
product: 	K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
104
bus info: 	
pci@0000:00:18.3
version: 	00
width: 	32 bits
clock: 	33MHz
id:	
pci:5
description: 	Host bridge
product: 	K10 [Opteron, Athlon64, Sempron] Link Control
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
105
bus info: 	
pci@0000:00:18.4
version: 	00
width: 	32 bits
clock: 	33MHz
id:	
battery
description: 	Lithium Ion Battery
product: 	TOSHIBA
vendor: 	TOSHIBA
physical id: 	
1
slot: 	1st Battery
capacity: 	60000mWh
configuration:	
voltage	=	10.8V

```
My laptop is Toshiba Satellite L555. Anyone experienced with this ?

**Running lspci :**
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

**Running lsmod**
```

Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
joydev                 13088  0 
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
psmouse                57124  0 
serio_raw               6596  0 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
amd64_edac_mod         26688  0 
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              11728  0 
edac_core              48876  1 amd64_edac_mod
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
shpchp                 37756  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
usbhid                 43968  0 
video                  23612  0 
output                  3680  1 video
r8169                  38884  0 
mii                     6368  1 r8169
radeon                684512  1 
ttm                    43056  1 radeon
drm                   193856  3 radeon,ttm
i2c_algo_bit            7076  1 radeon

```

**Running lsusb**
> 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by WILL_CHAN on 2010-02-23
**Also running sudo lshw -C network**
```

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:a000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:f7:82:4d
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.106 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:b000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)

```

**Running ipconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:26:22:f7:82:4d  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fef7:824d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7024834 (7.0 MB)  TX bytes:917175 (917.1 KB)
          Interrupt:28 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**Running iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

**Running nm-tool**
```

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:26:22:F7:82:4D

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             209.18.47.61
    DNS:             209.18.47.62
    DNS:             192.168.1.1

```

---

### Post by northd_tech on 2010-02-23
> **WILL_CHAN said:**
> 0e:00.0 Network controller: **Realtek** Semiconductor Co., Ltd. Device **8172**  (rev 10)
14:00.0 Ethernet controller: **Realtek** Semiconductor Co., Ltd.  **RTL8101E/RTL8102E** PCI 
Well, I've "gone my rounds" with the Toshiba Satellite P505D laptop, and we are "staying in our corners" until Realtek's technical support gets back to me...

I couldn't see the output of those commands until I tried to quote them, then they showed up, but there was something really strange in the code...

Anyway, your "lspci" identifies that wireless as a Realtek 8172, I believe.  There has been some confusion/cross-over between the 817x and the 819x Realtek's, and there are HUGE differences between the letter codes "e", "se", "su", etc. that they put on the end.  You should probably search this forum for "realtek 8172" and read the more recent threads.

My advice (and the concensus on this forum apparently) is to email Realtek directly (since the [censored] **won't post the current Linux drivers to their international website** [http://www.realtek.com.tw](http://www.realtek.com.tw) and they quit answering my emails about their 8192E "driver" about 2 weeks ago- grrrr... )

You can reach the Realtek "support" loop at:

[http://www.realtek.com.tw/contact/contentView.aspx?Langid=1&PNid=1&PFid=4&Level=2](http://www.realtek.com.tw/contact/contentView.aspx?Langid=1&PNid=1&PFid=4&Level=2)

[email]wlanfae@realtek.com[/email]

You will want to be CERTAIN to get the proper architecture version- 32-bit vs. 64-bit, and this terminal command will tell you that part:

```
uname -mr
```
an "i686" means 32 bit, where an "x86_64" means 64-bit

---

### Post by WILL_CHAN on 2010-02-23
Hello northd_tech ! First, thanks a lot for your reply but this sounds like there are too much trouble just for the wireless :( ! I've just bought this today, so I still have 14 days exchange policy. Is any other branch ( HP, Accer, Dell, Sony... ) easier for this configuration?
I used Ubuntu 8.04 LTS and 9.04 before, wireless works pretty smoothly. Don't know why this 9.10 Karmic has too many troubles.

---

### Post by northd_tech on 2010-02-23
> **WILL_CHAN said:**
> Hello northd_tech ! First, thanks a lot for your reply but this sounds like there are too much trouble just for the wireless :( ! I've just bought this today, so I still have 14 days exchange policy. Is any other branch ( HP, Accer, Dell, Sony... ) easier for this configuration?
I used Ubuntu 8.04 LTS and 9.04 before, wireless works pretty smoothly. Don't know why this 9.10 Karmic has too many troubles.

Well my HP DV9800 series has been really good under Linux, possibly one of the best Linux laptops that I've seen (but I stayed with ubuntu 9.04 and avoided 9.10).  My advice would be to take a LiveCD of whichever Linux distribution you prefer (or more that one) and try it out on whatever computers you are interested in.

HINT:  Run lspci, lshw | grep -C network, ifconfig, iwconfig, etc. both with and without cabled network connections.

I have the NVIDIA video and [older] nForce ethernet in mine- and those have been very good.  My Broadcom "4328" wireless is reported by Windows Vista as a 4321AG, and it worked very well with ndiswrapper (which I'm considering going back to to test the speed under ubuntu), and also the proprietary Broadcom "STA" driver when that was released.  Also, the NVIDIA "Hi-Def" sound has worked perfectly (but the volume thing gets messed up under Microsoft Vista- no surprises there though).

Realtek had given pretty good support (very quick email response), but I've been going in circles with them since about Nov. 2009 now, trying to get this 8192E wireless issue resolved.  Now they just seem to ignore my incoming emails, after claiming that I didn't know how to read a compiler error (when I had quoted the error message in the original email).

---

### Post by WILL_CHAN on 2010-02-23
Thanks northd_tech once again ! 
Another question is that if I come back with Ubuntu 8.04 LTS, could it solve this problem ?
I tried Ubuntu 8.04 on my HP Pavilion dv4-1430us before and it worked pretty well. I don't know is there any differences between HP and Toshiba under Ubuntu 8.04 LTS ?

---

### Post by northd_tech on 2010-02-23
No. from my ubuntu experience with the Toshiba Satellite laptops- the Toshiba hardware is just TOO NEW.   Perhaps Lucid ubuntu version 10.xx will "fix" that, but I'm not holding my breath waiting for that to happen.

I don't plan on leaving ubuntu 9.04 until/way past about June/July 2010 (with that release scheduled for Mar/April?), and there is a chance that I might do something other than ubuntu, but I'm still undecided.

Long ago, there was an "approved?" list of "Linux friendly" hardware (especially for laptops), but I fear that laptop computer usage, and Linux usage, and everything else has expanded so much that there probably is no longer a current "good list" for Linux hardware...

edit:  P.S.- 64 bit makes it Soooooo much worse, too.

---

### Post by WILL_CHAN on 2010-02-23
Just got my wireless working ;) ! Found the solution here:
[http://forum.novatech.co.uk/showthread.php?p=197789](http://forum.novatech.co.uk/showthread.php?p=197789)
Hope it help you too !

---

### Post by Kangarooo on 2010-05-24
> **WILL_CHAN said:**
> 
My laptop configuration:
```


id:	
cpu
description: 	CPU
product: 	AMD Turion(tm) II Dual-Core Mobile M520
vendor: 	Advanced Micro Devices [AMD]
physical id: 	
4
bus info: 	
cpu@0
version: 	New Processor Technology
slot: 	Socket M2/S1G1
size: 	800MHz
capacity: 	2300MHz
width: 	64 bits
clock: 	200MHz
capabilities: 	fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt 

```



What means for CPU ?
size: 	800MHz
capacity: 	2300MHz

couse for laptop i have just size:2500MHz and no capaciy
why like that why it means?

---

