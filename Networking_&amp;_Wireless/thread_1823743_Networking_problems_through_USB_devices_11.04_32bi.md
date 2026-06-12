---
title: "Networking problems through USB devices 11.04 32bit"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by aero13972486 on 2011-08-12
Hi
I have a D-Link DWA-126 usb wifi device. It won't connect to my wifi.

I didn't install any extra drivers for it, just plugged it in and it seemed happy enough. Its picking up all the WLAN in the area, but not letting me connect.

I'm still waiting for a custom driver from [http://linuxwireless.org/en/users/Devices/USB](http://linuxwireless.org/en/users/Devices/USB)

I also can't get my Huawei e180 usb GSM modem working with my PC, running 11.04 32bit. The modem works with my notebook running 10.04 and it worked on my PC before with 11.04 64bit.

I'm guessing it might be some configuration file that changed, but now I'm really just guessing. Any ideas?

THanks
aero

---

### Post by aero13972486 on 2011-08-12
this is the 'tailf /var/log/syslog' output while the D-Link is trying to connect:


[FONT=Courier New][SIZE=1][COLOR=Black]Aug 12 19:28:40 sarasvati kernel: [   45.796026] wlan0: direct probe to 00:04:ed:51:c6:04 timed out
Aug 12 19:28:49 sarasvati wpa_supplicant[833]: Authentication with 00:04:ed:51:c6:04 timed out.
Aug 12 19:28:49 sarasvati NetworkManager[673]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Aug 12 19:28:49 sarasvati NetworkManager[673]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug 12 19:28:50 sarasvati wpa_supplicant[833]: Trying to associate with 00:04:ed:51:c6:04 (SSID='vikramasila' freq=2412 MHz)
Aug 12 19:28:50 sarasvati NetworkManager[673]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 12 19:28:51 sarasvati kernel: [   56.505738] wlan0: direct probe to 00:04:ed:51:c6:04 (try 1/3)
Aug 12 19:28:51 sarasvati kernel: [   56.704029] wlan0: direct probe to 00:04:ed:51:c6:04 (try 2/3)
Aug 12 19:28:51 sarasvati kernel: [   56.904029] wlan0: direct probe to 00:04:ed:51:c6:04 (try 3/3)
Aug 12 19:28:51 sarasvati kernel: [   57.104026] wlan0: direct probe to 00:04:ed:51:c6:04 timed out
Aug 12 19:29:01 sarasvati wpa_supplicant[833]: Authentication with 00:04:ed:51:c6:04 timed out.
Aug 12 19:29:01 sarasvati NetworkManager[673]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Aug 12 19:29:01 sarasvati NetworkManager[673]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug 12 19:29:02 sarasvati wpa_supplicant[833]: Trying to associate with 00:04:ed:51:c6:04 (SSID='vikramasila' freq=2412 MHz)
Aug 12 19:29:02 sarasvati NetworkManager[673]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 12 19:29:02 sarasvati kernel: [   67.801987] wlan0: direct probe to 00:04:ed:51:c6:04 (try 1/3)
Aug 12 19:29:02 sarasvati kernel: [   68.000034] wlan0: direct probe to 00:04:ed:51:c6:04 (try 2/3)
Aug 12 19:29:02 sarasvati kernel: [   68.200027] wlan0: direct probe to 00:04:ed:51:c6:04 (try 3/3)
Aug 12 19:29:03 sarasvati kernel: [   68.400028] wlan0: direct probe to 00:04:ed:51:c6:04 timed out
Aug 12 19:29:08 sarasvati NetworkManager[673]: <warn> (wlan0): link timed out.
Aug 12 19:29:12 sarasvati wpa_supplicant[833]: Authentication with 00:04:ed:51:c6:04 timed out.
Aug 12 19:29:12 sarasvati NetworkManager[673]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Aug 12 19:29:12 sarasvati NetworkManager[673]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug 12 19:29:12 sarasvati NetworkManager[673]: <info> (wlan0): supplicant connection state:  disconnected -> scanning[/COLOR][/SIZE][/FONT]

