---
title: "Trouble with Atheros AR928x"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by meekrakkin on 2010-05-17
Hello, I am a very new ubuntu user and new to linux as well. I am using the Ubuntu Studio 10.04 distribution and cannot get my wireless network card to work at all. 

Here is the information you requested in the "How to" thread... some of the "hints" didn't generate any response at all for me so I included the longer versions...

any help with this would be greatly appreciated...

Thanks,
Michael

1. Gateway NV-73 Laptop

2. Atheros AR928X Wireless Network Adapter (PCI Express)

3. $ iwconfig wlan0
    wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

4. $ lsmod
    Module                  Size  Used by
    binfmt_misc             7960  1 
    ppdev                   6375  0 
    snd_hda_codec_atihdmi     3023  1 
    snd_hda_codec_realtek   278890  1 
    fbcon                  39270  71 
    tileblit                2487  1 fbcon
    font                    8053  1 fbcon
    bitblit                 5811  1 fbcon
    softcursor              1565  1 bitblit
    snd_hda_intel          25645  2 
    snd_hda_codec          85727  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
    vga16fb                12757  0 
    snd_hwdep               6924  1 snd_hda_codec
    arc4                    1473  2 
    vgastate                9857  1 vga16fb
    joydev                 11072  0 
    snd_pcm_oss            41394  0 
    snd_mixer_oss          16299  1 snd_pcm_oss
    snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
    snd_seq_dummy           1782  0 
    snd_seq_oss            31219  0 
    snd_seq_midi            5829  0 
    snd_rawmidi            23388  1 snd_seq_midi
    snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
    snd_seq                57417  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
    snd_timer              23553  2 snd_pcm,snd_seq
    ath9k                  76155  0 
    snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
    uvcvideo               62403  0 
    ath9k_common            3071  1 ath9k
    videodev               40486  1 uvcvideo
    radeon                739595  2 
    ttm                    60815  1 radeon
    snd                    70978  17       snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
    mac80211              243373  2 ath9k,ath9k_common
    v4l1_compat            15495  2 uvcvideo,videodev
    drm_kms_helper         30742  1 radeon
    v4l2_compat_ioctl32    12020  1 videodev
    drm                   198770  4 radeon,ttm,drm_kms_helper
    i2c_algo_bit            6024  1 radeon
    soundcore               8052  1 snd
    edac_core              45423  0 
    ath9k_hw              239668  2 ath9k,ath9k_common
    psmouse                64608  0 
    snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
    i2c_piix4               9639  0 
    edac_mce_amd            9214  0 
    serio_raw               4918  0 
    shpchp                 33679  0 
    ath                    10345  2 ath9k,ath9k_hw
    ndiswrapper           244768  0 
    cfg80211              152987  4 ath9k,ath9k_common,mac80211,ath
    led_class               3732  1 ath9k
    video                  20623  0 
    output                  2503  1 video
    lp                      9336  0 
    parport                37160  2 ppdev,lp
    tg3                   122350  0 
   ahci                   37646  2 

