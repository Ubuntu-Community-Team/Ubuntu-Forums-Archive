---
title: "On/Off Wifi Ubuntu 12.04 Advent T1600"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by T Bone on 2012-09-14
Hello all, 

I have been running Ubuntu 12.04 on my Advent T1600 for a while now; yesterday the wireless just disconnected and refused to reconnect!

My other devices are connecting with no problems, and I can connect via an ethernet cable. It used to connect automatically but nothing is happening now; when I search for hidden wireless networks I can find the network, but it keeps asking me to authenticate. I do this, but it still fails to connect. Any advice or assistance greatly appreciated!

As requested elsewhere, here's some info:

lspci...


"00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)"


lsusb...


"Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader"

ifconfig...

"eth0      Link encap:Ethernet  HWaddr 00:03:0d:ba:b3:fb  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:feba:b3fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3572410 (3.5 MB)  TX bytes:761496 (761.4 KB)
          Interrupt:44 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59145 (59.1 KB)  TX bytes:59145 (59.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:48:2a:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f8400000-f8400100 "

iwconfig...

"lo        no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions."

```

dmesg...

"[    0.834460] TCP reno registered
[    0.834466] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.834479] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.834610] NET: Registered protocol family 1
[    0.834645] pci 0000:00:02.0: Boot video device
[    0.834666] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.834690] pci 0000:00:1a.0: PCI INT A disabled
[    0.834714] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.834736] pci 0000:00:1a.1: PCI INT B disabled
[    0.834747] pci 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.834769] pci 0000:00:1a.2: PCI INT C disabled
[    0.834782] pci 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.834825] pci 0000:00:1a.7: PCI INT C disabled
[    0.834853] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.834875] pci 0000:00:1d.0: PCI INT A disabled
[    0.834886] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.834908] pci 0000:00:1d.1: PCI INT B disabled
[    0.834923] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.834946] pci 0000:00:1d.2: PCI INT C disabled
[    0.834958] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.834981] pci 0000:00:1d.7: PCI INT A disabled
[    0.835008] PCI: CLS 64 bytes, default 64
[    0.835017] Simple Boot Flag at 0x36 set to 0x1
[    0.835594] audit: initializing netlink socket (disabled)
[    0.835609] type=2000 audit(1347640965.828:1): initialized
[    0.863868] highmem bounce pool size: 64 pages
[    0.863875] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.866719] VFS: Disk quotas dquot_6.5.2
[    0.866808] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.867622] fuse init (API version 7.17)
[    0.867770] msgmni has been set to 1706
[    0.868327] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.868367] io scheduler noop registered
[    0.868370] io scheduler deadline registered
[    0.868383] io scheduler cfq registered (default)
[    0.868573] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.868646] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.868749] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.868815] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.868913] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.868978] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.869115] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.869150] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.869282] intel_idle: MWAIT substates: 0x1110
[    0.869285] intel_idle: does not run on family 6 model 15
[    0.888030] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.908039] ACPI: AC Adapter [AC0] (on-line)
[    0.908149] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.908156] ACPI: Power Button [PWRB]
[    0.908223] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.908244] ACPI: Lid Switch [LID]
[    0.908305] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.908310] ACPI: Sleep Button [SLPB]
[    0.908370] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.908375] ACPI: Power Button [PWRF]
[    0.909075] Monitor-Mwait will be used to enter C-1 state
[    0.909122] Monitor-Mwait will be used to enter C-2 state
[    0.909132] Marking TSC unstable due to TSC halts in idle
[    0.909143] ACPI: acpi_idle registered with cpuidle
[    0.913274] thermal LNXTHERM:00: registered as thermal_zone0
[    0.913278] ACPI: Thermal Zone [TZ00] (56 C)
[    0.913431] ACPI: Invalid active0 threshold
[    0.913540] thermal LNXTHERM:01: registered as thermal_zone1
[    0.913543] ACPI: Thermal Zone [TZ01] (0 C)
[    0.913583] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.913595] ACPI: Battery Slot [BAT0] (battery present)
[    0.913637] ERST: Table is not found!
[    0.913639] GHES: HEST is not enabled!
[    0.913701] isapnp: Scanning for PnP cards...
[    0.921070] ACPI: Battery Slot [BAT0] (battery present)
[    0.960114] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.268083] isapnp: No Plug & Play device found
[    1.328514] Linux agpgart interface v0.103
[    1.328684] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    1.328870] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.329809] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.329981] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.332266] brd: module loaded
[    1.333450] loop: module loaded
[    1.333618] ahci 0000:00:1f.2: version 3.0
[    1.333637] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.333709] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.333803] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x13 impl SATA mode
[    1.333808] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ccc sxs 
[    1.333816] ahci 0000:00:1f.2: setting latency timer to 64
[    1.334731] scsi0 : ahci
[    1.334878] scsi1 : ahci
[    1.334997] scsi2 : ahci
[    1.335114] scsi3 : ahci
[    1.335234] scsi4 : ahci
[    1.335318] ata1: SATA max UDMA/133 abar m2048@0xfe704000 port 0xfe704100 irq 43
[    1.335323] ata2: SATA max UDMA/133 abar m2048@0xfe704000 port 0xfe704180 irq 43
[    1.335327] ata3: DUMMY
[    1.335329] ata4: DUMMY
[    1.335333] ata5: SATA max UDMA/133 abar m2048@0xfe704000 port 0xfe704300 irq 43
[    1.335969] Fixed MDIO Bus: probed
[    1.336023] tun: Universal TUN/TAP device driver, 1.6
[    1.336026] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.336125] PPP generic driver version 2.4.2
[    1.336296] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.336325] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.336353] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.336358] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.336425] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.336466] ehci_hcd 0000:00:1a.7: debug port 1
[    1.340352] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.340377] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfe704800
[    1.356023] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.356230] hub 1-0:1.0: USB hub found
[    1.356237] hub 1-0:1.0: 6 ports detected
[    1.356352] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.356373] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.356378] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.356445] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.356477] ehci_hcd 0000:00:1d.7: debug port 1
[    1.360371] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.360393] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe704c00
[    1.376022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.376195] hub 2-0:1.0: USB hub found
[    1.376200] hub 2-0:1.0: 6 ports detected
[    1.376313] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.376335] uhci_hcd: USB Universal Host Controller Interface driver
[    1.376363] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.376374] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.376380] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.376446] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.376491] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    1.376687] hub 3-0:1.0: USB hub found
[    1.376693] hub 3-0:1.0: 2 ports detected
[    1.376792] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.376802] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.376807] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.376875] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.376919] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    1.377111] hub 4-0:1.0: USB hub found
[    1.377116] hub 4-0:1.0: 2 ports detected
[    1.377226] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.377236] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.377241] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.377312] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.377344] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    1.377534] hub 5-0:1.0: USB hub found
[    1.377539] hub 5-0:1.0: 2 ports detected
[    1.377635] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.377646] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.377650] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.377716] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.377747] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    1.377928] hub 6-0:1.0: USB hub found
[    1.377934] hub 6-0:1.0: 2 ports detected
[    1.378031] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.378041] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.378046] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.378109] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.378140] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    1.378323] hub 7-0:1.0: USB hub found
[    1.378329] hub 7-0:1.0: 2 ports detected
[    1.378425] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.378435] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.378439] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.378504] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.378550] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    1.378735] hub 8-0:1.0: USB hub found
[    1.378740] hub 8-0:1.0: 2 ports detected
[    1.378917] usbcore: registered new interface driver libusual
[    1.378985] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.382736] i8042: Detected active multiplexing controller, rev 1.1
[    1.383732] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.383741] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.383789] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.383827] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.383866] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.384081] mousedev: PS/2 mouse device common for all mice
[    1.384571] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.384607] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.384713] device-mapper: uevent: version 1.0.3
[    1.384831] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.384881] EISA: Probing bus 0 at eisa.0
[    1.384884] EISA: Cannot allocate resource for mainboard
[    1.384887] Cannot allocate resource for EISA slot 1
[    1.384890] Cannot allocate resource for EISA slot 2
[    1.384893] Cannot allocate resource for EISA slot 3
[    1.384895] Cannot allocate resource for EISA slot 4
[    1.384898] Cannot allocate resource for EISA slot 5
[    1.384900] Cannot allocate resource for EISA slot 6
[    1.384903] Cannot allocate resource for EISA slot 7
[    1.384906] Cannot allocate resource for EISA slot 8
[    1.384908] EISA: Detected 0 cards.
[    1.384921] cpufreq-nforce2: No nForce2 chipset.
[    1.384995] cpuidle: using governor ladder
[    1.385107] cpuidle: using governor menu
[    1.385110] EFI Variables Facility v0.08 2004-May-17
[    1.385496] TCP cubic registered
[    1.385671] NET: Registered protocol family 10
[    1.386543] NET: Registered protocol family 17
[    1.386549] Registering the dns_resolver key type
[    1.386580] Using IPI No-Shortcut mode
[    1.386786] PM: Hibernation image not present or could not be loaded.
[    1.386801] registered taskstats version 1
[    1.396929]   Magic number: 12:451:742
[    1.396948] ata_device dev5.0: hash matches
[    1.396951]  dev5.0: hash matches
[    1.397055] rtc_cmos 00:06: setting system clock to 2012-09-14 16:42:47 UTC (1347640967)
[    1.397091] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.397094] EDD information not available.
[    1.419414] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.656089] ata5: SATA link down (SStatus 0 SControl 300)
[    1.668064] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    1.818267] Initializing USB Mass Storage driver...
[    1.818351] usbcore: registered new interface driver usb-storage
[    1.818354] USB Mass Storage support registered.
[    1.824094] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.828066] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.837920] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, TM00, max UDMA/100
[    1.837924] ata2.00: applying bridge limits
[    1.851546] ata2.00: configured for UDMA/100
[    1.872776] ata1.00: ATA-8: TOSHIBA MK1652GSX, LV010J, max UDMA/100
[    1.872781] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.873702] ata1.00: configured for UDMA/100
[    1.873911] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1652GS LV01 PQ: 0 ANSI: 5
[    1.874113] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.874146] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.874183] sd 0:0:0:0: [sda] Write Protect is off
[    1.874188] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.874218] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.876477] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  TM00 PQ: 0 ANSI: 5
[    1.881670] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.881674] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.881873] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.881991] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.944597]  sda: sda1 sda2 < sda5 >
[    1.945288] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.945329] Freeing unused kernel memory: 712k freed
[    1.945735] Write protecting the kernel text: 5620k
[    1.945816] Write protecting the kernel read-only data: 2324k
[    1.971325] udevd[101]: starting version 175
[    2.103099] usbcore: registered new interface driver uas
[    2.110853] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.110882] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.110921] r8169 0000:05:00.0: setting latency timer to 64
[    2.111005] r8169 0000:05:00.0: irq 44 for MSI/MSI-X
[    2.111956] scsi5 : usb-storage 1-4:1.0
[    2.112266] usbcore: registered new interface driver ums-realtek
[    2.113938] r8169 0000:05:00.0: eth0: RTL8102e at 0xf8028000, 00:03:0d:ba:b3:fb, XID 14a00000 IRQ 44
[    2.457196] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.114355] scsi 5:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    3.115357] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    3.119084] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   18.382225] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.414715] udevd[335]: starting version 175
[   18.470326] lp: driver loaded but no devices found
[   18.507920] Adding 2055164k swap on /dev/sda5.  Priority:-1 extents:1 across:2055164k 
[   18.546831] [drm] Initialized drm 1.1.0 20060810
[   18.562046] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.562054] i915 0000:00:02.0: setting latency timer to 64
[   18.637292] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   18.637302] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.637304] [drm] Driver supports precise vblank timestamp query.
[   18.637356] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   18.702866] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.708682] fixme: max PWM is zero.
[   18.789584] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   18.791181] ieee80211_crypt: registered algorithm 'NULL'
[   18.791186] ieee80211_crypt: registered algorithm 'TKIP'
[   18.791189] ieee80211_crypt: registered algorithm 'CCMP'
[   18.791192] ieee80211_crypt: registered algorithm 'WEP'
[   18.791195] 
[   18.791196] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[   18.791198] Copyright (c) 2004-2005, Andrea Merello
[   18.791200] r8180: Initializing module
[   18.791203] r8180: Wireless extensions version 22
[   18.791205] r8180: Initializing proc filesystem
[   18.791247] r8180: Configuring chip resources
[   18.791271] r8180 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.791280] r8180 0000:04:00.0: setting latency timer to 64
[   18.795279] r8180: Channel plan is 2
[   18.795281] 
[   18.795285] Dot11d_Init()
[   18.795290] r8180: MAC controller is a RTL8187SE b/g
[   18.797555] r8180: usValue is 0xf00
[   18.797557] 
[   18.798930] type=1400 audit(1347637384.896:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=517 comm="apparmor_parser"
[   18.799544] type=1400 audit(1347637384.896:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=517 comm="apparmor_parser"
[   18.799879] type=1400 audit(1347637384.896:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=517 comm="apparmor_parser"
[   18.840993] r8180: EEPROM version 104
[   18.845338] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   18.851249] r8180: IRQ 17
[   18.859483] r8180: Driver probe completed
[   18.859485] 
[   19.038201] Bluetooth: Core ver 2.16
[   19.038305] NET: Registered protocol family 31
[   19.038308] Bluetooth: HCI device and connection manager initialized
[   19.038313] Bluetooth: HCI socket layer initialized
[   19.038316] Bluetooth: L2CAP socket layer initialized
[   19.038324] Bluetooth: SCO socket layer initialized
[   19.061469] ppdev: user-space parallel port driver
[   19.064205] Bluetooth: RFCOMM TTY layer initialized
[   19.064213] Bluetooth: RFCOMM socket layer initialized
[   19.064216] Bluetooth: RFCOMM ver 1.11
[   19.071423] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.071427] Bluetooth: BNEP filters: protocol multicast
[   19.126703] type=1400 audit(1347637385.224:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=658 comm="apparmor_parser"
[   19.127411] type=1400 audit(1347637385.224:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=658 comm="apparmor_parser"
[   19.292058] init: failsafe main process (673) killed by TERM signal
[   19.419269] type=1400 audit(1347637385.516:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=770 comm="apparmor_parser"
[   19.419722] type=1400 audit(1347637385.516:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=769 comm="apparmor_parser"
[   19.440378] type=1400 audit(1347637385.540:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=771 comm="apparmor_parser"
[   19.441140] type=1400 audit(1347637385.540:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=771 comm="apparmor_parser"
[   19.441480] type=1400 audit(1347637385.540:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=771 comm="apparmor_parser"
[   19.466971] r8180: Bringing up iface
[   19.665491] r8180: Card successfully reset
[   20.037963] init: alsa-restore main process (856) terminated with status 19
[   20.270784] fbcon: inteldrmfb (fb0) is primary device
[   20.271910] Console: switching to colour frame buffer device 160x50
[   20.271955] fb0: inteldrmfb frame buffer device
[   20.271957] drm: registered panic notifier
[   20.405296] r8180: WIRELESS_MODE_G
[   20.405298] 
[   20.419632] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.419971] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.425759] r8169 0000:05:00.0: eth0: link down
[   20.425767] r8169 0000:05:00.0: eth0: link down
[   20.431734] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.435485] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.628075] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000/0x0
[   20.665661] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   20.948455] acpi device:07: registered as cooling_device2
[   20.949688] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
[   20.949886] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   20.950355] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.950426] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.950517] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   20.950559] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   20.979410] init: plymouth-splash main process (1089) terminated with status 1
[   21.005826] HDMI status: Codec=1 Pin=3 Presence_Detect=0 ELD_Valid=0
[   21.007043] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   21.009347] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   21.009692] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   21.010283] init: gdm main process (1094) killed by TERM signal
[   22.204319] r8169 0000:05:00.0: eth0: link up
[   22.204532] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.496028] eth0: no IPv6 routers present
[   53.284873] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   53.287047] sd 5:0:0:0: [sdb] Asking for cache data failed
[   53.287052] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  104.980625] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  104.982740] sd 5:0:0:0: [sdb] Asking for cache data failed
[  104.982745] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  156.692727] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  156.694843] sd 5:0:0:0: [sdb] Asking for cache data failed
[  156.694848] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  208.404715] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  208.406848] sd 5:0:0:0: [sdb] Asking for cache data failed
[  208.406854] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  260.116679] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  260.118925] sd 5:0:0:0: [sdb] Asking for cache data failed
[  260.118930] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  311.828661] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  311.830795] sd 5:0:0:0: [sdb] Asking for cache data failed
[  311.830803] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  363.541164] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  363.543278] sd 5:0:0:0: [sdb] Asking for cache data failed
[  363.543283] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  415.252739] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  415.254859] sd 5:0:0:0: [sdb] Asking for cache data failed
[  415.254863] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  466.964595] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  466.966838] sd 5:0:0:0: [sdb] Asking for cache data failed
[  466.966843] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  518.676753] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  518.678871] sd 5:0:0:0: [sdb] Asking for cache data failed
[  518.678876] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  570.388638] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  570.390758] sd 5:0:0:0: [sdb] Asking for cache data failed
[  570.390762] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  622.100650] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  622.102893] sd 5:0:0:0: [sdb] Asking for cache data failed
[  622.102897] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  673.812659] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  673.814777] sd 5:0:0:0: [sdb] Asking for cache data failed
[  673.814783] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  725.528835] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  725.531077] sd 5:0:0:0: [sdb] Asking for cache data failed
[  725.531087] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  777.236681] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  777.238796] sd 5:0:0:0: [sdb] Asking for cache data failed
[  777.238801] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  824.949975] cfg80211: Calling CRDA to update world regulatory domain
[  825.014556] cfg80211: World regulatory domain updated:
[  825.014563] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  825.014567] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  825.014571] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  825.014575] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  825.014579] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  825.014583] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  825.097576] iwlwifi: Unknown parameter `lln_disable'
[  828.948694] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  828.950809] sd 5:0:0:0: [sdb] Asking for cache data failed
[  828.950813] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  880.660965] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  880.663078] sd 5:0:0:0: [sdb] Asking for cache data failed
[  880.663086] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  932.372587] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  932.374705] sd 5:0:0:0: [sdb] Asking for cache data failed
[  932.374710] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  984.084716] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  984.086837] sd 5:0:0:0: [sdb] Asking for cache data failed
[  984.086841] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1016.922270] atkbd serio0: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[ 1016.922276] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
[ 1016.932265] atkbd serio0: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[ 1016.932271] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
[ 1018.328635] atkbd serio0: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[ 1018.328641] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
[ 1018.338659] atkbd serio0: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[ 1018.338666] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
[ 1035.796732] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1035.798849] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1035.798854] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1087.508616] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1087.510734] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1087.510738] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1139.220879] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1139.223000] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1139.223005] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1190.932636] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1190.934753] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1190.934758] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1242.644794] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1242.647346] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1242.647353] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1294.356792] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1294.358924] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1294.358931] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1346.068917] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1346.071056] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1346.071062] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1397.781224] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1397.783427] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1397.783432] sd 5:0:0:0: [sdb] Assuming drive cache: write through"

