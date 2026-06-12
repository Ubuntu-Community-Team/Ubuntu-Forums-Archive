---
title: "mobile broadband does not work anymore on 12.10"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by barna on 2012-12-24
Hi,
I have been using a mobile broadband connection on my kubuntu 11.10 (T-Mobile Hungary, Huawei dongle, lsusb output: Bus 002 Device 016: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem). The connection crashed from time to time, but unplugging/plugging the device helped.
With kubuntu 12.10 it doesn't work anymore. The device is recognized without any problem, I can set up the connection in the same way as for 11.10 (the network provider is found in the preset list, I set all options as for 11.10), the connection is reported to be established, however I have no connection to any sites. 
Do you have any tips what to check?
Thank you
Daniel

---

### Post by offgridguy on 2012-12-24
Do you have another computer to try to see if you get a connection, or perhaps you could borrow one as it sounds like a hardware issue with your Huawei.

---

### Post by barna on 2012-12-25
Tried on another (freshly installed) notebook with kubuntu 12.10 - exactly the same things happen. The device is very quickly recognized, after setting up the connection in NetworkManager it is reported as OK, but I can not access anything.I do not find anything special in dmesg (I copy it by hand, sorry for occasional typos...)

```

usb 2-1.1: >New USB device found, idVendor=12d1, idProduct=1001
usb 2-1.1: >New USB device strings: Mfr=3, Product=2, SerialNumber=0
usb 2-1.1: >Product: HUAWEI Mobile
...
usbcore: registered new interface driver usbserial
usbcore: registered new interface driver usbserial_generic
...
USB Serial support registered for GSM modem (1-port)
option 2-1.1:1.0: >GSM modem (1-port) converter detected
... etc

```

Syslog is like this:

