---
title: "WUSB54G ver. 4 / 10.04 / Systemax SYXG31M3"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by sks24 on 2010-10-22
I'm having difficulty enabling a linksys USB wireless adapter in the above configuration. 

I tried to boot with the "pci=noapic" option, but the adapter always showed up as "disabled."  Also, even though a physical connection via cat5 cable works fine, I'm now getting this error message: "could not find information on interface "eth0avahi"

Thanks in advance for your help.

Here are the terminal results:



[    0.248853] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.248855] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.248857] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.248860] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.248897] NET: Registered protocol family 2
[    0.248993] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.249287] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.249757] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.250059] TCP: Hash tables configured (established 131072 bind 65536)
[    0.250062] TCP reno registered
[    0.250160] NET: Registered protocol family 1
[    0.250182] pci 0000:00:02.0: Boot video device
[    0.250444] cpufreq-nforce2: No nForce2 chipset.
[    0.250473] Scanning for low memory corruption every 60 seconds
[    0.250577] audit: initializing netlink socket (disabled)
[    0.250587] type=2000 audit(1287763060.247:1): initialized
[    0.258970] highmem bounce pool size: 64 pages
[    0.258976] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.260350] VFS: Disk quotas dquot_6.5.2
[    0.260412] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.260943] fuse init (API version 7.13)
[    0.261025] msgmni has been set to 1664
[    0.261235] alg: No test for stdrng (krng)
[    0.261290] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.261292] io scheduler noop registered
[    0.261294] io scheduler anticipatory registered
[    0.261296] io scheduler deadline registered
[    0.261331] io scheduler cfq registered (default)
[    0.261457]   alloc irq_desc for 24 on node -1
[    0.261460]   alloc kstat_irqs on node -1
[    0.261470] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.261478] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.261588]   alloc irq_desc for 25 on node -1
[    0.261590]   alloc kstat_irqs on node -1
[    0.261597] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.261604] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.261690] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.261710] Firmware did not grant requested _OSC control
[    0.261726] Firmware did not grant requested _OSC control
[    0.261751] Firmware did not grant requested _OSC control
[    0.261762] Firmware did not grant requested _OSC control
[    0.261774] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.261865] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.261868] ACPI: Power Button [PWRB]
[    0.261907] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.261909] ACPI: Power Button [PWRF]
[    0.262522] ACPI: SSDT bf6b00f0 00277 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.262815] processor LNXCPU:00: registered as cooling_device0
[    0.263188] ACPI: SSDT bf6b0370 00277 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.263460] processor LNXCPU:01: registered as cooling_device1
[    0.267366] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.267461] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.267556] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.267871] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.268078] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.269022] brd: module loaded
[    0.269437] loop: module loaded
[    0.269526] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.269625] ata_piix 0000:00:1f.1: version 2.13
[    0.269641]   alloc irq_desc for 18 on node -1
[    0.269643]   alloc kstat_irqs on node -1
[    0.269650] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.269692] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.269775] scsi0 : ata_piix
[    0.269850] scsi1 : ata_piix
[    0.271028] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.271031] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.271058]   alloc irq_desc for 19 on node -1
[    0.271060]   alloc kstat_irqs on node -1
[    0.271065] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.271069] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.271105] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.271158] scsi2 : ata_piix
[    0.271208] scsi3 : ata_piix
[    0.272375] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
[    0.272378] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
[    0.272446] isapnp: Scanning for PnP cards...
[    0.272700] Fixed MDIO Bus: probed
[    0.272730] PPP generic driver version 2.4.2
[    0.272780] tun: Universal TUN/TAP device driver, 1.6
[    0.272782] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.272863] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.272883]   alloc irq_desc for 23 on node -1
[    0.272885]   alloc kstat_irqs on node -1
[    0.272890] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.272906] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.272909] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.272937] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.272953] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.272963] ehci_hcd 0000:00:1d.7: debug port 1
[    0.276854] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.276867] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea77c00
[    0.291710] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.291833] usb usb1: configuration #1 chosen from 1 choice
[    0.291860] hub 1-0:1.0: USB hub found
[    0.291869] hub 1-0:1.0: 8 ports detected
[    0.291935] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.291951] uhci_hcd: USB Universal Host Controller Interface driver
[    0.291992] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.292002] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.292005] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.292038] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.292062] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    0.292137] usb usb2: configuration #1 chosen from 1 choice
[    0.292159] hub 2-0:1.0: USB hub found
[    0.292165] hub 2-0:1.0: 2 ports detected
[    0.292205] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.292210] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.292213] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.292239] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.292260] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.292337] usb usb3: configuration #1 chosen from 1 choice
[    0.292359] hub 3-0:1.0: USB hub found
[    0.292364] hub 3-0:1.0: 2 ports detected
[    0.292403] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.292408] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.292410] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.292436] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.292464] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    0.292541] usb usb4: configuration #1 chosen from 1 choice
[    0.292562] hub 4-0:1.0: USB hub found
[    0.292567] hub 4-0:1.0: 2 ports detected
[    0.292605] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.292611] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.292613] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.292639] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.292667] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[    0.292739] usb usb5: configuration #1 chosen from 1 choice
[    0.292763] hub 5-0:1.0: USB hub found
[    0.292768] hub 5-0:1.0: 2 ports detected
[    0.292859] PNP: No PS/2 controller found. Probing ports directly.
[    0.295354] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.295360] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.295476] mice: PS/2 mouse device common for all mice
[    0.295584] rtc_cmos 00:03: RTC can wake from S4
[    0.295628] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.295650] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.295745] device-mapper: uevent: version 1.0.3
[    0.321709] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.346174] Freeing initrd memory: 7780k freed
[    0.349845] device-mapper: multipath: version 1.1.0 loaded
[    0.349849] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.350014] EISA: Probing bus 0 at eisa.0
[    0.350021] Cannot allocate resource for EISA slot 1
[    0.350040] EISA: Detected 0 cards.
[    0.350111] cpuidle: using governor ladder
[    0.350113] cpuidle: using governor menu
[    0.350515] TCP cubic registered
[    0.350648] NET: Registered protocol family 10
[    0.351075] lo: Disabled Privacy Extensions
[    0.351374] NET: Registered protocol family 17
[    0.351949] Using IPI No-Shortcut mode
[    0.352032] PM: Resume from disk failed.
[    0.352042] registered taskstats version 1
[    0.352291]   Magic number: 14:710:993
[    0.352361] rtc_cmos 00:03: setting system clock to 2010-10-22 15:57:41 UTC (1287763061)
[    0.352363] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.352365] EDD information not available.
[    0.460047] ata1.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[    0.460069] ata1.00: limited to UDMA/33 due to 40-wire cable
[    0.460321] ata3.00: ATA-7: Hitachi HDT725025VLA380, V5DOA7EA, max UDMA/133
[    0.460323] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.476063] ata3.00: configured for UDMA/133
[    0.491784] ata1.00: configured for UDMA/33
[    0.615605] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    0.625356] isapnp: No Plug & Play device found
[    0.626430] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[    0.631590] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.631594] Uniform CD-ROM driver Revision: 3.20
[    0.631755] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.631809] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.631930] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5
[    0.632028] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.632040] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.632078] sd 2:0:0:0: [sda] Write Protect is off
[    0.632080] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.632101] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.632214]  sda: sda1 sda2 < sda5 sda6 >
[    0.679477] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.679490] Freeing unused kernel memory: 656k freed
[    0.679786] Write protecting the kernel text: 4684k
[    0.679823] Write protecting the kernel read-only data: 1840k
[    0.695315] udev: starting version 151
[    0.783691] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.783711] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.783747] r8169 0000:02:00.0: setting latency timer to 64
[    0.783792]   alloc irq_desc for 26 on node -1
[    0.783794]   alloc kstat_irqs on node -1
[    0.783808] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    0.784406] eth0: RTL8168c/8111c at 0xf8064000, 00:24:21:30:aa:84, XID 1c4000c0 IRQ 26
[    0.934166] usb 1-4: configuration #1 chosen from 1 choice
[    1.125233] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    1.396032] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    1.573596] usb 4-2: configuration #1 chosen from 1 choice
[   10.857423] udev: starting version 151
[   10.898730] Adding 4779000k swap on /dev/sda6.  Priority:-1 extents:1 across:4779000k 
[   10.999139] Linux agpgart interface v0.103
[   11.004204] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[   11.004490] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   11.052810] intel_rng: FWH not detected
[   11.065076] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   11.125026] [drm] Initialized drm 1.1.0 20060810
[   11.134920] parport_pc 00:0d: reported by Plug and Play ACPI
[   11.134964] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.156967] lp: driver loaded but no devices found
[   11.166862] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.166867] i915 0000:00:02.0: setting latency timer to 64
[   11.170705] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   11.170709] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   11.173331] ppdev: user-space parallel port driver
[   11.175320]   alloc irq_desc for 27 on node -1
[   11.175323]   alloc kstat_irqs on node -1
[   11.175331] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[   11.175338] [drm] set up 7M of stolen space
[   11.175708] [drm] initialized overlay support
[   11.179866] type=1505 audit(1287777472.323:2):  operation="profile_load" pid=574 name="/sbin/dhclient3"
[   11.180465] type=1505 audit(1287777472.327:3):  operation="profile_load" pid=574 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.180772] type=1505 audit(1287777472.327:4):  operation="profile_load" pid=574 name="/usr/lib/connman/scripts/dhclient-script"
[   11.210654] r8169: eth0: link down
[   11.210824] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.232694] lp0: using parport0 (interrupt-driven).
[   11.239663] Disabling lock debugging due to kernel taint
[   11.252751] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   11.320956] usbcore: registered new interface driver hiddev
[   11.334592] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3
[   11.334694] generic-usb 0003:046D:C509.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2/input0
[   11.336311] fb0: inteldrmfb frame buffer device
[   11.336314] registered panic notifier
[   11.336448] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.337071] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.337098] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.338974] vga16fb: initializing
[   11.338979] vga16fb: mapped to 0xc00a0000
[   11.338983] vga16fb: not registering due to another framebuffer present
[   11.368725] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input4
[   11.368829] generic-usb 0003:046D:C509.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2/input1
[   11.368860] usbcore: registered new interface driver usbhid
[   11.368862] usbhid: v2.6:USB HID core driver
[   11.408821] hda_codec: ALC888: BIOS auto-probing.
[   11.410212] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   11.448728] Console: switching to colour frame buffer device 160x64
[   11.832589] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[   11.971577] type=1505 audit(1287777473.115:5):  operation="profile_load" pid=891 name="/usr/share/gdm/guest-session/Xsession"
[   11.973205] type=1505 audit(1287777473.119:6):  operation="profile_replace" pid=892 name="/sbin/dhclient3"
[   11.973781] type=1505 audit(1287777473.119:7):  operation="profile_replace" pid=892 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.974092] type=1505 audit(1287777473.119:8):  operation="profile_replace" pid=892 name="/usr/lib/connman/scripts/dhclient-script"
[   11.977605] type=1505 audit(1287777473.123:9):  operation="profile_load" pid=893 name="/usr/bin/evince"
[   11.985413] type=1505 audit(1287777473.131:10):  operation="profile_load" pid=893 name="/usr/bin/evince-previewer"
[   11.990047] type=1505 audit(1287777473.135:11):  operation="profile_load" pid=893 name="/usr/bin/evince-thumbnailer"
[   12.097275] ndiswrapper: driver rt2500usb (Linksys,04/13/2005, 2.00.02.0000) loaded
[   12.156544] apm: BIOS not found.
[   12.670498] CPU0 attaching NULL sched-domain.
[   12.670504] CPU1 attaching NULL sched-domain.
[   12.680763] wlan0: ethernet device 00:1e:e5:f8:bf:1e using NDIS driver: rt2500usb, version: 0x20000, NDIS version: 0x500, vendor: 'Ralink Technology Inc.', 13B1:000D.F.conf
[   12.681561] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   12.682346] usbcore: registered new interface driver ndiswrapper
[   12.688156] CPU0 attaching sched-domain:
[   12.688159]  domain 0: span 0-1 level MC
[   12.688162]   groups: 0 1
[   12.688167] CPU1 attaching sched-domain:
[   12.688169]  domain 0: span 0-1 level MC
[   12.688171]   groups: 1 0
[   13.922851] CPU0 attaching NULL sched-domain.
[   13.922857] CPU1 attaching NULL sched-domain.
[   13.948612] CPU0 attaching sched-domain:
[   13.948615]  domain 0: span 0-1 level MC
[   13.948618]   groups: 0 1
[   13.948624] CPU1 attaching sched-domain:
[   13.948625]  domain 0: span 0-1 level MC
[   13.948627]   groups: 1 0
[ 1900.650263] BUG: unable to handle kernel paging request at 50002251
[ 1900.650274] IP: [<f833fc19>] 0xf833fc19
[ 1900.650283] *pde = 00000000 
[ 1900.650289] Oops: 0000 [#1] SMP 
[ 1900.650294] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/uevent
[ 1900.650300] Modules linked in: binfmt_misc snd_hda_codec_realtek fbcon tileblit font bitblit softcursor vga16fb vgastate usbhid snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device ndiswrapper ppdev i915 drm_kms_helper lp parport_pc snd parport hid drm psmouse serio_raw soundcore snd_page_alloc intel_agp agpgart i2c_algo_bit video output r8169 mii
[ 1900.650365] 
[ 1900.650371] Pid: 1006, comm: ntdriver Tainted: P           (2.6.32-25-generic #44-Ubuntu) Z1-7529
[ 1900.650376] EIP: 0060:[<f833fc19>] EFLAGS: 00010202 CPU: 0
[ 1900.650380] EIP is at 0xf833fc19
[ 1900.650384] EAX: 00000001 EBX: f46f72c0 ECX: 00000000 EDX: 50002251
[ 1900.650388] ESI: fa1a0000 EDI: f833c940 EBP: f244be24 ESP: f244be20
[ 1900.650393]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[ 1900.650398] Process ntdriver (pid: 1006, ti=f244a000 task=f46f72c0 task.ti=f244a000)
[ 1900.650401] Stack:
[ 1900.650404]  0044bf18 f244bf54 f8348ac9 50002251 f244bf18 0044be5c c0101c1d c2c08760
[ 1900.650416] <0> c2c08760 f46e5c00 0004be64 c0010146 968b8482 6c483024 6018120c f244be74
[ 1900.650429] <0> f46f0064 0844bebc 11692300 f24418b7 ff000b38 3000012f 00000118 1eddac0f
[ 1900.650443] Call Trace:
[ 1900.650452]  [<c0101c1d>] ? __switch_to+0xcd/0x180
[ 1900.650476]  [<f898e372>] ? ntdriver_thread+0x62/0xa0 [ndiswrapper]
[ 1900.650495]  [<f898e310>] ? ntdriver_thread+0x0/0xa0 [ndiswrapper]
[ 1900.650502]  [<c01677d4>] ? kthread+0x74/0x80
[ 1900.650507]  [<c0167760>] ? kthread+0x0/0x80
[ 1900.650514]  [<c0104087>] ? kernel_thread_helper+0x7/0x10
[ 1900.650517] Code: d4 8b e5 5d c2 04 00 cc cc cc cc cc cc cc cc cc cc cc 55 8b ec 51 c6 45 ff 00 eb 08 8a 45 ff 04 01 88 45 ff 0f b6 4d ff 8b 55 08 <0f> b6 02 3b c8 7d 29 6a 06 8b 4d 0c 51 0f b6 55 ff 69 d2 38 09 
[ 1900.650590] EIP: [<f833fc19>] 0xf833fc19 SS:ESP 0068:f244be20
[ 1900.650602] CR2: 0000000050002251
[ 1900.650607] ---[ end trace 48eb76bcbbd7a525 ]---
[ 3240.530681] r8169: eth0: link up
[ 3240.530982] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3251.068017] eth0: no IPv6 routers present
[ 3260.904650] lo: Disabled Privacy Extensions
[ 3277.654668] lo: Disabled Privacy Extensions
[ 3293.015078] r8169: eth0: link down
[ 3297.258841] r8169: eth0: link up
[ 3324.085151] lo: Disabled Privacy Extensions
[ 3542.484146] __ratelimit: 9 callbacks suppressed
[ 3542.484153] type=1503 audit(1287781003.631:15):  operation="capable" pid=1974 parent=1953 profile="/sbin/dhclient3" name="net_admin"
[ 3635.223651] r8169: eth0: link down
[ 3636.935572] r8169: eth0: link up
[ 3637.605540] r8169: eth0: link down
[ 5308.622866] r8169: eth0: link up
[ 5315.734228] lo: Disabled Privacy Extensions
jim@dhcppc1:~$ sudo lshw -C network
[sudo] password for jim: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:30:aa:84
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.105 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:febf0000-febfffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:f8:bf:1e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500usb driverversion=1.55+Linksys,04/13/2005, 2.00.02 link=no multicast=yes wireless=IEEE 802.11g
jim@dhcppc1:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:CD:10:70
                    ESSID:"pete"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:24:2C:50:18:4E
                    ESSID:"Staten"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:25:3C:29:E1:81
                    ESSID:"2WIRE342"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:00:00:00:09:96
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:26:50:C8:1A:B1
                    ESSID:"2WIRE851"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

jim@dhcppc1:~$ pete is the network i want to connect to
No command 'pete' found, did you mean:
 Command 'pente' from package 'pente' (universe)
 Command 'pee' from package 'moreutils' (universe)
pete: command not found
jim@dhcppc1:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
jim@dhcppc1:~$ lsb_release -d
Description:	Ubuntu 10.04.1 LTS
jim@dhcppc1:~$ uname -mr
2.6.32-25-generic i686
jim@dhcppc1:~$ sudo /ect/init.d/networking restart
sudo: /ect/init.d/networking: command not found
jim@dhcppc1:~$ sudo etc/init.d/networking restart
sudo: etc/init.d/networking: command not found
jim@dhcppc1:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 1599
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:24:21:30:aa:84
Sending on   LPF/eth0/00:24:21:30:aa:84
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:24:21:30:aa:84
Sending on   LPF/eth0/00:24:21:30:aa:84
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.105 from 192.168.1.1
DHCPREQUEST of 192.168.1.105 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.105 from 192.168.1.1
bound to 192.168.1.105 -- renewal in 32948 seconds.
                                                                         [ OK ]
jim@dhcppc1:~$

---

### Post by sks24 on 2010-10-23
In addition to selecting "pci=noapic" I went ahead and blacklisted the Windows drivers for this device (rt2500usb), but they wouldn't be blacklisted. I checked for dependencies and alias issues, and ran "sudo rmmod ssb".  Nothing phases that driver.

Here's what comes up in the terminal:

[INDENT]jim@dhcppc1:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2500usb : driver installed
	device (13B1:000D) present (alternate driver: rt2500usb)
jim@dhcppc1:~$ sudo lshw -C network
[sudo] password for jim: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:30:aa:84
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:febf0000-febfffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:f8:bf:1e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500usb driverversion=1.55+Linksys,04/13/2005, 2.00.02 link=no multicast=yes wireless=IEEE 802.11g
jim@dhcppc1:~$ sudo rmmod rt2500usb
ERROR: Module rt2500usb does not exist in /proc/modules
jim@dhcppc1:~$ depmod -n | grep alias | grep -v ':' | grep -i rt2500usb
jim@dhcppc1:~$ 
[/INDENT]

Does Ubuntu support this device?  If I were to go out and buy another pci wireless card for this tower . . . well, is there a cheap one which has at least average performance?

Thanks,
Scott

---

### Post by SeijiSensei on 2010-10-23
If you can download a Maverick live CD, try booting from that and see if it works better.  Lucid had problems with that wifi device for me.

---

### Post by sks24 on 2010-10-23
Thanks SeijiSensei,

Unless somebody chimes in here in the next day or so with a solution, I think I'm going to give up on this device for this machine and distro.  I'll just buy another usb wireless adapter which will plug and play with Linux.

---