```
Hope someone can assist!

Thanks.

UPDATE: 

Ran a full system check, turned wireless off then back on again, and it is working. Not a fix, as such, but at least some sort of solution for now.

---

### Post by T Bone on 2012-09-30
Further update: it has died again! No problems at all on other devices connecting to the same router. Has anyone else had this problem or found a fix?!

---

### Post by chili555 on 2012-09-30
>  iwlwifi: Unknown parameter `lln_disable':confused:

If you have a .conf file for iwlwifi, I'd remove it. I'm confident it's doing no good.

---

### Post by T Bone on 2012-09-30
Hi Chilli,

Thanks for replying (your fix to my previous problem is still going strong by the way!). How would I go about removing this?

---

### Post by T Bone on 2012-10-04
I've been looking all over the forum to try to find a solution to this problem and ran: 

dmesg | grep -e wlan -e eth1 -e wl

as you'd suggested to someone else. I got 


"[   23.678403] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.679136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1743.080456] wl: module license 'MIXED/Proprietary' taints kernel."

This, I think, means that I have mixed up my drivers, or the commands about what drivers the device should use. Is this the case, and can I fix it?

Thanks.

---

### Post by chili555 on 2012-10-05
> This, I think, means that I have mixed up my drivers, or the commands about what drivers the device should use. Is this the case, and can I fix it?Perhaps. The STA driver *wl* usually creates a wireless interface eth1. I wonder why you have wlan0, although it might be OK. Please post:```
sudo lshw -C network
nm-tool
```Thanks.

