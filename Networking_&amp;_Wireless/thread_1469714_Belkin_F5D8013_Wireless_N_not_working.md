---
title: "Belkin F5D8013 Wireless N not working"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by JackOfClubs on 2010-05-02
I've got an old IBM Thinkpad T41 that I just play around with Ubuntu on. The internal Wireless card is broken, so I bought a Belkin F5D8013 PCMCIA Wireless N card a while ago. It worked fine with Ubuntu 8.04-9.10, but it will not work with 10.04. It sees the networks just fine and will let me type in the network password, but it will not connect. Everything else in my house connects without a hitch, so I know it is Ubuntu causing the problem. Can anyone help me with this?

---

### Post by JackOfClubs on 2010-05-02
Added some info from the sticky:

lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
vga16fb                11385  0 
thinkpad_acpi          68083  0 
snd_seq_dummy           1338  0 
snd_pcm_oss            35308  0 
vgastate                8961  1 vga16fb
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            26726  0 
rt2860sta             481561  1 
snd_seq_midi            4557  0 
radeon                674135  3 
snd_rawmidi            19056  1 snd_seq_midi
ttm                    49943  1 radeon
pcmcia                 33024  0 
drm_kms_helper         29297  1 radeon
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm                   162471  5 radeon,ttm,drm_kms_helper
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
i2c_algo_bit            5028  1 radeon
yenta_socket           20408  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         10015  1 yenta_socket
snd                    54148  15 snd_intel8x0,snd_ac97_codec,thinkpad_acpi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
joydev                  8708  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
soundcore               6620  1 snd
intel_agp              24177  1 
agpgart                31724  3 ttm,drm,intel_agp
shpchp                 28820  0 
ppdev                   5259  0 
psmouse                63245  0 
led_class               2864  1 thinkpad_acpi
nvram                   6171  1 thinkpad_acpi
serio_raw               3978  0 
nsc_ircc               18220  0 
lp                      7028  0 
parport_pc             25962  1 
irda                  186556  1 nsc_ircc
crc_ccitt               1339  1 irda
video                  17375  0 
output                  1871  1 video
parport                32635  3 ppdev,lp,parport_pc
floppy                 53016  1 
e1000                  97396  0 
=======================================================================
dmesg
[    0.096448] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.096453] pci 0000:02:00.1: PME# disabled
[    0.096503] pci 0000:02:01.0: reg 10 32bit mmio: [0xc0220000-0xc023ffff]
[    0.096511] pci 0000:02:01.0: reg 14 32bit mmio: [0xc0200000-0xc020ffff]
[    0.096520] pci 0000:02:01.0: reg 18 io port: [0x8000-0x803f]
[    0.096542] pci 0000:02:01.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.096567] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.096572] pci 0000:02:01.0: PME# disabled
[    0.096618] pci 0000:00:1e.0: transparent bridge
[    0.096624] pci 0000:00:1e.0: bridge io port: [0x4000-0x8fff]
[    0.096630] pci 0000:00:1e.0: bridge 32bit mmio: [0xc0200000-0xcfffffff]
[    0.096636] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.096679] pci_bus 0000:00: on NUMA node 0
[    0.096686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.096753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.096790] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.101380] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.101618] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.101852] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.102086] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.102296] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.102507] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.102718] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.102952] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.103130] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.103136] vgaarb: loaded
[    0.103316] SCSI subsystem initialized
[    0.103380] libata version 3.00 loaded.
[    0.103475] usbcore: registered new interface driver usbfs
[    0.103497] usbcore: registered new interface driver hub
[    0.103531] usbcore: registered new device driver usb
[    0.103714] ACPI: WMI: Mapper loaded
[    0.103717] PCI: Using ACPI for IRQ routing
[    0.104059] NetLabel: Initializing
[    0.104062] NetLabel:  domain hash size = 128
[    0.104065] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.104084] NetLabel:  unlabeled traffic allowed by default
[    0.104123] Switching to clocksource tsc
[    0.106970] AppArmor: AppArmor Filesystem Enabled
[    0.106991] pnp: PnP ACPI init
[    0.107013] ACPI: bus type pnp registered
[    0.111150] pnp: PnP ACPI: found 13 devices
[    0.111153] ACPI: ACPI bus type pnp unregistered
[    0.111159] PnPBIOS: Disabled by ACPI PNP
[    0.111176] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.111181] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.111186] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.111190] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.111195] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.111199] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.111204] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.111208] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.111213] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.111217] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.111222] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.111226] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.111231] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[    0.111236] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.111247] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.111251] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.111255] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.111260] system 00:02: ioport range 0x1600-0x162f has been reserved
[    0.111264] system 00:02: ioport range 0x1632-0x167f has been reserved
[    0.111269] system 00:02: ioport range 0x1630-0x1631 has been reserved
[    0.146040] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.146045] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.146051] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.146056] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.146067] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.146071] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
[    0.146077] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
[    0.146083] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.146088] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.146094] pci 0000:02:00.1: CardBus bridge, secondary bus 0000:07
[    0.146098] pci 0000:02:00.1:   IO window: 0x004800-0x0048ff
[    0.146103] pci 0000:02:00.1:   IO window: 0x004c00-0x004cff
[    0.146109] pci 0000:02:00.1:   PREFETCH window: 0xec000000-0xefffffff
[    0.146115] pci 0000:02:00.1:   MEM window: 0xc8000000-0xcbffffff
[    0.146121] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.146126] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
[    0.146133] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
[    0.146139] pci 0000:00:1e.0:   PREFETCH window: 0xe8000000-0xefffffff
[    0.146159] pci 0000:00:1e.0: setting latency timer to 64
[    0.146575] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.146579] PCI: setting IRQ 11 as level-triggered
[    0.146586] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.146983] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.146988] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.146998] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.147002] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.147006] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.147010] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.147014] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.147019] pci_bus 0000:02: resource 0 io:  [0x4000-0x8fff]
[    0.147023] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xcfffffff]
[    0.147027] pci_bus 0000:02: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.147031] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.147035] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.147039] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.147043] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.147047] pci_bus 0000:03: resource 2 pref mem [0xe8000000-0xebffffff]
[    0.147051] pci_bus 0000:03: resource 3 mem: [0xc4000000-0xc7ffffff]
[    0.147055] pci_bus 0000:07: resource 0 io:  [0x4800-0x48ff]
[    0.147059] pci_bus 0000:07: resource 1 io:  [0x4c00-0x4cff]
[    0.147063] pci_bus 0000:07: resource 2 pref mem [0xec000000-0xefffffff]
[    0.147067] pci_bus 0000:07: resource 3 mem: [0xc8000000-0xcbffffff]
[    0.147123] NET: Registered protocol family 2
[    0.147268] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.147717] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.147870] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.148002] TCP: Hash tables configured (established 16384 bind 16384)
[    0.148006] TCP reno registered
[    0.148110] NET: Registered protocol family 1
[    0.148209] pci 0000:01:00.0: Boot video device
[    0.148313] Simple Boot Flag at 0x35 set to 0x1
[    0.148417] cpufreq-nforce2: No nForce2 chipset.
[    0.148450] Scanning for low memory corruption every 60 seconds
[    0.148620] audit: initializing netlink socket (disabled)
[    0.148639] type=2000 audit(1272815039.147:1): initialized
[    0.163932] Trying to unpack rootfs image as initramfs...
[    0.180187] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.186635] VFS: Disk quotas dquot_6.5.2
[    0.186747] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.187784] fuse init (API version 7.13)
[    0.187953] msgmni has been set to 977
[    0.192221] alg: No test for stdrng (krng)
[    0.192352] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.192357] io scheduler noop registered
[    0.192360] io scheduler anticipatory registered
[    0.192363] io scheduler deadline registered
[    0.192437] io scheduler cfq registered (default)
[    0.192612] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.192645] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.192982] ACPI: AC Adapter [AC] (on-line)
[    0.193080] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.193774] ACPI: Lid Switch [LID]
[    0.193841] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.193847] ACPI: Sleep Button [SLPB]
[    0.193931] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.193935] ACPI: Power Button [PWRF]
[    0.200280] Marking TSC unstable due to TSC halts in idle
[    0.200411] processor LNXCPU:00: registered as cooling_device0
[    0.202413] Switching to clocksource acpi_pm
[    0.210508] thermal LNXTHERM:01: registered as thermal_zone0
[    0.210522] ACPI: Thermal Zone [THM0] (56 C)
[    0.212765] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.213871] serial 00:0a: activated
[    0.213993] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.214133] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.214142] serial 0000:00:1f.6: PCI INT B disabled
[    0.215578] brd: module loaded
[    0.220444] isapnp: Scanning for PnP cards...
[    0.226783] loop: module loaded
[    0.227128] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.227395] ata_piix 0000:00:1f.1: version 2.13
[    0.227408] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.232378] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.232386] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.232517] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.232883] scsi0 : ata_piix
[    0.233175] scsi1 : ata_piix
[    0.234427] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    0.234431] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    0.235279] Fixed MDIO Bus: probed
[    0.235375] PPP generic driver version 2.4.2
[    0.235544] tun: Universal TUN/TAP device driver, 1.6
[    0.235547] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.235733] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.296503] ACPI: Battery Slot [BAT0] (battery present)
[    0.296682] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.297105] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.297112] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.297137] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.297143] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.297246] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.297289] ehci_hcd 0000:00:1d.7: debug port 1
[    0.301185] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.303542] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    0.324480] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.324685] usb usb1: configuration #1 chosen from 1 choice
[    0.324732] hub 1-0:1.0: USB hub found
[    0.324748] hub 1-0:1.0: 6 ports detected
[    0.324853] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.324880] uhci_hcd: USB Universal Host Controller Interface driver
[    0.325224] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.325239] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.325252] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.325258] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.325329] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.325361] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    0.325504] usb usb2: configuration #1 chosen from 1 choice
[    0.325544] hub 2-0:1.0: USB hub found
[    0.325555] hub 2-0:1.0: 2 ports detected
[    0.325789] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.326212] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.326217] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.326226] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.326231] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.326281] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.326305] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    0.326440] usb usb3: configuration #1 chosen from 1 choice
[    0.326477] hub 3-0:1.0: USB hub found
[    0.326488] hub 3-0:1.0: 2 ports detected
[    0.326550] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.326558] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.326562] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.326610] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.326634] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    0.326774] usb usb4: configuration #1 chosen from 1 choice
[    0.326817] hub 4-0:1.0: USB hub found
[    0.326826] hub 4-0:1.0: 2 ports detected
[    0.326963] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.336755] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.336771] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.340759] mice: PS/2 mouse device common for all mice
[    0.340954] rtc_cmos 00:06: RTC can wake from S4
[    0.341034] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.341056] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.341269] device-mapper: uevent: version 1.0.3
[    0.341475] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.385490] device-mapper: multipath: version 1.1.0 loaded
[    0.385495] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.386847] EISA: Probing bus 0 at eisa.0
[    0.386855] Cannot allocate resource for EISA slot 1
[    0.386860] Cannot allocate resource for EISA slot 2
[    0.386863] Cannot allocate resource for EISA slot 3
[    0.386866] Cannot allocate resource for EISA slot 4
[    0.386869] Cannot allocate resource for EISA slot 5
[    0.386872] Cannot allocate resource for EISA slot 6
[    0.386875] Cannot allocate resource for EISA slot 7
[    0.386878] Cannot allocate resource for EISA slot 8
[    0.386881] EISA: Detected 0 cards.
[    0.388580] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.392081] cpuidle: using governor ladder
[    0.392169] cpuidle: using governor menu
[    0.392947] TCP cubic registered
[    0.393219] NET: Registered protocol family 10
[    0.394699] lo: Disabled Privacy Extensions
[    0.395214] NET: Registered protocol family 17
[    0.395470] P-state transition latency capped at 20 uS
[    0.395784] Using IPI No-Shortcut mode
[    0.395934] PM: Resume from disk failed.
[    0.395951] registered taskstats version 1
[    0.396281]   Magic number: 10:417:739
[    0.396418] rtc_cmos 00:06: setting system clock to 2010-05-02 15:43:59 UTC (1272815039)
[    0.396423] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.396426] EDD information not available.
[    0.480074] ata2.01: NODEV after polling detection
[    0.488942] ata2.00: ATAPI: UJDA755zDVD/CDRW, 1.20, max UDMA/33
[    0.504680] ata2.00: configured for UDMA/33
[    0.567727] ata1.00: ATA-7: WDC WD800BEVE-00UYT0, 01.04A01, max UDMA/100
[    0.567734] ata1.00: 156301488 sectors, multi 16: LBA48 
[    0.581272] ata1.00: configured for UDMA/100
[    0.842285] Freeing initrd memory: 7778k freed
[    0.897630] isapnp: No Plug & Play device found
[    0.897871] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BEVE-00 01.0 PQ: 0 ANSI: 5
[    0.898104] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.898172] sd 0:0:0:0: [sda] Write Protect is off
[    0.898176] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.898210] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.898443]  sda:
[    0.898691] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.901302] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA755zDVD/CDRW 1.20 PQ: 0 ANSI: 5
[    0.906344] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.906349] Uniform CD-ROM driver Revision: 3.20
[    0.906497] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.906567] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.977543]  sda1 sda2 < sda5 sda6 sda7 >
[    1.023956] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.023977] Freeing unused kernel memory: 656k freed
[    1.024673] Write protecting the kernel text: 4676k
[    1.024730] Write protecting the kernel read-only data: 1840k
[    1.046547] udev: starting version 151
[    1.322273] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
[    1.322279] Copyright (c) 1999-2006 Intel Corporation.
[    1.322336] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.322765] Floppy drive(s): fd0 is 1.44M
[    1.340978] FDC 0 is a National Semiconductor PC87306
[    1.574946] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0d:60:b2:a7:a7
[    1.609883] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    1.878859] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    3.611979] Adding 1487864k swap on /dev/sda7.  Priority:-1 extents:1 across:1487864k 
[    3.779397] udev: starting version 151
[    4.964039] type=1505 audit(1272815044.067:2):  operation="profile_load" pid=428 name="/sbin/dhclient3"
[    4.964905] type=1505 audit(1272815044.067:3):  operation="profile_load" pid=428 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.965377] type=1505 audit(1272815044.067:4):  operation="profile_load" pid=428 name="/usr/lib/connman/scripts/dhclient-script"
[    5.106340] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:02/LNXVIDEO:00/input/input5
[    5.106522] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    5.193637] irda_init()
[    5.193657] NET: Registered protocol family 23
[    5.252270] parport_pc 00:0b: reported by Plug and Play ACPI
[    5.252316] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[    5.289753] lp: driver loaded but no devices found
[    5.348277] lp0: using parport0 (interrupt-driven).
[    5.374056] nsc-ircc 00:0c: activated
[    5.374064] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[    5.374279] nsc-ircc, chip->init
[    5.374289] nsc-ircc, Found chip at base=0x02e
[    5.374314] nsc-ircc, driver loaded (Dag Brattli)
[    5.376342] IrDA: Registered device irda0
[    5.376347] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[    5.415750] Non-volatile memory driver v1.3
[    5.552608] ppdev: user-space parallel port driver
[    5.580095] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.720787] intel_rng: FWH not detected
[    5.736715] Linux agpgart interface v0.103
[    6.144317] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[    6.144326] serio: Synaptics pass-through port at isa0060/serio1/input0
[    6.187417] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    6.268624] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    6.283907] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    6.672489] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0552]
[    6.672511] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[    6.672514] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[    6.672522] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21b22, devctl 0x64
[    6.908461] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0430, PCI irq 11
[    6.908468] yenta_cardbus 0000:02:00.0: Socket status: 30000020
[    6.908478] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[    6.908484] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
[    6.910170] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[    6.910174] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[    6.910644] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0552]
[    6.910663] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
[    6.910667] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
[    6.910673] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21b22, devctl 0x64
[    7.140993] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0430, PCI irq 11
[    7.141000] yenta_cardbus 0000:02:00.1: Socket status: 30000086
[    7.141013] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[    7.141019] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
[    7.142791] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[    7.142796] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[    7.156360] [drm] Initialized drm 1.1.0 20060810
[    7.475806] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[    7.477281] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[    7.477734] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    7.478119] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    7.478687] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    7.544069] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[    7.544122] pci 0000:03:00.0: reg 10 32bit mmio: [0xffff0000-0xffffffff]
[    7.667952] [drm] radeon defaulting to kernel modesetting.
[    7.667958] [drm] radeon kernel modesetting enabled.
[    7.668400] radeon 0000:01:00.0: power state changed by ACPI to D0
[    7.668415] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    7.675854] [drm] radeon: Initializing kernel modesetting.
[    7.675953] [drm] register mmio base: 0xC0100000
[    7.675956] [drm] register mmio size: 65536
[    7.676433] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[    7.677224] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[    7.677244] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[    7.677286] radeon 0000:01:00.0: putting AGP V2 device into 1x mode
[    7.677318] [drm] radeon: VRAM 64M
[    7.677321] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[    7.677324] [drm] radeon: GTT 256M
[    7.677327] [drm] radeon: GTT from 0xD0000000 to 0xDFFFFFFF
[    7.677357] [drm] radeon: irq initialized.
[    7.677756] [drm] Detected VRAM RAM=64M, BAR=128M
[    7.677761] [drm] RAM width 64bits DDR
[    7.678093] [TTM] Zone  kernel: Available graphics memory: 254352 kiB.
[    7.678117] [drm] radeon: 32M of VRAM memory ready
[    7.678121] [drm] radeon: 256M of GTT memory ready.
[    7.678372] [drm] radeon: cp idle (0x00008383)
[    7.678422] [drm] Loading R100 Microcode
[    7.678806] platform radeon_cp.0: firmware: requesting radeon/R100_cp.bin
[    7.841619] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    7.884983] rt2860 0000:03:00.0: enabling device (0000 -> 0002)
[    7.885000] rt2860 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    7.885374] 
[    7.885375] 
[    7.885376] === pAd = e0ac8000, size = 580808 ===
[    7.885377] 
[    7.885381] <-- RTMPAllocAdapterBlock, Status=0
[    7.885435] rt2860 0000:03:00.0: setting latency timer to 64
[    7.892340] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[    7.905522] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[    7.905976] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[    7.908541] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[    7.909115] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[    8.048499] [drm] radeon: ring at 0x00000000D0000000
[    8.048525] [drm] ring test succeeded in 1 usecs
[    8.051370] [drm] radeon: ib pool ready.
[    8.051501] [drm] ib test succeeded in 0 usecs
[    8.055079] [drm] DFP table revision: 2
[    8.055963] [drm] Panel ID String: 1024x768                
[    8.055968] [drm] Panel Size 1024x768
[    8.056482] [drm] Default TV standard: NTSC
[    8.056485] [drm] 27.000000000 MHz TV ref clk
[    8.056489] [drm] Default TV standard: NTSC
[    8.056491] [drm] 27.000000000 MHz TV ref clk
[    8.056654] [drm] Radeon Display Connectors
[    8.056657] [drm] Connector 0:
[    8.056660] [drm]   VGA
[    8.056664] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    8.056666] [drm]   Encoders:
[    8.056669] [drm]     CRT1: INTERNAL_DAC1
[    8.056671] [drm] Connector 1:
[    8.056673] [drm]   DVI-D
[    8.056675] [drm]   HPD1
[    8.056679] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    8.056681] [drm]   Encoders:
[    8.056683] [drm]     DFP1: INTERNAL_TMDS1
[    8.056686] [drm] Connector 2:
[    8.056688] [drm]   LVDS
[    8.056690] [drm]   Encoders:
[    8.056692] [drm]     LCD1: INTERNAL_LVDS
[    8.056694] [drm] Connector 3:
[    8.056696] [drm]   S-video
[    8.056698] [drm]   Encoders:
[    8.056701] [drm]     TV1: INTERNAL_DAC2
[    8.087310] [drm] fb mappable at 0xE0040000
[    8.087314] [drm] vram apper at 0xE0000000
[    8.087316] [drm] size 786432
[    8.087318] [drm] fb depth is 8
[    8.087321] [drm]    pitch is 1024
[    8.087742] fb0: radeondrmfb frame buffer device
[    8.087745] registered panic notifier
[    8.087753] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[    8.608492] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[    8.608496] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[    8.608500] thinkpad_acpi: ThinkPad BIOS 1RETDRWW (3.23 ), EC 1RHT68WW-3.01a
[    8.608504] thinkpad_acpi: IBM ThinkPad T41 , model 2378DHU
[    8.608507] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
[    8.608510] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
[    8.617500] vga16fb: initializing
[    8.617507] vga16fb: mapped to 0xc00a0000
[    8.617514] vga16fb: not registering due to another framebuffer present
[    8.643205] Registered led device: tpacpi::thinklight
[    8.643545] Registered led device: tpacpi::power
[    8.644447] Registered led device: tpacpi::standby
[    8.652924] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[    8.668537] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[    9.039240] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    9.039280] Intel ICH 0000:00:1f.5: setting latency timer to 64
[    9.542944] Console: switching to colour frame buffer device 128x48
[    9.964052] intel8x0_measure_ac97_clock: measured 55370 usecs (2668 samples)
[    9.964057] intel8x0: clocking to 48000
[   10.199320] psmouse serio2: ID: 10 00 64
[   10.685130] RX DESC d6ab5000  size = 2048
[   10.685536] <-- RTMPAllocTxRxRingMemory, Status=0
[   10.689581] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   10.689587] 1. Phy Mode = 0
[   10.689590] 2. Phy Mode = 0
[   10.706659] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   10.711760] 3. Phy Mode = 0
[   10.734335] MCS Set = 00 00 00 00 00
[   10.735926] <==== RTMPInitialize, Status=0
[   10.735995] 0x1300 = 00073200
[   10.741275] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.295046] type=1505 audit(1272815051.395:5):  operation="profile_load" pid=822 name="/usr/share/gdm/guest-session/Xsession"
[   12.301771] type=1505 audit(1272815051.403:6):  operation="profile_replace" pid=865 name="/sbin/dhclient3"
[   12.302643] type=1505 audit(1272815051.403:7):  operation="profile_replace" pid=865 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.303127] type=1505 audit(1272815051.403:8):  operation="profile_replace" pid=865 name="/usr/lib/connman/scripts/dhclient-script"
[   12.449209] type=1505 audit(1272815051.551:9):  operation="profile_load" pid=866 name="/usr/bin/evince"
[   12.477868] type=1505 audit(1272815051.579:10):  operation="profile_load" pid=866 name="/usr/bin/evince-previewer"
[   12.496058] type=1505 audit(1272815051.595:11):  operation="profile_load" pid=866 name="/usr/bin/evince-thumbnailer"
[   12.562570] type=1505 audit(1272815051.663:12):  operation="profile_load" pid=919 name="/usr/lib/cups/backend/cups-pdf"
[   12.563629] type=1505 audit(1272815051.663:13):  operation="profile_load" pid=919 name="/usr/sbin/cupsd"
[   12.585085] type=1505 audit(1272815051.687:14):  operation="profile_load" pid=929 name="/usr/sbin/tcpdump"
[   15.946941] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   16.290555] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[   17.552109] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 281
[   20.868030] wlan0: no IPv6 routers present
[   20.940038] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[   37.907887] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 287
[   42.682813] end_request: I/O error, dev fd0, sector 0
[   56.353338] end_request: I/O error, dev fd0, sector 0
[   67.913661] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 343
[   69.792584] end_request: I/O error, dev fd0, sector 0
[   77.924497] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 474
[   77.926379] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   83.080158] end_request: I/O error, dev fd0, sector 0
[   83.080170] Buffer I/O error on device fd0, logical block 0
[   90.340057] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[   95.349713] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 281
[   95.352281] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   96.158505] end_request: I/O error, dev fd0, sector 0
[   96.158522] Buffer I/O error on device fd0, logical block 0
[  107.440053] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  109.321923] end_request: I/O error, dev fd0, sector 0
[  109.321941] Buffer I/O error on device fd0, logical block 0
[  112.450258] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 282
[  112.452229] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  122.496097] end_request: I/O error, dev fd0, sector 0
[  122.496115] Buffer I/O error on device fd0, logical block 0
[  124.644056] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  129.655415] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 178
[  129.656896] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  131.904045] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  135.678830] end_request: I/O error, dev fd0, sector 0
[  135.678847] Buffer I/O error on device fd0, logical block 0
[  139.862596] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 178
[  139.863028] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  148.914556] end_request: I/O error, dev fd0, sector 0
[  148.914573] Buffer I/O error on device fd0, logical block 0
[  152.088050] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  157.098197] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 696
[  157.100258] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  162.173929] end_request: I/O error, dev fd0, sector 0
[  162.173946] Buffer I/O error on device fd0, logical block 0
[  169.192041] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  174.199183] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 456
[  174.201438] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  175.401334] end_request: I/O error, dev fd0, sector 0
[  175.401352] Buffer I/O error on device fd0, logical block 0
[  186.500049] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  188.748072] end_request: I/O error, dev fd0, sector 0
[  188.748089] Buffer I/O error on device fd0, logical block 0
===========================================================================================================================
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:b2:a7:a7
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8000(size=64) memory:c0210000-c021ffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1c:df:8e:17:0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:11 memory:c4000000-c400ffff
===========================================================================================================================
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:69:D9:F8
                    Protocol:802.11b/g/n
                    ESSID:"liles-at-home"
                    Mode:Managed
                    Channel:3
                    Quality:10/100  Signal level:-86 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
          Cell 02 - Address: 00:13:46:BF:A9:26
                    Protocol:802.11b/g
                    ESSID:"dlinkpmh"
                    Mode:Managed
                    Channel:6
                    Quality:5/100  Signal level:-88 dBm  Noise level:-97 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s
          Cell 03 - Address: 00:14:6C:DD:92:C4
                    Protocol:802.11b/g
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Channel:6
                    Quality:10/100  Signal level:-86 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:22:6B:5D:89:10
                    Protocol:802.11b/g/n
                    ESSID:"lannonhome"
                    Mode:Managed
                    Channel:11
                    Quality:100/100  Signal level:-33 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
============================================================================================================================
lsb_release -d
Description:    Ubuntu 10.04 LTS
============================================================================================================================
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                [ OK ]

---

