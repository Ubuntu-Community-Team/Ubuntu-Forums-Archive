---
title: "Mythbuntu 10.10 Kworld ATSC 120 Tuner"
date: 2010-11-21
forum: Multimedia Software
---

### Post by Brianbuntu on 2010-11-21
I recently upgraded my Mythbuntu system to 10.10.  After the upgrade, KWorld ATSC 120 tv tuner, which I use only in digital (dvb) mode stopped working.  The tuner worked fine with previous versions of Mythbuntu 8, even after upgrades through versions 9 and 10.04.  I am unable to get a lock on any channel when I attempt a channel scan in the MythTV-Backend.  To set up the firmware, I used the instructions found at [http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120).  I have followed all of the instructions in step 3 of this to set up the firmware and and blacklist the drivers, etc.  I had to follow these steps to this to get the card working originally, so I went back through these instructions again and verified that everything was in place.

I have the firmware file xc3028-v27.fw in /lib/firmware

I have the firmware file dvb-fe-xc5000-1.1.fw in /lib/firmware/2.6.35-22-generic

I created a file /etc/modprobe.d/blacklist-misc.conf with the following contents:
blacklist cx8800
blacklist cx8802
blacklist cx88-alsa
blacklist cx88-dvb

Then, In my /etc/rc.local file, I have the following to load the module for digital tv and restart the mythtv backend:
mv /etc/modprobe.d/blacklist-misc.conf /tmp
modprobe cx88-dvb
cp /tmp/blacklist-misc.conf /etc/modprobe.d
/etc/init.d/mythtv-backend restart


I have tried everything that I can think of, but I am unable to get a channel lock on any channel.  Any help would be greatly appreciated.

Thanks,

Brian

---

### Post by vertago1 on 2011-01-26
I blacklisted cx8800 and cx88_alsa and installed the firmwares but haven't been able to get the channel scan to work either.

---

### Post by GreenTaurus on 2011-01-28
> **vertago1 said:**
> I blacklisted cx8800 and cx88_alsa and installed the firmwares but haven't been able to get the channel scan to work either.

I'm trying to do the opposite and just run the card in analog and I'm having the same issue. Card worked fine with 10.04 and myth v23

---

