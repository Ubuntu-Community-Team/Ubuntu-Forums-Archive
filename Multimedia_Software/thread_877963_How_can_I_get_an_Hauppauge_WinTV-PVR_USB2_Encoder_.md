---
title: "How can I get an Hauppauge WinTV-PVR USB2 Encoder beginn to work"
date: 2008-08-02
forum: Multimedia Software
---

### Post by micsan on 2008-08-02
Hello,
is there anybody, who can give me some advice. Unfortunately i am an absolute beginner.
Regards micsan

---

### Post by xc3RnbFO8P on 2008-08-02
In Terminal:
> lsusb
show the output.

---

### Post by micsan on 2008-08-02
The result was:

"Bus 005 Device 003: ID 2040:2400 Hauppauge 
 Bus 005 Device 001: ID 0000:0000  
 Bus 004 Device 001: ID 0000:0000  
 Bus 003 Device 001: ID 0000:0000  
 Bus 002 Device 001: ID 0000:0000  
 Bus 001 Device 001: ID 0000:0000"
 :)

micsan

---

### Post by xc3RnbFO8P on 2008-08-02
And now show the output of **dmesg**.

---

### Post by micsan on 2008-08-02
> **Ringi said:**
> And now show the output of **dmesg**.
I can´t post the output of the terminal.
I got the message:

"The following errors occurred with your submission
1. You have included 10 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.
Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator."
I don´t understand, what I´ve done wrong.

micsan

---

### Post by xc3RnbFO8P on 2008-08-02
can you see this in dmesg:
**pvrusb2.ko**
**in warm state**
**firmware ???????.fw**
copy/paste that part.

---

### Post by micsan on 2008-08-02
> **Ringi said:**
> can you see this in dmesg:
**pvrusb2.ko**
**in warm state**
**firmware ???????.fw**
copy/paste that part.

