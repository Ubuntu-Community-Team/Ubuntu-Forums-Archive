---
title: "Wireless &quot;disconnected&quot; or &quot;device not ready.&quot;"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by Twizlerr on 2010-06-21
[FONT=Arial][SIZE=2]Hello,[/SIZE][/FONT]
[FONT=Arial][SIZE=2]     I'm new to Linux and I'm a bit stuck at the moment. I downloaded Ubuntu 10.04 and burnt it to a CD so I could try Ubuntu before installing it via Live CD. It automatically displayed the window where you download drivers for your hardware, I activated the Broadcom drivers, and WiFi worked fine. So then I installed it inside of Windows (as a dual-boot). Now, when I open the hardware managing window (I forget what it's called), there are no drivers listed to be activated. Since I am unable to activate the Broadcom divers, I can't get internet over wifi. Also, I don't have access to a wired connection, but I do have blank CD's and a USB stick (if that helps). How can I fix this?[/SIZE][/FONT]
[SIZE=2][FONT=Arial]Here are my results from the commands listed [on this post]("http://ubuntuforums.org/showthread.php?t=982880"):[/FONT][/SIZE]

Dell Laptop Inspiron 1501
Windows XP Home Edition
Ubuntu 10.04 LTS
```

    [FONT=&quot][    0.160127] NET: Registered protocol family 2
[    0.160224] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.160618] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.161586] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.162116] TCP: Hash tables configured (established 131072 bind 65536)
[    0.162120] TCP reno registered
[    0.162220] NET: Registered protocol family 1
[    0.162236] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.162241] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.162323] pci 0000:01:05.0: Boot video device
[    0.162542] cpufreq-nforce2: No nForce2 chipset.
[    0.162573] Scanning for low memory corruption every 60 seconds
[    0.162697] audit: initializing netlink socket (disabled)
[    0.162714] type=2000 audit(1277066991.159:1): initialized
[    0.173979] Trying to unpack rootfs image as initramfs...
[    0.188016] highmem bounce pool size: 64 pages
[    0.188023] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.189644] VFS: Disk quotas dquot_6.5.2
[    0.189711] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.196392] fuse init (API version 7.13)
[    0.196522] msgmni has been set to 1693
[    0.196753] alg: No test for stdrng (krng)
[    0.196813] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.196817] io scheduler noop registered
[    0.196820] io scheduler anticipatory registered
[    0.196822] io scheduler deadline registered
[    0.196871] io scheduler cfq registered (default)
[    0.197045] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.197069] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.197810] ACPI: AC Adapter [ACAD] (on-line)
[    0.197876] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.197881] ACPI: Power Button [PWRB]
[    0.197940] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.197947] ACPI: Sleep Button [SLPB]
[    0.197992] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.198626] ACPI: Lid Switch [LID]
[    0.198675] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.198678] ACPI: Power Button [PWRF]
[    0.198881] Marking TSC unstable due to TSC halts in idle
[    0.198948] processor LNXCPU:00: registered as cooling_device0
[    0.203092] Switching to clocksource acpi_pm
[    0.204389] thermal LNXTHERM:01: registered as thermal_zone0
[    0.204398] ACPI: Thermal Zone [THRM] (71 C)
[    0.205966] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.207300] brd: module loaded
[    0.207770] loop: module loaded
[    0.207863] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.212426]   alloc irq_desc for 16 on node -1
[    0.212430]   alloc kstat_irqs on node -1
[    0.212439] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.212518] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.212885] Fixed MDIO Bus: probed
[    0.212922] PPP generic driver version 2.4.2
[    0.212994] tun: Universal TUN/TAP device driver, 1.6
[    0.212996] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.213093] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.213112]   alloc irq_desc for 19 on node -1
[    0.213114]   alloc kstat_irqs on node -1
[    0.213119] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.213140] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.213181] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.213211] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.213228] ehci_hcd 0000:00:13.5: debug port 1
[    0.213256] ehci_hcd 0000:00:13.5: irq 19, io mem 0xc0004400
[    0.213414] isapnp: Scanning for PnP cards...
[    0.266874] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.267038] usb usb1: configuration #1 chosen from 1 choice
[    0.267071] hub 1-0:1.0: USB hub found
[    0.267084] hub 1-0:1.0: 10 ports detected
[    0.267176] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.267198] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.267246] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.267296] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.267332] ohci_hcd 0000:00:13.0: irq 16, io mem 0xc0005000
[    0.355813] usb usb2: configuration #1 chosen from 1 choice
[    0.355851] hub 2-0:1.0: USB hub found
[    0.355866] hub 2-0:1.0: 2 ports detected
[    0.355927]   alloc irq_desc for 17 on node -1
[    0.355930]   alloc kstat_irqs on node -1
[    0.355937] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.355959] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.355998] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.356044] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0006000
[    0.443952] usb usb3: configuration #1 chosen from 1 choice
[    0.443983] hub 3-0:1.0: USB hub found
[    0.444015] hub 3-0:1.0: 2 ports detected
[    0.444073]   alloc irq_desc for 18 on node -1
[    0.444076]   alloc kstat_irqs on node -1
[    0.444083] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.444129] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.444173] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.444208] ohci_hcd 0000:00:13.2: irq 18, io mem 0xc0007000
[    0.532306] usb usb4: configuration #1 chosen from 1 choice
[    0.532338] hub 4-0:1.0: USB hub found
[    0.532353] hub 4-0:1.0: 2 ports detected
[    0.532411] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.532460] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.532500] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.532522] ohci_hcd 0000:00:13.3: irq 17, io mem 0xc0008000
[    0.620057] usb usb5: configuration #1 chosen from 1 choice
[    0.620090] hub 5-0:1.0: USB hub found
[    0.620106] hub 5-0:1.0: 2 ports detected
[    0.620166] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.620190] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.620230] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.620251] ohci_hcd 0000:00:13.4: irq 18, io mem 0xc0009000
[    0.707926] usb usb6: configuration #1 chosen from 1 choice
[    0.707958] hub 6-0:1.0: USB hub found
[    0.707973] hub 6-0:1.0: 2 ports detected
[    0.708081] uhci_hcd: USB Universal Host Controller Interface driver
[    0.708183] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.711374] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.711380] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.716202] mice: PS/2 mouse device common for all mice
[    0.716390] rtc_cmos 00:04: RTC can wake from S4
[    0.716438] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.716470] rtc0: alarms up to one month, 114 bytes nvram
[    0.716606] device-mapper: uevent: version 1.0.3
[    0.716732] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.716962] Freeing initrd memory: 8085k freed
[    0.724483] device-mapper: multipath: version 1.1.0 loaded
[    0.724487] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.724720] EISA: Probing bus 0 at eisa.0
[    0.724729] Cannot allocate resource for EISA slot 1
[    0.724732] Cannot allocate resource for EISA slot 2
[    0.724735] Cannot allocate resource for EISA slot 3
[    0.724755] Cannot allocate resource for EISA slot 8
[    0.724758] EISA: Detected 0 cards.
[    0.724852] cpuidle: using governor ladder
[    0.724914] cpuidle: using governor menu
[    0.725399] TCP cubic registered
[    0.725564] NET: Registered protocol family 10
[    0.726052] lo: Disabled Privacy Extensions
[    0.726390] NET: Registered protocol family 17
[    0.726426] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[    0.726480] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x10
[    0.726483] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x12
[    0.726486] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x18
[    0.726531] Using IPI No-Shortcut mode
[    0.726629] PM: Resume from disk failed.
[    0.726645] registered taskstats version 1
[    0.726990]   Magic number: 14:412:852
[    0.727097] rtc_cmos 00:04: setting system clock to 2010-06-20 20:49:53 UTC (1277066993)
[    0.727101] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.727103] EDD information not available.
[    0.814299] isapnp: No Plug & Play device found
[    0.827956] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.864188] ACPI: Battery Slot [BAT1] (battery present)
[    1.228318] Freeing unused kernel memory: 656k freed
[    1.228830] Write protecting the kernel text: 4676k
[    1.228864] Write protecting the kernel read-only data: 1840k
[    1.249996] udev: starting version 151
[    1.495312] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.495325] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[    1.497204] usb 1-7: new high speed USB device using ehci_hcd and address 3
[    1.498739] scsi0 : pata_atiixp
[    1.498921] scsi1 : pata_atiixp
[    1.499685] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    1.499689] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    1.499874] ahci 0000:00:12.0: version 3.0
[    1.499891]   alloc irq_desc for 22 on node -1
[    1.499894]   alloc kstat_irqs on node -1
[    1.499902] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.499937] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.500076] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.500081] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pmp pio ccc 
[    1.500771] scsi2 : ahci
[    1.500984] scsi3 : ahci
[    1.501092] scsi4 : ahci
[    1.501195] scsi5 : ahci
[    1.501320] ata3: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004100 irq 22
[    1.501325] ata4: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004180 irq 22
[    1.501331] ata5: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004200 irq 22
[    1.501336] ata6: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004280 irq 22
[    1.552181] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[    1.602328]   alloc irq_desc for 21 on node -1
[    1.602332]   alloc kstat_irqs on node -1
[    1.602340] b44 0000:08:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.634456] usb 1-7: configuration #1 chosen from 4 choices
[    1.660159] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[    1.660315] b44.c:v2.0
[    1.664547] ata1.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4244N, B103, max UDMA/33
[    1.680506] ata1.00: configured for UDMA/33
[    1.681415] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:ca:bb:fc
[    1.685677] scsi 0:0:0:0: CD-ROM            HL-DT-ST CDRW/DVD GCC4244 B103 PQ: 0 ANSI: 5
[    1.696827] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.696830] Uniform CD-ROM driver Revision: 3.20
[    1.697074] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.697199] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.824068] ata4: SATA link down (SStatus 0 SControl 300)
[    1.824106] ata5: SATA link down (SStatus 0 SControl 300)
[    1.824139] ata6: SATA link down (SStatus 0 SControl 300)
[    1.900043] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    2.069507] usb 4-1: configuration #1 chosen from 1 choice
[    2.100063] ata3: softreset failed (device not ready)
[    2.100068] ata3: applying SB600 PMP SRST workaround and retrying
[    2.264068] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.708237] ata3.00: ATA-7: TOSHIBA MK6034GSX, AH101D, max UDMA/100
[    2.708241] ata3.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.708264] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.709597] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.709600] ata3.00: configured for UDMA/100
[    2.709718] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK6034GS AH10 PQ: 0 ANSI: 5
[    2.709893] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.710136] sd 2:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.710183] sd 2:0:0:0: [sda] Write Protect is off
[    2.710186] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.710211] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.710355]  sda: sda1 sda2 sda3
[    2.750677] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.766632] usbcore: registered new interface driver hiddev
[    2.772528] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.2/usb4/4-1/4-1:1.0/input/input6
[    2.772642] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.2-1/input0
[    2.772672] usbcore: registered new interface driver usbhid
[    2.772676] usbhid: v2.6:USB HID core driver
[    4.008903] EXT4-fs (loop0): mounted filesystem with ordered data mode
[   21.443842] udev: starting version 151
[   21.526167] lp: driver loaded but no devices found
[   21.666054] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   21.678589] acpi device:1c: registered as cooling_device1
[   21.679552] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1a/LNXVIDEO:00/input/input7
[   21.679694] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.111883] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   22.112688] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   22.166745] ricoh-mmc: Ricoh MMC Controller disabling driver
[   22.166749] ricoh-mmc: Copyright(c) Philip Langdale
[   22.166778] ricoh-mmc: Ricoh MMC controller found at 0000:08:01.1 [1180:0843] (rev 1)
[   22.166786] ricoh-mmc: Main Ricoh function not found. Cannot disable controller.
[   22.172765] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.172952] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   22.174948] sdhci: Secure Digital Host Controller Interface driver
[   22.174953] sdhci: Copyright(c) Pierre Ossman
[   22.182896] Linux agpgart interface v0.103
[   22.221433] sdhci-pci 0000:08:01.0: SDHCI controller found [1180:0822] (rev 19)
[   22.221456]   alloc irq_desc for 20 on node -1
[   22.221458]   alloc kstat_irqs on node -1
[   22.221466] sdhci-pci 0000:08:01.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[   22.260807] Registered led device: mmc0::
[   22.261974] mmc0: SDHCI controller on PCI [0000:08:01.0] using PIO
[   22.369873] cfg80211: Calling CRDA to update world regulatory domain
[   22.380784] cfg80211: World regulatory domain updated:
[   22.380788]    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.380793]    (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.380796]    (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.380799]    (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.380802]    (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.380806]    (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.429499] type=1505 audit(1277092215.200:2):  operation="profile_load" pid=614 name="/sbin/dhclient3"
[   22.429820] type=1505 audit(1277092215.200:3):  operation="profile_load" pid=614 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   22.430000] type=1505 audit(1277092215.200:4):  operation="profile_load" pid=614 name="/usr/lib/connman/scripts/dhclient-script"
[   22.455900] [drm] Initialized drm 1.1.0 20060810
[   22.476240] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   22.586984] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   22.668826] [drm] radeon defaulting to kernel modesetting.
[   22.668830] [drm] radeon kernel modesetting enabled.
[   22.668920] radeon 0000:01:05.0: power state changed by ACPI to D0
[   22.668930] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.674674] [drm] radeon: Initializing kernel modesetting.
[   22.683989] [drm] register mmio base: 0xC0100000
[   22.683993] [drm] register mmio size: 65536
[   22.684348] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   22.684364] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   22.684411] [drm] Generation 2 PCI interface, using max accessible memory
[   22.684415] [drm] radeon: VRAM 128M
[   22.684417] [drm] radeon: VRAM from 0x78000000 to 0x7FFFFFFF
[   22.684420] [drm] radeon: GTT 32M
[   22.684422] [drm] radeon: GTT from 0x80000000 to 0x81FFFFFF
[   22.684447] [drm] radeon: irq initialized.
[   22.684572] [drm] Detected VRAM RAM=128M, BAR=128M
[   22.684577] [drm] RAM width 128bits DDR
[   22.686846] [TTM] Zone  kernel: Available graphics memory: 437814 kiB.
[   22.686849] [TTM] Zone highmem: Available graphics memory: 965402 kiB.
[   22.686868] [drm] radeon: 128M of VRAM memory ready
[   22.686870] [drm] radeon: 32M of GTT memory ready.
[   22.686895] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   22.687334] [drm] radeon: 4 quad pipes, 1 z pipes initialized.
[   22.687348] [drm] radeon: cp idle (0x10000C03)
[   22.687469] [drm] Loading R300 Microcode
[   22.687945] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   22.695345] [drm] radeon: ring at 0x0000000080000000
[   22.695366] [drm] ring test succeeded in 1 usecs
[   22.695498] [drm] radeon: ib pool ready.
[   22.695568] [drm] ib test succeeded in 0 usecs
[   22.695685] [drm] Panel ID String: LPL                     
[   22.695688] [drm] Panel Size 1280x800
[   22.695746] [drm] Radeon Display Connectors
[   22.695749] [drm] Connector 0:
[   22.695750] [drm]   VGA
[   22.695753] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   22.695755] [drm]   Encoders:
[   22.695757] [drm]     CRT1: INTERNAL_DAC2
[   22.695759] [drm] Connector 1:
[   22.695760] [drm]   LVDS
[   22.695763] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   22.695765] [drm]   Encoders:
[   22.695767] [drm]     LCD1: INTERNAL_LVDS
[   22.787827] phy0: Selected rate control algorithm 'minstrel'
[   22.788614] Registered led device: b43-phy0::tx
[   22.788633] Registered led device: b43-phy0::rx
[   22.788654] Registered led device: b43-phy0::radio
[   22.788734] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   22.915755] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   23.003921] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.014140] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   23.042304] composite sync not supported
[   23.051167] [drm] fb mappable at 0xC8040000
[   23.051169] [drm] vram apper at 0xC8000000
[   23.051172] [drm] size 4096000
[   23.051173] [drm] fb depth is 24
[   23.051175] [drm]    pitch is 5120
[   23.057623] fb0: radeondrmfb frame buffer device
[   23.057625] registered panic notifier
[   23.057632] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   23.067602] vga16fb: initializing
[   23.067609] vga16fb: mapped to 0xc00a0000
[   23.067615] vga16fb: not registering due to another framebuffer present
[   23.202624] Console: switching to colour frame buffer device 160x50
[   23.214355] input: HDA ATI SB Mic at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   23.214460] input: HDA ATI SB HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   23.319881] composite sync not supported
[   24.685848] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:133 across:51111916k 
[   25.010172] type=1505 audit(1277092217.780:5):  operation="profile_load" pid=814 name="/usr/share/gdm/guest-session/Xsession"
[   25.018442] type=1505 audit(1277092217.788:6):  operation="profile_replace" pid=815 name="/sbin/dhclient3"
[   25.018780] type=1505 audit(1277092217.788:7):  operation="profile_replace" pid=815 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.018970] type=1505 audit(1277092217.788:8):  operation="profile_replace" pid=815 name="/usr/lib/connman/scripts/dhclient-script"
[   25.047057] type=1505 audit(1277092217.816:9):  operation="profile_load" pid=816 name="/usr/bin/evince"
[   25.059659] type=1505 audit(1277092217.828:10):  operation="profile_load" pid=816 name="/usr/bin/evince-previewer"
[   25.079274] type=1505 audit(1277092217.848:11):  operation="profile_load" pid=816 name="/usr/bin/evince-thumbnailer"
[   25.104184] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   25.114082] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   25.121792] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   25.121798] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   25.121801] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   25.127012] b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear.
[   25.144885] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.212097] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   25.217326] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   25.228749] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   25.228755] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   25.228759] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   25.483377] composite sync not supported
[   25.501422] ppdev: user-space parallel port driver
[   25.529401] composite sync not supported
[   26.338319] composite sync not supported
[   26.364292] composite sync not supported
[   26.389940] composite sync not supported
[   36.780712] composite sync not supported
[   36.807355] composite sync not supported
[   36.832408] composite sync not supported
[   39.032137] composite sync not supported
[   39.364050] composite sync not supported
[   42.520077] composite sync not supported
[  363.762678] composite sync not supported
[ 1803.028080] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 1803.165193] usb 1-3: configuration #1 chosen from 1 choice
[ 1803.248099] Initializing USB Mass Storage driver...
[ 1803.248418] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1803.248802] usbcore: registered new interface driver usb-storage
[ 1803.248810] USB Mass Storage support registered.
[ 1803.260322] usb-storage: device found at 4
[ 1803.260330] usb-storage: waiting for device to settle before scanning
[ 1808.260421] usb-storage: device scan complete
[ 1808.260997] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 1808.266521] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1808.269223] sd 6:0:0:0: [sdb] 7818184 512-byte logical blocks: (4.00 GB/3.72 GiB)
[ 1808.269714] sd 6:0:0:0: [sdb] Write Protect is off
[ 1808.269723] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1808.269730] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1808.282510] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1808.282527]  sdb:
[ 1808.288847] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1808.288862] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 1842.537368] usb 1-3: USB disconnect, address 4
[ 2146.830644] composite sync not supported
[ 2305.740069] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 2305.876166] usb 1-3: configuration #1 chosen from 1 choice
[ 2305.879748] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2305.892389] usb-storage: device found at 5
[ 2305.892398] usb-storage: waiting for device to settle before scanning
[ 2310.892384] usb-storage: device scan complete
[ 2310.892981] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2310.898471] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 2310.901186] sd 7:0:0:0: [sdb] 7818184 512-byte logical blocks: (4.00 GB/3.72 GiB)
[ 2310.901670] sd 7:0:0:0: [sdb] Write Protect is off
[ 2310.901678] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2310.901685] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 2310.914588] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 2310.914605]  sdb:
[ 2310.919927] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 2310.919941] sd 7:0:0:0: [sdb] Attached SCSI removable disk
linux@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:ca:bb:fc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:0c:e1:09
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
linux@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

linux@ubuntu:~$ lsb_release -d
Description:      Ubuntu 10.04 LTS
linux@ubuntu:~$ uname -mr
2.6.32-21-generic i686
linux@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...       [ OK ] 
linux@ubuntu:~$ [/FONT]
  
```Thanks in advance.

---

### Post by malatesta on 2010-07-06
I had the same problem with my wired connection, that is:


"[   25.127012] b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear."

Rarely my wireless connection works!

I hope some ubuntu veteran will help us!


x@x:~$ dmesg | grep -e eth0 -e bcm
[    1.266114] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 10:17:xx:19:xx:xx
[   13.429441] b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear.
[   13.437775] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.805192] b44: eth0: Link is up at 100 Mbps, full duplex.
[   16.805196] b44: eth0: Flow control is off for TX and off for RX.
[   16.805530] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.912067] eth0: no IPv6 routers present
[ 2249.989185] b44: eth0: Link is down.
[ 2250.748264] b44: eth0: powering down PHY
[ 2262.028162] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2265.004226] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 2265.004234] b44: eth0: Flow control is off for TX and off for RX.
[ 2265.004686] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2275.860049] eth0: no IPv6 routers present

---

### Post by LeeDaugherty on 2010-07-07
These Broadcom's can be a pain, especially without internet access.  Check this link out for help: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

