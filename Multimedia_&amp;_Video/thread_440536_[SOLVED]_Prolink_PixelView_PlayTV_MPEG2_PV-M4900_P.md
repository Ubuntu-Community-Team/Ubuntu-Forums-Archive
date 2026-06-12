---
title: "[SOLVED] Prolink PixelView PlayTV MPEG2 PV-M4900 PROBLEM, Please Help"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by psavva on 2007-05-11
Hi, 

I've tried over and over to configure this card to work on Ubuntu, but with no luck
Can someone please help
Greatly Appreciated.

I live in Greece which uses a PAL system
I'm running Linux Fiesty 7.04

i did a gmseg and this is what it came up with

```

[   51.054369] bttv: driver version 0.9.16 loaded
[   51.054419] bttv: Bt8xx card found (0).
[   51.054443] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 21
[   51.054454] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 21, latency: 32, mmio: 0xdc7fe000
[   51.054464] bttv0: detected: Prolink Pixelview PV-BT [card=72], PCI subsystem ID is 1554:4011
[   51.054467] bttv0: using: Prolink Pixelview PV-BT878P+ (Rev.4C,8E) [card=70,insmod option]
[   51.054469] bttv0: gpio config override: mask=0x3f, mux=0x21,0x20,0x23,0x23,0xd
[   51.054936] bttv0: using tuner=38
[   51.098523] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   51.098552] tuner 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   51.098556] tuner 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   51.099466] tuner 0-0063: chip found @ 0xc6 (bt878 #0 [sw])
[   51.108377] bttv0: registered device video0
[   51.108411] bttv0: registered device vbi0
[   51.108444] bttv0: registered device radio0
[   51.138887] input: bttv IR (card=70) as /class/input/input3
[   51.363069] Bluetooth: HCI USB driver ver 2.9
[   51.410721] bt878: AUDIO driver version 0.0.0 loaded
[   51.410759] bt878: Bt878 AUDIO function found (0).
[   51.410778] ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 22 (level, low) -> IRQ 21
[   51.410784] bt878_probe: card id=[0x40111554], Unknown card.
[   51.410786] Exiting..
[   51.410790] ACPI: PCI interrupt for device 0000:02:01.1 disabled
[   51.410794] bt878: probe of 0000:02:01.1 failed with error -22


```

---

### Post by spamking2000 on 2007-05-11
This is going to sound crazy, but bttv0 recognizes the BT878 card and registers it as video0... so tvtime ought to be pulling up /dev/video0 if it all were working.

This looks more like an ACPI error. I get ACPI problems on my machine with an AMD processor... so I just disabled ACPI in grub adding something like NOACPI to the boot string. A quick google search should give you the right string verbage. You'll just want to edit it in menu.lst.

---

### Post by psavva on 2007-05-12
Thanks, that worked perfectly

I am a student at University of Huddersfield  studding BSC Computing, Just for me to grasp why this worked, can anyone explain this?

---

### Post by psavva on 2007-05-16
> **spamking2000 said:**
> This is going to sound crazy, but bttv0 recognizes the BT878 card and registers it as video0... so tvtime ought to be pulling up /dev/video0 if it all were working.

This looks more like an ACPI error. I get ACPI problems on my machine with an AMD processor... so I just disabled ACPI in grub adding something like NOACPI to the boot string. A quick google search should give you the right string verbage. You'll just want to edit it in menu.lst.


I got the tvtuner working. I was able to get 1 channel out of the 20 i should be able to get.

I'm assuming i'm using the wrong tuner settings.

Can anybody help me get this tuner working?
I'm assuming i need to set the tuner for my country.  I live in Thessaloniki, Greece.

We use PAL I  for TV Tuners.

