---
title: "Trendnet TEW-421PC Not Working"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by najeer on 2009-07-08
Recieved the following errors:


sudo dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:c0:9f:12:38:bb
Sending on   LPF/eth0/00:c0:9f:12:38:bb
Listening on LPF/wlan0/00:14:d1:5f:f2:4b
Sending on   LPF/wlan0/00:14:d1:5f:f2:4b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Dell PowerEdge 500SC
Ubuntu 8.0.4.2 Server
2.6.24-23-Server i686
Realtek Semiconductor LTD, RTL8185 IEEE 802.11 a/b/g Wireless Lan Controller (REV. 20)


Script started on Wed 08 Jul 2009 12:05:51 PM EDT
root@asteriscos:/# lspci[K[K[K[K[Klspci
00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 06)
00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 06)
00:02.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:06.0 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
00:0b.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0f.0 ISA bridge: Broadcom CSB5 South Bridge (rev 92)
00:0f.1 IDE interface: Broadcom CSB5 IDE Controller (rev 92)
00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 05)
00:0f.3 Host bridge: Broadcom CSB5 LPC bridge
root@asteriscos:/# lsusb
Bus 001 Device 002: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)
Bus 001 Device 001: ID 0000:0000  
root@asteriscos:/# lspci -nn | grep Realtek
00:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
root@asteriscos:/# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@asteriscos:/# iwcoi[Knfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@asteriscos:/# iwcoinf[K[K[Knfig wlan0
wlan0     No such device

