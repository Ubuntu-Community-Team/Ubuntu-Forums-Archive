---
title: "atmel wifi pcmcia not running"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by dr.lnx on 2006-06-11
hi my atmel pcmcia wifi card is visible by the system but didn't become running is alway NOT RUNNING what can i do to make this device working?

iwconfig eth2:
```

eth2      IEEE 802.11-DS  ESSID:"Noi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:ED:55:D3:F3
          Bit Rate:11 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:3  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig eth2:
```

eth2      Link encap:Ethernet  HWaddr 00:04:DB:01:15:23
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x5100

```

lshw:
```

*-pcmcia
                description: CardBus bridge
                product: PCI4510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@06:04.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:c8005000-c8005fff irq:169
              *-network
                   description: ATMEL
                   physical id: 0
                   version: AT76C502AR
                   slot: Socket 0
                   resources: irq:3

*-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth2
       serial: 00:04:db:01:15:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

```

dmesg:
```

...[4294671.315000] PCI: Bridge: 0000:00:01.0
[4294671.315000]   IO window: 3000-3fff
[4294671.315000]   MEM window: c0100000-c01fffff
[4294671.315000]   PREFETCH window: d0000000-d7ffffff
[4294671.315000] PCI: Bridge: 0000:00:1c.0
[4294671.315000]   IO window: 4000-4fff
[4294671.315000]   MEM window: c4000000-c7ffffff
[4294671.315000]   PREFETCH window: d8000000-dbffffff
[4294671.315000] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[4294671.315000]   IO window: 00005000-000050ff
[4294671.315000]   IO window: 00005400-000054ff
[4294671.315000]   PREFETCH window: 50000000-51ffffff
[4294671.315000]   MEM window: 52000000-53ffffff
[4294671.315000] PCI: Bridge: 0000:00:1e.0
[4294671.315000]   IO window: 5000-5fff
[4294671.315000]   MEM window: c8000000-c80fffff
[4294671.315000]   PREFETCH window: 50000000-51ffffff
[4294671.315000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294671.316000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.316000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[4294671.316000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294671.316000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294671.316000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294671.316000] Simple Boot Flag at 0x36 set to 0x1
[4294671.316000] audit: initializing netlink socket (disabled)
[4294671.316000] audit(1150020501.315:1): initialized
[4294671.316000] highmem bounce pool size: 64 pages
[4294671.316000] VFS: Disk quotas dquot_6.5.1
[4294671.316000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.316000] Initializing Cryptographic API
[4294671.316000] io scheduler noop registered
[4294671.316000] io scheduler anticipatory registered
[4294671.316000] io scheduler deadline registered
[4294671.316000] io scheduler cfq registered
[4294671.316000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294671.316000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.316000] assign_interrupt_mode Found MSI capability
[4294671.316000] Allocate Port Service[pcie00]
[4294671.316000] Allocate Port Service[pcie03]
[4294671.316000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[4294671.316000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294671.316000] assign_interrupt_mode Found MSI capability
[4294671.316000] Allocate Port Service[pcie00]
[4294671.316000] Allocate Port Service[pcie02]
[4294671.316000] Allocate Port Service[pcie03]
[4294671.317000] isapnp: Scanning for PnP cards...
[4294671.674000] isapnp: No Plug & Play device found
[4294671.686000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.686000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294671.686000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294671.686000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294671.686000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294671.686000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294671.686000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.686000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.688000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 209
[4294671.688000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[4294671.688000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.688000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.688000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.688000] mice: PS/2 mouse device common for all mice
[4294671.689000] EISA: Probing bus 0 at eisa.0
[4294671.689000] Cannot allocate resource for EISA slot 1
[4294671.689000] Cannot allocate resource for EISA slot 2
[4294671.689000] Cannot allocate resource for EISA slot 3
[4294671.689000] Cannot allocate resource for EISA slot 4
[4294671.689000] Cannot allocate resource for EISA slot 5
[4294671.689000] EISA: Detected 0 cards.
[4294671.689000] NET: Registered protocol family 2
[4294671.699000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.699000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[4294671.699000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.700000] TCP: Hash tables configured (established 131072 bind 65536)
[4294671.700000] TCP reno registered
[4294671.700000] TCP bic registered
[4294671.700000] NET: Registered protocol family 1
[4294671.700000] NET: Registered protocol family 8
[4294671.700000] NET: Registered protocol family 20
[4294671.700000] Using IPI Shortcut mode
[4294671.700000] ACPI wakeup devices: 
[4294671.700000] RP01 USB1 USB2 USB3 USB4 USB7 MODM   BT 
[4294671.700000] ACPI: (supports S0 S3 S4 S5)
[4294671.700000] Freeing unused kernel memory: 288k freed
[4294671.738000] vga16fb: initializing
[4294671.738000] vga16fb: mapped to 0xc00a0000
[4294671.855000] Console: switching to colour frame buffer device 80x25
[4294671.855000] fb0: VGA16 VGA frame buffer device
[4294672.316000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294672.983000] Capability LSM initialized
[4294673.008000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294673.385000] SCSI subsystem initialized
[4294673.387000] ACPI: bus type scsi registered
[4294673.387000] libata version 1.20 loaded.
[4294673.388000] ahci 0000:00:1f.2: version 1.2
[4294673.388000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 217
[4294673.388000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[4294673.388000] ahci: probe of 0000:00:1f.2 failed with error -12
[4294673.389000] ata_piix 0000:00:1f.2: version 1.05
[4294673.389000] ata_pci_init_one: pci_dev class+intf: 0x10180
[4294673.389000] ata_pci_init_one: NO_LEGACY == 0
[4294673.389000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 217
[4294673.389000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294673.389000] ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x18F0 irq 14
[4294673.543000] ata1: dev 0 cfg 00:045a 49:0f00 82:746b 83:7fe9 84:6023 85:f469 86:3d49 87:6023 88:203f 93:600b
[4294673.543000] ata1: dev 0 ATA-6, max UDMA/100, 155910825 sectors: LBA48
[4294673.543000] ata1(0): applying bridge limits
[4294673.543000] ata_acpi_push_id: skipping for PATA mode
[4294673.543000] ata1: dev 0 configured for UDMA/100
[4294673.543000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294673.543000] pata_get_dev_handle: dev_handle: 0xdffe0360, parent_handle: 0xdffe9dc0
[4294673.543000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff70800, *handle=0xdffe0360
[4294673.543000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe0b00
[4294673.545000] scsi0 : ata_piix
[4294673.545000]   Vendor: ATA       Model: HTS541080G9AT00   Rev: MB4W
[4294673.545000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294673.545000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294673.545000] pata_get_dev_handle: dev_handle: 0xdffe0360, parent_handle: 0xdffe9dc0
[4294673.545000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff70800, *handle=0xdffe0360
[4294673.545000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x18F8 irq 15
[4294673.854000] ata2: dev 0 cfg 00:85c0 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407 93:4000
[4294673.854000] ata2: dev 0 ATAPI, max UDMA/33
[4294673.854000] ata2(0): applying bridge limits
[4294673.854000] ata_acpi_push_id: skipping for PATA mode
[4294673.854000] ata2: dev 0 configured for UDMA/33
[4294673.854000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294673.854000] pata_get_dev_handle: dev_handle: 0xdffe0360, parent_handle: 0xdffe9dc0
[4294673.854000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff70800, *handle=0xdffe0360
[4294673.854000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe09c0
[4294673.855000] scsi1 : ata_piix
[4294673.857000]   Vendor: MATSHITA  Model: DVD-RAM UJ-840S   Rev: 1.52
[4294673.857000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[4294673.857000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294673.857000] pata_get_dev_handle: dev_handle: 0xdffe0360, parent_handle: 0xdffe9dc0
[4294673.857000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff70800, *handle=0xdffe0360
[4294673.864000] Driver 'sd' needs updating - please use bus_type methods
[4294673.865000] SCSI device sda: 155910825 512-byte hdwr sectors (79826 MB)
[4294673.866000] SCSI device sda: drive cache: write back
[4294673.867000] SCSI device sda: 155910825 512-byte hdwr sectors (79826 MB)
[4294673.868000] SCSI device sda: drive cache: write back
[4294673.868000]  sda: sda1 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 sda14 >
[4294674.037000] sd 0:0:0:0: Attached scsi disk sda
[4294674.546000] usbcore: registered new driver usbfs
[4294674.546000] usbcore: registered new driver hub
[4294674.547000] USB Universal Host Controller Interface driver v2.3
[4294674.547000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 225
[4294674.547000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294674.547000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294674.548000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294674.548000] uhci_hcd 0000:00:1d.0: irq 225, io base 0x00001800
[4294674.549000] hub 1-0:1.0: USB hub found
[4294674.549000] hub 1-0:1.0: 2 ports detected
[4294674.615000] ieee1394: Initialized config rom entry `ip1394'
[4294674.650000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 217
[4294674.650000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294674.650000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294674.650000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294674.650000] uhci_hcd 0000:00:1d.1: irq 217, io base 0x00001820
[4294674.650000] hub 2-0:1.0: USB hub found
[4294674.650000] hub 2-0:1.0: 2 ports detected
[4294674.751000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 233
[4294674.751000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294674.751000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294674.751000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294674.751000] uhci_hcd 0000:00:1d.2: irq 233, io base 0x00001840
[4294674.751000] hub 3-0:1.0: USB hub found
[4294674.751000] hub 3-0:1.0: 2 ports detected
[4294674.852000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[4294674.852000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294674.852000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294674.852000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294674.852000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x00001860
[4294674.852000] hub 4-0:1.0: USB hub found
[4294674.852000] hub 4-0:1.0: 2 ports detected
[4294674.954000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 225
[4294674.954000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294674.954000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294674.954000] ehci_hcd 0000:00:1d.7: debug port 1
[4294674.954000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294674.955000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294674.955000] ehci_hcd 0000:00:1d.7: irq 225, io mem 0xc0000000
[4294674.958000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294674.959000] hub 5-0:1.0: USB hub found
[4294674.959000] hub 5-0:1.0: 8 ports detected
[4294675.060000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294675.060000] ACPI: PCI Interrupt 0000:06:04.1[A] -> GSI 16 (level, low) -> IRQ 169
[4294675.111000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[169]  MMIO=[c8006000-c80067ff]  Max Packet=[2048]
[4294675.131000] ide0: I/O resource 0x1F0-0x1F7 not free.
[4294675.131000] ide0: ports already in use, skipping probe
[4294675.131000] ide1: I/O resource 0x170-0x177 not free.
[4294675.131000] ide1: ports already in use, skipping probe
[4294675.154000] Attempting manual resume
[4294675.182000] EXT3-fs: mounted filesystem with ordered data mode.
[4294675.194000] kjournald starting.  Commit interval 5 seconds
[4294676.428000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f5775405947]
[4294681.760000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294681.760000]  1:0:0:0: Attached scsi generic sg1 type 5
[4294681.794000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[4294681.794000] Uniform CD-ROM driver Revision: 3.20
[4294681.794000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[4294682.845000] Linux agpgart interface v0.101 (c) Dave Jones
[4294682.859000] agpgart: Detected an Intel 915GM Chipset.
[4294682.877000] agpgart: AGP aperture is 256M @ 0x0
[4294682.893000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294682.896000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294683.468000] hw_random: RNG not detected
[4294683.489000] Real Time Clock Driver v1.12
[4294683.539000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294683.539000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[4294683.540000] sky2 v0.15 addr 0xc4000000 irq 169 Yukon-FE (0xb7) rev 1
[4294683.540000] sky2 eth0: addr 00:0f:b0:8c:47:ca
[4294683.656000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 177
[4294683.657000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294683.949000] input: PS/2 Mouse as /class/input/input1
[4294683.968000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input2
[4294684.089000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[4294684.090000] ts: Compaq touchscreen protocol output
[4294684.308000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[4294684.308000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294684.325000] ieee80211_crypt: registered algorithm 'NULL'
[4294684.327000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294684.327000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294684.362000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4294684.362000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294684.362000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4294684.469000] intel8x0_measure_ac97_clock: measured 4291598654 usecs
[4294684.469000] intel8x0: measured clock 0 rejected
[4294684.469000] intel8x0: clocking to 48000
[4294684.472000] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 22 (level, low) -> IRQ 50
[4294684.472000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294684.678000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[4294684.678000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294684.678000] Yenta: CardBus bridge found at 0000:06:04.0 [1179:ff00]
[4294684.678000] Yenta: Enabling burst memory read transactions
[4294684.678000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294684.678000] Yenta: Routing CardBus interrupts to PCI
[4294684.678000] Yenta TI: socket 0000:06:04.0, mfunc 0x00aa1b22, devctl 0x64
[4294684.901000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 169
[4294684.901000] Socket status: 30000011
[4294684.901000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[4294684.901000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[4294684.901000] cs: IO port probe 0x5000-0x5fff: clean.
[4294684.901000] pcmcia: parent PCI bridge Memory window: 0xc8000000 - 0xc80fffff
[4294684.901000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[4294684.983000] ieee80211_crypt: registered algorithm 'WEP'
[4294685.538000] pccard: PCMCIA card inserted into slot 0
[4294685.538000] cs: memory probe 0xc8000000-0xc80fffff: excluding 0xc8000000-0xc800ffff
[4294685.546000] pcmcia: registering new device pcmcia0.0
[4294685.679000] cs: IO port probe 0x100-0x4ff: excluding 0x370-0x377 0x3f0-0x3f7 0x4d0-0x4d7
[4294685.682000] cs: IO port probe 0xc00-0xcf7: clean.
[4294685.683000] cs: IO port probe 0xa00-0xaff: clean.
[4294686.193000] eth2: Atmel at76c50x. Version 0.98. MAC 00:04:db:01:15:23
[4294686.626000] lp: driver loaded but no devices found
[4294686.680000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294686.680000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294686.680000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294686.710000] Adding 1951824k swap on /dev/sda5.  Priority:-1 extents:1 across:1951824k
[4294686.877000] EXT3 FS on sda7, internal journal
[4294687.505000] kjournald starting.  Commit interval 5 seconds
[4294687.505000] EXT3 FS on sda14, internal journal
[4294687.505000] EXT3-fs: mounted filesystem with writeback data mode.
[4294687.506000] kjournald starting.  Commit interval 5 seconds
[4294687.507000] EXT3 FS on sda13, internal journal
[4294687.507000] EXT3-fs: mounted filesystem with writeback data mode.
[4294687.508000] kjournald starting.  Commit interval 5 seconds
[4294687.508000] EXT3 FS on sda9, internal journal
[4294687.508000] EXT3-fs: mounted filesystem with ordered data mode.
[4294687.511000] kjournald starting.  Commit interval 5 seconds
[4294687.511000] EXT3 FS on sda12, internal journal
[4294687.511000] EXT3-fs: mounted filesystem with writeback data mode.
[4294687.512000] kjournald starting.  Commit interval 5 seconds
[4294687.512000] EXT3 FS on sda11, internal journal
[4294687.512000] EXT3-fs: mounted filesystem with ordered data mode.
[4294687.513000] kjournald starting.  Commit interval 5 seconds
[4294687.514000] EXT3 FS on sda8, internal journal
[4294687.514000] EXT3-fs: mounted filesystem with ordered data mode.
[4294687.515000] kjournald starting.  Commit interval 5 seconds
[4294687.515000] EXT3 FS on sda6, internal journal
[4294687.515000] EXT3-fs: mounted filesystem with ordered data mode.
[4294691.939000] ACPI: AC Adapter [ACAD] (on-line)
[4294691.960000] ACPI: Battery Slot [BAT1] (battery present)
[4294692.240000] ACPI: Power Button (FF) [PWRF]
[4294692.240000] ACPI: Lid Switch [LID0]
[4294692.240000] ACPI: Power Button (CM) [PWRB]
[4294692.573000] ibm_acpi: ec object not found
[4294692.597000] pcc_acpi: loading...
[4294692.875000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294692.875000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[4294698.262000] NET: Registered protocol family 10
[4294698.262000] lo: Disabled Privacy Extensions
[4294698.262000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[4294698.262000] IPv6 over IPv4 tunneling driver
[4294700.138000] ppdev: user-space parallel port driver
[4294701.322000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294701.323000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[4294701.323000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294701.336000] [fglrx:firegl_pci_getinfo] *ERROR* Cannot find Asic ID: 0x3152
[4294701.336000] [fglrx:firegl_init_asic] *ERROR* Cannot get PCI info.
[4294702.856000] [fglrx:firegl_unlock] *ERROR* Process 4199 using kernel context 0
[4294708.776000] eth1: no IPv6 routers present
[4294715.644000] Bluetooth: Core ver 2.8
[4294715.644000] NET: Registered protocol family 31
[4294715.644000] Bluetooth: HCI device and connection manager initialized
[4294715.644000] Bluetooth: HCI socket layer initialized
[4294715.764000] Bluetooth: L2CAP ver 2.8
[4294715.764000] Bluetooth: L2CAP socket layer initialized
[4294715.805000] Bluetooth: RFCOMM socket layer initialized
[4294715.805000] Bluetooth: RFCOMM TTY layer initialized
[4294715.805000] Bluetooth: RFCOMM ver 1.7
[4294723.215000] NET: Registered protocol family 17
[4294759.534000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[4294957.299000] ACPI: PCI interrupt for device 0000:06:02.0 disabled
[4294957.302000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'
[4294960.700000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[4294960.702000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[4294960.702000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294960.704000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294960.704000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294960.708000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4294960.708000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294960.708000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4294960.708000] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 22 (level, low) -> IRQ 50
[4294960.708000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294961.104000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[4294961.195000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
[4294972.094000] eth1: no IPv6 routers present
[4295130.519000] ACPI: PCI interrupt for device 0000:06:02.0 disabled
[4295130.521000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'
[4295132.772000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[4295132.774000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[4295132.775000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4295132.795000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4295132.796000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4295132.800000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4295132.801000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4295132.802000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4295132.803000] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 22 (level, low) -> IRQ 50
[4295132.804000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4295132.943000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[4295133.019000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
[4295143.993000] eth1: no IPv6 routers present
[4295200.228000] ACPI: PCI interrupt for device 0000:06:02.0 disabled
[4295200.231000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'
[4295203.034000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[4295203.036000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[4295203.036000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4295203.038000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4295203.038000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4295203.042000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4295203.042000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4295203.042000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4295203.042000] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 22 (level, low) -> IRQ 50
[4295203.042000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4295203.224000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[4295255.012000] eth1: no IPv6 routers present
[4296857.094000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[4297730.962000] sky2 eth0: enabling interface
[4297730.965000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4297732.648000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control none
[4297732.648000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[4297743.571000] eth0: no IPv6 routers present
[4297753.455000] sky2 eth0: disabling interface
[4297753.462000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[4297756.560000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[4297756.560000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[4297756.560000] sky2 v0.15 addr 0xc4000000 irq 169 Yukon-FE (0xb7) rev 1
[4297756.560000] sky2 eth0: addr 00:0f:b0:8c:47:ca
[4297764.516000] sky2 eth0: enabling interface
[4297764.519000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4297766.202000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control none
[4297766.202000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[4297777.122000] eth0: no IPv6 routers present
[4298051.421000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4298051.765000] usbcore: registered new driver hiddev
[4298051.796000] input: Logitech USB RECEIVER as /class/input/input3
[4298051.797000] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.1-1
[4298051.797000] usbcore: registered new driver usbhid
[4298051.797000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4298077.164000] usb 2-1: USB disconnect, address 2
[4298253.078000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[4298287.506000] pcmcia: Detected deprecated PCMCIA ioctl usage.
[4298287.507000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[4298287.508000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[4298288.016000] sr 1:0:0:0: Device not ready.
[4298288.016000] end_request: I/O error, dev sr0, sector 0
[4298288.016000] Buffer I/O error on device sr0, logical block 0
[4298288.016000] Buffer I/O error on device sr0, logical block 1
[4298288.016000] Buffer I/O error on device sr0, logical block 2
[4298288.016000] Buffer I/O error on device sr0, logical block 3
[4298288.016000] Buffer I/O error on device sr0, logical block 4
[4298288.016000] Buffer I/O error on device sr0, logical block 5
[4298288.016000] Buffer I/O error on device sr0, logical block 6
[4298288.016000] Buffer I/O error on device sr0, logical block 7
[4298288.016000] Buffer I/O error on device sr0, logical block 8
[4298288.016000] Buffer I/O error on device sr0, logical block 9
[4298288.028000] sr 1:0:0:0: Device not ready.
[4298288.028000] end_request: I/O error, dev sr0, sector 0
[4298288.040000] sr 1:0:0:0: Device not ready.
[4298288.040000] end_request: I/O error, dev sr0, sector 0
[4298288.052000] sr 1:0:0:0: Device not ready.
[4298288.052000] end_request: I/O error, dev sr0, sector 0

```

tanks

---

### Post by mriya3 on 2006-06-11
Same problem for me (Atmel pcmcia card)

Shows in ifconfig and iwconfig.

Network Manager fails to manage connections because wpa_supplicant gives errors caused by things unsupported by the atmel kernel module. Plus Network Manager needs to be restarted (/etc/init.d/dbus restart) to make it see the card when it's inserted.

Sometimes manually setting the essid with iwconfig and doing a dhclient works, sometimes not.

In breezy it works like a charm.


Hopefully I've installed dapper only on a spare disk, so now I'm sticking with breezy on the main disk (and swap it once a week with the one with dapper to see if something gets fixed)

---

