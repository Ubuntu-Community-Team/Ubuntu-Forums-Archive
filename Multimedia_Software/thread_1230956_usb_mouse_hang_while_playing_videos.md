---
title: "usb mouse hang while playing videos"
date: 2009-08-04
forum: Multimedia Software
---

### Post by Pampanga on 2009-08-04
Hi Everyone,

Got a bit of a problem and hopefully someone out there can help me out.

Whenever I play youtube, totem, vlc or any type of multimedia videos, my usb mouse hang. The pointer just wont move at all until i restart or press reset. luckily keyboard work so i have to ctrl-alt-del to restart system...here is my dmesg taken after restart..

dmesg

[    0.721888] device-mapper: multipath: version 1.0.5 loaded
[    0.721892] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.722137] cpuidle: using governor ladder
[    0.722139] cpuidle: using governor menu
[    0.722499] TCP cubic registered
[    0.722618] NET: Registered protocol family 10
[    0.723008] lo: Disabled Privacy Extensions
[    0.723256] NET: Registered protocol family 17
[    0.723272] Bluetooth: L2CAP ver 2.13
[    0.723273] Bluetooth: L2CAP socket layer initialized
[    0.723275] Bluetooth: SCO (Voice Link) ver 0.6
[    0.723276] Bluetooth: SCO socket layer initialized
[    0.723304] Bluetooth: RFCOMM socket layer initialized
[    0.723308] Bluetooth: RFCOMM TTY layer initialized
[    0.723310] Bluetooth: RFCOMM ver 1.11
[    0.723363] powernow-k8: Found 1 AMD Phenom(tm) 9500 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    0.723377] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    0.723378] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    0.723624] PM: Resume from disk failed.
[    0.723634] registered taskstats version 1
[    0.723778]   Magic number: 5:105:512
[    0.723813] pci 0000:00:01.4: hash matches
[    0.723828] wmi pnp0c14:00: hash matches
[    0.723909] rtc_cmos 00:07: setting system clock to 2009-08-04 03:31:29 UTC (1249356689)
[    0.723912] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.723913] EDD information not available.
[    0.906028] ata3: SATA link down (SStatus 0 SControl 300)
[    0.906054] ata5: SATA link down (SStatus 0 SControl 300)
[    0.906066] ata6: SATA link down (SStatus 0 SControl 300)
[    1.058033] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.059265] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.060020] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.061221] ata1.00: ATAPI: ATAPI   iHES206   2, 6L0C, max UDMA/100
[    1.063447] ata1.00: configured for UDMA/100
[    1.066385] scsi 0:0:0:0: CD-ROM            ATAPI    iHES206   2      6L0C PQ: 0 ANSI: 5
[    1.073972] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.073975] Uniform CD-ROM driver Revision: 3.20
[    1.074045] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.074085] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.075747] ata4.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    1.075750] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.076664] ata4.00: configured for UDMA/133
[    1.086959] ata2.00: ATA-8: ST3500418AS, CC34, max UDMA/133
[    1.086962] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.126430] ata2.00: configured for UDMA/133
[    1.126488] scsi 1:0:0:0: Direct-Access     ATA      ST3500418AS      CC34 PQ: 0 ANSI: 5
[    1.126556] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.126597] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    1.126607] sd 1:0:0:0: [sda] Write Protect is off
[    1.126609] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.126626] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.126696]  sda:<5>scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    1.126839] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.126903] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    1.126914] sd 3:0:0:0: [sdb] Write Protect is off
[    1.126917] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.126932] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.127014]  sdb: sda1 sda2 < sdb1
[    1.141691] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.160600]  sda5 >
[    1.160715] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.160735] Freeing unused kernel memory: 500k freed
[    1.160905] Write protecting the kernel read-only data: 6828k
[    1.171147] usb 3-3: new low speed USB device using ohci_hcd and address 2
[    1.317580] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 16
[    1.317593] ohci1394 0000:01:09.0: PCI INT A -> Link[LNKD] -> GSI 16 (level, low) -> IRQ 16
[    1.320369] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.320855] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    1.320859] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.320864] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.372096] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4eff800-f4efffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.379205] usb 3-3: configuration #1 chosen from 1 choice
[    1.421193] usbcore: registered new interface driver hiddev
[    1.434355] input:   USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb3/3-3/3-3:1.0/input/input3
[    1.434449] generic-usb 0003:1241:1503.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:02.0-3/input0
[    1.459186] input:   USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb3/3-3/3-3:1.1/input/input4
[    1.459236] generic-usb 0003:1241:1503.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:02.0-3/input1
[    1.459251] usbcore: registered new interface driver usbhid
[    1.459254] usbhid: v2.6:USB HID core driver
[    1.643391] usb 3-5: new low speed USB device using ohci_hcd and address 3
[    1.834127] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:21:85:61:e5:56
[    1.834132] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
[    1.848235] usb 3-5: configuration #1 chosen from 1 choice
[    1.862392] input: Microsoft Microsoft&#65533; 2.4GHz Transceiver V1.0 as /devices/pci0000:00/0000:00:02.0/usb3/3-5/3-5:1.0/input/input5
[    1.862456] generic-usb 0003:045E:071D.0003: input,hidraw2: USB HID v1.11 Keyboard [Microsoft Microsoft&#65533; 2.4GHz Transceiver V1.0] on usb-0000:00:02.0-5/input0
[    1.933316] input: Microsoft Microsoft&#65533; 2.4GHz Transceiver V1.0 as /devices/pci0000:00/0000:00:02.0/usb3/3-5/3-5:1.1/input/input6
[    1.933395] generic-usb 0003:045E:071D.0004: input,hidraw3: USB HID v1.11 Mouse [Microsoft Microsoft&#65533; 2.4GHz Transceiver V1.0] on usb-0000:00:02.0-5/input1
[    2.644160] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00016a4ed5]
[    6.922691] EXT4-fs: INFO: recovery required on readonly filesystem.
[    6.922694] EXT4-fs: write access will be enabled during recovery.
[    6.933569] EXT4-fs: barriers enabled
[    6.963059] kjournald2 starting: pid 944, dev sda1:8, commit interval 5 seconds
[    6.963071] EXT4-fs: delayed allocation enabled
[    6.963073] EXT4-fs: file extents enabled
[    6.963600] EXT4-fs: mballoc enabled
[    6.963614] EXT4-fs: recovery complete.
[    6.964057] EXT4-fs: mounted filesystem sda1 with ordered data mode
[   10.257487] udev: starting version 141
[   10.667994] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.017042] nvidia: module license 'NVIDIA' taints kernel.
[   11.017047] Disabling lock debugging due to kernel taint
[   11.041320] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2d00
[   11.041335] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2e00
[   11.051166] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   11.220769] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.250797] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   11.251322] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   11.251327] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   11.251352] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.273941] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[   11.274414] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   11.274418] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   11.274425] nvidia 0000:02:00.0: setting latency timer to 64
[   11.274561] nvidia 0000:03:00.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[   11.274566] nvidia 0000:03:00.0: setting latency timer to 64
[   11.274681] nvidia 0000:04:00.0: enabling device (0000 -> 0003)
[   11.274686] nvidia 0000:04:00.0: PCI INT A -> Link[LN1A] -> GSI 18 (level, low) -> IRQ 18
[   11.274691] nvidia 0000:04:00.0: setting latency timer to 64
[   11.275092] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.29  Wed Jul 22 23:04:30 PDT 2009
[   11.318318] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   11.318897] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   11.318900] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   11.318902] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   11.497394] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   11.817271] lp: driver loaded but no devices found
[   12.425495] EXT4 FS on sda1, internal journal on sda1:8
[   13.126853] EXT4-fs: barriers enabled
[   13.126994] kjournald2 starting: pid 2267, dev sdb1:8, commit interval 5 seconds
[   13.127124] EXT4 FS on sdb1, internal journal on sdb1:8
[   13.127126] EXT4-fs: delayed allocation enabled
[   13.127128] EXT4-fs: file extents enabled
[   13.129370] EXT4-fs: mballoc enabled
[   13.129388] EXT4-fs: mounted filesystem sdb1 with ordered data mode
[   15.053717] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.053720] Bluetooth: BNEP filters: protocol multicast
[   15.076633] Bridge firewalling registered
[   16.189488] ppdev: user-space parallel port driver
[   20.225976] forcedeth 0000:00:0a.0: irq 28 for MSI/MSI-X
[   31.034023] eth0: no IPv6 routers present
[   44.482441] canberra-gtk-pl[3830]: segfault at 3a4 ip 00007fb11c9aa4c5 sp 00007fb111e7c270 error 6 in libvorbis.so.0.4.0[7fb11c990000+1f000]