5. [    0.503121] pci 0000:02:00.0: reg 10 64bit mmio: [0xf0100000-0xf010ffff]
[    0.503171] pci 0000:02:00.0: supports D1
[    0.503173] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.503178] pci 0000:02:00.0: PME# disabled
[    0.503272] pci 0000:00:06.0: bridge 32bit mmio: [0xf0100000-0xf01fffff]
[    0.503326] pci 0000:03:00.0: reg 10 64bit mmio: [0xf0000000-0xf000ffff]
[    0.503386] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.503390] pci 0000:03:00.0: PME# disabled
[    0.503481] pci 0000:00:07.0: bridge 32bit mmio: [0xf0000000-0xf00fffff]
[    0.503542] pci 0000:00:14.4: transparent bridge
[    0.503566] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.503703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.503800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.503882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.504012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.514474] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.514683] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.514834] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.514973] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.515126] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.515297] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.515502] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.515706] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.515863] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.515867] vgaarb: loaded
[    0.515970] SCSI subsystem initialized
[    0.516056] libata version 3.00 loaded.
[    0.516115] usbcore: registered new interface driver usbfs
[    0.516126] usbcore: registered new interface driver hub
[    0.516149] usbcore: registered new device driver usb
[    0.516317] ACPI: WMI: Mapper loaded
[    0.516319] PCI: Using ACPI for IRQ routing
[    0.516594] NetLabel: Initializing
[    0.516596] NetLabel:  domain hash size = 128
[    0.516598] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.516609] NetLabel:  unlabeled traffic allowed by default
[    0.516683] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.516688] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.518698] Switching to clocksource tsc
[    0.519014] AppArmor: AppArmor Filesystem Enabled
[    0.519014] pnp: PnP ACPI init
[    0.519014] ACPI: bus type pnp registered
[    0.539188] Freeing initrd memory: 8957k freed
[    0.581125] pnp: PnP ACPI: found 10 devices
[    0.581129] ACPI: ACPI bus type pnp unregistered
[    0.581150] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.581153] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.581156] system 00:01: iomem range 0xf7000000-0xf7ffffff has been reserved
[    0.581166] system 00:08: ioport range 0x400-0x4cf has been reserved
[    0.581168] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.581171] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.581173] system 00:08: ioport range 0x680-0x6ff has been reserved
[    0.581176] system 00:08: ioport range 0x77a-0x77a has been reserved
[    0.581178] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.581180] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.581183] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.581185] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.581187] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.581190] system 00:08: ioport range 0xcd0-0xcdb has been reserved
[    0.581196] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.581198] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
[    0.586113] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.586115] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.586119] pci 0000:00:01.0:   MEM window: 0xf0200000-0xf03fffff
[    0.586122] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.586127] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.586128] pci 0000:00:06.0:   IO window: disabled
[    0.586132] pci 0000:00:06.0:   MEM window: 0xf0100000-0xf01fffff
[    0.586134] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.586138] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.586140] pci 0000:00:07.0:   IO window: disabled
[    0.586143] pci 0000:00:07.0:   MEM window: 0xf0000000-0xf00fffff
[    0.586145] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.586149] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
[    0.586150] pci 0000:00:14.4:   IO window: disabled
[    0.586155] pci 0000:00:14.4:   MEM window: disabled
[    0.586159] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.586170] pci 0000:00:01.0: setting latency timer to 64
[    0.586177]   alloc irq_desc for 18 on node 0
[    0.586179]   alloc kstat_irqs on node 0
[    0.586185] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.586188] pci 0000:00:06.0: setting latency timer to 64
[    0.586193]   alloc irq_desc for 19 on node 0
[    0.586195]   alloc kstat_irqs on node 0
[    0.586198] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.586201] pci 0000:00:07.0: setting latency timer to 64
[    0.586209] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.586212] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.586215] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.586217] pci_bus 0000:01: resource 1 mem: [0xf0200000-0xf03fffff]
[    0.586219] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.586222] pci_bus 0000:02: resource 1 mem: [0xf0100000-0xf01fffff]
[    0.586224] pci_bus 0000:03: resource 1 mem: [0xf0000000-0xf00fffff]
[    0.586227] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.586229] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.586267] NET: Registered protocol family 2
[    0.586426] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.587531] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.590405] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.590758] TCP: Hash tables configured (established 524288 bind 65536)
[    0.590761] TCP reno registered
[    0.590856] NET: Registered protocol family 1
[    0.751132] pci 0000:01:05.0: Boot video device
[    0.751296] PCI-DMA: Disabling AGP.
[    0.751389] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.751391] PCI-DMA: using GART IOMMU.
[    0.751394] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.752644] Simple Boot Flag at 0x44 set to 0x1
[    0.752837] Scanning for low memory corruption every 60 seconds
[    0.752966] audit: initializing netlink socket (disabled)
[    0.752977] type=2000 audit(1274113711.751:1): initialized
[    0.761754] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.763026] VFS: Disk quotas dquot_6.5.2
[    0.763077] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.763675] fuse init (API version 7.13)
[    0.763752] msgmni has been set to 7414
[    0.763994] alg: No test for stdrng (krng)
[    0.764047] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.764050] io scheduler noop registered
[    0.764052] io scheduler anticipatory registered
[    0.764054] io scheduler deadline registered
[    0.764089] io scheduler cfq registered (default)
[    0.764308]   alloc irq_desc for 25 on node 0
[    0.764310]   alloc kstat_irqs on node 0
[    0.764318] pcieport 0000:00:06.0: irq 25 for MSI/MSI-X
[    0.764324] pcieport 0000:00:06.0: setting latency timer to 64
[    0.764444]   alloc irq_desc for 26 on node 0
[    0.764446]   alloc kstat_irqs on node 0
[    0.764451] pcieport 0000:00:07.0: irq 26 for MSI/MSI-X
[    0.764455] pcieport 0000:00:07.0: setting latency timer to 64
[    0.764521] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.764542] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.771322] ACPI: AC Adapter [ACAD] (on-line)
[    0.771404] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.771408] ACPI: Power Button [PWRB]
[    0.771442] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.771445] ACPI: Sleep Button [SLPB]
[    0.771498] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.771589] ACPI: Lid Switch [LID]
[    0.771622] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.771625] ACPI: Power Button [PWRF]
[    0.771994] ACPI: processor limited to max C-state 1
[    0.772019] processor LNXCPU:00: registered as cooling_device0
[    0.772160] processor LNXCPU:01: registered as cooling_device1
[    0.861385] ACPI: Invalid active0 threshold
[    0.871209] thermal LNXTHERM:01: registered as thermal_zone0
[    0.871219] ACPI: Thermal Zone [THR0] (61 C)
[    0.872363] Linux agpgart interface v0.103
[    0.872396] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.873469] brd: module loaded
[    0.873876] loop: module loaded
[    0.873959] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.874323] Fixed MDIO Bus: probed
[    0.874354] PPP generic driver version 2.4.2
[    0.874381] tun: Universal TUN/TAP device driver, 1.6
[    0.874383] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.874454] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.874564]   alloc irq_desc for 17 on node 0
[    0.874567]   alloc kstat_irqs on node 0
[    0.874573] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.874596] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    0.874600] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.874631] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.874670] ehci_hcd 0000:00:12.2: debug port 1
[    0.874691] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf0408500
[    0.891129] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.891248] usb usb1: configuration #1 chosen from 1 choice
[    0.891274] hub 1-0:1.0: USB hub found
[    0.891282] hub 1-0:1.0: 6 ports detected
[    0.891428] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.891450] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    0.891453] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.891491] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.891523] ehci_hcd 0000:00:13.2: debug port 1
[    0.891545] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf0408400
[    0.911209] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.911316] usb usb2: configuration #1 chosen from 1 choice
[    0.911353] hub 2-0:1.0: USB hub found
[    0.911361] hub 2-0:1.0: 6 ports detected
[    0.911440] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.911515]   alloc irq_desc for 16 on node 0
[    0.911518]   alloc kstat_irqs on node 0
[    0.911524] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.911548] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    0.911552] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.911586] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.911615] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf0407000
[    0.975260] usb usb3: configuration #1 chosen from 1 choice
[    0.975292] hub 3-0:1.0: USB hub found
[    0.975336] hub 3-0:1.0: 3 ports detected
[    0.975474] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.975497] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    0.975500] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.975537] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.975558] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf0406000
[    1.035308] usb usb4: configuration #1 chosen from 1 choice
[    1.035336] hub 4-0:1.0: USB hub found
[    1.035379] hub 4-0:1.0: 3 ports detected
[    1.035518] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.035542] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    1.035546] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.035581] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.035611] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf0405000
[    1.094290] usb usb5: configuration #1 chosen from 1 choice
[    1.094318] hub 5-0:1.0: USB hub found
[    1.094361] hub 5-0:1.0: 3 ports detected
[    1.094517] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.094541] ohci_hcd 0000:00:14.5: setting latency timer to 64
[    1.094544] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.094585] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.094606] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf0404000
[    1.154279] usb usb6: configuration #1 chosen from 1 choice
[    1.154307] hub 6-0:1.0: USB hub found
[    1.154351] hub 6-0:1.0: 2 ports detected
[    1.154414] uhci_hcd: USB Universal Host Controller Interface driver
[    1.154486] PNP: PS/2 Controller [PNP0303:KBCU,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.205734] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.205739] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.205850] mice: PS/2 mouse device common for all mice
[    1.207664] rtc_cmos 00:04: RTC can wake from S4
[    1.207698] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.207722] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.207833] device-mapper: uevent: version 1.0.3
[    1.207978] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.208030] device-mapper: multipath: version 1.1.0 loaded
[    1.208032] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.208200] cpuidle: using governor ladder
[    1.208202] cpuidle: using governor menu
[    1.208532] TCP cubic registered
[    1.208642] NET: Registered protocol family 10
[    1.209057] lo: Disabled Privacy Extensions
[    1.209318] NET: Registered protocol family 17
[    1.209367] powernow-k8: Found 1 AMD Athlon(tm) II Dual-Core M300 processors (2 cpu cores) (version 2.20.00)
[    1.209408] powernow-k8:    0 : pstate 0 (2000 MHz)
[    1.209410] powernow-k8:    1 : pstate 1 (1400 MHz)
[    1.209412] powernow-k8:    2 : pstate 2 (800 MHz)
[    1.209668] PM: Resume from disk failed.
[    1.209679] registered taskstats version 1
[    1.210019]   Magic number: 10:892:489
[    1.210121] rtc_cmos 00:04: setting system clock to 2010-05-17 16:28:32 UTC (1274113712)
[    1.210128] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.210134] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.210136] EDD information not available.
[    1.210208] Freeing unused kernel memory: 876k freed
[    1.210490] Write protecting the kernel read-only data: 7680k
[    1.232582] udev: starting version 151
[    1.263350] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.322318] ahci 0000:00:11.0: version 3.0
[    1.322367]   alloc irq_desc for 22 on node 0
[    1.322370]   alloc kstat_irqs on node 0
[    1.322377] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.322434]   alloc irq_desc for 27 on node 0
[    1.322436]   alloc kstat_irqs on node 0
[    1.322446] ahci 0000:00:11.0: irq 27 for MSI/MSI-X
[    1.322525] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0xd impl SATA mode
[    1.322530] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc sxs 
[    1.349835] scsi0 : ahci
[    1.364100] tg3.c:v3.102 (September 1, 2009)
[    1.364120] tg3 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.364130] tg3 0000:03:00.0: setting latency timer to 64
[    1.373220] scsi1 : ahci
[    1.380352] scsi2 : ahci
[    1.380512] scsi3 : ahci
[    1.380645] ata1: SATA max UDMA/133 abar m1024@0xf0408000 port 0xf0408100 irq 27
[    1.380648] ata2: DUMMY
[    1.380651] ata3: SATA max UDMA/133 abar m1024@0xf0408000 port 0xf0408200 irq 27
[    1.380654] ata4: SATA max UDMA/133 abar m1024@0xf0408000 port 0xf0408280 irq 27
[    1.400348] usb 1-4: configuration #1 chosen from 1 choice
[    1.690250] ACPI: Battery Slot [BAT1] (battery present)
[    1.730124] ata4: SATA link down (SStatus 0 SControl 300)
[    1.910119] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.910150] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.924593] ata3.00: ATAPI: TSSTcorp CDDVDW TS-L633C, AC01, max UDMA/100, ATAPI AN
[    1.924607] ata3.00: applying bridge limits
[    1.941042] ata3.00: configured for UDMA/100
[    1.961676] ata1.00: ATA-8: WDC WD2500BEVT-22ZCT0, 11.01A11, max UDMA/133
[    1.961680] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.963894] ata1.00: configured for UDMA/133
[    1.980204] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-2 11.0 PQ: 0 ANSI: 5
[    1.980385] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.980506] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.980549] sd 0:0:0:0: [sda] Write Protect is off
[    1.980552] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.980571] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.980712]  sda:
[    1.984158] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633C  AC01 PQ: 0 ANSI: 5
[    1.990618]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.998427] Uniform CD-ROM driver Revision: 3.20
[    1.998570] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.998632] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.002340]  sda5 >
[    2.002675] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.473819] EXT4-fs (dm-0): mounted filesystem with ordered data mode
[    2.671322] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:26:22:87:7b:0d
[    2.671326] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.671329] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.671331] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   11.098599] Adding 9924600k swap on /dev/mapper/Studio-swap_1.  Priority:-1 extents:1 across:9924600k 
[   11.129492] udev: starting version 151
[   11.361468] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   11.380804] acpi device:01: registered as cooling_device2
[   11.381239] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6
[   11.381418] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.388272] lp: driver loaded but no devices found
[   11.546691] cfg80211: Calling CRDA to update world regulatory domain
[   11.603207] Disabling lock debugging due to kernel taint
[   11.609889] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   11.671816]   alloc irq_desc for 28 on node 0
[   11.671820]   alloc kstat_irqs on node 0
[   11.671833] tg3 0000:03:00.0: irq 28 for MSI/MSI-X
[   11.779236] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.946875] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.953664] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.967480] type=1505 audit(1274113723.253:2):  operation="profile_load" pid=704 name="/sbin/dhclient3"
[   11.967756] type=1505 audit(1274113723.253:3):  operation="profile_load" pid=704 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.967910] type=1505 audit(1274113723.253:4):  operation="profile_load" pid=704 name="/usr/lib/connman/scripts/dhclient-script"
[   11.991819] usbcore: registered new interface driver ndiswrapper
[   12.185178] EDAC MC: Ver: 2.1.0 Apr 28 2010
[   12.281429] [drm] Initialized drm 1.1.0 20060810
[   12.336415] cfg80211: World regulatory domain updated:
[   12.336419]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.336422]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.336425]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.336427]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.336429]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.336432]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.465658] EDAC amd64_edac:  Ver: 3.2.0 Apr 28 2010
[   12.465734] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   12.465743] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   12.465745]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   12.465746]  (Note that use of the override may cause unknown side effects.)
[   12.465936] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   12.601351] [drm] radeon defaulting to kernel modesetting.
[   12.601355] [drm] radeon kernel modesetting enabled.
[   12.601513] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.601517] radeon 0000:01:05.0: setting latency timer to 64
[   12.603561] [drm] radeon: Initializing kernel modesetting.
[   12.606903] [drm] register mmio base: 0xF0300000
[   12.606905] [drm] register mmio size: 65536
[   12.607701] ATOM BIOS: Acer_SJV70TR
[   12.607715] [drm] Clocks initialized !
[   12.607883] [drm] Detected VRAM RAM=256M, BAR=256M
[   12.607888] [drm] RAM width 32bits DDR
[   12.607995] [TTM] Zone  kernel: Available graphics memory: 1898584 kiB.
[   12.608012] [drm] radeon: 256M of VRAM memory ready
[   12.608013] [drm] radeon: 512M of GTT memory ready.
[   12.608049] [drm] radeon: irq initialized.
[   12.608052] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   12.608700] [drm] Loading RS780 Microcode
[   12.608801] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin
[   12.615742] Linux video capture interface: v2.00
[   12.656868] uvcvideo: Found UVC 1.00 device Video WebCam (064e:a103)
[   12.673336] input: Video WebCam as /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/input/input7
[   12.673403] usbcore: registered new interface driver uvcvideo
[   12.673407] USB Video Class driver (v0.1.0)
[   12.674899] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin
[   12.686735] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
[   12.722868] ath9k 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.722878] ath9k 0000:02:00.0: setting latency timer to 64
[   13.151671] ath: EEPROM regdomain: 0x65
[   13.151673] ath: EEPROM indicates we should expect a direct regpair map
[   13.151677] ath: Country alpha2 being used: 00
[   13.151678] ath: Regpair used: 0x65
[   13.151701] [drm] ring test succeeded in 0 usecs
[   13.151796] [drm] radeon: ib pool ready.
[   13.151860] [drm] ib test succeeded in 0 usecs
[   13.151863] [drm] Enabling audio support
[   13.152046] [drm] Radeon Display Connectors
[   13.152048] [drm] Connector 0:
[   13.152049] [drm]   VGA
[   13.152052] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   13.152054] [drm]   Encoders:
[   13.152055] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.152057] [drm] Connector 1:
[   13.152058] [drm]   LVDS
[   13.152060] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   13.152061] [drm]   Encoders:
[   13.152063] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[   13.152064] [drm] Connector 2:
[   13.152066] [drm]   HDMI-A
[   13.152067] [drm]   HPD1
[   13.152069] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[   13.152070] [drm]   Encoders:
[   13.152072] [drm]     DFP1: INTERNAL_UNIPHY
[   13.344345] [drm] fb mappable at 0xE0141000
[   13.344349] [drm] vram apper at 0xE0000000
[   13.344351] [drm] size 5760000
[   13.344352] [drm] fb depth is 24
[   13.344354] [drm]    pitch is 6400
[   13.344516] fb0: radeondrmfb frame buffer device
[   13.344518] registered panic notifier
[   13.344524] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   13.357626] type=1505 audit(1274113724.639:5):  operation="profile_load" pid=934 name="/usr/share/gdm/guest-session/Xsession"
[   13.359347] type=1505 audit(1274113724.639:6):  operation="profile_replace" pid=935 name="/sbin/dhclient3"
[   13.359632] type=1505 audit(1274113724.639:7):  operation="profile_replace" pid=935 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.359789] type=1505 audit(1274113724.639:8):  operation="profile_replace" pid=935 name="/usr/lib/connman/scripts/dhclient-script"
[   13.362800] type=1505 audit(1274113724.649:9):  operation="profile_load" pid=936 name="/usr/bin/evince"
[   13.366288] type=1505 audit(1274113724.649:10):  operation="profile_load" pid=936 name="/usr/bin/evince-previewer"
[   13.368503] type=1505 audit(1274113724.649:11):  operation="profile_load" pid=936 name="/usr/bin/evince-thumbnailer"
[   13.369662] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa44000
[   13.536616] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   13.711883] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.712524] Registered led device: ath9k-phy0::radio
[   13.712541] Registered led device: ath9k-phy0::assoc
[   13.712555] Registered led device: ath9k-phy0::tx
[   13.712568] Registered led device: ath9k-phy0::rx
[   13.712581] phy0: Atheros AR9280 Rev:2 mem=0xffffc90002200000, irq=18
[   13.713645] vga16fb: initializing
[   13.713653] vga16fb: mapped to 0xffff8800000a0000
[   13.713659] vga16fb: not registering due to another framebuffer present
[   13.812962] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.813066] HDA Intel 0000:00:14.2: setting latency timer to 64
[   14.146096] hda_codec: ALC272: BIOS auto-probing.
[   14.147539] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
[   14.159274] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   14.159336] HDA Intel 0000:01:05.1: setting latency timer to 64
[   14.815468] Console: switching to colour frame buffer device 200x56
[   14.861829] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[   14.861833] tg3: eth0: Flow control is on for TX and on for RX.
[   14.862324] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.242901] ppdev: user-space parallel port driver
[   15.532630] CPU0 attaching NULL sched-domain.
[   15.532638] CPU1 attaching NULL sched-domain.
[   15.590166] CPU0 attaching sched-domain:
[   15.590171]  domain 0: span 0-1 level MC
[   15.590174]   groups: 0 1
[   15.590180] CPU1 attaching sched-domain:
[   15.590182]  domain 0: span 0-1 level MC
[   15.590184]   groups: 1 0
[   17.495397] CPU0 attaching NULL sched-domain.
[   17.495408] CPU1 attaching NULL sched-domain.
[   17.551366] CPU0 attaching sched-domain:
[   17.551371]  domain 0: span 0-1 level MC
[   17.551374]   groups: 0 1
[   17.551380] CPU1 attaching sched-domain:
[   17.551382]  domain 0: span 0-1 level MC
[   17.551384]   groups: 1 0
[   17.756556] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   25.840046] eth0: no IPv6 routers present
michael@Studio:~$ 

6. michael@Studio:~$ sudo lshw -c network
[sudo] password for michael: 
  *-network DISABLED      
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 70:1a:04:4f:0c:23
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.32-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:26:22:87:7b:0d
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 ip=192.168.1.130 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:28 memory:f0000000-f000ffff

7. michael@Studio:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

michael@Studio:~$ 

8. michael@Studio:~$ lsb_release -d
Description:    Ubuntu 10.04 LTS

9. michael@Studio:~$ uname -mr
2.6.32-22-generic x86_64

10. michael@Studio:~$ sudo /etc/init.d/networking restart
[sudo] password for michael: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1573
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:26:22:87:7b:0d
Sending on   LPF/eth0/00:26:22:87:7b:0d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:26:22:87:7b:0d
Sending on   LPF/eth0/00:26:22:87:7b:0d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.130 from 192.168.1.1
DHCPREQUEST of 192.168.1.130 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.130 from 192.168.1.1
bound to 192.168.1.130 -- renewal in 41838 seconds.
                                                                         [ OK ]

---

### Post by teh_drizzle on 2010-05-17
Hey,

I'm not familiar with the wireless card you have, nor wireless in general. :(

But did you see this post: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286503](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286503)

---

