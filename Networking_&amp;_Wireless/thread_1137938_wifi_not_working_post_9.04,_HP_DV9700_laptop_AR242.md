---
title: "wifi not working post 9.04, HP DV9700 laptop AR242x 802.11abg"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by VMysteriis on 2009-04-26
Was working fine before I upgraded from 8.10 to 9.04 (kernel 2.6.28-11-generic x86_64), but now I'm having some problems. I've tried a few different things, ndiswrapper and the like, not having a lot of success. Tried my google magic, nothing's working. Figured I'd ask you guys before I jacked up my system


IWConfig
```
vermis@vermis-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

LSMod

```
vermis@vermis-laptop:~$ lsmod
Module                  Size  Used by
ndiswrapper           250624  0 
isofs                  43688  0 
udf                    92584  0 
crc_itu_t              10496  1 udf
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
sbp2                   34700  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
joydev                 20864  0 
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               69512  0 
snd                    78792  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
sdhci_pci              16896  0 
compat_ioctl32         18304  1 uvcvideo
k8temp                 13440  0 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
sdhci                  27396  1 sdhci_pci
ricoh_mmc              12544  0 
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
pcspkr                 11136  0 
nvidia               8123768  38 
psmouse                64028  0 
serio_raw              14468  0 
ath_pci               108400  0 
wlan                  232736  1 ath_pci
ath_hal               225904  1 ath_pci
video                  29204  5 
output                 11648  1 video
ohci1394               42036  0 
forcedeth              68368  0 
ieee1394              108288  2 sbp2,ohci1394
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