```

Dec 25 09:31:54 gabcur-notebook kernel: [  946.480306] usb 2-1.1: >new high-speed USB device number 4 using ehci_hcd
Dec 25 09:31:54 gabcur-notebook kernel: [  946.574770] usb 2-1.1: >New USB device found, idVendor=12d1, idProduct=1446
Dec 25 09:31:54 gabcur-notebook kernel: [  946.574781] usb 2-1.1: >New USB device strings: Mfr=3, Product=2, SerialNumber=0
Dec 25 09:31:54 gabcur-notebook kernel: [  946.574787] usb 2-1.1: >Product: HUAWEI Mobile
Dec 25 09:31:54 gabcur-notebook kernel: [  946.574792] usb 2-1.1: >Manufacturer: HUAWEI Technology
Dec 25 09:31:54 gabcur-notebook kernel: [  946.577436] scsi8 : usb-storage 2-1.1:1.0
Dec 25 09:31:54 gabcur-notebook kernel: [  946.577987] scsi9 : usb-storage 2-1.1:1.1
Dec 25 09:31:54 gabcur-notebook mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Dec 25 09:31:54 gabcur-notebook mtp-probe: bus: 2, device: 4 was not an MTP device
Dec 25 09:31:55 gabcur-notebook kernel: [  947.576278] scsi 8:0:0:0: >CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Dec 25 09:31:55 gabcur-notebook kernel: [  947.576659] scsi 9:0:0:0: >Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Dec 25 09:31:55 gabcur-notebook kernel: [  947.581215] sr1: scsi-1 drive
Dec 25 09:31:55 gabcur-notebook kernel: [  947.581514] sr 8:0:0:0: >Attached scsi CD-ROM sr1
Dec 25 09:31:55 gabcur-notebook kernel: [  947.582235] sr 8:0:0:0: >Attached scsi generic sg4 type 5
Dec 25 09:31:55 gabcur-notebook kernel: [  947.584781] sd 9:0:0:0: >Attached scsi generic sg5 type 0
Dec 25 09:31:55 gabcur-notebook kernel: [  947.588978] sd 9:0:0:0: >[sdd] Attached SCSI removable disk
Dec 25 09:31:55 gabcur-notebook usb_modeswitch: switching device 12d1:1446 on 002/004
Dec 25 09:31:55 gabcur-notebook kernel: [  947.814625] usb 2-1.1: >USB disconnect, device number 4
Dec 25 09:32:00 gabcur-notebook kernel: [  952.359501] usb 2-1.1: >new high-speed USB device number 5 using ehci_hcd
Dec 25 09:32:00 gabcur-notebook kernel: [  952.454357] usb 2-1.1: >New USB device found, idVendor=12d1, idProduct=1001
Dec 25 09:32:00 gabcur-notebook kernel: [  952.454368] usb 2-1.1: >New USB device strings: Mfr=3, Product=2, SerialNumber=0
Dec 25 09:32:00 gabcur-notebook kernel: [  952.454374] usb 2-1.1: >Product: HUAWEI Mobile
Dec 25 09:32:00 gabcur-notebook kernel: [  952.454379] usb 2-1.1: >Manufacturer: HUAWEI Technology
Dec 25 09:32:00 gabcur-notebook kernel: [  952.458522] scsi13 : usb-storage 2-1.1:1.3
Dec 25 09:32:00 gabcur-notebook mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Dec 25 09:32:00 gabcur-notebook mtp-probe: bus: 2, device: 5 was not an MTP device
Dec 25 09:32:00 gabcur-notebook kernel: [  952.459353] scsi14 : usb-storage 2-1.1:1.4
Dec 25 09:32:00 gabcur-notebook kernel: [  952.516525] usbcore: registered new interface driver usbserial
Dec 25 09:32:00 gabcur-notebook kernel: [  952.516546] usbcore: registered new interface driver usbserial_generic
Dec 25 09:32:00 gabcur-notebook kernel: [  952.516561] USB Serial support registered for generic
Dec 25 09:32:00 gabcur-notebook kernel: [  952.516567] usbserial: USB Serial Driver core
Dec 25 09:32:00 gabcur-notebook kernel: [  952.527800] usbcore: registered new interface driver option
Dec 25 09:32:00 gabcur-notebook kernel: [  952.527817] USB Serial support registered for GSM modem (1-port)
Dec 25 09:32:00 gabcur-notebook kernel: [  952.527923] option 2-1.1:1.0: >GSM modem (1-port) converter detected
Dec 25 09:32:00 gabcur-notebook kernel: [  952.528392] usb 2-1.1: >GSM modem (1-port) converter now attached to ttyUSB0
Dec 25 09:32:00 gabcur-notebook kernel: [  952.528417] option 2-1.1:1.1: >GSM modem (1-port) converter detected
Dec 25 09:32:00 gabcur-notebook kernel: [  952.528474] usb 2-1.1: >GSM modem (1-port) converter now attached to ttyUSB1
Dec 25 09:32:00 gabcur-notebook kernel: [  952.528488] option 2-1.1:1.2: >GSM modem (1-port) converter detected
Dec 25 09:32:00 gabcur-notebook kernel: [  952.528541] usb 2-1.1: >GSM modem (1-port) converter now attached to ttyUSB2
Dec 25 09:32:00 gabcur-notebook modem-manager[858]: <info>  (ttyUSB0) opening serial port...
Dec 25 09:32:00 gabcur-notebook modem-manager[858]: <warn>  (ttyUSB0): port attributes not fully set
Dec 25 09:32:00 gabcur-notebook usb_modeswitch: switched to 12d1:1001 on 002/004
Dec 25 09:32:01 gabcur-notebook kernel: [  953.454833] scsi 13:0:0:0: >CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Dec 25 09:32:01 gabcur-notebook kernel: [  953.463050] scsi 14:0:0:0: >Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Dec 25 09:32:01 gabcur-notebook kernel: [  953.463164] sr1: scsi-1 drive
Dec 25 09:32:01 gabcur-notebook kernel: [  953.463277] sr 13:0:0:0: >Attached scsi CD-ROM sr1
Dec 25 09:32:01 gabcur-notebook kernel: [  953.463358] sr 13:0:0:0: >Attached scsi generic sg4 type 5
Dec 25 09:32:01 gabcur-notebook kernel: [  953.465607] sd 14:0:0:0: >Attached scsi generic sg5 type 0
Dec 25 09:32:01 gabcur-notebook kernel: [  953.467795] sd 14:0:0:0: >[sdd] Attached SCSI removable disk
Dec 25 09:32:01 gabcur-notebook usb_modeswitch[2052]: usb_modeswitch: switched to 12d1:1001 on 2/5
Dec 25 09:32:04 gabcur-notebook modem-manager[858]: <info>  (ttyUSB0) closing serial port...
Dec 25 09:32:04 gabcur-notebook modem-manager[858]: <info>  (ttyUSB0) serial port closed
Dec 25 09:32:04 gabcur-notebook modem-manager[858]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyUSB0
Dec 25 09:32:06 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2) opening serial port...
Dec 25 09:32:06 gabcur-notebook modem-manager[858]: <warn>  (ttyUSB2): port attributes not fully set
Dec 25 09:32:06 gabcur-notebook modem-manager[858]: <info>  (ttyUSB1) opening serial port...
Dec 25 09:32:06 gabcur-notebook modem-manager[858]: <warn>  (ttyUSB1): port attributes not fully set
Dec 25 09:32:08 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2) closing serial port...
Dec 25 09:32:08 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2) serial port closed
Dec 25 09:32:08 gabcur-notebook modem-manager[858]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyUSB2
Dec 25 09:32:19 gabcur-notebook modem-manager[858]: <info>  (ttyUSB1) closing serial port...
Dec 25 09:32:19 gabcur-notebook modem-manager[858]: <info>  (ttyUSB1) serial port closed
Dec 25 09:32:19 gabcur-notebook modem-manager[858]: <info>  (ttyUSB1) opening serial port...
Dec 25 09:32:19 gabcur-notebook modem-manager[858]: <info>  (ttyUSB1) closing serial port...
Dec 25 09:32:19 gabcur-notebook modem-manager[858]: <info>  (ttyUSB1) serial port closed
Dec 25 09:32:19 gabcur-notebook modem-manager[858]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyUSB1
Dec 25 09:32:19 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2) opening serial port...
Dec 25 09:32:19 gabcur-notebook modem-manager[858]: <warn>  (ttyUSB2): port attributes not fully set
Dec 25 09:32:19 gabcur-notebook NetworkManager[908]: <warn> (ttyUSB0): failed to look up interface index
Dec 25 09:32:19 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): new GSM/UMTS device (driver: 'option1' ifindex: 0)
Dec 25 09:32:19 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/2
Dec 25 09:32:19 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): now managed
Dec 25 09:32:19 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 25 09:32:19 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): deactivating device (reason 'managed') [2]
Dec 25 09:32:19 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Dec 25 09:32:20 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2) closing serial port...
Dec 25 09:32:20 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2) serial port closed
Dec 25 09:33:03 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2) opening serial port...
Dec 25 09:33:03 gabcur-notebook modem-manager[858]: <warn>  (ttyUSB2): port attributes not fully set
Dec 25 09:33:03 gabcur-notebook modem-manager[858]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Dec 25 09:33:04 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2): using PDU mode for SMS
Dec 25 09:33:04 gabcur-notebook modem-manager[858]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Dec 25 09:33:04 gabcur-notebook NetworkManager[908]: <info> WWAN now enabled by management service
Dec 25 09:33:04 gabcur-notebook modem-manager[858]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Auto-activating connection 'T-Mobile'.
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) starting connection 'T-Mobile'
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Dec 25 09:34:10 gabcur-notebook modem-manager[858]: <info>  (ttyUSB0) opening serial port...
Dec 25 09:34:10 gabcur-notebook modem-manager[858]: <warn>  (ttyUSB0): port attributes not fully set
Dec 25 09:34:10 gabcur-notebook modem-manager[858]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Dec 25 09:34:10 gabcur-notebook modem-manager[858]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> starting PPP connection
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> pppd started with pid 2180
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec 25 09:34:10 gabcur-notebook pppd[2180]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Dec 25 09:34:10 gabcur-notebook pppd[2180]: pppd 2.4.5 started by root, uid 0
Dec 25 09:34:10 gabcur-notebook pppd[2180]: Using interface ppp0
Dec 25 09:34:10 gabcur-notebook pppd[2180]: Connect: ppp0 <--> /dev/ttyUSB0
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 25 09:34:10 gabcur-notebook NetworkManager[908]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Dec 25 09:34:10 gabcur-notebook pppd[2180]: CHAP authentication succeeded
Dec 25 09:34:10 gabcur-notebook pppd[2180]: CHAP authentication succeeded
Dec 25 09:34:10 gabcur-notebook kernel: [ 1082.605434] PPP BSD Compression module registered
Dec 25 09:34:10 gabcur-notebook kernel: [ 1082.633519] PPP Deflate Compression module registered
Dec 25 09:34:11 gabcur-notebook NetworkManager[908]:    keyfile: updating /etc/NetworkManager/system-connections/T-Mobile-aef6630f-9161-4ac7-915a-3d50cdf76f61
Dec 25 09:34:12 gabcur-notebook NetworkManager[908]:    keyfile: updating /etc/NetworkManager/system-connections/T-Mobile-aef6630f-9161-4ac7-915a-3d50cdf76f61
Dec 25 09:34:12 gabcur-notebook pppd[2180]: Could not determine remote IP address: defaulting to 10.64.64.64
Dec 25 09:34:12 gabcur-notebook pppd[2180]: local  IP address 188.156.193.230
Dec 25 09:34:12 gabcur-notebook pppd[2180]: remote IP address 10.64.64.64
Dec 25 09:34:12 gabcur-notebook pppd[2180]: primary   DNS address 84.2.44.1
Dec 25 09:34:12 gabcur-notebook pppd[2180]: secondary DNS address 84.2.46.1
Dec 25 09:34:12 gabcur-notebook NetworkManager[908]: <info> PPP manager(IP Config Get) reply received.
Dec 25 09:34:12 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 25 09:34:12 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 5 of 5 (IPv4 Commit) started...
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <info> DNS: starting dnsmasq...
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <error> [1356424453.927588] [nm-dns-dnsmasq.c:390] update(): dnsmasq not available on the bus, can't update servers.
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <error> [1356424453.927623] [nm-dns-dnsmasq.c:392] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <warn> DNS: plugin dnsmasq update failed
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <info> Policy set 'T-Mobile' (ppp0) as default for IPv4 routing and DNS.
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) successful, device activated.
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <info> Activation (ttyUSB0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 25 09:34:13 gabcur-notebook dbus[797]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 25 09:34:13 gabcur-notebook dnsmasq[2200]: started, version 2.63rc6 cache disabled
Dec 25 09:34:13 gabcur-notebook dnsmasq[2200]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack
Dec 25 09:34:13 gabcur-notebook dnsmasq[2200]: DBus support enabled: connected to system bus
Dec 25 09:34:13 gabcur-notebook dnsmasq[2200]: warning: no upstream servers configured
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <warn> dnsmasq appeared on DBus: :1.68
Dec 25 09:34:13 gabcur-notebook NetworkManager[908]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Dec 25 09:34:13 gabcur-notebook dnsmasq[2200]: setting upstream servers from DBus
Dec 25 09:34:13 gabcur-notebook dnsmasq[2200]: using nameserver 194.176.224.6#53
Dec 25 09:34:13 gabcur-notebook dnsmasq[2200]: using nameserver 212.51.115.1#53
Dec 25 09:34:14 gabcur-notebook dbus[797]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 25 09:34:40 gabcur-notebook pppd[2180]: IPV6CP: timeout sending Config-Requests
Dec 25 09:34:54 gabcur-notebook ntpdate[2310]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Dec 25 09:34:54 gabcur-notebook ntpdate[2310]: no servers can be used, exiting
Dec 25 09:37:51 gabcur-notebook pppd[2180]: Modem hangup
Dec 25 09:37:51 gabcur-notebook pppd[2180]: Connect time 3.7 minutes.
Dec 25 09:37:51 gabcur-notebook pppd[2180]: Sent 2874 bytes, received 2464 bytes.
Dec 25 09:37:51 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2) closing serial port...
Dec 25 09:37:51 gabcur-notebook modem-manager[858]: <info>  (ttyUSB2) serial port closed
Dec 25 09:37:51 gabcur-notebook modem-manager[858]: <info>  (ttyUSB0) closing serial port...
Dec 25 09:37:51 gabcur-notebook modem-manager[858]: <info>  (ttyUSB0) serial port closed
Dec 25 09:37:51 gabcur-notebook pppd[2180]: Connection terminated.
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): device state change: activated -> failed (reason 'ip-config-unavailable') [100 120 5]
Dec 25 09:37:51 gabcur-notebook modem-manager[858]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
Dec 25 09:37:51 gabcur-notebook kernel: [ 1303.123196] usb 2-1.1: >USB disconnect, device number 5
Dec 25 09:37:51 gabcur-notebook kernel: [ 1303.123412] option1 ttyUSB0: >option_instat_callback: error -108
Dec 25 09:37:51 gabcur-notebook kernel: [ 1303.123776] option1 ttyUSB0: >GSM modem (1-port) converter now disconnected from ttyUSB0
Dec 25 09:37:51 gabcur-notebook kernel: [ 1303.123832] option 2-1.1:1.0: >device disconnected
Dec 25 09:37:51 gabcur-notebook kernel: [ 1303.124476] option1 ttyUSB1: >GSM modem (1-port) converter now disconnected from ttyUSB1
Dec 25 09:37:51 gabcur-notebook kernel: [ 1303.124522] option 2-1.1:1.1: >device disconnected
Dec 25 09:37:51 gabcur-notebook kernel: [ 1303.127308] option1 ttyUSB2: >GSM modem (1-port) converter now disconnected from ttyUSB2
Dec 25 09:37:51 gabcur-notebook kernel: [ 1303.127368] option 2-1.1:1.2: >device disconnected
Dec 25 09:37:51 gabcur-notebook modem-manager[858]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disabled)
Dec 25 09:37:51 gabcur-notebook pppd[2180]: Exit.
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <warn> Activation (ttyUSB0) failed for connection 'T-Mobile'
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): now unmanaged
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): deactivating device (reason 'removed') [36]
Dec 25 09:37:51 gabcur-notebook dbus[797]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <warn> could not read ppp stats: No such device
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <warn> DNS: plugin dnsmasq update failed
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <info> ((null)): removing resolv.conf from /sbin/resolvconf
Dec 25 09:37:51 gabcur-notebook dnsmasq[2200]: setting upstream servers from DBus
Dec 25 09:37:51 gabcur-notebook dbus[797]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): cleaning up...
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <info> (ttyUSB0): taking down device.
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Dec 25 09:37:51 gabcur-notebook NetworkManager[908]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

```

