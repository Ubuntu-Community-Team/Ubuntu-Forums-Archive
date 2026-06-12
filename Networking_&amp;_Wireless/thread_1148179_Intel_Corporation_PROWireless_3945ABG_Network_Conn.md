---
title: "Intel Corporation PRO/Wireless 3945ABG Network Connection"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by Faheed on 2009-05-04
**Machine Brand and Model (PC/Laptop)**:compaq presario v6700
**Wireless Brand, Model and Wireless Chipset:** Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)[B]


interface::::[/B]ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:66:f7:4d  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe66:f74d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:464486 (453.5 KB)  TX bytes:80453 (78.5 KB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120100 (117.2 KB)  TX bytes:120100 (117.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:5c:25:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-5C-25-3D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[B]
Modules::::[/B] lsmod

cfg80211               15112  1 iwlwifi_mac80211
[B]
kernel boot messages::::
[/B][   13.427616] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   13.427716] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   13.427818] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   13.427918] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   13.428017] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   13.428117] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   13.428255] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.428280] pnp: PnP ACPI init
[   13.428287] ACPI: bus type pnp registered
[   13.432578] pnp: PnP ACPI: found 11 devices
[   13.432581] ACPI: ACPI bus type pnp unregistered
[   13.432583] PnPBIOS: Disabled by ACPI PNP
[   13.432770] PCI: Using ACPI for IRQ routing
[   13.432772] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.541072] NET: Registered protocol family 8
[   13.541074] NET: Registered protocol family 20
[   13.541106] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.541110] hpet0: 3 64-bit timers, 14318180 Hz
[   13.542143] AppArmor: AppArmor Filesystem Enabled
[   13.544925] Time: tsc clocksource has been installed.
[   13.544936] Switched to high resolution mode on CPU 0
[   13.545029] Switched to high resolution mode on CPU 1
[   13.564883] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   13.564886] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   13.564888] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   13.564891] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   13.564893] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   13.564896] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   13.564899] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   13.564901] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   13.564908] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   13.564914] system 00:06: ioport range 0x380-0x383 has been reserved
[   13.564917] system 00:06: ioport range 0x680-0x69f has been reserved
[   13.564919] system 00:06: ioport range 0x800-0x80f has been reserved
[   13.564921] system 00:06: ioport range 0x1000-0x107f has been reserved
[   13.564924] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   13.564926] system 00:06: ioport range 0x1640-0x164f has been reserved
[   13.564928] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[   13.564934] system 00:07: ioport range 0x6a0-0x6af has been reserved
[   13.564936] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[   13.595271] PCI: Bridge: 0000:00:1c.0
[   13.595275]   IO window: 4000-7fff
[   13.595281]   MEM window: f4000000-f5ffffff
[   13.595286]   PREFETCH window: f0000000-f1ffffff
[   13.595292] PCI: Bridge: 0000:00:1c.1
[   13.595295]   IO window: 8000-bfff
[   13.595301]   MEM window: f6000000-f7ffffff
[   13.595305]   PREFETCH window: f2000000-f3ffffff
[   13.595312] PCI: Bridge: 0000:00:1c.5
[   13.595315]   IO window: c000-cfff
[   13.595321]   MEM window: f8200000-f82fffff
[   13.595325]   PREFETCH window: 88000000-880fffff
[   13.595331] PCI: Bridge: 0000:00:1e.0
[   13.595332]   IO window: disabled.
[   13.595338]   MEM window: f8300000-f83fffff
[   13.595342]   PREFETCH window: disabled.
[   13.595375] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   13.595382] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.595407] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   13.595413] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.595438] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 17
[   13.595443] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   13.595458] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.595468] NET: Registered protocol family 2
[   13.632796] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.633008] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.633407] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.633616] TCP: Hash tables configured (established 131072 bind 65536)
[   13.633618] TCP reno registered
[   13.644846] checking if image is initramfs... it is
[   14.523134] Freeing initrd memory: 11178k freed
[   14.523273] Simple Boot Flag at 0x35 set to 0x1
[   14.523834] audit: initializing netlink socket (disabled)
[   14.523847] audit(1241409273.721:1): initialized
[   14.524036] highmem bounce pool size: 64 pages
[   14.525773] VFS: Disk quotas dquot_6.5.1
[   14.525839] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.525953] io scheduler noop registered
[   14.525955] io scheduler anticipatory registered
[   14.525957] io scheduler deadline registered
[   14.525966] io scheduler cfq registered (default)
[   14.525977] Boot video device is 0000:00:02.0
[   14.526204] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.526267] assign_interrupt_mode Found MSI capability
[   14.526320] Allocate Port Service[0000:00:1c.0:pcie00]
[   14.526349] Allocate Port Service[0000:00:1c.0:pcie02]
[   14.526450] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.526512] assign_interrupt_mode Found MSI capability
[   14.526561] Allocate Port Service[0000:00:1c.1:pcie00]
[   14.526590] Allocate Port Service[0000:00:1c.1:pcie02]
[   14.526691] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   14.526754] assign_interrupt_mode Found MSI capability
[   14.526802] Allocate Port Service[0000:00:1c.5:pcie00]
[   14.526830] Allocate Port Service[0000:00:1c.5:pcie02]
[   14.527076] isapnp: Scanning for PnP cards...
[   14.881014] isapnp: No Plug & Play device found
[   14.903157] Real Time Clock Driver v1.12ac
[   14.903372] hpet_resources: 0xfed00000 is busy
[   14.903400] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.904455] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.904511] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   14.904600] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   14.946115] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.946119] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.966666] mice: PS/2 mouse device common for all mice
[   14.966761] EISA: Probing bus 0 at eisa.0
[   14.966768] Cannot allocate resource for EISA slot 1
[   14.966779] Cannot allocate resource for EISA slot 4
[   14.966781] Cannot allocate resource for EISA slot 5
[   14.966782] Cannot allocate resource for EISA slot 6
[   14.966784] Cannot allocate resource for EISA slot 7
[   14.966786] Cannot allocate resource for EISA slot 8
[   14.966787] EISA: Detected 0 cards.
[   14.966790] cpuidle: using governor ladder
[   14.966792] cpuidle: using governor menu
[   14.966867] NET: Registered protocol family 1
[   14.966895] Using IPI No-Shortcut mode
[   14.966921] registered taskstats version 1
[   14.967034]   Magic number: 9:498:916
[   14.967068]   hash matches device ptywf
[   14.967088]   hash matches device ptmx
[   14.967102] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.967104] EDD information not available.
[   14.967291] Freeing unused kernel memory: 368k freed
[   14.995470] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.170503] fuse init (API version 7.9)
[   16.190998] ACPI: SSDT 7F6D69F9, 01F6 (r1  HP    30CC         3000 INTL 20061109)
[   16.191222] ACPI: SSDT 7F6D639C, 05D8 (r1  HP    30CC         3001 INTL 20061109)
[   16.192993] Monitor-Mwait will be used to enter C-1 state
[   16.192996] Monitor-Mwait will be used to enter C-2 state
[   16.192998] Monitor-Mwait will be used to enter C-3 state
[   16.193103] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.193108] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.193332] ACPI: SSDT 7F6D6BEF, 00C8 (r1  HP    30CC         3000 INTL 20061109)
[   16.193539] ACPI: SSDT 7F6D6974, 0085 (r1  HP    30CC         3000 INTL 20061109)
[   16.194498] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   16.194503] ACPI: Processor [CPU1] (supports 8 throttling states)
[   16.196278] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
[   16.446204] usbcore: registered new interface driver usbfs
[   16.446226] usbcore: registered new interface driver hub
[   16.446249] usbcore: registered new device driver usb
[   16.447286] USB Universal Host Controller Interface driver v3.0
[   16.447329] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
[   16.447341] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   16.447345] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   16.447566] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   16.447600] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
[   16.447718] usb usb1: configuration #1 chosen from 1 choice
[   16.447740] hub 1-0:1.0: USB hub found
[   16.447745] hub 1-0:1.0: 2 ports detected
[   16.548145] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[   16.548157] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   16.548162] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   16.548182] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   16.548216] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001840
[   16.548318] usb usb2: configuration #1 chosen from 1 choice
[   16.548340] hub 2-0:1.0: USB hub found
[   16.548347] hub 2-0:1.0: 2 ports detected
[   16.657368] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   16.657380] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   16.657385] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   16.657409] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   16.657443] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001860
[   16.657550] usb usb3: configuration #1 chosen from 1 choice
[   16.657570] hub 3-0:1.0: USB hub found
[   16.657575] hub 3-0:1.0: 2 ports detected
[   16.685192] SCSI subsystem initialized
[   16.697847] libata version 3.00 loaded.
[   16.768741] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   16.768753] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   16.768758] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   16.768784] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   16.768818] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001880
[   16.768929] usb usb4: configuration #1 chosen from 1 choice
[   16.768950] hub 4-0:1.0: USB hub found
[   16.768955] hub 4-0:1.0: 2 ports detected
[   16.871645] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   16.871657] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   16.871661] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   16.871684] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   16.871717] uhci_hcd 0000:00:1d.2: irq 21, io base 0x000018a0
[   16.871828] usb usb5: configuration #1 chosen from 1 choice
[   16.871849] hub 5-0:1.0: USB hub found
[   16.871854] hub 5-0:1.0: 2 ports detected
[   16.975523] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 21
[   16.975538] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   16.975542] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   16.975567] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   16.979470] ehci_hcd 0000:00:1a.7: debug port 1
[   16.979476] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   16.979482] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xf8604800
[   16.995355] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.995471] usb usb6: configuration #1 chosen from 1 choice
[   16.995494] hub 6-0:1.0: USB hub found
[   16.995499] hub 6-0:1.0: 4 ports detected
[   17.099365] ahci 0000:00:1f.2: version 3.0
[   17.099394] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   17.294860] Clocksource tsc unstable (delta = -3495287421 ns)
[   17.299198] Time: hpet clocksource has been installed.
[   17.316295] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   17.332268] usb 2-2: configuration #1 chosen from 1 choice
[   17.348135] usbcore: registered new interface driver hiddev
[   17.353019] input: USB Mouse as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.0/input/input2
[   17.356684] input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:1a.1-2
[   17.356705] usbcore: registered new interface driver usbhid
[   17.356710] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   17.390490] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   17.390497] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   17.390506] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   17.390788] scsi0 : ahci
[   17.390978] scsi1 : ahci
[   17.391114] scsi2 : ahci
[   17.391197] ata1: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604100 irq 220
[   17.391200] ata2: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604180 irq 220
[   17.391203] ata3: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604200 irq 220
[   17.430960] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   17.431425] ata1.00: ATA-8: WDC WD1600BEVT-60ZCT0, 11.01A11, max UDMA/100
[   17.431431] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   17.432018] ata1.00: configured for UDMA/100
[   17.452393] ata2: SATA link down (SStatus 0 SControl 300)
[   17.471825] ata3: SATA link down (SStatus 0 SControl 300)
[   17.472067] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-6 11.0 PQ: 0 ANSI: 5
[   17.472397] ACPI: PCI Interrupt 0000:07:09.0[A] -> GSI 20 (level, low) -> IRQ 22
[   17.473687] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   17.473697] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   17.473701] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   17.473725] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   17.477641] ehci_hcd 0000:00:1d.7: debug port 1
[   17.477648] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   17.477653] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf8604c00
[   17.525035] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8300000-f83007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   17.529034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.529161] usb usb7: configuration #1 chosen from 1 choice
[   17.529184] hub 7-0:1.0: USB hub found
[   17.529190] hub 7-0:1.0: 6 ports detected
[   17.529239] Driver 'sd' needs updating - please use bus_type methods
[   17.533505] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   17.533557] sd 0:0:0:0: [sda] Write Protect is off
[   17.533563] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.533653] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.533740] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   17.533772] sd 0:0:0:0: [sda] Write Protect is off
[   17.533774] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.533833] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.533836]  sda: sda1 sda2 sda3 sda4
[   17.604529] sd 0:0:0:0: [sda] Attached SCSI disk
[   17.608469] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.624227] ata_piix 0000:00:1f.1: version 2.12
[   17.624245] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 20
[   17.624284] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   17.624755] scsi3 : ata_piix
[   17.624800] scsi4 : ata_piix
[   17.625329] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   17.625332] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   17.941904] ata4.00: ATAPI: TSSTcorp CDDVDW TS-L632N, 0503, max MWDMA2
[   17.944110] usb 7-4: new high speed USB device using ehci_hcd and address 2
[   18.094813] usb 7-4: configuration #1 chosen from 1 choice
[   18.111068] ata4.00: configured for MWDMA2
[   18.255597] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632N  0503 PQ: 0 ANSI: 5
[   18.255714] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   18.256024] r8169 Gigabit Ethernet driver 2.2LK loaded
[   18.256054] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   18.256075] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   18.256393] eth0: RTL8101e at 0xf8840000, 00:1e:68:66:f7:4d, XID 34200000 IRQ 219
[   18.267615] Driver 'sr' needs updating - please use bus_type methods
[   18.277715] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.277720] Uniform CD-ROM driver Revision: 3.20
[   18.277806] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   18.333221] Attempting manual resume
[   18.333224] swsusp: Resume From Partition 8:4
[   18.333225] PM: Checking swsusp image.
[   18.333377] PM: Resume from disk failed.
[   18.345580] EXT3-fs: INFO: recovery required on readonly filesystem.
[   18.345583] EXT3-fs: write access will be enabled during recovery.
[   18.518755] usb 5-2: new full speed USB device using uhci_hcd and address 2
[   18.671830] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b008340f300]
[   18.690932] usb 5-2: configuration #1 chosen from 1 choice
[   21.998670] kjournald starting.  Commit interval 5 seconds
[   21.998710] EXT3-fs: sda3: orphan cleanup on readonly fs
[   21.998720] ext3_orphan_cleanup: deleting unreferenced inode 2072590
[   21.998751] ext3_orphan_cleanup: deleting unreferenced inode 2072636
[   21.998767] EXT3-fs: sda3: 2 orphan inodes deleted
[   21.998768] EXT3-fs: recovery complete.
[   22.000780] EXT3-fs: mounted filesystem with ordered data mode.
[   30.072617] Linux agpgart interface v0.102
[   30.144348] iTCO_vendor_support: vendor-support=0
[   30.157033] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.157115] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   30.157155] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.223098] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   30.299116] agpgart: Detected an Intel 965GM Chipset.
[   30.300060] agpgart: Detected 7676K stolen memory.
[   30.313105] agpgart: AGP aperture is 256M @ 0xd0000000
[   30.342814] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.396246] shpchp: Unknown symbol acpi_run_oshp
[   30.396324] shpchp: Unknown symbol pci_hp_change_slot_info
[   30.396422] shpchp: Unknown symbol pci_hp_register
[   30.396666] shpchp: Unknown symbol pci_hp_deregister
[   30.396858] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   30.397448] shpchp: Unknown symbol acpi_run_oshp
[   30.397525] shpchp: Unknown symbol pci_hp_change_slot_info
[   30.397623] shpchp: Unknown symbol pci_hp_register
[   30.397866] shpchp: Unknown symbol pci_hp_deregister
[   30.398058] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   30.427660] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.482891] input: Power Button (FF) as /devices/virtual/input/input4
[   30.512582] ACPI: Battery Slot [BAT0] (battery present)
[   30.543422] ACPI: Power Button (FF) [PWRF]
[   30.543490] input: Power Button (CM) as /devices/virtual/input/input5
[   30.607314] ACPI: Power Button (CM) [PWRB]
[   30.607368] input: Sleep Button (CM) as /devices/virtual/input/input6
[   30.655233] ACPI: Sleep Button (CM) [SLPB]
[   30.655299] input: Lid Switch as /devices/virtual/input/input7
[   30.699738] ACPI: Lid Switch [LID]
[   30.699815] ACPI: WMI-Acer: Mapper loaded
[   30.703450] ACPI: AC Adapter [ACAD] (on-line)
[   30.902851] ricoh-mmc: Ricoh MMC Controller disabling driver
[   30.902854] ricoh-mmc: Copyright(c) Philip Langdale
[   30.902900] ricoh-mmc: Ricoh MMC controller found at 0000:07:09.2 [1180:0843] (rev 12)
[   30.902912] ricoh-mmc: Controller is now disabled.
[   30.947036] sdhci: Secure Digital Host Controller Interface driver
[   30.947040] sdhci: Copyright(c) Pierre Ossman
[   30.947091] sdhci: SDHCI controller found at 0000:07:09.1 [1180:0822] (rev 22)
[   30.947113] ACPI: PCI Interrupt 0000:07:09.1[B] -> GSI 21 (level, low) -> IRQ 18
[   30.947132] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   30.947173] mmc0: SDHCI at 0xf8300800 irq 18 DMA
[   31.103188] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input8
[   31.141466] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   31.148011] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   31.189385] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   31.449383] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   31.449410] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   31.555142] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   31.555146] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   31.557950] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   31.557966] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   31.557984] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   31.754561] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0x200000
[   31.861153] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   31.972813] Bluetooth: Core ver 2.11
[   31.976235] NET: Registered protocol family 31
[   31.976238] Bluetooth: HCI device and connection manager initialized
[   31.976241] Bluetooth: HCI socket layer initialized
[   31.990429] Bluetooth: HCI USB driver ver 2.9
[   31.992328] usbcore: registered new interface driver hci_usb
[   32.007566] Linux video capture interface: v2.00
[   32.064342] uvcvideo: Found UVC 1.00 device CNF7055 (04f2:b067)
[   32.067672] usbcore: registered new interface driver uvcvideo
[   32.067676] USB Video Class driver (v0.1.0)
[   32.998004] iwl3945: Tunable channels: 13 802.11bg, 0 802.11a channels
[   32.998425] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   33.078000] lp: driver loaded but no devices found
[   33.204091] Adding 2931852k swap on /dev/sda4.  Priority:-1 extents:1 across:2931852k
[   33.745533] EXT3 FS on sda3, internal journal
[   33.916819] device-mapper: uevent: version 1.0.3
[   33.916848] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   35.084165] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.661301] No dock devices found.
[   36.914401] apm: BIOS not found.
[   37.519970] ppdev: user-space parallel port driver
[   37.663627] audit(1241423702.723:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5554 profile="/usr/sbin/cupsd" namespace="default"
[   40.135687] r8169: eth0: link up
[   40.135700] r8169: eth0: link up
[   40.235520] Bluetooth: L2CAP ver 2.9
[   40.235527] Bluetooth: L2CAP socket layer initialized
[   40.324895] Bluetooth: RFCOMM socket layer initialized
[   40.324910] Bluetooth: RFCOMM TTY layer initialized
[   40.324913] Bluetooth: RFCOMM ver 1.8
[   40.654417] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[   40.654482] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
[   41.647572] iwl3945: Can't stop Rx DMA.
[   43.081064] NET: Registered protocol family 17
[   43.436469] [drm] Initialized drm 1.1.0 20060810
[   43.439820] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   43.439833] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   43.439915] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   45.025326] NET: Registered protocol family 10
[   45.025740] lo: Disabled Privacy Extensions
[   45.027207] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.282203] eth0: no IPv6 routers present
[   58.005302] CPU0 attaching NULL sched-domain.
[   58.005309] CPU1 attaching NULL sched-domain.
[   58.034367] CPU0 attaching sched-domain:
[   58.034373]  domain 0: span 03
[   58.034375]   groups: 01 02
[   58.034378] CPU1 attaching sched-domain:
[   58.034380]  domain 0: span 03
[   58.034381]   groups: 02 01
[  378.236256] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 4
[  378.237836] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  378.249821] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
[  378.329806] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  378.331985] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  378.333940] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  378.335543] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  378.338868] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  378.338878] psmouse.c: issuing reconnect request
[  379.343245] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0x200000
[  379.454157] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[  380.383338] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0x200000
[  380.492283] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12[B]



Network configuration::::
[/B]sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:5c:25:3d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:66:f7:4d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.69 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s[B]



scan for networks::::
[/B]iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

[B]UBUNTU VERSION:::


   [/B] Ubuntu 8.04.1[B] Kernel/architecture (including 32 vs. 64 bit)::::

[/B]2.6.24-21-generic i686


[B]Restarting the network:
[/B]sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                        ppp0: ERROR while getting interface flags: No such device
/usr/sbin/pppd: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'
Failed to bring up ppp0.

---

