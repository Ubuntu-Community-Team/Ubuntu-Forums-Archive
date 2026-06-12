---
title: "WLAN Wireless USB Adapter-Wireless Networks:Device Not Ready"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Ugeen on 2009-12-26
Connecting to my Linksys broadband router is not an option.  I'm thinking that it's a driver issue.  What do I do to get my wireless network to work?

It's visible via the Network Connections (System, Preferences, Network Connections, Wireless tab): linksys.

The following questions are from the thread: [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showpost.php?p=6183681&postcount=1").
[LIST=1]
[*]Machine Brand and Model (PC/Laptop): PC = 2 / Laptop = 1
[*]Wireless Brand, Model and Wireless Chipset:
[LIST=a]
[*]```
$ lspci

00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```
[*]```
$ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 006 Device 002: ID 0b38:0003  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
[/LIST]
(hint) use grep to get only information about the Wireless
```
$ lspci -nn | grep 'Wireless Brand'

$ 

```
[*]check interface:
[LIST=a]
[*]```
$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:1d:d8:54:45  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fed8:5445/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10862836 (10.8 MB)  TX bytes:1084345 (1.0 MB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```
[*]```
$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
[/LIST]
(hint) if the Wireless interface name is wlan0 you can also use
```
$ iwconfig wlan0

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

[*]Check for modules:
```
$ lsmod

Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26984  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75488  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_nat             5500  0 
nf_nat                 17808  1 iptable_nat
snd_timer              22276  2 snd_pcm,snd_seq
nf_conntrack_ipv4      13352  3 iptable_nat,nf_nat
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nf_conntrack           67608  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
r8192s_usb            222456  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
iptable_mangle          3452  0 
ieee80211_rsl         126448  1 r8192s_usb
snd_page_alloc          9252  2 snd_hda_intel,snd_pcm
i2c_piix4              10124  0 
nvidia               9587272  36 
ieee80211_crypt_ccmp     6012  1 ieee80211_rsl
iptable_filter          3100  0 
lp                      8964  0 
ppdev                   6688  0 
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
ieee80211_crypt_tkip     9276  1 ieee80211_rsl
parport_pc             32228  1 
ieee80211_crypt_wep     3932  1 ieee80211_rsl
parport                35340  3 lp,ppdev,parport_pc
ieee80211_crypt         5024  4 ieee80211_rsl,ieee80211_crypt_ccmp,ieee80211_crypt_tkip,ieee80211_crypt_wep
x_tables               16544  2 iptable_nat,ip_tables
serio_raw               5280  0 
joydev                 10272  0 
usbhid                 38304  0 
r8169                  32352  0 
mii                     5212  1 r8169
usb_storage            52608  0 
ohci1394               30220  0 
ieee1394               86628  1 ohci1394
ati_agp                 6760  0 
agpgart                35020  2 nvidia,ati_agp

```
(hint) search for the Wireless module
```
$ lsmod | grep "wlan_module_name"

$ 

```
[*]Kernel boot messages
```
$ dmesg

[    0.440425]   alloc irq_desc for 18 on node -1
[    0.440426]   alloc kstat_irqs on node -1
[    0.440432] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.440435] pci 0000:00:02.0: setting latency timer to 64
[    0.440439] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.440441] pci 0000:00:0a.0: setting latency timer to 64
[    0.440447] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.440449] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.440451] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.440453] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbffffff]
[    0.440454] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.440456] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.440458] pci_bus 0000:02: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.440459] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.440461] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.440463] pci_bus 0000:03: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.440464] pci_bus 0000:03: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.440466] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.440468] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.440488] NET: Registered protocol family 2
[    0.440543] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.440717] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.441062] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.441227] TCP: Hash tables configured (established 131072 bind 65536)
[    0.441229] TCP reno registered
[    0.441272] NET: Registered protocol family 1
[    0.441305] Trying to unpack rootfs image as initramfs...
[    0.500833] Switched to high resolution mode on CPU 1
[    0.500842] Switched to high resolution mode on CPU 2
[    0.500860] Switched to high resolution mode on CPU 3
[    0.504006] Switched to high resolution mode on CPU 0
[    0.567159] Freeing initrd memory: 7488k freed
[    0.569056] cpufreq-nforce2: No nForce2 chipset.
[    0.569071] Scanning for low memory corruption every 60 seconds
[    0.569127] audit: initializing netlink socket (disabled)
[    0.569135] type=2000 audit(1261858015.568:1): initialized
[    0.574682] highmem bounce pool size: 64 pages
[    0.574686] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.575483] VFS: Disk quotas dquot_6.5.2
[    0.575518] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.575821] fuse init (API version 7.12)
[    0.575865] msgmni has been set to 1534
[    0.576038] alg: No test for stdrng (krng)
[    0.576047] io scheduler noop registered
[    0.576049] io scheduler anticipatory registered
[    0.576050] io scheduler deadline registered
[    0.576076] io scheduler cfq registered (default)
[    1.468033] pci 0000:00:13.1: OHCI: BIOS handoff failed (BIOS bug?) 00000184
[    1.496052] pci 0000:01:00.0: Boot video device
[    1.496128]   alloc irq_desc for 25 on node -1
[    1.496130]   alloc kstat_irqs on node -1
[    1.496135] pcieport-driver 0000:00:02.0: irq 25 for MSI/MSI-X
[    1.496140] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.496195]   alloc irq_desc for 26 on node -1
[    1.496196]   alloc kstat_irqs on node -1
[    1.496199] pcieport-driver 0000:00:0a.0: irq 26 for MSI/MSI-X
[    1.496202] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.496241] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.496256] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.496329] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.496332] ACPI: Power Button [PWRF]
[    1.496360] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.496362] ACPI: Power Button [PWRB]
[    1.496554] processor LNXCPU:00: registered as cooling_device0
[    1.496587] processor LNXCPU:01: registered as cooling_device1
[    1.496616] processor LNXCPU:02: registered as cooling_device2
[    1.496646] processor LNXCPU:03: registered as cooling_device3
[    1.497838] isapnp: Scanning for PnP cards...
[    1.851428] isapnp: No Plug & Play device found
[    1.852077] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.852177] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.852399] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.852939] brd: module loaded
[    1.853164] loop: module loaded
[    1.853203] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.853239] ahci 0000:00:11.0: version 3.0
[    1.853249]   alloc irq_desc for 22 on node -1
[    1.853250]   alloc kstat_irqs on node -1
[    1.853257] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.853337] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.853340] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.853543] scsi0 : ahci
[    1.853598] scsi1 : ahci
[    1.853628] scsi2 : ahci
[    1.853658] scsi3 : ahci
[    1.853710] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.853713] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.853716] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.853719] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    1.853867]   alloc irq_desc for 16 on node -1
[    1.853868]   alloc kstat_irqs on node -1
[    1.853875] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.853951] scsi4 : pata_atiixp
[    1.853988] scsi5 : pata_atiixp
[    1.854607] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.854609] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    1.854999] Fixed MDIO Bus: probed
[    1.855020] PPP generic driver version 2.4.2
[    1.855070] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.855082]   alloc irq_desc for 17 on node -1
[    1.855083]   alloc kstat_irqs on node -1
[    1.855090] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.855099] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.855123] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.855151] ehci_hcd 0000:00:12.2: debug port 1
[    1.855170] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    1.864018] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.864066] usb usb1: configuration #1 chosen from 1 choice
[    1.864082] hub 1-0:1.0: USB hub found
[    1.864086] hub 1-0:1.0: 6 ports detected
[    1.864128]   alloc irq_desc for 19 on node -1
[    1.864129]   alloc kstat_irqs on node -1
[    1.864136] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.864145] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.864163] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.864187] ehci_hcd 0000:00:13.2: debug port 1
[    1.864208] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    1.876018] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.876066] usb usb2: configuration #1 chosen from 1 choice
[    1.876081] hub 2-0:1.0: USB hub found
[    1.876086] hub 2-0:1.0: 6 ports detected
[    1.876127] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.876138] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.876148] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.876167] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.876191] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    1.936037] usb usb3: configuration #1 chosen from 1 choice
[    1.936053] hub 3-0:1.0: USB hub found
[    1.936060] hub 3-0:1.0: 3 ports detected
[    1.936094] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.936102] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.936120] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.936133] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.992037] usb usb4: configuration #1 chosen from 1 choice
[    1.992052] hub 4-0:1.0: USB hub found
[    1.992059] hub 4-0:1.0: 3 ports detected
[    1.992095] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.992104] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.992121] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.992145] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    2.048036] usb usb5: configuration #1 chosen from 1 choice
[    2.048051] hub 5-0:1.0: USB hub found
[    2.048058] hub 5-0:1.0: 3 ports detected
[    2.048095] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.048103] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.048119] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    2.048132] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    2.104039] usb usb6: configuration #1 chosen from 1 choice
[    2.104054] hub 6-0:1.0: USB hub found
[    2.104061] hub 6-0:1.0: 3 ports detected
[    2.104098] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.104108] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.104124] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    2.104138] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    2.160042] usb usb7: configuration #1 chosen from 1 choice
[    2.160057] hub 7-0:1.0: USB hub found
[    2.160064] hub 7-0:1.0: 2 ports detected
[    2.160100] uhci_hcd: USB Universal Host Controller Interface driver
[    2.160141] PNP: No PS/2 controller found. Probing ports directly.
[    2.172045] ata3: SATA link down (SStatus 0 SControl 300)
[    2.172083] ata4: SATA link down (SStatus 0 SControl 300)
[    2.193492] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    2.193493] If AUX port is really absent please use the 'i8042.noaux' option.
[    2.193559] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.327754] usb 2-1: configuration #1 chosen from 1 choice
[    2.336033] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.336046] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.336714] ata2.00: ATAPI: ATAPI   iHAS124   A, BL0A, max UDMA/100, ATAPI AN
[    2.336776] ata1.00: ATA-8: Hitachi HDP725050GLA360, GM4OA5CA, max UDMA/133
[    2.336778] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.337694] ata1.00: configured for UDMA/133
[    2.337709] ata2.00: configured for UDMA/100
[    2.352095] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDP72505 GM4O PQ: 0 ANSI: 5
[    2.352172] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.352217] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.352239] sd 0:0:0:0: [sda] Write Protect is off
[    2.352241] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.352252] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.352319]  sda:
[    2.353243] scsi 1:0:0:0: CD-ROM            ATAPI    iHAS124   A      BL0A PQ: 0 ANSI: 5
[    2.355864] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.355866] Uniform CD-ROM driver Revision: 3.20
[    2.355908] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.355931] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.365794]  sda1 sda2 < sda5 >
[    2.392056] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.440019] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    2.444102] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.444136] mice: PS/2 mouse device common for all mice
[    2.444188] rtc_cmos 00:05: RTC can wake from S4
[    2.444205] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.444234] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.444293] device-mapper: uevent: version 1.0.3
[    2.444363] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.444440] device-mapper: multipath: version 1.1.0 loaded
[    2.444441] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.444511] EISA: Probing bus 0 at eisa.0
[    2.444526] Cannot allocate resource for EISA slot 4
[    2.444541] EISA: Detected 0 cards.
[    2.444646] cpuidle: using governor ladder
[    2.444647] cpuidle: using governor menu
[    2.444918] TCP cubic registered
[    2.445002] NET: Registered protocol family 10
[    2.445253] lo: Disabled Privacy Extensions
[    2.445437] NET: Registered protocol family 17
[    2.445447] Bluetooth: L2CAP ver 2.13
[    2.445448] Bluetooth: L2CAP socket layer initialized
[    2.445449] Bluetooth: SCO (Voice Link) ver 0.6
[    2.445450] Bluetooth: SCO socket layer initialized
[    2.445478] Bluetooth: RFCOMM TTY layer initialized
[    2.445480] Bluetooth: RFCOMM socket layer initialized
[    2.445481] Bluetooth: RFCOMM ver 1.11
[    2.445505] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor processors (4 cpu cores) (version 2.20.00)
[    2.445527] powernow-k8:    0 : pstate 0 (3200 MHz)
[    2.445528] powernow-k8:    1 : pstate 1 (2500 MHz)
[    2.445529] powernow-k8:    2 : pstate 2 (2100 MHz)
[    2.445530] powernow-k8:    3 : pstate 3 (800 MHz)
[    2.445703] Using IPI No-Shortcut mode
[    2.445742] PM: Resume from disk failed.
[    2.445749] registered taskstats version 1
[    2.445823]   Magic number: 5:179:145
[    2.445843] acpi device:16: hash matches
[    2.445876] rtc_cmos 00:05: setting system clock to 2009-12-26 20:06:58 UTC (1261858018)
[    2.445878] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.445880] EDD information not available.
[    2.519084] Freeing unused kernel memory: 544k freed
[    2.519247] Write protecting the kernel text: 4592k
[    2.519290] Write protecting the kernel read-only data: 1836k
[    2.577518] usb 2-2: configuration #1 chosen from 1 choice
[    2.590906] Linux agpgart interface v0.103
[    2.601233] ohci1394 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.606260] Initializing USB Mass Storage driver...
[    2.606362] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.606441] usbcore: registered new interface driver usb-storage
[    2.606444] USB Mass Storage support registered.
[    2.607127] usb-storage: device found at 2
[    2.607129] usb-storage: waiting for device to settle before scanning
[    2.609109] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.609121] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.609147] r8169 0000:02:00.0: setting latency timer to 64
[    2.609176]   alloc irq_desc for 27 on node -1
[    2.609178]   alloc kstat_irqs on node -1
[    2.609187] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    2.609576] eth0: RTL8168c/8111c at 0xf8350000, 00:24:1d:d8:54:45, XID 3c4000c0 IRQ 27
[    2.656548] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.953518] usb 6-2: new low speed USB device using ohci_hcd and address 2
[    3.120199] usb 6-2: configuration #1 chosen from 1 choice
[    3.128609] usbcore: registered new interface driver hiddev
[    3.133291] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input3
[    3.133326] generic-usb 0003:0B38:0003.0001: input,hidraw0: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:13.1-2/input0
[    3.141353] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.1/input/input4
[    3.141409] generic-usb 0003:0B38:0003.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:13.1-2/input1
[    3.141417] usbcore: registered new interface driver usbhid
[    3.141419] usbhid: v2.6:USB HID core driver
[    3.385507] usb 6-3: new low speed USB device using ohci_hcd and address 3
[    3.428202] PM: Starting manual resume from disk
[    3.428204] PM: Resume from partition 8:5
[    3.428206] PM: Checking hibernation image.
[    3.428331] PM: Resume from disk failed.
[    3.433842] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.433845] EXT4-fs (sda1): write access will be enabled during recovery
[    3.460531] EXT4-fs (sda1): barriers enabled
[    3.554228] usb 6-3: configuration #1 chosen from 1 choice
[    3.563354] input: Logitech Trackball as /devices/pci0000:00/0000:00:13.1/usb6/6-3/6-3:1.0/input/input5
[    3.563393] generic-usb 0003:046D:C404.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:13.1-3/input0
[    3.929641] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0f9a10000241d]
[    4.940360] kjournald2 starting: pid 431, dev sda1:8, commit interval 5 seconds
[    4.940371] EXT4-fs (sda1): delayed allocation enabled
[    4.940374] EXT4-fs: file extents enabled
[    4.984681] EXT4-fs: mballoc enabled
[    4.984690] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.984695] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 727
[    4.984755] EXT4-fs (sda1): 1 orphan inode deleted
[    4.984757] EXT4-fs (sda1): recovery complete
[    5.197555] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.648919] type=1505 audit(1261858021.702:2): operation="profile_load" pid=454 name=/usr/share/gdm/guest-session/Xsession
[    5.650550] type=1505 audit(1261858021.702:3): operation="profile_load" pid=455 name=/sbin/dhclient3
[    5.650732] type=1505 audit(1261858021.702:4): operation="profile_load" pid=455 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.650833] type=1505 audit(1261858021.702:5): operation="profile_load" pid=455 name=/usr/lib/connman/scripts/dhclient-script
[    5.674137] type=1505 audit(1261858021.727:6): operation="profile_load" pid=456 name=/usr/bin/evince
[    5.676971] type=1505 audit(1261858021.727:7): operation="profile_load" pid=456 name=/usr/bin/evince-previewer
[    5.678681] type=1505 audit(1261858021.731:8): operation="profile_load" pid=456 name=/usr/bin/evince-thumbnailer
[    5.706088] type=1505 audit(1261858021.759:9): operation="profile_load" pid=458 name=/usr/lib/cups/backend/cups-pdf
[    5.706305] type=1505 audit(1261858021.759:10): operation="profile_load" pid=458 name=/usr/sbin/cupsd
[    5.707604] type=1505 audit(1261858021.759:11): operation="profile_load" pid=459 name=/usr/sbin/tcpdump
[    6.495309] Adding 9823708k swap on /dev/sda5.  Priority:-1 extents:1 across:9823708k 
[    6.778413] EXT4-fs (sda1): internal journal on sda1:8
[    7.293958] udev: starting version 147
[    7.605395] usb-storage: device scan complete
[    7.606246] scsi 6:0:0:0: Direct-Access     Sony     Storage Media    0100 PQ: 0 ANSI: 0 CCS
[    7.606539] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    7.607614] sd 6:0:0:0: [sdb] 3915776 512-byte logical blocks: (2.00 GB/1.86 GiB)
[    7.608354] sd 6:0:0:0: [sdb] Write Protect is off
[    7.608356] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[    7.608357] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.611111] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.611114]  sdb: sdb1
[    7.613487] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.613489] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    8.195480] ieee80211_crypt: module is from the staging directory, the quality is unknown, you have been warned.
[    8.195870] ieee80211_crypt: registered algorithm 'NULL'
[    8.204151] ieee80211_crypt_wep: module is from the staging directory, the quality is unknown, you have been warned.
[    8.204627] ieee80211_crypt: registered algorithm 'WEP'
[    8.210091] parport_pc 00:09: reported by Plug and Play ACPI
[    8.210142] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.221390] ieee80211_crypt_tkip: module is from the staging directory, the quality is unknown, you have been warned.
[    8.221917] ieee80211_crypt: registered algorithm 'TKIP'
[    8.231480] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.237140] ppdev: user-space parallel port driver
[    8.256444] lp: driver loaded but no devices found
[    8.305598] lp0: using parport0 (interrupt-driven).
[    8.307597] ieee80211_crypt_ccmp: module is from the staging directory, the quality is unknown, you have been warned.
[    8.308057] ieee80211_crypt: registered algorithm 'CCMP'
[    9.177304] nvidia: module license 'NVIDIA' taints kernel.
[    9.177307] Disabling lock debugging due to kernel taint
[    9.184377] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    9.184380] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.184385] piix4_smbus: probe of 0000:00:14.0 failed with error -16
[    9.221989] ieee80211_rsl: module is from the staging directory, the quality is unknown, you have been warned.
[    9.282610] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[    9.286195] 
[    9.286196] Linux kernel driver for RTL8192 based WLAN cards
[    9.286197] Copyright (c) 2007-2008, Realsil Wlan
[    9.286311] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[    9.286313] ==>RtInPipes:3  
[    9.286314] ==>RtOutPipes:4  6  13  
[    9.286317] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[    9.286318] 1  1  0  0  2  2  2  2  2  
[    9.303192] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    9.303321] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[    9.303322] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[    9.303323] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[    9.428361] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.428367] nvidia 0000:01:00.0: setting latency timer to 64
[    9.428465] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[    9.444892] Dot11d_Init()
[    9.445399] usbcore: registered new interface driver rtl819xU
[   10.501241] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.631002] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   10.631167] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[   11.412211] type=1505 audit(1261858027.462:12): operation="profile_replace" pid=1014 name=/usr/share/gdm/guest-session/Xsession
[   11.413125] type=1505 audit(1261858027.466:13): operation="profile_replace" pid=1015 name=/sbin/dhclient3
[   11.413306] type=1505 audit(1261858027.466:14): operation="profile_replace" pid=1015 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   11.413407] type=1505 audit(1261858027.466:15): operation="profile_replace" pid=1015 name=/usr/lib/connman/scripts/dhclient-script
[   11.415306] type=1505 audit(1261858027.466:16): operation="profile_replace" pid=1016 name=/usr/bin/evince
[   11.418180] type=1505 audit(1261858027.470:17): operation="profile_replace" pid=1016 name=/usr/bin/evince-previewer
[   11.419888] type=1505 audit(1261858027.470:18): operation="profile_replace" pid=1016 name=/usr/bin/evince-thumbnailer
[   11.423047] type=1505 audit(1261858027.474:19): operation="profile_replace" pid=1018 name=/usr/lib/cups/backend/cups-pdf
[   11.423263] type=1505 audit(1261858027.474:20): operation="profile_replace" pid=1018 name=/usr/sbin/cupsd
[   11.424311] type=1505 audit(1261858027.474:21): operation="profile_replace" pid=1019 name=/usr/sbin/tcpdump
[   12.158351] r8169: eth0: link up
[   12.158356] r8169: eth0: link up
[   12.166523] rtl819xU: --->FirmwareDownload92S()
[   12.166524] 
[   12.166527] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   12.348594] rtl819xU:request firmware fail!
[   12.348595] 
[   12.348887] rtl819xU:Firmware Download Fail!!a
[   12.348888] 
[   12.355639] rtl819xU: --->FirmwareDownload92S()
[   12.355639] 
[   12.355641] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   12.357329] rtl819xU:request firmware fail!
[   12.357330] 
[   12.357667] rtl819xU:Firmware Download Fail!!a
[   12.357668] 
[   12.357670] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   12.357671] 
[   13.511964] rtl819xU: --->FirmwareDownload92S()
[   13.511965] 
[   13.511969] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.513700] rtl819xU:request firmware fail!
[   13.513701] 
[   13.513966] rtl819xU:Firmware Download Fail!!a
[   13.513967] 
[   13.520963] rtl819xU: --->FirmwareDownload92S()
[   13.520964] 
[   13.520966] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   13.522595] rtl819xU:request firmware fail!
[   13.522596] 
[   13.522966] rtl819xU:Firmware Download Fail!!a
[   13.522966] 
[   13.522968] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   13.522969] 
[   22.577512] eth0: no IPv6 routers present
[   31.981547] UDF-fs: No VRS found
[   31.981549] UDF-fs: No partition found (1)
[   32.028246] ISO 9660 Extensions: Microsoft Joliet Level 3
[   32.055701] ISOFS: changing to secondary root
[  603.307530] usb 2-2: USB disconnect, address 3
[  603.329601] rtl819xU:=============>wlan driver to be removed
[  603.329606] 
[  603.340083] rtl819xU:wlan driver removed
[  603.340086] 
[  624.456059] usb 2-2: new high speed USB device using ehci_hcd and address 6
[  624.591451] usb 2-2: configuration #1 chosen from 1 choice
[  624.593962] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[  624.593968] ==>RtInPipes:3  
[  624.593975] ==>RtOutPipes:4  6  13  
[  624.593985] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[  624.593990] 1  1  0  0  2  2  2  2  2  
[  624.747788] Dot11d_Init()
[  624.774032] rtl819xU: --->FirmwareDownload92S()
[  624.774036] 
[  624.774045] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  624.779804] rtl819xU:request firmware fail!
[  624.779807] 
[  624.780540] rtl819xU:Firmware Download Fail!!a
[  624.780544] 
[  624.788032] rtl819xU: --->FirmwareDownload92S()
[  624.788035] 
[  624.788042] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  624.793956] rtl819xU:request firmware fail!
[  624.793959] 
[  624.794539] rtl819xU:Firmware Download Fail!!a
[  624.794542] 
[  624.794547] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  624.794550] 
[  624.810155] rtl819xU: --->FirmwareDownload92S()
[  624.810160] 
[  624.810169] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  624.815788] rtl819xU:request firmware fail!
[  624.815791] 
[  624.816701] rtl819xU:Firmware Download Fail!!a
[  624.816704] 
[  624.825904] rtl819xU: --->FirmwareDownload92S()
[  624.825908] 
[  624.825916] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  624.831744] rtl819xU:request firmware fail!
[  624.831747] 
[  624.832412] rtl819xU:Firmware Download Fail!!a
[  624.832415] 
[  624.832420] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  624.832424] 
[10815.500470] usb 2-1: USB disconnect, address 2