Note that my mouse and keyboard are wireless but only the mouse becomes inoperable after a few minutes of video playback. I tried wired ones both ps2 and usb with same result...I see that theres an error on the last line about libvorbis.so but not sure if thats what causing the mouse to hang...anyone know what that is? Does anyone have suggestions i could try?

Thanks

[B]
Kernel 2.6.30.3-candela #1 SMP Wed Jul 29 16:29:47 EDT 2009 x86_64 GNU/Linux
Ubuntu 9.04 Jaunty 64-bit
Nvidia driver version 185.18.29[/B]

---

### Post by dajudge on 2009-10-10
I can 2nd that problem though I'm running Debian Squeeze (2.6.30-2-686) - but the interesting part is: I am also using a microsoft mouse - (intellipointer wireless killername something 2.0 or so) and while the HAL detects it nicely it doesn't work in X

I investigated a bit:
- other USB mouse works nicely
- X works with /dev/mice
- /dev/mice inputs data on both touchpad and noname-USB mouse, but not MS-USB mouse

I know it's not a debian forum here but since the problems are most likely related - you know ;-)

Any help or feedback would be greatly appreciated!

Thanks,
Alex

---

### Post by Pampanga on 2011-09-30
I know this is an old post but thought I should give an update...

As it turns out, lots of people has problems with these k/m combo where  two devices are controlled by a single usb transmitter. I have this  sneaking suspicion the usb port the dongle its hooked up to might be  underpowered causing the mouse to stop working. I could be wrong though.

In any event, I gave up on wireless keyboard/mouse combo from Micro$oft. Been trying to find a solution for this a while..but no dice. 

I'm a bit hesitant about dropping more dough on another wireless k/m, So I'm back to wired ps2 for both keyboard and mouse which saved me some extra usb ports for other devices.

CHEERS! ):P

---

