---
title: "Has anyone got a working DVB-S/S2 in Mythbuntu"
date: 2010-05-20
forum: Mythbuntu
---

### Post by petatkinson on 2010-05-20
Have been trying to get a functioning DVB-S/S2 card for quite a while.It seems the only cards that are discussed in any real detail here are DVB-T cards which appear to use a different chipset.The last functioning card I had working under Myth was the PVR350.It would be nice to have the cards I own working under MythTv which are the Hauppauge HVR4000, Hauppauge Nova S/S2and the Skystar HD.

---

### Post by mymythtv on 2010-05-20
I have a Nova S/S2 card running along with a Nova T-500 DVB-T - no problems.
Nova S/S2 is detected as card 69 ( if I remember correct ) out of the box in 0.22 / Mythbuntu 9.10

---

### Post by kamiKAC on 2010-05-20
I have DVB-S Technisat Skystar 2 (rev. 2.6D) card which worked in on Mythbuntu 9.10 with MythTV 0.22 out of the box. I have also configured sasc-ng and newcs with phoenix card reader to watch encrypted DVB-S channels.

---

### Post by petatkinson on 2010-05-20
Ok.I will give it a try again and report back

---

### Post by alien878 on 2010-05-21
You probably want to take a look here: [http://www.linuxtv.org/wiki/index.php/Hardware_Device_Information](http://www.linuxtv.org/wiki/index.php/Hardware_Device_Information)

I'm currently running a TerraTec Cinergy S2 PCI HD CI on 9.10 following the directions there.  I previously had a TechniSat SkyStar 2, but wanted an S2 card for HD.

---

### Post by dibuntux on 2010-05-21
I'm running on Nova TD-500 and an old Skystar 2 (believe 2.4); would like to go with a SkyStar HD but still unsure about being supported by Myth; I understand Nova S2 is working, but more expensive. 

Mythbuntu 9.10 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GS 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova TD-500 DVB-t

---

### Post by petatkinson on 2010-05-21
Ok.Tried to install Myth.No luck as expected.lsmod tells me that 26114 is not found.Most of the posts I found relating to this problem refer to 9.10 or earlier.Does anyone have any suggestions.

---

### Post by petatkinson on 2010-05-23
As I reported back 26114 firmware not loading.I assume this is the BDA driver from Hauppauge.I assumed that when I upgraded to 10.04 I would have solved my problem.Is there any way I can completely remove MythTV and reinstall it.What version of Myth is in the repos at the moment.I reckon this would be the only way to solve my problem

---

### Post by mymythtv on 2010-05-24
Arghh - thats right. I remember something about officiel firmware isn't working "out of the box".

I have 3 different firmwares available from different sources.

417cafd3b10e207e1dba9a03ad63e405  dvb-fe-cx24116-1.20.79.0.fw
b728b5d635393a4081e87d30d87a7632  dvb-fe-cx24116-1.22.82.0.fw
dd8dfdfca6b72462d9db8032f78631c8  dvb-fe-cx24116-1.23.86.1.fw

Currently I'm using dvb-fe-cx24116-1.22.82.0.fw which seems to work ok for me.

Getting one of those will proberly fix your problem. If you can't find then, just PM me.

---

### Post by Neon Dusk on 2010-05-24
The HVR4000 firmware in the ubuntu repos should be working now.

Just need to install linux-firmware-nonfree
```

sudo apt-get install linux-firmware-nonfree

```

---

### Post by petatkinson on 2010-05-24
Ok Neon Dusk.Did as you suggested.26114 is loading ok.Using Myth Backend the card probes both Analog cx88 Hauppauge HVR4000 Lite (which it is not) and cx24116/cx24118 DVB card.The Nova S2 as you know is purely a DVB-S card.When I select the DVB-S option and scan I get the message "failed to scan.....".The card is definitely working and scanning as confirmed in XP.Is there a conflict somewhere between the card being recognised as both an Analog and a DVB-S card.

---

### Post by Neon Dusk on 2010-05-25
In the backend you need to set card type as 'DVB DTV capture card (v3.x). It should then be shown as Conexant CX24116/CX24118

You also need to ensure that DiSEqc is set-up or else scanning will fail (it depends on your set-up but in most cases LNB -> Universal should work)

---

### Post by petatkinson on 2010-05-25
Ok.Tried your suggestion.No luck and Kaffeine reports device not found.Copy of dmesg output.

[    0.139712] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot
[    0.139717] pci 0000:00:09.0: PME# disabled
[    0.139805] pci 0000:01:00.0: reg 10 32bit mmio: [0xe4000000-0xe4ffffff]
[    0.139812] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.139836] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.139905] pci 0000:00:01.0: bridge 32bit mmio: [0xe4000000-0xe5ffffff]
[    0.139911] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.139921] pci_bus 0000:00: on NUMA node 0
[    0.139934] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.160975] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.161119] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.161243] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.161375] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.161507] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.161638] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[    0.161767] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
[    0.161896] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.162089] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.162094] vgaarb: loaded
[    0.162292] SCSI subsystem initialized
[    0.162428] libata version 3.00 loaded.
[    0.162564] usbcore: registered new interface driver usbfs
[    0.162582] usbcore: registered new interface driver hub
[    0.162633] usbcore: registered new device driver usb
[    0.162888] ACPI: WMI: Mapper loaded
[    0.162892] PCI: Using ACPI for IRQ routing
[    0.163126] NetLabel: Initializing
[    0.163129] NetLabel:  domain hash size = 128
[    0.163130] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.163149] NetLabel:  unlabeled traffic allowed by default
[    0.163215] Switching to clocksource tsc
[    0.163997] AppArmor: AppArmor Filesystem Enabled
[    0.163997] pnp: PnP ACPI init
[    0.163997] ACPI: bus type pnp registered
[    0.164606] pnp: PnP ACPI: found 9 devices
[    0.164612] ACPI: ACPI bus type pnp unregistered
[    0.164618] PnPBIOS: Disabled by ACPI PNP
[    0.164638] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[    0.164642] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.164646] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.164649] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.164652] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.164698] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.164702] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.164705] system 00:00: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.164709] system 00:00: iomem range 0xffee0000-0xffefffff has been reserved
[    0.164712] system 00:00: iomem range 0xfffe0000-0xfffeffff has been reserved
[    0.164715] system 00:00: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.164719] system 00:00: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.164731] system 00:02: ioport range 0x1c0-0x1cf has been reserved
[    0.164736] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.164739] system 00:02: ioport range 0x800-0x805 has been reserved
[    0.164742] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.199530] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.199533] pci 0000:00:01.0:   IO window: disabled
[    0.199540] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.199546] pci 0000:00:01.0:   PREFETCH window: 0xd8000000-0xdfffffff
[    0.199565] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.199569] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.199572] pci_bus 0000:01: resource 1 mem: [0xe4000000-0xe5ffffff]
[    0.199575] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xdfffffff]
[    0.199636] NET: Registered protocol family 2
[    0.199768] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.200287] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.201733] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.202470] TCP: Hash tables configured (established 131072 bind 65536)
[    0.202477] TCP reno registered
[    0.202702] NET: Registered protocol family 1
[    0.320698] pci 0000:01:00.0: Boot video device
[    0.320972] cpufreq-nforce2: No nForce2 chipset.
[    0.321015] Scanning for low memory corruption every 60 seconds
[    0.321182] audit: initializing netlink socket (disabled)
[    0.321201] type=2000 audit(1274784128.320:1): initialized
[    0.329696] Trying to unpack rootfs image as initramfs...
[    0.341161] highmem bounce pool size: 64 pages
[    0.341171] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.342901] VFS: Disk quotas dquot_6.5.2
[    0.342998] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.349219] fuse init (API version 7.13)
[    0.349409] msgmni has been set to 1716
[    0.349834] alg: No test for stdrng (krng)
[    0.349970] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.349974] io scheduler noop registered
[    0.349976] io scheduler anticipatory registered
[    0.349978] io scheduler deadline registered
[    0.350031] io scheduler cfq registered (default)
[    0.350179] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.350213] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.350351] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.350357] ACPI: Power Button [PWRB]
[    0.350424] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.350428] ACPI: Power Button [PWRF]
[    0.350489] fan PNP0C0B:00: registered as cooling_device0
[    0.350496] ACPI: Fan [FAN] (on)
[    0.350764] processor LNXCPU:00: registered as cooling_device1
[    0.352976] thermal LNXTHERM:01: registered as thermal_zone0
[    0.352991] ACPI: Thermal Zone [THRM] (61 C)
[    0.356916] isapnp: Scanning for PnP cards...
[    0.362804] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.364472] brd: module loaded
[    0.369423] loop: module loaded
[    0.369621] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.369829] pata_sis 0000:00:02.5: version 0.5.2
[    0.369860]   alloc irq_desc for 16 on node -1
[    0.369863]   alloc kstat_irqs on node -1
[    0.369875] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.370115] scsi0 : pata_sis
[    0.416546] scsi1 : pata_sis
[    0.417474] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14
[    0.417478] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15
[    0.417650]   alloc irq_desc for 17 on node -1
[    0.417654]   alloc kstat_irqs on node -1
[    0.417665] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.417737] pata_acpi 0000:00:05.0: PCI INT A disabled
[    0.418141] Fixed MDIO Bus: probed
[    0.418191] PPP generic driver version 2.4.2
[    0.418309] tun: Universal TUN/TAP device driver, 1.6
[    0.418312] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.418462] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.418506]   alloc irq_desc for 23 on node -1
[    0.418509]   alloc kstat_irqs on node -1
[    0.418520] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.418556] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.418635] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.418689] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
[    0.418713] ehci_hcd 0000:00:03.3: irq 23, io mem 0xea023000
[    0.429100] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.429334] usb usb1: configuration #1 chosen from 1 choice
[    0.429379] hub 1-0:1.0: USB hub found
[    0.429401] hub 1-0:1.0: 8 ports detected
[    0.429506] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.429544]   alloc irq_desc for 20 on node -1
[    0.429547]   alloc kstat_irqs on node -1
[    0.429558] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.429587] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.429674] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.429715] ohci_hcd 0000:00:03.0: irq 20, io mem 0xea020000
[    0.506481] usb usb2: configuration #1 chosen from 1 choice
[    0.506525] hub 2-0:1.0: USB hub found
[    0.506546] hub 2-0:1.0: 3 ports detected
[    0.506630]   alloc irq_desc for 21 on node -1
[    0.506633]   alloc kstat_irqs on node -1
[    0.506645] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.506674] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    0.506768] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    0.506806] ohci_hcd 0000:00:03.1: irq 21, io mem 0xea021000
[    0.598512] usb usb3: configuration #1 chosen from 1 choice
[    0.598566] hub 3-0:1.0: USB hub found
[    0.598587] hub 3-0:1.0: 3 ports detected
[    0.598664]   alloc irq_desc for 22 on node -1
[    0.598667]   alloc kstat_irqs on node -1
[    0.598678] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.598708] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    0.598792] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    0.598832] ohci_hcd 0000:00:03.2: irq 22, io mem 0xea022000
[    0.613307] ata1.00: ATA-7: Hitachi HDT725025VLAT80, V5DOA42A, max UDMA/133
[    0.613313] ata1.00: 488397168 sectors, multi 16: LBA48 
[    0.613360] ata1.01: ATAPI: QSI CD-RW/DVD-ROM SBW242C, UQ81, max UDMA/33
[    0.629484] ata1.00: configured for UDMA/133
[    0.645193] ata1.01: configured for UDMA/33
[    0.691049] usb usb4: configuration #1 chosen from 1 choice
[    0.691100] hub 4-0:1.0: USB hub found
[    0.691120] hub 4-0:1.0: 2 ports detected
[    0.691205] uhci_hcd: USB Universal Host Controller Interface driver
[    0.691335] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.691686] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.691705] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.692301] mice: PS/2 mouse device common for all mice
[    0.692489] rtc_cmos 00:04: RTC can wake from S4
[    0.692580] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.692614] rtc0: alarms up to one year, 242 bytes nvram
[    0.692814] device-mapper: uevent: version 1.0.3
[    0.693073] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.695228] device-mapper: multipath: version 1.1.0 loaded
[    0.695236] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.696582] EISA: Probing bus 0 at eisa.0
[    0.696594] Cannot allocate resource for EISA slot 1
[    0.696603] Cannot allocate resource for EISA slot 4
[    0.696620] EISA: Detected 0 cards.
[    0.700744] cpuidle: using governor ladder
[    0.700750] cpuidle: using governor menu
[    0.701451] TCP cubic registered
[    0.701651] NET: Registered protocol family 10
[    0.702247] lo: Disabled Privacy Extensions
[    0.702612] NET: Registered protocol family 17
[    0.702722] Using IPI No-Shortcut mode
[    0.702889] PM: Resume from disk failed.
[    0.702915] registered taskstats version 1
[    0.703225]   Magic number: 10:615:730
[    0.703340] rtc_cmos 00:04: setting system clock to 2010-05-25 10:42:09 UTC (1274784129)
[    0.703344] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.703346] EDD information not available.
[    0.715572] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.784274] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.894159] Freeing initrd memory: 7776k freed
[    0.992697] isapnp: No Plug & Play device found
[    0.992946] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5
[    0.993212] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.996876] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.996962] sd 0:0:0:0: [sda] Write Protect is off
[    0.996967] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.997010] scsi 0:0:1:0: CD-ROM            QSI      CDRW/DVD SBW242C UQ81 PQ: 0 ANSI: 5
[    0.997735] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.998923]  sda: sda1 sda2 <sr0: scsi3-mmc drive: 1x/24x writer cd/rw xa/form2 cdda tray
[    1.014917] Uniform CD-ROM driver Revision: 3.20
[    1.015106] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.015210] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.015346] ata2: port disabled. ignoring.
[    1.030021]  sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 >
[    1.118297] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.118322] Freeing unused kernel memory: 656k freed
[    1.119322] Write protecting the kernel text: 4676k
[    1.119355] Write protecting the kernel read-only data: 1840k
[    1.132160] usb 1-1: configuration #1 chosen from 1 choice
[    1.159949] udev: starting version 151
[    1.208118] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.354588] usb 1-3: configuration #1 chosen from 1 choice
[    1.536805] Initializing USB Mass Storage driver...
[    1.542146] sata_sis 0000:00:05.0: version 1.0
[    1.542234] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.542242] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[    1.548139] scsi3 : sata_sis
[    1.566426] sis900.c: v1.08.10 Apr. 2 2006
[    1.566489] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.566914] scsi4 : sata_sis
[    1.567238] ata3: SATA max UDMA/133 cmd 0xe300 ctl 0xe400 bmdma 0xe700 irq 17
[    1.567245] ata4: SATA max UDMA/133 cmd 0xe500 ctl 0xe600 bmdma 0xe708 irq 17
[    1.567734]   alloc irq_desc for 19 on node -1
[    1.567739]   alloc kstat_irqs on node -1
[    1.567750] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.568884] 0000:00:04.0: Unknown PHY transceiver found at address 1.
[    1.580042] 0000:00:04.0: Using transceiver found at address 1 as default
[    1.590224] usbcore: registered new interface driver usb-storage
[    1.590231] USB Mass Storage support registered.
[    1.590546] usb-storage: device found at 3
[    1.590551] usb-storage: waiting for device to settle before scanning
[    1.649624] eth0: SiS 900 PCI Fast Ethernet at 0xe200, IRQ 19, 00:01:6c:b9:28:3b
[    1.902857] ata3: SATA link down (SStatus 0 SControl 300)
[    2.098203] EXT4-fs (sda12): INFO: recovery required on readonly filesystem
[    2.098212] EXT4-fs (sda12): write access will be enabled during recovery
[    2.230911] ata4: SATA link down (SStatus 0 SControl 300)
[    2.238593] ohci1394 0000:00:09.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.294167] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[ea024000-ea0247ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    3.572216] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c20000b9475]
[    4.327661] EXT4-fs (sda12): recovery complete
[    4.328076] EXT4-fs (sda12): mounted filesystem with ordered data mode
[    6.588658] usb-storage: device scan complete
[    6.592756] scsi 2:0:0:0: Direct-Access     Foxconn  CF  USB2.0 Reade 9144 PQ: 0 ANSI: 0
[    6.597006] scsi 2:0:0:1: Direct-Access     Foxconn  SM  USB2.0 Reade 9144 PQ: 0 ANSI: 0
[    6.601625] scsi 2:0:0:2: Direct-Access     Foxconn  SD  USB2.0 Reade 9144 PQ: 0 ANSI: 0
[    6.605734] scsi 2:0:0:3: Direct-Access     Foxconn  MS  USB2.0 Reade 9144 PQ: 0 ANSI: 0
[    6.606493] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.606736] sd 2:0:0:1: Attached scsi generic sg3 type 0
[    6.606967] sd 2:0:0:2: Attached scsi generic sg4 type 0
[    6.607196] sd 2:0:0:3: Attached scsi generic sg5 type 0
[    6.613225] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    6.614206] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    6.615630] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[    6.616581] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   17.363216] Adding 2891660k swap on /dev/sda13.  Priority:-1 extents:1 across:2891660k 
[   17.662041] udev: starting version 151
[   17.919024] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.995094] Linux agpgart interface v0.103
[   18.105844] agpgart-sis 0000:00:00.0: SiS chipset [1039/0661]
[   18.180791] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   18.469927] lp: driver loaded but no devices found
[   18.500741] vga16fb: initializing
[   18.500747] vga16fb: mapped to 0xc00a0000
[   18.500870] fb0: VGA16 VGA frame buffer device
[   18.722996] cfg80211: Calling CRDA to update world regulatory domain
[   18.764691] cfg80211: World regulatory domain updated:
[   18.764698] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.764702] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.764705] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.764708] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.764711] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.764714] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.841696] type=1505 audit(1274780547.636:2):  operation="profile_load" pid=554 name="/sbin/dhclient3"
[   18.842387] type=1505 audit(1274780547.636:3):  operation="profile_load" pid=554 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.842756] type=1505 audit(1274780547.636:4):  operation="profile_load" pid=554 name="/usr/lib/connman/scripts/dhclient-script"
[   18.863731] type=1505 audit(1274780547.656:5):  operation="profile_load" pid=562 name="/usr/sbin/ntpd"
[   19.355370] type=1505 audit(1274780548.148:6):  operation="profile_load" pid=645 name="/usr/share/gdm/guest-session/Xsession"
[   19.360423] type=1505 audit(1274780548.156:7):  operation="profile_replace" pid=646 name="/sbin/dhclient3"
[   19.361147] type=1505 audit(1274780548.156:8):  operation="profile_replace" pid=646 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.361535] type=1505 audit(1274780548.156:9):  operation="profile_replace" pid=646 name="/usr/lib/connman/scripts/dhclient-script"
[   19.369677] type=1505 audit(1274780548.164:10):  operation="profile_load" pid=647 name="/usr/bin/evince"
[   19.381297] type=1505 audit(1274780548.176:11):  operation="profile_load" pid=647 name="/usr/bin/evince-previewer"
[   19.587938] nvidia: module license 'NVIDIA' taints kernel.
[   19.587945] Disabling lock debugging due to kernel taint
[   20.400192] NVRM: The NVIDIA GeForce FX 5200 GPU installed in this system is
[   20.400196] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers. Please
[   20.400198] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[   20.400199] NVRM:  information.  The 195.36.15 NVIDIA driver will ignore
[   20.400201] NVRM:  this GPU.  Continuing probe...
[   20.400211] NVRM: No NVIDIA graphics adapter found!
[   20.405569] Linux video capture interface: v2.00
[   20.572888] psmouse serio1: ID: 10 00 64
[   20.747715] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   21.161744] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   21.162081] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   21.162084] cx88[0]: TV tuner type -1, Radio tuner type -1
[   21.184600] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   21.186831] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.274712] Console: switching to colour frame buffer device 80x30
[   21.681546] cx2388x alsa driver version 0.0.7 loaded
[   21.773270] tveeprom 0-0050: Hauppauge model 69100, rev B4C3, serial# 6565967
[   21.773276] tveeprom 0-0050: MAC address is 00-0D-FE-64-30-4F
[   21.773279] tveeprom 0-0050: tuner model is Conexant CX24118A (idx 123, type 4)
[   21.773283] tveeprom 0-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   21.773286] tveeprom 0-0050: audio processor is None (idx 0)
[   21.773289] tveeprom 0-0050: decoder processor is CX880 (idx 20)
[   21.773292] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   21.773296] cx88[0]: hauppauge eeprom: model=69100
[   21.776743] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   21.777071] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   21.777434] usbcore: registered new interface driver rt2500usb
[   21.795128] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:08.2/input/input5
[   21.795483] cx88[0]/2: cx2388x 8802 Driver Manager
[   21.795515]   alloc irq_desc for 18 on node -1
[   21.795518]   alloc kstat_irqs on node -1
[   21.795531] cx88-mpeg driver manager 0000:00:08.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.795542] cx88[0]/2: found at 0000:00:08.2, rev: 5, irq: 18, latency: 32, mmio: 0xe8000000
[   21.795556] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   21.795706] cx8800 0000:00:08.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.795718] cx88[0]/0: found at 0000:00:08.0, rev: 5, irq: 18, latency: 32, mmio: 0xe6000000
[   21.795735] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   21.795894] cx88[0]/0: registered device video0 [v4l2]
[   21.795956] cx88[0]/0: registered device vbi0
[   21.796920] cx88_audio 0000:00:08.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.796934] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   21.796974] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   22.266194] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   22.508533] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   22.508539] cx88/2: registering cx8802 driver, type: dvb access: shared
[   22.508544] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   22.508548] cx88[0]/2: cx2388x based DVB/ATSC card
[   22.508551] cx8802_alloc_frontends() allocating 1 frontend(s)
[   22.547654] phy1: Selected rate control algorithm 'minstrel'
[   22.548797] Registered led device: rt73usb-phy1::radio
[   22.548825] Registered led device: rt73usb-phy1::assoc
[   22.548848] Registered led device: rt73usb-phy1::quality
[   22.552832] usbcore: registered new interface driver rt73usb
[   22.592160] rt73usb 1-1:1.0: firmware: requesting rt73.bin
[   22.600081] intel8x0_measure_ac97_clock: measured 53020 usecs (2551 samples)
[   22.600087] intel8x0: clocking to 48000
[   22.849608] DVB: registering new adapter (cx88[0])
[   22.849617] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[   22.895187] ppdev: user-space parallel port driver
[   22.904874] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.519480] [drm] Initialized drm 1.1.0 20060810
[   26.769205] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.784546] [drm] nouveau 0000:01:00.0: Detected an NV30 generation card (0x034200b1)
[   26.784647] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PROM
[   26.913383] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   26.913501] [drm] nouveau 0000:01:00.0: BMP BIOS found
[   26.913504] [drm] nouveau 0000:01:00.0: BMP version 5.38
[   26.913508] [drm] nouveau 0000:01:00.0: Bios version 04.34.20.18
[   26.913511] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 2.2
[   26.913516] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 000088b8
[   26.913520] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02010310 000088b8
[   26.913522] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 01010312 00000000
[   26.913525] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02020321 00000003
[   26.913615] [drm] nouveau 0000:01:00.0: Loading NV17 power sequencing microcode
[   26.913620] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x716A
[   26.913655] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x7365
[   26.913664] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x74AB
[   26.913699] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x7631
[   26.913704] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x764E
[   26.913709] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 5 at offset 0x766B
[   26.920429] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 6 at offset 0x77DC
[   26.934246] [TTM] Zone  kernel: Available graphics memory: 443594 kiB.
[   26.934251] [TTM] Zone highmem: Available graphics memory: 513198 kiB.
[   26.934279] [drm] nouveau 0000:01:00.0: 128 MiB VRAM
[   26.934883] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[   26.934905] agpgart: modprobe tried to set rate=x12. Setting to AGP3 x8 mode.
[   26.934915] agpgart-sis 0000:00:00.0: putting AGP V3 device into 8x mode
[   26.935905] nouveau 0000:01:00.0: putting AGP V3 device into 8x mode
[   26.935909] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   26.937434] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[   26.938394] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[   26.938410] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[   26.938536] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[   26.941875] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   26.942250] [drm] nouveau 0000:01:00.0: Detected a TV connector
[   26.943563] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   26.943569] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 1)
[   26.943573] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 2)
[   26.943577] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 3)
[   27.142262] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[   27.142274] cx88-mpeg driver manager 0000:00:08.2: firmware: requesting dvb-fe-cx24116.fw
[   27.175207] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[   32.264089] [drm] nouveau 0000:01:00.0: Load detected on output B
[   32.264330] [drm] nouveau 0000:01:00.0: allocated 1360x768 fb: 0x49000, bo f1632600
[   32.265506] fb1: nouveaufb frame buffer device
[   32.265510] registered panic notifier
[   32.265527] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[   32.508439] cx24116_load_firmware: FW version 1.26.90.0
[   32.508462] cx24116_firmware_ondemand: Firmware upload complete
[   32.541536] [drm] nouveau 0000:01:00.0: Load detected on output B
[   32.868300] [drm] nouveau 0000:01:00.0: Load detected on output B
[   32.904663] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   32.905657] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   33.015393] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[   33.015403] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
[   33.034772] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on TV encoder (output 3)
[   33.034782] [drm] nouveau 0000:01:00.0: Output TV-1 is running on CRTC 1 using output B
[   35.488013] [drm] nouveau 0000:01:00.0: Load detected on output B
[   35.792013] [drm] nouveau 0000:01:00.0: Load detected on output B
[   36.116015] [drm] nouveau 0000:01:00.0: Load detected on output B
[   42.992015] [drm] nouveau 0000:01:00.0: Load detected on output B
[   48.277429] wlan0: deauthenticating from 00:0f:cc:bb:bf:fc by local choice (reason=3)
[   48.282445] wlan0: direct probe to AP 00:0f:cc:bb:bf:fc (try 1)
[   48.284374] wlan0: direct probe responded
[   48.284382] wlan0: authenticate with AP 00:0f:cc:bb:bf:fc (try 1)
[   48.285808] wlan0: authenticated
[   48.285847] wlan0: associate with AP 00:0f:cc:bb:bf:fc (try 1)
[   48.287965] wlan0: RX AssocResp from 00:0f:cc:bb:bf:fc (capab=0x451 status=0 aid=1)
[   48.287977] wlan0: associated
[   48.300927] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.264022] wlan0: no IPv6 routers present

