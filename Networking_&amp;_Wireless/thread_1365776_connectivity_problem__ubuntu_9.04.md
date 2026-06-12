---
title: "connectivity problem  ubuntu 9.04"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by cleto65 on 2009-12-27
**anydata adu-5100 connectivity problem** 
hi,,
I am having problems connecting to the internet using **[COLOR=#ff0000]anydata[/COLOR]** adu-5100 cdma modem....


here is the output




NetworkManager: <info> starting...
NetworkManager: <info> (eth0): new Ethernet device (driver: 'smsc95xx')
NetworkManager: <info> (eth0): exported as /org/freedesktop/Hal/devices/net_00_24_25_07_02_62
NetworkManager: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
NetworkManager: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k_pci')
NetworkManager: <info> (wlan0): exported as /org/freedesktop/Hal/devices/net_00_25_d3_76_ee_7a
NetworkManager: <info> (ttyUSB1): ignoring due to lack of mobile broadband capabilties
NetworkManager: <info> (ttyUSB2): ignoring due to lack of mobile broadband capabilties
NetworkManager: <info> (ttyUSB0): found serial port (udev:CDMA hal:CDMA)
NetworkManager: <info> (ttyUSB0): new Modem device (driver: 'option')
NetworkManager: <info> (ttyUSB0): exported as /org/freedesktop/Hal/devices/usb_device_16d5_6502_noserial_if0_serial_usb_0
NetworkManager: <info> Unmanaged Device found; state CONNECTED forced. (see [[COLOR=#444444]http://bugs.launchpad.net/bugs/191889[/COLOR]]("http://bugs.launchpad.net/bugs/191889"))
NetworkManager: <info> Unmanaged Device found; state CONNECTED forced. (see [[COLOR=#444444]http://bugs.launchpad.net/bugs/191889[/COLOR]]("http://bugs.launchpad.net/bugs/191889"))
NetworkManager: <info> (eth0): device state change: 1 -> 2
NetworkManager: <info> (eth0): bringing up device.
NetworkManager: <info> (eth0): preparing device.
NetworkManager: <info> (eth0): deactivating device (reason: 2).
NetworkManager: <info> Unmanaged Device found; state CONNECTED forced. (see [[COLOR=#444444]http://bugs.launchpad.net/bugs/191889[/COLOR]]("http://bugs.launchpad.net/bugs/191889"))
NetworkManager: <info> (wlan0): device state change: 1 -> 2
NetworkManager: <info> (wlan0): bringing up device.
NetworkManager: <info> (wlan0): preparing device.
NetworkManager: <info> (wlan0): deactivating device (reason: 2).
NetworkManager: <info> Unmanaged Device found; state CONNECTED forced. (see [[COLOR=#444444]http://bugs.launchpad.net/bugs/191889[/COLOR]]("http://bugs.launchpad.net/bugs/191889"))
NetworkManager: <info> (ttyUSB0): device state change: 1 -> 2
NetworkManager: <info> (ttyUSB0): deactivating device (reason: 2).
NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: <info> (eth0): carrier now ON (device state 2)
NetworkManager: <info> (eth0): device state change: 2 -> 3
NetworkManager: <info> (wlan0): device state change: 2 -> 3
NetworkManager: <info> (ttyUSB0): device state change: 2 -> 3
NetworkManager: <info> Activation (eth0) starting connection 'osel'
NetworkManager: <info> (eth0): device state change: 3 -> 4
NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info> Activation (ttyUSB0) starting connection 'movinet'
NetworkManager: <info> (ttyUSB0): device state change: 3 -> 4
NetworkManager: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <debug> [1261696480.188866] nm_serial_device_open(): (ttyUSB0) opening device...
NetworkManager: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info> (eth0): device state change: 4 -> 5
NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info> (wlan0): supplicant interface state: starting -> ready
NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info> (eth0): device state change: 5 -> 7
NetworkManager: <info> Activation (eth0) Beginning DHCP transaction.
NetworkManager: <info> dhclient started with pid 4039
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
For info, please visit [[COLOR=#444444]http://www.isc.org/sw/dhcp/[/COLOR]]("http://www.isc.org/sw/dhcp/")
wmaster0: unknown hardware address type 801
NetworkManager: <info> DHCP: device eth0 state changed (null) -> preinit
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:24:25:07:02:62
Sending on LPF/eth0/00:24:25:07:02:62
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
NetworkManager: <debug> [1261696480.303151] nm_serial_debug(): Sending: 'ATZ E0
'
NetworkManager: <debug> [1261696480.337704] nm_serial_debug(): Got: '
OK
'
NetworkManager: <info> (ttyUSB0): powering up...
NetworkManager: <debug> [1261696480.339123] nm_serial_debug(): Sending: 'at!pcstate=1
'
NetworkManager: <debug> [1261696480.371223] nm_serial_debug(): Got: '
ERROR
'
NetworkManager: <debug> [1261696480.371577] nm_serial_debug(): Sending: 'ATDT#777
'
NetworkManager: <debug> [1261696480.699419] nm_serial_debug(): Got: '
CONNECT
'
NetworkManager: <info> Connected, Woo!
NetworkManager: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info> (ttyUSB0): device state change: 4 -> 5
NetworkManager: <info> Starting pppd connection
NetworkManager: <debug> [1261696480.714144] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user [EMAIL="911179332@movinet3g.co.ao"][COLOR=#444444]911179332@movinet3g.co.ao[/COLOR][/EMAIL] ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 5 lcp-echo-interval 30 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
NetworkManager: <debug> [1261696480.722353] nm_ppp_manager_start(): ppp started with pid 4044
NetworkManager: <info> Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
** (process:4044): WARNING **: Could not get secrets: Rejected send message, 7 matched rules; type="method_call", sender=":1.58" (uid=0 pid=4044 comm="/usr/sbin/pppd nodetach lock nodefaultroute user 9") interface="org.freedesktop.NetworkManager.PPP" member="NeedSecrets" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager" (uid=0 pid=4030 comm="NetworkManager --no-daemon "))
Unable to obtain CHAP password for [EMAIL="911179332@movinet3g.co.ao"][COLOR=#444444]911179332@movinet3g.co.ao[/COLOR][/EMAIL] on from plugin
No CHAP secret found for authenticating us to 
CHAP authentication succeeded
CHAP authentication succeeded
Cannot determine ethernet address for proxy ARP
local IP address 41.210.230.130
remote IP address 10.2.0.9
primary DNS address 217.168.127.15
secondary DNS address 217.168.127.14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
NetworkManager: <WARN> pppd_timed_out(): Looks like pppd didn't initialize our dbus module
NetworkManager: <info> (ttyUSB0): device state change: 5 -> 9
NetworkManager: <debug> [1261696496.004272] nm_serial_device_close(): Closing device 'ttyUSB0'
Terminating on signal 15
Connect time 0.3 minutes.
Sent 0 bytes, received 0 bytes.
NetworkManager: <info> Marking connection 'movinet' invalid.
NetworkManager: <info> Activation (ttyUSB0) failed.
NetworkManager: <info> (ttyUSB0): device state change: 9 -> 3
NetworkManager: <info> (ttyUSB0): deactivating device (reason: 0).
NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Connection terminated.
NetworkManager: <debug> [1261696498.001211] ensure_killed(): waiting for ppp pid 4044 to exit
NetworkManager: <debug> [1261696498.001547] ensure_killed(): ppp pid 4044 cleaned up
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
NetworkManager: <info> Device 'eth0' DHCP transaction took too long (>45s), stopping it.
NetworkManager: <info> eth0: canceled DHCP transaction, dhcp client pid 4039
NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled...
NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started...
NetworkManager: <info> (eth0): device state change: 7 -> 9
NetworkManager: <info> Marking connection 'osel' invalid.
NetworkManager: <info> Activation (eth0) failed.
NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete.
NetworkManager: <info> (eth0): device state change: 9 -> 3
NetworkManager: <info> (eth0): deactivating device (reason: 0).
NetworkManager: <info> Activation (eth0) starting connection 'local_camilo'
NetworkManager: <info> (eth0): device state change: 3 -> 4
NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info> (eth0): device state change: 4 -> 5
NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info> (eth0): device state change: 5 -> 7
NetworkManager: <info> Activation (eth0) Beginning DHCP transaction.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [[COLOR=#444444]http://www.isc.org/sw/dhcp/[/COLOR]]("http://www.isc.org/sw/dhcp/")
wmaster0: unknown hardware address type 801
NetworkManager: <info> dhclient started with pid 4078
NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <info> DHCP: device eth0 state changed normal exit -> preinit
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:24:25:07:02:62
Sending on LPF/eth0/00:24:25:07:02:62
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
NetworkManager: <info> Device 'eth0' DHCP transaction took too long (>45s), stopping it.
NetworkManager: <info> eth0: canceled DHCP transaction, dhcp client pid 4078
NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled...
NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started...
NetworkManager: <info> (eth0): device state change: 7 -> 9
NetworkManager: <info> Marking connection 'local_camilo' invalid.
NetworkManager: <info> Activation (eth0) failed.
NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete.
NetworkManager: <info> (eth0): device state change: 9 -> 3
NetworkManager: <info> (eth0): deactivating device (reason: 0).
NetworkManager: <info> (ttyUSB0): now unmanaged
NetworkManager: <info> (ttyUSB0): device state change: 3 -> 1
NetworkManager: <info> (ttyUSB0): cleaning up...
NetworkManager: <info> (ttyUSB0): taking down device.



I am using ubuntu 9.04 and this happened after an update

---

