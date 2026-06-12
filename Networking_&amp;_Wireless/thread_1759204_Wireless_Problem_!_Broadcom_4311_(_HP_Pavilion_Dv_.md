---
title: "Wireless Problem ! Broadcom 4311 ( HP Pavilion Dv 9074ea)"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by x-master on 2011-05-15
Hi !

Im fairly new to Linux, and have just installed the latest Ubuntu on my laptop ( HP pavilion DV 9074ea)

and right after installing i noticed that my wireless wasnt working ( using cable works )
And i started poking around the internett for solutions, and every different forum had a different solution.
But none worked for me so far.

So i tried one, then anotherone, then one more etc.
So now im thinking ive jammed the hole system with drivers and new paths so on :(

But the main issue is that i cant seem to get my card working, and im feeling quite frustrated.

 terminal: lspci
lspci

03:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

Terminal :
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

terminal : 
lsmod

Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
nvidia               9766978  41 
snd_hda_codec_conexant    43782  1 
rfcomm                 38125  8 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
sco                    17779  2 
bnep                   17785  2 
wl                   2642531  0 
snd_seq_midi           13132  0 
l2cap                  48656  16 rfcomm,bnep
snd_rawmidi            25269  1 snd_seq_midi
hp_wmi                 13418  0 
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13666  1 hp_wmi
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
btusb                  18160  2 
r852                   17878  0 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sm_common              16737  1 r852
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                73312  0 
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
videodev               75143  1 uvcvideo
serio_raw              12990  0 
k8temp                 12872  0 
mtd                    26720  2 sm_common,nand
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
nv_tco                 13331  0 
video                  18951  0 
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
firewire_core          56138  1 firewire_ohci
forcedeth              58190  0 
crc_itu_t              12627  1 firewire_core
sata_nv                23176  2 
pata_amd               13762  0

Terminal :
dmesg

[    0.219351] system 00:04: [io  0x1480-0x14ff] has been reserved
[    0.219355] system 00:04: [io  0x1800-0x187f] has been reserved
[    0.219358] system 00:04: [io  0x1880-0x18ff] has been reserved
[    0.219362] system 00:04: [io  0x2000-0x203f] has been reserved
[    0.219366] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.219381] pnp 00:05: [io  0x0010-0x001f]
[    0.219384] pnp 00:05: [io  0x0022-0x003f]
[    0.219387] pnp 00:05: [io  0x0044-0x005f]
[    0.219389] pnp 00:05: [io  0x0068-0x006f]
[    0.219392] pnp 00:05: [io  0x0080]
[    0.219394] pnp 00:05: [io  0x0091-0x0093]
[    0.219397] pnp 00:05: [io  0x0097-0x009f]
[    0.219400] pnp 00:05: [io  0x00a2-0x00bf]
[    0.219407] pnp 00:05: [io  0x00e0-0x00ef]
[    0.219410] pnp 00:05: [io  0x0360-0x0361]
[    0.219412] pnp 00:05: [io  0x0380-0x0383]
[    0.219415] pnp 00:05: [io  0x04d0-0x04d1]
[    0.219491] system 00:05: [io  0x0360-0x0361] has been reserved
[    0.219495] system 00:05: [io  0x0380-0x0383] has been reserved
[    0.219498] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.219503] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.219518] pnp 00:06: [io  0x0000-0x0008]
[    0.219521] pnp 00:06: [io  0x000a-0x000f]
[    0.219524] pnp 00:06: [io  0x0081-0x0083]
[    0.219526] pnp 00:06: [io  0x0087]
[    0.219529] pnp 00:06: [io  0x0089-0x008b]
[    0.219532] pnp 00:06: [io  0x008f]
[    0.219534] pnp 00:06: [io  0x00c0-0x00d1]
[    0.219537] pnp 00:06: [io  0x00d4-0x00df]
[    0.219540] pnp 00:06: [dma 4]
[    0.219574] pnp 00:06: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.219584] pnp 00:07: [io  0x0061]
[    0.219622] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.219633] pnp 00:08: [io  0x00f0-0x00f1]
[    0.219649] pnp 00:08: [irq 13]
[    0.219684] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.219714] pnp 00:09: [io  0x0070-0x0071]
[    0.219749] pnp 00:09: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.219800] pnp 00:0a: [irq 0 disabled]
[    0.219811] pnp 00:0a: [irq 8]
[    0.219814] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.219851] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.219863] pnp 00:0b: [io  0x0060]
[    0.219865] pnp 00:0b: [io  0x0064]
[    0.219874] pnp 00:0b: [irq 1]
[    0.219913] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.219931] pnp 00:0c: [irq 12]
[    0.219971] pnp 00:0c: Plug and Play ACPI device, IDs SYN0129 SYN0100 SYN0002 PNP0f13 (active)
[    0.220475] pnp: PnP ACPI: found 13 devices
[    0.220478] ACPI: ACPI bus type pnp unregistered
[    0.220481] PnPBIOS: Disabled by ACPI PNP
[    0.257355] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.257359] pci 0000:00:02.0:   bridge window [io  0x4000-0x4fff]
[    0.257364] pci 0000:00:02.0:   bridge window [mem 0xc2000000-0xc3ffffff]
[    0.257368] pci 0000:00:02.0:   bridge window [mem 0xc8200000-0xc83fffff 64bit pref]
[    0.257373] pci 0000:00:03.0: PCI bridge to [bus 03-03]
[    0.257376] pci 0000:00:03.0:   bridge window [io  disabled]
[    0.257380] pci 0000:00:03.0:   bridge window [mem 0xc4000000-0xc5ffffff]
[    0.257383] pci 0000:00:03.0:   bridge window [mem pref disabled]
[    0.257392] pci 0000:05:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.257395] pci 0000:00:04.0: PCI bridge to [bus 05-05]
[    0.257399] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
[    0.257403] pci 0000:00:04.0:   bridge window [mem 0xc6000000-0xc7ffffff]
[    0.257407] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.257413] pci 0000:00:10.0: PCI bridge to [bus 07-07]
[    0.257415] pci 0000:00:10.0:   bridge window [io  disabled]
[    0.257420] pci 0000:00:10.0:   bridge window [mem 0xc8000000-0xc80fffff]
[    0.257424] pci 0000:00:10.0:   bridge window [mem pref disabled]
[    0.257434] pci 0000:00:02.0: setting latency timer to 64
[    0.257440] pci 0000:00:03.0: setting latency timer to 64
[    0.257445] pci 0000:00:04.0: setting latency timer to 64
[    0.257451] pci 0000:00:10.0: setting latency timer to 64
[    0.257455] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.257459] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.257462] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.257465] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.257469] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.257472] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.257476] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.257479] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.257482] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.257486] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.257489] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.257492] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.257496] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.257499] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.257503] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
[    0.257506] pci_bus 0000:00: resource 19 [mem 0x40000000-0xfebfffff]
[    0.257510] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.257513] pci_bus 0000:01: resource 1 [mem 0xc2000000-0xc3ffffff]
[    0.257517] pci_bus 0000:01: resource 2 [mem 0xc8200000-0xc83fffff 64bit pref]
[    0.257520] pci_bus 0000:03: resource 1 [mem 0xc4000000-0xc5ffffff]
[    0.257524] pci_bus 0000:05: resource 0 [io  0x5000-0x5fff]
[    0.257527] pci_bus 0000:05: resource 1 [mem 0xc6000000-0xc7ffffff]
[    0.257531] pci_bus 0000:05: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.257534] pci_bus 0000:07: resource 1 [mem 0xc8000000-0xc80fffff]
[    0.257538] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
[    0.257541] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
[    0.257544] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
[    0.257547] pci_bus 0000:07: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.257551] pci_bus 0000:07: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.257554] pci_bus 0000:07: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.257558] pci_bus 0000:07: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.257561] pci_bus 0000:07: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.257564] pci_bus 0000:07: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.257568] pci_bus 0000:07: resource 13 [mem 0x000dc000-0x000dffff]
[    0.257571] pci_bus 0000:07: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.257574] pci_bus 0000:07: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.257578] pci_bus 0000:07: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.257581] pci_bus 0000:07: resource 17 [mem 0x000ec000-0x000effff]
[    0.257585] pci_bus 0000:07: resource 18 [mem 0x000f0000-0x000fffff]
[    0.257588] pci_bus 0000:07: resource 19 [mem 0x40000000-0xfebfffff]
[    0.257637] NET: Registered protocol family 2
[    0.257714] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.258044] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.258876] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.259297] TCP: Hash tables configured (established 131072 bind 65536)
[    0.259300] TCP reno registered
[    0.259304] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.259319] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.259430] NET: Registered protocol family 1
[    0.259460] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    0.259466] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.259511] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.259537] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.259568] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.462065] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.462126] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.462189] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.462255] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.462282] pci 0000:05:00.0: Boot video device
[    0.462296] PCI: CLS 64 bytes, default 64
[    0.462326] Simple Boot Flag at 0x36 set to 0x1
[    0.462580] cpufreq-nforce2: No nForce2 chipset.
[    0.462749] audit: initializing netlink socket (disabled)
[    0.462760] type=2000 audit(1305488457.460:1): initialized
[    0.475437] highmem bounce pool size: 64 pages
[    0.475443] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.477718] VFS: Disk quotas dquot_6.5.2
[    0.477787] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.478622] fuse init (API version 7.16)
[    0.478734] msgmni has been set to 1704
[    0.479017] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.479050] io scheduler noop registered
[    0.479052] io scheduler deadline registered
[    0.479073] io scheduler cfq registered (default)
[    0.479253] pcieport 0000:00:02.0: setting latency timer to 64
[    0.479292] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.479345] pcieport 0000:00:03.0: setting latency timer to 64
[    0.479372] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    0.479421] pcieport 0000:00:04.0: setting latency timer to 64
[    0.479447] pcieport 0000:00:04.0: irq 42 for MSI/MSI-X
[    0.479543] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.479576] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.480143] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.480427] ACPI: AC Adapter [ACAD] (on-line)
[    0.480528] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.480535] ACPI: Power Button [PWRB]
[    0.480591] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.480595] ACPI: Sleep Button [SLPB]
[    0.480649] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.480887] ACPI: Lid Switch [LID]
[    0.480965] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.480969] ACPI: Power Button [PWRF]
[    0.481206] ACPI: acpi_idle registered with cpuidle
[    0.481233] ACPI: processor limited to max C-state 1
[    0.484227] thermal LNXTHERM:00: registered as thermal_zone0
[    0.484231] ACPI: Thermal Zone [THRM] (73 C)
[    0.484254] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.484365] ERST: Table is not found!
[    0.484472] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.492113] isapnp: Scanning for PnP cards...
[    0.738567] Freeing initrd memory: 12516k freed
[    0.756349] ACPI: Battery Slot [BAT0] (battery present)
[    0.845662] isapnp: No Plug & Play device found
[    1.032534] Linux agpgart interface v0.103
[    1.034424] brd: module loaded
[    1.035150] loop: module loaded
[    1.035276] i2c-core: driver [adp5520] using legacy suspend method
[    1.035278] i2c-core: driver [adp5520] using legacy resume method
[    1.035496] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    1.035522] pata_acpi 0000:00:0e.0: enabling device (0005 -> 0007)
[    1.035732] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    1.035753] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    1.035775] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    1.035785] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    1.035798] pata_acpi 0000:00:0f.0: enabling device (0005 -> 0007)
[    1.035958] ACPI: PCI Interrupt Link [LSI1] enabled at IRQ 20
[    1.035972] pata_acpi 0000:00:0f.0: PCI INT A -> Link[LSI1] -> GSI 20 (level, high) -> IRQ 20
[    1.035993] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    1.036040] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    1.036532] Fixed MDIO Bus: probed
[    1.036589] PPP generic driver version 2.4.2
[    1.036644] tun: Universal TUN/TAP device driver, 1.6
[    1.036647] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.036757] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.036936] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    1.036951] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    1.036968] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    1.036972] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    1.037019] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    1.037111] ehci_hcd 0000:00:0b.1: debug port 1
[    1.037124] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    1.037155] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xc0005000
[    1.048034] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    1.048194] hub 1-0:1.0: USB hub found
[    1.048199] hub 1-0:1.0: 8 ports detected
[    1.048319] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.048555] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    1.048561] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    1.048581] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    1.048585] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    1.048645] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    1.048694] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xc0004000
[    1.106181] hub 2-0:1.0: USB hub found
[    1.106189] hub 2-0:1.0: 8 ports detected
[    1.106313] uhci_hcd: USB Universal Host Controller Interface driver
[    1.106422] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.121341] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.121351] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.121509] mousedev: PS/2 mouse device common for all mice
[    1.122377] rtc_cmos 00:09: RTC can wake from S4
[    1.122468] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.122515] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.122638] device-mapper: uevent: version 1.0.3
[    1.122741] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.122882] device-mapper: multipath: version 1.2.0 loaded
[    1.122885] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.122993] EISA: Probing bus 0 at eisa.0
[    1.122998] EISA: Cannot allocate resource for mainboard
[    1.123002] Cannot allocate resource for EISA slot 1
[    1.123005] Cannot allocate resource for EISA slot 2
[    1.123007] Cannot allocate resource for EISA slot 3
[    1.123010] Cannot allocate resource for EISA slot 4
[    1.123014] Cannot allocate resource for EISA slot 5
[    1.123017] Cannot allocate resource for EISA slot 6
[    1.123019] Cannot allocate resource for EISA slot 7
[    1.123023] Cannot allocate resource for EISA slot 8
[    1.123025] EISA: Detected 0 cards.
[    1.123138] cpuidle: using governor ladder
[    1.123141] cpuidle: using governor menu
[    1.123489] TCP cubic registered
[    1.123649] NET: Registered protocol family 10
[    1.124417] NET: Registered protocol family 17
[    1.124440] Registering the dns_resolver key type
[    1.124467] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 (2 cpu cores) (version 2.20.00)
[    1.124508] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[    1.124511] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15
[    1.124514] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[    1.124560] Using IPI No-Shortcut mode
[    1.124693] PM: Hibernation image not present or could not be loaded.
[    1.124707] registered taskstats version 1
[    1.125072]   Magic number: 11:269:698
[    1.125130] pci 0000:00:00.3: hash matches
[    1.125204] rtc_cmos 00:09: setting system clock to 2011-05-15 19:40:58 UTC (1305488458)
[    1.125208] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.125210] EDD information not available.
[    1.125332] Freeing unused kernel memory: 700k freed
[    1.125746] Write protecting the kernel text: 5192k
[    1.125801] Write protecting the kernel read-only data: 2148k
[    1.134517] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.158970] <30>udev[65]: starting version 167
[    1.316214] pata_amd 0000:00:0d.0: version 0.4.1
[    1.316271] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.328122] scsi0 : pata_amd
[    1.330855] scsi1 : pata_amd
[    1.331636] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.331640] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.333555] sata_nv 0000:00:0e.0: version 3.5
[    1.333574] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    1.333578] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.333644] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.336444] scsi2 : sata_nv
[    1.339074] scsi3 : sata_nv
[    1.339241] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    1.339246] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    1.339320] sata_nv 0000:00:0f.0: PCI INT A -> Link[LSI1] -> GSI 20 (level, high) -> IRQ 20
[    1.339324] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    1.339385] sata_nv 0000:00:0f.0: setting latency timer to 64
[    1.342624] scsi4 : sata_nv
[    1.344518] scsi5 : sata_nv
[    1.344706] ata5: SATA max UDMA/133 cmd 0x30d8 ctl 0x30cc bmdma 0x30a0 irq 20
[    1.344711] ata6: SATA max UDMA/133 cmd 0x30d0 ctl 0x30c8 bmdma 0x30a8 irq 20
[    1.344799] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.345002] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.345008] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    1.345015] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.350682] sdhci: Secure Digital Host Controller Interface driver
[    1.350684] sdhci: Copyright(c) Pierre Ossman
[    1.472047] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.492422] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-4084N, KQ09, max MWDMA2
[    1.492432] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    1.508263] ata1.00: configured for MWDMA2
[    1.514055] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4084N KQ09 PQ: 0 ANSI: 5
[    1.519237] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.519241] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.519405] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.519500] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.519612] ata2: port disabled. ignoring.
[    1.800061] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.808320] ata3.00: ATA-7: FUJITSU MHV2080BH PL, 892C, max UDMA/100
[    1.808325] ata3.00: 156301488 sectors, multi 16: LBA48 
[    1.816106] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.824306] ata3.00: configured for UDMA/100
[    1.824311] ata5.00: ATA-7: FUJITSU MHV2080BH PL, 892C, max UDMA/100
[    1.824315] ata5.00: 156301488 sectors, multi 16: LBA48 
[    1.824434] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHV2080B 892C PQ: 0 ANSI: 5
[    1.824679] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.824801] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.824859] sd 2:0:0:0: [sda] Write Protect is off
[    1.824863] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.824889] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.840229] ata5.00: configured for UDMA/100
[    1.865248] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:bb:b6:b0
[    1.865253] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    1.916043] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    2.136054] ata4: SATA link down (SStatus 0 SControl 300)
[    2.136250] scsi 4:0:0:0: Direct-Access     ATA      FUJITSU MHV2080B 892C PQ: 0 ANSI: 5
[    2.136426] sd 4:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.136475] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.136488] sd 4:0:0:0: [sdb] Write Protect is off
[    2.136492] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.136517] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.222758]  sda: sda1 < sda5 > sda2 sda3
[    2.223174] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.265120]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    2.265569] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.448041] ata6: SATA link down (SStatus 0 SControl 300)
[    2.450345] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[    2.450578] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[    2.450595] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[    2.451619] sdhci-pci 0000:07:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.451645] mmc0: no vmmc regulator found
[    2.455899] Registered led device: mmc0::
[    2.457030] mmc0: SDHCI controller on PCI [0000:07:05.1] using DMA
[    2.457308] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    2.457326] firewire_ohci 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    2.513242] firewire_ohci: Added fw-ohci device 0000:07:05.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    2.956294] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[    3.016147] firewire_core: created device fw0: GUID 009fc000cee2d000, S400
[   19.920220] <30>udev[347]: starting version 167
[   19.951362] lp: driver loaded but no devices found
[   19.977189] Adding 1046524k swap on /dev/sdb6.  Priority:-1 extents:1 across:1046524k 
[   20.238229] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
[   20.370969] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   20.371031] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   20.385550] NV_TCO: NV TCO WatchDog Timer Driver v0.01
[   20.385677] NV_TCO: Watchdog reboot not detected.
[   20.385789] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
[   20.418845] lib80211: common routines for IEEE802.11 drivers
[   20.418852] lib80211_crypt: registered algorithm 'NULL'
[   20.421475] acpi device:28: registered as cooling_device2
[   20.421626] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:26/LNXVIDEO:01/input/input5
[   20.421785] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.499439] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   20.517912] type=1400 audit(1305481277.889:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=608 comm="apparmor_parser"
[   20.518385] type=1400 audit(1305481277.889:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=608 comm="apparmor_parser"
[   20.518893] type=1400 audit(1305481277.889:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=608 comm="apparmor_parser"
[   20.670683] Linux video capture interface: v2.00
[   20.676500] r852 0000:07:05.3: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   20.676510] r852 0000:07:05.3: setting latency timer to 64
[   20.677465] Bluetooth: Core ver 2.15
[   20.679217] NET: Registered protocol family 31
[   20.679222] Bluetooth: HCI device and connection manager initialized
[   20.679226] Bluetooth: HCI socket layer initialized
[   20.696597] r852: Non dma capable device detected, dma disabled
[   20.696617] r852: driver loaded succesfully
[   20.709626] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   20.747658] usbcore: registered new interface driver btusb
[   20.767456] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.767462] Disabling lock debugging due to kernel taint
[   20.805337] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   20.892127] type=1400 audit(1305481278.265:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=739 comm="apparmor_parser"
[   20.898066] type=1400 audit(1305481278.269:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=740 comm="apparmor_parser"
[   20.900657] type=1400 audit(1305481278.273:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=740 comm="apparmor_parser"
[   20.900755] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/1-4:1.0/input/input6
[   20.900905] usbcore: registered new interface driver uvcvideo
[   20.900908] USB Video Class driver (v1.0.0)
[   20.900969] type=1400 audit(1305481278.273:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=740 comm="apparmor_parser"
[   20.916162] type=1400 audit(1305481278.289:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=746 comm="apparmor_parser"
[   20.916875] type=1400 audit(1305481278.289:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=746 comm="apparmor_parser"
[   20.924161] type=1400 audit(1305481278.297:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=749 comm="apparmor_parser"
[   21.280917] input: HP WMI hotkeys as /devices/virtual/input/input7
[   21.335314] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   21.335338] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[   21.335345] wl 0000:03:00.0: setting latency timer to 64
[   21.337760] malloc in abgphy done
[   21.341079] malloc in abgphy done
[   21.341185] eth%d: 5.100.82.38 driver failed with code 21
[   21.351911] Bluetooth: L2CAP ver 2.15
[   21.351916] Bluetooth: L2CAP socket layer initialized
[   21.368695] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.368700] Bluetooth: BNEP filters: protocol multicast
[   21.422287] Bluetooth: SCO (Voice Link) ver 0.6
[   21.422291] Bluetooth: SCO socket layer initialized
[   21.452933] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0
[   21.465903] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   21.465926] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   21.465931] hda_intel: Disable MSI for Nvidia chipset
[   21.465981] HDA Intel 0000:00:10.1: setting latency timer to 64
[   21.514803] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   21.629821] Bluetooth: RFCOMM TTY layer initialized
[   21.629829] Bluetooth: RFCOMM socket layer initialized
[   21.629832] Bluetooth: RFCOMM ver 1.11
[   23.083970] nvidia 0000:05:00.0: power state changed by ACPI to D0
[   23.083977] nvidia 0000:05:00.0: power state changed by ACPI to D0
[   23.084199] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 16
[   23.084220] nvidia 0000:05:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, high) -> IRQ 16
[   23.084231] nvidia 0000:05:00.0: setting latency timer to 64
[   23.084237] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   23.084545] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   23.199833] vesafb: framebuffer at 0xd0000000, mapped to 0xf8300000, using 3072k, total 3072k
[   23.199839] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   23.199842] vesafb: scrolling: redraw
[   23.199847] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   23.200341] Console: switching to colour frame buffer device 128x48
[   23.200374] fb0: VESA VGA frame buffer device
[   23.390990] ppdev: user-space parallel port driver
[   24.293543] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   29.074497] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   31.464030] eth0: no IPv6 routers present
[   79.612022] CE: hpet increased min_delta_ns to 11520 nsec
[  936.381257] forcedeth 0000:00:14.0: eth0: link down
[  945.529946] forcedeth 0000:00:14.0: eth0: link up
[ 2780.064084] ata1: lost interrupt (Status 0x0)
[ 2780.064118] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2780.064132] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 2780.064163] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 2780.064167]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 2780.064176] ata1.00: status: { DRDY }
[ 2780.064214] ata1: soft resetting link
[ 2780.228403] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[ 2780.244304] ata1.00: configured for MWDMA2
[ 2780.249843] ata1: EH complete
[ 2891.248411] forcedeth 0000:00:14.0: eth0: link down
[ 2898.770760] forcedeth 0000:00:14.0: eth0: link up


Terminal : 
sudo lshw -C network

 *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c4000000-c4003fff

Terminal lsb_release -d

Description:    Ubuntu 11.04

---

### Post by x-master on 2011-05-15
Status = solved

---

### Post by x-master on 2011-05-16
SOLVED IT !!!


Here is a quote from the solution, and it was really too simple -.-
Hope it helps others as well.

Fixed wireless : Broadcom 4311 ( rev01)
OS : Ubuntu 11.04

Problem: wireless card not discovered/ no drivers. ( used standard broadcom SAT driver )
lshw -c network : showed my wireless card ( UNCLAIMED )

[QUOTE=solution]My problem is solved after  removing "bcmwl-kernel-source" by using Synaptic Package Manager, then  installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic  Package Manager. After a restart, my wireless network connection works.  I hope it solves your problem, too.
          [/QUOTE]

---

