---
title: "Avermedia AverTV Hybrid+FM Volar A828 Issues"
date: 2008-05-24
forum: Multimedia Software
---

### Post by thormania on 2008-05-24
Hello,

I've recently purchased the Avermedia A828 thinking it was completely compatible with Linux - Unfortunately it doesn't seem to be so (in Hardy at least) as after installing the drivers my system will lockup and be unresponsive indefinately.

It will try to scan etc in programs for a period and be recognized fine but someway through scanning the computer will lock.

Also sometimes if it's plugged in the the driver is loaded some apps just crash such as Terminal.  The driver is listed as compatible with 7.10 - but it installs fine.  Could this mean that the driver just needs to be updated to Hardy? 

I'm not sure what data to give you guys to help diagnose this (I'm a bit of a noob) But thank you in advance for any help!

---

### Post by xc3RnbFO8P on 2008-05-25
You could try this drivers:
[http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver]("http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver")

> AVerTV USB Hybrid+FM Driver Install Howto


1. Launch command terminal
2. Act as root to install driver. There are two ways to do this.

  (1) Use sudo. Recommended for Ubuntu Linux users. You need to type your own
      password:

      $ sudo ./AVERMEDIA-Linux-x86-A828-0.18-beta.sh
      Password:"Type your password here"

  (2) Use su. Recommended for most users. You need to type root password:

      $ su
      Password:"Type root password here"
      # ./AVERMEDIA-Linux-x86-A828-0.18-beta.sh

---

### Post by thormania on 2008-05-25
> **Ringi said:**
> You could try this drivers:
[http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver]("http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver")

I've tried exactly those drivers - they seem to give me grief :(.

---

### Post by xc3RnbFO8P on 2008-05-25
Show the output of
**dmesg** in terminal

---

### Post by thormania on 2008-05-25
> **Ringi said:**
> Show the output of
**dmesg** in terminal


