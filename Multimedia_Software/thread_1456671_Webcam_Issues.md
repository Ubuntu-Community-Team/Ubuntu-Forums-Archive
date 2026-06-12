---
title: "Webcam Issues"
date: 2010-04-17
forum: Multimedia Software
---

### Post by hopkinsjeni on 2010-04-17
I bought a Dell Inspiron with pre-installed ubuntu. All has been working for the last year and recently my integrated webcam stopped working. I was trying to use it on skype and it did nothing, although the program recognises I have a webcam, I tried cheese and the power light on  my webcam comes on but again the screen does nothing.
I have searched through the forums and couldn't find anything to solve the problem,
Any ideas?

Thank you
Jeni

---

### Post by no2498 on 2010-04-17
open a terminal type gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1 
sorry but you tried cheese and it broke the cam 
now you need skype help

hope this helps

---

### Post by hopkinsjeni on 2010-04-18
Yes I didn't notice the problem until I tried using Skype. 
I tried what you suggested and on each try it said it failed to construct test pipeline, I have no idea what that means!

---

### Post by Linuxforall on 2010-04-18
Is your cam being detected in dmesg?

---

### Post by hopkinsjeni on 2010-04-18
Sorry for being so blonde, what's that?

---

### Post by no2498 on 2010-04-18
he would like you to open a terminal and type, dmesg
copy and paste the out put here

---

### Post by no2498 on 2010-04-18
i just seen you are on 7.04

do you have cheese installed

---

### Post by hopkinsjeni on 2010-04-18
Thanks
It's a bit long

