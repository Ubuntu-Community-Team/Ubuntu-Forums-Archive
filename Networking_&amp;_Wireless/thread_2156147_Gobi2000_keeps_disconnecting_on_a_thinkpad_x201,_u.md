---
title: "Gobi2000 keeps disconnecting on a thinkpad x201, ubuntu 12.10"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by shylingo on 2013-06-20
Hello Folks, please help me with the following problem:
I'm running a thinkpad x201 with a gobi2000 internal gsm device (don't ask me if it's hsdpa, edge or whatever).

Actually it works fine, but after a sudden period of time, it disconnects. I have no idea how to fix this, or where to look.

i appreciate every idea...

this is a syslog of what is happening all the time:

Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> starting PPP connection
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> pppd started with pid 1461
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 20 22:29:32 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 20 22:29:32 x201 pppd[1461]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Jun 20 22:29:32 x201 pppd[1461]: pppd 2.4.5 started by root, uid 0
Jun 20 22:29:32 x201 pppd[1461]: Using interface ppp0
Jun 20 22:29:32 x201 pppd[1461]: Connect: ppp0 <--> /dev/ttyUSB1
Jun 20 22:29:32 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 20 22:29:32 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun 20 22:29:32 x201 NetworkManager[1168]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jun 20 22:29:32 x201 pppd[1461]: CHAP authentication succeeded
Jun 20 22:29:32 x201 pppd[1461]: CHAP authentication succeeded
Jun 20 22:29:36 x201 pppd[1461]: Could not determine remote IP address: defaulting to 10.64.64.64
Jun 20 22:29:36 x201 dnsmasq[1401]: no servers found in /etc/resolv.conf, will retry
Jun 20 22:29:36 x201 pppd[1461]: local  IP address 10.38.82.206
Jun 20 22:29:36 x201 pppd[1461]: remote IP address 10.64.64.64
Jun 20 22:29:36 x201 pppd[1461]: primary   DNS address 213.94.78.16
Jun 20 22:29:36 x201 pppd[1461]: secondary DNS address 213.94.78.17
Jun 20 22:29:36 x201 NetworkManager[1168]: <info> PPP manager(IP Config Get) reply received.
Jun 20 22:29:36 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 20 22:29:36 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 5 of 5 (IPv4 Commit) started...
Jun 20 22:29:37 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 20 22:29:37 x201 NetworkManager[1168]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Jun 20 22:29:37 x201 dnsmasq[15173]: setting upstream servers from DBus
Jun 20 22:29:37 x201 dnsmasq[15173]: using nameserver 213.94.78.17#53
Jun 20 22:29:37 x201 dnsmasq[15173]: using nameserver 213.94.78.16#53
Jun 20 22:29:37 x201 NetworkManager[1168]: <info> Policy set '3 AT - Hutchinson 3G' (ppp0) as default for IPv4 routing and DNS.
Jun 20 22:29:37 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) successful, device activated.
Jun 20 22:29:37 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 5 of 5 (IPv4 Commit) complete.
Jun 20 22:29:37 x201 dbus[1126]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 20 22:29:37 x201 dbus[1126]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 20 22:29:38 x201 dnsmasq[1401]: reading /etc/resolv.conf
Jun 20 22:29:38 x201 dnsmasq[1401]: using nameserver 127.0.1.1#53
Jun 20 22:30:00 x201 ntpdate[1562]: adjust time server 91.189.94.4 offset 0.035515 sec
Jun 20 22:32:25 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/net/wwan0, iface: wwan0)
Jun 20 22:32:25 x201 kernel: [ 4850.219416] usb 2-1.4: USB disconnect, device number 13
Jun 20 22:32:25 x201 kernel: [ 4850.219524] qmi_wwan 2-1.4:1.0: wwan0: unregister 'qmi_wwan' usb-0000:00:1d.0-1.4, Qualcomm WWAN/QMI device
Jun 20 22:32:25 x201 pppd[1461]: Modem hangup
Jun 20 22:32:25 x201 pppd[1461]: Connect time 2.9 minutes.
Jun 20 22:32:25 x201 pppd[1461]: Sent 118382 bytes, received 278597 bytes.
Jun 20 22:32:25 x201 modem-manager[1138]: <info>  (ttyUSB1) closing serial port...
Jun 20 22:32:25 x201 modem-manager[1138]: <info>  (ttyUSB1) serial port closed
Jun 20 22:32:25 x201 kernel: [ 4850.236903] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
Jun 20 22:32:25 x201 kernel: [ 4850.236938] qcserial 2-1.4:1.1: device disconnected
Jun 20 22:32:25 x201 modem-manager[1138]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4
Jun 20 22:32:25 x201 kernel: [ 4850.240723] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
Jun 20 22:32:25 x201 kernel: [ 4850.240754] qcserial 2-1.4:1.2: device disconnected
Jun 20 22:32:25 x201 kernel: [ 4850.240997] qcserial ttyUSB2: Qualcomm USB modem converter now disconnected from ttyUSB2
Jun 20 22:32:25 x201 kernel: [ 4850.241033] qcserial 2-1.4:1.3: device disconnected
Jun 20 22:32:25 x201 modem-manager[1138]: <info>  (tty/ttyUSB1): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4
Jun 20 22:32:25 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/5: state changed (connected -> disabled)
Jun 20 22:32:25 x201 NetworkManager[1168]: <info> (ttyUSB1): now unmanaged
Jun 20 22:32:25 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Jun 20 22:32:25 x201 pppd[1461]: Connection terminated.
Jun 20 22:32:25 x201 NetworkManager[1168]: <info> (ttyUSB1): deactivating device (reason 'removed') [36]
Jun 20 22:32:25 x201 NetworkManager[1168]: <warn> could not read ppp stats: No such device
Jun 20 22:32:25 x201 pppd[1461]: Exit.
Jun 20 22:32:25 x201 NetworkManager[1168]: <warn> DNS: plugin dnsmasq update failed
Jun 20 22:32:25 x201 NetworkManager[1168]: <info> ((null)): removing resolv.conf from /sbin/resolvconf
Jun 20 22:32:25 x201 dnsmasq[15173]: setting upstream servers from DBus
Jun 20 22:32:25 x201 NetworkManager[1168]: <info> (ttyUSB1): cleaning up...
Jun 20 22:32:25 x201 NetworkManager[1168]: <info> (ttyUSB1): taking down device.
Jun 20 22:32:25 x201 NetworkManager[1168]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun 20 22:32:25 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 20 22:32:25 x201 dbus[1126]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 20 22:32:25 x201 dbus[1126]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 20 22:32:25 x201 kernel: [ 4850.438314] usb 2-1.4: new high-speed USB device number 14 using ehci_hcd
Jun 20 22:32:25 x201 kernel: [ 4850.535824] usb 2-1.4: config 1 has an invalid interface number: 1 but max is 0
Jun 20 22:32:25 x201 kernel: [ 4850.535831] usb 2-1.4: config 1 has no interface number 0
Jun 20 22:32:25 x201 kernel: [ 4850.537682] usb 2-1.4: New USB device found, idVendor=05c6, idProduct=9204
Jun 20 22:32:25 x201 kernel: [ 4850.537685] usb 2-1.4: New USB device strings: Mfr=3, Product=2, SerialNumber=0
Jun 20 22:32:25 x201 kernel: [ 4850.537689] usb 2-1.4: Product: Qualcomm Gobi 2000
Jun 20 22:32:25 x201 kernel: [ 4850.537691] usb 2-1.4: Manufacturer: Qualcomm Incorporated
Jun 20 22:32:25 x201 kernel: [ 4850.539317] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
Jun 20 22:32:25 x201 kernel: [ 4850.539419] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
Jun 20 22:32:25 x201 mtp-probe: checking bus 2, device 14: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Jun 20 22:32:25 x201 mtp-probe: bus: 2, device: 14 was not an MTP device
Jun 20 22:32:30 x201 kernel: [ 4855.330450] usb 2-1.4: USB disconnect, device number 14
Jun 20 22:32:30 x201 kernel: [ 4855.330707] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
Jun 20 22:32:30 x201 kernel: [ 4855.330741] qcserial 2-1.4:1.1: device disconnected
Jun 20 22:32:30 x201 kernel: [ 4855.593486] usb 2-1.4: new high-speed USB device number 15 using ehci_hcd
Jun 20 22:32:30 x201 kernel: [ 4855.688325] usb 2-1.4: New USB device found, idVendor=05c6, idProduct=9205
Jun 20 22:32:30 x201 kernel: [ 4855.688330] usb 2-1.4: New USB device strings: Mfr=3, Product=2, SerialNumber=0
Jun 20 22:32:30 x201 kernel: [ 4855.688334] usb 2-1.4: Product: Qualcomm Gobi 2000
Jun 20 22:32:30 x201 kernel: [ 4855.688337] usb 2-1.4: Manufacturer: Qualcomm Incorporated
Jun 20 22:32:30 x201 kernel: [ 4855.691834] qmi_wwan 2-1.4:1.0: cdc-wdm0: USB WDM device
Jun 20 22:32:30 x201 kernel: [ 4855.692047] qmi_wwan 2-1.4:1.0: wwan0: register 'qmi_wwan' at usb-0000:00:1d.0-1.4, Qualcomm WWAN/QMI device, ae:73:4a:98:24:63
Jun 20 22:32:30 x201 kernel: [ 4855.692108] qmi_wwan 2-1.4:1.1: not on our whitelist - ignored
Jun 20 22:32:30 x201 kernel: [ 4855.692669] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
Jun 20 22:32:30 x201 kernel: [ 4855.692776] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
Jun 20 22:32:30 x201 kernel: [ 4855.692839] qmi_wwan 2-1.4:1.2: not on our whitelist - ignored
Jun 20 22:32:30 x201 kernel: [ 4855.693610] qcserial 2-1.4:1.2: Qualcomm USB modem converter detected
Jun 20 22:32:30 x201 kernel: [ 4855.693772] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB1
Jun 20 22:32:30 x201 kernel: [ 4855.693881] qmi_wwan 2-1.4:1.3: not on our whitelist - ignored
Jun 20 22:32:30 x201 kernel: [ 4855.694463] qcserial 2-1.4:1.3: Qualcomm USB modem converter detected
Jun 20 22:32:30 x201 kernel: [ 4855.694631] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB2
Jun 20 22:32:30 x201 mtp-probe: checking bus 2, device 15: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Jun 20 22:32:30 x201 mtp-probe: bus: 2, device: 15 was not an MTP device
Jun 20 22:32:30 x201 modem-manager[1138]: <info>  (ttyUSB0) opening serial port...
Jun 20 22:32:30 x201 modem-manager[1138]: <warn>  (ttyUSB0): port attributes not fully set
Jun 20 22:32:30 x201 modem-manager[1138]: <info>  (ttyUSB2) opening serial port...
Jun 20 22:32:30 x201 modem-manager[1138]: <warn>  (ttyUSB2): port attributes not fully set
Jun 20 22:32:30 x201 modem-manager[1138]: <info>  (ttyUSB1) opening serial port...
Jun 20 22:32:30 x201 modem-manager[1138]: <warn>  (ttyUSB1): port attributes not fully set
Jun 20 22:32:30 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/net/wwan0, iface: wwan0)
Jun 20 22:32:30 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/net/wwan0, iface: wwan0): no ifupdown configuration found.
Jun 20 22:32:35 x201 modem-manager[1138]: <info>  (ttyUSB1) closing serial port...
Jun 20 22:32:35 x201 modem-manager[1138]: <info>  (ttyUSB1) serial port closed
Jun 20 22:32:35 x201 modem-manager[1138]: <info>  (Gobi): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 claimed port ttyUSB1
Jun 20 22:32:42 x201 modem-manager[1138]: <info>  (ttyUSB2) closing serial port...
Jun 20 22:32:42 x201 modem-manager[1138]: <info>  (ttyUSB2) serial port closed
Jun 20 22:32:42 x201 modem-manager[1138]: <info>  (ttyUSB2) opening serial port...
Jun 20 22:32:43 x201 modem-manager[1138]: <info>  (ttyUSB0) closing serial port...
Jun 20 22:32:43 x201 modem-manager[1138]: <info>  (ttyUSB0) serial port closed
Jun 20 22:32:43 x201 modem-manager[1138]: <info>  (ttyUSB0) opening serial port...
Jun 20 22:32:43 x201 modem-manager[1138]: <info>  (ttyUSB0) closing serial port...
Jun 20 22:32:43 x201 modem-manager[1138]: <info>  (ttyUSB0) serial port closed
Jun 20 22:32:43 x201 modem-manager[1138]: <info>  (Gobi): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 claimed port ttyUSB0
Jun 20 22:32:48 x201 modem-manager[1138]: <info>  (ttyUSB2) closing serial port...
Jun 20 22:32:48 x201 modem-manager[1138]: <info>  (ttyUSB2) serial port closed
Jun 20 22:32:48 x201 modem-manager[1138]: <info>  (ttyUSB1) opening serial port...
Jun 20 22:32:48 x201 modem-manager[1138]: <warn>  (ttyUSB1): port attributes not fully set
Jun 20 22:32:49 x201 NetworkManager[1168]: <warn> (ttyUSB1): failed to look up interface index
Jun 20 22:32:49 x201 NetworkManager[1168]: <info> WWAN now disabled by management service
Jun 20 22:32:49 x201 NetworkManager[1168]: <info> (ttyUSB1): new GSM/UMTS device (driver: 'qcserial' ifindex: 0)
Jun 20 22:32:49 x201 NetworkManager[1168]: <info> (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/8
Jun 20 22:32:49 x201 NetworkManager[1168]: <info> (ttyUSB1): now managed
Jun 20 22:32:49 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 20 22:32:49 x201 NetworkManager[1168]: <info> (ttyUSB1): deactivating device (reason 'managed') [2]
Jun 20 22:32:49 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jun 20 22:32:49 x201 modem-manager[1138]: <info>  (ttyUSB1) closing serial port...
Jun 20 22:32:49 x201 modem-manager[1138]: <info>  (ttyUSB1) serial port closed
Jun 20 22:32:50 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) starting connection '3 AT - Hutchinson 3G'
Jun 20 22:32:50 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 20 22:32:50 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Jun 20 22:32:50 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Jun 20 22:32:50 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Jun 20 22:32:50 x201 modem-manager[1138]: <info>  (ttyUSB1) opening serial port...
Jun 20 22:32:50 x201 modem-manager[1138]: <warn>  (ttyUSB1): port attributes not fully set
Jun 20 22:32:50 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/6: state changed (disabled -> enabling)
Jun 20 22:32:50 x201 modem-manager[1138]: <info>  (ttyUSB1): using PDU mode for SMS
Jun 20 22:32:51 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/6: state changed (enabling -> enabled)
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> WWAN now enabled by management service
Jun 20 22:32:51 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/6: state changed (enabled -> registered)
Jun 20 22:32:51 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/6: state changed (registered -> connecting)
Jun 20 22:32:51 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/6: state changed (connecting -> connected)
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> starting PPP connection
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> pppd started with pid 9508
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 20 22:32:51 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 20 22:32:51 x201 pppd[9508]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Jun 20 22:32:51 x201 pppd[9508]: pppd 2.4.5 started by root, uid 0
Jun 20 22:32:51 x201 pppd[9508]: Using interface ppp0
Jun 20 22:32:51 x201 pppd[9508]: Connect: ppp0 <--> /dev/ttyUSB1
Jun 20 22:32:51 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 20 22:32:51 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun 20 22:32:51 x201 NetworkManager[1168]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jun 20 22:32:51 x201 pppd[9508]: CHAP authentication succeeded
Jun 20 22:32:51 x201 pppd[9508]: CHAP authentication succeeded
Jun 20 22:32:55 x201 pppd[9508]: Could not determine remote IP address: defaulting to 10.64.64.64
Jun 20 22:32:55 x201 dnsmasq[1401]: no servers found in /etc/resolv.conf, will retry
Jun 20 22:32:55 x201 pppd[9508]: local  IP address 10.41.211.155
Jun 20 22:32:55 x201 pppd[9508]: remote IP address 10.64.64.64
Jun 20 22:32:55 x201 pppd[9508]: primary   DNS address 213.94.78.16
Jun 20 22:32:55 x201 pppd[9508]: secondary DNS address 213.94.78.17
Jun 20 22:32:55 x201 NetworkManager[1168]: <info> PPP manager(IP Config Get) reply received.
Jun 20 22:32:55 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 20 22:32:55 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 5 of 5 (IPv4 Commit) started...
Jun 20 22:32:56 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 20 22:32:56 x201 NetworkManager[1168]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Jun 20 22:32:56 x201 dnsmasq[15173]: setting upstream servers from DBus
Jun 20 22:32:56 x201 dnsmasq[15173]: using nameserver 213.94.78.17#53
Jun 20 22:32:56 x201 dnsmasq[15173]: using nameserver 213.94.78.16#53
Jun 20 22:32:56 x201 NetworkManager[1168]: <info> Policy set '3 AT - Hutchinson 3G' (ppp0) as default for IPv4 routing and DNS.
Jun 20 22:32:56 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) successful, device activated.
Jun 20 22:32:56 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 5 of 5 (IPv4 Commit) complete.
Jun 20 22:32:56 x201 dbus[1126]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 20 22:32:56 x201 dbus[1126]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 20 22:33:09 x201 ntpdate[9618]: adjust time server 91.189.94.4 offset 0.029304 sec
Jun 20 22:36:58 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/net/wwan0, iface: wwan0)
Jun 20 22:36:58 x201 kernel: [ 5123.667910] usb 2-1.4: USB disconnect, device number 15
Jun 20 22:36:58 x201 kernel: [ 5123.668006] qmi_wwan 2-1.4:1.0: wwan0: unregister 'qmi_wwan' usb-0000:00:1d.0-1.4, Qualcomm WWAN/QMI device
Jun 20 22:36:58 x201 pppd[9508]: Modem hangup
Jun 20 22:36:58 x201 pppd[9508]: Connect time 4.1 minutes.
Jun 20 22:36:58 x201 pppd[9508]: Sent 346350 bytes, received 975804 bytes.
Jun 20 22:36:58 x201 modem-manager[1138]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4
Jun 20 22:36:58 x201 modem-manager[1138]: <info>  (ttyUSB1) closing serial port...
Jun 20 22:36:58 x201 modem-manager[1138]: <info>  (ttyUSB1) serial port closed
Jun 20 22:36:58 x201 modem-manager[1138]: <info>  (tty/ttyUSB1): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4
Jun 20 22:36:58 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/6: state changed (connected -> disabled)
Jun 20 22:36:58 x201 dnsmasq[1401]: reading /etc/resolv.conf
Jun 20 22:36:58 x201 dnsmasq[1401]: using nameserver 127.0.1.1#53
Jun 20 22:36:59 x201 kernel: [ 5123.677196] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
Jun 20 22:36:59 x201 kernel: [ 5123.677229] qcserial 2-1.4:1.1: device disconnected
Jun 20 22:36:59 x201 kernel: [ 5123.677920] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
Jun 20 22:36:59 x201 kernel: [ 5123.677939] qcserial 2-1.4:1.2: device disconnected
Jun 20 22:36:59 x201 kernel: [ 5123.678963] qcserial ttyUSB2: Qualcomm USB modem converter now disconnected from ttyUSB2
Jun 20 22:36:59 x201 kernel: [ 5123.679003] qcserial 2-1.4:1.3: device disconnected
Jun 20 22:36:59 x201 NetworkManager[1168]: <info> (ttyUSB1): now unmanaged
Jun 20 22:36:59 x201 pppd[9508]: Connection terminated.
Jun 20 22:36:59 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Jun 20 22:36:59 x201 kernel: [ 5123.879110] usb 2-1.4: new high-speed USB device number 16 using ehci_hcd
Jun 20 22:36:59 x201 NetworkManager[1168]: <info> (ttyUSB1): deactivating device (reason 'removed') [36]
Jun 20 22:36:59 x201 NetworkManager[1168]: <warn> could not read ppp stats: No such device
Jun 20 22:36:59 x201 pppd[9508]: Exit.
Jun 20 22:36:59 x201 NetworkManager[1168]: <warn> DNS: plugin dnsmasq update failed
Jun 20 22:36:59 x201 NetworkManager[1168]: <info> ((null)): removing resolv.conf from /sbin/resolvconf
Jun 20 22:36:59 x201 dnsmasq[15173]: setting upstream servers from DBus
Jun 20 22:36:59 x201 NetworkManager[1168]: <info> (ttyUSB1): cleaning up...
Jun 20 22:36:59 x201 NetworkManager[1168]: <info> (ttyUSB1): taking down device.
Jun 20 22:36:59 x201 NetworkManager[1168]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun 20 22:36:59 x201 dbus[1126]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 20 22:36:59 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 20 22:36:59 x201 dbus[1126]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 20 22:36:59 x201 kernel: [ 5123.976570] usb 2-1.4: config 1 has an invalid interface number: 1 but max is 0
Jun 20 22:36:59 x201 kernel: [ 5123.976578] usb 2-1.4: config 1 has no interface number 0
Jun 20 22:36:59 x201 kernel: [ 5123.978442] usb 2-1.4: New USB device found, idVendor=05c6, idProduct=9204
Jun 20 22:36:59 x201 kernel: [ 5123.978447] usb 2-1.4: New USB device strings: Mfr=3, Product=2, SerialNumber=0
Jun 20 22:36:59 x201 kernel: [ 5123.978450] usb 2-1.4: Product: Qualcomm Gobi 2000
Jun 20 22:36:59 x201 kernel: [ 5123.978452] usb 2-1.4: Manufacturer: Qualcomm Incorporated
Jun 20 22:36:59 x201 kernel: [ 5123.980004] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
Jun 20 22:36:59 x201 kernel: [ 5123.980311] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
Jun 20 22:36:59 x201 mtp-probe: checking bus 2, device 16: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Jun 20 22:36:59 x201 mtp-probe: bus: 2, device: 16 was not an MTP device
Jun 20 22:37:04 x201 kernel: [ 5128.779112] usb 2-1.4: USB disconnect, device number 16
Jun 20 22:37:04 x201 kernel: [ 5128.779392] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
Jun 20 22:37:04 x201 kernel: [ 5128.779429] qcserial 2-1.4:1.1: device disconnected
Jun 20 22:37:04 x201 kernel: [ 5129.042316] usb 2-1.4: new high-speed USB device number 17 using ehci_hcd
Jun 20 22:37:04 x201 kernel: [ 5129.136658] usb 2-1.4: New USB device found, idVendor=05c6, idProduct=9205
Jun 20 22:37:04 x201 kernel: [ 5129.136666] usb 2-1.4: New USB device strings: Mfr=3, Product=2, SerialNumber=0
Jun 20 22:37:04 x201 kernel: [ 5129.136671] usb 2-1.4: Product: Qualcomm Gobi 2000
Jun 20 22:37:04 x201 kernel: [ 5129.136675] usb 2-1.4: Manufacturer: Qualcomm Incorporated
Jun 20 22:37:04 x201 kernel: [ 5129.140166] qmi_wwan 2-1.4:1.0: cdc-wdm0: USB WDM device
Jun 20 22:37:04 x201 kernel: [ 5129.140517] qmi_wwan 2-1.4:1.0: wwan0: register 'qmi_wwan' at usb-0000:00:1d.0-1.4, Qualcomm WWAN/QMI device, ae:73:4a:98:24:63
Jun 20 22:37:04 x201 kernel: [ 5129.140628] qmi_wwan 2-1.4:1.1: not on our whitelist - ignored
Jun 20 22:37:04 x201 kernel: [ 5129.141348] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
Jun 20 22:37:04 x201 kernel: [ 5129.141495] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
Jun 20 22:37:04 x201 kernel: [ 5129.141602] qmi_wwan 2-1.4:1.2: not on our whitelist - ignored
Jun 20 22:37:04 x201 kernel: [ 5129.142506] qcserial 2-1.4:1.2: Qualcomm USB modem converter detected
Jun 20 22:37:04 x201 kernel: [ 5129.142641] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB1
Jun 20 22:37:04 x201 kernel: [ 5129.142741] qmi_wwan 2-1.4:1.3: not on our whitelist - ignored
Jun 20 22:37:04 x201 kernel: [ 5129.143360] qcserial 2-1.4:1.3: Qualcomm USB modem converter detected
Jun 20 22:37:04 x201 kernel: [ 5129.143489] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB2
Jun 20 22:37:04 x201 mtp-probe: checking bus 2, device 17: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Jun 20 22:37:04 x201 mtp-probe: bus: 2, device: 17 was not an MTP device
Jun 20 22:37:04 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/net/wwan0, iface: wwan0)
Jun 20 22:37:04 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/net/wwan0, iface: wwan0): no ifupdown configuration found.
Jun 20 22:37:04 x201 modem-manager[1138]: <info>  (ttyUSB2) opening serial port...
Jun 20 22:37:04 x201 modem-manager[1138]: <warn>  (ttyUSB2): port attributes not fully set
Jun 20 22:37:04 x201 modem-manager[1138]: <info>  (ttyUSB0) opening serial port...
Jun 20 22:37:04 x201 modem-manager[1138]: <warn>  (ttyUSB0): port attributes not fully set
Jun 20 22:37:04 x201 modem-manager[1138]: <info>  (ttyUSB1) opening serial port...
Jun 20 22:37:04 x201 modem-manager[1138]: <warn>  (ttyUSB1): port attributes not fully set
Jun 20 22:37:12 x201 modem-manager[1138]: <info>  (ttyUSB1) closing serial port...
Jun 20 22:37:12 x201 modem-manager[1138]: <info>  (ttyUSB1) serial port closed
Jun 20 22:37:12 x201 modem-manager[1138]: <info>  (Gobi): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 claimed port ttyUSB1
Jun 20 22:37:16 x201 modem-manager[1138]: <info>  (ttyUSB2) closing serial port...
Jun 20 22:37:16 x201 modem-manager[1138]: <info>  (ttyUSB2) serial port closed
Jun 20 22:37:16 x201 modem-manager[1138]: <info>  (ttyUSB2) opening serial port...
Jun 20 22:37:17 x201 modem-manager[1138]: <info>  (ttyUSB0) closing serial port...
Jun 20 22:37:17 x201 modem-manager[1138]: <info>  (ttyUSB0) serial port closed
Jun 20 22:37:17 x201 modem-manager[1138]: <info>  (ttyUSB0) opening serial port...
Jun 20 22:37:17 x201 modem-manager[1138]: <info>  (ttyUSB0) closing serial port...
Jun 20 22:37:17 x201 modem-manager[1138]: <info>  (ttyUSB0) serial port closed
Jun 20 22:37:17 x201 modem-manager[1138]: <info>  (Gobi): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 claimed port ttyUSB0
Jun 20 22:37:22 x201 modem-manager[1138]: <info>  (ttyUSB2) closing serial port...
Jun 20 22:37:22 x201 modem-manager[1138]: <info>  (ttyUSB2) serial port closed
Jun 20 22:37:22 x201 modem-manager[1138]: <info>  (ttyUSB1) opening serial port...
Jun 20 22:37:22 x201 modem-manager[1138]: <warn>  (ttyUSB1): port attributes not fully set
Jun 20 22:37:23 x201 NetworkManager[1168]: <warn> (ttyUSB1): failed to look up interface index
Jun 20 22:37:23 x201 NetworkManager[1168]: <info> WWAN now disabled by management service
Jun 20 22:37:23 x201 NetworkManager[1168]: <info> (ttyUSB1): new GSM/UMTS device (driver: 'qcserial' ifindex: 0)
Jun 20 22:37:23 x201 NetworkManager[1168]: <info> (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/9
Jun 20 22:37:23 x201 NetworkManager[1168]: <info> (ttyUSB1): now managed
Jun 20 22:37:23 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 20 22:37:23 x201 NetworkManager[1168]: <info> (ttyUSB1): deactivating device (reason 'managed') [2]
Jun 20 22:37:23 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jun 20 22:37:23 x201 modem-manager[1138]: <info>  (ttyUSB1) closing serial port...
Jun 20 22:37:23 x201 modem-manager[1138]: <info>  (ttyUSB1) serial port closed
Jun 20 22:37:24 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) starting connection '3 AT - Hutchinson 3G'
Jun 20 22:37:24 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 20 22:37:24 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Jun 20 22:37:24 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Jun 20 22:37:24 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Jun 20 22:37:24 x201 modem-manager[1138]: <info>  (ttyUSB1) opening serial port...
Jun 20 22:37:24 x201 modem-manager[1138]: <warn>  (ttyUSB1): port attributes not fully set
Jun 20 22:37:24 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/7: state changed (disabled -> enabling)
Jun 20 22:37:24 x201 modem-manager[1138]: <info>  (ttyUSB1): using PDU mode for SMS
Jun 20 22:37:25 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/7: state changed (enabling -> enabled)
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> WWAN now enabled by management service
Jun 20 22:37:25 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/7: state changed (enabled -> registered)
Jun 20 22:37:25 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/7: state changed (registered -> connecting)
Jun 20 22:37:25 x201 modem-manager[1138]: <info>  Modem /org/freedesktop/ModemManager/Modems/7: state changed (connecting -> connected)
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> starting PPP connection
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> pppd started with pid 19590
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 20 22:37:25 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 20 22:37:25 x201 pppd[19590]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Jun 20 22:37:25 x201 pppd[19590]: pppd 2.4.5 started by root, uid 0
Jun 20 22:37:25 x201 pppd[19590]: Using interface ppp0
Jun 20 22:37:25 x201 pppd[19590]: Connect: ppp0 <--> /dev/ttyUSB1
Jun 20 22:37:25 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 20 22:37:25 x201 NetworkManager[1168]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun 20 22:37:25 x201 NetworkManager[1168]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jun 20 22:37:25 x201 pppd[19590]: CHAP authentication succeeded
Jun 20 22:37:25 x201 pppd[19590]: CHAP authentication succeeded
Jun 20 22:37:29 x201 pppd[19590]: Could not determine remote IP address: defaulting to 10.64.64.64
Jun 20 22:37:29 x201 dnsmasq[1401]: no servers found in /etc/resolv.conf, will retry
Jun 20 22:37:29 x201 pppd[19590]: local  IP address 10.34.8.202
Jun 20 22:37:29 x201 pppd[19590]: remote IP address 10.64.64.64
Jun 20 22:37:29 x201 pppd[19590]: primary   DNS address 213.94.78.16
Jun 20 22:37:29 x201 pppd[19590]: secondary DNS address 213.94.78.17
Jun 20 22:37:29 x201 NetworkManager[1168]: <info> PPP manager(IP Config Get) reply received.
Jun 20 22:37:29 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 20 22:37:29 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 5 of 5 (IPv4 Commit) started...
Jun 20 22:37:30 x201 NetworkManager[1168]: <info> (ttyUSB1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 20 22:37:30 x201 NetworkManager[1168]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Jun 20 22:37:30 x201 dnsmasq[15173]: setting upstream servers from DBus
Jun 20 22:37:30 x201 dnsmasq[15173]: using nameserver 213.94.78.17#53
Jun 20 22:37:30 x201 dnsmasq[15173]: using nameserver 213.94.78.16#53
Jun 20 22:37:30 x201 NetworkManager[1168]: <info> Policy set '3 AT - Hutchinson 3G' (ppp0) as default for IPv4 routing and DNS.
Jun 20 22:37:30 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) successful, device activated.
Jun 20 22:37:30 x201 NetworkManager[1168]: <info> Activation (ttyUSB1) Stage 5 of 5 (IPv4 Commit) complete.
Jun 20 22:37:30 x201 dbus[1126]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 20 22:37:30 x201 dbus[1126]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 20 22:37:43 x201 ntpdate[20422]: adjust time server 91.189.94.4 offset -0.064540 sec