dmesg (This thing is all jumbled up I have no idea what's going on)

```
[    0.437953] pci 0000:02:05.1: PME# disabled
[    0.437975] pci 0000:02:05.2: reg 10 32bit mmio: [0xf6100c00-0xf6100cff]
[    0.438001] pci 0000:02:05.2: supports D1 D2
[    0.438003] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.438006] pci 0000:02:05.2: PME# disabled
[    0.438029] pci 0000:02:05.3: reg 10 32bit mmio: [0xf6101000-0xf61010ff]
[    0.438054] pci 0000:02:05.3: supports D1 D2
[    0.438056] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.438059] pci 0000:02:05.3: PME# disabled
[    0.438084] pci 0000:02:05.4: reg 10 32bit mmio: [0xf6101400-0xf61014ff]
[    0.438110] pci 0000:02:05.4: supports D1 D2
[    0.438111] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.438115] pci 0000:02:05.4: PME# disabled
[    0.438144] pci 0000:00:08.0: transparent bridge
[    0.438148] pci 0000:00:08.0: bridge 32bit mmio: [0xf6100000-0xf61fffff]
[    0.438183] pci 0000:00:0c.0: bridge io port: [0x4000-0x4fff]
[    0.438186] pci 0000:00:0c.0: bridge 32bit mmio: [0xf2000000-0xf3ffffff]
[    0.438189] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.438224] pci 0000:03:00.0: reg 10 64bit mmio: [0xf6000000-0xf600ffff]
[    0.438292] pci 0000:00:0d.0: bridge 32bit mmio: [0xf6000000-0xf60fffff]
[    0.438301] bus 00 -> node 0
[    0.438307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.438409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.438434] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.438471] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.471602] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.471831] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.472072] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.472297] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.472522] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.472747] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.472971] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.473196] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.473420] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.473645] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.473870] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.474100] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.474325] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.474549] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.474774] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.474999] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.475224] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.475454] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.475685] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.475923] ACPI: WMI: Mapper loaded
[    0.480003] SCSI subsystem initialized
[    0.480018] libata version 3.00 loaded.
[    0.480031] usbcore: registered new interface driver usbfs
[    0.480051] usbcore: registered new interface driver hub
[    0.480056] usbcore: registered new device driver usb
[    0.480056] PCI: Using ACPI for IRQ routing
[    0.488010] Bluetooth: Core ver 2.13
[    0.492012] NET: Registered protocol family 31
[    0.492013] Bluetooth: HCI device and connection manager initialized
[    0.492016] Bluetooth: HCI socket layer initialized
[    0.492018] NET: Registered protocol family 8
[    0.492019] NET: Registered protocol family 20
[    0.492031] NetLabel: Initializing
[    0.492032] NetLabel:  domain hash size = 128
[    0.492034] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.492047] NetLabel:  unlabeled traffic allowed by default
[    0.492206] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.492210] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.496076] AppArmor: AppArmor Filesystem Enabled
[    0.504021] Switched to high resolution mode on CPU 0
[    0.504034] Switched to high resolution mode on CPU 1
[    0.509024] pnp: PnP ACPI init
[    0.509034] ACPI: bus type pnp registered
[    0.512899] pnp: PnP ACPI: found 12 devices
[    0.512901] ACPI: ACPI bus type pnp unregistered
[    0.512911] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.512917] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.512920] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.512922] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.512924] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.512927] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.512929] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.512935] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.512937] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.512944] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.512947] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.512949] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.512952] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.512955] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.517668] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.517670] pci 0000:00:08.0:   IO window: disabled
[    0.517674] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.517676] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.517680] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.517682] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.517685] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.517688] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.517691] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.517693] pci 0000:00:0d.0:   IO window: disabled
[    0.517696] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.517698] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.517705] pci 0000:00:08.0: setting latency timer to 64
[    0.517710] pci 0000:00:0c.0: setting latency timer to 64
[    0.517715] pci 0000:00:0d.0: setting latency timer to 64
[    0.517718] bus: 00 index 0 io port: [0x00-0xffff]
[    0.517720] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.517722] bus: 02 index 0 mmio: [0x0-0x0]
[    0.517724] bus: 02 index 1 mmio: [0xf6100000-0xf61fffff]
[    0.517726] bus: 02 index 2 mmio: [0x0-0x0]
[    0.517728] bus: 02 index 3 io port: [0x00-0xffff]
[    0.517730] bus: 02 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.517732] bus: 04 index 0 io port: [0x4000-0x4fff]
[    0.517733] bus: 04 index 1 mmio: [0xf2000000-0xf3ffffff]
[    0.517735] bus: 04 index 2 mmio: [0xf0000000-0xf1ffffff]
[    0.517737] bus: 04 index 3 mmio: [0x0-0x0]
[    0.517739] bus: 03 index 0 mmio: [0x0-0x0]
[    0.517741] bus: 03 index 1 mmio: [0xf6000000-0xf60fffff]
[    0.517742] bus: 03 index 2 mmio: [0x0-0x0]
[    0.517744] bus: 03 index 3 mmio: [0x0-0x0]
[    0.517755] NET: Registered protocol family 2
[    0.557070] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.557546] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.559445] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.559937] TCP: Hash tables configured (established 262144 bind 65536)
[    0.559940] TCP reno registered
[    0.569106] NET: Registered protocol family 1
[    0.569229] checking if image is initramfs... it is
[    1.155537] Freeing initrd memory: 7767k freed
[    1.159655] Simple Boot Flag at 0x36 set to 0x1
[    1.159969] audit: initializing netlink socket (disabled)
[    1.159983] type=2000 audit(1240722236.156:1): initialized
[    1.168110] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.169434] VFS: Disk quotas dquot_6.5.1
[    1.169490] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.170103] fuse init (API version 7.10)
[    1.170184] msgmni has been set to 3844
[    1.170382] alg: No test for stdrng (krng)
[    1.170397] io scheduler noop registered
[    1.170398] io scheduler anticipatory registered
[    1.170400] io scheduler deadline registered
[    1.170444] io scheduler cfq registered (default)
[    1.170474] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.170640] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.170654] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.170670] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.170686] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.170700] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.170715] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.170730] pci 0000:00:12.0: Boot video device
[    1.177407] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.177430] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.177447] pcieport-driver 0000:00:0c.0: irq 2303 for MSI/MSI-X
[    1.177453] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.177470] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.177508] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.177529] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.177541] pcieport-driver 0000:00:0d.0: irq 2302 for MSI/MSI-X
[    1.177547] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.177560] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.177606] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.177615] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.179015] ACPI: AC Adapter [ACAD] (on-line)
[    1.457273] ACPI: Battery Slot [BAT0] (battery present)
[    1.457355] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.457358] ACPI: Power Button (FF) [PWRF]
[    1.457400] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.457402] ACPI: Sleep Button (CM) [SLPB]
[    1.457450] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.458660] ACPI: Lid Switch [LID]
[    1.458718] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.458720] ACPI: Power Button (CM) [PWRB]
[    1.459044] ACPI: processor limited to max C-state 1
[    1.459070] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.459100] processor ACPI_CPU:00: registered as cooling_device0
[    1.459104] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.459188] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.459210] processor ACPI_CPU:01: registered as cooling_device1
[    1.459214] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.723195] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080926]
[    1.757267] Linux agpgart interface v0.103
[    1.757277] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.758188] brd: module loaded
[    1.758513] loop: module loaded
[    1.758589] Fixed MDIO Bus: probed
[    1.758595] PPP generic driver version 2.4.2
[    1.758649] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.758681] Driver 'sd' needs updating - please use bus_type methods
[    1.758690] Driver 'sr' needs updating - please use bus_type methods
[    1.758732] ahci 0000:00:09.0: version 3.0
[    1.759140] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    1.759151] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    1.759199] ahci 0000:00:09.0: irq 2301 for MSI/MSI-X
[    1.759261] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.759264] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[    1.759267] ahci 0000:00:09.0: setting latency timer to 64
[    1.759656] scsi0 : ahci
[    1.759799] scsi1 : ahci
[    1.759877] scsi2 : ahci
[    1.759950] scsi3 : ahci
[    1.760053] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 2301
[    1.760055] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 2301
[    1.760058] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 2301
[    1.760060] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 2301
[    2.240034] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.240433] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[    2.240436] ata1.00: 488397168 sectors, multi 16: LBA48 
[    2.240898] ata1.00: configured for UDMA/100
[    2.560026] ata2: SATA link down (SStatus 0 SControl 300)
[    2.880025] ata3: SATA link down (SStatus 0 SControl 300)
[    3.200024] ata4: SATA link down (SStatus 0 SControl 300)
[    3.200125] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[    3.200223] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.200241] sd 0:0:0:0: [sda] Write Protect is off
[    3.200243] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.200268] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.200342] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.200355] sd 0:0:0:0: [sda] Write Protect is off
[    3.200357] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.200381] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.200385]  sda: sda1 sda2 < sda5 >
[    3.273079] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.273126] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.273354] pata_amd 0000:00:06.0: version 0.3.10
[    3.273396] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.273483] scsi4 : pata_amd
[    3.273548] scsi5 : pata_amd
[    3.273926] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    3.273928] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    3.436307] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WC05, max MWDMA2
[    3.436329] ata5: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    3.452250] ata5.00: configured for MWDMA2
[    3.454536] ata6: port disabled. ignoring.
[    3.454577] isa bounce pool size: 16 pages
[    3.457580] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WC05 PQ: 0 ANSI: 5
[    3.468398] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.468401] Uniform CD-ROM driver Revision: 3.20
[    3.468499] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    3.468539] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.468949] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.469355] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    3.469366] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    3.469385] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.469387] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.469452] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    3.469482] ehci_hcd 0000:00:02.1: debug port 1
[    3.469486] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.469506] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    3.480028] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    3.480102] usb usb1: configuration #1 chosen from 1 choice
[    3.480127] hub 1-0:1.0: USB hub found
[    3.480135] hub 1-0:1.0: 7 ports detected
[    3.480580] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    3.480583] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    3.480594] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    3.480596] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    3.480635] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    3.480660] ehci_hcd 0000:00:04.1: debug port 1
[    3.480663] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    3.480668] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    3.492026] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    3.492086] usb usb2: configuration #1 chosen from 1 choice
[    3.492108] hub 2-0:1.0: USB hub found
[    3.492115] hub 2-0:1.0: 2 ports detected
[    3.492190] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.492547] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    3.492555] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    3.492565] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.492568] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.492612] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    3.492636] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    3.550061] usb usb3: configuration #1 chosen from 1 choice
[    3.550083] hub 3-0:1.0: USB hub found
[    3.550091] hub 3-0:1.0: 7 ports detected
[    3.550511] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    3.550514] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    3.550524] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    3.550527] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    3.550565] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    3.550583] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    3.606057] usb usb4: configuration #1 chosen from 1 choice
[    3.606079] hub 4-0:1.0: USB hub found
[    3.606087] hub 4-0:1.0: 2 ports detected
[    3.606163] uhci_hcd: USB Universal Host Controller Interface driver
[    3.606233] usbcore: registered new interface driver libusual
[    3.606268] usbcore: registered new interface driver usbserial
[    3.606277] USB Serial support registered for generic
[    3.606289] usbcore: registered new interface driver usbserial_generic
[    3.606291] usbserial: USB Serial Driver core
[    3.606331] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    3.633936] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.633942] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.645049] mice: PS/2 mouse device common for all mice
[    3.705092] rtc_cmos 00:07: RTC can wake from S4
[    3.705126] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.705164] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    3.705224] device-mapper: uevent: version 1.0.3
[    3.705334] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.705506] device-mapper: multipath: version 1.0.5 loaded
[    3.705509] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.705730] cpuidle: using governor ladder
[    3.705783] cpuidle: using governor menu
[    3.706182] TCP cubic registered
[    3.706251] NET: Registered protocol family 10
[    3.706613] lo: Disabled Privacy Extensions
[    3.706877] NET: Registered protocol family 17
[    3.706895] Bluetooth: L2CAP ver 2.11
[    3.706897] Bluetooth: L2CAP socket layer initialized
[    3.706899] Bluetooth: SCO (Voice Link) ver 0.6
[    3.706901] Bluetooth: SCO socket layer initialized
[    3.706956] Bluetooth: RFCOMM socket layer initialized
[    3.706964] Bluetooth: RFCOMM TTY layer initialized
[    3.706965] Bluetooth: RFCOMM ver 1.10
[    3.707018] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[    3.707071] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x11
[    3.707074] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[    3.707076] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[    3.707077] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    3.707204] registered taskstats version 1
[    3.707363]   Magic number: 5:980:62
[    3.707460] rtc_cmos 00:07: setting system clock to 2009-04-26 05:03:59 UTC (1240722239)
[    3.707463] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.707464] EDD information not available.
[    3.707504] Freeing unused kernel memory: 536k freed
[    3.707772] Write protecting the kernel read-only data: 6708k
[    3.735672] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.833029] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    3.974639] usb 2-2: configuration #1 chosen from 1 choice
[    4.213366] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.213819] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.213842] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    4.213851] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.243145] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    4.243162] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    4.294761] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.733035] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:fa:3a:bc
[    4.733040] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    4.775077] PM: Starting manual resume from disk
[    4.775080] PM: Resume from partition 8:5
[    4.775082] PM: Checking hibernation image.
[    4.775266] PM: Resume from disk failed.
[    4.828708] kjournald starting.  Commit interval 5 seconds
[    4.828720] EXT3-fs: mounted filesystem with ordered data mode.
[    5.569125] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0007b2a200]
[   11.653778] udev: starting version 141
[   11.950991] acpi device:25: registered as cooling_device2
[   11.951187] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input6
[   11.977143] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   12.055814] ath_hal: module license 'Proprietary' taints kernel.
[   12.057190] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   12.068370] wlan: 0.9.4
[   12.075759] ath_pci: 0.9.4
[   12.076297] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   12.076309] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   12.076319] ath_pci 0000:03:00.0: setting latency timer to 64
[   12.104257] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   12.104302] ath_pci 0000:03:00.0: PCI INT A disabled
[   12.494147] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.207976] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   13.207990] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   13.207996] nvidia 0000:00:12.0: setting latency timer to 64
[   13.209357] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   13.309148] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   13.331276] Linux video capture interface: v2.00
[   13.356225] ricoh-mmc: Ricoh MMC Controller disabling driver
[   13.356227] ricoh-mmc: Copyright(c) Philip Langdale
[   13.356264] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   13.356278] ricoh-mmc: Controller is now disabled.
[   13.360328] sdhci: Secure Digital Host Controller Interface driver
[   13.360332] sdhci: Copyright(c) Pierre Ossman
[   13.394633] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   13.395081] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   13.395094] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   13.398266] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   13.445468] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
[   13.447520] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input8
[   13.458878] usbcore: registered new interface driver uvcvideo
[   13.458882] USB Video Class driver (v0.1.0)
[   13.578428] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   13.623334] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   13.623348] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   13.623434] HDA Intel 0000:00:07.0: setting latency timer to 64
[   13.660496] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.339249] lp: driver loaded but no devices found
[   14.503906] Adding 5831552k swap on /dev/sda5.  Priority:-1 extents:1 across:5831552k
[   16.348926] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   16.349231] EXT3 FS on sda1, internal journal
[   17.509291] type=1505 audit(1240722253.300:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2144
[   17.558496] type=1505 audit(1240722253.348:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2148
[   17.558641] type=1505 audit(1240722253.348:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2148
[   17.558691] type=1505 audit(1240722253.348:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2148
[   17.558737] type=1505 audit(1240722253.348:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2148
[   17.693549] type=1505 audit(1240722253.484:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2153
[   17.693740] type=1505 audit(1240722253.484:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2153
[   17.725111] type=1505 audit(1240722253.516:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2157
[   21.500030] Clocksource tsc unstable (delta = -174359596 ns)
[   24.994389] forcedeth 0000:00:0a.0: irq 2300 for MSI/MSI-X
[   27.074576] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.074584] Bluetooth: BNEP filters: protocol multicast
[   27.170908] Bridge firewalling registered
[   27.396605] forcedeth 0000:00:0a.0: irq 2300 for MSI/MSI-X
[   28.614799] ppdev: user-space parallel port driver
[   37.569030] eth0: no IPv6 routers present
[  180.501807] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  180.596076] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  180.596090] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net5211'
[  180.597412] ndiswrapper (load_wrap_driver:108): couldn't load driver net5211; check system log for messages from 'loadndisdriver'
[  180.597572] usbcore: registered new interface driver ndiswrapper
[  211.332284] usbcore: deregistering interface driver ndiswrapper
[  211.332594] ndiswrapper (ntoskernel_exit:2671): object ffff88005b43c230(2) was not freed, freeing it now
[  211.362887] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  211.433878] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[  211.439811] ndiswrapper: driver net5211 (,07/26/2007,5.3.0.67) loaded
[  211.440635] ndiswrapper 0000:03:00.0: enabling device (0000 -> 0002)
[  211.440659] ndiswrapper 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[  211.440799] ndiswrapper (ZwClose:2198): closing handle 0x0 not implemented
[  211.441397] ndiswrapper 0000:03:00.0: setting latency timer to 64
[  211.443525] ndiswrapper (NdisWriteErrorLogEntry:190): log: C0001389, count: 4, return_address: ffffffffa0b4766e
[  211.443538] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x66524c00
[  211.443543] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x28
[  211.443548] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6fb000
[  211.443553] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6fb000
[  211.443785] ndiswrapper (mp_init:219): couldn't initialize device: C000009A
[  211.443800] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  211.443823] ndiswrapper (mp_halt:262): device ffff88005cdab800 is not initialized - not halting
[  211.443831] ndiswrapper: device eth%d removed
[  211.443863] ndiswrapper 0000:03:00.0: PCI INT A disabled
[  211.443903] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[  211.444057] usbcore: registered new interface driver ndiswrapper
[  762.512641] usbcore: deregistering interface driver ndiswrapper
[  762.513235] ndiswrapper (ntoskernel_exit:2671): object ffff88005b43c230(2) was not freed, freeing it now
[  762.541041] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  762.604235] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  762.604248] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net5211'
[  762.606146] ndiswrapper (load_wrap_driver:108): couldn't load driver net5211; check system log for messages from 'loadndisdriver'
[  762.606302] usbcore: registered new interface driver ndiswrapper
[  889.854635] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
vermis@vermis-laptop:~$ 

```

```
vermis@vermis-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:fa:3a:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.103 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:59:a2:56:6e:d1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

iwlist scanning doesn't work for obvious reasons (wlan0 not being detected for god knows what reason)

I know that everyone is busy helping with other problems at the moment, but some speedy assistance would be much appreciated. I've been burning myself out on this for the better part of six hours.

---

