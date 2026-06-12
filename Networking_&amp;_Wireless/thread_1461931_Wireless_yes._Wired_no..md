---
title: "Wireless yes. Wired no."
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by eshriek on 2010-04-24
I have a dual boot system with Win 7 and Ubuntu 9.10. I cannot access my router using an ethernet connection on either platform. Using an older mac I am able to access the router through a wired connection (so I know the router is good.)

My questions:

How do I get my wired connection back? Why do I have eth2 but not eth0?

*If I can access localhost or a server like apache does this happen through the ethernet card? Is the ethernet card distinct from the wireless card?

Could I have messed my network connections with vmware or virtualbox? How do I delete those network connections? I've remove the virtual images completely.

Thanks

ifconfig:
eth2      Link encap:Ethernet  HWaddr 00:22:5f:e5:ef:e9  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fee5:efe9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26571 errors:0 dropped:0 overruns:0 frame:11898
          TX packets:20828 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25566450 (25.5 MB)  TX bytes:3923654 (3.9 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.50.1  Bcast:172.16.50.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.137.1  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lshw -C network:
 id: my-laptop
description: 	Portable Computer
product: 	Inspiron 1545
vendor: 	Dell Inc. 
width: 	32 bits
capabilities: 	smbios-2.4 dmi-2.4
configuration:	
boot	=	normal
chassis	=	portable 
id:	
core
description: 	Motherboard 
vendor: 	Dell Inc.
physical id: 	
0
id:	
firmware
description: 	BIOS
vendor: 	Dell Inc.
physical id: 	
0
version: 	A08 (06/03/2009)
size: 	64KiB
capacity: 	15MiB
capabilities: 	isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
id:	
cpu
description: 	CPU
product: 	Pentium(R) Dual-Core CPU T4200 @ 2.00GHz
vendor: 	Intel Corp.
physical id: 	
400
bus info: 	
cpu@0
version: 	6.7.10
serial: 	0001-067A-0000-0000-0000-0000
slot: 	Microprocessor
size: 	1200MHz
capacity: 	2GHz
width: 	64 bits
clock: 	200MHz
capabilities: 	fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
configuration:	
id	=	1
id:	
cache:0
description: 	L1 cache
physical id: 	
700
size: 	128KiB
capacity: 	128KiB
capabilities: 	internal write-back data
id:	
cache:1
description: 	L2 cache
physical id: 	
701
size: 	1MiB
capacity: 	1MiB
clock: 	66MHz (15.0ns)
capabilities: 	pipeline-burst internal varies unified
id:	
logicalcpu:0
description: 	Logical CPU
physical id: 	
1.1
width: 	64 bits
capabilities: 	logical
id:	
logicalcpu:1
description: 	Logical CPU
physical id: 	
1.2
width: 	64 bits
capabilities: 	logical
id:	
memory
description: 	System Memory
physical id: 	
1000
slot: 	System board or motherboard
size: 	3GiB
id:	
bank:0
description: 	DIMM DDR Synchronous 800 MHz (1.2 ns)
product: 	HYMP112S64CP6-S6
vendor: 	AD00000000000000
physical id: 	
0
serial: 	5E70DC5E
slot: 	DIMM_A
size: 	1GiB
width: 	64 bits
clock: 	800MHz (1.2ns)
id:	
bank:1
description: 	DIMM DDR Synchronous 800 MHz (1.2 ns)
product: 	HYMP125S64CP8-S6
vendor: 	AD00000000000000
physical id: 	
1
serial: 	4E102D26
slot: 	DIMM_B
size: 	2GiB
width: 	64 bits
clock: 	800MHz (1.2ns)
id:	
pci
description: 	Host bridge
product: 	Mobile 4 Series Chipset Memory Controller Hub
vendor: 	Intel Corporation
physical id: 	
100
bus info: 	
pci@0000:00:00.0
version: 	07
width: 	32 bits
clock: 	33MHz
configuration:	
driver	=	agpgart-intel
resources:	
irq	:	0
id:	
display:0
description: 	VGA compatible controller
product: 	Mobile 4 Series Chipset Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	07
width: 	64 bits
clock: 	33MHz
capabilities: 	msi pm bus_master cap_list rom
configuration:	
driver	=	i915
latency	=	0
resources:	
irq	:	28
memory	:	f6c00000-f6ffffff
memory	:	e0000000-efffffff(prefetchable)
ioport	:	efe8(size=8)
id:	
display:1
description: 	Display controller
product: 	Mobile 4 Series Chipset Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2.1
bus info: 	
pci@0000:00:02.1
version: 	07
width: 	64 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	f6b00000-f6bfffff
id:	
usb:0
description: 	USB Controller
product: 	82801I (ICH9 Family) USB UHCI Controller #4
vendor: 	Intel Corporation
physical id: 	
1a
bus info: 	
pci@0000:00:1a.0
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	20
ioport	:	6f60(size=32)
id:	
usb:1
description: 	USB Controller
product: 	82801I (ICH9 Family) USB UHCI Controller #5
vendor: 	Intel Corporation
physical id: 	
1a.1
bus info: 	
pci@0000:00:1a.1
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	21
ioport	:	6f80(size=32)
id:	
usb:2
description: 	USB Controller
product: 	82801I (ICH9 Family) USB UHCI Controller #6
vendor: 	Intel Corporation
physical id: 	
1a.2
bus info: 	
pci@0000:00:1a.2
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	22
ioport	:	6fa0(size=32)
id:	
usb:3
description: 	USB Controller
product: 	82801I (ICH9 Family) USB2 EHCI Controller #2
vendor: 	Intel Corporation
physical id: 	
1a.7
bus info: 	
pci@0000:00:1a.7
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	pm debug bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	0
resources:	
irq	:	22
memory	:	fed1c400-fed1c7ff
id:	
multimedia
description: 	Audio device
product: 	82801I (ICH9 Family) HD Audio Controller
vendor: 	Intel Corporation
physical id: 	
1b
bus info: 	
pci@0000:00:1b.0
version: 	03
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	0
resources:	
irq	:	21
memory	:	f6afc000-f6afffff
id:	
pci:0
description: 	PCI bridge
product: 	82801I (ICH9 Family) PCI Express Port 1
vendor: 	Intel Corporation
physical id: 	
1c
bus info: 	
pci@0000:00:1c.0
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pciexpress msi pm bus_master cap_list
configuration:	
driver	=	pcieport-driver
resources:	
irq	:	24
id:	
pci:1
description: 	PCI bridge
product: 	82801I (ICH9 Family) PCI Express Port 2
vendor: 	Intel Corporation
physical id: 	
1c.1
bus info: 	
pci@0000:00:1c.1
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pciexpress msi pm bus_master cap_list
configuration:	
driver	=	pcieport-driver
resources:	
irq	:	25
memory	:	f6900000-f69fffff
id:	
network
description: 	Wireless interface
product: 	BCM4312 802.11b/g
vendor: 	Broadcom Corporation
physical id: 	
0
bus info: 	
pci@0000:0c:00.0
logical name: 	
eth2
version: 	01 
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	wl0
driverversion	=	5.10.91.9
ip	=	192.168.2.11
latency	=	0
multicast	=	yes
wireless	=	IEEE 802.11bg
resources:	
irq	:	17
memory	:	f69fc000-f69fffff
id:	
pci:2
description: 	PCI bridge
product: 	82801I (ICH9 Family) PCI Express Port 5
vendor: 	Intel Corporation
physical id: 	
1c.4
bus info: 	
pci@0000:00:1c.4
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pciexpress msi pm bus_master cap_list
configuration:	
driver	=	pcieport-driver
resources:	
irq	:	26
ioport	:	d000(size=4096)
memory	:	f6600000-f68fffff
ioport	:	f0000000(size=2097152)
id:	
usb:4
description: 	USB Controller
product: 	82801I (ICH9 Family) USB UHCI Controller #1
vendor: 	Intel Corporation
physical id: 	
1d
bus info: 	
pci@0000:00:1d.0
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	20
ioport	:	6f00(size=32)
id:	
usb:5
description: 	USB Controller
product: 	82801I (ICH9 Family) USB UHCI Controller #2
vendor: 	Intel Corporation
physical id: 	
1d.1
bus info: 	
pci@0000:00:1d.1
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	21
ioport	:	6f20(size=32)
id:	
usb:6
description: 	USB Controller
product: 	82801I (ICH9 Family) USB UHCI Controller #3
vendor: 	Intel Corporation
physical id: 	
1d.2
bus info: 	
pci@0000:00:1d.2
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	22
ioport	:	6f40(size=32)
id:	
usb:7
description: 	USB Controller
product: 	82801I (ICH9 Family) USB2 EHCI Controller #1
vendor: 	Intel Corporation
physical id: 	
1d.7
bus info: 	
pci@0000:00:1d.7
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	pm debug bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	0
resources:	
irq	:	20
memory	:	fed1c000-fed1c3ff
id:	
pci:3
description: 	PCI bridge
product: 	82801 Mobile PCI Bridge
vendor: 	Intel Corporation
physical id: 	
1e
bus info: 	
pci@0000:00:1e.0
version: 	93
width: 	32 bits
clock: 	33MHz
capabilities: 	pci bus_master cap_list
id:	
isa
description: 	ISA bridge
product: 	ICH9M LPC Interface Controller
vendor: 	Intel Corporation
physical id: 	
1f
bus info: 	
pci@0000:00:1f.0
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	isa bus_master cap_list
configuration:	
latency	=	0
id:	
storage
description: 	SATA controller
product: 	ICH9M/M-E SATA AHCI Controller
vendor: 	Intel Corporation
physical id: 	
1f.2
bus info: 	
pci@0000:00:1f.2
logical name: 	
scsi0
logical name: 	
scsi1
version: 	03
width: 	32 bits
clock: 	66MHz
capabilities: 	storage msi pm bus_master cap_list emulated
configuration:	
driver	=	ahci
latency	=	0
resources:	
irq	:	27
ioport	:	6e70(size=8)
ioport	:	6e78(size=4)
ioport	:	6e80(size=8)
ioport	:	6e88(size=4)
ioport	:	6ea0(size=32)
memory	:	fed1c800-fed1cfff
id:	
disk
description: 	ATA Disk
product: 	TOSHIBA MK2555GS
vendor: 	Toshiba
physical id: 	
0
bus info: 	
scsi@0:0.0.0
logical name: 	
/dev/sda
version: 	FG00
serial: 	79MFTPI6T
size: 	232GiB (250GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	f7e3aa15
id:	
volume:0
description: 	Windows FAT volume
vendor: 	Dell 8.0
physical id: 	
1
bus info: 	
scsi@0:0.0.0,1
logical name: 	
/dev/sda1
version: 	FAT16
serial: 	3030-3030
size: 	39MiB
capacity: 	39MiB
capabilities: 	primary fat initialized
configuration:	
FATs	=	2
filesystem	=	fat
label	=	DellUtility
id:	
volume:1
description: 	Linux swap volume
physical id: 	
2
bus info: 	
scsi@0:0.0.0,2
logical name: 	
/dev/sda2
version: 	1
serial: 	eea50349-b340-4667-9a2a-82ccdb3f0273
size: 	6675MiB
capacity: 	6675MiB
capabilities: 	primary nofs swap initialized
configuration:	
filesystem	=	swap
pagesize	=	4096
id:	
volume:2
description: 	Windows NTFS volume
physical id: 	
3
bus info: 	
scsi@0:0.0.0,3
logical name: 	
/dev/sda3
version: 	3.1
serial: 	e68cd5a3-8ed9-8545-bb40-40f95b39368e
size: 	115GiB
capacity: 	115GiB
capabilities: 	primary bootable ntfs initialized
configuration:	
clustersize	=	4096
created	=	2009-06-23 23:08:12
filesystem	=	ntfs
label	=	OS
state	=	clean
id:	
volume:3
description: 	EXT3 volume
vendor: 	Linux
physical id: 	
4
bus info: 	
scsi@0:0.0.0,4
logical name: 	
/dev/sda4
logical name: 	
/
version: 	1.0
serial: 	a6e6d5f1-8cfb-4f34-a6bc-eb697a8878e2
size: 	102GiB
capacity: 	102GiB
capabilities: 	primary journaled extended_attributes large_files recover ext3 ext2 initialized
configuration:	
created	=	2010-01-19 18:25:38
filesystem	=	ext3
modified	=	2010-04-24 18:22:13
mount.fstype	=	ext3
mount.options	=	rw,relatime,errors=remount-ro,data=writeback
mounted	=	2010-04-24 18:22:13
state	=	mounted
id:	
cdrom
description: 	DVD-RAM writer
product: 	DVD+-RW TS-L633C
vendor: 	TSSTcorp
physical id: 	
1
bus info: 	
scsi@1:0.0.0
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
version: 	D300
capabilities: 	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
status	=	nodisc
id:	
serial
description: 	SMBus
product: 	82801I (ICH9 Family) SMBus Controller
vendor: 	Intel Corporation
physical id: 	
1f.3
bus info: 	
pci@0000:00:1f.3
version: 	03
width: 	64 bits
clock: 	33MHz
configuration:	
latency	=	0
resources:	
memory	:	f6afbf00-f6afbfff
ioport	:	1100(size=32)
id:	
scsi
physical id: 	
1
bus info: 	
usb@1:5
logical name: 	
scsi6
capabilities: 	emulated scsi-host
configuration:	
driver	=	usb-storage
id:	
disk
description: 	SCSI Disk
physical id: 	
0.0.0
bus info: 	
scsi@6:0.0.0
logical name: 	
/dev/sdb
id:	
network
description: 	Ethernet interface
physical id: 	
1
logical name: 	
vboxnet0
serial: 	0a:00:27:00:00:00
capabilities: 	ethernet physical
configuration:	
broadcast	=	yes
multicast	=	yes

---

### Post by eshriek on 2010-04-25
Doh. I must have accidentally disabled ethernet in the BIOS. I have no recollection of doing that, but that is all it was.

---

### Post by Iowan on 2010-04-25
Congrats!
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

