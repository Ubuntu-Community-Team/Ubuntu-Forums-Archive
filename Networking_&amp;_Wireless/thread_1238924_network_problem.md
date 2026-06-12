---
title: "network problem"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by Rajwinder on 2009-08-12
I am using ubuntu 9.04.whenever i start my pc its network shows disconnected.after rebooting several times it gets connected and works fine until next reboot or shutdown.i have two lan cards.eth0 and eth1. I am using eth0 configured through NM. Any suggestions and help please.

---

### Post by arky on 2009-08-13
check the logs in /var/log/ for any network related errors

---

### Post by Rajwinder on 2009-08-13
dear arky
i checked the log it seems that first time the eth0 driver does not get loaded.
here are logs of both times when network worked and when it did not

Log when network did not worked

   2.517874] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    2.517878] Copyright (c) 1999-2006 Intel Corporation.
[    2.517922] e1000 0000:04:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.574093] e1000: 0000:04:05.0: e1000_probe: (PCI:33MHz:32-bit) 00:19:d1:74:8a:92
[    2.680550] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    2.758787] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    2.856280] usb 4-2: configuration #1 chosen from 1 choice
[    2.883404] usbcore: registered new interface driver hiddev
[    2.896432] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4
[    2.933419] generic-usb 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    2.933444] usbcore: registered new interface driver usbhid
[    2.933448] usbhid: v2.6:USB HID core driver
[    3.189220] PM: Starting manual resume from disk
[    3.189225] PM: Resume from partition 8:21
[    3.189227] PM: Checking hibernation image.
[    3.189400] PM: Resume from disk failed.
[    3.211454] kjournald starting.  Commit interval 5 seconds
[    3.211468] EXT3-fs: mounted filesystem with ordered data mode.
[    5.315081] udev: starting version 141
[    5.428523] EDAC MC: Ver: 2.1.0 Jul 25 2009
[    5.475554] EDAC MC0: Giving out device to 'i3000_edac' 'i3000': DEV 0000:00:00.0
[    5.475687] EDAC PCI0: Giving out device to module 'i3000_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
[    5.491075] udev: renamed network interface eth0 to eth1
[    5.505409] intel_rng: Firmware space is locked read-only. If you can't or
[    5.505411] intel_rng: don't want to disable this in firmware setup, and if
[    5.505413] intel_rng: you are certain that your system has a functional
[    5.505414] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    5.533489] iTCO_vendor_support: vendor-support=0
[    5.535306] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    5.535479] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[    5.535570] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    5.605784] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    6.292533] lp: driver loaded but no devices found



Log when network worked


    2.489802] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.489806] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.489877] e1000e 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.489889] e1000e 0000:03:00.0: setting latency timer to 64
[    2.490103] e1000e 0000:03:00.0: irq 2300 for MSI/MSI-X
[    2.523163] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    2.523167] Copyright (c) 1999-2006 Intel Corporation.
[    2.523217] e1000 0000:04:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.573928] e1000: 0000:04:05.0: e1000_probe: (PCI:33MHz:32-bit) 00:19:d1:74:8a:92
[    2.613610] 0000:03:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:74:8a:91
[    2.613614] 0000:03:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.613768] 0000:03:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
[    2.692637] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    2.743360] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[    2.871191] usb 4-2: configuration #1 chosen from 1 choice
[    2.894138] usbcore: registered new interface driver hiddev
[    2.907358] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4
[    2.983547] generic-usb 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    2.983573] usbcore: registered new interface driver usbhid
[    2.983577] usbhid: v2.6:USB HID core driver
[    3.119137] PM: Starting manual resume from disk
[    3.119142] PM: Resume from partition 8:21
[    3.119145] PM: Checking hibernation image.
[    3.119289] PM: Resume from disk failed.
[    3.156032] kjournald starting.  Commit interval 5 seconds
[    3.156045] EXT3-fs: mounted filesystem with ordered data mode.
[    5.247422] udev: starting version 141
[    5.335973] EDAC MC: Ver: 2.1.0 Jul 25 2009
[    5.343097] EDAC MC0: Giving out device to 'i3000_edac' 'i3000': DEV 0000:00:00.0
[    5.343207] EDAC PCI0: Giving out device to module 'i3000_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
[    5.437431] intel_rng: Firmware space is locked read-only. If you can't or
[    5.437434] intel_rng: don't want to disable this in firmware setup, and if
[    5.437435] intel_rng: you are certain that your system has a functional
[    5.437437] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    5.467032] iTCO_vendor_support: vendor-support=0
[    5.468778] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    5.468960] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[    5.469052] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    5.522305] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    6.123779] lp: driver loaded but no devices found

---

### Post by arky on 2009-08-13
Try these commands and watch for any errors with 'sudo tail -f /var/log/messages ' 

sudo /etc/init.d/networking restart 

route 


sudo /sbin/dhclinet

---

### Post by Rajwinder on 2009-08-13
I am not using dhcp. i am using manual conf. After running ur commands the output is
~# sudo tail -f /var/log/messages 
Aug 13 11:39:12 rsg kernel: [   15.906129] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 13 11:39:12 rsg kernel: [   15.906133] Bluetooth: BNEP filters: protocol multicast
Aug 13 11:39:12 rsg kernel: [   15.915906] Bridge firewalling registered
Aug 13 11:39:14 rsg kernel: [   18.099436] pci 0000:04:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 13 11:39:14 rsg kernel: [   18.684040] ppdev: user-space parallel port driver
Aug 13 11:39:19 rsg kernel: [   22.721574] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 13 11:39:19 rsg kernel: [   22.801444] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 13 11:39:20 rsg kernel: [   24.314431] 0000:03:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Aug 13 11:39:20 rsg kernel: [   24.314436] 0000:03:00.0: eth0: 10/100 speed: disabling TSO
Aug 13 11:39:20 rsg kernel: [   24.314682] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

---

### Post by Iowan on 2009-08-13
How are cards configured? If both are in same subnet, it might cause problems.

---

### Post by Rajwinder on 2009-08-13
i have configured only eth0 by NM. have not configured eth1 and it is disconnected.

---

