---
title: "Hauppauge HVR1100 and Realtek ALC883 problems"
date: 2009-10-31
forum: Multimedia Software
---

### Post by psd99 on 2009-10-31
Hi guys,

I've been using linux at work for a while more red hat. But today I've decided to jump on the ubuntu bandwagon. I've got 9.10 installed. But to make me want to keep it installed means I need to sort out my TV Card and the sound.

At one point I had the sound working - but then when trying to configure my TV card 
I've now lost sound - but only on media players. Sound still works fine on firefox.

I've checked alsa mixer definitely isn't muted.

My first concern is getting sound to work properly second is my TV card.
I know a little bit about linux so I thought I would leave my first post with a

dmesg
and 
lspci

dmesg:

> 
[    0.977233]   alloc kstat_irqs on node -1
[    0.977236] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.977244] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.977246] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.977275] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.981176] ehci_hcd 0000:00:1a.7: debug port 1
[    0.981181] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.981189] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf5fffc00
[    0.996005] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.996050] usb usb1: configuration #1 chosen from 1 choice
[    0.996069] hub 1-0:1.0: USB hub found
[    0.996073] hub 1-0:1.0: 6 ports detected
[    0.996113]   alloc irq_desc for 23 on node -1
[    0.996114]   alloc kstat_irqs on node -1
[    0.996119] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.996125] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.996127] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.996146] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.000035] ehci_hcd 0000:00:1d.7: debug port 1
[    1.000039] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.000048] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf5fff800
[    1.012006] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.012049] usb usb2: configuration #1 chosen from 1 choice
[    1.012067] hub 2-0:1.0: USB hub found
[    1.012071] hub 2-0:1.0: 6 ports detected
[    1.012108] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.012119] uhci_hcd: USB Universal Host Controller Interface driver
[    1.012133] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.012138] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.012140] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.012158] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.012176] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    1.012225] usb usb3: configuration #1 chosen from 1 choice
[    1.012241] hub 3-0:1.0: USB hub found
[    1.012245] hub 3-0:1.0: 2 ports detected
[    1.012274]   alloc irq_desc for 21 on node -1
[    1.012275]   alloc kstat_irqs on node -1
[    1.012278] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.012282] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.012284] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.012303] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.012327] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    1.012374] usb usb4: configuration #1 chosen from 1 choice
[    1.012390] hub 4-0:1.0: USB hub found
[    1.012396] hub 4-0:1.0: 2 ports detected
[    1.012427] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.012431] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.012433] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.012451] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.012469] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
[    1.012515] usb usb5: configuration #1 chosen from 1 choice
[    1.012531] hub 5-0:1.0: USB hub found
[    1.012535] hub 5-0:1.0: 2 ports detected
[    1.012564] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.012568] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.012571] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.012588] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.012606] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    1.012653] usb usb6: configuration #1 chosen from 1 choice
[    1.012672] hub 6-0:1.0: USB hub found
[    1.012676] hub 6-0:1.0: 2 ports detected
[    1.012704]   alloc irq_desc for 19 on node -1
[    1.012705]   alloc kstat_irqs on node -1
[    1.012707] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.012711] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.012713] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.012732] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.012755] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    1.012802] usb usb7: configuration #1 chosen from 1 choice
[    1.012818] hub 7-0:1.0: USB hub found
[    1.012821] hub 7-0:1.0: 2 ports detected
[    1.012849] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.012853] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.012855] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.012875] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.012892] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[    1.012938] usb usb8: configuration #1 chosen from 1 choice
[    1.012954] hub 8-0:1.0: USB hub found
[    1.012958] hub 8-0:1.0: 2 ports detected
[    1.013020] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.013021] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.013443] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.013487] mice: PS/2 mouse device common for all mice
[    1.013554] rtc_cmos 00:03: RTC can wake from S4
[    1.013574] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.013593] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.013655] device-mapper: uevent: version 1.0.3
[    1.013712] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.013792] device-mapper: multipath: version 1.1.0 loaded
[    1.013794] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.013866] EISA: Probing bus 0 at eisa.0
[    1.013887] EISA: Detected 0 cards.
[    1.013999] cpuidle: using governor ladder
[    1.014001] cpuidle: using governor menu
[    1.014303] TCP cubic registered
[    1.014400] NET: Registered protocol family 10
[    1.014687] lo: Disabled Privacy Extensions
[    1.014895] NET: Registered protocol family 17
[    1.014905] Bluetooth: L2CAP ver 2.13
[    1.014907] Bluetooth: L2CAP socket layer initialized
[    1.014908] Bluetooth: SCO (Voice Link) ver 0.6
[    1.014909] Bluetooth: SCO socket layer initialized
[    1.014930] Bluetooth: RFCOMM TTY layer initialized
[    1.014932] Bluetooth: RFCOMM socket layer initialized
[    1.014933] Bluetooth: RFCOMM ver 1.11
[    1.014964] Using IPI No-Shortcut mode
[    1.015003] PM: Resume from disk failed.
[    1.015011] registered taskstats version 1
[    1.015108]   Magic number: 13:858:884
[    1.015158] rtc_cmos 00:03: setting system clock to 2009-10-31 11:53:04 UTC (1256989984)
[    1.015160] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.015161] EDD information not available.
[    1.156346] ata7.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB02, max UDMA/33
[    1.156370] ata7.01: ATAPI: PIONEER DVD-RW  DVR-115D, 1.06, max UDMA/66
[    1.172358] ata7.00: configured for UDMA/33
[    1.188358] ata7.01: configured for UDMA/66
[    1.309507] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.441460] usb 1-1: configuration #1 chosen from 1 choice
[    1.441679] hub 1-1:1.0: USB hub found
[    1.442038] hub 1-1:1.0: 4 ports detected
[    1.460009] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.466338] ata1.00: ATA-7: SAMSUNG HD103SI, 1AG01118, max UDMA7
[    1.466340] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.472737] ata1.00: configured for UDMA/133
[    1.488077] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
[    1.488154] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.488178] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.488207] sd 0:0:0:0: [sda] Write Protect is off
[    1.488209] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.488223] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.488307]  sda: sda1 sda2
[    1.499561] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.608006] usb 1-3: new high speed USB device using ehci_hcd and address 4
[    1.740897] usb 1-3: configuration #1 chosen from 1 choice
[    2.148006] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    2.326007] usb 3-2: configuration #1 chosen from 1 choice
[    2.376008] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.382329] ata2.00: ATA-7: SAMSUNG HD103SI, 1AG01118, max UDMA7
[    2.382331] ata2.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.388728] ata2.00: configured for UDMA/133
[    2.404051] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
[    2.404112] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.404115] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.404140] sd 1:0:0:0: [sdb] Write Protect is off
[    2.404142] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.404157] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.404231]  sdb: sdb1 sdb2
[    2.428256] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.568005] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.741237] usb 5-1: configuration #1 chosen from 1 choice
[    2.984005] usb 8-1: new full speed USB device using uhci_hcd and address 2
[    3.130593] usb 8-1: configuration #1 chosen from 1 choice
[    3.204247] usb 1-1.1: new high speed USB device using ehci_hcd and address 6
[    3.292009] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.303756] usb 1-1.1: configuration #1 chosen from 1 choice
[    3.331033] ata3.00: ATA-7: ST3500630AS, 3.AAC, max UDMA/133
[    3.331035] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.376343] usb 1-1.4: new high speed USB device using ehci_hcd and address 7
[    3.389340] ata3.00: configured for UDMA/133
[    3.404060] scsi 2:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    3.404127] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.404148] sd 2:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.404175] sd 2:0:0:0: [sdc] Write Protect is off
[    3.404177] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.404191] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.404261]  sdc: sdc1
[    3.429100] sd 2:0:0:0: [sdc] Attached SCSI disk
[    3.469228] usb 1-1.4: configuration #1 chosen from 1 choice
[    3.469468] hub 1-1.4:1.0: USB hub found
[    3.469697] hub 1-1.4:1.0: 4 ports detected
[    4.292008] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.292547] ata4.00: ATA-7: ST3250310AS, 3.AAC, max UDMA/133
[    4.292549] ata4.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.293210] ata4.00: configured for UDMA/133
[    4.308055] scsi 3:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[    4.308112] sd 3:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    4.308119] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    4.308140] sd 3:0:0:0: [sdd] Write Protect is off
[    4.308142] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.308157] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.308226]  sdd: sdd1 sdd2 < sdd5 >
[    4.342148] sd 3:0:0:0: [sdd] Attached SCSI disk
[    5.196008] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.214134] ata5.00: ATA-8: SAMSUNG HD501LJ, CR100-11, max UDMA7
[    5.214136] ata5.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.216075] ata5.00: configured for UDMA/133
[    5.232055] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    5.232121] sd 4:0:0:0: [sde] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.232129] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    5.232164] sd 4:0:0:0: [sde] Write Protect is off
[    5.232166] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    5.232181] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.232259]  sde: sde1
[    5.250471] sd 4:0:0:0: [sde] Attached SCSI disk
[    6.120008] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.124924] ata6.00: ATA-7: SAMSUNG SP2504C, VT100-33, max UDMA7
[    6.124926] ata6.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.129850] ata6.00: configured for UDMA/133
[    6.144052] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5
[    6.144110] sd 5:0:0:0: [sdf] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    6.144117] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    6.144137] sd 5:0:0:0: [sdf] Write Protect is off
[    6.144139] sd 5:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    6.144153] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.144222]  sdf:
[    6.144930] scsi 6:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB02 PQ: 0 ANSI: 5
[    6.151791] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.151794] Uniform CD-ROM driver Revision: 3.20
[    6.151840] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    6.151871] sr 6:0:0:0: Attached scsi generic sg6 type 5
[    6.154062]  sdf1 sdf2
[    6.154190] sd 5:0:0:0: [sdf] Attached SCSI disk
[    6.157778] scsi 6:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-115D 1.06 PQ: 0 ANSI: 5
[    6.176077] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    6.176124] sr 6:0:1:0: Attached scsi CD-ROM sr1
[    6.176151] sr 6:0:1:0: Attached scsi generic sg7 type 5
[    6.343086] Freeing unused kernel memory: 544k freed
[    6.343272] Write protecting the kernel text: 4592k
[    6.343326] Write protecting the kernel read-only data: 1836k
[    6.420244] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    6.420247] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    6.420292] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.420311] e1000e 0000:02:00.0: setting latency timer to 64
[    6.420387]   alloc irq_desc for 30 on node -1
[    6.420388]   alloc kstat_irqs on node -1
[    6.420398] e1000e 0000:02:00.0: irq 30 for MSI/MSI-X
[    6.422400] Floppy drive(s): fd0 is 1.44M
[    6.426520] sky2 driver version 1.23
[    6.426551] sky2 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.426560] sky2 0000:03:00.0: setting latency timer to 64
[    6.426580] sky2 0000:03:00.0: Yukon-2 EC Ultra chip revision 3
[    6.426660]   alloc irq_desc for 31 on node -1
[    6.426662]   alloc kstat_irqs on node -1
[    6.426672] sky2 0000:03:00.0: irq 31 for MSI/MSI-X
[    6.427121] sky2 eth0: addr 00:1d:60:c8:d1:c9
[    6.432412] usbcore: registered new interface driver hiddev
[    6.443854] generic-usb 0003:0B05:172E.0003: hiddev96,hidraw0: USB HID v1.10 Device [T-wins ASUS DH Remote] on usb-0000:00:1a.2-1/input0
[    6.443871] usbcore: registered new interface driver usbhid
[    6.443873] usbhid: v2.6:USB HID core driver
[    6.452876] FDC 0 is a post-1991 82077
[    6.455876] ohci1394 0000:06:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.471459] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input3
[    6.471503] logitech 0003:046D:C512.0001: input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-2/input0
[    6.506777] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input4
[    6.506829] logitech 0003:046D:C512.0002: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-2/input1
[    6.514517] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[febfe000-febfe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    6.611291] 0000:02:00.0: eth1: (PCI Express:2.5GB/s:Width x4) 00:15:17:71:2c:ba
[    6.611293] 0000:02:00.0: eth1: Intel(R) PRO/1000 Network Connection
[    6.611367] 0000:02:00.0: eth1: MAC: 0, PHY: 4, PBA No: d50868-003
[    6.611389] e1000e 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.611405] e1000e 0000:02:00.1: setting latency timer to 64
[    6.611471]   alloc irq_desc for 32 on node -1
[    6.611473]   alloc kstat_irqs on node -1
[    6.611481] e1000e 0000:02:00.1: irq 32 for MSI/MSI-X
[    6.787289] 0000:02:00.1: eth2: (PCI Express:2.5GB/s:Width x4) 00:15:17:71:2c:bb
[    6.787291] 0000:02:00.1: eth2: Intel(R) PRO/1000 Network Connection
[    6.787365] 0000:02:00.1: eth2: MAC: 0, PHY: 4, PBA No: d50868-003
[    7.756588] PM: Starting manual resume from disk
[    7.756591] PM: Resume from partition 8:53
[    7.756593] PM: Checking hibernation image.
[    7.756714] PM: Resume from disk failed.
[    7.790494] EXT4-fs (sdd1): barriers enabled
[    7.793607] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800018a1afe]
[    7.807835] kjournald2 starting: pid 453, dev sdd1:8, commit interval 5 seconds
[    7.807843] EXT4-fs (sdd1): delayed allocation enabled
[    7.807846] EXT4-fs: file extents enabled
[    7.820225] EXT4-fs: mballoc enabled
[    7.820233] EXT4-fs (sdd1): mounted filesystem with ordered data mode
[    8.420128] type=1505 audit(1256989991.904:2): operation="profile_load" pid=476 name=/usr/share/gdm/guest-session/Xsession
[    8.427415] type=1505 audit(1256989991.908:3): operation="profile_load" pid=477 name=/sbin/dhclient3
[    8.427883] type=1505 audit(1256989991.908:4): operation="profile_load" pid=477 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.428139] type=1505 audit(1256989991.912:5): operation="profile_load" pid=477 name=/usr/lib/connman/scripts/dhclient-script
[    8.452958] type=1505 audit(1256989991.936:6): operation="profile_load" pid=478 name=/usr/bin/evince
[    8.460190] type=1505 audit(1256989991.944:7): operation="profile_load" pid=478 name=/usr/bin/evince-previewer
[    8.464464] type=1505 audit(1256989991.948:8): operation="profile_load" pid=478 name=/usr/bin/evince-thumbnailer
[    8.477863] type=1505 audit(1256989991.960:9): operation="profile_load" pid=480 name=/usr/lib/cups/backend/cups-pdf
[    8.478409] type=1505 audit(1256989991.960:10): operation="profile_load" pid=480 name=/usr/sbin/cupsd
[    8.496896] type=1505 audit(1256989991.980:11): operation="profile_load" pid=481 name=/usr/sbin/tcpdump
[    9.216481] Adding 9831740k swap on /dev/sdd5.  Priority:-1 extents:1 across:9831740k 
[    9.592129] EXT4-fs (sdd1): internal journal on sdd1:8
[    9.853862] udev: starting version 147
[   10.957045] cfg80211: Calling CRDA to update world regulatory domain
[   10.986144] EDAC MC: Ver: 2.1.0 Oct 16 2009
[   11.072669] Linux agpgart interface v0.103
[   11.219657] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   11.219746] usbcore: registered new interface driver btusb
[   11.668912] EDAC MC0: Giving out device to 'x38_edac' 'x38': DEV 0000:00:00.0
[   11.701180] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.486170] cfg80211: World regulatory domain updated:
[   12.486173]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.486175]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.486177]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.486178]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.486180]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.486181]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.542413] nvidia: module license 'NVIDIA' taints kernel.
[   13.542416] Disabling lock debugging due to kernel taint
[   13.793442] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.793449] nvidia 0000:01:00.0: setting latency timer to 64
[   13.793630] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
[   13.841624] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04E8 pid 0x328E
[   13.841647] usbcore: registered new interface driver usblp
[   13.918760] lp: driver loaded but no devices found
[   13.933308] Linux video capture interface: v2.00
[   14.729401] saa7130/34: v4l2 driver version 0.2.15 loaded
[   14.729442] saa7134 0000:06:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.729447] saa7133[0]: found at 0000:06:01.0, rev: 209, irq: 17, latency: 64, mmio: 0xfebff800
[   14.729452] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]
[   14.729465] saa7133[0]: board init: gpio is 843f00
[   14.729468] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   14.876511] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   14.876519] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   14.876526] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 03 01 08 ff 00 87 ff ff ff ff
[   14.876532] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876539] saa7133[0]: i2c eeprom 40: ff d6 00 c0 86 1c 02 01 02 ff ff ff ff ff ff ff
[   14.876546] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   14.876553] saa7133[0]: i2c eeprom 60: 35 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876560] saa7133[0]: i2c eeprom 70: 00 00 00 01 40 fe ff ff ff ff ff ff ff ff ff ff
[   14.876567] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876574] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876580] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876587] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876594] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876601] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876608] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876615] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.876622] i2c-adapter i2c-0: Invalid 7-bit address 0x7a
[   15.062995] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   15.108241] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   15.199959] saa7133[0]: dsp access error
[   15.199974] saa7133[0]: dsp access error
[   15.200000] saa7133[0]: dsp access error
[   15.199994] saa7133[0]: dsp access error
[   15.200039] saa7133[0]: registered device video0 [v4l2]
[   15.200054] saa7133[0]: registered device vbi0
[   15.200069] saa7133[0]: registered device radio0
[   15.200105] cx8800 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.200307] cx88[0]: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40,autodetected], frontend(s): 1
[   15.200309] cx88[0]: TV tuner type 63, Radio tuner type -1
[   15.393053] saa7134 ALSA driver for DMA sound loaded
[   15.393060] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   15.393073] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 17 registered as card -2
[   15.485372] saa7133[0]: dsp access error
[   15.485375] saa7133[0]: dsp access error
[   15.537577] cx2388x alsa driver version 0.0.7 loaded
[   15.711234] tuner 1-0043: chip found @ 0x86 (cx88[0])
[   15.713329] phy0: Selected rate control algorithm 'minstrel'
[   15.713851] phy0: hwaddr 00:1e:2a:b2:ba:25, RTL8187BvE V0 + rtl8225z2
[   15.735280] rtl8187: Customer ID is 0x00
[   15.735305] Registered led device: rtl8187-phy0::tx
[   15.735317] Registered led device: rtl8187-phy0::rx
[   15.735335] usbcore: registered new interface driver rtl8187
[   15.749614] tda9887 1-0043: creating new instance
[   15.749616] tda9887 1-0043: tda988[5/6/7] found
[   15.752156] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[   15.790384] tveeprom 1-0050: Hauppauge model 94009, rev C3A0, serial# 752373
[   15.790386] tveeprom 1-0050: MAC address is 00-0D-FE-0B-7A-F5
[   15.790388] tveeprom 1-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
[   15.790390] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   15.790393] tveeprom 1-0050: audio processor is CX882 (idx 33)
[   15.790394] tveeprom 1-0050: decoder processor is CX882 (idx 25)
[   15.790396] tveeprom 1-0050: has radio, has IR receiver, has no IR transmitter
[   15.790398] cx88[0]: hauppauge eeprom: model=94009
[   16.088310] tuner-simple 1-0061: creating new instance
[   16.088313] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   16.092251] input: cx88 IR (Hauppauge WinTV-HVR110 as /devices/pci0000:00/0000:00:1e.0/0000:06:00.0/input/input5
[   16.092286] cx88[0]/0: found at 0000:06:00.0, rev: 5, irq: 16, latency: 64, mmio: 0xfa000000
[   16.092293] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.092319] cx88[0]/0: registered device video1 [v4l2]
[   16.092341] cx88[0]/0: registered device vbi1
[   16.092359] cx88[0]/0: registered device radio1
[   16.094107] cx88[0]/2: cx2388x 8802 Driver Manager
[   16.094118] cx88-mpeg driver manager 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.094125] cx88[0]/2: found at 0000:06:00.2, rev: 5, irq: 16, latency: 64, mmio: 0xfc000000
[   16.094128] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.094164] cx88_audio 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.094173] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.094188] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   16.285648] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.285679] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.596805] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   16.596972] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   16.779469] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   16.779472] cx88/2: registering cx8802 driver, type: dvb access: shared
[   16.779474] cx88[0]/2: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40]
[   16.779476] cx88[0]/2: cx2388x based DVB/ATSC card
[   16.779477] cx8802_alloc_frontends() allocating 1 frontend(s)
[   17.198882] tuner-simple 1-0061: attaching existing instance
[   17.198884] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   17.201136] DVB: registering new adapter (cx88[0])
[   17.201138] DVB: registering adapter 0 frontend 0 (Conexant CX22702 DVB-T)...
[   19.824149] e1000e 0000:02:00.0: irq 30 for MSI/MSI-X
[   19.880039] e1000e 0000:02:00.0: irq 30 for MSI/MSI-X
[   19.880315] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   20.376649] e1000e 0000:02:00.1: irq 32 for MSI/MSI-X
[   20.432536] e1000e 0000:02:00.1: irq 32 for MSI/MSI-X
[   20.432817] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   22.465086] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.465088] vboxdrv: Successfully done.
[   22.465089] vboxdrv: Found 4 processor cores.
[   22.465171] vboxdrv: fAsync=0 offMin=0x5fa offMax=0x16f5
[   22.465201] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.465202] vboxdrv: Successfully loaded version 3.0.10 (interface 0x000e0001).
[   24.382333] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.475685] sky2 eth0: enabling interface
[   24.475809] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.655960] ppdev: user-space parallel port driver
[   24.779302] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.779304] Bluetooth: BNEP filters: protocol multicast
[   24.863892] Bridge firewalling registered
[   27.723963] usb 1-3: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[ 1123.133238] wlan0: authenticate with AP 00:18:4d:61:37:0e
[ 1123.135362] wlan0: authenticated
[ 1123.135365] wlan0: associate with AP 00:18:4d:61:37:0e
[ 1123.137864] wlan0: RX AssocResp from 00:18:4d:61:37:0e (capab=0x431 status=0 aid=1)
[ 1123.137866] wlan0: associated
[ 1123.143131] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1133.224003] wlan0: no IPv6 routers present 

---

### Post by psd99 on 2009-10-31
I've actually got two TV cards in this machine the other is a DVB-S card a phillips conexant one. But my main concern at the moment is getting the hauppague one to work + the sound!

Here is lspci:

>  00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01)
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01)
00:06.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge (rev 01)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
02:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
02:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
06:00.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
06:00.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
06:00.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
06:00.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
06:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
06:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)


As you can see I see no alsa written in there I think that means that I've messed up my sound drivers by trying to install the TV card drivers.

Does anyone know how I can get the sound working?

Please reply thanks

---

### Post by psd99 on 2009-10-31
ahh there must be someone out there that can help

here is a big reason why people find it difficult to go to linux
as soon as it all becomes "out of the box" then I believe it can be more mainstream

---

