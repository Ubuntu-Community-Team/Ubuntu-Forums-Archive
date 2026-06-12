---
title: "rtl8192su headache"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by icanhaszombie on 2010-10-13
Alright, so I've googled this subject for almost 3 hours and have found a similar cases but no resolution, so i figure it's safe to inquire. I have a D-Link DWA-130E USB wireless dongle, which is really just a Realtek RTL8192SU as far as Ubuntu is concerned. After initial install of 10.10 (64-bit) it was visible to network manager and iwconfig but not ifconfig. 

```
jer@Sisyphus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:177  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

wlan0     802.11b/g  ESSID:"D-Link"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
jer@Sisyphus:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:18:f8:ae:6d:8d  
          inet addr:192.168.1.83  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:feae:6d8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85220 errors:0 dropped:0 overruns:0 frame:282027
          TX packets:78590 errors:57 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54338719 (54.3 MB)  TX bytes:27069811 (27.0 MB)
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:205387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37662715 (37.6 MB)  TX bytes:37662715 (37.6 MB)


```

eth1 is an old Broadcom PCI card I had to install just to get wireless working. Trying to turn on wlan0 results thusly

```
jer@Sisyphus:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Resource temporarily unavailable

```

All I can find via google is that it may or may not be a driver issue. Any ideas?

---

### Post by P4man on 2010-10-13
Im confused, eth1 appears to be a wireless connection in the output of iwconfig?

---

### Post by Peter09 on 2010-10-13
When you do ifconfig you really should not have the wired card connected. It can confuse the issue as the wireless network will be disabled while the wired connection is active.

---

### Post by icanhaszombie on 2010-10-13
> Im confused, eth1 appears to be a wireless connection in the output of iwconfig?

You got it. Eth1 is a Broadcom PCI wireless card, don't ask me why it got labelled as a wired connection.

> When you do ifconfig you really should not have the wired card connected. It can confuse the issue as the wireless network will be disabled while the wired connection is active.

Duly noted, I'll remove it and try it again, though I was experiencing the same errors prior to the installation of the Broadcom card.

---

### Post by icanhaszombie on 2010-10-13
SO, d/c'd the PCI card and ran it all again, same response. Resource temporarily unavailable.

---

### Post by icanhaszombie on 2010-10-13
hate to triple-post but I ran dmesg usb and this came up

```
   54.770042] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   54.929040] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   54.932148] ieee80211_crypt: registered algorithm 'NULL'
[   54.932150] ieee80211_crypt: registered algorithm 'TKIP'
[   54.932152] ieee80211_crypt: registered algorithm 'CCMP'
[   54.932153] ieee80211_crypt: registered algorithm 'WEP'
[   54.932154] 
[   54.932155] Linux kernel driver for RTL8192 based WLAN cards
[   54.932156] Copyright (c) 2007-2008, Realsil Wlan
[   54.932286] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[   54.932287] ==>RtInPipes:3  
[   54.932289] ==>RtOutPipes:4  6  13  
[   54.932291] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[   54.932292] 1  1  0  0  2  2  2  2  2  
[   55.185215] Dot11d_Init()
[   55.185879] usbcore: registered new interface driver rtl819xU
[   55.215858] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   55.215860] 
[   55.216081] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   55.216083] 
[   55.230328] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   55.230330] 
[   55.230577] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   55.230579] 
[   55.230581] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   55.230582] 
[   55.246075] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   55.246077] 
[   55.246323] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   55.246325] 
[   55.259947] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   55.259948] 
[   55.260197] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   55.260198] 
[   55.260201] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   55.260202] 
[   82.941617] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   82.941620] 
[   82.941858] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   82.941861] 
[   82.958370] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   82.958374] 
[   82.958589] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   82.958593] 
[   82.958599] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   82.958602] 

```

I'm not fluent in error message but I'm pretty sure that says my firmware is the cause of my trouble?

---

### Post by fight2survive on 2010-10-13
this post might be useful to you. made my rtl8192 work on 10.4

