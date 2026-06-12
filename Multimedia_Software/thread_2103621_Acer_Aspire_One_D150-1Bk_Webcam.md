---
title: "Acer Aspire One D150-1Bk Webcam"
date: 2013-01-10
forum: Multimedia Software
---

### Post by blueeyeblue on 2013-01-10
Hi gals and guys,

I've recently realized, that I will need to use integrated webcam in AAO D150-1Bk.

I'm on Ubuntu 10.04


I have tried following: [http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/)

also tried installing v4l2ucp, but when I run it, message with "/dev/video0 not found" pop-up.


Any ideas how can I get webcam to work?



Thanks in advance for any help!

---

### Post by orbesnet on 2013-01-11
I have the same problem, Ubuntu Gods - we need you!

---

### Post by xc3RnbFO8P on 2013-01-11
Odin speaking, try:
> sudo modprobe uvcvideo
> dmesg

---

### Post by orbesnet on 2013-01-11
here' what i got oh mighty Odin:

```
[    0.428987] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.429155] pnp 00:01: [mem 0xfd000000-0xfd003fff]
[    0.429168] pnp 00:01: [mem 0x3f800000-0xafffffff]
[    0.429178] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.429188] pnp 00:01: [mem 0xfed00000-0xfed3ffff]
[    0.429199] pnp 00:01: [mem 0xfed45000-0xfed4bfff]
[    0.429404] system 00:01: [mem 0xfd000000-0xfd003fff] has been reserved
[    0.429419] system 00:01: [mem 0x3f800000-0xafffffff] could not be reserved
[    0.429432] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.429445] system 00:01: [mem 0xfed00000-0xfed3ffff] could not be reserved
[    0.429458] system 00:01: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.429473] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.430222] pnp 00:02: [io  0x0000-0x001f]
[    0.430234] pnp 00:02: [io  0x0081-0x0091]
[    0.430243] pnp 00:02: [io  0x0093-0x009f]
[    0.430253] pnp 00:02: [io  0x00c0-0x00df]
[    0.430263] pnp 00:02: [dma 4]
[    0.430429] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.430575] pnp 00:03: [irq 0 disabled]
[    0.430604] pnp 00:03: [irq 8]
[    0.430615] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.430772] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.430825] pnp 00:04: [io  0x00f0]
[    0.430843] pnp 00:04: [irq 13]
[    0.431003] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.431071] pnp 00:05: [io  0x002e-0x002f]
[    0.431081] pnp 00:05: [io  0x0050-0x0052]
[    0.431091] pnp 00:05: [io  0x0061]
[    0.431099] pnp 00:05: [io  0x0063]
[    0.431108] pnp 00:05: [io  0x0065]
[    0.431117] pnp 00:05: [io  0x0067]
[    0.431125] pnp 00:05: [io  0x0068]
[    0.431134] pnp 00:05: [io  0x006a]
[    0.431143] pnp 00:05: [io  0x006c]
[    0.431151] pnp 00:05: [io  0x006e]
[    0.431160] pnp 00:05: [io  0x0070]
[    0.431169] pnp 00:05: [io  0x0074-0x0077]
[    0.431178] pnp 00:05: [io  0x0080]
[    0.431187] pnp 00:05: [io  0x0092]
[    0.431196] pnp 00:05: [io  0x00b2-0x00b3]
[    0.431205] pnp 00:05: [io  0x0110-0x012e]
[    0.431215] pnp 00:05: [io  0x0374-0x0375]
[    0.431224] pnp 00:05: [io  0x03f4-0x03f5]
[    0.431234] pnp 00:05: [io  0x0680-0x069f]
[    0.431243] pnp 00:05: [io  0x8080]
[    0.431252] pnp 00:05: [io  0x1000-0x107f]
[    0.431261] pnp 00:05: [io  0x1180-0x11bf]
[    0.431271] pnp 00:05: [io  0x1640-0x164f]
[    0.431280] pnp 00:05: [io  0xfe00]
[    0.431562] system 00:05: [io  0x0110-0x012e] has been reserved
[    0.431576] system 00:05: [io  0x0374-0x0375] has been reserved
[    0.431588] system 00:05: [io  0x03f4-0x03f5] has been reserved
[    0.431601] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.431613] system 00:05: [io  0x8080] has been reserved
[    0.431625] system 00:05: [io  0x1000-0x107f] has been reserved
[    0.431637] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.431649] system 00:05: [io  0x1640-0x164f] has been reserved
[    0.431661] system 00:05: [io  0xfe00] has been reserved
[    0.431675] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.431790] pnp 00:06: [io  0x0070-0x0073]
[    0.431950] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.432069] pnp 00:07: [io  0x0060]
[    0.432080] pnp 00:07: [io  0x0064]
[    0.432106] pnp 00:07: [irq 1]
[    0.432285] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.432343] pnp 00:08: [irq 12]
[    0.432522] pnp 00:08: Plug and Play ACPI device, IDs SYN1b20 SYN1b00 SYN0002 PNP0f13 (active)
[    0.432582] pnp: PnP ACPI: found 9 devices
[    0.432590] ACPI: ACPI bus type pnp unregistered
[    0.432602] PnPBIOS: Disabled by ACPI PNP
[    0.476237] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x803fffff]
[    0.476259] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff pref]
[    0.476276] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.476291] pci 0000:02:00.0: BAR 6: assigned [mem 0xd0120000-0xd012ffff pref]
[    0.476304] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.476316] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.476332] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x803fffff]
[    0.476346] pci 0000:00:1c.0:   bridge window [mem 0xd0100000-0xd01fffff pref]
[    0.476363] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.476374] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.476389] pci 0000:00:1c.1:   bridge window [mem 0xd0000000-0xd00fffff]
[    0.476403] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff pref]
[    0.476467] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.476483] pci 0000:00:1c.0: setting latency timer to 64
[    0.476501] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.476547] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.476563] pci 0000:00:1c.1: setting latency timer to 64
[    0.476577] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.476587] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.476598] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.476610] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff]
[    0.476621] pci_bus 0000:00: resource 8 [mem 0x000f0000-0x000fffff]
[    0.476632] pci_bus 0000:00: resource 9 [mem 0x7f800000-0xfebfffff]
[    0.476643] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.476654] pci_bus 0000:02: resource 1 [mem 0x80000000-0x803fffff]
[    0.476665] pci_bus 0000:02: resource 2 [mem 0xd0100000-0xd01fffff pref]
[    0.476677] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.476687] pci_bus 0000:03: resource 1 [mem 0xd0000000-0xd00fffff]
[    0.476699] pci_bus 0000:03: resource 2 [mem 0x80400000-0x805fffff pref]
[    0.476854] NET: Registered protocol family 2
[    0.477093] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.478126] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.479560] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.480372] TCP: Hash tables configured (established 131072 bind 65536)
[    0.480388] TCP reno registered
[    0.480410] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.480453] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.480818] NET: Registered protocol family 1
[    0.480879] pci 0000:00:02.0: Boot video device
[    0.481042] PCI: CLS 64 bytes, default 64
[    0.481128] Simple Boot Flag at 0x36 set to 0x1
[    0.481933] cpufreq-nforce2: No nForce2 chipset.
[    0.482550] audit: initializing netlink socket (disabled)
[    0.482584] type=2000 audit(1357904889.476:1): initialized
[    0.512784] highmem bounce pool size: 64 pages
[    0.512805] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.521221] VFS: Disk quotas dquot_6.5.2
[    0.521491] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.524748] fuse init (API version 7.16)
[    0.525213] msgmni has been set to 1678
[    0.526268] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.526431] io scheduler noop registered
[    0.526440] io scheduler deadline registered
[    0.526527] io scheduler cfq registered (default)
[    0.527170] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.527310] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.527554] intel_idle: MWAIT substates: 0x3020220
[    0.527576] intel_idle: v0.4 model 0x1C
[    0.527583] intel_idle: lapic_timer_reliable_states 0x2
[    0.527605] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.528205] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.529032] ACPI: AC Adapter [ACAD] (on-line)
[    0.529453] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.530133] ACPI: Lid Switch [LID]
[    0.530555] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.596083] ACPI: Power Button [PWRB]
[    0.596386] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.596407] ACPI: Sleep Button [SLPB]
[    0.596651] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.596667] ACPI: Power Button [PWRF]
[    0.596685] ACPI Error: Could not enable PowerButton event (20110112/evxfevnt-198)
[    0.596702] ACPI Warning: Could not enable fixed event 0x2 (20110112/evxface-197)
[    0.628228] button: probe of LNXPWRBN:00 failed with error -22
[    0.628720] ACPI: acpi_idle yielding to intel_idle
[    0.634581] thermal LNXTHERM:00: registered as thermal_zone0
[    0.634593] ACPI: Thermal Zone [THRM] (55 C)
[    0.634790] ERST: Table is not found!
[    0.635048] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.636195] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.636218] isapnp: Scanning for PnP cards...
[    0.636225] ACPI: Battery Slot [BAT1] (battery absent)
[    0.980499] Freeing initrd memory: 12568k freed
[    0.991459] isapnp: No Plug & Play device found
[    1.005643] Linux agpgart interface v0.103
[    1.009770] brd: module loaded
[    1.011709] loop: module loaded
[    1.012072] i2c-core: driver [adp5520] using legacy suspend method
[    1.012079] i2c-core: driver [adp5520] using legacy resume method
[    1.012515] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    1.013709] Fixed MDIO Bus: probed
[    1.013845] PPP generic driver version 2.4.2
[    1.013996] tun: Universal TUN/TAP device driver, 1.6
[    1.014002] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.014291] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.014366] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    1.014404] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.014413] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.014535] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.014694] ehci_hcd 0000:00:1d.7: debug port 1
[    1.018594] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.018635] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xb0054000
[    1.032076] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.032556] hub 1-0:1.0: USB hub found
[    1.032570] hub 1-0:1.0: 8 ports detected
[    1.032786] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.032832] uhci_hcd: USB Universal Host Controller Interface driver
[    1.032940] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.032957] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.032965] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.033098] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.033224] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.033613] hub 2-0:1.0: USB hub found
[    1.033627] hub 2-0:1.0: 2 ports detected
[    1.033812] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.033827] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.033836] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.033964] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.034076] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.034459] hub 3-0:1.0: USB hub found
[    1.034473] hub 3-0:1.0: 2 ports detected
[    1.034660] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.034676] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.034684] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.034819] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.036178] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.036659] hub 4-0:1.0: USB hub found
[    1.036674] hub 4-0:1.0: 2 ports detected
[    1.036992] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.045095] i8042: Detected active multiplexing controller, rev 1.1
[    1.048880] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.048901] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.049004] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.049093] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.049186] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.049583] mousedev: PS/2 mouse device common for all mice
[    1.050064] rtc_cmos 00:06: RTC can wake from S4
[    1.052305] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.052360] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.052686] device-mapper: uevent: version 1.0.3
[    1.052954] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.053168] device-mapper: multipath: version 1.2.0 loaded
[    1.053179] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.053434] EISA: Probing bus 0 at eisa.0
[    1.053448] EISA: Cannot allocate resource for mainboard
[    1.053455] Cannot allocate resource for EISA slot 1
[    1.053462] Cannot allocate resource for EISA slot 2
[    1.053469] Cannot allocate resource for EISA slot 3
[    1.053476] Cannot allocate resource for EISA slot 4
[    1.053482] Cannot allocate resource for EISA slot 5
[    1.053489] Cannot allocate resource for EISA slot 6
[    1.053496] Cannot allocate resource for EISA slot 7
[    1.053502] Cannot allocate resource for EISA slot 8
[    1.053508] EISA: Detected 0 cards.
[    1.053930] cpuidle: using governor ladder
[    1.054344] cpuidle: using governor menu
[    1.055137] TCP cubic registered
[    1.055581] NET: Registered protocol family 10
[    1.057188] NET: Registered protocol family 17
[    1.057252] Registering the dns_resolver key type
[    1.058382] Using IPI No-Shortcut mode
[    1.058724] PM: Hibernation image not present or could not be loaded.
[    1.058754] registered taskstats version 1
[    1.059157]   Magic number: 13:746:832
[    1.059311] rtc_cmos 00:06: setting system clock to 2013-01-11 11:48:10 UTC (1357904890)
[    1.059322] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.059327] EDD information not available.
[    1.059660] Freeing unused kernel memory: 700k freed
[    1.060332] Write protecting the kernel text: 5196k
[    1.060438] Write protecting the kernel read-only data: 2152k
[    1.070743] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.121945] <30>udev[64]: starting version 167
[    1.411793] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.411862] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.411939] r8169 0000:02:00.0: setting latency timer to 64
[    1.412085] r8169 0000:02:00.0: irq 40 for MSI/MSI-X
[    1.413998] r8169 0000:02:00.0: eth0: RTL8102e at 0xf8008000, 00:23:8b:ec:0f:b8, XID 04c00000 IRQ 40
[    1.453778] pata_sch 0000:00:1f.1: version 0.2
[    1.453885] pata_sch 0000:00:1f.1: setting latency timer to 64
[    1.455368] scsi0 : pata_sch
[    1.455866] scsi1 : pata_sch
[    1.457210] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.457225] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.621250] ata1.00: ATA-8: ST9160310AS, 0303, max UDMA/133
[    1.621271] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.637215] ata1.00: configured for UDMA/100
[    1.637840] scsi 0:0:0:0: Direct-Access     ATA      ST9160310AS      0303 PQ: 0 ANSI: 5
[    1.638408] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.638571] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.638715] sd 0:0:0:0: [sda] Write Protect is off
[    1.638728] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.638851] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.707120]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    1.709276] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.380449] ACPI Error: [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dswload-802)
[    2.380472] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20110112/psloop-231)
[    2.380484] ACPI Error: Method parse/execution failed [\_SB_.BAT1.UBIF] (Node f4022d80), AE_ALREADY_EXISTS (20110112/psparse-536)
[    2.380506] ACPI Error: Method parse/execution failed [\_SB_.BAT1._BIF] (Node f4022d50), AE_ALREADY_EXISTS (20110112/psparse-536)
[    2.380526] ACPI: Marking method _BIF as Serialized because of AE_ALREADY_EXISTS error
[    2.380543] ACPI Exception: AE_ALREADY_EXISTS, Evaluating _BIF (20110112/battery-419)
[    2.385297] ACPI: Marking method UBIF as Serialized because of AE_ALREADY_EXISTS error
[    2.997894] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    5.928781] Adding 1645564k swap on /dev/sda7.  Priority:-1 extents:1 across:1645564k 
[    6.756079] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    7.329705] <30>udev[285]: starting version 167
[    7.982331] ACPI: resource (null) [io  0x1180-0x11bf] conflicts with ACPI region GPIO [io 0x1180-0x11bf]
[    7.982344] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.982548] lpc_sch: probe of 0000:00:1f.0 failed with error -16
[    8.607507] cfg80211: Calling CRDA to update world regulatory domain
[    9.713145] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[    9.776155] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input5
[    9.796140] lp: driver loaded but no devices found
[   10.062728] cfg80211: World regulatory domain updated:
[   10.062738] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.062749] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.062757] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.062765] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.062774] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.062782] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.159663] acpi device:03: registered as cooling_device2
[   10.215814] acpi device:05: registered as cooling_device3
[   10.219889] ath5k 0000:03:00.0: enabling device (0004 -> 0006)
[   10.219914] ath5k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.219937] ath5k 0000:03:00.0: setting latency timer to 64
[   10.220161] ath5k 0000:03:00.0: registered as 'phy0'
[   10.269699] acpi device:06: registered as cooling_device4
[   10.271873] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   10.274160] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.721108] ath: EEPROM regdomain: 0x65
[   10.721117] ath: EEPROM indicates we should expect a direct regpair map
[   10.721127] ath: Country alpha2 being used: 00
[   10.721132] ath: Regpair used: 0x65
[   10.721142] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.721151] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721158] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.721167] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721174] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.721183] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721190] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.721198] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721205] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.721214] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721221] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.721230] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721237] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.721245] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721252] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.721261] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721268] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.721277] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721284] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.721292] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721299] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.721308] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721315] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.721324] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721331] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.721339] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.721346] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   10.721493] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   11.113716] type=1400 audit(1357922900.551:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=487 comm="apparmor_parser"
[   11.113747] type=1400 audit(1357922900.551:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=488 comm="apparmor_parser"
[   11.115296] type=1400 audit(1357922900.551:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=487 comm="apparmor_parser"
[   11.115328] type=1400 audit(1357922900.551:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=488 comm="apparmor_parser"
[   11.116380] type=1400 audit(1357922900.555:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=487 comm="apparmor_parser"
[   11.116411] type=1400 audit(1357922900.555:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=488 comm="apparmor_parser"
[   11.401216] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   11.403535] Registered led device: ath5k-phy0::rx
[   11.403748] Registered led device: ath5k-phy0::tx
[   11.403790] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   11.512313] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.512433] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.169759] hda_codec: ALC272X: BIOS auto-probing.
[   12.212410] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.213685] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.066776] ppdev: user-space parallel port driver
[   15.071698] vesafb: framebuffer at 0x7f800000, mapped to 0xf8b80000, using 3072k, total 3072k
[   15.071714] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   15.071722] vesafb: scrolling: redraw
[   15.071734] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.072387] Console: switching to colour frame buffer device 128x48
[   15.072503] fb0: VESA VGA frame buffer device
[   15.419361] type=1400 audit(1357922904.855:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=739 comm="apparmor_parser"
[   15.421609] type=1400 audit(1357922904.859:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=739 comm="apparmor_parser"
[   15.422565] type=1400 audit(1357922904.859:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=739 comm="apparmor_parser"
[   15.551223] type=1400 audit(1357922904.987:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=738 comm="apparmor_parser"
[   16.361263] audit_printk_skb: 15 callbacks suppressed
[   16.361274] type=1400 audit(1357922905.799:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=740 comm="apparmor_parser"
[   16.375054] type=1400 audit(1357922905.811:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=740 comm="apparmor_parser"
[   16.383132] type=1400 audit(1357922905.819:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=740 comm="apparmor_parser"
[   17.666486] r8169 0000:02:00.0: eth0: link down
[   17.666504] r8169 0000:02:00.0: eth0: link down
[   17.667139] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.799892] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.383871] r8169 0000:02:00.0: eth0: link up
[   19.385863] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.390755] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   29.712046] eth0: no IPv6 routers present
[   31.679498] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   33.253288] hda-intel: Invalid position buffer, using LPIB read method instead.
[   33.253405] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   47.241640] wlan0: authenticate with 58:6d:8f:41:93:ad (try 1)
[   47.245334] wlan0: authenticated
[   47.245473] wlan0: associate with 58:6d:8f:41:93:ad (try 1)
[   47.247766] wlan0: RX AssocResp from 58:6d:8f:41:93:ad (capab=0x401 status=18 aid=0)
[   47.247783] wlan0: 58:6d:8f:41:93:ad denied association (code=18)
[   47.247868] wlan0: deauthenticating from 58:6d:8f:41:93:ad by local choice (reason=3)
[   58.261056] wlan0: authenticate with 58:6d:8f:41:93:ad (try 1)
[   58.268061] wlan0: authenticated
[   58.268196] wlan0: associate with 58:6d:8f:41:93:ad (try 1)
[   58.271269] wlan0: RX AssocResp from 58:6d:8f:41:93:ad (capab=0x401 status=18 aid=0)
[   58.271285] wlan0: 58:6d:8f:41:93:ad denied association (code=18)
[   58.271367] wlan0: deauthenticating from 58:6d:8f:41:93:ad by local choice (reason=3)
[   69.279651] wlan0: authenticate with 58:6d:8f:41:93:ad (try 1)
[   69.284338] wlan0: authenticated
[   69.284462] wlan0: associate with 58:6d:8f:41:93:ad (try 1)
[   69.287612] wlan0: RX AssocResp from 58:6d:8f:41:93:ad (capab=0x401 status=18 aid=0)
[   69.287628] wlan0: 58:6d:8f:41:93:ad denied association (code=18)
[   69.287708] wlan0: deauthenticating from 58:6d:8f:41:93:ad by local choice (reason=3)
[   80.286384] wlan0: authenticate with 58:6d:8f:41:93:ad (try 1)
[   80.288392] wlan0: authenticated
[   80.288476] wlan0: associate with 58:6d:8f:41:93:ad (try 1)
[   80.291442] wlan0: RX AssocResp from 58:6d:8f:41:93:ad (capab=0x401 status=18 aid=0)
[   80.291459] wlan0: 58:6d:8f:41:93:ad denied association (code=18)
[   80.291540] wlan0: deauthenticating from 58:6d:8f:41:93:ad by local choice (reason=3)
[   91.297295] wlan0: authenticate with 58:6d:8f:41:93:ad (try 1)
[   91.298951] wlan0: authenticated
[   91.299133] wlan0: associate with 58:6d:8f:41:93:ad (try 1)
[   91.301140] wlan0: RX AssocResp from 58:6d:8f:41:93:ad (capab=0x401 status=18 aid=0)
[   91.301167] wlan0: 58:6d:8f:41:93:ad denied association (code=18)
[   91.301284] wlan0: deauthenticating from 58:6d:8f:41:93:ad by local choice (reason=3)
[  102.303868] wlan0: authenticate with 58:6d:8f:41:93:ad (try 1)
[  102.305623] wlan0: authenticated
[  102.305798] wlan0: associate with 58:6d:8f:41:93:ad (try 1)
[  102.308739] wlan0: RX AssocResp from 58:6d:8f:41:93:ad (capab=0x401 status=18 aid=0)
[  102.308755] wlan0: 58:6d:8f:41:93:ad denied association (code=18)
[  102.308839] wlan0: deauthenticating from 58:6d:8f:41:93:ad by local choice (reason=3)
[  712.843368] Linux video capture interface: v2.00
[  712.875270] usbcore: registered new interface driver uvcvideo
[  712.875283] USB Video Class driver (v1.0.0)

```

