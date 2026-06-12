---
title: "Help for CDMA usb modem"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by chitragurung on 2009-10-28
I recently have Dell notebook Mini with Ubuntu OS. Everything works fine. But I could not use or setup CDMA USB modem to browse internet. I tried several forum but still I could not find solutions. Can any one help be to set up this stuff ?

---

### Post by pdc on 2009-10-28
which country are you in?
which network do you want to join?

Can you tell us what you have already tried, to get your device to work please?

If after that .............

if you insert your modem and in a terminal type the command

> lsusb

and after that 

> dmesg

and then copy and paste the results back here, 

folks on the forum may get a hint what your device is

---

### Post by chitragurung on 2011-01-11
here is results

[    8.814270] AppArmor: AppArmor initialized
[    8.814277] Failure registering capabilities with primary security module.
[    8.814292] Mount-cache hash table entries: 512
[    8.814479] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    8.814497] monitor/mwait feature present.
[    8.814500] using mwait in idle threads.
[    8.814506] CPU: L1 I cache: 32K, L1 D cache: 24K
[    8.814510] CPU: L2 cache: 512K
[    8.814514] CPU: Physical Processor ID: 0
[    8.814519] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00043940 0040c39d 00000000 00000001 00000000
[    8.814530] Intel machine check architecture supported.
[    8.814536] Intel machine check reporting enabled on CPU#0.
[    8.814543] Compat vDSO mapped to ffffe000.
[    8.814558] Checking 'hlt' instruction... OK.
[    8.830152] Disabling 4MB page tables to avoid TLB bug
[    8.830621] SMP alternatives: switching to UP code
[    8.832799] Early unpacking initramfs... done
[    9.033727] ACPI: Core revision 20070126
[    9.033834] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.043458] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.043486] SMP alternatives: switching to SMP code
[    9.044170] Booting processor 1/1 eip 3000
[    9.054185] Initializing CPU#1
[    9.133877] Calibrating delay using timer specific routine.. 3192.18 BogoMIPS (lpj=6384373)
[    9.133891] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    9.133903] monitor/mwait feature present.
[    9.133909] CPU: L1 I cache: 32K, L1 D cache: 24K
[    9.133913] CPU: L2 cache: 512K
[    9.133918] CPU: Physical Processor ID: 0
[    9.133923] CPU: After all inits, caps: bfe9fbf7 00100000 00000000 00043940 0040c39d 00000000 00000001 00000000
[    9.133934] Intel machine check architecture supported.
[    9.133940] Intel machine check reporting enabled on CPU#1.
[    9.134210] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.134252] Total of 2 processors activated (6384.28 BogoMIPS).
[    9.134460] ENABLING IO-APIC IRQs
[    9.134681] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.281968] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    9.301969] Brought up 2 CPUs
[    9.302011] CPU0 attaching sched-domain:
[    9.302015]  domain 0: span 03
[    9.302018]   groups: 01 02
[    9.302024]   domain 1: span 03
[    9.302028]    groups: 03
[    9.302032] CPU1 attaching sched-domain:
[    9.302035]  domain 0: span 03
[    9.302038]   groups: 02 01
[    9.302043]   domain 1: span 03
[    9.302046]    groups: 03
[    9.302435] net_namespace: 64 bytes
[    9.302448] Booting paravirtualized kernel on bare hardware
[    9.303416] Time: 14:03:07  Date: 01/11/11
[    9.303509] NET: Registered protocol family 16
[    9.303884] No dock devices found.
[    9.304061] ACPI: bus type pci registered
[    9.304896] PCI: PCI BIOS revision 3.00 entry at 0xfde5f, last bus=5
[    9.304902] PCI: Using configuration type 1
[    9.304915] Setting up standard PCI resources
[    9.309830] ACPI: EC: Look up EC in DSDT
[    9.312766] ACPI: BIOS _OSI(Linux) query honored via cmdline
[    9.312772] ACPI: DMI System Vendor: Dell Inc.
[    9.312775] ACPI: DMI Product Name: Inspiron 1011
[    9.312778] ACPI: DMI Product Version: A06
[    9.312781] ACPI: DMI Board Name: CN0Y53
[    9.312784] ACPI: DMI BIOS Vendor: Dell Inc.
[    9.312787] ACPI: DMI BIOS Date: 07/29/2009
[    9.312790] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[    9.313705] ACPI: Interpreter enabled
[    9.313711] ACPI: (supports S0 S3 S4 S5)
[    9.313738] ACPI: Using IOAPIC for interrupt routing
[    9.314332] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.406940] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    9.406949] ACPI: EC: driver started in interrupt mode
[    9.407035] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.407977] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.407984] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    9.409428] PCI: Transparent bridge - 0000:00:1e.0
[    9.409483] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.410094] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.410359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.410613] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    9.410894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.426108] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    9.426318] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.426524] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.426728] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    9.426933] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    9.427138] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    9.427344] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    9.427548] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    9.427912] ACPI: WMI: Mapper loaded
[    9.427917] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.427982] pnp: PnP ACPI init
[    9.427997] ACPI: bus type pnp registered
[    9.453961] pnp: PnP ACPI: found 11 devices
[    9.453966] ACPI: ACPI bus type pnp unregistered
[    9.454305] SCSI subsystem initialized
[    9.454383] libata version 3.00 loaded.
[    9.454700] usbcore: registered new interface driver usbfs
[    9.454773] usbcore: registered new interface driver hub
[    9.454856] usbcore: registered new device driver usb
[    9.455490] PCI: Using ACPI for IRQ routing
[    9.455497] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.541758] NET: Registered protocol family 8
[    9.541762] NET: Registered protocol family 20
[    9.541873] AppArmor: AppArmor Filesystem Enabled
[    9.545529] Time: tsc clocksource has been installed.
[    9.561804] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.561811] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    9.561817] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    9.561822] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    9.561828] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    9.561834] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    9.561839] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    9.561845] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    9.561859] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    9.561871] system 00:06: ioport range 0x680-0x69f has been reserved
[    9.561876] system 00:06: ioport range 0x800-0x80f has been reserved
[    9.561881] system 00:06: ioport range 0x1000-0x107f has been reserved
[    9.561886] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    9.561892] system 00:06: ioport range 0x1640-0x164f has been reserved
[    9.561898] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[    9.561903] system 00:06: ioport range 0xff00-0xff7f has been reserved
[    9.561914] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    9.561919] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    9.597289] PCI: Bridge: 0000:00:1c.0
[    9.597293]   IO window: disabled.
[    9.597301]   MEM window: disabled.
[    9.597306]   PREFETCH window: disabled.
[    9.597314] PCI: Bridge: 0000:00:1c.1
[    9.597317]   IO window: disabled.
[    9.597325]   MEM window: f0100000-f01fffff
[    9.597331]   PREFETCH window: disabled.
[    9.597339] PCI: Bridge: 0000:00:1c.2
[    9.597344]   IO window: 2000-2fff
[    9.597352]   MEM window: 50000000-500fffff
[    9.597359]   PREFETCH window: f0500000-f05fffff
[    9.597366] PCI: Bridge: 0000:00:1e.0
[    9.597369]   IO window: disabled.
[    9.597376]   MEM window: disabled.
[    9.597382]   PREFETCH window: disabled.
[    9.597429] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    9.597440] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.597470] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    9.597480] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.597512] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.597521] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.597538] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.597559] NET: Registered protocol family 2
[    9.633784] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.634254] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.635299] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.635853] TCP: Hash tables configured (established 131072 bind 65536)
[    9.635859] TCP reno registered
[    9.645920] checking if image is initramfs... it is
[   10.035135] Freeing initrd memory: 2751k freed
[   10.035414] Simple Boot Flag at 0x36 set to 0x80
[   10.036641] audit: initializing netlink socket (disabled)
[   10.036662] audit(1294754588.100:1): initialized
[   10.036936] highmem bounce pool size: 64 pages
[   10.040668] VFS: Disk quotas dquot_6.5.1
[   10.040815] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.041725] io scheduler noop registered
[   10.041730] io scheduler anticipatory registered
[   10.041734] io scheduler deadline registered
[   10.041850] io scheduler cfq registered (default)
[   10.041873] Boot video device is 0000:00:02.0
[   10.042170] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.042237] assign_interrupt_mode Found MSI capability
[   10.042295] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.042361] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.042504] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.042569] assign_interrupt_mode Found MSI capability
[   10.042622] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.042708] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.042851] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   10.042916] assign_interrupt_mode Found MSI capability
[   10.042968] Allocate Port Service[0000:00:1c.2:pcie00]
[   10.043036] Allocate Port Service[0000:00:1c.2:pcie02]
[   10.048329] ACPI: AC Adapter [ACAD] (off-line)
[   10.097039] Switched to high resolution mode on CPU 0
[   10.097239] Switched to high resolution mode on CPU 1
[   10.428705] ACPI: Battery Slot [BAT1] (battery present)
[   10.429059] input: Power Button (FF) as /devices/virtual/input/input0
[   10.429066] ACPI: Power Button (FF) [PWRF]
[   10.429185] input: Lid Switch as /devices/virtual/input/input1
[   10.429276] ACPI: Lid Switch [LID0]
[   10.429404] input: Power Button (CM) as /devices/virtual/input/input2
[   10.429410] ACPI: Power Button (CM) [PWRB]
[   10.438339] ACPI: device:01 is registered as cooling_device0
[   10.438709] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input3
[   10.438717] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.439436] ACPI: SSDT 3F6DBC78, 0245 (r2  PmRef  Cpu0Ist     3000 INTL 20050624)
[   10.439785] ACPI: SSDT 3F6DB60E, 05E5 (r2  PmRef  Cpu0Cst     3001 INTL 20050624)
[   10.440546] Monitor-Mwait will be used to enter C-1 state
[   10.440551] Monitor-Mwait will be used to enter C-2 state
[   10.440556] Monitor-Mwait will be used to enter C-3 state
[   10.440634] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.440732] ACPI: ACPI0007:00 is registered as cooling_device1
[   10.440740] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.441238] ACPI: SSDT 3F6DBEBD, 00D4 (r2  PmRef  Cpu1Ist     3000 INTL 20050624)
[   10.441563] ACPI: SSDT 3F6DBBF3, 0085 (r2  PmRef  Cpu1Cst     3000 INTL 20050624)
[   10.442541] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   10.442623] ACPI: ACPI0007:01 is registered as cooling_device2
[   10.442632] ACPI: Processor [CPU1] (supports 8 throttling states)
[   10.477816] ACPI: LNXTHERM:01 is registered as thermal_zone0
[   10.481693] ACPI: Thermal Zone [TZ01] (9 C)
[   10.591450] Real Time Clock Driver v1.12ac
[   10.591825] hpet_acpi_add: no address or irqs in _CRS
[   10.591856] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.594085] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.594692] loop: module loaded
[   10.594778] Driver 'sd' needs updating - please use bus_type methods
[   10.594842] Driver 'sr' needs updating - please use bus_type methods
[   10.595043] ata_piix 0000:00:1f.2: version 2.12
[   10.595055] ata_piix 0000:00:1f.2: MAP [ P0 P2 -- -- ]
[   10.748409] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   10.748462] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   10.748588] scsi0 : ata_piix
[   10.748742] scsi1 : ata_piix
[   10.750425] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   10.750432] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   10.958571] ata1.00: ATA-8: WDC WD1600BEVT-75ZCT2, 11.01A11, max UDMA/133
[   10.958577] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   10.973675] ata1.00: configured for UDMA/133
[   11.139430] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-7 11.0 PQ: 0 ANSI: 5
[   11.139672] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   11.139701] sd 0:0:0:0: [sda] Write Protect is off
[   11.139708] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.139755] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.139847] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   11.139874] sd 0:0:0:0: [sda] Write Protect is off
[   11.139880] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.139924] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.139933]  sda: sda1 sda2 sda3
[   11.148593] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.148738] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.149141] USB Universal Host Controller Interface driver v3.0
[   11.149249] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   11.149264] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.149271] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.149439] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.149483] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   11.149816] usb usb1: configuration #1 chosen from 1 choice
[   11.149902] hub 1-0:1.0: USB hub found
[   11.149916] hub 1-0:1.0: 2 ports detected
[   11.252036] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   11.252051] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.252058] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.252217] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.252256] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   11.252524] usb usb2: configuration #1 chosen from 1 choice
[   11.252610] hub 2-0:1.0: USB hub found
[   11.252622] hub 2-0:1.0: 2 ports detected
[   11.355925] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.355939] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.355945] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.356112] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.356153] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   11.356440] usb usb3: configuration #1 chosen from 1 choice
[   11.356528] hub 3-0:1.0: USB hub found
[   11.356540] hub 3-0:1.0: 2 ports detected
[   11.459829] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   11.459843] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.459850] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.460002] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.460045] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   11.460308] usb usb4: configuration #1 chosen from 1 choice
[   11.460392] hub 4-0:1.0: USB hub found
[   11.460404] hub 4-0:1.0: 2 ports detected
[   11.563785] Initializing USB Mass Storage driver...
[   11.563871] usbcore: registered new interface driver usb-storage
[   11.563877] USB Mass Storage support registered.
[   11.563951] usbcore: registered new interface driver libusual
[   11.564180] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.567008] i8042_command I8042_CMD_KBD_DISABLE OK
[   11.596124] i8042_command I8042_CMD_KBD_ENABLE OK
[   11.599006] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.599015] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.599240] mice: PS/2 mouse device common for all mice
[   11.655785] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   11.677384] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[   11.727819] cpuidle: using governor ladder
[   12.727091] cpuidle: using governor menu
[   12.727160] sdhci: Secure Digital Host Controller Interface driver
[   12.727166] sdhci: Copyright(c) Pierre Ossman
[   12.727988] NET: Registered protocol family 1
[   12.728434] NET: Registered protocol family 10
[   12.728777] lo: Disabled Privacy Extensions
[   12.729387] NET: Registered protocol family 17
[   12.729427] Using IPI No-Shortcut mode
[   12.729623]   Magic number: 11:790:80
[   12.729967] Freeing unused kernel memory: 296k freed
[   13.072039] usbcore: registered new interface driver hiddev
[   13.072121] usbcore: registered new interface driver usbhid
[   13.072129] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   13.090332] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   13.090359] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.090367] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.090579] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   13.094532] ehci_hcd 0000:00:1d.7: debug port 1
[   13.094551] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.094564] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf0444000
[   13.110111] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.110435] usb usb5: configuration #1 chosen from 1 choice
[   13.110535] hub 5-0:1.0: USB hub found
[   13.110550] hub 5-0:1.0: 8 ports detected
[   13.352371] Registering unionfs 1.4
[   13.352376] unionfs: debugging is not enabled
[   13.360596] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   13.448015] fuse init (API version 7.9)
[   13.617626] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   13.796084] usb 5-2: configuration #1 chosen from 1 choice
[   14.041201] usb 5-3: new high speed USB device using ehci_hcd and address 3
[   14.873842] kjournald starting.  Commit interval 5 seconds
[   14.873893] EXT3-fs: mounted filesystem with ordered data mode.
[   15.475302] usb 5-3: configuration #1 chosen from 1 choice
[   15.477361] scsi2 : SCSI emulation for USB Mass Storage devices
[   15.477537] usb-storage: device found at 3
[   15.477544] usb-storage: waiting for device to settle before scanning
[   17.087287] Clocksource tsc unstable (delta = -65069466 ns)
[   17.090250] Time: acpi_pm clocksource has been installed.
[   18.341598] 2.6.2X-Elan-touchpad-2009-03-09
[   18.341606] +elantech_detect
[   18.700907] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[   18.737297] elantech.c: unexpected magic knock result 0x00, 0x02, 0x64.
[   18.737307] 2.6.2X-Elan-touchpad-2009-03-09
[   18.737312] +elantech_detect
[   19.091288] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[   19.129004] elantech.c: unexpected magic knock result 0x00, 0x02, 0x64.
[   19.129010] 2.6.2X-Elan-touchpad-2009-03-09
[   19.129013] +elantech_detect
[   19.483718] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[   19.521317] elantech.c: unexpected magic knock result 0x00, 0x02, 0x64.
[   20.107504] usb-storage: device scan complete
[   20.109658] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   20.113870] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   20.113941] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   20.358672] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04711/0xa40000
[   20.384422] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   20.546007] intel_rng: FWH not detected
[   20.613250] iTCO_vendor_support: vendor-support=0
[   20.642384] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   20.642521] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   20.642585] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.700909] ieee80211_crypt: registered algorithm 'NULL'
[   20.737309] r8169 Gigabit Ethernet driver 2.2LK loaded
[   20.737396] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   20.737471] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   20.738948] eth0: RTL8102e at 0xf886c000, 00:24:e8:db:1a:9e, XID 24c00000 IRQ 220
[   20.828787] ieee80211_crypt: registered algorithm 'TKIP'
[   20.961078] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   20.961489] EXT3 FS on sda2, internal journal
[   23.319292] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.853691] PPP generic driver version 2.4.2
[   27.744071] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   27.744118] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.103985] Linux agpgart interface v0.102
[   28.122727] agpgart: Detected an Intel 945GME Chipset.
[   28.122951] agpgart: Detected 7932K stolen memory.
[   28.141049] agpgart: AGP aperture is 256M @ 0xd0000000
[   28.198554] [drm] Initialized drm 1.1.0 20060810
[   33.080645] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   33.080666] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.080818] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   39.990345] parport 0x378 (WARNING): CTR: wrote 0x0c, read 0xff
[   39.990374] parport 0x378 (WARNING): DATA: wrote 0xaa, read 0xff
[   39.990387] parport 0x378: You gave this address, but there is probably no parallel port there!
[   39.990479] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.078744] ppdev: user-space parallel port driver
[   41.929882] audit(1294754621.204:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5043 profile="/usr/sbin/cupsd" namespace="default"
[   42.719195] r8169: eth0: link down
[   42.722365] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   70.212969] Bluetooth: Core ver 2.11
[   70.213487] NET: Registered protocol family 31
[   70.213498] Bluetooth: HCI device and connection manager initialized
[   70.213508] Bluetooth: HCI socket layer initialized
[   70.267253] Bluetooth: HCI USB driver ver 2.9
[   70.267338] usbcore: registered new interface driver hci_usb
[   70.597121] Bluetooth: L2CAP ver 2.9
[   70.597131] Bluetooth: L2CAP socket layer initialized
[   70.978395] Bluetooth: RFCOMM socket layer initialized
[   70.978878] Bluetooth: RFCOMM TTY layer initialized
[   70.978890] Bluetooth: RFCOMM ver 1.8
[   71.372077] Linux video capture interface: v2.00
[   71.405059] uvcvideo: Found UVC 1.00 device Integrated Webcam (064e:a129)
[   71.420904] usbcore: registered new interface driver uvcvideo
[   71.420920] USB Video Class driver (v0.1.0)
[   71.496283] usbcore: registered new interface driver cdc_acm
[   71.496301] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/class/cdc-acm.c: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   71.574324] usbcore: registered new interface driver cdc_ether
[   71.578482] usbcore: registered new interface driver mbm
[   72.139677] wl: module license 'MIXED/Proprietary' taints kernel.
[   72.145078] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   72.145105] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   72.169999] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   83.447538] eth1: no IPv6 routers present
[  193.653986] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  193.814269] usb 2-2: configuration #1 chosen from 1 choice
[  194.380972] usbcore: registered new interface driver usbserial
[  194.383878] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  194.389808] usbcore: registered new interface driver usbserial_generic
[  194.389834] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  194.407113] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[  194.412962] pl2303 2-2:1.0: pl2303 converter detected
[  194.415851] usb 2-2: pl2303 converter now attached to ttyUSB0
[  194.419511] usbcore: registered new interface driver pl2303
[  194.419536] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
[  205.833388] usb 2-2: USB disconnect, address 2
[  205.834266] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[  205.834349] pl2303 2-2:1.0: device disconnected
[  226.921162] usb 2-2: new full speed USB device using uhci_hcd and address 3
[  227.082485] usb 2-2: configuration #1 chosen from 1 choice
[  227.084316] pl2303 2-2:1.0: pl2303 converter detected
[  227.084797] usb 2-2: pl2303 converter now attached to ttyUSB0
[  644.141505] usb 2-2: USB disconnect, address 3
[  644.142684] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[  644.142771] pl2303 2-2:1.0: device disconnected
[  860.399327] usb 2-2: new full speed USB device using uhci_hcd and address 4
[  860.614575] usb 2-2: configuration #1 chosen from 1 choice
[  860.616431] pl2303 2-2:1.0: pl2303 converter detected
[  860.617733] usb 2-2: pl2303 converter now attached to ttyUSB0
[ 1820.816636] usb 1-1: new low speed USB device using uhci_hcd and address 2
[ 1820.989933] usb 1-1: configuration #1 chosen from 1 choice
[ 1821.009436] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input7
[ 1821.052546] input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-1
chitra@chitra:~$

---

