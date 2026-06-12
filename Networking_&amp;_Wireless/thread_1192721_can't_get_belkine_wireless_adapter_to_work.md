---
title: "can't get belkine wireless adapter to work"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by sandjkirkland on 2009-06-20
can't get wireless adapter to work 

--------------------------------------------------------------------------------

I can not get my usb Belkin Wireless adapter to work on Ubuntu 8.04.1 LTS Desktop Edition. 
I also tried Fedora 10 no luck there either.
Be AWARE that this is a VERY long post due to the info that was requested.

I followed your info request in the order that you gave
1)lsusb -v ;had to use -v for version
2)lsmod
3)dmesg ;VERY LONG list
4)dmesg | grep firmware; did NOT come up with any info NOT POSTED HERE
5)uname-r ;info can also be found in dmesg with more info on line 3

<BEGIN lsusb -v
admin1@admin1-desktop:~$ lsusb -v
Bus 003 Device 005: ID 050d:935a Belkin Components 
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 2.00
bDeviceClass 0 (Defined at Interface level)
bDeviceSubClass 0 
bDeviceProtocol 0 
bMaxPacketSize0 64
idVendor 0x050d Belkin Components
idProduct 0x935a 
bcdDevice 1.01
iManufacturer 1 
iProduct 2 
iSerial 3 
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 67
bNumInterfaces 1
bConfigurationValue 1
iConfiguration 0 
bmAttributes 0x80
(Bus Powered)
MaxPower 450mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 7
bInterfaceClass 255 Vendor Specific Class
bInterfaceSubClass 255 Vendor Specific Subclass
bInterfaceProtocol 255 Vendor Specific Protocol
iInterface 5 
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x01 EP 1 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x02 EP 2 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x03 EP 3 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x04 EP 4 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x05 EP 5 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x06 EP 6 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

<^THERE WERE OTHER DEVICES AND PORTS LISTED BUT THIS ONE IS THE WIRELESS ADAPTER^>
<i.e Printer was listed, and unused ports listed>
END>


<BEGIN lsmod
admin1@admin1-desktop:~$ lsmod
Module Size Used by
isofs 36388 0 
udf 88612 0 
nls_iso8859_1 4992 1 
nls_cp437 6656 1 
vfat 14464 1 
fat 54556 1 vfat
ipv6 267780 8 
radeon 124192 2 
drm 82452 3 radeon
rfcomm 41744 2 
l2cap 25728 13 rfcomm
bluetooth 61156 4 rfcomm,l2cap
ppdev 10372 0 
powernow_k8 16704 0 
cpufreq_userspace 5284 0 
cpufreq_powersave 2688 0 
cpufreq_ondemand 9740 1 
cpufreq_conservative 8712 0 
cpufreq_stats 7104 0 
freq_table 5536 3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs 15112 0 
dock 11280 0 
container 5632 0 
sbshc 7680 1 sbs
video 19856 0 
output 4736 1 video
battery 14212 0 
iptable_filter 3840 0 
ip_tables 14820 1 iptable_filter
x_tables 16132 1 ip_tables
ac 6916 0 
sbp2 24072 0 
lp 12324 0 
snd_atiixp 21388 3 
snd_ac97_codec 101028 1 snd_atiixp
ac97_bus 3072 1 snd_ac97_codec
snd_pcm_oss 42144 0 
snd_mixer_oss 17920 1 snd_pcm_oss
snd_pcm 78596 3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
evdev 13056 3 
serio_raw 7940 0 
snd_seq_dummy 4868 0 
parport_pc 36260 1 
parport 37832 3 ppdev,lp,parport_pc
psmouse 40336 0 
snd_seq_oss 35584 0 
snd_seq_midi 9376 0 
snd_rawmidi 25760 1 snd_seq_midi
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi
pcspkr 4224 0 
k8temp 6656 0 
snd_seq 54224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 24836 2 snd_pcm,snd_seq
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
snd 56996 17 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_os s,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,sn d_seq,snd_timer,snd_seq_device
soundcore 8800 1 snd
snd_page_alloc 11400 2 snd_atiixp,snd_pcm
usblp 15872 0 
i2c_piix4 9612 0 
button 9232 0 
i2c_core 24832 1 i2c_piix4
ati_agp 9996 0 
agpgart 34760 2 drm,ati_agp
shpchp 34452 0 
pci_hotplug 30880 1 shpchp
usb_storage 73664 0 
ext3 136712 1 
jbd 48404 1 ext3
mbcache 9600 1 ext3
sg 36880 0 
sr_mod 17956 0 
cdrom 37408 1 sr_mod
sd_mod 30720 4 
atiixp 5648 0 [permanent]
ide_core 113996 1 atiixp
libusual 19108 1 usb_storage
8139cp 24704 0 
pata_acpi 8320 0 
ohci1394 33584 0 
ieee1394 93752 2 sbp2,ohci1394
8139too 27520 0 
mii 6400 2 8139cp,8139too
pata_atiixp 8960 0 
ehci_hcd 37900 0 
ohci_hcd 25348 0 
sata_sil 12296 3 
ata_generic 8324 0 
usbcore 146028 6 usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
libata 159344 4 pata_acpi,pata_atiixp,sata_sil,ata_generic
scsi_mod 151436 6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
thermal 16796 0 
processor 36872 2 powernow_k8,thermal
fan 5636 0 
fbcon 42912 0 
tileblit 3456 1 fbcon
font 9472 1 fbcon
bitblit 6784 1 fbcon
softcursor 3072 1 bitblit
fuse 50580 3 
<^ EVERYTHING THAT WAS LISTED IS ABOVE , NOTHING KEPT OUT ^>
END>

