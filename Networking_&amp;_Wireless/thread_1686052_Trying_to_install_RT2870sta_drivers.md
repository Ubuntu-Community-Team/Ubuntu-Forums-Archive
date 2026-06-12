---
title: "Trying to install RT2870sta drivers"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by Alterbridge82 on 2011-02-11
Hey guys please help close to giving up

tried installing these drivers

changed the common file for wpa support then it comes to making to .ko file and this error comes up




Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2


please help i cant go on trying

---

### Post by chili555 on 2011-02-11
The driver rt2870sta is already built in to the kernel. I wonder why you are building it from scratch. If the driver that's built-in doesn't work, either it's wrong for your device or something else is wrong. Please post:> lsmod | grep rt2
dmesg | grep rt2

---

### Post by Alterbridge82 on 2011-02-11
really new to linux hoe do i get the line up after lsmod

---

### Post by Alterbridge82 on 2011-02-11
Module                  Size  Used by
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
ufs                    73069  0 
qnx4                    6877  0 
hfsplus                71344  0 
hfs                    41250  0 
minix                  25303  0 
ntfs                   95015  0 
msdos                   6436  0 
jfs                   171034  0 
xfs                   693150  0 
exportfs                3449  1 xfs
reiserfs              225942  0 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  2 msdos,vfat
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_idt      54887  1 
tuner_simple           13641  1 
tuner_types            14575  1 tuner_simple
snd_hda_intel          22107  2 
wm8775                  2941  1 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
tda9887                 9697  1 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
tda8290                12538  0 
tuner                  20578  2 
cx25840                28795  1 
i915                  290938  3 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ivtv                  141210  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cx2341x                12385  1 ivtv
drm                   168054  4 i915,drm_kms_helper
usbhid                 36882  0 
v4l2_common            17329  5 wm8775,tuner,cx25840,ivtv,cx2341x
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               43098  5 wm8775,tuner,cx25840,ivtv,v4l2_common
hid                    67742  1 usbhid
intel_agp              26360  2 i915
dcdbas                  5402  0 
v4l1_compat            13359  1 videodev
tveeprom               11178  1 ivtv
psmouse                59033  0 
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5168  2 i915,ivtv
video                  18712  1 i915
serio_raw               4022  0 
output                  1883  1 video
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  1 
e100                   30356  0 
mii                     4425  1 e100

thats the lsmod

