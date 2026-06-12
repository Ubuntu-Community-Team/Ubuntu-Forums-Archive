---
title: "linksys wireless networking issues"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by Chad Likehart on 2009-03-18
Hello all,

I am currently using the ububtu 8.04 download. I am new to linux and really want to learn it.  I just bought the linksys wpc600n NIC hoping that it would link up properly. It didn't. Linux recognizes the windows driver.....now what????I am including copied data from a few of the commands i have learned so far. So here they are. Any direction on how to get this lan working would be greatly appreciated.
u18 
[   41.620531] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection 
[   42.214856] pccard: CardBus card inserted into slot 0 
[   42.641158] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa0b1, caps: 0xa04713/0x20040a 
[   42.678789] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input10 
[   43.824069] ipw2200: Radio Frequency Kill Switch is On: 
[   43.824072] Kill switch must be turned off for wireless networking to work. 
[   43.825374] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels) 
[   43.932276] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   44.016810] ndiswrapper: driver bcmwl5 (Linksys, A Division of Cisco Systems, Inc.,07/18/2007, 4.150.31.0) loaded 
[   44.016987] PCI: Enabling device 0000:02:00.0 (0000 -> 0002) 
[   44.016995] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 16 
[   44.017027] PCI: Setting latency timer of device 0000:02:00.0 to 64 
[   44.041899] ndiswrapper: using IRQ 16 
[   44.147892] cs: IO port probe 0x100-0x3af: clean. 
[   44.149563] cs: IO port probe 0x3e0-0x4ff: clean. 
[   44.150030] cs: IO port probe 0x820-0x8ff: clean. 
[   44.150378] cs: IO port probe 0xc00-0xcf7: clean. 
[   44.151096] cs: IO port probe 0xa00-0xaff: clean. 
[   44.163577] wlan0: ethernet device 00:1e:e5:fa:d7:4b using NDIS driver: bcmwl5, version: 0x4961f00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf 
[   44.163622] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[   44.164327] usbcore: registered new interface driver ndiswrapper 
[   44.277906] lp: driver loaded but no devices found 
[   44.469641] Adding 1975952k swap on /dev/sda7.  Priority:-1 extents:1 across:1975952k 
[   44.903320] EXT3 FS on sda6, internal journal 
[   45.576990] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   46.005248] No dock devices found. 
[   46.943192] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
[   46.943196] apm: overridden by ACPI. 
[   47.078049] ppdev: user-space parallel port driver 
[   47.252917] audit(1237349199.687:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4972 profile="/usr/sbin/cupsd" namespace="default" 
[   89.016984] Marking TSC unstable due to: cpufreq changes. 
[  125.406429] r8169: eth0: link down 
[   62.807461] Bluetooth: Core ver 2.11 
[   62.807868] NET: Registered protocol family 31 
[   62.807871] Bluetooth: HCI device and connection manager initialized 
[   62.807875] Bluetooth: HCI socket layer initialized 
[   62.842953] Bluetooth: L2CAP ver 2.9 
[   62.842957] Bluetooth: L2CAP socket layer initialized 
[   62.928448] Bluetooth: RFCOMM socket layer initialized 
[   62.928462] Bluetooth: RFCOMM TTY layer initialized 
[   62.928464] Bluetooth: RFCOMM ver 1.8 
[   54.568539] [drm] Initialized drm 1.1.0 20060810 
[   54.571494] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20 
[   54.571501] PCI: Setting latency timer of device 0000:00:02.0 to 64 
[   54.571557] [drm] Initialized i915 1.6.0 20060119 on minor 0 
[  162.527782] NET: Registered protocol family 10 
[  162.528903] lo: Disabled Privacy Extensions 
[  162.530242] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  191.241748] UDF-fs: No VRS found 
[  191.275579] ISO 9660 Extensions: Microsoft Joliet Level 3 
[  191.304113] ISOFS: changing to secondary root 
chad@chad-laptop:~$ 
chad@chad-laptop:~$ iwconfig wlan0 
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

chad@chad-laptop:~$ 
Help. Not sure how to read this yet.

Thank you.

---