```
[   21.161765] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   21.161770] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   21.161776] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   21.161781] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   21.161787] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   21.161801] system 00:06: ioport range 0x680-0x69f has been reserved
[   21.161806] system 00:06: ioport range 0x800-0x80f has been reserved
[   21.161811] system 00:06: ioport range 0x1000-0x107f has been reserved
[   21.161816] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   21.161821] system 00:06: ioport range 0x1640-0x164f has been reserved
[   21.161826] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[   21.161831] system 00:06: ioport range 0xff00-0xff7f has been reserved
[   21.161841] system 00:07: ioport range 0x6a0-0x6af has been reserved
[   21.161846] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[   21.162571] PCI: Bridge: 0000:00:1c.0
[   21.162574]   IO window: disabled.
[   21.162581]   MEM window: disabled.
[   21.162587]   PREFETCH window: disabled.
[   21.162594] PCI: Bridge: 0000:00:1c.1
[   21.162596]   IO window: disabled.
[   21.162604]   MEM window: d0000000-d00fffff
[   21.162610]   PREFETCH window: disabled.
[   21.162629] PCI: Bus 6, cardbus bridge: 0000:05:04.0
[   21.162632]   IO window: 00002400-000024ff
[   21.162638]   IO window: 00002800-000028ff
[   21.162645]   PREFETCH window: 68000000-6bffffff
[   21.162652]   MEM window: 6c000000-6fffffff
[   21.162659] PCI: Bridge: 0000:00:1e.0
[   21.162663]   IO window: 2000-2fff
[   21.162670]   MEM window: d0100000-d01fffff
[   21.162678]   PREFETCH window: disabled.
[   21.162721] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   21.162730] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.162762] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   21.162770] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.162785] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   21.162793] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.162815] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.162834] NET: Registered protocol family 2
[   21.197797] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   21.198940] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   21.202493] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   21.203502] TCP: Hash tables configured (established 262144 bind 65536)
[   21.203505] TCP reno registered
[   21.213855] checking if image is initramfs... it is
[   22.052219] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   22.566021] Freeing initrd memory: 7510k freed
[   22.571410] Simple Boot Flag at 0x36 set to 0x1
[   22.572922] audit: initializing netlink socket (disabled)
[   22.572949] audit(1211716596.468:1): initialized
[   22.576810] VFS: Disk quotas dquot_6.5.1
[   22.576929] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   22.577129] io scheduler noop registered
[   22.577132] io scheduler anticipatory registered
[   22.577135] io scheduler deadline registered
[   22.577326] io scheduler cfq registered (default)
[   22.577341] Boot video device is 0000:00:02.0
[   22.579514] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.579590] assign_interrupt_mode Found MSI capability
[   22.579651] Allocate Port Service[0000:00:1c.0:pcie00]
[   22.579717] Allocate Port Service[0000:00:1c.0:pcie02]
[   22.579870] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   22.579943] assign_interrupt_mode Found MSI capability
[   22.580001] Allocate Port Service[0000:00:1c.1:pcie00]
[   22.580060] Allocate Port Service[0000:00:1c.1:pcie02]
[   22.626011] Real Time Clock Driver v1.12ac
[   22.626349] hpet_resources: 0xfed00000 is busy
[   22.626393] Linux agpgart interface v0.102
[   22.626397] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.628346] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.628457] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.628621] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.651054] i8042.c: Detected active multiplexing controller, rev 1.1.
[   22.672379] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.672386] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   22.672391] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   22.672395] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   22.672399] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   22.683176] mice: PS/2 mouse device common for all mice
[   22.683244] cpuidle: using governor ladder
[   22.683247] cpuidle: using governor menu
[   22.683474] NET: Registered protocol family 1
[   22.683638] registered taskstats version 1
[   22.683802]   Magic number: 8:927:934
[   22.683942] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   22.683947] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.683950] EDD information not available.
[   22.683960] Freeing unused kernel memory: 320k freed
[   22.730991] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   24.023668] fuse init (API version 7.9)
[   24.056453] ACPI: SSDT 5F6949EE, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   24.057170] ACPI: SSDT 5F694481, 04E8 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   24.061127] Monitor-Mwait will be used to enter C-1 state
[   24.061132] Monitor-Mwait will be used to enter C-2 state
[   24.061135] Monitor-Mwait will be used to enter C-3 state
[   24.061345] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   24.061354] ACPI: Processor [CPU0] (supports 8 throttling states)
[   24.063962] ACPI: SSDT 5F694BE4, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   24.064320] ACPI: SSDT 5F694969, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   24.065852] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   24.065861] ACPI: Processor [CPU1] (supports 8 throttling states)
[   24.073005] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   24.073919] ACPI: Thermal Zone [TZ00] (64 C)
[   24.524267] usbcore: registered new interface driver usbfs
[   24.524302] usbcore: registered new interface driver hub
[   24.524345] usbcore: registered new device driver usb
[   24.525663] USB Universal Host Controller Interface driver v3.0
[   24.525732] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   24.525747] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.525753] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.526082] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   24.526119] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[   24.526309] usb usb1: configuration #1 chosen from 1 choice
[   24.526345] hub 1-0:1.0: USB hub found
[   24.526353] hub 1-0:1.0: 2 ports detected
[   24.599142] SCSI subsystem initialized
[   24.608026] libata version 3.00 loaded.
[   24.629945] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   24.629963] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   24.629969] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   24.630007] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   24.630046] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   24.630214] usb usb2: configuration #1 chosen from 1 choice
[   24.630252] hub 2-0:1.0: USB hub found
[   24.630261] hub 2-0:1.0: 2 ports detected
[   24.666379] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   24.733770] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   24.733794] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   24.733800] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   24.733840] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   24.733880] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   24.734065] usb usb3: configuration #1 chosen from 1 choice
[   24.734103] hub 3-0:1.0: USB hub found
[   24.734112] hub 3-0:1.0: 2 ports detected
[   24.837614] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   24.837635] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   24.837641] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   24.837680] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   24.837719] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[   24.837893] usb usb4: configuration #1 chosen from 1 choice
[   24.837930] hub 4-0:1.0: USB hub found
[   24.837938] hub 4-0:1.0: 2 ports detected
[   24.869417] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   24.941480] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   24.941537] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.941555] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   24.942853] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   24.943732] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.943741] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.943806] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   24.947734] ehci_hcd 0000:00:1d.7: debug port 1
[   24.947744] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.947755] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0544000
[   24.993158] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.993333] usb usb5: configuration #1 chosen from 1 choice
[   24.993371] hub 5-0:1.0: USB hub found
[   24.993382] hub 5-0:1.0: 8 ports detected
[   25.099528] 8139cp 0000:05:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   25.099535] 8139cp 0000:05:01.0: Try the "8139too" driver instead.
[   25.101781] PCI: Enabling device 0000:05:06.0 (0000 -> 0002)
[   25.101797] ACPI: PCI Interrupt 0000:05:06.0[A] -> GSI 22 (level, low) -> IRQ 22
[   25.101809] PCI: Setting latency timer of device 0000:05:06.0 to 64
[   25.154909] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0100800-d0100fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   25.159306] 8139too Fast Ethernet driver 0.9.28
[   25.166828] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[   25.166847] PCI: Setting latency timer of device 0000:05:01.0 to 64
[   25.167932] eth0: RealTek RTL8139 at 0x2000, 00:0f:b0:cc:0f:21, IRQ 21
[   25.167936] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   25.168093] ata_piix 0000:00:1f.2: version 2.12
[   25.168101] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   25.320626] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   25.320680] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   25.320841] scsi0 : ata_piix
[   25.320921] scsi1 : ata_piix
[   25.322345] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   25.322350] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   25.399497] usb 1-2: device not accepting address 2, error -71
[   25.484957] ata1.00: ATA-7: HTS541080G9SA00, MB4IC60R, max UDMA/100
[   25.484964] ata1.00: 156301488 sectors, multi 16: LBA48 
[   25.500904] ata1.00: configured for UDMA/100
[   25.516656] Clocksource tsc unstable (delta = -74704819 ns)
[   25.549720] ata2.00: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HA01, max UDMA/33
[   25.571118] ata2.00: configured for UDMA/33
[   25.571302] scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9SA00  MB4I PQ: 0 ANSI: 5
[   25.574189] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HA01 PQ: 0 ANSI: 5
[   25.583850] Driver 'sd' needs updating - please use bus_type methods
[   25.583976] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   25.583995] sd 0:0:0:0: [sda] Write Protect is off
[   25.583999] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.584028] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.584101] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   25.584117] sd 0:0:0:0: [sda] Write Protect is off
[   25.584121] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.584149] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.584155]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   25.608259]  sda1 sda2 < sda5 >
[   25.634136] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.641553] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.641587] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   25.654847] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.654854] Uniform CD-ROM driver Revision: 3.20
[   25.654937] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   25.881758] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   25.907897] Attempting manual resume
[   25.907903] swsusp: Resume From Partition 8:5
[   25.907905] PM: Checking swsusp image.
[   25.908212] PM: Resume from disk failed.
[   25.927344] EXT3-fs: INFO: recovery required on readonly filesystem.
[   25.927350] EXT3-fs: write access will be enabled during recovery.
[   25.978033] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f688f40192b]
[   26.010875] usb 5-1: configuration #1 chosen from 1 choice
[   26.356380] usb 5-4: new high speed USB device using ehci_hcd and address 5
[   26.453950] kjournald starting.  Commit interval 5 seconds
[   26.453984] EXT3-fs: sda1: orphan cleanup on readonly fs
[   26.453995] ext3_orphan_cleanup: deleting unreferenced inode 1482764
[   26.454037] EXT3-fs: sda1: 1 orphan inode deleted
[   26.454040] EXT3-fs: recovery complete.
[   26.475011] EXT3-fs: mounted filesystem with ordered data mode.
[   26.490859] usb 5-4: configuration #1 chosen from 1 choice
[   26.965503] usb 5-7: new high speed USB device using ehci_hcd and address 7
[   27.106388] usb 5-7: configuration #1 chosen from 1 choice
[   27.106666] hub 5-7:1.0: USB hub found
[   27.106852] hub 5-7:1.0: 3 ports detected
[   27.448646] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   27.611942] usb 1-2: configuration #1 chosen from 1 choice
[   27.851953] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   28.029226] usb 2-1: configuration #1 chosen from 1 choice
[   28.271220] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   28.432543] usb 3-2: configuration #1 chosen from 1 choice
[   28.634769] usb 5-7.2: new low speed USB device using ehci_hcd and address 8
[   28.733643] usb 5-7.2: configuration #1 chosen from 1 choice
[   38.858965] intel_rng: FWH not detected
[   38.895364] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   38.930931] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.964682] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.129934] iTCO_vendor_support: vendor-support=0
[   39.166125] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   39.248141] agpgart: Detected an Intel 945GM Chipset.
[   39.249811] agpgart: Detected 7932K stolen memory.
[   39.279382] agpgart: AGP aperture is 256M @ 0xc0000000
[   39.432768] input: Power Button (FF) as /devices/virtual/input/input3
[   39.484380] ACPI: Power Button (FF) [PWRF]
[   39.484497] input: Lid Switch as /devices/virtual/input/input4
[   39.518563] ACPI: Lid Switch [LID0]
[   39.518677] input: Power Button (CM) as /devices/virtual/input/input5
[   39.563518] ACPI: Power Button (CM) [PWRB]
[   39.588362] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04753/0x200000
[   39.659895] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   39.712369] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   39.712422] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   39.891091] Yenta: CardBus bridge found at 0000:05:04.0 [17aa:2075]
[   39.891125] Yenta: Using CSCINT to route CSC interrupts to PCI
[   39.891128] Yenta: Routing CardBus interrupts to PCI
[   39.891135] Yenta TI: socket 0000:05:04.0, mfunc 0x01111c12, devctl 0x44
[   40.010457] ricoh-mmc: Ricoh MMC Controller disabling driver
[   40.010494] ricoh-mmc: Copyright(c) Philip Langdale
[   40.123392] Yenta: ISA IRQ mask 0x0c58, PCI irq 16
[   40.123398] Socket status: 30000006
[   40.123403] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   40.123410] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   40.123414] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff
[   40.123556] sdhci: Secure Digital Host Controller Interface driver
[   40.123559] sdhci: Copyright(c) Pierre Ossman
[   40.162670] ricoh-mmc: Ricoh MMC controller found at 0000:05:06.2 [1180:0843] (rev 1)
[   40.162688] ricoh-mmc: Controller is now disabled.
[   40.162744] sdhci: SDHCI controller found at 0000:05:06.1 [1180:0822] (rev 19)
[   40.162765] PCI: Enabling device 0000:05:06.1 (0000 -> 0002)
[   40.162774] ACPI: PCI Interrupt 0000:05:06.1[B] -> GSI 23 (level, low) -> IRQ 23
[   40.163622] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   40.163637] PCI: Setting latency timer of device 0000:05:06.1 to 64
[   40.163726] mmc0: SDHCI at 0xd0100400 irq 23 DMA
[   40.305108] video: Unknown symbol video_output_register
[   40.305155] video: Unknown symbol video_output_unregister
[   40.356712] ACPI: AC Adapter [ACAD] (on-line)
[   40.410790] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   40.461891] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   40.462387] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   40.509852] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   40.631218] ACPI: Battery Slot [BAT1] (battery present)
[   40.829340] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   40.829346] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   40.829520] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   40.829538] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   40.830391] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   40.980342] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   40.981253] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   41.244113] Bluetooth: Core ver 2.11
[   41.268742] NET: Registered protocol family 31
[   41.268747] Bluetooth: HCI device and connection manager initialized
[   41.268754] Bluetooth: HCI socket layer initialized
[   41.373360] Bluetooth: HCI USB driver ver 2.9
[   41.374845] usbcore: registered new interface driver hci_usb
[   41.403085] usbcore: registered new interface driver hiddev
[   41.406793] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input9
[   41.444216] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[   41.449476] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input10
[   41.500159] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1
[   41.503722] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7.2/5-7.2:1.0/input/input11
[   41.568004] input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-7.2
[   41.571067] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7.2/5-7.2:1.1/input/input12
[   41.572224] Linux video capture interface: v2.00
[   41.627340] a828: module license 'AVerMedia TECHNOLOGIES, Inc.' taints kernel.
[   41.627656] a828: no version for "snd_pcm_new" found: kernel tainted.
[   41.627882] Symbol usb_register_driver is being used by a non-GPL module, which will not be allowed in the future
[   41.627886] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
[   41.628862] Symbol usb_deregister is being used by a non-GPL module, which will not be allowed in the future
[   41.628866] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
[   41.628924] input,hidraw3: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-7.2
[   41.628951] usbcore: registered new interface driver usbhid
[   41.628956] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.632708] USB Hybrid+FM Volar version 0.18 loaded
[   41.749531] A828 registered V4L2 device video0[video]
[   41.749570] A828 registered V4L2 device video1[audio]
[   41.749609] A828 registered V4L2 device radio0[radio]
[   41.749644] A828 registered V4L2 device vbi0[vbi]
[   41.750090] A828 registered ALSA sound interface
[   41.750102] DVB: registering new adapter (A828[0] DVB-T)
[   41.750106] A828[0] DVB-T registered DVB adapter 0
[   41.750483] DVB: registering frontend 0 (A828[0] DVB-T)...
[   41.853288] usbcore: registered new interface driver USB Hybrid+FM Volar
[   43.165074] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   43.168861] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   44.499858] lp: driver loaded but no devices found
[   44.788123] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   45.353511] EXT3 FS on sda1, internal journal
[   46.651618] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.844103]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[   46.844113]  CIFS VFS: cifs_mount failed w/return code = -101
[   47.179383] No dock devices found.
[   48.566708] ppdev: user-space parallel port driver
[   48.762582] audit(1211716624.450:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5243 profile="/usr/sbin/cupsd" namespace="default"
[   76.133465] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   76.234820] Bluetooth: L2CAP ver 2.9
[   76.234827] Bluetooth: L2CAP socket layer initialized
[   76.320540] Bluetooth: RFCOMM socket layer initialized
[   76.320570] Bluetooth: RFCOMM TTY layer initialized
[   76.320573] Bluetooth: RFCOMM ver 1.8
[   78.609742] NET: Registered protocol family 17
[   79.197876] [drm] Initialized drm 1.1.0 20060810
[   79.206305] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   79.206318] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   79.206407] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   81.994112] NET: Registered protocol family 10
[   81.994486] lo: Disabled Privacy Extensions
[   81.995838] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   92.606719] eth0: no IPv6 routers present
[   95.623330] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP: 
[   95.623340]  [<ffffffff8827f6dd>] :snd_pcm:snd_pcm_open_substream+0x4d/0x90
[   95.623362] PGD 47290067 PUD 5c30c067 PMD 0 
[   95.623368] Oops: 0000 [1] SMP 
[   95.623373] CPU 0 
[   95.623376] Modules linked in: ipv6 i915 drm af_packet binfmt_misc rfcomm l2cap ppdev acpi_cpufreq cpufreq_stats cpufreq_userspace cpufreq_conservative cpufreq_ondemand freq_table cpufreq_powersave sbs sbshc container dock nls_cp437 cifs iptable_filter ip_tables x_tables sbp2 parport_pc lp parport arc4 ecb blkcipher joydev pcmcia a828(PF) dvb_core videodev v4l2_common v4l1_compat usbhid hci_usb hid bluetooth snd_hda_intel snd_pcm_oss snd_mixer_oss iwl3945 iwlwifi_mac80211 snd_pcm snd_page_alloc snd_hwdep cfg80211 battery snd_seq_dummy video ac output snd_seq_oss sdhci snd_seq_midi ricoh_mmc mmc_core yenta_socket rsrc_nonstatic snd_rawmidi pcmcia_core snd_seq_midi_event snd_seq snd_timer snd_seq_device button snd intel_agp serio_raw iTCO_wdt iTCO_vendor_support soundcore evdev shpchp pci_hotplug pcspkr psmouse ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_piix 8139too ata_generic ohci1394 ieee1394 8139cp mii pata_acpi libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   95.623496] Pid: 6059, comm: pulseaudio Tainted: PF       2.6.24-17-generic #1
[   95.623500] RIP: 0010:[<ffffffff8827f6dd>]  [<ffffffff8827f6dd>] :snd_pcm:snd_pcm_open_substream+0x4d/0x90
[   95.623517] RSP: 0018:ffff810043d23d48  EFLAGS: 00010246
[   95.623521] RAX: 0000000000000000 RBX: 0000000000000000 RCX: ffff81005d081b90
[   95.623524] RDX: 0000000000000000 RSI: 0000000000000002 RDI: ffff81005d0e6260
[   95.623528] RBP: ffff810043d23db0 R08: 00000000000f4240 R09: 0000000000000011
[   95.623532] R10: 0000000000000000 R11: 0000000000000000 R12: ffff81005c5f4200
[   95.623535] R13: ffff8100473339c0 R14: ffff810043d23db0 R15: 0000000000000001
[   95.623540] FS:  00007f35060376f0(0000) GS:ffffffff805b9000(0000) knlGS:0000000000000000
[   95.623544] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   95.623547] CR2: 0000000000000000 CR3: 00000000471b0000 CR4: 00000000000006e0
[   95.623551] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   95.623555] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   95.623559] Process pulseaudio (pid: 6059, threadinfo ffff810043d22000, task ffff81004ec537a0)
[   95.623562] Stack:  0000000000000246 ffffffff80253ccc ffff81005d0e6260 00000000fffffff2
[   95.623571]  ffff81005c5f4368 ffffffff8827f845 ffff81005cc39b00 ffff81005c5f4380
[   95.623577]  ffffffff00000000 ffff81004ec537a0 ffffffff80233e20 ffff81005c5f4388
[   95.623584] Call Trace:
[   95.623595]  [<ffffffff80253ccc>] add_wait_queue+0x1c/0x60
[   95.623614]  [<ffffffff8827f845>] :snd_pcm:snd_pcm_open+0x125/0x200
[   95.623627]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
[   95.623637]  [<ffffffff80466d39>] mutex_lock+0x9/0x20
[   95.623652]  [<ffffffff802b5dd0>] chrdev_open+0x0/0x1d0
[   95.623668]  [<ffffffff881cf5f5>] :snd:snd_open+0x95/0x190
[   95.623679]  [<ffffffff802b5e91>] chrdev_open+0xc1/0x1d0
[   95.623695]  [<ffffffff802b0bfb>] __dentry_open+0xdb/0x200
[   95.623709]  [<ffffffff802b0e2a>] do_filp_open+0x3a/0x50
[   95.623731]  [<ffffffff802b0a67>] get_unused_fd_flags+0x77/0x120
[   95.623746]  [<ffffffff802b0e9a>] do_sys_open+0x5a/0xf0
[   95.623758]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[   95.623780] 
[   95.623781] 
[   95.623782] Code: ff 10 85 c0 89 c3 78 29 48 8b 44 24 10 80 88 80 01 00 00 01 
[   95.623799] RIP  [<ffffffff8827f6dd>] :snd_pcm:snd_pcm_open_substream+0x4d/0x90
[   95.623814]  RSP <ffff810043d23d48>
[   95.623817] CR2: 0000000000000000
[   95.623827] ---[ end trace ad473b3c36d21ce3 ]---
[  111.047899] CPU0 attaching NULL sched-domain.
[  111.047909] CPU1 attaching NULL sched-domain.
[  111.075489] CPU0 attaching sched-domain:
[  111.075501]  domain 0: span 03
[  111.075505]   groups: 01 02
[  111.075511]   domain 1: span 03
[  111.075515]    groups: 03
[  111.075522] CPU1 attaching sched-domain:
[  111.075526]  domain 0: span 03
[  111.075529]   groups: 02 01
[  111.075535]   domain 1: span 03
[  111.075538]    groups: 03

```