<BEGIN dmesg
admin1@admin1-desktop:~$ dmesg
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 0000000037ef0000 (usable)
[ 0.000000] BIOS-e820: 0000000037ef0000 - 0000000037ef3000 (ACPI NVS)
[ 0.000000] BIOS-e820: 0000000037ef3000 - 0000000037f00000 (ACPI data)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 894MB LOWMEM available.
[ 0.000000] found SMP MP-table at 000f4650
[ 0.000000] Entering add_active_range(0, 0, 229104) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 229104
[ 0.000000] HighMem 229104 -> 229104
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 229104
[ 0.000000] On node 0 totalpages: 229104
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 1757 pages used for memmap
[ 0.000000] Normal zone: 223251 pages, LIFO batch:31
[ 0.000000] HighMem zone: 0 pages used for memmap
[ 0.000000] Movable zone: 0 pages used for memmap
[ 0.000000] DMI 2.4 present.
[ 0.000000] ACPI: RSDP signature @ 0xC00F84A0 checksum 0
[ 0.000000] ACPI: RSDP 000F84A0, 0014 (r0 HP-CPC)
[ 0.000000] ACPI: RSDT 37EF3040, 0030 (r1 HP-CPC AWRDACPI 42302E31 AWRD 0)
[ 0.000000] ACPI: FACP 37EF30C0, 0084 (r2 HP-CPC AWRDACPI 42302E31 AWRD 0)
[ 0.000000] ACPI: DSDT 37EF31C0, 3785 (r1 HP-CPC AWRDACPI 1000 MSFT 100000E)
[ 0.000000] ACPI: FACS 37EF0000, 0040
[ 0.000000] ACPI: MCFG 37EF6A80, 003C (r1 HP-CPC AWRDACPI 42302E31 AWRD 0)
[ 0.000000] ACPI: APIC 37EF69C0, 005A (r1 HP-CPC AWRDACPI 42302E31 AWRD 0)
[ 0.000000] ATI board detected. Disabling timer routing over 8254.
[ 0.000000] ACPI: PM-Timer IO Port: 0x4008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] Processor #0 15:15 APIC version 16
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] Allocating PCI resources starting at 40000000 (gap: 37f00000:a8100000)
[ 0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[ 0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[ 0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 227315
[ 0.000000] Kernel command line: root=UUID=bb6fd9a4-e4ff-42da-99ae-cd25faaa0010 ro quiet splash
[ 0.000000] mapped APIC to ffffb000 (fee00000)
[ 0.000000] mapped IOAPIC to ffffa000 (fec00000)
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] Detected 2188.899 MHz processor.
[ 27.447186] Console: colour VGA+ 80x25
[ 27.447189] console [tty0] enabled
[ 27.447477] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 27.447800] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 27.460066] Memory: 896004k/916416k available (2177k kernel code, 19812k reserved, 1006k data, 368k init, 0k highmem)
[ 27.460072] virtual kernel memory layout:
[ 27.460073] fixmap : 0xfff4b000 - 0xfffff000 ( 720 kB)
[ 27.460074] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 27.460075] vmalloc : 0xf8800000 - 0xff7fe000 ( 111 MB)
[ 27.460076] lowmem : 0xc0000000 - 0xf7ef0000 ( 894 MB)
[ 27.460077] .init : 0xc0421000 - 0xc047d000 ( 368 kB)
[ 27.460078] .data : 0xc0320434 - 0xc041bdc4 (1006 kB)
[ 27.460079] .text : 0xc0100000 - 0xc0320434 (2177 kB)
[ 27.460082] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 27.460107] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[ 27.539991] Calibrating delay using timer specific routine.. 4382.03 BogoMIPS (lpj=8764061)
[ 27.540009] Security Framework initialized
[ 27.540013] SELinux: Disabled at boot.
[ 27.540024] AppArmor: AppArmor initialized
[ 27.540027] Failure registering capabilities with primary security module.
[ 27.540033] Mount-cache hash table entries: 512
[ 27.540110] Initializing cgroup subsys ns
[ 27.540113] Initializing cgroup subsys cpuacct
[ 27.540120] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[ 27.540127] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 27.540129] CPU: L2 Cache: 512K (64 bytes/line)
[ 27.540131] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[ 27.540138] Compat vDSO mapped to ffffe000.
[ 27.540146] Checking 'hlt' instruction... OK.
[ 27.556172] SMP alternatives: switching to UP code
[ 27.557032] Freeing SMP alternatives: 11k freed
[ 27.557123] Early unpacking initramfs... done
[ 27.844430] ACPI: Core revision 20070126
[ 27.844471] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[ 27.852224] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 00
[ 27.852244] Total of 1 processors activated (4382.03 BogoMIPS).
[ 27.852406] ENABLING IO-APIC IRQs
[ 27.852582] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 27.892239] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 27.892279] ...trying to set up timer (IRQ0) through the 8259A ... failed.
[ 27.892281] ...trying to set up timer as Virtual Wire IRQ... works.
[ 28.039172] Brought up 1 CPUs
[ 28.039189] CPU0 attaching sched-domain:
[ 28.039192] domain 0: span 01
[ 28.039193] groups: 01
[ 28.039325] net_namespace: 64 bytes
[ 28.039330] Booting paravirtualized kernel on bare hardware
[ 28.039705] Time: 20:33:50 Date: 06/16/09
[ 28.039723] NET: Registered protocol family 16
[ 28.039854] EISA bus registered
[ 28.039881] ACPI: bus type pci registered
[ 28.072335] PCI: PCI BIOS revision 3.00 entry at 0xfa900, last bus=2
[ 28.072337] PCI: Using configuration type 1
[ 28.072345] Setting up standard PCI resources
[ 28.074759] ACPI: EC: Look up EC in DSDT
[ 28.077081] ACPI: Interpreter enabled
[ 28.077084] ACPI: (supports S0 S1 S3 S4 S5)
[ 28.077094] ACPI: Using IOAPIC for interrupt routing
[ 28.079635] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 28.080776] PCI: Transparent bridge - 0000:00:14.4
[ 28.080803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 28.080924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[ 28.081032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[ 28.092412] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[ 28.092481] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[ 28.092548] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[ 28.092614] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[ 28.092681] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11)
[ 28.092747] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[ 28.092813] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
[ 28.092879] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *10 11)
[ 28.092956] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 28.092976] pnp: PnP ACPI init
[ 28.092981] ACPI: bus type pnp registered
[ 28.094608] pnpacpi: exceeded the max number of mem resources: 12
[ 28.094643] pnp: PnP ACPI: found 12 devices
[ 28.094645] ACPI: ACPI bus type pnp unregistered
[ 28.094647] PnPBIOS: Disabled by ACPI PNP
[ 28.094799] PCI: Using ACPI for IRQ routing
[ 28.094801] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 28.094808] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[ 28.142984] NET: Registered protocol family 8
[ 28.142985] NET: Registered protocol family 20
[ 28.143036] AppArmor: AppArmor Filesystem Enabled
[ 28.146952] Time: tsc clocksource has been installed.
[ 28.154963] system 00:01: ioport range 0x228-0x22f has been reserved
[ 28.154965] system 00:01: ioport range 0x40b-0x40b has been reserved
[ 28.154968] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[ 28.154970] system 00:01: ioport range 0xc00-0xc01 has been reserved
[ 28.154972] system 00:01: ioport range 0xc14-0xc14 has been reserved
[ 28.154974] system 00:01: ioport range 0xc50-0xc52 has been reserved
[ 28.154977] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[ 28.154979] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[ 28.154981] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[ 28.154983] system 00:01: ioport range 0x4000-0x40fe has been reserved
[ 28.154985] system 00:01: ioport range 0x4210-0x4217 has been reserved
[ 28.154991] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[ 28.154993] system 00:06: ioport range 0x800-0x87f has been reserved
[ 28.154999] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[ 28.155003] system 00:0b: iomem range 0xf0000-0xf3fff could not be reserved
[ 28.155006] system 00:0b: iomem range 0xf4000-0xf7fff could not be reserved
[ 28.155008] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[ 28.155011] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[ 28.155013] system 00:0b: iomem range 0x37f00000-0x37ffffff has been reserved
[ 28.155015] system 00:0b: iomem range 0x37ef0000-0x37efffff could not be reserved
[ 28.155018] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
[ 28.155020] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[ 28.155023] system 00:0b: iomem range 0x100000-0x37eeffff could not be reserved
[ 28.155025] system 00:0b: iomem range 0x38000000-0x3fffffff has been reserved
[ 28.155028] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[ 28.155030] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[ 28.185274] PCI: Bridge: 0000:00:01.0
[ 28.185276] IO window: e000-efff
[ 28.185278] MEM window: fdd00000-fddfffff
[ 28.185280] PREFETCH window: d0000000-dfffffff
[ 28.185283] PCI: Bridge: 0000:00:14.4
[ 28.185286] IO window: d000-dfff
[ 28.185291] MEM window: fdc00000-fdcfffff
[ 28.185296] PREFETCH window: fde00000-fdefffff
[ 28.185320] NET: Registered protocol family 2
[ 28.222880] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 28.223108] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 28.223770] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 28.224114] TCP: Hash tables configured (established 131072 bind 65536)
[ 28.224116] TCP reno registered
[ 28.234910] checking if image is initramfs... it is
[ 28.686026] Switched to high resolution mode on CPU 0
[ 28.791436] Freeing initrd memory: 7701k freed
[ 28.791887] audit: initializing netlink socket (disabled)
[ 28.791897] audit(1245184431.188:1): initialized
[ 28.793306] VFS: Disk quotas dquot_6.5.1
[ 28.793357] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 28.793451] io scheduler noop registered
[ 28.793453] io scheduler anticipatory registered
[ 28.793454] io scheduler deadline registered
[ 28.793462] io scheduler cfq registered (default)
[ 28.793467] PCI: MSI quirk detected. MSI deactivated.
[ 28.845712] Boot video device is 0000:01:05.0
[ 28.845896] isapnp: Scanning for PnP cards...
[ 29.199623] isapnp: No Plug & Play device found
[ 29.220483] Real Time Clock Driver v1.12ac
[ 29.220550] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 29.221398] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 29.221448] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 29.221513] PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[ 29.224455] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 29.224459] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 29.225234] mice: PS/2 mouse device common for all mice
[ 29.225320] EISA: Probing bus 0 at eisa.0
[ 29.225339] Cannot allocate resource for EISA slot 4
[ 29.225357] EISA: Detected 0 cards.
[ 29.225359] cpuidle: using governor ladder
[ 29.225361] cpuidle: using governor menu
[ 29.225428] NET: Registered protocol family 1
[ 29.225447] Using IPI No-Shortcut mode
[ 29.225469] registered taskstats version 1
[ 29.225553] Magic number: 13:353:599
[ 29.225556] hash matches device serial8250
[ 29.225613] hash matches device ptyd3
[ 29.225688] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 29.225690] EDD information not available.
[ 29.225873] Freeing unused kernel memory: 368k freed
[ 29.260960] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[ 30.394359] fuse init (API version 7.9)
[ 30.412180] ACPI: Processor [CPU0] (supports 8 throttling states)
[ 30.826297] SCSI subsystem initialized
[ 30.870077] libata version 3.00 loaded.
[ 30.882116] usbcore: registered new interface driver usbfs
[ 30.882134] usbcore: registered new interface driver hub
[ 30.906034] usbcore: registered new device driver usb
[ 30.914044] sata_sil 0000:00:11.0: version 2.3
[ 30.914086] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 16
[ 30.921989] scsi0 : sata_sil
[ 30.929992] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 30.936199] scsi1 : sata_sil
[ 30.936243] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 16
[ 30.936247] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 16
[ 30.973918] 8139too Fast Ethernet driver 0.9.28
[ 31.245407] ata1: SATA link down (SStatus 0 SControl 300)
[ 31.556817] ata2: SATA link down (SStatus 0 SControl 300)
[ 31.556892] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[ 31.556966] scsi2 : sata_sil
[ 31.557140] scsi3 : sata_sil
[ 31.557163] ata3: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e080 irq 17
[ 31.557167] ata4: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e0c0 irq 17
[ 32.023994] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 32.033718] ata3.00: ATA-6: WDC WD2500JD-22HBC0, 08.02D08, max UDMA/133
[ 32.033721] ata3.00: 488397168 sectors, multi 16: LBA48 
[ 32.049708] ata3.00: configured for UDMA/100
[ 32.359370] ata4: SATA link down (SStatus 0 SControl 300)
[ 32.359460] scsi 2:0:0:0: Direct-Access ATA WDC WD2500JD-22H 08.0 PQ: 0 ANSI: 5
[ 32.362201] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[ 32.362213] ohci_hcd 0000:00:13.0: OHCI Host Controller
[ 32.362410] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[ 32.362428] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02d000
[ 32.419339] usb usb1: configuration #1 chosen from 1 choice
[ 32.419358] hub 1-0:1.0: USB hub found
[ 32.419367] hub 1-0:1.0: 4 ports detected
[ 32.523149] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[ 32.523163] ohci_hcd 0000:00:13.1: OHCI Host Controller
[ 32.523180] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[ 32.523194] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02c000
[ 32.583021] usb usb2: configuration #1 chosen from 1 choice
[ 32.583039] hub 2-0:1.0: USB hub found
[ 32.583047] hub 2-0:1.0: 4 ports detected
[ 32.687060] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[ 32.687073] ehci_hcd 0000:00:13.2: EHCI Host Controller
[ 32.687092] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[ 32.687140] ehci_hcd 0000:00:13.2: irq 18, io mem 0xfe02b000
[ 32.826519] usb 1-3: new full speed USB device using ohci_hcd and address 2
[ 32.838496] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 32.838581] usb usb3: configuration #1 chosen from 1 choice
[ 32.838599] hub 3-0:1.0: USB hub found
[ 32.838603] hub 3-0:1.0: 8 ports detected
[ 32.942571] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[ 32.943141] scsi4 : pata_atiixp
[ 32.943506] scsi5 : pata_atiixp
[ 32.943962] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf300 irq 14
[ 32.943965] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf308 irq 15
[ 32.944006] ata5: port disabled. ignoring.
[ 33.553730] ata6.00: ATAPI: ATAPI DVD C DH52C2P, MP55, max UDMA/33
[ 33.553747] ata6.01: ATAPI: LITE-ON DVDRW SOHW-1693S, KS0A, max UDMA/66
[ 33.553757] ata6.01: limited to UDMA/33 due to 40-wire cable
[ 33.741363] ata6.00: configured for UDMA/33
[ 33.772815] usb 3-2: new high speed USB device using ehci_hcd and address 2
[ 33.907592] usb 3-2: configuration #1 chosen from 1 choice
[ 33.913127] ata6.01: configured for UDMA/33
[ 33.914364] scsi 5:0:0:0: CD-ROM ATAPI DVD C DH52C2P MP55 PQ: 0 ANSI: 5
[ 33.915204] scsi 5:0:1:0: CD-ROM LITE-ON DVDRW SOHW-1693S KS0A PQ: 0 ANSI: 5
[ 33.916523] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[ 33.917710] eth0: RealTek RTL8139 at 0xdf00, 00:11:09:11:d8:f7, IRQ 20
[ 33.917712] eth0: Identified 8139 chip type 'RTL-8100B/8139D'
[ 33.918921] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[ 33.971573] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21] MMIO=[fdcfe000-fdcfe7ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 33.981687] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 33.990260] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 33.990265] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 33.995846] Driver 'sd' needs updating - please use bus_type methods
[ 33.995912] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 33.995922] sd 2:0:0:0: [sda] Write Protect is off
[ 33.995924] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 33.995937] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 33.995971] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 33.995978] sd 2:0:0:0: [sda] Write Protect is off
[ 33.995980] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 33.995992] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 33.995994] sda:<4>Driver 'sr' needs updating - please use bus_type methods
[ 34.015100] sda1 sda2 < sda5 sda6 sda7 > sda3
[ 34.057426] sd 2:0:0:0: [sda] Attached SCSI disk
[ 34.062189] sd 2:0:0:0: Attached scsi generic sg0 type 0
[ 34.062205] sr 5:0:0:0: Attached scsi generic sg1 type 5
[ 34.062218] scsi 5:0:1:0: Attached scsi generic sg2 type 5
[ 34.069218] sr0: scsi3-mmc drive: 0x/52x writer cd/rw xa/form2 cdda tray
[ 34.069222] Uniform CD-ROM driver Revision: 3.20
[ 34.069263] sr 5:0:0:0: Attached scsi CD-ROM sr0
[ 34.074818] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[ 34.074861] sr 5:0:1:0: Attached scsi CD-ROM sr1
[ 34.184079] usb 3-4: new high speed USB device using ehci_hcd and address 3
[ 34.323790] usb 3-4: configuration #1 chosen from 1 choice
[ 34.421488] Attempting manual resume
[ 34.421491] swsusp: Resume From Partition 8:7
[ 34.421492] PM: Checking swsusp image.
[ 34.421637] PM: Resume from disk failed.
[ 34.453780] kjournald starting. Commit interval 5 seconds
[ 34.453791] EXT3-fs: mounted filesystem with ordered data mode.
[ 34.567389] usb 3-5: new high speed USB device using ehci_hcd and address 4
[ 34.701786] usb 3-5: configuration #1 chosen from 1 choice
[ 34.938728] usb 3-6: new high speed USB device using ehci_hcd and address 5
[ 35.087907] usb 3-6: configuration #1 chosen from 1 choice
[ 35.250245] ieee1394: Host added: ID:BUS[0-00:1023] GUID[0011066600980842]
[ 35.326106] usbcore: registered new interface driver libusual
[ 35.629487] usb 1-4: new full speed USB device using ohci_hcd and address 3
[ 35.838246] usb 1-4: configuration #1 chosen from 1 choice
[ 35.987802] Initializing USB Mass Storage driver...
[ 35.987850] scsi6 : SCSI emulation for USB Mass Storage devices
[ 35.987903] usb-storage: device found at 2
[ 35.987905] usb-storage: waiting for device to settle before scanning
[ 35.987923] scsi7 : SCSI emulation for USB Mass Storage devices
[ 35.987959] usb-storage: device found at 3
[ 35.987960] usb-storage: waiting for device to settle before scanning
[ 35.987977] scsi8 : SCSI emulation for USB Mass Storage devices
[ 35.988015] usb-storage: device found at 4
[ 35.988017] usb-storage: waiting for device to settle before scanning
[ 35.988034] scsi9 : SCSI emulation for USB Mass Storage devices
[ 35.988066] usbcore: registered new interface driver usb-storage
[ 35.988068] USB Mass Storage support registered.
[ 35.988208] usb-storage: device found at 3
[ 35.988210] usb-storage: waiting for device to settle before scanning
[ 40.816156] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 40.877843] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 40.931036] Linux agpgart interface v0.102
[ 41.059682] usb-storage: device scan complete
[ 41.060235] scsi 6:0:0:0: Direct-Access Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 41.061466] sd 6:0:0:0: [sdb] 1953792 512-byte hardware sectors (1000 MB)
[ 41.062097] sd 6:0:0:0: [sdb] Write Protect is off
[ 41.062100] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 41.062102] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 41.064712] sd 6:0:0:0: [sdb] 1953792 512-byte hardware sectors (1000 MB)
[ 41.065338] sd 6:0:0:0: [sdb] Write Protect is off
[ 41.065340] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 41.065342] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 41.065346] sdb: sdb1
[ 41.066184] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 41.066233] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 41.087630] usb-storage: device scan complete
[ 41.089452] scsi 7:0:0:0: Direct-Access EPSON Stylus Storage 1.00 PQ: 0 ANSI: 2
[ 41.092956] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 41.093001] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 41.123569] usb-storage: device scan complete
[ 41.124131] scsi 8:0:0:0: Direct-Access SanDisk U3 Cruzer Micro 2.18 PQ: 0 ANSI: 2
[ 41.124619] scsi 8:0:0:1: CD-ROM SanDisk U3 Cruzer Micro 2.18 PQ: 0 ANSI: 2
[ 41.125858] sd 8:0:0:0: [sdd] 990865 512-byte hardware sectors (507 MB)
[ 41.126493] sd 8:0:0:0: [sdd] Write Protect is off
[ 41.126496] sd 8:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 41.126498] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 41.129103] sd 8:0:0:0: [sdd] 990865 512-byte hardware sectors (507 MB)
[ 41.129744] sd 8:0:0:0: [sdd] Write Protect is off
[ 41.129746] sd 8:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 41.129748] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 41.129752] sdd: sdd1 sdd2
[ 41.132981] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[ 41.133033] sd 8:0:0:0: Attached scsi generic sg5 type 0
[ 41.135347] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 41.135406] sr 8:0:0:1: Attached scsi CD-ROM sr2
[ 41.135467] sr 8:0:0:1: Attached scsi generic sg6 type 5
[ 41.149816] usb-storage: device scan complete
[ 41.154712] scsi 9:0:0:0: Direct-Access Generic USB SD Reader 1.00 PQ: 0 ANSI: 0
[ 41.160710] scsi 9:0:0:1: Direct-Access Generic USB CF Reader 1.01 PQ: 0 ANSI: 0
[ 41.166694] scsi 9:0:0:2: Direct-Access Generic USB SM Reader 1.02 PQ: 0 ANSI: 0
[ 41.172671] scsi 9:0:0:3: Direct-Access Generic USB MS Reader 1.03 PQ: 0 ANSI: 0
[ 41.182726] sd 9:0:0:0: [sde] Attached SCSI removable disk
[ 41.182782] sd 9:0:0:0: Attached scsi generic sg7 type 0
[ 41.192700] sd 9:0:0:1: [sdf] Attached SCSI removable disk
[ 41.192753] sd 9:0:0:1: Attached scsi generic sg8 type 0
[ 41.202694] sd 9:0:0:2: [sdg] Attached SCSI removable disk
[ 41.202748] sd 9:0:0:2: Attached scsi generic sg9 type 0
[ 41.212685] sd 9:0:0:3: [sdh] Attached SCSI removable disk
[ 41.212753] sd 9:0:0:3: Attached scsi generic sg10 type 0
[ 41.263467] input: Power Button (FF) as /devices/virtual/input/input2
[ 41.275349] ACPI: Power Button (FF) [PWRF]
[ 41.275417] input: Power Button (CM) as /devices/virtual/input/input3
[ 41.287271] ACPI: Power Button (CM) [PWRB]
[ 41.303308] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[ 42.660868] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0838
[ 42.660885] usbcore: registered new interface driver usblp
[ 43.411556] input: PC Speaker as /devices/platform/pcspkr/input/input4
[ 43.926907] ACPI: PCI Interrupt 0000:00:14.5[b] -> GSI 17 (level, low) -> IRQ 22
[ 44.328617] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[ 44.352819] parport_pc 00:07: reported by Plug and Play ACPI
[ 44.352861] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[ 46.266254] lp0: using parport0 (interrupt-driven).
[ 46.331213] Adding 1614492k swap on /dev/sda7. Priority:-1 extents:1 across:1614492k
[ 46.864344] EXT3 FS on sda6, internal journal
[ 47.877810] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 48.214740] No dock devices found.
[ 48.421534] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[ 48.421566] powernow-k8: 0 : fid 0xe (2200 MHz), vid 0x6
[ 48.421568] powernow-k8: 1 : fid 0xc (2000 MHz), vid 0x8
[ 48.421570] powernow-k8: 2 : fid 0xa (1800 MHz), vid 0xa
[ 48.421572] powernow-k8: 3 : fid 0x2 (1000 MHz), vid 0x12
[ 48.942567] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[ 48.942572] apm: overridden by ACPI.
[ 49.046463] ppdev: user-space parallel port driver
[ 49.141652] audit(1245184451.967:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5196 profile="/usr/sbin/cupsd" namespace="default"
[ 54.526889] Marking TSC unstable due to: cpufreq changes.
[ 54.530642] Time: acpi_pm clocksource has been installed.
[ 62.228887] eth0: link down
[ 62.306681] Bluetooth: Core ver 2.11
[ 62.307185] NET: Registered protocol family 31
[ 62.307189] Bluetooth: HCI device and connection manager initialized
[ 62.307192] Bluetooth: HCI socket layer initialized
[ 62.313708] Clocksource tsc unstable (delta = -77702287 ns)
[ 62.349676] Bluetooth: L2CAP ver 2.9
[ 62.349681] Bluetooth: L2CAP socket layer initialized
[ 62.426195] Bluetooth: RFCOMM socket layer initialized
[ 62.426406] Bluetooth: RFCOMM TTY layer initialized
[ 62.426409] Bluetooth: RFCOMM ver 1.8
[ 115.416836] [drm] Initialized drm 1.1.0 20060810
[ 115.476961] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[ 115.477098] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[ 116.365009] [drm] Setting GART location based on new memory map
[ 116.365344] [drm] Loading R300 Microcode
[ 116.365368] [drm] writeback test succeeded in 1 usecs
[ 176.048941] NET: Registered protocol family 10
[ 176.049593] lo: Disabled Privacy Extensions
[ 176.050485] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 84.106934] kjournald starting. Commit interval 5 seconds
[ 84.110996] EXT3 FS on sdd2, internal journal
[ 84.111004] EXT3-fs: mounted filesystem with ordered data mode.
[ 234.040221] end_request: I/O error, dev sr1, sector 64
[ 234.040230] Buffer I/O error on device sr1, logical block 8
[ 234.042243] end_request: I/O error, dev sr1, sector 64
[ 234.042249] Buffer I/O error on device sr1, logical block 8
[ 234.059377] end_request: I/O error, dev sr1, sector 0
[ 234.059385] Buffer I/O error on device sr1, logical block 0
[ 234.061313] end_request: I/O error, dev sr1, sector 8
[ 234.061319] Buffer I/O error on device sr1, logical block 1
[ 234.063202] end_request: I/O error, dev sr1, sector 0
[ 234.063208] Buffer I/O error on device sr1, logical block 0
[ 234.081190] end_request: I/O error, dev sr1, sector 0
[ 234.081196] Buffer I/O error on device sr1, logical block 0
[ 234.082790] end_request: I/O error, dev sr1, sector 0
[ 234.082796] Buffer I/O error on device sr1, logical block 0
[ 1386.999728] end_request: I/O error, dev sr1, sector 64
[ 1386.999738] Buffer I/O error on device sr1, logical block 8
[ 1387.001512] end_request: I/O error, dev sr1, sector 64
[ 1387.001520] Buffer I/O error on device sr1, logical block 8
[ 1387.023062] end_request: I/O error, dev sr1, sector 0
[ 1387.023072] Buffer I/O error on device sr1, logical block 0
[ 1387.024851] end_request: I/O error, dev sr1, sector 8
[ 1387.024858] Buffer I/O error on device sr1, logical block 1
[ 1387.026599] end_request: I/O error, dev sr1, sector 0
[ 1387.026606] Buffer I/O error on device sr1, logical block 0
[ 1387.044579] end_request: I/O error, dev sr1, sector 0
[ 1387.044589] Buffer I/O error on device sr1, logical block 0
[ 1387.046413] end_request: I/O error, dev sr1, sector 0
[ 1387.046422] Buffer I/O error on device sr1, logical block 0
[ 1870.968768] cdrom: This disc doesn't have any tracks I recognize!
[ 2588.912992] end_request: I/O error, dev sr1, sector 64
[ 2588.913001] Buffer I/O error on device sr1, logical block 8
[ 2588.914995] end_request: I/O error, dev sr1, sector 64
[ 2588.915001] Buffer I/O error on device sr1, logical block 8
[ 2588.931701] end_request: I/O error, dev sr1, sector 0
[ 2588.931710] Buffer I/O error on device sr1, logical block 0
[ 2588.933277] end_request: I/O error, dev sr1, sector 8
[ 2588.933283] Buffer I/O error on device sr1, logical block 1
[ 2588.934956] end_request: I/O error, dev sr1, sector 0
[ 2588.934962] Buffer I/O error on device sr1, logical block 0
[ 2588.953022] end_request: I/O error, dev sr1, sector 0
[ 2588.953028] Buffer I/O error on device sr1, logical block 0
[ 2588.954643] end_request: I/O error, dev sr1, sector 0
[ 2588.954648] Buffer I/O error on device sr1, logical block 0
[ 2589.022294] end_request: I/O error, dev sr1, sector 64
[ 2589.022303] Buffer I/O error on device sr1, logical block 8
[ 2589.023832] end_request: I/O error, dev sr1, sector 64
[ 2589.023838] Buffer I/O error on device sr1, logical block 8
[ 2589.025382] end_request: I/O error, dev sr1, sector 64
[ 2589.025388] Buffer I/O error on device sr1, logical block 8
[ 2605.035083] ata6.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2605.035102] ata6.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 2605.035104] cdb 1b 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00
[ 2605.035107] res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 2605.035113] ata6.01: status: { DRDY }
[ 2607.610314] ata6: soft resetting link
[ 2608.410618] ata6.00: configured for UDMA/33
[ 2608.574566] ata6.01: configured for UDMA/33
[ 2608.574587] ata6: EH complete
[ 2716.500554] nautilus[5838] general protection eip:8c30b5a esp:bf88ca48 error:0
[ 2824.437898] cdrom: sr0: mrw address space DMA selected
[ 2824.644472] cdrom: sr0: mrw address space DMA selected
[ 2824.867373] UDF-fs: Partition marked readonly; forcing readonly mount
[ 2824.912793] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD Video Recording', timestamp 2006/12/11 10:17 (1f10)
[ 3213.482256] cdrom: This disc doesn't have any tracks I recognize!
[ 3864.352898] ata6.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3864.352918] ata6.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 3864.352921] cdb 1b 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00
[ 3864.352924] res 40/00:03:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 3864.352929] ata6.01: status: { DRDY }
[ 3868.831592] ata6: soft resetting link
[ 3869.631893] ata6.00: configured for UDMA/33
[ 3870.892129] ata6.01: configured for UDMA/33
[ 3870.892155] ata6: EH complete
[ 3994.419993] ata6.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3994.420012] ata6.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 3994.420015] cdb 1b 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00
[ 3994.420017] res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 3994.420023] ata6.01: status: { DRDY }
[ 3998.842695] ata6: soft resetting link
[ 3999.643014] ata6.00: configured for UDMA/33
[ 4000.814682] ata6.01: configured for UDMA/33
[ 4000.814706] ata6: EH complete
[ 4103.953652] end_request: I/O error, dev sr1, sector 64
[ 4103.953663] Buffer I/O error on device sr1, logical block 8
[ 4103.955682] end_request: I/O error, dev sr1, sector 64
[ 4103.955691] Buffer I/O error on device sr1, logical block 8
[ 4888.733400] usb 3-5: USB disconnect, address 4
[ 4892.416665] usb 3-2: USB disconnect, address 2
END>


<BEGIN uname -r
admin1@admin1-desktop:~$ uname -r
2.6.24-19-generic
END>

---

### Post by tmht on 2009-06-23
With the device plugged in do an iwconfig and then unplug the device and do an iwconfig.

---

### Post by drrdf2 on 2009-06-24
Try the procedure here: 


[http://ubuntuforums.org/showthread.php?t=1118187](http://ubuntuforums.org/showthread.php?t=1118187)

---

### Post by sandjkirkland on 2009-06-30
I've tried ndiswrapper and installed the driver but I can't go any further than that. I think it is trying to load the realtek ethernet driver  before the belkin driver so there seems to conflict. How do I blacklist the realtek ethernet driver.

---