[    8.701217] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    8.701317] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    8.701417] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    8.701517] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    8.701608] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.701729] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.701755] pnp: PnP ACPI init
[    8.701762] ACPI: bus type pnp registered
[    8.737581] pnpacpi: exceeded the max number of mem resources: 12
[    8.737762] pnp: PnP ACPI: found 13 devices
[    8.737764] ACPI: ACPI bus type pnp unregistered
[    8.737767] PnPBIOS: Disabled by ACPI PNP
[    8.737942] PCI: Using ACPI for IRQ routing
[    8.737944] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.815147] NET: Registered protocol family 8
[    8.815148] NET: Registered protocol family 20
[    8.815179] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    8.815182] hpet0: 3 64-bit timers, 14318180 Hz
[    8.816216] AppArmor: AppArmor Filesystem Enabled
[    8.819138] Time: tsc clocksource has been installed.
[    8.819153] Switched to high resolution mode on CPU 0
[    8.827134] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    8.827137] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    8.827144] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    8.827151] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    8.827156] system 00:0a: ioport range 0x900-0x97f has been reserved
[    8.827158] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    8.827160] system 00:0a: ioport range 0x1000-0x1005 has been reserved
[    8.827162] system 00:0a: ioport range 0x1008-0x100f has been reserved
[    8.827167] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    8.827170] system 00:0b: ioport range 0x1006-0x1007 has been reserved
[    8.827172] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
[    8.827174] system 00:0b: ioport range 0x1060-0x107f has been reserved
[    8.827176] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    8.827178] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    8.827180] system 00:0b: ioport range 0x1010-0x102f has been reserved
[    8.827182] system 00:0b: ioport range 0x809-0x809 has been reserved
[    8.827187] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    8.827190] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    8.827192] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    8.827194] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    8.827196] system 00:0c: iomem range 0x100000-0x7f66d7ff could not be reserved
[    8.827198] system 00:0c: iomem range 0x7f66d800-0x7f6fffff could not be reserved
[    8.827201] system 00:0c: iomem range 0x7f700000-0x7f7fffff could not be reserved
[    8.827203] system 00:0c: iomem range 0x7f700000-0x7fefffff could not be reserved
[    8.827205] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    8.827208] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    8.827210] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    8.827212] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    8.857552] PCI: Bridge: 0000:00:1c.0
[    8.857555]   IO window: d000-dfff
[    8.857562]   MEM window: fe800000-fe8fffff
[    8.857566]   PREFETCH window: disabled.
[    8.857572] PCI: Bridge: 0000:00:1c.1
[    8.857573]   IO window: disabled.
[    8.857579]   MEM window: fe700000-fe7fffff
[    8.857583]   PREFETCH window: disabled.
[    8.857589] PCI: Bridge: 0000:00:1c.4
[    8.857592]   IO window: c000-cfff
[    8.857597]   MEM window: fe400000-fe6fffff
[    8.857602]   PREFETCH window: f0000000-f01fffff
[    8.857608] PCI: Bridge: 0000:00:1e.0
[    8.857609]   IO window: disabled.
[    8.857615]   MEM window: fe300000-fe3fffff
[    8.857619]   PREFETCH window: disabled.
[    8.857654] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.857661] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    8.857687] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    8.857693] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    8.857717] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[    8.857723] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    8.857737] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.857747] NET: Registered protocol family 2
[    8.895118] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.895324] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.895827] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.896166] TCP: Hash tables configured (established 131072 bind 65536)
[    8.896168] TCP reno registered
[    8.907202] checking if image is initramfs... it is
[    9.470120] Freeing initrd memory: 7320k freed
[    9.470281] Simple Boot Flag at 0x79 set to 0x1
[    9.470703] audit: initializing netlink socket (disabled)
[    9.470717] audit(1271621349.176:1): initialized
[    9.470903] highmem bounce pool size: 64 pages
[    9.472488] VFS: Disk quotas dquot_6.5.1
[    9.472551] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.472665] io scheduler noop registered
[    9.472667] io scheduler anticipatory registered
[    9.472668] io scheduler deadline registered
[    9.472677] io scheduler cfq registered (default)
[    9.472688] Boot video device is 0000:00:02.0
[    9.472913] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.472976] assign_interrupt_mode Found MSI capability
[    9.473028] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.473058] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.473159] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.473222] assign_interrupt_mode Found MSI capability
[    9.473271] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.473299] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.473408] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    9.473471] assign_interrupt_mode Found MSI capability
[    9.473519] Allocate Port Service[0000:00:1c.4:pcie00]
[    9.473546] Allocate Port Service[0000:00:1c.4:pcie02]
[    9.473777] isapnp: Scanning for PnP cards...
[    9.827691] isapnp: No Plug & Play device found
[    9.849548] Real Time Clock Driver v1.12ac
[    9.849676] hpet_resources: 0xfed00000 is busy
[    9.849714] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.850706] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.850763] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    9.850841] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.865223] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.874932] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.874936] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.874938] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.874939] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.874941] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.886535] mice: PS/2 mouse device common for all mice
[    9.886630] EISA: Probing bus 0 at eisa.0
[    9.886638] Cannot allocate resource for EISA slot 1
[    9.886667] EISA: Detected 0 cards.
[    9.886670] cpuidle: using governor ladder
[    9.886671] cpuidle: using governor menu
[    9.886741] NET: Registered protocol family 1
[    9.886765] Using IPI No-Shortcut mode
[    9.886792] registered taskstats version 1
[    9.886901]   Magic number: 6:79:195
[    9.886922]   hash matches device ttys7
[    9.886928]   hash matches device ttypa
[    9.886983] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.886985] EDD information not available.
[    9.887160] Freeing unused kernel memory: 368k freed
[    9.887176] Write protecting the kernel read-only data: 803k
[    9.918495] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.137520] fuse init (API version 7.9)
[   11.154603] Monitor-Mwait will be used to enter C-1 state
[   11.154606] Monitor-Mwait will be used to enter C-2 state
[   11.154608] Monitor-Mwait will be used to enter C-3 state
[   11.154713] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.154717] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.154730] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
[   11.155808] ACPI: Thermal Zone [THM] (22 C)
[   11.642054] usbcore: registered new interface driver usbfs
[   11.642076] usbcore: registered new interface driver hub
[   11.649443] usbcore: registered new device driver usb
[   11.654805] USB Universal Host Controller Interface driver v3.0
[   11.654856] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 18
[   11.654867] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   11.654871] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   11.655091] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   11.655126] uhci_hcd 0000:00:1a.0: irq 18, io base 0x00006f20
[   11.655241] usb usb1: configuration #1 chosen from 1 choice
[   11.655260] hub 1-0:1.0: USB hub found
[   11.655263] hub 1-0:1.0: 2 ports detected
[   11.757458] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[   11.757470] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   11.757475] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   11.757495] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   11.757529] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00006f00
[   11.757626] usb usb2: configuration #1 chosen from 1 choice
[   11.757645] hub 2-0:1.0: USB hub found
[   11.757648] hub 2-0:1.0: 2 ports detected
[   11.830112] SCSI subsystem initialized
[   11.861382] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[   11.861394] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.861398] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.861418] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   11.861450] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006f80
[   11.861553] usb usb3: configuration #1 chosen from 1 choice
[   11.861574] hub 3-0:1.0: USB hub found
[   11.861577] hub 3-0:1.0: 2 ports detected
[   11.861593] libata version 3.00 loaded.
[   11.965312] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
[   11.965325] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.965329] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.965350] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   11.965381] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006f60
[   11.965483] usb usb4: configuration #1 chosen from 1 choice
[   11.965501] hub 4-0:1.0: USB hub found
[   11.965505] hub 4-0:1.0: 2 ports detected
[   11.997220] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   12.069269] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
[   12.069281] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.069285] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.069306] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   12.069339] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00006f40
[   12.069440] usb usb5: configuration #1 chosen from 1 choice
[   12.069459] hub 5-0:1.0: USB hub found
[   12.069463] hub 5-0:1.0: 2 ports detected
[   12.173307] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 20
[   12.173322] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   12.173326] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   12.173350] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   12.177263] ehci_hcd 0000:00:1a.7: debug port 1
[   12.177270] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   12.177276] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfed1c400
[   12.193077] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.193197] usb usb6: configuration #1 chosen from 1 choice
[   12.193217] hub 6-0:1.0: USB hub found
[   12.193222] hub 6-0:1.0: 4 ports detected
[   12.193875] usb 1-1: unable to read config index 0 descriptor/all
[   12.193880] usb 1-1: can't read configurations, error -71
[   12.297130] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[   12.297148] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.297151] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.297173] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   12.301090] ehci_hcd 0000:00:1d.7: debug port 1
[   12.301096] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.301103] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfed1c000
[   12.317022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.317130] usb usb7: configuration #1 chosen from 1 choice
[   12.317154] hub 7-0:1.0: USB hub found
[   12.317160] hub 7-0:1.0: 6 ports detected
[   12.421115] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.473791] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   12.486319] ahci 0000:00:1f.2: version 3.0
[   12.486350] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   12.486400] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   12.486402] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   12.588840] usb 6-1: new high speed USB device using ehci_hcd and address 2
[   12.725741] usb 6-1: configuration #1 chosen from 1 choice
[   12.788724] Clocksource tsc unstable (delta = -3840968476 ns)
[   12.803950] Time: hpet clocksource has been installed.
[   12.892481] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   12.892484] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   12.892490] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   12.892698] scsi0 : ahci
[   12.892908] scsi1 : ahci
[   12.893029] scsi2 : ahci
[   12.893263] ata1: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 220
[   12.893267] ata2: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb980 irq 220
[   12.893270] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 220
[   12.900201] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc0000bcd8490]
[   12.912651] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   12.913292] ata1.00: ATA-8: ST9120817AS, 3.ADB, max UDMA/133
[   12.913294] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   12.913781] ata1.00: configured for UDMA/133
[   12.920405] ata2: SATA link down (SStatus 0 SControl 0)
[   12.927427] ata3: SATA link down (SStatus 0 SControl 300)
[   12.927533] scsi 0:0:0:0: Direct-Access     ATA      ST9120817AS      3.AD PQ: 0 ANSI: 5
[   12.928274] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   12.928308] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.928321] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   12.931133] ata_piix 0000:00:1f.1: version 2.12
[   12.931150] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   12.931183] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.931565] scsi3 : ata_piix
[   12.931905] scsi4 : ata_piix
[   12.932467] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   12.932469] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   12.937443] Driver 'sd' needs updating - please use bus_type methods
[   12.940160] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   12.940172] sd 0:0:0:0: [sda] Write Protect is off
[   12.940174] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.940188] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.940232] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   12.940240] sd 0:0:0:0: [sda] Write Protect is off
[   12.940242] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.940254] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.940258]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   13.009143] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.014403] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.264426] ata4.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D400, max UDMA/33
[   13.336624] ata4.00: configured for UDMA/33
[   13.336676] ata5: port disabled. ignoring.
[   13.337375] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D400 PQ: 0 ANSI: 5
[   13.337443] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   13.345274] Driver 'sr' needs updating - please use bus_type methods
[   13.352323] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   13.352327] Uniform CD-ROM driver Revision: 3.20
[   13.352371] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   13.507890] Attempting manual resume
[   13.507893] swsusp: Resume From Partition 8:5
[   13.507895] PM: Checking swsusp image.
[   13.508070] PM: Resume from disk failed.
[   13.520031] EXT3-fs: INFO: recovery required on readonly filesystem.
[   13.520035] EXT3-fs: write access will be enabled during recovery.
[   15.306621] kjournald starting.  Commit interval 5 seconds
[   15.306634] EXT3-fs: sda3: orphan cleanup on readonly fs
[   15.306640] ext3_orphan_cleanup: deleting unreferenced inode 5742757
[   15.306657] ext3_orphan_cleanup: deleting unreferenced inode 180243
[   15.306663] ext3_orphan_cleanup: deleting unreferenced inode 180232
[   15.306667] ext3_orphan_cleanup: deleting unreferenced inode 180231
[   15.306671] ext3_orphan_cleanup: deleting unreferenced inode 180230
[   15.306675] ext3_orphan_cleanup: deleting unreferenced inode 180229
[   15.306678] ext3_orphan_cleanup: deleting unreferenced inode 180228
[   15.306682] EXT3-fs: sda3: 7 orphan inodes deleted
[   15.306683] EXT3-fs: recovery complete.
[   15.323992] EXT3-fs: mounted filesystem with ordered data mode.
[   25.651798] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.416529] Linux agpgart interface v0.102
[   26.461332] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.508188] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.751699] iTCO_vendor_support: vendor-support=0
[   26.789400] input: PS/2 Mouse as /devices/virtual/input/input3
[   26.803030] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   26.837877] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input4
[   26.859472] agpgart: Detected an Intel 965GM Chipset.
[   26.859737] agpgart: Detected 7676K stolen memory.
[   26.875858] agpgart: AGP aperture is 256M @ 0xe0000000
[   27.013007] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.013064] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   27.013101] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.023505] ACPI: AC Adapter [AC] (on-line)
[   27.231251] ACPI: Battery Slot [BAT0] (battery present)
[   27.231350] input: Lid Switch as /devices/virtual/input/input5
[   27.248485] ACPI: Lid Switch [LID]
[   27.248553] input: Power Button (CM) as /devices/virtual/input/input6
[   27.279208] ACPI: Power Button (CM) [PBTN]
[   27.279261] input: Sleep Button (CM) as /devices/virtual/input/input7
[   27.311185] ACPI: Sleep Button (CM) [SBTN]
[   27.319333] ACPI: WMI-Acer: Mapper loaded
[   27.388214] ricoh-mmc: Ricoh MMC Controller disabling driver
[   27.388217] ricoh-mmc: Copyright(c) Philip Langdale
[   27.388286] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   27.388299] ricoh-mmc: Controller is now disabled.
[   27.466202] sdhci: Secure Digital Host Controller Interface driver
[   27.466205] sdhci: Copyright(c) Pierre Ossman
[   27.466248] sdhci: SDHCI controller found at 0000:02:09.1 [1180:0822] (rev 22)
[   27.466278] ACPI: PCI Interrupt 0000:02:09.1[B] -> GSI 18 (level, low) -> IRQ 21
[   27.466344] mmc0: SDHCI at 0xfe3ff400 irq 21 DMA
[   27.954750] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input8
[   27.978794] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   27.978945] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input9
[   28.002791] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   28.683461] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
[   28.683487] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.941414] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[   29.274154] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   29.274158] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   29.401964] Linux video capture interface: v2.00
[   29.565095] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   29.565449] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   29.597894] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb6/6-1/6-1:1.0/input/input10
[   29.613827] usbcore: registered new interface driver uvcvideo
[   29.613831] USB Video Class driver (SVN r217)
[   31.089074] ttySHSF0 at MMIO 0x0 (irq = 0) is a Conexant HSF softmodem (HDA-14f12c06:14f1000f-0)
[   31.320968] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.320983] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   31.321021] sky2 0000:09:00.0: v1.20 addr 0xfe8fc000 irq 16 Yukon-FE+ (0xb8) rev 0
[   31.321409] sky2 eth0: addr 00:21:9b:f3:bf:01
[   31.321586] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   31.321600] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   31.321616] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   31.393302] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   31.394706] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   31.585523] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[   31.585593] input: 3945ABG as /devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/input/input11
[   31.843580] lp: driver loaded but no devices found
[   32.006312] Adding 2016116k swap on /dev/sda5.  Priority:-1 extents:1 across:2016116k
[   32.551576] EXT3 FS on sda3, internal journal
[   33.667678] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.142313] No dock devices found.
[   35.481735] NET: Registered protocol family 10
[   35.482101] lo: Disabled Privacy Extensions
[   37.669913] apm: BIOS not found.
[   37.952753] ppdev: user-space parallel port driver
[   38.234376] audit(1271621383.545:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5402 profile="/usr/sbin/cupsd" namespace="default"
[   39.979770] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   39.979903] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[   40.180621] Registered led device: iwl-phy0:radio
[   40.180639] Registered led device: iwl-phy0:assoc
[   40.180690] Registered led device: iwl-phy0:RX
[   40.180704] Registered led device: iwl-phy0:TX
[   40.187961] Bluetooth: Core ver 2.11
[   40.189968] NET: Registered protocol family 31
[   40.189972] Bluetooth: HCI device and connection manager initialized
[   40.189976] Bluetooth: HCI socket layer initialized
[   40.208215] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.227297] Bluetooth: L2CAP ver 2.9
[   40.227302] Bluetooth: L2CAP socket layer initialized
[   40.247224] sky2 eth0: enabling interface
[   40.251570] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.292847] Bluetooth: RFCOMM socket layer initialized
[   40.293036] Bluetooth: RFCOMM TTY layer initialized
[   40.293039] Bluetooth: RFCOMM ver 1.8
[   44.350525] [drm] Initialized drm 1.1.0 20060810
[   44.353255] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.353263] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   44.353326] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  197.954205] NET: Registered protocol family 17
[  200.488595] wlan0: Initial auth_alg=0
[  200.488601] wlan0: direct probe to AP 00:24:d2:7d:1f:0f try 1
[  200.490914] wlan0 direct probe responded
[  200.490918] wlan0: authenticate with AP 00:24:d2:7d:1f:0f
[  200.492689] wlan0: RX authentication from 00:24:d2:7d:1f:0f (alg=0 transaction=2 status=0)
[  200.492692] wlan0: authenticated
[  200.492694] wlan0: associate with AP 00:24:d2:7d:1f:0f
[  200.494964] wlan0: RX AssocResp from 00:24:d2:7d:1f:0f (capab=0x411 status=0 aid=1)
[  200.494968] wlan0: associated
[  200.496730] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  203.479830] usb 7-4: new high speed USB device using ehci_hcd and address 2
[  204.607630] usb 7-4: configuration #1 chosen from 1 choice
[  204.858346] usbcore: registered new interface driver libusual
[  204.981873] Initializing USB Mass Storage driver...
[  204.983423] scsi5 : SCSI emulation for USB Mass Storage devices
[  204.985924] usbcore: registered new interface driver usb-storage
[  204.985931] USB Mass Storage support registered.
[  204.986323] usb-storage: device found at 2
[  204.986325] usb-storage: waiting for device to settle before scanning
[  209.980334] usb-storage: device scan complete
[  209.981331] scsi 5:0:0:0: Direct-Access     Lexar    JD FireFly       1100 PQ: 0 ANSI: 0 CCS
[  209.991548] sd 5:0:0:0: [sdb] 15663104 512-byte hardware sectors (8020 MB)
[  209.992796] sd 5:0:0:0: [sdb] Write Protect is off
[  209.992800] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  209.992802] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  209.993912] sd 5:0:0:0: [sdb] 15663104 512-byte hardware sectors (8020 MB)
[  209.994914] sd 5:0:0:0: [sdb] Write Protect is off
[  209.994918] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  209.994919] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  209.994924]  sdb: sdb1
[  209.995977] sd 5:0:0:0: [sdb] Attached SCSI disk
[  209.996015] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  216.783723] wlan0: no IPv6 routers present
[  454.931184] /usr/bin/soundc[6983]: segfault at 00000004 eip 080e89d5 esp bfc522e0 error 4
jeni@dell-desktop:~$