---

### Post by xc3RnbFO8P on 2008-05-25
Did you try Tvtime?

---

### Post by thormania on 2008-05-25
Sure have it will scan for channels and then crash and lock the entire system.  Kaffine will scan and locate channel and then become un-responsive when trying to play the stream.

Generally speaking if the thing is plugged in the system is much less responsive and much less stable.  I don't know whats going on :(.

---

### Post by xc3RnbFO8P on 2008-05-25
Its nothing to do but wait and hope that this Tv tuner get supported soon.

---

### Post by thormania on 2008-05-25
Looks like i might have to - I guess the new kernal additions etc in hardy are the problem here - what I find crazy is that it really does mess with my system.  It makes it much, much less reliable.  The driver must be fairly intrusive to cause so many issues with my system.  I wonder is anyone else could try it and see if it's just as bad for them.

---

### Post by thormania on 2008-05-27
Avermedia emailed me new 0.19 version drivers ! Once I get home i'll give it a shot and report back and upload them here incase somebody else needs them too!

---

### Post by gazglusk on 2008-06-02
Hi, I'm new here, but thought you might be interested, I have just tried drivers 0.18 and 0.19 on both Hardy kernels and I get the same problems as above....it's a shame when you go backwards with a new system , when things went just fine with 7.10 !!! Good luck all, hope we find a way

---

### Post by thormania on 2008-06-02
> **gazglusk said:**
> Hi, I'm new here, but thought you might be interested, I have just tried drivers 0.18 and 0.19 on both Hardy kernels and I get the same problems as above....it's a shame when you go backwards with a new system , when things went just fine with 7.10 !!! Good luck all, hope we find a way

