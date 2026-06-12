---
title: "Pinnacle TV Tuner Card"
date: 2008-10-12
forum: Multimedia Software
---

### Post by tvks on 2008-10-12
Hi,

I am a new entrant in Linux (I have started with Ubuntu :) ).

I have just now installed Ubuntu and am wondering how to start using my Pinnacle TV Tuner card to start watching the Television channels.

Any help.. thanx a lot !!!

Regards,

tvks

---

### Post by lovinglinux on 2008-10-15
This is for analog card PCTV Stereo.

First install TVTime. You can find it in the Add/Remove manager or run the following command on a terminal.

```
sudo apt-get tvtime
```

Then you need to edit /etc/modprobe.d/options

Run the following command to open it with the text editor:

```
sudo gedit /etc/modprobe.d/options
```

In the editor, add the following line to the end of the file

```
options saa7134 [COLOR="Red"]**card=26**[/COLOR] [COLOR="Red"]**tuner=33**[/COLOR] alsa=1
```

You need to change the values in red, since they are card specific. Unless you have the same card as I have. You can find your card number [[COLOR="Red"]**here**[/COLOR]]("http://www.techsupportteam.org/forum/linux-alternative-os/5417-saa7134-pci-tv-tuner-cards-linux.html")

Back to the terminal run: 

```
sudo modprobe saa7134 [COLOR="Red"]**card=26**[/COLOR] [COLOR="Red"]**tuner=33**[/COLOR]
```

Reboot. Open TVTime through the Applications menu or by running this command:

```
tvtime
```

Configure TVTime with the OSD menu.Some important settings:

Input Configuration > Change video source: Television
Input Configuration > Television standard: NTSC, PAL-M....
Channel Management > Change Frequency table: Cable

Then do a channel scan:

Channel Management > Scan channels for signal

This should be enough to make TVTime tune some channels.

When you successfully run TVTime you can take a look the media center extension on my sig.

---

### Post by tvks on 2008-10-25
Hi,

Thanx a lot for the help.

But I am still stuck.

I do not know how to get my card number

"You need to change the values in red, since they are card specific. Unless you have the same card as I have. You can find your card number here"

I am also in a dilemma that I live in India and India is nowhere listed in the list of countries.

Pls help.

Regards

---

### Post by xc3RnbFO8P on 2008-10-25
We need more information about your TV card.
Is it **pci** or **usb**?
In Terminal show the output of :
> dmesg

---

### Post by uberdonkey5 on 2008-10-29
hey Ringi, have same problem.. here is my output (thanks for help):