### Post by GreenTaurus on 2011-02-17
DMESG:
[    0.262741] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.263073] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.263236] TCP: Hash tables configured (established 131072 bind 65536)
[    0.263237] TCP reno registered
[    0.263297] NET: Registered protocol family 1
[    0.263415] pci 0000:01:00.0: Boot video device
[    0.263553] cpufreq-nforce2: No nForce2 chipset.
[    0.263572] Scanning for low memory corruption every 60 seconds
[    0.263650] audit: initializing netlink socket (disabled)
[    0.263658] type=2000 audit(1297977297.259:1): initialized
[    0.270961] highmem bounce pool size: 64 pages
[    0.270965] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.271958] VFS: Disk quotas dquot_6.5.2
[    0.271998] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.272389] fuse init (API version 7.13)
[    0.272446] msgmni has been set to 1517
[    0.272597] alg: No test for stdrng (krng)
[    0.272634] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.272636] io scheduler noop registered
[    0.272637] io scheduler anticipatory registered
[    0.272638] io scheduler deadline registered
[    0.272665] io scheduler cfq registered (default)
[    0.272767]   alloc irq_desc for 24 on node -1
[    0.272769]   alloc kstat_irqs on node -1
[    0.272776] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.272780] pcieport 0000:00:01.0: setting latency timer to 64
[    0.272854]   alloc irq_desc for 25 on node -1
[    0.272856]   alloc kstat_irqs on node -1
[    0.272861] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.272867] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.272952]   alloc irq_desc for 26 on node -1
[    0.272953]   alloc kstat_irqs on node -1
[    0.272958] pcieport 0000:00:1c.5: irq 26 for MSI/MSI-X
[    0.272964] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.273026] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.273085] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.273160] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.273163] ACPI: Power Button [PWRB]
[    0.273193] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.273195] ACPI: Power Button [PWRF]
[    0.273736] ACPI: SSDT cff90100 002B9 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.274162] processor LNXCPU:00: registered as cooling_device0
[    0.274483] ACPI: SSDT cff903c0 002B9 (v01 DpgPmm  P002Ist 00000012 INTL 20060113)
[    0.274892] processor LNXCPU:01: registered as cooling_device1
[    0.277691] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.278623] brd: module loaded
[    0.278937] loop: module loaded
[    0.278995] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.279072] ata_piix 0000:00:1f.2: version 2.13
[    0.279084]   alloc irq_desc for 19 on node -1
[    0.279085]   alloc kstat_irqs on node -1
[    0.279089] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.279093] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.279129] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.279179] scsi0 : ata_piix
[    0.279231] scsi1 : ata_piix
[    0.280150] ata1: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 19
[    0.280154] ata2: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 19
[    0.280170] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.280173] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.280199] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.280224] scsi2 : ata_piix
[    0.280259] scsi3 : ata_piix
[    0.280359] isapnp: Scanning for PnP cards...
[    0.281196] ata3: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb480 irq 19
[    0.281199] ata4: SATA max UDMA/133 cmd 0xb880 ctl 0xb800 bmdma 0xb488 irq 19
[    0.281423] Fixed MDIO Bus: probed
[    0.281445] PPP generic driver version 2.4.2
[    0.281468] tun: Universal TUN/TAP device driver, 1.6
[    0.281470] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.281532] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.281545]   alloc irq_desc for 18 on node -1
[    0.281546]   alloc kstat_irqs on node -1
[    0.281549] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.281558] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.281560] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.281583] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.281602] ehci_hcd 0000:00:1a.7: debug port 1
[    0.285495] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.285514] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfadff000
[    0.312815] Freeing initrd memory: 7733k freed
[    0.332939] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.333059] usb usb1: configuration #1 chosen from 1 choice
[    0.333089] hub 1-0:1.0: USB hub found
[    0.333097] hub 1-0:1.0: 6 ports detected
[    0.333154]   alloc irq_desc for 23 on node -1
[    0.333156]   alloc kstat_irqs on node -1
[    0.333161] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.333178] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.333181] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.333207] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.333227] ehci_hcd 0000:00:1d.7: debug port 1
[    0.337098] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.337113] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfadfe000
[    0.351878] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.351934] usb usb2: configuration #1 chosen from 1 choice
[    0.351952] hub 2-0:1.0: USB hub found
[    0.351956] hub 2-0:1.0: 6 ports detected
[    0.352004] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.352019] uhci_hcd: USB Universal Host Controller Interface driver
[    0.352055] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.352060] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.352063] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.352086] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.352111] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c800
[    0.352170] usb usb3: configuration #1 chosen from 1 choice
[    0.352187] hub 3-0:1.0: USB hub found
[    0.352192] hub 3-0:1.0: 2 ports detected
[    0.352225]   alloc irq_desc for 21 on node -1
[    0.352226]   alloc kstat_irqs on node -1
[    0.352229] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.352233] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.352235] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.352255] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.352279] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c880
[    0.352336] usb usb4: configuration #1 chosen from 1 choice
[    0.352355] hub 4-0:1.0: USB hub found
[    0.352359] hub 4-0:1.0: 2 ports detected
[    0.352388] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.352392] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.352395] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.352415] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.352434] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000cc00
[    0.352491] usb usb5: configuration #1 chosen from 1 choice
[    0.352509] hub 5-0:1.0: USB hub found
[    0.352514] hub 5-0:1.0: 2 ports detected
[    0.352545] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.352549] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.352551] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.352571] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.352590] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c080
[    0.352650] usb usb6: configuration #1 chosen from 1 choice
[    0.352667] hub 6-0:1.0: USB hub found
[    0.352671] hub 6-0:1.0: 2 ports detected
[    0.352700] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.352704] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.352706] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.352727] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.352746] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c400
[    0.352808] usb usb7: configuration #1 chosen from 1 choice
[    0.352825] hub 7-0:1.0: USB hub found
[    0.352830] hub 7-0:1.0: 2 ports detected
[    0.352859] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.352864] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.352866] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.352887] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.352905] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
[    0.352966] usb usb8: configuration #1 chosen from 1 choice
[    0.352982] hub 8-0:1.0: USB hub found
[    0.352987] hub 8-0:1.0: 2 ports detected
[    0.353056] PNP: No PS/2 controller found. Probing ports directly.
[    0.355828] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.355834] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.355888] mice: PS/2 mouse device common for all mice
[    0.355961] rtc_cmos 00:03: RTC can wake from S4
[    0.355990] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.356010] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.356081] device-mapper: uevent: version 1.0.3
[    0.356160] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.356202] device-mapper: multipath: version 1.1.0 loaded
[    0.356204] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.356278] EISA: Probing bus 0 at eisa.0
[    0.356282] Cannot allocate resource for EISA slot 1
[    0.356299] EISA: Detected 0 cards.
[    0.356348] cpuidle: using governor ladder
[    0.356349] cpuidle: using governor menu
[    0.356640] TCP cubic registered
[    0.356744] NET: Registered protocol family 10
[    0.357067] lo: Disabled Privacy Extensions
[    0.357295] NET: Registered protocol family 17
[    0.357931] Using IPI No-Shortcut mode
[    0.357987] PM: Resume from disk failed.
[    0.357997] registered taskstats version 1
[    0.358325]   Magic number: 15:647:247
[    0.358385] rtc_cmos 00:03: setting system clock to 2011-02-17 21:14:58 UTC (1297977298)
[    0.358387] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.358388] EDD information not available.
[    0.643992] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    0.644958] isapnp: No Plug & Play device found
[    0.798215] usb 1-3: configuration #1 chosen from 1 choice
[    0.799903] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.808046] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22LS40, LL02, max UDMA/100
[    0.824050] ata3.00: configured for UDMA/100
[    0.855907] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.896202] ata4.00: ATA-8: WDC WD2500BEVS-22UST0, 01.01A01, max UDMA/133
[    0.896206] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.912836] ata4.00: configured for UDMA/133
[    0.974408] ata2.00: SATA link down (SStatus 0 SControl 300)
[    0.974418] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.120055] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.120066] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.168444] ata1.00: ATA-7: ST3160815AS, 4.AAB, max UDMA/133
[    1.168447] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.208008] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    1.235098] ata1.00: configured for UDMA/133
[    1.235204] scsi 0:0:0:0: Direct-Access     ATA      ST3160815AS      4.AA PQ: 0 ANSI: 5
[    1.235285] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.235293] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.235315] sd 0:0:0:0: [sda] Write Protect is off
[    1.235317] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.235339] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.235432]  sda:
[    1.238735] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22LS40  LL02 PQ: 0 ANSI: 5
[    1.260480] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.260483] Uniform CD-ROM driver Revision: 3.20
[    1.260569] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.260598] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.260671] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5
[    1.260734] sd 3:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.260744] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.260771] sd 3:0:0:0: [sdb] Write Protect is off
[    1.260773] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.260793] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.260883]  sdb: sda1 sda2 < sda5 sdb1
[    1.318440] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.322388]  sda6 >
[    1.322600] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.322610] Freeing unused kernel memory: 676k freed
[    1.322866] Write protecting the kernel text: 4840k
[    1.322918] Write protecting the kernel read-only data: 1884k
[    1.333737] udev: starting version 151
[    1.385634] usb 6-2: configuration #1 chosen from 1 choice
[    1.390456] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.390473] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.390512] r8169 0000:02:00.0: setting latency timer to 64
[    1.390552]   alloc irq_desc for 27 on node -1
[    1.390554]   alloc kstat_irqs on node -1
[    1.390566] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    1.391023] eth0: RTL8168c/8111c at 0xf826e000, 00:23:54:37:6a:74, XID 1c4000c0 IRQ 27
[    1.428519] Initializing USB Mass Storage driver...
[    1.428586] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.428651] usbcore: registered new interface driver usb-storage
[    1.428653] USB Mass Storage support registered.
[    1.428734] usb-storage: device found at 2
[    1.428735] usb-storage: waiting for device to settle before scanning
[    1.428762] usbcore: registered new interface driver hiddev
[    1.428820] usbcore: registered new interface driver usbhid
[    1.428822] usbhid: v2.6:USB HID core driver
[    1.444738] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input3
[    1.444959] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-2/input0
[    1.476562] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    1.477058] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input4
[    1.477146] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2/input1
[    1.628014] usb 8-2: new full speed USB device using uhci_hcd and address 2
[    1.734001] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    1.734004] EXT4-fs (sda5): write access will be enabled during recovery
[    2.509128] EXT4-fs (sda5): orphan cleanup on readonly fs
[    2.509134] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 524317
[    2.509156] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 524310
[    2.509162] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 524309
[    2.509168] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 524297
[    2.509174] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 524295
[    2.509179] EXT4-fs (sda5): 5 orphan inodes deleted
[    2.509181] EXT4-fs (sda5): recovery complete
[    3.099200] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.430393] usb-storage: device scan complete
[    6.434011] scsi 4:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[    6.434383] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    6.447990] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    6.628012] uhci_hcd 0000:00:1d.2: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   16.740014] usb 8-2: device descriptor read/64, error -110
[   18.431123] udev: starting version 151
[   18.501523] Linux agpgart interface v0.103
[   18.506794] vga16fb: initializing
[   18.506797] vga16fb: mapped to 0xc00a0000
[   18.506856] fb0: VGA16 VGA frame buffer device
[   18.511373] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   18.511377] Disabling lock debugging due to kernel taint
[   18.589502] Adding 224868k swap on /dev/sda6.  Priority:-1 extents:1 across:224868k 
[   18.666522] type=1505 audit(1297998916.806:2):  operation="profile_load" pid=674 name="/sbin/dhclient3"
[   18.666997] type=1505 audit(1297998916.806:3):  operation="profile_load" pid=674 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.667262] type=1505 audit(1297998916.806:4):  operation="profile_load" pid=674 name="/usr/lib/connman/scripts/dhclient-script"
[   18.671200] type=1505 audit(1297998916.810:5):  operation="profile_load" pid=687 name="/usr/sbin/ntpd"
[   18.673319] type=1505 audit(1297998916.814:6):  operation="profile_replace" pid=688 name="/sbin/dhclient3"
[   18.673816] type=1505 audit(1297998916.814:7):  operation="profile_replace" pid=688 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.674084] type=1505 audit(1297998916.814:8):  operation="profile_replace" pid=688 name="/usr/lib/connman/scripts/dhclient-script"
[   18.675691] type=1505 audit(1297998916.814:9):  operation="profile_replace" pid=701 name="/usr/sbin/ntpd"
[   18.697515] [fglrx] Maximum main memory to use for locked dma buffers: 3810 MBytes.
[   18.697576] [fglrx]   vendor: 1002 device: 68d9 count: 1
[   18.697920] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[   18.697932] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.697936] pci 0000:01:00.0: setting latency timer to 64
[   18.711973] [fglrx] Kernel PAT support is enabled
[   18.711987] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[   18.722219] lp: driver loaded but no devices found
[   18.779840]   alloc irq_desc for 22 on node -1
[   18.779842]   alloc kstat_irqs on node -1
[   18.779847] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.779872] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.814446] Console: switching to colour frame buffer device 80x30
[   18.865367] type=1505 audit(1297998917.006:10):  operation="profile_replace" pid=833 name="/sbin/dhclient3"
[   18.865850] type=1505 audit(1297998917.006:11):  operation="profile_replace" pid=833 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.949736] r8169: eth0: link up
[   18.949740] r8169: eth0: link up
[   19.476411] ppdev: user-space parallel port driver
[   19.812511] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   20.038821] CPU0 attaching NULL sched-domain.
[   20.038825] CPU1 attaching NULL sched-domain.
[   20.160047] CPU0 attaching sched-domain:
[   20.160050]  domain 0: span 0-1 level MC
[   20.160052]   groups: 0 1
[   20.160056] CPU1 attaching sched-domain:
[   20.160057]  domain 0: span 0-1 level MC
[   20.160059]   groups: 1 0
[   20.284027] Linux video capture interface: v2.00
[   20.320540] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   20.320570] cx8800 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.320780] cx88[0]: subsystem: 17de:08c1, board: Kworld PlusTV HD PCI 120 (ATSC 120) [card=67,autodetected], frontend(s): 1
[   20.320782] cx88[0]: TV tuner type 71, Radio tuner type -1
[   20.460042] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   20.596096] xc2028 0-0061: creating new instance
[   20.596098] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   20.596101] cx88[0]: Asking xc2028/3028 to load firmware xc3028-v27.fw
[   20.616022] cx88[0]/0: found at 0000:04:00.0, rev: 5, irq: 16, latency: 64, mmio: 0xfb000000
[   20.616031] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   20.616379] cx88[0]/0: registered device video0 [v4l2]
[   20.616621] cx88[0]/0: registered device vbi0
[   20.616859] cx88[0]/0: registered device radio0
[   20.616928] cx8800 0000:04:00.0: firmware: requesting xc3028-v27.fw
[   20.668015] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   20.668070] cx88[0]: Calling XC2028/3028 callback
[   20.816503] hda-intel: Codec #1 probe error; disabling it...
[   20.866502] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   20.866505] cx88[0]: Calling XC2028/3028 callback
[   20.887809] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   20.897696] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.897731] HDA Intel 0000:01:00.1: setting latency timer to 64
[   21.853180] i2c i2c-0: sendbytes: NAK bailout.
[   21.853204] xc2028 0-0061: i2c output error: rc = -5 (should be 4)
[   21.853206] xc2028 0-0061: -5 returned from send
[   21.853208] xc2028 0-0061: Error -22 while loading base firmware
[   21.912010] cx88[0]: Calling XC2028/3028 callback
[   22.110446] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   22.110451] cx88[0]: Calling XC2028/3028 callback
[   23.634301] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   23.655932] SCODE (20000000), id 000000000000b700:
[   23.655935] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   23.724007] cx88[0]: Calling XC2028/3028 callback
[   23.848013] cx88[0]: Calling XC2028/3028 callback
[   24.046434] xc2028 0-0061: Loading firmware for type=BASE FM (401), id 0000000000000000.
[   24.046437] cx88[0]: Calling XC2028/3028 callback
[   24.249379] cx2388x alsa driver version 0.0.7 loaded
[   24.249414] cx88_audio 0000:04:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.249421] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.249436] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   24.879688] i2c i2c-0: sendbytes: NAK bailout.
[   24.879805] xc2028 0-0061: i2c output error: rc = -5 (should be 4)
[   24.879807] xc2028 0-0061: -5 returned from send
[   24.879903] xc2028 0-0061: Error -22 while loading base firmware
[   24.932507] cx88[0]: Calling XC2028/3028 callback
[   25.130927] xc2028 0-0061: Loading firmware for type=BASE FM (401), id 0000000000000000.
[   25.130931] cx88[0]: Calling XC2028/3028 callback
[   26.630304] xc2028 0-0061: Loading firmware for type=FM (400), id 0000000000000000.
[   26.664009] cx88[0]: Calling XC2028/3028 callback
[   26.784013] cx88[0]: Calling XC2028/3028 callback
[   26.982444] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   26.982447] cx88[0]: Calling XC2028/3028 callback
[   27.810789] i2c i2c-0: sendbytes: NAK bailout.
[   27.810906] xc2028 0-0061: i2c output error: rc = -5 (should be 4)
[   27.810907] xc2028 0-0061: -5 returned from send
[   27.811003] xc2028 0-0061: Error -22 while loading base firmware
[   27.864010] cx88[0]: Calling XC2028/3028 callback
[   28.062442] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   28.062445] cx88[0]: Calling XC2028/3028 callback
[   29.122592] i2c i2c-0: sendbytes: NAK bailout.
[   29.122708] xc2028 0-0061: i2c output error: rc = -5 (should be 4)
[   29.122710] xc2028 0-0061: -5 returned from send
[   29.122806] xc2028 0-0061: Error -22 while loading base firmware
[   29.124035] cx88[0]: Calling XC2028/3028 callback
[   29.322461] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   29.322464] cx88[0]: Calling XC2028/3028 callback
[   29.676504] eth0: no IPv6 routers present
[   30.383978] i2c i2c-0: sendbytes: NAK bailout.
[   30.384001] xc2028 0-0061: i2c output error: rc = -5 (should be 4)
[   30.384003] xc2028 0-0061: -5 returned from send
[   30.384005] xc2028 0-0061: Error -22 while loading base firmware
[   30.524454] cx88[0]: Calling XC2028/3028 callback
[   30.722878] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   30.722882] cx88[0]: Calling XC2028/3028 callback
[   30.960498]   alloc irq_desc for 28 on node -1
[   30.960500]   alloc kstat_irqs on node -1
[   30.960508] fglrx_pci 0000:01:00.0: irq 28 for MSI/MSI-X
[   31.000163] [fglrx] Firegl kernel thread PID: 1551
[   31.039421] [fglrx] IRQ 28 Enabled
[   31.391073] [fglrx] Gart USWC size:1279 M.
[   31.391076] [fglrx] Gart cacheable size:508 M.
[   31.391080] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   31.391082] [fglrx] Reserved FB block: Unshared offset:f8ff000, size:401000 
[   31.391084] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   31.788898] i2c i2c-0: sendbytes: NAK bailout.
[   31.788922] xc2028 0-0061: i2c output error: rc = -5 (should be 4)
[   31.788924] xc2028 0-0061: -5 returned from send
[   31.788926] xc2028 0-0061: Error -22 while loading base firmware
[   31.788975] cx88[0]: Calling XC2028/3028 callback
[   31.987394] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   31.987397] cx88[0]: Calling XC2028/3028 callback
[   32.310149] usb 8-2: device descriptor read/64, error -110
[   32.536069] usb 8-2: new full speed USB device using uhci_hcd and address 3
[   33.514814] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   33.536707] SCODE (20000000), id 000000000000b700:
[   33.536710] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   33.570403] xc2028 0-0061: Incorrect readback of firmware version.
[   33.624507] cx88[0]: Calling XC2028/3028 callback
[   33.822931] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   33.822935] cx88[0]: Calling XC2028/3028 callback
[   35.439061] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   35.464729] SCODE (20000000), id 000000000000b700:
[   35.464734] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   35.528010] cx88[0]: Calling XC2028/3028 callback
[   35.720040] cx88[0]: Calling XC2028/3028 callback
[   35.892016] cx88[0]: Calling XC2028/3028 callback
[   36.485523] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   47.648011] usb 8-2: device descriptor read/64, error -110
[   62.864012] usb 8-2: device descriptor read/64, error -110
[   63.080011] usb 8-2: new full speed USB device using uhci_hcd and address 4
[   73.488010] usb 8-2: device not accepting address 4, error -110
[   73.600011] usb 8-2: new full speed USB device using uhci_hcd and address 5
[   84.008512] usb 8-2: device not accepting address 5, error -110
[   84.008526] hub 8-0:1.0: unable to enumerate USB device on port 2
[   84.222131] CPU0 attaching NULL sched-domain.
[   84.222135] CPU1 attaching NULL sched-domain.
[   84.244200] CPU0 attaching sched-domain:
[   84.244203]  domain 0: span 0-1 level MC
[   84.244205]   groups: 0 1
[   84.244209] CPU1 attaching sched-domain:
[   84.244211]  domain 0: span 0-1 level MC
[   84.244212]   groups: 1 0
[   84.377413] cx88[0]: Calling XC2028/3028 callback
[   84.575836] xc2028 0-0061: Loading firmware for type=BASE FM (401), id 0000000000000000.
[   84.575841] cx88[0]: Calling XC2028/3028 callback
[   86.114388] xc2028 0-0061: Loading firmware for type=FM (400), id 0000000000000000.
[   86.148012] cx88[0]: Calling XC2028/3028 callback

