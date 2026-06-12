---
title: "Wireless driver apparently working, but no networks appear"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by polt on 2012-01-17
Today I reverted back to Ubuntu 10.04.3 LTS (2.6.32-37-generic i686) after hating 11.10, switching to Linux Mint 12 and seeing the error of my ways (Gnome 3!), and finally reverting to the last distro I liked.  Anyhow, now the wireless is not working.

I have a Dell Latitude D630.

The Broadcom STA driver (found in proprietary Hardware drivers section) has been activated, but there are no networks in the Wireless networks list, and it reads "disconnected".  However, the Wireless is enabled (both mentally via Ubuntu, as well as physically via the hard Wireless on/off switch).

Sorry if I'm doing something obviously dumb.

Some outputs:

lspci:
```
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:21:70:d2:b5:39  
          inet addr:10.0.1.4  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fed2:b539/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1425594 (1.4 MB)  TX bytes:294169 (294.1 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:5e:93:1f  
          inet6 addr: fe80::222:5fff:fe5e:931f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


```

lshw -C network:
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:5e:93:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f6cfc000-f6cfffff

```

iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

sudo /etc/init.d/networking restart:
```
 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
                                                                                               [ OK ]

```

dmesg:
```
[    0.464731] NET: Registered protocol family 2
[    0.464893] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.465367] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.466523] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.467128] TCP: Hash tables configured (established 131072 bind 65536)
[    0.467132] TCP reno registered
[    0.467364] NET: Registered protocol family 1
[    0.467401] pci 0000:00:02.0: Boot video device
[    0.467867] cpufreq-nforce2: No nForce2 chipset.
[    0.467906] Scanning for low memory corruption every 60 seconds
[    0.468076] audit: initializing netlink socket (disabled)
[    0.468096] type=2000 audit(1326782664.467:1): initialized
[    0.478238] highmem bounce pool size: 64 pages
[    0.478243] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.479938] VFS: Disk quotas dquot_6.5.2
[    0.479999] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.480600] fuse init (API version 7.13)
[    0.480691] msgmni has been set to 1705
[    0.480913] alg: No test for stdrng (krng)
[    0.480969] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.480972] io scheduler noop registered
[    0.480974] io scheduler anticipatory registered
[    0.480976] io scheduler deadline registered
[    0.481017] io scheduler cfq registered (default)
[    0.481200]   alloc irq_desc for 24 on node -1
[    0.481202]   alloc kstat_irqs on node -1
[    0.481214] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.481227] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.481393]   alloc irq_desc for 25 on node -1
[    0.481395]   alloc kstat_irqs on node -1
[    0.481405] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.481416] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.481580]   alloc irq_desc for 26 on node -1
[    0.481582]   alloc kstat_irqs on node -1
[    0.481591] pcieport 0000:00:1c.5: irq 26 for MSI/MSI-X
[    0.481603] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.481714] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.481818] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.481948] ACPI: AC Adapter [AC] (off-line)
[    0.482041] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.482593] ACPI: Lid Switch [LID]
[    0.482641] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.482648] ACPI: Power Button [PBTN]
[    0.482695] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.482698] ACPI: Sleep Button [SBTN]
[    0.483378] ACPI: SSDT 7f65c4f6 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.483889] ACPI: SSDT 7f65be8c 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.484282] Monitor-Mwait will be used to enter C-1 state
[    0.484305] Monitor-Mwait will be used to enter C-2 state
[    0.484327] Monitor-Mwait will be used to enter C-3 state
[    0.484333] Marking TSC unstable due to TSC halts in idle
[    0.484380] Switching to clocksource hpet
[    0.484395] processor LNXCPU:00: registered as cooling_device0
[    0.484737] ACPI: SSDT 7f65c77c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.485073] ACPI: SSDT 7f65c471 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.485576] processor LNXCPU:01: registered as cooling_device1
[    0.511810] thermal LNXTHERM:01: registered as thermal_zone0
[    0.511819] ACPI: Thermal Zone [THM] (51 C)
[    0.514922] isapnp: Scanning for PnP cards...
[    0.537752] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.537885] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.538344] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.539460] brd: module loaded
[    0.539948] loop: module loaded
[    0.540026] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.540110] ata_piix 0000:00:1f.1: version 2.13
[    0.540122] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.540160] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.540240] scsi0 : ata_piix
[    0.540310] scsi1 : ata_piix
[    0.540472] ACPI: Battery Slot [BAT1] (battery absent)
[    0.548355] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.548358] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.548845] Fixed MDIO Bus: probed
[    0.548880] PPP generic driver version 2.4.2
[    0.548914] tun: Universal TUN/TAP device driver, 1.6
[    0.548916] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.549021] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.549041]   alloc irq_desc for 22 on node -1
[    0.549043]   alloc kstat_irqs on node -1
[    0.549049] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.549061] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.549065] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.549098] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.549136] ehci_hcd 0000:00:1a.7: debug port 1
[    0.553022] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.553036] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.556931] ACPI: Battery Slot [BAT0] (battery present)
[    0.562697] ata2: port disabled. ignoring.
[    0.565018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.565100] usb usb1: configuration #1 chosen from 1 choice
[    0.565129] hub 1-0:1.0: USB hub found
[    0.565136] hub 1-0:1.0: 4 ports detected
[    0.565200]   alloc irq_desc for 20 on node -1
[    0.565202]   alloc kstat_irqs on node -1
[    0.565207] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.565217] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.565221] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.565254] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.565290] ehci_hcd 0000:00:1d.7: debug port 1
[    0.569165] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.569179] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.585016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.585086] usb usb2: configuration #1 chosen from 1 choice
[    0.585113] hub 2-0:1.0: USB hub found
[    0.585120] hub 2-0:1.0: 6 ports detected
[    0.585184] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.585199] uhci_hcd: USB Universal Host Controller Interface driver
[    0.585219] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.585227] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.585230] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.585262] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.585290] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.585383] usb usb3: configuration #1 chosen from 1 choice
[    0.585411] hub 3-0:1.0: USB hub found
[    0.585418] hub 3-0:1.0: 2 ports detected
[    0.585467]   alloc irq_desc for 21 on node -1
[    0.585468]   alloc kstat_irqs on node -1
[    0.585473] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.585480] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.585483] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.585518] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.585554] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.585644] usb usb4: configuration #1 chosen from 1 choice
[    0.585672] hub 4-0:1.0: USB hub found
[    0.585678] hub 4-0:1.0: 2 ports detected
[    0.585726] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.585733] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.585736] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.585767] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.585795] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.585890] usb usb5: configuration #1 chosen from 1 choice
[    0.585916] hub 5-0:1.0: USB hub found
[    0.585923] hub 5-0:1.0: 2 ports detected
[    0.585968] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.585975] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.585979] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.586011] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.586039] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.586131] usb usb6: configuration #1 chosen from 1 choice
[    0.586157] hub 6-0:1.0: USB hub found
[    0.586163] hub 6-0:1.0: 2 ports detected
[    0.586210] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.586217] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.586221] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.586257] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.586285] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.586378] usb usb7: configuration #1 chosen from 1 choice
[    0.586403] hub 7-0:1.0: USB hub found
[    0.586410] hub 7-0:1.0: 2 ports detected
[    0.586508] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.589747] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.589755] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.589827] mice: PS/2 mouse device common for all mice
[    0.589944] rtc_cmos 00:03: RTC can wake from S4
[    0.589980] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.590012] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.590110] device-mapper: uevent: version 1.0.3
[    0.590206] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.590271] device-mapper: multipath: version 1.1.0 loaded
[    0.590273] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.590377] EISA: Probing bus 0 at eisa.0
[    0.590379] EISA: Cannot allocate resource for mainboard
[    0.590381] Cannot allocate resource for EISA slot 1
[    0.590383] Cannot allocate resource for EISA slot 2
[    0.590385] Cannot allocate resource for EISA slot 3
[    0.590387] Cannot allocate resource for EISA slot 4
[    0.590389] Cannot allocate resource for EISA slot 5
[    0.590404] EISA: Detected 0 cards.
[    0.590549] cpuidle: using governor ladder
[    0.590666] cpuidle: using governor menu
[    0.591094] TCP cubic registered
[    0.591252] NET: Registered protocol family 10
[    0.592098] NET: Registered protocol family 17
[    0.593173] Using IPI No-Shortcut mode
[    0.593243] PM: Resume from disk failed.
[    0.593254] registered taskstats version 1
[    0.594009]   Magic number: 12:563:721
[    0.594018] block loop1: hash matches
[    0.594092] rtc_cmos 00:03: setting system clock to 2012-01-17 06:44:25 UTC (1326782665)
[    0.594095] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.594096] EDD information not available.
[    0.596949] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.725424] ata1.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D400, max UDMA/33
[    0.757325] ata1.00: configured for UDMA/33
[    0.871851] isapnp: No Plug & Play device found
[    0.874121] scsi 0:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D400 PQ: 0 ANSI: 5
[    0.888957] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.888962] Uniform CD-ROM driver Revision: 3.20
[    0.889108] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.889173] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.889269] Freeing unused kernel memory: 668k freed
[    0.889667] Write protecting the kernel text: 4684k
[    0.889726] Write protecting the kernel read-only data: 1844k
[    0.897089] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    0.906722] udev: starting version 151
[    1.005947] ahci 0000:00:1f.2: version 3.0
[    1.005970]   alloc irq_desc for 18 on node -1
[    1.005972]   alloc kstat_irqs on node -1
[    1.005980] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.006025]   alloc irq_desc for 27 on node -1
[    1.006027]   alloc kstat_irqs on node -1
[    1.006038] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    1.006114] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    1.006118] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    1.006124] ahci 0000:00:1f.2: setting latency timer to 64
[    1.029197] usb 2-1: configuration #1 chosen from 1 choice
[    1.055393] scsi2 : ahci
[    1.060072] scsi3 : ahci
[    1.061828] scsi4 : ahci
[    1.062117] ata3: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb900 irq 27
[    1.062120] ata4: DUMMY
[    1.062123] ata5: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfba00 irq 27
[    1.068213] tg3.c:v3.102 (September 1, 2009)
[    1.068235] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.068246] tg3 0000:09:00.0: setting latency timer to 64
[    1.075159] Initializing USB Mass Storage driver...
[    1.075315] scsi5 : SCSI emulation for USB Mass Storage devices
[    1.075406] usb-storage: device found at 2
[    1.075408] usb-storage: waiting for device to settle before scanning
[    1.075412] usbcore: registered new interface driver usb-storage
[    1.075450] USB Mass Storage support registered.
[    1.088494] eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:21:70:d2:b5:39
[    1.088497] eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.088500] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.088502] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.380123] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.380155] ata5: SATA link down (SStatus 0 SControl 300)
[    1.385052] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    1.420720] ata3.00: ATA-8: WDC WD1200BEVT-75ZCT2, 11.01A11, max UDMA/133
[    1.420726] ata3.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
[    1.422245] ata3.00: configured for UDMA/133
[    1.436283] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVT-7 11.0 PQ: 0 ANSI: 5
[    1.436451] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.436531] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.436578] sd 2:0:0:0: [sda] Write Protect is off
[    1.436581] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.436605] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.436736]  sda: sda1 sda2 < sda5 >
[    1.470217] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.473302] ohci1394 0000:03:01.4: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.529413] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f6aff000-f6aff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    1.537455] usb 7-1: configuration #1 chosen from 1 choice
[    1.540404] hub 7-1:1.0: USB hub found
[    1.542339] hub 7-1:1.0: 4 ports detected
[    1.718120] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.825355] usb 7-1.2: new full speed USB device using uhci_hcd and address 3
[    1.943484] usb 7-1.2: configuration #1 chosen from 1 choice
[    2.805671] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[334fc00006b575e1]
[    6.072357] usb-storage: device scan complete
[    6.072939] scsi 5:0:0:0: Direct-Access     Seagate  FreeAgent GoFlex 0148 PQ: 0 ANSI: 4
[    6.073036] scsi: killing requests for dead queue
[    6.073099] scsi: killing requests for dead queue
[    6.073158] scsi: killing requests for dead queue
[    6.073210] scsi: killing requests for dead queue
[    6.073271] scsi: killing requests for dead queue
[    6.073319] scsi: killing requests for dead queue
[    6.073369] scsi: killing requests for dead queue
[    6.073418] scsi: killing requests for dead queue
[    6.073587] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    6.074142] sd 5:0:0:0: [sdb] 625142447 512-byte logical blocks: (320 GB/298 GiB)
[    6.074640] sd 5:0:0:0: [sdb] Write Protect is off
[    6.074645] sd 5:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[    6.074649] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    6.075882] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    6.075886]  sdb: sdb1
[    6.077765] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    6.077770] sd 5:0:0:0: [sdb] Attached SCSI disk
[   11.623841] udev: starting version 151
[   11.649375] Adding 4805624k swap on /dev/sda5.  Priority:-1 extents:1 across:4805624k 
[   11.668542] lp: driver loaded but no devices found
[   11.819082] lib80211: common routines for IEEE802.11 drivers
[   11.819085] lib80211_crypt: registered algorithm 'NULL'
[   11.824406] Linux agpgart interface v0.103
[   11.898186] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.898190] Disabling lock debugging due to kernel taint
[   11.942384] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   11.942933] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   11.959685] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.959705] wl 0000:0c:00.0: setting latency timer to 64
[   11.974054] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.980276] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   12.019426] [drm] Initialized drm 1.1.0 20060810
[   12.052472] input: Dell WMI hotkeys as /devices/virtual/input/input5
[   12.054957] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01f9]
[   12.054985] yenta_cardbus 0000:03:01.0: O2: res at 0x94/0xD4: 00/ea
[   12.054987] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst
[   12.056185] lib80211_crypt: registered algorithm 'TKIP'
[   12.056517] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   12.064370] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.064375] i915 0000:00:02.0: setting latency timer to 64
[   12.078846]   alloc irq_desc for 28 on node -1
[   12.078849]   alloc kstat_irqs on node -1
[   12.078858] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[   12.078865] [drm] set up 7M of stolen space
[   12.104602] type=1505 audit(1326782677.009:2):  operation="profile_load" pid=768 name="/sbin/dhclient3"
[   12.105343] type=1505 audit(1326782677.009:3):  operation="profile_load" pid=768 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.105743] type=1505 audit(1326782677.009:4):  operation="profile_load" pid=768 name="/usr/lib/connman/scripts/dhclient-script"
[   12.111105] type=1505 audit(1326782677.013:5):  operation="profile_replace" pid=780 name="/sbin/dhclient3"
[   12.111841] type=1505 audit(1326782677.013:6):  operation="profile_replace" pid=780 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.112246] type=1505 audit(1326782677.017:7):  operation="profile_replace" pid=780 name="/usr/lib/connman/scripts/dhclient-script"
[   12.183409] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   12.183414] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   12.183418] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   12.183427] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   12.183430] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: clean.
[   12.183652] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xf6a00000 - 0xf6afffff
[   12.183655] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   12.203143] composite sync not supported
[   12.400350] type=1505 audit(1326782677.305:8):  operation="profile_load" pid=899 name="/usr/share/gdm/guest-session/Xsession"
[   12.410024] type=1505 audit(1326782677.313:9):  operation="profile_replace" pid=900 name="/sbin/dhclient3"
[   12.410764] type=1505 audit(1326782677.313:10):  operation="profile_replace" pid=900 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.411172] type=1505 audit(1326782677.313:11):  operation="profile_replace" pid=900 name="/usr/lib/connman/scripts/dhclient-script"
[   12.486392] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.488453] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   12.489294] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.489977] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.490664] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.630954] [drm] initialized overlay support
[   12.850801]   alloc irq_desc for 29 on node -1
[   12.850805]   alloc kstat_irqs on node -1
[   12.850823] tg3 0000:09:00.0: irq 29 for MSI/MSI-X
[   12.854804] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input6
[   12.875374] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input7
[   12.888417] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.015691] ppdev: user-space parallel port driver
[   13.046400] composite sync not supported
[   13.198623] fb0: inteldrmfb frame buffer device
[   13.198626] registered panic notifier
[   13.200580] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input8
[   13.200630] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   13.200691] ACPI Warning for \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) (20090903/nspredef-433)
[   13.200775] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:02/input/input9
[   13.200810] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   13.200835] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.200883] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   13.200912] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.203032] vga16fb: initializing
[   13.203036] vga16fb: mapped to 0xc00a0000
[   13.203039] vga16fb: not registering due to another framebuffer present
[   13.313063] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   13.337893] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.338139] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.541208] Console: switching to colour frame buffer device 160x50
[   13.689229] composite sync not supported
[   13.962000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.053918] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   14.477525] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   14.477529] tg3: eth0: Flow control is on for TX and on for RX.
[   14.477654] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.621608] composite sync not supported
[   15.077461] composite sync not supported
[   16.899329] composite sync not supported
[   17.361090] composite sync not supported
[   17.829390] composite sync not supported
[   18.828095] composite sync not supported
[   20.758018] composite sync not supported
[   23.388069] eth1: no IPv6 routers present
[   23.622060] composite sync not supported
[   24.792058] eth0: no IPv6 routers present
[   72.180657] padlock: VIA PadLock not detected.
[   72.680822] kjournald starting.  Commit interval 5 seconds
[   72.680842] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   72.687986] EXT3 FS on dm-0, internal journal
[   72.687994] EXT3-fs: mounted filesystem with ordered data mode.
[  903.171328] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  903.171331] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  903.171333] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.

```

---

### Post by KV Salzgitter on 2012-01-17
Hallo,

could you post the output of 'sudo rfkill list' ?

---

### Post by polt on 2012-01-17
Embarrassingly, the wireless now works... not that I did anything.  Sorry about this everyone.

---