---

### Post by gordintoronto on 2011-08-12
Did you go into "edit connections" to specify wpa security, and the password? (One assumes that a router will be set up with wpa security, since anything else is an invitation to disaster.)

---

### Post by aero13972486 on 2011-08-12
Yes my notebook is connecting fine with same password and security type.

---

### Post by aero13972486 on 2011-08-12
Here is 'tailf /var/log/syslog' output for the usb GSM modem set to autoconnect
plug in, connect, drop, connect, drop, remove:

[FONT=Courier New][SIZE=1]
Aug 12 23:30:50 sarasvati kernel: [ 1172.408048] usb 1-2: new high speed USB device using ehci_hcd and address 4
Aug 12 23:30:50 sarasvati kernel: [ 1172.649863] usbcore: registered new interface driver uas
Aug 12 23:30:50 sarasvati kernel: [ 1172.758460] Initializing USB Mass Storage driver...
Aug 12 23:30:50 sarasvati kernel: [ 1172.759112] scsi4 : usb-storage 1-2:1.0
Aug 12 23:30:50 sarasvati kernel: [ 1172.759190] usb 1-2: USB disconnect, address 4
Aug 12 23:30:50 sarasvati kernel: [ 1172.759655] scsi5 : usb-storage 1-2:1.1
Aug 12 23:30:50 sarasvati kernel: [ 1172.761191] usbcore: registered new interface driver usb-storage
Aug 12 23:30:50 sarasvati kernel: [ 1172.761199] USB Mass Storage support registered.
Aug 12 23:30:55 sarasvati kernel: [ 1177.720038] usb 1-2: new high speed USB device using ehci_hcd and address 5
Aug 12 23:30:55 sarasvati kernel: [ 1177.869655] scsi8 : usb-storage 1-2:1.2
Aug 12 23:30:55 sarasvati kernel: [ 1177.870587] scsi9 : usb-storage 1-2:1.3
Aug 12 23:30:55 sarasvati kernel: [ 1177.939677] usbcore: registered new interface driver usbserial
Aug 12 23:30:55 sarasvati kernel: [ 1177.939736] USB Serial support registered for generic
Aug 12 23:30:55 sarasvati kernel: [ 1177.939736] USB Serial support registered for generic
Aug 12 23:30:55 sarasvati kernel: [ 1177.943656] usbcore: registered new interface driver usbserial_generic
Aug 12 23:30:55 sarasvati kernel: [ 1177.943671] usbserial: USB Serial Driver core
Aug 12 23:30:55 sarasvati kernel: [ 1177.978142] USB Serial support registered for GSM modem (1-port)
Aug 12 23:30:55 sarasvati kernel: [ 1177.979640] option 1-2:1.0: GSM modem (1-port) converter detected
Aug 12 23:30:55 sarasvati kernel: [ 1177.980571] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Aug 12 23:30:55 sarasvati kernel: [ 1177.980607] option 1-2:1.1: GSM modem (1-port) converter detected
Aug 12 23:30:55 sarasvati kernel: [ 1177.980902] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Aug 12 23:30:55 sarasvati kernel: [ 1177.982511] usbcore: registered new interface driver option
Aug 12 23:30:55 sarasvati kernel: [ 1177.982521] option: v0.7.2:USB Driver for GSM modems
Aug 12 23:30:55 sarasvati modem-manager[619]: <info>  (ttyUSB0) opening serial port...
Aug 12 23:30:56 sarasvati kernel: [ 1178.871557] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Aug 12 23:30:56 sarasvati kernel: [ 1178.873340] scsi 9:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Aug 12 23:30:56 sarasvati kernel: [ 1178.883316] sr1: scsi-1 drive
Aug 12 23:30:56 sarasvati kernel: [ 1178.883687] sr 8:0:0:0: Attached scsi CD-ROM sr1
Aug 12 23:30:56 sarasvati kernel: [ 1178.883904] sr 8:0:0:0: Attached scsi generic sg2 type 5
Aug 12 23:30:56 sarasvati kernel: [ 1178.890163] sd 9:0:0:0: Attached scsi generic sg3 type 0
Aug 12 23:30:56 sarasvati kernel: [ 1178.898619] sd 9:0:0:0: [sdb] Attached SCSI removable disk
Aug 12 23:30:57 sarasvati modem-manager[619]: <info>  (ttyUSB0) closing serial port...
Aug 12 23:30:57 sarasvati modem-manager[619]: <info>  (ttyUSB0) serial port closed
Aug 12 23:30:57 sarasvati modem-manager[619]: <info>  (ttyUSB0) opening serial port...
Aug 12 23:30:57 sarasvati modem-manager[619]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2 claimed port ttyUSB0
Aug 12 23:30:58 sarasvati modem-manager[619]: <info>  (ttyUSB1) opening serial port...
Aug 12 23:31:02 sarasvati kernel: [ 1185.016287] option: option_instat_callback: error -108
Aug 12 23:31:08 sarasvati kernel: [ 1191.024511] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Aug 12 23:31:08 sarasvati kernel: [ 1191.024548] option 1-2:1.0: device disconnected
Aug 12 23:31:13 sarasvati modem-manager[619]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2
Aug 12 23:31:13 sarasvati modem-manager[619]: <info>  (ttyUSB0) closing serial port...
Aug 12 23:31:13 sarasvati modem-manager[619]: <info>  (ttyUSB0) serial port closed
Aug 12 23:31:13 sarasvati modem-manager[619]: mm_serial_port_close: assertion `priv->open_count > 0' failed
Aug 12 23:31:13 sarasvati modem-manager[619]: <info>  (ttyUSB1) closing serial port...
Aug 12 23:31:13 sarasvati kernel: [ 1196.024554] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Aug 12 23:31:13 sarasvati kernel: [ 1196.024589] option 1-2:1.1: device disconnected
Aug 12 23:31:13 sarasvati modem-manager[619]: <info>  (ttyUSB1) serial port closed
Aug 12 23:31:13 sarasvati kernel: [ 1196.136063] usb 1-2: reset high speed USB device using ehci_hcd and address 5
Aug 12 23:31:13 sarasvati kernel: [ 1196.273231] option 1-2:1.1: GSM modem (1-port) converter detected
Aug 12 23:31:13 sarasvati kernel: [ 1196.273526] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Aug 12 23:31:13 sarasvati kernel: [ 1196.273681] option 1-2:1.0: GSM modem (1-port) converter detected
Aug 12 23:31:13 sarasvati kernel: [ 1196.273885] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Aug 12 23:31:13 sarasvati modem-manager[619]: <info>  (ttyUSB1) opening serial port...
Aug 12 23:31:13 sarasvati modem-manager[619]: <info>  (ttyUSB0) opening serial port...
Aug 12 23:31:28 sarasvati modem-manager[619]: <info>  (ttyUSB0) closing serial port...
Aug 12 23:31:33 sarasvati modem-manager[619]: <info>  (ttyUSB0) serial port closed
Aug 12 23:31:34 sarasvati modem-manager[619]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2 claimed port ttyUSB0
Aug 12 23:31:34 sarasvati modem-manager[619]: <info>  (ttyUSB1) closing serial port...
Aug 12 23:31:34 sarasvati modem-manager[619]: <info>  (ttyUSB1) closing serial port...
Aug 12 23:31:34 sarasvati modem-manager[619]: <info>  (ttyUSB1) serial port closed
Aug 12 23:31:34 sarasvati modem-manager[619]: <info>  (ttyUSB1) opening serial port...
Aug 12 23:31:34 sarasvati modem-manager[619]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2 claimed port ttyUSB1
Aug 12 23:31:34 sarasvati modem-manager[619]: <info>  (ttyUSB1) closing serial port...
Aug 12 23:31:34 sarasvati modem-manager[619]: <info>  (ttyUSB1) serial port closed
Aug 12 23:31:34 sarasvati NetworkManager[613]: <warn> (ttyUSB1): failed to look up interface index
Aug 12 23:31:34 sarasvati NetworkManager[613]: <info> (ttyUSB1): new GSM device (driver: 'option1' ifindex: -1)
Aug 12 23:31:34 sarasvati NetworkManager[613]: <info> (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/2
Aug 12 23:31:34 sarasvati NetworkManager[613]: <info> (ttyUSB1): now managed
Aug 12 23:31:34 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 1 -> 2 (reason 2)
Aug 12 23:31:34 sarasvati NetworkManager[613]: <info> (ttyUSB1): deactivating device (reason: 2).
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 2 -> 3 (reason 0)
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) starting connection 'Vodacom Default 1'
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 3 -> 4 (reason 0)
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Aug 12 23:31:35 sarasvati modem-manager[619]: <info>  (ttyUSB1) opening serial port...
Aug 12 23:31:35 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Aug 12 23:31:35 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> WWAN now enabled by management service
Aug 12 23:31:35 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Aug 12 23:31:35 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Aug 12 23:31:35 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 4 -> 5 (reason 0)
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 5 -> 7 (reason 0)
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> starting PPP connection
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> pppd started with pid 2077
Aug 12 23:31:35 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
Aug 12 23:31:35 sarasvati pppd[2077]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Aug 12 23:31:36 sarasvati pppd[2077]: pppd 2.4.5 started by root, uid 0
Aug 12 23:31:36 sarasvati pppd[2077]: Using interface ppp0
Aug 12 23:31:36 sarasvati pppd[2077]: Connect: ppp0 <--> /dev/ttyUSB1
Aug 12 23:31:36 sarasvati NetworkManager[613]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 12 23:31:36 sarasvati NetworkManager[613]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug 12 23:31:36 sarasvati pppd[2077]: CHAP authentication succeeded
Aug 12 23:31:36 sarasvati pppd[2077]: CHAP authentication succeeded
Aug 12 23:31:36 sarasvati kernel: [ 1218.505550] PPP BSD Compression module registered
Aug 12 23:31:36 sarasvati kernel: [ 1218.539466] PPP Deflate Compression module registered
Aug 12 23:31:38 sarasvati pppd[2077]: Could not determine remote IP address: defaulting to 10.64.64.64
Aug 12 23:31:38 sarasvati pppd[2077]: local  IP address 41.4.16.42
Aug 12 23:31:38 sarasvati pppd[2077]: remote IP address 10.64.64.64
Aug 12 23:31:38 sarasvati pppd[2077]: primary   DNS address 196.207.40.167
Aug 12 23:31:38 sarasvati pppd[2077]: secondary DNS address 196.207.40.165
Aug 12 23:31:38 sarasvati NetworkManager[613]: <info> PPP manager(IP Config Get) reply received.
Aug 12 23:31:38 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 12 23:31:38 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 4 of 5 (IP4 Configure Get) started...
Aug 12 23:31:38 sarasvati NetworkManager[613]: <info> Scheduling stage 5
Aug 12 23:31:38 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 12 23:31:38 sarasvati NetworkManager[613]: <info> Done scheduling stage 5
Aug 12 23:31:38 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 12 23:31:38 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 5 of 5 (IP Configure Commit) started...
Aug 12 23:31:39 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 7 -> 8 (reason 0)
Aug 12 23:31:40 sarasvati NetworkManager[613]: <info> Policy set 'Vodacom Default 1' (ppp0) as default for IPv4 routing and DNS.
Aug 12 23:31:40 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) successful, device activated.
Aug 12 23:31:40 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 5 of 5 (IP Configure Commit) complete.
Aug 12 23:31:44 sarasvati pppd[2077]: Modem hangup
Aug 12 23:31:44 sarasvati pppd[2077]: Connect time 0.1 minutes.
Aug 12 23:31:44 sarasvati pppd[2077]: Sent 434 bytes, received 722 bytes.

Aug 12 23:31:44 sarasvati kernel: [ 1227.040275] option: option_instat_callback: error -108
Aug 12 23:31:44 sarasvati kernel: [ 1227.040735] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Aug 12 23:31:44 sarasvati kernel: [ 1227.040764] option 1-2:1.0: device disconnected
Aug 12 23:31:44 sarasvati kernel: [ 1227.040891] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Aug 12 23:31:44 sarasvati kernel: [ 1227.040930] option 1-2:1.1: device disconnected
Aug 12 23:31:44 sarasvati modem-manager[619]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2
Aug 12 23:31:44 sarasvati modem-manager[619]: <info>  (ttyUSB1) closing serial port...
Aug 12 23:31:44 sarasvati modem-manager[619]: <info>  (ttyUSB1) serial port closed
Aug 12 23:31:44 sarasvati modem-manager[619]: <info>  (tty/ttyUSB1): released by modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2
Aug 12 23:31:44 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disabled)
Aug 12 23:31:44 sarasvati NetworkManager[613]: <info> (ttyUSB1): now unmanaged
Aug 12 23:31:44 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 8 -> 1 (reason 36)
Aug 12 23:31:44 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 8 -> 1 (reason 36)
Aug 12 23:31:44 sarasvati NetworkManager[613]: <info> (ttyUSB1): deactivating device (reason: 36).
Aug 12 23:31:44 sarasvati pppd[2077]: Connection terminated.
Aug 12 23:31:44 sarasvati avahi-daemon[606]: Withdrawing workstation service for ppp0.
Aug 12 23:31:44 sarasvati NetworkManager[613]: <info> (ttyUSB1): cleaning up...
Aug 12 23:31:44 sarasvati NetworkManager[613]: <info> (ttyUSB1): taking down device.
Aug 12 23:31:44 sarasvati NetworkManager[613]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Aug 12 23:31:44 sarasvati NetworkManager[613]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 12 23:31:44 sarasvati nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist#012
Aug 12 23:31:44 sarasvati kernel: [ 1227.152105] usb 1-2: reset high speed USB device using ehci_hcd and address 5
Aug 12 23:31:44 sarasvati kernel: [ 1227.292162] option 1-2:1.1: GSM modem (1-port) converter detected
Aug 12 23:31:44 sarasvati kernel: [ 1227.292344] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Aug 12 23:31:44 sarasvati kernel: [ 1227.300142] option 1-2:1.0: GSM modem (1-port) converter detected
Aug 12 23:31:44 sarasvati kernel: [ 1227.300316] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Aug 12 23:31:44 sarasvati modem-manager[619]: <info>  (ttyUSB2) opening serial port...
Aug 12 23:31:45 sarasvati ntpdate[2144]: sendto(91.189.94.4): Network is unreachable
Aug 12 23:31:45 sarasvati pppd[2077]: Exit.
Aug 12 23:31:46 sarasvati modem-manager[619]: <info>  (ttyUSB2) closing serial port...
Aug 12 23:31:46 sarasvati modem-manager[619]: <info>  (ttyUSB2) serial port closed
Aug 12 23:31:46 sarasvati modem-manager[619]: <info>  (ttyUSB2) opening serial port...
Aug 12 23:31:46 sarasvati modem-manager[619]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2 claimed port ttyUSB2
Aug 12 23:31:47 sarasvati ntpdate[2144]: sendto(91.189.94.4): Network is unreachable
Aug 12 23:31:47 sarasvati modem-manager[619]: <info>  (ttyUSB2) closing serial port...
Aug 12 23:31:47 sarasvati modem-manager[619]: <info>  (ttyUSB2) serial port closed
Aug 12 23:31:47 sarasvati modem-manager[619]: <info>  (ttyUSB0) opening serial port...
Aug 12 23:31:49 sarasvati ntpdate[2144]: adjust time server 91.189.94.4 offset -0.066165 sec
Aug 12 23:31:52 sarasvati kernel: [ 1235.012216] option: option_instat_callback: error -108
Aug 12 23:31:52 sarasvati kernel: [ 1235.012478] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Aug 12 23:31:52 sarasvati kernel: [ 1235.012523] option 1-2:1.0: device disconnected
Aug 12 23:31:57 sarasvati modem-manager[619]: <warn>  (Huawei) ttyUSB0: couldn't open serial port: (0) Could not lock serial device ttyUSB0: Input/output error
Aug 12 23:31:57 sarasvati kernel: [ 1240.312493] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Aug 12 23:31:57 sarasvati kernel: [ 1240.312528] option 1-2:1.1: device disconnected
Aug 12 23:31:57 sarasvati modem-manager[619]: <info>  (tty/ttyUSB2): released by modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2
Aug 12 23:31:57 sarasvati NetworkManager[613]: <warn> could not get device type: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist
Aug 12 23:31:58 sarasvati kernel: [ 1240.424083] usb 1-2: reset high speed USB device using ehci_hcd and address 5
Aug 12 23:31:58 sarasvati kernel: [ 1240.561146] option 1-2:1.1: GSM modem (1-port) converter detected
Aug 12 23:31:58 sarasvati kernel: [ 1240.561447] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Aug 12 23:31:58 sarasvati kernel: [ 1240.561610] option 1-2:1.0: GSM modem (1-port) converter detected
Aug 12 23:31:58 sarasvati kernel: [ 1240.561836] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Aug 12 23:31:58 sarasvati modem-manager[619]: <info>  (ttyUSB1) opening serial port...
Aug 12 23:31:59 sarasvati modem-manager[619]: <info>  (ttyUSB1) closing serial port...
Aug 12 23:31:59 sarasvati modem-manager[619]: <info>  (ttyUSB1) serial port closed
Aug 12 23:31:59 sarasvati modem-manager[619]: <info>  (ttyUSB1) opening serial port...
Aug 12 23:31:59 sarasvati modem-manager[619]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2 claimed port ttyUSB1
Aug 12 23:31:59 sarasvati modem-manager[619]: <info>  (ttyUSB1) closing serial port...
Aug 12 23:31:59 sarasvati modem-manager[619]: <info>  (ttyUSB1) serial port closed
Aug 12 23:32:01 sarasvati modem-manager[619]: <info>  (ttyUSB0) opening serial port...
Aug 12 23:32:16 sarasvati modem-manager[619]: <info>  (ttyUSB0) closing serial port...
Aug 12 23:32:21 sarasvati modem-manager[619]: <info>  (ttyUSB0) serial port closed
Aug 12 23:32:21 sarasvati modem-manager[619]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2 claimed port ttyUSB0
Aug 12 23:32:21 sarasvati NetworkManager[613]: <warn> (ttyUSB1): failed to look up interface index
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> WWAN now disabled by management service
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> (ttyUSB1): new GSM device (driver: 'option1' ifindex: -1)
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/3
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> (ttyUSB1): now managed
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 1 -> 2 (reason 2)
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> (ttyUSB1): deactivating device (reason: 2).
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 2 -> 3 (reason 0)
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) starting connection 'Vodacom Default 1'
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 3 -> 4 (reason 0)
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Aug 12 23:32:21 sarasvati modem-manager[619]: <info>  (ttyUSB1) opening serial port...
Aug 12 23:32:21 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (disabled -> enabling)
Aug 12 23:32:21 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (enabling -> enabled)
Aug 12 23:32:21 sarasvati NetworkManager[613]: <info> WWAN now enabled by management service
Aug 12 23:32:21 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (enabled -> registered)
Aug 12 23:32:22 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (registered -> connecting)
Aug 12 23:32:22 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (connecting -> connected)
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 4 -> 5 (reason 0)
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 5 -> 7 (reason 0)
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> starting PPP connection
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> pppd started with pid 2225
Aug 12 23:32:22 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
Aug 12 23:32:22 sarasvati pppd[2225]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Aug 12 23:32:22 sarasvati pppd[2225]: pppd 2.4.5 started by root, uid 0
Aug 12 23:32:22 sarasvati NetworkManager[613]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 12 23:32:22 sarasvati NetworkManager[613]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug 12 23:32:22 sarasvati pppd[2225]: Using interface ppp0
Aug 12 23:32:22 sarasvati pppd[2225]: Connect: ppp0 <--> /dev/ttyUSB1
Aug 12 23:32:22 sarasvati pppd[2225]: CHAP authentication succeeded
Aug 12 23:32:22 sarasvati pppd[2225]: CHAP authentication succeeded
Aug 12 23:32:24 sarasvati pppd[2225]: Could not determine remote IP address: defaulting to 10.64.64.64
Aug 12 23:32:24 sarasvati pppd[2225]: local  IP address 41.3.224.10
Aug 12 23:32:24 sarasvati pppd[2225]: remote IP address 10.64.64.64
Aug 12 23:32:24 sarasvati pppd[2225]: primary   DNS address 196.207.40.167
Aug 12 23:32:24 sarasvati pppd[2225]: secondary DNS address 196.207.40.165
Aug 12 23:32:24 sarasvati NetworkManager[613]: <info> PPP manager(IP Config Get) reply received.
Aug 12 23:32:24 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 12 23:32:24 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 4 of 5 (IP4 Configure Get) started...
Aug 12 23:32:24 sarasvati NetworkManager[613]: <info> Scheduling stage 5
Aug 12 23:32:24 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 12 23:32:24 sarasvati NetworkManager[613]: <info> Done scheduling stage 5
Aug 12 23:32:24 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 12 23:32:24 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 5 of 5 (IP Configure Commit) started...
Aug 12 23:32:25 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 7 -> 8 (reason 0)
Aug 12 23:32:25 sarasvati NetworkManager[613]: <info> Policy set 'Vodacom Default 1' (ppp0) as default for IPv4 routing and DNS.
Aug 12 23:32:25 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) successful, device activated.
Aug 12 23:32:25 sarasvati NetworkManager[613]: <info> Activation (ttyUSB1) Stage 5 of 5 (IP Configure Commit) complete.
Aug 12 23:32:28 sarasvati pppd[2225]: Modem hangup
Aug 12 23:32:28 sarasvati pppd[2225]: Connect time 0.1 minutes.
Aug 12 23:32:28 sarasvati pppd[2225]: Sent 542 bytes, received 740 bytes.

Aug 12 23:32:28 sarasvati kernel: [ 1271.008210] option: option_instat_callback: error -108
Aug 12 23:32:28 sarasvati kernel: [ 1271.008689] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Aug 12 23:32:28 sarasvati kernel: [ 1271.008719] option 1-2:1.0: device disconnected
Aug 12 23:32:28 sarasvati kernel: [ 1271.008845] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Aug 12 23:32:28 sarasvati kernel: [ 1271.008884] option 1-2:1.1: device disconnected
Aug 12 23:32:28 sarasvati modem-manager[619]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2
Aug 12 23:32:28 sarasvati modem-manager[619]: <info>  (ttyUSB1) closing serial port...
Aug 12 23:32:28 sarasvati modem-manager[619]: <info>  (ttyUSB1) serial port closed
Aug 12 23:32:28 sarasvati modem-manager[619]: <info>  (tty/ttyUSB1): released by modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2
Aug 12 23:32:28 sarasvati modem-manager[619]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (connected -> disabled)
Aug 12 23:32:28 sarasvati NetworkManager[613]: <info> (ttyUSB1): now unmanaged
Aug 12 23:32:28 sarasvati NetworkManager[613]: <info> (ttyUSB1): device state change: 8 -> 1 (reason 36)
Aug 12 23:32:28 sarasvati NetworkManager[613]: <info> (ttyUSB1): deactivating device (reason: 36).
Aug 12 23:32:28 sarasvati pppd[2225]: Connection terminated.
Aug 12 23:32:28 sarasvati avahi-daemon[606]: Withdrawing workstation service for ppp0.
Aug 12 23:32:28 sarasvati NetworkManager[613]: <info> (ttyUSB1): cleaning up...
Aug 12 23:32:28 sarasvati NetworkManager[613]: <info> (ttyUSB1): taking down device.
Aug 12 23:32:28 sarasvati NetworkManager[613]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Aug 12 23:32:28 sarasvati NetworkManager[613]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 12 23:32:28 sarasvati NetworkManager[613]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 12 23:32:28 sarasvati nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist#012
Aug 12 23:32:28 sarasvati kernel: [ 1271.120092] usb 1-2: reset high speed USB device using ehci_hcd and address 5
Aug 12 23:32:28 sarasvati kernel: [ 1271.257365] option 1-2:1.1: GSM modem (1-port) converter detected
Aug 12 23:32:28 sarasvati kernel: [ 1271.257510] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Aug 12 23:32:28 sarasvati kernel: [ 1271.264104] option 1-2:1.0: GSM modem (1-port) converter detected
Aug 12 23:32:28 sarasvati kernel: [ 1271.264266] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Aug 12 23:32:28 sarasvati modem-manager[619]: <info>  (ttyUSB2) opening serial port...
Aug 12 23:32:29 sarasvati ntpdate[2285]: sendto(91.189.94.4): Network is unreachable
Aug 12 23:32:29 sarasvati pppd[2225]: Exit.
Aug 12 23:32:30 sarasvati modem-manager[619]: <info>  (ttyUSB2) closing serial port...
Aug 12 23:32:30 sarasvati modem-manager[619]: <info>  (ttyUSB2) serial port closed
Aug 12 23:32:30 sarasvati modem-manager[619]: <info>  (ttyUSB2) opening serial port...
Aug 12 23:32:30 sarasvati modem-manager[619]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2 claimed port ttyUSB2
Aug 12 23:32:31 sarasvati ntpdate[2285]: sendto(91.189.94.4): Network is unreachable
Aug 12 23:32:31 sarasvati modem-manager[619]: <info>  (ttyUSB2) closing serial port...
Aug 12 23:32:31 sarasvati modem-manager[619]: <info>  (ttyUSB2) serial port closed
Aug 12 23:32:31 sarasvati modem-manager[619]: <info>  (ttyUSB0) opening serial port...
Aug 12 23:32:33 sarasvati ntpdate[2285]: sendto(91.189.94.4): Network is unreachable
Aug 12 23:32:34 sarasvati ntpdate[2285]: adjust time server 91.189.94.4 offset -0.036007 sec
Aug 12 23:32:36 sarasvati kernel: [ 1279.016199] option: option_instat_callback: error -108
Aug 12 23:32:36 sarasvati kernel: [ 1279.016464] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Aug 12 23:32:36 sarasvati kernel: [ 1279.016464] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Aug 12 23:32:36 sarasvati kernel: [ 1279.016516] option 1-2:1.0: device disconnected
Aug 12 23:32:41 sarasvati modem-manager[619]: <warn>  (Huawei) ttyUSB0: couldn't open serial port: (0) Could not lock serial device ttyUSB0: Input/output error
Aug 12 23:32:41 sarasvati kernel: [ 1284.280439] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Aug 12 23:32:41 sarasvati kernel: [ 1284.280439] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Aug 12 23:32:41 sarasvati kernel: [ 1284.280475] option 1-2:1.1: device disconnected
Aug 12 23:32:41 sarasvati modem-manager[619]: <info>  (tty/ttyUSB2): released by modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2
Aug 12 23:32:41 sarasvati NetworkManager[613]: <warn> could not get device type: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist

[/SIZE][/FONT]

---

