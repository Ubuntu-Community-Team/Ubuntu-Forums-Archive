---
title: "Problem with Huawei E398 USB modem"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by alexb888 on 2013-03-04
Hi all. I can't connect my 3G/4G/LTE USB modem ([here]("http://moscow.megafon.ru/devices/usbModem/m150-1/") is spec in Russian) under Ubuntu 12.04.2 (kernel 3.5.0-25-generic). When I connect it to laptop it detected as

lsusb
```

Bus 002 Device 004: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 002 Device 002: ID 17ef:4808 Lenovo 
Bus 005 Device 002: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

usb-devices
```

T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=01.02
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=12 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=02 Prot=16 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```

dmesg
```

[   47.368060] usb 2-4: new high-speed USB device number 3 using ehci_hcd
[   47.505107] usb 2-4: New USB device found, idVendor=12d1, idProduct=14fe
[   47.505111] usb 2-4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[   47.505115] usb 2-4: Product: HUAWEI Mobile
[   47.505118] usb 2-4: Manufacturer: HUAWEI Technology
[   47.593743] Initializing USB Mass Storage driver...
[   47.594140] scsi6 : usb-storage 2-4:1.0
[   47.594319] scsi7 : usb-storage 2-4:1.1
[   47.594412] usbcore: registered new interface driver usb-storage
[   47.594415] USB Mass Storage support registered.
[   48.592906] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   48.593012] scsi 7:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[   48.595001] sr1: scsi-1 drive
[   48.595539] sr 6:0:0:0: Attached scsi CD-ROM sr1
[   48.596319] sr 6:0:0:0: Attached scsi generic sg2 type 5
[   48.597042] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   48.599733] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[   48.793122] ISO 9660 Extensions: Microsoft Joliet Level 1
[   48.805002] ISOFS: changing to secondary root
[   49.086259] usb 2-4: USB disconnect, device number 3
[   49.460042] usb 2-4: new high-speed USB device number 4 using ehci_hcd
[   49.593110] usb 2-4: New USB device found, idVendor=12d1, idProduct=1506
[   49.593115] usb 2-4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[   49.593119] usb 2-4: Product: HUAWEI Mobile
[   49.593122] usb 2-4: Manufacturer: HUAWEI Technology
[   49.595328] scsi8 : usb-storage 2-4:1.2
[   49.595684] scsi9 : usb-storage 2-4:1.3
[   49.634308] usbcore: registered new interface driver usbserial
[   49.634687] usbcore: registered new interface driver usbserial_generic
[   49.635021] USB Serial support registered for generic
[   49.635035] usbserial: USB Serial Driver core
[   49.656631] usbcore: registered new interface driver option
[   49.656654] USB Serial support registered for GSM modem (1-port)
[   49.657426] option 2-4:1.0: GSM modem (1-port) converter detected
[   49.657641] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[   50.592889] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   50.592955] scsi 9:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[   50.594193] sd 9:0:0:0: Attached scsi generic sg2 type 0
[   50.596761] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[   50.596919] sr1: scsi-1 drive
[   50.597341] sr 8:0:0:0: Attached scsi CD-ROM sr1
[   50.597460] sr 8:0:0:0: Attached scsi generic sg3 type 5
[   50.740110] ISO 9660 Extensions: Microsoft Joliet Level 1
[   50.740994] ISOFS: changing to secondary root

```

NetworkManager also see this device and even show notification "You registered in your home GSM network". But when I try to establish connection it failed with next logs:
```

