---
title: "cant find/connect to wireless"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by Hoffert88 on 2010-12-18
I have a HP Pavillion dv5000 laptop. I cannot find or connect to my home  network or any other wireless. I am running ubuntu 10.10.  im still  learning the ubuntu system so not to familiar with it. I was running  version 9.10 I believe it was and could connect just fine to any  wireless. i enable the driver and it doesnt help at all. i have checked  for updates but it dosent fix the problem.  there is a on/off button for the wireless and it is on. The driver i am  running now is the same one i was using in the previous version so i  dont know what else to do. please help.

---

### Post by Mosabama on 2010-12-18
can you post more info?

```

lsmod
ifconfig
dmesg | grep wl

```

---

### Post by Hoffert88 on 2010-12-18
_**dmesg**_

[    0.150284] NetLabel: Initializing
[    0.150286] NetLabel:  domain hash size = 128
[    0.150288] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.150303] NetLabel:  unlabeled traffic allowed by default
[    0.150365] Switching to clocksource tsc
[    0.159173] AppArmor: AppArmor Filesystem Enabled
[    0.159196] pnp: PnP ACPI init
[    0.159226] ACPI: bus type pnp registered
[    0.161376] pnp 00:09: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.181681] pnp: PnP ACPI: found 10 devices
[    0.181684] ACPI: ACPI bus type pnp unregistered
[    0.181688] PnPBIOS: Disabled by ACPI PNP
[    0.181702] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.181706] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.181710] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.181718] system 00:08: [io  0x1080] has been reserved
[    0.181722] system 00:08: [io  0x040b] has been reserved
[    0.181725] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.181728] system 00:08: [io  0x04d6] has been reserved
[    0.181732] system 00:08: [io  0x0870-0x087f] has been reserved
[    0.181735] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.181738] system 00:08: [io  0x0c14] has been reserved
[    0.181742] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.181745] system 00:08: [io  0x0c6c] has been reserved
[    0.181748] system 00:08: [io  0x0c6f] has been reserved
[    0.181751] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.181755] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.181758] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.181762] system 00:08: [io  0x8000-0x805f] has been reserved
[    0.181765] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.181769] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.181772] system 00:08: [io  0x0280-0x0293] has been reserved
[    0.181779] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.181783] system 00:09: [mem 0xfff80000-0xffffffff] has been reserved
[    0.218036] pci 0000:00:14.4: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.218041] pci 0000:01:05.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
[    0.218045] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.218049] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.218053] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
[    0.218058] pci 0000:00:01.0:   bridge window [mem 0xc8000000-0xcfffffff 64bit pref]
[    0.218063] pci 0000:00:05.0: PCI bridge to [bus 02-03]
[    0.218065] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.218069] pci 0000:00:05.0:   bridge window [mem disabled]
[    0.218072] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.218078] pci 0000:06:04.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.218082] pci 0000:06:04.0: BAR 16: assigned [mem 0x84000000-0x87ffffff]
[    0.218086] pci 0000:06:04.0: BAR 13: assigned [io  0xa400-0xa4ff]
[    0.218089] pci 0000:06:04.0: BAR 14: assigned [io  0xa800-0xa8ff]
[    0.218092] pci 0000:06:04.0: CardBus bridge to [bus 07-07]
[    0.218095] pci 0000:06:04.0:   bridge window [io  0xa400-0xa4ff]
[    0.218102] pci 0000:06:04.0:   bridge window [io  0xa800-0xa8ff]
[    0.218109] pci 0000:06:04.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.218116] pci 0000:06:04.0:   bridge window [mem 0x84000000-0x87ffffff]
[    0.218123] pci 0000:00:14.4: PCI bridge to [bus 06-08]
[    0.218127] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.218135] pci 0000:00:14.4:   bridge window [mem 0xc0200000-0xc02fffff]
[    0.218141] pci 0000:00:14.4:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.218161] pci 0000:00:05.0: setting latency timer to 64
[    0.218182]   alloc irq_desc for 20 on node -1
[    0.218185]   alloc kstat_irqs on node -1
[    0.218191] pci 0000:06:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.218200] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.218203] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.218206] pci_bus 0000:00: resource 6 [mem 0x80000000-0xffffffff]
[    0.218209] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.218212] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
[    0.218215] pci_bus 0000:01: resource 2 [mem 0xc8000000-0xcfffffff 64bit pref]
[    0.218219] pci_bus 0000:06: resource 0 [io  0xa000-0xafff]
[    0.218222] pci_bus 0000:06: resource 1 [mem 0xc0200000-0xc02fffff]
[    0.218225] pci_bus 0000:06: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.218228] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
[    0.218231] pci_bus 0000:06: resource 5 [mem 0x000a0000-0x000bffff]
[    0.218234] pci_bus 0000:06: resource 6 [mem 0x80000000-0xffffffff]
[    0.218237] pci_bus 0000:07: resource 0 [io  0xa400-0xa4ff]
[    0.218240] pci_bus 0000:07: resource 1 [io  0xa800-0xa8ff]
[    0.218243] pci_bus 0000:07: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.218246] pci_bus 0000:07: resource 3 [mem 0x84000000-0x87ffffff]
[    0.218293] NET: Registered protocol family 2
[    0.218362] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.218722] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.219720] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.220283] TCP: Hash tables configured (established 131072 bind 65536)
[    0.220286] TCP reno registered
[    0.220291] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.220317] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.220429] NET: Registered protocol family 1
[    0.220442] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.220450] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.220545] pci 0000:01:05.0: Boot video device
[    0.220571] PCI: CLS 32 bytes, default 64
[    0.220830] cpufreq-nforce2: No nForce2 chipset.
[    0.220867] Scanning for low memory corruption every 60 seconds
[    0.221070] audit: initializing netlink socket (disabled)
[    0.221082] type=2000 audit(1292468182.216:1): initialized
[    0.233639] Trying to unpack rootfs image as initramfs...
[    0.249730] highmem bounce pool size: 64 pages
[    0.249738] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.257779] VFS: Disk quotas dquot_6.5.2
[    0.257858] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.258552] fuse init (API version 7.14)
[    0.258647] msgmni has been set to 1683
[    0.266263] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.266269] io scheduler noop registered
[    0.266271] io scheduler deadline registered
[    0.266286] io scheduler cfq registered (default)
[    0.266431] pcieport 0000:00:05.0: setting latency timer to 64
[    0.266475] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.266504] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.272346] ACPI: AC Adapter [ACAD] (on-line)
[    0.272426] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.272480] ACPI: Lid Switch [LID]
[    0.272533] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.272538] ACPI: Power Button [PWRB]
[    0.272600] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.272604] ACPI: Power Button [PWRF]
[    0.272666] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input3
[    0.272670] ACPI: Sleep Button [SLPF]
[    0.272784] ACPI: acpi_idle registered with cpuidle
[    0.272819] Marking TSC unstable due to TSC halts in idle
[    0.280892] Switching to clocksource acpi_pm
[    0.304060] ACPI: Invalid active0 threshold
[    0.309437] thermal LNXTHERM:01: registered as thermal_zone0
[    0.309447] ACPI: Thermal Zone [THRM] (0 C)
[    0.309543] ERST: Table is not found!
[    0.309733] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.310108]   alloc irq_desc for 17 on node -1
[    0.310111]   alloc kstat_irqs on node -1
[    0.310120] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.310128] serial 0000:00:14.6: PCI INT B disabled
[    0.311490] brd: module loaded
[    0.312195] loop: module loaded
[    0.312442]   alloc irq_desc for 16 on node -1
[    0.312445]   alloc kstat_irqs on node -1
[    0.312450] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.312502] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.312899] Fixed MDIO Bus: probed
[    0.312944] PPP generic driver version 2.4.2
[    0.312986] tun: Universal TUN/TAP device driver, 1.6
[    0.312989] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.313072] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.313090]   alloc irq_desc for 19 on node -1
[    0.313092]   alloc kstat_irqs on node -1
[    0.313097] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.313120] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.313161] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.313229] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[    0.320468] isapnp: Scanning for PnP cards...
[    0.326029] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.326191] hub 1-0:1.0: USB hub found
[    0.326198] hub 1-0:1.0: 8 ports detected
[    0.326310] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.326332] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.326354] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.326399] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.326424] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[    0.388261] hub 2-0:1.0: USB hub found
[    0.388273] hub 2-0:1.0: 4 ports detected
[    0.388359] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.388386] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.388435] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.388465] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[    0.471922] hub 3-0:1.0: USB hub found
[    0.471933] hub 3-0:1.0: 4 ports detected
[    0.472197] ACPI: Battery Slot [BAT1] (battery present)
[    0.476058] uhci_hcd: USB Universal Host Controller Interface driver
[    0.476175] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.510760] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.510776] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.510963] mice: PS/2 mouse device common for all mice
[    0.515982] rtc_cmos 00:04: RTC can wake from S4
[    0.516048] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.516090] rtc0: alarms up to one month, 114 bytes nvram
[    0.516234] device-mapper: uevent: version 1.0.3
[    0.516369] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.522607] device-mapper: multipath: version 1.1.1 loaded
[    0.522612] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.522782] EISA: Probing bus 0 at eisa.0
[    0.522786] EISA: Cannot allocate resource for mainboard
[    0.522789] Cannot allocate resource for EISA slot 1
[    0.522792] Cannot allocate resource for EISA slot 2
[    0.522795] Cannot allocate resource for EISA slot 3
[    0.522797] Cannot allocate resource for EISA slot 4
[    0.522800] Cannot allocate resource for EISA slot 5
[    0.522803] Cannot allocate resource for EISA slot 6
[    0.522805] Cannot allocate resource for EISA slot 7
[    0.522808] Cannot allocate resource for EISA slot 8
[    0.522810] EISA: Detected 0 cards.
[    0.526908] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.528237] cpuidle: using governor ladder
[    0.528307] cpuidle: using governor menu
[    0.528631] TCP cubic registered
[    0.528775] NET: Registered protocol family 10
[    0.529182] lo: Disabled Privacy Extensions
[    0.529416] NET: Registered protocol family 17
[    0.529453] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-34 (1 cpu cores) (version 2.20.00)
[    0.538567] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[    0.538571] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[    0.538574] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[    0.538617] powernow-k8: ph2 null fid transition 0xa
[    0.538648] Using IPI No-Shortcut mode
[    0.538765] PM: Resume from disk failed.
[    0.538779] registered taskstats version 1
[    0.539068]   Magic number: 6:339:915
[    0.539195] rtc_cmos 00:04: setting system clock to 2010-12-16 02:56:23 UTC (1292468183)
[    0.539200] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.539203] EDD information not available.
[    0.889450] Freeing initrd memory: 10508k freed
[    0.987990] isapnp: No Plug & Play device found
[    0.988022] Freeing unused kernel memory: 684k freed
[    0.988867] Write protecting the kernel text: 4932k
[    0.988901] Write protecting the kernel read-only data: 1976k
[    1.006370] udev[65]: starting version 163
[    1.192144] scsi0 : pata_atiixp
[    1.247972] scsi1 : pata_atiixp
[    1.249275] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    1.249279] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    1.266497] sdhci: Secure Digital Host Controller Interface driver
[    1.266501] sdhci: Copyright(c) Pierre Ossman
[    1.267331] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.267355] 8139cp 0000:06:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.268115]   alloc irq_desc for 21 on node -1
[    1.268118]   alloc kstat_irqs on node -1
[    1.268127] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.288084] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.288097] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.288107] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.288116] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.328119] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[    1.413150] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4084N, KQ09, max MWDMA2
[    1.427332] ata1.00: ATA-8: WDC WD3200BEVE-00A0HT0, 11.01A11, max UDMA/100
[    1.427335] ata1.00: 625142448 sectors, multi 16: LBA48 
[    1.428597] ata2.00: configured for MWDMA2
[    1.437450] ata1.00: configured for UDMA/100
[    1.437566] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVE-0 11.0 PQ: 0 ANSI: 5
[    1.437730] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.438008] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.438059] sd 0:0:0:0: [sda] Write Protect is off
[    1.438063] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.438085] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.438230]  sda:
[    1.441693] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4084N KQ09 PQ: 0 ANSI: 5
[    1.445347]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.453669] Uniform CD-ROM driver Revision: 3.20
[    1.453968] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.454075] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.477441]  sda5 >
[    1.477969] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.483946]   alloc irq_desc for 23 on node -1
[    1.483949]   alloc kstat_irqs on node -1
[    1.483958] firewire_ohci 0000:06:04.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    1.489236] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.544108] firewire_ohci: Added fw-ohci device 0000:06:04.2, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.544281] sdhci-pci 0000:06:04.4: SDHCI controller found [104c:8034] (rev 0)
[    1.544305] sdhci-pci 0000:06:04.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.544386] Registered led device: mmc0::
[    1.544426] mmc0: SDHCI controller on PCI [0000:06:04.4] using PIO
[    1.544469] Registered led device: mmc1::
[    1.544502] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
[    1.544545] Registered led device: mmc2::
[    1.544577] mmc2: SDHCI controller on PCI [0000:06:04.4] using PIO
[    1.544791]   alloc irq_desc for 22 on node -1
[    1.544794]   alloc kstat_irqs on node -1
[    1.544801] 8139too 0000:06:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.546311] 8139too 0000:06:06.0: eth0: RealTek RTL8139 at 0xa000, 00:16:d4:34:18:e4, IRQ 22
[    1.728706] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.728713] EXT4-fs (sda1): write access will be enabled during recovery
[    2.044147] firewire_core: created device fw0: GUID 673f020092d2407d, S400
[    7.157164] EXT4-fs (sda1): orphan cleanup on readonly fs
[    7.157179] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804839
[    7.157311] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804823
[    7.259621] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804831
[    7.259638] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804830
[    7.259656] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804836
[    7.259672] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804843
[    7.259687] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804834
[    7.259703] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3804816
[    7.259721] EXT4-fs (sda1): 8 orphan inodes deleted
[    7.259725] EXT4-fs (sda1): recovery complete
[    7.808682] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    9.974815] Adding 6142972k swap on /dev/sda5.  Priority:-1 extents:1 across:6142972k 
[   10.980580] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.137385] udev[330]: starting version 163
[   12.439078] input: HP WMI hotkeys as /devices/virtual/input/input5
[   12.671608] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.733675] lp: driver loaded but no devices found
[   12.988638] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   13.436499] Linux agpgart interface v0.103
[   13.443280] acpi device:10: registered as cooling_device1
[   13.443438] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:0e/LNXVIDEO:00/input/input6
[   13.443501] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   13.500279] tifm_7xx1 0000:06:04.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   13.522507] cfg80211: Calling CRDA to update world regulatory domain
[   13.616217] [drm] Initialized drm 1.1.0 20060810
[   13.855514] yenta_cardbus 0000:06:04.0: CardBus bridge found [103c:30a4]
[   13.855541] yenta_cardbus 0000:06:04.0: Enabling burst memory read transactions
[   13.855549] yenta_cardbus 0000:06:04.0: Using INTVAL to route CSC interrupts to PCI
[   13.855552] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to ISA
[   13.855560] yenta_cardbus 0000:06:04.0: TI: mfunc 0x00a61b22, devctl 0x64
[   13.984230] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0
[   14.048424] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   14.084836] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   14.084842] yenta_cardbus 0000:06:04.0: Socket status: 30000006
[   14.084852] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [io  0xa000-0xafff]
[   14.084856] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: excluding 0xa000-0xa0ff 0xa400-0xa4ff 0xa800-0xa8ff
[   14.093408] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xc02fffff]
[   14.093412] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0200000-0xc02fffff: excluding 0xc0200000-0xc020ffff
[   14.093429] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   14.093433] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   14.662037] [drm] radeon defaulting to kernel modesetting.
[   14.662042] [drm] radeon kernel modesetting enabled.
[   14.662138] radeon 0000:01:05.0: power state changed by ACPI to D0
[   14.662148] radeon 0000:01:05.0: power state changed by ACPI to D0
[   14.662158] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.665257] [drm] initializing kernel modesetting (RS480 0x1002:0x5955).
[   14.665366] [drm] register mmio base: 0xC0100000
[   14.665369] [drm] register mmio size: 65536
[   14.665614] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   14.665665] [drm] Generation 2 PCI interface, using max accessible memory
[   14.665671] radeon 0000:01:05.0: VRAM: 128M 0x80000000 - 0x87FFFFFF (128M used)
[   14.665675] radeon 0000:01:05.0: GTT: 32M 0x7E000000 - 0x7FFFFFFF
[   14.665714] [drm] radeon: irq initialized.
[   14.666116] [drm] Detected VRAM RAM=128M, BAR=128M
[   14.666122] [drm] RAM width 128bits DDR
[   14.666229] [TTM] Zone  kernel: Available graphics memory: 436588 kiB.
[   14.666232] [TTM] Zone highmem: Available graphics memory: 1029808 kiB.
[   14.666234] [TTM] Initializing pool allocator.
[   14.666261] [drm] radeon: 128M of VRAM memory ready
[   14.666263] [drm] radeon: 32M of GTT memory ready.
[   14.666290] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   14.666817] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
[   14.667204] [drm] Loading R300 Microcode
[   14.690088] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   15.021759] [drm] radeon: ring at 0x000000007E000000
[   15.021782] [drm] ring test succeeded in 2 usecs
[   15.021957] [drm] radeon: ib pool ready.
[   15.023800] [drm] ib test succeeded in 0 usecs
[   15.023836] [drm] Default TV standard: NTSC
[   15.023838] [drm] 14.318180000 MHz TV ref clk
[   15.024116] [drm] Panel ID String: AUO                     
[   15.024119] [drm] Panel Size 1280x800
[   15.024182] [drm] Default TV standard: NTSC
[   15.024184] [drm] 14.318180000 MHz TV ref clk
[   15.024218] [drm] Radeon Display Connectors
[   15.024220] [drm] Connector 0:
[   15.024221] [drm]   VGA
[   15.024225] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   15.024227] [drm]   Encoders:
[   15.024229] [drm]     CRT1: INTERNAL_DAC2
[   15.024231] [drm] Connector 1:
[   15.024232] [drm]   LVDS
[   15.024235] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   15.024237] [drm]   Encoders:
[   15.024239] [drm]     LCD1: INTERNAL_LVDS
[   15.024241] [drm] Connector 2:
[   15.024243] [drm]   S-video
[   15.024244] [drm]   Encoders:
[   15.024246] [drm]     TV1: INTERNAL_DAC2
[   15.066936] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x280-0x297 0x370-0x377
[   15.069352] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x408-0x40f 0x4d0-0x4d7
[   15.070370] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x870-0x87f
[   15.071184] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   15.071975] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   15.076151] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   15.076455] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   15.076524] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.106604] [drm] radeon: power management initialized
[   15.184801] cfg80211: World regulatory domain updated:
[   15.184807]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.184811]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.184815]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.184818]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.184822]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.184825]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.211025] [drm] fb mappable at 0xC8040000
[   15.211029] [drm] vram apper at 0xC8000000
[   15.211031] [drm] size 4096000
[   15.211033] [drm] fb depth is 24
[   15.211035] [drm]    pitch is 5120
[   15.250964] Console: switching to colour frame buffer device 160x50
[   15.257159] fb0: radeondrmfb frame buffer device
[   15.257162] drm: registered panic notifier
[   15.257166] Slow work thread pool: Starting up
[   15.257219] Slow work thread pool: Ready
[   15.257228] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[   15.276158] phy0: Selected rate control algorithm 'minstrel'
[   15.276874] Registered led device: b43-phy0::radio
[   15.276955] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   15.371708] type=1400 audit(1292468198.330:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=491 comm="apparmor_parser"
[   15.372077] type=1400 audit(1292468198.330:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=491 comm="apparmor_parser"
[   15.372375] type=1400 audit(1292468198.330:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=491 comm="apparmor_parser"
[   16.743065] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   16.852127] MC'97 0 converters and GPIO not ready (0x1)
[   16.853134] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   19.131731] ppdev: user-space parallel port driver
[   20.570066] type=1400 audit(1292468203.526:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=850 comm="apparmor_parser"
[   20.573357] type=1400 audit(1292468203.530:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=851 comm="apparmor_parser"
[   20.573703] type=1400 audit(1292468203.530:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=851 comm="apparmor_parser"
[   20.573905] type=1400 audit(1292468203.530:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=851 comm="apparmor_parser"
[   21.158033] type=1400 audit(1292468204.114:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=852 comm="apparmor_parser"
[   21.163221] type=1400 audit(1292468204.118:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=852 comm="apparmor_parser"
[   21.166285] type=1400 audit(1292468204.122:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=852 comm="apparmor_parser"
[   21.288632] type=1400 audit(1292468204.246:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=855 comm="apparmor_parser"
[   21.289096] type=1400 audit(1292468204.246:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=855 comm="apparmor_parser"
[   21.460550] type=1400 audit(1292468204.418:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=920 comm="apparmor_parser"
[   21.581316] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   31.664022] eth0: no IPv6 routers present
[   37.161322] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[170208.442707] [drm:subconnector_show] *ERROR* Unable to find subconnector property
[170208.442788] [drm:select_subconnector_show] *ERROR* Unable to find select subconnector property
[170617.397098] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[170619.576767] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[170619.601088] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[170621.205319] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[170621.630761] type=1400 audit(1292638801.321:15): apparmor="DENIED" operation="open" parent=11663 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=11682 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[170631.320043] eth0: no IPv6 routers present

[U][B]ifconfig

[/B][/U]eth0      Link encap:Ethernet  HWaddr 00:16:d4:34:18:e4  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe34:18e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17125716 (17.1 MB)  TX bytes:3948455 (3.9 MB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35776 (35.7 KB)  TX bytes:35776 (35.7 KB)


[U][B]lsmod

[/B][/U][B]Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_atiixp             12426  2 
snd_atiixp_modem        9147  5 
snd_ac97_codec         99227  2 snd_atiixp,snd_atiixp_modem
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi            4588  0 
arc4                    1165  2 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
b43                   168681  0 
radeon                827837  3 
pcmcia                 35973  0 
joydev                  8735  0 
mac80211              231541  1 b43
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    56633  1 radeon
yenta_socket           21518  0 
snd                    49006  20 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         30168  1 radeon
drm                   168054  5 radeon,ttm,drm_kms_helper
pcmcia_rsrc            10566  1 yenta_socket
cfg80211              144470  2 b43,mac80211
tifm_7xx1               3766  0 
ati_agp                 5202  0 
soundcore                880  1 snd
k8temp                  3228  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
agpgart                32011  3 ttm,drm,ati_agp
video                  18712  0 
tifm_core               6089  1 tifm_7xx1
psmouse                59033  0 
serio_raw               4022  0 
i2c_piix4               8635  0 
i2c_algo_bit            5168  1 radeon
snd_page_alloc          7120  3 snd_atiixp,snd_atiixp_modem,snd_pcm
output                  1883  1 video
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
hp_wmi                  5223  0 
8139too                19581  0 
firewire_ohci          21106  0 
sdhci_pci               6339  0 
8139cp                 16934  0 
sdhci                  15890  1 sdhci_pci
ssb                    39288  1 b43
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
led_class               2633  2 b43,sdhci
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  2 
[/B]

---

### Post by Mosabama on 2010-12-18
from dmesg:

> [ 14.690088] b43-phy0: Broadcom 4318 WLAN found (core revision 9)

but I dont think there is a driver loaded.

did you activate the driver from:

System -> administration -> additional drivers ?

---

### Post by Hoffert88 on 2010-12-18
yes. i activated it and it says active and in use. iv tried restarting but that dosent work either. i reloaded 9.10 to see what driver came up and what one i was using on that version and they are the same.

---

### Post by TBABill on 2010-12-18
b43 168681 0

It is active. It's listed. But it's Broadcom. Can you type ```
sudo rfkill list
``` and see if you are hard or soft blocked. If either says YES, then ```
sudo rfkill unblock all
```

---

### Post by TBABill on 2010-12-18
Can you also give the output of ```
lspci
``` so we can see which version of b43 you need. There is the b43 and b43-legacy, and it depends on which one you have which driver you need (and firmware). [https://help.ubuntu.com/community/WifiDocs/Driver/b43](https://help.ubuntu.com/community/WifiDocs/Driver/b43)

---

### Post by Hoffert88 on 2010-12-19
Problem solved. it was soft blocked. unblocked it and all is working great. thank you TBABill and Mosabama for the help.

---