root@asteriscos:/# ;s[K[Klsmod
Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14592  1 
fat                    54300  1 vfat
usb_storage            73536  1 
libusual               19108  1 usb_storage
ipv6                  272932  17 
dahdi_echocan_mg2       6920  0 
xpp_usb                19400  0 
xpp                   152640  1 xpp_usb
wctc4xxp               49180  0 
dahdi_transcode         9352  1 wctc4xxp
wcb4xxp                83492  0 
wctdm                  40652  0 
wcfxo                  13984  0 
wctdm24xxp            135136  0 
wcte11xp               27424  0 
wct1xxp                16544  0 
wcte12xp               71392  0 
wct4xxp               353920  0 
dahdi                 197768  11 dahdi_echocan_mg2,xpp,dahdi_transcode,wcb4xxp,wctdm,wcfxo,wctdm24xxp,wcte11xp,wct1xxp,wcte12xp,wct4xxp
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
loop                   19076  0 
serio_raw               7940  0 
snd_emu10k1           146880  0 
i2c_piix4               9612  0 
snd_rawmidi            25632  1 snd_emu10k1
snd_ac97_codec        100772  1 snd_emu10k1
i2c_core               24832  1 i2c_piix4
ac97_bus                3072  1 snd_ac97_codec
hisax                 501760  0 
snd_pcm                78596  2 snd_emu10k1,snd_ac97_codec
snd_seq_device          9612  2 snd_emu10k1,snd_rawmidi
button                  9232  0 
crc_ccitt               3072  2 dahdi,hisax
cfi_probe               6912  0 
gen_probe               4608  1 cfi_probe
snd_timer              24836  2 snd_emu10k1,snd_pcm
snd_page_alloc         11528  2 snd_emu10k1,snd_pcm
snd_util_mem            5632  1 snd_emu10k1
isdn                  139232  1 hisax
scb2_flash              5388  0 
mtd                    17540  1 scb2_flash
snd_hwdep              10500  1 snd_emu10k1
snd                    56868  7 snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
sworks_agp             10656  0 
slhc                    7040  1 isdn
chipreg                 4224  2 cfi_probe,scb2_flash
soundcore               8800  1 snd
parport_pc             36644  1 
parport                37704  2 lp,parport_pc
agpgart                34760  1 sworks_agp
emu10k1_gp              4736  0 
map_funcs               2816  1 scb2_flash
dcdbas                  9508  0 
gameport               16008  2 emu10k1_gp
evdev                  12928  0 
psmouse                40208  0 
pcspkr                  4224  0 
ext3                  136584  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36496  0 
sr_mod                 17828  0 
cdrom                  37280  1 sr_mod
sd_mod                 30720  5 
ata_generic             8324  0 
pata_acpi               8320  0 
pata_serverworks       11008  2 
floppy                 59332  0 
ohci_hcd               27024  0 
libata                159600  3 ata_generic,pata_acpi,pata_serverworks
usbcore               146284  5 usb_storage,libusual,xpp_usb,ohci_hcd
scsi_mod              151180  5 usb_storage,sg,sr_mod,sd_mod,libata
e100                   37516  0 
mii                     6400  1 e100
thermal                16796  0 
processor              36616  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 
root@asteriscos:/# l[Kdmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-server (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 22:22:14 UTC 2009 (Ubuntu 2.6.24-23.52-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffffc00 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FDC80 checksum 0
[    0.000000] ACPI: RSDP 000FDC80, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FDC94, 0030 (r1 DELL   PE500SC         2 MSFT  100000A)
[    0.000000] ACPI: FACP 000FDCC4, 0074 (r1 DELL   PE500SC         2 MSFT  100000A)
[    0.000000] ACPI: DSDT 1FFF0000, 2496 (r1 DELL   PE500SC         2 MSFT  100000A)
[    0.000000] ACPI: FACS 1FFFFC00, 0040
[    0.000000] ACPI: APIC 000FDD38, 0052 (r1 DELL   PE500SC         2 MSFT  100000A)
[    0.000000] ACPI: SPCR 000FDD8A, 0050 (r1 DELL   PE500SC         2 MSFT  100000A)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:11 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-15
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec01000] gsi_base[16])
[    0.000000] IOAPIC[1]: apic_id 2, version 17, address 0xfec01000, GSI 16-31
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=0c28c79d-7e83-4eff-8dfa-ba763dee3a5e ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fec01000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1196.861 MHz processor.
[   28.819137] Console: colour VGA+ 80x25
[   28.819146] console [tty0] enabled
[   28.819889] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.821173] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.870831] Memory: 507624k/524224k available (2258k kernel code, 15988k reserved, 1037k data, 384k init, 0k highmem)
[   28.870849] virtual kernel memory layout:
[   28.870851]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[   28.870854]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   28.870857]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
[   28.870859]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   28.870861]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
[   28.870864]       .data : 0xc0334a39 - 0xc0437fe4   (1037 kB)
[   28.870866]       .text : 0xc0100000 - 0xc0334a39   (2258 kB)
[   28.870872] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.870954] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   29.020877] Calibrating delay using timer specific routine.. 2394.85 BogoMIPS (lpj=11974282)
[   29.020934] Security Framework initialized
[   29.020951] SELinux:  Disabled at boot.
[   29.020982] AppArmor: AppArmor initialized
[   29.020991] Failure registering capabilities with primary security module.
[   29.021009] Mount-cache hash table entries: 512
[   29.021262] Initializing cgroup subsys ns
[   29.021271] Initializing cgroup subsys cpuacct
[   29.021293] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   29.021313] CPU: L1 I cache: 16K, L1 D cache: 16K
[   29.021317] CPU: L2 cache: 256K
[   29.021323] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   29.021340] Compat vDSO mapped to ffffe000.
[   29.021367] Checking 'hlt' instruction... OK.
[   29.061444] SMP alternatives: switching to UP code
[   29.063862] Freeing SMP alternatives: 12k freed
[   29.064134] Early unpacking initramfs... done
[   29.652410] ACPI: Core revision 20070126
[   29.652608] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.654959] CPU0: Intel(R) Celeron(TM) CPU                1200MHz stepping 04
[   29.655009] Total of 1 processors activated (2394.85 BogoMIPS).
[   29.655360] ENABLING IO-APIC IRQs
[   29.655609] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   29.870431] Brought up 1 CPUs
[   29.870504] CPU0 attaching sched-domain:
[   29.870511]  domain 0: span 01
[   29.870514]   groups: 01
[   29.871008] net_namespace: 64 bytes
[   29.871035] Booting paravirtualized kernel on bare hardware
[   29.872116] Time: 15:31:21  Date: 07/08/09
[   29.872195] NET: Registered protocol family 16
[   29.872670] EISA bus registered
[   29.872711] ACPI: bus type pci registered
[   29.889581] PCI: PCI BIOS revision 2.10 entry at 0xfc82e, last bus=1
[   29.889589] PCI: Using configuration type 1
[   29.889624] Setting up standard PCI resources
[   29.892782] ACPI: EC: Look up EC in DSDT
[   29.896070] ACPI: Interpreter enabled
[   29.896077] ACPI: (supports S0 S4 S5)
[   29.896097] ACPI: Using IOAPIC for interrupt routing
[   29.904837] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.904984] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   29.904989] * this clock source is slow. If you are sure your timer does not have
[   29.904992] * this bug, please use "acpi_pm_good" to disable the workaround
[   29.905026] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   29.905029] * this clock source is slow. If you are sure your timer does not have
[   29.905032] * this bug, please use "acpi_pm_good" to disable the workaround
[   29.905473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.907957] ACPI: PCI Root Bridge [PCI1] (0000:01)
[   29.908163] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   29.908869] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.909081] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.909274] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.909465] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.909660] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14)
[   29.909851] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.910043] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.910237] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14)
[   29.910525] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.910717] ACPI: PCI Interrupt Link [LNKJ] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.910910] ACPI: PCI Interrupt Link [LNKK] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.911103] ACPI: PCI Interrupt Link [LNKL] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.911297] ACPI: PCI Interrupt Link [LNKM] (IRQs 3 4 *5 6 7 9 10 11 12 14)
[   29.911490] ACPI: PCI Interrupt Link [LNKN] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.911685] ACPI: PCI Interrupt Link [LNKO] (IRQs 3 4 5 6 7 9 10 *11 12 14)
[   29.911877] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[   29.912073] ACPI: PCI Interrupt Link [LUSB] (IRQs *3 4 5 6 7 10 11 12 14)
[   29.912425] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.912493] pnp: PnP ACPI init
[   29.912518] ACPI: bus type pnp registered
[   29.922146] pnp: PnP ACPI: found 13 devices
[   29.922156] ACPI: ACPI bus type pnp unregistered
[   29.922165] PnPBIOS: Disabled by ACPI PNP
[   29.922704] PCI: Using ACPI for IRQ routing
[   29.922715] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.930641] NET: Registered protocol family 8
[   29.930648] NET: Registered protocol family 20
[   29.930765] NetLabel: Initializing
[   29.930770] NetLabel:  domain hash size = 128
[   29.930773] NetLabel:  protocols = UNLABELED CIPSOv4
[   29.930803] NetLabel:  unlabeled traffic allowed by default
[   29.930895] AppArmor: AppArmor Filesystem Enabled
[   29.940256] Time: tsc clocksource has been installed.
[   29.960362] system 00:0a: ioport range 0x814-0x85b has been reserved
[   29.960369] system 00:0a: ioport range 0x820-0x83f has been reserved
[   29.960374] system 00:0a: ioport range 0x580-0x58f has been reserved
[   29.960380] system 00:0a: ioport range 0xc00-0xcd7 has been reserved
[   29.960385] system 00:0a: ioport range 0xf50-0xf58 has been reserved
[   29.960407] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   29.960412] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   29.960417] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   29.960423] system 00:0c: iomem range 0xf0000-0xfffff could not be reserved
[   29.960430] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   29.960435] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   29.960441] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[   29.991338] NET: Registered protocol family 2
[   30.090346] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   30.090811] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   30.091219] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   30.091881] TCP: Hash tables configured (established 16384 bind 16384)
[   30.091889] TCP reno registered
[   30.120521] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   30.587956]  it is
[   31.204750] Freeing initrd memory: 7185k freed
[   31.206410] audit: initializing netlink socket (disabled)
[   31.206449] audit(1247067081.220:1): initialized
[   31.206794] Total HugeTLB memory allocated, 0
[   31.211279] VFS: Disk quotas dquot_6.5.1
[   31.211505] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.212113] io scheduler noop registered
[   31.212122] io scheduler anticipatory registered
[   31.212127] io scheduler deadline registered (default)
[   31.212165] io scheduler cfq registered
[   31.212205] PCI: Firmware left 0000:00:02.0 e100 interrupts enabled, disabling
[   31.212229] Boot video device is 0000:00:0b.0
[   31.229973] isapnp: Scanning for PnP cards...
[   31.586255] isapnp: No Plug & Play device found
[   31.664810] Real Time Clock Driver v1.12ac
[   31.664999] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.665169] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.666647] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.668281] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.668439] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   31.668687] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   31.671376] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.671389] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.679634] mice: PS/2 mouse device common for all mice
[   31.679907] EISA: Probing bus 0 at eisa.0
[   31.679922] EISA: Cannot allocate resource for mainboard
[   31.679965] EISA: Detected 0 cards.
[   31.679972] cpuidle: using governor ladder
[   31.679976] cpuidle: using governor menu
[   31.680336] NET: Registered protocol family 1
[   31.680412] Using IPI No-Shortcut mode
[   31.680494] registered taskstats version 1
[   31.680714]   Magic number: 1:674:537
[   31.680954] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   31.682432] Freeing unused kernel memory: 384k freed
[   31.682590] Write protecting the kernel read-only data: 828k
[   31.719156] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   32.085277] fuse init (API version 7.9)
[   33.038324] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   33.038334] e100: Copyright(c) 1999-2006 Intel Corporation
[   33.038473] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 20 (level, low) -> IRQ 16
[   33.061431] e100: eth0: e100_probe: addr 0xfe103000, irq 16, MAC addr 00:c0:9f:12:38:bb
[   33.509801] SCSI subsystem initialized
[   33.571527] usbcore: registered new interface driver usbfs
[   33.571584] usbcore: registered new interface driver hub
[   33.576742] usbcore: registered new device driver usb
[   33.666546] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   33.667106] ACPI: PCI Interrupt Link [LUSB] enabled at IRQ 11
[   33.667126] ACPI: PCI Interrupt 0000:00:0f.2[A] -> Link [LUSB] -> GSI 11 (level, low) -> IRQ 11
[   33.667157] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[   33.667839] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
[   33.667880] ohci_hcd 0000:00:0f.2: irq 11, io mem 0xfe100000
[   33.683192] libata version 3.00 loaded.
[   33.697936] Floppy drive(s): fd0 is 1.44M
[   33.719624] FDC 0 is a National Semiconductor PC87306
[   33.730080] usb usb1: configuration #1 chosen from 1 choice
[   33.730146] hub 1-0:1.0: USB hub found
[   33.730163] hub 1-0:1.0: 2 ports detected
[   33.855967] scsi0 : pata_serverworks
[   33.857413] scsi1 : pata_serverworks
[   33.857538] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8b0 irq 14
[   33.857544] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8b8 irq 15
[   34.057916] ata1.00: HPA unlocked: 78125000 -> 78125040, native 78125040
[   34.057933] ata1.00: ATA-5: WDC WD400BB-18DEA0, 05.03E05, max UDMA/100
[   34.057939] ata1.00: 78125040 sectors, multi 8: LBA 
[   34.098748] ata1.00: configured for UDMA/100
[   34.437561] ata2.00: ATAPI: SAMSUNG CD-ROM  SC-148C, C002, max UDMA/33
[   34.597715] ata2.00: configured for UDMA/33
[   34.598022] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-18DE 05.0 PQ: 0 ANSI: 5
[   34.598430] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   C002 PQ: 0 ANSI: 5
[   35.134079] Driver 'sd' needs updating - please use bus_type methods
[   35.134283] sd 0:0:0:0: [sda] 78125040 512-byte hardware sectors (40000 MB)
[   35.134312] sd 0:0:0:0: [sda] Write Protect is off
[   35.134318] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.134356] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.134467] sd 0:0:0:0: [sda] 78125040 512-byte hardware sectors (40000 MB)
[   35.134488] sd 0:0:0:0: [sda] Write Protect is off
[   35.134493] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.134529] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.134537]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   35.169260]  sda1 sda2 < sda5 >
[   35.192243] sd 0:0:0:0: [sda] Attached SCSI disk
[   35.206023] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   35.206037] Uniform CD-ROM driver Revision: 3.20
[   35.206164] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   35.207154] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   35.207197] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   35.655966] Attempting manual resume
[   35.655977] swsusp: Resume From Partition 8:5
[   35.655980] PM: Checking swsusp image.
[   35.656260] PM: Resume from disk failed.
[   35.729820] kjournald starting.  Commit interval 5 seconds
[   35.729860] EXT3-fs: mounted filesystem with ordered data mode.
[   40.426733] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   41.473506] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   41.591707] gameport: EMU10K1 is pci0000:00:09.1/gameport0, io 0xec98, speed 1242kHz
[   41.623812] Linux agpgart interface v0.102
[   41.742490] parport_pc 00:08: reported by Plug and Play ACPI
[   41.742573] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   42.012235] agpgart: unable to determine aperture size.
[   42.012289] agpgart: agp_backend_initialize() failed.
[   42.012304] agpgart-serverworks: probe of 0000:00:00.0 failed with error -22
[   42.012323] agpgart: unable to determine aperture size.
[   42.012363] agpgart: agp_backend_initialize() failed.
[   42.012370] agpgart-serverworks: probe of 0000:00:00.1 failed with error -22
[   42.361978] scb2_flash: warning - can't reserve rom window, continuing
[   42.422441] ISDN subsystem Rev: 1.1.2.3/1.1.2.3/1.1.2.2/1.1.2.3/1.1.2.2/1.1.2.2 loaded
[   42.729029] CFI: Found no SCB2 BIOS Flash device at location zero
[   42.729040] scb2_flash: flash probe failed!
[   42.851813] input: Power Button (FF) as /devices/virtual/input/input3
[   42.921530] ACPI: Power Button (FF) [PWRF]
[   43.101385] HiSax: Linux Driver for passive ISDN cards
[   43.101395] HiSax: Version 3.5 (module)
[   43.101401] HiSax: Layer1 Revision 2.46.2.5
[   43.101404] HiSax: Layer2 Revision 2.30.2.4
[   43.101408] HiSax: TeiMgr Revision 2.20.2.3
[   43.101411] HiSax: Layer3 Revision 2.22.2.3
[   43.101415] HiSax: LinkLayer Revision 2.59.2.4
[   43.481222] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[   43.553570] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 28 (level, low) -> IRQ 17
[   47.976605] loop: module loaded
[   48.010384] lp0: using parport0 (interrupt-driven).
[   48.311885] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   48.815410] EXT3 FS on sda1, internal journal
[   50.132485] ip_tables: (C) 2000-2006 Netfilter Core Team
[   52.954722] dahdi: Telephony Interface Registered on major 196
[   52.954735] dahdi: Version: 2.1.0.4
[   53.268311] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 23 (level, low) -> IRQ 18
[   53.268481] Freshmaker version: 73
[   53.268730] Freshmaker passed register test
[   54.643906] Module 0: Installed -- AUTO FXS/DPO
[   54.643976] Module 1: Not installed
[   54.644044] Module 2: Not installed
[   54.843458] Module 3: Installed -- AUTO FXO (FCC mode)
[   54.862774] Found a Wildcard TDM: Wildcard TDM400P REV I (2 modules)
[   54.999014] dahdi_transcode: Loaded.
[   55.134052] INFO-xpp: revision trunk-r6056 MAX_XPDS=64 (8*8)
[   55.134066] INFO-xpp: FEATURE: without BRISTUFF support
[   55.134081] INFO-xpp: FEATURE: with PROTOCOL_DEBUG
[   55.134235] INFO-xpp: FEATURE: with sync_tick() from DAHDI
[   55.160696] INFO-xpp_usb: revision trunk-r6056
[   55.160946] usbcore: registered new interface driver xpp_usb
[   55.250504] dahdi_echocan_mg2: Registered echo canceler 'MG2'
[   55.268653] dahdi: Registered tone zone 0 (United States / North America)
[   55.900559] NET: Registered protocol family 10
[   55.901096] lo: Disabled Privacy Extensions
[ 1495.538871] usb 1-1: new full speed USB device using ohci_hcd and address 2
[ 1495.768834] usb 1-1: configuration #1 chosen from 1 choice
[ 1495.896486] usbcore: registered new interface driver libusual
[ 1495.920257] Initializing USB Mass Storage driver...
[ 1495.925484] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1495.929071] usbcore: registered new interface driver usb-storage
[ 1495.929091] USB Mass Storage support registered.
[ 1495.930091] usb-storage: device found at 2
[ 1495.930102] usb-storage: waiting for device to settle before scanning
[ 1500.927122] usb-storage: device scan complete
[ 1500.963090] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.2  PQ: 0 ANSI: 2
[ 1500.974067] sd 2:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[ 1500.987041] sd 2:0:0:0: [sdb] Write Protect is off
[ 1500.987058] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1500.987064] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1501.013000] sd 2:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[ 1501.026023] sd 2:0:0:0: [sdb] Write Protect is off
[ 1501.026041] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1501.026046] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1501.026114]  sdb: sdb1
[ 1501.038216] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1501.038308] sd 2:0:0:0: Attached scsi generic sg2 type 0
root@asteriscos:/# sudo lshw -C network