```
(hint) the same as in (4)
```
$ dmesg | grep "wlan_module_name"

$ 
```
[*]Network configuration
```
$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:d8:54:45
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:de00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:fdf00000-fdf0ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:33:81:00:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

```
[*]Scan for networks:
```
$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down


```
(hint) the same as in (3)
```
$ iwlist scan wlan0

iwlist: unknown command `wlan0' (check 'iwlist --help').

```
[*]Ubuntu Version:
```
$ lsb_release -d

Description:	Ubuntu 9.10

```
[*]Kernel/architecture (including 32 vs. 64 bit):
```
$ uname -mr

2.6.31-16-generic-pae i686

```
[*]Restarting the network:
```
$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                   [ OK ] 

```
[/LIST]

---

### Post by Ugeen on 2009-12-26
WiFi Radar shows no Access Points (i.e. wireless networks).

Do I need this program (i.e. should I uninstall it)?
[LIST][*]Install WiFi Radar
[LIST][*]Applications
[*]Ubuntu Software Center
[*]Search: WiFi Radar
[/LIST]
[*]Run WiFi Radar
[LIST][*]Applications
[*]Internet
[*]WiFi Radar
[/LIST]
[/LIST]
The WiFi Radar Preferences window appeared and I clicked on the Save button.  Do I need to do something to show the Access Points (i.e. my router)?

