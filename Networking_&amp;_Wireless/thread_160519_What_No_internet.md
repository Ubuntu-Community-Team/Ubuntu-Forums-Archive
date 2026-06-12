---
title: "What? No internet?"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by nolongerlivecd on 2006-04-15
I can get my wired ethernet to work.

However, I cannot get Intel PRO/Wireless 2200BG configured. Can anybody help me?

---

### Post by encompass on 2006-04-15
[http://doc.gwos.org/index.php/HCL]("http://doc.gwos.org/index.php/HCL")
to see if your card is supported yet...
then... look up your card in the forms... I found many links when looking for 2200bg.  It would probably help lots.
even check if it is running in ... System-- administration-- netowrking... and see you you see your card there.

---

### Post by nolongerlivecd on 2006-04-15
It appears in the networking, but I can't get it to work, as in connect to my network. It just stalls there.

---

### Post by nolongerlivecd on 2006-04-15
Can anyone tell me how to get rf_kill to 0, in terminal?

---

### Post by nolongerlivecd on 2006-04-15
Any help? The wireless rf_kill is set to 2, and I don't know how to change it.

---

### Post by encompass on 2006-04-16
Consider this programm...
> sudo apt-get install wifi-radar
It may help you get rolling... it is a simple wifi setup program... run it in terminal and see if it can find your wireless network.  It sure helps me out.:-D

---

### Post by nolongerlivecd on 2006-04-16
rf_kill is set to 2, and wifi-radar jams everything up. It was the third program I installed.

---

### Post by encompass on 2006-04-16
what is that... never heard of rf-kill... you got me lost from there... did you know you can edit previous posts as not to take up so much space to give updates?
In addition... have you tried...
> iwlist scan
and see if you see any netowrks?

---

### Post by nolongerlivecd on 2006-04-17
They said no scan results. Even though my router is just ~30cm away, and definitely functioning with 1 other wireless-enabled computer connected.

DMESG:
02] PCI: Found IRQ 11 for device 0000:00:01.0
[   18.089206] PCI: Sharing IRQ 11 with 0000:00:1c.0
[   18.089214] PCI: Sharing IRQ 11 with 0000:00:1d.3
[   18.089227] PCI: Sharing IRQ 11 with 0000:01:00.0
[   18.089235] PCI: Sharing IRQ 11 with 0000:06:04.0
[   18.089247] PCI: IRQ 0 for device 0000:00:1c.1 doesn't match PIRQ mask - try pci=usepirqmask
[   18.089251] PCI: Found IRQ 5 for device 0000:00:1c.1
[   18.089265] PCI: Sharing IRQ 5 with 0000:00:1e.2
[   18.089282] PCI: Sharing IRQ 5 with 0000:06:04.1
[   18.089285] PCI: Sharing IRQ 5 with 0000:06:04.2
[   18.089288] PCI: Sharing IRQ 5 with 0000:06:04.3
[   18.089291] PCI: Sharing IRQ 5 with 0000:06:04.4
[   18.089307] PCI: IRQ 0 for device 0000:00:1f.1 doesn't match PIRQ mask - try pci=usepirqmask
[   18.089311] PCI: Found IRQ 11 for device 0000:00:1f.1
[   18.089320] PCI: Sharing IRQ 11 with 0000:00:1d.2
[   18.101371] audit: initializing netlink socket (disabled)
[   18.101375] audit: initialized
[   18.101410] highmem bounce pool size: 64 pages
[   18.101451] VFS: Disk quotas dquot_6.5.1
[   18.101464] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.101484] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   18.101488] devfs: boot_options: 0x0
[   18.101508] Initializing Cryptographic API
[   18.101590] PCI: Found IRQ 11 for device 0000:00:01.0
[   18.101594] PCI: Sharing IRQ 11 with 0000:00:1c.0
[   18.101602] PCI: Sharing IRQ 11 with 0000:00:1d.3
[   18.101614] PCI: Sharing IRQ 11 with 0000:01:00.0
[   18.101623] PCI: Sharing IRQ 11 with 0000:06:04.0
[   18.101633] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.101658] assign_interrupt_mode Found MSI capability
[   18.101660] Allocate Port Service[pcie00]
[   18.101704] PCI: Found IRQ 11 for device 0000:00:1c.0
[   18.101706] PCI: Sharing IRQ 11 with 0000:00:01.0
[   18.101716] PCI: Sharing IRQ 11 with 0000:00:1d.3
[   18.101728] PCI: Sharing IRQ 11 with 0000:01:00.0
[   18.101737] PCI: Sharing IRQ 11 with 0000:06:04.0
[   18.101748] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.101796] assign_interrupt_mode Found MSI capability
[   18.101798] Allocate Port Service[pcie00]
[   18.101818] Allocate Port Service[pcie02]
[   18.101857] PCI: IRQ 5 for device 0000:00:1c.1 doesn't match PIRQ mask - try pci=usepirqmask
[   18.101861] PCI: Found IRQ 5 for device 0000:00:1c.1
[   18.101892] PCI: Sharing IRQ 5 with 0000:00:1e.2
[   18.101909] PCI: Sharing IRQ 5 with 0000:06:04.1
[   18.101912] PCI: Sharing IRQ 5 with 0000:06:04.2
[   18.101916] PCI: Sharing IRQ 5 with 0000:06:04.3
[   18.101919] PCI: Sharing IRQ 5 with 0000:06:04.4
[   18.101923] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.101972] assign_interrupt_mode Found MSI capability
[   18.101974] Allocate Port Service[pcie00]
[   18.101990] Allocate Port Service[pcie02]
[   18.102013] isapnp: Scanning for PnP cards...
[   18.455133] isapnp: No Plug & Play device found
[   18.467170] PNP: No PS/2 controller found. Probing ports directly.
[   18.467317] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.467362] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.467373] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.467383] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.467393] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.467405] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.467408] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   18.467588] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.468766] PCI: Found IRQ 10 for device 0000:00:1e.3
[   18.468790] PCI: Sharing IRQ 10 with 0000:06:00.0
[   18.468814] io scheduler noop registered
[   18.468825] io scheduler anticipatory registered
[   18.468828] io scheduler deadline registered
[   18.468833] io scheduler cfq registered
[   18.469071] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.469123] NET: Registered protocol family 2
[   18.478661] IP: routing cache hash table of 8192 buckets, 64Kbytes
[   18.478806] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[   18.481111] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   18.481444] TCP: Hash tables configured (established 262144 bind 65536)
[   18.481529] NET: Registered protocol family 8
[   18.481532] NET: Registered protocol family 20
[   18.481737] Freeing unused kernel memory: 168k freed
[   18.490597] vga16fb: initializing
[   18.490618] vga16fb: mapped to 0xc00a0000
[   18.607504] Console: switching to colour frame buffer device 80x30
[   18.607508] fb0: VGA16 VGA frame buffer device
[   19.074006] input: AT Translated Set 2 keyboard on isa0060/serio0
[   19.476452] spurious 8259A interrupt: IRQ15.
[   19.741433] Capability LSM initialized
[   19.748783] NET: Registered protocol family 1
[   19.759618] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.759626] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.763831] ICH6: IDE controller at PCI slot 0000:00:1f.1
[   19.763844] PCI: Found IRQ 11 for device 0000:00:1f.1
[   19.763855] PCI: Sharing IRQ 11 with 0000:00:1d.2
[   19.763888] ICH6: chipset revision 4
[   19.763890] ICH6: not 100% native mode: will probe irqs later
[   19.763899]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:DMA
[   19.763909] Probing IDE interface ide0...
[   20.027808] hda: ST9100822A, ATA DISK drive
[   20.435513] hdb: MATSHITAUJ-845D, ATAPI CD/DVD-ROM drive
[   20.486539] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.486608] Probing IDE interface ide1...
[   20.998848] Probing IDE interface ide2...
[   21.510488] Probing IDE interface ide3...
[   22.022127] Probing IDE interface ide4...
[   22.533767] Probing IDE interface ide5...
[   23.047483] hda: max request size: 1024KiB
[   23.047983] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   23.048131] hda: cache flushes supported
[   23.048169]  /dev/ide/host0/bus0/target0/lun0: p1 p2
[   23.075960] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   23.075964] Uniform CD-ROM driver Revision: 3.20
[   23.247948] usbcore: registered new driver usbfs
[   23.247969] usbcore: registered new driver hub
[   23.248563] USB Universal Host Controller Interface driver v2.2
[   23.248607] PCI: Found IRQ 11 for device 0000:00:1d.0
[   23.248621] PCI: Sharing IRQ 11 with 0000:00:1d.7
[   23.248653] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.248657] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[   23.310326] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.310334] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001200
[   23.310414] hub 1-0:1.0: USB hub found
[   23.310419] hub 1-0:1.0: 2 ports detected
[   23.313231] PCI: Found IRQ 11 for device 0000:00:1d.1
[   23.313252] PCI: Sharing IRQ 11 with 0000:00:1f.3
[   23.313272] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.313276] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[   23.375195] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.375200] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[   23.375275] hub 2-0:1.0: USB hub found
[   23.375280] hub 2-0:1.0: 2 ports detected
[   23.378183] PCI: Found IRQ 11 for device 0000:00:1d.2
[   23.378203] PCI: Sharing IRQ 11 with 0000:00:1f.1
[   23.378224] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.378227] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[   23.440145] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   23.440149] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[   23.440220] hub 3-0:1.0: USB hub found
[   23.440225] hub 3-0:1.0: 2 ports detected
[   23.443141] PCI: Found IRQ 11 for device 0000:00:1d.3
[   23.443144] PCI: Sharing IRQ 11 with 0000:00:01.0
[   23.443146] PCI: Sharing IRQ 11 with 0000:00:1c.0
[   23.443166] PCI: Sharing IRQ 11 with 0000:01:00.0
[   23.443174] PCI: Sharing IRQ 11 with 0000:06:04.0
[   23.443186] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.443190] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[   23.505101] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   23.505105] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[   23.505178] hub 4-0:1.0: USB hub found
[   23.505183] hub 4-0:1.0: 2 ports detected
[   23.531850] PCI: Found IRQ 11 for device 0000:00:1d.7
[   23.531858] PCI: Sharing IRQ 11 with 0000:00:1d.0
[   23.531897] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.531901] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[   23.531915] ehci_hcd 0000:00:1d.7: debug port 1
[   23.531945] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.531951] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf0000000
[   23.535839] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.535846] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   23.535899] hub 5-0:1.0: USB hub found
[   23.535904] hub 5-0:1.0: 8 ports detected
[   23.607990] tg3.c:v3.31 (June 8, 2005)
[   23.608027] PCI: Found IRQ 11 for device 0000:06:01.0
[   23.631424] eth0: Tigon3 [partno(BCM95788A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0f:b0:81:ea:05
[   23.631429] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[1]
[   23.631432] eth0: dma_rwctrl[763f0000]
[   26.151737] EXT3-fs: INFO: recovery required on readonly filesystem.
[   26.151740] EXT3-fs: write access will be enabled during recovery.
[   27.563376] kjournald starting.  Commit interval 5 seconds
[   27.563388] EXT3-fs: recovery complete.
[   27.583247] EXT3-fs: mounted filesystem with ordered data mode.
[   28.585998] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   32.272922] EXT3 FS on hda2, internal journal
[   36.258526] lp: driver loaded but no devices found
[   36.283899] mice: PS/2 mouse device common for all mice
[   36.347013] ieee1394: Initialized config rom entry `ip1394'
[   36.367573] SCSI subsystem initialized
[   36.408193] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   36.509795] Linux agpgart interface v0.101 (c) Dave Jones
[   36.557484] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   36.559056] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[   36.559094] PCI: Found IRQ 11 for device 0000:01:00.0
[   36.559098] PCI: Sharing IRQ 11 with 0000:00:01.0
[   36.559101] PCI: Sharing IRQ 11 with 0000:00:1c.0
[   36.559110] PCI: Sharing IRQ 11 with 0000:00:1d.3
[   36.559130] PCI: Sharing IRQ 11 with 0000:06:04.0
[   36.559151] [fglrx] module loaded - fglrx 8.24.8 [Apr 11 2006] on minor 0
[   36.740706] logips2pp: Detected unknown logitech mouse model 99
[   36.811036] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio4
[   37.074614] ts: Compaq touchscreen protocol output
[   39.688436] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   40.826831] cdrom: open failed.
[   44.005729] agpgart: Detected an Intel 915GM Chipset.
[   44.032504] agpgart: AGP aperture is 256M @ 0x0
[   44.308139] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.321263] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
[   44.378777] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
[   44.435568] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
[   44.664575] hw_random hardware driver 1.0.0 loaded
[   45.967527] PCI: IRQ 5 for device 0000:00:1e.2 doesn't match PIRQ mask - try pci=usepirqmask
[   45.967533] PCI: Found IRQ 5 for device 0000:00:1e.2
[   45.967539] PCI: Sharing IRQ 5 with 0000:00:1c.1
[   45.967568] PCI: Sharing IRQ 5 with 0000:06:04.1
[   45.967571] PCI: Sharing IRQ 5 with 0000:06:04.2
[   45.967575] PCI: Sharing IRQ 5 with 0000:06:04.3
[   45.967578] PCI: Sharing IRQ 5 with 0000:06:04.4
[   45.967600] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   46.775689] intel8x0_measure_ac97_clock: measured 49521 usecs
[   46.775691] intel8x0: clocking to 48000
[   47.310257] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[   47.310281] PCI: Found IRQ 10 for device 0000:06:00.0
[   47.310315] PCI: Sharing IRQ 10 with 0000:00:1e.3
[   47.362326] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[b0020000-b00207ff]  Max Packet=[2048]
[   47.471641] ieee80211_crypt: registered algorithm 'NULL'
[   47.565935] ieee80211: 802.11 data/management/control stack, 1.1.13
[   47.565938] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   47.596645] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.0
[   47.596648] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   47.600078] PCI: Found IRQ 11 for device 0000:06:02.0
[   47.600163] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[B][I][U][   47.954028] ipw2200: Radio Frequency Kill Switch is On:
[   47.954030] Kill switch must be turned off for wireless networking to work.[/U][/I][/B]
[   47.967117] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   48.032273] Linux Kernel Card Services
[   48.032276]   options:  [pci] [cardbus] [pm]
[   48.038269] PCI: Found IRQ 11 for device 0000:06:04.0
[   48.038273] PCI: Sharing IRQ 11 with 0000:00:01.0
[   48.038277] PCI: Sharing IRQ 11 with 0000:00:1c.0
[   48.038286] PCI: Sharing IRQ 11 with 0000:00:1d.3
[   48.038299] PCI: Sharing IRQ 11 with 0000:01:00.0
[   48.038320] Yenta: CardBus bridge found at 0000:06:04.0 [1025:0081]
[   48.158226] Yenta: ISA IRQ mask 0x0210, PCI irq 11
[   48.158229] Socket status: 30000006
[   48.618345] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f587740173e]
[   49.826678] NET: Registered protocol family 17
[  116.624023] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  116.624026] tg3: eth0: Flow control is on for TX and on for RX.
[  123.658699] NET: Registered protocol family 10
[  123.658786] Disabled Privacy Extensions on device c031eb40(lo)
[  123.658936] IPv6 over IPv4 tunneling driver
[  131.455638] [fglrx] free  PCIe = 51118080
[  131.455645] [fglrx] max   PCIe = 51118080
[  131.455647] [fglrx] free  LFB = 52654080
[  131.455648] [fglrx] max   LFB = 52654080
[  131.455650] [fglrx] free  Inv = 0
[  131.455651] [fglrx] max   Inv = 0
[  131.455652] [fglrx] total Inv = 0
[  131.455654] [fglrx] total TIM = 0
[  131.455655] [fglrx] total FB  = 0
[  131.455657] [fglrx] total PCIe = 16384
[  134.346990] eth1: no IPv6 routers present
[  134.380964] eth0: no IPv6 routers present
[  135.122398] apm: BIOS not found.
[  135.862064] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[  135.864556] cs: IO port probe 0xc00-0xcf7: clean.
[  135.865234] cs: IO port probe 0xa00-0xaff: clean.
[  138.374918] Bluetooth: Core ver 2.7
[  138.374925] NET: Registered protocol family 31
[  138.374926] Bluetooth: HCI device and connection manager initialized
[  138.374934] Bluetooth: HCI socket layer initialized
[  138.446155] Bluetooth: L2CAP ver 2.7
[  138.446159] Bluetooth: L2CAP socket layer initialized
[  138.448560] Bluetooth: RFCOMM ver 1.5
[  138.448565] Bluetooth: RFCOMM socket layer initialized
[  138.448571] Bluetooth: RFCOMM TTY layer initialized
[  167.591214] psmouse.c: Wheel Mouse at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
****

---

### Post by mengqing on 2006-04-17
Im having the same problem... except I can find AP

however I can not get any IP from DHCP server...

the console is repeatedly showing the following

Warning: Driver for device eth1 has been compiled with version 19
of Wireless Extension, while this program supports up to version 18.
Some things may be broken...


I tried to specify a static IP but still no luck...I looked at my router setup page to see if I am connected, surprisingly.. my notebook is connected... but the problem is there is no connection between the two..

---

### Post by nolongerlivecd on 2006-04-18
Can anyone help?

---

### Post by nolongerlivecd on 2006-04-19
Solved. On my own. But thanks to all the kind guys who tried to help.

For all those struggling with their stuff, here's my advice.
1. Backup your documents ONLY. No extra config stuff.
2. Reformat entirely. At least that's how it worked for me. Wireless started, and battery detected. Heavenly

---

### Post by CameronCalver on 2006-04-19
Hey this is my story

first i have a home computer will dial up external modem i use gnome ppp for internet and mozilla for browsing and i built my own computer(both use ubuntu) and i pluged a network cable to both of them and plugged other end to hub and people said i should download network-manager and i did and the external modem says its connected but ubuntu thinks its not i think it is something to do with network manager.

And NOMORELIVECD how did you get a wired network working can you give me a step by step plz for like sharing internet and files  and possobly printer but thats not neccesary

---

### Post by encompass on 2006-04-19
[QUOTE=CameronCalver]Hey this is my story

first i have a home computer will dial up external modem i use gnome ppp for internet and mozilla for browsing and i built my own computer(both use ubuntu) and i pluged a network cable to both of them and plugged other end to hub and people said i should download network-manager and i did and the external modem says its connected but ubuntu thinks its not i think it is something to do with network manager.

And NOMORELIVECD how did you get a wired network working can you give me a step by step plz for like sharing internet and files  and possobly printer but thats not neccesary[/QUOTE]

You will get better results and answers if you start a new thread. Not try to get answers off of an old one.  He or I may know the answer... but if you start your own thread many more people will see it.

---

### Post by CameronCalver on 2006-04-19
thanks ill do that

---