[    0.764421] system 00:07: [io  0x6900-0x69fe] has been reserved
[    0.764428] system 00:07: [io  0x6a00-0x6afe] has been reserved
[    0.764436] system 00:07: [io  0x6b00-0x6bfe] has been reserved
[    0.764443] system 00:07: [io  0x6c00-0x6cfe] has been reserved
[    0.764450] system 00:07: [io  0x6d00-0x6dfe] has been reserved
[    0.764457] system 00:07: [io  0x6e00-0x6efe] has been reserved
[    0.764464] system 00:07: [io  0x6f00-0x6ffe] has been reserved
[    0.764472] system 00:07: [io  0xa000-0xa0fe] has been reserved
[    0.764479] system 00:07: [io  0xa100-0xa1fe] has been reserved
[    0.764487] system 00:07: [io  0xa200-0xa2fe] has been reserved
[    0.764494] system 00:07: [io  0xa300-0xa3fe] has been reserved
[    0.764502] system 00:07: [io  0xa400-0xa4fe] has been reserved
[    0.764509] system 00:07: [io  0xa500-0xa5fe] has been reserved
[    0.764516] system 00:07: [io  0xa600-0xa6fe] has been reserved
[    0.764524] system 00:07: [io  0xa700-0xa7fe] has been reserved
[    0.764531] system 00:07: [io  0xa800-0xa8fe] has been reserved
[    0.764539] system 00:07: [io  0xa900-0xa9fe] has been reserved
[    0.764547] system 00:07: [io  0xaa00-0xaafe] has been reserved
[    0.764554] system 00:07: [io  0xab00-0xabfe] has been reserved
[    0.764562] system 00:07: [io  0xac00-0xacfe] has been reserved
[    0.764569] system 00:07: [io  0xad00-0xadfe] has been reserved
[    0.764577] system 00:07: [io  0xae00-0xaefe] has been reserved
[    0.764585] system 00:07: [io  0xaf00-0xaffe] has been reserved
[    0.764593] system 00:07: [mem 0xe0000000-0xefffffff] has been reserved
[    0.764600] system 00:07: [mem 0xfeda0000-0xfedacfff] has been reserved
[    0.802669] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.802681] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.802688] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.802694] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.802704] pci 0000:00:1c.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.802712] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.802723] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.802727] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.802736] pci 0000:00:1c.1:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.802743] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.802754] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.802760] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.802769] pci 0000:00:1e.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.802777] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xd3ffffff 64bit pref]
[    0.802805]   alloc irq_desc for 16 on node -1
[    0.802810]   alloc kstat_irqs on node -1
[    0.802823] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.802831] pci 0000:00:1c.0: setting latency timer to 64
[    0.802846]   alloc irq_desc for 17 on node -1
[    0.802850]   alloc kstat_irqs on node -1
[    0.802860] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.802869] pci 0000:00:1c.1: setting latency timer to 64
[    0.802880] pci 0000:00:1e.0: setting latency timer to 64
[    0.802890] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.802895] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.802901] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.802906] pci_bus 0000:01: resource 1 [mem 0xdfe00000-0xdfefffff]
[    0.802912] pci_bus 0000:01: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.802918] pci_bus 0000:02: resource 1 [mem 0xdfd00000-0xdfdfffff]
[    0.802923] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.802928] pci_bus 0000:03: resource 1 [mem 0xdfc00000-0xdfcfffff]
[    0.802934] pci_bus 0000:03: resource 2 [mem 0xd0000000-0xd3ffffff 64bit pref]
[    0.802939] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.802945] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.803019] NET: Registered protocol family 2
[    0.803170] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.803679] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.804378] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.804733] TCP: Hash tables configured (established 131072 bind 65536)
[    0.804738] TCP reno registered
[    0.804745] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.804761] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.805033] NET: Registered protocol family 1
[    0.805065] pci 0000:00:02.0: Boot video device
[    0.805229] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[    0.805241] PCI: CLS 64 bytes, default 64
[    0.805282] Simple Boot Flag at 0x7a set to 0x1
[    0.805598] cpufreq-nforce2: No nForce2 chipset.
[    0.805659] Scanning for low memory corruption every 60 seconds
[    0.805915] audit: initializing netlink socket (disabled)
[    0.805933] type=2000 audit(1297449972.800:1): initialized
[    0.820449] highmem bounce pool size: 64 pages
[    0.820461] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.823688] VFS: Disk quotas dquot_6.5.2
[    0.823828] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.825172] fuse init (API version 7.14)
[    0.825373] msgmni has been set to 1682
[    0.826076] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.826082] io scheduler noop registered
[    0.826086] io scheduler deadline registered
[    0.826120] io scheduler cfq registered (default)
[    0.826331] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.826380]   alloc irq_desc for 40 on node -1
[    0.826384]   alloc kstat_irqs on node -1
[    0.826400] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.826551] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.826598]   alloc irq_desc for 41 on node -1
[    0.826602]   alloc kstat_irqs on node -1
[    0.826615] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.826781] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.826891] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.827253] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.827266] ACPI: Power Button [VBTN]
[    0.827374] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.827383] ACPI: Power Button [PWRF]
[    0.828008] ACPI: acpi_idle registered with cpuidle
[    0.867976] ERST: Table is not found!
[    0.868283] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.871384] brd: module loaded
[    0.872686] loop: module loaded
[    0.873061] ata_piix 0000:00:1f.1: version 2.13
[    0.873081] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.873146] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.873268] scsi0 : ata_piix
[    0.873430] scsi1 : ata_piix
[    0.873520] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.873526] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.873559]   alloc irq_desc for 20 on node -1
[    0.873564]   alloc kstat_irqs on node -1
[    0.873577] ata_piix 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.873602] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.873720] isapnp: Scanning for PnP cards...
[    0.922766] ata2: port disabled. ignoring.
[    0.960340] Freeing initrd memory: 10504k freed
[    1.028284] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.028410] scsi2 : ata_piix
[    1.028545] scsi3 : ata_piix
[    1.028617] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    1.028623] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    1.029314] Fixed MDIO Bus: probed
[    1.029384] PPP generic driver version 2.4.2
[    1.029482] tun: Universal TUN/TAP device driver, 1.6
[    1.029486] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.029653] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.029686]   alloc irq_desc for 21 on node -1
[    1.029690]   alloc kstat_irqs on node -1
[    1.029701] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.029725] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.029731] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.029803] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.029839] ehci_hcd 0000:00:1d.7: debug port 1
[    1.033736] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.033762] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[    1.048017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.048250] hub 1-0:1.0: USB hub found
[    1.048260] hub 1-0:1.0: 8 ports detected
[    1.048402] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.048429] uhci_hcd: USB Universal Host Controller Interface driver
[    1.048484] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.048500] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.048506] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.048571] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.048601] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[    1.048818] hub 2-0:1.0: USB hub found
[    1.048827] hub 2-0:1.0: 2 ports detected
[    1.048929]   alloc irq_desc for 22 on node -1
[    1.048934]   alloc kstat_irqs on node -1
[    1.048943] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.048954] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.048960] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.049022] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.049065] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    1.049282] hub 3-0:1.0: USB hub found
[    1.049295] hub 3-0:1.0: 2 ports detected
[    1.049403]   alloc irq_desc for 18 on node -1
[    1.049407]   alloc kstat_irqs on node -1
[    1.049416] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.049426] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.049431] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.049494] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.049537] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    1.049749] hub 4-0:1.0: USB hub found
[    1.049756] hub 4-0:1.0: 2 ports detected
[    1.049863]   alloc irq_desc for 23 on node -1
[    1.049867]   alloc kstat_irqs on node -1
[    1.049875] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.049885] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.049890] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.049953] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.049995] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    1.050228] hub 5-0:1.0: USB hub found
[    1.050236] hub 5-0:1.0: 2 ports detected
[    1.050439] PNP: No PS/2 controller found. Probing ports directly.
[    1.053134] ata1.00: ATA-7: Maxtor 6E040L0, NAR61EA0, max UDMA/133
[    1.053140] ata1.00: 80293248 sectors, multi 8: LBA 
[    1.053545] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.053557] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.053672] mice: PS/2 mouse device common for all mice
[    1.053868] rtc_cmos 00:05: RTC can wake from S4
[    1.053950] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.053981] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    1.054187] device-mapper: uevent: version 1.0.3
[    1.054380] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.054492] device-mapper: multipath: version 1.1.1 loaded
[    1.054497] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.054703] EISA: Probing bus 0 at eisa.0
[    1.054708] EISA: Cannot allocate resource for mainboard
[    1.054713] Cannot allocate resource for EISA slot 1
[    1.054717] Cannot allocate resource for EISA slot 2
[    1.054731] Cannot allocate resource for EISA slot 5
[    1.054735] Cannot allocate resource for EISA slot 6
[    1.054749] EISA: Detected 0 cards.
[    1.054882] cpuidle: using governor ladder
[    1.054887] cpuidle: using governor menu
[    1.055494] TCP cubic registered
[    1.055762] NET: Registered protocol family 10
[    1.056583] lo: Disabled Privacy Extensions
[    1.057071] NET: Registered protocol family 17
[    1.057149] Using IPI No-Shortcut mode
[    1.057298] PM: Resume from disk failed.
[    1.057325] registered taskstats version 1
[    1.057664]   Magic number: 15:944:796
[    1.057756] rtc_cmos 00:05: setting system clock to 2011-02-11 18:46:14 UTC (1297449974)
[    1.057762] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.057765] EDD information not available.
[    1.068437] ata1.00: configured for UDMA/100
[    1.207039] ata3.00: ATA-7: SAMSUNG SP0411C/R, UU100-05, max UDMA/100
[    1.207046] ata3.00: 78165360 sectors, multi 8: LBA48 
[    1.216182] ata3.00: configured for UDMA/100
[    1.227080] isapnp: No Plug & Play device found
[    1.227277] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[    1.227483] sd 0:0:0:0: [sda] 80293248 512-byte logical blocks: (41.1 GB/38.2 GiB)
[    1.227543] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.227603] sd 0:0:0:0: [sda] Write Protect is off
[    1.227610] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.227680] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.227806] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SP0411C/ UU10 PQ: 0 ANSI: 5
[    1.228045] sd 2:0:0:0: [sdb] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.228079] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.228178] sd 2:0:0:0: [sdb] Write Protect is off
[    1.228185] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.228244]  sda:
[    1.228250] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.228590]  sdb: sdb1
[    1.235706] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.249559]  sda1 sda2 < sda5 >
[    1.273650] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.273675] Freeing unused kernel memory: 684k freed
[    1.274202] Write protecting the kernel text: 4932k
[    1.274265] Write protecting the kernel read-only data: 1976k
[    1.302744] udev[82]: starting version 163
[    1.448342] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.466464] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.466470] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.466529] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.491687] e100 0000:03:08.0: PME# disabled
[    1.527595] e100 0000:03:08.0: eth0: addr 0xdfcff000, irq 20, MAC addr 00:13:20:af:7f:5c
[    1.610671] Initializing USB Mass Storage driver...
[    1.610889] scsi4 : usb-storage 1-2:1.0
[    1.611066] usbcore: registered new interface driver usb-storage
[    1.611072] USB Mass Storage support registered.
[    1.708026] usb 1-3: new high speed USB device using ehci_hcd and address 4
[    1.788031] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.024025] usb 1-5: new high speed USB device using ehci_hcd and address 6
[    2.158132] scsi5 : usb-storage 1-5:1.0
[    2.396023] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.643784] scsi 4:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1P   KL0A PQ: 0 ANSI: 0
[    2.651761] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.651767] Uniform CD-ROM driver Revision: 3.20
[    2.651937] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.652040] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    2.820030] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    3.156929] scsi 5:0:0:0: Direct-Access     USB      Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[    3.157676] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    3.158287] sd 5:0:0:0: [sdc] 3915776 512-byte logical blocks: (2.00 GB/1.86 GiB)
[    3.159029] sd 5:0:0:0: [sdc] Write Protect is off
[    3.159034] sd 5:0:0:0: [sdc] Mode Sense: 43 00 00 00
[    3.159038] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    3.160528] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    3.160536]  sdc: sdc1
[    3.162527] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    3.162533] sd 5:0:0:0: [sdc] Attached SCSI disk
[   10.837574] udev[286]: starting version 163
[   10.900734] Adding 1690620k swap on /dev/sda5.  Priority:-1 extents:1 across:1690620k 
[   11.042819] intel_rng: Firmware space is locked read-only. If you can't or
[   11.042823] intel_rng: don't want to disable this in firmware setup, and if
[   11.042826] intel_rng: you are certain that your system has a functional
[   11.042829] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   11.200903] lp: driver loaded but no devices found
[   11.279718] Linux agpgart interface v0.103
[   11.291227] agpgart-intel 0000:00:00.0: Intel 915G Chipset
[   11.291942] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   11.308483] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.360230] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   11.427120] Linux video capture interface: v2.00
[   11.490873] usbcore: registered new interface driver hiddev
[   11.494162] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.506452] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
[   11.506668] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.0-1/input0
[   11.523833] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3
[   11.524229] generic-usb 0003:0A81:0101.0002: input,hidraw1: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:1d.1-2/input0
[   11.556731] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input4
[   11.556907] generic-usb 0003:0A81:0101.0003: input,hidraw2: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:1d.1-2/input1
[   11.556949] usbcore: registered new interface driver usbhid
[   11.556954] usbhid: USB HID core driver
[   11.601513] type=1400 audit(1297449985.040:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=519 comm="apparmor_parser"
[   11.602670] type=1400 audit(1297449985.040:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=519 comm="apparmor_parser"
[   11.604205] type=1400 audit(1297449985.044:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=519 comm="apparmor_parser"
[   11.628292] ivtv: Start initialization, version 1.4.1
[   11.628381] ivtv0: Initializing card 0
[   11.628388] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   11.652262] ivtv 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.663906] [drm] Initialized drm 1.1.0 20060810
[   11.711471] tveeprom 0-0050: The eeprom says no radio is present, but the tuner type
[   11.711479] tveeprom 0-0050: indicates otherwise. I will assume that radio is present.
[   11.711486] tveeprom 0-0050: Hauppauge model 26589, rev C9A5, serial# 8769269
[   11.711492] tveeprom 0-0050: tuner model is TCL MPE05-2 (idx 105, type 38)
[   11.711498] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   11.711504] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   11.711510] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   11.711514] tveeprom 0-0050: has radio
[   11.711519] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   11.852376] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.852389] i915 0000:00:02.0: setting latency timer to 64
[   11.871137] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   11.902104] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   11.927804] tda9887 0-0043: creating new instance
[   11.927813] tda9887 0-0043: tda988[5/6/7] found
[   11.945813] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   11.971903] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   11.989984] [drm] set up 7M of stolen space
[   11.990650] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   11.991075] [drm] initialized overlay support
[   12.012859] tuner-simple 0-0061: creating new instance
[   12.012870] tuner-simple 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   12.016601] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   12.016673] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   12.016809] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   12.016950] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   12.017092] ivtv0: Registered device radio0 for encoder radio
[   12.017099] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   12.017196] ivtv: End initialization
[   12.140310] type=1400 audit(1297449985.580:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=724 comm="apparmor_parser"
[   12.143283] type=1400 audit(1297449985.580:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=725 comm="apparmor_parser"
[   12.144274] type=1400 audit(1297449985.584:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=725 comm="apparmor_parser"
[   12.144755] type=1400 audit(1297449985.584:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=725 comm="apparmor_parser"
[   12.151921] type=1400 audit(1297449985.588:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=726 comm="apparmor_parser"
[   12.165220] type=1400 audit(1297449985.604:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=726 comm="apparmor_parser"
[   12.175116] type=1400 audit(1297449985.612:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=730 comm="apparmor_parser"
[   12.298651] Console: switching to colour frame buffer device 180x56
[   12.303935] fb0: inteldrmfb frame buffer device
[   12.303939] drm: registered panic notifier
[   12.303945] Slow work thread pool: Starting up
[   12.304069] Slow work thread pool: Ready
[   12.304086] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.304143] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.304214]   alloc irq_desc for 42 on node -1
[   12.304219]   alloc kstat_irqs on node -1
[   12.304238] HDA Intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   12.304305] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.380674] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   12.380829] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   12.380956] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.381078] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.466255] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.746677] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   12.944423] ivtv0: Encoder revision: 0x02060039
[   14.097732] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.759545] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   17.072203] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   17.516460] ppdev: user-space parallel port driver
[   17.774487] audit_printk_skb: 9 callbacks suppressed
[   17.774492] type=1400 audit(1297449991.212:15): apparmor="DENIED" operation="capable" parent=1232 profile="/sbin/dhclient3" pid=1233 comm="dhclient3" capability=12  capname="net_admin"
[   17.933390] type=1400 audit(1297449991.372:16): apparmor="DENIED" operation="capable" parent=1232 profile="/sbin/dhclient3" pid=1233 comm="dhclient3" capability=12  capname="net_admin"
[  649.004149] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[  649.004359] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  659.416007] eth0: no IPv6 routers present
[ 2746.769858] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 2746.777566] SGI XFS Quota Management subsystem
[ 2746.787870] JFS: nTxBlock = 8192, nTxLock = 65536
[ 2746.806123] NTFS driver 2.1.29 [Flags: R/O MODULE].
[ 2746.836430] QNX4 filesystem 0.2.3 registered.
[ 2746.874264] Btrfs loaded
[ 2747.212337] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[ 2788.058510] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[ 2793.705036] udev[24041]: starting version 163
[ 2803.722507] type=1400 audit(1297463385.824:17): apparmor="STATUS" operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" pid=24124 comm="apparmor_parser"
[ 2803.924228] type=1400 audit(1297463386.028:18): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=24125 comm="apparmor_parser"
[ 2803.924459] type=1400 audit(1297463386.028:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=24125 comm="apparmor_parser"
[ 2803.924613] type=1400 audit(1297463386.028:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=24125 comm="apparmor_parser"
[ 2804.837074] type=1400 audit(1297463386.940:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=24128 comm="apparmor_parser"
[ 2804.837457] type=1400 audit(1297463386.940:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=24128 comm="apparmor_parser"
[ 2805.068266] type=1400 audit(1297463387.172:23): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=24129 comm="apparmor_parser"
[ 2811.051668] type=1400 audit(1297463393.152:24): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=24126 comm="apparmor_parser"
[ 2811.053440] type=1400 audit(1297463393.156:25): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=24126 comm="apparmor_parser"
[ 2811.054573] type=1400 audit(1297463393.156:26): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=24126 comm="apparmor_parser"
[ 2811.333628] type=1400 audit(1297463393.436:27): apparmor="STATUS" operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" pid=24167 comm="apparmor_parser"
[ 2811.546414] type=1400 audit(1297463393.648:28): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=24168 comm="apparmor_parser"
[ 2811.546631] type=1400 audit(1297463393.648:29): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=24168 comm="apparmor_parser"
[ 2811.546781] type=1400 audit(1297463393.648:30): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=24168 comm="apparmor_parser"
[ 2812.370284] type=1400 audit(1297463394.472:31): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=24171 comm="apparmor_parser"
[ 2812.370654] type=1400 audit(1297463394.472:32): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=24171 comm="apparmor_parser"
[ 2812.636948] type=1400 audit(1297463394.740:33): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=24172 comm="apparmor_parser"
[ 2818.879548] type=1400 audit(1297463400.980:34): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=24169 comm="apparmor_parser"
[ 2818.881288] type=1400 audit(1297463400.984:35): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=24169 comm="apparmor_parser"
[ 2818.882391] type=1400 audit(1297463400.984:36): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=24169 comm="apparmor_parser"
[ 2858.067492] type=1400 audit(1297463440.168:37): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=24609 comm="apparmor_parser"
[ 2858.067791] type=1400 audit(1297463440.168:38): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=24609 comm="apparmor_parser"
[ 2858.093751] type=1400 audit(1297463440.196:39): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=24620 comm="apparmor_parser"
[ 2858.094716] type=1400 audit(1297463440.196:40): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=24620 comm="apparmor_parser"
[ 2875.797256] type=1400 audit(1297463457.900:41): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=24704 comm="apparmor_parser"
[ 2875.798786] type=1400 audit(1297463457.900:42): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=24704 comm="apparmor_parser"
[ 2875.799862] type=1400 audit(1297463457.900:43): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=24704 comm="apparmor_parser"

thats the dmesg

---

### Post by chili555 on 2011-02-11
> really new to linux hoe do i get the line up after lsmodI'm sorry about that! The pipe symbol | is on the right side of my US keyboard on the same key with \.

rt2870sta is not loading, nor any other wireless driver. I assume yours is a USB device. If so, please post:```
lsusb
```Thanks.

---

