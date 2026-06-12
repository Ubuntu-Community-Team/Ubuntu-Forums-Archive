---
title: "Ipod Nano 8gb not mounting."
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by sdmike on 2007-01-16
Ok so I got a 8gb nano and it won't mount but before I had a 4gb nano and it mounted but then again that was on Dapper and I'm on Edgy now.

I tried adding a song thinking it would format it but I was wrong.

In my devices ubuntu sees and puts the name ipod under the usb listing.

I do have windows xp and Ubuntu Edgy 6.10 computers.

So what should I do and I have been searching around the forums but I can't seem to find anything that helps me out.

Future thanks.

---

### Post by codejunkie on 2007-01-16
if it has never been formated the quickest/easiest thing to do is use it under windows first and then after you've added a song or two through itunes, try it under ubuntu i know there are utilities out there to format a new ipod but it may take sometime searching the forum and google for them.

---

### Post by sdmike on 2007-01-16
Is the ipod under a ntfs file system and it needs to be switched to at fat32 system?

My ipod already has songs on it.

So do I need to format it to another filing system?

---

### Post by NeoLithium on 2007-01-16
[http://www.ubuntuforums.org/showthread.php?t=64841&highlight=ipod](http://www.ubuntuforums.org/showthread.php?t=64841&highlight=ipod)

This thread helped me out when I had the same issue.

---

### Post by codejunkie on 2007-01-16
> **sdmike said:**
> Is the ipod under a ntfs file system and it needs to be switched to at fat32 system?

My ipod already has songs on it.

So do I need to format it to another filing system?

no it should be formatted with a fat32 partition if you set it up under windows and that should work fine under linux, if you set it up using a mac first it will use an HFS partition.

---

### Post by sdmike on 2007-01-16
But I did load songs under windows so why wouldn't it work? What do I use to format it in windows?

thank you

---

### Post by codejunkie on 2007-01-17
> **sdmike said:**
> But I did load songs under windows so why wouldn't it work? What do I use to format it in windows?

thank you

iTunes will automatically format it with the correct file system which is fat32, the first time you use the ipod with windows, so you don't need to reformat it again. this has to be an error with edgy if the ipod works fine under windows. have you tried the suggestions in the [_**[COLOR="DarkSlateBlue"]Thread[/COLOR]**_]("http://www.ubuntuforums.org/showthread.php?t=64841&highlight=ipod") NeoLithium posted earlier? if those didn't work plug in the ipod and open a terminal and enter ```
dmesg
```and copy and paste the output here.

---

### Post by sdmike on 2007-01-17
jack@laptop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000037ef0000 (usable)
[17179569.184000]  BIOS-e820: 0000000037ef0000 - 0000000037eff000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000037eff000 - 0000000037f00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 894MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f8130
[17179569.184000] On node 0 totalpages: 229104
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225008 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 HP                                    ) @ 0x000f8080
[17179569.184000] ACPI: RSDT (v001 HP     3093     0x20040323  LTP 0x00000000) @ 0x37ef8bae
[17179569.184000] ACPI: FADT (v001 HP     3093     0x20040323 PTL  0x0000005f) @ 0x37efee09
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x20040323  LTP 0x00000001) @ 0x37efee7d
[17179569.184000] ACPI: MADT (v001 PTLTD         3093   0x20040323  LTP 0x00000000) @ 0x37efef74
[17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x20040323  LTP 0x00000000) @ 0x37efefc4
[17179569.184000] ACPI: DSDT (v001 HP     3091     0x20040323 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=37ee7293-1b49-4706-b922-8a6526e893be ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1994.621 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.456000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.456000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.472000] Memory: 897556k/916416k available (1829k kernel code, 18232k reserved, 1038k data, 288k init, 0k highmem)
[17179570.472000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.552000] Calibrating delay using timer specific routine.. 3994.99 BogoMIPS (lpj=7989997)
[17179570.552000] Security Framework v1.0.0 initialized
[17179570.552000] SELinux:  Disabled at boot.
[17179570.552000] Mount-cache hash table entries: 512
[17179570.552000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179570.552000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179570.552000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.552000] CPU: L2 Cache: 1024K (64 bytes/line)
[17179570.552000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179570.552000] CPU: AMD Turion(tm) 64 Mobile Technology ML-37 stepping 02
[17179570.552000] Checking 'hlt' instruction... OK.
[17179570.568000] SMP alternatives: switching to UP code
[17179570.568000] Freeing SMP alternatives: 0k freed
[17179570.568000] checking if image is initramfs... it is
[17179571.116000] Freeing initrd memory: 6692k freed
[17179571.116000] ACPI: Core revision 20060707
[17179571.116000] ACPI: Looking for DSDT ... not found!
[17179571.120000] ENABLING IO-APIC IRQs
[17179571.120000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179571.264000] NET: Registered protocol family 16
[17179571.264000] EISA bus registered
[17179571.264000] ACPI: bus type pci registered
[17179571.264000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179571.264000] PCI: Not using MMCONFIG.
[17179571.264000] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=5
[17179571.264000] PCI: Using configuration type 1
[17179571.264000] Setting up standard PCI resources
[17179571.264000] ACPI: Interpreter enabled
[17179571.264000] ACPI: Using IOAPIC for interrupt routing
[17179571.264000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.264000] PCI: Probing PCI hardware (bus 00)
[17179571.268000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179571.268000] Boot video device is 0000:01:05.0
[17179571.268000] PCI: Transparent bridge - 0000:00:14.4
[17179571.268000] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#05) (try 'pci=assign-busses')
[17179571.268000] Please report the result to linux-kernel to fix this permanently
[17179571.268000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.268000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179571.268000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179571.272000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179571.272000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179571.272000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179571.272000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179571.272000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179571.272000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179571.272000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[17179571.272000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179571.272000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179571.272000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.272000] pnp: PnP ACPI init
[17179571.276000] pnp: PnP ACPI: found 10 devices
[17179571.276000] PnPBIOS: Disabled by ACPI PNP
[17179571.276000] PCI: Using ACPI for IRQ routing
[17179571.276000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.296000] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[17179571.296000] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[17179571.296000] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[17179571.296000] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[17179571.296000] PCI: Bridge: 0000:00:01.0
[17179571.296000]   IO window: 9000-9fff
[17179571.296000]   MEM window: c0100000-c01fffff
[17179571.296000]   PREFETCH window: c8000000-cfffffff
[17179571.296000] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[17179571.296000]   IO window: 0000a400-0000a4ff
[17179571.296000]   IO window: 0000a800-0000a8ff
[17179571.296000]   PREFETCH window: 50000000-51ffffff
[17179571.296000]   MEM window: 52000000-53ffffff
[17179571.296000] PCI: Bridge: 0000:00:14.4
[17179571.296000]   IO window: a000-afff
[17179571.296000]   MEM window: c0200000-c02fffff
[17179571.296000]   PREFETCH window: 50000000-51ffffff
[17179571.296000] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179571.296000] PCI: Setting latency timer of device 0000:05:09.0 to 64
[17179571.296000] NET: Registered protocol family 2
[17179571.332000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.332000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.332000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.332000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.332000] TCP reno registered
[17179571.332000] audit: initializing netlink socket (disabled)
[17179571.332000] audit(1169010795.332:1): initialized
[17179571.332000] VFS: Disk quotas dquot_6.5.1
[17179571.332000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.332000] Initializing Cryptographic API
[17179571.332000] io scheduler noop registered
[17179571.332000] io scheduler anticipatory registered
[17179571.332000] io scheduler deadline registered
[17179571.332000] io scheduler cfq registered (default)
[17179571.332000] isapnp: Scanning for PnP cards...
[17179571.688000] isapnp: No Plug & Play device found
[17179571.704000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.704000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 185
[17179571.704000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[17179571.704000] mice: PS/2 mouse device common for all mice
[17179571.704000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.704000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.704000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.704000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179571.716000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.716000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.716000] EISA: Probing bus 0 at eisa.0
[17179571.716000] Cannot allocate resource for EISA slot 1
[17179571.716000] Cannot allocate resource for EISA slot 8
[17179571.716000] EISA: Detected 0 cards.
[17179571.716000] TCP bic registered
[17179571.716000] NET: Registered protocol family 1
[17179571.716000] NET: Registered protocol family 8
[17179571.716000] NET: Registered protocol family 20
[17179571.716000] Using IPI Shortcut mode
[17179571.716000] ACPI: (supports S0 S3 S4 S5)
[17179571.716000] Freeing unused kernel memory: 288k freed
[17179571.752000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.884000] Capability LSM initialized
[17179572.904000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.904000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.908000] ACPI: Thermal Zone [THRM] (44 C)
[17179573.168000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179573.168000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 193
[17179573.168000] ATIIXP: chipset revision 0
[17179573.168000] ATIIXP: not 100% native mode: will probe irqs later
[17179573.168000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[17179573.168000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[17179573.168000] Probing IDE interface ide0...
[17179573.460000] hda: FUJITSU MHV2080AT PL, ATA DISK drive
[17179574.132000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.208000] Probing IDE interface ide1...
[17179574.944000] hdc: MATSHITAUJ-840D, ATAPI CD/DVD-ROM drive
[17179575.280000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.284000] hda: max request size: 128KiB
[17179575.284000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179575.292000] hda: cache flushes supported
[17179575.292000]  hda: hda1 hda2 hda3 hda4
[17179575.380000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, (U)DMA
[17179575.380000] Uniform CD-ROM driver Revision: 3.20
[17179575.748000] usbcore: registered new driver usbfs
[17179575.748000] usbcore: registered new driver hub
[17179575.748000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179575.748000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179575.748000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179575.748000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179576.084000] ohci_hcd 0000:00:13.0: irq 201, io mem 0xc0000000
[17179576.128000] ieee1394: Initialized config rom entry `ip1394'
[17179576.144000] usb usb1: configuration #1 chosen from 1 choice
[17179576.144000] hub 1-0:1.0: USB hub found
[17179576.144000] hub 1-0:1.0: 4 ports detected
[17179576.248000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 201
[17179576.248000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179576.248000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[17179576.248000] ehci_hcd 0000:00:13.2: irq 201, io mem 0xc0002000
[17179576.248000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.248000] usb usb2: configuration #1 chosen from 1 choice
[17179576.248000] hub 2-0:1.0: USB hub found
[17179576.248000] hub 2-0:1.0: 8 ports detected
[17179576.356000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 201
[17179576.356000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179576.356000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[17179576.692000] ohci_hcd 0000:00:13.1: irq 201, io mem 0xc0001000
[17179576.752000] usb usb3: configuration #1 chosen from 1 choice
[17179576.752000] hub 3-0:1.0: USB hub found
[17179576.752000] hub 3-0:1.0: 4 ports detected
[17179576.868000] ACPI: PCI Interrupt 0000:05:09.2[C] -> GSI 22 (level, low) -> IRQ 209
[17179576.920000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[209]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179577.116000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179577.116000] EXT3-fs: write access will be enabled during recovery.
[17179579.384000] kjournald starting.  Commit interval 5 seconds
[17179579.384000] EXT3-fs: recovery complete.
[17179579.388000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.940000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.948000] Real Time Clock Driver v1.12ac
[17179592.072000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.076000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.180000] 8139too Fast Ethernet driver 0.9.27
[17179592.180000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 217
[17179592.184000] eth0: RealTek RTL8139 at 0xf88ea000, 00:16:36:2c:cd:96, IRQ 217
[17179592.184000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179592.228000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179592.456000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179592.456000] sdhci: Copyright(c) Pierre Ossman
[17179592.456000] sdhci: SDHCI controller found at 0000:05:09.4 [104c:8034] (rev 0)
[17179592.456000] ACPI: PCI Interrupt 0000:05:09.4[A] -> GSI 17 (level, low) -> IRQ 185
[17179592.456000] mmc0: SDHCI at 0xc0209400 irq 185 DMA
[17179592.456000] mmc1: SDHCI at 0xc0209000 irq 185 DMA
[17179592.456000] mmc2: SDHCI at 0xc0208400 irq 185 DMA
[17179592.464000] input: PC Speaker as /class/input/input1
[17179592.896000] ACPI: PCI Interrupt 0000:05:09.3[A] -> GSI 17 (level, low) -> IRQ 185
[17179593.064000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[17179593.096000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179593.132000] eth0: link down
[17179593.136000] ts: Compaq touchscreen protocol output
[17179593.148000] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179593.148000] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[17179593.148000] Yenta: Enabling burst memory read transactions
[17179593.148000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179593.148000] Yenta: Routing CardBus interrupts to PCI
[17179593.148000] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x64
[17179593.388000] Yenta: ISA IRQ mask 0x0ee8, PCI irq 185
[17179593.388000] Socket status: 30000006
[17179593.388000] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[17179593.388000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179593.388000] cs: IO port probe 0xa000-0xafff: clean.
[17179593.388000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[17179593.388000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[17179593.388000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 185
[17179593.500000] MC'97 0 converters and GPIO not ready (0x1)
[17179593.500000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 185
[17179593.824000] cs: IO port probe 0x100-0x3af: clean.
[17179593.828000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179593.828000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179593.832000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179593.832000] cs: IO port probe 0xa00-0xaff: clean.
[17179593.980000] lp: driver loaded but no devices found
[17179594.036000] SCSI subsystem initialized
[17179594.056000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179594.056000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.124000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179594.248000] NET: Registered protocol family 17
[17179594.304000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[17179594.304000] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 225
[17179594.312000] ndiswrapper: using irq 225
[17179594.948000] wlan0: vendor: ''
[17179594.948000] wlan0: ethernet device 00:14:a5:74:45:d6 using NDIS driver bcmwl5, 14E4:4318:103C:1355.5.conf
[17179594.948000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179594.968000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[17179595.000000] Adding 1445840k swap on /dev/disk/by-uuid/9c4ac7ea-23e1-42a9-96fa-6a5b34f7c3c6.  Priority:-1 extents:1 across:1445840k
[17179595.184000] EXT3 FS on hda3, internal journal
[17179595.324000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179595.324000] md: bitmap version 4.39
[17179595.496000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179597.064000] NET: Registered protocol family 10
[17179597.064000] lo: Disabled Privacy Extensions
[17179597.064000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179597.064000] IPv6 over IPv4 tunneling driver
[17179598.412000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179598.500000] NTFS volume version 3.1.
[17179602.844000] ACPI: AC Adapter [ACAD] (off-line)
[17179602.932000] ACPI: Battery Slot [BAT1] (battery present)
[17179602.944000] ACPI: Power Button (FF) [PWRF]
[17179602.944000] ACPI: Power Button (CM) [PWRB]
[17179602.944000] ACPI: Sleep Button (CM) [SLPB]
[17179602.944000] ACPI: Lid Switch [LID]
[17179603.040000] ibm_acpi: ec object not found
[17179603.064000] pcc_acpi: loading...
[17179603.100000] wmi_add device=dff97400
[17179603.100000] calling WQBA
[17179603.144000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179603.324000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179603.324000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x4 (1450 mV)
[17179603.324000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6 (1400 mV)
[17179603.324000] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x8 (1350 mV)
[17179603.324000] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[17179603.324000] cpu_init done, current fid 0xc, vid 0x4
[17179606.132000] apm: BIOS not found.
[17179607.284000] eth1: no IPv6 routers present
[17179614.056000] Bluetooth: Core ver 2.8
[17179614.056000] NET: Registered protocol family 31
[17179614.056000] Bluetooth: HCI device and connection manager initialized
[17179614.056000] Bluetooth: HCI socket layer initialized
[17179614.068000] Bluetooth: L2CAP ver 2.8
[17179614.068000] Bluetooth: L2CAP socket layer initialized
[17179614.104000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179614.120000] Bluetooth: RFCOMM socket layer initialized
[17179614.120000] Bluetooth: RFCOMM TTY layer initialized
[17179614.120000] Bluetooth: RFCOMM ver 1.7
[17179878.188000] ohci_hcd 0000:00:13.0: wakeup
[17179878.572000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[17179878.768000] usb 1-1: not running at top speed; connect to a high speed hub
[17179878.784000] usb 1-1: configuration #1 chosen from 2 choices
[17179879.108000] usbcore: registered new driver libusual
[17179879.192000] Initializing USB Mass Storage driver...
[17179879.192000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179879.196000] usb-storage: device found at 2
[17179879.196000] usb-storage: waiting for device to settle before scanning
[17179879.196000] usbcore: registered new driver usb-storage
[17179879.196000] USB Mass Storage support registered.
[17179885.196000] usb-storage: device scan complete
[17179890.872000] usb 1-1: reset full speed USB device using ohci_hcd and address 2
jack@laptop:~$

---

### Post by sdmike on 2007-01-21
bump!

---

### Post by codejunkie on 2007-01-21
dmesg is not showing any error messages when you plug in the ipod, is it even showing up as a hard drive in Ubuntu, if it's not you might need to create a mount point for it and try manually mounting it.

---

### Post by sdmike on 2007-01-25
how would I go about doing that?

---

### Post by sdmike on 2007-01-25
I think it isn't mounted because it's plugged in via usb and when I go to /media/ it isn't there. So I guess I gotta find out how to update it now.

---

### Post by sdmike on 2007-01-25
I made the directories and made gtkpod aware of it but still I get this.

'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.

Do I need to make a iTunesDB directory too???

---

### Post by sdmike on 2007-01-25
Ok I officially have no idea what I am doing now.

---

### Post by sdmike on 2007-01-25
Ok I got it to mount and work in gtkpod but it gave me this message:

Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.

Should I be concerned about this?

---

### Post by Ptero-4 on 2007-01-25
You probably shouldn't be concerned about it. The "Extended Info" is IIRC just some extra fluff that iTunes put in the songs that is usually not visible outside of iTunes.

---

