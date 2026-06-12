---
title: "No Sound on either 6.10 or 7.04 (New to Linux)"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by chewjoel on 2007-05-13
I'd installed Ubuntu 7.04 few days ago, everything works quite well except that my soundcard is not working.  After searching around for solutions and tried out each of them given, it still not working.  (Maybe I made some mistake as I'm still very new in Linux, hence there's loads of things I can't really understand.)  So I decided to install Ubuntu 6.10 instead to try if it works.
Still the sound is not working.  Though there is warning / alert beep from the system, but no sound at all otherwise.  

Right clicked on Volume Control for 'Open Volume Control', error message shows up: No volume control GStreamer plugins and/devices found

This is the output of dmesg:

joelle-birta@birta-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000002f740000 (usable)
[17179569.184000]  BIOS-e820: 000000002f740000 - 000000002f750000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000002f750000 - 000000002f800000 (ACPI NVS)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 759MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 194368
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 190272 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 2f800000:d0800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
[17179569.184000] Found and enabled local APIC!
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1300.262 MHz processor.
[   10.381911] Using tsc for high-res timesource
[   10.383432] Console: colour VGA+ 80x25
[   10.383916] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.384525] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.411432] Memory: 760680k/777472k available (1910k kernel code, 16220k reserved, 1070k data, 308k init, 0k highmem)
[   10.411437] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.489748] Calibrating delay using timer specific routine.. 2603.60 BogoMIPS (lpj=5207206)
[   10.489802] Security Framework v1.0.0 initialized
[   10.489811] SELinux:  Disabled at boot.
[   10.489832] Mount-cache hash table entries: 512
[   10.489997] CPU: After generic identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[   10.490009] CPU: After vendor identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[   10.490021] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.490025] CPU: L2 cache: 1024K
[   10.490028] CPU: After all inits, caps: a7e9fbbf 00000000 00000000 00000040 00000180 00000000 00000000
[   10.490048] Checking 'hlt' instruction... OK.
[   10.505811] SMP alternatives: switching to UP code
[   10.505956] Freeing SMP alternatives: 16k freed
[   10.506105] checking if image is initramfs... it is
[   11.227030] Freeing initrd memory: 5563k freed
[   11.227041] CPU0: Intel(R) Pentium(R) M processor 1300MHz stepping 05
[   11.227050] SMP motherboard not detected.
[   11.333199] Brought up 1 CPUs
[   11.333223] migration_cost=0
[   11.333645] NET: Registered protocol family 16
[   11.333685] EISA bus registered
[   11.334384] PCI: Using configuration type 1
[   11.334387] Setting up standard PCI resources
[   11.342228] ACPI: Interpreter disabled.
[   11.342233] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.342244] pnp: PnP ACPI: disabled
[   11.342249] PnPBIOS: Scanning system for PnP BIOS support...
[   11.342256] PnPBIOS: Found PnP BIOS installation structure at 0xc00f2e10
[   11.342261] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x39ea, dseg 0xf0000
[   11.342825] PnPBIOS: Unknown tag '0x0', length '1'.
[   11.342871] PnPBIOS: Unknown tag '0x8', length '7'.
[   11.342910] PnPBIOS: Unknown tag '0x8', length '7'.
[   11.342949] PnPBIOS: Resource structure does not contain an end tag.
[   11.343171] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   11.343222] PCI: Probing PCI hardware
[   11.343227] PCI: Probing PCI hardware (bus 00)
[   11.343390] Boot video device is 0000:00:02.0
[   11.343728] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   11.343733] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   11.343782] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[   11.344166] PCI: Transparent bridge - 0000:00:1e.0
[   11.344230] PCI: Bus #02 (-#05) is hidden behind transparent bridge #01 (-#01) (try 'pci=assign-busses')
[   11.344234] Please report the result to linux-kernel to fix this permanently
[   11.344277] PCI: Bus #06 (-#09) is hidden behind transparent bridge #01 (-#01) (try 'pci=assign-busses')
[   11.344280] Please report the result to linux-kernel to fix this permanently
[   11.345129] PCI: Using IRQ router default [8086/24cc] at 0000:00:1f.0
[   11.345281] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   11.345285] pnp: 00:0a: ioport range 0xcf8-0xcff could not be reserved
[   11.345520] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   11.345547] PCI: Bus 2, cardbus bridge: 0000:01:03.0
[   11.345550]   IO window: 0000c000-0000c0ff
[   11.345554]   IO window: 0000c400-0000c4ff
[   11.345559]   PREFETCH window: 32000000-33ffffff
[   11.345564]   MEM window: 34000000-35ffffff
[   11.345569] PCI: Bus 6, cardbus bridge: 0000:01:03.1
[   11.345572]   IO window: 0000cc00-0000ccff
[   11.345576]   IO window: 00001000-000010ff
[   11.345581]   PREFETCH window: 36000000-37ffffff
[   11.345586]   MEM window: 38000000-39ffffff
[   11.345591] PCI: Bridge: 0000:00:1e.0
[   11.345594]   IO window: c000-cfff
[   11.345600]   MEM window: ff700000-ff7fffff
[   11.345605]   PREFETCH window: dea00000-deafffff
[   11.345620] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.345634] PCI: No IRQ known for interrupt pin A of device 0000:01:03.0. Please try using pci=biosirq.
[   11.345649] PCI: No IRQ known for interrupt pin B of device 0000:01:03.1. Please try using pci=biosirq.
[   11.345655] PCI: Setting latency timer of device 0000:01:03.1 to 64
[   11.345683] NET: Registered protocol family 2
[   11.373130] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.373287] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.375078] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.376211] TCP: Hash tables configured (established 131072 bind 65536)
[   11.376217] TCP reno registered
[   11.377179] audit: initializing netlink socket (disabled)
[   11.377199] audit(1179025879.080:1): initialized
[   11.377379] VFS: Disk quotas dquot_6.5.1
[   11.377407] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.377477] Initializing Cryptographic API
[   11.377484] io scheduler noop registered
[   11.377493] io scheduler anticipatory registered
[   11.377501] io scheduler deadline registered
[   11.377521] io scheduler cfq registered (default)
[   19.406634] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   19.407032] isapnp: Scanning for PnP cards...
[   19.762294] isapnp: No Plug & Play device found
[   19.794612] Real Time Clock Driver v1.12ac
[   19.794690] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.794923] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[   19.795613] PCI: No IRQ known for interrupt pin B of device 0000:00:1f.6. Please try using pci=biosirq.
[   19.795685] mice: PS/2 mouse device common for all mice
[   19.796340] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.796616] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.796621] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.796873] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   19.798947] i8042.c: Detected active multiplexing controller, rev 1.1.
[   19.800246] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   19.800411] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   19.800623] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   19.800784] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   19.800995] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.801341] EISA: Probing bus 0 at eisa.0
[   19.801351] Cannot allocate resource for EISA slot 1
[   19.801380] EISA: Detected 0 cards.
[   19.801692] TCP bic registered
[   19.801707] NET: Registered protocol family 1
[   19.801715] NET: Registered protocol family 8
[   19.801718] NET: Registered protocol family 20
[   19.801749] Using IPI No-Shortcut mode
[   19.801984] Freeing unused kernel memory: 308k freed
[   19.959673] input: AT Translated Set 2 keyboard as /class/input/input0
[   20.945896] Capability LSM initialized
[   21.332717] ICH4: IDE controller at PCI slot 0000:00:1f.1
[   21.332729] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   21.332747] ICH4: chipset revision 3
[   21.332750] ICH4: not 100% native mode: will probe irqs later
[   21.332761]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   21.332775]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[   21.332786] Probing IDE interface ide0...
[   21.625002] hda: IC25N020ATCS04-0, ATA DISK drive
[   22.300584] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   22.300746] Probing IDE interface ide1...
[   23.039861] hdc: TOSHIBA DVD-ROM SD-C2612, ATAPI CD/DVD-ROM drive
[   23.733163] ide1 at 0x170-0x177,0x376 on irq 15
[   23.740272] hda: max request size: 128KiB
[   23.758252] hda: 39070080 sectors (20003 MB) w/1768KiB Cache, CHS=38760/16/63, UDMA(100)
[   23.758262] hda: cache flushes not supported
[   23.758317]  hda: hda1 hda2 < hda5 >
[   23.825713] hdc: ATAPI 24X DVD-ROM drive, 192kB Cache, UDMA(33)
[   23.825724] Uniform CD-ROM driver Revision: 3.20
[   24.003684] usbcore: registered new driver usbfs
[   24.003710] usbcore: registered new driver hub
[   24.005303] USB Universal Host Controller Interface driver v3.0
[   24.005363] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.005368] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.005530] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   24.005555] uhci_hcd 0000:00:1d.0: irq 5, io base 0x0000d480
[   24.005651] usb usb1: configuration #1 chosen from 1 choice
[   24.005676] hub 1-0:1.0: USB hub found
[   24.005683] hub 1-0:1.0: 2 ports detected
[   24.087347] ieee1394: Initialized config rom entry `ip1394'
[   24.111134] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   24.111141] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   24.111273] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   24.111300] uhci_hcd 0000:00:1d.1: irq 5, io base 0x0000d800
[   24.111494] usb usb2: configuration #1 chosen from 1 choice
[   24.111628] hub 2-0:1.0: USB hub found
[   24.111635] hub 2-0:1.0: 2 ports detected
[   24.218954] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   24.218959] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   24.219090] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   24.219110] uhci_hcd 0000:00:1d.2: irq 5, io base 0x0000d880
[   24.219296] usb usb3: configuration #1 chosen from 1 choice
[   24.219428] hub 3-0:1.0: USB hub found
[   24.219435] hub 3-0:1.0: 2 ports detected
[   24.338872] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.338880] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.338933] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   24.338970] ehci_hcd 0000:00:1d.7: debug port 1
[   24.338977] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.338990] ehci_hcd 0000:00:1d.7: irq 4, io mem 0xffa7fc00
[   24.342877] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.354719] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   24.364660] usb usb4: configuration #1 chosen from 1 choice
[   24.364697] hub 4-0:1.0: USB hub found
[   24.364706] hub 4-0:1.0: 6 ports detected
[   24.534962] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[5]  MMIO=[ff7ef000-ff7ef7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   24.594324] Attempting manual resume
[   24.626431] kjournald starting.  Commit interval 5 seconds
[   24.626444] EXT3-fs: mounted filesystem with ordered data mode.
[   25.110076] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   25.293363] usb 1-1: configuration #1 chosen from 1 choice
[   25.817731] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800030b6439]
[   39.019330] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.111448] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.142573] hw_random: RNG not detected
[   39.430578] Linux agpgart interface v0.101 (c) Dave Jones
[   39.436858] agpgart: Detected an Intel 855 Chipset.
[   39.437196] agpgart: Detected 8060K stolen memory.
[   39.446084] agpgart: AGP aperture is 128M @ 0xf0000000
[   40.052804] PCI: No IRQ known for interrupt pin A of device 0000:01:03.0. Please try using pci=biosirq.
[   40.052817] Yenta: CardBus bridge found at 0000:01:03.0 [1043:1754]
[   40.052834] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   40.052836] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   40.182705] Yenta: ISA IRQ mask 0x0e88, PCI irq 0
[   40.182711] Socket status: 30000006
[   40.182715] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   40.182723] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   40.182727] cs: IO port probe 0xc000-0xcfff: clean.
[   40.183012] pcmcia: parent PCI bridge Memory window: 0xff700000 - 0xff7fffff
[   40.183017] pcmcia: parent PCI bridge Memory window: 0xdea00000 - 0xdeafffff
[   40.183212] PCI: No IRQ known for interrupt pin B of device 0000:01:03.1. Please try using pci=biosirq.
[   40.183230] Yenta: CardBus bridge found at 0000:01:03.1 [1043:1754]
[   40.183246] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   40.183248] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   40.318285] Yenta: ISA IRQ mask 0x0e88, PCI irq 0
[   40.318291] Socket status: 30000006
[   40.318294] Yenta: Raising subordinate bus# of parent bus (#01) from #05 to #09
[   40.318302] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   40.318306] cs: IO port probe 0xc000-0xcfff: clean.
[   40.318597] pcmcia: parent PCI bridge Memory window: 0xff700000 - 0xff7fffff
[   40.318601] pcmcia: parent PCI bridge Memory window: 0xdea00000 - 0xdeafffff
[   40.524668] Floppy drive(s): fd0 is 1.44M
[   40.544890] FDC 0 is a National Semiconductor PC87306
[   40.598857] input: PC Speaker as /class/input/input1
[   40.861961] irda_init()
[   40.861975] NET: Registered protocol family 23
[   41.094797] PCI: Enabling device 0000:00:1f.5 (0005 -> 0007)
[   41.094808] PCI: No IRQ known for interrupt pin B of device 0000:00:1f.5. Please try using pci=biosirq.
[   41.094828] setup_irq: irq handler mismatch
[   41.094839]  <c01497d7> setup_irq+0x127/0x140  <f02cfcb0> snd_intel8x0_interrupt+0x0/0x210 [snd_intel8x0]
[   41.094860]  <c0149889> request_irq+0x99/0xb0  <f02d101e> snd_intel8x0_probe+0x48e/0x1160 [snd_intel8x0]
[   41.094877]  <c011aa69> __wake_up_common+0x39/0x60  <c011cdf8> __wake_up+0x38/0x50
[   41.094896]  <c0286288> netlink_broadcast+0x208/0x320  <c01edc33> pci_match_device+0x13/0xe0
[   41.094912]  <c01edd76> pci_device_probe+0x56/0x80  <c0245f44> driver_probe_device+0x44/0xc0
[   41.094927]  <c02460c2> __driver_attach+0x82/0x90  <c02458bb> bus_for_each_dev+0x3b/0x60
[   41.094940]  <c0245e86> driver_attach+0x16/0x20  <c0246040> __driver_attach+0x0/0x90
[   41.094948]  <c024552c> bus_add_driver+0x8c/0x140  <c02462f1> driver_register+0x41/0xa0
[   41.094960]  <c01edf17> __pci_register_driver+0x47/0x70  <c013cda8> sys_init_module+0x148/0x19c0
[   41.094984]  <c012bfb0> msleep+0x0/0x30  <c0102fbb> sysenter_past_esp+0x54/0x79
[   41.095007] unable to grab IRQ 0
[   41.095026] Intel ICH: probe of 0000:00:1f.5 failed with error -16
[   41.129615] parport: PnPBIOS parport detected.
[   41.129717] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   41.164570] ieee80211_crypt: registered algorithm 'NULL'
[   41.168419] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   41.168424] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   41.230983] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   41.230989] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   41.231533] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   41.260575] Synaptics Touchpad, model: 1, fw: 4.6, id: 0x925ea1, caps: 0x80471b/0x0
[   41.301237] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   41.303933] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   41.303958] nsc-ircc, chip->init
[   41.303967] nsc-ircc, Found chip at base=0x02e
[   41.303990] nsc-ircc, driver loaded (Dag Brattli)
[   41.303997] nsc_ircc_open(), can't get iobase of 0x2f8
[   41.304022] nsc-ircc, Found chip at base=0x02e
[   41.304045] nsc-ircc, driver loaded (Dag Brattli)
[   41.304049] nsc_ircc_open(), can't get iobase of 0x2f8
[   41.304162] pnp: Device 00:0c disabled.
[   41.328568] usbcore: registered new driver hiddev
[   41.344163] input: Logitech Optical USB Mouse as /class/input/input3
[   41.344254] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
[   41.344269] usbcore: registered new driver usbhid
[   41.344273] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   41.372463] 8139too Fast Ethernet driver 0.9.27
[   41.477549] ts: Compaq touchscreen protocol output
[   41.754281] cs: IO port probe 0x100-0x3af: clean.
[   41.755892] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[   41.756560] cs: IO port probe 0x820-0x8ff: clean.
[   41.757151] cs: IO port probe 0xc00-0xcf7: clean.
[   41.757863] cs: IO port probe 0xa00-0xaff: clean.
[   41.789720] cs: IO port probe 0x100-0x3af: clean.
[   41.791329] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[   41.791997] cs: IO port probe 0x820-0x8ff: clean.
[   41.792572] cs: IO port probe 0xc00-0xcf7: clean.
[   41.793303] cs: IO port probe 0xa00-0xaff: clean.
[   42.208864] eth1: RealTek RTL8139 at 0xf010ec00, 00:0c:6e:68:fd:a4, IRQ 5
[   42.208870] eth1:  Identified 8139 chip type 'RTL-8101'
[   42.235419] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   42.280296] eth0: link down
[   42.403133] lp0: using parport0 (interrupt-driven).
[   42.472445] SCSI subsystem initialized
[   42.486020] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   42.486025] ieee1394: sbp2: Try serialize_io=0 for better performance
[   42.512762] Adding 827308k swap on /dev/disk/by-uuid/e777f5a7-ffdf-4210-9f49-0c017aab661c.  Priority:-1 extents:1 across:827308k
[   42.613855] EXT3 FS on hda1, internal journal
[   43.366556] NET: Registered protocol family 17
[   44.177534] NET: Registered protocol family 10
[   44.177666] lo: Disabled Privacy Extensions
[   44.177789] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.177827] IPv6 over IPv4 tunneling driver
[   50.059278] [drm] Initialized drm 1.0.1 20051102
[   50.063803] [drm] Initialized i915 1.5.0 20060119 on minor 0
[   50.064974] [drm] Initialized i915 1.5.0 20060119 on minor 1
[   51.289954] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   54.470599] eth1: no IPv6 routers present
[   56.031626] ttyS1: LSR safety check engaged!
[   57.995525] Bluetooth: Core ver 2.8
[   57.995532] NET: Registered protocol family 31
[   57.995534] Bluetooth: HCI device and connection manager initialized
[   57.995560] Bluetooth: HCI socket layer initialized
[   58.023368] Bluetooth: L2CAP ver 2.8
[   58.023373] Bluetooth: L2CAP socket layer initialized
[   58.046662] Bluetooth: RFCOMM socket layer initialized
[   58.046673] Bluetooth: RFCOMM TTY layer initialized
[   58.046676] Bluetooth: RFCOMM ver 1.7

I'm using an ASUS M2400N laptop.

Any one have any idea how to fix this problem?  Thanks in advanced.

---

### Post by deadgobby on 2007-05-13
Please input this in the terminal and post back

lspci -v 


If you have like a Sound Blaster Live sound card for a example. And you are only getting sound from the boot up and the shut down. You'll need to go into your BIOS and disable the onboard sound device.

Gobby

---

### Post by chewjoel on 2007-05-13
Here's the output for lspci -v

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1751
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 175a
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 175b
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1712
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at dc00 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1712
        Flags: bus master, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at ff980000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1758
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at d480 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1758
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at d800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1758
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at d880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1759
        Flags: bus master, medium devsel, latency 0, IRQ 4
        Memory at ffa7fc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=09, sec-latency=64
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: ff700000-ff7fffff
        Prefetchable memory behind bridge: dea00000-deafffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1758
        Flags: bus master, medium devsel, latency 0
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1713
        Flags: medium devsel
        I/O ports at e000 [size=256]
        I/O ports at e100 [size=64]
        Memory at 30000400 (32-bit, non-prefetchable) [size=512]
        Memory at 30000600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1716
        Flags: medium devsel
        I/O ports at e200 [size=256]
        I/O ports at e300 [size=128]
        Capabilities: <access denied>

01:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1754
        Flags: bus master, medium devsel, latency 168
        Memory at ff700000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 32000000-33fff000 (prefetchable)
        Memory window 1: 34000000-35fff000
        I/O window 0: 0000c000-0000c0ff
        I/O window 1: 0000c400-0000c4ff
        16-bit legacy interface ports at 0001

01:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1754
        Flags: bus master, medium devsel, latency 168
        Memory at ff701000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 36000000-37fff000 (prefetchable)
        Memory window 1: 38000000-39fff000
        I/O window 0: 0000cc00-0000ccff
        I/O window 1: 00001000-000010ff
        16-bit legacy interface ports at 0001

01:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1757
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at ff7ef000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1045
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at c800 [size=256]
        Memory at ff7efc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation MIM2000/Centrino
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at ff7ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

* No sound on boot up and shutdown either.

Thanks for the help. :)

---

### Post by chewjoel on 2007-05-13
By the way, I'm using Asus M2400N laptop.
I can't find configuration for sound card in BIOS.

---

### Post by deadgobby on 2007-05-13
[COLOR="Blue"]00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
Subsystem: ASUSTeK Computer Inc. Unknown device 1713
Flags: medium devsel
I/O ports at e000 [size=256]
I/O ports at e100 [size=64]
Memory at 30000400 (32-bit, non-prefetchable) [size=512]
Memory at 30000600 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>[/COLOR]
 
 This sound card should work right away. Double click on the speaker Icon and go to edit>preferences Select 
all of the options. Put a CD in and start playing with the sliders/ volume control setting.

---

### Post by chewjoel on 2007-05-13
an error message with : no volume control Gstreamer plugins and/or devices found.

when I double clicked on the speaker icon.

---

### Post by deadgobby on 2007-05-13
If only one user account can't use the sound, check System > Admin > Users and make sure the user has audio enabled.


[http://ubuntuforums.org/showthread.php?t=411661&highlight=Gstreamer+plugins+and%2For+devices+found](http://ubuntuforums.org/showthread.php?t=411661&highlight=Gstreamer+plugins+and%2For+devices+found)

---

### Post by chewjoel on 2007-05-13
Yes, I checked on that.
the user is granted with audio privilege.

But still the problem persist.

---

### Post by deadgobby on 2007-05-13
Check in Synaptic and see if gstreamer0.10-alsa & gstreamer0.10-plugins-base are installed
gstreamer0.10-plugins (good) 
gstreamer0.10-plugins (Bad)
gstreamer0.10-plugins (Ugly)

---

### Post by deadgobby on 2007-05-13
[https://answers.launchpad.net/ubuntu/+question/1834](https://answers.launchpad.net/ubuntu/+question/1834)
[http://www.debianhelp.org/node/6352](http://www.debianhelp.org/node/6352)

I am going to bed, but check on your progress after some sleep.

---

### Post by chewjoel on 2007-05-13
gstreamer0.10-alsa  and gsreamer0.10-plugins-base
are installed.

gstreamer0.10-plugins(good) and gstreamer0.10-plugins(ugly)
are installed.

But I can't find gstreamer0.10-plugins(bad) there.

Try out the link now, would post the result here later.
Thanks a lot, sleep well. ;)

---

### Post by arkangel on 2007-05-13
stupid question ?

have you checked if you have sound with the built in speakers , or only with the headphones?

---

### Post by chewjoel on 2007-05-13
No sound with either of them.

---

### Post by arkangel on 2007-05-13
can you post a shot of alsamixer, in a terminal 
$ alsamixer

---

### Post by chewjoel on 2007-05-13
OK, here's the result: 
alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by deadgobby on 2007-05-13
Inastall ALSAmixer via synaptic or terminal. If you use gnome you can install Gnome ALSA Mixer. It is better looking.

---

### Post by chewjoel on 2007-05-13
already installed Gnome ALSA mixer

Still the output:

joelle-birta@birta-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by deadgobby on 2007-05-13
In the terminal type in 

sudo aptitude install alsamixer

---

### Post by chewjoel on 2007-05-13
Here's what I get.

joelle-birta@birta-laptop:~$ sudo aptitude install alsamixer
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find package "alsamixer".  However, the following
packages contain "alsamixer" in their name:
  gnome-alsamixer alsamixergui 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
joelle-birta@birta-laptop:~$ 

what does that means?

---

### Post by deadgobby on 2007-05-13
it means that alsamixer is not there. Go ahead and installed alsamixergui. It controls the same darn thing. After install it will be in Sound file menu.
Gobby

---

### Post by arkangel on 2007-05-13
Hi  try the following

$  sudo aptitude install alsa-base alsa-utils gstreamer0.10-alsa 

this will install alsa if not installed.

---

### Post by chewjoel on 2007-05-14
I got alsamixergui installed through synaptic.
Would try the command line you gave me later when I go home: in school now.
Would post the result here tomorrow, when I get internet access again.
Thanks a lot.

---

### Post by rase on 2007-05-14
hi,

my problem is: sound is so quiet. music is playing and other sounds too, but everything is so quiet.
master in alsamixer is o 00 position and i can not turn it up.
please help me.

---

### Post by deadgobby on 2007-05-15
right click on the speaker icon and see if it on mute? All so check if the speaker icon volume is all the way up.

---

### Post by chewjoel on 2007-05-15
Hi, finally get internet access.

Here's the output for $ sudo aptitude install alsamixer: 

joelle-birta@penguin:~$ sudo aptitude install alsamixer
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "alsamixer".  However, the following
packages contain "alsamixer" in their name:
  gnome-alsamixer alsamixergui 
The following packages have been kept back:
  apport apport-gtk capplets-data gnome-control-center gnome-panel 
  gnome-panel-data libgnome-window-settings1 libpanel-applet2-0 libslab0 
  python-apport python-problem-report rdesktop tzdata 
0 packages upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
joelle-birta@penguin:~$ sudo aptitude install alsa-base alsa-utils gstreamer0.10-alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  apport apport-gtk capplets-data gnome-control-center gnome-panel 
  gnome-panel-data libgnome-window-settings1 libpanel-applet2-0 libslab0 
  python-apport python-problem-report rdesktop tzdata 
0 packages upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
joelle-birta@penguin:~$

joelle-birta@penguin:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by chewjoel on 2007-05-15
By the way, when I open Gnome Alsa Mixer in "Sound & Video", chose 'Sound Card Properties' in edit, this error message shown:

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by deadgobby on 2007-05-15
OK You'll need to go this route then. Just try to keep it simple. Now we are going to do some mojo.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by chewjoel on 2007-05-17
Still doesn't work after following all the instructions in HdaIntelSoundHowTo. :(

---

### Post by arkangel on 2007-05-17
and with the live cd  was the same ?  maybe is blacklisted in bios 
so you have complied alsa again , is there special instruction for your card ?

by running  
sudo alsaconf

it recognizes  your card?

---

### Post by chewjoel on 2007-05-17
Yeah, even with live CD, sound is not working too.
Yes, I'd re-installed alsa as instructed in that linked-page.
ehm... special instruction for my card?

joelle-birta@penguin:~$ sudo alsaconf
sudo: alsaconf: command not found

---

### Post by chewjoel on 2007-05-17
I just realize, it could be blacklisted.
This is what I found from the blacklisted file:

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

Is there anything I can do for this?

---

### Post by arkangel on 2007-05-19
there is nothing to loose 

put a comment mark (#) at the beginning of the line and see what happens

---

### Post by chewjoel on 2007-05-20
Still the same. :(

---

### Post by Jshippee on 2008-01-10
I also have an Asus M2400N laptop and I am also having the sound card issue.  I have tried everything in every forum I can find and I have yet to make any progress at all.  Is it confirmed that this soundcard is blacklisted?  Is there nothing that can be done in order to get sound working on this laptop?  Should I try using linux by someone else or is this not going to matter?  What a drag, I was really excited about my new linux adventure, guess its going to have to wait.

---

### Post by chewjoel on 2008-01-10
I'm not sure about that.
I tried many ways but the sound card system persisted, though I read that some actually managed to get it solved.
I installed OpenSuse on the Asus after then, everything works well.

---

