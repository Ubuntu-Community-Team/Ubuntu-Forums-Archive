---
title: "HP DV6 Wireless Suspend issue + Graphics card overheating"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by LazyHobbit on 2012-04-24
I'm using an Hp Pavilion DV6 with Ubuntu 12.04 LTS and the 3.2.0-23-generic x86_64

 

The issues:
1) On suspend, wifi locks out and repeatedly throws authentication screen
- After i finish this post i'll try the terminal wifi restart and post results
[Edit by OP: Tried a wifi restart and driver update but the restart didn't correct anything and the update failed with reference to var/key/jockey.log]

2) Graphics card is TREMENDOUSLY hot (upwards of 70C); not sure if i can have this solved too


I'm a complete beginner with Ubuntu, but i'm curious that if this does not have a solution; would it be wise for me to go back to windows regarding the graphics card issue (even though i'm not a fan of W7 OS)??


Here's an inclusive list from what all reports/terminal codes/etc i could produce.



```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09) 
 00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) 
 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 
 00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04) 
 00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) 
 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05) 
 00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) 
 00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) 
 00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5) 
 00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) 
 00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) 
 00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05) 
 00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) 
 00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05) 
 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series] 
 07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 
 0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 
 13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01) 
 19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) 
 

 dmesg
 [    1.219503] pci 0000:00:1c.3: setting latency timer to 64 
 [    1.219507] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7] 
 [    1.219509] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff] 
 [    1.219511] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff] 
 [    1.219513] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff] 
 [    1.219515] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff] 
 [    1.219517] pci_bus 0000:01: resource 1 [mem 0xc6500000-0xc74fffff] 
 [    1.219520] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref] 
 [    1.219522] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff] 
 [    1.219524] pci_bus 0000:07: resource 1 [mem 0xc5500000-0xc64fffff] 
 [    1.219526] pci_bus 0000:07: resource 2 [mem 0xc0400000-0xc13fffff 64bit pref] 
 [    1.219529] pci_bus 0000:0d: resource 0 [io  0x3000-0x3fff] 
 [    1.219531] pci_bus 0000:0d: resource 1 [mem 0xc4500000-0xc54fffff] 
 [    1.219533] pci_bus 0000:0d: resource 2 [mem 0xc1400000-0xc23fffff 64bit pref] 
 [    1.219535] pci_bus 0000:13: resource 0 [io  0x2000-0x2fff] 
 [    1.219537] pci_bus 0000:13: resource 1 [mem 0xc3500000-0xc44fffff] 
 [    1.219539] pci_bus 0000:13: resource 2 [mem 0xc2400000-0xc33fffff 64bit pref] 
 [    1.219541] pci_bus 0000:19: resource 1 [mem 0xc3400000-0xc34fffff] 
 [    1.219567] NET: Registered protocol family 2 
 [    1.219792] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes) 
 [    1.220720] TCP established hash table entries: 524288 (order: 11, 8388608 bytes) 
 [    1.222050] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
 [    1.222179] TCP: Hash tables configured (established 524288 bind 65536) 
 [    1.222180] TCP reno registered 
 [    1.222197] UDP hash table entries: 4096 (order: 5, 131072 bytes) 
 [    1.222233] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes) 
 [    1.222318] NET: Registered protocol family 1 
 [    1.222332] pci 0000:00:02.0: Boot video device 
 [    1.222346] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    1.237251] pci 0000:00:1a.0: PCI INT A disabled 
 [    1.237311] pci 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 [    1.253227] pci 0000:00:1d.0: PCI INT A disabled 
 [    1.253339] pci 0000:19:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
 [    1.265543] pci 0000:19:00.0: PCI INT A disabled 
 [    1.265550] PCI: CLS 64 bytes, default 64 
 [    1.265552] PCI-DMA: Using software bounce buffering for IO (SWIOTLB) 
 [    1.265554] Placing 64MB software IO TLB between ffff880098e34000 - ffff88009ce34000 
 [    1.265556] software IO TLB at phys 0x98e34000 - 0x9ce34000 
 [    1.265571] Simple Boot Flag at 0x44 set to 0x1 
 [    1.266155] audit: initializing netlink socket (disabled) 
 [    1.266168] type=2000 audit(1335251526.032:1): initialized 
 [    1.299138] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
 [    1.319495] VFS: Disk quotas dquot_6.5.2 
 [    1.319545] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
 [    1.319961] fuse init (API version 7.17) 
 [    1.320035] msgmni has been set to 15861 
 [    1.320344] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
 [    1.320368] io scheduler noop registered 
 [    1.320370] io scheduler deadline registered 
 [    1.320395] io scheduler cfq registered (default) 
 [    1.320481] pcieport 0000:00:01.0: setting latency timer to 64 
 [    1.320510] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X 
 [    1.320739] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
 [    1.320757] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
 [    1.320798] intel_idle: MWAIT substates: 0x21120 
 [    1.320800] intel_idle: v0.4 model 0x2A 
 [    1.320801] intel_idle: lapic_timer_reliable_states 0xffffffff 
 [    1.322471] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared 
 [    1.323476] ACPI: AC Adapter [AC] (on-line) 
 [    1.323552] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0D:00/input/input0 
 [    1.325194] ACPI: Lid Switch [LID] 
 [    1.325249] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1 
 [    1.325253] ACPI: Power Button [PWRB] 
 [    1.325285] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2 
 [    1.325287] ACPI: Power Button [PWRF] 
 [    1.339175] thermal LNXTHERM:00: registered as thermal_zone0 
 [    1.339182] ACPI: Thermal Zone [THRM] (44 C) 
 [    1.339218] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared 
 [    1.339226] ACPI: Battery Slot [BAT0] (battery present) 
 [    1.339245] ERST: Table is not found! 
 [    1.339247] GHES: HEST is not enabled! 
 [    1.339303] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled 
 [    1.377479] ACPI: Battery Slot [BAT0] (battery present) 
 [    1.513251] Linux agpgart interface v0.103 
 [    1.513327] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset 
 [    1.513436] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable 
 [    1.514742] agpgart-intel 0000:00:00.0: detected 32768K stolen memory 
 [    1.514861] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000 
 [    1.516102] brd: module loaded 
 [    1.516709] loop: module loaded 
 [    1.516815] ahci 0000:00:1f.2: version 3.0 
 [    1.516829] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
 [    1.516877] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X 
 [    1.532928] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x21 impl SATA mode 
 [    1.532937] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst  
 [    1.532948] ahci 0000:00:1f.2: setting latency timer to 64 
 [    1.541346] scsi0 : ahci 
 [    1.541418] scsi1 : ahci 
 [    1.541479] scsi2 : ahci 
 [    1.541539] scsi3 : ahci 
 [    1.541601] scsi4 : ahci 
 [    1.541662] scsi5 : ahci 
 [    1.541746] ata1: SATA max UDMA/133 abar m2048@0xc7508000 port 0xc7508100 irq 41 
 [    1.541748] ata2: DUMMY 
 [    1.541749] ata3: DUMMY 
 [    1.541751] ata4: DUMMY 
 [    1.541752] ata5: DUMMY 
 [    1.541755] ata6: SATA max UDMA/133 abar m2048@0xc7508000 port 0xc7508380 irq 41 
 [    1.542086] Fixed MDIO Bus: probed 
 [    1.542103] tun: Universal TUN/TAP device driver, 1.6 
 [    1.542105] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
 [    1.542144] PPP generic driver version 2.4.2 
 [    1.542231] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
 [    1.542245] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    1.542260] ehci_hcd 0000:00:1a.0: setting latency timer to 64 
 [    1.542263] ehci_hcd 0000:00:1a.0: EHCI Host Controller 
 [    1.542300] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1 
 [    1.542326] ehci_hcd 0000:00:1a.0: debug port 2 
 [    1.546212] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported 
 [    1.546226] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc750a000 
 [    1.560875] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00 
 [    1.561024] hub 1-0:1.0: USB hub found 
 [    1.561028] hub 1-0:1.0: 2 ports detected 
 [    1.561083] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 [    1.561097] ehci_hcd 0000:00:1d.0: setting latency timer to 64 
 [    1.561100] ehci_hcd 0000:00:1d.0: EHCI Host Controller 
 [    1.561141] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
 [    1.561161] ehci_hcd 0000:00:1d.0: debug port 2 
 [    1.565053] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported 
 [    1.565068] ehci_hcd 0000:00:1d.0: irq 20, io mem 0xc7509000 
 [    1.580853] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00 
 [    1.580987] hub 2-0:1.0: USB hub found 
 [    1.580990] hub 2-0:1.0: 2 ports detected 
 [    1.581043] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
 [    1.581052] uhci_hcd: USB Universal Host Controller Interface driver 
 [    1.581083] xhci_hcd 0000:19:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
 [    1.581103] xhci_hcd 0000:19:00.0: setting latency timer to 64 
 [    1.581109] xhci_hcd 0000:19:00.0: xHCI Host Controller 
 [    1.581145] xhci_hcd 0000:19:00.0: new USB bus registered, assigned bus number 3 
 [    1.581341] xhci_hcd 0000:19:00.0: irq 19, io mem 0xc3400000 
 [    1.581442] xhci_hcd 0000:19:00.0: irq 42 for MSI/MSI-X 
 [    1.581447] xhci_hcd 0000:19:00.0: irq 43 for MSI/MSI-X 
 [    1.581451] xhci_hcd 0000:19:00.0: irq 44 for MSI/MSI-X 
 [    1.581455] xhci_hcd 0000:19:00.0: irq 45 for MSI/MSI-X 
 [    1.581459] xhci_hcd 0000:19:00.0: irq 46 for MSI/MSI-X 
 [    1.581465] xhci_hcd 0000:19:00.0: irq 47 for MSI/MSI-X 
 [    1.581469] xhci_hcd 0000:19:00.0: irq 48 for MSI/MSI-X 
 [    1.581473] xhci_hcd 0000:19:00.0: irq 49 for MSI/MSI-X 
 [    1.581664] xHCI xhci_add_endpoint called for root hub 
 [    1.581666] xHCI xhci_check_bandwidth called for root hub 
 [    1.581686] hub 3-0:1.0: USB hub found 
 [    1.581694] hub 3-0:1.0: 2 ports detected 
 [    1.581747] xhci_hcd 0000:19:00.0: xHCI Host Controller 
 [    1.581781] xhci_hcd 0000:19:00.0: new USB bus registered, assigned bus number 4 
 [    1.584786] xHCI xhci_add_endpoint called for root hub 
 [    1.584787] xHCI xhci_check_bandwidth called for root hub 
 [    1.584807] hub 4-0:1.0: USB hub found 
 [    1.584833] hub 4-0:1.0: 2 ports detected 
 [    1.628878] usbcore: registered new interface driver libusual 
 [    1.628914] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
 [    1.636503] serio: i8042 KBD port at 0x60,0x64 irq 1 
 [    1.636509] serio: i8042 AUX port at 0x60,0x64 irq 12 
 [    1.636591] mousedev: PS/2 mouse device common for all mice 
 [    1.636735] rtc_cmos 00:06: RTC can wake from S4 
 [    1.636844] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0 
 [    1.636874] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs 
 [    1.636939] device-mapper: uevent: version 1.0.3 
 [    1.636993] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com 
 [    1.637209] cpuidle: using governor ladder 
 [    1.637526] cpuidle: using governor menu 
 [    1.637528] EFI Variables Facility v0.08 2004-May-17 
 [    1.637693] TCP cubic registered 
 [    1.637774] NET: Registered protocol family 10 
 [    1.638132] NET: Registered protocol family 17 
 [    1.638145] Registering the dns_resolver key type 
 [    1.638269] PM: Hibernation image not present or could not be loaded. 
 [    1.638278] registered taskstats version 1 
 [    1.652131] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3 
 [    1.654123]   Magic number: 8:698:218 
 [    1.654161] acpi device:3c: hash matches 
 [    1.654244] rtc_cmos 00:06: setting system clock to 2012-04-24 07:12:07 UTC (1335251527) 
 [    1.655631] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
 [    1.655632] EDD information not available. 
 [    1.860656] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
 [    1.863965] ata6.00: ATAPI: hp      DVD A  DS8A5LH, 1H68, max UDMA/100 
 [    1.865484] ata6.00: configured for UDMA/100 
 [    1.868615] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
 [    1.869107] ata1.00: ATA-8: TOSHIBA MK1059GSMP, GU001C, max UDMA/100 
 [    1.869110] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA 
 [    1.869656] ata1.00: configured for UDMA/100 
 [    1.869894] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1059GS GU00 PQ: 0 ANSI: 5 
 [    1.870103] sd 0:0:0:0: Attached scsi generic sg0 type 0 
 [    1.870137] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB) 
 [    1.870148] sd 0:0:0:0: [sda] 4096-byte physical blocks 
 [    1.870332] sd 0:0:0:0: [sda] Write Protect is off 
 [    1.870335] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
 [    1.870440] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
 [    1.872611] usb 1-1: new high-speed USB device number 2 using ehci_hcd 
 [    1.875882] scsi 5:0:0:0: CD-ROM            hp       DVD A  DS8A5LH   1H68 PQ: 0 ANSI: 5 
 [    1.881963] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray 
 [    1.881974] cdrom: Uniform CD-ROM driver Revision: 3.20 
 [    1.882192] sr 5:0:0:0: Attached scsi CD-ROM sr0 
 [    1.882355] sr 5:0:0:0: Attached scsi generic sg1 type 5 
 [    1.958096]  sda: sda1 sda2 sda3 sda4 
 [    1.959113] sd 0:0:0:0: [sda] Attached SCSI disk 
 [    1.960271] Freeing unused kernel memory: 920k freed 
 [    1.960351] Write protecting the kernel read-only data: 12288k 
 [    1.964173] Freeing unused kernel memory: 1608k freed 
 [    1.967060] Freeing unused kernel memory: 1196k freed 
 [    1.979769] udevd[124]: starting version 175 
 [    1.998134] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
 [    1.998157] r8169 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    1.998200] r8169 0000:07:00.0: setting latency timer to 64 
 [    1.998288] r8169 0000:07:00.0: irq 50 for MSI/MSI-X 
 [    1.998699] r8169 0000:07:00.0: eth0: RTL8168evl/8111evl at 0xffffc90000c7c000, 10:1f:74:1d:3c:24, XID 0c900800 IRQ 50 
 [    1.998702] r8169 0000:07:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko] 
 [    2.004936] hub 1-1:1.0: USB hub found 
 [    2.005020] hub 1-1:1.0: 6 ports detected 
 [    2.116378] usb 2-1: new high-speed USB device number 2 using ehci_hcd 
 [    2.248826] hub 2-1:1.0: USB hub found 
 [    2.248877] hub 2-1:1.0: 6 ports detected 
 [    2.264100] Refined TSC clocksource calibration: 2195.013 MHz. 
 [    2.264109] Switching to clocksource tsc 
 [    2.320229] usb 1-1.1: new full-speed USB device number 3 using ehci_hcd 
 [    2.484037] usb 1-1.2: new high-speed USB device number 4 using ehci_hcd 
 [    4.040199] EXT4-fs (loop0): INFO: recovery required on readonly filesystem 
 [    4.040202] EXT4-fs (loop0): write access will be enabled during recovery 
 [    4.968525] EXT4-fs (loop0): orphan cleanup on readonly fs 
 [    4.968532] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 796970 
 [    4.968572] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 796968 
 [    4.968600] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 796959 
 [    4.968609] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 797394 
 [    4.968617] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 797391 
 [    4.968626] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1574593 
 [    4.968655] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 797190 
 [    4.968684] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 797185 
 [    4.968707] EXT4-fs (loop0): 8 orphan inodes deleted 
 [    4.968709] EXT4-fs (loop0): recovery complete 
 [    6.139194] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null) 
 [   18.929823] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   18.968037] udevd[462]: starting version 175 
 [   18.978706] lp: driver loaded but no devices found 
 [   18.991510] hp_accel: laptop model unknown, using default axes configuration 
 [   19.002323] [drm] Initialized drm 1.1.0 20060810 
 [   19.006327] mei: module is from the staging directory, the quality is unknown, you have been warned. 
 [   19.006644] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [   19.006652] mei 0000:00:16.0: setting latency timer to 64 
 [   19.006718] mei 0000:00:16.0: irq 51 for MSI/MSI-X 
 [   19.007587] [drm] radeon defaulting to kernel modesetting. 
 [   19.007590] [drm] radeon kernel modesetting enabled. 
 [   19.007604] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle 
 [   19.007641] radeon 0000:01:00.0: enabling device (0000 -> 0003) 
 [   19.007647] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [   19.007653] radeon 0000:01:00.0: setting latency timer to 64 
 [   19.007844] [drm] initializing kernel modesetting (TURKS 0x1002:0x6740 0x103C:0x1657). 
 [   19.007882] [drm] register mmio base: 0xC6500000 
 [   19.007884] [drm] register mmio size: 131072 
 [   19.012095] cfg80211: Calling CRDA to update world regulatory domain 
 [   19.012590] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [   19.012594] i915 0000:00:02.0: setting latency timer to 64 
 [   19.013849] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned. 
 [   19.014687] Initializing Realtek PCIE storage driver... 
 [   19.014719] rts_pstor 0000:13:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
 [   19.014817] Resource length: 0x1000 
 [   19.014833] Original address: 0xc3500000, remapped address: 0xffffc900117cc000 
 [   19.014837] pci->irq = 18 
 [   19.014839] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18 
 [   19.014864] rts_pstor 0000:13:00.0: setting latency timer to 64 
 [   19.017008] Linux video capture interface: v2.00 
 [   19.017427] uvcvideo: Found UVC 1.00 device HP TrueVision HD (5986:02ac) 
 [   19.021401] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree: 
 [   19.021404] Copyright(c) 2003-2011 Intel Corporation 
 [   19.021445] iwlwifi 0000:0d:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [   19.021454] iwlwifi 0000:0d:00.0: setting latency timer to 64 
 [   19.021478] iwlwifi 0000:0d:00.0: pci_resource_len = 0x00002000 
 [   19.021480] iwlwifi 0000:0d:00.0: pci_resource_base = ffffc900117d0000 
 [   19.021482] iwlwifi 0000:0d:00.0: HW Revision ID = 0x0 
 [   19.021567] iwlwifi 0000:0d:00.0: irq 52 for MSI/MSI-X 
 [   19.021602] iwlwifi 0000:0d:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C 
 [   19.021673] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S 
 [   19.024188] input: HP TrueVision HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input4 
 [   19.024260] usbcore: registered new interface driver uvcvideo 
 [   19.024262] USB Video Class driver (1.1.1) 
 [   19.032725] type=1400 audit(1335276744.894:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=573 comm="apparmor_parser" 
 [   19.033077] type=1400 audit(1335276744.894:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=573 comm="apparmor_parser" 
 [   19.033278] type=1400 audit(1335276744.894:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=573 comm="apparmor_parser" 
 [   19.042764] iwlwifi 0000:0d:00.0: device EEPROM VER=0x15d, CALIB=0x6 
 [   19.042767] iwlwifi 0000:0d:00.0: Device SKU: 0X50 
 [   19.042768] iwlwifi 0000:0d:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3 
 [   19.042779] iwlwifi 0000:0d:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels 
 [   19.063430] cfg80211: World regulatory domain updated: 
 [   19.063432] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
 [   19.063434] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   19.063436] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
 [   19.063438] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
 [   19.063440] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   19.063441] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   19.217788] scsi6 : SCSI emulation for PCI-Express Mass Storage devices 
 [   19.218000] rts_pstor: waiting for device to settle before scanning 
 [   19.306202] iwlwifi 0000:0d:00.0: loaded firmware version 39.31.5.1 build 35138 
 [   19.306291] Registered led device: phy0-led 
 [   19.306319] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
 [   19.307944] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs' 
 [   19.334551] ip_tables: (C) 2000-2006 Netfilter Core Team 
 [   19.354558] nf_conntrack version 0.5.0 (16384 buckets, 65536 max) 
 [   19.371347] ip6_tables: (C) 2000-2006 Netfilter Core Team 
 [   19.841965] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400 
 [   19.886309] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5 
 [   20.060253] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k  
 [   20.216644] rts_pstor: device scan complete 
 [   20.216780] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS 
 [   20.216824] Bad LUN (0:1) 
 [   20.216912] Bad target number (1:0) 
 [   20.216996] Bad target number (2:0) 
 [   20.217078] Bad target number (3:0) 
 [   20.217160] Bad target number (4:0) 
 [   20.217242] Bad target number (5:0) 
 [   20.217347] Bad target number (6:0) 
 [   20.217436] Bad target number (7:0) 
 [   20.217584] sd 6:0:0:0: Attached scsi generic sg2 type 0 
 [   20.217717] sd 6:0:0:0: [sdb] Attached SCSI removable disk 
 [   20.341017] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro 
 [   20.367228] init: failsafe main process (879) killed by TERM signal 
 [   20.402526] type=1400 audit(1335276746.266:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=954 comm="apparmor_parser" 
 [   20.402575] type=1400 audit(1335276746.266:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=956 comm="apparmor_parser" 
 [   20.403037] type=1400 audit(1335276746.266:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=954 comm="apparmor_parser" 
 [   20.403102] type=1400 audit(1335276746.266:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=949 comm="apparmor_parser" 
 [   20.403301] type=1400 audit(1335276746.266:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=948 comm="apparmor_parser" 
 [   20.403610] type=1400 audit(1335276746.266:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=953 comm="apparmor_parser" 
 [   20.403864] type=1400 audit(1335276746.266:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=949 comm="apparmor_parser" 
 [   20.406405] ppdev: user-space parallel port driver 
 [   20.411049] Bluetooth: Core ver 2.16 
 [   20.411071] NET: Registered protocol family 31 
 [   20.411073] Bluetooth: HCI device and connection manager initialized 
 [   20.411076] Bluetooth: HCI socket layer initialized 
 [   20.411078] Bluetooth: L2CAP socket layer initialized 
 [   20.411084] Bluetooth: SCO socket layer initialized 
 [   20.416416] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
 [   20.416418] Bluetooth: BNEP filters: protocol multicast 
 [   20.429600] Bluetooth: RFCOMM TTY layer initialized 
 [   20.429604] Bluetooth: RFCOMM socket layer initialized 
 [   20.429605] Bluetooth: RFCOMM ver 1.11 
 [   20.476392] init: alsa-restore main process (1031) terminated with status 19 
 [   20.572980] r8169 0000:07:00.0: eth0: link down 
 [   20.573430] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   20.573698] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   20.575210] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S 
 [   20.639120] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S 
 [   20.648288] lis3lv02d: 8 bits 3DC sensor found 
 [   20.703615] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [   20.704300] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [   21.297709] ATOM BIOS: HP/Flex 
 [   21.297751] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used) 
 [   21.297753] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF 
 [   21.297760] mtrr: no more MTRRs available 
 [   21.297761] [drm] Detected VRAM RAM=1024M, BAR=256M 
 [   21.297762] [drm] RAM width 128bits DDR 
 [   21.297803] [TTM] Zone  kernel: Available graphics memory: 4062502 kiB. 
 [   21.297804] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB. 
 [   21.297806] [TTM] Initializing pool allocator. 
 [   21.297822] [drm] radeon: 1024M of VRAM memory ready 
 [   21.297824] [drm] radeon: 512M of GTT memory ready. 
 [   21.297831] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010). 
 [   21.297832] [drm] Driver supports precise vblank timestamp query. 
 [   21.297874] radeon 0000:01:00.0: irq 53 for MSI/MSI-X 
 [   21.297880] radeon 0000:01:00.0: radeon: using MSI. 
 [   21.297940] [drm] radeon: irq initialized. 
 [   21.297943] [drm] GART: num cpu pages 131072, num gpu pages 131072 
 [   21.298264] [drm] Loading TURKS Microcode 
 [   21.304723] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000). 
 [   21.304845] radeon 0000:01:00.0: WB enabled 
 [   21.321140] [drm] ring test succeeded in 3 usecs 
 [   21.321217] [drm] radeon: ib pool ready. 
 [   21.321336] [drm] ib test succeeded in 0 usecs 
 [   21.321485] [drm] Radeon Display Connectors 
 [   21.321500] [drm] Internal thermal controller with fan control 
 [   21.322657] [drm] radeon: power management initialized 
 [   21.322895] No connectors reported connected with modes 
 [   21.322897] [drm] Cannot find any crtc or sizes - going 1024x768 
 [   21.324476] [drm] fb mappable at 0xA0142000 
 [   21.324477] [drm] vram apper at 0xA0000000 
 [   21.324478] [drm] size 3145728 
 [   21.324479] [drm] fb depth is 24 
 [   21.324480] [drm]    pitch is 4096 
 [   21.324636] Console: switching to colour frame buffer device 128x48 
 [   21.324650] fb0: radeondrmfb frame buffer device 
 [   21.324651] drm: registered panic notifier 
 [   21.324655] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0 
 [   21.337920] init: plymouth-splash main process (1250) terminated with status 1 
 [   21.355938] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none 
 [   21.364293] mtrr: no more MTRRs available 
 [   21.364295] [drm] MTRR allocation failed.  Graphics performance may suffer. 
 [   21.364562] i915 0000:00:02.0: irq 54 for MSI/MSI-X 
 [   21.364565] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010). 
 [   21.364567] [drm] Driver supports precise vblank timestamp query. 
 [   21.365280] vga_switcheroo: enabled 
 [   21.365323] radeon atpx: version is 1 
 [   21.391128] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6 
 [   21.391271] Registered led device: hp::hddprotect 
 [   21.391287] hp_accel: driver loaded 
 [   21.391570] wmi: Mapper loaded 
 [   21.394093] input: HP WMI hotkeys as /devices/virtual/input/input7 
 [   21.926508] fbcon: inteldrmfb (fb1) is primary device 
 [   21.926511] fbcon: Remapping primary device, fb1, to tty 1-63 
 [   22.118526] fb1: inteldrmfb frame buffer device 
 [   22.118664] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS 
 [   22.235798] acpi device:2f: registered as cooling_device8 
 [   22.235962] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/LNXVIDEO:00/input/input8 
 [   22.236022] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no) 
 [   22.352286] acpi device:3c: registered as cooling_device9 
 [   22.352459] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9 
 [   22.352510] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no) 
 [   22.352561] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1 
 [   22.352619] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
 [   22.352696] snd_hda_intel 0000:00:1b.0: irq 55 for MSI/MSI-X 
 [   22.352729] snd_hda_intel 0000:00:1b.0: setting latency timer to 64 
 [   22.890298] wlan0: authenticate with 00:24:b2:6f:5b:ba (try 1) 
 [   22.893246] wlan0: authenticated 
 [   22.899667] wlan0: associate with 00:24:b2:6f:5b:ba (try 1) 
 [   22.903255] wlan0: RX AssocResp from 00:24:b2:6f:5b:ba (capab=0x411 status=0 aid=1) 
 [   22.903258] wlan0: associated 
 [   22.909337] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
 [   22.917961] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0 
 [   22.918024] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10 
 [   22.918115] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11 
 [   22.918193] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12 
 [   33.333836] wlan0: no IPv6 routers present 
 

 Network config
   *-network                
        description: Ethernet interface 
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:07:00.0 
        logical name: eth0 
        version: 06 
        serial: 10:1f:74:1d:3c:24 
        size: 10Mbit/s 
        capacity: 1Gbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
        resources: irq:50 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff 
   *-network 
        description: Wireless interface 
        product: Centrino Wireless-N 1000 
        vendor: Intel Corporation 
        physical id: 0 
        bus info: pci@0000:0d:00.0 
        logical name: wlan0 
        version: 00 
        serial: 74:e5:0b:2c:d0:c0 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=39.31.5.1 build 35138 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn 
        resources: irq:52 memory:c4500000-c4501fff

```

---

### Post by cmacia06 on 2012-04-24
This used to happen to my dv7. What i did is I edited one of the the files that is run when you come back from suspending it. I made a script. I forgot where the folder that holds this information is. Ill look for it and get back to you.

---

### Post by cmacia06 on 2012-04-24
Im new at using these forums so if i post something incorrectly sorry. OK I found the directory. 

Press ctrl+alt+t to open the terminal. Then type sudo gedit 

Make a file containing this in it.
[IMG]http://i45.tinypic.com/350a2xx.jpg[/IMG]

```

case "${1}" in
    resume|thaw)
        rmmod iwlwifi
	modprobe iwlwifi bt_coex_active=0
;;
esac

```

Then just save it to the folder "/etc/pm/sleep.d". Save it as a normal file with no extension. Name it what you like. Restart to make sure it all works. Suspend the resume and all should work.

---

### Post by LazyHobbit on 2012-04-25
@Cmacia - i've tried your suggestion and saved it as wifiresume .. Did a restart just in case; when it got back to the desktop i logged into wifi to check connection then went to suspend and now my router won't let me log in again.

I've restarted a few times to check but i think the file is causing an unannounced error. Thank you for the suggestion; i'm gonna look around for the command to remove the file and await further reply.

---

### Post by QIII on 2012-04-25
Is your card that hot at idle or under load?

Do you have the proprietary ATI driver installed?  (HD 7xxx series GPUs currently don't have a Linux driver, unless something has changed in the last week.).

---

### Post by LazyHobbit on 2012-04-25
I'm a complete noob at this stuff but i'll try to answer your questions as best as i can based off what i've read and can understand.

(Estimates) After resume it doesn't seem that hot; so i'm assuming only under load (no matter how minor the load). Takes roughly 5 minutes to get upwards of 80C (estimation as i don't know how to pull any information from the computer itself)

Proprietary driver = yes. i haven't changed anything (aside from all updates for windows 7).. Right now my ubuntu is a dualboot (not sure if that matters due to load in background??)
-- EDIT ** Also, the ATI in linux (driver) did not install correctly.. It dropped with an error in var/key/jockey.log.. Maybe if i was smart i should've mentioned that but it didn't dawn on me until now. I'll play fetch for a second and see if i can get that error log

---

### Post by LazyHobbit on 2012-04-25
Here's the log that i could find; keep in mind that this log was created while trying to install the ATI graphics card driver in Ubuntu 12.04

```
2012-04-24 08:03:28,226 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0>
2012-04-24 08:03:29,746 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-24 08:03:29,917 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-24 08:03:29,917 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-24 08:03:29,970 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-24 08:03:29,993 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-24 08:03:30,024 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-24 08:03:30,025 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-24 08:03:30,025 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-24 08:03:30,051 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-24 08:03:30,059 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-24 08:03:30,059 DEBUG: fglrx.available: falling back to default
2012-04-24 08:03:30,167 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 08:03:30,174 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 08:03:30,182 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-24 08:03:30,182 DEBUG: fglrx.available: falling back to default
2012-04-24 08:03:30,239 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-24 08:03:30,239 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-24 08:03:30,271 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-24 08:03:30,296 DEBUG: Software modem not available
2012-04-24 08:03:30,297 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-24 08:03:30,306 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-24 08:03:30,307 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-24 08:03:30,307 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-24 08:03:30,307 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-24 08:03:30,315 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-24 08:03:30,316 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-24 08:03:30,344 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-24 08:03:30,345 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-24 08:03:30,395 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-24 08:03:30,396 DEBUG: Firmware for DVB cards not available
2012-04-24 08:03:30,396 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-24 08:03:30,408 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-24 08:03:30,416 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-24 08:03:30,467 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-24 08:03:30,468 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-24 08:03:30,481 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-24 08:03:30,489 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-24 08:03:30,491 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,492 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:03:30,498 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 08:03:30,507 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-24 08:03:30,508 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,508 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:03:30,515 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 08:03:30,523 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-24 08:03:30,524 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,524 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:03:30,531 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-24 08:03:30,540 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-24 08:03:30,541 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,541 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:03:30,548 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-24 08:03:30,556 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-24 08:03:30,558 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,558 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:03:30,564 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-24 08:03:30,572 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-24 08:03:30,573 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,574 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:03:30,574 DEBUG: all custom handlers loaded
2012-04-24 08:03:30,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 08:03:30,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 08:03:30,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:30,659 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,659 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:30,659 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 08:03:30,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 08:03:30,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000103Csd00001657bc07sc80i00')
2012-04-24 08:03:30,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-24 08:03:30,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:dock')
2012-04-24 08:03:30,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 08:03:30,840 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-24 08:03:30,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,840 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-24 08:03:30,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 08:03:30,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-24 08:03:30,849 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:30,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,849 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:30,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-24 08:03:30,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 08:03:30,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-24 08:03:30,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-24 08:03:30,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-24 08:03:30,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00001002d00006740sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:03:31,044 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-24 08:03:31,067 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,068 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,044 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:03:31,074 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-24 08:03:31,082 DEBUG: fglrx.available: falling back to default
2012-04-24 08:03:31,137 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,138 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,113 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:03:31,138 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-24 08:03:31,163 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,164 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,139 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-24 08:03:31,170 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 08:03:31,178 DEBUG: fglrx.available: falling back to default
2012-04-24 08:03:31,230 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,231 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,207 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-24 08:03:31,231 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-24 08:03:31,232 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-24 08:03:31,240 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2012-04-24 08:03:31,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-24 08:03:31,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 08:03:31,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 08:03:31,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00000116sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:03:31,249 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-04-24 08:03:31,249 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00001657bc02sc00i00')
2012-04-24 08:03:31,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-04-24 08:03:31,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 08:03:31,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000103Csd00001657bc06sc01i00')
2012-04-24 08:03:31,261 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-24 08:03:31,261 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc02ip00')
2012-04-24 08:03:31,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 08:03:31,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 08:03:31,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-24 08:03:31,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:03:31,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-24 08:03:31,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:03:31,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-24 08:03:31,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 08:03:31,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1B:bd10/05/2011:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvr0589110014244710000620100:rvnHewlett-Packard:rn1657:rvr10.31:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-24 08:03:31,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 08:03:31,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000103Csd00001657bc01sc06i01')
2012-04-24 08:03:31,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-24 08:03:31,276 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,277 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:31,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-04-24 08:03:31,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:03:31,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v138Ap0018d0078dcFFdsc11dpFFicFFisc00ip00')
2012-04-24 08:03:31,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:03:31,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0003v5986p02ACe0924-e0,1,kD4,ramlsfw')
2012-04-24 08:03:31,279 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,279 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:31,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:SYN1E47:SYN1E00:SYN0002:PNP0F13:')
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-24 08:03:31,280 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-04-24 08:03:31,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-24 08:03:31,280 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:31,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc01ip00')
2012-04-24 08:03:31,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-24 08:03:31,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 08:03:31,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:regulatory')
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000103Csd00001657bc0Csc05i00')
2012-04-24 08:03:31,283 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-24 08:03:31,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000103Csd00001657bc04sc03i00')
2012-04-24 08:03:31,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 08:03:31,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 08:03:31,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00001033d00000194sv0000103Csd00001657bc0Csc03i30')
2012-04-24 08:03:31,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,292 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:31,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v000010ECd00005209sv0000103Csd00001657bcFFsc00i00')
2012-04-24 08:03:31,292 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2012-04-24 08:03:31,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000103Csd00001657bc07sc80i00')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:dock')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00001002d00006740sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00000116sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00001657bc02sc00i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000103Csd00001657bc06sc01i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc02ip00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1B:bd10/05/2011:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvr0589110014244710000620100:rvnHewlett-Packard:rn1657:rvr10.31:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000103Csd00001657bc01sc06i01')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v138Ap0018d0078dcFFdsc11dpFFicFFisc00ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0003v5986p02ACe0924-e0,1,kD4,ramlsfw')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:SYN1E47:SYN1E00:SYN0002:PNP0F13:')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc01ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:regulatory')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000103Csd00001657bc0Csc05i00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000103Csd00001657bc04sc03i00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00001033d00000194sv0000103Csd00001657bc0Csc03i30')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v000010ECd00005209sv0000103Csd00001657bcFFsc00i00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 08:03:31,371 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,371 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,409 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,409 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,444 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,445 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,497 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,498 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,532 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,532 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,587 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,588 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,658 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,659 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,710 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,711 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,744 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,745 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,797 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,798 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:38,607 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:38,608 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:42,807 DEBUG: Installing package: fglrx-updates
2012-04-24 08:03:43,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.000000
2012-04-24 08:03:43,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.000000
2012-04-24 08:03:43,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.000000
2012-04-24 08:03:43,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.000000
2012-04-24 08:03:44,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.001570
2012-04-24 08:03:44,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.015539
2012-04-24 08:03:45,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.035494
2012-04-24 08:03:45,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.045472
2012-04-24 08:03:46,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.055450
2012-04-24 08:03:46,782 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.071415
2012-04-24 08:03:47,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.087379
2012-04-24 08:03:47,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.095361
2012-04-24 08:03:47,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.100698
2012-04-24 08:03:47,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.100918
2012-04-24 08:03:48,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.104909
2012-04-24 08:03:48,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.108900
2012-04-24 08:03:49,315 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.114887
2012-04-24 08:03:49,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.124865
2012-04-24 08:03:50,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.134843
2012-04-24 08:03:50,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.144821
2012-04-24 08:03:51,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.154798
2012-04-24 08:03:51,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.156794
2012-04-24 08:03:52,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.166772
2012-04-24 08:03:52,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.168767
2012-04-24 08:03:53,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.168767
2012-04-24 08:03:53,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.170763
2012-04-24 08:03:54,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.174754
2012-04-24 08:03:54,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.174754
2012-04-24 08:03:55,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.174754
2012-04-24 08:03:55,833 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.178745
2012-04-24 08:03:56,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.182736
2012-04-24 08:03:56,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.184732
2012-04-24 08:03:57,337 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.186728
2012-04-24 08:03:57,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.190719
2012-04-24 08:03:58,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.196705
2012-04-24 08:03:58,841 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.202692
2012-04-24 08:03:59,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.212670
2012-04-24 08:03:59,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.218657
2012-04-24 08:04:00,345 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.224643
2012-04-24 08:04:00,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.232626
2012-04-24 08:04:01,348 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.240608
2012-04-24 08:04:01,849 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.248590
2012-04-24 08:04:02,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.254577
2012-04-24 08:04:02,852 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.260564
2012-04-24 08:04:03,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.268546
2012-04-24 08:04:03,855 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.278524
2012-04-24 08:04:04,356 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.294488
2012-04-24 08:04:04,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.318435
2012-04-24 08:04:05,359 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.324422
2012-04-24 08:04:05,860 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.334400
2012-04-24 08:04:06,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.334400
2012-04-24 08:04:06,863 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.334400
2012-04-24 08:04:07,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.336395
2012-04-24 08:04:07,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.338391
2012-04-24 08:04:08,367 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.338391
2012-04-24 08:04:08,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.338391
2012-04-24 08:04:09,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.338391
2012-04-24 08:04:09,871 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.340386
2012-04-24 08:04:10,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.340386
2012-04-24 08:04:10,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.342382
2012-04-24 08:04:11,375 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.344377
2012-04-24 08:04:11,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.348369
2012-04-24 08:04:12,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.354355
2012-04-24 08:04:12,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.366329
2012-04-24 08:04:13,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.374311
2012-04-24 08:04:13,882 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.384289
2012-04-24 08:04:14,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.394267
2012-04-24 08:04:14,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.410231
2012-04-24 08:04:15,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.418214
2012-04-24 08:04:15,888 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.424200
2012-04-24 08:04:16,389 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.440165
2012-04-24 08:04:16,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.452138
2012-04-24 08:04:17,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.464112
2012-04-24 08:04:17,893 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.474089
2012-04-24 08:04:18,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.484067
2012-04-24 08:04:18,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.494045
2012-04-24 08:04:19,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.504023
2012-04-24 08:04:19,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.517992
2012-04-24 08:04:20,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.539943
2012-04-24 08:04:20,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.573868
2012-04-24 08:04:21,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.597815
2012-04-24 08:04:21,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.605797
2012-04-24 08:04:22,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.609788
2012-04-24 08:04:22,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.615775
2012-04-24 08:04:23,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.623757
2012-04-24 08:04:23,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.629744
2012-04-24 08:04:24,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.637726
2012-04-24 08:04:24,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.647704
2012-04-24 08:04:25,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.657682
2012-04-24 08:04:25,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.669655
2012-04-24 08:04:26,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.683624
2012-04-24 08:04:26,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.693602
2012-04-24 08:04:27,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.707571
2012-04-24 08:04:27,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.723535
2012-04-24 08:04:28,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.739500
2012-04-24 08:04:28,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.753469
2012-04-24 08:04:29,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.769434
2012-04-24 08:04:29,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.775420
2012-04-24 08:04:30,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.779411
2012-04-24 08:04:30,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.785398
2012-04-24 08:04:31,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.801363
2012-04-24 08:04:31,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.813336
2012-04-24 08:04:32,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.829301
2012-04-24 08:04:32,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.845265
2012-04-24 08:04:33,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.859234
2012-04-24 08:04:33,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.871207
2012-04-24 08:04:34,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.877194
2012-04-24 08:04:34,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.885176
2012-04-24 08:04:35,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.903137
2012-04-24 08:04:35,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.919101
2012-04-24 08:04:36,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.935066
2012-04-24 08:04:36,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.957017
2012-04-24 08:04:37,447 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.970986
2012-04-24 08:04:37,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.984955
2012-04-24 08:04:38,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.000919
2012-04-24 08:04:38,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.016884
2012-04-24 08:04:39,451 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.036840
2012-04-24 08:04:39,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.066773
2012-04-24 08:04:40,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.100698
2012-04-24 08:04:40,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.126640
2012-04-24 08:04:41,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.158569
2012-04-24 08:04:41,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.192494
2012-04-24 08:04:42,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.228414
2012-04-24 08:04:42,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.254357
2012-04-24 08:04:43,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.276308
2012-04-24 08:04:43,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.286286
2012-04-24 08:04:44,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.312228
2012-04-24 08:04:44,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.318215
2012-04-24 08:04:45,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.326197
2012-04-24 08:04:45,969 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.338170
2012-04-24 08:04:46,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.354135
2012-04-24 08:04:46,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.374091
2012-04-24 08:04:47,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.382073
2012-04-24 08:04:47,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.392051
2012-04-24 08:04:48,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.404024
2012-04-24 08:04:48,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.425975
2012-04-24 08:04:49,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.447927
2012-04-24 08:04:49,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.463891
2012-04-24 08:04:50,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.483847
2012-04-24 08:04:50,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.499812
2012-04-24 08:04:51,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.517772
2012-04-24 08:04:51,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.525754
2012-04-24 08:04:52,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.535732
2012-04-24 08:04:52,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.549701
2012-04-24 08:04:53,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.565665
2012-04-24 08:04:53,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.599590
2012-04-24 08:04:54,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.609568
2012-04-24 08:04:54,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.619546
2012-04-24 08:04:55,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.631519
2012-04-24 08:04:55,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.645488
2012-04-24 08:04:56,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.663448
2012-04-24 08:04:56,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.677417
2012-04-24 08:04:57,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.717328
2012-04-24 08:04:58,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.733293
2012-04-24 08:04:58,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.755244
2012-04-24 08:04:59,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.759235
2012-04-24 08:04:59,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.789169
2012-04-24 08:05:00,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.799147
2012-04-24 08:05:00,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.815111
2012-04-24 08:05:01,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.835067
2012-04-24 08:05:01,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.845045
2012-04-24 08:05:02,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.855023
2012-04-24 08:05:02,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.865000
2012-04-24 08:05:03,014 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.878969
2012-04-24 08:05:03,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.892938
2012-04-24 08:05:04,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.906907
2012-04-24 08:05:04,519 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.918881
2012-04-24 08:05:05,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.928859
2012-04-24 08:05:05,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.932850
2012-04-24 08:05:06,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.938837
2012-04-24 08:05:06,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.948814
2012-04-24 08:05:07,025 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.962783
2012-04-24 08:05:07,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.976752
2012-04-24 08:05:08,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.990721
2012-04-24 08:05:08,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.004690
2012-04-24 08:05:09,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.028637
2012-04-24 08:05:09,532 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.048593
2012-04-24 08:05:10,033 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.064557
2012-04-24 08:05:10,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.072540
2012-04-24 08:05:11,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.074535
2012-04-24 08:05:11,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.076531
2012-04-24 08:05:12,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.080522
2012-04-24 08:05:12,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.086509
2012-04-24 08:05:13,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.096486
2012-04-24 08:05:13,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.102473
2012-04-24 08:05:14,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.110455
2012-04-24 08:05:14,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.118438
2012-04-24 08:05:15,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.134402
2012-04-24 08:05:15,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.150367
2012-04-24 08:05:16,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.170322
2012-04-24 08:05:16,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.196265
2012-04-24 08:05:17,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.234181
2012-04-24 08:05:17,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.244158
2012-04-24 08:05:18,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.254136
2012-04-24 08:05:18,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.274092
2012-04-24 08:05:19,058 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.312008
2012-04-24 08:05:19,559 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.329968
2012-04-24 08:05:20,061 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.345932
2012-04-24 08:05:20,562 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.359901
2012-04-24 08:05:21,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.391831
2012-04-24 08:05:21,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.421764
2012-04-24 08:05:22,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.439724
2012-04-24 08:05:22,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.445711
2012-04-24 08:05:23,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.457684
2012-04-24 08:05:23,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.465667
2012-04-24 08:05:24,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.471653
2012-04-24 08:05:24,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.487618
2012-04-24 08:05:25,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.501587
2012-04-24 08:05:25,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.515556
2012-04-24 08:05:26,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.529525
2012-04-24 08:05:26,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.547485
2012-04-24 08:05:27,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.563449
2012-04-24 08:05:27,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.585401
2012-04-24 08:05:28,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.611343
2012-04-24 08:05:28,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.621321
2012-04-24 08:05:29,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.633294
2012-04-24 08:05:29,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.657241
2012-04-24 08:05:30,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.683183
2012-04-24 08:05:30,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.711121
2012-04-24 08:05:31,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.741055
2012-04-24 08:05:31,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.774980
2012-04-24 08:05:32,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.812895
2012-04-24 08:05:32,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.844825
2012-04-24 08:05:33,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.874758
2012-04-24 08:05:33,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.922652
2012-04-24 08:05:34,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.954581
2012-04-24 08:05:34,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.984514
2012-04-24 08:05:35,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.010457
2012-04-24 08:05:35,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.020435
2012-04-24 08:05:36,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.030412
2012-04-24 08:05:36,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.046377
2012-04-24 08:05:37,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.068328
2012-04-24 08:05:37,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.104248
2012-04-24 08:05:38,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.128195
2012-04-24 08:05:38,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.156133
2012-04-24 08:05:39,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.180080
2012-04-24 08:05:39,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.202031
2012-04-24 08:05:40,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.208018
2012-04-24 08:05:40,615 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.216000
2012-04-24 08:05:41,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.227974
2012-04-24 08:05:41,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.243938
2012-04-24 08:05:42,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.271876
2012-04-24 08:05:42,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.301810
2012-04-24 08:05:43,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.329748
2012-04-24 08:05:43,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.357686
2012-04-24 08:05:44,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.377641
2012-04-24 08:05:44,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.401588
2012-04-24 08:05:45,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.423539
2012-04-24 08:05:45,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.447486
2012-04-24 08:05:46,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.473429
2012-04-24 08:05:46,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.537287
2012-04-24 08:05:47,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.607132
2012-04-24 08:05:47,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.621101
2012-04-24 08:05:48,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.625092
2012-04-24 08:05:48,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.629083
2012-04-24 08:05:49,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.637065
2012-04-24 08:05:49,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.645047
2012-04-24 08:05:50,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.651034
2012-04-24 08:05:50,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.657021
2012-04-24 08:05:51,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.666999
2012-04-24 08:05:51,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.676976
2012-04-24 08:05:52,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.684959
2012-04-24 08:05:52,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.694937
2012-04-24 08:05:53,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.706910
2012-04-24 08:05:53,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.728861
2012-04-24 08:05:54,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.746821
2012-04-24 08:05:54,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.784737
2012-04-24 08:05:55,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.838618
2012-04-24 08:05:55,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.876533
2012-04-24 08:05:56,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.938396
2012-04-24 08:05:56,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.018219
2012-04-24 08:05:57,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.068108
2012-04-24 08:05:57,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.108019
2012-04-24 08:05:58,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.161900
2012-04-24 08:05:58,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.235736
2012-04-24 08:05:59,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.315558
2012-04-24 08:05:59,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.401368
2012-04-24 08:06:00,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.449261
2012-04-24 08:06:00,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.509128
2012-04-24 08:06:01,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.574982
2012-04-24 08:06:01,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.640836
2012-04-24 08:06:02,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.700703
2012-04-24 08:06:02,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.710681
2012-04-24 08:06:03,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.762566
2012-04-24 08:06:03,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.794495
2012-04-24 08:06:04,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.810459
2012-04-24 08:06:04,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.832411
2012-04-24 08:06:05,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.850371
2012-04-24 08:06:05,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.874317
2012-04-24 08:06:06,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.894273
2012-04-24 08:06:06,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.914229
2012-04-24 08:06:07,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.958131
2012-04-24 08:06:07,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.984074
2012-04-24 08:06:08,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.016003
2012-04-24 08:06:08,690 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.043941
2012-04-24 08:06:09,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.083852
2012-04-24 08:06:09,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.117777
2012-04-24 08:06:10,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.163675
2012-04-24 08:06:10,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.231524
2012-04-24 08:06:11,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.307356
2012-04-24 08:06:11,698 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.407134
2012-04-24 08:06:12,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.467001
2012-04-24 08:06:12,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.540837
2012-04-24 08:06:13,202 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.616669
2012-04-24 08:06:13,703 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.642611
2012-04-24 08:06:14,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.660571
2012-04-24 08:06:14,706 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.680527
2012-04-24 08:06:15,207 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.696492
2012-04-24 08:06:15,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.726425
2012-04-24 08:06:16,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.752367
2012-04-24 08:06:16,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.778310
2012-04-24 08:06:17,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.786292
2012-04-24 08:06:17,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.798266
2012-04-24 08:06:18,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.816226
2012-04-24 08:06:18,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.820217
2012-04-24 08:06:19,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.832190
2012-04-24 08:06:19,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.836181
2012-04-24 08:06:20,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.840172
2012-04-24 08:06:20,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.840172
2012-04-24 08:06:21,223 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.842168
2012-04-24 08:06:21,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.844164
2012-04-24 08:06:22,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.844164
2012-04-24 08:06:22,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.848155
2012-04-24 08:06:23,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.854141
2012-04-24 08:06:23,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.860128
2012-04-24 08:06:24,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.860128
2012-04-24 08:06:24,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.872102
2012-04-24 08:06:25,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.878088
2012-04-24 08:06:25,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.882079
2012-04-24 08:06:26,237 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.888066
2012-04-24 08:06:26,738 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.894053
2012-04-24 08:06:27,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.900040
2012-04-24 08:06:27,741 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.908022
2012-04-24 08:06:28,242 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.921991
2012-04-24 08:06:28,744 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.935960
2012-04-24 08:06:29,245 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.949929
2012-04-24 08:06:29,746 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.967889
2012-04-24 08:06:30,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.993831
2012-04-24 08:06:30,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.009796
2012-04-24 08:06:31,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.025760
2012-04-24 08:06:31,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.041725
2012-04-24 08:06:32,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.061681
2012-04-24 08:06:32,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.071658
2012-04-24 08:06:33,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.087623
2012-04-24 08:06:33,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.103587
2012-04-24 08:06:34,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.119552
2012-04-24 08:06:34,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.135517
2012-04-24 08:06:35,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.151481
2012-04-24 08:06:35,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.167446
2012-04-24 08:06:36,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.177424
2012-04-24 08:06:36,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.185406
2012-04-24 08:06:37,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.199375
2012-04-24 08:06:37,768 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.215339
2012-04-24 08:06:38,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.231304
2012-04-24 08:06:38,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.251260
2012-04-24 08:06:39,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.273211
2012-04-24 08:06:39,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.295162
2012-04-24 08:06:40,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.313122
2012-04-24 08:06:40,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.353034
2012-04-24 08:06:41,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.380971
2012-04-24 08:06:41,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.410905
2012-04-24 08:06:42,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.440839
2012-04-24 08:06:42,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.484741
2012-04-24 08:06:43,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.498710
2012-04-24 08:06:43,794 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.512679
2012-04-24 08:06:44,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.536626
2012-04-24 08:06:44,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.572546
2012-04-24 08:06:45,297 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.600484
2012-04-24 08:06:45,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.662347
2012-04-24 08:06:46,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.724209
2012-04-24 08:06:46,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.772103
2012-04-24 08:06:47,303 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.819997
2012-04-24 08:06:47,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.839952
2012-04-24 08:06:48,306 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.861903
2012-04-24 08:06:48,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.895828
2012-04-24 08:06:49,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.933744
2012-04-24 08:06:49,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.973655
2012-04-24 08:06:50,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.007580
2012-04-24 08:06:50,813 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.055474
2012-04-24 08:06:51,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.081416
2012-04-24 08:06:51,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.109354
2012-04-24 08:06:52,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.157248
2012-04-24 08:06:52,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.195163
2012-04-24 08:06:53,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.235075
2012-04-24 08:06:53,821 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.255030
2012-04-24 08:06:54,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.268999
2012-04-24 08:06:54,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.276982
2012-04-24 08:06:55,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.286959
2012-04-24 08:06:55,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.296937
2012-04-24 08:06:56,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.308911
2012-04-24 08:06:56,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.322880
2012-04-24 08:06:57,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.338844
2012-04-24 08:06:57,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.362791
2012-04-24 08:06:58,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.388733
2012-04-24 08:06:58,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.416671
2012-04-24 08:06:59,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.456583
2012-04-24 08:06:59,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.532414
2012-04-24 08:07:00,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.598268
2012-04-24 08:07:00,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.688069
2012-04-24 08:07:01,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.799821
2012-04-24 08:07:01,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.941506
2012-04-24 08:07:02,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.993391
2012-04-24 08:07:02,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.087182
2012-04-24 08:07:03,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.182970
2012-04-24 08:07:03,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.340620
2012-04-24 08:07:04,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.464345
2012-04-24 08:07:04,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.568114
2012-04-24 08:07:05,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.619999
2012-04-24 08:07:05,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.699822
2012-04-24 08:07:06,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.741729
2012-04-24 08:07:06,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.747715
2012-04-24 08:07:07,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.821551
2012-04-24 08:07:07,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.869445
2012-04-24 08:07:08,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.907361
2012-04-24 08:07:08,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.949268
2012-04-24 08:07:09,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.973215
2012-04-24 08:07:09,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.001153
2012-04-24 08:07:10,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.025099
2012-04-24 08:07:10,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.059024
2012-04-24 08:07:11,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.102927
2012-04-24 08:07:11,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.144834
2012-04-24 08:07:12,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.168780
2012-04-24 08:07:12,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.186740
2012-04-24 08:07:13,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.200709
2012-04-24 08:07:13,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.218670
2012-04-24 08:07:14,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.228647
2012-04-24 08:07:14,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.236630
2012-04-24 08:07:15,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.254590
2012-04-24 08:07:15,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.278537
2012-04-24 08:07:16,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.296497
2012-04-24 08:07:16,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.304479
2012-04-24 08:07:17,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.314457
2012-04-24 08:07:17,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.328426
2012-04-24 08:07:18,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.340399
2012-04-24 08:07:18,888 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.354368
2012-04-24 08:07:19,389 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.368337
2012-04-24 08:07:19,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.400266
2012-04-24 08:07:20,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.418226
2012-04-24 08:07:20,893 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.448160
2012-04-24 08:07:21,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.486076
2012-04-24 08:07:21,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.506031
2012-04-24 08:07:22,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.521996
2012-04-24 08:07:22,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.539956
2012-04-24 08:07:23,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.561907
2012-04-24 08:07:23,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.597828
2012-04-24 08:07:24,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.635743
2012-04-24 08:07:24,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.651708
2012-04-24 08:07:25,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.657695
2012-04-24 08:07:25,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.665677
2012-04-24 08:07:26,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.671664
2012-04-24 08:07:26,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.671664
2012-04-24 08:07:27,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.671664
2012-04-24 08:07:27,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.673659
2012-04-24 08:07:28,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.675655
2012-04-24 08:07:28,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.675655
2012-04-24 08:07:29,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.683637
2012-04-24 08:07:29,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.687628
2012-04-24 08:07:30,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.687628
2012-04-24 08:07:30,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.699602
2012-04-24 08:07:31,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.705588
2012-04-24 08:07:31,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.713570
2012-04-24 08:07:32,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.721553
2012-04-24 08:07:32,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.729535
2012-04-24 08:07:33,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.737517
2012-04-24 08:07:33,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.755477
2012-04-24 08:07:34,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.765455
2012-04-24 08:07:34,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.777429
2012-04-24 08:07:35,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.791398
2012-04-24 08:07:35,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.809358
2012-04-24 08:07:36,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.827318
2012-04-24 08:07:36,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.837296
2012-04-24 08:07:37,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.847274
2012-04-24 08:07:37,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.877207
2012-04-24 08:07:38,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.901154
2012-04-24 08:07:38,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.927096
2012-04-24 08:07:39,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.953039
2012-04-24 08:07:39,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.965012
2012-04-24 08:07:40,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.969003
2012-04-24 08:07:40,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.970999
2012-04-24 08:07:41,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.970999
2012-04-24 08:07:41,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.972994
2012-04-24 08:07:42,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.976986
2012-04-24 08:07:42,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.982972
2012-04-24 08:07:43,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.986963
2012-04-24 08:07:43,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.992950
2012-04-24 08:07:44,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.000932
2012-04-24 08:07:44,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.008915
2012-04-24 08:07:45,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.018892
2012-04-24 08:07:45,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.022884
2012-04-24 08:07:46,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.028870
2012-04-24 08:07:46,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.034857
2012-04-24 08:07:47,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.042839
2012-04-24 08:07:47,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.054813
2012-04-24 08:07:48,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.074768
2012-04-24 08:07:48,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.086742
2012-04-24 08:07:49,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.098715
2012-04-24 08:07:49,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.116675
2012-04-24 08:07:50,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.132640
2012-04-24 08:07:50,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.152596
2012-04-24 08:07:51,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.178538
2012-04-24 08:07:51,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.206476
2012-04-24 08:07:52,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.248383
2012-04-24 08:07:52,978 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.256365
2012-04-24 08:07:53,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.258361
2012-04-24 08:07:53,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.262352
2012-04-24 08:07:54,482 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.262352
2012-04-24 08:07:54,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.264347
2012-04-24 08:07:55,485 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.264347
2012-04-24 08:07:55,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.266343
2012-04-24 08:07:56,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.270334
2012-04-24 08:07:56,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.272330
2012-04-24 08:07:57,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.274325
2012-04-24 08:07:57,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.278316
2012-04-24 08:07:58,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.284303
2012-04-24 08:07:58,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.296276
2012-04-24 08:07:59,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.304259
2012-04-24 08:07:59,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.314237
2012-04-24 08:08:00,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.322219
2012-04-24 08:08:01,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.328206
2012-04-24 08:08:01,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.338183
2012-04-24 08:08:02,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.350157
2012-04-24 08:08:02,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.362130
2012-04-24 08:08:03,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.382086
2012-04-24 08:08:03,507 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.398050
2012-04-24 08:08:04,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.410024
2012-04-24 08:08:04,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.423993
2012-04-24 08:08:05,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.441953
2012-04-24 08:08:05,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.449935
2012-04-24 08:08:06,014 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.477873
2012-04-24 08:08:06,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.491842
2012-04-24 08:08:07,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.501820
2012-04-24 08:08:07,518 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.511798
2012-04-24 08:08:08,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.535745
2012-04-24 08:08:08,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.545722
2012-04-24 08:08:09,022 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.561687
2012-04-24 08:08:09,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.583638
2012-04-24 08:08:10,025 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.611576
2012-04-24 08:08:10,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.647496
2012-04-24 08:08:11,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.693395
2012-04-24 08:08:11,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.749270
2012-04-24 08:08:12,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.801155
2012-04-24 08:08:12,532 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.861022
2012-04-24 08:08:13,033 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.034637
2012-04-24 08:08:13,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.138406
2012-04-24 08:08:14,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.210247
2012-04-24 08:08:14,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.242176
2012-04-24 08:08:15,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.278096
2012-04-24 08:08:15,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.333972
2012-04-24 08:08:16,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.335967
2012-04-24 08:08:16,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.365901
2012-04-24 08:08:17,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.381866
2012-04-24 08:08:17,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.393839
2012-04-24 08:08:18,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.411799
2012-04-24 08:08:18,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.421777
2012-04-24 08:08:19,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.435746
2012-04-24 08:08:19,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.449715
2012-04-24 08:08:20,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.457697
2012-04-24 08:08:20,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.461688
2012-04-24 08:08:21,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.465679
2012-04-24 08:08:21,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.471666
2012-04-24 08:08:22,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.473662
2012-04-24 08:08:22,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.475657
2012-04-24 08:08:23,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.479648
2012-04-24 08:08:23,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.479648
2012-04-24 08:08:24,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.481644
2012-04-24 08:08:24,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.483640
2012-04-24 08:08:25,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.483640
2012-04-24 08:08:25,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.487631
2012-04-24 08:08:26,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.493617
2012-04-24 08:08:26,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.497609
2012-04-24 08:08:27,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.499604
2012-04-24 08:08:27,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.499604
2012-04-24 08:08:28,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.499604
2012-04-24 08:08:28,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.503595
2012-04-24 08:08:29,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.507586
2012-04-24 08:08:29,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.513573
2012-04-24 08:08:30,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.519560
2012-04-24 08:08:30,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.521555
2012-04-24 08:08:31,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.523551
2012-04-24 08:08:31,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.527542
2012-04-24 08:08:32,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.533529
2012-04-24 08:08:32,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.539515
2012-04-24 08:08:33,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.545502
2012-04-24 08:08:33,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.549493
2012-04-24 08:08:34,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.567453
2012-04-24 08:08:34,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.581422
2012-04-24 08:08:35,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.599383
2012-04-24 08:08:35,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.619338
2012-04-24 08:08:36,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.647276
2012-04-24 08:08:36,597 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.653263
2012-04-24 08:08:37,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.661245
2012-04-24 08:08:37,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.673219
2012-04-24 08:08:38,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.685192
2012-04-24 08:08:38,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.693174
2012-04-24 08:08:39,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.703152
2012-04-24 08:08:39,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.727099
2012-04-24 08:08:40,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.727099
2012-04-24 08:08:40,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.747055
2012-04-24 08:08:41,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.757032
2012-04-24 08:08:41,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.767010
2012-04-24 08:08:42,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.778984
2012-04-24 08:08:42,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.790957
2012-04-24 08:08:43,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.804926
2012-04-24 08:08:43,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.824882
2012-04-24 08:08:44,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.838851
2012-04-24 08:08:44,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.860802
2012-04-24 08:08:45,121 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.884749
2012-04-24 08:08:45,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.912687
2012-04-24 08:08:46,124 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.944616
2012-04-24 08:08:46,625 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.988518
2012-04-24 08:08:47,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.026434
2012-04-24 08:08:47,628 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.048385
2012-04-24 08:08:48,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.082310
2012-04-24 08:08:48,631 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.124217
2012-04-24 08:08:49,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.170115
2012-04-24 08:08:49,633 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.239960
2012-04-24 08:08:50,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.241955
2012-04-24 08:08:50,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.339738
2012-04-24 08:08:51,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.383641
2012-04-24 08:08:51,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.419561
2012-04-24 08:08:52,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.469450
2012-04-24 08:08:52,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.521335
2012-04-24 08:08:53,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.573220
2012-04-24 08:08:53,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.607144
2012-04-24 08:08:54,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.627100
2012-04-24 08:08:54,647 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.639074
2012-04-24 08:08:55,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.645060
2012-04-24 08:08:55,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.649051
2012-04-24 08:08:56,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.659029
2012-04-24 08:08:56,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.669007
2012-04-24 08:08:57,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.680981
2012-04-24 08:08:57,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.690958
2012-04-24 08:08:58,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.700936
2012-04-24 08:08:58,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.714905
2012-04-24 08:08:59,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.728874
2012-04-24 08:08:59,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.742843
2012-04-24 08:09:00,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.750825
2012-04-24 08:09:00,663 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.760803
2012-04-24 08:09:01,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.782754
2012-04-24 08:09:01,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.804706
2012-04-24 08:09:02,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.824661
2012-04-24 08:09:02,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.842622
2012-04-24 08:09:03,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.852599
2012-04-24 08:09:03,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.860582
2012-04-24 08:09:04,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.872555
2012-04-24 08:09:04,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.886524
2012-04-24 08:09:05,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.906480
2012-04-24 08:09:05,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.932422
2012-04-24 08:09:06,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.948387
2012-04-24 08:09:06,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.968342
2012-04-24 08:09:07,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.986302
2012-04-24 08:09:07,683 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.006258
2012-04-24 08:09:08,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.016236
2012-04-24 08:09:08,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.026214
2012-04-24 08:09:09,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.044174
2012-04-24 08:09:09,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.064130
2012-04-24 08:09:10,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.082090
2012-04-24 08:09:10,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.090072
2012-04-24 08:09:11,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.100050
2012-04-24 08:09:11,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.116014
2012-04-24 08:09:12,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.133975
2012-04-24 08:09:12,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.151935
2012-04-24 08:09:13,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.155926
2012-04-24 08:09:13,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.157921
2012-04-24 08:09:14,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.159917
2012-04-24 08:09:14,703 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.163908
2012-04-24 08:09:15,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.169895
2012-04-24 08:09:15,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.175881
2012-04-24 08:09:16,207 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.185859
2012-04-24 08:09:16,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.193842
2012-04-24 08:09:17,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.195837
2012-04-24 08:09:17,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.197833
2012-04-24 08:09:18,212 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.201824
2012-04-24 08:09:18,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.207811
2012-04-24 08:09:19,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.213797
2012-04-24 08:09:19,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.215793
2012-04-24 08:09:20,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.217788
2012-04-24 08:09:20,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.217788
2012-04-24 08:09:21,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.221780
2012-04-24 08:09:21,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.233753
2012-04-24 08:09:22,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.241735
2012-04-24 08:09:22,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.251713
2012-04-24 08:09:23,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.259695
2012-04-24 08:09:23,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.269673
2012-04-24 08:09:24,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.279651
2012-04-24 08:09:24,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.287633
2012-04-24 08:09:25,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.293620
2012-04-24 08:09:25,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.299607
2012-04-24 08:09:26,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.303598
2012-04-24 08:09:26,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.307589
2012-04-24 08:09:27,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.313576
2012-04-24 08:09:27,738 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.315571
2012-04-24 08:09:28,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.315571
2012-04-24 08:09:28,741 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.319562
2012-04-24 08:09:29,242 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.325549
2012-04-24 08:09:29,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.331536
2012-04-24 08:09:30,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.339518
2012-04-24 08:09:30,746 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.351491
2012-04-24 08:09:31,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.373443
2012-04-24 08:09:31,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.393398
2012-04-24 08:09:32,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.401381
2012-04-24 08:09:32,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.413354
2012-04-24 08:09:33,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.427323
2012-04-24 08:09:33,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.445283
2012-04-24 08:09:34,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.467234
2012-04-24 08:09:34,756 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.467234
2012-04-24 08:09:35,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.469230
2012-04-24 08:09:35,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.471226
2012-04-24 08:09:36,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.475217
2012-04-24 08:09:36,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.481203
2012-04-24 08:09:37,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.491181
2012-04-24 08:09:37,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.503155
2012-04-24 08:09:38,266 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.521115
2012-04-24 08:09:38,768 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.539075
2012-04-24 08:09:39,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.559031
2012-04-24 08:09:39,770 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.580982
2012-04-24 08:09:40,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.602933
2012-04-24 08:09:40,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.644840
2012-04-24 08:09:41,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.666791
2012-04-24 08:09:41,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.694729
2012-04-24 08:09:42,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.716680
2012-04-24 08:09:42,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.752601
2012-04-24 08:09:43,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.766570
2012-04-24 08:09:43,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.820450
2012-04-24 08:09:44,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.838410
2012-04-24 08:09:44,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.866348
2012-04-24 08:09:45,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.896282
2012-04-24 08:09:45,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.914242
2012-04-24 08:09:46,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.944175
2012-04-24 08:09:46,790 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.966126
2012-04-24 08:09:47,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.990073
2012-04-24 08:09:47,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.018011
2012-04-24 08:09:48,294 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.051936
2012-04-24 08:09:48,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.087856
2012-04-24 08:09:49,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.137745
2012-04-24 08:09:49,798 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.169674
2012-04-24 08:09:50,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.189630
2012-04-24 08:09:50,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.249497
2012-04-24 08:09:51,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.309364
2012-04-24 08:09:51,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.357258
2012-04-24 08:09:52,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.399165
2012-04-24 08:09:52,806 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.413134
2012-04-24 08:09:53,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.435085
2012-04-24 08:09:53,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.451050
2012-04-24 08:09:54,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.455041
2012-04-24 08:09:54,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.457036
2012-04-24 08:09:55,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.459032
2012-04-24 08:09:55,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.463023
2012-04-24 08:09:56,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.474996
2012-04-24 08:09:56,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.480983
2012-04-24 08:09:57,319 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.486970
2012-04-24 08:09:57,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.494952
2012-04-24 08:09:58,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.506925
2012-04-24 08:09:58,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.522890
2012-04-24 08:09:59,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.536859
2012-04-24 08:09:59,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.556815
2012-04-24 08:10:00,328 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.574775
2012-04-24 08:10:00,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.592735
2012-04-24 08:10:01,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.604708
2012-04-24 08:10:01,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.632646
2012-04-24 08:10:02,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.642624
2012-04-24 08:10:02,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.654598
2012-04-24 08:10:03,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.672558
2012-04-24 08:10:03,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.688522
2012-04-24 08:10:04,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.704487
2012-04-24 08:10:04,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.724442
2012-04-24 08:10:05,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.740407
2012-04-24 08:10:05,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.764354
2012-04-24 08:10:06,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.800274
2012-04-24 08:10:06,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.824221
2012-04-24 08:10:07,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.832203
2012-04-24 08:10:07,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.842181
2012-04-24 08:10:08,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.854154
2012-04-24 08:10:08,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.876106
2012-04-24 08:10:09,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.902048
2012-04-24 08:10:09,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.929986
2012-04-24 08:10:10,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.953933
2012-04-24 08:10:10,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.977880
2012-04-24 08:10:11,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.001826
2012-04-24 08:10:11,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.019787
2012-04-24 08:10:12,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.029764
2012-04-24 08:10:12,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.063689
2012-04-24 08:10:13,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.083645
2012-04-24 08:10:13,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.095618
2012-04-24 08:10:14,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.111583
2012-04-24 08:10:14,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.127547
2012-04-24 08:10:15,369 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.151494
2012-04-24 08:10:15,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.173445
2012-04-24 08:10:16,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.177436
2012-04-24 08:10:16,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.181428
2012-04-24 08:10:17,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.187414
2012-04-24 08:10:17,876 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.189410
2012-04-24 08:10:18,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.191405
2012-04-24 08:10:18,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.195397
2012-04-24 08:10:19,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.195397
2012-04-24 08:10:19,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.195397
2012-04-24 08:10:20,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.197392
2012-04-24 08:10:20,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.199388
2012-04-24 08:10:21,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.199388
2012-04-24 08:10:21,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.203379
2012-04-24 08:10:22,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.213357
2012-04-24 08:10:22,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.219343
2012-04-24 08:10:23,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.225330
2012-04-24 08:10:23,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.231317
2012-04-24 08:10:24,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.239299
2012-04-24 08:10:24,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.251272
2012-04-24 08:10:25,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.267237
2012-04-24 08:10:25,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.287193
2012-04-24 08:10:26,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.307148
2012-04-24 08:10:26,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.333091
2012-04-24 08:10:27,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.351051
2012-04-24 08:10:27,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.371007
2012-04-24 08:10:28,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.396949
2012-04-24 08:10:28,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.410918
2012-04-24 08:10:29,406 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.416905
2012-04-24 08:10:29,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.428878
2012-04-24 08:10:30,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.446838
2012-04-24 08:10:30,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.462803
2012-04-24 08:10:31,412 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.472781
2012-04-24 08:10:31,913 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.488745
2012-04-24 08:10:32,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.504710
2012-04-24 08:10:32,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.520674
2012-04-24 08:10:33,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.538634
2012-04-24 08:10:33,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.542625
2012-04-24 08:10:34,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.570563
2012-04-24 08:10:34,921 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.586528
2012-04-24 08:10:35,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.606484
2012-04-24 08:10:35,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.628435
2012-04-24 08:10:36,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.638413
2012-04-24 08:10:36,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.648391
2012-04-24 08:10:37,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.652382
2012-04-24 08:10:37,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.652382
2012-04-24 08:10:38,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.652382
2012-04-24 08:10:38,932 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.654377
2012-04-24 08:10:39,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.656373
2012-04-24 08:10:39,935 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.660364
2012-04-24 08:10:40,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.666351
2012-04-24 08:10:40,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.670342
2012-04-24 08:10:41,439 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.672337
2012-04-24 08:10:41,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.674333
2012-04-24 08:10:42,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.678324
2012-04-24 08:10:42,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.684311
2012-04-24 08:10:43,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.694289
2012-04-24 08:10:43,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.700275
2012-04-24 08:10:44,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.704266
2012-04-24 08:10:44,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.706262
2012-04-24 08:10:45,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.708258
2012-04-24 08:10:45,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.712249
2012-04-24 08:10:46,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.718235
2012-04-24 08:10:46,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.724222
2012-04-24 08:10:47,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.730209
2012-04-24 08:10:47,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.736196
2012-04-24 08:10:48,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.742182
2012-04-24 08:10:48,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.754156
2012-04-24 08:10:49,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.770120
2012-04-24 08:10:49,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.780098
2012-04-24 08:10:50,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.792071
2012-04-24 08:10:50,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.798058
2012-04-24 08:10:51,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.810032
2012-04-24 08:10:51,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.816018
2012-04-24 08:10:52,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.820009
2012-04-24 08:10:52,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.827992
2012-04-24 08:10:53,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.829987
2012-04-24 08:10:53,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.829987
2012-04-24 08:10:54,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.831983
2012-04-24 08:10:54,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.835974
2012-04-24 08:10:55,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.841961
2012-04-24 08:10:55,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.845952
2012-04-24 08:10:56,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.851938
2012-04-24 08:10:56,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.859921
2012-04-24 08:10:57,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.869899
2012-04-24 08:10:57,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.879876
2012-04-24 08:10:58,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.891850
2012-04-24 08:10:58,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.905819
2012-04-24 08:10:59,485 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.925775
2012-04-24 08:10:59,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.953712
2012-04-24 08:11:00,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.989633
2012-04-24 08:11:00,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.067460
2012-04-24 08:11:01,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.131318
2012-04-24 08:11:01,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.191185
2012-04-24 08:11:02,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.207150
2012-04-24 08:11:02,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.332870
2012-04-24 08:11:03,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.400720
2012-04-24 08:11:03,997 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.476551
2012-04-24 08:11:04,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.526441
2012-04-24 08:11:05,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.562361
2012-04-24 08:11:05,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.602272
2012-04-24 08:11:06,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.688082
2012-04-24 08:11:06,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.745953
2012-04-24 08:11:07,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.803825
2012-04-24 08:11:07,507 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.871674
2012-04-24 08:11:08,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.917572
2012-04-24 08:11:08,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.975443
2012-04-24 08:11:09,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.041297
2012-04-24 08:11:09,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.073226
2012-04-24 08:11:10,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.103160
2012-04-24 08:11:10,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.125111
2012-04-24 08:11:11,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.151053
2012-04-24 08:11:11,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.180987
2012-04-24 08:11:12,018 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.202938
2012-04-24 08:11:12,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.222894
2012-04-24 08:11:13,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.228881
2012-04-24 08:11:13,522 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.234867
2012-04-24 08:11:14,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.240854
2012-04-24 08:11:14,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.256819
2012-04-24 08:11:15,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.278770
2012-04-24 08:11:15,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.304712
2012-04-24 08:11:16,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.330655
2012-04-24 08:11:16,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.356597
2012-04-24 08:11:17,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.380544
2012-04-24 08:11:17,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.410477
2012-04-24 08:11:18,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.432429
2012-04-24 08:11:18,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.442406
2012-04-24 08:11:19,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.464358
2012-04-24 08:11:19,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.500278
2012-04-24 08:11:20,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.514247
2012-04-24 08:11:20,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.552163
2012-04-24 08:11:21,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.574114
2012-04-24 08:11:21,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.598061
2012-04-24 08:11:22,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.622008
2012-04-24 08:11:22,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.645954
2012-04-24 08:11:23,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.657928
2012-04-24 08:11:23,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.659923
2012-04-24 08:11:24,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.661919
2012-04-24 08:11:24,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.663914
2012-04-24 08:11:25,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.667906
2012-04-24 08:11:25,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.673892
2012-04-24 08:11:26,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.679879
2012-04-24 08:11:26,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.685866
2012-04-24 08:11:27,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.697839
2012-04-24 08:11:27,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.701830
2012-04-24 08:11:28,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.713804
2012-04-24 08:11:28,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.719790
2012-04-24 08:11:29,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.737750
2012-04-24 08:11:29,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.755711
2012-04-24 08:11:30,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.773671
2012-04-24 08:11:30,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.785644
2012-04-24 08:11:31,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.801609
2012-04-24 08:11:31,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.823560
2012-04-24 08:11:32,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.847507
2012-04-24 08:11:32,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.879436
2012-04-24 08:11:33,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.903383
2012-04-24 08:11:33,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.927329
2012-04-24 08:11:34,079 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.939303
2012-04-24 08:11:34,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.949281
2012-04-24 08:11:35,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.959259
2012-04-24 08:11:35,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.975223
2012-04-24 08:11:36,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.997174
2012-04-24 08:11:36,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.021121
2012-04-24 08:11:37,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.031099
2012-04-24 08:11:37,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.043072
2012-04-24 08:11:38,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.053050
2012-04-24 08:11:38,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.069015
2012-04-24 08:11:39,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.090966
2012-04-24 08:11:39,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.114913
2012-04-24 08:11:40,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.136864
2012-04-24 08:11:40,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.158815
2012-04-24 08:11:41,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.178771
2012-04-24 08:11:41,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.200722
2012-04-24 08:11:42,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.226665
2012-04-24 08:11:42,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.236643
2012-04-24 08:11:43,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.246620
2012-04-24 08:11:43,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.262585
2012-04-24 08:11:44,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.272563
2012-04-24 08:11:44,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.284536
2012-04-24 08:11:45,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.294514
2012-04-24 08:11:45,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.308483
2012-04-24 08:11:46,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.322452
2012-04-24 08:11:46,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.338417
2012-04-24 08:11:47,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.352386
2012-04-24 08:11:47,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.382319
2012-04-24 08:11:48,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.398284
2012-04-24 08:11:48,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.416244
2012-04-24 08:11:49,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.442186
2012-04-24 08:11:49,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.450168
2012-04-24 08:11:50,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.460146
2012-04-24 08:11:50,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.476111
2012-04-24 08:11:51,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.498062
2012-04-24 08:11:51,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.522009
2012-04-24 08:11:52,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.543960
2012-04-24 08:11:52,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.571898
2012-04-24 08:11:53,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.591854
2012-04-24 08:11:53,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.615801
2012-04-24 08:11:54,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.635756
2012-04-24 08:11:54,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.677663
2012-04-24 08:11:55,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.707597
2012-04-24 08:11:55,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.733539
2012-04-24 08:11:56,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.779437
2012-04-24 08:11:56,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.835313
2012-04-24 08:11:57,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.901167
2012-04-24 08:11:57,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.988972
2012-04-24 08:11:58,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.072786
2012-04-24 08:11:58,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.196511
2012-04-24 08:11:59,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.226444
2012-04-24 08:11:59,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.400059
2012-04-24 08:12:00,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.521789
2012-04-24 08:12:00,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.623563
2012-04-24 08:12:01,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.695403
2012-04-24 08:12:01,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.789195
2012-04-24 08:12:02,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.878995
2012-04-24 08:12:02,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.962809
2012-04-24 08:12:03,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.002720
2012-04-24 08:12:03,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.046623
2012-04-24 08:12:04,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.092521
2012-04-24 08:12:04,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.166357
2012-04-24 08:12:05,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.182322
2012-04-24 08:12:05,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.226224
2012-04-24 08:12:06,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.234206
2012-04-24 08:12:06,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.308042
2012-04-24 08:12:07,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.351945
2012-04-24 08:12:07,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.373896
2012-04-24 08:12:08,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.397843
2012-04-24 08:12:08,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.435759
2012-04-24 08:12:09,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.469683
2012-04-24 08:12:09,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.497621
2012-04-24 08:12:10,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.531546
2012-04-24 08:12:10,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.547511
2012-04-24 08:12:11,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.571457
2012-04-24 08:12:11,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.599395
2012-04-24 08:12:12,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.611369
2012-04-24 08:12:12,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.617356
2012-04-24 08:12:13,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.629329
2012-04-24 08:12:13,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.643298
2012-04-24 08:12:14,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.687200
2012-04-24 08:12:14,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.711147
2012-04-24 08:12:15,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.733098
2012-04-24 08:12:15,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.755050
2012-04-24 08:12:16,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.777001
2012-04-24 08:12:16,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.802943
2012-04-24 08:12:17,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.830881
2012-04-24 08:12:17,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.860815
2012-04-24 08:12:18,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.902722
2012-04-24 08:12:18,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.920682
2012-04-24 08:12:19,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.946624
2012-04-24 08:12:19,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.964584
2012-04-24 08:12:20,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.996513
2012-04-24 08:12:20,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.054385
2012-04-24 08:12:21,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.108265
2012-04-24 08:12:21,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.154163
2012-04-24 08:12:22,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.182101
2012-04-24 08:12:22,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.243964
2012-04-24 08:12:23,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.315804
2012-04-24 08:12:23,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.361702
2012-04-24 08:12:24,212 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.413587
2012-04-24 08:12:24,713 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.457490
2012-04-24 08:12:25,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.521348
2012-04-24 08:12:25,716 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.533321
2012-04-24 08:12:26,217 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.567246
2012-04-24 08:12:26,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.587202
2012-04-24 08:12:27,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.605162
2012-04-24 08:12:27,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.631104
2012-04-24 08:12:28,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.659042
2012-04-24 08:12:28,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.677002
2012-04-24 08:12:29,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.682989
2012-04-24 08:12:29,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.682989
2012-04-24 08:12:30,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.700949
2012-04-24 08:12:30,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.708931
2012-04-24 08:12:31,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.716914
2012-04-24 08:12:31,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.724896
2012-04-24 08:12:32,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.734874
2012-04-24 08:12:32,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.740860
2012-04-24 08:12:33,235 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.748843
2012-04-24 08:12:33,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.758821
2012-04-24 08:12:34,237 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.770794
2012-04-24 08:12:34,739 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.780772
2012-04-24 08:12:35,240 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.784763
2012-04-24 08:12:35,741 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.788754
2012-04-24 08:12:36,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.794741
2012-04-24 08:12:36,744 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.804719
2012-04-24 08:12:37,245 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.808710
2012-04-24 08:12:37,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.810705
2012-04-24 08:12:38,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.812701
2012-04-24 08:12:38,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.816692
2012-04-24 08:12:39,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.816692
2012-04-24 08:12:39,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.818688
2012-04-24 08:12:40,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.818688
2012-04-24 08:12:40,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.820683
2012-04-24 08:12:41,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.824674
2012-04-24 08:12:41,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.830661
2012-04-24 08:12:42,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.836648
2012-04-24 08:12:42,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.842634
2012-04-24 08:12:43,262 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.850617
2012-04-24 08:12:43,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.860595
2012-04-24 08:12:44,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.876559
2012-04-24 08:12:44,766 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.896515
2012-04-24 08:12:45,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.918466
2012-04-24 08:12:45,768 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.946404
2012-04-24 08:12:46,270 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.966360
2012-04-24 08:12:46,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.990306
2012-04-24 08:12:47,273 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.990306
2012-04-24 08:12:47,774 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.990306
2012-04-24 08:12:48,276 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.026227
2012-04-24 08:12:48,777 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.034209
2012-04-24 08:12:49,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.052169
2012-04-24 08:12:49,780 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.052169
2012-04-24 08:12:50,281 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.062147
2012-04-24 08:12:50,782 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.072125
2012-04-24 08:12:51,284 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.080107
2012-04-24 08:12:51,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.086094
2012-04-24 08:12:52,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.096072
2012-04-24 08:12:52,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.096072
2012-04-24 08:12:53,289 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.108045
2012-04-24 08:12:53,791 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.114032
2012-04-24 08:12:54,292 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.120018
2012-04-24 08:12:54,793 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.129996
2012-04-24 08:12:55,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.133987
2012-04-24 08:12:55,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.147956
2012-04-24 08:12:56,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.157934
2012-04-24 08:12:56,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.169908
2012-04-24 08:12:57,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.185872
2012-04-24 08:12:57,802 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.201837
2012-04-24 08:12:58,303 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.227779
2012-04-24 08:12:58,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.259708
2012-04-24 08:12:59,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.301615
2012-04-24 08:12:59,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.349509
2012-04-24 08:13:00,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.369464
2012-04-24 08:13:00,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.399398
2012-04-24 08:13:01,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.439309
2012-04-24 08:13:01,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.471238
2012-04-24 08:13:02,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.519132
2012-04-24 08:13:02,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.559043
2012-04-24 08:13:03,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.602946
2012-04-24 08:13:03,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.640862
2012-04-24 08:13:04,319 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.694742
2012-04-24 08:13:04,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.748622
2012-04-24 08:13:05,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.782547
2012-04-24 08:13:05,823 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.794520
2012-04-24 08:13:06,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.812481
2012-04-24 08:13:06,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.836427
2012-04-24 08:13:07,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.876339
2012-04-24 08:13:07,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.920241
2012-04-24 08:13:08,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.940197
2012-04-24 08:13:08,830 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.952170
2012-04-24 08:13:09,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.970130
2012-04-24 08:13:09,833 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.998068
2012-04-24 08:13:10,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.033989
2012-04-24 08:13:10,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.037980
2012-04-24 08:13:11,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.043967
2012-04-24 08:13:11,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.059931
2012-04-24 08:13:12,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.067913
2012-04-24 08:13:12,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.087869
2012-04-24 08:13:13,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.115807
2012-04-24 08:13:13,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.135763
2012-04-24 08:13:14,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.151727
2012-04-24 08:13:14,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.167692
2012-04-24 08:13:15,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.167692
2012-04-24 08:13:15,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.185652
2012-04-24 08:13:16,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.213590
2012-04-24 08:13:16,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.247514
2012-04-24 08:13:17,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.269466
2012-04-24 08:13:17,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.289421
2012-04-24 08:13:18,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.303390
2012-04-24 08:13:18,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.325342
2012-04-24 08:13:19,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.333324
2012-04-24 08:13:19,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.351284
2012-04-24 08:13:20,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.363257
2012-04-24 08:13:20,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.385209
2012-04-24 08:13:21,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.413147
2012-04-24 08:13:21,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.445076
2012-04-24 08:13:22,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.482992
2012-04-24 08:13:22,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.516916
2012-04-24 08:13:23,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.550841
2012-04-24 08:13:23,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.572792
2012-04-24 08:13:24,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.606717
2012-04-24 08:13:24,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.652615
2012-04-24 08:13:25,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.710486
2012-04-24 08:13:25,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.768358
2012-04-24 08:13:26,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.822238
2012-04-24 08:13:26,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.894079
2012-04-24 08:13:27,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.906052
2012-04-24 08:13:27,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.011817
2012-04-24 08:13:28,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.053724
2012-04-24 08:13:28,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.101618
2012-04-24 08:13:29,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.169467
2012-04-24 08:13:29,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.235321
2012-04-24 08:13:30,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.253281
2012-04-24 08:13:30,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.321130
2012-04-24 08:13:31,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.365033
2012-04-24 08:13:31,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.414922
2012-04-24 08:13:32,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.478780
2012-04-24 08:13:32,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.534656
2012-04-24 08:13:33,399 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.558603
2012-04-24 08:13:33,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.626452
2012-04-24 08:13:34,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.646408
2012-04-24 08:13:34,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.684324
2012-04-24 08:13:35,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.734213
2012-04-24 08:13:35,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.758160
2012-04-24 08:13:36,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.810044
2012-04-24 08:13:36,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.843969
2012-04-24 08:13:37,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.863925
2012-04-24 08:13:37,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.907827
2012-04-24 08:13:38,412 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.929779
2012-04-24 08:13:38,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.975677
2012-04-24 08:13:39,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.013592
2012-04-24 08:13:39,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.061486
2012-04-24 08:13:40,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.109380
2012-04-24 08:13:40,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.157273
2012-04-24 08:13:41,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.205167
2012-04-24 08:13:41,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.257052
2012-04-24 08:13:42,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.298959
2012-04-24 08:13:42,925 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.322905
2012-04-24 08:13:43,426 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.334879
2012-04-24 08:13:43,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.354835
2012-04-24 08:13:44,429 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.388759
2012-04-24 08:13:44,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.430666
2012-04-24 08:13:45,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.468582
2012-04-24 08:13:45,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.498515
2012-04-24 08:13:46,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.526453
2012-04-24 08:13:46,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.564369
2012-04-24 08:13:47,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.606276
2012-04-24 08:13:47,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.642196
2012-04-24 08:13:48,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.686099
2012-04-24 08:13:48,941 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.708050
2012-04-24 08:13:49,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.751953
2012-04-24 08:13:49,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.809824
2012-04-24 08:13:50,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.861709
2012-04-24 08:13:50,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.889647
2012-04-24 08:13:51,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.937541
2012-04-24 08:13:51,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.973461
2012-04-24 08:13:52,451 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.993416
2012-04-24 08:13:52,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.047297
2012-04-24 08:13:53,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.087208
2012-04-24 08:13:53,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.121133
2012-04-24 08:13:54,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.149071
2012-04-24 08:13:54,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.208938
2012-04-24 08:13:55,459 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.270800
2012-04-24 08:13:55,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.312707
2012-04-24 08:13:56,462 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.346632
2012-04-24 08:13:56,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.404503
2012-04-24 08:13:57,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.446410
2012-04-24 08:13:57,966 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.480335
2012-04-24 08:13:58,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.538207
2012-04-24 08:13:58,969 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.600069
2012-04-24 08:13:59,470 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.641976
2012-04-24 08:13:59,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.671910
2012-04-24 08:14:00,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.715812
2012-04-24 08:14:00,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.767697
2012-04-24 08:14:01,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.823573
2012-04-24 08:14:01,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.865480
2012-04-24 08:14:02,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.929338
2012-04-24 08:14:02,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.973240
2012-04-24 08:14:03,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.019139
2012-04-24 08:14:03,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.082997
2012-04-24 08:14:04,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.148850
2012-04-24 08:14:04,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.198740
2012-04-24 08:14:05,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.270580
2012-04-24 08:14:05,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.288540
2012-04-24 08:14:06,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.310491
2012-04-24 08:14:06,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.332443
2012-04-24 08:14:07,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.388319
2012-04-24 08:14:07,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.424239
2012-04-24 08:14:08,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.462155
2012-04-24 08:14:08,997 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.462155
2012-04-24 08:14:09,498 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.500070
2012-04-24 08:14:09,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.532000
2012-04-24 08:14:10,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.557942
2012-04-24 08:14:11,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.589871
2012-04-24 08:14:11,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.623796
2012-04-24 08:14:12,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.641756
2012-04-24 08:14:12,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.655725
2012-04-24 08:14:13,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.697632
2012-04-24 08:14:13,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.749516
2012-04-24 08:14:14,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.777454
2012-04-24 08:14:14,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.809384
2012-04-24 08:14:15,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.837321
2012-04-24 08:14:15,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.865259
2012-04-24 08:14:16,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.877233
2012-04-24 08:14:16,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.917144
2012-04-24 08:14:17,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.931113
2012-04-24 08:14:17,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.945082
2012-04-24 08:14:18,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.979007
2012-04-24 08:14:18,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.998963
2012-04-24 08:14:19,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.030892
2012-04-24 08:14:19,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.068807
2012-04-24 08:14:20,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.110714
2012-04-24 08:14:20,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.122688
2012-04-24 08:14:21,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.138652
2012-04-24 08:14:21,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.162599
2012-04-24 08:14:22,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.194528
2012-04-24 08:14:22,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.222466
2012-04-24 08:14:23,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.260382
2012-04-24 08:14:23,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.280338
2012-04-24 08:14:24,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.290315
2012-04-24 08:14:24,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.296302
2012-04-24 08:14:25,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.306280
2012-04-24 08:14:25,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.314262
2012-04-24 08:14:26,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.324240
2012-04-24 08:14:26,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.334218
2012-04-24 08:14:27,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.344196
2012-04-24 08:14:27,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.352178
2012-04-24 08:14:28,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.356169
2012-04-24 08:14:28,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.360160
2012-04-24 08:14:29,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.366147
2012-04-24 08:14:29,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.376125
2012-04-24 08:14:30,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.386103
2012-04-24 08:14:30,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.400072
2012-04-24 08:14:31,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.400072
2012-04-24 08:14:31,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.408054
2012-04-24 08:14:32,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.414041
2012-04-24 08:14:32,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.424019
2012-04-24 08:14:33,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.433996
2012-04-24 08:14:33,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.441979
2012-04-24 08:14:34,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.447965
2012-04-24 08:14:34,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.461934
2012-04-24 08:14:35,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.475903
2012-04-24 08:14:35,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.487877
2012-04-24 08:14:36,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.493863
2012-04-24 08:14:36,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.501846
2012-04-24 08:14:37,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.513819
2012-04-24 08:14:37,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.527788
2012-04-24 08:14:38,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.545748
2012-04-24 08:14:38,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.559717
2012-04-24 08:14:39,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.567699
2012-04-24 08:14:39,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.575682
2012-04-24 08:14:40,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.583664
2012-04-24 08:14:40,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.599629
2012-04-24 08:14:41,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.613598
2012-04-24 08:14:41,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.631558
2012-04-24 08:14:42,087 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.635549
2012-04-24 08:14:42,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.649518
2012-04-24 08:14:43,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.665482
2012-04-24 08:14:43,591 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.689429
2012-04-24 08:14:44,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.719363
2012-04-24 08:14:44,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.741314
2012-04-24 08:14:45,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.765261
2012-04-24 08:14:45,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.779230
2012-04-24 08:14:46,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.805172
2012-04-24 08:14:46,599 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.851070
2012-04-24 08:14:47,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.904951
2012-04-24 08:14:47,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.976791
2012-04-24 08:14:48,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.122467
2012-04-24 08:14:48,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.220250
2012-04-24 08:14:49,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.363931
2012-04-24 08:14:49,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.461714
2012-04-24 08:14:50,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.615373
2012-04-24 08:14:50,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.623355
2012-04-24 08:14:51,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.976571
2012-04-24 08:14:51,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.114265
2012-04-24 08:14:52,114 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.180119
2012-04-24 08:14:52,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.285884
2012-04-24 08:14:53,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.361715
2012-04-24 08:14:53,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.409609
2012-04-24 08:14:54,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.475463
2012-04-24 08:14:54,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.541316
2012-04-24 08:14:55,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.593201
2012-04-24 08:14:55,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.639099
2012-04-24 08:14:56,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.665042
2012-04-24 08:14:56,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.720918
2012-04-24 08:14:57,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.736882
2012-04-24 08:14:57,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.770807
2012-04-24 08:14:58,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.804732
2012-04-24 08:14:58,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.844643
2012-04-24 08:14:59,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.894532
2012-04-24 08:14:59,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.936439
2012-04-24 08:15:00,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.992315
2012-04-24 08:15:00,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.026240
2012-04-24 08:15:01,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.060164
2012-04-24 08:15:01,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.096084
2012-04-24 08:15:02,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.143978
2012-04-24 08:15:02,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.149965
2012-04-24 08:15:03,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.211827
2012-04-24 08:15:03,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.245752
2012-04-24 08:15:04,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.261717
2012-04-24 08:15:04,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.295641
2012-04-24 08:15:05,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.329566
2012-04-24 08:15:05,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.357504
2012-04-24 08:15:06,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.391429
2012-04-24 08:15:06,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.419367
2012-04-24 08:15:07,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.455287
2012-04-24 08:15:07,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.483225
2012-04-24 08:15:08,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.525132
2012-04-24 08:15:08,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.525132
2012-04-24 08:15:09,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.569034
2012-04-24 08:15:09,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.616928
2012-04-24 08:15:10,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.668813
2012-04-24 08:15:10,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.694755
2012-04-24 08:15:11,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.724688
2012-04-24 08:15:11,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.754622
2012-04-24 08:15:12,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.784556
2012-04-24 08:15:12,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.814489
2012-04-24 08:15:13,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.824467
2012-04-24 08:15:13,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.824467
2012-04-24 08:15:14,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.866374
2012-04-24 08:15:14,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.890321
2012-04-24 08:15:15,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.908281
2012-04-24 08:15:15,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.916263
2012-04-24 08:15:16,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.964157
2012-04-24 08:15:16,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.990099
2012-04-24 08:15:17,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.020033
2012-04-24 08:15:17,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.047971
2012-04-24 08:15:18,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.079900
2012-04-24 08:15:18,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.109833
2012-04-24 08:15:19,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.137771
2012-04-24 08:15:19,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.149745
2012-04-24 08:15:20,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.171696
2012-04-24 08:15:20,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.205620
2012-04-24 08:15:21,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.245532
2012-04-24 08:15:21,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.245532
2012-04-24 08:15:22,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.293425
2012-04-24 08:15:22,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.335332
2012-04-24 08:15:23,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.349301
2012-04-24 08:15:23,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.365266
2012-04-24 08:15:24,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.387217
2012-04-24 08:15:24,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.423137
2012-04-24 08:15:25,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.465044
2012-04-24 08:15:25,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.516929
2012-04-24 08:15:26,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.572805
2012-04-24 08:15:26,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.572805
2012-04-24 08:15:27,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.610721
2012-04-24 08:15:27,710 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.646641
2012-04-24 08:15:28,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.646641
2012-04-24 08:15:28,713 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.664601
2012-04-24 08:15:29,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.678570
2012-04-24 08:15:29,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.696530
2012-04-24 08:15:30,217 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.716486
2012-04-24 08:15:30,718 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.732450
2012-04-24 08:15:31,220 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.748415
2012-04-24 08:15:31,721 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.766375
2012-04-24 08:15:32,222 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.776353
2012-04-24 08:15:32,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.792318
2012-04-24 08:15:33,225 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.816264
2012-04-24 08:15:33,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.852185
2012-04-24 08:15:34,228 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.892096
2012-04-24 08:15:34,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.924025
2012-04-24 08:15:35,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.959945
2012-04-24 08:15:35,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.983892
2012-04-24 08:15:36,233 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.997861
2012-04-24 08:15:36,734 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.035777
2012-04-24 08:15:37,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.071697
2012-04-24 08:15:37,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.095644
2012-04-24 08:15:38,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.111608
2012-04-24 08:15:38,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.139546
2012-04-24 08:15:39,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.157506
2012-04-24 08:15:39,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.187440
2012-04-24 08:15:40,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.221365
2012-04-24 08:15:40,746 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.257285
2012-04-24 08:15:41,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.297196
2012-04-24 08:15:41,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.339103
2012-04-24 08:15:42,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.375023
2012-04-24 08:15:42,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.402961
2012-04-24 08:15:43,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.422917
2012-04-24 08:15:43,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.466820
2012-04-24 08:15:44,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.508727
2012-04-24 08:15:44,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.562607
2012-04-24 08:15:45,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.574580
2012-04-24 08:15:45,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.628461
2012-04-24 08:15:46,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.700301
2012-04-24 08:15:46,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.728239
2012-04-24 08:15:47,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.766155
2012-04-24 08:15:47,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.810057
2012-04-24 08:15:48,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.868679
2012-04-24 08:15:48,768 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.933783
2012-04-24 08:15:49,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.013605
2012-04-24 08:15:49,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.073472
2012-04-24 08:15:50,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.085446
2012-04-24 08:15:50,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.085446
2012-04-24 08:15:51,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.211167
2012-04-24 08:15:51,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.247087
2012-04-24 08:15:52,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.281011
2012-04-24 08:15:52,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.298972
2012-04-24 08:15:53,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.322918
2012-04-24 08:15:53,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.340878
2012-04-24 08:15:54,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.358839
2012-04-24 08:15:54,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.386777
2012-04-24 08:15:55,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.414715
2012-04-24 08:15:55,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.422697
2012-04-24 08:15:56,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.442652
2012-04-24 08:15:56,789 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.486555
2012-04-24 08:15:57,290 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.532453
2012-04-24 08:15:57,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.562387
2012-04-24 08:15:58,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.600302
2012-04-24 08:15:58,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.686112
2012-04-24 08:15:59,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.732010
2012-04-24 08:15:59,798 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.795868
2012-04-24 08:16:00,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.861722
2012-04-24 08:16:00,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.903629
2012-04-24 08:16:01,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.947531
2012-04-24 08:16:01,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.955514
2012-04-24 08:16:02,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.997420
2012-04-24 08:16:02,806 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.049305
2012-04-24 08:16:03,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.101190
2012-04-24 08:16:03,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.101190
2012-04-24 08:16:04,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.149084
2012-04-24 08:16:04,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.169039
2012-04-24 08:16:05,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.186999
2012-04-24 08:16:05,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.210946
2012-04-24 08:16:06,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.248862
2012-04-24 08:16:06,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.280791
2012-04-24 08:16:07,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.314716
2012-04-24 08:16:07,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.364605
2012-04-24 08:16:08,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.414494
2012-04-24 08:16:08,823 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.452410
2012-04-24 08:16:09,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.466379
2012-04-24 08:16:09,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.518264
2012-04-24 08:16:10,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.572144
2012-04-24 08:16:10,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.624029
2012-04-24 08:16:11,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.639993
2012-04-24 08:16:11,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.695869
2012-04-24 08:16:12,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.771701
2012-04-24 08:16:12,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.819595
2012-04-24 08:16:13,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.843541
2012-04-24 08:16:13,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.931346
2012-04-24 08:16:14,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.961280
2012-04-24 08:16:14,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.003187
2012-04-24 08:16:15,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.027134
2012-04-24 08:16:15,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.055072
2012-04-24 08:16:16,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.083010
2012-04-24 08:16:16,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.092987
2012-04-24 08:16:17,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.110948
2012-04-24 08:16:17,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.136890
2012-04-24 08:16:18,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.144872
2012-04-24 08:16:18,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.162832
2012-04-24 08:16:19,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.204739
2012-04-24 08:16:19,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.226690
2012-04-24 08:16:20,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.252633
2012-04-24 08:16:20,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.280571
2012-04-24 08:16:21,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.302522
2012-04-24 08:16:21,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.306513
2012-04-24 08:16:22,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.352411
2012-04-24 08:16:22,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.376358
2012-04-24 08:16:23,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.390327
2012-04-24 08:16:23,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.398309
2012-04-24 08:16:24,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.422256
2012-04-24 08:16:24,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.444207
2012-04-24 08:16:25,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.466159
2012-04-24 08:16:25,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.492101
2012-04-24 08:16:26,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.520039
2012-04-24 08:16:26,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.520039
2012-04-24 08:16:27,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.549973
2012-04-24 08:16:27,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.581902
2012-04-24 08:16:28,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.627800
2012-04-24 08:16:28,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.661724
2012-04-24 08:16:29,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.715605
2012-04-24 08:16:29,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.777467
2012-04-24 08:16:30,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.815383
2012-04-24 08:16:30,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.873255
2012-04-24 08:16:31,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.915162
2012-04-24 08:16:31,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.979020
2012-04-24 08:16:32,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.032900
2012-04-24 08:16:32,888 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.088776
2012-04-24 08:16:33,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.142656
2012-04-24 08:16:33,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.212501
2012-04-24 08:16:34,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.240439
2012-04-24 08:16:34,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.302302
2012-04-24 08:16:35,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.366160
2012-04-24 08:16:35,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.441992
2012-04-24 08:16:36,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.525805
2012-04-24 08:16:36,898 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.575695
2012-04-24 08:16:37,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.627579
2012-04-24 08:16:37,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.741327
2012-04-24 08:16:38,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.885008
2012-04-24 08:16:38,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.910950
2012-04-24 08:16:39,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.010729
2012-04-24 08:16:39,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.064609
2012-04-24 08:16:40,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.172370
2012-04-24 08:16:40,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.238223
2012-04-24 08:16:41,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.310064
2012-04-24 08:16:41,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.373922
2012-04-24 08:16:42,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.451749
2012-04-24 08:16:42,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.513612
2012-04-24 08:16:43,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.591439
2012-04-24 08:16:43,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.667270
2012-04-24 08:16:44,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.715164
2012-04-24 08:16:44,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.715164
2012-04-24 08:16:45,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.838889
2012-04-24 08:16:45,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.886783
2012-04-24 08:16:46,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.922703
2012-04-24 08:16:46,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.950641
2012-04-24 08:16:47,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.994544
2012-04-24 08:16:47,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.052415
2012-04-24 08:16:48,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.096318
2012-04-24 08:16:48,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.130242
2012-04-24 08:16:49,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.148202
2012-04-24 08:16:49,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.152194
2012-04-24 08:16:50,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.178136
2012-04-24 08:16:50,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.188114
2012-04-24 08:16:51,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.198092
2012-04-24 08:16:51,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.210065
2012-04-24 08:16:52,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.224034
2012-04-24 08:16:52,943 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.239999
2012-04-24 08:16:53,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.243990
2012-04-24 08:16:53,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.271928
2012-04-24 08:16:54,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.283901
2012-04-24 08:16:54,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.291883
2012-04-24 08:16:55,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.311839
2012-04-24 08:16:55,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.331795
2012-04-24 08:16:56,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.353746
2012-04-24 08:16:56,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.375697
2012-04-24 08:16:57,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.395653
2012-04-24 08:16:57,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.395653
2012-04-24 08:16:58,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.421595
2012-04-24 08:16:58,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.449533
2012-04-24 08:16:59,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.475476
2012-04-24 08:16:59,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.483458
2012-04-24 08:17:00,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.513391
2012-04-24 08:17:00,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.565276
2012-04-24 08:17:01,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.595210
2012-04-24 08:17:01,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.615165
2012-04-24 08:17:02,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.663059
2012-04-24 08:17:02,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.712948
2012-04-24 08:17:03,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.754855
2012-04-24 08:17:03,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.800753
2012-04-24 08:17:04,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.840665
2012-04-24 08:17:04,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.888558
2012-04-24 08:17:05,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.920487
2012-04-24 08:17:05,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.978359
2012-04-24 08:17:06,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.038226
2012-04-24 08:17:06,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.100088
2012-04-24 08:17:07,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.143991
2012-04-24 08:17:07,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.197871
2012-04-24 08:17:08,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.243769
2012-04-24 08:17:08,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.299645
2012-04-24 08:17:09,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.375477
2012-04-24 08:17:09,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.481242
2012-04-24 08:17:10,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.579025
2012-04-24 08:17:10,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.714724
2012-04-24 08:17:11,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.714724
2012-04-24 08:17:11,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.936232
2012-04-24 08:17:12,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.036010
2012-04-24 08:17:12,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.181686
2012-04-24 08:17:13,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.231576
2012-04-24 08:17:14,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.393217
2012-04-24 08:17:14,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.471044
2012-04-24 08:17:15,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.586787
2012-04-24 08:17:15,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.706521
2012-04-24 08:17:16,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.788339
2012-04-24 08:17:16,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.910069
2012-04-24 08:17:17,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.985901
2012-04-24 08:17:17,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.067719
2012-04-24 08:17:18,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.139559
2012-04-24 08:17:18,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.233351
2012-04-24 08:17:19,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.255302
2012-04-24 08:17:19,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.367054
2012-04-24 08:17:20,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.432908
2012-04-24 08:17:20,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.432908
2012-04-24 08:17:21,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.514726
2012-04-24 08:17:21,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.560624
2012-04-24 08:17:22,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.598540
2012-04-24 08:17:22,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.644438
2012-04-24 08:17:23,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.654416
2012-04-24 08:17:23,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.714283
2012-04-24 08:17:24,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.746212
2012-04-24 08:17:24,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.774150
2012-04-24 08:17:25,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.814061
2012-04-24 08:17:25,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.840004
2012-04-24 08:17:26,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.893884
2012-04-24 08:17:26,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.957742
2012-04-24 08:17:27,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.001645
2012-04-24 08:17:27,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.007631
2012-04-24 08:17:28,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.009627
2012-04-24 08:17:28,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.083463
2012-04-24 08:17:29,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.121379
2012-04-24 08:17:29,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.155304
2012-04-24 08:17:30,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.201202
2012-04-24 08:17:30,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.245104
2012-04-24 08:17:31,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.273042
2012-04-24 08:17:31,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.281024
2012-04-24 08:17:32,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.320936
2012-04-24 08:17:32,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.362843
2012-04-24 08:17:33,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.412732
2012-04-24 08:17:33,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.452643
2012-04-24 08:17:34,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.468608
2012-04-24 08:17:34,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.518497
2012-04-24 08:17:35,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.528475
2012-04-24 08:17:35,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.538453
2012-04-24 08:17:36,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.550426
2012-04-24 08:17:36,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.572377
2012-04-24 08:17:37,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.606302
2012-04-24 08:17:37,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.654196
2012-04-24 08:17:38,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.706080
2012-04-24 08:17:38,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.757965
2012-04-24 08:17:39,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.811845
2012-04-24 08:17:39,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.825814
2012-04-24 08:17:40,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.877699
2012-04-24 08:17:40,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.931580
2012-04-24 08:17:41,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.973487
2012-04-24 08:17:41,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.991447
2012-04-24 08:17:42,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.059296
2012-04-24 08:17:42,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.107190
2012-04-24 08:17:43,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.133132
2012-04-24 08:17:43,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.204972
2012-04-24 08:17:44,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.276813
2012-04-24 08:17:44,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.304751
2012-04-24 08:17:45,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.414507
2012-04-24 08:17:45,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.414507
2012-04-24 08:17:46,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.568166
2012-04-24 08:17:46,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.620051
2012-04-24 08:17:47,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.655971
2012-04-24 08:17:47,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.675927
2012-04-24 08:17:48,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.769718
2012-04-24 08:17:48,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.825594
2012-04-24 08:17:49,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.887457
2012-04-24 08:17:49,599 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.943333
2012-04-24 08:17:50,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.971271
2012-04-24 08:17:50,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.055085
2012-04-24 08:17:51,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.104974
2012-04-24 08:17:51,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.144885
2012-04-24 08:17:52,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.198765
2012-04-24 08:17:52,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.226703
2012-04-24 08:17:53,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.272601
2012-04-24 08:17:53,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.338455
2012-04-24 08:17:54,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.402313
2012-04-24 08:17:54,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.442225
2012-04-24 08:17:55,114 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.498101
2012-04-24 08:17:55,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.543999
2012-04-24 08:17:56,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.583910
2012-04-24 08:17:56,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.649764
2012-04-24 08:17:57,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.707635
2012-04-24 08:17:57,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.787458
2012-04-24 08:17:58,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.849321
2012-04-24 08:17:58,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.961072
2012-04-24 08:17:59,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.040895
2012-04-24 08:17:59,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.114731
2012-04-24 08:18:00,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.206527
2012-04-24 08:18:00,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.272381
2012-04-24 08:18:01,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.364177
2012-04-24 08:18:01,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.442004
2012-04-24 08:18:02,134 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.442004
2012-04-24 08:18:02,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.603645
2012-04-24 08:18:03,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.681473
2012-04-24 08:18:03,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.765287
2012-04-24 08:18:04,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.847105
2012-04-24 08:18:04,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.942892
2012-04-24 08:18:05,142 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.040675
2012-04-24 08:18:05,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.134467
2012-04-24 08:18:06,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.218281
2012-04-24 08:18:06,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.266174
2012-04-24 08:18:07,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.361961
2012-04-24 08:18:07,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.453758
2012-04-24 08:18:08,150 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.541563
2012-04-24 08:18:08,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.641341
2012-04-24 08:18:09,153 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.755088
2012-04-24 08:18:09,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.840898
2012-04-24 08:18:10,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.898769
2012-04-24 08:18:10,657 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.032472
2012-04-24 08:18:11,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.210078
2012-04-24 08:18:11,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.277927
2012-04-24 08:18:12,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.391675
2012-04-24 08:18:12,663 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.507418
2012-04-24 08:18:13,164 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.625156
2012-04-24 08:18:13,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.778815
2012-04-24 08:18:14,167 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.882584
2012-04-24 08:18:14,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.078150
2012-04-24 08:18:15,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.227818
2012-04-24 08:18:15,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.237796
2012-04-24 08:18:16,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.417397
2012-04-24 08:18:16,674 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.509193
2012-04-24 08:18:17,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.596998
2012-04-24 08:18:17,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.686798
2012-04-24 08:18:18,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.778595
2012-04-24 08:18:18,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.862408
2012-04-24 08:18:19,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.930258
2012-04-24 08:18:19,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.016067
2012-04-24 08:18:20,184 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.101877
2012-04-24 08:18:20,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.195668
2012-04-24 08:18:21,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.263518
2012-04-24 08:18:21,688 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.317398
2012-04-24 08:18:22,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.411190
2012-04-24 08:18:22,691 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.455092
2012-04-24 08:18:23,192 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.596778
2012-04-24 08:18:23,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.624716
2012-04-24 08:18:24,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.700547
2012-04-24 08:18:24,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.776379
2012-04-24 08:18:25,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.842232
2012-04-24 08:18:25,698 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.906091
2012-04-24 08:18:26,200 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.977931
2012-04-24 08:18:26,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.053763
2012-04-24 08:18:27,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.133585
2012-04-24 08:18:27,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.213408
2012-04-24 08:18:28,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.293231
2012-04-24 08:18:28,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.325160
2012-04-24 08:18:29,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.381036
2012-04-24 08:18:29,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.460859
2012-04-24 08:18:30,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.534695
2012-04-24 08:18:30,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.622500
2012-04-24 08:18:31,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.714296
2012-04-24 08:18:31,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.816070
2012-04-24 08:18:32,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.921835
2012-04-24 08:18:32,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.971724
2012-04-24 08:18:33,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.097445
2012-04-24 08:18:33,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.183254
2012-04-24 08:18:34,222 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.269064
2012-04-24 08:18:34,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.348887
2012-04-24 08:18:35,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.432700
2012-04-24 08:18:35,726 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.522501
2012-04-24 08:18:36,227 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.640239
2012-04-24 08:18:36,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.702102
2012-04-24 08:18:37,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.763965
2012-04-24 08:18:37,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.849774
2012-04-24 08:18:38,233 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.875717
2012-04-24 08:18:38,734 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.907646
2012-04-24 08:18:39,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.045340
2012-04-24 08:18:39,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.109198
2012-04-24 08:18:40,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.187025
2012-04-24 08:18:40,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.198999
2012-04-24 08:18:41,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.276826
2012-04-24 08:18:41,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.324719
2012-04-24 08:18:42,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.378600
2012-04-24 08:18:42,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.442458
2012-04-24 08:18:43,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.498334
2012-04-24 08:18:43,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.532259
2012-04-24 08:18:44,249 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.600108
2012-04-24 08:18:44,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.663966
2012-04-24 08:18:45,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.743789
2012-04-24 08:18:45,753 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.799665
2012-04-24 08:18:46,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.881483
2012-04-24 08:18:46,756 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.959310
2012-04-24 08:18:47,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.003213
2012-04-24 08:18:47,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.106982
2012-04-24 08:18:48,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.144898
2012-04-24 08:18:48,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.230707
2012-04-24 08:18:49,263 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.312526
2012-04-24 08:18:49,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.360419
2012-04-24 08:18:50,266 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.420286
2012-04-24 08:18:50,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.474167
2012-04-24 08:18:51,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.526052
2012-04-24 08:18:51,770 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.593901
2012-04-24 08:18:52,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.657759
2012-04-24 08:18:52,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.699666
2012-04-24 08:18:53,274 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.771506
2012-04-24 08:18:53,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.817404
2012-04-24 08:18:54,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.871285
2012-04-24 08:18:54,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.931152
2012-04-24 08:18:55,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.985032
2012-04-24 08:18:55,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.012970
2012-04-24 08:18:56,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.048890
2012-04-24 08:18:56,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.068846
2012-04-24 08:18:57,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.098780
2012-04-24 08:18:57,786 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.126718
2012-04-24 08:18:58,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.184589
2012-04-24 08:18:58,789 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.256429
2012-04-24 08:18:59,290 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.314301
2012-04-24 08:18:59,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.416075
2012-04-24 08:19:00,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.491907
2012-04-24 08:19:00,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.551774
2012-04-24 08:19:01,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.643570
2012-04-24 08:19:01,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.695455
2012-04-24 08:19:02,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.777273
2012-04-24 08:19:02,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.837140
2012-04-24 08:19:03,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.871065
2012-04-24 08:19:03,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.934923
2012-04-24 08:19:04,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.998781
2012-04-24 08:19:04,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.998781
2012-04-24 08:19:05,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.072617
2012-04-24 08:19:05,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.118515
2012-04-24 08:19:06,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.144457
2012-04-24 08:19:06,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.172395
2012-04-24 08:19:07,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.198338
2012-04-24 08:19:07,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.218293
2012-04-24 08:19:08,315 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.244236
2012-04-24 08:19:08,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.272174
2012-04-24 08:19:09,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.302107
2012-04-24 08:19:09,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.328050
2012-04-24 08:19:10,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.357983
2012-04-24 08:19:10,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.383926
2012-04-24 08:19:11,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.403881
2012-04-24 08:19:11,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.433815
2012-04-24 08:19:12,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.433815
2012-04-24 08:19:12,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.501664
2012-04-24 08:19:13,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.527606
2012-04-24 08:19:13,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.551553
2012-04-24 08:19:14,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.573505
2012-04-24 08:19:14,833 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.573505
2012-04-24 08:19:15,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.573505
2012-04-24 08:19:15,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.575500
2012-04-24 08:19:16,337 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.577496
2012-04-24 08:19:16,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.589469
2012-04-24 08:19:17,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.605434
2012-04-24 08:19:17,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.633372
2012-04-24 08:19:18,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.659314
2012-04-24 08:19:18,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.693239
2012-04-24 08:19:19,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.731154
2012-04-24 08:19:19,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.785035
2012-04-24 08:19:20,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.842906
2012-04-24 08:19:20,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.882818
2012-04-24 08:19:21,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.942685
2012-04-24 08:19:21,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.998561
2012-04-24 08:19:22,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.062419
2012-04-24 08:19:22,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.122286
2012-04-24 08:19:23,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.200113
2012-04-24 08:19:23,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.305878
2012-04-24 08:19:24,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.407652
2012-04-24 08:19:24,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.575280
2012-04-24 08:19:25,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.760868
2012-04-24 08:19:25,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.966411
2012-04-24 08:19:26,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.195902
2012-04-24 08:19:26,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.467299
2012-04-24 08:19:27,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.529161
2012-04-24 08:19:27,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.818519
2012-04-24 08:19:28,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.930271
2012-04-24 08:19:28,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.008098
2012-04-24 08:19:29,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.123841
2012-04-24 08:19:29,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.257544
2012-04-24 08:19:30,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.369296
2012-04-24 08:19:30,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.473065
2012-04-24 08:19:31,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.572844
2012-04-24 08:19:31,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.726502
2012-04-24 08:19:32,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.886148
2012-04-24 08:19:32,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.942024
2012-04-24 08:19:33,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.073731
2012-04-24 08:19:33,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.203443
2012-04-24 08:19:34,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.379053
2012-04-24 08:19:34,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.546681
2012-04-24 08:19:35,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.772180
2012-04-24 08:19:35,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.939808
2012-04-24 08:19:36,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.045573
2012-04-24 08:19:36,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.265086
2012-04-24 08:19:37,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.370851
2012-04-24 08:19:37,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.502558
2012-04-24 08:19:38,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.604332
2012-04-24 08:19:38,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.674177
2012-04-24 08:19:39,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.807880
2012-04-24 08:19:39,903 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.925619
2012-04-24 08:19:40,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.017415
2012-04-24 08:19:40,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.091251
2012-04-24 08:19:41,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.149122
2012-04-24 08:19:41,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.206994
2012-04-24 08:19:42,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.294799
2012-04-24 08:19:42,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.376617
2012-04-24 08:19:43,412 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.446462
2012-04-24 08:19:43,913 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.528280
2012-04-24 08:19:44,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.602116
2012-04-24 08:19:44,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.677948
2012-04-24 08:19:45,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.753779
2012-04-24 08:19:45,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.815642
2012-04-24 08:19:46,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.903447
2012-04-24 08:19:46,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.991252
2012-04-24 08:19:47,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.095022
2012-04-24 08:19:47,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.208769
2012-04-24 08:19:48,426 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.298570
2012-04-24 08:19:48,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.448237
2012-04-24 08:19:49,429 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.647794
2012-04-24 08:19:49,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.837373
2012-04-24 08:19:50,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.955112
2012-04-24 08:19:50,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 64.290367
2012-04-24 08:19:51,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 64.465977
2012-04-24 08:19:51,935 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 64.777286
2012-04-24 08:19:52,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 64.944913
2012-04-24 08:19:52,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.120523
2012-04-24 08:19:53,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.274182
2012-04-24 08:19:53,941 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.411876
2012-04-24 08:19:54,442 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.447797
2012-04-24 08:19:54,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.653340
2012-04-24 08:19:55,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.747132
2012-04-24 08:19:55,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.846910
2012-04-24 08:19:56,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.922742
2012-04-24 08:19:56,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.956667
2012-04-24 08:19:57,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.088374
2012-04-24 08:19:57,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.120303
2012-04-24 08:19:58,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.218086
2012-04-24 08:19:58,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.269971
2012-04-24 08:19:59,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.299904
2012-04-24 08:19:59,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.379727
2012-04-24 08:20:00,459 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.413652
2012-04-24 08:20:00,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.495470
2012-04-24 08:20:01,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.559328
2012-04-24 08:20:01,963 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.621191
2012-04-24 08:20:02,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.683053
2012-04-24 08:20:02,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.730947
2012-04-24 08:20:03,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.782832
2012-04-24 08:20:03,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.822743
2012-04-24 08:20:04,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.890592
2012-04-24 08:20:04,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.942477
2012-04-24 08:20:05,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.992366
2012-04-24 08:20:05,974 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.052234
2012-04-24 08:20:06,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.112101
2012-04-24 08:20:06,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.171968
2012-04-24 08:20:07,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.231835
2012-04-24 08:20:07,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.293697
2012-04-24 08:20:08,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.357555
2012-04-24 08:20:08,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.429396
2012-04-24 08:20:09,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.491259
2012-04-24 08:20:09,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.539152
2012-04-24 08:20:10,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.605006
2012-04-24 08:20:10,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.668864
2012-04-24 08:20:11,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.764651
2012-04-24 08:20:11,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.828510
2012-04-24 08:20:12,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.878399
2012-04-24 08:20:12,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.940261
2012-04-24 08:20:13,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.996137
2012-04-24 08:20:13,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.065982
2012-04-24 08:20:14,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.109885
2012-04-24 08:20:14,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.181725
2012-04-24 08:20:15,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.245583
2012-04-24 08:20:16,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.315428
2012-04-24 08:20:16,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.385273
2012-04-24 08:20:17,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.465096
2012-04-24 08:20:17,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.514985
2012-04-24 08:20:18,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.632724
2012-04-24 08:20:18,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.716537
2012-04-24 08:20:19,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.808334
2012-04-24 08:20:19,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.876183
2012-04-24 08:20:20,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.045806
2012-04-24 08:20:20,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.151571
2012-04-24 08:20:21,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.257336
2012-04-24 08:20:21,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.363102
2012-04-24 08:20:22,018 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.456893
2012-04-24 08:20:22,519 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.562658
2012-04-24 08:20:23,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.670419
2012-04-24 08:20:23,522 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.808113
2012-04-24 08:20:24,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.949799
2012-04-24 08:20:24,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.951794
2012-04-24 08:20:25,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.123413
2012-04-24 08:20:25,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.237160
2012-04-24 08:20:26,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.312992
2012-04-24 08:20:26,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.392815
2012-04-24 08:20:27,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.502571
2012-04-24 08:20:27,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.590376
2012-04-24 08:20:28,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.668203
2012-04-24 08:20:28,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.736053
2012-04-24 08:20:29,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.817871
2012-04-24 08:20:29,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.917649
2012-04-24 08:20:30,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.971530
2012-04-24 08:20:30,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.021419
2012-04-24 08:20:31,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.083281
2012-04-24 08:20:31,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.103237
2012-04-24 08:20:32,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.224967
2012-04-24 08:20:32,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.272860
2012-04-24 08:20:33,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.322750
2012-04-24 08:20:33,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.372639
2012-04-24 08:20:34,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.434501
2012-04-24 08:20:34,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.496364
2012-04-24 08:20:35,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.564213
2012-04-24 08:20:35,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.620089
2012-04-24 08:20:36,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.675965
2012-04-24 08:20:36,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.757783
2012-04-24 08:20:37,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.863549
2012-04-24 08:20:37,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.971309
2012-04-24 08:20:38,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.109004
2012-04-24 08:20:38,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.188826
2012-04-24 08:20:39,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.416321
2012-04-24 08:20:39,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.587940
2012-04-24 08:20:40,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.899249
2012-04-24 08:20:40,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 73.011000
2012-04-24 08:20:41,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 73.593706
2012-04-24 08:20:41,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 73.930957
2012-04-24 08:20:42,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 74.190381
2012-04-24 08:20:42,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 74.475747
2012-04-24 08:20:43,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 74.793043
2012-04-24 08:20:43,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 75.140272
2012-04-24 08:20:44,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 75.443598
2012-04-24 08:20:44,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 75.663111
2012-04-24 08:20:45,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 75.728964
2012-04-24 08:20:45,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.018322
2012-04-24 08:20:46,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.189941
2012-04-24 08:20:46,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.357568
2012-04-24 08:20:47,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.527192
2012-04-24 08:20:47,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.696815
2012-04-24 08:20:48,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.852469
2012-04-24 08:20:48,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.990163
2012-04-24 08:20:49,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.185729
2012-04-24 08:20:49,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.383290
2012-04-24 08:20:50,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.582847
2012-04-24 08:20:50,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.776417
2012-04-24 08:20:51,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.969988
2012-04-24 08:20:51,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.155575
2012-04-24 08:20:52,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.335177
2012-04-24 08:20:52,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.416995
2012-04-24 08:20:53,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.586618
2012-04-24 08:20:53,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.714334
2012-04-24 08:20:54,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.834069
2012-04-24 08:20:54,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.941829
2012-04-24 08:20:55,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.071541
2012-04-24 08:20:55,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.205244
2012-04-24 08:20:56,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.340943
2012-04-24 08:20:56,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.464668
2012-04-24 08:20:57,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.580411
2012-04-24 08:20:57,615 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.732074
2012-04-24 08:20:58,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.825866
2012-04-24 08:20:58,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.019436
2012-04-24 08:20:59,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.131188
2012-04-24 08:20:59,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.270878
2012-04-24 08:21:00,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.428528
2012-04-24 08:21:00,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.564226
2012-04-24 08:21:01,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.719881
2012-04-24 08:21:01,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.851588
2012-04-24 08:21:02,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.007242
2012-04-24 08:21:02,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.160901
2012-04-24 08:21:03,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.278640
2012-04-24 08:21:03,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.432298
2012-04-24 08:21:04,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.518108
2012-04-24 08:21:04,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.703696
2012-04-24 08:21:05,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.859350
2012-04-24 08:21:05,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.011013
2012-04-24 08:21:06,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.200592
2012-04-24 08:21:06,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.374207
2012-04-24 08:21:07,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.553808
2012-04-24 08:21:07,643 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.725427
2012-04-24 08:21:08,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.875094
2012-04-24 08:21:08,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.044718
2012-04-24 08:21:09,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.220328
2012-04-24 08:21:09,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.411902
2012-04-24 08:21:10,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.599486
2012-04-24 08:21:10,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.789065
2012-04-24 08:21:11,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.988621
2012-04-24 08:21:11,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.096382
2012-04-24 08:21:12,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.275983
2012-04-24 08:21:12,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.389731
2012-04-24 08:21:13,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.479531
2012-04-24 08:21:13,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.571327
2012-04-24 08:21:14,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.659132
2012-04-24 08:21:14,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.742946
2012-04-24 08:21:15,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.838733
2012-04-24 08:21:15,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.920552
2012-04-24 08:21:16,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.998379
2012-04-24 08:21:16,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.090175
2012-04-24 08:21:17,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.209909
2012-04-24 08:21:17,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.333634
2012-04-24 08:21:18,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.493280
2012-04-24 08:21:18,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.672881
2012-04-24 08:21:19,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.882416
2012-04-24 08:21:19,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.085964
2012-04-24 08:21:20,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.287516
2012-04-24 08:21:20,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.511020
2012-04-24 08:21:21,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.752483
2012-04-24 08:21:21,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.912129
2012-04-24 08:21:22,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.109690
2012-04-24 08:21:22,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.293282
2012-04-24 08:21:23,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.504813
2012-04-24 08:21:23,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.668449
2012-04-24 08:21:24,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.854037
2012-04-24 08:21:24,690 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.023660
2012-04-24 08:21:25,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.189293
2012-04-24 08:21:25,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.402818
2012-04-24 08:21:26,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.598384
2012-04-24 08:21:26,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.847830
2012-04-24 08:21:27,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.071334
2012-04-24 08:21:27,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.185081
2012-04-24 08:21:28,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.318784
2012-04-24 08:21:28,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.472443
2012-04-24 08:21:29,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.598164
2012-04-24 08:21:29,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.755814
2012-04-24 08:21:30,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.849605
2012-04-24 08:21:30,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.021224
2012-04-24 08:21:31,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.126989
2012-04-24 08:21:31,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.220781
2012-04-24 08:21:32,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.356480
2012-04-24 08:21:32,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.434307
2012-04-24 08:21:33,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.526103
2012-04-24 08:21:33,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.615904
2012-04-24 08:21:34,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.713686
2012-04-24 08:21:34,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.807478
2012-04-24 08:21:35,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.911248
2012-04-24 08:21:35,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.999053
2012-04-24 08:21:36,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.110805
2012-04-24 08:21:36,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.192623
2012-04-24 08:21:37,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.288410
2012-04-24 08:21:37,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.372224
2012-04-24 08:21:38,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.444064
2012-04-24 08:21:38,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.527878
2012-04-24 08:21:39,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.597723
2012-04-24 08:21:39,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.669564
2012-04-24 08:21:40,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.753378
2012-04-24 08:21:40,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.835881
2012-04-24 08:21:40,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.835881
2012-04-24 08:21:40,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.835881
2012-04-24 08:21:40,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.837446
2012-04-24 08:21:41,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.877358
2012-04-24 08:21:41,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.046981
2012-04-24 08:21:42,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.184675
2012-04-24 08:21:42,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.240551
2012-04-24 08:21:43,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.482015
2012-04-24 08:21:43,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.709510
2012-04-24 08:21:44,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.885120
2012-04-24 08:21:44,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.038778
2012-04-24 08:21:45,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.168490
2012-04-24 08:21:45,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.266273
2012-04-24 08:21:46,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.374034
2012-04-24 08:21:46,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.473812
2012-04-24 08:21:47,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.597538
2012-04-24 08:21:47,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.699312
2012-04-24 08:21:48,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.803081
2012-04-24 08:21:48,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.908846
2012-04-24 08:21:49,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.032571
2012-04-24 08:21:49,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.174257
2012-04-24 08:21:50,462 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.313947
2012-04-24 08:21:50,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.493548
2012-04-24 08:21:51,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.727029
2012-04-24 08:21:51,966 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 95.006409
2012-04-24 08:21:52,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 95.323704
2012-04-24 08:21:52,969 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 95.593106
2012-04-24 08:21:53,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.072042
2012-04-24 08:21:53,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.263617
2012-04-24 08:21:54,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.401311
2012-04-24 08:21:54,974 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.580912
2012-04-24 08:21:55,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.752531
2012-04-24 08:21:55,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.874261
2012-04-24 08:21:56,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.029915
2012-04-24 08:21:56,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.199538
2012-04-24 08:21:57,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.367166
2012-04-24 08:21:57,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.486900
2012-04-24 08:21:58,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.588674
2012-04-24 08:21:58,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.702421
2012-04-24 08:21:59,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.822156
2012-04-24 08:21:59,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.913952
2012-04-24 08:22:00,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.025704
2012-04-24 08:22:00,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.123486
2012-04-24 08:22:01,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.257189
2012-04-24 08:22:01,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.380915
2012-04-24 08:22:02,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.530582
2012-04-24 08:22:02,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.628365
2012-04-24 08:22:03,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.718166
2012-04-24 08:22:03,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.799984
2012-04-24 08:22:04,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.895771
2012-04-24 08:22:05,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.981581
2012-04-24 08:22:05,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.091337
2012-04-24 08:22:06,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.191115
2012-04-24 08:22:06,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.290894
2012-04-24 08:22:07,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.388677
2012-04-24 08:22:07,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.516393
2012-04-24 08:22:08,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.678034
2012-04-24 08:22:08,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.849653
2012-04-24 08:22:08,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 100.000000
2012-04-24 08:22:09,078 DEBUG: install progress dpkg-exec 0.000000
2012-04-24 08:22:09,857 DEBUG: install progress dkms 0.000000
2012-04-24 08:22:09,958 DEBUG: install progress dkms 6.666670
2012-04-24 08:22:10,844 DEBUG: install progress dkms 13.333300
2012-04-24 08:22:11,047 DEBUG: install progress dkms 20.000000
2012-04-24 08:22:12,074 DEBUG: install progress fglrx-updates 20.000000
2012-04-24 08:22:12,174 DEBUG: install progress fglrx-updates 26.666700
2012-04-24 08:22:18,891 DEBUG: install progress fglrx-updates 33.333300
2012-04-24 08:22:19,067 DEBUG: install progress fglrx-updates 40.000000
2012-04-24 08:22:19,551 DEBUG: install progress fglrx-amdcccle-updates 40.000000
2012-04-24 08:22:19,652 DEBUG: install progress fglrx-amdcccle-updates 46.666700
2012-04-24 08:22:21,091 DEBUG: install progress fglrx-amdcccle-updates 53.333300
2012-04-24 08:22:21,265 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-04-24 08:22:21,437 DEBUG: install progress man-db 60.000000
2012-04-24 08:22:23,277 DEBUG: install progress ureadahead 60.000000
2012-04-24 08:22:24,000 DEBUG: install progress dpkg-exec 60.000000
2012-04-24 08:22:24,035 DEBUG: install progress dkms 60.000000
2012-04-24 08:22:27,160 DEBUG: install progress dkms 66.666700
2012-04-24 08:22:27,356 DEBUG: install progress dkms 73.333300
2012-04-24 08:22:27,551 DEBUG: install progress fglrx-updates 73.333300
2012-04-24 08:22:28,345 DEBUG: install progress fglrx-updates 80.000000
2012-04-24 08:22:56,203 DEBUG: install progress fglrx-updates 86.666700
2012-04-24 08:22:57,180 DEBUG: install progress bamfdaemon 86.666700
2012-04-24 08:22:57,761 DEBUG: install progress fglrx-amdcccle-updates 86.666700
2012-04-24 08:22:57,951 DEBUG: install progress fglrx-amdcccle-updates 93.333300
2012-04-24 08:22:58,140 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-04-24 08:22:58,342 DEBUG: install progress initramfs-tools 100.000000
2012-04-24 08:23:12,656 DEBUG: install progress libc-bin 100.000000
2012-04-24 08:23:15,665 DEBUG: Selecting previously unselected package dkms.
(Reading database ... 174424 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-23-generic
Building for architecture x86_64
Building initial module for 3.2.0-23-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic/updates/dkms/

depmod......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
Warning: No support for locale: en_US.utf8
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-04-24 08:23:15,882 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-24 08:23:35,952 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:35,952 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:35,982 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:35,983 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,671 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,671 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,702 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,703 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,761 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,762 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-24 08:23:43,834 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,834 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,865 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,866 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,951 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,951 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,982 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,983 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:44,036 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:44,037 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-24 08:23:48,963 DEBUG: Shutting down
2012-04-24 08:28:27,576 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0>
2012-04-24 08:28:29,045 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-24 08:28:29,111 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-24 08:28:29,111 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-24 08:28:29,163 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-24 08:28:29,172 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-24 08:28:29,200 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-24 08:28:29,201 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-24 08:28:29,201 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-24 08:28:29,223 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-24 08:28:29,223 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:29,327 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 08:28:29,334 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 08:28:29,343 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-24 08:28:29,343 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:29,399 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-24 08:28:29,400 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-24 08:28:29,431 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-24 08:28:29,447 DEBUG: Software modem not available
2012-04-24 08:28:29,447 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-24 08:28:29,456 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-24 08:28:29,457 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-24 08:28:29,457 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-24 08:28:29,457 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-24 08:28:29,464 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-24 08:28:29,465 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-24 08:28:29,493 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-24 08:28:29,493 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-24 08:28:29,531 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-24 08:28:29,532 DEBUG: Firmware for DVB cards not available
2012-04-24 08:28:29,532 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-24 08:28:29,543 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-24 08:28:29,553 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-24 08:28:29,603 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-24 08:28:29,604 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-24 08:28:29,616 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-24 08:28:29,625 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-24 08:28:29,628 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,628 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:28:29,635 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 08:28:29,644 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-24 08:28:29,645 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,645 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:28:29,652 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 08:28:29,660 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-24 08:28:29,662 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,662 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:28:29,668 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-24 08:28:29,677 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-24 08:28:29,678 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,679 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:28:29,685 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-24 08:28:29,694 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-24 08:28:29,695 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,695 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:28:29,702 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-24 08:28:29,711 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-24 08:28:29,712 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,712 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:28:29,712 DEBUG: all custom handlers loaded
2012-04-24 08:28:29,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 08:28:29,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 08:28:29,725 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:29,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,792 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:29,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 08:28:29,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 08:28:29,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000103Csd00001657bc07sc80i00')
2012-04-24 08:28:29,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-24 08:28:29,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:dock')
2012-04-24 08:28:29,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 08:28:29,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-24 08:28:29,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-24 08:28:29,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-24 08:28:29,980 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:29,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,980 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:29,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-24 08:28:29,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-24 08:28:29,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00001002d00006740sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:28:30,183 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-24 08:28:30,207 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,208 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:30,183 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:28:30,217 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:30,272 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,272 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:30,247 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:28:30,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-24 08:28:30,298 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,298 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-24 08:28:30,273 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-24 08:28:30,305 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 08:28:30,314 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:30,370 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,370 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-24 08:28:30,344 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-24 08:28:30,371 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-24 08:28:30,371 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,371 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-24 08:28:30,396 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,397 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:30,371 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:28:30,405 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:30,460 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,460 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:30,434 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:28:30,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-24 08:28:30,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2012-04-24 08:28:30,470 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-24 08:28:30,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 08:28:30,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 08:28:30,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00000116sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:28:30,478 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-04-24 08:28:30,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00001657bc02sc00i00')
2012-04-24 08:28:30,487 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-04-24 08:28:30,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 08:28:30,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000103Csd00001657bc06sc01i00')
2012-04-24 08:28:30,489 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-24 08:28:30,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc02ip00')
2012-04-24 08:28:30,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 08:28:30,489 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 08:28:30,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-24 08:28:30,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:28:30,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-24 08:28:30,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:28:30,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-24 08:28:30,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 08:28:30,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1B:bd10/05/2011:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvr0589110014244710000620100:rvnHewlett-Packard:rn1657:rvr10.31:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-24 08:28:30,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 08:28:30,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000103Csd00001657bc01sc06i01')
2012-04-24 08:28:30,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-24 08:28:30,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:30,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-04-24 08:28:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:28:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v138Ap0018d0078dcFFdsc11dpFFicFFisc00ip00')
2012-04-24 08:28:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:28:30,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0003v5986p02ACe0924-e0,1,kD4,ramlsfw')
2012-04-24 08:28:30,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:30,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:SYN1E47:SYN1E00:SYN0002:PNP0F13:')
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-24 08:28:30,508 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-04-24 08:28:30,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-24 08:28:30,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-24 08:28:30,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc01ip00')
2012-04-24 08:28:30,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-24 08:28:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 08:28:30,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:regulatory')
2012-04-24 08:28:30,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000103Csd00001657bc0Csc05i00')
2012-04-24 08:28:30,512 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-24 08:28:30,512 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000103Csd00001657bc04sc03i00')
2012-04-24 08:28:30,514 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 08:28:30,514 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,514 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 08:28:30,514 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00001033d00000194sv0000103Csd00001657bc0Csc03i30')
2012-04-24 08:28:30,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:30,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v000010ECd00005209sv0000103Csd00001657bcFFsc00i00')
2012-04-24 08:28:30,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2012-04-24 08:28:30,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000103Csd00001657bc07sc80i00')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:dock')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00001002d00006740sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00000116sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00001657bc02sc00i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000103Csd00001657bc06sc01i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc02ip00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1B:bd10/05/2011:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvr0589110014244710000620100:rvnHewlett-Packard:rn1657:rvr10.31:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000103Csd00001657bc01sc06i01')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v138Ap0018d0078dcFFdsc11dpFFicFFisc00ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0003v5986p02ACe0924-e0,1,kD4,ramlsfw')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:SYN1E47:SYN1E00:SYN0002:PNP0F13:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc01ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:regulatory')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000103Csd00001657bc0Csc05i00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000103Csd00001657bc04sc03i00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00001033d00000194sv0000103Csd00001657bc0Csc03i30')
2012-04-24 08:28:30,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 08:28:30,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-24 08:28:30,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v000010ECd00005209sv0000103Csd00001657bcFFsc00i00')
2012-04-24 08:28:30,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 08:28:30,566 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,566 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:32,474 DEBUG: Shutting down
```

---

### Post by LazyHobbit on 2012-04-25
Thanks for the help guys but it's been 2-3 days with only a few replies and nothing has helped; i'm not gonna put my computer under jeopardy for a dual boot.. It's not worth it to me. Who knows, maybe when i have extra money to buy a POS laptop that won't have driver compatibility issues (because hopefully ubuntu would have an inclusive list by then) i may return. Until then, thank you all for your help and keep up the good work. It's pretty sad that the manufacturers aren't trying to work more with Ubuntu / other linux OS's.

---

### Post by cmacia06 on 2012-04-25
Sorry to hear that your going to switch. My laptop gets very hot as well but I cant do much about it. Especially since it used a hybrid system which i believe switch between a intel one and amd. idk but it sucks. I kept the graphics driver that it came with because the fglrx causes to many problem. The wifi command that I had given you was for a dv7-6135dx so you might of had to mess with it to make it work. Sorry it took so long to reply i was busy but if you havent switch to windows or other os you can try to run sudo lshw look for network and then find the driver. It will say "driver=XXX" for its configuration. Then go to the file you created and replace iwlwifi with yours if it is not already there.

---

### Post by QIII on 2012-04-26
Speaking of Intel/AMD hybrid graphics issues, this might be helpful:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by morhook on 2012-05-01
It has worked awesome on my HP Pavilion DV6!! Now I can suspend without worries. Thanks a lot!

> **cmacia06 said:**
> Im new at using these forums so if i post something incorrectly sorry. OK I found the directory. 

Press ctrl+alt+t to open the terminal. Then type sudo gedit 

Make a file containing this in it.
[IMG]http://i45.tinypic.com/350a2xx.jpg[/IMG]

```

case "${1}" in
    resume|thaw)
        rmmod iwlwifi
	modprobe iwlwifi bt_coex_active=0
;;
esac

```

Then just save it to the folder "/etc/pm/sleep.d". Save it as a normal file with no extension. Name it what you like. Restart to make sure it all works. Suspend the resume and all should work.

---

### Post by morhook on 2012-05-01
If you are still with the Ubuntu boot, you could try to start the config of ATI although the install failed, you can type:

```
sudo aticonfig --initial

```

> **LazyHobbit said:**
> Here's the log that i could find; keep in mind that this log was created while trying to install the ATI graphics card driver in Ubuntu 12.04

```
2012-04-24 08:03:28,226 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0>
2012-04-24 08:03:29,746 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-24 08:03:29,917 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-24 08:03:29,917 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-24 08:03:29,970 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-24 08:03:29,993 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-24 08:03:30,024 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-24 08:03:30,025 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-24 08:03:30,025 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-24 08:03:30,051 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-24 08:03:30,059 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-24 08:03:30,059 DEBUG: fglrx.available: falling back to default
2012-04-24 08:03:30,167 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 08:03:30,174 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 08:03:30,182 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-24 08:03:30,182 DEBUG: fglrx.available: falling back to default
2012-04-24 08:03:30,239 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-24 08:03:30,239 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-24 08:03:30,271 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-24 08:03:30,296 DEBUG: Software modem not available
2012-04-24 08:03:30,297 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-24 08:03:30,306 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-24 08:03:30,307 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-24 08:03:30,307 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-24 08:03:30,307 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-24 08:03:30,315 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-24 08:03:30,316 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-24 08:03:30,344 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-24 08:03:30,345 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-24 08:03:30,395 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-24 08:03:30,396 DEBUG: Firmware for DVB cards not available
2012-04-24 08:03:30,396 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-24 08:03:30,408 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-24 08:03:30,416 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-24 08:03:30,467 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-24 08:03:30,468 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-24 08:03:30,481 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-24 08:03:30,489 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-24 08:03:30,491 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,492 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:03:30,498 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 08:03:30,507 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-24 08:03:30,508 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,508 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:03:30,515 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 08:03:30,523 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-24 08:03:30,524 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,524 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:03:30,531 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-24 08:03:30,540 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-24 08:03:30,541 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,541 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:03:30,548 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-24 08:03:30,556 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-24 08:03:30,558 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,558 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:03:30,564 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-24 08:03:30,572 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-24 08:03:30,573 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:03:30,574 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:03:30,574 DEBUG: all custom handlers loaded
2012-04-24 08:03:30,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 08:03:30,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 08:03:30,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:30,659 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,659 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:30,659 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 08:03:30,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 08:03:30,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000103Csd00001657bc07sc80i00')
2012-04-24 08:03:30,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-24 08:03:30,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:dock')
2012-04-24 08:03:30,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 08:03:30,840 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-24 08:03:30,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,840 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-24 08:03:30,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 08:03:30,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-24 08:03:30,849 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:30,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,849 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:30,849 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:30,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-24 08:03:30,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 08:03:30,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-24 08:03:30,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-24 08:03:30,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-24 08:03:30,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00001002d00006740sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:03:31,044 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-24 08:03:31,067 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,068 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,044 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:03:31,074 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-24 08:03:31,082 DEBUG: fglrx.available: falling back to default
2012-04-24 08:03:31,137 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,138 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,113 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:03:31,138 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-24 08:03:31,163 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,164 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,139 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-24 08:03:31,170 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 08:03:31,178 DEBUG: fglrx.available: falling back to default
2012-04-24 08:03:31,230 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,231 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,207 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-24 08:03:31,231 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-24 08:03:31,232 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-24 08:03:31,240 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2012-04-24 08:03:31,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-24 08:03:31,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 08:03:31,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 08:03:31,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00000116sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:03:31,249 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-04-24 08:03:31,249 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00001657bc02sc00i00')
2012-04-24 08:03:31,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-04-24 08:03:31,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 08:03:31,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000103Csd00001657bc06sc01i00')
2012-04-24 08:03:31,261 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-24 08:03:31,261 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc02ip00')
2012-04-24 08:03:31,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 08:03:31,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 08:03:31,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-24 08:03:31,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:03:31,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-24 08:03:31,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:03:31,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-24 08:03:31,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 08:03:31,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1B:bd10/05/2011:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvr0589110014244710000620100:rvnHewlett-Packard:rn1657:rvr10.31:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-24 08:03:31,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 08:03:31,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000103Csd00001657bc01sc06i01')
2012-04-24 08:03:31,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-24 08:03:31,276 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,277 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:31,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-04-24 08:03:31,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:03:31,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v138Ap0018d0078dcFFdsc11dpFFicFFisc00ip00')
2012-04-24 08:03:31,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:03:31,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0003v5986p02ACe0924-e0,1,kD4,ramlsfw')
2012-04-24 08:03:31,279 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,279 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:31,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:SYN1E47:SYN1E00:SYN0002:PNP0F13:')
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-24 08:03:31,280 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-04-24 08:03:31,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:03:31,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-24 08:03:31,280 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:31,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc01ip00')
2012-04-24 08:03:31,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-24 08:03:31,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 08:03:31,281 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'platform:regulatory')
2012-04-24 08:03:31,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000103Csd00001657bc0Csc05i00')
2012-04-24 08:03:31,283 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-24 08:03:31,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000103Csd00001657bc04sc03i00')
2012-04-24 08:03:31,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 08:03:31,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,285 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 08:03:31,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v00001033d00000194sv0000103Csd00001657bc0Csc03i30')
2012-04-24 08:03:31,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:03:31,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,292 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:03:31,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'pci:v000010ECd00005209sv0000103Csd00001657bcFFsc00i00')
2012-04-24 08:03:31,292 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2012-04-24 08:03:31,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x13a1ef0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000103Csd00001657bc07sc80i00')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:dock')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-24 08:03:31,292 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00001002d00006740sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00000116sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00001657bc02sc00i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000103Csd00001657bc06sc01i00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc02ip00')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1B:bd10/05/2011:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvr0589110014244710000620100:rvnHewlett-Packard:rn1657:rvr10.31:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000103Csd00001657bc01sc06i01')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-24 08:03:31,293 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v138Ap0018d0078dcFFdsc11dpFFicFFisc00ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0003v5986p02ACe0924-e0,1,kD4,ramlsfw')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:SYN1E47:SYN1E00:SYN0002:PNP0F13:')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc01ip00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'platform:regulatory')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000103Csd00001657bc0Csc05i00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000103Csd00001657bc04sc03i00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v00001033d00000194sv0000103Csd00001657bc0Csc03i30')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'pci:v000010ECd00005209sv0000103Csd00001657bcFFsc00i00')
2012-04-24 08:03:31,294 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x170e440> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 08:03:31,371 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,371 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,409 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,409 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,444 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,445 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,497 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,498 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,532 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,532 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,587 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,588 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,658 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,659 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,710 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,711 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:31,744 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,745 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:31,797 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:31,798 DEBUG: fglrx is not the alternative in use
2012-04-24 08:03:38,607 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-24 08:03:38,608 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:03:42,807 DEBUG: Installing package: fglrx-updates
2012-04-24 08:03:43,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.000000
2012-04-24 08:03:43,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.000000
2012-04-24 08:03:43,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.000000
2012-04-24 08:03:43,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.000000
2012-04-24 08:03:44,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.001570
2012-04-24 08:03:44,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.015539
2012-04-24 08:03:45,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.035494
2012-04-24 08:03:45,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.045472
2012-04-24 08:03:46,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.055450
2012-04-24 08:03:46,782 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.071415
2012-04-24 08:03:47,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.087379
2012-04-24 08:03:47,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.095361
2012-04-24 08:03:47,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.100698
2012-04-24 08:03:47,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.100918
2012-04-24 08:03:48,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.104909
2012-04-24 08:03:48,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.108900
2012-04-24 08:03:49,315 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.114887
2012-04-24 08:03:49,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.124865
2012-04-24 08:03:50,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.134843
2012-04-24 08:03:50,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.144821
2012-04-24 08:03:51,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.154798
2012-04-24 08:03:51,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.156794
2012-04-24 08:03:52,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.166772
2012-04-24 08:03:52,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.168767
2012-04-24 08:03:53,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.168767
2012-04-24 08:03:53,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.170763
2012-04-24 08:03:54,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.174754
2012-04-24 08:03:54,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.174754
2012-04-24 08:03:55,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.174754
2012-04-24 08:03:55,833 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.178745
2012-04-24 08:03:56,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.182736
2012-04-24 08:03:56,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.184732
2012-04-24 08:03:57,337 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.186728
2012-04-24 08:03:57,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.190719
2012-04-24 08:03:58,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.196705
2012-04-24 08:03:58,841 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.202692
2012-04-24 08:03:59,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.212670
2012-04-24 08:03:59,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.218657
2012-04-24 08:04:00,345 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.224643
2012-04-24 08:04:00,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.232626
2012-04-24 08:04:01,348 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.240608
2012-04-24 08:04:01,849 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.248590
2012-04-24 08:04:02,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.254577
2012-04-24 08:04:02,852 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.260564
2012-04-24 08:04:03,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.268546
2012-04-24 08:04:03,855 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.278524
2012-04-24 08:04:04,356 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.294488
2012-04-24 08:04:04,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.318435
2012-04-24 08:04:05,359 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.324422
2012-04-24 08:04:05,860 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.334400
2012-04-24 08:04:06,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.334400
2012-04-24 08:04:06,863 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.334400
2012-04-24 08:04:07,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.336395
2012-04-24 08:04:07,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.338391
2012-04-24 08:04:08,367 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.338391
2012-04-24 08:04:08,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.338391
2012-04-24 08:04:09,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.338391
2012-04-24 08:04:09,871 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.340386
2012-04-24 08:04:10,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.340386
2012-04-24 08:04:10,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.342382
2012-04-24 08:04:11,375 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.344377
2012-04-24 08:04:11,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.348369
2012-04-24 08:04:12,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.354355
2012-04-24 08:04:12,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.366329
2012-04-24 08:04:13,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.374311
2012-04-24 08:04:13,882 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.384289
2012-04-24 08:04:14,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.394267
2012-04-24 08:04:14,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.410231
2012-04-24 08:04:15,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.418214
2012-04-24 08:04:15,888 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.424200
2012-04-24 08:04:16,389 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.440165
2012-04-24 08:04:16,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.452138
2012-04-24 08:04:17,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.464112
2012-04-24 08:04:17,893 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.474089
2012-04-24 08:04:18,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.484067
2012-04-24 08:04:18,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.494045
2012-04-24 08:04:19,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.504023
2012-04-24 08:04:19,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.517992
2012-04-24 08:04:20,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.539943
2012-04-24 08:04:20,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.573868
2012-04-24 08:04:21,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.597815
2012-04-24 08:04:21,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.605797
2012-04-24 08:04:22,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.609788
2012-04-24 08:04:22,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.615775
2012-04-24 08:04:23,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.623757
2012-04-24 08:04:23,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.629744
2012-04-24 08:04:24,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.637726
2012-04-24 08:04:24,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.647704
2012-04-24 08:04:25,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.657682
2012-04-24 08:04:25,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.669655
2012-04-24 08:04:26,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.683624
2012-04-24 08:04:26,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.693602
2012-04-24 08:04:27,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.707571
2012-04-24 08:04:27,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.723535
2012-04-24 08:04:28,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.739500
2012-04-24 08:04:28,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.753469
2012-04-24 08:04:29,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.769434
2012-04-24 08:04:29,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.775420
2012-04-24 08:04:30,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.779411
2012-04-24 08:04:30,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.785398
2012-04-24 08:04:31,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.801363
2012-04-24 08:04:31,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.813336
2012-04-24 08:04:32,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.829301
2012-04-24 08:04:32,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.845265
2012-04-24 08:04:33,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.859234
2012-04-24 08:04:33,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.871207
2012-04-24 08:04:34,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.877194
2012-04-24 08:04:34,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.885176
2012-04-24 08:04:35,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.903137
2012-04-24 08:04:35,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.919101
2012-04-24 08:04:36,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.935066
2012-04-24 08:04:36,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.957017
2012-04-24 08:04:37,447 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.970986
2012-04-24 08:04:37,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 0.984955
2012-04-24 08:04:38,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.000919
2012-04-24 08:04:38,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.016884
2012-04-24 08:04:39,451 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.036840
2012-04-24 08:04:39,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.066773
2012-04-24 08:04:40,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.100698
2012-04-24 08:04:40,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.126640
2012-04-24 08:04:41,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.158569
2012-04-24 08:04:41,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.192494
2012-04-24 08:04:42,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.228414
2012-04-24 08:04:42,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.254357
2012-04-24 08:04:43,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.276308
2012-04-24 08:04:43,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.286286
2012-04-24 08:04:44,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.312228
2012-04-24 08:04:44,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.318215
2012-04-24 08:04:45,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.326197
2012-04-24 08:04:45,969 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.338170
2012-04-24 08:04:46,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.354135
2012-04-24 08:04:46,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.374091
2012-04-24 08:04:47,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.382073
2012-04-24 08:04:47,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.392051
2012-04-24 08:04:48,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.404024
2012-04-24 08:04:48,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.425975
2012-04-24 08:04:49,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.447927
2012-04-24 08:04:49,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.463891
2012-04-24 08:04:50,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.483847
2012-04-24 08:04:50,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.499812
2012-04-24 08:04:51,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.517772
2012-04-24 08:04:51,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.525754
2012-04-24 08:04:52,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.535732
2012-04-24 08:04:52,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.549701
2012-04-24 08:04:53,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.565665
2012-04-24 08:04:53,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.599590
2012-04-24 08:04:54,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.609568
2012-04-24 08:04:54,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.619546
2012-04-24 08:04:55,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.631519
2012-04-24 08:04:55,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.645488
2012-04-24 08:04:56,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.663448
2012-04-24 08:04:56,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.677417
2012-04-24 08:04:57,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.717328
2012-04-24 08:04:58,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.733293
2012-04-24 08:04:58,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.755244
2012-04-24 08:04:59,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.759235
2012-04-24 08:04:59,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.789169
2012-04-24 08:05:00,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.799147
2012-04-24 08:05:00,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.815111
2012-04-24 08:05:01,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.835067
2012-04-24 08:05:01,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.845045
2012-04-24 08:05:02,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.855023
2012-04-24 08:05:02,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.865000
2012-04-24 08:05:03,014 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.878969
2012-04-24 08:05:03,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.892938
2012-04-24 08:05:04,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.906907
2012-04-24 08:05:04,519 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.918881
2012-04-24 08:05:05,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.928859
2012-04-24 08:05:05,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.932850
2012-04-24 08:05:06,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.938837
2012-04-24 08:05:06,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.948814
2012-04-24 08:05:07,025 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.962783
2012-04-24 08:05:07,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.976752
2012-04-24 08:05:08,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 1.990721
2012-04-24 08:05:08,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.004690
2012-04-24 08:05:09,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.028637
2012-04-24 08:05:09,532 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.048593
2012-04-24 08:05:10,033 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.064557
2012-04-24 08:05:10,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.072540
2012-04-24 08:05:11,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.074535
2012-04-24 08:05:11,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.076531
2012-04-24 08:05:12,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.080522
2012-04-24 08:05:12,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.086509
2012-04-24 08:05:13,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.096486
2012-04-24 08:05:13,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.102473
2012-04-24 08:05:14,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.110455
2012-04-24 08:05:14,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.118438
2012-04-24 08:05:15,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.134402
2012-04-24 08:05:15,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.150367
2012-04-24 08:05:16,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.170322
2012-04-24 08:05:16,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.196265
2012-04-24 08:05:17,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.234181
2012-04-24 08:05:17,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.244158
2012-04-24 08:05:18,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.254136
2012-04-24 08:05:18,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.274092
2012-04-24 08:05:19,058 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.312008
2012-04-24 08:05:19,559 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.329968
2012-04-24 08:05:20,061 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.345932
2012-04-24 08:05:20,562 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.359901
2012-04-24 08:05:21,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.391831
2012-04-24 08:05:21,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.421764
2012-04-24 08:05:22,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.439724
2012-04-24 08:05:22,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.445711
2012-04-24 08:05:23,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.457684
2012-04-24 08:05:23,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.465667
2012-04-24 08:05:24,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.471653
2012-04-24 08:05:24,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.487618
2012-04-24 08:05:25,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.501587
2012-04-24 08:05:25,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.515556
2012-04-24 08:05:26,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.529525
2012-04-24 08:05:26,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.547485
2012-04-24 08:05:27,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.563449
2012-04-24 08:05:27,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.585401
2012-04-24 08:05:28,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.611343
2012-04-24 08:05:28,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.621321
2012-04-24 08:05:29,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.633294
2012-04-24 08:05:29,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.657241
2012-04-24 08:05:30,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.683183
2012-04-24 08:05:30,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.711121
2012-04-24 08:05:31,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.741055
2012-04-24 08:05:31,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.774980
2012-04-24 08:05:32,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.812895
2012-04-24 08:05:32,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.844825
2012-04-24 08:05:33,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.874758
2012-04-24 08:05:33,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.922652
2012-04-24 08:05:34,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.954581
2012-04-24 08:05:34,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 2.984514
2012-04-24 08:05:35,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.010457
2012-04-24 08:05:35,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.020435
2012-04-24 08:05:36,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.030412
2012-04-24 08:05:36,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.046377
2012-04-24 08:05:37,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.068328
2012-04-24 08:05:37,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.104248
2012-04-24 08:05:38,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.128195
2012-04-24 08:05:38,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.156133
2012-04-24 08:05:39,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.180080
2012-04-24 08:05:39,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.202031
2012-04-24 08:05:40,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.208018
2012-04-24 08:05:40,615 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.216000
2012-04-24 08:05:41,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.227974
2012-04-24 08:05:41,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.243938
2012-04-24 08:05:42,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.271876
2012-04-24 08:05:42,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.301810
2012-04-24 08:05:43,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.329748
2012-04-24 08:05:43,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.357686
2012-04-24 08:05:44,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.377641
2012-04-24 08:05:44,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.401588
2012-04-24 08:05:45,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.423539
2012-04-24 08:05:45,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.447486
2012-04-24 08:05:46,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.473429
2012-04-24 08:05:46,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.537287
2012-04-24 08:05:47,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.607132
2012-04-24 08:05:47,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.621101
2012-04-24 08:05:48,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.625092
2012-04-24 08:05:48,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.629083
2012-04-24 08:05:49,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.637065
2012-04-24 08:05:49,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.645047
2012-04-24 08:05:50,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.651034
2012-04-24 08:05:50,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.657021
2012-04-24 08:05:51,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.666999
2012-04-24 08:05:51,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.676976
2012-04-24 08:05:52,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.684959
2012-04-24 08:05:52,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.694937
2012-04-24 08:05:53,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.706910
2012-04-24 08:05:53,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.728861
2012-04-24 08:05:54,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.746821
2012-04-24 08:05:54,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.784737
2012-04-24 08:05:55,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.838618
2012-04-24 08:05:55,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.876533
2012-04-24 08:05:56,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 3.938396
2012-04-24 08:05:56,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.018219
2012-04-24 08:05:57,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.068108
2012-04-24 08:05:57,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.108019
2012-04-24 08:05:58,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.161900
2012-04-24 08:05:58,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.235736
2012-04-24 08:05:59,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.315558
2012-04-24 08:05:59,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.401368
2012-04-24 08:06:00,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.449261
2012-04-24 08:06:00,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.509128
2012-04-24 08:06:01,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.574982
2012-04-24 08:06:01,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.640836
2012-04-24 08:06:02,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.700703
2012-04-24 08:06:02,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.710681
2012-04-24 08:06:03,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.762566
2012-04-24 08:06:03,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.794495
2012-04-24 08:06:04,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.810459
2012-04-24 08:06:04,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.832411
2012-04-24 08:06:05,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.850371
2012-04-24 08:06:05,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.874317
2012-04-24 08:06:06,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.894273
2012-04-24 08:06:06,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.914229
2012-04-24 08:06:07,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.958131
2012-04-24 08:06:07,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 4.984074
2012-04-24 08:06:08,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.016003
2012-04-24 08:06:08,690 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.043941
2012-04-24 08:06:09,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.083852
2012-04-24 08:06:09,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.117777
2012-04-24 08:06:10,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.163675
2012-04-24 08:06:10,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.231524
2012-04-24 08:06:11,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.307356
2012-04-24 08:06:11,698 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.407134
2012-04-24 08:06:12,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.467001
2012-04-24 08:06:12,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.540837
2012-04-24 08:06:13,202 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.616669
2012-04-24 08:06:13,703 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.642611
2012-04-24 08:06:14,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.660571
2012-04-24 08:06:14,706 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.680527
2012-04-24 08:06:15,207 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.696492
2012-04-24 08:06:15,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.726425
2012-04-24 08:06:16,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.752367
2012-04-24 08:06:16,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.778310
2012-04-24 08:06:17,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.786292
2012-04-24 08:06:17,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.798266
2012-04-24 08:06:18,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.816226
2012-04-24 08:06:18,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.820217
2012-04-24 08:06:19,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.832190
2012-04-24 08:06:19,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.836181
2012-04-24 08:06:20,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.840172
2012-04-24 08:06:20,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.840172
2012-04-24 08:06:21,223 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.842168
2012-04-24 08:06:21,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.844164
2012-04-24 08:06:22,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.844164
2012-04-24 08:06:22,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.848155
2012-04-24 08:06:23,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.854141
2012-04-24 08:06:23,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.860128
2012-04-24 08:06:24,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.860128
2012-04-24 08:06:24,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.872102
2012-04-24 08:06:25,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.878088
2012-04-24 08:06:25,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.882079
2012-04-24 08:06:26,237 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.888066
2012-04-24 08:06:26,738 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.894053
2012-04-24 08:06:27,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.900040
2012-04-24 08:06:27,741 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.908022
2012-04-24 08:06:28,242 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.921991
2012-04-24 08:06:28,744 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.935960
2012-04-24 08:06:29,245 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.949929
2012-04-24 08:06:29,746 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.967889
2012-04-24 08:06:30,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 5.993831
2012-04-24 08:06:30,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.009796
2012-04-24 08:06:31,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.025760
2012-04-24 08:06:31,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.041725
2012-04-24 08:06:32,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.061681
2012-04-24 08:06:32,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.071658
2012-04-24 08:06:33,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.087623
2012-04-24 08:06:33,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.103587
2012-04-24 08:06:34,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.119552
2012-04-24 08:06:34,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.135517
2012-04-24 08:06:35,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.151481
2012-04-24 08:06:35,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.167446
2012-04-24 08:06:36,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.177424
2012-04-24 08:06:36,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.185406
2012-04-24 08:06:37,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.199375
2012-04-24 08:06:37,768 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.215339
2012-04-24 08:06:38,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.231304
2012-04-24 08:06:38,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.251260
2012-04-24 08:06:39,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.273211
2012-04-24 08:06:39,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.295162
2012-04-24 08:06:40,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.313122
2012-04-24 08:06:40,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.353034
2012-04-24 08:06:41,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.380971
2012-04-24 08:06:41,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.410905
2012-04-24 08:06:42,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.440839
2012-04-24 08:06:42,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.484741
2012-04-24 08:06:43,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.498710
2012-04-24 08:06:43,794 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.512679
2012-04-24 08:06:44,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.536626
2012-04-24 08:06:44,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.572546
2012-04-24 08:06:45,297 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.600484
2012-04-24 08:06:45,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.662347
2012-04-24 08:06:46,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.724209
2012-04-24 08:06:46,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.772103
2012-04-24 08:06:47,303 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.819997
2012-04-24 08:06:47,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.839952
2012-04-24 08:06:48,306 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.861903
2012-04-24 08:06:48,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.895828
2012-04-24 08:06:49,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.933744
2012-04-24 08:06:49,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 6.973655
2012-04-24 08:06:50,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.007580
2012-04-24 08:06:50,813 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.055474
2012-04-24 08:06:51,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.081416
2012-04-24 08:06:51,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.109354
2012-04-24 08:06:52,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.157248
2012-04-24 08:06:52,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.195163
2012-04-24 08:06:53,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.235075
2012-04-24 08:06:53,821 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.255030
2012-04-24 08:06:54,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.268999
2012-04-24 08:06:54,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.276982
2012-04-24 08:06:55,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.286959
2012-04-24 08:06:55,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.296937
2012-04-24 08:06:56,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.308911
2012-04-24 08:06:56,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.322880
2012-04-24 08:06:57,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.338844
2012-04-24 08:06:57,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.362791
2012-04-24 08:06:58,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.388733
2012-04-24 08:06:58,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.416671
2012-04-24 08:06:59,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.456583
2012-04-24 08:06:59,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.532414
2012-04-24 08:07:00,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.598268
2012-04-24 08:07:00,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.688069
2012-04-24 08:07:01,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.799821
2012-04-24 08:07:01,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.941506
2012-04-24 08:07:02,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 7.993391
2012-04-24 08:07:02,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.087182
2012-04-24 08:07:03,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.182970
2012-04-24 08:07:03,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.340620
2012-04-24 08:07:04,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.464345
2012-04-24 08:07:04,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.568114
2012-04-24 08:07:05,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.619999
2012-04-24 08:07:05,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.699822
2012-04-24 08:07:06,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.741729
2012-04-24 08:07:06,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.747715
2012-04-24 08:07:07,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.821551
2012-04-24 08:07:07,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.869445
2012-04-24 08:07:08,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.907361
2012-04-24 08:07:08,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.949268
2012-04-24 08:07:09,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 8.973215
2012-04-24 08:07:09,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.001153
2012-04-24 08:07:10,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.025099
2012-04-24 08:07:10,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.059024
2012-04-24 08:07:11,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.102927
2012-04-24 08:07:11,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.144834
2012-04-24 08:07:12,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.168780
2012-04-24 08:07:12,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.186740
2012-04-24 08:07:13,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.200709
2012-04-24 08:07:13,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.218670
2012-04-24 08:07:14,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.228647
2012-04-24 08:07:14,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.236630
2012-04-24 08:07:15,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.254590
2012-04-24 08:07:15,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.278537
2012-04-24 08:07:16,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.296497
2012-04-24 08:07:16,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.304479
2012-04-24 08:07:17,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.314457
2012-04-24 08:07:17,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.328426
2012-04-24 08:07:18,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.340399
2012-04-24 08:07:18,888 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.354368
2012-04-24 08:07:19,389 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.368337
2012-04-24 08:07:19,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.400266
2012-04-24 08:07:20,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.418226
2012-04-24 08:07:20,893 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.448160
2012-04-24 08:07:21,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.486076
2012-04-24 08:07:21,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.506031
2012-04-24 08:07:22,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.521996
2012-04-24 08:07:22,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.539956
2012-04-24 08:07:23,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.561907
2012-04-24 08:07:23,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.597828
2012-04-24 08:07:24,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.635743
2012-04-24 08:07:24,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.651708
2012-04-24 08:07:25,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.657695
2012-04-24 08:07:25,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.665677
2012-04-24 08:07:26,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.671664
2012-04-24 08:07:26,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.671664
2012-04-24 08:07:27,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.671664
2012-04-24 08:07:27,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.673659
2012-04-24 08:07:28,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.675655
2012-04-24 08:07:28,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.675655
2012-04-24 08:07:29,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.683637
2012-04-24 08:07:29,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.687628
2012-04-24 08:07:30,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.687628
2012-04-24 08:07:30,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.699602
2012-04-24 08:07:31,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.705588
2012-04-24 08:07:31,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.713570
2012-04-24 08:07:32,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.721553
2012-04-24 08:07:32,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.729535
2012-04-24 08:07:33,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.737517
2012-04-24 08:07:33,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.755477
2012-04-24 08:07:34,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.765455
2012-04-24 08:07:34,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.777429
2012-04-24 08:07:35,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.791398
2012-04-24 08:07:35,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.809358
2012-04-24 08:07:36,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.827318
2012-04-24 08:07:36,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.837296
2012-04-24 08:07:37,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.847274
2012-04-24 08:07:37,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.877207
2012-04-24 08:07:38,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.901154
2012-04-24 08:07:38,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.927096
2012-04-24 08:07:39,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.953039
2012-04-24 08:07:39,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.965012
2012-04-24 08:07:40,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.969003
2012-04-24 08:07:40,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.970999
2012-04-24 08:07:41,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.970999
2012-04-24 08:07:41,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.972994
2012-04-24 08:07:42,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.976986
2012-04-24 08:07:42,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.982972
2012-04-24 08:07:43,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.986963
2012-04-24 08:07:43,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 9.992950
2012-04-24 08:07:44,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.000932
2012-04-24 08:07:44,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.008915
2012-04-24 08:07:45,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.018892
2012-04-24 08:07:45,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.022884
2012-04-24 08:07:46,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.028870
2012-04-24 08:07:46,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.034857
2012-04-24 08:07:47,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.042839
2012-04-24 08:07:47,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.054813
2012-04-24 08:07:48,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.074768
2012-04-24 08:07:48,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.086742
2012-04-24 08:07:49,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.098715
2012-04-24 08:07:49,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.116675
2012-04-24 08:07:50,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.132640
2012-04-24 08:07:50,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.152596
2012-04-24 08:07:51,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.178538
2012-04-24 08:07:51,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.206476
2012-04-24 08:07:52,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.248383
2012-04-24 08:07:52,978 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.256365
2012-04-24 08:07:53,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.258361
2012-04-24 08:07:53,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.262352
2012-04-24 08:07:54,482 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.262352
2012-04-24 08:07:54,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.264347
2012-04-24 08:07:55,485 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.264347
2012-04-24 08:07:55,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.266343
2012-04-24 08:07:56,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.270334
2012-04-24 08:07:56,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.272330
2012-04-24 08:07:57,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.274325
2012-04-24 08:07:57,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.278316
2012-04-24 08:07:58,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.284303
2012-04-24 08:07:58,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.296276
2012-04-24 08:07:59,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.304259
2012-04-24 08:07:59,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.314237
2012-04-24 08:08:00,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.322219
2012-04-24 08:08:01,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.328206
2012-04-24 08:08:01,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.338183
2012-04-24 08:08:02,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.350157
2012-04-24 08:08:02,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.362130
2012-04-24 08:08:03,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.382086
2012-04-24 08:08:03,507 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.398050
2012-04-24 08:08:04,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.410024
2012-04-24 08:08:04,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.423993
2012-04-24 08:08:05,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.441953
2012-04-24 08:08:05,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.449935
2012-04-24 08:08:06,014 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.477873
2012-04-24 08:08:06,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.491842
2012-04-24 08:08:07,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.501820
2012-04-24 08:08:07,518 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.511798
2012-04-24 08:08:08,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.535745
2012-04-24 08:08:08,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.545722
2012-04-24 08:08:09,022 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.561687
2012-04-24 08:08:09,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.583638
2012-04-24 08:08:10,025 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.611576
2012-04-24 08:08:10,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.647496
2012-04-24 08:08:11,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.693395
2012-04-24 08:08:11,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.749270
2012-04-24 08:08:12,030 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.801155
2012-04-24 08:08:12,532 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 10.861022
2012-04-24 08:08:13,033 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.034637
2012-04-24 08:08:13,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.138406
2012-04-24 08:08:14,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.210247
2012-04-24 08:08:14,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.242176
2012-04-24 08:08:15,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.278096
2012-04-24 08:08:15,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.333972
2012-04-24 08:08:16,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.335967
2012-04-24 08:08:16,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.365901
2012-04-24 08:08:17,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.381866
2012-04-24 08:08:17,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.393839
2012-04-24 08:08:18,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.411799
2012-04-24 08:08:18,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.421777
2012-04-24 08:08:19,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.435746
2012-04-24 08:08:19,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.449715
2012-04-24 08:08:20,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.457697
2012-04-24 08:08:20,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.461688
2012-04-24 08:08:21,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.465679
2012-04-24 08:08:21,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.471666
2012-04-24 08:08:22,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.473662
2012-04-24 08:08:22,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.475657
2012-04-24 08:08:23,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.479648
2012-04-24 08:08:23,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.479648
2012-04-24 08:08:24,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.481644
2012-04-24 08:08:24,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.483640
2012-04-24 08:08:25,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.483640
2012-04-24 08:08:25,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.487631
2012-04-24 08:08:26,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.493617
2012-04-24 08:08:26,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.497609
2012-04-24 08:08:27,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.499604
2012-04-24 08:08:27,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.499604
2012-04-24 08:08:28,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.499604
2012-04-24 08:08:28,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.503595
2012-04-24 08:08:29,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.507586
2012-04-24 08:08:29,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.513573
2012-04-24 08:08:30,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.519560
2012-04-24 08:08:30,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.521555
2012-04-24 08:08:31,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.523551
2012-04-24 08:08:31,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.527542
2012-04-24 08:08:32,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.533529
2012-04-24 08:08:32,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.539515
2012-04-24 08:08:33,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.545502
2012-04-24 08:08:33,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.549493
2012-04-24 08:08:34,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.567453
2012-04-24 08:08:34,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.581422
2012-04-24 08:08:35,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.599383
2012-04-24 08:08:35,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.619338
2012-04-24 08:08:36,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.647276
2012-04-24 08:08:36,597 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.653263
2012-04-24 08:08:37,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.661245
2012-04-24 08:08:37,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.673219
2012-04-24 08:08:38,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.685192
2012-04-24 08:08:38,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.693174
2012-04-24 08:08:39,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.703152
2012-04-24 08:08:39,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.727099
2012-04-24 08:08:40,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.727099
2012-04-24 08:08:40,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.747055
2012-04-24 08:08:41,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.757032
2012-04-24 08:08:41,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.767010
2012-04-24 08:08:42,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.778984
2012-04-24 08:08:42,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.790957
2012-04-24 08:08:43,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.804926
2012-04-24 08:08:43,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.824882
2012-04-24 08:08:44,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.838851
2012-04-24 08:08:44,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.860802
2012-04-24 08:08:45,121 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.884749
2012-04-24 08:08:45,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.912687
2012-04-24 08:08:46,124 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.944616
2012-04-24 08:08:46,625 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 11.988518
2012-04-24 08:08:47,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.026434
2012-04-24 08:08:47,628 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.048385
2012-04-24 08:08:48,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.082310
2012-04-24 08:08:48,631 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.124217
2012-04-24 08:08:49,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.170115
2012-04-24 08:08:49,633 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.239960
2012-04-24 08:08:50,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.241955
2012-04-24 08:08:50,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.339738
2012-04-24 08:08:51,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.383641
2012-04-24 08:08:51,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.419561
2012-04-24 08:08:52,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.469450
2012-04-24 08:08:52,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.521335
2012-04-24 08:08:53,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.573220
2012-04-24 08:08:53,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.607144
2012-04-24 08:08:54,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.627100
2012-04-24 08:08:54,647 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.639074
2012-04-24 08:08:55,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.645060
2012-04-24 08:08:55,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.649051
2012-04-24 08:08:56,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.659029
2012-04-24 08:08:56,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.669007
2012-04-24 08:08:57,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.680981
2012-04-24 08:08:57,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.690958
2012-04-24 08:08:58,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.700936
2012-04-24 08:08:58,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.714905
2012-04-24 08:08:59,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.728874
2012-04-24 08:08:59,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.742843
2012-04-24 08:09:00,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.750825
2012-04-24 08:09:00,663 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.760803
2012-04-24 08:09:01,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.782754
2012-04-24 08:09:01,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.804706
2012-04-24 08:09:02,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.824661
2012-04-24 08:09:02,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.842622
2012-04-24 08:09:03,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.852599
2012-04-24 08:09:03,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.860582
2012-04-24 08:09:04,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.872555
2012-04-24 08:09:04,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.886524
2012-04-24 08:09:05,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.906480
2012-04-24 08:09:05,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.932422
2012-04-24 08:09:06,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.948387
2012-04-24 08:09:06,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.968342
2012-04-24 08:09:07,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 12.986302
2012-04-24 08:09:07,683 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.006258
2012-04-24 08:09:08,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.016236
2012-04-24 08:09:08,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.026214
2012-04-24 08:09:09,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.044174
2012-04-24 08:09:09,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.064130
2012-04-24 08:09:10,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.082090
2012-04-24 08:09:10,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.090072
2012-04-24 08:09:11,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.100050
2012-04-24 08:09:11,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.116014
2012-04-24 08:09:12,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.133975
2012-04-24 08:09:12,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.151935
2012-04-24 08:09:13,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.155926
2012-04-24 08:09:13,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.157921
2012-04-24 08:09:14,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.159917
2012-04-24 08:09:14,703 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.163908
2012-04-24 08:09:15,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.169895
2012-04-24 08:09:15,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.175881
2012-04-24 08:09:16,207 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.185859
2012-04-24 08:09:16,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.193842
2012-04-24 08:09:17,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.195837
2012-04-24 08:09:17,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.197833
2012-04-24 08:09:18,212 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.201824
2012-04-24 08:09:18,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.207811
2012-04-24 08:09:19,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.213797
2012-04-24 08:09:19,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.215793
2012-04-24 08:09:20,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.217788
2012-04-24 08:09:20,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.217788
2012-04-24 08:09:21,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.221780
2012-04-24 08:09:21,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.233753
2012-04-24 08:09:22,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.241735
2012-04-24 08:09:22,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.251713
2012-04-24 08:09:23,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.259695
2012-04-24 08:09:23,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.269673
2012-04-24 08:09:24,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.279651
2012-04-24 08:09:24,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.287633
2012-04-24 08:09:25,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.293620
2012-04-24 08:09:25,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.299607
2012-04-24 08:09:26,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.303598
2012-04-24 08:09:26,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.307589
2012-04-24 08:09:27,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.313576
2012-04-24 08:09:27,738 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.315571
2012-04-24 08:09:28,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.315571
2012-04-24 08:09:28,741 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.319562
2012-04-24 08:09:29,242 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.325549
2012-04-24 08:09:29,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.331536
2012-04-24 08:09:30,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.339518
2012-04-24 08:09:30,746 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.351491
2012-04-24 08:09:31,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.373443
2012-04-24 08:09:31,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.393398
2012-04-24 08:09:32,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.401381
2012-04-24 08:09:32,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.413354
2012-04-24 08:09:33,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.427323
2012-04-24 08:09:33,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.445283
2012-04-24 08:09:34,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.467234
2012-04-24 08:09:34,756 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.467234
2012-04-24 08:09:35,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.469230
2012-04-24 08:09:35,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.471226
2012-04-24 08:09:36,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.475217
2012-04-24 08:09:36,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.481203
2012-04-24 08:09:37,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.491181
2012-04-24 08:09:37,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.503155
2012-04-24 08:09:38,266 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.521115
2012-04-24 08:09:38,768 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.539075
2012-04-24 08:09:39,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.559031
2012-04-24 08:09:39,770 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.580982
2012-04-24 08:09:40,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.602933
2012-04-24 08:09:40,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.644840
2012-04-24 08:09:41,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.666791
2012-04-24 08:09:41,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.694729
2012-04-24 08:09:42,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.716680
2012-04-24 08:09:42,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.752601
2012-04-24 08:09:43,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.766570
2012-04-24 08:09:43,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.820450
2012-04-24 08:09:44,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.838410
2012-04-24 08:09:44,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.866348
2012-04-24 08:09:45,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.896282
2012-04-24 08:09:45,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.914242
2012-04-24 08:09:46,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.944175
2012-04-24 08:09:46,790 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.966126
2012-04-24 08:09:47,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 13.990073
2012-04-24 08:09:47,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.018011
2012-04-24 08:09:48,294 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.051936
2012-04-24 08:09:48,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.087856
2012-04-24 08:09:49,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.137745
2012-04-24 08:09:49,798 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.169674
2012-04-24 08:09:50,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.189630
2012-04-24 08:09:50,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.249497
2012-04-24 08:09:51,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.309364
2012-04-24 08:09:51,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.357258
2012-04-24 08:09:52,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.399165
2012-04-24 08:09:52,806 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.413134
2012-04-24 08:09:53,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.435085
2012-04-24 08:09:53,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.451050
2012-04-24 08:09:54,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.455041
2012-04-24 08:09:54,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.457036
2012-04-24 08:09:55,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.459032
2012-04-24 08:09:55,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.463023
2012-04-24 08:09:56,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.474996
2012-04-24 08:09:56,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.480983
2012-04-24 08:09:57,319 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.486970
2012-04-24 08:09:57,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.494952
2012-04-24 08:09:58,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.506925
2012-04-24 08:09:58,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.522890
2012-04-24 08:09:59,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.536859
2012-04-24 08:09:59,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.556815
2012-04-24 08:10:00,328 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.574775
2012-04-24 08:10:00,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.592735
2012-04-24 08:10:01,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.604708
2012-04-24 08:10:01,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.632646
2012-04-24 08:10:02,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.642624
2012-04-24 08:10:02,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.654598
2012-04-24 08:10:03,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.672558
2012-04-24 08:10:03,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.688522
2012-04-24 08:10:04,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.704487
2012-04-24 08:10:04,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.724442
2012-04-24 08:10:05,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.740407
2012-04-24 08:10:05,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.764354
2012-04-24 08:10:06,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.800274
2012-04-24 08:10:06,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.824221
2012-04-24 08:10:07,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.832203
2012-04-24 08:10:07,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.842181
2012-04-24 08:10:08,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.854154
2012-04-24 08:10:08,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.876106
2012-04-24 08:10:09,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.902048
2012-04-24 08:10:09,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.929986
2012-04-24 08:10:10,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.953933
2012-04-24 08:10:10,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 14.977880
2012-04-24 08:10:11,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.001826
2012-04-24 08:10:11,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.019787
2012-04-24 08:10:12,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.029764
2012-04-24 08:10:12,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.063689
2012-04-24 08:10:13,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.083645
2012-04-24 08:10:13,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.095618
2012-04-24 08:10:14,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.111583
2012-04-24 08:10:14,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.127547
2012-04-24 08:10:15,369 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.151494
2012-04-24 08:10:15,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.173445
2012-04-24 08:10:16,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.177436
2012-04-24 08:10:16,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.181428
2012-04-24 08:10:17,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.187414
2012-04-24 08:10:17,876 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.189410
2012-04-24 08:10:18,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.191405
2012-04-24 08:10:18,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.195397
2012-04-24 08:10:19,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.195397
2012-04-24 08:10:19,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.195397
2012-04-24 08:10:20,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.197392
2012-04-24 08:10:20,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.199388
2012-04-24 08:10:21,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.199388
2012-04-24 08:10:21,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.203379
2012-04-24 08:10:22,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.213357
2012-04-24 08:10:22,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.219343
2012-04-24 08:10:23,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.225330
2012-04-24 08:10:23,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.231317
2012-04-24 08:10:24,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.239299
2012-04-24 08:10:24,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.251272
2012-04-24 08:10:25,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.267237
2012-04-24 08:10:25,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.287193
2012-04-24 08:10:26,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.307148
2012-04-24 08:10:26,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.333091
2012-04-24 08:10:27,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.351051
2012-04-24 08:10:27,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.371007
2012-04-24 08:10:28,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.396949
2012-04-24 08:10:28,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.410918
2012-04-24 08:10:29,406 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.416905
2012-04-24 08:10:29,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.428878
2012-04-24 08:10:30,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.446838
2012-04-24 08:10:30,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.462803
2012-04-24 08:10:31,412 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.472781
2012-04-24 08:10:31,913 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.488745
2012-04-24 08:10:32,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.504710
2012-04-24 08:10:32,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.520674
2012-04-24 08:10:33,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.538634
2012-04-24 08:10:33,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.542625
2012-04-24 08:10:34,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.570563
2012-04-24 08:10:34,921 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.586528
2012-04-24 08:10:35,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.606484
2012-04-24 08:10:35,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.628435
2012-04-24 08:10:36,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.638413
2012-04-24 08:10:36,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.648391
2012-04-24 08:10:37,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.652382
2012-04-24 08:10:37,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.652382
2012-04-24 08:10:38,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.652382
2012-04-24 08:10:38,932 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.654377
2012-04-24 08:10:39,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.656373
2012-04-24 08:10:39,935 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.660364
2012-04-24 08:10:40,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.666351
2012-04-24 08:10:40,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.670342
2012-04-24 08:10:41,439 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.672337
2012-04-24 08:10:41,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.674333
2012-04-24 08:10:42,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.678324
2012-04-24 08:10:42,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.684311
2012-04-24 08:10:43,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.694289
2012-04-24 08:10:43,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.700275
2012-04-24 08:10:44,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.704266
2012-04-24 08:10:44,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.706262
2012-04-24 08:10:45,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.708258
2012-04-24 08:10:45,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.712249
2012-04-24 08:10:46,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.718235
2012-04-24 08:10:46,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.724222
2012-04-24 08:10:47,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.730209
2012-04-24 08:10:47,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.736196
2012-04-24 08:10:48,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.742182
2012-04-24 08:10:48,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.754156
2012-04-24 08:10:49,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.770120
2012-04-24 08:10:49,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.780098
2012-04-24 08:10:50,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.792071
2012-04-24 08:10:50,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.798058
2012-04-24 08:10:51,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.810032
2012-04-24 08:10:51,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.816018
2012-04-24 08:10:52,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.820009
2012-04-24 08:10:52,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.827992
2012-04-24 08:10:53,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.829987
2012-04-24 08:10:53,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.829987
2012-04-24 08:10:54,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.831983
2012-04-24 08:10:54,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.835974
2012-04-24 08:10:55,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.841961
2012-04-24 08:10:55,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.845952
2012-04-24 08:10:56,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.851938
2012-04-24 08:10:56,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.859921
2012-04-24 08:10:57,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.869899
2012-04-24 08:10:57,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.879876
2012-04-24 08:10:58,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.891850
2012-04-24 08:10:58,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.905819
2012-04-24 08:10:59,485 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.925775
2012-04-24 08:10:59,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.953712
2012-04-24 08:11:00,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 15.989633
2012-04-24 08:11:00,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.067460
2012-04-24 08:11:01,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.131318
2012-04-24 08:11:01,992 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.191185
2012-04-24 08:11:02,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.207150
2012-04-24 08:11:02,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.332870
2012-04-24 08:11:03,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.400720
2012-04-24 08:11:03,997 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.476551
2012-04-24 08:11:04,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.526441
2012-04-24 08:11:05,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.562361
2012-04-24 08:11:05,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.602272
2012-04-24 08:11:06,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.688082
2012-04-24 08:11:06,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.745953
2012-04-24 08:11:07,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.803825
2012-04-24 08:11:07,507 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.871674
2012-04-24 08:11:08,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.917572
2012-04-24 08:11:08,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 16.975443
2012-04-24 08:11:09,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.041297
2012-04-24 08:11:09,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.073226
2012-04-24 08:11:10,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.103160
2012-04-24 08:11:10,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.125111
2012-04-24 08:11:11,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.151053
2012-04-24 08:11:11,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.180987
2012-04-24 08:11:12,018 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.202938
2012-04-24 08:11:12,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.222894
2012-04-24 08:11:13,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.228881
2012-04-24 08:11:13,522 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.234867
2012-04-24 08:11:14,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.240854
2012-04-24 08:11:14,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.256819
2012-04-24 08:11:15,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.278770
2012-04-24 08:11:15,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.304712
2012-04-24 08:11:16,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.330655
2012-04-24 08:11:16,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.356597
2012-04-24 08:11:17,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.380544
2012-04-24 08:11:17,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.410477
2012-04-24 08:11:18,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.432429
2012-04-24 08:11:18,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.442406
2012-04-24 08:11:19,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.464358
2012-04-24 08:11:19,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.500278
2012-04-24 08:11:20,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.514247
2012-04-24 08:11:20,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.552163
2012-04-24 08:11:21,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.574114
2012-04-24 08:11:21,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.598061
2012-04-24 08:11:22,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.622008
2012-04-24 08:11:22,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.645954
2012-04-24 08:11:23,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.657928
2012-04-24 08:11:23,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.659923
2012-04-24 08:11:24,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.661919
2012-04-24 08:11:24,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.663914
2012-04-24 08:11:25,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.667906
2012-04-24 08:11:25,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.673892
2012-04-24 08:11:26,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.679879
2012-04-24 08:11:26,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.685866
2012-04-24 08:11:27,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.697839
2012-04-24 08:11:27,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.701830
2012-04-24 08:11:28,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.713804
2012-04-24 08:11:28,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.719790
2012-04-24 08:11:29,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.737750
2012-04-24 08:11:29,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.755711
2012-04-24 08:11:30,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.773671
2012-04-24 08:11:30,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.785644
2012-04-24 08:11:31,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.801609
2012-04-24 08:11:31,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.823560
2012-04-24 08:11:32,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.847507
2012-04-24 08:11:32,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.879436
2012-04-24 08:11:33,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.903383
2012-04-24 08:11:33,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.927329
2012-04-24 08:11:34,079 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.939303
2012-04-24 08:11:34,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.949281
2012-04-24 08:11:35,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.959259
2012-04-24 08:11:35,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.975223
2012-04-24 08:11:36,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 17.997174
2012-04-24 08:11:36,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.021121
2012-04-24 08:11:37,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.031099
2012-04-24 08:11:37,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.043072
2012-04-24 08:11:38,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.053050
2012-04-24 08:11:38,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.069015
2012-04-24 08:11:39,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.090966
2012-04-24 08:11:39,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.114913
2012-04-24 08:11:40,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.136864
2012-04-24 08:11:40,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.158815
2012-04-24 08:11:41,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.178771
2012-04-24 08:11:41,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.200722
2012-04-24 08:11:42,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.226665
2012-04-24 08:11:42,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.236643
2012-04-24 08:11:43,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.246620
2012-04-24 08:11:43,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.262585
2012-04-24 08:11:44,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.272563
2012-04-24 08:11:44,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.284536
2012-04-24 08:11:45,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.294514
2012-04-24 08:11:45,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.308483
2012-04-24 08:11:46,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.322452
2012-04-24 08:11:46,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.338417
2012-04-24 08:11:47,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.352386
2012-04-24 08:11:47,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.382319
2012-04-24 08:11:48,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.398284
2012-04-24 08:11:48,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.416244
2012-04-24 08:11:49,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.442186
2012-04-24 08:11:49,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.450168
2012-04-24 08:11:50,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.460146
2012-04-24 08:11:50,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.476111
2012-04-24 08:11:51,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.498062
2012-04-24 08:11:51,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.522009
2012-04-24 08:11:52,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.543960
2012-04-24 08:11:52,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.571898
2012-04-24 08:11:53,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.591854
2012-04-24 08:11:53,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.615801
2012-04-24 08:11:54,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.635756
2012-04-24 08:11:54,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.677663
2012-04-24 08:11:55,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.707597
2012-04-24 08:11:55,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.733539
2012-04-24 08:11:56,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.779437
2012-04-24 08:11:56,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.835313
2012-04-24 08:11:57,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.901167
2012-04-24 08:11:57,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 18.988972
2012-04-24 08:11:58,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.072786
2012-04-24 08:11:58,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.196511
2012-04-24 08:11:59,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.226444
2012-04-24 08:11:59,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.400059
2012-04-24 08:12:00,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.521789
2012-04-24 08:12:00,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.623563
2012-04-24 08:12:01,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.695403
2012-04-24 08:12:01,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.789195
2012-04-24 08:12:02,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.878995
2012-04-24 08:12:02,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 19.962809
2012-04-24 08:12:03,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.002720
2012-04-24 08:12:03,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.046623
2012-04-24 08:12:04,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.092521
2012-04-24 08:12:04,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.166357
2012-04-24 08:12:05,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.182322
2012-04-24 08:12:05,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.226224
2012-04-24 08:12:06,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.234206
2012-04-24 08:12:06,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.308042
2012-04-24 08:12:07,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.351945
2012-04-24 08:12:07,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.373896
2012-04-24 08:12:08,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.397843
2012-04-24 08:12:08,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.435759
2012-04-24 08:12:09,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.469683
2012-04-24 08:12:09,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.497621
2012-04-24 08:12:10,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.531546
2012-04-24 08:12:10,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.547511
2012-04-24 08:12:11,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.571457
2012-04-24 08:12:11,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.599395
2012-04-24 08:12:12,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.611369
2012-04-24 08:12:12,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.617356
2012-04-24 08:12:13,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.629329
2012-04-24 08:12:13,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.643298
2012-04-24 08:12:14,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.687200
2012-04-24 08:12:14,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.711147
2012-04-24 08:12:15,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.733098
2012-04-24 08:12:15,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.755050
2012-04-24 08:12:16,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.777001
2012-04-24 08:12:16,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.802943
2012-04-24 08:12:17,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.830881
2012-04-24 08:12:17,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.860815
2012-04-24 08:12:18,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.902722
2012-04-24 08:12:18,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.920682
2012-04-24 08:12:19,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.946624
2012-04-24 08:12:19,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.964584
2012-04-24 08:12:20,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 20.996513
2012-04-24 08:12:20,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.054385
2012-04-24 08:12:21,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.108265
2012-04-24 08:12:21,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.154163
2012-04-24 08:12:22,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.182101
2012-04-24 08:12:22,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.243964
2012-04-24 08:12:23,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.315804
2012-04-24 08:12:23,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.361702
2012-04-24 08:12:24,212 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.413587
2012-04-24 08:12:24,713 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.457490
2012-04-24 08:12:25,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.521348
2012-04-24 08:12:25,716 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.533321
2012-04-24 08:12:26,217 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.567246
2012-04-24 08:12:26,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.587202
2012-04-24 08:12:27,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.605162
2012-04-24 08:12:27,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.631104
2012-04-24 08:12:28,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.659042
2012-04-24 08:12:28,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.677002
2012-04-24 08:12:29,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.682989
2012-04-24 08:12:29,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.682989
2012-04-24 08:12:30,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.700949
2012-04-24 08:12:30,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.708931
2012-04-24 08:12:31,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.716914
2012-04-24 08:12:31,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.724896
2012-04-24 08:12:32,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.734874
2012-04-24 08:12:32,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.740860
2012-04-24 08:12:33,235 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.748843
2012-04-24 08:12:33,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.758821
2012-04-24 08:12:34,237 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.770794
2012-04-24 08:12:34,739 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.780772
2012-04-24 08:12:35,240 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.784763
2012-04-24 08:12:35,741 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.788754
2012-04-24 08:12:36,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.794741
2012-04-24 08:12:36,744 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.804719
2012-04-24 08:12:37,245 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.808710
2012-04-24 08:12:37,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.810705
2012-04-24 08:12:38,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.812701
2012-04-24 08:12:38,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.816692
2012-04-24 08:12:39,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.816692
2012-04-24 08:12:39,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.818688
2012-04-24 08:12:40,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.818688
2012-04-24 08:12:40,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.820683
2012-04-24 08:12:41,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.824674
2012-04-24 08:12:41,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.830661
2012-04-24 08:12:42,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.836648
2012-04-24 08:12:42,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.842634
2012-04-24 08:12:43,262 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.850617
2012-04-24 08:12:43,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.860595
2012-04-24 08:12:44,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.876559
2012-04-24 08:12:44,766 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.896515
2012-04-24 08:12:45,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.918466
2012-04-24 08:12:45,768 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.946404
2012-04-24 08:12:46,270 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.966360
2012-04-24 08:12:46,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.990306
2012-04-24 08:12:47,273 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.990306
2012-04-24 08:12:47,774 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 21.990306
2012-04-24 08:12:48,276 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.026227
2012-04-24 08:12:48,777 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.034209
2012-04-24 08:12:49,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.052169
2012-04-24 08:12:49,780 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.052169
2012-04-24 08:12:50,281 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.062147
2012-04-24 08:12:50,782 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.072125
2012-04-24 08:12:51,284 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.080107
2012-04-24 08:12:51,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.086094
2012-04-24 08:12:52,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.096072
2012-04-24 08:12:52,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.096072
2012-04-24 08:12:53,289 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.108045
2012-04-24 08:12:53,791 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.114032
2012-04-24 08:12:54,292 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.120018
2012-04-24 08:12:54,793 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.129996
2012-04-24 08:12:55,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.133987
2012-04-24 08:12:55,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.147956
2012-04-24 08:12:56,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.157934
2012-04-24 08:12:56,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.169908
2012-04-24 08:12:57,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.185872
2012-04-24 08:12:57,802 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.201837
2012-04-24 08:12:58,303 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.227779
2012-04-24 08:12:58,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.259708
2012-04-24 08:12:59,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.301615
2012-04-24 08:12:59,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.349509
2012-04-24 08:13:00,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.369464
2012-04-24 08:13:00,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.399398
2012-04-24 08:13:01,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.439309
2012-04-24 08:13:01,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.471238
2012-04-24 08:13:02,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.519132
2012-04-24 08:13:02,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.559043
2012-04-24 08:13:03,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.602946
2012-04-24 08:13:03,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.640862
2012-04-24 08:13:04,319 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.694742
2012-04-24 08:13:04,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.748622
2012-04-24 08:13:05,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.782547
2012-04-24 08:13:05,823 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.794520
2012-04-24 08:13:06,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.812481
2012-04-24 08:13:06,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.836427
2012-04-24 08:13:07,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.876339
2012-04-24 08:13:07,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.920241
2012-04-24 08:13:08,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.940197
2012-04-24 08:13:08,830 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.952170
2012-04-24 08:13:09,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.970130
2012-04-24 08:13:09,833 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 22.998068
2012-04-24 08:13:10,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.033989
2012-04-24 08:13:10,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.037980
2012-04-24 08:13:11,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.043967
2012-04-24 08:13:11,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.059931
2012-04-24 08:13:12,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.067913
2012-04-24 08:13:12,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.087869
2012-04-24 08:13:13,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.115807
2012-04-24 08:13:13,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.135763
2012-04-24 08:13:14,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.151727
2012-04-24 08:13:14,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.167692
2012-04-24 08:13:15,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.167692
2012-04-24 08:13:15,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.185652
2012-04-24 08:13:16,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.213590
2012-04-24 08:13:16,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.247514
2012-04-24 08:13:17,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.269466
2012-04-24 08:13:17,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.289421
2012-04-24 08:13:18,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.303390
2012-04-24 08:13:18,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.325342
2012-04-24 08:13:19,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.333324
2012-04-24 08:13:19,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.351284
2012-04-24 08:13:20,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.363257
2012-04-24 08:13:20,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.385209
2012-04-24 08:13:21,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.413147
2012-04-24 08:13:21,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.445076
2012-04-24 08:13:22,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.482992
2012-04-24 08:13:22,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.516916
2012-04-24 08:13:23,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.550841
2012-04-24 08:13:23,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.572792
2012-04-24 08:13:24,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.606717
2012-04-24 08:13:24,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.652615
2012-04-24 08:13:25,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.710486
2012-04-24 08:13:25,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.768358
2012-04-24 08:13:26,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.822238
2012-04-24 08:13:26,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.894079
2012-04-24 08:13:27,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 23.906052
2012-04-24 08:13:27,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.011817
2012-04-24 08:13:28,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.053724
2012-04-24 08:13:28,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.101618
2012-04-24 08:13:29,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.169467
2012-04-24 08:13:29,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.235321
2012-04-24 08:13:30,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.253281
2012-04-24 08:13:30,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.321130
2012-04-24 08:13:31,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.365033
2012-04-24 08:13:31,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.414922
2012-04-24 08:13:32,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.478780
2012-04-24 08:13:32,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.534656
2012-04-24 08:13:33,399 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.558603
2012-04-24 08:13:33,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.626452
2012-04-24 08:13:34,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.646408
2012-04-24 08:13:34,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.684324
2012-04-24 08:13:35,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.734213
2012-04-24 08:13:35,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.758160
2012-04-24 08:13:36,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.810044
2012-04-24 08:13:36,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.843969
2012-04-24 08:13:37,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.863925
2012-04-24 08:13:37,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.907827
2012-04-24 08:13:38,412 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.929779
2012-04-24 08:13:38,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 24.975677
2012-04-24 08:13:39,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.013592
2012-04-24 08:13:39,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.061486
2012-04-24 08:13:40,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.109380
2012-04-24 08:13:40,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.157273
2012-04-24 08:13:41,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.205167
2012-04-24 08:13:41,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.257052
2012-04-24 08:13:42,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.298959
2012-04-24 08:13:42,925 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.322905
2012-04-24 08:13:43,426 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.334879
2012-04-24 08:13:43,928 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.354835
2012-04-24 08:13:44,429 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.388759
2012-04-24 08:13:44,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.430666
2012-04-24 08:13:45,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.468582
2012-04-24 08:13:45,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.498515
2012-04-24 08:13:46,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.526453
2012-04-24 08:13:46,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.564369
2012-04-24 08:13:47,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.606276
2012-04-24 08:13:47,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.642196
2012-04-24 08:13:48,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.686099
2012-04-24 08:13:48,941 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.708050
2012-04-24 08:13:49,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.751953
2012-04-24 08:13:49,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.809824
2012-04-24 08:13:50,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.861709
2012-04-24 08:13:50,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.889647
2012-04-24 08:13:51,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.937541
2012-04-24 08:13:51,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.973461
2012-04-24 08:13:52,451 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 25.993416
2012-04-24 08:13:52,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.047297
2012-04-24 08:13:53,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.087208
2012-04-24 08:13:53,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.121133
2012-04-24 08:13:54,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.149071
2012-04-24 08:13:54,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.208938
2012-04-24 08:13:55,459 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.270800
2012-04-24 08:13:55,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.312707
2012-04-24 08:13:56,462 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.346632
2012-04-24 08:13:56,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.404503
2012-04-24 08:13:57,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.446410
2012-04-24 08:13:57,966 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.480335
2012-04-24 08:13:58,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.538207
2012-04-24 08:13:58,969 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.600069
2012-04-24 08:13:59,470 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.641976
2012-04-24 08:13:59,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.671910
2012-04-24 08:14:00,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.715812
2012-04-24 08:14:00,975 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.767697
2012-04-24 08:14:01,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.823573
2012-04-24 08:14:01,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.865480
2012-04-24 08:14:02,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.929338
2012-04-24 08:14:02,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 26.973240
2012-04-24 08:14:03,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.019139
2012-04-24 08:14:03,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.082997
2012-04-24 08:14:04,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.148850
2012-04-24 08:14:04,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.198740
2012-04-24 08:14:05,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.270580
2012-04-24 08:14:05,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.288540
2012-04-24 08:14:06,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.310491
2012-04-24 08:14:06,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.332443
2012-04-24 08:14:07,493 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.388319
2012-04-24 08:14:07,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.424239
2012-04-24 08:14:08,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.462155
2012-04-24 08:14:08,997 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.462155
2012-04-24 08:14:09,498 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.500070
2012-04-24 08:14:09,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.532000
2012-04-24 08:14:10,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.557942
2012-04-24 08:14:11,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.589871
2012-04-24 08:14:11,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.623796
2012-04-24 08:14:12,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.641756
2012-04-24 08:14:12,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.655725
2012-04-24 08:14:13,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.697632
2012-04-24 08:14:13,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.749516
2012-04-24 08:14:14,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.777454
2012-04-24 08:14:14,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.809384
2012-04-24 08:14:15,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.837321
2012-04-24 08:14:15,515 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.865259
2012-04-24 08:14:16,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.877233
2012-04-24 08:14:16,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.917144
2012-04-24 08:14:17,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.931113
2012-04-24 08:14:17,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.945082
2012-04-24 08:14:18,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.979007
2012-04-24 08:14:18,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 27.998963
2012-04-24 08:14:19,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.030892
2012-04-24 08:14:19,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.068807
2012-04-24 08:14:20,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.110714
2012-04-24 08:14:20,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.122688
2012-04-24 08:14:21,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.138652
2012-04-24 08:14:21,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.162599
2012-04-24 08:14:22,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.194528
2012-04-24 08:14:22,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.222466
2012-04-24 08:14:23,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.260382
2012-04-24 08:14:23,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.280338
2012-04-24 08:14:24,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.290315
2012-04-24 08:14:24,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.296302
2012-04-24 08:14:25,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.306280
2012-04-24 08:14:25,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.314262
2012-04-24 08:14:26,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.324240
2012-04-24 08:14:26,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.334218
2012-04-24 08:14:27,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.344196
2012-04-24 08:14:27,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.352178
2012-04-24 08:14:28,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.356169
2012-04-24 08:14:28,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.360160
2012-04-24 08:14:29,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.366147
2012-04-24 08:14:29,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.376125
2012-04-24 08:14:30,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.386103
2012-04-24 08:14:30,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.400072
2012-04-24 08:14:31,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.400072
2012-04-24 08:14:31,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.408054
2012-04-24 08:14:32,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.414041
2012-04-24 08:14:32,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.424019
2012-04-24 08:14:33,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.433996
2012-04-24 08:14:33,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.441979
2012-04-24 08:14:34,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.447965
2012-04-24 08:14:34,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.461934
2012-04-24 08:14:35,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.475903
2012-04-24 08:14:35,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.487877
2012-04-24 08:14:36,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.493863
2012-04-24 08:14:36,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.501846
2012-04-24 08:14:37,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.513819
2012-04-24 08:14:37,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.527788
2012-04-24 08:14:38,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.545748
2012-04-24 08:14:38,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.559717
2012-04-24 08:14:39,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.567699
2012-04-24 08:14:39,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.575682
2012-04-24 08:14:40,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.583664
2012-04-24 08:14:40,583 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.599629
2012-04-24 08:14:41,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.613598
2012-04-24 08:14:41,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.631558
2012-04-24 08:14:42,087 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.635549
2012-04-24 08:14:42,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.649518
2012-04-24 08:14:43,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.665482
2012-04-24 08:14:43,591 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.689429
2012-04-24 08:14:44,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.719363
2012-04-24 08:14:44,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.741314
2012-04-24 08:14:45,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.765261
2012-04-24 08:14:45,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.779230
2012-04-24 08:14:46,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.805172
2012-04-24 08:14:46,599 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.851070
2012-04-24 08:14:47,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.904951
2012-04-24 08:14:47,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 28.976791
2012-04-24 08:14:48,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.122467
2012-04-24 08:14:48,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.220250
2012-04-24 08:14:49,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.363931
2012-04-24 08:14:49,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.461714
2012-04-24 08:14:50,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.615373
2012-04-24 08:14:50,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.623355
2012-04-24 08:14:51,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 29.976571
2012-04-24 08:14:51,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.114265
2012-04-24 08:14:52,114 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.180119
2012-04-24 08:14:52,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.285884
2012-04-24 08:14:53,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.361715
2012-04-24 08:14:53,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.409609
2012-04-24 08:14:54,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.475463
2012-04-24 08:14:54,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.541316
2012-04-24 08:14:55,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.593201
2012-04-24 08:14:55,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.639099
2012-04-24 08:14:56,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.665042
2012-04-24 08:14:56,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.720918
2012-04-24 08:14:57,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.736882
2012-04-24 08:14:57,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.770807
2012-04-24 08:14:58,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.804732
2012-04-24 08:14:58,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.844643
2012-04-24 08:14:59,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.894532
2012-04-24 08:14:59,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.936439
2012-04-24 08:15:00,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 30.992315
2012-04-24 08:15:00,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.026240
2012-04-24 08:15:01,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.060164
2012-04-24 08:15:01,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.096084
2012-04-24 08:15:02,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.143978
2012-04-24 08:15:02,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.149965
2012-04-24 08:15:03,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.211827
2012-04-24 08:15:03,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.245752
2012-04-24 08:15:04,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.261717
2012-04-24 08:15:04,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.295641
2012-04-24 08:15:05,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.329566
2012-04-24 08:15:05,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.357504
2012-04-24 08:15:06,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.391429
2012-04-24 08:15:06,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.419367
2012-04-24 08:15:07,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.455287
2012-04-24 08:15:07,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.483225
2012-04-24 08:15:08,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.525132
2012-04-24 08:15:08,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.525132
2012-04-24 08:15:09,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.569034
2012-04-24 08:15:09,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.616928
2012-04-24 08:15:10,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.668813
2012-04-24 08:15:10,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.694755
2012-04-24 08:15:11,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.724688
2012-04-24 08:15:11,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.754622
2012-04-24 08:15:12,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.784556
2012-04-24 08:15:12,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.814489
2012-04-24 08:15:13,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.824467
2012-04-24 08:15:13,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.824467
2012-04-24 08:15:14,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.866374
2012-04-24 08:15:14,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.890321
2012-04-24 08:15:15,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.908281
2012-04-24 08:15:15,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.916263
2012-04-24 08:15:16,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.964157
2012-04-24 08:15:16,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 31.990099
2012-04-24 08:15:17,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.020033
2012-04-24 08:15:17,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.047971
2012-04-24 08:15:18,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.079900
2012-04-24 08:15:18,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.109833
2012-04-24 08:15:19,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.137771
2012-04-24 08:15:19,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.149745
2012-04-24 08:15:20,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.171696
2012-04-24 08:15:20,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.205620
2012-04-24 08:15:21,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.245532
2012-04-24 08:15:21,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.245532
2012-04-24 08:15:22,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.293425
2012-04-24 08:15:22,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.335332
2012-04-24 08:15:23,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.349301
2012-04-24 08:15:23,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.365266
2012-04-24 08:15:24,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.387217
2012-04-24 08:15:24,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.423137
2012-04-24 08:15:25,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.465044
2012-04-24 08:15:25,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.516929
2012-04-24 08:15:26,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.572805
2012-04-24 08:15:26,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.572805
2012-04-24 08:15:27,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.610721
2012-04-24 08:15:27,710 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.646641
2012-04-24 08:15:28,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.646641
2012-04-24 08:15:28,713 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.664601
2012-04-24 08:15:29,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.678570
2012-04-24 08:15:29,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.696530
2012-04-24 08:15:30,217 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.716486
2012-04-24 08:15:30,718 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.732450
2012-04-24 08:15:31,220 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.748415
2012-04-24 08:15:31,721 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.766375
2012-04-24 08:15:32,222 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.776353
2012-04-24 08:15:32,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.792318
2012-04-24 08:15:33,225 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.816264
2012-04-24 08:15:33,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.852185
2012-04-24 08:15:34,228 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.892096
2012-04-24 08:15:34,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.924025
2012-04-24 08:15:35,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.959945
2012-04-24 08:15:35,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.983892
2012-04-24 08:15:36,233 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 32.997861
2012-04-24 08:15:36,734 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.035777
2012-04-24 08:15:37,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.071697
2012-04-24 08:15:37,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.095644
2012-04-24 08:15:38,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.111608
2012-04-24 08:15:38,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.139546
2012-04-24 08:15:39,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.157506
2012-04-24 08:15:39,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.187440
2012-04-24 08:15:40,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.221365
2012-04-24 08:15:40,746 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.257285
2012-04-24 08:15:41,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.297196
2012-04-24 08:15:41,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.339103
2012-04-24 08:15:42,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.375023
2012-04-24 08:15:42,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.402961
2012-04-24 08:15:43,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.422917
2012-04-24 08:15:43,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.466820
2012-04-24 08:15:44,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.508727
2012-04-24 08:15:44,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.562607
2012-04-24 08:15:45,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.574580
2012-04-24 08:15:45,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.628461
2012-04-24 08:15:46,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.700301
2012-04-24 08:15:46,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.728239
2012-04-24 08:15:47,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.766155
2012-04-24 08:15:47,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.810057
2012-04-24 08:15:48,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.868679
2012-04-24 08:15:48,768 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 33.933783
2012-04-24 08:15:49,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.013605
2012-04-24 08:15:49,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.073472
2012-04-24 08:15:50,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.085446
2012-04-24 08:15:50,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.085446
2012-04-24 08:15:51,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.211167
2012-04-24 08:15:51,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.247087
2012-04-24 08:15:52,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.281011
2012-04-24 08:15:52,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.298972
2012-04-24 08:15:53,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.322918
2012-04-24 08:15:53,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.340878
2012-04-24 08:15:54,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.358839
2012-04-24 08:15:54,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.386777
2012-04-24 08:15:55,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.414715
2012-04-24 08:15:55,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.422697
2012-04-24 08:15:56,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.442652
2012-04-24 08:15:56,789 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.486555
2012-04-24 08:15:57,290 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.532453
2012-04-24 08:15:57,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.562387
2012-04-24 08:15:58,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.600302
2012-04-24 08:15:58,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.686112
2012-04-24 08:15:59,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.732010
2012-04-24 08:15:59,798 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.795868
2012-04-24 08:16:00,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.861722
2012-04-24 08:16:00,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.903629
2012-04-24 08:16:01,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.947531
2012-04-24 08:16:01,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.955514
2012-04-24 08:16:02,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 34.997420
2012-04-24 08:16:02,806 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.049305
2012-04-24 08:16:03,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.101190
2012-04-24 08:16:03,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.101190
2012-04-24 08:16:04,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.149084
2012-04-24 08:16:04,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.169039
2012-04-24 08:16:05,313 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.186999
2012-04-24 08:16:05,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.210946
2012-04-24 08:16:06,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.248862
2012-04-24 08:16:06,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.280791
2012-04-24 08:16:07,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.314716
2012-04-24 08:16:07,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.364605
2012-04-24 08:16:08,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.414494
2012-04-24 08:16:08,823 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.452410
2012-04-24 08:16:09,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.466379
2012-04-24 08:16:09,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.518264
2012-04-24 08:16:10,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.572144
2012-04-24 08:16:10,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.624029
2012-04-24 08:16:11,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.639993
2012-04-24 08:16:11,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.695869
2012-04-24 08:16:12,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.771701
2012-04-24 08:16:12,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.819595
2012-04-24 08:16:13,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.843541
2012-04-24 08:16:13,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.931346
2012-04-24 08:16:14,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 35.961280
2012-04-24 08:16:14,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.003187
2012-04-24 08:16:15,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.027134
2012-04-24 08:16:15,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.055072
2012-04-24 08:16:16,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.083010
2012-04-24 08:16:16,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.092987
2012-04-24 08:16:17,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.110948
2012-04-24 08:16:17,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.136890
2012-04-24 08:16:18,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.144872
2012-04-24 08:16:18,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.162832
2012-04-24 08:16:19,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.204739
2012-04-24 08:16:19,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.226690
2012-04-24 08:16:20,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.252633
2012-04-24 08:16:20,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.280571
2012-04-24 08:16:21,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.302522
2012-04-24 08:16:21,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.306513
2012-04-24 08:16:22,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.352411
2012-04-24 08:16:22,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.376358
2012-04-24 08:16:23,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.390327
2012-04-24 08:16:23,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.398309
2012-04-24 08:16:24,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.422256
2012-04-24 08:16:24,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.444207
2012-04-24 08:16:25,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.466159
2012-04-24 08:16:25,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.492101
2012-04-24 08:16:26,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.520039
2012-04-24 08:16:26,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.520039
2012-04-24 08:16:27,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.549973
2012-04-24 08:16:27,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.581902
2012-04-24 08:16:28,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.627800
2012-04-24 08:16:28,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.661724
2012-04-24 08:16:29,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.715605
2012-04-24 08:16:29,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.777467
2012-04-24 08:16:30,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.815383
2012-04-24 08:16:30,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.873255
2012-04-24 08:16:31,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.915162
2012-04-24 08:16:31,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 36.979020
2012-04-24 08:16:32,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.032900
2012-04-24 08:16:32,888 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.088776
2012-04-24 08:16:33,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.142656
2012-04-24 08:16:33,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.212501
2012-04-24 08:16:34,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.240439
2012-04-24 08:16:34,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.302302
2012-04-24 08:16:35,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.366160
2012-04-24 08:16:35,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.441992
2012-04-24 08:16:36,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.525805
2012-04-24 08:16:36,898 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.575695
2012-04-24 08:16:37,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.627579
2012-04-24 08:16:37,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.741327
2012-04-24 08:16:38,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.885008
2012-04-24 08:16:38,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 37.910950
2012-04-24 08:16:39,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.010729
2012-04-24 08:16:39,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.064609
2012-04-24 08:16:40,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.172370
2012-04-24 08:16:40,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.238223
2012-04-24 08:16:41,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.310064
2012-04-24 08:16:41,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.373922
2012-04-24 08:16:42,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.451749
2012-04-24 08:16:42,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.513612
2012-04-24 08:16:43,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.591439
2012-04-24 08:16:43,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.667270
2012-04-24 08:16:44,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.715164
2012-04-24 08:16:44,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.715164
2012-04-24 08:16:45,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.838889
2012-04-24 08:16:45,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.886783
2012-04-24 08:16:46,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.922703
2012-04-24 08:16:46,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.950641
2012-04-24 08:16:47,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 38.994544
2012-04-24 08:16:47,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.052415
2012-04-24 08:16:48,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.096318
2012-04-24 08:16:48,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.130242
2012-04-24 08:16:49,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.148202
2012-04-24 08:16:49,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.152194
2012-04-24 08:16:50,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.178136
2012-04-24 08:16:50,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.188114
2012-04-24 08:16:51,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.198092
2012-04-24 08:16:51,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.210065
2012-04-24 08:16:52,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.224034
2012-04-24 08:16:52,943 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.239999
2012-04-24 08:16:53,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.243990
2012-04-24 08:16:53,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.271928
2012-04-24 08:16:54,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.283901
2012-04-24 08:16:54,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.291883
2012-04-24 08:16:55,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.311839
2012-04-24 08:16:55,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.331795
2012-04-24 08:16:56,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.353746
2012-04-24 08:16:56,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.375697
2012-04-24 08:16:57,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.395653
2012-04-24 08:16:57,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.395653
2012-04-24 08:16:58,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.421595
2012-04-24 08:16:58,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.449533
2012-04-24 08:16:59,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.475476
2012-04-24 08:16:59,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.483458
2012-04-24 08:17:00,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.513391
2012-04-24 08:17:00,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.565276
2012-04-24 08:17:01,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.595210
2012-04-24 08:17:01,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.615165
2012-04-24 08:17:02,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.663059
2012-04-24 08:17:02,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.712948
2012-04-24 08:17:03,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.754855
2012-04-24 08:17:03,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.800753
2012-04-24 08:17:04,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.840665
2012-04-24 08:17:04,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.888558
2012-04-24 08:17:05,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.920487
2012-04-24 08:17:05,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 39.978359
2012-04-24 08:17:06,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.038226
2012-04-24 08:17:06,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.100088
2012-04-24 08:17:07,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.143991
2012-04-24 08:17:07,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.197871
2012-04-24 08:17:08,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.243769
2012-04-24 08:17:08,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.299645
2012-04-24 08:17:09,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.375477
2012-04-24 08:17:09,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.481242
2012-04-24 08:17:10,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.579025
2012-04-24 08:17:10,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.714724
2012-04-24 08:17:11,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.714724
2012-04-24 08:17:11,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 40.936232
2012-04-24 08:17:12,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.036010
2012-04-24 08:17:12,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.181686
2012-04-24 08:17:13,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.231576
2012-04-24 08:17:14,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.393217
2012-04-24 08:17:14,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.471044
2012-04-24 08:17:15,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.586787
2012-04-24 08:17:15,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.706521
2012-04-24 08:17:16,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.788339
2012-04-24 08:17:16,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.910069
2012-04-24 08:17:17,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 41.985901
2012-04-24 08:17:17,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.067719
2012-04-24 08:17:18,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.139559
2012-04-24 08:17:18,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.233351
2012-04-24 08:17:19,016 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.255302
2012-04-24 08:17:19,517 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.367054
2012-04-24 08:17:20,019 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.432908
2012-04-24 08:17:20,520 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.432908
2012-04-24 08:17:21,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.514726
2012-04-24 08:17:21,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.560624
2012-04-24 08:17:22,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.598540
2012-04-24 08:17:22,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.644438
2012-04-24 08:17:23,027 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.654416
2012-04-24 08:17:23,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.714283
2012-04-24 08:17:24,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.746212
2012-04-24 08:17:24,531 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.774150
2012-04-24 08:17:25,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.814061
2012-04-24 08:17:25,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.840004
2012-04-24 08:17:26,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.893884
2012-04-24 08:17:26,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 42.957742
2012-04-24 08:17:27,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.001645
2012-04-24 08:17:27,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.007631
2012-04-24 08:17:28,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.009627
2012-04-24 08:17:28,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.083463
2012-04-24 08:17:29,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.121379
2012-04-24 08:17:29,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.155304
2012-04-24 08:17:30,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.201202
2012-04-24 08:17:30,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.245104
2012-04-24 08:17:31,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.273042
2012-04-24 08:17:31,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.281024
2012-04-24 08:17:32,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.320936
2012-04-24 08:17:32,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.362843
2012-04-24 08:17:33,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.412732
2012-04-24 08:17:33,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.452643
2012-04-24 08:17:34,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.468608
2012-04-24 08:17:34,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.518497
2012-04-24 08:17:35,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.528475
2012-04-24 08:17:35,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.538453
2012-04-24 08:17:36,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.550426
2012-04-24 08:17:36,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.572377
2012-04-24 08:17:37,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.606302
2012-04-24 08:17:37,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.654196
2012-04-24 08:17:38,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.706080
2012-04-24 08:17:38,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.757965
2012-04-24 08:17:39,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.811845
2012-04-24 08:17:39,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.825814
2012-04-24 08:17:40,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.877699
2012-04-24 08:17:40,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.931580
2012-04-24 08:17:41,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.973487
2012-04-24 08:17:41,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 43.991447
2012-04-24 08:17:42,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.059296
2012-04-24 08:17:42,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.107190
2012-04-24 08:17:43,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.133132
2012-04-24 08:17:43,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.204972
2012-04-24 08:17:44,084 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.276813
2012-04-24 08:17:44,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.304751
2012-04-24 08:17:45,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.414507
2012-04-24 08:17:45,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.414507
2012-04-24 08:17:46,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.568166
2012-04-24 08:17:46,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.620051
2012-04-24 08:17:47,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.655971
2012-04-24 08:17:47,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.675927
2012-04-24 08:17:48,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.769718
2012-04-24 08:17:48,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.825594
2012-04-24 08:17:49,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.887457
2012-04-24 08:17:49,599 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.943333
2012-04-24 08:17:50,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 44.971271
2012-04-24 08:17:50,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.055085
2012-04-24 08:17:51,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.104974
2012-04-24 08:17:51,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.144885
2012-04-24 08:17:52,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.198765
2012-04-24 08:17:52,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.226703
2012-04-24 08:17:53,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.272601
2012-04-24 08:17:53,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.338455
2012-04-24 08:17:54,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.402313
2012-04-24 08:17:54,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.442225
2012-04-24 08:17:55,114 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.498101
2012-04-24 08:17:55,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.543999
2012-04-24 08:17:56,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.583910
2012-04-24 08:17:56,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.649764
2012-04-24 08:17:57,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.707635
2012-04-24 08:17:57,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.787458
2012-04-24 08:17:58,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.849321
2012-04-24 08:17:58,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 45.961072
2012-04-24 08:17:59,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.040895
2012-04-24 08:17:59,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.114731
2012-04-24 08:18:00,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.206527
2012-04-24 08:18:00,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.272381
2012-04-24 08:18:01,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.364177
2012-04-24 08:18:01,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.442004
2012-04-24 08:18:02,134 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.442004
2012-04-24 08:18:02,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.603645
2012-04-24 08:18:03,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.681473
2012-04-24 08:18:03,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.765287
2012-04-24 08:18:04,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.847105
2012-04-24 08:18:04,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 46.942892
2012-04-24 08:18:05,142 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.040675
2012-04-24 08:18:05,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.134467
2012-04-24 08:18:06,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.218281
2012-04-24 08:18:06,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.266174
2012-04-24 08:18:07,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.361961
2012-04-24 08:18:07,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.453758
2012-04-24 08:18:08,150 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.541563
2012-04-24 08:18:08,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.641341
2012-04-24 08:18:09,153 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.755088
2012-04-24 08:18:09,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.840898
2012-04-24 08:18:10,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 47.898769
2012-04-24 08:18:10,657 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.032472
2012-04-24 08:18:11,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.210078
2012-04-24 08:18:11,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.277927
2012-04-24 08:18:12,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.391675
2012-04-24 08:18:12,663 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.507418
2012-04-24 08:18:13,164 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.625156
2012-04-24 08:18:13,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.778815
2012-04-24 08:18:14,167 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 48.882584
2012-04-24 08:18:14,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.078150
2012-04-24 08:18:15,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.227818
2012-04-24 08:18:15,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.237796
2012-04-24 08:18:16,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.417397
2012-04-24 08:18:16,674 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.509193
2012-04-24 08:18:17,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.596998
2012-04-24 08:18:17,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.686798
2012-04-24 08:18:18,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.778595
2012-04-24 08:18:18,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.862408
2012-04-24 08:18:19,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 49.930258
2012-04-24 08:18:19,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.016067
2012-04-24 08:18:20,184 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.101877
2012-04-24 08:18:20,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.195668
2012-04-24 08:18:21,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.263518
2012-04-24 08:18:21,688 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.317398
2012-04-24 08:18:22,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.411190
2012-04-24 08:18:22,691 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.455092
2012-04-24 08:18:23,192 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.596778
2012-04-24 08:18:23,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.624716
2012-04-24 08:18:24,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.700547
2012-04-24 08:18:24,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.776379
2012-04-24 08:18:25,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.842232
2012-04-24 08:18:25,698 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.906091
2012-04-24 08:18:26,200 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 50.977931
2012-04-24 08:18:26,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.053763
2012-04-24 08:18:27,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.133585
2012-04-24 08:18:27,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.213408
2012-04-24 08:18:28,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.293231
2012-04-24 08:18:28,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.325160
2012-04-24 08:18:29,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.381036
2012-04-24 08:18:29,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.460859
2012-04-24 08:18:30,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.534695
2012-04-24 08:18:30,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.622500
2012-04-24 08:18:31,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.714296
2012-04-24 08:18:31,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.816070
2012-04-24 08:18:32,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.921835
2012-04-24 08:18:32,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 51.971724
2012-04-24 08:18:33,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.097445
2012-04-24 08:18:33,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.183254
2012-04-24 08:18:34,222 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.269064
2012-04-24 08:18:34,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.348887
2012-04-24 08:18:35,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.432700
2012-04-24 08:18:35,726 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.522501
2012-04-24 08:18:36,227 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.640239
2012-04-24 08:18:36,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.702102
2012-04-24 08:18:37,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.763965
2012-04-24 08:18:37,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.849774
2012-04-24 08:18:38,233 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.875717
2012-04-24 08:18:38,734 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 52.907646
2012-04-24 08:18:39,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.045340
2012-04-24 08:18:39,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.109198
2012-04-24 08:18:40,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.187025
2012-04-24 08:18:40,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.198999
2012-04-24 08:18:41,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.276826
2012-04-24 08:18:41,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.324719
2012-04-24 08:18:42,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.378600
2012-04-24 08:18:42,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.442458
2012-04-24 08:18:43,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.498334
2012-04-24 08:18:43,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.532259
2012-04-24 08:18:44,249 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.600108
2012-04-24 08:18:44,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.663966
2012-04-24 08:18:45,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.743789
2012-04-24 08:18:45,753 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.799665
2012-04-24 08:18:46,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.881483
2012-04-24 08:18:46,756 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 53.959310
2012-04-24 08:18:47,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.003213
2012-04-24 08:18:47,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.106982
2012-04-24 08:18:48,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.144898
2012-04-24 08:18:48,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.230707
2012-04-24 08:18:49,263 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.312526
2012-04-24 08:18:49,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.360419
2012-04-24 08:18:50,266 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.420286
2012-04-24 08:18:50,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.474167
2012-04-24 08:18:51,269 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.526052
2012-04-24 08:18:51,770 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.593901
2012-04-24 08:18:52,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.657759
2012-04-24 08:18:52,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.699666
2012-04-24 08:18:53,274 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.771506
2012-04-24 08:18:53,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.817404
2012-04-24 08:18:54,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.871285
2012-04-24 08:18:54,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.931152
2012-04-24 08:18:55,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 54.985032
2012-04-24 08:18:55,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.012970
2012-04-24 08:18:56,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.048890
2012-04-24 08:18:56,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.068846
2012-04-24 08:18:57,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.098780
2012-04-24 08:18:57,786 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.126718
2012-04-24 08:18:58,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.184589
2012-04-24 08:18:58,789 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.256429
2012-04-24 08:18:59,290 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.314301
2012-04-24 08:18:59,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.416075
2012-04-24 08:19:00,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.491907
2012-04-24 08:19:00,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.551774
2012-04-24 08:19:01,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.643570
2012-04-24 08:19:01,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.695455
2012-04-24 08:19:02,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.777273
2012-04-24 08:19:02,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.837140
2012-04-24 08:19:03,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.871065
2012-04-24 08:19:03,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.934923
2012-04-24 08:19:04,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.998781
2012-04-24 08:19:04,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 55.998781
2012-04-24 08:19:05,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.072617
2012-04-24 08:19:05,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.118515
2012-04-24 08:19:06,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.144457
2012-04-24 08:19:06,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.172395
2012-04-24 08:19:07,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.198338
2012-04-24 08:19:07,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.218293
2012-04-24 08:19:08,315 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.244236
2012-04-24 08:19:08,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.272174
2012-04-24 08:19:09,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.302107
2012-04-24 08:19:09,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.328050
2012-04-24 08:19:10,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.357983
2012-04-24 08:19:10,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.383926
2012-04-24 08:19:11,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.403881
2012-04-24 08:19:11,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.433815
2012-04-24 08:19:12,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.433815
2012-04-24 08:19:12,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.501664
2012-04-24 08:19:13,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.527606
2012-04-24 08:19:13,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.551553
2012-04-24 08:19:14,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.573505
2012-04-24 08:19:14,833 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.573505
2012-04-24 08:19:15,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.573505
2012-04-24 08:19:15,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.575500
2012-04-24 08:19:16,337 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.577496
2012-04-24 08:19:16,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.589469
2012-04-24 08:19:17,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.605434
2012-04-24 08:19:17,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.633372
2012-04-24 08:19:18,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.659314
2012-04-24 08:19:18,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.693239
2012-04-24 08:19:19,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.731154
2012-04-24 08:19:19,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.785035
2012-04-24 08:19:20,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.842906
2012-04-24 08:19:20,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.882818
2012-04-24 08:19:21,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.942685
2012-04-24 08:19:21,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 56.998561
2012-04-24 08:19:22,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.062419
2012-04-24 08:19:22,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.122286
2012-04-24 08:19:23,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.200113
2012-04-24 08:19:23,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.305878
2012-04-24 08:19:24,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.407652
2012-04-24 08:19:24,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.575280
2012-04-24 08:19:25,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.760868
2012-04-24 08:19:25,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 57.966411
2012-04-24 08:19:26,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.195902
2012-04-24 08:19:26,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.467299
2012-04-24 08:19:27,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.529161
2012-04-24 08:19:27,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.818519
2012-04-24 08:19:28,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 58.930271
2012-04-24 08:19:28,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.008098
2012-04-24 08:19:29,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.123841
2012-04-24 08:19:29,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.257544
2012-04-24 08:19:30,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.369296
2012-04-24 08:19:30,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.473065
2012-04-24 08:19:31,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.572844
2012-04-24 08:19:31,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.726502
2012-04-24 08:19:32,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.886148
2012-04-24 08:19:32,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 59.942024
2012-04-24 08:19:33,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.073731
2012-04-24 08:19:33,886 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.203443
2012-04-24 08:19:34,387 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.379053
2012-04-24 08:19:34,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.546681
2012-04-24 08:19:35,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.772180
2012-04-24 08:19:35,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 60.939808
2012-04-24 08:19:36,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.045573
2012-04-24 08:19:36,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.265086
2012-04-24 08:19:37,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.370851
2012-04-24 08:19:37,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.502558
2012-04-24 08:19:38,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.604332
2012-04-24 08:19:38,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.674177
2012-04-24 08:19:39,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.807880
2012-04-24 08:19:39,903 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 61.925619
2012-04-24 08:19:40,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.017415
2012-04-24 08:19:40,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.091251
2012-04-24 08:19:41,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.149122
2012-04-24 08:19:41,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.206994
2012-04-24 08:19:42,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.294799
2012-04-24 08:19:42,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.376617
2012-04-24 08:19:43,412 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.446462
2012-04-24 08:19:43,913 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.528280
2012-04-24 08:19:44,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.602116
2012-04-24 08:19:44,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.677948
2012-04-24 08:19:45,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.753779
2012-04-24 08:19:45,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.815642
2012-04-24 08:19:46,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.903447
2012-04-24 08:19:46,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 62.991252
2012-04-24 08:19:47,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.095022
2012-04-24 08:19:47,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.208769
2012-04-24 08:19:48,426 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.298570
2012-04-24 08:19:48,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.448237
2012-04-24 08:19:49,429 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.647794
2012-04-24 08:19:49,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.837373
2012-04-24 08:19:50,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 63.955112
2012-04-24 08:19:50,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 64.290367
2012-04-24 08:19:51,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 64.465977
2012-04-24 08:19:51,935 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 64.777286
2012-04-24 08:19:52,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 64.944913
2012-04-24 08:19:52,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.120523
2012-04-24 08:19:53,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.274182
2012-04-24 08:19:53,941 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.411876
2012-04-24 08:19:54,442 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.447797
2012-04-24 08:19:54,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.653340
2012-04-24 08:19:55,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.747132
2012-04-24 08:19:55,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.846910
2012-04-24 08:19:56,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.922742
2012-04-24 08:19:56,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 65.956667
2012-04-24 08:19:57,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.088374
2012-04-24 08:19:57,952 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.120303
2012-04-24 08:19:58,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.218086
2012-04-24 08:19:58,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.269971
2012-04-24 08:19:59,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.299904
2012-04-24 08:19:59,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.379727
2012-04-24 08:20:00,459 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.413652
2012-04-24 08:20:00,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.495470
2012-04-24 08:20:01,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.559328
2012-04-24 08:20:01,963 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.621191
2012-04-24 08:20:02,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.683053
2012-04-24 08:20:02,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.730947
2012-04-24 08:20:03,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.782832
2012-04-24 08:20:03,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.822743
2012-04-24 08:20:04,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.890592
2012-04-24 08:20:04,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.942477
2012-04-24 08:20:05,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 66.992366
2012-04-24 08:20:05,974 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.052234
2012-04-24 08:20:06,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.112101
2012-04-24 08:20:06,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.171968
2012-04-24 08:20:07,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.231835
2012-04-24 08:20:07,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.293697
2012-04-24 08:20:08,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.357555
2012-04-24 08:20:08,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.429396
2012-04-24 08:20:09,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.491259
2012-04-24 08:20:09,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.539152
2012-04-24 08:20:10,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.605006
2012-04-24 08:20:10,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.668864
2012-04-24 08:20:11,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.764651
2012-04-24 08:20:11,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.828510
2012-04-24 08:20:12,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.878399
2012-04-24 08:20:12,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.940261
2012-04-24 08:20:13,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 67.996137
2012-04-24 08:20:13,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.065982
2012-04-24 08:20:14,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.109885
2012-04-24 08:20:14,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.181725
2012-04-24 08:20:15,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.245583
2012-04-24 08:20:16,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.315428
2012-04-24 08:20:16,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.385273
2012-04-24 08:20:17,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.465096
2012-04-24 08:20:17,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.514985
2012-04-24 08:20:18,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.632724
2012-04-24 08:20:18,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.716537
2012-04-24 08:20:19,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.808334
2012-04-24 08:20:19,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 68.876183
2012-04-24 08:20:20,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.045806
2012-04-24 08:20:20,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.151571
2012-04-24 08:20:21,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.257336
2012-04-24 08:20:21,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.363102
2012-04-24 08:20:22,018 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.456893
2012-04-24 08:20:22,519 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.562658
2012-04-24 08:20:23,021 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.670419
2012-04-24 08:20:23,522 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.808113
2012-04-24 08:20:24,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.949799
2012-04-24 08:20:24,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 69.951794
2012-04-24 08:20:25,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.123413
2012-04-24 08:20:25,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.237160
2012-04-24 08:20:26,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.312992
2012-04-24 08:20:26,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.392815
2012-04-24 08:20:27,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.502571
2012-04-24 08:20:27,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.590376
2012-04-24 08:20:28,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.668203
2012-04-24 08:20:28,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.736053
2012-04-24 08:20:29,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.817871
2012-04-24 08:20:29,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.917649
2012-04-24 08:20:30,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 70.971530
2012-04-24 08:20:30,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.021419
2012-04-24 08:20:31,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.083281
2012-04-24 08:20:31,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.103237
2012-04-24 08:20:32,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.224967
2012-04-24 08:20:32,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.272860
2012-04-24 08:20:33,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.322750
2012-04-24 08:20:33,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.372639
2012-04-24 08:20:34,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.434501
2012-04-24 08:20:34,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.496364
2012-04-24 08:20:35,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.564213
2012-04-24 08:20:35,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.620089
2012-04-24 08:20:36,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.675965
2012-04-24 08:20:36,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.757783
2012-04-24 08:20:37,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.863549
2012-04-24 08:20:37,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 71.971309
2012-04-24 08:20:38,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.109004
2012-04-24 08:20:38,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.188826
2012-04-24 08:20:39,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.416321
2012-04-24 08:20:39,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.587940
2012-04-24 08:20:40,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 72.899249
2012-04-24 08:20:40,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 73.011000
2012-04-24 08:20:41,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 73.593706
2012-04-24 08:20:41,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 73.930957
2012-04-24 08:20:42,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 74.190381
2012-04-24 08:20:42,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 74.475747
2012-04-24 08:20:43,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 74.793043
2012-04-24 08:20:43,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 75.140272
2012-04-24 08:20:44,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 75.443598
2012-04-24 08:20:44,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 75.663111
2012-04-24 08:20:45,081 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 75.728964
2012-04-24 08:20:45,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.018322
2012-04-24 08:20:46,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.189941
2012-04-24 08:20:46,585 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.357568
2012-04-24 08:20:47,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.527192
2012-04-24 08:20:47,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.696815
2012-04-24 08:20:48,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.852469
2012-04-24 08:20:48,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 76.990163
2012-04-24 08:20:49,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.185729
2012-04-24 08:20:49,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.383290
2012-04-24 08:20:50,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.582847
2012-04-24 08:20:50,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.776417
2012-04-24 08:20:51,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 77.969988
2012-04-24 08:20:51,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.155575
2012-04-24 08:20:52,100 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.335177
2012-04-24 08:20:52,601 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.416995
2012-04-24 08:20:53,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.586618
2012-04-24 08:20:53,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.714334
2012-04-24 08:20:54,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.834069
2012-04-24 08:20:54,606 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 78.941829
2012-04-24 08:20:55,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.071541
2012-04-24 08:20:55,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.205244
2012-04-24 08:20:56,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.340943
2012-04-24 08:20:56,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.464668
2012-04-24 08:20:57,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.580411
2012-04-24 08:20:57,615 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.732074
2012-04-24 08:20:58,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 79.825866
2012-04-24 08:20:58,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.019436
2012-04-24 08:20:59,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.131188
2012-04-24 08:20:59,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.270878
2012-04-24 08:21:00,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.428528
2012-04-24 08:21:00,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.564226
2012-04-24 08:21:01,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.719881
2012-04-24 08:21:01,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 80.851588
2012-04-24 08:21:02,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.007242
2012-04-24 08:21:02,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.160901
2012-04-24 08:21:03,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.278640
2012-04-24 08:21:03,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.432298
2012-04-24 08:21:04,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.518108
2012-04-24 08:21:04,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.703696
2012-04-24 08:21:05,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 81.859350
2012-04-24 08:21:05,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.011013
2012-04-24 08:21:06,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.200592
2012-04-24 08:21:06,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.374207
2012-04-24 08:21:07,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.553808
2012-04-24 08:21:07,643 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.725427
2012-04-24 08:21:08,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 82.875094
2012-04-24 08:21:08,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.044718
2012-04-24 08:21:09,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.220328
2012-04-24 08:21:09,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.411902
2012-04-24 08:21:10,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.599486
2012-04-24 08:21:10,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.789065
2012-04-24 08:21:11,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 83.988621
2012-04-24 08:21:11,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.096382
2012-04-24 08:21:12,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.275983
2012-04-24 08:21:12,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.389731
2012-04-24 08:21:13,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.479531
2012-04-24 08:21:13,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.571327
2012-04-24 08:21:14,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.659132
2012-04-24 08:21:14,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.742946
2012-04-24 08:21:15,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.838733
2012-04-24 08:21:15,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.920552
2012-04-24 08:21:16,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 84.998379
2012-04-24 08:21:16,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.090175
2012-04-24 08:21:17,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.209909
2012-04-24 08:21:17,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.333634
2012-04-24 08:21:18,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.493280
2012-04-24 08:21:18,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.672881
2012-04-24 08:21:19,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 85.882416
2012-04-24 08:21:19,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.085964
2012-04-24 08:21:20,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.287516
2012-04-24 08:21:20,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.511020
2012-04-24 08:21:21,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.752483
2012-04-24 08:21:21,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 86.912129
2012-04-24 08:21:22,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.109690
2012-04-24 08:21:22,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.293282
2012-04-24 08:21:23,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.504813
2012-04-24 08:21:23,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.668449
2012-04-24 08:21:24,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 87.854037
2012-04-24 08:21:24,690 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.023660
2012-04-24 08:21:25,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.189293
2012-04-24 08:21:25,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.402818
2012-04-24 08:21:26,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.598384
2012-04-24 08:21:26,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 88.847830
2012-04-24 08:21:27,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.071334
2012-04-24 08:21:27,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.185081
2012-04-24 08:21:28,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.318784
2012-04-24 08:21:28,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.472443
2012-04-24 08:21:29,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.598164
2012-04-24 08:21:29,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.755814
2012-04-24 08:21:30,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 89.849605
2012-04-24 08:21:30,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.021224
2012-04-24 08:21:31,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.126989
2012-04-24 08:21:31,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.220781
2012-04-24 08:21:32,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.356480
2012-04-24 08:21:32,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.434307
2012-04-24 08:21:33,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.526103
2012-04-24 08:21:33,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.615904
2012-04-24 08:21:34,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.713686
2012-04-24 08:21:34,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.807478
2012-04-24 08:21:35,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.911248
2012-04-24 08:21:35,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 90.999053
2012-04-24 08:21:36,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.110805
2012-04-24 08:21:36,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.192623
2012-04-24 08:21:37,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.288410
2012-04-24 08:21:37,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.372224
2012-04-24 08:21:38,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.444064
2012-04-24 08:21:38,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.527878
2012-04-24 08:21:39,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.597723
2012-04-24 08:21:39,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.669564
2012-04-24 08:21:40,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.753378
2012-04-24 08:21:40,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.835881
2012-04-24 08:21:40,593 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.835881
2012-04-24 08:21:40,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.835881
2012-04-24 08:21:40,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.837446
2012-04-24 08:21:41,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 91.877358
2012-04-24 08:21:41,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.046981
2012-04-24 08:21:42,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.184675
2012-04-24 08:21:42,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.240551
2012-04-24 08:21:43,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.482015
2012-04-24 08:21:43,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.709510
2012-04-24 08:21:44,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 92.885120
2012-04-24 08:21:44,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.038778
2012-04-24 08:21:45,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.168490
2012-04-24 08:21:45,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.266273
2012-04-24 08:21:46,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.374034
2012-04-24 08:21:46,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.473812
2012-04-24 08:21:47,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.597538
2012-04-24 08:21:47,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.699312
2012-04-24 08:21:48,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.803081
2012-04-24 08:21:48,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 93.908846
2012-04-24 08:21:49,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.032571
2012-04-24 08:21:49,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.174257
2012-04-24 08:21:50,462 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.313947
2012-04-24 08:21:50,964 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.493548
2012-04-24 08:21:51,465 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 94.727029
2012-04-24 08:21:51,966 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 95.006409
2012-04-24 08:21:52,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 95.323704
2012-04-24 08:21:52,969 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 95.593106
2012-04-24 08:21:53,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.072042
2012-04-24 08:21:53,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.263617
2012-04-24 08:21:54,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.401311
2012-04-24 08:21:54,974 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.580912
2012-04-24 08:21:55,476 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.752531
2012-04-24 08:21:55,977 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 96.874261
2012-04-24 08:21:56,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.029915
2012-04-24 08:21:56,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.199538
2012-04-24 08:21:57,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.367166
2012-04-24 08:21:57,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.486900
2012-04-24 08:21:58,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.588674
2012-04-24 08:21:58,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.702421
2012-04-24 08:21:59,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.822156
2012-04-24 08:21:59,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 97.913952
2012-04-24 08:22:00,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.025704
2012-04-24 08:22:00,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.123486
2012-04-24 08:22:01,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.257189
2012-04-24 08:22:01,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.380915
2012-04-24 08:22:02,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.530582
2012-04-24 08:22:02,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.628365
2012-04-24 08:22:03,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.718166
2012-04-24 08:22:03,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.799984
2012-04-24 08:22:04,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.895771
2012-04-24 08:22:05,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 98.981581
2012-04-24 08:22:05,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.091337
2012-04-24 08:22:06,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.191115
2012-04-24 08:22:06,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.290894
2012-04-24 08:22:07,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.388677
2012-04-24 08:22:07,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.516393
2012-04-24 08:22:08,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.678034
2012-04-24 08:22:08,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 99.849653
2012-04-24 08:22:08,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16891L> 100.000000
2012-04-24 08:22:09,078 DEBUG: install progress dpkg-exec 0.000000
2012-04-24 08:22:09,857 DEBUG: install progress dkms 0.000000
2012-04-24 08:22:09,958 DEBUG: install progress dkms 6.666670
2012-04-24 08:22:10,844 DEBUG: install progress dkms 13.333300
2012-04-24 08:22:11,047 DEBUG: install progress dkms 20.000000
2012-04-24 08:22:12,074 DEBUG: install progress fglrx-updates 20.000000
2012-04-24 08:22:12,174 DEBUG: install progress fglrx-updates 26.666700
2012-04-24 08:22:18,891 DEBUG: install progress fglrx-updates 33.333300
2012-04-24 08:22:19,067 DEBUG: install progress fglrx-updates 40.000000
2012-04-24 08:22:19,551 DEBUG: install progress fglrx-amdcccle-updates 40.000000
2012-04-24 08:22:19,652 DEBUG: install progress fglrx-amdcccle-updates 46.666700
2012-04-24 08:22:21,091 DEBUG: install progress fglrx-amdcccle-updates 53.333300
2012-04-24 08:22:21,265 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-04-24 08:22:21,437 DEBUG: install progress man-db 60.000000
2012-04-24 08:22:23,277 DEBUG: install progress ureadahead 60.000000
2012-04-24 08:22:24,000 DEBUG: install progress dpkg-exec 60.000000
2012-04-24 08:22:24,035 DEBUG: install progress dkms 60.000000
2012-04-24 08:22:27,160 DEBUG: install progress dkms 66.666700
2012-04-24 08:22:27,356 DEBUG: install progress dkms 73.333300
2012-04-24 08:22:27,551 DEBUG: install progress fglrx-updates 73.333300
2012-04-24 08:22:28,345 DEBUG: install progress fglrx-updates 80.000000
2012-04-24 08:22:56,203 DEBUG: install progress fglrx-updates 86.666700
2012-04-24 08:22:57,180 DEBUG: install progress bamfdaemon 86.666700
2012-04-24 08:22:57,761 DEBUG: install progress fglrx-amdcccle-updates 86.666700
2012-04-24 08:22:57,951 DEBUG: install progress fglrx-amdcccle-updates 93.333300
2012-04-24 08:22:58,140 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-04-24 08:22:58,342 DEBUG: install progress initramfs-tools 100.000000
2012-04-24 08:23:12,656 DEBUG: install progress libc-bin 100.000000
2012-04-24 08:23:15,665 DEBUG: Selecting previously unselected package dkms.
(Reading database ... 174424 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-23-generic
Building for architecture x86_64
Building initial module for 3.2.0-23-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic/updates/dkms/

depmod......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
Warning: No support for locale: en_US.utf8
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-04-24 08:23:15,882 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-24 08:23:35,952 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:35,952 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:35,982 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:35,983 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,671 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,671 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,702 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,703 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,761 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,762 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-24 08:23:43,834 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,834 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,865 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,866 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,951 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,951 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:43,982 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:43,983 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:23:44,036 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:23:44,037 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-24 08:23:48,963 DEBUG: Shutting down
2012-04-24 08:28:27,576 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0>
2012-04-24 08:28:29,045 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-04-24 08:28:29,111 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-24 08:28:29,111 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-24 08:28:29,163 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-24 08:28:29,172 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-24 08:28:29,200 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-24 08:28:29,201 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-24 08:28:29,201 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-24 08:28:29,223 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-24 08:28:29,223 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:29,327 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 08:28:29,334 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 08:28:29,343 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-24 08:28:29,343 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:29,399 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-24 08:28:29,400 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-24 08:28:29,431 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-24 08:28:29,447 DEBUG: Software modem not available
2012-04-24 08:28:29,447 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-24 08:28:29,456 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-24 08:28:29,457 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-24 08:28:29,457 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-24 08:28:29,457 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-24 08:28:29,464 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-24 08:28:29,465 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-24 08:28:29,493 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-24 08:28:29,493 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-24 08:28:29,531 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-24 08:28:29,532 DEBUG: Firmware for DVB cards not available
2012-04-24 08:28:29,532 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-24 08:28:29,543 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-24 08:28:29,553 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-24 08:28:29,603 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-24 08:28:29,604 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-24 08:28:29,616 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-24 08:28:29,625 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-24 08:28:29,628 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,628 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:28:29,635 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 08:28:29,644 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-24 08:28:29,645 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,645 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:28:29,652 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 08:28:29,660 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-24 08:28:29,662 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,662 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:28:29,668 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-24 08:28:29,677 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-24 08:28:29,678 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,679 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:28:29,685 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-24 08:28:29,694 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-24 08:28:29,695 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,695 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 08:28:29,702 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-24 08:28:29,711 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-24 08:28:29,712 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-04-24 08:28:29,712 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 08:28:29,712 DEBUG: all custom handlers loaded
2012-04-24 08:28:29,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 08:28:29,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 08:28:29,725 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:29,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,792 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:29,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 08:28:29,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 08:28:29,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000103Csd00001657bc07sc80i00')
2012-04-24 08:28:29,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-04-24 08:28:29,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:dock')
2012-04-24 08:28:29,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 08:28:29,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-24 08:28:29,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-24 08:28:29,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-24 08:28:29,980 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:29,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,980 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:29,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-24 08:28:29,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-24 08:28:29,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-24 08:28:29,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00001002d00006740sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:28:30,183 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-24 08:28:30,207 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,208 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:30,183 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:28:30,217 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:30,272 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,272 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:30,247 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:28:30,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-24 08:28:30,298 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,298 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-24 08:28:30,273 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-24 08:28:30,305 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 08:28:30,314 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:30,370 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,370 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-04-24 08:28:30,344 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-24 08:28:30,371 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-24 08:28:30,371 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,371 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-04-24 08:28:30,396 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,397 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:30,371 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:28:30,405 DEBUG: fglrx.available: falling back to default
2012-04-24 08:28:30,460 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,460 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:30,434 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-24 08:28:30,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-24 08:28:30,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2012-04-24 08:28:30,470 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-24 08:28:30,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 08:28:30,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 08:28:30,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00000116sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:28:30,478 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-04-24 08:28:30,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00001657bc02sc00i00')
2012-04-24 08:28:30,487 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-04-24 08:28:30,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 08:28:30,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000103Csd00001657bc06sc01i00')
2012-04-24 08:28:30,489 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-24 08:28:30,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc02ip00')
2012-04-24 08:28:30,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 08:28:30,489 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 08:28:30,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-24 08:28:30,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,490 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:28:30,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-24 08:28:30,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:28:30,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-24 08:28:30,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 08:28:30,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1B:bd10/05/2011:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvr0589110014244710000620100:rvnHewlett-Packard:rn1657:rvr10.31:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-24 08:28:30,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 08:28:30,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000103Csd00001657bc01sc06i01')
2012-04-24 08:28:30,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-24 08:28:30,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:30,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-04-24 08:28:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:28:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v138Ap0018d0078dcFFdsc11dpFFicFFisc00ip00')
2012-04-24 08:28:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:28:30,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0003v5986p02ACe0924-e0,1,kD4,ramlsfw')
2012-04-24 08:28:30,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:30,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:SYN1E47:SYN1E00:SYN0002:PNP0F13:')
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-24 08:28:30,508 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-04-24 08:28:30,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:28:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-24 08:28:30,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-24 08:28:30,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc01ip00')
2012-04-24 08:28:30,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-24 08:28:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 08:28:30,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'platform:regulatory')
2012-04-24 08:28:30,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000103Csd00001657bc0Csc05i00')
2012-04-24 08:28:30,512 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-04-24 08:28:30,512 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000103Csd00001657bc04sc03i00')
2012-04-24 08:28:30,514 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 08:28:30,514 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,514 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 08:28:30,514 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v00001033d00000194sv0000103Csd00001657bc0Csc03i30')
2012-04-24 08:28:30,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 08:28:30,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 08:28:30,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'pci:v000010ECd00005209sv0000103Csd00001657bcFFsc00i00')
2012-04-24 08:28:30,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2012-04-24 08:28:30,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x221eef0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000103Csd00001657bc07sc80i00')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:dock')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 08:28:30,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00001002d00006740sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00000084sv00008086sd00001315bc02sc80i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00000116sv0000103Csd00001657bc03sc00i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00001657bc02sc00i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000103Csd00001657bc06sc01i00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc02ip00')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-24 08:28:30,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1B:bd10/05/2011:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvr0589110014244710000620100:rvnHewlett-Packard:rn1657:rvr10.31:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000103Csd00001657bc01sc06i01')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v138Ap0018d0078dcFFdsc11dpFFicFFisc00ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000103Csd00001657bc0Csc03i20')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0003v5986p02ACe0924-e0,1,kD4,ramlsfw')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:SYN1E47:SYN1E00:SYN0002:PNP0F13:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'usb:v5986p02ACd0924dcEFdsc02dp01ic0Eisc01ip00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'platform:regulatory')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000103Csd00001657bc0Csc05i00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000103Csd00001657bc04sc03i00')
2012-04-24 08:28:30,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v00001033d00000194sv0000103Csd00001657bc0Csc03i30')
2012-04-24 08:28:30,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 08:28:30,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-24 08:28:30,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'pci:v000010ECd00005209sv0000103Csd00001657bcFFsc00i00')
2012-04-24 08:28:30,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x25940e0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 08:28:30,566 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-24 08:28:30,566 DEBUG: fglrx_updates is not the alternative in use
2012-04-24 08:28:32,474 DEBUG: Shutting down
```

---