[   13.876370] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   13.876407] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   13.880311] ehci_hcd 0000:00:1a.7: debug port 1
[   13.880319] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   13.880327] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xfed1c400
[   13.896031] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.896180] usb usb6: configuration #1 chosen from 1 choice
[   13.896213] hub 6-0:1.0: USB hub found
[   13.896221] hub 6-0:1.0: 4 ports detected
[   14.000094] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[   14.000115] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.000120] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.000153] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   14.004083] ehci_hcd 0000:00:1d.7: debug port 1
[   14.004092] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   14.004099] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfed1c000
[   14.019967] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.020130] usb usb7: configuration #1 chosen from 1 choice
[   14.020163] hub 7-0:1.0: USB hub found
[   14.020171] hub 7-0:1.0: 6 ports detected
[   14.124036] ahci 0000:00:1f.2: version 3.0
[   14.124076] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   14.124134] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   14.124138] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   14.491703] Clocksource tsc unstable (delta = -24332484755 ns)
[   14.495764] Time: hpet clocksource has been installed.
[   14.507071] usb 7-6: new high speed USB device using ehci_hcd and address 2
[   14.515878] usb 7-6: configuration #1 chosen from 1 choice
[   14.578551] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   14.578557] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   14.578565] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   14.578839] scsi0 : ahci
[   14.579144] scsi1 : ahci
[   14.579342] scsi2 : ahci
[   14.579712] ata1: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 219
[   14.579717] ata2: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb980 irq 219
[   14.579721] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 219
[   14.608393] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   14.648346] ata1.00: ATA-8: TOSHIBA MK2546GSX, LB012D, max UDMA/100
[   14.648352] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   14.648787] ata1.00: configured for UDMA/100
[   14.675701] ata2: SATA link down (SStatus 0 SControl 0)
[   14.692812] ata3: SATA link down (SStatus 0 SControl 300)
[   14.693072] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2546GS LB01 PQ: 0 ANSI: 5
[   14.693620] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   14.693661] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.693680] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   14.694216] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[   14.746935] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   14.757847] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.768767] Driver 'sd' needs updating - please use bus_type methods
[   14.768862] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   14.768879] sd 0:0:0:0: [sda] Write Protect is off
[   14.768882] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.768905] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.768970] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   14.768985] sd 0:0:0:0: [sda] Write Protect is off
[   14.768988] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.769010] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.769015]  sda:<6>ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   14.774089] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   14.774099] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   14.795131] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   14.795166] ata_piix 0000:00:1f.1: version 2.12
[   14.795186] b44.c:v2.0
[   14.795189] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   14.795233] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.795346] scsi3 : ata_piix
[   14.795433] scsi4 : ata_piix
[   14.796333] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   14.796337] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   14.801312] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:a5:36:89
[   14.806491]  sda1 sda2 sda3 < sda5 sda6 sda7 >
[   14.829958] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.836646] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.951778] ata4.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D200, max UDMA/33
[   15.033203] ata4.00: configured for UDMA/33
[   15.033301] ata5: port disabled. ignoring.
[   15.033543] Attempting manual resume
[   15.033546] swsusp: Resume From Partition 8:7
[   15.033549] PM: Checking swsusp image.
[   15.033695] PM: Resume from disk failed.
[   15.036782] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D200 PQ: 0 ANSI: 5
[   15.036888] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   15.053900] Driver 'sr' needs updating - please use bus_type methods
[   15.065505] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   15.065511] Uniform CD-ROM driver Revision: 3.20
[   15.065586] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   15.080439] kjournald starting.  Commit interval 5 seconds
[   15.080452] EXT3-fs: mounted filesystem with ordered data mode.
[   15.272224] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00030bb2470]
[   17.699338] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.751886] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.805858] Linux agpgart interface v0.102
[   18.143180] ACPI: AC Adapter [AC] (off-line)
[   18.252983] input: Lid Switch as /devices/virtual/input/input2
[   18.253687] ACPI: Lid Switch [LID]
[   18.253775] input: Power Button (CM) as /devices/virtual/input/input3
[   18.275883] ACPI: Power Button (CM) [PBTN]
[   18.276021] input: Sleep Button (CM) as /devices/virtual/input/input4
[   18.309986] ACPI: Sleep Button (CM) [SBTN]
[   18.551094] ACPI: Battery Slot [BAT0] (battery present)
[   18.592683] ACPI: WMI-Acer: Mapper loaded
[   18.830931] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input5
[   18.850483] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   18.862540] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
[   18.878463] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   18.878691] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
[   18.894452] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   19.207351] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   19.207356] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   19.207545] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   19.207563] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   19.207590] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.295978] nvidia: module license 'NVIDIA' taints kernel.
[   20.112521] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   20.112548] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   20.353009] iTCO_vendor_support: vendor-support=0
[   20.378968] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   20.733384] ricoh-mmc: Ricoh MMC Controller disabling driver
[   20.733388] ricoh-mmc: Copyright(c) Philip Langdale
[   20.930510] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000
[   20.930517] serio: Synaptics pass-through port at isa0060/serio1/input0
[   20.945346] sdhci: Secure Digital Host Controller Interface driver
[   20.945350] sdhci: Copyright(c) Pierre Ossman
[   20.970219] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   21.064189] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   21.064238] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.064562] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   21.146167] Linux video capture interface: v2.00
[   21.217276] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   21.217588] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   21.274890] usbcore: registered new interface driver uvcvideo
[   21.274897] USB Video Class driver (v0.1.0)
[   21.353402] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   22.350932] NET: Registered protocol family 17
[   22.426406] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   22.426436] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
[   22.426515] mmc0: SDHCI at 0xf9bfd400 irq 22 DMA
[   22.426773] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.426784] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   22.426911] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   22.438362] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   22.438378] ricoh-mmc: Controller is now disabled.
[   22.475139] iwl3945: Radio Frequency Kill Switch is On:
[   22.475142] Kill switch must be turned off for wireless networking to work.
[   22.481315] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   22.491364] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   22.511327] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   22.538901] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   22.559540] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   23.023967] lp: driver loaded but no devices found
[   23.168688] Adding 4313412k swap on /dev/sda7.  Priority:-1 extents:1 across:4313412k
[   23.205571] EXT3 FS on sda6, internal journal
[   23.721628] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.923482] PPP generic driver version 2.4.2
[   24.476346] No dock devices found.
[   26.381618] Bluetooth: Core ver 2.11
[   26.381992] NET: Registered protocol family 31
[   26.381998] Bluetooth: HCI device and connection manager initialized
[   26.382004] Bluetooth: HCI socket layer initialized
[   26.399621] Bluetooth: L2CAP ver 2.9
[   26.399630] Bluetooth: L2CAP socket layer initialized
[   26.455758] Bluetooth: RFCOMM socket layer initialized
[   26.455778] Bluetooth: RFCOMM TTY layer initialized
[   26.455782] Bluetooth: RFCOMM ver 1.8
[   35.403069] NET: Registered protocol family 10
[   35.403518] lo: Disabled Privacy Extensions
[   35.405257] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.599266] CPU0 attaching NULL sched-domain.
[   40.599278] CPU1 attaching NULL sched-domain.
[   40.622264] CPU0 attaching sched-domain:
[   40.622275]  domain 0: span 03
[   40.622279]   groups: 01 02
[   40.622286]   domain 1: span 03
[   40.622290]    groups: 03
[   40.622295] CPU1 attaching sched-domain:
[   40.622298]  domain 0: span 03
[   40.622302]   groups: 02 01
[   40.622308]   domain 1: span 03
[   40.622311]    groups: 03
[  325.603448] CPU0 attaching NULL sched-domain.
[  325.603459] CPU1 attaching NULL sched-domain.
[  325.608707] CPU0 attaching sched-domain:
[  325.608718]  domain 0: span 03
[  325.608722]   groups: 01 02
[  325.608729] CPU1 attaching sched-domain:
[  325.608733]  domain 0: span 03
[  325.608737]   groups: 02 01
[ 1451.489322] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 1451.514420] usb 3-1: configuration #1 chosen from 1 choice
[ 1451.701544] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.704717] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.706381] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.708388] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.825287] usbcore: registered new interface driver usbserial
[ 1451.825430] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 1451.825814] usbcore: registered new interface driver usbserial_generic
[ 1451.825817] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 1451.829941] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[ 1451.829966] airprime 3-1:1.0: airprime converter detected
[ 1451.830053] usb 3-1: airprime converter now attached to ttyUSB0
[ 1451.830096] usb 3-1: airprime converter now attached to ttyUSB1
[ 1451.830138] usb 3-1: airprime converter now attached to ttyUSB2
[ 1451.830147] usbcore: registered new interface driver airprime
[ 1451.853689] usbcore: registered new interface driver libusual
[ 1451.864300] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.866286] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.868288] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.870285] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.877063] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.879636] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.879793] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.880021] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.882279] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.883354] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.884357] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.885409] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.886314] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.887536] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.888270] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.889277] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.890279] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.891279] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.892278] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.893272] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.894272] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.895270] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.900440] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.901332] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.904290] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.910273] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.910481] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.910961] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1451.911506] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.913265] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.914239] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1451.915268] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.916254] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.917318] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1451.918241] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.919260] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1451.928079] usb 3-1: USB disconnect, address 2
[ 1451.928367] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
[ 1451.928458] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
[ 1451.928542] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
[ 1451.928554] airprime 3-1:1.0: device disconnected
[ 1452.466301] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 1452.529684] usb 3-1: configuration #1 chosen from 1 choice
[ 1452.532998] airprime 3-1:1.0: airprime converter detected
[ 1452.533165] usb 3-1: airprime converter now attached to ttyUSB0
[ 1452.533269] usb 3-1: airprime converter now attached to ttyUSB1
[ 1452.533371] usb 3-1: airprime converter now attached to ttyUSB2
[ 1452.536860] airprime 3-1:1.1: airprime converter detected
[ 1452.537018] usb 3-1: airprime converter now attached to ttyUSB3
[ 1452.537122] usb 3-1: airprime converter now attached to ttyUSB4
[ 1452.537243] usb 3-1: airprime converter now attached to ttyUSB5
[ 1452.539649] airprime 3-1:1.2: airprime converter detected
[ 1452.539767] usb 3-1: airprime converter now attached to ttyUSB6
[ 1452.539873] usb 3-1: airprime converter now attached to ttyUSB7
[ 1452.539977] usb 3-1: airprime converter now attached to ttyUSB8
[ 1452.640523] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[ 1452.640552] usbcore: registered new interface driver option
[ 1452.640554] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[ 1457.163470] airprime ttyUSB1: airprime_open - failed submitting read urb 0 for port 1, error -8
[ 1520.130326] usb 3-1: USB disconnect, address 3
[ 1520.131000] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
[ 1520.131288] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
[ 1520.131488] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
[ 1520.131517] airprime 3-1:1.0: device disconnected
[ 1520.131924] airprime ttyUSB3: airprime converter now disconnected from ttyUSB3
[ 1520.132109] airprime ttyUSB4: airprime converter now disconnected from ttyUSB4
[ 1520.132297] airprime ttyUSB5: airprime converter now disconnected from ttyUSB5
[ 1520.132325] airprime 3-1:1.1: device disconnected
[ 1520.132708] airprime ttyUSB6: airprime converter now disconnected from ttyUSB6
[ 1520.132895] airprime ttyUSB7: airprime converter now disconnected from ttyUSB7
[ 1520.133079] airprime ttyUSB8: airprime converter now disconnected from ttyUSB8
[ 1520.133107] airprime 3-1:1.2: device disconnected
[ 1523.827723] usb 3-2: new full speed USB device using uhci_hcd and address 4
[ 1523.986921] usb 3-2: configuration #1 chosen from 1 choice
[ 1523.990329] airprime 3-2:1.0: airprime converter detected
[ 1523.990522] usb 3-2: airprime converter now attached to ttyUSB0
[ 1523.990627] usb 3-2: airprime converter now attached to ttyUSB1
[ 1523.990730] usb 3-2: airprime converter now attached to ttyUSB2
[ 1524.170543] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.172531] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.174528] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.176530] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.244487] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.246488] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.248480] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.250479] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.253456] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.255452] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.257453] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.260468] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.261534] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.264522] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.265916] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.266179] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.267005] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.268169] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.269630] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.269851] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.271263] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.271493] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.273227] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.273506] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.274446] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.275468] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.277783] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.279618] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.279850] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.280464] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.282282] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.283640] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.284917] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.285445] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.287437] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.288435] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.289434] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 18 ret -71
[ 1524.295131] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 9 ret -71
[ 1524.297435] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 128 rq 6 len 32 ret -71
[ 1524.299476] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd huaweiAktBbo rqt 0 rq 3 len 0 ret -71
[ 1524.387367] usb 3-2: USB disconnect, address 4
[ 1524.387657] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
[ 1524.387748] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
[ 1524.387833] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
[ 1524.387845] airprime 3-2:1.0: device disconnected
[ 1525.339928] usb 3-2: new full speed USB device using uhci_hcd and address 5
[ 1525.422000] usb 3-2: configuration #1 chosen from 1 choice
[ 1525.424790] airprime 3-2:1.0: GSM modem (1-port) converter detected
[ 1525.424984] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1525.427976] airprime 3-2:1.1: GSM modem (1-port) converter detected
[ 1525.428154] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1525.429876] airprime 3-2:1.2: airprime converter detected
[ 1525.429991] usb 3-2: airprime converter now attached to ttyUSB2
[ 1525.430097] usb 3-2: airprime converter now attached to ttyUSB3
[ 1525.430203] usb 3-2: airprime converter now attached to ttyUSB4
[ 4113.723553] CPU0 attaching NULL sched-domain.
[ 4113.723568] CPU1 attaching NULL sched-domain.
[ 4113.728906] CPU0 attaching sched-domain:
[ 4113.728926]  domain 0: span 03
[ 4113.728930]   groups: 01 02
[ 4113.728941]   domain 1: span 03
[ 4113.728945]    groups: 03
[ 4113.728954] CPU1 attaching sched-domain:
[ 4113.728958]  domain 0: span 03
[ 4113.728966]   groups: 02 01
[ 4113.728971]   domain 1: span 03
[ 4113.728979]    groups: 03
[ 9421.690610] usb 7-3: new high speed USB device using ehci_hcd and address 7
[ 9421.729765] usb 7-3: configuration #1 chosen from 1 choice

