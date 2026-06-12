---
title: "Wireless Transmitting but very slow"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by ktechman on 2009-04-28
Here are the particulars I have a Compaq Presario 2100amd notebook with a Cisco PCM352 using the airo_cs driver I have a strong signal but very slow download speeds anywhere from 5-17 kbps the wired connection runs at normal speed 197-275 kbps. It is an open system (live in the boonies) running DHCP on Ubuntu 9.04 32bit patched

I found this in dmesg
```

[   17.744775] airo(eth1): MAC enabled 00:0c:ce:c0:79:aa

```

lspci 
```
 lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
00:09.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

```

lspci -v | less
```
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
        Subsystem: Hewlett-Packard Company Device 0024
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at 80000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 44000000-47fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001
        Kernel driver in use: yenta_cardbus
        Kernel modules: yenta_socket

```


ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:79:ee:d4  
          inet addr:192.168.254.30  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe79:eed4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19972248 (19.9 MB)  TX bytes:760054 (760.0 KB)
          Interrupt:11 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:0c:ce:c0:79:aa  
          inet addr:192.168.254.29  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:ceff:fec0:79aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:748 errors:6 dropped:0 overruns:0 frame:6
          TX packets:19 errors:6 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:82599 (82.5 KB)  TX bytes:3749 (3.7 KB)
          Interrupt:3 Base address:0x100 

eth2      Link encap:Ethernet  HWaddr 00:04:76:3f:ad:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


iwconfig
```

lo        no wireless extensions.

eth2      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"green"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:04:24:68:86   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-34 dBm  Noise level=-75 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11949   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"green"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:04:24:68:86   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-34 dBm  Noise level=-75 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11949   Missed beacon:0

pan0      no wireless extensions.

```


/etc/network/interfaces
```

auto lo
iface lo inet loopback

```

lsmod
```

Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
airo_cs                12288  1 
airo                   76960  1 airo_cs
snd_ali5451            27276  3 
snd_ac97_codec        112292  1 snd_ali5451
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 44748  1 airo_cs
ppdev                  15620  0 
snd                    62628  16 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
ati_agp                14988  1 
yenta_socket           32396  3 
rsrc_nonstatic         19328  1 yenta_socket
soundcore              15200  1 snd
pcspkr                 10496  0 
serio_raw              13316  0 
i2c_ali15x3            14724  0 
i2c_ali1535            14212  0 
agpgart                42696  2 drm,ati_agp
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         16904  1 snd_pcm
shpchp                 40212  0 
joydev                 18368  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
video                  25360  0 
output                 11008  1 video
usbhid                 42336  0 
natsemi                35552  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
3c59x                  49192  0 
mii                    13312  1 3c59x
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

dmesg
```