---

### Post by offgridguy on 2012-12-25
With my huawei device i know that the OS will recognize the connection to the
device even if the device itself is unable to connect to the internet.
   This is why i suspect the problem is with the device, not the OS.  However
probably the only way to verify that would be if you still had a connection with
11.10,  which i assume you have uninstalled.
   Sorry i can't be of more help.

---

### Post by barna on 2012-12-25
oh yes, I am quite pessimistic with linux: I always install the new distro on another partition, because more often than not the new one just doesn't work (on my notebook with 12.10 I have a problem with the mobile internet + it crashes every 3-4 days with vertical colour stripes on the screen). 

To make it short: I still have kubuntu 11.10, and the device works on this distro just as before (once in 1/2 hours it stops working, but then I restart it again). It only does not work on kubuntu 12.10 (tried on two different notebooks: mine and that of my brother). So I guess it is the OS and not the device. 

As far as I remember, on 11.10 I even had to play with udev and modesetting to make my OS recognize the device. On 12.10 it 'works' out of the box (i.e. it is recognized), but there is no connection. I don't know what to check. 

Any hint is welcome.
Thank you

---

### Post by offgridguy on 2012-12-25
You deserve high marks for perseverance:D
 With the connection problems you describe, i wonder about the connection between
your huawei and your internet service provider ?
    I live in an area where the signal strength is not the best, and do lose connectivity
because of that, however nowhere near the extent which you describe.

---

### Post by barna on 2012-12-25
I am experiencing this problem with 12.10 from the very same place, and (almost) very same time, and it always works with 11.10 and never works with 12.10 so I am pretty sure it's the OS and not the provider. 

Any hints what to check? 

I messed up my working OS by upgrading to the next one too many times so I am now careful. I suggest this to everyone: a 10G partition is more than enough to have a new release installed for a few weeks as testing, and if it works, install it on the other partition. In fact I planned to go in an alternating way: install a new release on partition 2 and use that, and when yet another release is out, install it on partition 1 and use that, etc etc - but in practice I could never get that far, I was always stuck with one release and later ones hardly ever worked - until my notebook died, and then I could start with a new release on that, and get stuck very soon again... I am tired and usually I don't even try to fix problems, if something doesn't work then just use the good old release - but now I have to make a new notebook running for my brother.

---