```

[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 261935) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261935
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261935
[    0.000000] On node 0 totalpages: 261935
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32305 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f61e0
[    0.000000] ACPI: RSDT (v001 INTEL  D865GBF  0x20050804 MSFT 0x00000097) @ 0x3ff30000
[    0.000000] ACPI: FADT (v002 INTEL  D865GBF  0x20050804 MSFT 0x00000097) @ 0x3ff30200
[    0.000000] ACPI: MADT (v001 INTEL  D865GBF  0x20050804 MSFT 0x00000097) @ 0x3ff30300
[    0.000000] ACPI: ASF! (v016 LEGEND I865PASF 0x00000001 MSFT 0x0100000d) @ 0x3ff34680
[    0.000000] ACPI: TCPA (v001 INTEL  TBLOEMID 0x00000001 MSFT 0x00000097) @ 0x3ff34719
[    0.000000] ACPI: WDDT (v001 INTEL  OEMWDDT  0x00000001 MSFT 0x0100000d) @ 0x3ff3474d
[    0.000000] ACPI: DSDT (v001 INTEL  D865GBF  0x00000001 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID:  Product ID: Springdale-G APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 32 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:becf0000)
[    0.000000] Detected 2992.806 MHz processor.
[   17.597850] Built 1 zonelists.  Total pages: 259889
[   17.597852] Kernel command line: root=UUID=d9a7b03e-39ac-479a-8f75-960a48e63a0a ro quiet splash pci=noacpi
[   17.598019] mapped APIC to ffffd000 (fee00000)
[   17.598021] mapped IOAPIC to ffffc000 (fec00000)
[   17.598025] Enabling fast FPU save and restore... done.
[   17.598027] Enabling unmasked SIMD FPU exception support... done.
[   17.598037] Initializing CPU#0
[   17.598104] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   17.599392] Console: colour VGA+ 80x25
[   17.599856] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.600280] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.619078] Memory: 1026424k/1047740k available (1916k kernel code, 20560k reserved, 864k data, 328k init, 130236k highmem)
[   17.619088] virtual kernel memory layout:
[   17.619089]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[   17.619091]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.619092]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.619093]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.619094]       .init : 0xc03ba000 - 0xc040c000   ( 328 kB)
[   17.619095]       .data : 0xc02df353 - 0xc03b7434   ( 864 kB)
[   17.619096]       .text : 0xc0100000 - 0xc02df353   (1916 kB)
[   17.619099] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.698058] Calibrating delay using timer specific routine.. 5989.17 BogoMIPS (lpj=11978346)
[   17.698092] Security Framework v1.0.0 initialized
[   17.698100] SELinux:  Disabled at boot.
[   17.698110] Mount-cache hash table entries: 512
[   17.698219] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   17.698226] monitor/mwait feature present.
[   17.698228] using mwait in idle threads.
[   17.698234] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   17.698237] CPU: L2 cache: 1024K
[   17.698239] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   17.698250] Compat vDSO mapped to ffffe000.
[   17.698254] Remapping vsyscall page to ffffe000
[   17.698266] CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   17.698273] Checking 'hlt' instruction... OK.
[   17.714459] Early unpacking initramfs... done
[   18.039809] ACPI: Core revision 20060707
[   18.040554] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.042807] ExtINT not setup in hardware but reported by MP table
[   18.042880] ENABLING IO-APIC IRQs
[   18.043061] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   18.189992] Booting paravirtualized kernel on bare hardware
[   18.190054] Time: 12:45:53  Date: 04/16/107
[   18.190075] NET: Registered protocol family 16
[   18.190145] EISA bus registered
[   18.190149] ACPI: bus type pci registered
[   18.191450] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[   18.191452] PCI: Using configuration type 1
[   18.191454] Setting up standard PCI resources
[   18.206329] ACPI: Interpreter enabled
[   18.206331] ACPI: Using PIC for interrupt routing
[   18.210586] ACPI: Power Resource [URP1] (off)
[   18.210651] ACPI: Power Resource [FDDP] (off)
[   18.210714] ACPI: Power Resource [LPTP] (off)
[   18.212982] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.212990] pnp: PnP ACPI init
[   18.216858] pnp: PnP ACPI: found 14 devices
[   18.216863] PnPBIOS: Disabled by ACPI PNP
[   18.216900] PCI: Probing PCI hardware
[   18.216909] PCI: Probing PCI hardware (bus 00)
[   18.217442] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   18.217446] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   18.217671] Boot video device is 0000:01:00.0
[   18.217878] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   18.217935] PCI: Transparent bridge - 0000:00:1e.0
[   18.219405] PCI: Using IRQ router PIIX/ICH [8086/24d0] at 0000:00:1f.0
[   18.219414] PCI->APIC IRQ transform: 0000:00:1d.0[A] -> IRQ 16
[   18.219417] PCI->APIC IRQ transform: 0000:00:1d.1[B] -> IRQ 19
[   18.219421] PCI->APIC IRQ transform: 0000:00:1d.2[C] -> IRQ 18
[   18.219424] PCI->APIC IRQ transform: 0000:00:1d.3[A] -> IRQ 16
[   18.219427] PCI->APIC IRQ transform: 0000:00:1d.7[D] -> IRQ 23
[   18.219433] PCI->APIC IRQ transform: 0000:00:1f.1[A] -> IRQ 18
[   18.219436] PCI->APIC IRQ transform: 0000:00:1f.2[A] -> IRQ 18
[   18.219439] PCI->APIC IRQ transform: 0000:00:1f.3[B] -> IRQ 17
[   18.219442] PCI->APIC IRQ transform: 0000:00:1f.5[B] -> IRQ 17
[   18.219445] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16
[   18.219448] PCI->APIC IRQ transform: 0000:02:01.0[A] -> IRQ 22
[   18.219451] PCI->APIC IRQ transform: 0000:02:01.1[A] -> IRQ 22
[   18.219454] PCI->APIC IRQ transform: 0000:02:08.0[A] -> IRQ 20
[   18.223843] NET: Registered protocol family 8
[   18.223846] NET: Registered protocol family 20
[   18.224945] pnp: 00:0c: ioport range 0x400-0x47f could not be reserved
[   18.224948] pnp: 00:0c: ioport range 0x680-0x6ff has been reserved
[   18.224951] pnp: 00:0c: ioport range 0x500-0x53f has been reserved
[   18.225215] PCI: Bridge: 0000:00:01.0
[   18.225217]   IO window: disabled.
[   18.225222]   MEM window: fc900000-fe9fffff
[   18.225225]   PREFETCH window: bc700000-dc6fffff
[   18.225230] PCI: Bridge: 0000:00:1e.0
[   18.225233]   IO window: b000-bfff
[   18.225238]   MEM window: fea00000-feafffff
[   18.225241]   PREFETCH window: dc700000-dc7fffff
[   18.225258] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.225276] NET: Registered protocol family 2
[   18.261818] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.261956] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   18.262235] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   18.262380] TCP: Hash tables configured (established 131072 bind 65536)
[   18.262383] TCP reno registered
[   18.273900] checking if image is initramfs... it is
[   18.896809] Freeing initrd memory: 8057k freed
[   18.897224] audit: initializing netlink socket (disabled)
[   18.897239] audit(1179319553.376:1): initialized
[   18.897301] highmem bounce pool size: 64 pages
[   18.897348] VFS: Disk quotas dquot_6.5.1
[   18.897364] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.897413] io scheduler noop registered
[   18.897416] io scheduler anticipatory registered
[   18.897418] io scheduler deadline registered
[   18.897425] io scheduler cfq registered (default)
[   26.893509] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   26.893769] isapnp: Scanning for PnP cards...
[   27.245488] isapnp: No Plug & Play device found
[   27.268279] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.268382] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.269069] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.269263] mice: PS/2 mouse device common for all mice
[   27.269754] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.269887] input: Macintosh mouse button emulation as /class/input/input0
[   27.269921] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.269925] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.270141] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   27.273065] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.273069] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.273168] EISA: Probing bus 0 at eisa.0
[   27.273203] EISA: Detected 0 cards.
[   27.303266] TCP cubic registered
[   27.303272] NET: Registered protocol family 1
[   27.303290] Using IPI Shortcut mode
[   27.303346] ACPI: (supports S0 S1 S4 S5)
[   27.303385]   Magic number: 7:702:784
[   27.303473]   hash matches device ptyq6
[   27.303735] Freeing unused kernel memory: 328k freed
[   27.305305] Time: tsc clocksource has been installed.
[   27.348654] input: AT Translated Set 2 keyboard as /class/input/input1
[   28.507512] Capability LSM initialized
[   28.522425] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   28.549836] ACPI: Processor [CPU1] (supports 8 throttling states)
[   28.610114] md: linear personality registered for level -1
[   28.613407] md: multipath personality registered for level -4
[   28.616451] md: raid0 personality registered for level 0
[   28.620044] md: raid1 personality registered for level 1
[   28.622985] raid5: automatically using best checksumming function: pIII_sse
[   28.640649]    pIII_sse  :  4537.000 MB/sec
[   28.640652] raid5: using function: pIII_sse (4537.000 MB/sec)
[   28.724627] raid6: int32x1    715 MB/s
[   28.792623] raid6: int32x2    857 MB/s
[   28.860552] raid6: int32x4    704 MB/s
[   28.928557] raid6: int32x8    554 MB/s
[   28.996471] raid6: mmxx1     1802 MB/s
[   29.064440] raid6: mmxx2     2116 MB/s
[   29.132449] raid6: sse1x1    1060 MB/s
[   29.200379] raid6: sse1x2    2095 MB/s
[   29.268355] raid6: sse2x1    2166 MB/s
[   29.336318] raid6: sse2x2    3172 MB/s
[   29.336320] raid6: using algorithm sse2x2 (3172 MB/s)
[   29.336323] md: raid6 personality registered for level 6
[   29.336325] md: raid5 personality registered for level 5
[   29.336327] md: raid4 personality registered for level 4
[   29.370997] md: raid10 personality registered for level 10
[   29.694909] usbcore: registered new interface driver usbfs
[   29.694932] usbcore: registered new interface driver hub
[   29.694953] usbcore: registered new device driver usb
[   29.695727] USB Universal Host Controller Interface driver v3.0
[   29.695775] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.695778] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.695891] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   29.695914] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[   29.696010] usb usb1: configuration #1 chosen from 1 choice
[   29.696034] hub 1-0:1.0: USB hub found
[   29.696041] hub 1-0:1.0: 2 ports detected
[   29.780040] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   29.780044] e100: Copyright(c) 1999-2006 Intel Corporation
[   29.796230] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.796235] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.796257] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   29.796283] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[   29.796372] usb usb2: configuration #1 chosen from 1 choice
[   29.796399] hub 2-0:1.0: USB hub found
[   29.796406] hub 2-0:1.0: 2 ports detected
[   29.874325] Floppy drive(s): fd0 is 1.44M
[   29.900159] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.900165] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.900186] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   29.900211] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   29.900300] usb usb3: configuration #1 chosen from 1 choice
[   29.900327] hub 3-0:1.0: USB hub found
[   29.900333] hub 3-0:1.0: 2 ports detected
[   29.913995] FDC 0 is a National Semiconductor PC87306
[   30.004101] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   30.004106] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   30.004129] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   30.004153] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[   30.004242] usb usb4: configuration #1 chosen from 1 choice
[   30.004268] hub 4-0:1.0: USB hub found
[   30.004275] hub 4-0:1.0: 2 ports detected
[   30.108915] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   30.108920] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   30.108947] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   30.108981] ehci_hcd 0000:00:1d.7: debug port 1
[   30.108987] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   30.108996] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00
[   30.112865] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.112942] usb usb5: configuration #1 chosen from 1 choice
[   30.112968] hub 5-0:1.0: USB hub found
[   30.112976] hub 5-0:1.0: 8 ports detected
[   30.221826] SCSI subsystem initialized
[   30.227164] libata version 2.20 loaded.
[   30.230429] ata_piix 0000:00:1f.1: version 2.10ac1
[   30.230442] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   30.230461] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.230503] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   30.230534] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   30.230553] scsi0 : ata_piix
[   30.556066] ata1.00: ata_hpa_resize 1: sectors = 80293248, hpa_sectors = 80293248
[   30.556071] ata1.00: ATA-7: Maxtor 6E040L0, NAR61EA0, max UDMA/133
[   30.556074] ata1.00: 80293248 sectors, multi 16: LBA 
[   30.556076] ata1.01: ATAPI, max UDMA/33
[   30.564060] ata1.00: ata_hpa_resize 1: sectors = 80293248, hpa_sectors = 80293248
[   30.564063] ata1.00: configured for UDMA/133
[   30.635661] usb 5-4: new high speed USB device using ehci_hcd and address 2
[   30.727800] ata1.01: configured for UDMA/33
[   30.727811] scsi1 : ata_piix
[   30.891849] ata2.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[   30.891853] ata2.00: ATA-7: SAMSUNG HD300LD, WK100-12, max UDMA/100
[   30.891856] ata2.00: 586072368 sectors, multi 16: LBA48 
[   30.899840] ata2.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[   30.899843] ata2.00: configured for UDMA/100
[   30.899944] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[   30.900603] scsi 0:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4520B 1.00 PQ: 0 ANSI: 5
[   30.900920] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD300LD  WK10 PQ: 0 ANSI: 5
[   30.901172] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   30.901202] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   30.901232] ata3: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e802 bmdma 0x0001dc00 irq 18
[   30.901256] ata4: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x0001dc08 irq 18
[   30.901266] scsi2 : ata_piix
[   30.906636] usb 5-4: configuration #1 chosen from 1 choice
[   31.065590] ATA: abnormal status 0x7F on port 0x0001ec07
[   31.065610] scsi3 : ata_piix
[   31.229509] ATA: abnormal status 0x7F on port 0x0001e407
[   31.248757] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:13:20:21:6A:9F
[   31.262059] SCSI device sda: 80293248 512-byte hdwr sectors (41110 MB)
[   31.262076] sda: Write Protect is off
[   31.262078] sda: Mode Sense: 00 3a 00 00
[   31.262093] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.262146] SCSI device sda: 80293248 512-byte hdwr sectors (41110 MB)
[   31.262154] sda: Write Protect is off
[   31.262157] sda: Mode Sense: 00 3a 00 00
[   31.262169] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.262174]  sda: sda1
[   31.271311] sd 0:0:0:0: Attached scsi disk sda
[   31.271536] SCSI device sdb: 586072368 512-byte hdwr sectors (300069 MB)
[   31.271547] sdb: Write Protect is off
[   31.271549] sdb: Mode Sense: 00 3a 00 00
[   31.271564] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.271602] SCSI device sdb: 586072368 512-byte hdwr sectors (300069 MB)
[   31.271611] sdb: Write Protect is off
[   31.271613] sdb: Mode Sense: 00 3a 00 00
[   31.271625] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.271725]  sdb:sr0: scsi3-mmc drive: 6x/6x writer cd/rw xa/form2 cdda tray
[   31.272549] Uniform CD-ROM driver Revision: 3.20
[   31.272655] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   31.279218]  sdb1 sdb2 sdb3 < sdb5 >
[   31.298777] sd 1:0:0:0: Attached scsi disk sdb
[   31.302980] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.303082] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   31.303177] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   31.363308] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   31.527418] kjournald starting.  Commit interval 5 seconds
[   31.527428] EXT3-fs: mounted filesystem with ordered data mode.
[   31.791984] usb 4-1: configuration #1 chosen from 1 choice
[   46.694121] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.698066] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.893054] iTCO_vendor_support: vendor-support=0
[   46.894357] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   46.894445] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   46.894482] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   46.918037] intel_rng: Firmware space is locked read-only. If you can't or
[   46.918040] intel_rng: don't want to disable this in firmware setup, and if
[   46.918041] intel_rng: you are certain that your system has a functional
[   46.918043] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   47.118660] Linux agpgart interface v0.102 (c) Dave Jones
[   47.282789] agpgart: Detected an Intel 865 Chipset.
[   47.292891] agpgart: AGP aperture is 256M @ 0xe0000000
[   47.758706] Bluetooth: Core ver 2.11
[   47.758764] NET: Registered protocol family 31
[   47.758766] Bluetooth: HCI device and connection manager initialized
[   47.758769] Bluetooth: HCI socket layer initialized
[   47.776710] Real Time Clock Driver v1.12ac
[   47.788947] Linux video capture interface: v2.00
[   47.825118] bttv: driver version 0.9.16 loaded
[   47.825123] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   47.825173] bttv: Bt8xx card found (0).
[   47.825200] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 22, latency: 32, mmio: 0xdc7fe000
[   47.825209] bttv0: detected: Prolink Pixelview PV-BT [card=72], PCI subsystem ID is 1554:4011
[   47.825212] bttv0: using: Prolink PixelView PlayTV MPEG2 PV-M4900 [card=139,insmod option]
[   47.825239] bttv0: gpio: en=00000000, out=00000000 in=006fc0ff [init]
[   47.825256] i2c-algo-bit.o: (0) scl=1, sda=1
[   47.825264] i2c-algo-bit.o: (1) scl=1, sda=0
[   47.825272] i2c-algo-bit.o: (2) scl=1, sda=1
[   47.825280] i2c-algo-bit.o: (3) scl=0, sda=1
[   47.825289] i2c-algo-bit.o: (4) scl=1, sda=1
[   47.825291] i2c-algo-bit.o: bt878 #0 [sw] passed test.
[   47.825737] bttv0: using tuner=5
[   47.825740] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   47.826461] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   47.827198] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   47.858399] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   47.858427] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   47.858431] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   47.859413] tuner 0-0063: chip found @ 0xc6 (bt878 #0 [sw])
[   47.868351] bttv0: registered device video0
[   47.868382] bttv0: registered device vbi0
[   47.868412] bttv0: registered device radio0
[   47.868431] bttv0: PLL: 28636363 => 35468950 .<6>Bluetooth: HCI USB driver ver 2.9
[   47.897366] . ok
[   47.912029] input: bttv IR (card=139) as /class/input/input2
[   47.915924] input: PC Speaker as /class/input/input3
[   47.966434] usbcore: registered new interface driver hci_usb
[   48.053134] rtusb init ====>
[   48.105947] bt878: AUDIO driver version 0.0.0 loaded
[   48.105986] bt878: Bt878 AUDIO function found (0).
[   48.106007] bt878_probe: card id=[0x40111554], Unknown card.
[   48.106008] Exiting..
[   48.106015] bt878: probe of 0000:02:01.1 failed with error -22
[   48.108433] parport: PnPBIOS parport detected.
[   48.108482] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   48.135161] idVendor = 0x7d1, idProduct = 0x3c03 
[   48.442422] input: ImPS/2 Generic Wheel Mouse as /class/input/input4
[   49.041012] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   49.098237] usbcore: registered new interface driver rt73
[   49.105099] rt73 driver version - 1.0.3.6 CVS
[   49.262967] ***rt73***: Interface goes up for the first time, activating permanent MAC
[   49.262972] ***rt73***: Active MAC is: 00:15:e9:4b:44:d1.
[   49.358397] intel8x0_measure_ac97_clock: measured 55233 usecs
[   49.358402] intel8x0: clocking to 48000
[   49.525678] Intel ISA PCIC probe: not found.
[   49.586390] lp0: using parport0 (interrupt-driven).
[   49.698559] Adding 168640k swap on /dev/disk/by-uuid/7eb0399d-6bf2-47d6-9555-dbb7cad5babd.  Priority:-1 extents:1 across:168640k
[   49.809672] EXT3 FS on sdb2, internal journal
[   50.495937] NET: Registered protocol family 17
[   50.983264] cdrom: sr0: mrw address space DMA selected
[   51.556350] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   51.598254] NTFS volume version 3.1.
[   51.625317] NTFS volume version 3.1.
[   51.673843] Adding 168640k swap on /dev/disk/by-uuid/7eb0399d-6bf2-47d6-9555-dbb7cad5babd.  Priority:-2 extents:1 across:168640k
[   52.522996] input: Power Button (FF) as /class/input/input5
[   52.526594] ACPI: Power Button (FF) [PWRF]
[   52.559502] input: Sleep Button (CM) as /class/input/input6
[   52.563135] ACPI: Sleep Button (CM) [SLPB]
[   52.578672] Using specific hotkey driver
[   52.610825] No dock devices found.
[   52.645980] ibm_acpi: ec object not found
[   52.768664] pcc_acpi: loading...
[   57.880531] ppdev: user-space parallel port driver
[   58.835186] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   58.835191] apm: overridden by ACPI.
[   65.103288] vmmon: module license 'unspecified' taints kernel.
[   65.108953] /dev/vmmon[5305]: Module vmmon: registered with major=10 minor=165
[   65.109194] /dev/vmmon[5305]: Module vmmon: initialized
[   65.485367] /dev/vmnet: open called by PID 5335 (vmnet-bridge)
[   65.485589] /dev/vmnet: hub 0 does not exist, allocating memory.
[   65.485743] /dev/vmnet: port on hub 0 successfully opened
[   65.485868] bridge-eth0: peer interface eth0 not found, will wait for it to come up
[   65.486004] bridge-eth0: attached
[   65.598614] /dev/vmnet: open called by PID 5350 (vmnet-netifup)
[   65.598830] /dev/vmnet: hub 1 does not exist, allocating memory.
[   65.598958] /dev/vmnet: port on hub 1 successfully opened
[   65.601706] /dev/vmnet: open called by PID 5351 (vmnet-netifup)
[   65.601906] /dev/vmnet: hub 8 does not exist, allocating memory.
[   65.602034] /dev/vmnet: port on hub 8 successfully opened
[   65.749773] /dev/vmnet: open called by PID 5349 (vmnet-natd)
[   65.749945] /dev/vmnet: port on hub 8 successfully opened
[   65.792550] /dev/vmnet: open called by PID 5371 (vmnet-dhcpd)
[   65.792706] /dev/vmnet: port on hub 8 successfully opened
[   65.909517] /dev/vmnet: open called by PID 5373 (vmnet-dhcpd)
[   65.909673] /dev/vmnet: port on hub 1 successfully opened
[   66.779191] NET: Registered protocol family 10
[   66.779265] lo: Disabled Privacy Extensions
[   71.531056] Bluetooth: L2CAP ver 2.8
[   71.531060] Bluetooth: L2CAP socket layer initialized
[   71.618507] Bluetooth: RFCOMM socket layer initialized
[   71.618520] Bluetooth: RFCOMM TTY layer initialized
[   71.618522] Bluetooth: RFCOMM ver 1.8
[   77.408510] vmnet1: no IPv6 routers present
[   77.448489] wlan0: no IPv6 routers present
[   77.688370] vmnet8: no IPv6 routers present
[   96.154251] cdrom: sr0: mrw address space DMA selected
[   96.234712] cdrom: sr0: mrw address space DMA selected
[   96.446499] ISO 9660 Extensions: Microsoft Joliet Level 3
[   96.493369] ISOFS: changing to secondary root
[  222.569751] rt73 driver version - 1.0.3.6 CVS
[  222.731572] ***rt73***: net_device supplies MAC, activating this one
[  222.731579] ***rt73***: Active MAC is: 00:15:e9:4b:44:d1.
[  233.123449] wlan0: no IPv6 routers present


```


Any help will be greatly appreciated.

:popcorn:

---

### Post by psavva on 2007-05-17
Some Help,

anybody...

Please...

You're So Kind :D

---

### Post by psavva on 2007-05-24
To whom ever it may concern

Hi, I would like help with my BTTV Tv tuner Card 
as you can see in the psst above...

I really want to get this card working....
PLEZZZZZZZ anybody

Kind Regards
:p

---