[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 4581760 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 888220k/916416k available (4126k kernel code, 27584k reserved, 2208k data, 532k init, 11208k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004019] Calibrating delay loop (skipped), value calculated using timer frequency.. 3577.84 BogoMIPS (lpj=7155680)
[    0.004051] Security Framework initialized
[    0.004065] SELinux:  Disabled at boot.
[    0.004112] AppArmor: AppArmor initialized
[    0.004126] Mount-cache hash table entries: 512
[    0.004368] Initializing cgroup subsys ns
[    0.004374] Initializing cgroup subsys cpuacct
[    0.004377] Initializing cgroup subsys memory
[    0.004384] Initializing cgroup subsys freezer
[    0.004406] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004410] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004438] Checking 'hlt' instruction... OK.
[    0.020666] SMP alternatives: switching to UP code
[    0.193008] Freeing SMP alternatives: 18k freed
[    0.193016] ACPI: Core revision 20080926
[    0.199543] ACPI: Checking initramfs for custom DSDT
[    0.532647] ACPI: setting ELCR to 0200 (from 0e28)
[    0.534679] weird, boot CPU (#0) not listedby the BIOS.
[    0.534683] SMP motherboard not detected.
[    0.534687] Local APIC not detected. Using dummy APIC emulation.
[    0.534690] SMP disabled
[    0.535214] Brought up 1 CPUs
[    0.535218] Total of 1 processors activated (3577.84 BogoMIPS).
[    0.535242] CPU0 attaching NULL sched-domain.
[    0.535789] net_namespace: 776 bytes
[    0.535810] Booting paravirtualized kernel on bare hardware
[    0.536168] Time:  8:47:03  Date: 04/28/09
[    0.536178] regulator: core version 0.5
[    0.536252] NET: Registered protocol family 16
[    0.536481] EISA bus registered
[    0.536506] ACPI: bus type pci registered
[    0.536849] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
[    0.536853] PCI: Using configuration type 1 for base access
[    0.538902] ACPI: EC: Look up EC in DSDT
[    0.550668] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.550740] ACPI: Interpreter enabled
[    0.550740] ACPI: (supports S0 S3 S4 S5)
[    0.550740] ACPI: Using PIC for interrupt routing
[    0.560535] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.560539] ACPI: EC: driver started in interrupt mode
[    0.560675] ACPI: No dock devices found.
[    0.560687] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.560747] pci 0000:00:00.0: reg 10 32bit mmio: [0xd4000000-0xd7ffffff]
[    0.560754] pci 0000:00:00.0: reg 14 32bit mmio: [0xd0500000-0xd0500fff]
[    0.560760] pci 0000:00:00.0: reg 18 io port: [0x8090-0x8093]
[    0.560823] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0004000-0xd0004fff]
[    0.560850] pci 0000:00:02.0: PME# supported from D3cold
[    0.560856] pci 0000:00:02.0: PME# disabled
[    0.560882] pci 0000:00:06.0: reg 10 io port: [0x8400-0x84ff]
[    0.560888] pci 0000:00:06.0: reg 14 32bit mmio: [0xd0005000-0xd0005fff]
[    0.560911] pci 0000:00:06.0: supports D1 D2
[    0.560913] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.560917] pci 0000:00:06.0: PME# disabled
[    0.560989] pci 0000:00:08.0: reg 10 32bit mmio: [0xd0006000-0xd0006fff]
[    0.560995] pci 0000:00:08.0: reg 14 io port: [0x8800-0x88ff]
[    0.561017] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.561021] pci 0000:00:08.0: PME# disabled
[    0.561045] pci 0000:00:09.0: reg 10 io port: [0x8c00-0x8cff]
[    0.561051] pci 0000:00:09.0: reg 14 32bit mmio: [0xd0007400-0xd000747f]
[    0.561057] pci 0000:00:09.0: reg 18 32bit mmio: [0xd0007000-0xd000707f]
[    0.561072] pci 0000:00:09.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.561079] pci 0000:00:09.0: supports D1 D2
[    0.561082] pci 0000:00:09.0: PME# supported from D1 D2 D3hot D3cold
[    0.561085] pci 0000:00:09.0: PME# disabled
[    0.561109] pci 0000:00:09.1: reg 10 io port: [0x9000-0x90ff]
[    0.561115] pci 0000:00:09.1: reg 14 32bit mmio: [0xd0007c00-0xd0007cff]
[    0.561121] pci 0000:00:09.1: reg 18 32bit mmio: [0xd0007800-0xd000787f]
[    0.561140] pci 0000:00:09.1: supports D2
[    0.561143] pci 0000:00:09.1: PME# supported from D2 D3hot D3cold
[    0.561146] pci 0000:00:09.1: PME# disabled
[    0.561177] pci 0000:00:0a.0: reg 10 32bit mmio: [0x80000000-0x80000fff]
[    0.561185] pci 0000:00:0a.0: supports D1 D2
[    0.561187] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.561191] pci 0000:00:0a.0: PME# disabled
[    0.561217] pci 0000:00:0c.0: reg 10 32bit mmio: [0xd0008000-0xd00087ff]
[    0.561223] pci 0000:00:0c.0: reg 14 32bit mmio: [0xd0000000-0xd0003fff]
[    0.561248] pci 0000:00:0c.0: supports D1 D2
[    0.561250] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot
[    0.561254] pci 0000:00:0c.0: PME# disabled
[    0.561294] pci 0000:00:10.0: reg 20 io port: [0x8080-0x808f]
[    0.561351] pci 0000:00:11.0: quirk: region 8000-803f claimed by ali7101 ACPI
[    0.561355] pci 0000:00:11.0: quirk: region 8040-805f claimed by ali7101 SMB
[    0.561379] pci 0000:00:12.0: reg 10 io port: [0x9400-0x94ff]
[    0.561385] pci 0000:00:12.0: reg 14 32bit mmio: [0xd0009000-0xd0009fff]
[    0.561404] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.561411] pci 0000:00:12.0: supports D1 D2
[    0.561414] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.561418] pci 0000:00:12.0: PME# disabled
[    0.561466] pci 0000:01:05.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[    0.561471] pci 0000:01:05.0: reg 14 io port: [0xa000-0xa0ff]
[    0.561477] pci 0000:01:05.0: reg 18 32bit mmio: [0xd0100000-0xd010ffff]
[    0.561491] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.561500] pci 0000:01:05.0: supports D1 D2
[    0.561529] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.561533] pci 0000:00:01.0: bridge 32bit mmio: [0xd0100000-0xd01fffff]
[    0.561538] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.561559] bus 00 -> node 0
[    0.561568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.561680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.564754] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[    0.564970] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[    0.565180] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) *9
[    0.565390] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 *10)
[    0.565600] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[    0.565810] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 *11)
[    0.566031] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[    0.566240] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[    0.566448] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[    0.566644] ACPI: WMI: Mapper loaded
[    0.567006] SCSI subsystem initialized
[    0.567089] libata version 3.00 loaded.
[    0.567173] usbcore: registered new interface driver usbfs
[    0.567199] usbcore: registered new interface driver hub
[    0.567244] usbcore: registered new device driver usb
[    0.567428] PCI: Using ACPI for IRQ routing
[    0.567553] Bluetooth: Core ver 2.13
[    0.567553] NET: Registered protocol family 31
[    0.567553] Bluetooth: HCI device and connection manager initialized
[    0.567553] Bluetooth: HCI socket layer initialized
[    0.567553] NET: Registered protocol family 8
[    0.567553] NET: Registered protocol family 20
[    0.567553] NetLabel: Initializing
[    0.567553] NetLabel:  domain hash size = 128
[    0.567553] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.567553] NetLabel:  unlabeled traffic allowed by default
[    0.567553] AppArmor: AppArmor Filesystem Enabled
[    0.567553] pnp: PnP ACPI init
[    0.567553] ACPI: bus type pnp registered
[    0.569327] pnp 00:07: mem resource (0xe0500000-0xe0500fff) overlaps 0000:00:01.0 BAR 9 (0xe0000000-0xefffffff), disabling
[    0.569357] pnp 00:07: io resource (0x8004-0x8005) overlaps 0000:00:11.0 BAR 7 (0x8000-0x803f), disabling
[    0.569365] pnp 00:07: mem resource (0xe0500000-0xe0500fff) overlaps 0000:01:05.0 BAR 0 (0xe0000000-0xefffffff), disabling
[    0.572361] pnp: PnP ACPI: found 11 devices
[    0.572364] ACPI: ACPI bus type pnp unregistered
[    0.572369] PnPBIOS: Disabled by ACPI PNP
[    0.572390] system 00:07: ioport range 0x40b-0x40b has been reserved
[    0.572394] system 00:07: ioport range 0x480-0x48f has been reserved
[    0.572397] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.572400] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[    0.572403] system 00:07: ioport range 0x8000-0x807f could not be reserved
[    0.572407] system 00:07: ioport range 0xff00-0xff01 has been reserved
[    0.572410] system 00:07: ioport range 0xfe00-0xfefe has been reserved
[    0.572415] system 00:07: iomem range 0xd0500000-0xd0500fff has been reserved
[    0.607183] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.607187] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.607193] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
[    0.607197] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.607204] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    0.607207] pci 0000:00:0a.0:   IO window: 0x001000-0x0010ff
[    0.607212] pci 0000:00:0a.0:   IO window: 0x001400-0x0014ff
[    0.607216] pci 0000:00:0a.0:   PREFETCH window: 0x40000000-0x43ffffff
[    0.607220] pci 0000:00:0a.0:   MEM window: 0x44000000-0x47ffffff
[    0.607535] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    0.607539] PCI: setting IRQ 11 as level-triggered
[    0.607545] pci 0000:00:0a.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    0.607552] bus: 00 index 0 io port: [0x00-0xffff]
[    0.607555] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.607557] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.607560] bus: 01 index 1 mmio: [0xd0100000-0xd01fffff]
[    0.607562] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.607565] bus: 01 index 3 mmio: [0x0-0x0]
[    0.607567] bus: 02 index 0 io port: [0x1000-0x10ff]
[    0.607569] bus: 02 index 1 io port: [0x1400-0x14ff]
[    0.607572] bus: 02 index 2 mmio: [0x40000000-0x43ffffff]
[    0.607574] bus: 02 index 3 mmio: [0x44000000-0x47ffffff]
[    0.607598] NET: Registered protocol family 2
[    0.607784] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.608383] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.611086] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.612520] TCP: Hash tables configured (established 131072 bind 65536)
[    0.612525] TCP reno registered
[    0.612715] NET: Registered protocol family 1
[    0.612936] checking if image is initramfs... it is
[    1.108095] Switched to high resolution mode on CPU 0
[    1.349142] Freeing initrd memory: 7367k freed
[    1.349215] Simple Boot Flag at 0x36 set to 0x1
[    1.349314] cpufreq: No nForce2 chipset.
[    1.349536] audit: initializing netlink socket (disabled)
[    1.349571] type=2000 audit(1240908424.348:1): initialized
[    1.358539] highmem bounce pool size: 64 pages
[    1.358550] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.360219] VFS: Disk quotas dquot_6.5.1
[    1.360304] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.361087] fuse init (API version 7.10)
[    1.361182] msgmni has been set to 1727
[    1.361498] alg: No test for stdrng (krng)
[    1.361519] io scheduler noop registered
[    1.361522] io scheduler anticipatory registered
[    1.361524] io scheduler deadline registered
[    1.361545] io scheduler cfq registered (default)
[    1.361568] pci 0000:00:00.0: ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb
[    1.576066] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    1.576102] pci 0000:01:05.0: Boot video device
[    1.579988] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.580035] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.580404] ACPI: AC Adapter [ACAD] (on-line)
[    1.580612] ACPI: Battery Slot [BAT1] (battery absent)
[    1.580713] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.580718] ACPI: Power Button (FF) [PWRF]
[    1.580779] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.580782] ACPI: Power Button (CM) [PWRB]
[    1.580834] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.584748] ACPI: Lid Switch [LID]
[    1.584931] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.584968] processor ACPI_CPU:00: registered as cooling_device0
[    1.588270] thermal LNXTHERM:01: registered as thermal_zone0
[    1.589963] ACPI: Thermal Zone [THRM] (36 C)
[    1.590016] isapnp: Scanning for PnP cards...
[    1.856913] isapnp: No Plug & Play device found
[    1.858531] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.858658] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.859069] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.859509] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[    1.859514] PCI: setting IRQ 3 as level-triggered
[    1.859520] serial 0000:00:08.0: PCI INT A -> Link[LNKG] -> GSI 3 (level, low) -> IRQ 3
[    1.859528] serial 0000:00:08.0: PCI INT A disabled
[    1.860546] brd: module loaded
[    1.861004] loop: module loaded
[    1.861163] Fixed MDIO Bus: probed
[    1.861174] PPP generic driver version 2.4.2
[    1.861266] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.861326] Driver 'sd' needs updating - please use bus_type methods
[    1.861338] Driver 'sr' needs updating - please use bus_type methods
[    1.861638] pata_ali 0000:00:10.0: can't derive routing for PCI INT A
[    1.862061] scsi0 : pata_ali
[    1.862413] scsi1 : pata_ali
[    1.862791] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8080 irq 14
[    1.862796] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8088 irq 15
[    2.024467] ata1.00: ATA-6: IC25N030ATMR04-0, MOAOAD0A, max UDMA/100
[    2.024471] ata1.00: 58605120 sectors, multi 16: LBA48 
[    2.040395] ata1.00: configured for UDMA/100
[    2.204260] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0C27, max MWDMA2
[    2.204286] ata2.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    2.204289] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    2.220221] ata2.00: configured for MWDMA2
[    2.221140] scsi 0:0:0:0: Direct-Access     ATA      IC25N030ATMR04-0 MOAO PQ: 0 ANSI: 5
[    2.221298] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors: (30.0 GB/27.9 GiB)
[    2.221326] sd 0:0:0:0: [sda] Write Protect is off
[    2.221330] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.221367] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.221485] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors: (30.0 GB/27.9 GiB)
[    2.221505] sd 0:0:0:0: [sda] Write Protect is off
[    2.221508] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.221542] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.221548]  sda: sda1 sda2 sda3 < sda5 >
[    2.272702] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.272784] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.277855] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0C27 PQ: 0 ANSI: 5
[    2.290810] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.290815] Uniform CD-ROM driver Revision: 3.20
[    2.290976] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.291031] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.291600] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.291624] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.292089] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[    2.292094] PCI: setting IRQ 10 as level-triggered
[    2.292100] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LNKU] -> GSI 10 (level, low) -> IRQ 10
[    2.292149] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.292265] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.292301] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0004000
[    2.350139] usb usb1: configuration #1 chosen from 1 choice
[    2.350181] hub 1-0:1.0: USB hub found
[    2.350203] hub 1-0:1.0: 4 ports detected
[    2.350362] uhci_hcd: USB Universal Host Controller Interface driver
[    2.350491] usbcore: registered new interface driver libusual
[    2.350540] usbcore: registered new interface driver usbserial
[    2.350555] USB Serial support registered for generic
[    2.350569] usbcore: registered new interface driver usbserial_generic
[    2.350572] usbserial: USB Serial Driver core
[    2.350633] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.355763] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.355774] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.355933] mice: PS/2 mouse device common for all mice
[    2.356226] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.356256] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    2.356336] device-mapper: uevent: version 1.0.3
[    2.356527] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.356613] device-mapper: multipath: version 1.0.5 loaded
[    2.356617] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.356744] EISA: Probing bus 0 at eisa.0
[    2.356757] Cannot allocate resource for EISA slot 1
[    2.356785] Cannot allocate resource for EISA slot 8
[    2.356788] EISA: Detected 0 cards.
[    2.356869] cpuidle: using governor ladder
[    2.356924] cpuidle: using governor menu
[    2.357577] TCP cubic registered
[    2.357707] NET: Registered protocol family 10
[    2.358238] lo: Disabled Privacy Extensions
[    2.358639] NET: Registered protocol family 17
[    2.358667] Bluetooth: L2CAP ver 2.11
[    2.358669] Bluetooth: L2CAP socket layer initialized
[    2.358673] Bluetooth: SCO (Voice Link) ver 0.6
[    2.358676] Bluetooth: SCO socket layer initialized
[    2.358736] Bluetooth: RFCOMM socket layer initialized
[    2.358751] Bluetooth: RFCOMM TTY layer initialized
[    2.358754] Bluetooth: RFCOMM ver 1.10
[    2.358783] powernow-k8: Processor cpuid 681 not supported
[    2.358877] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[    2.364696] powernow: SGTC: 13333
[    2.364699] powernow: Minimum speed 530 MHz. Maximum speed 1788 MHz.
[    2.364775] IO APIC resources could be not be allocated.
[    2.364825] Using IPI No-Shortcut mode
[    2.364999] registered taskstats version 1
[    2.365161]   Magic number: 5:175:777
[    2.365351] rtc_cmos 00:02: setting system clock to 2009-04-28 08:47:07 UTC (1240908427)
[    2.365356] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.365358] EDD information not available.
[    2.366528] Freeing unused kernel memory: 532k freed
[    2.366690] Write protecting the kernel text: 4128k
[    2.366737] Write protecting the kernel read-only data: 1532k
[    2.405762] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.716085] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    2.935129] usb 1-1: configuration #1 chosen from 1 choice
[    3.040808] Floppy drive(s): fd0 is 1.44M
[    3.059454] FDC 0 is a post-1991 82077
[    3.344275] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    3.344287] 3c59x 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.344348] 3c59x: Donald Becker and others.
[    3.344362] 0000:00:09.0: 3Com PCI 3c556 Laptop Tornado at f7d6e400.
[    3.422978] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    3.422990] ohci1394 0000:00:0c.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    3.472899] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0008000-d00087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.572896] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[    3.572900]   originally by Donald Becker <becker@scyld.com>
[    3.572902]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[    3.573398] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    3.573406] natsemi 0000:00:12.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    3.576213] natsemi eth1: NatSemi DP8381[56] at 0xd0009000 (0000:00:12.0), 00:0b:cd:79:ee:d4, IRQ 11, port TP.
[    4.526232] usbcore: registered new interface driver hiddev
[    4.533366] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input5
[    4.568300] generic-usb 0003:046D:C521.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-1/input0
[    4.575702] Marking TSC unstable due to TSC halts in idle
[    4.580913] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.1/input/input6
[    4.581446] generic-usb 0003:046D:C521.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.0-1/input1
[    4.581484] usbcore: registered new interface driver usbhid
[    4.581490] usbhid: v2.6:USB HID core driver
[    4.716239] PM: Starting manual resume from disk
[    4.716247] PM: Resume from partition 8:5
[    4.716249] PM: Checking hibernation image.
[    4.716522] PM: Resume from disk failed.
[    4.762425] kjournald starting.  Commit interval 5 seconds
[    4.762452] EXT3-fs: mounted filesystem with ordered data mode.
[    4.808302] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000bcd009e348159]
[   14.078906] udev: starting version 141
[   14.338891] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input7
[   14.368395] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.406548] udev: renamed network interface eth0 to eth2
[   14.481831] udev: renamed network interface eth1 to eth0
[   14.495731] parport_pc 00:09: reported by Plug and Play ACPI
[   14.495814] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   14.803179] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.887497] Linux agpgart interface v0.103
[   14.941675] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   15.043844] yenta_cardbus 0000:00:0a.0: CardBus bridge found [103c:0024]
[   15.043870] yenta_cardbus 0000:00:0a.0: O2: res at 0x94/0xD4: 00/ea
[   15.043873] yenta_cardbus 0000:00:0a.0: O2: enabling read prefetch/write burst
[   15.177379] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0038, PCI irq 11
[   15.177387] yenta_cardbus 0000:00:0a.0: Socket status: 30000411
[   15.180650] agpgart-ati 0000:00:00.0: Ati IGP320/M chipset
[   15.189774] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[   15.397786] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   15.529759] ppdev: user-space parallel port driver
[   16.140072] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   16.179752] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   16.179760] PCI: setting IRQ 5 as level-triggered
[   16.179767] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNKH] -> GSI 5 (level, low) -> IRQ 5
[   16.232963] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   16.235152] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   16.236054] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   16.236863] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   16.237878] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.238802] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   16.261299] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   16.339551] airo(): Probing for PCI adapters
[   16.339694] airo(): Finished probing for PCI adapters
[   16.411385] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x2348b3, caps: 0x904713/0x10008
[   16.449335] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   17.648383] airo(): cmd:111 status:7f11 rsp0:2 rsp1:0 rsp2:0
[   17.648395] airo(): Doing fast bap_reads
[   17.736663] padlock: VIA PadLock not detected.
[   17.740858] airo(): WPA unsupported (only firmware versions 5.30.17 and greater support WPA.  Detected 5.02.19)
[   17.744775] airo(eth1): MAC enabled 00:0c:ce:c0:79:aa
[   17.745863] eth1: index 0x05: , Vpp 5.0, irq 3, io 0x0100-0x013f
[   19.048038] AC'97 1 does not respond - RESET
[   19.064039] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   19.064048] ali mixer 1 creating error.
[   19.274128] lp0: using parport0 (interrupt-driven).
[   19.437340] Adding 1196800k swap on /dev/sda5.  Priority:-1 extents:1 across:1196800k
[   20.017271] EXT3 FS on sda2, internal journal
[   21.582686] type=1505 audit(1240922846.714:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1985
[   21.667989] type=1505 audit(1240922846.798:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1989
[   21.668480] type=1505 audit(1240922846.802:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1989
[   21.668606] type=1505 audit(1240922846.802:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1989
[   21.668711] type=1505 audit(1240922846.802:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1989
[   21.910877] type=1505 audit(1240922847.042:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1994
[   21.911426] type=1505 audit(1240922847.042:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1994
[   21.966289] type=1505 audit(1240922847.098:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1998
[   25.726080] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.726087] Bluetooth: BNEP filters: protocol multicast
[   25.781333] Bridge firewalling registered
[   27.261381] pci 0000:01:05.0: power state changed by ACPI to D0
[   27.261404] pci 0000:01:05.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   27.528919] [drm] Initialized drm 1.1.0 20060810
[   27.701519] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   28.364128] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   28.364158] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   28.364206] pci 0000:01:05.0: putting AGP V2 device into 4x mode
[   28.563930] [drm] Setting GART location based on new memory map
[   28.563946] [drm] Loading R100 Microcode
[   28.563995] [drm] writeback test succeeded in 1 usecs
[   31.870457] eth0: DSPCFG accepted after 0 usec.
[   31.870468] eth0: link up.
[   31.870487] eth0: Setting full-duplex based on negotiated link capability.
[   31.890595] eth2:  setting half-duplex.
[   31.891145] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   32.317575] irq 3: nobody cared (try booting with the "irqpoll" option)
[   32.317589] Pid: 2589, comm: NetworkManager Not tainted 2.6.28-11-generic #42-Ubuntu
[   32.317592] Call Trace:
[   32.317615]  [<c0500ac6>] ? printk+0x18/0x1a
[   32.317626]  [<c017fd27>] __report_bad_irq+0x27/0x90
[   32.317630]  [<c017feee>] note_interrupt+0x15e/0x1a0
[   32.317634]  [<c017eab9>] ? handle_IRQ_event+0x39/0x70
[   32.317639]  [<c0180903>] handle_level_irq+0xc3/0xf0
[   32.317646]  [<c010684e>] do_IRQ+0x7e/0xa0
[   32.317650]  [<c0106853>] ? do_IRQ+0x83/0xa0
[   32.317653]  [<c01051f3>] common_interrupt+0x23/0x30
[   32.317664]  [<c013f16a>] ? __do_softirq+0x6a/0x170
[   32.317668]  [<c013f2cd>] do_softirq+0x5d/0x60
[   32.317672]  [<c013f445>] irq_exit+0x55/0x90
[   32.317676]  [<c0106853>] do_IRQ+0x83/0xa0
[   32.317679]  [<c01051f3>] common_interrupt+0x23/0x30
[   32.317686]  [<c0502d6d>] ? _spin_unlock_irqrestore+0x1d/0x40
[   32.317690]  [<c017f8bf>] __setup_irq+0xef/0x1f0
[   32.317693]  [<c017fa70>] request_irq+0xb0/0xf0
[   32.317721]  [<f7cc6ac0>] ? airo_interrupt+0x0/0x9c0 [airo]
[   32.317728]  [<f7cc434c>] airo_open+0xac/0x1a0 [airo]
[   32.317740]  [<c0434ed2>] dev_open+0xa2/0xe0
[   32.317743]  [<c0502f01>] ? _spin_unlock_bh+0x11/0x20
[   32.317747]  [<c043430a>] ? dev_set_rx_mode+0x2a/0x40
[   32.317751]  [<c0434581>] dev_change_flags+0x131/0x1c0
[   32.317759]  [<c043d3cd>] do_setlink+0x1ed/0x3a0
[   32.317764]  [<c044eca3>] ? nla_reserve+0x43/0x60
[   32.317768]  [<c043cccf>] ? rtnl_fill_ifinfo+0x2cf/0x3b0
[   32.317772]  [<c043d661>] rtnl_setlink+0xe1/0x120
[   32.317776]  [<c044de10>] ? netlink_dump_start+0x130/0x170
[   32.317779]  [<c043d580>] ? rtnl_setlink+0x0/0x120
[   32.317783]  [<c043c7b5>] rtnetlink_rcv_msg+0x165/0x200
[   32.317787]  [<c043cdb0>] ? rtnl_dump_ifinfo+0x0/0xa0
[   32.317790]  [<c043c650>] ? rtnetlink_rcv_msg+0x0/0x200
[   32.317793]  [<c044dcb6>] netlink_rcv_skb+0x76/0xa0
[   32.317797]  [<c043c63c>] rtnetlink_rcv+0x1c/0x30
[   32.317800]  [<c044d43d>] netlink_unicast+0x25d/0x290
[   32.317804]  [<c044e4bb>] netlink_sendmsg+0x1cb/0x2b0
[   32.317813]  [<c0426e0a>] sock_sendmsg+0xea/0x110
[   32.317822]  [<c02a8440>] ? apparmor_socket_recvmsg+0x10/0x20
[   32.317831]  [<c014ecb0>] ? autoremove_wake_function+0x0/0x50
[   32.317835]  [<c014ecb0>] ? autoremove_wake_function+0x0/0x50
[   32.317841]  [<c02cd465>] ? copy_from_user+0x35/0x130
[   32.317845]  [<c042e2a0>] ? verify_iovec+0x30/0xb0
[   32.317849]  [<c0426f41>] sys_sendmsg+0x111/0x230
[   32.317853]  [<c0427152>] ? sys_sendto+0xa2/0xd0
[   32.317857]  [<c0432d3d>] ? __dev_get_by_name+0x7d/0xa0
[   32.317860]  [<c02cd596>] ? copy_to_user+0x36/0x120
[   32.317864]  [<c0425010>] ? sock_destroy_inode+0x10/0x20
[   32.317870]  [<c01cfdea>] ? destroy_inode+0x2a/0x50
[   32.317873]  [<c01d079e>] ? generic_forget_inode+0x17e/0x1f0
[   32.317884]  [<c02ca49d>] ? rb_erase+0xcd/0x150
[   32.317888]  [<c0102ab7>] ? __switch_to+0xb7/0x1a0
[   32.317893]  [<c04276f5>] sys_socketcall+0xd5/0x2b0
[   32.317900]  [<c01bb5da>] ? sys_close+0x7a/0xc0
[   32.317903]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
[   32.317906] handlers:
[   32.317908] [<f7cc6ac0>] (airo_interrupt+0x0/0x9c0 [airo])
[   32.317916] Disabling IRQ #3
[   42.316072] eth0: no IPv6 routers present
[   42.804065] eth1: no IPv6 routers present
[   89.604071] Clocksource tsc unstable (delta = -85852549 ns)

```

sudo lshw -C network
```

*-network:0             
       description: Ethernet interface
       product: 3c556 Hurricane CardBus [Cyclone]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth2
       version: 10
       serial: 00:04:76:3f:ad:9b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=80 link=no maxlatency=5 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:79:ee:d4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.254.30 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:0c:ce:c0:79:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.254.29 multicast=yes wireless=IEEE 802.11-DS
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:36:87:92:23:24
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

iwlist scan
```
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:21:04:24:68:86
                    ESSID:"green"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=100/100  Signal level=-29 dBm  Noise level:-73 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=200

wifi0     Scan completed :
          Cell 01 - Address: 00:21:04:24:68:86
                    ESSID:"green"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=100/100  Signal level=-29 dBm  Noise level:-73 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=200

pan0      Interface doesn't support scanning.

```

I set the rate with this in /etc/network/if-up.d
```

#!/bin/sh

# set the wireless bit rate
iwconfig wlan0 rate 54M
sudo 0755 /etc/network/if-up.d/rate54M

```

I tried ndiswrapper to no avail "no hardware present" and the driver (bcmwl5)??? supposedly is in use in XP.  Thank you in advance for any help

---

### Post by ktechman on 2009-04-29
I have found that Windows at 29-30kbps does not handle this card any better than Ubuntu 10-14kbps if I could I would mark this thread as solved but...........

Ktechman

---

