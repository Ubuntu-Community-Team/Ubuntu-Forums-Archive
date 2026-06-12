---
title: "Webcam in Ubuntu"
date: 2011-12-24
forum: Multimedia Software
---

### Post by 4042966262 on 2011-12-24
can you help get my Microsoft cam to run in Ubuntu (latest version)
coffeegulpers@coffeegulpers:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:a13c Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
coffeegulpers@coffeegulpers:~$ 

(i learned lsusb from looking at forums. you have t explain terminal codes to me)

---

### Post by gareththered on 2011-12-24
The device in your list comes up as a HP KQ246AA webcam.  Regardless, it should work when plugged in.  Have you looked in the logs to see if it appears?

Run 'dmesg', before plugging in the camera, then run it asap after plugging it in and see what turns up.  The 'uvc' driver is responsible for the HP camera, so another ploy would be to run 'dmesg | grep uvc' to filter for log entries with only the term 'uvc' in it.

Good luck!

---

### Post by 4042966262 on 2012-01-01
works! how do i keep it working?

---

### Post by gareththered on 2012-01-01
Well, considering you've done nothing to get it to work, then I suppose that you don't need to do anything to keep it working ;-)

What exactly did you do to get it to work?

---

### Post by 4042966262 on 2012-01-25
opened a terminal and typed in ''lbusb''
it then spit out...
```

[    0.321631] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.321634] pci_bus 0000:06: resource 1 [mem 0xdc000000-0xdc0fffff]
[    0.321638] pci_bus 0000:06: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.321642] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.321645] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.321649] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.321652] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.321656] pci_bus 0000:06: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.321659] pci_bus 0000:06: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.321663] pci_bus 0000:06: resource 10 [mem 0x40000000-0xfebfffff]
[    0.321667] pci_bus 0000:07: resource 0 [io  0x5000-0x50ff]
[    0.321670] pci_bus 0000:07: resource 1 [io  0x5400-0x54ff]
[    0.321674] pci_bus 0000:07: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.321677] pci_bus 0000:07: resource 3 [mem 0x44000000-0x47ffffff]
[    0.321739] NET: Registered protocol family 2
[    0.321840] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.322188] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.323002] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.323433] TCP: Hash tables configured (established 131072 bind 65536)
[    0.323438] TCP reno registered
[    0.323445] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.323465] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.323626] NET: Registered protocol family 1
[    0.323654] pci 0000:00:02.0: Boot video device
[    0.323815] PCI: CLS 64 bytes, default 64
[    0.323824] Simple Boot Flag at 0x36 set to 0x1
[    0.324327] audit: initializing netlink socket (disabled)
[    0.324343] type=2000 audit(1327502921.320:1): initialized
[    0.354144] highmem bounce pool size: 64 pages
[    0.354153] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.362394] VFS: Disk quotas dquot_6.5.2
[    0.362502] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.363476] fuse init (API version 7.16)
[    0.363620] msgmni has been set to 1704
[    0.364160] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.364204] io scheduler noop registered
[    0.364206] io scheduler deadline registered
[    0.364228] io scheduler cfq registered (default)
[    0.364398] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.364470] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.364571] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.364632] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.364721] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.364783] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.364909] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.364943] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.365017] intel_idle: MWAIT substates: 0x1110
[    0.365020] intel_idle: does not run on family 6 model 14
[    0.365111] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.365188] ACPI: AC Adapter [ACAD] (on-line)
[    0.365282] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.365308] ACPI: Lid Switch [LID0]
[    0.365368] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.365374] ACPI: Power Button [PWRB]
[    0.365450] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.365455] ACPI: Power Button [PWRF]
[    0.365495] ACPI: acpi_idle registered with cpuidle
[    0.368123] Marking TSC unstable due to TSC halts in idle
[    0.392372] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.392461] ERST: Table is not found!
[    0.392592] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.392860] isapnp: Scanning for PnP cards...
[    0.569189] Freeing initrd memory: 13328k freed
[    0.582293] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.720092] ACPI: Battery Slot [BAT1] (battery present)
[    0.747847] isapnp: No Plug & Play device found
[    0.750415] Linux agpgart interface v0.103
[    0.750529] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    0.750581] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.750953] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.751117] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.752870] brd: module loaded
[    0.753691] loop: module loaded
[    0.753902] ata_piix 0000:00:1f.2: version 2.13
[    0.753935] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.753943] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.908034] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.908463] scsi0 : ata_piix
[    0.908603] scsi1 : ata_piix
[    0.909393] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    0.909397] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    0.909902] Fixed MDIO Bus: probed
[    0.909935] PPP generic driver version 2.4.2
[    0.910007] tun: Universal TUN/TAP device driver, 1.6
[    0.910010] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.910129] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.910164] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.910184] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.910189] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.910240] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.910269] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.910284] ehci_hcd 0000:00:1d.7: debug port 1
[    0.914179] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.914203] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdc444000
[    0.928022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.928192] hub 1-0:1.0: USB hub found
[    0.928198] hub 1-0:1.0: 8 ports detected
[    0.928311] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.928330] uhci_hcd: USB Universal Host Controller Interface driver
[    0.928371] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.928380] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.928384] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.928434] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.928467] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.928631] hub 2-0:1.0: USB hub found
[    0.928636] hub 2-0:1.0: 2 ports detected
[    0.928722] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.928731] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.928735] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.928797] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.928840] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.929001] hub 3-0:1.0: USB hub found
[    0.929006] hub 3-0:1.0: 2 ports detected
[    0.929093] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.929101] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.929106] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.929151] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.929197] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.929367] hub 4-0:1.0: USB hub found
[    0.929373] hub 4-0:1.0: 2 ports detected
[    0.929457] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.929466] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.929470] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.929517] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.929559] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    0.929717] hub 5-0:1.0: USB hub found
[    0.929723] hub 5-0:1.0: 2 ports detected
[    0.929876] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.930214] i8042: Detected active multiplexing controller, rev 1.1
[    0.930303] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.930315] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.930356] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.930389] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.930426] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.930571] mousedev: PS/2 mouse device common for all mice
[    0.930772] rtc_cmos 00:07: RTC can wake from S4
[    0.930910] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.930946] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.931077] device-mapper: uevent: version 1.0.3
[    0.931196] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    0.931251] EISA: Probing bus 0 at eisa.0
[    0.931255] EISA: Cannot allocate resource for mainboard
[    0.931258] Cannot allocate resource for EISA slot 1
[    0.931261] Cannot allocate resource for EISA slot 2
[    0.931263] Cannot allocate resource for EISA slot 3
[    0.931266] Cannot allocate resource for EISA slot 4
[    0.931269] Cannot allocate resource for EISA slot 5
[    0.931271] Cannot allocate resource for EISA slot 6
[    0.931274] Cannot allocate resource for EISA slot 7
[    0.931277] Cannot allocate resource for EISA slot 8
[    0.931279] EISA: Detected 0 cards.
[    0.931293] cpufreq-nforce2: No nForce2 chipset.
[    0.931391] cpuidle: using governor ladder
[    0.931526] cpuidle: using governor menu
[    0.931529] EFI Variables Facility v0.08 2004-May-17
[    0.931945] TCP cubic registered
[    0.932157] NET: Registered protocol family 10
[    0.932992] NET: Registered protocol family 17
[    0.933032] Registering the dns_resolver key type
[    0.933059] Using IPI No-Shortcut mode
[    0.933170] PM: Hibernation image not present or could not be loaded.
[    0.933187] registered taskstats version 1
[    0.935703] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.945396]   Magic number: 12:120:840
[    0.945535] rtc_cmos 00:07: setting system clock to 2012-01-25 14:48:42 UTC (1327502922)
[    0.946091] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.946093] EDD information not available.
[    1.072572] ata1.00: ATA-8: Hitachi HTS542512K9SA00, BB2OC33P, max UDMA/133
[    1.072577] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.072708] ata2.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.90, max UDMA/33
[    1.088528] ata2.00: configured for UDMA/33
[    1.088728] ata1.00: configured for UDMA/133
[    1.088978] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BB2O PQ: 0 ANSI: 5
[    1.089164] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.089202] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.089240] sd 0:0:0:0: [sda] Write Protect is off
[    1.089244] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.089279] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.091230] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.90 PQ: 0 ANSI: 5
[    1.092697] sr0: scsi3-mmc drive: 47x/47x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.092701] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.092828] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.092902] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.128453]  sda: sda1 sda2 < sda5 >
[    1.129033] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.129132] Freeing unused kernel memory: 696k freed
[    1.129490] Write protecting the kernel text: 5340k
[    1.129573] Write protecting the kernel read-only data: 2192k
[    1.152797] udevd[84]: starting version 173
[    1.233708] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.233743] r8169 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.233804] r8169 0000:05:00.0: setting latency timer to 64
[    1.233908] r8169 0000:05:00.0: irq 43 for MSI/MSI-X
[    1.234622] r8169 0000:05:00.0: eth0: RTL8101e at 0xf8004000, 00:16:d4:fe:d6:45, XID 14000000 IRQ 43
[    1.249682] sdhci: Secure Digital Host Controller Interface driver
[    1.249687] sdhci: Copyright(c) Pierre Ossman
[    1.250023] sdhci-pci 0000:06:04.3: SDHCI controller found [104c:803c] (rev 0)
[    1.250048] sdhci-pci 0000:06:04.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.254931] mmc0: no vmmc regulator found
[    1.254991] Registered led device: mmc0::
[    1.255051] mmc0: SDHCI controller on PCI [0000:06:04.3] using DMA
[    1.269683] firewire_ohci 0000:06:04.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.324193] firewire_ohci: Added fw-ohci device 0000:06:04.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.643067] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.824185] firewire_core: created device fw0: GUID 00023f75a840f3b8, S400
[   14.905270] udevd[298]: starting version 173
[   14.951609] lp: driver loaded but no devices found
[   15.022634] Adding 3068924k swap on /dev/sda5.  Priority:-1 extents:1 across:3068924k 
[   15.132433] acpi device:08: registered as cooling_device2
[   15.132548] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input4
[   15.132639] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.219553] intel_rng: FWH not detected
[   15.230260] leds_ss4200: no LED devices found
[   15.233212] type=1400 audit(1327502936.783:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=477 comm="apparmor_parser"
[   15.233803] type=1400 audit(1327502936.783:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=477 comm="apparmor_parser"
[   15.234178] type=1400 audit(1327502936.783:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=477 comm="apparmor_parser"
[   15.234695] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.252248] cfg80211: Calling CRDA to update world regulatory domain
[   15.312226] yenta_cardbus 0000:06:04.0: CardBus bridge found [1179:ff00]
[   15.312250] yenta_cardbus 0000:06:04.0: Enabling burst memory read transactions
[   15.312257] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
[   15.312261] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
[   15.312268] yenta_cardbus 0000:06:04.0: TI: mfunc 0x10aa1b22, devctl 0x64
[   15.312867] [drm] Initialized drm 1.1.0 20060810
[   15.325006] ath5k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.325024] ath5k 0000:04:00.0: setting latency timer to 64
[   15.325081] ath5k 0000:04:00.0: registered as 'phy0'
[   15.544831] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   15.544838] yenta_cardbus 0000:06:04.0: Socket status: 30000006
[   15.544843] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   15.544855] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   15.544860] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: excluding 0x5000-0x50ff 0x5400-0x54ff
[   15.573238] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [mem 0xdc000000-0xdc0fffff]
[   15.573244] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdc000000-0xdc0fffff: excluding 0xdc000000-0xdc00ffff
[   15.573262] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[   15.573266] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff: excluding 0x40000000-0x43ffffff
[   15.668397] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.668468] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   15.668506] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.701675] cfg80211: World regulatory domain updated:
[   15.701681] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.701685] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.701689] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.701693] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.701697] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.701700] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.768496] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.768505] i915 0000:00:02.0: setting latency timer to 64
[   15.792509] tifm_7xx1 0000:06:04.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   15.797580] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.797585] [drm] Driver supports precise vblank timestamp query.
[   15.808406] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   15.810779] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   15.811768] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.814687] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.815586] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xdc000-0xfffff
[   15.815660] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   15.815732] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   15.815807] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   15.835781] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.841971]  clean.
[   15.843473] ath: EEPROM regdomain: 0x64
[   15.843477] ath: EEPROM indicates we should expect a direct regpair map
[   15.843482] ath: Country alpha2 being used: 00
[   15.843485] ath: Regpair used: 0x64
[   15.843675] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.843679] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843683] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.843687] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843690] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.843694] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843697] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.843701] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843705] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.843708] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843712] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.843716] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843719] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.843723] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843726] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.843730] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843733] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.843737] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843741] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.843745] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843748] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.843752] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.843755] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.843759] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.843762] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.843879] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   15.847973] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.849192] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa0, PHY: 0x61)
[   15.919099] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0/0x0
[   15.919112] synaptics: Toshiba Satellite A135 detected, limiting rate to 40pps.
[   15.948119] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   15.979297] init: failsafe main process (699) killed by TERM signal
[   16.076840] type=1400 audit(1327502937.627:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=760 comm="apparmor_parser"
[   16.083988] type=1400 audit(1327502937.631:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=763 comm="apparmor_parser"
[   16.085701] type=1400 audit(1327502937.635:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=763 comm="apparmor_parser"
[   16.087598] type=1400 audit(1327502937.635:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=763 comm="apparmor_parser"
[   16.100743] type=1400 audit(1327502937.651:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=769 comm="apparmor_parser"
[   16.109523] type=1400 audit(1327502937.659:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=769 comm="apparmor_parser"
[   16.117476] type=1400 audit(1327502937.667:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=759 comm="apparmor_parser"
[   16.159826] [drm] initialized overlay support
[   16.313502] fbcon: inteldrmfb (fb0) is primary device
[   16.314869] Console: switching to colour frame buffer device 160x50
[   16.314921] fb0: inteldrmfb frame buffer device
[   16.314924] drm: registered panic notifier
[   16.314981] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.377147] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.386254] r8169 0000:05:00.0: eth0: link down
[   16.388305] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.474668] init: apport pre-start process (852) terminated with status 1
[   16.495389] init: apport post-stop process (894) terminated with status 1
[   16.509133] init: gdm main process (891) killed by TERM signal
[   16.928058] vboxdrv: Found 2 processor cores.
[   16.928234] vboxdrv: fAsync=0 offMin=0x3dc offMax=0x1bba
[   16.928314] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   16.928317] vboxdrv: Successfully loaded version 4.1.2_Ubuntu (interface 0x00190000).
[   16.951100] vboxpci: IOMMU not found (not registered)
[   17.039982] Bluetooth: Core ver 2.16
[   17.040340] NET: Registered protocol family 31
[   17.040344] Bluetooth: HCI device and connection manager initialized
[   17.040348] Bluetooth: HCI socket layer initialized
[   17.040351] Bluetooth: L2CAP socket layer initialized
[   17.043053] Bluetooth: SCO socket layer initialized
[   17.047895] Bluetooth: RFCOMM TTY layer initialized
[   17.047904] Bluetooth: RFCOMM socket layer initialized
[   17.047907] Bluetooth: RFCOMM ver 1.11
[   17.072245] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.072250] Bluetooth: BNEP filters: protocol multicast
[   17.085921] ppdev: user-space parallel port driver
[   18.044489] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   18.226361] init: plymouth-stop pre-start process (1146) terminated with status 1
[   21.326485] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   44.831392] wlan0: authenticate with 00:22:a4:07:a0:99 (try 1)
[   44.832812] wlan0: authenticated
[   44.847700] wlan0: associate with 00:22:a4:07:a0:99 (try 1)
[   44.849787] wlan0: RX AssocResp from 00:22:a4:07:a0:99 (capab=0x421 status=0 aid=2)
[   44.849793] wlan0: associated
[   44.850609] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   44.850881] cfg80211: Calling CRDA for country: US
[   44.857145] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   44.857152] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857155] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   44.857159] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857163] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   44.857167] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857170] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   44.857174] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857177] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   44.857181] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857185] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   44.857189] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857192] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   44.857196] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857199] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   44.857203] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857207] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   44.857211] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857214] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   44.857218] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857221] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   44.857225] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   44.857228] cfg80211: Disabling freq 2467 MHz
[   44.857231] cfg80211: Disabling freq 2472 MHz
[   44.857233] cfg80211: Disabling freq 2484 MHz
[   44.857239] cfg80211: Regulatory domain changed to country: US
[   44.857242] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   44.857246] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   44.857250] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   44.857253] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.857257] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.857261] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.857265] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   54.777016] UDF-fs: Partition marked readonly; forcing readonly mount
[   54.829155] UDF-fs INFO UDF: Mounting volume 'CARS_2', timestamp 2011/08/15 03:31 (1ed4)
[   55.232050] wlan0: no IPv6 routers present
[ 5720.400192] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[ 6009.800057] usb 1-5: new high speed USB device number 2 using ehci_hcd
[ 6015.977519] Linux video capture interface: v2.00
[ 6016.018938] uvcvideo: Found UVC 1.00 device HP Deluxe Webcam KQ246AA (04f2:a13c)
[ 6016.026258] input: HP Deluxe Webcam KQ246AA as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input6
[ 6016.026359] usbcore: registered new interface driver uvcvideo
[ 6016.026362] USB Video Class driver (v1.1.0)
[ 6016.294904] 2:3:1: cannot get freq at ep 0x84
[ 6016.296470] usbcore: registered new interface driver snd-usb-audio
[ 6016.636817] input: HP Deluxe Webcam KQ246AA HP Deluxe Webcam KQ246AA as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.4/input/input7
[ 6016.637718] generic-usb 0003:04F2:A13C.0001: input,hidraw0: USB HID v1.11 Joystick [HP Deluxe Webcam KQ246AA HP Deluxe Webcam KQ246AA] on usb-0000:00:1d.7-5/input4
[ 6016.637754] usbcore: registered new interface driver usbhid
[ 6016.637757] usbhid: USB HID core driver
[ 6030.882789] 2:3:1: cannot get freq at ep 0x84
[ 6031.753437] 2:3:1: cannot get freq at ep 0x84
coffeegulpers@coffeegulpers:~$

```

---