---

### Post by Ugeen on 2009-12-26
My computer does not have a 64 bit processor.  So, I chose the WinXP2k driver from my installation cd that came with the hardware: WLAN USB Adapter.

[LIST][*]Install Windows Wireless Drivers
[LIST][*]Applications
[*]Ubuntu Software Center
[*]Search: Windows Wireless Drivers
[/LIST]
[*]Run Windows Wireless Drivers
[LIST][*]System
[*]Administration
[*]Windows Wireless Drivers
[/LIST]
[*]Install Driver
[LIST][*]Install New Driver button
[*]Location options
[LIST][*]cdrom0
[*]fscommand
[*]88_91_92_SU_Driver
[*]operating system version
[LIST=1][*]VistaX64
[*]VistaX86
[*]WinX64
[*]WinXP2k -- I selected, right?
[/LIST]
[*]net8192su.inf
[/LIST]
[*]Install button
[LIST][*]Error Message says
> Unable to see if hardware is present.
[/LIST]
[/LIST]
[/LIST]

---

### Post by Ugeen on 2009-12-26
I rebooted my computer and I got the following results.

[LIST][*]Ubuntu's easy connection to a network icon (located at the top of the screen by the date and time).
[LIST][*]Message says> Disconnected - you are now offline.
[/LIST]
[*]WiFi Radar
[LIST][*]linksys (i.e. my router's name (a.k.a. router's default name))
[*]Connect button
[*]Acquiring IP Address (DHCP)
[LIST][*]Does this process end?  After typing this up and after having a smoke, this continued to be processed.  So, I cancelled this process.  When that didn't cancel it, I closed the window.
[/LIST]
[*]Close button
[/LIST]
[/LIST]