Mar  3 11:17:02 laptop kernel: [   47.368060] usb 2-4: new high-speed USB device number 3 using ehci_hcd
Mar  3 11:17:02 laptop kernel: [   47.505107] usb 2-4: New USB device found, idVendor=12d1, idProduct=14fe
Mar  3 11:17:02 laptop mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4"
Mar  3 11:17:02 laptop kernel: [   47.505111] usb 2-4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Mar  3 11:17:02 laptop kernel: [   47.505115] usb 2-4: Product: HUAWEI Mobile
Mar  3 11:17:02 laptop kernel: [   47.505118] usb 2-4: Manufacturer: HUAWEI Technology
Mar  3 11:17:02 laptop mtp-probe: bus: 2, device: 3 was not an MTP device
Mar  3 11:17:02 laptop kernel: [   47.593743] Initializing USB Mass Storage driver...
Mar  3 11:17:02 laptop kernel: [   47.594140] scsi6 : usb-storage 2-4:1.0
Mar  3 11:17:02 laptop kernel: [   47.594319] scsi7 : usb-storage 2-4:1.1
Mar  3 11:17:02 laptop kernel: [   47.594412] usbcore: registered new interface driver usb-storage
Mar  3 11:17:02 laptop kernel: [   47.594415] USB Mass Storage support registered.
Mar  3 11:17:03 laptop kernel: [   48.592906] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Mar  3 11:17:03 laptop kernel: [   48.593012] scsi 7:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Mar  3 11:17:03 laptop kernel: [   48.595001] sr1: scsi-1 drive
Mar  3 11:17:03 laptop kernel: [   48.595539] sr 6:0:0:0: Attached scsi CD-ROM sr1
Mar  3 11:17:03 laptop kernel: [   48.596319] sr 6:0:0:0: Attached scsi generic sg2 type 5
Mar  3 11:17:03 laptop kernel: [   48.597042] sd 7:0:0:0: Attached scsi generic sg3 type 0
Mar  3 11:17:03 laptop kernel: [   48.599733] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Mar  3 11:17:03 laptop kernel: [   48.793122] ISO 9660 Extensions: Microsoft Joliet Level 1
Mar  3 11:17:03 laptop kernel: [   48.805002] ISOFS: changing to secondary root
Mar  3 11:17:03 laptop usb_modeswitch: switching device 12d1:14fe on 002/003
Mar  3 11:17:03 laptop kernel: [   49.086259] usb 2-4: USB disconnect, device number 3
Mar  3 11:17:04 laptop kernel: [   49.460042] usb 2-4: new high-speed USB device number 4 using ehci_hcd
Mar  3 11:17:04 laptop kernel: [   49.593110] usb 2-4: New USB device found, idVendor=12d1, idProduct=1506
Mar  3 11:17:04 laptop kernel: [   49.593115] usb 2-4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Mar  3 11:17:04 laptop kernel: [   49.593119] usb 2-4: Product: HUAWEI Mobile
Mar  3 11:17:04 laptop kernel: [   49.593122] usb 2-4: Manufacturer: HUAWEI Technology
Mar  3 11:17:04 laptop kernel: [   49.595328] scsi8 : usb-storage 2-4:1.2
Mar  3 11:17:04 laptop kernel: [   49.595684] scsi9 : usb-storage 2-4:1.3
Mar  3 11:17:04 laptop mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4"
Mar  3 11:17:04 laptop mtp-probe: bus: 2, device: 4 was not an MTP device
Mar  3 11:17:04 laptop kernel: [   49.634308] usbcore: registered new interface driver usbserial
Mar  3 11:17:04 laptop kernel: [   49.634687] usbcore: registered new interface driver usbserial_generic
Mar  3 11:17:04 laptop kernel: [   49.635021] USB Serial support registered for generic
Mar  3 11:17:04 laptop kernel: [   49.635035] usbserial: USB Serial Driver core
Mar  3 11:17:04 laptop kernel: [   49.656631] usbcore: registered new interface driver option
Mar  3 11:17:04 laptop kernel: [   49.656654] USB Serial support registered for GSM modem (1-port)
Mar  3 11:17:04 laptop kernel: [   49.657426] option 2-4:1.0: GSM modem (1-port) converter detected
Mar  3 11:17:04 laptop kernel: [   49.657641] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
Mar  3 11:17:04 laptop modem-manager[788]: <info>  (ttyUSB0) opening serial port...
Mar  3 11:17:05 laptop usb_modeswitch: switched to 12d1:1506 on 002/003
Mar  3 11:17:05 laptop kernel: [   50.592889] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Mar  3 11:17:05 laptop kernel: [   50.592955] scsi 9:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Mar  3 11:17:05 laptop kernel: [   50.594193] sd 9:0:0:0: Attached scsi generic sg2 type 0
Mar  3 11:17:05 laptop kernel: [   50.596761] sd 9:0:0:0: [sdb] Attached SCSI removable disk
Mar  3 11:17:05 laptop kernel: [   50.596919] sr1: scsi-1 drive
Mar  3 11:17:05 laptop kernel: [   50.597341] sr 8:0:0:0: Attached scsi CD-ROM sr1
Mar  3 11:17:05 laptop kernel: [   50.597460] sr 8:0:0:0: Attached scsi generic sg3 type 5
Mar  3 11:17:05 laptop kernel: [   50.740110] ISO 9660 Extensions: Microsoft Joliet Level 1
Mar  3 11:17:05 laptop kernel: [   50.740994] ISOFS: changing to secondary root
Mar  3 11:17:06 laptop usb_modeswitch[1891]: usb_modeswitch: switched to 12d1:1506 on 2/4
Mar  3 11:17:09 laptop modem-manager[788]: <info>  (ttyUSB0) closing serial port...
Mar  3 11:17:09 laptop modem-manager[788]: <info>  (ttyUSB0) serial port closed
Mar  3 11:17:09 laptop modem-manager[788]: <info>  (ttyUSB0) opening serial port...
Mar  3 11:17:09 laptop modem-manager[788]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4 claimed port ttyUSB0
Mar  3 11:17:09 laptop modem-manager[788]: <info>  (ttyUSB0) closing serial port...
Mar  3 11:17:09 laptop modem-manager[788]: <info>  (ttyUSB0) serial port closed
Mar  3 11:17:09 laptop NetworkManager[880]: <warn> (ttyUSB0): failed to look up interface index
Mar  3 11:17:09 laptop NetworkManager[880]: <info> (ttyUSB0): new GSM/UMTS device (driver: 'option1' ifindex: 0)
Mar  3 11:17:09 laptop NetworkManager[880]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/2
Mar  3 11:17:09 laptop NetworkManager[880]: <info> (ttyUSB0): now managed
Mar  3 11:17:09 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  3 11:17:09 laptop NetworkManager[880]: <info> (ttyUSB0): deactivating device (reason 'managed') [2]
Mar  3 11:17:09 laptop NetworkManager[880]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Mar  3 11:17:09 laptop NetworkManager[880]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Mar  3 11:17:09 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Mar  3 11:17:44 laptop dbus[775]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Mar  3 11:17:46 laptop AptDaemon: INFO: Initializing daemon
Mar  3 11:17:46 laptop AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Mar  3 11:17:46 laptop dbus[775]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Mar  3 11:17:46 laptop AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Mar  3 11:17:46 laptop AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/4f87c3d0361a4523bf951968ba4971b8
Mar  3 11:17:46 laptop AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/4f87c3d0361a4523bf951968ba4971b8
Mar  3 11:17:49 laptop AptDaemon.PackageKit: INFO: Get updates()
Mar  3 11:17:50 laptop AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/4f87c3d0361a4523bf951968ba4971b8
Mar  3 11:18:03 laptop kernel: [  108.607542] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
Mar  3 11:18:09 laptop NetworkManager[880]: <info> Activation (ttyUSB0) starting connection 'Megafon'
Mar  3 11:18:09 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar  3 11:18:09 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  3 11:18:09 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Mar  3 11:18:09 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Mar  3 11:18:09 laptop modem-manager[788]: <info>  (ttyUSB0) opening serial port...
Mar  3 11:18:09 laptop modem-manager[788]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Mar  3 11:18:10 laptop modem-manager[788]: <info>  (ttyUSB0): using text mode for SMS
Mar  3 11:18:10 laptop modem-manager[788]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Mar  3 11:18:10 laptop NetworkManager[880]: <info> WWAN now enabled by management service
Mar  3 11:18:10 laptop modem-manager[788]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Mar  3 11:18:10 laptop modem-manager[788]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Mar  3 11:18:10 laptop modem-manager[788]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Mar  3 11:18:10 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
Mar  3 11:18:10 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar  3 11:18:10 laptop NetworkManager[880]: <info> starting PPP connection
Mar  3 11:18:10 laptop NetworkManager[880]: <info> pppd started with pid 2155
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar  3 11:18:10 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar  3 11:18:10 laptop pppd[2155]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Mar  3 11:18:10 laptop pppd[2155]: pppd 2.4.5 started by root, uid 0
Mar  3 11:18:10 laptop pppd[2155]: Using interface ppp0
Mar  3 11:18:10 laptop pppd[2155]: Connect: ppp0 <--> /dev/ttyUSB0
Mar  3 11:18:10 laptop NetworkManager[880]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar  3 11:18:10 laptop NetworkManager[880]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Mar  3 11:18:30 laptop NetworkManager[880]: <warn> pppd timed out or didn't initialize our dbus module
Mar  3 11:18:30 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Mar  3 11:18:30 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Mar  3 11:18:30 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar  3 11:18:30 laptop NetworkManager[880]: <warn> Activation (ttyUSB0) failed.
Mar  3 11:18:30 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Mar  3 11:18:30 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar  3 11:18:30 laptop NetworkManager[880]: <info> (ttyUSB0): deactivating device (reason 'none') [0]
Mar  3 11:18:30 laptop NetworkManager[880]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Mar  3 11:18:30 laptop NetworkManager[880]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Mar  3 11:18:30 laptop pppd[2155]: Terminating on signal 15
Mar  3 11:18:30 laptop modem-manager[788]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
Mar  3 11:18:32 laptop avahi-daemon[847]: Withdrawing workstation service for ppp0.
Mar  3 11:18:32 laptop NetworkManager[880]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar  3 11:18:35 laptop modem-manager[788]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> registered)
Mar  3 11:19:29 laptop NetworkManager[880]: <info> Activation (ttyUSB0) starting connection 'Megafon'
Mar  3 11:19:29 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar  3 11:19:29 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  3 11:19:29 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Mar  3 11:19:29 laptop NetworkManager[880]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Mar  3 11:19:36 laptop NetworkManager[880]: <warn> GSM connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Mar  3 11:19:36 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Mar  3 11:19:36 laptop NetworkManager[880]: <warn> Activation (ttyUSB0) failed.
Mar  3 11:19:36 laptop NetworkManager[880]: <info> (ttyUSB0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar  3 11:19:36 laptop NetworkManager[880]: <info> (ttyUSB0): deactivating device (reason 'none') [0]
Mar  3 11:19:36 laptop NetworkManager[880]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Mar  3 11:19:36 laptop NetworkManager[880]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed

```

Any ideas what's wrong and how to fix this? Many thanks for help and sorry for my English

---

### Post by bmork on 2013-03-20
> **alexb888 said:**
> Hi all. I can't connect my 3G/4G/LTE USB modem ([here]("http://moscow.megafon.ru/devices/usbModem/m150-1/") is spec in Russian) under Ubuntu 12.04.2 (kernel 3.5.0-25-generic). When I connect it to laptop it detected as

lusb-devices
```

T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=01.02
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=12 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=02 Prot=16 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```


Right.  This looks like firmware we've seen in the Huawei E3276 before.  Googling that will provide some more details, but the basic issues are:
[LIST=1]
[*]the serial port is only for connection/device management.  PPP is not supported! 
[*]if#1 is really a CDC NCM function, but needs a recent patch to the cdc_ncm driver to be recognised as such 
[/LIST]


So to use this, you need the commit

  ```
bbc8d92 net: cdc_ncm: add Huawei devices

```
which first appeared in Linux v3.7.  It was also backported to stable-3.6.  I don't know the status wrt 3.5.  Could be planned there as well.  The Ubuntu folks will know more about that.

You also need a very recent ModemManager with support for these devices.  The connection is started and stopped using the Huawei proprietary AT^NDISDUP command, and the only available data channel is the wwanX interface provided by the cdc_ncm driver.

---

