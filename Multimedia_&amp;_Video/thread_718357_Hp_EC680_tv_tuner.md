---
title: "Hp EC680 tv tuner"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by Firecad2006 on 2008-03-08
i have a HP EC680 tv tuner that i got with my computer and i want to use it on ubuntu but i cant iv looked all over for a tv viewer but they dont work iv tryed mythtv and never got it to work can some one help please

---

### Post by steefjeqv on 2008-03-08
Hi,

Is it a digital or an analog tuner ?

Can you post your lspci output ?

Greetings,
Steven

---

### Post by Firecad2006 on 2008-03-08
its an Analog tuner


donald@donald-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
donald@donald-laptop:~$

---

### Post by steefjeqv on 2008-03-09
Hi,

I didn't know that it was a pcmcia card, used with your laptop.

Can you post the output of "lspcmcia" ?

You can also try testing your card with the following applications :

- TVtime

- XawTV

These two apps are available in the standard Ubuntu repos.

Greetings,
Steven

---

### Post by Firecad2006 on 2008-03-09
donald@donald-laptop:~$ lspcmcia
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:0b:00.0)
donald@donald-laptop:~$

---

### Post by steefjeqv on 2008-03-09
Hi,

Your pcmcia card is detected [yenta_cardbus].

Did you try the two applications I mentioned in my previous post ?

Can you post your "dmesg" output ?

Greetings,
Steven

---

### Post by Firecad2006 on 2008-03-09
tryed them both and just get a blank screen 