---

### Post by no2498 on 2010-04-18
have you restarted the computer after you did what i ask ?
and try it again

see if you can use wxcam
getdeb has it also
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

and do not try cheese and skype yet
lets git the cam back first

---

### Post by hopkinsjeni on 2010-04-19
My pc wouldn't let me install the app.
Yes I have cheese installed it was on my pc when I bought it

---

### Post by no2498 on 2010-04-19
ah cheese it not working well now days
im not much better off than you
you need some thing to see the cam in/on not cheese or skype
try the cam in ekiga softphone
not that you need to use it in it
we just need to get the cam on/up so it comes on

---

### Post by arpoodle on 2010-04-20
I've had similar issues.
Dell Latitude E6400
Linux 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

Webcam was working fine until a couple of days ago.
gstreamer-properties shows 4 options for video:
- test input
- video for linux (v4l)
- video for linux2 (v4l2)
- Custom

None of them work, with the error
"cannot identify device '/dev/video[]'"

As I'd run gstreamer-properties from the command line, I've got some more verbose error messages there:

```
:/dev$ sudo gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc2]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(482): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src4:
system error: No such file or directory]

```

It's proving a pain, since I work from home and use the cam for videoconferencing both with skype and other apps.

---

### Post by no2498 on 2010-04-20
i have seen this file but cant find it on the computer and know i installed it