---

### Post by Supercomputerpower on 2013-06-20
[http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889) try to login there is a bugfix this could be the problem

---

### Post by bmork on 2013-06-21
> **shylingo said:**
> Jun 20 22:36:58 x201 kernel: [ 5123.667910] usb 2-1.4: USB disconnect, device number 15


The modem was disconnected from the USB bus.  Based on your report I assume that you didn't trigger this (using rfkill or a radio killswitch).  The only likely cause remaining is a firmware crash.  I don't have any better advice than trying to locate some other firmware version and see if it works better.  Being a Gobi card it is at least easy to experiment with different firmware versions.

---

### Post by shylingo on 2013-06-21
@bmork: thank you very much, i totally forgot that option!! i'll give it a try within the next hours and i'll post the results!

---

### Post by shylingo on 2013-06-21
hm. the first different one - exactly the same thing happens...

first the usb device disconnects:

Jun 21 20:39:37 x201 NetworkManager[1154]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/net/wwan0, iface: wwan0)
Jun 21 20:39:37 x201 kernel: [ 1187.982047] usb 2-1.4: USB disconnect, device number 3
Jun 21 20:39:37 x201 kernel: [ 1187.982152] qmi_wwan 2-1.4:1.0: wwan0: unregister 'qmi_wwan' usb-0000:00:1d.0-1.4, Qualcomm WWAN/QMI device
Jun 21 20:39:37 x201 pppd[5197]: Modem hangup
Jun 21 20:39:37 x201 pppd[5197]: Connect time 18.6 minutes.
Jun 21 20:39:37 x201 pppd[5197]: Sent 1142752 bytes, received 16614129 bytes.
Jun 21 20:39:37 x201 kernel: [ 1187.987719] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0

---

### Post by Supercomputerpower on 2013-06-21
[http://support.lenovo.com/en_US/product-and-parts/detail.page?LegacyDocID=MIGR-70149](http://support.lenovo.com/en_US/product-and-parts/detail.page?LegacyDocID=MIGR-70149) maybe it connects bad page 90 of pdf put it out and in again, but only if you are capable of doing such a thing and warranty is not compromised.

---

### Post by shylingo on 2013-06-26
@supercomputerpower: i tried even that, it did not work.

---

