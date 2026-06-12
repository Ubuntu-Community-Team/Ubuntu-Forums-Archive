---
title: "Tvtime won't work."
date: 2008-06-11
forum: Multimedia Software
---

### Post by Sprocket_dk on 2008-06-11
I have a haupauge wintv nova-t card with cx88 chips. It works great in mythtv, but i would like to use tvtime. In tvtime I can see that video source is set to DVB, witch should be right i guess. When I run tvtime-scanner it gives me: 

Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/dennis/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/dennis/.tvtime/stationlist.xml: No existing PAL station list "Custom".

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.

dmesg:
dennis@dennis:~$ dmesg | grep cx88
[   43.913017] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   43.913136] cx88[0]: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18,insmod option]
[   43.913139] cx88[0]: TV tuner type 0, Radio tuner type -1
[   43.915263] cx8802: Unknown parameter `video_nr'
[   44.059940] cx88[0]: hauppauge eeprom: model=90003
[   44.069882] input: cx88 IR (Hauppauge Nova-T DVB-T as /devices/pci0000:00/0000:00:1e.0/0000:01:01.0/input/input8
[   44.089846] cx88[0]/0: found at 0000:01:01.0, rev: 5, irq: 21, latency: 64, mmio: 0xd8000000
[   44.089906] cx88[0]/0: registered device video0 [v4l2]
[   44.089930] cx88[0]/0: registered device vbi0
[   57.650065] cx88[0]/0: unknown tv audio mode [0]

---

### Post by Sprocket_dk on 2008-06-13
I've now also tried Kaffeine, and it gives me: "can't bind info socket" message at startup. 

Also Me-tv gives an error: "Failed to open tuner: Device or resource busy"

Anyone know what that means and how to solve it?

---

### Post by xc3RnbFO8P on 2008-06-13
Try in Terminal:
> modprobe cx88_dvb
and try Kaffeine or Me-tv

---

### Post by Sprocket_dk on 2008-06-13
That didn't do anything. I think its allready running, the card works fine in mythtv.

---

### Post by Jose Catre-Vandis on 2008-06-13
tvtime is for analog tv only, use kaffiene for dvb as a test, or mplayer if you have a channels.conf file
```
mplayer dvb://
```

post your output from dmesg so we can see what's loaded

---

### Post by wolfen69 on 2008-06-13
if you cant get it to work, consider doing what i do. install mythbuntu, and then install ubuntu-desktop. that way you can have myth tv and regular ubuntu.

---

### Post by xc3RnbFO8P on 2008-06-13
How old is this card?

---

### Post by Sprocket_dk on 2008-06-13
> **Jose Catre-Vandis said:**
> tvtime is for analog tv only, use kaffiene for dvb as a test, or mplayer if you have a channels.conf file
```
mplayer dvb://
```

post your output from dmesg so we can see what's loaded

dennis@dennis:~$ mplayer dvb://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 6, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://.
DVB CONFIGURATION IS EMPTY, exit
Failed to open dvb://.


Exiting... (End of file)
dennis@dennis:~$ mplayer dvb://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 6, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://.
DVB CONFIGURATION IS EMPTY, exit
Failed to open dvb://.


Exiting... (End of file)

dmesg:
[   27.483216] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.525330] NET: Registered protocol family 8
[   27.525333] NET: Registered protocol family 20
[   27.525457] hpet clockevent registered
[   27.525463] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   27.525469] hpet0: 3 64-bit timers, 14318180 Hz
[   27.526506] AppArmor: AppArmor Filesystem Enabled
[   27.529949] Time: tsc clocksource has been installed.
[   27.541356] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   27.541371] system 00:08: ioport range 0x290-0x297 has been reserved
[   27.541381] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   27.541384] system 00:09: ioport range 0x800-0x87f has been reserved
[   27.541387] system 00:09: ioport range 0x400-0x41f has been reserved
[   27.541391] system 00:09: ioport range 0x480-0x4bf has been reserved
[   27.541394] system 00:09: ioport range 0x900-0x91f has been reserved
[   27.541397] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   27.541401] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[   27.541405] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[   27.541408] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   27.541416] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   27.541419] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[   27.541432] system 00:0c: iomem range 0xf0000000-0xf3ffffff has been reserved
[   27.541439] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   27.541442] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[   27.541445] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   27.541448] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[   27.541451] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   27.572071] PCI: Bridge: 0000:00:01.0
[   27.572075]   IO window: e000-efff
[   27.572079]   MEM window: dc000000-dfffffff
[   27.572083]   PREFETCH window: e0000000-efffffff
[   27.572087] PCI: Bridge: 0000:00:1c.0
[   27.572090]   IO window: d000-dfff
[   27.572095]   MEM window: disabled.
[   27.572099]   PREFETCH window: disabled.
[   27.572104] PCI: Bridge: 0000:00:1c.4
[   27.572107]   IO window: c000-cfff
[   27.572112]   MEM window: dbf00000-dbffffff
[   27.572116]   PREFETCH window: disabled.
[   27.572121] PCI: Bridge: 0000:00:1c.5
[   27.572124]   IO window: b000-bfff
[   27.572129]   MEM window: dbe00000-dbefffff
[   27.572133]   PREFETCH window: disabled.
[   27.572141] PCI: Bridge: 0000:00:1e.0
[   27.572145]   IO window: 8000-afff
[   27.572150]   MEM window: d8000000-dbdfffff
[   27.572154]   PREFETCH window: disabled.
[   27.572176] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.572182] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   27.572202] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.572208] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.572228] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   27.572233] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   27.572254] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[   27.572259] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   27.572271] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   27.572283] NET: Registered protocol family 2
[   27.609329] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.609637] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   27.610258] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   27.610566] TCP: Hash tables configured (established 131072 bind 65536)
[   27.610568] TCP reno registered
[   27.621416] checking if image is initramfs... it is
[   28.026347] Switched to high resolution mode on CPU 0
[   28.028803] Switched to high resolution mode on CPU 1
[   28.239054] Freeing initrd memory: 7311k freed
[   28.239752] audit: initializing netlink socket (disabled)
[   28.239765] audit(1213391704.364:1): initialized
[   28.240073] highmem bounce pool size: 64 pages
[   28.242988] VFS: Disk quotas dquot_6.5.1
[   28.243089] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.243265] io scheduler noop registered
[   28.243269] io scheduler anticipatory registered
[   28.243271] io scheduler deadline registered
[   28.243286] io scheduler cfq registered (default)
[   28.243381] Boot video device is 0000:05:00.0
[   28.243532] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.243583] assign_interrupt_mode Found MSI capability
[   28.243623] Allocate Port Service[0000:00:01.0:pcie00]
[   28.243733] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.243780] assign_interrupt_mode Found MSI capability
[   28.243817] Allocate Port Service[0000:00:1c.0:pcie00]
[   28.243868] Allocate Port Service[0000:00:1c.0:pcie02]
[   28.243984] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   28.244033] assign_interrupt_mode Found MSI capability
[   28.244075] Allocate Port Service[0000:00:1c.4:pcie00]
[   28.244187] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   28.244240] assign_interrupt_mode Found MSI capability
[   28.244278] Allocate Port Service[0000:00:1c.5:pcie00]
[   28.244651] isapnp: Scanning for PnP cards...
[   28.599726] isapnp: No Plug & Play device found
[   28.642563] Real Time Clock Driver v1.12ac
[   28.642700] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.642843] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.643771] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.645165] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.645263] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   28.645476] PNP: No PS/2 controller found. Probing ports directly.
[   28.648241] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.648248] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.672762] mice: PS/2 mouse device common for all mice
[   28.672939] EISA: Probing bus 0 at eisa.0
[   28.672960] Cannot allocate resource for EISA slot 5
[   28.672963] Cannot allocate resource for EISA slot 6
[   28.672966] Cannot allocate resource for EISA slot 7
[   28.672968] Cannot allocate resource for EISA slot 8
[   28.672971] EISA: Detected 0 cards.
[   28.672974] cpuidle: using governor ladder
[   28.672977] cpuidle: using governor menu
[   28.673066] NET: Registered protocol family 1
[   28.673099] Using IPI No-Shortcut mode
[   28.673133] registered taskstats version 1
[   28.673267]   Magic number: 12:922:297
[   28.673279]   hash matches device ttywe
[   28.673315] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   28.673317] EDD information not available.
[   28.673519] Freeing unused kernel memory: 368k freed
[   29.926131] fuse init (API version 7.9)
[   29.947845] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  C8, should be D2 [20070126]
[   29.947855] ACPI: SSDT 7FF88840, 02DE (r1    AMI   CPU1PM        1 INTL  2002026)
[   29.948394] ACPI: Processor [CPU1] (supports 8 throttling states)
[   29.948474] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  75, should be C5 [20070126]
[   29.948482] ACPI: SSDT 7FF88B20, 02E6 (r1    AMI   CPU2PM        1 INTL  2002026)
[   29.948987] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.949004] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   30.251898] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   30.251903] Copyright (c) 1999-2006 Intel Corporation.
[   30.251968] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.251983] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   30.271871] usbcore: registered new interface driver usbfs
[   30.271897] usbcore: registered new interface driver hub
[   30.275873] usbcore: registered new device driver usb
[   30.283701] USB Universal Host Controller Interface driver v3.0
[   30.310401] e1000: 0000:03:00.0: e1000_probe: The EEPROM Checksum Is Not Valid
[   30.330510] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   30.330523] e1000: probe of 0000:03:00.0 failed with error -5
[   30.330839] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[   30.330850] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   30.330854] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   30.331072] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   30.331103] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00005000
[   30.331259] usb usb1: configuration #1 chosen from 1 choice
[   30.331291] hub 1-0:1.0: USB hub found
[   30.331298] hub 1-0:1.0: 2 ports detected
[   30.378916] SCSI subsystem initialized
[   30.395806] libata version 3.00 loaded.
[   30.435731] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   30.435743] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   30.435748] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   30.435774] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   30.435805] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00005400
[   30.435932] usb usb2: configuration #1 chosen from 1 choice
[   30.435962] hub 2-0:1.0: USB hub found
[   30.435969] hub 2-0:1.0: 2 ports detected
[   30.455927] Floppy drive(s): fd0 is 1.44M
[   30.474208] FDC 0 is a post-1991 82077
[   30.539574] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   30.539591] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   30.539596] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   30.539623] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   30.539652] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00005800
[   30.539784] usb usb3: configuration #1 chosen from 1 choice
[   30.539813] hub 3-0:1.0: USB hub found
[   30.539820] hub 3-0:1.0: 2 ports detected
[   30.643448] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 20
[   30.643465] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   30.643469] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   30.643496] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   30.643524] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00006000
[   30.643650] usb usb4: configuration #1 chosen from 1 choice
[   30.643678] hub 4-0:1.0: USB hub found
[   30.643684] hub 4-0:1.0: 2 ports detected
[   30.675339] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   30.747492] sata_sil24 0000:02:00.0: version 1.1
[   30.747506] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
[   30.747524] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   30.747592] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   30.797788] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[dbdfb800-dbdfbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   30.799955] scsi0 : sata_sil24
[   30.800055] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[   30.800100] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.800115] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   30.800144] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[   30.800168] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   30.800180] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   30.800922] scsi1 : sata_sil24
[   30.800966] ata1: SATA max UDMA/100 host m128@0xdbeffc00 port 0xdbef8000 irq 17
[   30.800971] ata2: SATA max UDMA/100 host m128@0xdbeffc00 port 0xdbefa000 irq 17
[   30.859644] usb 1-1: configuration #1 chosen from 1 choice
[   30.862581] hub 1-1:1.0: USB hub found
[   30.864541] hub 1-1:1.0: 3 ports detected
[   31.210683] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   31.384043] usb 1-2: configuration #1 chosen from 1 choice
[   31.625201] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   31.800340] usb 3-2: configuration #1 chosen from 1 choice
[   32.018206] usb 1-1.2: new full speed USB device using uhci_hcd and address 4
[   32.068857] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000500bb1]
[   32.162140] usb 1-1.2: configuration #1 chosen from 1 choice
[   32.373792] usb 1-1.3: new full speed USB device using uhci_hcd and address 5
[   32.517739] usb 1-1.3: configuration #1 chosen from 1 choice
[   32.875768] ata1: SATA link down (SStatus 0 SControl 0)
[   34.954367] ata2: SATA link down (SStatus 0 SControl 0)
[   34.954454] pata_it821x: controller in pass through mode.
[   34.954483] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 19 (level, low) -> IRQ 20
[   34.954526] PCI: Setting latency timer of device 0000:01:04.0 to 64
[   34.954600] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[   34.954613] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   34.954617] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   34.954657] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   34.954773] scsi2 : pata_it821x
[   34.954833] scsi3 : pata_it821x
[   34.954869] ata3: PATA max UDMA/133 cmd 0xa400 ctl 0xa000 bmdma 0x9000 irq 20
[   34.954872] ata4: PATA max UDMA/133 cmd 0x9800 ctl 0x9400 bmdma 0x9008 irq 20
[   34.958558] ehci_hcd 0000:00:1d.7: debug port 1
[   34.958566] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   34.958571] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd7fff800
[   34.973324] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.973470] usb usb5: configuration #1 chosen from 1 choice
[   34.973502] hub 5-0:1.0: USB hub found
[   34.973509] hub 5-0:1.0: 8 ports detected
[   35.304874] ata4.00: ATA-7: WDC WD1600JB-00REA0, 20.00K20, max UDMA/100
[   35.304880] ata4.00: 312581808 sectors, multi 0: LBA48 
[   35.313421] ata4.00: configured for UDMA/100
[   35.313590] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600JB-00R 20.0 PQ: 0 ANSI: 5
[   35.318217] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 21 (level, low) -> IRQ 21
[   35.318253] skge 1.13 addr 0xdbdfc000 irq 21 chip Yukon-Lite rev 9
[   35.318572] skge eth0: addr 00:13:d4:7b:46:77
[   35.337252] ata_piix 0000:00:1f.1: version 2.12
[   35.337272] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[   35.337313] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   35.339196] scsi4 : ata_piix
[   35.339254] scsi5 : ata_piix
[   35.340654] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   35.340657] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   35.355650] Driver 'sd' needs updating - please use bus_type methods
[   35.355830] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   35.355848] sd 3:0:0:0: [sda] Write Protect is off
[   35.355852] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.355877] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.355936] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   35.355951] sd 3:0:0:0: [sda] Write Protect is off
[   35.355954] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.355979] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.355982]  sda: sda1 < sda5 sda6 > sda2
[   35.397986] sd 3:0:0:0: [sda] Attached SCSI disk
[   35.403269] sd 3:0:0:0: Attached scsi generic sg0 type 0
[   35.673897] ata5.01: ATAPI: PLEXTOR DVDR   PX-712A, 1.07, max UDMA/33
[   35.693528] usb 1-1: USB disconnect, address 2
[   35.693532] usb 1-1.2: USB disconnect, address 4
[   35.693536] usbcore: registered new interface driver hiddev
[   35.693748] usb 1-1.3: USB disconnect, address 5
[   35.836647] ata5.01: configured for UDMA/33
[   35.932212] usb 1-1: new full speed USB device using uhci_hcd and address 6
[   36.003120] scsi 4:0:1:0: CD-ROM            PLEXTOR  DVDR   PX-712A   1.07 PQ: 0 ANSI: 5
[   36.003227] scsi 4:0:1:0: Attached scsi generic sg1 type 5
[   36.003254] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   36.003279] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[   36.003321] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   36.003386] scsi6 : ata_piix
[   36.003438] scsi7 : ata_piix
[   36.003474] ata7: SATA max UDMA/133 cmd 0x7800 ctl 0x7400 bmdma 0x6400 irq 23
[   36.003477] ata8: SATA max UDMA/133 cmd 0x7000 ctl 0x6800 bmdma 0x6408 irq 23
[   36.113587] usb 1-1: configuration #1 chosen from 1 choice
[   36.116502] hub 1-1:1.0: USB hub found
[   36.118470] hub 1-1:1.0: 3 ports detected
[   36.164276] ata7.00: ATA-7: WDC WD1600JS-00NCB1, 10.02E02, max UDMA/133
[   36.164280] ata7.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   36.173184] ata7.00: configured for UDMA/133
[   36.223959] usb 1-2: USB disconnect, address 3
[   36.338140] scsi 6:0:0:0: Direct-Access     ATA      WDC WD1600JS-00N 10.0 PQ: 0 ANSI: 5
[   36.338229] sd 6:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   36.338246] sd 6:0:0:0: [sdb] Write Protect is off
[   36.338249] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   36.338275] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.338332] sd 6:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   36.338347] sd 6:0:0:0: [sdb] Write Protect is off
[   36.338350] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   36.338376] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.338380]  sdb: sdb1 sdb2
[   36.344390] sd 6:0:0:0: [sdb] Attached SCSI disk
[   36.344430] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   36.362156] Driver 'sr' needs updating - please use bus_type methods
[   36.365130] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   36.365134] Uniform CD-ROM driver Revision: 3.20
[   36.365198] sr 4:0:1:0: Attached scsi CD-ROM sr0
[   36.464595] usb 1-2: new low speed USB device using uhci_hcd and address 7
[   36.522454] Attempting manual resume
[   36.522458] swsusp: Resume From Partition 8:6
[   36.522460] PM: Checking swsusp image.
[   36.522644] PM: Resume from disk failed.
[   36.563499] kjournald starting.  Commit interval 5 seconds
[   36.563513] EXT3-fs: mounted filesystem with ordered data mode.
[   36.637996] usb 1-2: configuration #1 chosen from 1 choice
[   36.640970] usb 3-2: USB disconnect, address 2
[   36.879114] usb 3-2: new low speed USB device using uhci_hcd and address 3
[   37.062276] usb 3-2: configuration #1 chosen from 1 choice
[   37.093609] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input1
[   37.102902] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   37.117166] input: SealieComputing RetroPad as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input2
[   37.117191] input,hidraw1: USB HID v1.00 Gamepad [SealieComputing RetroPad] on usb-0000:00:1d.2-2
[   37.117207] usbcore: registered new interface driver usbhid
[   37.117211] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   37.280137] usb 1-1.2: new full speed USB device using uhci_hcd and address 8
[   37.432082] usb 1-1.2: configuration #1 chosen from 1 choice
[   37.443048] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input3
[   37.454471] input,hidraw2: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.2
[   37.655696] usb 1-1.3: new full speed USB device using uhci_hcd and address 9
[   37.806624] usb 1-1.3: configuration #1 chosen from 1 choice
[   37.822622] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input4
[   37.854061] input,hiddev96,hidraw3: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.3
[   43.749505] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   43.796200] iTCO_vendor_support: vendor-support=0
[   43.824972] parport_pc 00:07: reported by Plug and Play ACPI
[   43.825089] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   43.860098] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.876713] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.899101] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   43.899191] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   43.899226] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   44.041684] intel_rng: FWH not detected
[   44.199471] input: Power Button (FF) as /devices/virtual/input/input6
[   44.258774] ACPI: Power Button (FF) [PWRF]
[   44.258864] input: Power Button (CM) as /devices/virtual/input/input7
[   44.318535] ACPI: Power Button (CM) [PWRB]
[   44.351658] Linux video capture interface: v2.00
[   44.666679] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   44.666770] cx88[0]: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18,autodetected]
[   44.666773] cx88[0]: TV tuner type 4, Radio tuner type -1
[   44.671284] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   44.710385] Linux agpgart interface v0.102
[   44.784085] nvidia: module license 'NVIDIA' taints kernel.
[   44.814854] tveeprom 0-0050: Hauppauge model 90003, rev C2B0, serial# 3621111
[   44.814859] tveeprom 0-0050: MAC address is 00-0D-FE-37-40-F7
[   44.814862] tveeprom 0-0050: tuner model is Thompson DTT75105 (idx 110, type 4)
[   44.814865] tveeprom 0-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   44.814868] tveeprom 0-0050: audio processor is None (idx 0)
[   44.814870] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[   44.814873] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   44.814875] cx88[0]: hauppauge eeprom: model=90003
[   44.814951] input: cx88 IR (Hauppauge Nova-T DVB-T as /devices/pci0000:00/0000:00:1e.0/0000:01:01.2/input/input8
[   45.117612] cx88[0]/2: cx2388x 8802 Driver Manager
[   45.117633] ACPI: PCI Interrupt 0000:01:01.2[A] -> GSI 22 (level, low) -> IRQ 22
[   45.117645] cx88[0]/2: found at 0000:01:01.2, rev: 5, irq: 22, latency: 64, mmio: 0xd9000000
[   45.117799] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[   45.117809] cx88[0]/0: found at 0000:01:01.0, rev: 5, irq: 22, latency: 64, mmio: 0xd8000000
[   45.117847] cx88[0]/0: registered device video0 [v4l2]
[   45.117874] cx88[0]/0: registered device vbi0
[   45.274433] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   45.274438] cx88/2: registering cx8802 driver, type: dvb access: shared
[   45.274442] cx88[0]/2: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18]
[   45.274446] cx88[0]/2: cx2388x based DVB/ATSC card
[   45.393733] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.393744] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   45.393887] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   45.528643] DVB: registering new adapter (cx88[0])
[   45.528648] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   45.664024] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 23 (level, low) -> IRQ 23
[   45.668148] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:226: Audigy2 value: Special config.
[   46.656821] lp0: using parport0 (interrupt-driven).
[   46.731017] Adding 2048248k swap on /dev/sda6.  Priority:-1 extents:1 across:2048248k
[   47.286744] EXT3 FS on sdb1, internal journal
[   48.150345] kjournald starting.  Commit interval 5 seconds
[   48.150618] EXT3 FS on sdb2, internal journal
[   48.150625] EXT3-fs: mounted filesystem with ordered data mode.
[   49.102881] ip_tables: (C) 2000-2006 Netfilter Core Team
[   49.467029] No dock devices found.
[   52.462988] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   52.462995] apm: disabled - APM is not SMP safe.
[   52.668261] ppdev: user-space parallel port driver
[   52.977022] audit(1213391729.434:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5595 profile="/usr/sbin/cupsd" namespace="default"
[   53.703749] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   53.703757] vboxdrv: Successfully done.
[   53.704286] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   53.704291] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[   54.413183] NET: Registered protocol family 10
[   54.413502] lo: Disabled Privacy Extensions
[   55.493167] skge eth0: enabling interface
[   55.498837] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.401572] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   57.404507] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   58.118595] Bluetooth: Core ver 2.11
[   58.119201] NET: Registered protocol family 31
[   58.119206] Bluetooth: HCI device and connection manager initialized
[   58.119211] Bluetooth: HCI socket layer initialized
[   58.161803] Bluetooth: L2CAP ver 2.9
[   58.161809] Bluetooth: L2CAP socket layer initialized
[   58.167382] Bluetooth: RFCOMM socket layer initialized
[   58.167399] Bluetooth: RFCOMM TTY layer initialized
[   58.167401] Bluetooth: RFCOMM ver 1.8
[   58.398753] usb 1-1.1: new full speed USB device using uhci_hcd and address 10
[   58.542724] usb 1-1.1: configuration #1 chosen from 1 choice
[   58.654999] Bluetooth: HCI USB driver ver 2.9
[   58.656756] usbcore: registered new interface driver hci_usb
[   58.713814] cx88[0]/0: unknown tv audio mode [0]
[   59.618655] NET: Registered protocol family 17
[   76.884707] eth0: no IPv6 routers present
[  151.626046] usb 1-1: USB disconnect, address 6
[  151.626054] usb 1-1.1: USB disconnect, address 10
[  151.878481] usb 1-1.2: USB disconnect, address 8
[  151.910449] usb 1-1.3: USB disconnect, address 9
[  152.608840] usb 1-1: new full speed USB device using uhci_hcd and address 11
[  152.785929] usb 1-1: configuration #1 chosen from 1 choice
[  152.789704] hub 1-1:1.0: USB hub found
[  152.790797] hub 1-1:1.0: 3 ports detected
[  153.101434] usb 1-1.2: new full speed USB device using uhci_hcd and address 12
[  153.252389] usb 1-1.2: configuration #1 chosen from 1 choice
[  153.264630] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input9
[  153.304091] input,hidraw2: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.2
[  153.512957] usb 1-1.3: new full speed USB device using uhci_hcd and address 13
[  153.663917] usb 1-1.3: configuration #1 chosen from 1 choice
[  153.680975] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input10
[  153.763759] input,hiddev96,hidraw3: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.3

---

### Post by Sprocket_dk on 2008-06-13
> **wolfen69 said:**
> if you cant get it to work, consider doing what i do. install mythbuntu, and then install ubuntu-desktop. that way you can have myth tv and regular ubuntu.

I've have ubuntu 8.04 and installed mythtv. It works great in mythtv, but not in mplayer, kaffeine or me-tv

---

### Post by Sprocket_dk on 2008-06-13
> **Ringi said:**
> How old is this card?

Just bought it. I don't know when it was released, but its the new version of the card and it has the Conexant CX chipset

---

### Post by xc3RnbFO8P on 2008-06-13
> New Version: This model is based on a Conexant CX2388x.

It should be automagically detected and work "out of the box" since kernel 2.6.12 and onwards. If by chance it is not, try getting the card to work by simply running "modprobe cx88_dvb". 
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T_PCI]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T_PCI")

---

### Post by Sprocket_dk on 2008-06-13
> **Ringi said:**
> [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T_PCI]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T_PCI")

You've allready suggested that. It still does'nt work :( [http://ubuntuforums.org/showpost.php?p=5177299&postcount=3](http://ubuntuforums.org/showpost.php?p=5177299&postcount=3)

---

### Post by xc3RnbFO8P on 2008-06-13
> 44.814854] tveeprom 0-0050: Hauppauge model 90003, rev C2B0, serial# 3621111
[ 44.814859] tveeprom 0-0050: MAC address is 00-0D-FE-37-40-F7
[ 44.814862] tveeprom 0-0050: tuner model is [COLOR="Red"]Thompson DTT75105[/COLOR] (idx 110, type 4)
[ 44.814865] tveeprom 0-0050: TV standards [COLOR="Red"]ATSC/DVB Digital[/COLOR] (eeprom 0x80)
[ 44.814868] tveeprom 0-0050: audio processor is None (idx 0)
[ 44.814870] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[ 44.814873] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[ 44.814875] cx88[0]: hauppauge eeprom: [COLOR="Red"]model=90003[/COLOR]
[ 44.814951] input: cx88 IR (Hauppauge Nova-T DVB-T as /devices/pci0000:00/0000:00:1e.0/0000:01:01.2/input/input8
[ 45.117612] cx88[0]/2: cx2388x 8802 Driver Manager

confusing
> 
 features: fullts
 board markings: sticker [COLOR="Red"]"DVB-T 90002"[/COLOR], board "900000-03, HannStar MV-4 94V-O"
 card driver: cx88
 interface: PCI
 PCI device id: 14f1:8804
 PCI subsystem id: 0070:9002
 EEPROM: 128 bytes @0x50
 Bridge: Conexant CX2388x
 frontend 1:
   tin box: [COLOR="Red"]Thomson dtt7592[/COLOR]
   frontend driver: cx22702
   demodulator location: separate
   demodulator: Conexant cx22702 @0x43
   PLL: Infineon tua6034 @0x61
  

---

### Post by Sprocket_dk on 2008-06-13
tell me about it. :confused:

---

### Post by Sprocket_dk on 2008-06-13
[http://en.wikipedia.org/wiki/Hauppauge_Computer_Works](http://en.wikipedia.org/wiki/Hauppauge_Computer_Works)

scrool down to: Table of products. Thomson DTT75105 is the tuner on Nova-t PCI (90003)

---

### Post by xc3RnbFO8P on 2008-06-13
Do you have a ATSC TV station in your neighborhood?

---

### Post by xc3RnbFO8P on 2008-06-13
Nova-t PCI (reason why it doesnt work 9000**[COLOR="Red"]3[/COLOR]**) ?	Thomson DTT75105 	PCI

CX2388x
	
No analog (don't work with Tvtime)

DVB-T (CX22702)

---

### Post by Sprocket_dk on 2008-06-13
I guess. You can see it here: [http://vhaf.dk/index.php/572129](http://vhaf.dk/index.php/572129) (its in danish)

---

### Post by Sprocket_dk on 2008-06-13
But it should work in kaffeine, me-tv or mplayer.

---

### Post by xc3RnbFO8P on 2008-06-13
In Denmark we use DVB-T MPEG2
2010 or 2011 we will change it to 
ATSC MPEG4. (Maybe your Tv card will work then)
 > TV broadcasting end-to-end system based on ATSC, MPEG-4 and MPEG-7
Did you buy DVB-T TV? :)

---

### Post by Jose Catre-Vandis on 2008-06-13
Well, you are obviously loading modules for your card!

have your tried installing dvb-utils from synaptic or ```
sudo apt-get install dvb-utils
``` if you run the scan utility, this should evidence the finding of dvb channels. You can also create a channels.conf to run mplayer with

---

### Post by wolfen69 on 2008-06-14
try vlc player. go to file>open capture device>DVB>OK

---

### Post by Sprocket_dk on 2008-06-14
> **Ringi said:**
> In Denmark we use DVB-T MPEG2
2010 or 2011 we will change it to 
ATSC MPEG4. (Maybe your Tv card will work then)
 
Did you buy DVB-T TV? :)

The card is DVB-T MPEG 2 based and works in mythtv. I don't own a DVB-T tv yet. For that I'm waiting till year 2011.

---

### Post by Sprocket_dk on 2008-06-14
> **Jose Catre-Vandis said:**
> Well, you are obviously loading modules for your card!

have your tried installing dvb-utils from synaptic or ```
sudo apt-get install dvb-utils
``` if you run the scan utility, this should evidence the finding of dvb channels. You can also create a channels.conf to run mplayer with

I have dvb-utils and I have a channels.conf. How do I open it in mplayer, does it have to be stored in a certiain folder?

---

### Post by Sprocket_dk on 2008-06-14
> **wolfen69 said:**
> try vlc player. go to file>open capture device>DVB>OK

Vlc: 
Unable to open 'dvb://'
Unable to open 'dvb://'
:(

---

### Post by xc3RnbFO8P on 2008-06-14
Can you show the output of channels.conf
in /home/your folder/.me-tv/

---

### Post by Sprocket_dk on 2008-06-14
> **Ringi said:**
> Can you show the output of channels.conf
in /home/your folder/.me-tv/

here you go:

DR2                      (0x0066) 01: PCR == V   V 0x00d3 A 0x00dd (dan) TT 0x00e7 SUB 0x00eb
DR UPDATE / Tegnsprog    (0x0067) 01: PCR == V   V 0x0137 A 0x0141 (dan) TT 0x014b
TV 2 (Nord)              (0x00d3) 01: PCR == V   V 0x083f A 0x0849 (dan) TT 0x0853 AC3 0x084b SUB 0x0857
STB Opdateringer         (0x0051) 0c:                    
DR1                      (0x0065) 01: PCR == V   V 0x006f A 0x0079 (dan) TT 0x0083 SUB 0x0087

---

### Post by xc3RnbFO8P on 2008-06-14
Here is mine:
> TV 2 (Syd):602000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:2111:2121:214
DR1:602000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:111:121:101
DR2:602000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:211:221:102
DR UPDATE / Tegnsprog:602000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:311:321:103
STB Opdateringer:602000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:0:0:81

your should look like this:
> TV 2 (Syd):222000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:2111:2121:214
DR1:222000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:111:121:101
DR2:222000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:211:221:102
DR UPDATE / Tegnsprog:222000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:311:321:103
STB Opdateringer:222000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:0:0:81

You can rename your Channels.conf.back and make new with this.
I use > sudo gedit
and copy/paste and save it as channels.conf

---

### Post by xc3RnbFO8P on 2008-06-14
I am going to work, Ill be back in the evening.
You can also check Xine in Synaptic Package Manager
see if something is missing.

---

### Post by Sprocket_dk on 2008-06-14
In vlc with new channels.conf:

Unable to open 'dvb://'
Unable to open 'dvb://'
Unable to open 'dvb://'
Unable to open 'dvb://'
Unable to open 'dvb:'
Unable to open 'dvb:'
Unable to open 'dvb:'
Unable to open 'dvb:'
Unable to open 'dvb:'
Unable to open 'pvr://'
Unable to open 'dvb://'
Unable to open 'dvb://'
Unable to open 'dvb://'
Unable to open 'dvb://'
Unable to open 'dvb://'
Unable to open 'dvb://'

And in mplayer:

dennis@dennis:~$ mplayer dvb://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 6, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://.
ERROR OPENING FRONTEND DEVICE /dev/dvb/adapter0/frontend0: ERRNO 16
DVB_SET_CHANNEL2, COULDN'T OPEN DEVICES OF CARD: 0, EXIT
ERROR, COULDN'T SET CHANNEL  0: Failed to open dvb://.
Select error: Bad file descriptor


Exiting... (End of file)

---

### Post by xc3RnbFO8P on 2008-06-14
Can you do **modprobe cx88_dvb** 
then **dmesg**
and see if it change something.

Maybe you got this card:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-SE2]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-SE2")

---

### Post by Sprocket_dk on 2008-06-17
I did the modprobe again and its still the same. Dmesg is also the same. I'm pretty shure its the right card as it is printed on the board.

---

### Post by Sprocket_dk on 2008-06-21
Problem solved. :guitar:

As i mentioned earlyer it worked fine in mythtv. Mythtv backend application was running all the time and using the card. I had to stop the mythtv-backend service by:

$ /etc/init.d/mythtv-backend stop

Thanks to all who helped me on the way.

---

### Post by xc3RnbFO8P on 2008-06-21
Tillykke :)

---

### Post by Jose Catre-Vandis on 2008-07-02
> **Sprocket_dk said:**
> Problem solved. :guitar:

As i mentioned earlyer it worked fine in mythtv. Mythtv backend application was running all the time and using the card. I had to stop the mythtv-backend service by:

$ /etc/init.d/mythtv-backend stop

Thanks to all who helped me on the way.

Sigh! :D

---