---

### Post by xc3RnbFO8P on 2013-01-11
Now try Cheese
> sudo apt-get install cheese

---

### Post by orbesnet on 2013-01-11
"cheese is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

when i run it, it pinwheels for a bit and then just is blank and does nothing....

---

### Post by xc3RnbFO8P on 2013-01-11
If you run cheese from terminal, any errors.?

---

### Post by orbesnet on 2013-01-11
pops up and says "no device found"

seems like the computer doesn't even know that it has a webcam... idk.

---

### Post by mysteriousdarren on 2013-01-11
are the drivers installed?

---

### Post by orbesnet on 2013-01-11
I believe so, how can i check? (noob)

---

### Post by blueeyeblue on 2013-01-12
> **mysteriousdarren said:**
> are the drivers installed?

Could you kindly refer me to any site, where I can download and install package in one go?

It's more than 2 months and I still can't get my webcam to work! :-(

Thanks for any help in advance!

---

### Post by blueeyeblue on 2013-01-12
..so I have tried installing V4L-DVB Device Drivers: [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers), since "04f2:b084 - Unnamed (Acer Aspire One D150) - Chicony Electronics) is in the following list: [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

I still don't  see integrated webcam in "lsusb" list.


Any ideas?

---

### Post by xc3RnbFO8P on 2013-01-12
Check
> gstreamer-properties
> ls /dev/video*

---

### Post by blueeyeblue on 2013-01-12
> **Ringi said:**
> Check

Tried it, but it still does not recognize my webcam.

```
root@blueeyeblue:~# gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'alsasink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
root@blueeyeblue:~# ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
```

I've also tried to reloading some mudules, here is what I got:

```
WARNING: Error inserting v4l2_common (/lib/modules/3.2.6/kernel/drivers/media/v4l2-core/v4l2-common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting saa7134 (/lib/modules/3.2.6/kernel/drivers/media/pci/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

---

### Post by xc3RnbFO8P on 2013-01-12
Read this:
[http://askubuntu.com/questions/57704/is-there-a-ubuntu-sanity-check/57728#57728]("http://askubuntu.com/questions/57704/is-there-a-ubuntu-sanity-check/57728#57728")

---

### Post by blueeyeblue on 2013-01-12
> **Ringi said:**
> Read this:
[http://askubuntu.com/questions/57704/is-there-a-ubuntu-sanity-check/57728#57728]("http://askubuntu.com/questions/57704/is-there-a-ubuntu-sanity-check/57728#57728")

I've done it, went through the whole process and no change?

I can't still see my webcam, when I type "lsusb" command..

Edit 1: Command: "uvcvideo" still not recognized :-(

Thanks for any further help or ideas!

---

### Post by blueeyeblue on 2013-01-13
bump..

Anybody any news or suggestions?

---

### Post by mörgæs on 2013-01-13
Before putting more time into troubleshooting in 10.04 I would begin with a fresh install of 12.10, plain and simple. Fighting with these problems is not a noob-job.

---

### Post by blueeyeblue on 2013-01-14
> **mörgæs said:**
> Before putting more time into troubleshooting in 10.04 I would begin with a fresh install of 12.10, plain and simple. Fighting with these problems is not a noob-job.

Heh, I have installed fedora, xubuntu, kubuntu, ubuntu, mandriva and opensuse, all the latest version with no luck, even with drivers installed..

---

### Post by xc3RnbFO8P on 2013-01-15
Then it's a hardware failure?

---

### Post by blueeyeblue on 2013-01-15
> **Ringi said:**
> Then it's a hardware failure?

It does work in Windows. I haven't seen anyone who had webcam working.

---

### Post by xc3RnbFO8P on 2013-01-15
Maybe a longshot check 
> /etc/modprobe.d/blacklist.conf

---

### Post by blueeyeblue on 2013-01-16
> **Ringi said:**
> Maybe a longshot check

So here's what I got:

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug
blacklist ar9170usb
blacklist r8187
blacklist ath_pci

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


What line should I uncomment/comment? Thanks for help though!

---

### Post by xc3RnbFO8P on 2013-01-16
> **blueeyeblue said:**
> So here's what I got:




What line should I uncomment/comment? Thanks for help though!

Nothing.

I have search the www and found one possible solution if you
want to try it.
Download XP driver [**here**]("http://global-download.acer.com/GDFiles/Driver/Camera/CCD_Suyin_AP_2.2.0.2_XPx86.zip?acerid=633701164600666001&Step1=Netbook,%20Chromebook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=EMEA_9")
and try to get it working in Wine,
see if the camera is seen in > dmesg
or
> lsusb
if so start cheese.

---

### Post by blueeyeblue on 2013-01-17
> **Ringi said:**
> Nothing.

I have search the www and found one possible solution if you
want to try it.
Download XP driver [**here**]("http://global-download.acer.com/GDFiles/Driver/Camera/CCD_Suyin_AP_2.2.0.2_XPx86.zip?acerid=633701164600666001&Step1=Netbook,%20Chromebook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=EMEA_9")
and try to get it working in Wine,
see if the camera is seen in 
or

if so start cheese.

Hi,

I haven't been able to get driver to work.
I've successfully installed it under Wine though.

Thanks for help nevertheless!

---

### Post by xc3RnbFO8P on 2013-01-17
Another option is to use **VMware**
[https://help.ubuntu.com/community/VMware/Server]("https://help.ubuntu.com/community/VMware/Server")

---

### Post by blueeyeblue on 2013-01-17
> **Ringi said:**
> Another option is to use **VMware**
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

Hey, AAO does not support HW virtualization, so I won't be able to use VMware here :-/

Could you please tell me why the installed software through Wine should get rid of problems with the webcam?

---

### Post by xc3RnbFO8P on 2013-01-17
> **blueeyeblue said:**
> Hey, AAO does not support HW virtualization, so I won't be able to use VMware here :-/

Could you please tell me why the installed software through Wine should get rid of problems with the webcam?

This webcam is working in Windows, I think there is a hardware switch (works like hotkey) but opens by software.
If you can start (open) the webcam, then Ubuntu can see it and hopefully use the webcam.

I have similar problem with acerhk on my 2006 Medion laptop, my wireless didn't work, the solution was to start with Ubuntu 9.10 (it worked in 9.10) and update it to 12.04 (it wasn't easy).
Now I got wireless working only with usb wireless, the wireless card inside the computer don't.
Install XP   didn't help.

---

### Post by blueeyeblue on 2013-01-17
So? I won't get my webcam to work under any Linux Distro, right?

---

### Post by xc3RnbFO8P on 2013-01-17
> **blueeyeblue said:**
> So? I won't get my webcam to work under any Linux Distro, right?
I'm saying its maybe possible it will work, if you get this Win webcam program to run.

---

### Post by blueeyeblue on 2013-01-17
> **Ringi said:**
> I'm saying its maybe possible it will work, if you get this Win webcam program to run.

I tried it, installed it, but when I try to run the Webcam control app under Wine, it just opened for a short time and then it fcs.

---

### Post by xc3RnbFO8P on 2013-01-17
This is what I get (see screenshot)
run it from terminal

---

### Post by blueeyeblue on 2013-01-18
I've also seen that executable, but after I've clicked it, it just disappeared.

---

### Post by xc3RnbFO8P on 2013-01-18
> **blueeyeblue said:**
> I've also seen that executable, but after I've clicked it, it just disappeared.

did you try to run it from terminal?
> wine
drag and drop the .exe into terminal

---

### Post by blueeyeblue on 2013-01-18
Okey, I did it, but still missing some library or sth..

> root@blueeyeblue:~# wine '/root/.wine/dosdevices/c:/windows/Acer Crystal Eye webcam.exe' 
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\Acer Crystal Eye webcam.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Acer Crystal Eye webcam.exe" failed, status c0000135


---

### Post by xc3RnbFO8P on 2013-01-18
Use  winetricks to install VCRUN6 and MFC42.DLL
select the default wineprefix/install a windows DLL/VCRUN6

---

### Post by blueeyeblue on 2013-01-19
Cheers!

The same here...

---