main.c: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[ 1735.911853] /build/buildd/linux-2.6.24/drivers/media/video/pvrusb2/pvrusb2-main.c: Debug mask is 31 (0x1f)
[ 1736.933471] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
[ 1736.954119] usb 5-2: USB disconnect, address 2
[ 1737.163062] usb 5-2: new high speed USB device using ehci_hcd and address 3
[ 1737.299102] usb 5-2: configuration #1 chosen from 1 choice
[ 1737.415450] usb 5-2: reset high speed USB device using ehci_hcd and address 3
[ 1737.906256] cx25840 0-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[ 1737.939213] tuner 0-0043: chip found @ 0x86 (pvrusb2_a)
[ 1737.939284] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[ 1737.939292] tuner 0-0043: type set to tda9887
[ 1737.969544] tuner 0-0061: chip found @ 0xc2 (pvrusb2_a)
[ 1737.974785] wm8775 0-001b: chip found @ 0x36 (pvrusb2_a)
[ 1738.003120] tveeprom 0-00a2: Hauppauge model 24019, rev E189, serial# 8682138
[ 1738.003129] tveeprom 0-00a2: tuner model is TCL MFPE05 2 (idx 89, type 38)
[ 1738.003137] tveeprom 0-00a2: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[ 1738.003145] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[ 1738.003151] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[ 1738.003157] tveeprom 0-00a2: has radio, has IR receiver, has no IR transmitter
[ 1738.003170] pvrusb2: Supported video standard(s) reported by eeprom: PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K
[ 1738.003183] pvrusb2: Mapping standards mask=0xff00ff (PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K1/L/LC)
[ 1738.003191] pvrusb2: Setting up 20 unique standard(s)
[ 1738.003201] pvrusb2: Set up standard idx=0 name=PAL-B/G
[ 1738.003215] pvrusb2: Set up standard idx=1 name=PAL-D/K
[ 1738.003222] pvrusb2: Set up standard idx=2 name=SECAM-B/G
[ 1738.003230] pvrusb2: Set up standard idx=3 name=SECAM-D/K
[ 1738.003237] pvrusb2: Set up standard idx=4 name=PAL-B
[ 1738.003244] pvrusb2: Set up standard idx=5 name=PAL-B1
[ 1738.003251] pvrusb2: Set up standard idx=6 name=PAL-G
[ 1738.003257] pvrusb2: Set up standard idx=7 name=PAL-H
[ 1738.003264] pvrusb2: Set up standard idx=8 name=PAL-I
[ 1738.003271] pvrusb2: Set up standard idx=9 name=PAL-D
[ 1738.003278] pvrusb2: Set up standard idx=10 name=PAL-D1
[ 1738.003284] pvrusb2: Set up standard idx=11 name=PAL-K
[ 1738.003291] pvrusb2: Set up standard idx=12 name=SECAM-B
[ 1738.003298] pvrusb2: Set up standard idx=13 name=SECAM-D
[ 1738.003305] pvrusb2: Set up standard idx=14 name=SECAM-G
[ 1738.003312] pvrusb2: Set up standard idx=15 name=SECAM-H
[ 1738.003319] pvrusb2: Set up standard idx=16 name=SECAM-K
[ 1738.003325] pvrusb2: Set up standard idx=17 name=SECAM-K1
[ 1738.003332] pvrusb2: Set up standard idx=18 name=SECAM-L
[ 1738.003339] pvrusb2: Set up standard idx=19 name=SECAM-LC
[ 1738.003346] pvrusb2: Initial video standard auto-selected to PAL-B/G
[ 1740.208235] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[ 1740.394217] tuner-simple 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[ 1740.394233] tuner 0-0061: type set to Philips PAL/SECAM m
[ 1740.470988] cx25840 0-0044: Video signal:              not present
[ 1740.471000] cx25840 0-0044: Detected format:           NTSC-M
[ 1740.471005] cx25840 0-0044: Specified standard:        PAL-BDGHI
[ 1740.471010] cx25840 0-0044: Specified video input:     Composite 7
[ 1740.471016] cx25840 0-0044: Specified audioclock freq: 48000 Hz
[ 1740.478831] cx25840 0-0044: Detected audio mode:       forced mode
[ 1740.478842] cx25840 0-0044: Detected audio standard:   no detected audio standard
[ 1740.478848] cx25840 0-0044: Audio muted:               no
[ 1740.478856] cx25840 0-0044: Audio microcontroller:     detecting
[ 1740.478862] cx25840 0-0044: Configured audio standard: automatic detection
[ 1740.478868] cx25840 0-0044: Configured audio system:   automatic standard and mode detection
[ 1740.478874] cx25840 0-0044: Specified audio input:     Tuner (In8)
[ 1740.478881] cx25840 0-0044: Preferred audio mode:      stereo
[ 1740.478888] cx25840 0-0044: Selected 65 MHz format:    autodetect
[ 1740.478894] cx25840 0-0044: Selected 45 MHz format:    chroma
[ 1740.478903] tda9887 0-0043: Data bytes: b=0x14 c=0x6e e=0x49
[ 1740.478910] tuner 0-0061: Tuner mode:      analog TV
[ 1740.478916] tuner 0-0061: Frequency:       175.25 MHz
[ 1740.478922] tuner 0-0061: Standard:        0x00000005
[ 1740.478928] wm8775 0-001b: Input: 2
[ 1740.478944] pvrusb2: Device initialization completed successfully.
[ 1740.479029] pvrusb2: registered device video0 [mpeg]
[ 1740.479067] pvrusb2: registered device radio0 [mpeg]

---