it looks like the file you need for skype

this is not it but looks like
lib v4l so v4l2 so

you may get by with the same file they use in skype
take skype out and put in cheese

btw cheese has all the settings for webcams now days 

so you may need to go bug cheese

---

### Post by hopkinsjeni on 2010-04-21
Ok,
so I have tried using Ekiga, as recommended by one of these replies, it didn't work, the program stopped responding as soon as I tried to view webcam.
I am still absolutely clueless, any other advice out there?
Jeni

---

### Post by no2498 on 2010-04-21
can you find and install guvcvideo,xawtv

look in the usb see if you have had any bad unmounts

---

### Post by hopkinsjeni on 2010-04-21
I can't fidn the file you suggested and I haven't had any bad unmounts as far as I know

---

### Post by no2498 on 2010-04-21
look in the system, administration, synaptic package manager, type in, webcam

---

### Post by hopkinsjeni on 2010-05-10
Couldn't find that package in the list. I feel I am being very blonde about this whole thing, there must be something simple i am missing

---

### Post by no2498 on 2010-05-10
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 

see if that helps with cheese
open a terminal copy and past it

then look for this in synaptic
libv4l/v4l1compat.so

or this
libv4l/v4l2compat.so

---

### Post by hopkinsjeni on 2010-06-19
jeni@dell-desktop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/jeni/.gnome2/cheese/media/0004.ogg'
Reason: Stream contains no data..

** (cheese:13488): WARNING **: could not load /home/jeni/.gnome2/cheese/media/0004.ogg (application/ogg)



Any Ideas??

---

### Post by no2498 on 2010-06-20
im sorry i cant help any more than i have

it looks like to me you may need to install a new op sys

or look in the old ?'s

i had to go back 3 years to get mine running the first time on 710

an did you try it in xawtv

---

### Post by hopkinsjeni on 2010-06-20
Thank you for your help 2498, it was much appreciated, I shall keep trying.

---

### Post by no2498 on 2010-06-21
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

see if that helps

---

### Post by no2498 on 2010-06-22
is the cam pluged in the back of the computer
move it to the front and do not use a hub
if in the front try the other plug

---

### Post by hopkinsjeni on 2010-06-22
It's an integrated cam, that's why i can't understand the problem. I am very blonde on this whole issue.
Thank you for being such a help, it is much appreciated

---

### Post by Linuxforall on 2010-06-22
Not all integrated cams are supported, if its a RICOH as is common on SONY Vaios, you need to compile a driver for it which is available.

---

### Post by hopkinsjeni on 2010-06-23
Oh Ok. It did used to work, just stopped one day. I have a dell inspirion, pre-installed with Linux

---