---

### Post by Ugeen on 2009-12-26
```
$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by Ugeen on 2009-12-26
```
$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:d8:54:45
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.103 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:de00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:fdf00000-fdf0ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:33:81:00:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192su driverversion=1.55+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g

```

---

### Post by Ugeen on 2009-12-26
```
$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:16:3D:00
                    ESSID:"HL411"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:24:01:33:F2:4D
                    ESSID:"MRM"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:16:B6:08:2F:D5
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:23:69:62:D5:AC
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:0C:41:C3:03:D3
                    ESSID:"sara"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:1D:7E:5A:B9:8C
                    ESSID:"CPS"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:1C:DF:F3:31:2B
                    ESSID:"Candace "
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 00:1B:2F:55:09:EA
                    ESSID:"The Swamp"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 09 - Address: 00:22:75:20:87:BC
                    ESSID:"COGIC Boy"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


```

---

### Post by Ugeen on 2009-12-27
MAC Address from Wired connection to Wireless connection.

I'm not sure why I tried this but I took my MAC Address from my Wired connection and put it into my Wireless Address to get it working on one (1) of my computers.

I have one (1) other computer that I want this to be working on and then I'll mark this thread as:  Solved.

---

### Post by Ugeen on 2009-12-27
On the second computer, I did not need to put in my Wired MAC Address into my Wireless MAC Address.  All I had to do was to install [Software: Windows Wireless Drivers]("http://ubuntuforums.org/showpost.php?p=8563993&postcount=3").

Why the first computer setup is different than the the second computer setup is unknown to me but I've got it working on both of the computers.  So, I got what I needed.

The following is additional information that may or may not help someone else get their Wireless network to work for them.

The Ubuntu network connections (located at the top of the screen by the date and time) gives me a name on the second computer, "Wireless Networks (Manufacturer Realtek 11n Adapter)."  And, in the Interface under the Connection Information, it says, "802.11 WiFi (wlan14)."

---

### Post by xxGrenxx on 2010-02-12
what driver are u using for your wifi i recently had a similar issue with an internal wireless card n i saw u were not getting any help so figured id see what i could do 4 yas

---

### Post by xxGrenxx on 2010-02-12
nvrmnd didnt quite get all that but its fixed so nvmnd

---