### Post by micsan on 2008-08-02
[   24.762872] NET: Registered protocol family 8
[   24.762877] NET: Registered protocol family 20
[   24.763074] hpet clockevent registered
[   24.763084] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   24.763093] hpet0: 3 64-bit timers, 14318180 Hz
[   24.764158] AppArmor: AppArmor Filesystem Enabled
[   24.766610] Time: tsc clocksource has been installed.
[   24.782881] system 00:01: ioport range 0x164e-0x164f has been reserved
[   24.782888] system 00:01: ioport range 0x600-0x60f has been reserved
[   24.782895] system 00:01: ioport range 0x610-0x610 has been reserved
[   24.782901] system 00:01: ioport range 0x800-0x80f has been reserved
[   24.782907] system 00:01: ioport range 0x400-0x47f has been reserved
[   24.782914] system 00:01: ioport range 0x500-0x53f has been reserved
[   24.782920] system 00:01: ioport range 0x378-0x37f has been reserved
[   24.782926] system 00:01: ioport range 0x778-0x77f has been reserved
[   24.782934] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   24.782941] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   24.782949] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   24.782956] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   24.782963] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   24.782970] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   24.782977] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   24.813846] PCI: Bridge: 0000:00:1c.0
[   24.813853]   IO window: 5000-5fff
[   24.813862]   MEM window: 8b300000-8c2fffff
[   24.813870]   PREFETCH window: 84100000-850fffff
[   24.813880] PCI: Bridge: 0000:00:1c.1
[   24.813885]   IO window: 4000-4fff
[   24.813895]   MEM window: 8a200000-8b2fffff
[   24.813902]   PREFETCH window: 85100000-860fffff
[   24.813912] PCI: Bridge: 0000:00:1c.2
[   24.813917]   IO window: 3000-3fff
[   24.813926]   MEM window: 89200000-8a1fffff
[   24.813934]   PREFETCH window: 86100000-870fffff
[   24.813944] PCI: Bridge: 0000:00:1c.3
[   24.813949]   IO window: 2000-2fff
[   24.813958]   MEM window: 88100000-891fffff
[   24.813966]   PREFETCH window: 87100000-880fffff
[   24.813984] PCI: Bus 6, cardbus bridge: 0000:05:05.0
[   24.813989]   IO window: 00001000-000010ff
[   24.813997]   IO window: 00001400-000014ff
[   24.814006]   PREFETCH window: 68000000-6bffffff
[   24.814014]   MEM window: 6c000000-6fffffff
[   24.814022] PCI: Bridge: 0000:00:1e.0
[   24.814028]   IO window: 1000-1fff
[   24.814037]   MEM window: 82000000-840fffff
[   24.814045]   PREFETCH window: 80000000-81ffffff
[   24.814091] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.814104] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.814140] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   24.814151] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.814186] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   24.814197] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.814231] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   24.814242] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   24.814263] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.814288] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.814300] PCI: Setting latency timer of device 0000:05:05.0 to 64
[   24.814321] NET: Registered protocol family 2
[   24.850821] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.851265] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.852832] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.853613] TCP: Hash tables configured (established 131072 bind 65536)
[   24.853618] TCP reno registered
[   24.862973] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   25.266124] Switched to high resolution mode on CPU 1
[   25.617890]  it is
[   26.414947] Freeing initrd memory: 7462k freed
[   26.415209] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[   26.415215] Simple Boot Flag at 0x44 set to 0x1
[   26.416583] audit: initializing netlink socket (disabled)
[   26.416604] audit(1217692420.120:1): initialized
[   26.416993] highmem bounce pool size: 64 pages
[   26.421284] VFS: Disk quotas dquot_6.5.1
[   26.421443] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.421716] io scheduler noop registered
[   26.421721] io scheduler anticipatory registered
[   26.421725] io scheduler deadline registered
[   26.421749] io scheduler cfq registered (default)
[   26.421769] Boot video device is 0000:00:02.0
[   26.422214] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   26.422294] assign_interrupt_mode Found MSI capability
[   26.422362] Allocate Port Service[0000:00:1c.0:pcie00]
[   26.422437] Allocate Port Service[0000:00:1c.0:pcie02]
[   26.422604] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   26.422683] assign_interrupt_mode Found MSI capability
[   26.422746] Allocate Port Service[0000:00:1c.1:pcie00]
[   26.422820] Allocate Port Service[0000:00:1c.1:pcie02]
[   26.422982] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   26.423061] assign_interrupt_mode Found MSI capability
[   26.423123] Allocate Port Service[0000:00:1c.2:pcie00]
[   26.423198] Allocate Port Service[0000:00:1c.2:pcie02]
[   26.423362] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   26.423440] assign_interrupt_mode Found MSI capability
[   26.423504] Allocate Port Service[0000:00:1c.3:pcie00]
[   26.423576] Allocate Port Service[0000:00:1c.3:pcie02]
[   26.424089] isapnp: Scanning for PnP cards...
[   26.778596] isapnp: No Plug & Play device found
[   26.838369] Real Time Clock Driver v1.12ac
[   26.838582] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.841113] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.841255] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.841458] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[   26.846822] i8042.c: Detected active multiplexing controller, rev 1.1.
[   26.849571] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.849580] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   26.849586] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   26.849592] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   26.849598] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   26.871632] mice: PS/2 mouse device common for all mice
[   26.871872] EISA: Probing bus 0 at eisa.0
[   26.871883] Cannot allocate resource for EISA slot 1
[   26.871889] Cannot allocate resource for EISA slot 2
[   26.871894] Cannot allocate resource for EISA slot 3
[   26.871899] Cannot allocate resource for EISA slot 4
[   26.871904] Cannot allocate resource for EISA slot 5
[   26.871908] Cannot allocate resource for EISA slot 6
[   26.871925] EISA: Detected 0 cards.
[   26.871931] cpuidle: using governor ladder
[   26.871935] cpuidle: using governor menu
[   26.872101] NET: Registered protocol family 1
[   26.872150] Using IPI No-Shortcut mode
[   26.872202] registered taskstats version 1
[   26.872424]   Magic number: 4:92:891
[   26.872494]   hash matches device ptyy1
[   26.872558] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.872563] EDD information not available.
[   26.872847] Freeing unused kernel memory: 368k freed
[   26.876832] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   28.346944] fuse init (API version 7.9)
[   28.397214] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   28.397229] ACPI: Processor [CPU0] (supports 8 throttling states)
[   28.398028] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   28.398041] ACPI: Processor [CPU1] (supports 8 throttling states)
[   28.403703] ACPI: Thermal Zone [TZ0] (28 C)
[   29.200510] usbcore: registered new interface driver usbfs
[   29.200557] usbcore: registered new interface driver hub
[   29.214379] usbcore: registered new device driver usb
[   29.242618] tg3.c:v3.86 (November 9, 2007)
[   29.242663] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   29.242683] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   29.287630] USB Universal Host Controller Interface driver v3.0
[   29.323804] eth0: Tigon3 [partno(BCM95789) rev 4201 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:40:d0:9d:a6:25
[   29.323820] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   29.323827] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   29.323872] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 22 (level, low) -> IRQ 20
[   29.323902] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.323911] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.324235] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   29.324282] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006080
[   29.324552] usb usb1: configuration #1 chosen from 1 choice
[   29.324601] hub 1-0:1.0: USB hub found
[   29.324613] hub 1-0:1.0: 2 ports detected
[   29.371554] SCSI subsystem initialized
[   29.427895] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   29.427917] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.427925] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.427972] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   29.428020] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006060
[   29.428253] usb usb2: configuration #1 chosen from 1 choice
[   29.428303] hub 2-0:1.0: USB hub found
[   29.428314] hub 2-0:1.0: 2 ports detected
[   29.454819] libata version 3.00 loaded.
[   29.531945] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   29.531967] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.531975] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.532029] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   29.532077] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[   29.532303] usb usb3: configuration #1 chosen from 1 choice
[   29.532353] hub 3-0:1.0: USB hub found
[   29.532364] hub 3-0:1.0: 2 ports detected
[   29.635623] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[   29.635644] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   29.635652] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   29.635701] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   29.635748] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006020
[   29.635976] usb usb4: configuration #1 chosen from 1 choice
[   29.636031] hub 4-0:1.0: USB hub found
[   29.636043] hub 4-0:1.0: 2 ports detected
[   29.739694] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 22 (level, low) -> IRQ 20
[   29.739718] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.739726] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.739775] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   29.743710] ehci_hcd 0000:00:1d.7: debug port 1
[   29.743721] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   29.743733] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x8c444400
[   29.759275] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.759489] usb usb5: configuration #1 chosen from 1 choice
[   29.759542] hub 5-0:1.0: USB hub found
[   29.759554] hub 5-0:1.0: 8 ports detected
[   29.863503] ACPI: PCI Interrupt 0000:05:05.1[B] -> GSI 17 (level, low) -> IRQ 17
[   29.863518] PCI: Setting latency timer of device 0000:05:05.1 to 64
[   29.914882] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[84006000-840067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   29.915658] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   29.915717] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   29.915740] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   29.926567] ata_piix 0000:00:1f.2: version 2.12
[   29.926577] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   29.926608] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   29.926666] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   29.927417] scsi0 : ata_piix
[   29.927555] scsi1 : ata_piix
[   29.929367] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
[   29.929375] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
[   30.091359] ata1.00: ATA-7: FUJITSU MHV2080BH PL, 00000029, max UDMA/100
[   30.091369] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   30.107372] ata1.00: configured for UDMA/100
[   30.427010] ata2.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.20, max UDMA/33
[   30.598688] ata2.00: configured for UDMA/33
[   30.598983] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080B 0000 PQ: 0 ANSI: 5
[   30.601142] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.20 PQ: 0 ANSI: 5
[   30.621233] Driver 'sd' needs updating - please use bus_type methods
[   30.621385] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   30.621412] sd 0:0:0:0: [sda] Write Protect is off
[   30.621418] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.621456] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.621561] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   30.621585] sd 0:0:0:0: [sda] Write Protect is off
[   30.621591] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.621628] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.621636]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   30.705209]  sda1 sda2 sda3 sda4
[   30.736067] sd 0:0:0:0: [sda] Attached SCSI disk
[   30.747662] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   30.747703] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   30.749650] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   30.749658] Uniform CD-ROM driver Revision: 3.20
[   30.749747] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   30.754795] Clocksource tsc unstable (delta = -560020294 ns)
[   30.757784] Time: hpet clocksource has been installed.
[   31.122214] Attempting manual resume
[   31.122222] swsusp: Resume From Partition 8:4
[   31.122226] PM: Checking swsusp image.
[   31.122534] PM: Resume from disk failed.
[   31.179550] kjournald starting.  Commit interval 5 seconds
[   31.179591] EXT3-fs: mounted filesystem with ordered data mode.
[   45.694361] Linux agpgart interface v0.102
[   45.800906] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   45.850774] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.900782] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.049801] intel_rng: FWH not detected
[   46.158333] agpgart: Detected an Intel 945GM Chipset.
[   46.160576] agpgart: Detected 7932K stolen memory.
[   46.182418] agpgart: AGP aperture is 256M @ 0x70000000
[   46.313402] iTCO_vendor_support: vendor-support=0
[   46.356187] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   46.356335] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0460)
[   46.356395] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   46.465539] input: Power Button (FF) as /devices/virtual/input/input3
[   46.525064] ACPI: Power Button (FF) [PWRF]
[   46.525184] input: Lid Switch as /devices/virtual/input/input4
[   46.559744] ACPI: Lid Switch [LID0]
[   46.559872] input: Sleep Button (CM) as /devices/virtual/input/input5
[   46.611938] ACPI: Sleep Button (CM) [SLPB]
[   46.918978] ACPI: Battery Slot [BAT0] (battery present)
[   47.040390] ACPI: AC Adapter [AC] (off-line)
[   47.465002] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x92a0b1, caps: 0xa04713/0x200000
[   47.510378] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   47.731240] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   47.778200] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[   48.315158] ACPI: PCI Interrupt 0000:05:05.2[A] -> GSI 16 (level, low) -> IRQ 16
[   48.315176] PCI: Setting latency timer of device 0000:05:05.2 to 64
[   48.442358] Yenta: CardBus bridge found at 0000:05:05.0 [17ff:0600]
[   48.442389] Yenta: Enabling burst memory read transactions
[   48.442399] Yenta: Using CSCINT to route CSC interrupts to PCI
[   48.442403] Yenta: Routing CardBus interrupts to PCI
[   48.442414] Yenta TI: socket 0000:05:05.0, mfunc 0x01aa1b22, devctl 0x64
[   48.494378] sdhci: Secure Digital Host Controller Interface driver
[   48.494386] sdhci: Copyright(c) Pierre Ossman
[   48.534429] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   48.534439] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   48.674622] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   48.674630] Socket status: 30000006
[   48.674636] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
[   48.674645] pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[   48.674651] cs: IO port probe 0x1000-0x1fff: clean.
[   48.675173] pcmcia: parent PCI bridge Memory window: 0x82000000 - 0x840fffff
[   48.675180] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x81ffffff
[   48.689717] sdhci: SDHCI controller found at 0000:05:05.3 [104c:803c] (rev 0)
[   48.689750] ACPI: PCI Interrupt 0000:05:05.3[A] -> GSI 16 (level, low) -> IRQ 16
[   48.689842] mmc0: SDHCI at 0x84006800 irq 16 PIO
[   48.689958] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   48.689981] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   48.690013] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   49.185980] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 23 (level, low) -> IRQ 21
[   49.186020] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   49.217802] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   50.705735] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   50.706468] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   50.904951] udev: renamed network interface wlan0 to eth1
[   50.947844] cs: IO port probe 0x100-0x3af: clean.
[   50.950161] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   50.950792] cs: IO port probe 0x820-0x8ff: clean.
[   50.951660] cs: IO port probe 0xc00-0xcf7: clean.
[   50.952814] cs: IO port probe 0xa00-0xaff: clean.
[   51.102869] lp: driver loaded but no devices found
[   51.360239] Adding 1967952k swap on /dev/sda4.  Priority:-1 extents:1 across:1967952k
[   51.399892] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   51.400240] EXT3 FS on sda2, internal journal
[   51.849655] kjournald starting.  Commit interval 5 seconds
[   51.849680] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   51.850178] EXT3 FS on sda3, internal journal
[   51.850187] EXT3-fs: mounted filesystem with ordered data mode.
[   52.961366] ip_tables: (C) 2000-2006 Netfilter Core Team
[   54.010253] No dock devices found.
[   55.481463] ppdev: user-space parallel port driver
[   55.767489] audit(1217685251.444:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4971 profile="/usr/sbin/cupsd" namespace="default"
[   55.822565] apm: BIOS not found.
[   59.657765] [drm] Initialized drm 1.1.0 20060810
[   59.663961] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   59.663981] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   59.664110] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   59.688265] mtrr: type mismatch for 70000000,10000000 old: write-back new: write-combining
[   79.566716] NET: Registered protocol family 10
[   79.567470] lo: Disabled Privacy Extensions
[   79.568713] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   79.570089] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   86.966931] CPU0 attaching NULL sched-domain.
[   86.966944] CPU1 attaching NULL sched-domain.
[   86.982055] CPU0 attaching sched-domain:
[   86.982069]  domain 0: span 03
[   86.982073]   groups: 01 02
[   86.982080]   domain 1: span 03
[   86.982085]    groups: 03
[   86.982092] CPU1 attaching sched-domain:
[   86.982096]  domain 0: span 03
[   86.982100]   groups: 02 01
[   86.982107]   domain 1: span 03
[   86.982111]    groups: 03
[  101.888580] NET: Registered protocol family 17
[  102.421165] eth1: Initial auth_alg=0
[  102.421178] eth1: authenticate with AP 00:1e:8c:3e:07:d9
[  102.422437] eth1: RX authentication from 00:1e:8c:3e:07:d9 (alg=0 transaction=2 status=0)
[  102.422446] eth1: authenticated
[  102.422451] eth1: associate with AP 00:1e:8c:3e:07:d9
[  102.423930] eth1: RX AssocResp from 00:1e:8c:3e:07:d9 (capab=0x411 status=0 aid=1)
[  102.423936] eth1: associated
[  102.428094] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  104.037282] eth1: no IPv6 routers present
[  111.566437] eth1: no IPv6 routers present
[ 1091.593116] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[ 1091.593128] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[ 1091.594272] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[ 1091.594279] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[ 1091.695849] CPU0 attaching NULL sched-domain.
[ 1091.695861] CPU1 attaching NULL sched-domain.
[ 1091.699481] CPU0 attaching sched-domain:
[ 1091.699494]  domain 0: span 03
[ 1091.699498]   groups: 01 02
[ 1091.699506] CPU1 attaching sched-domain:
[ 1091.699510]  domain 0: span 03
[ 1091.699516]   groups: 02 01
[ 1735.554449] usb 5-2: new high speed USB device using ehci_hcd and address 2
[ 1735.691163] usb 5-2: configuration #1 chosen from 1 choice
[ 1735.886492] Linux video capture interface: v2.00
[ 1735.911841] usbcore: registered new interface driver pvrusb2
[ 1735.911849] /build/buildd/linux-2.6.24/drivers/media/video/pvrusb2/pvrusb2-main.c: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[ 1735.911853] /build/buildd/linux-2.6.24/drivers/media/video/pvrusb2/pvrusb2-

---

### Post by xc3RnbFO8P on 2008-08-02
Try this TV-viewer:
[http://ubuntuforums.org/showthread.php?t=763698]("http://ubuntuforums.org/showthread.php?t=763698")

---

