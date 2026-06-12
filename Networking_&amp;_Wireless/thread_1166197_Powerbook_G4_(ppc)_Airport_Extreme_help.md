---
title: "Powerbook G4 (ppc) Airport Extreme help"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by matamoscas on 2009-05-21
Please help. Here is all the information.

Short version: I installed 6.x a while back, and never really bothered to get wifi to work.  I recently upgraded to 8.0.4, and this time - I TRIED - to get it to work, but I am at my wits end.  I just want to know if anyone has gotten this to work, or if I should give up? =(

Long version - here is all the information, one through ten. I am not a guru, or I would have already been able to figure this out myself, so any precise information to solve the problem would be GREATLY appreciated. I want to be a guru someday. I can almost figure out that the system is not initializing - for reasons I am not experienced enough to know - the wifi card.  I have tried all the information on the topic I can find online, mostly with blind stabbing (not really knowing what I am doing - but at least, without fear).  If I knew how, I would probably try to blacklist the drivers, and/or probably rebuild my kernel.  Lastly, I just want to know if any other PPC G4 users have gotten wifi to work with 8.0+ ubuntu?  I have reasoned that this particular chipset, Broadcom, is problematic for all, but it appears Windows users have been able to get it to work. But, PPC users?

1. machine brand and model: 
Apple PPC G4 1.25GHz Powerbook 15"
AirPort Extreme 802.11g
001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Apple Computer Inc. AirPort Extreme [106b:004e]
	Flags: bus master, fast devsel, latency 16, IRQ 52
	Memory at a0006000 (32-bit, non-prefetchable) [disabled] [size=8K]

2. wireless brand, model and wireless chipset
Broadcom, 4306 rev 3, PCI-ID: 14e4:4320

3. check interface ifconfig + iwconfig or iwconfig wlan0
eth0      Link encap:Ethernet  HWaddr 00:0a:95:d1:4b:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4700 (4.5 KB)  TX bytes:4700 (4.5 KB)

e@Ubuntu-book:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

e@Ubuntu-book:~$ iwconfig wlan0
wlan0     No such device


4. check for modules: lsmod 
Module                  Size  Used by
nls_utf8                2304  1 
hfsplus                94852  1 
ipv6                  323492  6 
ppdev                  11748  0 
lp                     13804  0 
parport                45936  2 ppdev,lp
radeon                136968  2 
drm                    90744  3 radeon
cpufreq_userspace       5640  1 
cpufreq_stats           6276  0 
cpufreq_powersave       1920  0 
cpufreq_ondemand        8284  0 
cpufreq_conservative     9764  0 
af_packet              27080  0 
iptable_filter          3264  0 
ip_tables              24160  1 iptable_filter
fuse                   46568  0 
therm_adt746x          14252  0 
sr_mod                 20100  0 
sbp2                   28068  0 
scsi_mod              179588  2 sr_mod,sbp2
apm_emu                 8364  1 
snd_powermac           57920  2 
snd_pcm_oss            68480  0 
snd_mixer_oss          23072  1 snd_pcm_oss
snd_pcm               109892  2 snd_powermac,snd_pcm_oss
snd_seq_dummy           4164  0 
snd_seq_oss            43604  0 
snd_seq_midi           10656  0 
snd_rawmidi            31520  1 snd_seq_midi
snd_seq_midi_event      8384  2 snd_seq_oss,snd_seq_midi
snd_seq                66136  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29188  2 snd_pcm,snd_seq
snd_seq_device         10700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    72532  13 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11716  1 snd
snd_page_alloc         12424  1 snd_pcm
pcmcia                 49456  0 
sungem                 38948  0 
yenta_socket           33228  1 
rsrc_nonstatic         14368  1 yenta_socket
pcmcia_core            51384  3 pcmcia,yenta_socket,rsrc_nonstatic
sungem_phy             10432  1 sungem
uninorth_agp           11432  1 
agpgart                39900  2 drm,uninorth_agp
ext3                  167112  1 
jbd                    72436  1 ext3
usbhid                 51844  0 
ehci_hcd               39272  0 
ohci1394               42868  0 
ieee1394              436560  2 sbp2,ohci1394
ohci_hcd               25732  0 
usbcore               156704  4 usbhid,ehci_hcd,ohci_hcd
ide_disk               20800  4 
ide_cd                 38372  0 
cdrom                  49500  2 sr_mod,ide_cd
i2c_keywest            11936  0 
capability              5352  0 
commoncap               8256  1 capability


5. Kernel boot messages: dmesg
[    0.000000] Total memory = 2048MB; using 4096kB for hash table (at cfc00000)
[    0.000000] Linux version 2.6.15-26-powerpc (buildd@royal) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 Fri Sep 8 19:51:33 UTC 2006
[    0.000000] Found initrd at 0xc1900000:0xc20c6000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xd2
[    0.000000] Mapped at 0xfdfc0000
[    0.000000] Found a Intrepid mac-io controller, rev: 0, mapped at 0xfdf40000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: PowerBook G4 15"
[    0.000000] Enabling clock spreading on Intrepid ASIC
[    0.000000] Found UniNorth PCI host bridge at 0xf0000000. Firmware bus number: 0->1
[    0.000000] Found UniNorth PCI host bridge at 0xf2000000. Firmware bus number: 0->1
[    0.000000] Found UniNorth PCI host bridge at 0xf4000000. Firmware bus number: 0->1
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver 2 initialized for Core99, firmware: 0c
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=1006, gen1=1007
[    0.000000] nvram: Active bank is: 1
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Top of RAM: 0x80000000, Total RAM: 0x80000000
[    0.000000] Memory hole size: 0MB
[    0.000000] On node 0 totalpages: 524288
[    0.000000]   DMA zone: 196608 pages, LIFO batch:31
[    0.000000]   DMA32 zone: 0 pages, LIFO batch:0
[    0.000000]   Normal zone: 0 pages, LIFO batch:0
[    0.000000]   HighMem zone: 327680 pages, LIFO batch:31
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hda11 ro quiet splash 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 18.432000 MHz
[    0.000000] time_init: processor frequency   = 1249.999995 MHz
[   69.055174] Console: colour dummy device 80x25
[   69.056207] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   69.057634] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   69.281121] High memory: 1310720k
[   69.281132] Memory: 2062828k/2097152k available (2692k kernel code, 1343892k reserved, 276k data, 304k bss, 180k init)
[   69.281365] Calibrating delay loop... 36.73 BogoMIPS (lpj=73472)
[   69.350966] Security Framework v1.0.0 initialized
[   69.350996] SELinux:  Disabled at boot.
[   69.351035] Mount-cache hash table entries: 512
[   69.351402] device-tree: property "l2-cache" name conflicts with node in /cpus/PowerPC,G4@0
[   69.353792] checking if image is initramfs... it is
[   70.797225] Freeing initrd memory: 7960k freed
[   70.799020] NET: Registered protocol family 16
[   70.799814] PCI: Probing PCI hardware
[   70.802051] Can't get bus-range for /pci@f2000000/cardbus@13, assuming it starts at 0
[   70.802183] PCI: Cannot allocate resource region 0 of device 0001:10:18.0
[   70.802203] PCI: Cannot allocate resource region 0 of device 0001:10:19.0
[   70.802230] Apple USB OHCI 0001:10:18.0 disabled by firmware
[   70.802241] Apple USB OHCI 0001:10:19.0 disabled by firmware
[   70.804153] Registering PowerMac CPU frequency driver
[   70.804165] Low: 765 Mhz, High: 1249 Mhz, Boot: 765 Mhz
[   70.826895] Thermal assist unit not available
[   70.827659] audit: initializing netlink socket (disabled)
[   70.827679] audit(1242921127.768:1): initialized
[   70.827772] highmem bounce pool size: 64 pages
[   70.827892] VFS: Disk quotas dquot_6.5.1
[   70.827925] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   70.828019] Initializing Cryptographic API
[   70.828028] io scheduler noop registered
[   70.828038] io scheduler anticipatory registered
[   70.828048] io scheduler deadline registered
[   70.828073] io scheduler cfq registered
[   70.828473] PCI: Enabling device 0000:00:10.0 (0006 -> 0007)
[   71.024270] radeonfb (0000:00:10.0): Invalid ROM signature 303 should be 0xaa55
[   71.024280] radeonfb: Retreived PLL infos from Open Firmware
[   71.024287] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=200.00 Mhz, System=300.00 MHz
[   71.024293] radeonfb: PLL min 12000 max 35000
[   71.791869] radeonfb: Monitor 1 type LCD found
[   71.791874] radeonfb: EDID probed
[   71.791878] radeonfb: Monitor 2 type no found
[   71.791892] radeonfb: Using Firmware dividers 0x0002008e from PPLL 0
[   71.791960] radeonfb: Dynamic Clock Power Management enabled
[   71.847609] Console: switching to colour frame buffer device 160x53
[   71.847717] Registered "mnca" backlight controller,level: 15/15
[   71.847722] radeonfb (0000:00:10.0): ATI Radeon NP 
[   71.872212] Macintosh non-volatile memory driver v1.1
[   71.873119] i8042.c: No controller found.
[   71.873822] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   71.874007] MacIO PCI driver attached to Intrepid chipset
[   71.875181] input: Macintosh mouse button emulation as /class/input/input0
[   71.875376] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   71.875385] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   71.875406] adb: starting probe task...
[   71.876500] PCI: Enabling device 0002:24:0d.0 (0000 -> 0002)
[   72.125481] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[   72.131392] ADB keyboard at 2, handler 1
[   72.131403] Detected ADB keyboard, type ANSI.
[   72.131487] input: ADB keyboard as /class/input/input1
[   72.131567] input: ADB Powerbook buttons as /class/input/input2
[   72.146491] ADB mouse at 3, handler set to 4 (trackpad)
[   72.204746] input: ADB mouse as /class/input/input3
[   72.204754] adb: finished probe task...
[   72.894886] ide0: Found Apple UniNorth ATA-6 controller, bus ID 3, irq 39
[   72.894904] Probing IDE interface ide0...
[   73.183068] hda: FUJITSU MHT2080AT, ATA DISK drive
[   73.854893] hda: Enabling Ultra DMA 5
[   73.857895] ide0 at 0xf101a000-0xf101a007,0xf101a160 on irq 39
[   74.874884] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 24
[   74.874899] Probing IDE interface ide1...
[   75.275068] hdc: MATSHITADVD-R UJ-816, ATAPI CD/DVD-ROM drive
[   75.610889] hdc: Enabling MultiWord DMA 2
[   75.611913] ide1 at 0xf100e000-0xf100e007,0xf100e160 on irq 24
[   75.612203] mice: PS/2 mouse device common for all mice
[   75.612311] NET: Registered protocol family 2
[   75.646977] IP route cache hash table entries: 131072 (order: 7, 524288 bytes)
[   75.648020] TCP established hash table entries: 524288 (order: 9, 2097152 bytes)
[   75.651461] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   75.651898] TCP: Hash tables configured (established 524288 bind 65536)
[   75.651905] TCP reno registered
[   75.652086] TCP bic registered
[   75.652104] NET: Registered protocol family 1
[   75.652119] NET: Registered protocol family 8
[   75.652124] NET: Registered protocol family 20
[   75.652218] Freeing unused kernel memory: 180k init
[   76.890840] Capability LSM initialized
[   76.966394] Found KeyWest i2c on "uni-n", 2 channels, stepping: 4 bits
[   76.966546] Found KeyWest i2c on "mac-io", 1 channel, stepping: 4 bits
[   77.731776] hda: max request size: 1024KiB
[   77.737852] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, (U)DMA
[   77.737872] Uniform CD-ROM driver Revision: 3.20
[   77.792776] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   77.795737] hda: cache flushes supported
[   77.795832]  hda: [mac] hda1 hda2 hda3 hda4 hda5 hda6 hda7 hda8 hda9 hda10 hda11 hda12 hda13
[   78.575289] usbcore: registered new driver usbfs
[   78.575920] usbcore: registered new driver hub
[   78.580523] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   78.581164] Apple USB OHCI 0001:10:18.0 disabled by firmware
[   78.581178] Apple USB OHCI 0001:10:19.0 disabled by firmware
[   78.581192] PCI: Enabling device 0001:10:1a.0 (0000 -> 0002)
[   78.581217] ohci_hcd 0001:10:1a.0: OHCI Host Controller
[   78.582340] ohci_hcd 0001:10:1a.0: new USB bus registered, assigned bus number 1
[   78.582363] ohci_hcd 0001:10:1a.0: irq 29, io mem 0xa0003000
[   78.631061] hub 1-0:1.0: USB hub found
[   78.631089] hub 1-0:1.0: 2 ports detected
[   78.887990] PCI: Enabling device 0001:10:1b.0 (0000 -> 0002)
[   78.888024] ohci_hcd 0001:10:1b.0: OHCI Host Controller
[   78.888250] ohci_hcd 0001:10:1b.0: new USB bus registered, assigned bus number 2
[   78.888272] ohci_hcd 0001:10:1b.0: irq 63, io mem 0xa0002000
[   78.983354] hub 2-0:1.0: USB hub found
[   78.983382] hub 2-0:1.0: 3 ports detected
[   79.043035] ieee1394: Initialized config rom entry `ip1394'
[   79.062916] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   79.122969] PCI: Enabling device 0001:10:1b.1 (0000 -> 0002)
[   79.122997] ohci_hcd 0001:10:1b.1: OHCI Host Controller
[   79.123210] ohci_hcd 0001:10:1b.1: new USB bus registered, assigned bus number 3
[   79.123229] ohci_hcd 0001:10:1b.1: irq 63, io mem 0xa0001000
[   79.158936] hub 3-0:1.0: USB hub found
[   79.158957] hub 3-0:1.0: 2 ports detected
[   79.268238] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[   79.268276] PCI: Enabling device 0002:24:0e.0 (0000 -> 0002)
[   79.268810] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[   79.317875] PCI: Enabling device 0001:10:1b.2 (0004 -> 0006)
[   79.317891] ehci_hcd 0001:10:1b.2: EHCI Host Controller
[   79.320111] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[4096]
[   79.339467] ehci_hcd 0001:10:1b.2: new USB bus registered, assigned bus number 4
[   79.339490] ehci_hcd 0001:10:1b.2: irq 63, io mem 0xa0000000
[   79.339504] ehci_hcd 0001:10:1b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   79.339946] hub 4-0:1.0: USB hub found
[   79.339966] hub 4-0:1.0: 5 ports detected
[   79.484646] usbcore: registered new driver hiddev
[   79.888665] input: HID 05ac:1000 as /class/input/input4
[   79.888700] input: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0001:10:1a.0-1
[   79.910578] input: HID 05ac:1000 as /class/input/input5
[   79.910740] input: USB HID v1.11 Mouse [HID 05ac:1000] on usb-0001:10:1a.0-1
[   79.910760] usbcore: registered new driver usbhid
[   79.910767] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   80.046273] Attempting manual resume
[   80.108559] kjournald starting.  Commit interval 5 seconds
[   80.108585] EXT3-fs: mounted filesystem with ordered data mode.
[   80.599193] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000a95fffed14b90]
[   90.788660] Linux agpgart interface v0.101 (c) Dave Jones
[   90.790827] agpgart: Detected Apple UniNorth 2 chipset
[   90.790932] agpgart: configuring for size idx: 4
[   90.791002] agpgart: AGP aperture is 16M @ 0x0
[   92.955307] Yenta: CardBus bridge found at 0001:10:13.0 [0000:0000]
[   92.955343] PCI: Bus 17, cardbus bridge: 0001:10:13.0
[   92.955348]   IO window: 00001000-000011ff
[   92.955355]   IO window: 00001400-000015ff
[   92.955363]   PREFETCH window: 90000000-9fffffff
[   92.955370]   MEM window: f3000000-f33fffff
[   92.955377] Yenta: Enabling burst memory read transactions
[   92.955384] Yenta: Using CSCINT to route CSC interrupts to PCI
[   92.955388] Yenta: Routing CardBus interrupts to PCI
[   92.955396] Yenta TI: socket 0001:10:13.0, mfunc 0x00001002, devctl 0x60
[   93.058929] Yenta: ISA IRQ mask 0x0000, PCI irq 53
[   93.058939] Socket status: 30000007
[   93.058947] pcmcia: parent PCI bridge I/O window: 0x0 - 0x7fffff
[   93.058955] pcmcia: parent PCI bridge Memory window: 0xf3000000 - 0xf3ffffff
[   93.058961] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0xafffffff
[   93.085169] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[   93.151238] PHY ID: 1410cc1, addr: 0
[   93.151764] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:95:d1:4b:90 
[   93.151776] eth0: Found Marvell 88E1101 PHY
[   95.651886] input: PowerMac Beep as /class/input/input6
[   95.771759] apm_emu: APM Emulation 0.5 initialized.
[   95.967136] SCSI subsystem initialized
[   95.994770] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[   95.994781] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   95.994787] ieee1394: sbp2: Try serialize_io=0 for better performance
[   96.133532] adt746x: version 1 (supported)
[   96.133544] adt746x: Thermostat bus: 1, address: 0x2e, limit_adjust: 0, fan_speed: -1
[   96.133552] sensor 0: CPU/INTREPID BOTTOMSIDE
[   96.133557] sensor 1: CPU BOTTOMSIDE
[   96.133561] sensor 2: PWR SUPPLY BOTTOMSIDE
[   96.189370] adt746x: ADT7460 initializing
[   96.192413] adt746x: Lowering max temperatures from 81, 80, 87 to 70, 50, 70
[   96.327453] fuse init (API version 7.3)
[   96.735780] Adding 656472k swap on /dev/hda12.  Priority:-1 extents:1 across:656472k
[   97.663661] EXT3 FS on hda11, internal journal
[   99.371688] ip_tables: (C) 2000-2002 Netfilter core team
[  101.445251] NET: Registered protocol family 17
[  111.955518] [drm] Initialized drm 1.0.1 20051102
[  112.006025] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[  112.460966] lp: driver loaded but no devices found
[  112.636599] ppdev: user-space parallel port driver
[  114.483810] agpgart: Putting AGP V2 device at 0000:00:0b.0 into 4x mode
[  114.483826] agpgart: Putting AGP V2 device at 0000:00:10.0 into 4x mode
[  115.007359] [drm] Setting GART location based on new memory map
[  115.007386] [drm] Loading R300 Microcode
[  115.007451] [drm] writeback test succeeded in 1 usecs
[  140.237608] NET: Registered protocol family 10
[  140.237842] lo: Disabled Privacy Extensions
[  140.237946] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  140.238003] IPv6 over IPv4 tunneling driver


6. Network configuration: sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@0001:10:12.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=16
  *-network
       description: Ethernet interface
       product: UniNorth 2 GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:24:0f.0
       logical name: eth0
       version: 80
       serial: 00:0a:95:d1:4b:90
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=gem latency=16 maxlatency=64 mingnt=6


7. scan for networks: iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

8. ubuntu version:
$ lsb_release -d
Description:	Ubuntu 8.04.2


9. kernel/architechure (32 or 64 bit):
$ uname -mr
2.6.15-26-powerpc ppc


10. restarting the network:
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                  eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 805316956
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 805316956
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 805316956
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

Thanks for reading this far...

Mat

---

### Post by matamoscas on 2009-05-22
I figured it out.

=)


The following link pointed me in the right direction!!

enjoy:
[http://georgia.ubuntuforums.org/showthread.php?p=7230968](http://georgia.ubuntuforums.org/showthread.php?p=7230968)

---