[http://ubuntuforums.org/showpost.php?p=8566513&postcount=14](http://ubuntuforums.org/showpost.php?p=8566513&postcount=14)

---

### Post by icanhaszombie on 2010-10-14
thanks! I tried it, but to no avail. :\

dmesg output has changed slightly now. It's been showing that bit about the USB cable sometimes randomly at startup and I still don't know what to make of it. Here's everything that didn't scroll off the terminal. 

```
[    0.383644] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfe9fffff]
[    0.383646] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.383648] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.383650] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.383652] pci_bus 0000:02: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.383654] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.383655] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.383657] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.383659] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.383660] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.383662] pci_bus 0000:03: resource 8 [mem 0x80000000-0xdfffffff]
[    0.383664] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.383691] NET: Registered protocol family 2
[    0.383773] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.384331] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.385674] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.385996] TCP: Hash tables configured (established 262144 bind 65536)
[    0.385998] TCP reno registered
[    0.386005] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.386021] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.386112] NET: Registered protocol family 1
[    0.571712] pci 0000:01:00.0: Boot video device
[    0.571721] PCI: CLS 64 bytes, default 64
[    0.581739] Freeing initrd memory: 10752k freed
[    0.585675] Scanning for low memory corruption every 60 seconds
[    0.585767] audit: initializing netlink socket (disabled)
[    0.585775] type=2000 audit(1287010764.580:1): initialized
[    0.595543] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.596560] VFS: Disk quotas dquot_6.5.2
[    0.596606] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.597067] fuse init (API version 7.14)
[    0.597161] msgmni has been set to 4010
[    0.598859] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.598862] io scheduler noop registered
[    0.598863] io scheduler deadline registered
[    0.598890] io scheduler cfq registered (default)
[    0.599023] pcieport 0000:00:02.0: setting latency timer to 64
[    0.599045]   alloc irq_desc for 40 on node 0
[    0.599047]   alloc kstat_irqs on node 0
[    0.599054] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.599173] pcieport 0000:00:06.0: setting latency timer to 64
[    0.599192]   alloc irq_desc for 41 on node 0
[    0.599193]   alloc kstat_irqs on node 0
[    0.599197] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    0.599292] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.599308] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.599438] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.599447] ACPI: Power Button [PWRB]
[    0.599476] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.599478] ACPI: Power Button [PWRF]
[    0.599695] ACPI: acpi_idle registered with cpuidle
[    0.601318] ERST: Table is not found!
[    0.601452] Linux agpgart interface v0.103
[    0.601455] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.601560] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.601799] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.602492] brd: module loaded
[    0.602805] loop: module loaded
[    0.602999]   alloc irq_desc for 16 on node 0
[    0.603001]   alloc kstat_irqs on node 0
[    0.603007] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.603030] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.603322] Fixed MDIO Bus: probed
[    0.603346] PPP generic driver version 2.4.2
[    0.603388] tun: Universal TUN/TAP device driver, 1.6
[    0.603389] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.603447] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.603523]   alloc irq_desc for 17 on node 0
[    0.603526]   alloc kstat_irqs on node 0
[    0.603533] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.603551] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.603613] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.603641] ehci_hcd 0000:00:12.2: debug port 1
[    0.603662] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf9fff800
[    0.621623] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.621744] hub 1-0:1.0: USB hub found
[    0.621747] hub 1-0:1.0: 6 ports detected
[    0.621874]   alloc irq_desc for 19 on node 0
[    0.621876]   alloc kstat_irqs on node 0
[    0.621881] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.621898] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.621926] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.621953] ehci_hcd 0000:00:13.2: debug port 1
[    0.621973] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf9fff400
[    0.641632] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.641754] hub 2-0:1.0: USB hub found
[    0.641757] hub 2-0:1.0: 6 ports detected
[    0.641857] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.641910] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.641926] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.641954] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.641980] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf9ffe000
[    0.705744] hub 3-0:1.0: USB hub found
[    0.705751] hub 3-0:1.0: 3 ports detected
[    0.705875] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.705892] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.705921] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.705939] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf9ffd000
[    0.765742] hub 4-0:1.0: USB hub found
[    0.765749] hub 4-0:1.0: 3 ports detected
[    0.765880]   alloc irq_desc for 18 on node 0
[    0.765882]   alloc kstat_irqs on node 0
[    0.765887] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.765904] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.765937] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.765963] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf9ffc000
[    0.825767] hub 5-0:1.0: USB hub found
[    0.825773] hub 5-0:1.0: 3 ports detected
[    0.825896] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.825914] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.825941] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.825958] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf9ffb000
[    0.885742] hub 6-0:1.0: USB hub found
[    0.885748] hub 6-0:1.0: 3 ports detected
[    0.885873] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.885890] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    0.885919] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    0.885937] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf9ffa000
[    0.945739] hub 7-0:1.0: USB hub found
[    0.945746] hub 7-0:1.0: 2 ports detected
[    0.945838] uhci_hcd: USB Universal Host Controller Interface driver
[    0.945931] PNP: No PS/2 controller found. Probing ports directly.
[    0.946285] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.946296] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.946367] mice: PS/2 mouse device common for all mice
[    0.946438] rtc_cmos 00:02: RTC can wake from S4
[    0.946466] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.946492] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.946555] device-mapper: uevent: version 1.0.3
[    0.946634] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.946708] device-mapper: multipath: version 1.1.1 loaded
[    0.946712] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.946912] cpuidle: using governor ladder
[    0.946913] cpuidle: using governor menu
[    0.947105] TCP cubic registered
[    0.947186] NET: Registered protocol family 10
[    0.947442] lo: Disabled Privacy Extensions
[    0.947580] NET: Registered protocol family 17
[    0.947614] powernow-k8: Found 1 AMD Athlon(tm) II X2 240 Processor (2 cpu cores) (version 2.20.00)
[    0.947648] powernow-k8:    0 : pstate 0 (2800 MHz)
[    0.947649] powernow-k8:    1 : pstate 1 (2100 MHz)
[    0.947651] powernow-k8:    2 : pstate 2 (1600 MHz)
[    0.947652] powernow-k8:    3 : pstate 3 (800 MHz)
[    0.947860] PM: Resume from disk failed.
[    0.947870] registered taskstats version 1
[    0.948074]   Magic number: 14:777:1007
[    0.948101] system 00:09: hash matches
[    0.948150] rtc_cmos 00:02: setting system clock to 2010-10-13 22:59:25 UTC (1287010765)
[    0.948153] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.948154] EDD information not available.
[    0.948212] Freeing unused kernel memory: 908k freed
[    0.948391] Write protecting the kernel read-only data: 10240k
[    0.948511] Freeing unused kernel memory: 416k freed
[    0.948726] Freeing unused kernel memory: 1644k freed
[    0.965679] udev[109]: starting version 163
[    1.048032] scsi0 : pata_atiixp
[    1.048208] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.048227] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.048259] r8169 0000:02:00.0: setting latency timer to 64
[    1.048291]   alloc irq_desc for 42 on node 0
[    1.048292]   alloc kstat_irqs on node 0
[    1.048303] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.048668] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc9000033a000, 40:61:86:02:b8:e4, XID 081000c0 IRQ 42
[    1.099472] scsi1 : pata_atiixp
[    1.100450] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.100453] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.100726] ahci 0000:00:11.0: version 3.0
[    1.100737]   alloc irq_desc for 22 on node 0
[    1.100738]   alloc kstat_irqs on node 0
[    1.100743] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.100836] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.100839] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.101061] scsi2 : ahci
[    1.101119] scsi3 : ahci
[    1.101160] scsi4 : ahci
[    1.101198] scsi5 : ahci
[    1.101284] ata3: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd00 irq 22
[    1.101287] ata4: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd80 irq 22
[    1.101290] ata5: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe00 irq 22
[    1.101293] ata6: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe80 irq 22
[    1.220039] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    1.316842] ata1.00: ATA-8: WDC WD3200AAJS-00VWA0, 12.01B02, max UDMA/133
[    1.316845] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.331275] ata1.00: configured for UDMA/100
[    1.331447] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-0 12.0 PQ: 0 ANSI: 5
[    1.331588] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.331675] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.331748] sd 0:0:0:0: [sda] Write Protect is off
[    1.331750] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.331773] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.331934]  sda: sda1 sda2 < sda5 >
[    1.351107] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.450050] ata6: SATA link down (SStatus 0 SControl 300)
[    1.450079] ata3: SATA link down (SStatus 0 SControl 300)
[    1.450104] ata4: SATA link down (SStatus 0 SControl 300)
[    1.630044] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.640281] ata5.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[    1.640284] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.640872] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    1.641163] ata5.00: configured for UDMA/133
[    1.660175] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[    1.660310] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.660326] sd 4:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.660367] sd 4:0:0:0: [sdb] Write Protect is off
[    1.660369] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.660389] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.660523]  sdb: sdb1
[    1.667798] sd 4:0:0:0: [sdb] Attached SCSI disk
[    1.672604] usbcore: registered new interface driver hiddev
[    1.677774] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input2
[    1.677845] generic-usb 0003:046D:C315.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:12.0-1/input0
[    1.677861] usbcore: registered new interface driver usbhid
[    1.677862] usbhid: USB HID core driver
[    1.798735] Initializing USB Mass Storage driver...
[    1.798833] scsi6 : usb-storage 2-4:1.0
[    1.798897] usbcore: registered new interface driver usb-storage
[    1.798899] USB Mass Storage support registered.
[    1.828865] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    1.828869] EXT4-fs (sda5): write access will be enabled during recovery
[    2.220038] usb 5-1: new full speed USB device using ohci_hcd and address 2
[    2.445811] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input3
[    2.445881] generic-usb 0003:046D:C52B.0002: input,hidraw1: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-1/input0
[    2.450882] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input4
[    2.451021] generic-usb 0003:046D:C52B.0003: input,hiddev96,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1/input1
[    2.459703] generic-usb 0003:046D:C52B.0004: hiddev97,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-1/input2
[    2.820714] scsi 6:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[    2.821104] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.822705] sd 6:0:0:0: [sdc] 3946367 512-byte logical blocks: (2.02 GB/1.88 GiB)
[    2.823205] sd 6:0:0:0: [sdc] Write Protect is off
[    2.823209] sd 6:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[    2.823211] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.825314] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.825324]  sdc: sdc1
[    2.829904] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.829907] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    2.840529] EXT4-fs (sda5): orphan cleanup on readonly fs
[    2.840537] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794238
[    2.840563] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 2359764
[    2.840594] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 2363043
[    2.840639] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 2363042
[    2.840648] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794235
[    2.840657] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794232
[    2.840665] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794230
[    2.840671] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794222
[    2.840679] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794216
[    2.840687] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794214
[    2.840696] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794211
[    2.840704] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794197
[    2.840713] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 794195
[    2.840722] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5242943
[    2.840741] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 2363041
[    2.840751] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 2359886
[    2.840760] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5242941
[    2.840768] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5242940
[    2.840779] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 2360200
[    2.840788] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 2359984
[    2.840805] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 5242934
[    2.840813] EXT4-fs (sda5): 21 orphan inodes deleted
[    2.840837] EXT4-fs (sda5): recovery complete
[    3.324855] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    5.820036] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[    9.030040] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   11.822228] udev[465]: starting version 163
[   11.939002] Adding 975868k swap on /dev/sda1.  Priority:-1 extents:1 across:975868k 
[   11.976885] EDAC MC: Ver: 2.1.0 Oct 10 2010
[   11.990199] lib80211: common routines for IEEE802.11 drivers
[   11.990202] lib80211_crypt: registered algorithm 'NULL'
[   11.993735] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.993738] Disabling lock debugging due to kernel taint
[   11.995635] lp: driver loaded but no devices found
[   12.039503] EDAC amd64_edac:  Ver: 3.3.0 Oct 10 2010
[   12.050683] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [bus b00-b0f pref window disabled]
[   12.050686] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.051172] wl 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.077845] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   12.077852] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   12.077853]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   12.077854]  (Note that use of the override may cause unknown side effects.)
[   12.077865] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   12.086443] type=1400 audit(1287010776.627:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=725 comm="apparmor_parser"
[   12.086657] type=1400 audit(1287010776.627:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=725 comm="apparmor_parser"
[   12.086776] type=1400 audit(1287010776.627:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=725 comm="apparmor_parser"
[   12.118677] lib80211_crypt: registered algorithm 'TKIP'
[   12.118782] eth1: Broadcom BCM4329 802.11 Hybrid Wireless Controller 5.60.48.36 
[   12.181929] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.242603] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   12.255619] hda_codec: ALC889A: BIOS auto-probing.
[   12.271391] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   12.375509] type=1400 audit(1287010776.917:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1003 comm="apparmor_parser"
[   12.375723] type=1400 audit(1287010776.917:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1003 comm="apparmor_parser"
[   12.375842] type=1400 audit(1287010776.917:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1003 comm="apparmor_parser"
[   12.379176] type=1400 audit(1287010776.917:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1002 comm="apparmor_parser"
[   12.381987] type=1400 audit(1287010776.927:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1005 comm="apparmor_parser"
[   12.384717] type=1400 audit(1287010776.927:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1005 comm="apparmor_parser"
[   12.385157] type=1400 audit(1287010776.927:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1010 comm="apparmor_parser"
[   12.637500] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.637508] nvidia 0000:01:00.0: setting latency timer to 64
[   12.637512] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.637666] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   12.785604] r8169 0000:02:00.0: eth0: link down
[   12.785849] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.207459] ppdev: user-space parallel port driver
[   13.597209] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   15.520040] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   15.520048] hub 6-0:1.0: unable to enumerate USB device on port 2
[   16.749696] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   22.240018] eth1: no IPv6 routers present
[   54.770042] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   54.929040] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   54.932148] ieee80211_crypt: registered algorithm 'NULL'
[   54.932150] ieee80211_crypt: registered algorithm 'TKIP'
[   54.932152] ieee80211_crypt: registered algorithm 'CCMP'
[   54.932153] ieee80211_crypt: registered algorithm 'WEP'
[   54.932154] 
[   54.932155] Linux kernel driver for RTL8192 based WLAN cards
[   54.932156] Copyright (c) 2007-2008, Realsil Wlan
[   54.932286] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[   54.932287] ==>RtInPipes:3  
[   54.932289] ==>RtOutPipes:4  6  13  
[   54.932291] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[   54.932292] 1  1  0  0  2  2  2  2  2  
[   55.185215] Dot11d_Init()
[   55.185879] usbcore: registered new interface driver rtl819xU
[   55.215858] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   55.215860] 
[   55.216081] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   55.216083] 
[   55.230328] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   55.230330] 
[   55.230577] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   55.230579] 
[   55.230581] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   55.230582] 
[   55.246075] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   55.246077] 
[   55.246323] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   55.246325] 
[   55.259947] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   55.259948] 
[   55.260197] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   55.260198] 
[   55.260201] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   55.260202] 
[   82.941617] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   82.941620] 
[   82.941858] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   82.941861] 
[   82.958370] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   82.958374] 
[   82.958589] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   82.958593] 
[   82.958599] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   82.958602] 
[   88.340025] lo: Disabled Privacy Extensions
[  622.720078] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[  626.030080] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[  629.310079] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[  632.610906] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[  632.610925] hub 6-0:1.0: unable to enumerate USB device on port 2
[ 1358.876053] lo: Disabled Privacy Extensions
[17630.335545] lo: Disabled Privacy Extensions
[17812.851972] ieee80211_crypt: registered algorithm 'NULL'
[17812.851981] ieee80211_crypt: registered algorithm 'TKIP'
[17812.851986] ieee80211_crypt: registered algorithm 'CCMP'
[17812.851991] ieee80211_crypt: registered algorithm 'WEP'
[17812.852001] ------------[ cut here ]------------
[17812.852014] WARNING: at /build/buildd/linux-2.6.35/fs/proc/generic.c:583 proc_register+0x118/0x200()
[17812.852020] Hardware name: MS-7388
[17812.852025] proc_dir_entry 'net/ieee80211' already registered
[17812.852028] Modules linked in: r8192_pci(+) r8192s_usb(C) eeprom_93cx6 nls_iso8859_1 nls_cp437 vfat fat parport_pc ppdev binfmt_misc nvidia(P) snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi lib80211_crypt_tkip snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd wl(P) psmouse lib80211 joydev serio_raw edac_core soundcore lp edac_mce_amd snd_page_alloc i2c_piix4 parport k10temp usb_storage usbhid hid ahci r8169 mii libahci pata_atiixp
[17812.852103] Pid: 4269, comm: modprobe Tainted: P         C  2.6.35-22-generic #34-Ubuntu
[17812.852109] Call Trace:
[17812.852123]  [<ffffffff8106077f>] warn_slowpath_common+0x7f/0xc0
[17812.852131]  [<ffffffff81060876>] warn_slowpath_fmt+0x46/0x50
[17812.852140]  [<ffffffff811b0a98>] proc_register+0x118/0x200
[17812.852148]  [<ffffffff811b0da7>] ? __proc_create+0xf7/0x150
[17812.852173]  [<ffffffffa02e6000>] ? rtl8192_pci_module_init+0x0/0xc7 [r8192_pci]
[17812.852181]  [<ffffffff811b0f2e>] create_proc_entry+0x5e/0xb0
[17812.852204]  [<ffffffffa02e6147>] ieee80211_init+0x80/0xfb [r8192_pci]
[17812.852224]  [<ffffffffa02e600e>] rtl8192_pci_module_init+0xe/0xc7 [r8192_pci]
[17812.852233]  [<ffffffff8100204c>] do_one_initcall+0x3c/0x1a0
[17812.852243]  [<ffffffff8109bc6b>] sys_init_module+0xbb/0x200
[17812.852252]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
[17812.852258] ---[ end trace e9ef7ad09375957f ]---
[17812.852264] 
[17812.852266] Linux kernel driver for RTL8192 based WLAN cards
[17812.852270] Copyright (c) 2007-2008, Realsil Wlan
[17850.340531] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[17850.340535] 
[17850.340792] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[17850.340796] 
[17850.357787] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[17850.357791] 
[17850.358038] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[17850.358042] 
[17850.358049] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[17850.358052] 
[17856.830087] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17860.060096] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17863.260080] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17866.530913] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17866.530932] hub 6-0:1.0: unable to enumerate USB device on port 2
[18185.540087] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[18188.780909] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[18192.040082] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[18195.290068] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[18195.290086] hub 6-0:1.0: unable to enumerate USB device on port 2
[18339.200083] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[18342.400087] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[18345.610071] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[18348.820081] hub 6-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[18348.820099] hub 6-0:1.0: unable to enumerate USB device on port 2

```

---