DMI

   
SMP

   
PA-RISC

       
device-tree

           
SPD

   
memory

      
/proc/cpuinfo

             
CPUID

     
PCI (sysfs)

           
ISA PnP

       
PCMCIA

      
PCMCIA

      
kernel device tree (sysfs)

                          
USB

   
IDE

   
SCSI

    
Network interfaces

                  
Framebuffer devices

                   
Display

       
CPUFreq

       

  *-network:0 DISABLED
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: eth0
       version: 08
       serial: 00:c0:9f:12:38:bb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
root@asteriscos:/# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

root@asteriscos:/# iwlist c[Kscan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
root@asteriscos:/# lsb [K_release -d
Description:	Ubuntu 8.04.2
root@asteriscos:/# uname -mr
2.6.24-23-server i686
root@asteriscos:/# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...       [80G wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.

[74G[ OK ]
root@asteriscos:/# lspci -n
00:00.0 0600: 1166:0009 (rev 06)
00:00.1 0600: 1166:0009 (rev 06)
00:02.0 0200: 8086:1229 (rev 08)
00:06.0 0780: e159:0001
00:09.0 0401: 1102:0002 (rev 0a)
00:09.1 0980: 1102:7002 (rev 0a)
00:0a.0 0200: 10ec:8185 (rev 20)
00:0b.0 0300: 1002:4752 (rev 27)
00:0f.0 0601: 1166:0201 (rev 92)
00:0f.1 0101: 1166:0212 (rev 92)
00:0f.2 0c03: 1166:0220 (rev 05)
00:0f.3 0600: 1166:0230
root@asteriscos:/# dep[Kpmod -a
root@asteriscos:/# modprobe ndiswrapper
root@asteriscos:/# tail /var/log/messages
Jul  8 11:55:53 asteriscos kernel: [ 1501.026114]  sdb: sdb1
Jul  8 11:55:53 asteriscos kernel: [ 1501.038216] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Jul  8 11:55:53 asteriscos kernel: [ 1501.038308] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jul  8 12:10:53 asteriscos kernel: [ 2400.828216] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Jul  8 12:10:53 asteriscos kernel: [ 2400.908862] ndiswrapper: driver net8185 (Realtek,11/20/2007,5.1102.1120.2007) loaded
Jul  8 12:10:53 asteriscos kernel: [ 2400.910151] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 30 (level, low) -> IRQ 19
Jul  8 12:10:54 asteriscos kernel: [ 2401.181494] ndiswrapper: using IRQ 19
Jul  8 12:11:00 asteriscos kernel: [ 2407.546996] wlan0: ethernet device 00:14:d1:5f:f2:4b using NDIS driver: net8185, version: 0x50449, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
Jul  8 12:11:00 asteriscos kernel: [ 2407.547144] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jul  8 12:11:00 asteriscos kernel: [ 2407.575367] usbcore: registered new interface driver ndiswrapper
root@asteriscos:/# iwcoinfig[K[K[K[K[Kf[Knfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NOT_FREE_GOODBYE"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:73:C8:D2   
          Bit Rate=54 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:55E4-052C-47   Security mode:restricted
          Power Management:off
          Link Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx

Read many forum chats and run the following:

lspci
depmod -a
modprobe ndiswrapper
iwconfig wlan0 key off
iwconfig wlan0 mode Auto
dhclient 

Receive the error about dhcpdiscover.

Please send clear, and to the point instructions to assist me with getting this to work.  Last bit of info is it is an IP Asterisk PBX.

Jeer

---