Agreed - I can't fix it I've given up for now :(.

---

### Post by Ryozanpaku Tiger on 2008-06-02
Guys, did I get it right that there are no problems with 7.10? I would like to buy Avermedia AverTV Hybrid+FM Volar A828 and I have 7.10 installed.

---

### Post by marrabld on 2008-06-02
I wouldn't say no issues.  I got it working no worriesin7.10 but after a reboot.  it just stopped working, i am now using 8.04 and i am having no luck at all.  I am searching for an answer with no luck so far. :(

---

### Post by dinoj on 2008-06-07
> **marrabld said:**
> I wouldn't say no issues.  I got it working no worriesin7.10 but after a reboot.  it just stopped working, i am now using 8.04 and i am having no luck at all.  I am searching for an answer with no luck so far. :(
It is very important to unplug A828 stick before shutdown/reboot. If I do not do this, the stick stops to work after reboot. I use eeeXubuntu (7.10 kernel 2.6.22) on my eeepc . I have tested also tuner with Ubuntu 8.04. There was problem to compile 0.18 driver,  but new 0.19 seems to be OK with DVB-T channels, but  crashes with analog channels.

---

### Post by vivedekananda on 2008-07-01
I have recently bought this card (usb) and it doesn't work on my dell 1501 laptop with kubuntu 7.10.
The card usually stops working right after it is initialized, the blue led goes on but thats about it. Also the /dev/video(radio) stays locked
until reboot after the initialization.
Funny thing is that when I boot into recovery mode the radio-player tool seems to work. I am able to init the device tune a frequency and close the device(the blue led goes off). I can't hear the radio though, so maybe no data stream is received from the tuner or it might be just a problem with the /dev/dsp not working correcly in the recovery mode, will have to test this.
From this one could deduce that the a828 driver conflicts with "something"
that is only initialized at later stages of the boot sequence, and I suspect that this is a bug in the a828 driver that causes a conflict with a laptop specific device/module (also this might be the same reason the driver doens't work in ubuntu 8.04).

Does someone have this tv card working on a laptop (except of the eeeps)? Or any ideas what can be the problem here (I got no usefull info from dmesg)?

I also tried the card on a desktop machine (with kubuntu 7.10) and there it seems to work well (the fm radio works for sure, couldn't test the digital tv because of no signal but i could scan for channels). I didn't even need to plug/unplug the tv card before/after reboot in order for it to work.

I am going to contact avertv support, to see if they can find out what the problem is.

---

### Post by pidou46 on 2008-10-16
Hi everybody,

Nothing new about this usb tnt ?

---

### Post by backstep on 2008-10-26
Hello guys, I have this tuner too and it works fine without any problems (with DVB-T, I have some issues with FM radio, but DVB is great). What kernel versions do you use? Now I have fedora with 2.6.26.6, drivers by Avermedia (0.19-Beta) doesn't work for kernel >= 2.6.26, couldn't this be your issues? My tuner works before reboot and after too (without unplugging). I've patched this 0.19-Beta drivers available at Avermedia, **PATCH for kernels > 2.6.26** is available at [http://backstep.net/aver/]("http://backstep.net/aver/"), it works fine for me, I can't guarantee it will work for you, but any feedbacks are welcome. Also try to paste some info about your system (kernel version etc.) it must works ;) :cool:

---

### Post by macu on 2008-11-01
Don't you know, where can I find path for kernel 2.6.27 64bit (Ubuntu 8.10 64bit)?

---

### Post by backstep on 2008-11-01
Hi, I think my patch should work for 64bit sources too, do you have some problems with this? post some compile output or something and I'll try to help you. I don't have 2.6.27 kernel yet, but I think there wasn't any major changes which could stop drivers from working.

Regards,

lukash

---

### Post by richi.chen on 2008-11-02
Hi, I've try to build the Avermedia A828 0.19 beta driver on x64 Ubuntu 8.10, and has following compiling errors,

root@ubuntu-x64:~/A828-expert-install# make
mv aver/osdep_dvb.o_shipped aver/osdep_dvb.o_shipped.skip
mv: cannot stat `aver/osdep_dvb.o_shipped': No such file or directory
make: [default] Error 1 (ignored)
make -C /lib/modules/2.6.27-7-generic/source O=/lib/modules/2.6.27-7-generic/build SUBDIRS=`pwd` 
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/richi/A828-expert-install/aver/osdep.o
/home/richi/A828-expert-install/aver/osdep.c:78:27: error: asm/semaphore.h: No such file or directory
/home/richi/A828-expert-install/aver/osdep.c: In function ‘SysPciMapSingle’:
/home/richi/A828-expert-install/aver/osdep.c:944: warning: passing argument 1 of ‘pci_dma_mapping_error’ makes pointer from integer without a cast
/home/richi/A828-expert-install/aver/osdep.c:944: error: too few arguments to function ‘pci_dma_mapping_error’
make[3]: *** [/home/richi/A828-expert-install/aver/osdep.o] Error 1
make[2]: *** [_module_/home/richi/A828-expert-install] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

---

### Post by xc3RnbFO8P on 2008-11-02
Did you do:
> sudo apt-get install build-essential

---

### Post by backstep on 2008-11-02
> **richi.chen said:**
> Hi, I've try to build the Avermedia A828 0.19 beta driver on x64 Ubuntu 8.10, and has following compiling errors,

root@ubuntu-x64:~/A828-expert-install# make
mv aver/osdep_dvb.o_shipped aver/osdep_dvb.o_shipped.skip
mv: cannot stat `aver/osdep_dvb.o_shipped': No such file or directory
make: [default] Error 1 (ignored)
make -C /lib/modules/2.6.27-7-generic/source O=/lib/modules/2.6.27-7-generic/build SUBDIRS=`pwd` 
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/richi/A828-expert-install/aver/osdep.o
/home/richi/A828-expert-install/aver/osdep.c:78:27: error: asm/semaphore.h: No such file or directory
/home/richi/A828-expert-install/aver/osdep.c: In function ‘SysPciMapSingle’:
/home/richi/A828-expert-install/aver/osdep.c:944: warning: passing argument 1 of ‘pci_dma_mapping_error’ makes pointer from integer without a cast
/home/richi/A828-expert-install/aver/osdep.c:944: error: too few arguments to function ‘pci_dma_mapping_error’
make[3]: *** [/home/richi/A828-expert-install/aver/osdep.o] Error 1
make[2]: *** [_module_/home/richi/A828-expert-install] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

Hi, I'll try to explain your errors.

1) ```
mv aver/osdep_dvb.o_shipped aver/osdep_dvb.o_shipped.skip
mv: cannot stat `aver/osdep_dvb.o_shipped': No such file or directory
make: [default] Error 1 (ignored)
```
It seems that 64bit drivers sources doesn't contain pre-built osdep_dvb.c, but it really doesn't matter, make was just unable to move it (because it doesn't exist), however error was ignored and file should be compiled by make.

2) You're missing some header files (asm/semaphore.h), in debian pkgs it's in package **linux-kernel-headers**, as this search shows: [http://packages.debian.org/search?searchon=contents&keywords=asm%2Fsemaphore.h&mode=path&suite=stable&arch=any]("http://packages.debian.org/search?searchon=contents&keywords=asm%2Fsemaphore.h&mode=path&suite=stable&arch=any")

3) In kernel >= 2.6.27 function **pci_dma_mapping_error** has been changed. pci_dev argument has been added to the funtion, more information here: [http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6-stable.git;a=commit;h=8d8bb39b9eba32dd70e87fd5ad5c5dd4ba118e06]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6-stable.git;a=commit;h=8d8bb39b9eba32dd70e87fd5ad5c5dd4ba118e06"), I've made a patch for this, you can apply to already patched sources (by first patch), this will solve these error msgs: ```
/home/richi/A828-expert-install/aver/osdep.c: In function ‘SysPciMapSingle’:
/home/richi/A828-expert-install/aver/osdep.c:944: error: too few arguments to function ‘pci_dma_mapping_error’
```
Patch is located here: [http://backstep.net/aver/AVERMEDIA-Linux-x86-A828-0.19-beta_patch_2.6.26_beta27.diff]("http://backstep.net/aver/AVERMEDIA-Linux-x86-A828-0.19-beta_patch_2.6.26_beta27.diff")

However I still don't have machine running 2.6.27 kernel, hope this will helps, I'll try to test it myself ASAP.

Regards,

lukash

---

### Post by backstep on 2008-11-02
Ok guys, I'm sorry about my previous post, there are more changes in 2.6.27, for example in v4l:

```
/root/aver/A828-expert-install/aver/osdep_v4l2.c: In function ‘SysVideoDevRegister’:
/root/aver/A828-expert-install/aver/osdep_v4l2.c:185: error: incompatible types in assignment
/root/aver/A828-expert-install/aver/osdep_v4l2.c:192: error: ‘struct video_device’ has no member named ‘type’
/root/aver/A828-expert-install/aver/osdep_v4l2.c:192: error: ‘VID_TYPE_CAPTURE’ undeclared (first use in this function)
/root/aver/A828-expert-install/aver/osdep_v4l2.c:192: error: (Each undeclared identifier is reported only once
/root/aver/A828-expert-install/aver/osdep_v4l2.c:192: error: for each function it appears in.)
/root/aver/A828-expert-install/aver/osdep_v4l2.c:192: error: ‘VID_TYPE_TUNER’ undeclared (first use in this function)
/root/aver/A828-expert-install/aver/osdep_v4l2.c:196: error: ‘struct video_device’ has no member named ‘type’
/root/aver/A828-expert-install/aver/osdep_v4l2.c:196: error: ‘VID_TYPE_TELETEXT’ undeclared (first use in this function)
/root/aver/A828-expert-install/aver/osdep_v4l2.c:200: error: ‘struct video_device’ has no member named ‘type’
/root/aver/A828-expert-install/aver/osdep_v4l2.c:204: error: ‘struct video_device’ has no member named ‘type’
/root/aver/A828-expert-install/aver/osdep_v4l2.c: In function ‘video_ioctl’:
/root/aver/A828-expert-install/aver/osdep_v4l2.c:335: error: implicit declaration of function ‘video_usercopy’

```

I'm working on some patch for 2.6.27 on my newly installed Ubuntu 2.6.27, I'll let u know.

Regards,

lukash

---

### Post by backstep on 2008-11-04
Hello guys!

New beta patch has been released at: [http://backstep.net/aver/AVERMEDIA-Linux-x86-A828-0.19-beta_patch_2.6.26_2.6.27BETA.diff]("http://backstep.net/aver/AVERMEDIA-Linux-x86-A828-0.19-beta_patch_2.6.26_2.6.27BETA.diff")

I can compile it on 2.6.27-7-generic (Ubuntu 8.10 x86) without problems.

More info available at: [http://backstep.net/aver/readme.txt]("http://backstep.net/aver/readme.txt")

Any feedbacks are welcome.

Regards,

lukash

---

### Post by Azelight on 2008-11-07
> **backstep said:**
> Hello guys!

New beta patch has been released at: [http://backstep.net/aver/AVERMEDIA-Linux-x86-A828-0.19-beta_patch_2.6.26_2.6.27BETA.diff]("http://backstep.net/aver/AVERMEDIA-Linux-x86-A828-0.19-beta_patch_2.6.26_2.6.27BETA.diff")

I can compile it on 2.6.27-7-generic (Ubuntu 8.10 x86) without problems.

More info available at: [http://backstep.net/aver/readme.txt]("http://backstep.net/aver/readme.txt")

Any feedbacks are welcome.

Regards,

lukash

Hi, thanks for the patch, it works fine on my x86_64 box with kernel 2.6.27-zen3

My steps:

First download the official x86_64 driver and the patch to somewhere, then change directory to there

# unzip A828_Installer_x64_0.19Beta_080528.zip

# cd A828_Installer_x64_0.19-Beta

# tail -n +115 AVERMEDIA-Linux-x64-A828-0.19-beta.sh | tar jxvf -

# cp installer/kdep/2.6.25/OBJ-x64/_prebuild.o_shipped installer/src/

# cd installer/src

# patch -p1 < ../../../AVERMEDIA-Linux-x86-A828-0.19-beta_patch_2.6.26_2.6.27BETA.diff

# cd ..

# ./installer.sh

And install the driver like ever.

Now plug A828 into USB slot and it works!

---

### Post by backstep on 2008-11-07
Hey!

Thanks for reply, I'm glad it works on x64 too :)

Enjoy watching TV ;)

lukash

---

### Post by macu on 2008-11-08
i try this help from Azelight byt id doesn't work. I can't install this patched driver for II 64bit :-(

```

/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:88:20: error: dvbdev.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:89:19: error: demux.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:90:23: error: dvb_demux.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:91:20: error: dmxdev.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:92:24: error: dvb_filter.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:93:21: error: dvb_net.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:94:28: error: dvb_ringbuffer.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:95:26: error: dvb_frontend.h: No such file or directory
In file included from /home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:101:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:98: warning: ‘struct dvb_frontend_info’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:98: warning: its scope is only this definition or declaration, which is probably not what you want
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:110: error: expected declaration specifiers or ‘...’ before ‘fe_status_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:114: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:115: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:122: warning: ‘struct dvb_diseqc_master_cmd’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:123: warning: ‘struct dvb_diseqc_slave_reply’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:124: error: expected declaration specifiers or ‘...’ before ‘fe_sec_mini_cmd_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:125: error: expected declaration specifiers or ‘...’ before ‘fe_sec_tone_mode_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:126: error: expected declaration specifiers or ‘...’ before ‘fe_sec_voltage_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:119: warning: data definition has no type or storage class
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:119: warning: type defaults to ‘int’ in declaration of ‘DVB_DEFINE_MOD_OPT_ADAPTER_NR’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:119: warning: parameter names (without types) in function declaration
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:127: error: field ‘fe’ has incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:128: error: field ‘dmxdev_sw’ has incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:130: error: field ‘demux_sw’ has incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:133: error: field ‘hw_frontend’ has incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:135: error: field ‘mem_frontend’ has incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:146: error: field ‘feedlock’ has incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:159: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:160: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:162: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:164: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:165: error: expected declaration specifiers or ‘...’ before ‘fe_status_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:171: warning: ‘struct dvb_frontend_tune_settings’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:178: warning: ‘struct dvb_diseqc_master_cmd’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:179: warning: ‘struct dvb_diseqc_slave_reply’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:180: error: expected declaration specifiers or ‘...’ before ‘fe_sec_mini_cmd_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:181: error: expected declaration specifiers or ‘...’ before ‘fe_sec_tone_mode_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:182: error: expected declaration specifiers or ‘...’ before ‘fe_sec_voltage_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘SysDVBInit’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:224: error: implicit declaration of function ‘init_MUTEX’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:241: error: conflicting types for ‘SysDVBRegisterFrontend’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.h:98: error: previous declaration of ‘SysDVBRegisterFrontend’ was here
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘SysDVBRegisterFrontend’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:254: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:269: error: ‘FE_QPSK’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:269: error: (Each undeclared identifier is reported only once
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:269: error: for each function it appears in.)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:269: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:328: error: implicit declaration of function ‘dvb_register_frontend’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘SysDVBRegisterAdapter’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:375: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_adapter’ 
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:386: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:388: error: implicit declaration of function ‘dvb_register_adapter’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:388: error: ‘THIS_MODULE’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:388: error: ‘adapter_nr’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:416: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:442: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_demux’ 
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:451: error: ‘DMX_TS_FILTERING’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:452: error: ‘DMX_SECTION_FILTERING’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:453: error: ‘DMX_MEMORY_BASED_FILTERING’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:456: error: implicit declaration of function ‘dvb_dmx_init’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:469: error: implicit declaration of function ‘dvb_dmxdev_init’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:483: error: ‘DMX_FRONTEND_0’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:499: error: ‘DMX_MEMORY_FE’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:537: error: implicit declaration of function ‘dvb_dmxdev_release’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:539: error: implicit declaration of function ‘dvb_dmx_release’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:545: error: implicit declaration of function ‘dvb_unregister_adapter’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘SysDVBUnRegisterFrontend’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:566: error: implicit declaration of function ‘dvb_unregister_frontend’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘SysDVBFeedTSPackets’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:609: error: implicit declaration of function ‘dvb_dmx_swfilter_packets’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:626: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:626: error: conflicting types for ‘demux_sw_start_feed’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:159: error: previous declaration of ‘demux_sw_start_feed’ was here
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘demux_sw_start_feed’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:628: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:629: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:640: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:668: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:668: error: conflicting types for ‘demux_sw_stop_feed’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:160: error: previous declaration of ‘demux_sw_stop_feed’ was here
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘demux_sw_stop_feed’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:670: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:671: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:698: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:697: error: conflicting types for ‘dvbfe_set_parameters’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:161: error: previous declaration of ‘dvbfe_set_parameters’ was here
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_set_parameters’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:700: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:702: warning: passing argument 2 of ‘SetParameters’ from incompatible pointer type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:706: warning: ‘struct dvb_frontend_parameters’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:705: error: conflicting types for ‘dvbfe_get_parameters’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:163: error: previous declaration of ‘dvbfe_get_parameters’ was here
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_get_parameters’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:708: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:710: warning: passing argument 2 of ‘GetParameters’ from incompatible pointer type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:713: error: expected declaration specifiers or ‘...’ before ‘fe_status_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_read_status’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:715: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:717: error: ‘status’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:717: error: too many arguments to function ‘GetStatus’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_read_ber’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:722: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_read_signal_strength’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:729: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_read_snr’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:736: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_read_ucblocks’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:743: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_init’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:750: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_sleep’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:757: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:763: warning: ‘struct dvb_frontend_tune_settings’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:762: error: conflicting types for ‘dvbfe_get_tune_settings’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:170: error: previous declaration of ‘dvbfe_get_tune_settings’ was here
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_get_tune_settings’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:766: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:767: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:768: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_diseqc_reset_overload’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:777: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:782: warning: ‘struct dvb_diseqc_master_cmd’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:782: error: conflicting types for ‘dvbfe_diseqc_send_master_cmd’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:178: error: previous declaration of ‘dvbfe_diseqc_send_master_cmd’ was here
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_diseqc_send_master_cmd’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:784: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:786: warning: passing argument 2 of ‘DiseqcSendMasterCMD’ from incompatible pointer type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:789: warning: ‘struct dvb_diseqc_slave_reply’ declared inside parameter list
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:789: error: conflicting types for ‘dvbfe_diseqc_recv_slave_reply’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:179: error: previous declaration of ‘dvbfe_diseqc_recv_slave_reply’ was here
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_diseqc_recv_slave_reply’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:791: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:793: warning: passing argument 2 of ‘DiseqcRecvSlaveReply’ from incompatible pointer type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:796: error: expected declaration specifiers or ‘...’ before ‘fe_sec_mini_cmd_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_diseqc_send_burst’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:798: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:800: error: ‘arg’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:800: error: too many arguments to function ‘DiseqcSendBurst’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:803: error: expected declaration specifiers or ‘...’ before ‘fe_sec_tone_mode_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_set_tone’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:805: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:807: error: ‘arg’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:807: error: too many arguments to function ‘SetTone’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:810: error: expected declaration specifiers or ‘...’ before ‘fe_sec_voltage_t’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_set_voltage’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:812: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:814: error: ‘arg’ undeclared (first use in this function)
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:814: error: too many arguments to function ‘SetVoltage’
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: In function ‘dvbfe_enable_high_lnb_voltage’:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:823: error: dereferencing pointer to incomplete type
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c: At top level:
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:834: fatal error: opening dependency file /home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/.osdep_dvb.o.d: Permission denied
compilation terminated.
make[3]: *** [/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.o] Error 1
make[2]: *** [_module_/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

```

---

### Post by backstep on 2008-11-08
Hi,

look at the errors on the top of text you've pasted:

```
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:88:20: error: dvbdev.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:89:19: error: demux.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:90:23: error: dvb_demux.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:91:20: error: dmxdev.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:92:24: error: dvb_filter.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:93:21: error: dvb_net.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:94:28: error: dvb_ringbuffer.h: No such file or directory
/home/vladimir/SW/aver/A828_Installer_x64_0.19-Beta/installer/src/aver/osdep_dvb.c:95:26: error: dvb_frontend.h: No such file or directory
```

You're missing dvb-core sources in the kernel sources, it should be located here: ```
/lib/modules/<kernel version>/source/drivers/media/dvb/dvb-core
```

I had a same problem with my fedora, look for some pkg which contains these files or just simply download full kernel sources from kernel.org, unpack and copy these missing files to kernel sources of your running kernel.

Hope this helps.

Regards,

lukash

---

### Post by sergyum on 2008-11-08
> **backstep said:**
> Hello guys!

New beta patch has been released at: [http://backstep.net/aver/AVERMEDIA-Linux-x86-A828-0.19-beta_patch_2.6.26_2.6.27BETA.diff]("http://backstep.net/aver/AVERMEDIA-Linux-x86-A828-0.19-beta_patch_2.6.26_2.6.27BETA.diff")

I can compile it on 2.6.27-7-generic (Ubuntu 8.10 x86) without problems.

More info available at: [http://backstep.net/aver/readme.txt]("http://backstep.net/aver/readme.txt")

Any feedbacks are welcome.

Regards,

lukash


I tried many times to install the driver on Kubuntu 8.10 (2.6.27-7) and i failed, could you explain me step by step like azelight how can I install on x86 ?
i am a new user on linux. Thanks in advance

---

### Post by father on 2008-11-08
> **backstep said:**
> 
You're missing dvb-core sources in the kernel sources, it should be located here: ```
/lib/modules/<kernel version>/source/drivers/media/dvb/dvb-core
```



Hi!

diff and the driver was prepared for x86 as Azelight mentioned, dvb-core source was copied, the driver was compiled, copied, but I get error message:

"FATAL: Error inserting a828 (/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/dvb-usb/a828.ko): Unknow symbol in module,..."

dmesg

[ 3686.247361] AVerMedia USB Wrapper version 0.01 unloaded
[ 3686.291356] AVerMedia USB Wrapper version 0.01 loaded
[ 3686.295215] a828: disagrees about version of symbol snd_pcm_new
[ 3686.295231] a828: Unknown symbol snd_pcm_new
[ 3686.295784] a828: disagrees about version of symbol snd_card_register
[ 3686.295788] a828: Unknown symbol snd_card_register
[ 3686.295991] a828: disagrees about version of symbol snd_card_free
[ 3686.295995] a828: Unknown symbol snd_card_free
[ 3686.299150] a828: disagrees about version of symbol snd_card_new
[ 3686.299154] a828: Unknown symbol snd_card_new
[ 3686.299758] a828: disagrees about version of symbol snd_pcm_lib_ioctl
[ 3686.299762] a828: Unknown symbol snd_pcm_lib_ioctl
[ 3686.300711] a828: disagrees about version of symbol snd_card_free_when_closed
[ 3686.300716] a828: Unknown symbol snd_card_free_when_closed
[ 3686.301141] a828: disagrees about version of symbol snd_pcm_set_ops
[ 3686.301146] a828: Unknown symbol snd_pcm_set_ops
[ 3686.302854] a828: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 3686.302859] a828: Unknown symbol snd_pcm_hw_constraint_integer
[ 3686.305438] a828: disagrees about version of symbol snd_pcm_period_elapsed
[ 3686.305443] a828: Unknown symbol snd_pcm_period_elapsed
[ 3710.937639] a828: disagrees about version of symbol snd_pcm_new
[ 3710.937656] a828: Unknown symbol snd_pcm_new
[ 3710.938207] a828: disagrees about version of symbol snd_card_register
[ 3710.938212] a828: Unknown symbol snd_card_register
[ 3710.938418] a828: disagrees about version of symbol snd_card_free
[ 3710.938422] a828: Unknown symbol snd_card_free
[ 3710.941765] a828: disagrees about version of symbol snd_card_new
[ 3710.941771] a828: Unknown symbol snd_card_new
[ 3710.942403] a828: disagrees about version of symbol snd_pcm_lib_ioctl
[ 3710.942408] a828: Unknown symbol snd_pcm_lib_ioctl
[ 3710.943385] a828: disagrees about version of symbol snd_card_free_when_closed
[ 3710.943389] a828: Unknown symbol snd_card_free_when_closed
[ 3710.943823] a828: disagrees about version of symbol snd_pcm_set_ops
[ 3710.943827] a828: Unknown symbol snd_pcm_set_ops
[ 3710.945629] a828: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 3710.945636] a828: Unknown symbol snd_pcm_hw_constraint_integer
[ 3710.948206] a828: disagrees about version of symbol snd_pcm_period_elapsed
[ 3710.948210] a828: Unknown symbol snd_pcm_period_elapsed

Any idea?

Thanks in advance!
Gabor

---

### Post by backstep on 2008-11-08
Hi, 

you have to use Expert mode in installer, that will unpack sources to some directory you'll choose, then you have to patch sources with my patch (as described above) and compile it with make. I don't know what's your real problem, if you don't know how to do some step, ask for it, explaining whole installation process is not necessary i think.

Ask more specific question pls.

lukash

---

### Post by backstep on 2008-11-08
> **father said:**
> Hi!

diff and the driver was prepared for x86 as Azelight mentioned, dvb-core source was copied, the driver was compiled, copied, but I get error message:

"FATAL: Error inserting a828 (/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/dvb-usb/a828.ko): Unknow symbol in module,..."

dmesg

[ 3686.247361] AVerMedia USB Wrapper version 0.01 unloaded
[ 3686.291356] AVerMedia USB Wrapper version 0.01 loaded
[ 3686.295215] a828: disagrees about version of symbol snd_pcm_new
[ 3686.295231] a828: Unknown symbol snd_pcm_new
[ 3686.295784] a828: disagrees about version of symbol snd_card_register
[ 3686.295788] a828: Unknown symbol snd_card_register
[ 3686.295991] a828: disagrees about version of symbol snd_card_free
[ 3686.295995] a828: Unknown symbol snd_card_free
[ 3686.299150] a828: disagrees about version of symbol snd_card_new
[ 3686.299154] a828: Unknown symbol snd_card_new
[ 3686.299758] a828: disagrees about version of symbol snd_pcm_lib_ioctl
[ 3686.299762] a828: Unknown symbol snd_pcm_lib_ioctl
[ 3686.300711] a828: disagrees about version of symbol snd_card_free_when_closed
[ 3686.300716] a828: Unknown symbol snd_card_free_when_closed
[ 3686.301141] a828: disagrees about version of symbol snd_pcm_set_ops
[ 3686.301146] a828: Unknown symbol snd_pcm_set_ops
[ 3686.302854] a828: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 3686.302859] a828: Unknown symbol snd_pcm_hw_constraint_integer
[ 3686.305438] a828: disagrees about version of symbol snd_pcm_period_elapsed
[ 3686.305443] a828: Unknown symbol snd_pcm_period_elapsed
[ 3710.937639] a828: disagrees about version of symbol snd_pcm_new
[ 3710.937656] a828: Unknown symbol snd_pcm_new
[ 3710.938207] a828: disagrees about version of symbol snd_card_register
[ 3710.938212] a828: Unknown symbol snd_card_register
[ 3710.938418] a828: disagrees about version of symbol snd_card_free
[ 3710.938422] a828: Unknown symbol snd_card_free
[ 3710.941765] a828: disagrees about version of symbol snd_card_new
[ 3710.941771] a828: Unknown symbol snd_card_new
[ 3710.942403] a828: disagrees about version of symbol snd_pcm_lib_ioctl
[ 3710.942408] a828: Unknown symbol snd_pcm_lib_ioctl
[ 3710.943385] a828: disagrees about version of symbol snd_card_free_when_closed
[ 3710.943389] a828: Unknown symbol snd_card_free_when_closed
[ 3710.943823] a828: disagrees about version of symbol snd_pcm_set_ops
[ 3710.943827] a828: Unknown symbol snd_pcm_set_ops
[ 3710.945629] a828: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 3710.945636] a828: Unknown symbol snd_pcm_hw_constraint_integer
[ 3710.948206] a828: disagrees about version of symbol snd_pcm_period_elapsed
[ 3710.948210] a828: Unknown symbol snd_pcm_period_elapsed

Any idea?

Thanks in advance!
Gabor



Hi, driver require snd_pcm module for sound, that's why you're missing so many symbols. So try to modprobe snd_pcm  .. or try it without sound with module snd-dummy (it will create all missing symbols without sound card). Then rmmod a828 and modprobe it again. But this is just missing sound symbols for sure.

lukash

---

### Post by macu on 2008-11-09
It work's great on 64bit Ubuntu II after I have copied files of kernel-source Thank you for your help :-)

---

### Post by father on 2008-11-17
> **backstep said:**
> Hi, driver require snd_pcm module for sound, that's why you're missing so many symbols. So try to modprobe snd_pcm  .. or try it without sound with module snd-dummy (it will create all missing symbols without sound card). Then rmmod a828 and modprobe it again. But this is just missing sound symbols for sure.

lukash

Hi,

Thanks. Almost done... I can watch analogue tv, but there is no sound... (tvtime, mplayer)

I'm getting to give up...

Any advice? Thanks in advance,
Gabor

---

### Post by backstep on 2008-11-17
> **father said:**
> Hi,

Thanks. Almost done... I can watch analogue tv, but there is no sound... (tvtime, mplayer)

I'm getting to give up...

Any advice? Thanks in advance,
Gabor

Hi,

I don't have enough information to give you some good advice .. however if u used snd-dummy module it's normal, because this module just create empty sound devices, if not try to past some debug info (fe. from dmesg etc.)..

Regards,

lukash

---

### Post by father on 2008-12-09
> **backstep said:**
> Hi,

I don't have enough information to give you some good advice .. however if u used snd-dummy module it's normal, because this module just create empty sound devices, if not try to past some debug info (fe. from dmesg etc.)..

Regards,

lukash

Hi,

I've just tried the 0.21 beta from Avermedia, too. Same issue..

dmesg:
[ 8937.589590] usb 5-1: configuration #1 chosen from 1 choice
[ 8937.799081] AVerMedia USB Wrapper for A828 version 0.21 loaded
[ 8937.884677] USB Hybrid+FM Volar version 0.21 loaded
[ 8938.002054] A828 registered V4L2 device video0[video]
[ 8938.002648] A828 registered V4L2 device video1[audio]
[ 8938.003153] A828 registered V4L2 device radio0[radio]
[ 8938.003796] A828 registered V4L2 device vbi0[vbi]
[ 8938.004378] A828 registered ALSA sound card 1
[ 8938.004781] DVB: registering new adapter (A828[0] DVB-T)
[ 8938.004786] A828[0] DVB-T registered DVB adapter 0
[ 8938.005961] DVB: registering frontend 0 (A828[0] DVB-T)...
[ 8938.105818] usbcore: registered new interface driver USB Hybrid+FM Volar


from messages log:
Dec  9 09:59:41 laptop kernel: [ 8937.884677] USB Hybrid+FM Volar version 0.21 loaded
Dec  9 09:59:41 laptop kernel: [ 8938.002054] A828 registered V4L2 device video0[video]
Dec  9 09:59:41 laptop kernel: [ 8938.002648] A828 registered V4L2 device video1[audio]
Dec  9 09:59:41 laptop kernel: [ 8938.003153] A828 registered V4L2 device radio0[radio]
Dec  9 09:59:41 laptop kernel: [ 8938.003796] A828 registered V4L2 device vbi0[vbi]
Dec  9 09:59:41 laptop kernel: [ 8938.004378] A828 registered ALSA sound card 1
Dec  9 09:59:41 laptop kernel: [ 8938.004781] DVB: registering new adapter (A828[0] DVB-T)
Dec  9 09:59:41 laptop kernel: [ 8938.004786] A828[0] DVB-T registered DVB adapter 0
Dec  9 09:59:41 laptop kernel: [ 8938.005961] DVB: registering frontend 0 (A828[0] DVB-T)...
Dec  9 09:59:41 laptop kernel: [ 8938.105818] usbcore: registered new interface driver USB Hybrid+FM Volar
Dec  9 10:00:01 laptop pulseaudio[7593]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Dec  9 10:00:01 laptop pulseaudio[7593]: alsa-util.c: Cannot find fallback mixer control "Mic".

Which program do u use for watching tv?

Gabor

---

### Post by Tamale on 2008-12-14
Can someone provide instructions for using the diff patch with the new .21 beta driver so it works with ubuntu 8.10?

I've got this same USB stick but don't have a clue how to use digital tuners like this in linux... any and all help would be greatly appreciated!

---

### Post by backstep on 2008-12-14
Hey guys,

maybe it could be an issue with pulseaudio (is video working correctly? just sound is a problem?),

I use mplayer, i think it's the best. You need to scan channels with (dvb)scan(dvb), name is various depending on distro. 

scandvb /usr/share/dvb-apps/dvb-t/cz-Praha > .mplayer/channels.conf

replace cz-Praha with file providing transponders in your country/city.
after this you can watch tv using:

mplayer "dvb://<channel name (first column in channels.conf)>"

pretty simple, isnt it?
what issues do you have with new avermedia drivers on 8.10? It works fine for me.

Regards,

lukash

---

### Post by Tamale on 2008-12-14
> **backstep said:**
> Hey guys,

maybe it could be an issue with pulseaudio (is video working correctly? just sound is a problem?),

I use mplayer, i think it's the best. You need to scan channels with (dvb)scan(dvb), name is various depending on distro. 

scandvb /usr/share/dvb-apps/dvb-t/cz-Praha > .mplayer/channels.conf

replace cz-Praha with file providing transponders in your country/city.
after this you can watch tv using:

mplayer "dvb://<channel name (first column in channels.conf)>"

pretty simple, isnt it?
what issues do you have with new avermedia drivers on 8.10? It works fine for me.

Regards,

lukash

When I run the driver install script, even as root, nothing seems to happen after I agree to the terms and conditions.  Do I still need your patch?  How do I apply it to this new driver?

---

### Post by backstep on 2008-12-15
> **Tamale said:**
> When I run the driver install script, even as root, nothing seems to happen after I agree to the terms and conditions.  Do I still need your patch?  How do I apply it to this new driver?

Hi, I just diffed avermedia's 0.21 drivers and 0.19 drivers with my patch, it looks pretty similar, so I think it doesn't matter which one you will use, u can use 0.21 without any patching or 0.19 with my patch.

Referring to Changelog:

0.20-beta => 0.21-beta
        1. Support kernel 2.6.27
        2. Add more verbose description to TV player in user documents.

I'm not sure why nothing happened after running script, no error msgs? nothing? I think you need dialog pkg in your system for that installation, however it should be installed by default, try post more debug info.

Regards, 

lukash

---

### Post by frosch6669 on 2009-01-04
Hello,
did someone get the fm-radio to work with an normal radio application such as gnome radio or kradio?
Greets

---

### Post by blue_led on 2009-01-20
Solved problem with a828 & dell mini 9 & ubuntu 8.10 :D

**1)** when i first try to watch TV with tvtime i can't select source
**Reason** : dell mini 9 have a usb web camera registered as /dev/video0 so tvtime can't use this 
**Solution :** edit /etc/tvtime/tvtime.xml , find [COLOR="Red"]/dev/video0[/COLOR] & change it to [COLOR="Green"]/dev/video1[/COLOR]

**2)** no audio
**Reason :** audio channel don't fit with default audio settings 
**Solution :** You must install a828 tools founded in driver archive
for sound you must type in a terminal window 
sudo /[COLOR="Purple"]tools folder[/COLOR]/audio -s /dev/video2
where [COLOR="Purple"]tools folder[/COLOR] is replaced with actual tools folder Ex: /opt/A828-tools
/dev/video2 is analog part audio channel ](*,)

**radio** work too 
in a terminal window "CD"-it to tools folder 
edit radio-player.c and type over 87750 frequency your favorite radio ( for me 94800 :D ). "make" it and run " sudo radio-player "

**Bonus:**
if you don't have sound after u8.10 fresh install on dell mini9 you must add this line 
[COLOR="Blue"]options snd-hda-intel model=dell[/COLOR]
at the end of file
[COLOR="Blue"]etc/modprobe.d/alsa-base[/COLOR]

P.S. Excuse my english , i drink the ink at english class

---

### Post by om1978 on 2009-02-09
Hi I followed the explanation step by step but when I open the tvtime a fews minutes while I was freezing ubuntu, I have ubuntu 8.10 with the 0.21 drivers for the a828 in a laptop dell inspiron 1520. not happening to you?

	
I could not see it for the world peace tv ubuntu even install VirtualBox with support for usb installing winxp to see if there could do nothing but run the capture.

Sorry for my bad english.

---

### Post by Yoann31 on 2009-02-24
> **frosch6669 said:**
> Hello,
did someone get the fm-radio to work with an normal radio application such as gnome radio or kradio?
Greets

I don't get fm-radio working with gnomeradio but with mplayer, it's so far better than A828-tools

**channel.conf could be used** (not tested yet)

Need libsox-fmt-all & sox packages
```

mplayer radio://104.3

sox -V -s -w -c 2 -r 48000 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp
```

(/dev/dsp2 or /dev/dsp1, check "arecord -l")


> **om1978 said:**
> Hi I followed the explanation step by step but when I open the tvtime a fews minutes while I was freezing ubuntu, I have ubuntu 8.10 with the 0.21 drivers for the a828 in a laptop dell inspiron 1520. not happening to you?

	
I could not see it for the world peace tv ubuntu even install VirtualBox with support for usb installing winxp to see if there could do nothing but run the capture.

Sorry for my bad english.

You don't use the last drivers, take the 0.24, they are officially supported on ubuntu 8.10! :)
I had some freeze problems with old drivers but now it's really perfect!

---

### Post by bikrus on 2009-04-17
Hi!

I have not a828 driver installed on system yet.

I recently upgraded to jaunty. I've downloaded 0.25beta driver for linux x86 from Aver site. Kernel: 2.6.28-11-generic. While installing in normal mode I got:

```
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in future release.
FATAL: Error inserting a828 (/lib/modules/2.6.28-11-generic/kernel/drivers/media/dvb/dvb-usb/a828.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

and dmesg:

```
[ 1982.408632] Linux video capture interface: v2.00
[ 1982.420248] AVerMedia USB Wrapper for A828 version 0.25 loaded
[ 1982.445960] a828: Unknown symbol mcount
```

Then in expert mode while 'make':

```
root@xyz:/A828-expert-install# make
make -C /lib/modules/2.6.28-11-generic/source O=/lib/modules/2.6.28-11-generic/build SUBDIRS=`pwd` 
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  LD      /A828-expert-install/built-in.o
  CC [M]  /A828-expert-install/aver/osdep.o
  CC [M]  /A828-expert-install/a828-core.o
  SHIPPED /A828-expert-install/aver/osdep_dvb.o
  CC [M]  /A828-expert-install/aver/osdep_th2.o
  CC [M]  /A828-expert-install/aver/osdep_v4l2.o
  CC [M]  /A828-expert-install/aver/osdep_vbuf.o
  CC [M]  /A828-expert-install/aver/osdep_alsa.o
  SHIPPED /A828-expert-install/_prebuild.o
  CC [M]  /A828-expert-install/aver/averusb-mod.o
  LD [M]  /A828-expert-install/a828.o
  LD [M]  /A828-expert-install/averusba828.o
  Building modules, stage 2.
  MODPOST 2 modules
WARNING: could not find /A828-expert-install/aver/.osdep_dvb.o.cmd for /A828-expert-install/aver/osdep_dvb.o
WARNING: "mcount" [/A828-expert-install/a828.ko] undefined!
  CC      /A828-expert-install/a828.mod.o
  LD [M]  /A828-expert-install/a828.ko
  CC      /A828-expert-install/averusba828.mod.o
  LD [M]  /A828-expert-install/averusba828.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
strip --strip-debug *.ko
root@xyz:/A828-expert-install# 

```

Could someone help with installing this driver? Or is this wrong forum? Thanks.

---

### Post by nealio on 2009-05-01
Just letting you know I'm having the exact same problems on Jaunty with 0.25beta.  Will keep looking around for a solution.

---

### Post by nealio on 2009-05-01
Actually, bikrus, your post is a couple weeks old now.  have you managed to install 0.25 on jaunty?  Was wondering if I should contact Avermedia for advice.

---

### Post by father on 2009-05-05
> **nealio said:**
> Actually, bikrus, your post is a couple weeks old now.  have you managed to install 0.25 on jaunty?  Was wondering if I should contact Avermedia for advice.

Same problem, again...:confused: Avermedia tech support is not too bad, so go ahead. And please drop us the solution :)

F

---

### Post by nealio on 2009-05-06
Have submitted a support request to avermedia.  i'll post when i get a response.  in the mean-time i think the "mcount" symbol is unresolved during the insertion of the module into the kernel.  it may boil down to having the wrong environment setup when compiling packages.  I though having "build-essentials" was enough but maybe the kernel source is needed as well.

---

### Post by morpheus.pv on 2009-05-08
hi, i have found working combination
it works for me on x86 platform under 8.10 (kernel 2.6.27-11-generic) and 9.04 (kernel 2.6.28) too
/note: under jaunty 9.04 works but sometimes freezes my computer/

**A828-tools** from installer **v0.24** (only needed for analog tv audio) *A828_Installer_x64_0.24Beta_090218.zip* or *A828_Installer_x86_0.24Beta_090218.zip*

then install

**kernel modules** (a828.ko, averusba828.ko) from installer **v0.21** *A828_Installer_x64_0.21-Beta.zip* or *A828_Installer_x86_0.21-Beta.zip* 


another combinations or installers won't run or freeze my computer
don't plug tv tuner before the computer boots (it cause hang up at boot if plugged)
to find old avermedia installers use google or try one of thse: [http://rapidshare.com/users/9OMH18](http://rapidshare.com/users/9OMH18)

sorry for my poor english

---

### Post by geekua on 2009-05-08
thanks, morpheus.pv, drivers have been installed by this way
but my system freezes while tvtime scans channels as in previous versions of Ubuntu :(

---

### Post by nealio on 2009-05-08
geeuka, whats the output of lsusb for your tuner?  Mine is the A301.  Output looks like this:

Bus 001 Device 002: ID 07ca:a301 AVerMedia Technologies, Inc. 

The 0.21 driver worked perfectly in Hardy and Intrepid.

---

### Post by morpheus.pv on 2009-05-09
mine is the a828
Bus 002 Device 002: ID 07ca:a828 AVerMedia Technologies, Inc.

**i try all available installers and none of them 'works' under newest kernel, drivers won't compile *under* 2.6.29+ *kernel*s**

*hope* that somebody *make* a *patch for 2.2.29+ kernels *

```
# root@morpheus:/tmp# cat A828-install.log 
Installer started
Installer version: 0.25
System Info:
Kernel: Linux morpheus 2.6.30-020630rc4-generic #020630rc4 SMP Fri May 1 09:06:03 UTC 2009 i686 GNU/Linux
GCC: gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Make: /usr/bin/make
Distribution: "Ubuntu 9.04"
EUID: 0
Dialog: /usr/bin/dialog
Dialog version: Version: 1.1-20080819
Screen size: Columns=157, Lines=41
Basedir: /tmp/avm-install/installer
===== /proc/asound/version BEGIN HERE =====
Advanced Linux Sound Architecture Driver Version 1.0.19.
===== /proc/asound/version END HERE =======
===== /proc/asound/cards BEGIN HERE =====
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc300000 irq 21
===== /proc/asound/cards END HERE =======
===== /proc/asound/devices BEGIN HERE =====
  2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
===== /proc/asound/devices END HERE =======
===== /proc/asound/pcm BEGIN HERE =====
00-00: ALC268 Analog : ALC268 Analog : playback 1 : capture 1
00-02: ALC268 Analog : ALC268 Analog : capture 1
===== /proc/asound/pcm END HERE =======
Show Welcome Screen
check if root: EUID=0
check kernel source : /lib/modules/2.6.30-020630rc4-generic/source
check kernel build : /lib/modules/2.6.30-020630rc4-generic/build
check architecture, current is x86, installer is x86
show EULA
Select Install Method
Normal Install Selected
Install New Driver
generate_kdep_string: KVSTR=4GREG
generate_kdep_string: KVVER=2.6.30
Building driver on-site
Building driver failed, error log follows
===== .err BEGIN HERE =====
/tmp/avm-install/installer/src/aver/osdep_v4l2.c: In function ‘SysVideoDevRegister’:
/tmp/avm-install/installer/src/aver/osdep_v4l2.c:187: warning: assignment from incompatible pointer type
/tmp/avm-install/installer/src/aver/osdep_v4l2.c: In function ‘video_ioctl’:
/tmp/avm-install/installer/src/aver/osdep_v4l2.c:350: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
/tmp/avm-install/installer/src/aver/osdep_v4l2.c:350: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
/tmp/avm-install/installer/src/aver/osdep_v4l2.c:350: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
/tmp/avm-install/installer/src/aver/osdep_v4l2.c:350: error: too many arguments to function ‘video_usercopy’
make[3]: *** [/tmp/avm-install/installer/src/aver/osdep_v4l2.o] Error 1
make[2]: *** [_module_/tmp/avm-install/installer/src] Error 2
make[1]: *** [sub-make] Error 2
make: *** [default] Error 2
ls: cannot access /tmp/avm-install/installer/src/a828.ko: No such file or directory
ls: cannot access /tmp/avm-install/installer/src/averusba828.ko: No such file or directory
===== .err END HERE =======
Driver Building failed
User abort after driver building failed
```

---

### Post by nealio on 2009-05-10
I seriously doubt Avermedia will release drivers that work in release candidate kernels.  That's a risk you take when you want bleeding edge.  I personally would never upgrade my kernel to any RC for that reason alone... what's the point really?

---

### Post by morpheus.pv on 2009-05-11
...main point is that the ubuntu jaunty users want a working drivers 

- only drivers working for me under 2.6.28 (default jaunty kernel) are v0.21
- installers v0.21 are not available for download from official avermedia homepage
- modules v0.21 are unstable under 2.6.28 - watching tv is a easy way you can freeze your computer
- newest kernels 2.6.29+ aren't supported by installer

---

### Post by morpheus.pv on 2009-05-15
[B]Good News Everyone! :popcorn:
[/B]

the project is not dead
i received a reply from avermedia customer service...


[B][B]Thank you for choosing AVerMedia.
 
Currently, the available driver doesn't support Ubuntu 9.04. However, are 
engineers are working on a newer driver that does support the new Linux 
distribution. It is estimated that the new driver will be released sometime next 
week. Please kindly refer to our website to download the new driver when available.

If you have any further questions, please don't hesitate to let us know.
 [/B][/B]

---

### Post by bikrus on 2009-05-15
**2 morpheus.pv:** Thank you for such great news! 

So, let's check aver site for updates next week ;)

---

### Post by garyczek on 2009-05-26
Hi!
Check out [Avermedia AverTV Hybrid+FM Volar A828 drivers]("http://www.avermedia.com/avertv/Support/Download.aspx?Type=Software&id=31&tab=APDriver"). 0.26 Beta is present. I can't test it this week. Upgrade from 0.25 Beta was without any problem, so I believe it works.

---

### Post by bikrus on 2009-05-26
**2 garyczek:**

Thank you very much for good news (0.26 beta drv). Just downloaded and installed. Installation was without any troubles. Will check functionality with real device today later.

$ uname -a
Linux rnb 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686 GNU/Linux

**edited later**

No success yet. tvtime found channels, but no audio. gnomeradio haven't found FM channels at all. Will continue investigation. Maybe it related to v4l and v4l2...

---

### Post by bikrus on 2009-06-10
Hi everyone!

Have spent some time to get tuner works. No success yet. But have some progress. So. "radio-player" from Aver extra tools works for me with next output:

```
user@xyz:~/var/aver/A828-tools$ ./radio-player 
Please wait about 10 seconds for device init.

=============================================
 Call audio to play FM audio                 
=============================================
Press Enter key to continue...

Setting FM 100 kHZ 

Press Enter key to continue ...
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
Playing WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
underrun!!! (at least 22001.286 ms long)
underrun!!! (at least 10892.530 ms long)
^CAborted by signal Interrupt...
Aborted by signal Interrupt...
Setting FM 81.75 kHZ 

Press Enter key to continue ...
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
Playing WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo

user@xyz:~/var/aver/A828-tools$ arecord: pcm_read:1529: read error: Input/output error

user@xyz:~/var/aver/A828-tools$ 

```

After this "success" I've tried mplayer:

```
user@xyz:~/var/aver/A828-tools$ mplayer -msglevel all=6 radio://100.
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2500  @ 2.00GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/user/.mplayer/codecs.conf'
Reading /home/user/.mplayer/codecs.conf: Can't open '/home/user/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-gui --enable-mencoder
CommandLine: '-msglevel' 'all=6' 'radio://100.'
init_freetype
get_path('font/font.desc') -> '/home/user/.mplayer/font/font.desc'
font: can't open file: /home/user/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/user/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/user/.mplayer/input.conf'
Can't open input config file /home/user/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
get_path('100..conf') -> '/home/user/.mplayer/100..conf'

Playing radio://100..
get_path('sub/') -> '/home/user/.mplayer/sub/'
[radio] Available drivers: v4l2, v4l, 
**[radio] Using V4Lv2 radio interface.**
[radio] Radio fd: 4, /dev/radio0
**[radio] ioctl get volume failed: Invalid argument**
**[radio] ioctl set volume failed: Invalid argument**
[radio] Allowed frequency range is 76.00-108.00 MHz.
[radio] Radio frequency parameter detected.
[radio] Using frequency: 100.00.
**[radio] ioctl set volume failed: Invalid argument**
STREAM: [Radio] radio://100.
STREAM: Description: Radio stream
STREAM: Author: Vladimir Voroshilov
STREAM: Comment: In development
rawaudio file format detected.
==> Found audio stream: 0
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
dec_audio: Allocating 2048 + 65536 = 67584 bytes for output buffer.
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
A: 183.4 (03:03.3) of 0.0 (unknown)  0.1% 

MPlayer interrupted by signal 2 in module: play_audio
Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: pcm
[radio] ioctl set volume failed: Invalid argument
vo: x11 uninit called but X11 not inited..
user@xyz:~/var/aver/A828-tools$ 

```

No sound and "[radio] ioctl get/set volume failed: Invalid argument". :( 

Please, point me who should I ask for solution:
- AverMedia support - seems their tools are works.
- v4l support - at v4l-dvb site there are no support for device.
- mplayer support - why I've got no sound?

If you have any suggestion - please, help.

Have tried KRadio - no success too. At simple radio interface the "antenna icon" and "frequency label" are bright, but no sound at speakers.

Thank you.

---

### Post by phamthanhnam on 2009-06-11
I have Avermedia AVerTV Hybrid Volar HX A827, but I think it will the same for Avermedia products.
Avermedia tuners have no Audio-Out port (which is usually connected to sound card's Line-In port for other brands' products). Audio stream from tuner will be redirected to speakers by driver or by software.
So you need use this command after activating radio/tv applications like mplayer, gnomeradio, tvtime, rhythmbox... (suppose that you have 1 sound card):
```
arecord -D hw:1,0 -r 48000 -c 2 -f S16_LE | aplay -
```
If you find asynchronism between video/audio (audio is played later), replace the above command by: (but you must turn all other programs which are playing/recording sound, and you need packages "sox" and "libsox-fmt-alsa" installed)
```
sox -c 2 -r 48000 -t alsa hw:1,0 -t alsa hw:0,0
```
The program radio_player in Avermedia's tools also uses directly the above command (you will see it if you read the source code).
Get/Set volume will not work for all applications, maybe because there's a bug in driver.
kradio has a feature called "active playback", try to find it yourself, so you won't need to use the above command.
You will also have problems if you use gnomeradio "in the normal way" :(. Press Alt+F2, type gconf-editor, go to apps/gnomeradio, double click the key "driver", replace the value "any" by "v4l2". Uncheck the key "first_time_flag". Execute again gnomeradio. Now you will have channel scanning list (wait for some minutes), and radio works! :)
Besides, you can also use this tuner with Rhythmbox. Choose Edit - Plugins from menu, choose FM radio. Right click on the label "FM radio" on the left, create a new channel. Type "100" for 100 MHz, "95.5" for 95.5 MHz, for example.
Hope it help! ;)

---

### Post by bikrus on 2009-06-11
Thank you **phamthanhnam**!

At least gnomeradio works! WOW!!! :p

But... I steel can't configure KRadio. There are so many configuration params (plugins, ALSA, OSS, V4L...) and so little knowledge of linux... PCM, mixer, microphone, alsa, oss, pulse audio, hw:0.1 or hw:0.0, capture, playback - which to use and what this mean... I am in maze. But I want configure it. And I hope knowledge from this thread will help other.

After KRadio I will investigate of TV possibilities. :)

Anyway. Some progress is completed. Radio (in some form) is works.

Thank you **phamthanhnam**!

(Hope this post is not offtopic :))

---

### Post by phamthanhnam on 2009-06-12
Hi
I've tried my Avermedia TV tuner with kradio and now I share my experience.
First, I recommend [new kradio version]("http://kradio.sourceforge.net/"). The kradio version in Ubuntu repositories was too obsolete.
Installation is a bit hard because there's not Ubuntu package yet.
**Prepare requirements (here example for Jaunty):**
```
sudo apt-get install build-essential cmake kdelibs5-dev libavformat-dev libmms-dev libsndfile1-dev libmp3lame-dev libogg-dev libvorbis-dev liblircclient-dev libasound2-dev
```
Download kradio4 source from homepage and unpack, e.g to your home directory.
**Build and install:**
```
cd ~
mkdir kradio-build
cd kradio-build
cmake -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=/usr ../kradio4-4.0.0
make
sudo make install
```
OK. Now, execute kradio4 from menu *Applications* - *Sound & Video*. For the first time, you may get many warnings/errors. Don't bother.
**Configuration is quite complicated, but I simplify it 4u:**
[LIST=1]
[*]Right click on the icon on the taskbar, choose *Show/Hide Plugins* - *Show Configuration Dialog* if the configuration window isn't displayed. You may have to move around the configuration window with Alt + Left mouse button if its size is too big. :o
[*]Choose *V4L Radio* from the left categories, in *Radio Device*, type in */dev/radio0*. Click *Apply*.
[*]Choose the category *ALSA Sound*. In *PCM Playback Card* and *PCM Playback Device*, you will see your sound card settings. Choose the correct device which will play sound on your speakers. You **must** check *Soft Playback Volume* because hardware volume is not available for Avermedia tuners.
[*]In *PCM Capture Card* and *PCM Capture Device*, you choose your tuner (*AVerMedia AVerTV ... Volar A828* ). You **must** also check *Override Capture Format*, keep all other parameters default (48000, 16 bits signed, Little Endian, Stereo, Buffer Sizes) if you want to have stable audio. Click *Apply*.
[*]Return to the category *V4L Radio*. Choose *Playback Mixer Device* as *ALSA Sound Device ...*, choose *Playback Mixer Channel* as *PCM*, choose *Capture Mixer Device* as *ALSA Sound Device ...*. You may have no option in *Capture Mixer Channel*, don't worry, let it be. You **must** check *Use active playback by capturing* if you don't want to have to type the additional command that I mentioned in the last post. Check *Mute playback of capture channel when active playback is running* to avoid echo in the recordings. Click *Apply*.
[*]Now, choose the category *Radio Stations*. You should add your favorite channels manually because automatic scanning is not always good. Click *OK* to close the configuration window.
[/LIST]
Right click on the icon and choose *Power On*.
If you want to ignore annoying errors (that's right, because your tuner does not support hardware volume change/switch!!!) each time you do Power On/Off, channel switching or recording, go to the category Plugins in the configuration dialog and remove *ErrorLog* from *Created Plugin Instances*.
Good luck!

---

### Post by eastir on 2009-06-16
Hi everyone.

I have this Avermedia's card (A828) and now i'm using ubuntu 9.04, but, since ubuntu 8.10 and i think since 8.04 i have a little big problem. Sometimes, when i am searching  channels, suddenly, computer is blocked, with the light of caps-lock maintains intermittent. This is more probable when i'm using analog tv (all of times) and sometimes with digital tv.

I'm using now 2.6.30 kernel but the problem is too with 2.6.28 native kernel and with 2.6.27 kernel. I don't know where i can search in ubuntu's log.

I hope you can help me. I only maintain windows for i can see tv, and i want erase it.

PD: I'm using the latest avermedia's driver (0.26Beta)

---

### Post by panteraz on 2010-01-05
> **eastir said:**
> Hi everyone.

I have this Avermedia's card (A828) and now i'm using ubuntu 9.04, but, since ubuntu 8.10 and i think since 8.04 i have a little big problem. Sometimes, when i am searching  channels, suddenly, computer is blocked, with the light of caps-lock maintains intermittent. This is more probable when i'm using analog tv (all of times) and sometimes with digital tv.

I'm using now 2.6.30 kernel but the problem is too with 2.6.28 native kernel and with 2.6.27 kernel. I don't know where i can search in ubuntu's log.

I hope you can help me. I only maintain windows for i can see tv, and i want erase it.

PD: I'm using the latest avermedia's driver (0.26Beta)

I have the same problem. Using Ubuntu 9.10 and 0.28beta drivers...

---

### Post by Viser on 2010-02-19
> **panteraz said:**
> I have the same problem. Using Ubuntu 9.10 and 0.28beta drivers...

Right, the same problem. 9.10, 0.28-Beta_091125.

---

### Post by Viser on 2010-02-22
Seems like Aver driver has some issues with tvtime. Freez happens while tvtime is running. Mplayer works great.

---

### Post by marrabld on 2010-05-15
This worked for me with Ubuntu 10.04 reasonably fresh install

Downloaded the drivers from here 0.28-beta

[http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver](http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver)

unzip into something like ~/workingDirectory

```
sudo apt-get install dialog
sudo apt-get install Kaffeine

cd ~/workingDirectory/A828_Installer_x64_0.28-Beta

sudo ./AVERMEDIA-Linux-x64-A828-0.28-beta.sh
```

Choose normal install 

```
dmesg
``` should return something like

...
[13567.090830] A828 registered V4L2 device video1[video]
[13567.092127] A828 registered V4L2 device radio0[radio]
[13567.092327] A828 registered V4L2 device vbi0[vbi]
[13567.099659] A828 registered ALSA sound card 1
[13567.099681] DVB: registering new adapter (A828[0] DVB-T)
[13567.099686] A828[0] DVB-T registered DVB adapter 0
[13567.100731] DVB: registering adapter 0 frontend 0 (A828[0] DVB-T)...

start Kaffeine

Television --> Configure Television --> Device 1[tab]
Source -->autoscan Australia (becasue that is where I am of course :-) )
OK

Television Channels --> Start Scan

Hopefully you will see Scan Results populate.  Highlight the ones you want, then select Add Selected

OK 

Then enjoy the inane babble that is broadcast over the air.

Hope this works for you too.

---

### Post by codegateway on 2010-05-18
hi marrabld, thanks for the driver, I tested it but now i need to uninstall it, any idea on how to do it? I looked for a command to uninstall that driver with no luck, should I type some commands or just delete some files? thanks

---

### Post by ppjsgml on 2010-05-24
> **codegateway said:**
> ...i need to uninstall it, any idea on how to do it? I looked for a command to uninstall that driver with no luck...

Try to "reinstall" it, I don't remember but I think it will prompt you what to do because it will detect a version installed. I'm sure that one option it's to upgrade but I'm not sure about the other ones

---

### Post by codegateway on 2010-05-26
> **ppjsgml said:**
> Try to "reinstall" it, I don't remember but I think it will prompt you what to do because it will detect a version installed. I'm sure that one option it's to upgrade but I'm not sure about the other ones

Thans ppjsgml!! it worked exactly as you said! i can't believe that was the solution :S...
Ok i'&#314;l transfer the output here so somebody who'd need it as i  did would be easy about it:
sudo ./AVERMEDIA-Linux-x86-A828-0.28-beta.sh
OUTPUT  of 5th screen (after clicking "Normal" installation method on 4th one) :
                                Upgrade or remove?
Avertv usb hybrid+fm driver v0.28 is already installed for the running kernel.
Do you wish to upgrade or remove the installed driver?
"Upgrade"        ................................
"Remove"          ................................
"Install Tools"   ................................
OUTPUT after clicking "Remove"
                                Driver is removed
Avertv usb hybrid+fm driver is successfully removed

:) thanks a lot for the help!

---

### Post by aimwin on 2011-04-18
New Correct Download link is here

[http://www.avermedia.com/avertv/Support/DownloadCount.aspx?FDFId=3205](http://www.avermedia.com/avertv/Support/DownloadCount.aspx?FDFId=3205)

and the page that have all OS driver is below, with linux driver last 2 buttom page

[http://www.avermedia.com/avertv/Support/Download.aspx?Type=Software&id=31&tab=APDriver](http://www.avermedia.com/avertv/Support/Download.aspx?Type=Software&id=31&tab=APDriver)


> **marrabld said:**
> This worked for me with Ubuntu 10.04 reasonably fresh install

Downloaded the drivers from here 0.28-beta

[http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver](http://www.avermedia.com/AVerTV/Product/ProductDetail.aspx?Id=31&tab=APDriver)

unzip into something like ~/workingDirectory

```
sudo apt-get install dialog
sudo apt-get install Kaffeine

cd ~/workingDirectory/A828_Installer_x64_0.28-Beta

sudo ./AVERMEDIA-Linux-x64-A828-0.28-beta.sh
```

Choose normal install 

```
dmesg
``` should return something like

...
[13567.090830] A828 registered V4L2 device video1[video]
[13567.092127] A828 registered V4L2 device radio0[radio]
[13567.092327] A828 registered V4L2 device vbi0[vbi]
[13567.099659] A828 registered ALSA sound card 1
[13567.099681] DVB: registering new adapter (A828[0] DVB-T)
[13567.099686] A828[0] DVB-T registered DVB adapter 0
[13567.100731] DVB: registering adapter 0 frontend 0 (A828[0] DVB-T)...

start Kaffeine

Television --> Configure Television --> Device 1[tab]
Source -->autoscan Australia (becasue that is where I am of course :-) )
OK

Television Channels --> Start Scan

Hopefully you will see Scan Results populate.  Highlight the ones you want, then select Add Selected

OK 

Then enjoy the inane babble that is broadcast over the air.

Hope this works for you too.

---