---

### Post by T Bone on 2012-10-05
Hi, and thanks (again),

sudo lshw -C newtork gives 

  *-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 22
       serial: 00:22:5f:48:2a:7c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:17 ioport:3000(size=256) memory:fa000000-fa003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:03:0d:ba:b3:fb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:f6000000-f6000fff memory:f4000000-f400ffff memory:f4010000-f401ffff


nm-tool gives:

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:03:0D:BA:B3:FB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8180
  State:             disconnected
  Default:           no
  HW Address:        00:22:5F:48:2A:7C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by chili555 on 2012-10-05
> [ 1743.080456] [COLOR="Red"]wl[/COLOR]: module license 'MIXED/Proprietary' taints kernel."My, oh my! You have tried a lot of competing fixes, haven't you? Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot, disconnect the ethernet and let's look again:```
dmesg | grep -e wlan -e r818
```

---

### Post by T Bone on 2012-10-05
> **chili555 said:**
> My, oh my! You have tried a lot of competing fixes, haven't you?

I have indeed, a little knowledge is a dangerous thing: in my case almost no knowledge, in some sort of evil synergy with bloody-mindedness and a mistaken faith in blind luck appears to have lead me to an impasse where only expert help will suffice! (I'm a muppet and I really appreciate your help.)

dmesg | grep -e wlan -e r818 gives

[   19.748700] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   19.750290] r8180: Initializing module
[   19.750292] r8180: Wireless extensions version 22
[   19.750294] r8180: Initializing proc filesystem
[   19.750335] r8180: Configuring chip resources
[   19.750356] r8180 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.750367] r8180 0000:04:00.0: setting latency timer to 64
[   19.786318] r8180: Channel plan is 2
[   19.786330] r8180: MAC controller is a RTL8187SE b/g
[   19.788524] r8180: usValue is 0xf00
[   19.832112] r8180: EEPROM version 104
[   19.836457] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   19.864401] r8180: IRQ 17
[   19.866443] r8180: Driver probe completed
[   20.718477] r8180: Bringing up iface
[   20.916983] r8180: Card successfully reset
[   21.657341] r8180: WIRELESS_MODE_G
[   21.675216] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.682564] ADDRCONF(NETDEV_UP): wlan0: link is not ready"

If any other background information helps, startup with the ethernet out gave no network options, just the little sort of "blank" network symbol, even clicking on this didn't offer any connection options, even the option to connect to hidden networks. 

Strangely, once the ethernet was in, these options appeared. If I then select "connect to a hidden wireless network" I can find my network (which isn't actually hidden) and attempt to connect. After a minute it asks for the password, but doesn't connect and then asks for the password again.

---

### Post by T Bone on 2012-10-05
Even more strange, the wifi has just spontaneously reconnected! I was awaiting further instruction whilst reading a book (a real, physical book, the computer was left completely alone) and I noticed the notification. 

Perhaps in the interests of posterity I should post some details  for comparison purposes?

[EDIT] I say spontaneously, but I do not wish to deny credit where it is due- it is almost certainly down to your advice, but on an unexpected 30 minute delay!

---

### Post by T Bone on 2012-10-05
I think I should note the output of some commands, just in case this happens again. It reminds me of Robert M Pirsig's thoughts on the evils of recurrent problems (although in a different form):

lspci:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:03:0d:ba:b3:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9752167 (9.7 MB)  TX bytes:1757820 (1.7 MB)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186233 (186.2 KB)  TX bytes:186233 (186.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:48:2a:7c  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fe48:2a7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6228 errors:16 dropped:6551 overruns:0 frame:0
          TX packets:6685 errors:18 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4229680 (4.2 MB)  TX bytes:1515308 (1.5 MB)
          Interrupt:17 Memory:f83a8000-f83a8100 


dmesg:


[   19.750292] r8180: Wireless extensions version 22
[   19.750294] r8180: Initializing proc filesystem
[   19.750335] r8180: Configuring chip resources
[   19.750356] r8180 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.750367] r8180 0000:04:00.0: setting latency timer to 64
[   19.771085] type=1400 audit(1349465906.878:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=451 comm="apparmor_parser"
[   19.771697] type=1400 audit(1349465906.878:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=451 comm="apparmor_parser"
[   19.772144] type=1400 audit(1349465906.882:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=451 comm="apparmor_parser"
[   19.778636] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.783713] [drm] Initialized drm 1.1.0 20060810
[   19.786318] r8180: Channel plan is 2
[   19.786321] 
[   19.786325] Dot11d_Init()
[   19.786330] r8180: MAC controller is a RTL8187SE b/g
[   19.788524] r8180: usValue is 0xf00
[   19.788525] 
[   19.832112] r8180: EEPROM version 104
[   19.836457] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   19.864401] r8180: IRQ 17
[   19.866443] r8180: Driver probe completed
[   19.866446] 
[   19.940797] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.940806] i915 0000:00:02.0: setting latency timer to 64
[   20.008342] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   20.008351] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   20.008354] [drm] Driver supports precise vblank timestamp query.
[   20.008410] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   20.130935] fixme: max PWM is zero.
[   20.179948] ppdev: user-space parallel port driver
[   20.193174] Bluetooth: Core ver 2.16
[   20.193298] NET: Registered protocol family 31
[   20.193302] Bluetooth: HCI device and connection manager initialized
[   20.193307] Bluetooth: HCI socket layer initialized
[   20.193310] Bluetooth: L2CAP socket layer initialized
[   20.193319] Bluetooth: SCO socket layer initialized
[   20.206278] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.206283] Bluetooth: BNEP filters: protocol multicast
[   20.222319] Bluetooth: RFCOMM TTY layer initialized
[   20.222327] Bluetooth: RFCOMM socket layer initialized
[   20.222330] Bluetooth: RFCOMM ver 1.11
[   20.293139] type=1400 audit(1349465907.402:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=669 comm="apparmor_parser"
[   20.293895] type=1400 audit(1349465907.402:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=669 comm="apparmor_parser"
[   20.557810] init: failsafe main process (723) killed by TERM signal
[   20.712609] type=1400 audit(1349465907.822:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=811 comm="apparmor_parser"
[   20.715087] type=1400 audit(1349465907.822:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=810 comm="apparmor_parser"
[   20.718477] r8180: Bringing up iface
[   20.723660] type=1400 audit(1349465907.830:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=812 comm="apparmor_parser"
[   20.729100] type=1400 audit(1349465907.838:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=812 comm="apparmor_parser"
[   20.729437] type=1400 audit(1349465907.838:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=812 comm="apparmor_parser"
[   20.821530] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000/0x0
[   20.858581] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   20.916983] r8180: Card successfully reset
[   20.982598] fbcon: inteldrmfb (fb0) is primary device
[   20.983689] Console: switching to colour frame buffer device 160x50
[   20.983730] fb0: inteldrmfb frame buffer device
[   20.983733] drm: registered panic notifier
[   21.657341] r8180: WIRELESS_MODE_G
[   21.657344] 
[   21.675216] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.682564] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.710808] r8169 0000:05:00.0: eth0: link down
[   21.714445] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.714982] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.737570] init: alsa-restore main process (875) terminated with status 19
[   22.208371] acpi device:07: registered as cooling_device2
[   22.208578] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
[   22.208660] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.208741] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.209116] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   22.209197] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   22.209237] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   22.274827] HDMI status: Codec=1 Pin=3 Presence_Detect=0 ELD_Valid=0
[   22.276764] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   22.277154] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   22.277505] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   22.285758] init: gdm main process (1094) killed by TERM signal
[   48.227140] r8169 0000:05:00.0: eth0: link up
[   48.227351] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   53.284783] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   53.288233] sd 5:0:0:0: [sdb] Asking for cache data failed
[   53.288241] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   58.544034] eth0: no IPv6 routers present
[  104.980595] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  104.982844] sd 5:0:0:0: [sdb] Asking for cache data failed
[  104.982849] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  156.692755] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  156.695010] sd 5:0:0:0: [sdb] Asking for cache data failed
[  156.695016] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  208.404637] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  208.406751] sd 5:0:0:0: [sdb] Asking for cache data failed
[  208.406756] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  260.116652] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  260.118792] sd 5:0:0:0: [sdb] Asking for cache data failed
[  260.118798] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  311.828671] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  311.830785] sd 5:0:0:0: [sdb] Asking for cache data failed
[  311.830791] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  363.540686] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  363.542800] sd 5:0:0:0: [sdb] Asking for cache data failed
[  363.542805] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  415.252698] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  415.254813] sd 5:0:0:0: [sdb] Asking for cache data failed
[  415.254818] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  466.964719] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  466.966834] sd 5:0:0:0: [sdb] Asking for cache data failed
[  466.966839] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  518.676734] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  518.678848] sd 5:0:0:0: [sdb] Asking for cache data failed
[  518.678853] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  570.388752] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  570.390867] sd 5:0:0:0: [sdb] Asking for cache data failed
[  570.390872] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  591.538526] r8169 0000:05:00.0: eth0: link down
[  596.273484] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  622.101323] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  622.103404] sd 5:0:0:0: [sdb] Asking for cache data failed
[  622.103413] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  673.812659] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  673.814900] sd 5:0:0:0: [sdb] Asking for cache data failed
[  673.814906] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  701.427539] r8169 0000:05:00.0: eth0: link up
[  701.427757] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  712.016032] eth0: no IPv6 routers present
[  725.524675] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  725.526917] sd 5:0:0:0: [sdb] Asking for cache data failed
[  725.526921] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  777.236567] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  777.238682] sd 5:0:0:0: [sdb] Asking for cache data failed
[  777.238687] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  828.948583] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  828.950701] sd 5:0:0:0: [sdb] Asking for cache data failed
[  828.950706] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  880.660598] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  880.662705] sd 5:0:0:0: [sdb] Asking for cache data failed
[  880.662710] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  932.372616] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  932.374732] sd 5:0:0:0: [sdb] Asking for cache data failed
[  932.374737] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  984.084805] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  984.086926] sd 5:0:0:0: [sdb] Asking for cache data failed
[  984.086930] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1035.796699] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1035.798814] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1035.798819] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1087.508585] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1087.510697] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1087.510702] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1139.220714] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1139.222832] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1139.222837] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1190.932724] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1190.934844] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1190.934849] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1242.644609] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1242.646730] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1242.646734] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1294.356746] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1294.358865] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1294.358870] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1346.068756] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1346.070875] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1346.070880] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1397.780642] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1397.782761] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1397.782765] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1449.492777] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1449.494896] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1449.494901] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1501.204786] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1501.206907] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1501.206911] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1552.916679] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1552.918790] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1552.918795] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1604.628680] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1604.630799] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1604.630804] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1656.340697] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1656.342811] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1656.342816] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1708.052578] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1708.054695] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1708.054700] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1759.764712] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1759.766830] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1759.766837] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1811.476599] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1811.478716] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1811.478721] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1863.188607] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1863.190733] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1863.190738] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1914.900751] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1914.902862] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1914.902867] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1966.612751] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1966.614868] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 1966.614873] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2018.324763] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2018.326882] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2018.326886] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2070.036772] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2070.038893] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2070.038898] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2121.748784] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2121.750903] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2121.750907] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2173.460670] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2173.462786] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2173.462791] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2225.172679] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2225.174798] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2225.174803] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2236.725380] atkbd serio0: Unknown key pressed (translated set 2, code 0xb4 on isa0060/serio0).
[ 2236.725386] atkbd serio0: Use 'setkeycodes e034 <keycode>' to make it known.
[ 2236.735381] atkbd serio0: Unknown key released (translated set 2, code 0xb4 on isa0060/serio0).
[ 2236.735387] atkbd serio0: Use 'setkeycodes e034 <keycode>' to make it known.
[ 2275.375205] Linking with BTHomeHub2-86M8: channel is 7
[ 2275.415645] Linking with BTHomeHub2-86M8: channel is 7
[ 2275.434373] Associated successfully
[ 2275.434378] Using G rates
[ 2275.448438] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2276.884816] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2276.886933] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2276.886938] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2286.448028] wlan0: no IPv6 routers present
[ 2328.596606] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2328.598721] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2328.598726] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2380.308627] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2380.310748] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2380.310753] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2432.022428] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2432.024621] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2432.024627] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2483.732758] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2483.734876] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2483.734881] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2535.444645] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2535.446762] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2535.446767] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2587.156659] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2587.158897] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2587.158902] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2638.868664] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2638.870782] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2638.870786] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2690.580677] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2690.582792] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2690.582797] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2742.292564] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2742.294804] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2742.294809] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2794.004695] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2794.006813] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2794.006818] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2845.716577] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2845.718695] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2845.718700] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2858.124438] r8169 0000:05:00.0: eth0: link down
[ 2862.255663] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2878.679427] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 00000000016e received PN 00000000016d
[ 2878.782942] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000001a5 received PN 0000000001a4
[ 2878.783103] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000001a8 received PN 0000000001a6
[ 2878.783317] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000001a9 received PN 0000000001a7
[ 2878.894657] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000001e8 received PN 0000000001e7
[ 2878.895628] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000001ed received PN 0000000001ec
[ 2879.013565] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 00000000021a received PN 000000000219
[ 2883.023078] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000275 received PN 000000000274
[ 2883.284251] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000291 received PN 00000000028f
[ 2897.428591] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2897.430836] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2897.430842] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2898.757124] net_ratelimit: 1 callbacks suppressed
[ 2898.757130] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 00000000032a received PN 000000000329
[ 2926.189292] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000430 received PN 00000000042f
[ 2926.313927] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 00000000046f received PN 00000000046d
[ 2936.144103] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000004cb received PN 0000000004ca
[ 2937.793818] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000509 received PN 000000000506
[ 2938.157797] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000542 received PN 000000000541
[ 2938.544226] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000570 received PN 00000000056f
[ 2938.627945] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 00000000057c received PN 00000000057a
[ 2938.628068] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 00000000057c received PN 00000000057b
[ 2938.839185] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000592 received PN 000000000591
[ 2939.613702] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000005ab received PN 0000000005a8
[ 2939.614008] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000005ab received PN 0000000005a9
[ 2939.614164] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000005ab received PN 0000000005aa
[ 2947.439661] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000685 received PN 000000000683
[ 2947.439748] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000685 received PN 000000000684
[ 2949.140726] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2949.142845] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 2949.142850] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2962.719424] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 00000000072f received PN 000000000718
[ 2962.723112] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000731 received PN 00000000071c
[ 2962.723259] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000731 received PN 00000000071e
[ 2962.723613] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000731 received PN 000000000720
[ 2962.724244] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000731 received PN 000000000722
[ 2962.725378] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000731 received PN 00000000072a
[ 2963.745399] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000767 received PN 000000000765
[ 2963.747860] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000767 received PN 000000000766
[ 2965.059311] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000786 received PN 000000000784
[ 2965.060102] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000786 received PN 000000000785
[ 2972.318183] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000007d3 received PN 0000000007d2
[ 2981.545522] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000806 received PN 000000000805
[ 2990.566775] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000830 received PN 00000000082f
[ 3000.852736] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3000.854853] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3000.854857] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3002.145424] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000008db received PN 0000000008da
[ 3032.574034] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000a02 received PN 000000000a01
[ 3032.735942] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000a14 received PN 000000000a13
[ 3032.736719] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000a19 received PN 000000000a17
[ 3032.736812] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000a19 received PN 000000000a18
[ 3033.062785] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000a6a received PN 000000000a69
[ 3033.452998] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000ab7 received PN 000000000ab5
[ 3033.453096] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000ab7 received PN 000000000ab6
[ 3033.454914] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000abe received PN 000000000aba
[ 3033.455213] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000abe received PN 000000000abb
[ 3033.455300] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000abe received PN 000000000abc
[ 3040.724936] net_ratelimit: 7 callbacks suppressed
[ 3040.724942] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000be1 received PN 000000000bdf
[ 3040.725027] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000be1 received PN 000000000be0
[ 3051.039708] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000c32 received PN 000000000c2f
[ 3051.039756] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000c32 received PN 000000000c31
[ 3051.311371] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000c43 received PN 000000000c42
[ 3052.564622] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3052.566741] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3052.566746] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3060.794570] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000c73 received PN 000000000c70
[ 3060.794666] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000c73 received PN 000000000c71
[ 3093.495863] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000d1a received PN 000000000d19
[ 3095.244873] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000d37 received PN 000000000d36
[ 3095.910947] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000d53 received PN 000000000d52
[ 3096.481564] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000d90 received PN 000000000d8f
[ 3096.517733] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000da5 received PN 000000000da4
[ 3096.536956] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000dae received PN 000000000dad
[ 3104.280927] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3104.283035] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3104.283041] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3104.286274] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000e2c received PN 000000000e2b
[ 3104.941773] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000e76 received PN 000000000e75
[ 3113.433386] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000ed7 received PN 000000000ed6
[ 3114.949926] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000000f7e received PN 000000000f7d
[ 3133.408892] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000010b9 received PN 0000000010b8
[ 3155.988648] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3155.990888] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3155.990895] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3170.825571] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000001169 received PN 000000001167
[ 3170.825675] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000001169 received PN 000000001168
[ 3207.700779] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3207.702895] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3207.702900] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3258.471398] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000011fb received PN 0000000011fa
[ 3259.412667] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3259.414779] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3259.414785] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3311.124677] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3311.126914] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3311.126920] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3362.836813] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3362.838924] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3362.838930] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3411.014821] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000013ea received PN 0000000013e9
[ 3414.548572] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3414.550686] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3414.550691] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3466.260705] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3466.262945] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3466.262950] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3479.273861] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000001443 received PN 000000001441
[ 3479.273976] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000001443 received PN 000000001442
[ 3479.535561] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000014c1 received PN 0000000014c0
[ 3479.930335] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 00000000152e received PN 00000000152d
[ 3517.972592] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3517.974705] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3517.974710] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3569.684603] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3569.686718] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3569.686724] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3621.396612] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3621.398852] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3621.398857] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3673.108614] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3673.110736] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3673.110741] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3724.820627] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3724.822748] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3724.822753] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3741.477146] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 000000001696 received PN 000000001694
[ 3755.497011] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000016df received PN 0000000016da
[ 3755.497099] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000016df received PN 0000000016db
[ 3755.497201] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000016df received PN 0000000016dc
[ 3755.497304] CCMP: replay detected: STA=00:26:44:1a:39:cf previous PN 0000000016df received PN 0000000016de
[ 3776.532641] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3776.534881] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3776.534887] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3828.244778] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3828.246893] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3828.246897] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3879.956665] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3879.958778] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3879.958782] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3931.676977] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3931.679202] sd 5:0:0:0: [sdb] Asking for cache data failed
[ 3931.679210] sd 5:0:0:0: [sdb] Assuming drive cache: write through


Just in case!

---

### Post by chili555 on 2012-10-05
> wlan0 Link encap:Ethernet HWaddr 00:22:5f:48:2a:7c
inet addr:192.168.1.70 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::222:5fff:fe48:2a7c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:6228 errors:16 dropped:6551 overruns:0 frame:0
TX packets:6685 errors:18 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4229680 (4.2 MB) TX bytes:1515308 (1.5 MB)
Interrupt:17 Memory:f83a8000-f83a8100 It is well and truly connected now. Are we happy? Solved?

---

### Post by T Bone on 2012-10-06
> **chili555 said:**
> It is well and truly connected now. Are we happy? Solved?

Very happy. Confused as to the intermittent nature of it all, but happy that it works again! Will mark it solved forthwith.

Many thanks again Chili555, you are a gem.

---