[   18.411302] ata1.00: 156301488 sectors, multi 16: LBA 
[   18.411308] ata1.01: ATAPI: MATSHITAUJ-840D, 1.02, max MWDMA2
[   18.427255] ata1.00: configured for UDMA/100
[   18.598984] ata1.01: configured for MWDMA2
[   18.599012] ata2: port disabled. ignoring.
[   18.599157] scsi 0:0:0:0: Direct-Access     ATA      ST98823A         3.05 PQ: 0 ANSI: 5
[   18.601079] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-840D          1.02 PQ: 0 ANSI: 5
[   18.617097] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   18.617120] sd 0:0:0:0: [sda] Write Protect is off
[   18.617125] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.617157] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.617232] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   18.617251] sd 0:0:0:0: [sda] Write Protect is off
[   18.617255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.617286] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.617293]  sda: sda1 sda2 < sda5 >
[   18.653043] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.657588] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.657620] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   18.663455] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   18.663460] Uniform CD-ROM driver Revision: 3.20
[   18.663522] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   18.945743] Attempting manual resume
[   18.945749] swsusp: Resume From Partition 8:5
[   18.945752] PM: Checking swsusp image.
[   18.945964] PM: Resume from disk failed.
[   18.989828] kjournald starting.  Commit interval 5 seconds
[   18.989842] EXT3-fs: mounted filesystem with ordered data mode.
[   19.296982] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08002856000bce27]
[   28.493515] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.498416] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.716500] Linux agpgart interface v0.102 (c) Dave Jones
[   29.282255] intel_rng: FWH not detected
[   29.379627] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   29.421386] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   29.421511] [fglrx] ASYNCIO init succeed!
[   29.422900] [fglrx] PAT is enabled successfully!
[   29.422927] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   29.482357] ieee80211_crypt: registered algorithm 'NULL'
[   29.494410] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   29.494415] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   29.630194] bcm43xx driver
[   29.630317] PCI: Enabling device 0000:0b:03.0 (0000 -> 0002)
[   29.630327] ACPI: PCI Interrupt 0000:0b:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[   29.661102] iTCO_vendor_support: vendor-support=0
[   29.662599] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   29.713308] Yenta: CardBus bridge found at 0000:0b:00.0 [103c:3082]
[   29.713330] Yenta: Enabling burst memory read transactions
[   29.713337] Yenta: Using CSCINT to route CSC interrupts to PCI
[   29.713341] Yenta: Routing CardBus interrupts to PCI
[   29.713348] Yenta TI: socket 0000:0b:00.0, mfunc 0x01a01b22, devctl 0x64
[   29.715148] sdhci: Secure Digital Host Controller Interface driver
[   29.715153] sdhci: Copyright(c) Pierre Ossman
[   29.943243] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   29.943248] Socket status: 30000006
[   29.943252] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   29.943256] cs: IO port probe 0x5000-0x5fff: clean.
[   29.943545] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[   29.943548] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   29.948516] sdhci: SDHCI controller found at 0000:0b:00.4 [104c:8034] (rev 0)
[   29.948535] PCI: Enabling device 0000:0b:00.4 (0000 -> 0002)
[   29.948542] ACPI: PCI Interrupt 0000:0b:00.4[A] -> GSI 16 (level, low) -> IRQ 16
[   29.948625] mmc0: SDHCI at 0xb0209000 irq 16 DMA
[   29.952664] mmc1: SDHCI at 0xb0208c00 irq 16 DMA
[   29.952721] mmc2: SDHCI at 0xb0208800 irq 16 DMA
[   29.952759] PCI: Enabling device 0000:0b:00.3 (0000 -> 0002)
[   29.952766] ACPI: PCI Interrupt 0000:0b:00.3[A] -> GSI 16 (level, low) -> IRQ 16
[   29.975692] tifm_core: MMC/SD card detected in socket 0:3
[   30.084009] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 22 (level, low) -> IRQ 18
[   30.084034] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   30.185716] mmcblk0: mmc3:b368 LEXAR 1967616KiB 
[   30.185762]  mmcblk0: p1
[   30.189601] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x80b1, caps: 0xa04713/0x20040a
[   30.223075] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   30.225598] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x1060)
[   30.225667] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.225768] input: PC Speaker as /class/input/input3
[   30.342243] cs: IO port probe 0x100-0x3af: clean.
[   30.346279] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   30.347410] cs: IO port probe 0x820-0x8ff: clean.
[   30.347913] cs: IO port probe 0xc00-0xcf7: clean.
[   30.348512] cs: IO port probe 0xa00-0xaff: clean.
[   30.401324] intel8x0_measure_ac97_clock: measured 53976 usecs
[   30.401328] intel8x0: clocking to 48000
[   31.132252] lp: driver loaded but no devices found
[   31.213508] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   31.537110] EXT3 FS on sda1, internal journal
[   32.764979] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   32.777914] ACPI: Battery Slot [BAT1] (battery present)
[   32.803577] input: Power Button (FF) as /class/input/input4
[   32.803607] ACPI: Power Button (FF) [PWRF]
[   32.803727] input: Lid Switch as /class/input/input5
[   32.803750] ACPI: Lid Switch [LID0]
[   32.803819] input: Power Button (CM) as /class/input/input6
[   32.803848] ACPI: Power Button (CM) [PWRB]
[   32.803911] input: Sleep Button (CM) as /class/input/input7
[   32.803941] ACPI: Sleep Button (CM) [SLPB]
[   33.041935] No dock devices found.
[   33.083211] ACPI: AC Adapter [ACAD] (off-line)
[   34.468034] ACPI: PCI Interrupt 0000:00:1e.3[A] -> GSI 22 (level, low) -> IRQ 18
[   34.468064] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[   34.715626] eth0: link down
[   34.822407] MC'97 0 converters and GPIO not ready (0x1)
[   35.368100] ppdev: user-space parallel port driver
[   35.522806] audit(1205108451.127:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4971 profile="/usr/sbin/cupsd"
[   35.561546] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   35.561553] apm: disabled - APM is not SMP safe.
[   36.361085] Failure registering capabilities with primary security module.
[   36.567138] Bluetooth: Core ver 2.11
[   36.567413] NET: Registered protocol family 31
[   36.567496] Bluetooth: HCI device and connection manager initialized
[   36.567502] Bluetooth: HCI socket layer initialized
[   36.593294] Bluetooth: L2CAP ver 2.8
[   36.593301] Bluetooth: L2CAP socket layer initialized
[   36.665125] Bluetooth: RFCOMM socket layer initialized
[   36.665281] Bluetooth: RFCOMM TTY layer initialized
[   36.665286] Bluetooth: RFCOMM ver 1.8
[   39.043711] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.630027] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   41.630035] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000
[   41.630042] [fglrx] Reserve Block - 2 offset =  0X7fc0000 length = 0X40000
[   41.759714] [fglrx] interrupt source 20008000 successfully enabled
[   41.759722] [fglrx] enable ID = 0x00000004
[   41.759734] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   41.759824] [fglrx] interrupt source 10000000 successfully enabled
[   41.759831] [fglrx] enable ID = 0x00000005
[   41.759839] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   75.190202] NET: Registered protocol family 17
[   75.646522] SoftMAC: Open Authentication completed with 00:18:d1:69:6c:83
[   75.918214] ieee80211_crypt: registered algorithm 'TKIP'
[   85.497052] NET: Registered protocol family 10
[   85.497349] lo: Disabled Privacy Extensions
[   85.497523] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   95.950841] eth1: no IPv6 routers present
[  186.719618] printk: 1 messages suppressed.
[  196.776040] printk: 1 messages suppressed.
[  201.881327] printk: 1 messages suppressed.
[  206.902939] printk: 1 messages suppressed.
[  211.920394] printk: 1 messages suppressed.
[  222.052083] printk: 1 messages suppressed.
[  226.274841] printk: 5 messages suppressed.
[  232.217195] printk: 2 messages suppressed.
[  238.257224] printk: 1 messages suppressed.
[  247.325715] printk: 1 messages suppressed.
[  267.549697] printk: 1 messages suppressed.
[  272.568669] printk: 1 messages suppressed.
[  282.731107] printk: 1 messages suppressed.
[  287.767266] printk: 1 messages suppressed.
[  292.798689] printk: 1 messages suppressed.
[  297.852221] printk: 1 messages suppressed.
[  303.208985] printk: 1 messages suppressed.
[  308.215241] printk: 1 messages suppressed.
[  313.422514] printk: 1 messages suppressed.
[  318.252892] printk: 1 messages suppressed.
[  323.351496] printk: 1 messages suppressed.
[  333.395243] printk: 1 messages suppressed.
[  360.448565] printk: 1 messages suppressed.
[  365.537159] printk: 1 messages suppressed.
[  510.113623] printk: 1 messages suppressed.
[  515.159558] printk: 1 messages suppressed.
[  520.266746] printk: 1 messages suppressed.
[  525.260600] printk: 1 messages suppressed.
[  530.414282] printk: 1 messages suppressed.
[  535.431560] printk: 1 messages suppressed.
[  540.454069] printk: 1 messages suppressed.
[  548.128574] printk: 1 messages suppressed.
[  555.613842] printk: 1 messages suppressed.
[  560.655169] printk: 1 messages suppressed.
[  570.828608] printk: 1 messages suppressed.
[  575.854229] printk: 1 messages suppressed.
[  580.882852] printk: 1 messages suppressed.
[  585.897536] printk: 3 messages suppressed.
[  591.003034] printk: 1 messages suppressed.
[  599.040439] printk: 1 messages suppressed.
[  606.064523] printk: 1 messages suppressed.
[  616.367699] printk: 1 messages suppressed.
[  621.384659] printk: 1 messages suppressed.
[  626.428534] printk: 1 messages suppressed.
[  631.522688] printk: 1 messages suppressed.
[  641.580407] printk: 1 messages suppressed.
[  644.699544] printk: 5 messages suppressed.
[  651.781050] printk: 3 messages suppressed.
[  659.920123] printk: 1 messages suppressed.
[  664.974382] printk: 1 messages suppressed.
[  670.342563] printk: 1 messages suppressed.
[  676.917403] printk: 1 messages suppressed.
[  685.409601] printk: 1 messages suppressed.
[  692.127623] printk: 1 messages suppressed.
[  702.340877] printk: 1 messages suppressed.
[  710.550600] printk: 1 messages suppressed.
[  715.594640] printk: 1 messages suppressed.
[  720.618610] printk: 1 messages suppressed.
[  727.474670] printk: 1 messages suppressed.
[  745.926410] printk: 1 messages suppressed.
[  752.686289] printk: 1 messages suppressed.
[  808.291868] printk: 1 messages suppressed.
[  832.242342] printk: 1 messages suppressed.
[  838.588601] printk: 1 messages suppressed.
[  848.627163] printk: 1 messages suppressed.
[  862.134536] printk: 1 messages suppressed.
[  868.836156] printk: 1 messages suppressed.
[  882.914827] printk: 1 messages suppressed.
[  884.917006] printk: 5 messages suppressed.
[  889.071441] printk: 1 messages suppressed.
[  894.093773] printk: 1 messages suppressed.
[  899.171627] printk: 2 messages suppressed.
[  904.184779] printk: 1 messages suppressed.
[  909.207879] printk: 1 messages suppressed.
[  914.476160] printk: 1 messages suppressed.
[  919.541955] printk: 1 messages suppressed.
[  924.593628] printk: 1 messages suppressed.
[  944.761214] printk: 1 messages suppressed.
[  954.802978] printk: 1 messages suppressed.
[  969.116866] printk: 1 messages suppressed.
[  974.122199] printk: 1 messages suppressed.
[  979.331234] printk: 1 messages suppressed.
[  984.438569] printk: 1 messages suppressed.
[  989.373948] printk: 1 messages suppressed.
[  995.176925] printk: 1 messages suppressed.
[ 1004.630133] printk: 3 messages suppressed.
[ 1010.293727] printk: 1 messages suppressed.
[ 1025.041227] printk: 1 messages suppressed.
[ 1030.148960] printk: 1 messages suppressed.
[ 1035.255745] printk: 1 messages suppressed.
[ 1040.363161] printk: 1 messages suppressed.
[ 1045.215397] printk: 1 messages suppressed.
[ 1050.256839] printk: 1 messages suppressed.
[ 1055.715895] printk: 1 messages suppressed.
[ 1065.643951] printk: 1 messages suppressed.
[ 1070.751644] printk: 1 messages suppressed.
[ 1075.986863] printk: 1 messages suppressed.
[ 1088.766710] printk: 2 messages suppressed.
[ 1096.210919] printk: 32 messages suppressed.
[ 1101.259990] printk: 1 messages suppressed.
[ 1106.398586] printk: 1 messages suppressed.
[ 1111.427553] printk: 1 messages suppressed.
[ 1116.541154] printk: 1 messages suppressed.
[ 1126.755221] printk: 4 messages suppressed.
[ 1131.821328] printk: 1 messages suppressed.
[ 1133.810081] printk: 1 messages suppressed.
[ 1141.821886] printk: 2 messages suppressed.
[ 1152.036599] printk: 1 messages suppressed.
[ 1161.995444] printk: 1 messages suppressed.
[ 1172.210196] printk: 1 messages suppressed.
[ 1177.059815] printk: 1 messages suppressed.
[ 1187.191888] printk: 1 messages suppressed.
[ 1197.491057] printk: 1 messages suppressed.
[ 1207.450414] printk: 1 messages suppressed.
[ 1212.424729] printk: 1 messages suppressed.
[ 1223.458116] printk: 1 messages suppressed.
[ 1233.672703] printk: 1 messages suppressed.
[ 1238.591317] printk: 1 messages suppressed.
[ 1244.260968] printk: 6 messages suppressed.
[ 1248.772515] printk: 2 messages suppressed.
[ 1261.915283] printk: 2 messages suppressed.
[ 1263.149433] printk: 2 messages suppressed.
[ 1268.261740] printk: 1 messages suppressed.
[ 1273.293161] printk: 1 messages suppressed.
[ 1278.441300] printk: 3 messages suppressed.
[ 1289.341951] printk: 1 messages suppressed.
[ 1345.011051] printk: 1 messages suppressed.
[ 1364.074019] printk: 1 messages suppressed.
[ 1369.208257] printk: 1 messages suppressed.
[ 1374.238149] printk: 1 messages suppressed.
[ 1379.257206] printk: 1 messages suppressed.
[ 1384.273829] printk: 1 messages suppressed.
[ 1394.421424] printk: 1 messages suppressed.
[ 1399.452184] printk: 1 messages suppressed.
[ 1404.458728] printk: 1 messages suppressed.
[ 1414.806049] printk: 1 messages suppressed.
[ 1419.151379] printk: 1 messages suppressed.
[ 1424.019295] printk: 3 messages suppressed.
[ 1429.842212] printk: 1 messages suppressed.
[ 1434.892458] printk: 1 messages suppressed.
[ 1439.902587] printk: 1 messages suppressed.
[ 1444.923531] printk: 1 messages suppressed.
[ 1452.242702] printk: 1 messages suppressed.
[ 1460.063636] printk: 1 messages suppressed.
[ 1465.107334] printk: 1 messages suppressed.
[ 1470.118309] printk: 1 messages suppressed.
[ 1470.118317] SoftMAC: Open Authentication completed with 00:18:d1:69:6c:83
[ 1500.609449] printk: 1 messages suppressed.
[ 1536.358804] printk: 1 messages suppressed.
[ 1544.091607] printk: 1 messages suppressed.
[ 1549.301328] printk: 1 messages suppressed.
[ 1554.158103] printk: 1 messages suppressed.
[ 1559.260478] printk: 1 messages suppressed.
[ 1564.290208] printk: 1 messages suppressed.
[ 1569.352935] printk: 1 messages suppressed.
[ 1574.457853] printk: 1 messages suppressed.
[ 1579.585389] printk: 2 messages suppressed.
[ 1584.796710] printk: 1 messages suppressed.
[ 1589.722673] printk: 1 messages suppressed.
[ 1594.752541] printk: 1 messages suppressed.
[ 1599.860168] printk: 1 messages suppressed.
[ 1604.898547] printk: 1 messages suppressed.
[ 1609.959173] printk: 1 messages suppressed.
[ 1614.992822] printk: 1 messages suppressed.
[ 1625.168587] printk: 2 messages suppressed.
[ 1632.375854] printk: 1 messages suppressed.
[ 1642.338038] printk: 1 messages suppressed.
[ 1647.442246] printk: 1 messages suppressed.
[ 1652.549518] printk: 1 messages suppressed.
[ 1657.656868] printk: 1 messages suppressed.
[ 1662.764889] printk: 1 messages suppressed.
[ 1667.615787] printk: 1 messages suppressed.
[ 1682.938180] printk: 1 messages suppressed.
[ 1688.048688] printk: 1 messages suppressed.
[ 1692.897279] printk: 1 messages suppressed.
[ 1698.006919] printk: 22 messages suppressed.
[ 1703.112159] printk: 1 messages suppressed.
[ 1708.224282] printk: 1 messages suppressed.
[ 1716.354960] printk: 1 messages suppressed.
[ 1723.285254] printk: 1 messages suppressed.
[ 1728.392652] printk: 1 messages suppressed.
[ 1733.500111] printk: 1 messages suppressed.
[ 1738.607619] printk: 1 messages suppressed.
[ 1743.458840] printk: 1 messages suppressed.
[ 1751.851219] printk: 1 messages suppressed.
[ 1758.780771] printk: 1 messages suppressed.
[ 1767.083648] printk: 1 messages suppressed.
[ 1772.139216] printk: 1 messages suppressed.
[ 1777.184067] printk: 1 messages suppressed.
[ 1782.286208] printk: 1 messages suppressed.
[ 1788.913714] printk: 1 messages suppressed.
[ 1797.621095] printk: 1 messages suppressed.
[ 1802.784103] printk: 1 messages suppressed.
[ 1807.820537] printk: 1 messages suppressed.
[ 1812.907487] printk: 1 messages suppressed.
[ 1817.986111] printk: 1 messages suppressed.
[ 1823.094273] printk: 1 messages suppressed.
[ 1828.152090] printk: 1 messages suppressed.
[ 1833.185372] printk: 1 messages suppressed.
[ 1838.219629] printk: 1 messages suppressed.
[ 1843.355109] printk: 4 messages suppressed.
[ 1848.380572] printk: 1 messages suppressed.
[ 1853.445929] printk: 1 messages suppressed.
[ 1858.510241] printk: 1 messages suppressed.
[ 1863.660052] printk: 1 messages suppressed.
[ 1868.700528] printk: 1 messages suppressed.
[ 1874.798981] printk: 1 messages suppressed.
[ 1883.879195] printk: 1 messages suppressed.
[ 1888.905165] printk: 1 messages suppressed.
[ 1893.998775] printk: 1 messages suppressed.
[ 1899.051295] printk: 1 messages suppressed.
[ 1904.187179] printk: 4 messages suppressed.
[ 1909.363183] printk: 1 messages suppressed.
[ 1914.263166] printk: 1 messages suppressed.
[ 1920.272571] printk: 1 messages suppressed.
[ 1929.446947] printk: 1 messages suppressed.
[ 1934.477194] printk: 1 messages suppressed.
[ 1939.520493] printk: 1 messages suppressed.
[ 1944.721115] printk: 1 messages suppressed.
[ 1949.928511] printk: 1 messages suppressed.
[ 1954.961395] printk: 1 messages suppressed.
[ 1959.998519] printk: 1 messages suppressed.
[ 1965.100124] printk: 1 messages suppressed.
[ 1970.130719] printk: 1 messages suppressed.
[ 1975.193417] printk: 1 messages suppressed.
[ 1980.801023] printk: 1 messages suppressed.
[ 1988.224724] printk: 2 messages suppressed.
[ 1995.464642] printk: 1 messages suppressed.
[ 2000.530704] printk: 1 messages suppressed.
[ 2002.219146] printk: 1 messages suppressed.
[ 2010.722562] printk: 3 messages suppressed.
[ 2015.828193] printk: 1 messages suppressed.
[ 2020.856898] printk: 2 messages suppressed.
[ 2025.988707] printk: 1 messages suppressed.
[ 2031.374918] printk: 1 messages suppressed.
[ 2036.394546] printk: 1 messages suppressed.
[ 2041.509407] printk: 1 messages suppressed.
[ 2051.250473] printk: 1 messages suppressed.
[ 2056.289887] printk: 1 messages suppressed.
[ 2061.344855] printk: 1 messages suppressed.
[ 2066.497986] printk: 1 messages suppressed.
[ 2071.169930] printk: 1 messages suppressed.
[ 2076.626287] printk: 2 messages suppressed.
[ 2081.617141] printk: 3 messages suppressed.
[ 2086.772091] printk: 1 messages suppressed.
[ 2092.008197] printk: 2 messages suppressed.
[ 2097.164913] printk: 3 messages suppressed.
[ 2102.162522] printk: 1 messages suppressed.
[ 2107.324892] printk: 1 messages suppressed.
[ 2112.029472] printk: 1 messages suppressed.
[ 2117.510344] printk: 2 messages suppressed.
[ 2122.530906] printk: 1 messages suppressed.
[ 2127.677600] printk: 1 messages suppressed.
[ 2132.808324] printk: 1 messages suppressed.
[ 2137.842293] printk: 1 messages suppressed.
[ 2142.867063] printk: 1 messages suppressed.
[ 2145.943012] printk: 1 messages suppressed.
[ 2153.101639] printk: 2 messages suppressed.
[ 2157.894434] printk: 1 messages suppressed.
[ 2161.061222] printk: 3 messages suppressed.
[ 2168.199226] printk: 3 messages suppressed.
[ 2173.368524] printk: 1 messages suppressed.
[ 2178.412188] printk: 1 messages suppressed.
[ 2183.461534] printk: 1 messages suppressed.
[ 2187.824164] printk: 2 messages suppressed.
[ 2193.658765] printk: 2 messages suppressed.
[ 2198.721001] printk: 2 messages suppressed.
[ 2203.783549] printk: 1 messages suppressed.
[ 2208.815082] printk: 1 messages suppressed.
[ 2213.911156] printk: 2 messages suppressed.
[ 2218.945882] printk: 1 messages suppressed.
[ 2223.965786] printk: 1 messages suppressed.
[ 2234.118867] printk: 1 messages suppressed.
[ 2241.783984] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 2241.946697] usb 3-1: configuration #1 chosen from 1 choice
[ 2242.162368] Linux video capture interface: v2.00
[ 2242.184380] usbcore: registered new interface driver snd-usb-audio
[ 2242.238033] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[ 2242.239857] usb 3-1: SN9C105 PC Camera Controller detected (vid:pid 0x0471:0x0328)
[ 2242.345584] usb 3-1: No supported image sensor detected for this bridge
[ 2242.345636] usbcore: registered new interface driver sn9c102
[ 2242.350592] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. SONIX JPEG (sn9c1xx) 
[ 2242.351839] usbcore: registered new interface driver gspca
[ 2242.351844] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[ 2254.281647] printk: 1 messages suppressed.
[ 2259.332095] printk: 1 messages suppressed.
[ 2269.680891] printk: 1 messages suppressed.
[ 2273.457494] usb 3-1: USB disconnect, address 2
[ 2279.637852] printk: 2 messages suppressed.
[ 2285.135012] printk: 1 messages suppressed.
[ 2294.790494] printk: 1 messages suppressed.
[ 2297.160241] printk: 1 messages suppressed.
[ 2304.864382] printk: 32 messages suppressed.
[ 2309.880288] printk: 1 messages suppressed.
[ 2315.009919] printk: 1 messages suppressed.
[ 2320.626089] printk: 2 messages suppressed.
[ 2325.666727] printk: 1 messages suppressed.
[ 2335.219813] printk: 5 messages suppressed.
[ 2340.639434] printk: 1 messages suppressed.
[ 2345.928977] printk: 3 messages suppressed.
[ 2350.458930] printk: 1 messages suppressed.
[ 2355.881168] usb 5-6: new high speed USB device using ehci_hcd and address 3
[ 2356.013670] usb 5-6: configuration #1 chosen from 1 choice
[ 2356.248723] printk: 2 messages suppressed.
[ 2365.460778] printk: 2 messages suppressed.
[ 2370.479057] printk: 1 messages suppressed.
[ 2382.092169] printk: 3 messages suppressed.
[ 2387.460888] printk: 1 messages suppressed.
[ 2392.480255] printk: 1 messages suppressed.
[ 2397.500708] printk: 1 messages suppressed.
[ 2407.593007] printk: 1 messages suppressed.
[ 2432.796492] printk: 1 messages suppressed.
[ 2438.048847] printk: 1 messages suppressed.
[ 2442.911098] printk: 3 messages suppressed.
[ 2451.266806] printk: 1 messages suppressed.
[ 2457.970744] printk: 1 messages suppressed.
[ 2468.110293] printk: 1 messages suppressed.
[ 2503.398078] printk: 1 messages suppressed.
[ 2513.436452] printk: 1 messages suppressed.
[ 2523.566123] printk: 1 messages suppressed.
[ 2526.820636] [fglrx] interrupt source 10000000 successfully disabled!
[ 2526.820643] [fglrx] enable ID = 0x00000000
[ 2526.820647] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000005
[ 2526.820665] [fglrx] interrupt source 20008000 successfully disabled!
[ 2526.820669] [fglrx] enable ID = 0x00000000
[ 2526.820672] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000004
[ 2532.710093] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 2532.728335] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[ 2532.728343] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000
[ 2532.728347] [fglrx] Reserve Block - 2 offset =  0X7fc0000 length = 0X40000
[ 2532.836720] [fglrx] interrupt source 20008000 successfully enabled
[ 2532.836727] [fglrx] enable ID = 0x00000004
[ 2532.836759] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[ 2532.837766] [fglrx] interrupt source 10000000 successfully enabled
[ 2532.837771] [fglrx] enable ID = 0x00000005
[ 2532.837841] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[ 2563.942989] printk: 2 messages suppressed.
donald@donald-laptop:~$

---