and copy of lsmod

Module                  Size  Used by
nouveau               467048  1 
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
drm                   162471  4 nouveau,ttm,drm_kms_helper
binfmt_misc             6587  1 
ppdev                   5259  0 
isl6421                 1349  1 
cx24116                14429  1 
arc4                    1153  2 
cx88_dvb               19413  1 
cx88_vp3054_i2c         1808  1 cx88_dvb
snd_intel8x0           25588  2 
videobuf_dvb            5175  1 cx88_dvb
snd_ac97_codec        100646  1 snd_intel8x0
dvb_core               86142  2 cx88_dvb,videobuf_dvb
ac97_bus                1002  1 snd_ac97_codec
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
snd_seq_dummy           1338  0 
tuner                  20412  0 
snd_seq_oss            26726  0 
cx88_alsa               8051  1 
snd_pcm_oss            35308  0 
snd_seq_midi            4557  0 
rt2500usb              18141  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_mixer_oss          13746  1 snd_pcm_oss
rt2x00usb               9703  2 rt73usb,rt2500usb
snd_pcm                70662  4 snd_intel8x0,snd_ac97_codec,cx88_alsa,snd_pcm_oss
cx8800                 27188  0 
fbcon                  35102  71 
cx8802                 12841  1 cx88_dvb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
tileblit                2031  1 fbcon
cx88xx                 72596  4 cx88_dvb,cx88_alsa,cx8800,cx8802
led_class               2864  1 rt2x00lib
font                    7557  1 fbcon
v4l2_common            15431  3 tuner,cx8800,cx88xx
ir_common              38875  1 cx88xx
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              204922  2 rt2x00usb,rt2x00lib
snd_timer              19098  2 snd_pcm,snd_seq
bitblit                 4707  1 fbcon
i2c_algo_bit            5028  3 nouveau,cx88_vp3054_i2c,cx88xx
videodev               34361  4 tuner,cx8800,cx88xx,v4l2_common
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63245  0 
v4l1_compat            13251  1 videodev
tveeprom               11102  1 cx88xx
cfg80211              126485  2 rt2x00lib,mac80211
vga16fb                11385  1 
videobuf_dma_sg        10782  5 cx88_dvb,cx88_alsa,cx8800,cx8802,cx88xx
videobuf_core          16356  5 videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg
btcx_risc               3624  4 cx88_alsa,cx8800,cx8802,cx88xx
vgastate                8961  1 vga16fb
serio_raw               3978  0 
snd                    54148  17 snd_intel8x0,snd_ac97_codec,snd_seq_oss,cx88_alsa,snd_pcm_oss,snd_rawmidi,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
sis_agp                 4047  1 
lp                      7028  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
agpgart                31724  3 ttm,drm,sis_agp
shpchp                 28820  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
sis900                 17048  0 
mii                     4381  1 sis900
sata_sis                3332  0 
usb_storage            39425  0 