---

### Post by xc3RnbFO8P on 2008-10-29
What is it pci or usb?

---

### Post by uberdonkey5 on 2008-10-29
ah, sorry... it is a usb Pinnacle PCTV Hybrid Pro

---

### Post by xc3RnbFO8P on 2008-10-29
Show the output of:
> lsusb

---

### Post by uberdonkey5 on 2008-10-29
Bus 007 Device 007: ID 2304:0226 Pinnacle Systems, Inc. [hex] 
Bus 007 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


:D

---

### Post by xc3RnbFO8P on 2008-10-29
Read this very carefully:
[http://mcentral.de/wiki/index.php5/Installation_Guide]("http://mcentral.de/wiki/index.php5/Installation_Guide")

---

### Post by uberdonkey5 on 2008-10-29
thanks ringi - will work through this and get back to you

ud5

---

### Post by tvks on 2008-11-16
Eureka !! :)

My TV is right now working properly.

[HTML]http://www.cyberciti.biz/tips/debian-ubuntu-linux-configure-pinnacle-pctv-tuner.html[/HTML]

The above website almost solved my problem.

I followed the instructions there but was still unable to get the Television going on.

Finally I changed the ownership of the folder in which TVTIME was installed using "chown" with my username and thats it !!!

I am watching TV right now... :guitar:

Thanx for everyone who tried to help me.

Regards,

tvks

---