Ok, I'm dead in the water and all I did was upgrade the kernel and now I can't use my tv tuner in 10.04 or 10.10.

Again its a KWorld 120 and I'm trying to run it in analog mode. I have blacklisted the digital side of the card as per the linux wiki located at [http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028](http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028) and the card worked until I added multiverse and upgraded kernels.

---

### Post by mpeg4codec on 2012-01-19
I have the same card with the same problem. Anyone ever get it to work?

---

### Post by gtippitt on 2012-05-10
Has anyone got this card working with current 12.04 LTS release.  I had it working with 10.04 just fine, but now it won't work.  The device is detected, but whenever I try to tune stations, all get nothing except errors in DMESG that repeated say:
 "cx88[0]: Calling XC2028/3028 callback" 

Any help please ...

---

### Post by GreenTaurus on 2013-01-03
For whatever reason support for this card was stripped from the kernel...

If you want to use it, you basically are stuck with 10.04 LTS

---

### Post by vertago1 on 2013-01-04
I was able to get the analog capture to work on kubuntu 12.10 using the instructions here: [http://linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://linuxtv.org/wiki/index.php/KWorld_ATSC_120)

Specifically:> 3. Set up the drivers
The aforementioned analog-versus-digital bug has an additional side effect, aside from the need for a reboot - the kernel will try to load all of the modules this card can use, causing the card to fail to work properly. In order to have more precise control of what modules get loaded, and exactly when, create a new file to blacklist the new modules, to keep them from being auto-loaded:```

  # nano /etc/modprobe.d/blacklist-misc

  blacklist cx8800
  blacklist cx8802
  blacklist cx88-alsa
  blacklist cx88-dvb
```
Save the file out. If so desired, reboot your system and do an lsmod, to verify that the drivers were successfully blacklisted.
Decide which mode you wish to use as the default: NTSC and the various analog sources, or digital/ATSC mode.
To make digital/ATSC the default (for Debian, Ubuntu, and similar):```

  # nano /etc/rc.local

  mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx88-dvb
  cp /root/blacklist-misc /etc/modprobe.d
```
Here, we move the blacklist file off to root's home directory to temporarily disable it (and to create a backup copy), load the modules, then put the blacklist back into place so that it works for the next reboot. Skipping the move commands will cause the modprobe command to fail in many systems.
To make Analog mode the default, do this instead:```

  # nano /etc/rc.local

  mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx8800
  modprobe cx88-alsa
  cp /root/blacklist-misc /etc/modprobe.d
```
If there is an "exit 0" or similar command in the script, be sure your changes precede it.

---

### Post by GreenTaurus on 2013-01-05
Just for the fun of it, I reinstalled this card in a Dual Xeon server running 10.04 and it works fine. When I try this same card on my 12.04 machine (that worked with the same card on 10.04) it fails. No rhyme or reason that I can find, just nothing.

I can't speak to 12.10 as I haven't upgraded and have little intention to do so. I tried to have my desktop bleeding edge and my server on the latest LTS for the longest time, now once it works I just leave it be.

---