anything obvious from these reports

---

### Post by petatkinson on 2010-05-25
Just to update.I disconnected my wireless USB dongle.I then launched Kaffeine and for the first time ever I was able to do a scan.When I finished the scan I tried to view a channel.Just got channel numbers.Closed Kaffeine restarted it again and  got "Device not found" again.I am convinced the problem lies with some sort if IRQ conflict somewhere but where is the problem

---

### Post by Neon Dusk on 2010-05-25
Are you stopping the mythtv-backend when trying to use the card in other software?
```

sudo stop mythtv-backend

```
(if you don't it may be locking the card preventing it being used)

What happens when you try to scan in mythtv - are you supplying the details (freq, symbol rate, polairty etc..) for the transponder to start the scan on

---

### Post by petatkinson on 2010-05-25
Ok Neon.Done as  you suggested.Stopped Myth backend and Kaffeine is working fine.Now I know the card is working.Put the settings etc into Myth and still nothing.Says it cant find any channels on a transponder.When configuring the card Myth probes the Analog Hauppauge HVR4000 as well as DVB 26114/26116 even though this is purely a DVB S2 card

---

### Post by Neon Dusk on 2010-05-25
It shouldn't matter is Myth is picking up an anlogue card as long as it's set to 'DVB DTV capture card (v3.x)'

When you do the scan what are using for the initial scan settings?

If your scanning Astra 28.2 / Eurobird 28.5 you can use :-
```

Freq: 10714000
Polarity: Horizontal
Symbol rate: 22000000
Mod Sys: DVB-S
FEC: 5/6
Modulation: QPSK
Inversion: leave at auto
Rolloff: leave at 0.35

```

As shown [here](http://parker1.co.uk/mythtv_freesat.php) Otherwise you'll need to look up the details at one of the satellite sites e.g. Lyngsat KingOfSat

Edit: Can you also confirm that DiSEqc is set-up. I've seen reports of people setting up DiSEqc but when they return to the DiSEqc screen the values haven't been saved.

---

### Post by petatkinson on 2010-05-25
Neon Dusk.I done a fresh installation of 10.04 (I had 10.04 by way of upgrade from 9.10).Firstly I have Kaffeine working rock solid so thats that solved.I installed the latest version of Myth from the repos.Ran backend and got "No UPnP" and it kicks me back to page 1 of the config screen asking me to enter my hostname,username password, port number.Everytime I enter the info I'm back to the same screen.Do you think this is something to do with the MySQL file for Myth.The UPnP message really has me stumped.At least I know the card is working under Linux now but I really would like to get Myth working.A real PITA I know.Thanks for all your help so far

---

### Post by Neon Dusk on 2010-05-25
It sounds like MySQL isn't running. How did you do the install of 10.04? Was it Ubuntu 10.04 or Mythbuntu 10.04.

If it was Ubuntu 10.04 how did you add MythTV? - it's probably best to install the mythbuntu-control-centre and then configure the roles from there.

---

### Post by petatkinson on 2010-05-26
Neon.I installed Mythbuntu Control Centre downloaded from the Mythbuntu site.Everything downloads fine and as soon as it comes to card configuration I cannot pass page 1 of 2.It appears to be that I cannot connect to Port 3006, the default port and I cannot connect to MySQL database.Could you confirm what port you are connected to and how do I edit MySQL database and settings.It looks like this is the area that is causing the difficulty.I completely removed Myth and am going to try again.

---

### Post by petatkinson on 2010-05-26
Neon.Solved the backend problem.Copied the contents of mysql.txt and used it as the sign on for backend.I'm in and configuring now.Back to my old problem.No successful scan yet.This is a Hauppauge HVR4000 card which incorporates DVB-S/DVB-T Analogue and FM Radio.I tried the Analogue option and it scanned and found two channels.Interference I might add but it found something but there is no way it will scan using the Connexant 24116/24118 firmware.I am sure I saw a post somewhere that said you could assign the DVB-S option to a particular IRQ.I noticed that under Myth the assigned IRQ for 24116 is 1 while running Kaffeine the IRQ is 6.This would explain how the cx88 firmware is operational and not the 24116 as the cx88 is getting preference on IRQ 1 while the 24116 is causing conflict.Could you confirm what IRQ is assigned to your 24116 driver.Anyone else that might have a solution please feel to throw your lot in.

---

### Post by bance on 2010-05-26
I have the same hauppage 4000 quad mode card, and I did manage to get it to scan..... eventually.  

The problem I had was that when I made the settings for dseq they wouldn't stick........  you have to keep making the settings.

Meanwhile I now have a problem setting the port for the database, same problem, the settings won't stick. This on a remote machine.

---

### Post by petatkinson on 2010-05-26
When I get to the "2.Capture cards" menu I sellect "Diseqc" and the option is "Unconnected".I select this and nothing happens.What does unconnected mean in this case.

---

### Post by Neon Dusk on 2010-05-26
It means that DiSEqC isn't configured.

If you press the down key then the background colour for 'unconnected' should change and you can then use <enter> to enter the DiSEqC settings screen

---

### Post by petatkinson on 2010-05-26
Neon Dusk.That simple option called Diseqc was the problem.The LNB settings are not Diseqc settings.Before Diseqc was ever invented there was LNB settings.The fact that it was the only option on the screen and when I hit return and got "not connected" message (which is as verbose as ever) I assumed it pointed to another problem.Also DVBS support has always been flaky at best over the years so I assumed, here we go again.Also why has the kernel still got dodgy firmware ala cx26114 in it.

Again, a big thank you to you for resolving this.Your answers were simple, straight to the point and most of all very helpful.I think the forum for Mythbuntu should be broken up into the different releases it has worked in.Saves a lot of hassle searching for a solution when you find the answer refers to release 8.10 when you are using 10.04 etc.:popcorn:

I owe you one:P:popcorn:

---

