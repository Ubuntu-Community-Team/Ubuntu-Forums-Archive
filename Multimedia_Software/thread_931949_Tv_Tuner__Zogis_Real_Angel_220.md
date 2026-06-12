---
title: "Tv Tuner : Zogis Real Angel 220"
date: 2008-09-27
forum: Multimedia Software
---

### Post by lolmike on 2008-09-27
Hey guys, Im brand new to Ubuntu and Linux in general and I just wanted to say that im loving it so far.

Everything that i've had a problem with ive been able to research and there always seems to be some fix on the forums or somewhere on the web.

However, i ran into a dead end while trying to get my TV Tuner to work. Granted this is my first time installing/using a TV Tuner, and im not quite sure if its set up properly or being recognized by Ubuntu.

I have tried a slew of applications, TVTime opens for about .5 seconds and closes, xawTV seems like it opens and goes into a fullscreen mode, but i cant exit so i have to restart my system, MythTV comes across an error while installing (cant remember the exact error atm), and Me TV comes up with an error "No tuner device." 

I did some searching around and tried finding a fix, but nothing was working for me. Here's a few things other users have asked for trying to help out others having problems:

Make: Zogis
Model: Real Angel 220 PCI Analog Tv Tuner

lspci returns:
> 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3450
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
03:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


Any help is appreciated.

---

### Post by lolmike on 2008-09-28
bump?

---

### Post by xc3RnbFO8P on 2008-09-28
**dmesg** (just Tv tuner information)
and **lspci -vn**

---

### Post by cariboo on 2008-09-28
Your tv tuner card is support, the hard thing to discover is what card number to use so that Ubuntu can configure the tuner properly. I have this little script in /etc/modprobe.d for my tv tuner card:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

Go here:

[http://www.linuxtv.org/v4lwiki/index.php/Main_Page](http://www.linuxtv.org/v4lwiki/index.php/Main_Page)

To see if your card is listed.

Jim

---

### Post by lolmike on 2008-09-28
Okay, dmesg came up looking very very wrong, and actually cut off the beginning portion of the script?

```

[   29.697553] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   29.697593] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[   29.748038] SCSI subsystem initialized
[   29.752403] libata version 3.00 loaded.
[   29.759336] usb usb1: configuration #1 chosen from 1 choice
[   29.759365] hub 1-0:1.0: USB hub found
[   29.759375] hub 1-0:1.0: 3 ports detected
[   29.853275] Floppy drive(s): fd0 is 1.44M
[   29.863223] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 16
[   29.863837] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   29.863919] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[   29.863941] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[   29.874909] FDC 0 is a post-1991 82077
[   29.919199] usb usb2: configuration #1 chosen from 1 choice
[   29.919222] hub 2-0:1.0: USB hub found
[   29.919230] hub 2-0:1.0: 3 ports detected
[   30.023088] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
[   30.023713] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   30.023795] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   30.023826] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[   30.079062] usb usb3: configuration #1 chosen from 1 choice
[   30.079081] hub 3-0:1.0: USB hub found
[   30.079088] hub 3-0:1.0: 3 ports detected
[   30.170949] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   30.183000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 18
[   30.183630] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   30.183711] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   30.183733] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[   30.246982] usb usb4: configuration #1 chosen from 1 choice
[   30.247003] hub 4-0:1.0: USB hub found
[   30.247012] hub 4-0:1.0: 3 ports detected
[   30.350878] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 18
[   30.351509] ohci_hcd 0000:00:14.5: OHCI Host Controller
[   30.351589] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
[   30.351613] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[   30.399965] usb 1-1: configuration #1 chosen from 1 choice
[   30.410894] usb usb5: configuration #1 chosen from 1 choice
[   30.410918] hub 5-0:1.0: USB hub found
[   30.410926] hub 5-0:1.0: 2 ports detected
[   30.518861] ahci 0000:00:11.0: version 3.0
[   30.518902] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 22
[   30.519551] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   30.711544] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   30.949630] usb 1-2: configuration #1 chosen from 1 choice
[   30.951639] usbcore: registered new interface driver hiddev
[   30.964850] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1:1.0/input/input1
[   30.979398] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:12.0-1
[   30.988681] input: Microsoft Microsoft&#65533; Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:12.0/usb1/1-2/1-2:1.0/input/input2
[   31.003370] input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft&#65533; Digital Media Pro Keyboard] on usb-0000:00:12.0-2
[   31.020636] input: Microsoft Microsoft&#65533; Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:12.0/usb1/1-2/1-2:1.1/input/input3
[   31.051340] input,hidraw2: USB HID v1.11 Device [Microsoft Microsoft&#65533; Digital Media Pro Keyboard] on usb-0000:00:12.0-2
[   31.051355] usbcore: registered new interface driver usbhid
[   31.051359] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.518073] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   31.518080] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
[   31.519549] scsi0 : ahci
[   31.519995] scsi1 : ahci
[   31.520160] scsi2 : ahci
[   31.520308] scsi3 : ahci
[   31.520455] scsi4 : ahci
[   31.520657] scsi5 : ahci
[   31.520740] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 509
[   31.520744] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 509
[   31.520747] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 509
[   31.520749] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 509
[   31.520752] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 509
[   31.520755] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 509
[   31.993715] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.003709] ata1.00: HPA unlocked: 625140335 -> 625142448, native 625142448
[   32.003716] ata1.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133
[   32.003719] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   32.004649] ata1.00: configured for UDMA/133
[   32.313489] ata2: SATA link down (SStatus 0 SControl 300)
[   32.789186] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   32.948899] ata3.00: ATAPI: HL-DT-ST BDDVDRW GGC-H20L, 1.03, max UDMA/133
[   33.109039] ata3.00: configured for UDMA/133
[   33.420754] ata4: SATA link down (SStatus 0 SControl 300)
[   33.732552] ata5: SATA link down (SStatus 0 SControl 300)
[   34.044341] ata6: SATA link down (SStatus 0 SControl 300)
[   34.044467] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[   34.047881] scsi 2:0:0:0: CD-ROM            HL-DT-ST BDDVDRW GGC-H20L 1.03 PQ: 0 ANSI: 5
[   34.048347] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 17
[   34.048980] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   34.049059] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 6
[   34.049101] ehci_hcd 0000:00:12.2: debug port 1
[   34.049122] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[   34.049350] usb 1-1: USB disconnect, address 2
[   34.060853] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.060994] usb usb6: configuration #1 chosen from 1 choice
[   34.061015] hub 6-0:1.0: USB hub found
[   34.061022] hub 6-0:1.0: 6 ports detected
[   34.062883] Driver 'sd' needs updating - please use bus_type methods
[   34.062975] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   34.062985] sd 0:0:0:0: [sda] Write Protect is off
[   34.062986] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.062997] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.063049] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   34.063056] sd 0:0:0:0: [sda] Write Protect is off
[   34.063058] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.063067] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.063070]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   34.080874]  sda1 sda2 < sda5 sda6 >
[   34.120567] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.125710] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.125730] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   34.127984] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   34.127991] Uniform CD-ROM driver Revision: 3.20
[   34.128048] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   34.168921] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 19
[   34.169547] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   34.169639] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
[   34.169681] ehci_hcd 0000:00:13.2: debug port 1
[   34.169702] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[   34.184747] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.184878] usb usb7: configuration #1 chosen from 1 choice
[   34.184900] hub 7-0:1.0: USB hub found
[   34.184907] hub 7-0:1.0: 6 ports detected
[   34.205246] usb 1-2: USB disconnect, address 3
[   34.288809] r8169 Gigabit Ethernet driver 2.2LK loaded
[   34.288836] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   34.288857] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   34.289106] eth0: RTL8168c/8111c at 0xffffc20001042000, 00:1f:d0:5a:dd:d6, XID 3c4000c0 IRQ 508
[   34.290863] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 22 (level, low) -> IRQ 22
[   34.291458] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   34.291566] scsi6 : pata_atiixp
[   34.291619] scsi7 : pata_atiixp
[   34.292309] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[   34.292311] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[   34.341007] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fddfe000-fddfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   34.619775] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   34.619784] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   34.714703] Attempting manual resume
[   34.714707] swsusp: Resume From Partition 8:6
[   34.714709] PM: Checking swsusp image.
[   34.714877] PM: Resume from disk failed.
[   34.728283] EXT3-fs: INFO: recovery required on readonly filesystem.
[   34.728288] EXT3-fs: write access will be enabled during recovery.
[   35.055674] usb 1-1: new low speed USB device using ohci_hcd and address 4
[   35.279162] usb 1-1: configuration #1 chosen from 1 choice
[   35.293345] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1:1.0/input/input4
[   35.308523] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:12.0-1
[   35.533517] kjournald starting.  Commit interval 5 seconds
[   35.533533] EXT3-fs: sda5: orphan cleanup on readonly fs
[   35.533541] ext3_orphan_cleanup: deleting unreferenced inode 11256448
[   35.533581] ext3_orphan_cleanup: deleting unreferenced inode 9101328
[   35.533588] EXT3-fs: sda5: 2 orphan inodes deleted
[   35.533589] EXT3-fs: recovery complete.
[   35.535748] EXT3-fs: mounted filesystem with ordered data mode.
[   35.608436] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0072601900001fd0]
[   35.620296] usb 1-2: new low speed USB device using ohci_hcd and address 5
[   35.856828] usb 1-2: configuration #1 chosen from 1 choice
[   35.868937] input: Microsoft Microsoft&#65533; Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:12.0/usb1/1-2/1-2:1.0/input/input5
[   35.880164] input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft&#65533; Digital Media Pro Keyboard] on usb-0000:00:12.0-2
[   35.897836] input: Microsoft Microsoft&#65533; Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:12.0/usb1/1-2/1-2:1.1/input/input6
[   35.908107] input,hidraw2: USB HID v1.11 Device [Microsoft Microsoft&#65533; Digital Media Pro Keyboard] on usb-0000:00:12.0-2
[   41.797317] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.799051] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.840471] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   41.891470] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   42.009429] input: Power Button (FF) as /devices/virtual/input/input8
[   42.036058] ACPI: Power Button (FF) [PWRF]
[   42.036150] input: Power Button (CM) as /devices/virtual/input/input9
[   42.064002] ACPI: Power Button (CM) [PWRB]
[   42.091158] ACPI: WMI-Acer: Mapper loaded
[   42.267954] Linux video capture interface: v2.00
[   42.375831] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   42.431899] [fglrx] Maximum main memory to use for locked dma buffers: 3796 MBytes.
[   42.431938] [fglrx] ASYNCIO init succeed!
[   42.432979] [fglrx] PAT is enabled successfully!
[   42.433014] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   42.485250] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   42.522974] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   42.558139] parport_pc 00:0a: reported by Plug and Play ACPI
[   42.558275] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   42.558533] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 19 (level, low) -> IRQ 19
[   42.559142] PCI: Setting latency timer of device 0000:01:00.1 to 64
[   42.590893] saa7130/34: v4l2 driver version 0.2.14 loaded
[   42.608505] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 20 (level, low) -> IRQ 20
[   42.608520] saa7130[0]: found at 0000:03:06.0, rev: 1, irq: 20, latency: 32, mmio: 0xfddff000
[   42.608530] saa7134: <rant>
[   42.608530] saa7134:  Congratulations!  Your TV card vendor saved a few
[   42.608531] saa7134:  cents for a eeprom, thus your pci board has no
[   42.608532] saa7134:  subsystem ID and I can't identify it automatically
[   42.608533] saa7134: </rant>
[   42.608533] saa7134: I feel better now.  Ok, here are the good news:
[   42.608534] saa7134: You can use the card=<nr> insmod option to specify
[   42.608535] saa7134: which board do you have.  The list:
[   42.608538] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   42.608540] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   42.608544] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   42.608547] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   42.608550] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   42.608552] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   42.608554] saa7134:   card=6 -> Tevion MD 9717                          
[   42.608556] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   42.608559] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   42.608561] saa7134:   card=9 -> Medion 5044                             
[   42.608563] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   42.608565] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   42.608567] saa7134:   card=12 -> Medion 7134                              16be:0003
[   42.608569] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   42.608571] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   42.608573] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   42.608575] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   42.608578] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   42.608581] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   42.608583] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   42.608585] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   42.608587] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   42.608590] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   42.608592] saa7134:   card=23 -> BMK MPEX Tuner                          
[   42.608594] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   42.608596] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   42.608598] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   42.608600] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM   
[   42.608602] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401      
[   42.608604] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   42.608606] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   42.608608] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   42.608610] saa7134:   card=32 -> AVACS SmartTV                           
[   42.608612] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   42.608615] saa7134:   card=34 -> Noval Prime TV 7133                     
[   42.608616] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   42.608619] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   42.608621] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   42.608623] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   42.608625] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[   42.608627] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   42.608629] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   42.608632] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   42.608633] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   42.608635] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   42.608637] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   42.608639] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   42.608642] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   42.608644] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   42.608646] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   42.608648] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   42.608651] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   42.608653] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   42.608655] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   42.608657] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   42.608660] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   42.608663] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   42.608665] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   42.608667] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   42.608670] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   42.608672] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   42.608675] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   42.608678] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   42.608680] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   42.608682] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   42.608684] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   42.608686] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   42.608688] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   42.608690] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   42.608692] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   42.608694] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   42.608696] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   42.608698] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   42.608701] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   42.608703] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   42.608705] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   42.608707] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   42.608710] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   42.608712] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4857
[   42.608714] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   42.608716] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   42.608719] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   42.608721] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[   42.608723] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   42.608725] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   42.608727] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   42.608730] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   42.608732] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   42.608734] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   42.608737] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   42.608739] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   42.608742] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   42.608744] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   42.608746] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   42.608748] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 4e42:3502
[   42.608751] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   42.608753] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008
[   42.608756] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   42.608758] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   42.608761] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   42.608763] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   42.608765] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   42.608767] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   42.608770] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   42.608772] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6701
[   42.608774] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   42.608776] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   42.608780] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   42.608782] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   42.608784] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   42.608786] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   42.608788] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   42.608790] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   42.608793] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   42.608795] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   42.608797] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   42.608799] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   42.608801] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   42.608804] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   42.608817] saa7130[0]: board init: gpio is 80c008
[   42.711277] saa7130[0]: Huh, no eeprom present (err=-5)?
[   42.711347] saa7130[0]: registered device video0 [v4l2]
[   42.711363] saa7130[0]: registered device vbi0
[   42.711489] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 21 (level, low) -> IRQ 21
[   42.711533] snd-ca0106: Model 1013 Rev 00000000 Serial 10131102
[   42.729579] saa7134 ALSA driver for DMA sound loaded
[   42.729618] saa7130[0]/alsa: saa7130[0] at 0xfddff000 irq 20 registered as card -2
[   45.219289] lp0: using parport0 (interrupt-driven).
[   45.327617] Adding 11880028k swap on /dev/sda6.  Priority:-1 extents:1 across:11880028k
[   45.893900] EXT3 FS on sda5, internal journal
[   46.997473] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.495764] No dock devices found.
[   48.904430] ppdev: user-space parallel port driver
[   49.052912] audit(1222561903.954:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5531 profile="/usr/sbin/cupsd" namespace="default"
[   54.025336] r8169: eth0: link up
[   54.025348] r8169: eth0: link up
[   54.111290] Bluetooth: Core ver 2.11
[   54.111387] NET: Registered protocol family 31
[   54.111389] Bluetooth: HCI device and connection manager initialized
[   54.111394] Bluetooth: HCI socket layer initialized
[   54.149243] Bluetooth: L2CAP ver 2.9
[   54.149249] Bluetooth: L2CAP socket layer initialized
[   54.212009] Bluetooth: RFCOMM socket layer initialized
[   54.212026] Bluetooth: RFCOMM TTY layer initialized
[   54.212028] Bluetooth: RFCOMM ver 1.8
[   56.233057] NET: Registered protocol family 17
[   56.259942] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   57.581584] [fglrx] Reserve Block - 0 offset =  0X1fffc000 length = 0X4000
[   57.581590] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   57.581593] [fglrx] Reserve Block - 2 offset =  0Xff7f000 length = 0X80000
[   57.682472] NET: Registered protocol family 10
[   57.682709] lo: Disabled Privacy Extensions
[   57.846710] [fglrx] interrupt source ff000034 successfully enabled
[   57.846720] [fglrx] enable ID = 0x00000006
[   57.846732] [fglrx] Receive enable interrupt message with irqEnableMask: ff000034
[   57.846889] [fglrx] interrupt source 10000000 successfully enabled
[   57.846896] [fglrx] enable ID = 0x00000007
[   57.846902] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   57.856568] [fglrx] interrupt source 60000001 successfully enabled
[   57.856578] [fglrx] enable ID = 0x00000008
[   57.856585] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[   57.856631] [fglrx] interrupt source 00000040 successfully enabled
[   57.856633] [fglrx] enable ID = 0x00000009
[   57.856637] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[   57.856880] [fglrx] interrupt source ff00002c successfully enabled
[   57.856884] [fglrx] enable ID = 0x0000000A
[   57.856888] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[   57.856912] [fglrx] interrupt source ff00002d successfully enabled
[   57.856915] [fglrx] enable ID = 0x0000000B
[   57.856918] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[   57.856943] [fglrx] interrupt source 20000400 successfully enabled
[   57.856945] [fglrx] enable ID = 0x0000000C
[   57.856949] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[   63.349273] hda-intel: Invalid position buffer, using LPIB read method instead.
[   67.758593] eth0: no IPv6 routers present
[   77.722694] UDF-fs: No VRS found
[   77.740796] ISO 9660 Extensions: Microsoft Joliet Level 3
[   77.742629] ISOFS: changing to secondary root
[11146.435040] npviewer.bin[12031]: segfault at f5b07030 rip f78fb540 rsp ff9cac4c error 4
[11364.152294] UDF-fs: Partition marked readonly; forcing readonly mount
[11364.187944] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DIRTYDANCING20TH_D1', timestamp 2007/03/09 21:57 (1f10)
[17432.532776] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483518 frees, -2147483648 allocs
[17432.532790] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483519 frees, -2147483647 allocs
[17432.532793] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483520 frees, -2147483646 allocs
[17432.532796] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483521 frees, -2147483645 allocs
[17432.532801] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483522 frees, -2147483644 allocs
[17432.532803] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483523 frees, -2147483643 allocs
[17432.532806] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483524 frees, -2147483642 allocs
[17432.532809] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483525 frees, -2147483641 allocs
[17432.532812] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483526 frees, -2147483640 allocs
[17432.532815] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483527 frees, -2147483639 allocs
[17432.532817] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483528 frees, -2147483638 allocs
[17432.532820] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483529 frees, -2147483637 allocs
[17432.532824] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483530 frees, -2147483636 allocs
[17432.532827] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483531 frees, -2147483635 allocs
[17432.532831] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483532 frees, -2147483634 allocs
[17432.532835] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483533 frees, -2147483633 allocs
[17432.532839] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483534 frees, -2147483632 allocs
[17432.532843] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483535 frees, -2147483631 allocs
[17432.532846] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483536 frees, -2147483630 allocs
[17432.532850] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483537 frees, -2147483629 allocs
[17432.532854] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483538 frees, -2147483628 allocs
[17432.532858] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483539 frees, -2147483627 allocs
[17432.532861] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483540 frees, -2147483626 allocs
[17432.532865] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483541 frees, -2147483625 allocs
[17432.532869] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483542 frees, -2147483624 allocs
[17432.532872] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483543 frees, -2147483623 allocs
[17432.532876] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483544 frees, -2147483622 allocs
[17432.532880] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483545 frees, -2147483621 allocs
[17432.532884] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483546 frees, -2147483620 allocs
[17432.532887] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483547 frees, -2147483619 allocs
[17432.532891] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483548 frees, -2147483618 allocs
[17432.532895] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483549 frees, -2147483617 allocs
[17432.532899] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483550 frees, -2147483616 allocs
[17432.532903] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483551 frees, -2147483615 allocs
[17432.532907] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483552 frees, -2147483614 allocs
[17432.532911] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483553 frees, -2147483613 allocs
[17432.532914] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483554 frees, -2147483612 allocs
[17432.532918] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483555 frees, -2147483611 allocs
[17432.532922] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483556 frees, -2147483610 allocs
[17432.532926] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483557 frees, -2147483609 allocs
[17432.532929] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483558 frees, -2147483608 allocs
[17432.532933] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483559 frees, -2147483607 allocs
[17432.532937] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483560 frees, -2147483606 allocs
[17432.532941] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483561 frees, -2147483605 allocs
[17432.532945] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483562 frees, -2147483604 allocs
[17432.532948] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483563 frees, -2147483603 allocs
[17432.532952] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483564 frees, -2147483602 allocs
[17432.532955] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483565 frees, -2147483601 allocs
[17432.532959] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483566 frees, -2147483600 allocs
[17432.532962] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483567 frees, -2147483599 allocs
[17432.532966] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483568 frees, -2147483598 allocs
[17432.532970] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483569 frees, -2147483597 allocs
[17432.532974] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483570 frees, -2147483596 allocs
[17432.532977] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483571 frees, -2147483595 allocs
[17432.532981] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483572 frees, -2147483594 allocs
[17432.532985] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483573 frees, -2147483593 allocs
[17432.532989] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483574 frees, -2147483592 allocs
[17432.532993] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483575 frees, -2147483591 allocs
[17432.532996] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483576 frees, -2147483590 allocs
[17432.533000] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483577 frees, -2147483589 allocs
[17432.533003] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483578 frees, -2147483588 allocs
[17432.533007] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483579 frees, -2147483587 allocs
[17432.533011] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483580 frees, -2147483586 allocs
[17432.533015] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483581 frees, -2147483585 allocs
[17432.533018] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483582 frees, -2147483584 allocs
[17432.533022] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483583 frees, -2147483583 allocs
[17432.533026] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483584 frees, -2147483582 allocs
[17432.533029] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483585 frees, -2147483581 allocs
[17432.533034] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483586 frees, -2147483580 allocs
[17432.533037] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483587 frees, -2147483579 allocs
[17432.533041] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483588 frees, -2147483578 allocs
[17432.533045] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483589 frees, -2147483577 allocs
[17432.533049] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483590 frees, -2147483576 allocs
[17432.533052] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483591 frees, -2147483575 allocs
[17432.533056] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483592 frees, -2147483574 allocs
[17432.533060] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483593 frees, -2147483573 allocs
[17432.533063] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483594 frees, -2147483572 allocs
[17432.533067] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483595 frees, -2147483571 allocs
[17432.533071] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483596 frees, -2147483570 allocs
[17432.533074] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483597 frees, -2147483569 allocs
[17432.533078] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483598 frees, -2147483568 allocs
[17432.533082] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483599 frees, -2147483567 allocs
[17432.533150] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483600 frees, -2147483566 allocs
[17432.533154] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483601 frees, -2147483565 allocs
[17432.533157] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483602 frees, -2147483564 allocs
[17432.533161] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483603 frees, -2147483563 allocs
[17432.533164] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483604 frees, -2147483562 allocs
[17432.533168] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483605 frees, -2147483561 allocs
[17432.533172] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483606 frees, -2147483560 allocs
[17432.533176] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483607 frees, -2147483559 allocs
[17432.533179] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483608 frees, -2147483558 allocs
[17432.533183] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483609 frees, -2147483557 allocs
[17432.533187] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483610 frees, -2147483556 allocs
[17432.533190] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483611 frees, -2147483555 allocs
[17432.533194] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483612 frees, -2147483554 allocs
[17432.533197] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483613 frees, -2147483553 allocs
[17432.533201] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483614 frees, -2147483552 allocs
[17432.533205] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483615 frees, -2147483551 allocs
[17432.533209] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483616 frees, -2147483550 allocs
[17432.533213] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483617 frees, -2147483549 allocs
[17432.533217] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483618 frees, -2147483548 allocs
[17432.533221] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483619 frees, -2147483547 allocs
[17432.533225] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483620 frees, -2147483546 allocs
[17432.533228] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483621 frees, -2147483545 allocs
[17432.533232] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483622 frees, -2147483544 allocs
[17432.533236] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483623 frees, -2147483543 allocs
[17432.533240] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483624 frees, -2147483542 allocs
[17432.533243] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483625 frees, -2147483541 allocs
[17432.533248] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483626 frees, -2147483540 allocs
[17432.533251] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483627 frees, -2147483539 allocs
[17432.533255] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483628 frees, -2147483538 allocs
[17432.533258] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483629 frees, -2147483537 allocs
[17432.533262] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483630 frees, -2147483536 allocs
[17432.533266] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483631 frees, -2147483535 allocs
[17432.533270] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483632 frees, -2147483534 allocs
[17432.533274] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483633 frees, -2147483533 allocs
[17432.533278] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483634 frees, -2147483532 allocs
[17432.533282] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483635 frees, -2147483531 allocs
[17432.533285] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483636 frees, -2147483530 allocs
[17432.533289] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483637 frees, -2147483529 allocs
[17432.533293] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483638 frees, -2147483528 allocs
[17432.533296] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483639 frees, -2147483527 allocs
[17432.533300] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483640 frees, -2147483526 allocs
[17432.533304] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483641 frees, -2147483525 allocs
[17432.533308] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483642 frees, -2147483524 allocs
[17432.533311] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483643 frees, -2147483523 allocs
[17432.533315] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483644 frees, -2147483522 allocs
[17432.533319] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483645 frees, -2147483521 allocs
[17432.533323] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483646 frees, -2147483520 allocs
[17432.533327] [fglrx:drm_free] *ERROR* [driver] Excess frees: 2147483647 frees, -2147483519 allocs

```

and here is the lspci -vn
```

00:00.0 0600: 1022:9600
	Subsystem: 1022:9600
	Flags: bus master, 66MHz, medium devsel, latency 32
	Memory at <ignored> (64-bit, non-prefetchable)
	Capabilities: <access denied>

00:02.0 0604: 1022:9603 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:0a.0 0604: 1022:9609 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: <access denied>

00:11.0 0106: 1002:4391 (prog-if 01 [AHCI 1.0])
	Subsystem: 1458:b002
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 509
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:12.0 0c03: 1002:4397 (prog-if 10 [OHCI])
	Subsystem: 1458:5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]

00:12.1 0c03: 1002:4398 (prog-if 10 [OHCI])
	Subsystem: 1458:5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]

00:12.2 0c03: 1002:4396 (prog-if 20 [EHCI])
	Subsystem: 1458:5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:13.0 0c03: 1002:4397 (prog-if 10 [OHCI])
	Subsystem: 1458:5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]

00:13.1 0c03: 1002:4398 (prog-if 10 [OHCI])
	Subsystem: 1458:5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]

00:13.2 0c03: 1002:4396 (prog-if 20 [EHCI])
	Subsystem: 1458:5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 0c05: 1002:4385 (rev 3a)
	Subsystem: 1458:4385
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>

00:14.1 0101: 1002:439c (prog-if 8a [Master SecP PriP])
	Subsystem: 1458:5002
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at fa00 [size=16]
	Capabilities: <access denied>

00:14.2 0403: 1002:4383
	Subsystem: 1458:a022
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 0601: 1002:439d
	Subsystem: 1002:4383
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 0604: 1002:4384 (prog-if 01 [Subtractive decode])
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff

00:14.5 0c03: 1002:4399 (prog-if 10 [OHCI])
	Subsystem: 1458:5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe028000 (32-bit, non-prefetchable) [size=4K]

00:18.0 0600: 1022:1200
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 0600: 1022:1201
	Flags: fast devsel

00:18.2 0600: 1022:1202
	Flags: fast devsel

00:18.3 0600: 1022:1203
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 0600: 1022:1204
	Flags: fast devsel

01:00.0 0300: 1002:95c5 (prog-if 00 [VGA controller])
	Subsystem: 1043:01e2
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdfe0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ee00 [size=256]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 0403: 1002:aa28
	Subsystem: 1043:aa28
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

02:00.0 0200: 10ec:8168 (rev 02)
	Subsystem: 1458:e000
	Flags: bus master, fast devsel, latency 0, IRQ 508
	I/O ports at de00 [size=256]
	Memory at fdbff000 (64-bit, prefetchable) [size=4K]
	Memory at fdbe0000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at fdb00000 [disabled] [size=64K]
	Capabilities: <access denied>

03:06.0 0480: 1131:7130 (rev 01)
	Subsystem: 1131:0000
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at fddff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

03:07.0 0401: 1102:0007
	Subsystem: 1102:1013
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at cf00 [size=32]
	Capabilities: <access denied>

03:0e.0 0c00: 104c:8024 (prog-if 10 [OHCI])
	Subsystem: 1458:1000
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at fddfe000 (32-bit, non-prefetchable) [size=2K]
	Memory at fddf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

and according to that site it does not look like my tuner is listed. would the best course of action be buying a new tuner?

---

### Post by xc3RnbFO8P on 2008-09-28
> 03:06.0 0480: 1131:7130 (rev 01)
	Subsystem: [COLOR="Green"]1131:0000[/COLOR]
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at fddff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

Read this:
[http://www.linuxtv.org/v4lwiki/index.php/Tevion_MD_9717]("http://www.linuxtv.org/v4lwiki/index.php/Tevion_MD_9717")
Find out which Tv card you have (type 1 or 2)
> sudo gedit /etc/modprobe.d/options
and add card=6 or card=5, card=88.
Restart the computer and check dmesg.

---

### Post by Darkhaund on 2012-01-10
Do I have to make a file or what?  I am a bit lost and I would appreciate help :D

---

