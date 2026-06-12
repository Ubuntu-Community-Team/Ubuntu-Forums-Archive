---
title: "Sierra Wireless 313u (AT&amp;T Laptop Connect) on 13.04 Raring"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by phenym on 2013-06-01
Is anybody else having trouble using their aircard on 13.04?

It seems like it's detected and modem-manager starts to go to work on it, but nothing shows up in network manager.

I have been through all the threads on here, through sierra's linux howto, and tried usb_modeswitch to get it out of mmc mode, but I think that the problem may be either modem-manager or network-manager.

syslog shows:

> 
Jun  1 22:34:29 computer kernel: [ 7811.712063] usb 1-3: new high-speed USB device number 18 using ehci-pci
Jun  1 22:34:29 computer kernel: [ 7811.845670] usb 1-3: config 1 has an invalid interface number: 9 but max is 0
Jun  1 22:34:29 computer kernel: [ 7811.845682] usb 1-3: config 1 has no interface number 0
Jun  1 22:34:29 computer kernel: [ 7811.847663] usb 1-3: New USB device found, idVendor=1199, idProduct=0fff
Jun  1 22:34:29 computer kernel: [ 7811.847671] usb 1-3: New USB device strings: Mfr=3, Product=2, SerialNumber=4
Jun  1 22:34:29 computer kernel: [ 7811.847679] usb 1-3: Product: USB MMC Storage
Jun  1 22:34:29 computer kernel: [ 7811.847685] usb 1-3: Manufacturer: Sierra Wireless, Incorporated
Jun  1 22:34:29 computer kernel: [ 7811.847692] usb 1-3: SerialNumber: SWOC22905731
Jun  1 22:34:29 computer kernel: [ 7811.850351] usb-storage: probe of 1-3:1.9 failed with error -5
Jun  1 22:34:29 computer mtp-probe: checking bus 1, device 18: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3"
Jun  1 22:34:29 computer mtp-probe: bus: 1, device: 18 was not an MTP device
Jun  1 22:34:31 computer usb_modeswitch: switching device 1199:0fff on 001/018
Jun  1 22:34:32 computer kernel: [ 7814.693743] usb 1-3: USB disconnect, device number 18
Jun  1 22:34:32 computer kernel: [ 7815.060280] usb 1-3: new high-speed USB device number 19 using ehci-pci
Jun  1 22:34:32 computer kernel: [ 7815.193966] usb 1-3: config 1 has an invalid interface number: 9 but max is 6
Jun  1 22:34:32 computer kernel: [ 7815.193978] usb 1-3: config 1 has an invalid interface number: 7 but max is 6
Jun  1 22:34:32 computer kernel: [ 7815.193985] usb 1-3: config 1 has no interface number 5
Jun  1 22:34:32 computer kernel: [ 7815.193991] usb 1-3: config 1 has no interface number 6
Jun  1 22:34:32 computer kernel: [ 7815.196405] usb 1-3: New USB device found, idVendor=0f3d, idProduct=68aa
Jun  1 22:34:32 computer kernel: [ 7815.196419] usb 1-3: New USB device strings: Mfr=3, Product=2, SerialNumber=4
Jun  1 22:34:32 computer kernel: [ 7815.196426] usb 1-3: Product: AirCard 313U
Jun  1 22:34:32 computer kernel: [ 7815.196433] usb 1-3: Manufacturer: Sierra Wireless, Incorporated
Jun  1 22:34:32 computer kernel: [ 7815.196440] usb 1-3: SerialNumber: 012615002626365
Jun  1 22:34:32 computer kernel: [ 7815.198640] sierra 1-3:1.0: Sierra USB modem converter detected
Jun  1 22:34:32 computer kernel: [ 7815.199200] usb 1-3: Sierra USB modem converter now attached to ttyUSB0
Jun  1 22:34:32 computer kernel: [ 7815.199356] sierra 1-3:1.1: Sierra USB modem converter detected
Jun  1 22:34:32 computer kernel: [ 7815.200088] usb 1-3: Sierra USB modem converter now attached to ttyUSB1
Jun  1 22:34:32 computer kernel: [ 7815.200239] sierra 1-3:1.2: Sierra USB modem converter detected
Jun  1 22:34:32 computer kernel: [ 7815.201053] usb 1-3: Sierra USB modem converter now attached to ttyUSB2
Jun  1 22:34:32 computer kernel: [ 7815.201210] sierra 1-3:1.3: Sierra USB modem converter detected
Jun  1 22:34:32 computer kernel: [ 7815.201682] usb 1-3: Sierra USB modem converter now attached to ttyUSB3
Jun  1 22:34:32 computer kernel: [ 7815.201861] sierra 1-3:1.4: Sierra USB modem converter detected
Jun  1 22:34:32 computer kernel: [ 7815.202293] usb 1-3: Sierra USB modem converter now attached to ttyUSB4
Jun  1 22:34:32 computer kernel: [ 7815.202643] scsi23 : usb-storage 1-3:1.9
Jun  1 22:34:32 computer kernel: [ 7815.205618] sierra_net 1-3:1.7 wwan0: register 'sierra_net' at usb-0000:00:1a.7-3, Sierra Wireless USB-to-WWAN Modem, 02:41:57:1a:09:07
Jun  1 22:34:32 computer mtp-probe: checking bus 1, device 19: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3"
Jun  1 22:34:32 computer mtp-probe: bus: 1, device: 19 was not an MTP device
Jun  1 22:34:33 computer modem-manager[8362]: <info>  (ttyUSB4) opening serial port...
Jun  1 22:34:33 computer modem-manager[8362]: <warn>  (ttyUSB4): port attributes not fully set
Jun  1 22:34:33 computer modem-manager[8362]: <info>  (ttyUSB1) opening serial port...
Jun  1 22:34:33 computer modem-manager[8362]: <warn>  (ttyUSB1): port attributes not fully set
Jun  1 22:34:33 computer NetworkManager[1096]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.7/net/wwan0, iface: wwan0)
Jun  1 22:34:33 computer NetworkManager[1096]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.7/net/wwan0, iface: wwan0): no ifupdown configuration found.
Jun  1 22:34:33 computer modem-manager[8362]: <info>  (ttyUSB3) opening serial port...
Jun  1 22:34:33 computer modem-manager[8362]: <warn>  (ttyUSB3): port attributes not fully set
Jun  1 22:34:33 computer modem-manager[8362]: <info>  (ttyUSB2) opening serial port...
Jun  1 22:34:33 computer modem-manager[8362]: <warn>  (ttyUSB2): port attributes not fully set
Jun  1 22:34:33 computer modem-manager[8362]: <info>  (ttyUSB0) opening serial port...
Jun  1 22:34:33 computer modem-manager[8362]: <warn>  (ttyUSB0): port attributes not fully set
Jun  1 22:34:33 computer kernel: [ 7816.201720] scsi 23:0:0:0: Direct-Access     SWI      SD Card          2.31 PQ: 0 ANSI: 2
Jun  1 22:34:33 computer kernel: [ 7816.203313] sd 23:0:0:0: Attached scsi generic sg3 type 0
Jun  1 22:34:33 computer kernel: [ 7816.211781] sd 23:0:0:0: [sdc] Attached SCSI removable disk
Jun  1 22:34:36 computer modem-manager[8362]: <info>  (ttyUSB4) opening serial port...
Jun  1 22:34:36 computer modem-manager[8362]: <warn>  (ttyUSB4): port attributes not fully set
Jun  1 22:34:37 computer modem-manager[8362]: <info>  (ttyUSB3) closing serial port...
Jun  1 22:34:37 computer modem-manager[8362]: <info>  (ttyUSB3) serial port closed
Jun  1 22:34:37 computer modem-manager[8362]: <info>  (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3 claimed port ttyUSB3
Jun  1 22:34:39 computer modem-manager[8362]: <info>  (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3 claimed port wwan0
Jun  1 22:34:44 computer modem-manager[8362]: <info>  (ttyUSB1) closing serial port...
Jun  1 22:34:44 computer modem-manager[8362]: <info>  (ttyUSB1) serial port closed
Jun  1 22:34:44 computer modem-manager[8362]: <info>  (ttyUSB1) opening serial port...
Jun  1 22:34:44 computer modem-manager[8362]: <info>  (ttyUSB2) closing serial port...
Jun  1 22:34:44 computer modem-manager[8362]: <info>  (ttyUSB2) serial port closed
Jun  1 22:34:44 computer modem-manager[8362]: <info>  (ttyUSB2) opening serial port...
Jun  1 22:34:44 computer modem-manager[8362]: <info>  (ttyUSB1) closing serial port...
Jun  1 22:34:44 computer modem-manager[8362]: <info>  (ttyUSB1) serial port closed
Jun  1 22:34:45 computer modem-manager[8362]: <info>  (ttyUSB0) closing serial port...
Jun  1 22:34:45 computer modem-manager[8362]: <info>  (ttyUSB0) serial port closed
Jun  1 22:34:45 computer modem-manager[8362]: <info>  (ttyUSB0) opening serial port...
Jun  1 22:34:48 computer modem-manager[8362]: <info>  (ttyUSB4) closing serial port...
Jun  1 22:34:48 computer modem-manager[8362]: <info>  (ttyUSB4) serial port closed
Jun  1 22:34:48 computer modem-manager[8362]: <info>  (ttyUSB4) opening serial port...
Jun  1 22:34:48 computer modem-manager[8362]: <info>  (ttyUSB0) closing serial port...
Jun  1 22:34:48 computer modem-manager[8362]: <info>  (ttyUSB0) serial port closed
Jun  1 22:34:50 computer modem-manager[8362]: <info>  (ttyUSB2) closing serial port...
Jun  1 22:34:50 computer modem-manager[8362]: <info>  (ttyUSB2) serial port closed
Jun  1 22:34:54 computer modem-manager[8362]: <info>  (ttyUSB4) closing serial port...
Jun  1 22:34:54 computer modem-manager[8362]: <info>  (ttyUSB4) serial port closed
Jun  1 22:34:55 computer NetworkManager[1096]: <info> the modem manager disappeared
Jun  1 22:34:55 computer dbus[959]: [system] Activating service name='org.freedesktop.ModemManager' (using servicehelper)
Jun  1 22:34:55 computer modem-manager[10213]: <info>  ModemManager (version 0.6.0.0) starting...
Jun  1 22:34:55 computer dbus[959]: [system] Successfully activated service 'org.freedesktop.ModemManager'
Jun  1 22:34:55 computer NetworkManager[1096]: <info> modem-manager is now available
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Gobi'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Option High-Speed'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Sierra'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Option'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Wavecom'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Novatel'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'SimTech'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'MotoC'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'X22X'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Ericsson MBM'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'AnyData'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Samsung'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Longcheer'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Huawei'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'ZTE'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Linktop'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Nokia'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Cinterion'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Iridium'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Loaded plugin 'Generic'
Jun  1 22:34:55 computer modem-manager[10213]: <info>  Successfully loaded 20 plugins
Jun  1 22:34:55 computer modem-manager[10213]: <info>  (ttyUSB0) opening serial port...
Jun  1 22:34:55 computer modem-manager[10213]: <warn>  (ttyUSB0): port attributes not fully set
Jun  1 22:34:55 computer modem-manager[10213]: <info>  (ttyUSB1) opening serial port...
Jun  1 22:34:55 computer modem-manager[10213]: <warn>  (ttyUSB1): port attributes not fully set
Jun  1 22:34:55 computer modem-manager[10213]: <info>  (ttyUSB2) opening serial port...
Jun  1 22:34:55 computer modem-manager[10213]: <warn>  (ttyUSB2): port attributes not fully set
Jun  1 22:34:55 computer modem-manager[10213]: <info>  (ttyUSB3) opening serial port...
Jun  1 22:34:55 computer modem-manager[10213]: <warn>  (ttyUSB3): port attributes not fully set
Jun  1 22:34:55 computer modem-manager[10213]: <info>  (ttyUSB4) opening serial port...
Jun  1 22:34:55 computer modem-manager[10213]: <warn>  (ttyUSB4): port attributes not fully set
Jun  1 22:34:57 computer modem-manager[10213]: <info>  (ttyUSB3) closing serial port...
Jun  1 22:34:57 computer modem-manager[10213]: <info>  (ttyUSB3) serial port closed
Jun  1 22:34:57 computer modem-manager[10213]: <info>  (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3 claimed port ttyUSB3
Jun  1 22:34:57 computer modem-manager[10213]: <info>  (ttyUSB4) closing serial port...
Jun  1 22:34:57 computer modem-manager[10213]: <info>  (ttyUSB4) serial port closed
Jun  1 22:34:57 computer modem-manager[10213]: <info>  (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3 claimed port ttyUSB4
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB0) closing serial port...
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB0) serial port closed
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB0) opening serial port...
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB1) closing serial port...
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB1) serial port closed
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB1) opening serial port...
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB2) closing serial port...
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB2) serial port closed
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB2) opening serial port...
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB1) closing serial port...
Jun  1 22:35:07 computer modem-manager[10213]: <info>  (ttyUSB1) serial port closed
Jun  1 22:35:11 computer modem-manager[10213]: <info>  (ttyUSB0) closing serial port...
Jun  1 22:35:11 computer modem-manager[10213]: <info>  (ttyUSB0) serial port closed
Jun  1 22:35:13 computer modem-manager[10213]: <info>  (ttyUSB2) closing serial port...
Jun  1 22:35:13 computer modem-manager[10213]: <info>  (ttyUSB2) serial port closed


lsusb:

> 
Bus 001 Device 019: ID 0f3d:68aa Airprime, Incorporated 
Bus 002 Device 002: ID 5986:0143 Acer, Inc 
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Help!

---

### Post by High1ander on 2013-09-13
Excuse me, was your modem working on 12.04 LTS? Planning to purchase that model, need to know.

---

### Post by ken-zwn on 2013-09-13
> **High1ander said:**
> Excuse me, was your modem working on 12.04 LTS? Planning to purchase that model, need to know.

I never had 12.04... It was working fine in 10.04. I did eventually get it working in 13.04 after some trial and error with modemmanager (had to build from source).

---

### Post by High1ander on 2013-09-14
> **ken-zwn said:**
> I never had 12.04... It was working fine in 10.04. I did eventually get it working in 13.04 after some trial and error with modemmanager (had to build from source).

Thanks, and could you please give more detail, how you made it to work on 13.04? Thank you in advance.

---

